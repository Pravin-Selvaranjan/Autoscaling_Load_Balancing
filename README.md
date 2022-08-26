# Autoscaling and Load Balancing 

![load balancer](https://user-images.githubusercontent.com/110179866/186463396-855eb422-cf25-46e5-82d1-29cf28a05e7a.jpeg)


### Autoscaling automatically adjusts the amount of computational resources based on the server load

### Load Balancing distributes traffic beetween ec2 instances so that no one instance gets overwhelmed

## Application Load Balancer
An Application Load Balancer makes routing decisions at the application layer (HTTP/HTTPS), supports path-based routing, and can route requests to one or more ports on each container instance in your cluster. Application Load Balancers support dynamic host port mapping. For example, if your task's container definition specifies port 80 for an NGINX container port, and port 0 for the host port, then the host port is dynamically chosen from the ephemeral port range of the container instance (such as 32768 to 61000 on the latest Amazon ECS-optimized AMI). 

## Network Load Balancer

A Network Load Balancer makes routing decisions at the transport layer (TCP/SSL). It can handle millions of requests per second. After the load balancer receives a connection, it selects a target from the target group for the default rule using a flow hash routing algorithm. It attempts to open a TCP connection to the selected target on the port specified in the listener configuration.


## Auto scaling policies 
- Simple - Simple scaling relies on a metric as a basis for scaling. For example, you can set a CloudWatch alarm to have a CPU Utilization threshold of 80%, and then set the scaling policy to add 20% more capacity to your Auto Scaling group by launching new instances. Accordingly, you can also set a CloudWatch alarm to have a CPU utilization threshold of 30%. When the threshold is met, the Auto Scaling group will remove 20% of its capacity by terminating EC2 instances. 


- Step - Step Scaling further improves the features of simple scaling. Step scaling applies “step adjustments” which means you can set multiple actions to vary the scaling depending on the size of the alarm breach. 


- Target tracking - Target tracking policy lets you specify a scaling metric and metric value that your auto scaling group should maintain at all times. Let’s say for example your scaling metric is the average CPU utilization of your EC2 auto scaling instances, and that their average should always be 80%. When CloudWatch detects that the average CPU utilization is beyond 80%, it will trigger your target tracking policy to scale out the auto scaling group to meet this target utilization.


## Target Groups

Target Group is a way of getting network traffic routed via specified protocols and ports to specified instances. It's basically load balancing on a port level. This is used mostly to allow accessing many applications running on different ports but the same instance.

A target group contains EC2 instances to which a load balancer distributes workload.

A load balancer paired with a target group does NOT yet have auto scaling capability.

This is where auto scaling comes in. An auto scaling group (ASG) can be attached to a load balancer.

We can attach auto scaling rules to an ASG. Then, when thresholds are met (e.g. CPU utilization), the number of instances will be adjusted programatically.


![Blank diagram (9)](https://user-images.githubusercontent.com/110179866/186898622-2a22eda9-b789-407d-a7be-2a1a315acfe9.jpeg)



