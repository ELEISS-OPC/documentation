# Configuration

This page discusses how the network is configured concerning [MikroTik devices via WinBox v4.0.1](https://mikrotik.com/winbox). The official documention of WinBox is found [here](https://help.mikrotik.com/docs/).


## Queues

??? info "Definition"

    A queue is a collection of data packets collectively waiting to be transmitted by a network device using a pre-defined structure methodology. Queuing works almost on the same methodology used at banks or supermarkets, where the customer is treated according to its arrival.

    Queues are used to:

    - limit data rate for certain IP addresses, subnets, protocols, ports, etc.;
    - limit peer-to-peer traffic;
    - packet prioritization;
    - configure traffic bursts for traffic acceleration;
    - apply different time-based limits;
    - share available traffic among users equally, or depending on the load of the channel

    [Reference](https://help.mikrotik.com/docs/spaces/ROS/pages/328088/Queues)


There are two (2) types of queues we want to implement:

1. Interface Queues: Limit the upload/download throughput of each switch port
2. Per Connection Queues (PCQ): Limit the upload/download throughput of each client device (customer) in the network


### Interface Queues

Start off with adding a Simple Queue for the entire network, make sure to specify its IPv4 address and CIDR. Make the the download and upload limit the same with the available uplink connection. Then add children queues to that queue, and change the limits per use case.

We can also allocate bandwidth to specific IPs in our network, an example setup with a 500mbps internet plan would be to reserve 100/100mbps download and upload bandwidth to the `Office` by setting the `Limit at` option to 100mbps for both up and download, while the remaining 400mbps is allocated to our customers. Make sure its priority is the highest priority by setting its priority level to `1`, the lower values get prioritized first.

??? tip "Recommended Watch"

    <iframe width="560" height="315" src="https://www.youtube.com/embed/tnzxrt6bgbs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

This [forum thread](https://forum.mikrotik.com/t/problems-with-queues/160459/5) discusses why devices on the same network don't hit the queue and thus have no limits. Basically, traffic is offloaded to the hardware itself (switch), instead of going through the router CPU. WAN (uplink) download and upload traffic always goes through the CPU.

### PCQs

PCQs are used for dynamically distributing bandwidth for each connected client. To set PCQs simply add a queue for the network itself (i.e 192.168.88.0/24), set max up and download limits, then set the respective queue types to `pcq-<traffic type>-default`.

??? tip "Recommended Watch"

    <iframe width="560" height="315" src="https://www.youtube.com/embed/JKeyrecL3uc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Limiting Connections

Setting connection limits can be done in `IP > Firewall`, set `Chain` to `forward` then set your source IPv4 address. In the `Advanced` tab, set the `Connection Rate` as the connection limit for your use case. In the `Action` tab, set the `Action` to `drop`.
