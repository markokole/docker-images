# Prepare local Terraform environment for work with Azure

Uncomment the last 4 lines in Dockerfile and rebuild if Azure cli is needed - keep in mind the image grows for 1 GB.

## Build the image

```bash
docker build --file Dockerfile --tag=markokole/terraformer-azure:1.0.3 --build-arg TERRAFORM_VERSION=1.0.3 .
```

## Test image

### Run container

```bash
docker run -itd --name terraformer-azure markokole/terraformer-azure:1.0.3
```

Prepare *azure.env* file if you wish to connect to azure with argument **--env-file**.

### Step into container

```bash
docker exec -it terraformer-azure /bin/sh
```

## Push image to Docker Hub

```bash
docker push markokole/terraformer-azure:1.0.3
```
