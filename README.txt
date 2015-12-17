Create a Dockerfile

FROM registry.access.redhat.com/jboss-eap/eap-openshift:6.4

EXPOSE 8080 8888

$JBOSS_HOME/standalone/deployments/ROOT.war
COPY rhc-ose-license.txt $JBOSS_HOME/

Create the Licence document

RHC Bootcamp Middleware License 

This software is meets the standard set forth by the company and can be used within all deployment environments

Run commands on master

oadm policy add0role0to0user system:image-builder <USER> -n openshift
oc login
token=`oc whoami -t`
docker login -u <your user> -e ankledeep@water.com -p $token <your ip>:5000
docker tag eaplicense 172.30.200.172:5000/openshift/eaplicense
docker push 172.30.200.172:5000/openshift/eaplicense
