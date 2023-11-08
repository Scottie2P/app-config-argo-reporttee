# Deployment

## Install
```
docker build -t datawow/kiyo-prime-text:api-test -f DockerfileAPI .
docker build -t datawow/kiyo-prime-text:predictor-test -f DockerfilePredictor .
docker build -t datawow/kiyo-prime-text:worker-test -f DockerfileWorker .

docker push datawow/kiyo-prime-text:api-test
docker push datawow/kiyo-prime-text:predictor-test
docker push datawow/kiyo-prime-text:worker-test


helm upgrade -i kiyo-prime-text deployment \
  -n kiyo-prime \
  -f deployment/value-override/staging.yaml \
  --set image.sha=test --debug --dry-run > debug.yaml


helm upgrade -i kiyo-prime-text deployment \
  -n kiyo-prime \
  -f deployment/value-override/staging.yaml \
  --set image.sha=test
```

## Uninstall
```
helm -n kiyo-prime delete kiyo-prime-text
```
