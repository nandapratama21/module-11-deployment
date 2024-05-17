## MODULE 11

1. Compare the application logs before and after you exposed it as a Service.
Answer: Yes, there are differences because when the service exposed. When the service is not exposed, the application logs primarily contain information about the application's internal operations. However, once the service is exposed, it starts to receive requests.  


2. Notice that there are two versions of `kubectl get` invocation during this tutorial section.
13
The first does not have any option, while the latter has `-n` option with value set to
`kube-system`.
What is the purpose of the `-n` option and why did the output not list the pods/services that you
explicitly created?
Answer: The -n option in kubectl get is used to specify the namespace in which to look for resources. Namespaces are a way to divide cluster resources between multiple users or applications. If we don't specify a namespace, kubectl commands operate in the default namespace.


