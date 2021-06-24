# Kubernetes container 생성시에 private-registry-howto-secret

- ref: https://blog.uniqbuild.co.kr/?p=724

[준비]

1) authentication을 위한 secret 생성

$ kubectl create secret docker-registry my-secret --docker-server=DOCKER_REGISTRY_SERVER --docker-username=DOCKER_USER
--docker-password=DOCKER_PASSWORD --docker-email=DOCKER_EMAIL

```
$ kubectl create secret docker-registry mycartcred --docker-server=cart.lge.com --docker-username='user.name' --docker-password='1234567890' --docker-email="user.email@lge.com"
```

2) 확인
```
$ kubectl get secret mycartcred --output=yaml
```
   출력 결과에서 .dockerconfigjosn이라는 내용은 실제 docker registry 접속정보를 나타냅니다.
   
```
kubectl get secret mycartcred --output="jsonpath={.data.\.dockerconfigjson}" | base64 -d
```


3) 쿠버네티스에서 deploy할 yaml 작성
```
apiVersion: v1
kind: Pod
metadata:
  name: private-reg
spec:
  containers:
  - name: private-reg-container-nginx
    image: cart.lge.com/cloud-robotics/nginx-custom:0.1.0
  imagePullSecrets:
  - name: mycartcred
```

4) 이미지를 사내 cart.lge.com 으로 부터 다운받아서 사용합니다.

