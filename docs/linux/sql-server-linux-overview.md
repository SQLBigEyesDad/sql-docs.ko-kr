---
title: "Linux에서 SQL Server 개요 | Microsoft Docs"
description: "이 항목에서는 SQL 서버가 Linux에서 실행 하 고 자세한 방법에 대해 설명 하는 방법을 설명 합니다."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 80c1228faeaaa4012afc0fd27992a2f5cf389f6e
ms.openlocfilehash: 48e2d1ae54100f7ea83bdd677bf4a98859825b67
ms.contentlocale: ko-kr
ms.lasthandoff: 10/05/2017

---
# <a name="sql-server-on-linux"></a>Linux에서 SQL Server

이제 SQL Server 2017이 Linux에서 실행 됩니다. 운영 체제와 상관없이 많은 유사 기능과 서비스를 가진 동일한 SQL Server 데이터베이스 엔진입니다.

## <a name="install"></a>Install

시작하기위해서 다음 빠른 시작 자습서 중 하나를 사용 하 여 Linux에 SQL Server를 설치 합니다.

- [Red Hat Enterprise Linux에 설치](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server에 설치](quickstart-install-connect-suse.md)
- [Ubuntu 설치](quickstart-install-connect-ubuntu.md)
- [Docker에서 실행](quickstart-install-connect-docker.md)
- [Azure에서 SQL VM 프로비전](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docket 이미지를 Linux, Mac 및 Windows 같은 여러 플랫폼에서 실행할 수 있습니다.

## <a name="connect"></a>Connect

설치가 끝나면 Linux 컴퓨터상의 SQL Server 인스턴스에 연결 합니다. 다양한 도구와 드라이버를 가지고 로컬 또는 원격에 연결할 수 있습니다. 빠른 시작 자습서는 [sqlcmd](sql-server-linux-setup-tools.md) 명령줄 도구 사용법을 보여줍니다. 다른 도구는 다음과 같습니다.

| 도구 | 자습서 |
|-----|-----|
| Visual Studio Code (VS Code) | [VS Code로 Linux에 SQL Server 사용](sql-server-linux-develop-use-vscode.md) |
| SSMS(SQL Server Management Studio) | [Windows에서 SSMS를 사용 하 여 Linux에 SQL Server에 연결](sql-server-linux-develop-use-ssms.md) |
| SQL  Server  Data  Tools(SSDT) | [SSDT로 Linux에 SQL Server 사용](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>탐색

SQL Server 2017는 Linux를 포함한 모드 지원 플랫폼에서 동일한 기본 데이터베이스를 엔진을 가집니다. 많은 기존 기능과 능력이 Lunix에서 동일한 방법으로 작동합니다.  본 문서에서는 Linux 측면에서의 몇 가지 기능을 보여줍니다. 또한 Linux 에서 고유하게 요구되는 몇 가지 영역을 호출합니다.

당신이 SQL Server에 이미 익숙하다면, 일반적인 지침인 [릴리스 노트](sql-server-linux-release-notes.md)와 이번 릴리스에서 알려진 문제점들을 검토하세요. 그런 다음 [Linux에서 SQL Server의 새로운 기능](sql-server-linux-whats-new.md) 과 더불어 [전반적인 SQL Server 2017의 새로운 기능](../sql-server/what-s-new-in-sql-server-2017.md)을 살펴보세요.

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) SQL Server 엔지니어링 팀에 문의

- [DBA 스택 Exchange](https://dba.stackexchange.com/questions/tagged/sql-server): 데이터베이스 관리 질문 하기
- [스택 오버플로](http://stackoverflow.com/questions/tagged/sql-server): 개발 질문 하기
- [MSDN 포럼](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): 기술 관련 질문하기
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): 기능 요청 및 버그 보고하기
- [Reddit](https://www.reddit.com/r/SQLServer/): SQL Server 토론하기

