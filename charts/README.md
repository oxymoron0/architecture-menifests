# Charts Directory

This directory contains Helm charts for various applications in our infrastructure.

## Directory Structure

```
charts/
├── <application-name>/
│   ├── <version>/
│   │   ├── Chart.yaml
│   │   ├── values.yaml
│   │   └── templates/
│   └── <version>/
```

### Example
```
charts/
├── argocd/
│   ├── 1.0.0/
│   └── 1.0.2/
└── nginx/
    ├── 1.0.0/
    └── 1.0.2/
```

## Chart Management

### Adding New Charts
To add a new chart from a Helm repository:
```bash
helm pull <repo>/<app> --untar
```

### Version Management
- Each application has its own directory
- Different versions are stored in separate subdirectories
- Version numbers follow semantic versioning (MAJOR.MINOR.PATCH)

## Branching Strategy

### Chart Development
- All chart modifications must be done in the `Chart` branch
- Do not modify charts directly in the main branch
- Create feature branches from the `Chart` branch for specific changes

### Workflow
1. Switch to the `Chart` branch
2. Create a feature branch for your changes
3. Make your modifications
4. Submit a pull request to merge into the `Chart` branch
5. After review and approval, changes can be merged

---

# 차트 디렉토리

이 디렉토리는 인프라의 다양한 애플리케이션을 위한 Helm 차트를 포함하고 있습니다.

## 디렉토리 구조

```
charts/
├── <애플리케이션-이름>/
│   ├── <버전>/
│   │   ├── Chart.yaml
│   │   ├── values.yaml #Default Value
│   │   └── templates/
│   └── <버전>/
```

### 예시
```
charts/
├── argocd/
│   ├── 1.0.0/
│   └── 1.0.2/
└── nginx/
    ├── 1.0.0/
    └── 1.0.2/
```

## 차트 관리

### 새 차트 추가
Helm 저장소에서 새 차트를 추가하려면:
```bash
helm pull <repo>/<app> --untar
```

### 버전 관리
- 각 애플리케이션은 자체 디렉토리를 가집니다
- 다른 버전은 별도의 하위 디렉토리에 저장됩니다
- 버전 번호는 시맨틱 버저닝(MAJOR.MINOR.PATCH)을 따릅니다

## 브랜칭 전략

### 차트 개발
- 모든 차트 수정은 `Chart` 브랜치에서 진행해야 합니다
- 메인 브랜치에서 직접 차트를 수정하지 마세요
- 특정 변경사항을 위해 `Chart` 브랜치에서 기능 브랜치를 생성하세요

### 작업 흐름
1. `Chart` 브랜치로 전환
2. 변경사항을 위한 기능 브랜치 생성
3. 수정사항 적용
4. `Chart` 브랜치로 병합하기 위한 풀 리퀘스트 제출
5. 검토 및 승인 후 병합 가능
