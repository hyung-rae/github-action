# Github Actions

- [Github Actions](#github-actions)
  - [github actions?](#github-actions-1)
  - [Workflows](#workflows)
    - [Using workflows](#using-workflows)
    - [Reusing workflows](#reusing-workflows)
  - [Events](#events)
    - [Events that trigger workflows](#events-that-trigger-workflows)
  - [Jobs](#jobs)
    - [Using jobs](#using-jobs)
  - [Actions](#actions)
  - [Runners](#runners)

## github actions?
- 레포지토리에 대한 모든 풀 요청을 빌드 및 테스트하거나 병합된 풀 요청을 프로덕션에 배포하는 워크플로 생성
- 이 외에 레포지토리에서 다른 이벤트가 발생할 때 워크플로를 실행가능
- 워크플로를 실행할 수 있는 가상머신([runners](#runners)) 제공 또는 자체적으로 환경을 구성 호스팅 가능
- YAML 구문을 사용하여 워크플로를 정의
- Workflow file 
<br>

    ```YAML
    # Workflows name
    name: learn-github-actions

    # 워크플로 실행의 이름으로, 레포지토리 "Actions" 탭에 있는 워크플로 실행 목록에 표시.
    run-name: ${{ github.actor }} is learning GitHub Actions

    # Trigger Event
    on: [push]

    # (...실행될 jobs...)
    ```

## Workflows
- 레포지토리의 .github/workflows 디렉터리에 정의되어 있으며, 여러 워크플로가 있을 수 있으며 각 워크플로는 서로 다른 작업을 수행할 수 있음 
- 워크플로에는 순차적 또는 병렬로 실행될 수 있는 작업이 하나 이상 포함 되어야 함
- 이벤트에 의해 트리거될 때 실행되거나 수동으로 또는 정의된 일정에 따라 실행됨
- **다른 워크플로 내에서 워크플로를 참조 가능**

### Using workflows

### Reusing workflows

## Events
- 워크플로 실행을 트리거하는 활동

### Events that trigger workflows

## Jobs
- 같은 runner 에서 실행되는 워크플로 내의 각각의 단계
- 기본적으로 작업은 종속성이 없으며 서로 병렬로 실행, 작업이 다른 작업에 종속되면 종속 작업이 완료될 때까지 기다렸다가 실행
- **동일한 runner에서 실행되므로 데이터를 공유가능**

### Using jobs

## Actions
- 자주 사용되는 작업들을 제공해주는 애플리케이션
- [GitHub Marketplace](https://github.com/marketplace?type=actions) 에서 탐색 가능
  
```YAML
steps:
    - uses: actions/javascript-action@v1
```

## Runners
- 워크플로가 트리거될 때 워크플로를 실행하는 서버
- GitHub는 워크플로를 실행하기 위한 Ubuntu Linux, Microsoft Windows 및 macOS 실행기를 제공
- 자체 실행기를 호스팅할 수 있음
