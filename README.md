# testapp-threepilars-UWL
I use this to demonstrate collecting metrics, logs and traces from a testapp in Openshift

1. Ensure the following operators are installed on your cluster:
     Red Hat cluster observability operator
     Red Hat Build of OpenTelemetry
     Red Hat Openshift logging
     Red Hat Loki operator
     Red Hat Tempo operator
     
2. Ensure User workload Monitoring is enabled

3. oc apply -Rf . 
4. ./Logging/01_commands.sh
5. 

oc scale --replicas=0 deployment/threepilar-example-deployment
oc scale --replicas=1 deployment/threepilar-example-deployment 
     
     
     
     
