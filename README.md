# Pure Storage Helm Chart for Jupyterhub on  K8s

Read more about installing JupyterHub on this site [Zero to JupyterHub](https://zero-to-jupyterhub.readthedocs.io/en/latest/)
### Prereqs
* You read the zero to jupyterhub page
* You have [helm](https://blog.2vcps.io) working.
* You went back and read [Setup JupyterHub](https://zero-to-jupyterhub.readthedocs.io/en/latest/setup-jupyterhub.html)

```
openssl rand -hex 32
```
Then enter the output into a file config.yaml as show below
```
proxy:
  secretToken: "<OUTPUT-OF-`openssl rand -hex 32`>"
```
