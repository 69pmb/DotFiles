# Openshift

- List pods with version:  
`oc get pods -o go-template --template '{{range .items}}{{.metadata.name}} - {{.metadata.labels.version}}{{"\n"}}{{end}}'`
- Delete all deployments:  
`oc get deployments -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete deployments`
- Delete all services:  
`oc get services -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete services`
- Delete all routes:  
`oc get routes -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete routes`
- Delete configmap:  
`oc get configmaps -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete configmaps`
- Delete secrets:  
`oc get secrets -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete secrets`
- Delete service account:  
`oc get serviceaccount -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete serviceaccount`
- Delete storage:  
`oc get pvc -o jsonpath='{range .items[*].metadata}{.name}{"\n"}{end}' | xargs oc delete pvc`
