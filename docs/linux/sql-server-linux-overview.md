---
title: "SQL Server on Linux 개요 | Microsoft Docs"
description: "이 항목에서는 SQL 서버를 Linux에서 실행하는 방법 및 보다 자세히 학습하는 방법에 대한 정보를 제공합니다."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 48e2d1ae54100f7ea83bdd677bf4a98859825b67
ms.contentlocale: ko-kr
ms.lasthandoff: 10/05/2017

---
# <a name="sql-server-on-linux">Linux에서 SQL Server</a>

SQL Server 2017이 이제 Linux에서 실행됩니다. 운영체제와 관계없이 많은 유사 기능 및 서비스를 제공하는 동일한 SQL Server 데이터베이스 엔진입니다.

## <a name="install">설치</a>

시작 하려면, 다음 빠른 시작 자습서 중 하나를 참고하여 Linux에 SQL Server를 설치합니다.

- [Red Hat Enterprise Linux에 설치](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server에 설치](quickstart-install-connect-suse.md)
- [Ubuntu에 설치](quickstart-install-connect-ubuntu.md)
- [Docker에서 실행](quickstart-install-connect-docker.md)
- [Azure에 SQL VM 프로비전](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker 자체는 여러 플랫폼에서 실행됩니다 즉, Linux, Mac 및 Windows에서 Docker 이미지를 실행할 수 있음을 의미합니다.

## <a name="connect">연결</a>

설치 후, Linux 컴퓨터에서 SQL Server 인스턴스에 연결합니다. 로컬 또는 원격으로 다양한 도구 및 드라이버를 사용하여 연결할 수 있습니다. 빠른 시작 자습서에서는 [sqlcmd](sql-server-linux-setup-tools.md) 명령줄 도구를 사용하는 방법을 보여줍니다. 다음과 같은 다른 도구들도 있습니다.

| 도구 | 자습서 |
|-----|-----|
| Visual Studio Code (VS Code) | [SQL Server on Linux와 함께 VS Code 사용](sql-server-linux-develop-use-vscode.md) |
| SSMS(SQL Server Management Studio) | [SQL Server on Linux에 연결하기 위해 Windows에서 SSMS 사용](sql-server-linux-develop-use-ssms.md) |
| SQL  Server  Data  Tools(SSDT) | [SQL Server on Linux와 함께 SSDT 사용](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore">탐색</a>

SQL Server 2017은 Linux를 포함하여 모든 지원되는 플랫폼에 동일한 기본 데이터베이스 엔진을 가지고 있습니다. 따라서 많은 기존 기능 및 성능이 Linux에서 동일한 방식으로 동작합니다. 이 문서에서는 Linux 관점에서 해당 기능 중 일부 범위에 대해 설명합니다. 또한 Linux에만 해당하는 요구 사항에 대해 설명합니다.

SQL Server에 이미 익숙한 경우, [릴리스 정보](sql-server-linux-release-notes.md) 를 참고하여 일반적인 지침과 릴리스의 알려진 문제에 대해 살펴봅니다. 그리고 [SQL Server on Linux에 대한 새로운 기능](sql-server-linux-whats-new.md) 및 [SQL Server 2017 전반에 대한 새로운 기능](../sql-server/what-s-new-in-sql-server-2017.md) 을 살펴봅니다.

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"> SQL Server 엔지니어링 팀에 문의</a>![info_tip](./media/general/info_tip.png)

- [DBA 스택 Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): 데이터베이스 관리에 대해 질문하기
- [스택 오버플로](http://stackoverflow.com/questions/tagged/sql-server): 개발에 대해 질문하기
- [MSDN 포럼](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): 기술 관련 질문하기
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): 요청 기능 및 버그를 보고하기.
- [Reddit](https://www.reddit.com/r/SQLServer/): SQL Server 토론

