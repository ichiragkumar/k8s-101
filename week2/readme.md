// To run the nginx container on port 3000 and expose it to the host machine
 docker run -p 3000:80 nginx  


// ceate kubernetes cluster

kind create cluster --name kind-cluster
kind create cluster --name sunday

//  how to create a pod
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl run moongo-pod --image=nginx --port=80
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl run nginx-pod --image=nginx --port=80


 // how to delete pods 

 ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl delete pod moongo-pod


 // apply Deploymenent manifest


 // check deployment explanation
 kubectl explain deployment


// get al deployments
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl get deployment    


// now you can get pods , from this deployment
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl get pods


/// and if you delete any pods from , deployment , Deployment will make sure, 
all pods are up


// delete a pods
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl delete pod nginx-pod

// check deployment
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl get deployment

// check the pods
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl get pods



// get all replicasets
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl get replicaset



// delete the deployemnt 
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl delete deployment nginx-deployment
NOTE:
    1. Deployment creaets the replica sets
    2. Replica sets creates the pods

    and if you delete the deployment, 
    replica sets will be deleted as well
    and pods will be deleted as well



// creting a replicaset, write a .yml file [ manifest ] and apply it
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl apply -f replicaset.yml
replicaset.apps/nginx-replicaset created
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ kubectl get rs                 
NAME               DESIRED   CURRENT   READY   AGE
nginx-replicaset   3         3         2       6s
ichiragkumar:~/Desktop/Projects/k8s/k8s-101/week2$ 



it looks like , same as deployment, replica set creates the pods
but replica set is not a deployment
"if you delete the replica set, pods will not be deleted"

It deletes:

The Deployment

The associated ReplicaSet

All Pods (since RS owns the Pods)





