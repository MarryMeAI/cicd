# ECR Create Action

이 액션은 Amazon ECR 레포지토리를 생성하거나 업데이트합니다. 레포지토리가 존재하지 않으면 생성하고, 존재하면 Immutable 태그 설정만 적용합니다.

## 기능

- ECR 레포지토리 존재 여부 확인
- 새 레포지토리 생성 (필요한 경우)
- Immutable 태그 설정 적용
- AWS 자격증명이 액션에 내장되어 있어 별도 설정 불필요

## 입력 파라미터

- `ecr_repository`: (필수) ECR 레포지토리 이름

## 사용 예시

```yaml
- name: configure aws credentials
  uses: aws-actions/configure-aws-credentials@v1
  with:
    role-to-assume: ${{ env.AWS_ROLE }}
    role-session-name: ${{ env.APP_NAME }}-${{ env.PHASE }}
    aws-region: ap-northeast-2
- name: Create or Update ECR Repository
  uses: MarryMeAI/cicd/ecr-create@main
  with:
    ecr_repository: my-app
```
