# AWS CLI

## Get ECR image versions for `myorg/myimage` sorted by creation date

Outputs a JSON string array. Useful for creating a Jenkins UI to pick a release version.

```
aws ecr describe-images --repository-name myorg/myimage \
  --profile=stg --region=us-west-2 \
  --query 'reverse(sort_by(imageDetails,& imagePushedAt))' | \
  jq 'map(.imageTags) | add'
```

```json
[
  "0.15.5",
  "0.15.4-canary-813d69f",
  "0.15.3",
  "0.15.2-canary-4c3dbfe",
  "0.15.2",
  "0.15.1",
  "0.15.0"
 ]
```
