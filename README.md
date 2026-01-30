# testapp-threepilars-UWL
I use this to demonstrate collecting metrics, logs and traces in Openshift.
A testapp is deployed with always firing alerts for both metrics and logs. 

Demo App: https://github.com/coffeegoesincodecomesout/testapp-ThreePilars

1. Ensure the following operators are installed on your cluster:
     Openshift Data Foundation,
     Red Hat cluster observability operator, 
     Red Hat Build of OpenTelemetry, 
     Red Hat Openshift logging, 
     Red Hat Loki operator, 
     Red Hat Tempo operator
     
2. Ensure User workload Monitoring is enabled

3. Deploy the test app:

```
oc apply -Rf App/
```

4. Run Logging commands: 

```
./Logging/01_commands.sh
```

5. Deploy the LoggingStack

```
oc apply -Rf Logging/
```

6. Create bucket secret

```
./Logging/03_bucketsecret.sh
```

7. Deploy OpenTelemetry

```
oc apply -Rf Opentelemetry/ 
```

8. Deploy Tempo

```
oc apply -Rf Tempo/
```

9. Create bucket secret

```
./Tempo/02_bucketsecret.sh
```

10 . scale the testapp down and back up, inorder to deploy the OTEL sidecar

```
oc scale -n ns1-uwl --replicas=0 deployment/threepilar-uwl-example-app
oc scale -n ns1-uwl --replicas=1 deployment/threepilar-uwl-example-app
```
