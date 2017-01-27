Nginx Ingress Controller w/ LetsEncrypt + DNS for Google Container Engine
------

Within here lie manifests to set up an automated letsencrypt environment using
kubernetes and nginx.

the nginx ingresscontrller runs as a daemonset on every pod, which is placed into
a tcp load balancer


# installation

Step 1. Install the nginx IngressController, `kube-lego`, and the default http backend

in order, create the namespace, the configmaps, services, deployments, daemonsets
found in this folder.

Step 2. Configure a GCP TCP Load Balancer and Health Check for all instances
(/healthz) on the default-http-backend returns 200 OK - be sure to have a
firewall setting so that the load balancer can reach the cluster on port 80 and
443

Step 3. Create ingress resources in any namespace, i.e. `echoserver/`

Step 4. ??

Step 5. Enjoy your load balanced LetsEncrypt

### notes

this also works with non-letsencrypt certificates set up as normal kubernetes tls
secrets

http->https redirection is automatically handled

it may take a minute or two for the certificate to be provisioned and loaded into
the load balancer
