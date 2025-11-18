# testapp-threepilars-UWL
I use this to demonstrate collecting metrics, logs and traces from a testapp in Openshift.
Always firing alerts for both metrics and logs are also deployed

1. Ensure the following operators are installed on your cluster:
     Red Hat cluster observability operator
     Red Hat Build of OpenTelemetry
     Red Hat Openshift logging
     Red Hat Loki operator
     Red Hat Tempo operator
     
2. Ensure User workload Monitoring is enabled

3. Run logging commands

```
./Logging/01_commands.sh
```

4. deploy the contents of this repo 

```
oc apply -Rf . 
```

5. scale the testapp down and back up, inorder to deploy the OTEL sidecar

```
oc scale --replicas=0 deployment/threepilar-example-deployment
oc scale --replicas=1 deployment/threepilar-example-deployment      
```
