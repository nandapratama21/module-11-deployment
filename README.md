## MODULE 11

## Minikube

1. Compare the application logs before and after you exposed it as a Service.
Answer: Yes, there are differences because when the service exposed. When the service is not exposed, the application logs primarily contain information about the application's internal operations. However, once the service is exposed, it starts to receive requests.  


2. Notice that there are two versions of `kubectl get` invocation during this tutorial section.
13
The first does not have any option, while the latter has `-n` option with value set to
`kube-system`.
What is the purpose of the `-n` option and why did the output not list the pods/services that you
explicitly created?
Answer: The -n option in kubectl get is used to specify the namespace in which to look for resources. Namespaces are a way to divide cluster resources between multiple users or applications. If we don't specify a namespace, kubectl commands operate in the default namespace.


## Reflection on Rolling Update & Kubernetes Manifest File

1. What is the difference between Rolling Update and Recreate deployment strategy?
Answer: In rolling update, when we update a deployment, the Deployment Controller gradually replaces old Pods with new ones. The benefit of this strategy is that the application remains available during the update process, and the update is rolled out progressively to ensure that not all instances are updated at the same time.

In Recreate deployment, all existing Pods are killed before new ones are created. The downside of this approach is that it causes downtime during the update process as the application becomes briefly unavailable. However, it can be useful in scenarios where our application cannot run with both old and new versions of the Pods at the same time.


2. Try deploying the Spring Petclinic REST using Recreate deployment strategy and document
your attempt.
Answer: 

At first, We will recreate springboot-petclinic-rest version 3.0.2 and edit the replicaset

![Screenshot 1](screenshot1.png)

To verify the success of the changes, we can use command like this

![Screenshot 2](screenshot2.png)

And then, we delete the pod

![Screenshot 3](screenshot3.png)

We can see that the new pods are replacing the old pods before and then the deploy is successful.

![Screenshot 4](screenshot4.png)


3. Prepare different manifest files for executing Recreate deployment strategy.
Answer: We will named the file "deployment2.yaml" and change a part of line to this

```yaml
selector:
        matchLabels:
        app: spring-petclinic-rest
    strategy:
        type: Recreate
```

4. What do you think are the benefits of using Kubernetes manifest files? Recall your experience
in deploying the app manually and compare it to your experience when deploying the same app
by applying the manifest files (i.e., invoking `kubectl apply -f` command) to the cluste
Answer: I think the benefits of using Kubernetes manifest files are automation. Manifest files allows to automate the deployment process, reducing the risk of human error and making the process more repeatable and reliable. Using manual deployment can be tedious, especially for complex applications with many components. 




