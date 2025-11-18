# testapp-threepilars-UWL
I use this to demonstrate collecting metrics, logs and traces in Openshift.
A testapp is deployed with always firing alerts for both metrics and logs. 

Demo App: https://github.com/coffeegoesincodecomesout/testapp-ThreePilars

1. Ensure the following operators are installed on your cluster:
     Red Hat cluster observability operator, 
     Red Hat Build of OpenTelemetry, 
     Red Hat Openshift logging, 
     Red Hat Loki operator, 
     Red Hat Tempo operator
     
2. Ensure User workload Monitoring is enabled

3. Run logging commands

```
./Logging/01_commands.sh
```

4. Deploy the contents of this repo 

```
oc apply -Rf . 
```

5. scale the testapp down and back up, inorder to deploy the OTEL sidecar

```
oc scale --replicas=0 deployment/threepilar-example-deployment
oc scale --replicas=1 deployment/threepilar-example-deployment      
```
