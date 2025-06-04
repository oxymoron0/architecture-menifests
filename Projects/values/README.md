# Helm Values Directory

This directory contains private Helm values files that should not be exposed publicly. These values files contain sensitive configuration and environment-specific settings for our applications.

## Directory Structure

```
values/
├── <application-name>/
│   ├── dev.yaml
│   └── prod.yaml
```

### Example
```
values/
├── argocd/
│   ├── dev.yaml
│   └── prod.yaml
└── nginx/
    ├── dev.yaml
    └── prod.yaml
```

## Usage Guidelines

### Value File Management
- Store environment-specific values in separate files (dev.yaml, prod.yaml)
- Keep sensitive information like passwords, tokens, and keys in these files
- Do not commit these files to public repositories
- Use appropriate access controls and encryption

### Security Best Practices
1. **Access Control**
   - Restrict access to this directory
   - Use appropriate file permissions
   - Implement proper authentication and authorization

2. **Value Management**
   - Use secrets management tools when possible
   - Encrypt sensitive values
   - Regularly rotate sensitive credentials

3. **Documentation**
   - Document the purpose of each value
   - Keep track of value changes
   - Maintain a changelog for significant updates

---

# Helm Values 디렉토리

이 디렉토리는 공개되지 않아야 하는 private Helm values 파일들을 포함하고 있습니다. 이 values 파일들은 애플리케이션의 민감한 구성과 환경별 설정을 포함하고 있습니다.

## 디렉토리 구조

```
values/
├── <애플리케이션-이름>/
│   ├── dev.yaml
│   └── prod.yaml
```

### 예시
```
values/
├── argocd/
│   ├── dev.yaml
│   └── prod.yaml
└── nginx/
    ├── dev.yaml
    └── prod.yaml
```

## 사용 가이드라인

### Values 파일 관리
- 환경별 values를 별도 파일로 관리 (dev.yaml, prod.yaml)
- 비밀번호, 토큰, 키 등 민감한 정보를 이 파일들에 보관
- 이 파일들을 공개 저장소에 커밋하지 않기
- 적절한 접근 제어와 암호화 사용

### 보안 모범 사례
1. **접근 제어**
   - 이 디렉토리에 대한 접근 제한
   - 적절한 파일 권한 설정
   - 적절한 인증 및 인가 구현

2. **Values 관리**
   - 가능한 경우 시크릿 관리 도구 사용
   - 민감한 값 암호화
   - 민감한 자격 증명 정기적 교체

3. **문서화**
   - 각 값의 용도 문서화
   - 값 변경 사항 추적
   - 중요 업데이트에 대한 변경 로그 유지
