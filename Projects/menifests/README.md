# Kubernetes Manifests

This directory contains Kubernetes manifests for various applications and services in our infrastructure. These manifests are managed through GitOps and deployed using Argo CD.

## Directory Structure

```
manifests/
├── <application-name>/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── configmap.yaml
```

## Manifest Management

### Base Configuration
- Contains the base Kubernetes manifests for each application
- Includes common configurations like deployments, services, and configmaps
- Serves as the foundation for environment-specific overlays

### Overlays
- Environment-specific configurations (development, staging, production)
- Customizes base configurations for different environments
- Includes environment-specific values and settings

## Best Practices

1. **Resource Organization**
   - Group related resources in the same directory
   - Use meaningful names for resources
   - Follow Kubernetes naming conventions

2. **Configuration Management**
   - Use ConfigMaps and Secrets for configuration
   - Avoid hardcoding values in manifests
   - Document any special configurations

3. **Version Control**
   - Keep manifests in version control
   - Use meaningful commit messages
   - Review changes before merging

---

# Kubernetes 매니페스트

이 디렉토리는 인프라의 다양한 애플리케이션과 서비스를 위한 Kubernetes 매니페스트를 포함하고 있습니다. 이 매니페스트들은 GitOps를 통해 관리되며 Argo CD를 사용하여 배포됩니다.

## 디렉토리 구조

```
manifests/
├── <애플리케이션-이름>/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── configmap.yaml
```

## 매니페스트 관리

### 기본 구성
- 각 애플리케이션의 기본 Kubernetes 매니페스트를 포함
- deployment, service, configmap 등 공통 구성 포함
- 환경별 오버레이의 기반이 됨

### 오버레이
- 환경별 구성 (개발, 스테이징, 프로덕션)
- 기본 구성을 각 환경에 맞게 커스터마이징
- 환경별 값과 설정 포함

## 모범 사례

1. **리소스 구성**
   - 관련 리소스를 같은 디렉토리에 그룹화
   - 리소스에 의미 있는 이름 사용
   - Kubernetes 명명 규칙 준수

2. **구성 관리**
   - ConfigMap과 Secret을 사용하여 구성
   - 매니페스트에 값을 하드코딩하지 않기
   - 특별한 구성에 대한 문서화