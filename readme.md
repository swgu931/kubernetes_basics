# Kubernetes를 활용한 분산 시스템 구축 (21.05.10-21.05.14)

## Google instance 로 준비함
## 다음 

### Master node
```
docker run -it --rm \
--name gcp-sdk \
-h gcp-sdk \
-v /var/run:/var/run:rw \
-v ~/second/workspace-cloud/:/shared:rw \
swgu931/google-cloud-sdk-kubespray-terraform \
/bin/bash
```
```
#
gcloud auth login
glcoud config set project $PROJECT_ID
gcloud compute instances list
gcloud compute ssh $id@gce-k8s-master --zone=asia-northeast3-a
```
### worker1 node
```
docker run -it --rm \
--name gcp-sdk2 \
-h gcp-sdk2 \
-v /var/run:/var/run:rw \
-v ~/second/workspace-cloud/:/shared:rw \
swgu931/google-cloud-sdk-kubespray-terraform \
/bin/bash
```
```
#
gcloud auth login
glcoud config set project $PROJECT_ID
gcloud compute instances list
gcloud compute ssh $id@gce-k8s-master --zone=asia-northeast3-a
```
### worker2 node
```
docker run -it --rm \
--name gcp-sdk3 \
-h gcp-sdk3 \
-v /var/run:/var/run:rw \
-v ~/second/workspace-cloud/:/shared:rw \
swgu931/google-cloud-sdk-kubespray-terraform \
/bin/bash
```
```
#
gcloud auth login
glcoud config set project $PROJECT_ID
gcloud compute instances list
gcloud compute ssh $id@gce-k8s-master --zone=asia-northeast3-a
```

