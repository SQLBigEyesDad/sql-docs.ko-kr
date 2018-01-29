---
title: "입력 및 출력 작업 (R in SQL 빠른 시작) | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
- SQL
ms.assetid: 75480e5c-f37f-45b9-a176-67e08e9a9daf
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: a5ffcfafc29f0b741d8e6ada0d50ef6f94fecc7f
ms.contentlocale: ko-kr
ms.lasthandoff: 09/27/2017

---
# <a name="working-with-inputs-and-outputs-r-in-sql-quickstart"></a>입력 및 출력 작업 (R in SQL 빠른 시작)

SQL Server에서 R 코드를 실행하려는 경우 R 스크립트를 시스템 저장 프로시저 [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 내부에 지정합니다. 이 저장 프로시저는 SQL Server의 컨텍스트에서 R 런타임 시작하고, 데이터를 R에 전달하고, R 사용자 세션을 안전하게 관리하며 결과를 클라이언트로 반환하는데 사용됩니다.

## <a name="bkmk_SSMSBasics"></a>몇 가지 간단한 테스트 데이터 만들기

다음 T-SQL 문을 실행하여 테스트 데이터로 구성된 작은 테이블을 만듭니다.

```sql
CREATE TABLE RTestData ([col1] int not null) ON [PRIMARY]
INSERT INTO RTestData   VALUES (1);
INSERT INTO RTestData   VALUES (10);
INSERT INTO RTestData   VALUES (100) ;
GO
```

테이블을 만들었으면 다음 문을 사용하여 테이블을 쿼리합니다.
  
```sql
SELECT * FROM RTestData
```

**결과**

|col1|
|------|
|*1.*|
|*10*|
|*100*|

## <a name="get-the-same-data-using-r-script"></a>R 스크립트를 사용하여 동일한 데이터 가져오기

테이블을 만든 후 다음 문을 실행합니다.

```sql
EXECUTE sp_execute_external_script
      @language = N'R'
    , @script = N' OutputDataSet <- InputDataSet;'
    , @input_data_1 = N' SELECT *  FROM RTestData;'
    WITH RESULT SETS (([NewColName] int NOT NULL));
```

테이블에서 데이터를 가져옵니다, R 런타임을 왕복한 뒤 *NewColName*열 이름으로 값을 반환합니다.

**결과**

![rsql_basictut_getsamedataR](media/rsql-basictut-getsamedatar.PNG)


**주석**

+ Management Studio에서는 테이블 형식 결과가 **결과** 탭에 반환됩니다. R 런타임에서 반환된 메시지는 **메시지** 탭에 제공됩니다. (역주: 원문은 Values pane에 결과가 반환된다고 언급하고 있어서 “결과” 탭으로 수정했습니다).
+ *@language* 매개 변수는 호출할 언어 확장(이 경우 R)을 정의합니다.
+ *@script* 매개 변수에서 R 런타임에 전달할 명령을 정의합니다. 전체 R 스크립트는 이 인수에 유니코드 텍스트로 포함되어야 합니다. **nvarchar** 형식의 변수에 텍스트를 추가한 다음 변수를 호출할 수도 있습니다.
+ 쿼리에서 반환된 데이터는 R 런타임에 전달되고 R 런타임은 데이터를 SQL Server에 데이터 프레임으로 전달합니다.
+ WITH RESULT SETS 절은 SQL Server에 반환된 데이터 테이블의 스키마를 정의합니다.

## <a name="change-input-or-output-variables"></a>입력 또는 출력 변수 변경

이전 예제에서는 기본 입력 및 출력 변수 이름으로 _InputDataSet_ 및 _OutputDataSet_을 사용했습니다. _InputDatSet_과 연결된 입력 데이터를 정의하려면 *@input_data_1* 변수를 사용합니다.

이 예제에서는 저장 프로시저에 대한 출력 및 입력 변수의 이름이 *SQL_Out* 및 *SQL_In*으로 변경되었습니다.

```sql
EXECUTE sp_execute_external_script
  @language = N'R'
  , @script = N' SQL_out <- SQL_in;'
  , @input_data_1 = N' SELECT 12 as Col;'
  , @input_data_1_name  = N'SQL_In'
  , @output_data_1_name =  N'SQL_Out'
  WITH RESULT SETS (([NewColName] int NOT NULL));
```
(역주. 이후 설명과 실제 오류 내용이 맞지 않아 내용을 편집했습니다. 궁금하신 분들은 원문을 참조하세요)

“sp_execute_external_script'를 실행하는 동안 'R' 스크립트 오류가 발생했습니다…” 라는 오류가 발생합니다. 원인은 R이 대/소문자를 구분하기 때문입니다. R 스크립트에서는 변수명으로 *SQL_in* 및 *SQL_out*을 사용하지만 저장 프로시저의 매개 변수는 *SQL_In* 및 *SQL_Out*으로 정의되었기 때문입니다. 

이제 *SQL_In* 변수를 대소문자 동일하게 맞춘 뒤 프로시저를 다시 실행합니다.

또 **다른** 오류가 발생합니다:

```Error
EXECUTE 문의 WITH RESULT SETS 절에 1개의 결과 집합이 지정되었지만 런타임에 0개의 결과 집합만 보냈으므로 문이 실패했습니다.
```

새로운 R 코드를 테스트할 때 자주 만날 수 있는 오류입니다. R 스크립트는 성공적으로 실행했지만 SQL Server가 수신한 데이터가 없거나 혹은 잘못되거나 예기치 않은 데이터를 받았음을 의미합니다.

위의 경우 출력 스키마(**WITH**로 시작하는 줄)는 정수 데이터 열 하나를 반환되도록 지정했지만, R에서 다른 변수에 데이터를 넣기 때문에 SQL Server에 아무것도 반환되지 않으므로 오류가 발생합니다. 오류를 해결하려면 두 번째 변수 이름을 수정하십시오.

**다음 요구 사항을 기억하세요!**

- 변수 이름은 유효한 SQL 식별자 규칙을 따라야 합니다.
- 매개 변수의 순서가 중요합니다. 선택적 매개 변수 *@input_data_1_name* 및 *@output_data_1_name*을 사용하기 위해 먼저 필수 매개 변수 *@input_data_1* 및 *@output_data_1*을 지정해야 합니다.
- 하나의 입력 데이터 집합만 매개 변수로 전달할 수 있으며 하나의 데이터 집합만 반환할 수 있습니다. 그러나 R 코드 내에서 다른 데이터 집합을 호출할 수 있으며 데이터 집합 외에 다른 유형의 출력을 반환할 수 있습니다. 또한 모든 매개 변수에 OUTPUT 키워드를 추가하여 결과와 함께 매개 변수를 반환할 수도 있습니다. 이 자습서의 뒷부분에 간단한 예제가 있습니다.
- `WITH RESULT SETS` 문은 SQL Server를 위해 데이터에 대한 스키마를 정의합니다. R에서 반환하는 각 열에 대한 SQL 호환 데이터 형식을 제공해야 합니다. 스키마 정의를 사용하여 새 열 이름도 제공할 수 있고 R data.frame의 열 이름을 사용할 필요가 없습니다. 경우에 따라 이 절은 생략 가능합니다. 생략하면 어떻게 되는지 확인해 보세요.

## <a name="generate-results-using-r"></a>R을 사용하여 결과 생성

R 스크립트를 사용하여 값을 생성하고 _@input_data_1_ 의 입력 쿼리 문자열은 비워 둘 수도 있습니다. 또는 유효한 SQL SELECT 문을 자리 표시자로 사용하고 R 스크립트에는 SQL 결과를 사용하지 마세요.

```sql
EXECUTE sp_execute_external_script
    @language = N'R'
   , @script = N' mytextvariable <- c("hello", " ", "world");
       OutputDataSet <- as.data.frame(mytextvariable);'
   , @input_data_1 = N' SELECT 1 as Temp1'
   WITH RESULT SETS (([Col1] char(20) NOT NULL));
```

**결과**

*Col1*
*hello*
<code>   </code>
*world*

## <a name="next-lesson"></a>다음 단원

R과 SQL 간 테이블 형식 데이터의 암시적 변환 및 차이점을 포함하여 R과 SQL Server 간에 데이터를 전달할 때 발생할 수 있는 몇 가지 문제를 살펴보겠습니다.

[R 및 SQL 데이터 형식 및 데이터 개체](../tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)

