﻿---
lab:
    title: 'Azure 데이터 플랫폼 보호'
    module: '모듈 8: Azure 데이터 플랫폼 보호'
---

# DP 200 - 데이터 플랫폼 솔루션 구현
# 랩 8 - Azure 데이터 플랫폼 보안

**예상 시간**: 75분

**필수 구성 요소**: 이 랩에 대한 사례 연구는 이미 읽은 것으로 가정합니다. 모듈 1~7의 콘텐츠와 랩을 완료했다고 가정합니다.

**랩 파일**: 이 랩의 파일은 _Allfiles\Labfiles\Starter\DP-200.8_ 폴더에 있습니다.

## 랩 개요

학생들은 심층적인 방어를 위해 사용할 수 있는 다양한 보안 방식을 설명하고 문서로 작성할 수 있게 됩니다. 이 과정에는 학생이 지금까지 설정된 보안을 문서화하는 작업이 포함됩니다. 또한 학생들은 AdventureWorks에 존재할 수 있는 보안의 틈새를 식별할 수 있습니다.

## 랩 목표
  
이 랩을 완료하면 다음과 같은 것들을 수행할 수 있습니다.

1. 보안 설명
1. 주요 보안 구성 요소 설명
1. 스토리지 계정 및 Data Lake Storage 보안
1. 데이터 저장소 보안
1. 스트리밍 데이터 보안

## 시나리오
  
귀하께서는 AdventureWorks의 수석 데이터 엔지니어로서 데이터 재산의 보안을 보장할 책임이 있습니다. 현재 인프라에 대한 보안 검사를 수행하여 필요한 곳에 보안을 잘 배치했는지 확인합니다. 지금까지 만든 모든 서비스와 데이터를 전체적으로 확인하고 보안 구성에 있을 수 있는 빈틈을 식별해야 합니다. 

또한 SQL Database DeptDatabasesxx의 보안을 강화하라는 요청을 받았으며 데이터베이스에 대한 액세스를 모니터링할 수 있도록 데이터베이스에 대한 감사를 설정하라는 요청을 받았습니다. 그뿐만 아니라 이벤트 허브에 대한 관리 권한이 충분히 제한되지 않은 것을 알게 되었고 이 권한을 제거하고 싶습니다.

이 랩을 마치면 다음 작업을 수행할 수 있습니다.

1. 설명한 보안
1. 설명된 주요 보안 구성 요소
1. 보안된 스토리지 계정 및 Data Lake Storage
1. 보안된 데이터 저장소
1. 보안된 스트리밍 데이터

> **중요**: 이 랩을 진행하면서 프로비전 또는 구성 작업에서 발생한 모든 이슈를 기록하고 _\Labfiles\DP-200-Issues-Doc.docx_에 있는 문서의 테이블에 로그합니다. 랩 번호를 문서화하고, 기술을 기록하고, 문제와 해결 방법을 설명합니다. 이후 모듈에서 다시 참조할 수 있도록 이 문서를 저장합니다.

## 연습 1: 보안 소개

예상 시간: 15분

그룹 연습
  
이 연습의 주요 작업은 다음과 같습니다.

1. 계층적 접근 방식으로서의 보안.

1. 강사는 그룹과 결과에 대해 논의합니다.

### 작업 1: 계층적 접근 방식으로서의 보안.

1. 랩 가상 머신에서 **Microsoft Word**를 시작하고 **Allfiles\Labfiles\Starter\DP-200.8** 폴더에서 **DP-200-Lab08-Ex01.docx** 파일을 엽니다.

1. 지금까지의 과정 콘텐츠, 사례 연구 및 시나리오에서 그룹별로 **10분** 동안 랩에서 AdventureWorks를 보호하는 데 영향을 준 보안 계층을 식별합니다. 세 가지 예제를 찾습니다.

### 작업 2: 강사와 결과에 대해 토론합니다.

1. 강사는 결과를 논의하기 위해 그룹을 멈춥니다.

> **결과**: 이 연습을 완료한 후 Adventureworks에서 보안을 구현한 방법과 영향을 준 보안 계층에 대한 세 가지 이상의 예가 포함된 Microsoft Word 문서를 만들었습니다.

## 연습 2: 주요 보안 구성 요소
  
예상 시간: 10분

개인 연습
  
이 연습의 주요 작업은 다음과 같습니다.

1. 데이터 및 스토리지 보안 위생 평가

### 작업 1: 데이터 및 저장소 보안 위생 평가.

1. Azure Portal 탭에서 **보안 센터**를 클릭합니다.

    ![Azure Portal의 Security Center](Linked_Image_Files/M08-E01-T01-img01.png)

1. Security Center에서 - 개요 화면에서 **리소스 보안 위생** 아래에 있는 데이터 및 스토리지를 클릭합니다.

    ![Security Center - Azure Portal의 데이터 스토리지](Linked_Image_Files/M08-E01-T01-img02.png)

1. 주의가 필요한 상위 2개의 주요 데이터 및 스토리지 구성 요소를 식별합니다.

    1. __답변은 다를 수 있습니다.____
    1. __답변은 다를 수 있습니다.____

> **결과**: 이 연습을 완료한 후 Azure 구독에 있는 모든 데이터 및 스토리지 보안 취약점을 식별할 수 있는 곳을 배웠습니다.

## 연습 3: 저장소 계정 및 Data Lake Storage 보안
  
예상 시간: 15분

개별 연습
  
이 연습의 주요 작업은 다음과 같습니다.

1. Azure Blob용으로 적절한 보안 접근 방식 결정

1. 강사와 결과에 대해 토론합니다.

### 작업 1: Azure Blob용으로 적절한 보안 접근 방식 결정

1. 사내 웹 개발자가 타사 웹 디자인 회사에게 awsastudxx 스토리지 계정에 있는 웹 이미지에 대한 액세스를 제공하는 것을 도와달라고 요청했습니다. AdventureWorks의 수석 데이터 엔지니어로서 올바른 실사를 적용하면서 이러한 작업이 가능하게 하기 위해 취해야 할 조치는 무엇입니까?

1. 랩 가상 머신에서 **Microsoft Word**를 시작하고 **Allfiles\Labfiles\Starter\DP-200.8** 폴더에서 **DP-200-Lab08-Ex03.docx** 파일을 엽니다.

### 작업 2: 강사와 결과에 대해 토론합니다.

1. 강사는 결과를 논의하기 위해 그룹을 마무리합니다.

> **결과**: 이 연습을 완료한 후 타사 웹 개발 회사에게 Blob 스토리지 계정에 대한 보안 액세스를 제공하기 위해 수행할 단계가 포함된 Microsoft Word 문서를 만들었습니다.

## 연습 4: 데이터 저장소 보안
  
예상 시간: 15분

개인 연습
  
이 연습의 주요 작업은 다음과 같습니다.

1. 감사 활성화

1. 데이터베이스 쿼리

1. 감사 로그 보기

### 작업 1: 감사 활성화

1. Azure Portal의 블레이드에서 **리소스 그룹**을 클릭하고 **awrgstudxx**, **awdlsstudxx**를 차례로 클릭합니다. 여기서 **xx**는 귀하의 이니셜입니다.

1. Azure Portal의 블레이드에서 리소스 그룹을 클릭하고 awrgstudxx, **AdventureWorksLT**를 차례로 클릭합니다.

1. deptdatabasesxx (sqlservicexx/AdventureWorksLT) 화면에서 **감사** 블레이드를 클릭합니다.

1. **감사** 아래에서 **켜기** 버튼을 클릭합니다.

1. **스토리지** 옆에 있는 확인란을 선택합니다.

1. **스토리지 세부 정보 - 구성**을 클릭합니다.

1. **스토리지 설정** 화면에서 **구독 - 스토리지 구독 변경**을 클릭한 다음 구독을 클릭합니다.

1. **스토리지 설정** 화면에서 **스토리지 설정 - 필수 설정 구성**을 클릭합니다. **스토리지 계정 선택** 화면에서 **awsastudxx**를 클릭합니다.

1. **보존일** 텍스트 상자에서 **90**을 입력한 다음 **확인**을 클릭합니다.

    ![Azure Portal에서 감사 구성](Linked_Image_Files/M08-E04-T01-img01.png)

1. **저장**을 클릭합니다.

### 작업 2: 데이터베이스 쿼리

1. Windows 데스크톱에서 **시작**을 클릭하고 **"SQL Server"**를 입력한 다음 **Microsoft SQL Server Management Studio 17**을 클릭합니다.

1. **서버에 연결** 대화 상자에서 다음 세부 사항을 기입합니다.
    - 서버 이름: **sqlservicexx.database.windows.net**
    - 인증: **SQL Server 인증**
    - 사용자 이름: **xxsqladmin**
    - 암호: **P@ssw0r**

1. **서버에 연결** 대화 상자에서 **연결**을 클릭합니다. 

> **참고**: 암호가 올바르지 않으면 오류 메시지가 반환됩니다. 올바른 암호 **P@Ssw0rd**를 입력합니다.

1. **Pa55w.rd**의 올바른 암호를 입력합니다.

1. **SQL Server Management Studio**의 Object Explorer에서 **AdventureWorksLT**, **테이블**을 차례로 펼칩니다.

1. [SalesLT].[Customers]를 마우스 오른쪽 버튼으로 클릭하고 **상위 1000개 행 선택**을 클릭합니다.

### 작업 2: 감사 로그 보기

1. Azure Portal로 돌아갑니다. AdventureWorksLT (sqlservicexx/AdventureWorksLT) - 감사 화면에서 **감사 로그 보기**를 클릭합니다.

1. **감사 레코드** 로그 파일에서 **실패한 인증** 레코드를 확인합니다. **감사 레코드** 화면을 닫습니다.

    ![Azure Portal에서 감사 레코드 보기](Linked_Image_Files/M08-E04-T01-img02.png)

> **결과**: 이 연습을 통해 데이터베이스 감사를 사용하도록 설정하고 감사가 작동하는 것을 확인했습니다.

## 연습 5: 스트리밍 데이터 보안
  
예상 시간: 15분

개별 연습
  
이 연습의 주요 작업은 다음과 같습니다.

1. 이벤트 허브 사용 권한 변경

### 작업 1: 이벤트 허브 사용 권한 변경

1. Azure Portal의 블레이드에서 **리소스 그룹**을 클릭하고 **awrgstudxx**, **xx-phoneanalysis-ehn**를 차례로 클릭합니다. 여기서 **xx**는 이니셜입니다.

1. Azure Portal의 **xx-phoneanalysis-ehn**에서 **xx**는 귀하의 이니셜입니다. 창 아래쪽으로 스크롤하고 **xx-phoneanalysis-eh** 이벤트 허브를 클릭합니다.

1. 이벤트 허브에 대한 액세스 권한을 부여하려면 **공유 액세스 정책**을 클릭합니다.

1. **xx-phoneanalysis-eh - 공유 액세스 정책** 화면 아래에서 **phoneanalysis-eh-sap**을 클릭합니다.

1. **관리** 사용 권한 옆에 있는 체크 박스를 클릭하여 제거하고 **저장**을 클릭합니다.

1. Azure Portal의 블레이드에서 **홈**을 클릭합니다.

> **결과**: 이 연습을 통해 이벤트 허브 공유 액세스 정책의 보안을 수정했습니다.