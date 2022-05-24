Following are the steps to setup a VPC and subnet in Google cloud

# Create a network
We create a network hello-net with the parameters custom for subnet mode and regional for bgp routing

```shell
gcloud compute networks create hello-net --subnet-mode=custom --bgp-routing-mode=regional
```

* To understand more on
    * subnet-mode see: https://cloud.google.com/vpc/docs/vpc#subnet-ranges
    * routing mode visit https://cloud.google.com/vpc/docs/vpc#routing_for_hybrid_networks

# Create a subnet
Visit https://cloud.google.com/vpc/docs/vpc for a good overview of the options for VPC and subnets

Here, we create a subnet in the region us-west1 attached to network hello-net

```shell
gcloud compute networks subnets create hello-net-us-west1-01 --network=hello-net --range=10.1.0.0/24 --secondary-range=hellonet-sec-range-01=10.2.0.0/24 --region=us-west1
```

The following commands are useful to list and describe the subnets created

```shell
 gcloud compute networks  subnets list
 ```

```shell
gcloud compute networks  subnets describe hello-net-us-west1-01
```
A sample output looks like the one below:
```text

```

## Verify the network created

```shell
gcloud compute networks list
```

# Firewall setup


```shell
gcloud compute firewall-rules create hello-net-allow-ssh-etc --network hello-net --allow tcp:22,icmp
```

```shell
gcloud compute firewall-rules create hello-net-allow-httpx --network hello-net --allow tcp:80,tcp:443
```

```shell
gcloud compute firewall-rules list
```