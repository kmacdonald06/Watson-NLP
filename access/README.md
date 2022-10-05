# Access Watson NLP Assets

This document describes how to access Watson NLP container images and other assets.

## Watson NLP Runtime and Pretrained Models

The Watson NLP Runtime and Pretrained Models are stored in Artifactory. To gain access you will need an [API key](https://na.artifactory.swg-devops.com/ui/admin/artifactory/user_profile).

### Docker
Run the following command to allow Docker to access the images.
```
docker login https://na.artifactory.swg-devops.com
```
Enter your Artifactory user profile and API key at the prompts.

### Kubernetes and OpenShift
To allow your Kubernetes or OpenShift cluster to access the container images, you can use the methods from the [Kubernetes documentation](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/) to store your credentials as a Kubernetes Secret. 

For example, use the following command to create a Secret named `regcred`.
```
kubectl create secret docker-registry regcred --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
```
Where:
- `<your-name>` is your Artifactory user profile
- `<you-pword>` is your Artifactory API key
- `<your-email>` is your email address

## Watson NLP Client SDKs
### Python
The Watson NLP Python Client SDK is stored in [PyPI](https://pypi.org/). Install it with the following command.
```
pip install -i https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple/ watson-nlp-runtime-client
```
Note that the above command is only for when the SDK is in the test area. Once it is pushed to the public PyPI you will use the command:
```
pip install watson-nlp-runtime-client
```
## Model Packager
This tool is used to package custom trained models into container images in the same way as are the Watson NLP pretrained models. It is stored on public [PyPI](https://pypi.org/).
```
pip install watson-embed-model-packager
```