Usage:

log in to your openshift:

    oc login <cluster URL> --username <username> --password <password>

create a namespace (project):

    oc new-project flask-morse-app

create a secret (for the docker registry, so you wont pull as anonymouse user):

    oc create secret docker-registry docker --docker-server=docker.io --docker-username=<username> --docker-password=<password> --docker-email=<email> -n flask-morse-app
	    
link the secret to your project:

    oc secrets link default docker --for=pull -n flask-morse-app

run helm to deploy the app:

    helm install flask-morse-app -f values.yaml .

to update run :

    helm upgrade flask-morse-app -f values.yaml .

to delete the app:

    helm uninstall flask-morse-app .
