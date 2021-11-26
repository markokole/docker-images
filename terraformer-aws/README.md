# Local container in Windows for work with Amazon Web Services

The base image for this container is ubuntu. Terraform and aws cli are installed.

The container has volume */local-git* which can be used to map local folder to that folder in the container. The idea is to execute the code from the container while writing the code in the IDE of your choice in Windows.

My choice of ID for Infrastructure-as-code is Visual Studio Code in which I load the git repository, open a terminal window pointing to the repository.

First, step into Powershell, or better yet, open a terminal window in Visual Studio Code.

Make sure to use a Terraform version as a tag!

```bash
$env:TERRAFORM_VERSION = "1.0.11"
```

```bash
docker build --file Dockerfile --tag=markokole/terraformer:$env:TERRAFORM_VERSION --build-arg TERRAFORM_VERSION=$env:TERRAFORM_VERSION .
```

## Push the image to the dockerhub

 **Make sure no sensitive information is in the image!**

```bash
docker push markokole/terraformer:$env:TERRAFORM_VERSION
```

## Test the image locally

Run the container with the newly created image.

The following is not needed unless you plan to communicate with AWS:

Rename the aws/credentials.template to /aws/credentials and add key and secret. Change the region accordingly.

If only testing the container, drop the argument *--env-file*. Or if you plan to connect to AWS in some other way (AWS SSO for example).

For mapping a Docker volume (in this case local-git) to a folder in Windows - the folder in repository where Terraform files are gathered - add the following switch to the below command *--volume $PWD/terraform:/local-git*.

```bash
docker run -itd --name terraformer --env-file "aws/credentials" markokole/terraformer:$env:TERRAFORM_VERSION
```

Step into the container.

```bash
docker exec -it terraformer /bin/sh
```

The image was pushed to the docker hub and can also be retrieved using the following command:

```bash
docker pull markokole/terraformer:<TAG>
```
