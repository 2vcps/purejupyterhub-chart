# Pure Storage Helm Chart for Jupyterhub on  K8s

Read more about installing JupyterHub on this site [Zero to JupyterHub](https://zero-to-jupyterhub.readthedocs.io/en/latest/)
### Prereqs
* You read the zero to jupyterhub page
* You have [helm](http://blog.2vcps.io/2018/03/27/getting-started-with-helm-for-k8s/) working.
* You went back and read [Setup JupyterHub](https://zero-to-jupyterhub.readthedocs.io/en/latest/setup-jupyterhub.html)

From your CLI run

```
openssl rand -hex 32
```
Then enter the output into a file config.yaml as show below
```
proxy:
  secretToken: "<OUTPUT-OF-`openssl rand -hex 32`>"
```
### Now to add the repo of PureJupyterHub
```
helm repo add purejupyterhub https://raw.githubusercontent.com/2vcps/purejupyterhub-chart/master/
helm repo update
```
This will add the repo and update the database of where to find our Chart.
This is for demo/test/dev purposes there are Oauth settings you must learn and setup before using this in production.
```
helm install purejupyterhub/jupyterhub \
    --version=v0.6 \
    --name=<YOUR-RELEASE-NAME> \
    --namespace=<YOUR-NAMESPACE> \
    -f config.yaml
```
--name is the release name and you can name it how you like.

--namespace is the namespace in k8s and you can remove this line if you want JupyterHub to run in the default namespace.

-f config.yaml is the file you created above. This contains the ssl hex for jupyter hub to use.

# Important to note
This chart defaults to using the Tensorflow Jupyter Notebook image because my sample code requires TF. Additionally, I have also defaulted the sqllite db persistent storage to use pure-block as the storageClass and for the home directories per user we are using NFS and the pure-file storageClass.

This means you must have the Pure Storage Kubernetes plugin installed with a FlashArray and a Flashblade configured in the pure.json file.