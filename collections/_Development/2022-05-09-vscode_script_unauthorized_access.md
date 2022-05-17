---
layout: post
title: VSCode 터미널의 스크립트 에러 해결하기
subtitle: 이 시스템에서 스크립트를 실행할 수 없으므로 ~.ps1 파일을 로드할 수 없습니다.
tags: [Github Pages, VSCode, PowserShell, ExecutionPolicy]
image: /assets/images/2022-05-09-vscode_script_unauthorized_access/powershell.png
comments: true
---

Github page를 로컬에서 작성하기 위해 VSCode를 열어 터미널에서 yo code를 실행했더니 권한이 없다면서 스크립트의 실행이 되지 않았습니다. 다른 스크립트도 같은 증상입니다.

![VSCode 터미널 스크립트 오류](/../../assets/images/2022-05-09-vscode_script_unauthorized_access/script_execution_successed.png)

```bash
이 시스템에서 스크립트를 실행할 수 없으므로 C:\Users\user\AppData\Roaming\npm\yo.ps1 파일을 로드할 수 없습니다. 자세한 내용은 about_Execution_Policies(https://go.microsoft.com/fwlink/?LinkID=135170)를 참조하십시오.
```

이는 시스템의 설정에서 스크립트를 실행할 수 있는 권한이 없기 때문에 해당 명령을 수행할 수 없어 발생된 것입니다.

### 1. Windows PowerShell 관리자 권한으로 실행하기

시작 메뉴를 눌러 검색창에서 PowerShell을 찾은 후 관리자로 실행을 선택합니다.

![Windows PowerShell을 관리자 권한으로 실행](/../../assets/images/2022-05-09-vscode_script_unauthorized_access/run_powershell_withadministrator.png)


### 2. 현재 권한 확인하기

PowerShell에서 get-ExecutionPolicy 명령어로 현재 설정된 권한 상태를 확인합니다.
"Restricted"로 설정되어 있어서 실행이 안되었을 것입니다.

```bash
> get-ExecutionPolicy
```

### 3. 설정할 수 있는 권한 확인하기

PowerShell에서 get-help Set-ExecutionPolicy 명령어로 설정할 수 있는 권한들을 확인합니다.

```bash
> get-help Set-ExecutionPolicy
```

![get-help Set-ExecutionPolicy](/../../assets/images/2022-05-09-vscode_script_unauthorized_access/help_execution_policy.png)

- Restricted : default설정값으로, 스크립트 파일을 실행 불가
- AllSigned : 서명된 신뢰할 수 있는 스크립트 파일만 실행 가능
- RemoteSigned : 로컬에서 생성한 스크립트 및 서명된 신뢰할 수 있는 스크립트 파일 실행 가능
- Unrestricted : 모든 스크립트 실행 가능
- ByPass : 경고/차단 없이 모든 것을 실행 가능
- Undefined : 권한을 설정하지 않음

### 4. "RemoteSigned" 권한으로 설정하기

PowerShell에서 Set-ExecutionPolicy 명령어로 "RemoteSigned" 권한으로 설정합니다.

```bash
> Set-ExecutionPolicy RemoteSigned
```

![Set-ExecutionPolicy RemoteSigned](/../../assets/images/2022-05-09-vscode_script_unauthorized_access/set_execution_policy.png)


### 5. VSCode 스크립트 다시 실행하기

권한 설정이 되었다면 VSCode에서 다시 오류가 발생했던 스크립트를 실행하면 정상적으로 동작되는 것을 확인할 수 있습니다.

![VSCode 터미널 스크립트 정상 동작](/../../assets/images/2022-05-09-vscode_script_unauthorized_access/script_execution_successed.png)
