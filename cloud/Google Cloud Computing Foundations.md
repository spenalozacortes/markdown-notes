# Cloud Computing Fundamentals

## So, what's the cloud anyway?
### Cloud computing
The US National Institute of Standards and Technology created the term cloud computing, although there’s nothing US-specific about it.

Cloud computing is a way of using information technology (IT) that has these five equally important traits.

First, customers get computing resources that are on-demand and self-service.

Through a web interface, users get the processing power, storage, and network they need with no need for human intervention.

Second, customers get access to those resources over the internet, from anywhere they have a connection.

Third, the provider of those resources has a large pool of them, and allocates them to users out of that pool.

That allows the provider to buy in bulk and pass the savings on to the customers.

Customers don't have to know or care about the exact physical location of those resources.

Fourth, the resources are elastic–which means they can increase or decrease as needed, so customers can be flexible.

If they need more resources they can get more, and quickly.

If they need less, they can scale back.

And finally, the customers pay only for what they use, or reserve as they go.

If they stop using resources, they stop paying.

An infrastructure is the basic underlying framework of facilities and systems.

### Cloud vs. traditional architecture
The trend toward cloud computing started with a first wave known as colocation. Colocation gave users the financial efficiency of renting physical space, instead of investing in data center real estate. 

Virtualized data centers of today, which is the second wave, share similarities with the private data centers and colocation facilities of decades past. The components of virtualized data centers match the physical building blocks of hosted computing—servers, CPUs, disks, load balancers, and so on—but now they’re virtual devices. With virtualization, enterprises still maintained the infrastructure; it’s still a user-controlled and user-configured environment.

Several years ago, Google realized that its business couldn’t move fast enough within the confines of the virtualization model. So Google switched to a container-based architecture—a fully automated, elastic third-wave cloud that consists of a combination of automated services and scalable data. Services automatically provision and configure the infrastructure used to run applications. Today, Google Cloud makes this third-wave cloud available to Google customers.

It’s important to note that Google's data centers were the first to achieve ISO 14001 certification, which is a standard that maps out a framework for improving resource efficiency and reducing waste.

### IaaS, PaaS, and SaaS
The move to virtualized data centers introduced customers to two new types of offerings: infrastructure as a service, commonly referred to as IaaS, and platform as a service, or PaaS.

IaaS offerings provide raw compute, storage, and network capabilities, organized virtually into resources that are similar to physical data centers.

PaaS offerings bind code to libraries that provide access to the infrastructure applications need. This allows more resources to be focused on application logic.

In the IaaS model, customers pay for the resources they allocate ahead of time; in the PaaS model, customers pay for the resources they actually use.

As cloud computing has evolved, the momentum has shifted toward managed infrastructure and managed services. Leveraging managed resources and services allows companies to concentrate more on their business goals and spend less time and money on creating and maintaining their technical infrastructure. 

Serverless is yet another step in the evolution of cloud computing. Serverless computing allows developers to concentrate on their code, rather than on server configuration, by eliminating the need for any infrastructure management.

Serverless technologies offered by Google include Cloud Functions, which manages event-driven code as a pay-as-you-go service, and Cloud Run, which allows customers to deploy their containerized microservices–based application in a fully managed environment.

SaaS applications are not installed on your local computer; they run in the cloud as a service and are consumed directly over the internet by end users. Google's popular applications like Gmail, Docs, and Drive, collectively known as Google Workspace, are all classified as SaaS.

### Google Cloud architecture
You can think of the Google Cloud infrastructure in three layers. 

At the base layer is networking and security, which lays the foundation to support all of Google’s infrastructure and applications.

On the next layer sit compute and storage. Google Cloud separates, or decouples, as it’s technically called, compute and storage so they can scale independently based on need.

And on the top layer sit the big data and machine learning products, which enable you to perform tasks to ingest, store, process, and deliver business insights, data pipelines, and machine learning models.

And thanks to Google Cloud, you can accomplish these tasks without needing to manage and scale the underlying infrastructure.

Google offers a range of computing services, which includes: 

- Compute Engine
- Google Kubernetes Engine
- App Engine
- Cloud Functions
- Cloud Run

Google Cloud also offers a variety of managed storage options. The list includes:

- Cloud Storage
- Cloud SQL
- Cloud Spanner
- Cloud Bigtable
- Firestore

Firestore Cloud SQL and Cloud Spanner are relational databases, while Bigtable and Firestore are NoSQL databases.

And then there’s a robust big data and machine learning product line. This includes:

- Cloud Storage
- Dataproc
- Bigtable
- BigQuery
- Dataflow
- Firestore
- Pub/Sub
- Looker
- Cloud Spanner
- AutoML
- Vertex AI

A zone is an area where Google Cloud resources are deployed.

It will run in the zone that you specify to ensure resource redundancy. Zonal resources operate within a single zone, which means that if a zone becomes unavailable, the resources won’t be available either.

Google Cloud lets users specify the geographical locations to run services and resources. In many cases, you can even specify the location on a zonal, regional, or multi-regional level.

Google Cloud currently supports 103 zones in 34 regions, though this is increasing all the time. The most up to date info can be found at cloud.google.com/about/locations.


## Start with a platform
### The Cloud Console
There are actually four ways to access and interact with Google Cloud.

The list includes the Google Cloud console, the Cloud SDK and Cloud Shell, the APIs, and the Cloud Mobile App.

The Google Cloud console, which is Google Cloud’s Graphical User Interface (GUI), helps you deploy, scale, and diagnose production issues in a simple web-based interface.

With the console, you can easily find your resources, check their health, have full management control over them, and set budgets to control how much you spend on them.

The console also provides a search facility to quickly find resources and connect to instances through SSH, which is the Secure Shell Protocol, in the browser.

To access the console, navigate to console.cloud.google.com.

### Understanding projects
The console is used to access and use resources.

Resources are organized in projects.

This hierarchy is made up of four levels, and starting from the bottom up they are: resources, projects, folders, and an organization node.

At the first level are resources.

These represent virtual machines, Cloud Storage buckets, tables in BigQuery, or anything else in Google Cloud.

Resources are organized into projects, which sit on the second level.

Projects can be organized into folders, or even subfolders. These sit at the third level.

And then at the top level is an organization node, which encompasses all the projects, folders, and resources in your organization.

Projects are the basis for enabling and using Google Cloud services, like managing APIs, enabling billing, adding and removing collaborators, and enabling other Google services.

Each project is a separate compartment, and each resource belongs to exactly one project.

Projects can have different owners and users, because they’re billed and managed separately.

Each Google Cloud project has three identifying attributes: a project ID, a project name, and a project number.

The project ID is a globally unique identifier assigned by Google that cannot be changed–it is immutable–after creation.

Project IDs are used in different contexts to inform Google Cloud of the exact project to work with.

The project names, however, are user-created.

They don’t have to be unique and they can be changed at any time, so they are not immutable.

Google Cloud also assigns each project a unique project number.

They are mainly used internally, by Google Cloud, to keep track of resources.

Google Cloud has the Resource Manager tool, designed to programmatically help you do just that.

It’s an API that can gather a list of all the projects associated with an account, create new projects, update existing projects, and delete projects.

It can even recover projects that were previously deleted and can be accessed through the RPC API and the REST API.

The third level of the Google Cloud resource hierarchy is folders.

You can use folders to group projects under an organization in a hierarchy.

Folders give teams the ability to delegate administrative rights so that they can work independently.

To use folders, you must have an organization node, which is the topmost resource in the Google Cloud hierarchy.

Everything else attached to that account goes under this node, which includes projects, folders, and other resources.

### Google Cloud billing
Billing is established at the project level. This means that when you define a Google Cloud project, you link a billing account to it.

A billing account can be linked to zero or more projects, but projects that aren’t linked to a billing account can only use free Google Cloud services.

Billing accounts are charged automatically and invoiced every month or at every threshold limit. Billing sub accounts can be used to separate billing by project.

You can define budgets at the billing account level or at the project level. A budget can be a fixed limit, or it can be tied to another metric - for example, a percentage of the previous month’s spend. 2. To be notified when costs approach your budget limit, you can create an alert.

Alerts are generally set at 50%, 90% and 100%, but can also be customized.

Reports is a visual tool in the Google Cloud console that lets you monitor expenditure based on a project or services.

Finally, Google Cloud also implements quotas, which are designed to prevent the over-consumption of resources because of an error or a malicious attack, protecting both account owners and the Google Cloud community as a whole.

There are two types of quotas: rate quotas and allocation quotas. Both are applied at the project level.

Rate quotas reset after a specific time.

Allocation quotas govern the number of resources you can have in your projects. For example, by default, each Google Cloud project has a quota allowing it no more than 5 Virtual Private Cloud networks.

Although projects all start with the same quotas, you can change some of them by requesting an increase from Google Cloud Support.

If you’re interested in estimating cloud computing costs on Google Cloud, you can try out the Google Cloud Pricing Calculator at cloud.google.com/products/calculator.

### Install and configure the Cloud SDK
Now let’s explore the Cloud Software Development Kit (SDK), which lets users run Google Cloud command-line tools from a local desktop.

The Cloud SDK is a set of command-line tools that you can use to manage resources and applications hosted on Google Cloud.

These include: the gcloud CLI, which provides the main command-line interface for Google Cloud products and services, gsutil (g-s-util), which lets you access Cloud Storage from the command line, and bq, a command-line tool for BigQuery.

When installed, all of the tools within the Cloud SDK are located under the bin directory. To install the Cloud SDK to your desktop, go to cloud.google.com/sdk and select the operating system for your desktop; this will download the SDK.

Run the gcloud init (gee-cloud in-it) command. You will be prompted for information including your login credentials, default project, and default region and zone.

### Cloud Shell
Cloud Shell provides command-line access to cloud resources directly from a browser.

It’s a Debian-based virtual machine with a persistent 5-GB home directory.

With Cloud Shell, the Cloud SDK gcloud command and other utilities are always installed, available, up to date, and fully authenticated.

To start Cloud Shell, navigate to console.cloud.google.com and click the Activate Cloud Shell icon on the toolbar.

This tool is convenient for working with code-first applications or container-based workloads, because you can easily edit files without needing to download and upload changes.

### Lab: Getting started with Cloud Shell and gcloud
You can list the active account name with this command:

```shell
gcloud auth list
```

You can list the project ID with this command:

```shell
gcloud config list project
```

Your `$HOME` directory is private to you and cannot be accessed by other users.

#### Configuring your environment

##### Understanding regions and zones
Certain [Google Compute Engine](https://cloud.google.com/compute/docs/instances "Compute Engine Docs") resources live in regions or zones. A region is a specific geographical location where you can run your resources. Each region has one or more zones.

The following table shows zones in their respective regions:

|Western US|Central US|Eastern US|Western Europe|Eastern Asia|
|---|---|---|---|---|
|us-west1-a|us-central1-a|us-east1-b|europe-west1-b|asia-east1-a|
|us-west1-b|us-central1-b|us-east1-c|europe-west1c|asia-east1-b|
|-|us-central1-c|us-east1-d|europe-west1-d|aisia-east1-c|
|-|us-central1-f|-|-|-|

Resources that live in a zone are referred to as _zonal_ resources. Virtual machine instances and persistent disks live in a zone. If you want to attach a persistent disk to a virtual machine instance, both resources must be in the same zone. Similarly, if you want to assign a static IP address to an instance, the instance must be in the same region as the static IP address.

1. Set the region to `us-west1`

```shell
gcloud config set compute/region us-west1
```

2. To view the project region setting, run the following command:

```
gcloud config get-value compute/region
```

3. Set the zone to `us-west1-a`:

```shell
gcloud config set compute/zone us-west1-a
```

4. To view the project zone setting, run the following command:

```shell
gcloud config get-value compute/zone
```

##### Finding project information
In Cloud Shell, run the following `gcloud` command, to view the project id for your project:

```shell
gcloud config get-value project
```

In Cloud Shell, run the following `gcloud` command to view details about the project:

```shell
gcloud compute project-info describe --project $(gcloud config get-value project)
```

##### Setting environment variables
Environment variables define your environment and help save time when you write scripts that contain APIs or executables.

Create an environment variable to store your Project ID:

```shell
export PROJECT_ID=$(gcloud config get-value project)
```

Create an environment variable to store your Zone:

```shell
export ZONE=$(gcloud config get-value compute/zone)
```

To verify that your variables were set properly, run the following commands:

```shell
echo -e "PROJECT ID: $PROJECT_ID\nZONE: $ZONE"
```

##### Creating a virtual machine with the gcloud tool

To create your VM, run the following command:

```shell
gcloud compute instances create gcelab2 --machine-type e2-medium --zone $ZONE
```

**Command details**

- `gcloud compute` allows you to manage your Compute Engine resources in a format that's simpler than the Compute Engine API.
- `instances create` creates a new instance.
- `gcelab2` is the name of the VM.
- The `--machine-type` flag specifies the machine type as _e2-medium_.
- The `--zone` flag specifies where the VM is created.
- If you omit the `--zone` flag, the `gcloud` tool can infer your desired zone based on your default properties. Other required instance settings, such as `machine type` and `image`, are set to default values if not specified in the `create` command.

To open help for the `create` command, run the following command:

```shell
gcloud compute instances create --help
```

##### Exploring gcloud commands
The `gcloud` tool offers simple usage guidelines that are available by adding the `-h` flag (for help) onto the end of any `gcloud` command.

```shell
gcloud -h
```

You can access more verbose help by appending the `--help` flag onto a command or running the `gcloud help` command.

```shell
gcloud config --help
```

Run the following command:

```shell
gcloud help config
```

The results of the `gcloud config --help` and `gcloud help config` commands are equivalent. Both return long, detailed help.

There are [global flags](https://cloud.google.com/sdk/gcloud/reference/) in `gcloud` that govern the behavior of commands on a per-invocation level. Flags override any values set in SDK properties.

View the list of configurations in your environment:

```shell
gcloud config list
```

To see all properties and their settings:

```shell
gcloud config list --all
```

List your components:

```shell
gcloud components list
```

#### Filtering command-line output
List the compute instance available in the project:

```shell
gcloud compute instances list
```

List the gcelab2 virtual machine:

```shell
gcloud compute instances list --filter="name=('gcelab2')"
```

List the firewall rules in the project:

```shell
gcloud compute firewall-rules list
```

List the firewall rules for the default network:

```shell
gcloud compute firewall-rules list --filter="network='default'"
```

List the firewall rules for the default network where the allow rule matches an ICMP rule:

```shell
gcloud compute firewall-rules list --filter="NETWORK:'default' AND ALLOW:'icmp'"
```

#### Connecting to your VM instance
The `gcloud compute ssh` command provides a wrapper around SSH, which takes care of authentication and the mapping of instance names to IP addresses.

To connect to your VM with SSH, run the following command:

```shell
gcloud compute ssh gcelab2 --zone $ZONE
```

Install `nginx` web server on to virtual machine:

```shell
sudo apt install -y nginx
```

To disconnect from SSH and exit the remote shell, run the following command:

```shell
exit
```

#### Updating the firewall
List the firewall rules for the project:

```shell
gcloud compute firewall-rules list
```

Try to access the nginx service running on the `gcelab2` virtual machine.

Add a tag to the virtual machine:

```shell
gcloud compute instances add-tags gcelab2 --tags http-server,https-server
```

Update the firewall rule to allow:

```shell
gcloud compute firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server
```

List the firewall rules for the project:

```shell
gcloud compute firewall-rules list --filter=ALLOW:'80'
```

Verify communication is possible for http to the virtual machine:

```shell
curl http://$(gcloud compute instances list --filter=name:gcelab2 --format='value(EXTERNAL_IP)')
```

#### Viewing the system logs
View the available logs on the system:

```shell
gcloud logging logs list
```

View the logs that relate to compute resources:

```shell
gcloud logging logs list --filter="compute"
```

Read the logs related to the resource type of `gce_instance`:

```shell
gcloud logging read "resource.type=gce_instance" --limit 5
```

Read the logs for a specific virtual machine:

```shell
gcloud logging read "resource.type=gce_instance AND labels.instance_name='gcelab2'" --limit 5
```

 
### Google Cloud APIs
Application developers structure the software they write in a clean, well-defined interface that abstracts away needless detail, and then they document that interface. That’s an Application Programming Interface.

The underlying implementation can change as long as the interface doesn’t, and other pieces of software that use the API don’t have to know or care.

The services that make up Google Cloud offer APIs so that code you write can control them.

The Google Cloud console includes a tool called the Google APIs Explorer that shows what APIs are available, and in what versions.

Google provides Cloud Client and Google API Client Libraries in many popular languages to take much of the drudgery out of the task of calling Google Cloud from your code.

Languages currently represented in these libraries are: Java, Python, PHP, C#, Go, Node.js, Ruby and C++.

### The Cloud Console Mobile App
The Cloud Mobile App can be used to start, stop, and use ssh to connect to Compute Engine instances and to see logs from each instance.

It also lets you stop and start Cloud SQL instances.

Additionally, you can administer applications deployed on App Engine by viewing errors, rolling back deployments, and changing traffic splitting.

The Cloud Mobile App provides up-to-date billing information for your projects and billing alerts for projects that are going over budget.

You can set up customizable graphs showing key metrics such as CPU usage, network usage, requests per second, and server errors.

The mobile app also offers alerts and incident management.


## Use Google Cloud to build your apps

### Compute Options in the Cloud
Google Cloud offers a variety of compute services spanning different usage options.

For general workloads that require dedicated resources for your applications, Compute Engine is a good option.

If you’re looking for a platform as a service, App Engine is a good option.

Cloud Functions offers a serverless option for triggering code to run based on some kind of event.

To run containers on a managed Kubernetes platform, you can leverage GKE.

And Cloud Run is a fully managed serverless platform that lets you develop and deploy highly scalable containerized applications.

### Exploring IaaS with Compute Engine
With Compute Engine, users can create and run virtual machines in Google's innovative data centers and on its global fiber network.

There are no upfront investments, and thousands of virtual CPUs can run on a system that is designed to be fast and offer consistent performance.

Each virtual machine contains the power and functionality of a full-fledged operating system. This means a virtual machine can be configured much like a physical server: by specifying the amount of CPU power and memory needed, the amount and type of storage needed, and the operating system.

You can run any computing workload on Compute Engine, such as web-server hosting, application hosting, or application backends.

A virtual machine instance can be created by using the Google Cloud console, which is a web-based tool to manage Google Cloud projects and resources, or through the gcloud CLI.

The instance can run Linux and Windows Server images provided by Google or any customized versions of these images. You can also build and run images of other operating systems and flexibly reconfigure virtual machines.

For the use of virtual machines, Compute Engine bills by the second with a one-minute minimum, and sustained-use discounts start to apply automatically to virtual machines the longer they run. So, for each VM that runs for more than 25% of a month, Compute Engine automatically applies a discount for every additional minute. 

Compute Engine also offers committed-use discounts. This means that for stable and predictable workloads, a specific amount of vCPUs and memory can be purchased for up to a 57% discount off normal prices in return for committing to a usage term of one year or three years.

And then there are Preemptible VMs. Let’s say you have a workload that doesn’t require a human to sit and wait for it to finish–like a batch job analyzing a large dataset, for example. You can save money, in some cases up to 90%, by choosing Preemptible VMs to run the job.

A Preemptible VM is different from an ordinary VM in only one respect: Compute Engine has permission to terminate a job if its resources are needed elsewhere. While savings are possible with preemptible VMs, you'll need to ensure that your job can be stopped and restarted.

### Lab - Creating a Virtual Machine

#### Overview
Compute Engine lets you create virtual machines that run different operating systems, including multiple flavors of Linux (Debian, Ubuntu, Suse, Red Hat, CoreOS) and Windows Server, on Google infrastructure. You can run thousands of virtual CPUs on a system that is designed to be fast and to offer strong consistency of performance.

#### Create a new instance from the Cloud Console
1. In the Cloud Console, on the **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click **Compute Engine** > **VM Instances**.

	This may take a minute to initialize for the first time.

2. To create a new instance, click **CREATE INSTANCE**.

3. There are many parameters you can configure when creating a **new instance**. 

|   |   |   |
|---|---|---|
|**Machine Type**|**2 vCPU**|This is an (e2-medium), 2-CPU, 4GB RAM instance. Several machine types are available, ranging from micro instance types to 32-core/208GB RAM instance types. For more information, see the Compute Engine guide, [About machine families](https://cloud.google.com/compute/docs/machine-types). **Note:** A new project has a default [resource quota](https://cloud.google.com/compute/docs/resource-quotas), which may limit the number of CPU cores. You can request more when you work on projects outside this lab.|
|**Firewall**|**Allow HTTP traffic**|Select this option in order to access a web server that you'll install later. **Note:** This will automatically create a firewall rule to allow HTTP traffic on port 80.|

5. Click **Create**.
    
    It should take about a minute for the machine to be created. After that, the new virtual machine is listed on the **VM Instances** page.

6. To use **SSH** to connect to the virtual machine, in the row for your machine, click **SSH**.

	This launches an SSH client directly from your browser.

#### Install an NGINX web server
Now you'll install an NGINX web server, one of the most popular web servers in the world, to connect your virtual machine to something.

1. Update the OS:

```shell
sudo apt-get update
```
 
2. Install **NGINX**:

```shell
sudo apt-get install -y nginx
```
 
3. Confirm that **NGINX is running**:

```shell
ps auwx | grep nginx
```
 
4. To see the web page, return to the Cloud Console and click the **External IP** link in the row for your machine, or add the **External IP** value to `http://EXTERNAL_IP/` in a new browser window or tab.

#### Create a new instance with gcloud
Instead of using the Cloud Console to create a virtual machine instance, you can use the command line tool `gcloud`, which is pre-installed in [Google Cloud Shell](https://cloud.google.com/developer-shell/#how_do_i_get_started). Cloud Shell is a Debian-based virtual machine loaded with all the development tools you'll need (`gcloud`, `git`, and others) and offers a persistent 5-GB home directory.

1. In the Cloud Shell, use `gcloud` to create a new virtual machine instance from the command line:

```shell
gcloud compute instances create gcelab2 --machine-type e2-medium --zone us-east1-d
```

The new instance has these default values:

- The latest [Debian 11 (bullseye)](https://cloud.google.com/compute/docs/images#debian) image.
- The `e2-medium` [machine type](https://cloud.google.com/compute/docs/machine-types).
- A root persistent disk with the same name as the instance; the disk is automatically attached to the instance.

2. To see all the defaults, run:

```shell
gcloud compute instances create --help
```
 
Note: You can set the default region and zones that gcloud uses if you are always working within one region/zone and you don't want to append the --zone flag every time.

```shell
gcloud config set compute/zone ...
gcloud config set compute/region ...
```

3. In the Cloud Console, on the **Navigation menu**, click **Compute Engine > VM instances**.  
our 2 new instances should be listed.

4. You can also use SSH to connect to your instance via `gcloud`. Make sure to add your zone, or omit the `--zone` flag if you've set the option globally:

```shell
gcloud compute ssh gcelab2 --zone us-east1-d 
```

### Configuring Elastic Apps with Autoscaling
With Compute Engine you can choose the most appropriate machine properties for your instances, like the number of virtual CPUs and the amount of memory.

You can use a set of predefined machine types or create your own custom machine types. To do this, Compute Engine has a feature called autoscaling, where VMs can be added to or subtracted from an application based on load metrics.

The other part of making that work is balancing the incoming traffic among the VMs. Google’s Virtual Private Cloud (VPC) supports several different kinds of load balancing.

With Compute Engine, you can in fact configure very large VMs, which are great for workloads such as in-memory databases and CPU-intensive analytics, but most Google Cloud customers start off with scaling out, not up.

The maximum number of CPUs per VM is tied to its “machine family” and is also constrained by the quota available to the user, which is zone-dependent.

Specs for currently available VM machine types are at cloud.google.com/compute/docs/machine-types

### Exploring PaaS with App Engine
You’ll explore how App Engine can run your applications without requiring you to manage the infrastructure.

App Engine lets you build highly scalable applications on a fully managed, serverless platform.

App Engine is ideal if time-to-market is highly valuable to you and you want to focus on writing code without ever having to touch a server, cluster, or infrastructure.

It’s also ideal if you don’t want to worry about a pager going off or receiving 5xx errors! App Engine allows you to have high availability apps without a complex architecture.

With App Engine, you can choose from popular coding languages, libraries, and frameworks to develop apps with tools you’re familiar with, and then automatically provision servers and scale app instances based on demand.

Options include Eclipse, IntelliJ, Maven, Git, Jenkins, and PyCharm. That means that you can upload your code, and Google will manage your app's availability.

App Engine also provides built-in services and APIs, like NoSQL datastores, Memcache, load balancing, health checks, application logging, and a user authentication API that is common to most applications.

App Engine offers software development kits, or SDKs, to help you develop, deploy, and manage your apps on your local machine.

Each SDK includes: 

- All of the APIs and libraries available to App Engine, 
- A simulated, secure sandbox environment that emulates all of the App Engine services on your local computer,
- And deployment tools to upload your application to the cloud and manage different versions.

The SDK manages your application locally, and the Google Cloud console manages your application in production.

Use the Google Cloud console’s web-based interface to create new applications, configure domain names, change which version of your application is live, examine access and error logs, and more.

There are two types of App Engine environments: standard and flexible.

The first is the App Engine standard environment, which is based on container instances running on Google's infrastructure.

Containers are preconfigured with a runtime from a standardized list of supported languages and versions, which include libraries that support App Engine standard APIs.

For many applications, the standard environment runtimes and libraries may be all you need.

The standard environment features include:

- Persistent storage with queries, sorting, and transactions.
- Automatic scaling and load balancing.
- Asynchronous task queues for performing work outside the scope of a request.
- Scheduled tasks for triggering events at specified times or regular intervals.
- And integration with other Google Cloud services and APIs.

There are a couple of requirements for using the standard environment: 

1. You must use specified versions of Java, Python, PHP, Go, Node.js, and Ruby.
2. Your application must conform to sandbox constraints that are dependent on runtime.

Applications run in a secure, sandboxed environment. This allows the App Engine standard environment to distribute requests across multiple servers and scale servers to meet traffic demands.

This means that your application runs within its own secure, reliable environment that is independent of the hardware, operating system, or physical location of the server.

A standard environment workflow typically follows these three steps: 

1. First, a web application is developed and tested locally. 
2. Second, the SDK is used to deploy the application to App Engine.
3. And third, App Engine scales and services the application.

App Engine also offers a flexible environment. If the standard environment’s sandbox model is too restrictive for you, the flexible environment can let you specify the type of container your web application will run in. This option lets an application run inside Docker containers on Google Cloud’s Compute Engine virtual machines.

In this case, App Engine manages Compute Engine machines for you. This means that:  

- Instances are health-checked, healed as necessary, and colocated with other module instances within the project.
- Critical, backward-compatible updates are automatically applied to the underlying operating system.
- VM instances are automatically located by geographical region according to the settings in your project. Google's management services ensure that all of a project's VM instances are colocated for optimal performance.
- And VM instances are restarted on a weekly basis. During restarts, Google's management services will apply any necessary operating system and security updates.

The flexible environment supports microservices, authorization, SQL and NoSQL databases, traffic splitting, logging, search, versioning, security scanning, Memcache, and content delivery networks.

App Engine flexible environment allows users to also benefit from custom configurations and libraries while still keeping their main focus on what they do best – writing code.

In addition, the App Engine flexible environment allows you to customize the runtime and the operating system of your virtual machine by using Dockerfiles.

As in the App Engine standard environment, supported runtimes include Python, Java, Go, Node.js, PHP, and Ruby.

However, in the App Engine flexible environment, developers can also use different versions of these runtimes or provide their own custom runtime by supplying a custom Docker image or using a Dockerfile from the open source community.

So, how do these two environments compare to each other? Let’s start with the standard environment, which is fast. It starts up instances of your application in seconds, but you have less access to the infrastructure in which your application runs.

With the standard environment, you can’t use ssh to connect to the virtual machines on which your application runs, and you can’t write to a local disk.

The standard environment does support third-party binaries for certain languages, and you can use App Engine to make calls to the network.

Finally, in terms of pricing, after a free tier usage, you pay per instance class with automatic shutdown.

The flexible environment takes minutes to start up, instead of seconds. But it lets you use ssh to connect to the virtual machines on which your application runs, it lets you use local disk for scratch space, it lets you install third-party software, and it lets your application make calls to the network without going through App Engine.

In terms of pricing, with the flexible environment, you pay for resource allocation per hour with no automatic shutdown.

Because App Engine uses Docker containers, you may be wondering how App Engine compares to Google Kubernetes Engine. App Engine standard environment is for people who want the service to take maximum control of their web and mobile application’s deployment and scaling. Google Kubernetes Engine, however, gives the application owner the full flexibility of Kubernetes. App Engine flexible environment is somewhere between the two.

### Lab - App Engine: Python

#### Overview
[App Engine](https://cloud.google.com/appengine) allows developers to focus on doing what they do best, writing code, and not what it runs on. Developers upload their apps to App Engine, and Google Cloud takes care of the rest. The notion of servers, virtual machines, and instances have been abstracted away, with App Engine providing all the compute necessary. Developers don't have to worry about operating systems, web servers, logging, monitoring, load-balancing, system administration, or scaling, as App Engine takes care of all that. Developers only need to focus on building solutions for their organizations or their users.

The App Engine standard environment provides application-hosting services supporting the following languages: Python, Java, PHP, Go, Node.js, and Ruby). The App Engine flexible environment provides even more flexibility by supporting custom runtimes, however it is out-of-scope for this lab.

App Engine is Google Cloud's original serverless runtime, and since its original launch in 2008, has been joined by:

- [Cloud Functions](https://cloud.google.com/functions), great for situations where you don't have an entire app, have broken up a larger, monolithic app into multiple microservices, or have short event-driven tasks that execute based on user activity.
- [Cloud Run](http://cloud.run), the serverless container-hosting service similar to App Engine but more accurately reflects the state of software development today.

App Engine makes it easy to build and deploy an application that runs reliably even under heavy load and with large amounts of data. (Cloud Functions and Cloud Run do the same.)

App Engine apps can access numerous additional Cloud or other Google services for use in their applications:

- **NoSQL database:** [Cloud Datastore](https://cloud.google.com/datastore), [Cloud Firestore](https://cloud.google.com/firestore), [Cloud BigTable](https://cloud.google.com/bigtable)
- **Relational database:** [Cloud SQL](https://cloud.google.com/sql) or [Cloud AlloyDB](https://cloud.google.com/alloydb), [Cloud Spanner](https://cloud.google.com/spanner)
- **File/object storage:** [Cloud Storage](https://cloud.google.com/storage), [Cloud Filestore](https://cloud.google.com/filestore), [Google Drive](https://developers.google.com/drive)
- **Caching:** [Cloud Memorystore](https://cloud.google.com/memorystore) (Redis or `memcached`)
- **Task execution:** [Cloud Tasks](https://cloud.google.com/tasks), [Cloud Pub/Sub](https://cloud.google.com/pubsub), [Cloud Scheduler](https://cloud.google.com/scheduler), [Cloud Workflows](https://cloud.google.com/workflows)
- **User authentication:** [Cloud Identity Platform](https://cloud.google.com/identity-platform), [Firebase Auth](https://firebase.google.com/docs/auth), [Google Identity Services](https://developers.google.com/identity)
Applications run in a secure, sandboxed environment, allowing App Engine standard environment to distribute requests across multiple servers, and scaling servers to meet traffic demands. Your application runs within its own secure, reliable environment that is independent of the hardware, operating system, or physical location of the server.
 
#### Enable Google App Engine Admin API
The App Engine Admin API enables developers to provision and manage their App Engine Applications.

1. In the left **Navigation menu**, click **APIs & Services** > **Library**.
2. Type "App Engine Admin API" in the search box.
3. Click the **App Engine Admin API** card.
4. Click **Enable**. If there is no prompt to enable the API, then it is already enabled and no action is needed.

#### Test the application
Test the application using the Google Cloud development server (`dev_appserver.py`), which is included with the preinstalled App Engine SDK.

1. From within your helloworld directory where the app's [app.yaml](https://cloud.google.com/appengine/docs/standard/python/config/appref) configuration file is located, start the Google Cloud development server with the following command:

```shell
dev_appserver.py app.yaml
```

The development server is now running and listening for requests on port 8080.

2. View the results by clicking the **Web preview** (![web preview icon](https://cdn.qwiklabs.com/7b9oXblGsiFuNK7hmDZjFB%2B7Lrwdv5T64bbmo8X9FAo%3D)) > **Preview on port 8080**.

	You'll see this in a new browser window:

#### Make a change
You can leave the development server running while you develop your application. The development server watches for changes in your source files and reloads them if necessary.

Leave the development server running. We'll open another command line window, then edit `main.py` to change "Hello World!" to "Hello, Cruel World!".

1. Click the (**+**) next to your Cloud Shell tab to open a new command line session.
2. Enter this command to go to the directory that contains the sample code:
3. Enter the following to open main.py in nano to edit the content:

```shell
nano main.py
```

#### Deploy your app
1. To deploy your app to App Engine, run the following command from within the root directory of your application where the app.yaml file is located:

```shell
gcloud app deploy
```

2. Enter the number that represents your region:
3. The App Engine application will then be created.
4. Enter **Y** when prompted to confirm the details and begin the deployment of service.

#### View your application
To launch your browser enter the following command, then click on the link it provides:

```shell
gcloud app browse
```

Your application is deployed and you can read the short message in your browser.

### Event-Driven Programs with Cloud Functions
Cloud Functions is serverless code that lets you run it based on certain events.

Many applications contain event-driven parts. For example, maybe you have an application that lets users upload images. When that event takes place, the image might need to be processed in a few different ways, like converting the image to a standard format, converting a thumbnail into different sizes, and storing each new file in a repository.

You could integrate this function into your application, but then you’d have to provide compute resources for it–whether it happens once a millisecond or once a day.

With Cloud Functions, you could write a single-purpose function that completes the necessary image manipulations, and then arrange for it to automatically run whenever a new image is uploaded.

Cloud Functions is a lightweight, event-based, asynchronous compute solution that allows you to create small, single-purpose functions that respond to cloud events without needing to manage a server or a runtime environment.

You can use these functions to construct applications from bite-sized business logic. You can also use Cloud Functions to connect and extend cloud services.

You are billed to the nearest 100 milliseconds, but only while your code is running.

Individual Cloud Functions are written in Javascript (Node.js), Python, or Go and executed in a managed Node.js environment on Google Cloud.

Events from Cloud Storage and Pub/Sub can trigger Cloud Functions asynchronously, or you can use HTTP invocation for synchronous execution.

### Lab - Cloud Functions: Command Line

#### Overview
A cloud function is a piece of code that runs in response to an event, such as an HTTP request, a message from a messaging service, or a file upload. Cloud events are _things_ that happen in your cloud environment. These might be things like changes to data in a database, files added to a storage system, or a new virtual machine instance being created.

Since cloud functions are event-driven, they only run when something happens. This makes them a good choice for tasks that need to be done quickly or that don't need to be running all the time.

For example, you can use a cloud function to:

- automatically generate thumbnails for images that are uploaded to Cloud Storage.
- send a notification to a user's phone when a new message is received in Cloud Pub/Sub.
- process data from a Cloud Firestore database and generate a report.

You can write your code in any language that supports Node.js, and you can deploy your code to the cloud with a few clicks. Once your cloud function is deployed, it will automatically start running in response to events.

#### Create a function
First, you're going to create a simple function named helloWorld. This function writes a message to the Cloud Functions logs. It is triggered by cloud function events and accepts a callback function used to signal completion of the function.

For this lab the cloud function event is a cloud pub/sub topic event. A pub/sub is a messaging service where the senders of messages are decoupled from the receivers of messages. When a message is sent or posted, a subscription is required for a receiver to be alerted and receive the message. To learn more about pub/subs, in Cloud Pub/Sub Guides, see [Google Cloud Pub/Sub: A Google-Scale Messaging Service](https://cloud.google.com/pubsub/architecture).

To learn more about the event parameter and the callback parameter, in Cloud Functions Documentation, see [Background Functions](https://cloud.google.com/functions/docs/writing/background).

To create a cloud function:

1. In Cloud Shell, run the following command to set the default region:

```shell
gcloud config set compute/region ""
```

2. Create a directory for the function code:

```shell
mkdir gcf_hello_world
```

3. Move to the `gcf_hello_world` directory:

```shell
cd gcf_hello_world
```

4. Create and open `index.js` to edit:

```shell
nano index.js
```

5. Copy the following into the `index.js` file:

```js
/**
* Background Cloud Function to be triggered by Pub/Sub.
* This function is exported by index.js, and executed when
* the trigger topic receives a message.
*
* @param {object} data The event payload.
* @param {object} context The event metadata.
*/
exports.helloWorld = (data, context) => {
const pubSubMessage = data;
const name = pubSubMessage.data
    ? Buffer.from(pubSubMessage.data, 'base64').toString() : "Hello World";
console.log(`My Cloud Function: ${name}`);
};
```

6. Exit nano (Ctrl+x) and save (Y) the file.

#### Create a cloud storage bucket
- Use the following command to create a new cloud storage bucket for your function:

```shell
gsutil mb -p [PROJECT_ID] gs://[BUCKET_NAME]
```

**PROJECT_ID** is the Project ID in the lab details panel on the left of this lab:

**BUCKET_NAME** is the name you give to the bucket. You can use the Project ID as the bucket name to ensure a globally unique name:

To learn more about naming buckets, In Cloud Storage Documentation, see [Bucket naming guidelines](https://cloud.google.com/storage/docs/naming-buckets).

#### Deploy your function
When deploying a new function, you must specify `--trigger-topic`, `--trigger-bucket`, or `--trigger-http`. When deploying an update to an existing function, the function keeps the existing trigger unless otherwise specified.

For this lab, you'll set the `--trigger-topic` as `hello_world`.

1. Deploy the function to a pub/sub topic named **hello_world**, replacing `[BUCKET_NAME]` with the name of your bucket:

```shell
gcloud functions deploy helloWorld \
  --stage-bucket [BUCKET_NAME] \
  --trigger-topic hello_world \
  --runtime nodejs8
```

If prompted, enter `Y` to allow unauthenticated invocations of a new function.

2. Verify the status of the function:

```shell
gcloud functions describe helloWorld
```

An ACTIVE status indicates that the function has been deployed.

Every message published in the topic triggers function execution, the message contents are passed as input data.

#### Test the function
After you deploy the function and know that it's active, test that the function writes a message to the cloud log after detecting an event.

- Enter this command to create a message test of the function:

```shell
DATA=$(printf 'Hello World!'|base64) && gcloud functions call helloWorld --data '{"data":"'$DATA'"}'
```

The cloud tool returns the execution ID for the function, which means a message has been written in the log.

View logs to confirm that there are log messages with that execution ID.

#### View logs
- Check the logs to see your messages in the log history:

```shell
gcloud functions logs read helloWorld
```

If the function executed successfully, messages in the log appear.

Note: The logs will take around 10 mins to appear. Also, the alternative way to view the logs is, go to **Logging > Logs Explorer**.

Your application is deployed, tested, and you can view the logs.

### Containerizing and Orchestrating Apps with GKE
Now you’ll be introduced to containers and GKE, which is a hybrid that conceptually sits between the two, offering the managed infrastructure of an IaaS, with the developer orientation of a PaaS offering.

IaaS lets you share compute resources with other developers by using virtual machines to virtualize the hardware. This lets each developer deploy their own operating system, or OS, access the hardware, and build their applications in a self-contained environment with access to RAM, file systems, networking interfaces, etc.

This is where containers come in. The idea of a container is to give the independent scalability of workloads in PaaS and an abstraction layer of the OS and hardware in IaaS.

A configurable system lets you install your favorite runtime, web server, database, or middleware, configure the underlying system resources, such as disk space, disk I/O, or networking, and build as you like. 

But flexibility comes with a cost. The smallest unit of compute is an app with its VM. The guest OS might be large, even gigabytes in size, and take minutes to boot. As demand for your application increases, you have to copy an entire VM and boot the guest OS for each instance of your app, which can be slow and costly.

Now, with App Engine, you have access to programming services, so you only need to write your code in self-contained workloads that use these services and include any dependent libraries. 

This means that as demand for your app increases, the platform scales your app seamlessly and independently by workload and infrastructure. This scales rapidly but there’s no option to fine-tune the underlying architecture to save cost.

A container is an invisible box around your code and its dependencies with limited access to its own partition of the file system and hardware.

It only requires a few system calls to create and it starts as quickly as a process.

All that’s needed on each host is an OS kernel that supports containers and a container runtime. In essence, the OS is being virtualized.

It scales like PaaS but gives you nearly the same flexibility as IaaS.

This makes code ultra portable, and the OS and hardware can be treated as a black box. So you can go from development, to staging, to production, or from your laptop to the cloud, without changing or rebuilding anything.

As an example, let’s say you want to scale a web server. With a container, you can do this in seconds and deploy dozens or hundreds of servers, depending on the size or your workload, on a single host. That's just a simple example of scaling one container running the whole application on a single host. 

However, you'll probably want to build your applications using lots of containers, each performing their own function, as is done when using a microservices architecture. If you build applications this way and connect them with network connections, you can make them modular, easily deployable, and scaled independently across a group of hosts.

The hosts can scale up and down and start and stop containers as demand for your app changes or as hosts fail.

Kubernetes is a container orchestration tool you can use to simplify the management of containerized environments.

You can install Kubernetes on a group of your own managed servers or run it as a hosted service in Google Cloud on a cluster of managed Compute Engine instances called Google Kubernetes Engine.

Kubernetes was built by Google to run applications at scale. It lets you install the system on local servers in the cloud, manage container networking and data storage, deploy rollouts and rollbacks, and monitor and manage container and host health.

A software container makes it easier for teams to package, manage, and ship their code. They write software applications that run in a container. The container provides the operating system needed to run their application. The container will run on any container platform. This can save a lot of time and cost compared to running servers or virtual machines.

Like a virtual machine imitates a computer, a container imitates an operating system.

Everything at Google runs on containers: Gmail, Web search, Maps, MapReduce, batch, Google File System, Colossus, even Cloud Functions (VMs in containers).

Google launches over 2 billion containers per week.

Docker is the tool that puts the application and everything it needs in the container. Once the application is in a container, it can be moved anywhere that will run Docker containers—any laptop, server, or cloud provider. This portability makes code easier to produce, manage, troubleshoot, and update.

For service providers, containers make it easy to develop code that can be easily transferred and run both in the cloud and on a customer's on-premises servers.

Kubernetes is an open source container orchestration tool for managing a cluster of Docker Linux containers as a single system. It can be run in the cloud and on-premises environments. It’s inspired and informed by Google’s experiences and internal systems.

Google Kubernetes Engine, GKE, is a managed environment for deploying containerized apps. It brings Google’s latest innovations in developer productivity, resource efficiency, automated operations, and open source flexibility to accelerate time to market.

GKE is a powerful cluster manager and orchestration system for running Docker containers in Google Cloud.

GKE manages containers automatically based on specifications such as CPU and memory. It's built on the open source Kubernetes system, making it easy for users to orchestrate container clusters or groups of containers, and it also gives customers the flexibility to take advantage of on-premises, hybrid, or public cloud infrastructure.

### Lab - Kubernetes Engine

#### Overview
[Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) (GKE) provides a managed environment for deploying, managing, and scaling your containerized applications using Google infrastructure.

The Kubernetes Engine environment consists of multiple machines (specifically [Compute Engine](https://cloud.google.com/compute) instances) grouped to form a [container cluster](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture).

#### Cluster orchestration with Google Kubernetes Engine
Google Kubernetes Engine (GKE) clusters are powered by the [Kubernetes](https://kubernetes.io/) open source cluster management system. Kubernetes provides the mechanisms through which you interact with your container cluster. You use Kubernetes commands and resources to deploy and manage your applications, perform administrative tasks, set policies, and monitor the health of your deployed workloads.

Kubernetes draws on the same design principles that run popular Google services and provides the same benefits: automatic management, monitoring and liveness probes for application containers, automatic scaling, rolling updates, and more. When you run your applications on a container cluster, you're using technology based on Google's 10+ years of experience with running production workloads in containers.

#### Kubernetes on Google Cloud
When you run a GKE cluster, you also gain the benefit of advanced cluster management features that Google Cloud provides. These include:

- [Load balancing](https://cloud.google.com/compute/docs/load-balancing-and-autoscaling) for Compute Engine instances
- [Node pools](https://cloud.google.com/kubernetes-engine/docs/node-pools) to designate subsets of nodes within a cluster for additional flexibility
- [Automatic scaling](https://cloud.google.com/kubernetes-engine/docs/cluster-autoscaler) of your cluster's node instance count
- [Automatic upgrades](https://cloud.google.com/kubernetes-engine/docs/node-auto-upgrade) for your cluster's node software
- [Node auto-repair](https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-repair) to maintain node health and availability
- [Logging and Monitoring](https://cloud.google.com/kubernetes-engine/docs/how-to/logging) with Cloud Monitoring for visibility into your cluster

#### Set a default compute zone
Your [compute zone](https://cloud.google.com/compute/docs/regions-zones/#available) is an approximate regional location in which your clusters and their resources live.

1. **Set the default compute region**,

```shell
gcloud config set compute/region assigned_at_lab_start
```

2. **Set the default compute zone**,

```shell
gcloud config set compute/zone assigned_at_lab_start
```

#### Create a GKE cluster
A [cluster](https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-architecture) consists of at least one **cluster master** machine and multiple worker machines called **nodes**. Nodes are [Compute Engine virtual machine (VM) instances](https://cloud.google.com/compute/docs/instances/) that run the Kubernetes processes necessary to make them part of the cluster.

Note: Cluster names must start with a letter and end with an alphanumeric, and cannot be longer than 40 caracters.

Run the following command:

1. **Create a cluster**

```shell
gcloud container clusters create --machine-type=e2-medium --zone=assigned_at_lab_start lab-cluster 
```

You can ignore any warnings in the output. It might take several minutes to finish creating the cluster.

#### Get authentication credentials for the cluster
After creating your cluster, you need authentication credentials to interact with it.

1. **Authenticate with the cluster**:

```shell
gcloud container clusters get-credentials lab-cluster 
```

#### Deploy an application to the cluster
You can now deploy a containerized application to the cluster.

GKE uses Kubernetes objects to create and manage your cluster's resources. Kubernetes provides the [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) object for deploying stateless applications like web servers. [Service](https://kubernetes.io/docs/concepts/services-networking/service/) objects define rules and load balancing for accessing your application from the internet.

1. To **create a new Deployment** `hello-server` from the `hello-app` container image, run the following [kubectl create](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#create) command:

```shell
kubectl create deployment hello-server --image=gcr.io/google-samples/hello-app:1.0
```

This Kubernetes command creates a Deployment object that represents `hello-server`. In this case, `--image` specifies a container image to deploy. The command pulls the example image from a [Container Registry](https://cloud.google.com/container-registry/docs) bucket. `gcr.io/google-samples/hello-app:1.0` indicates the specific image version to pull. If a version is not specified, the latest version is used.

2. To **create a Kubernetes Service**, which is a Kubernetes resource that lets you expose your application to external traffic, run the following [kubectl expose](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#expose) command:

```shell
kubectl expose deployment hello-server --type=LoadBalancer --port 8080
```

In this command:

- `--port` specifies the port that the container exposes.
- `type="LoadBalancer"` creates a Compute Engine load balancer for your container.

3. To **inspect** the `hello-server` Service, run [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get):

```shell
kubectl get service
```

Note: It might take a minute for an external IP address to be generated. Run the previous command again if the `EXTERNAL-IP` column status is pending.

4. To view the application from your web browser, open a new tab and enter the following address, replacing `[EXTERNAL IP]` with the `EXTERNAL-IP` for `hello-server`.

```shell
http://[EXTERNAL-IP]:8080
```

#### Deleting the cluster
1. To **delete** the cluster, run the following command:

```shell
gcloud container clusters delete lab-cluster 
```

2. When prompted, type **Y** to confirm.

Deleting the cluster can take a few minutes. For more information on deleted GKE clusters from the Google Kubernetes Engine (GKE) article, [Deleting a cluster](https://cloud.google.com/kubernetes-engine/docs/how-to/deleting-a-cluster).
 
### Managed serverless computing with Cloud Run
Cloud Run is a managed compute platform that lets you run stateless containers by using web requests or Pub/Sub events. 

Cloud Run is serverless. That means it removes all infrastructure management tasks so you can focus on developing applications.

It’s built on Knative, an open API and runtime environment built on Kubernetes that gives you freedom to move your workloads across different environments and platforms. 

It can be fully managed on Google Cloud, on Google Kubernetes Engine, or anywhere Knative runs.

Cloud Run is fast. It can automatically scale up from zero and back down almost instantaneously, and it charges you only for the resources you use, calculated down to the nearest 100 milliseconds, so you‘ll never pay for your over-provisioned resources.

The Cloud Run developer workflow is a straightforward three-step process. 

First, you write your application using your favorite programming language. This application should start a server that listens for web requests.

Second, you build and package your application into a container image.

Finally, you deploy the container image to Cloud Run.

After you’ve deployed your container image, you’ll receive a unique HTTPS URL back, which you will use to run your new containerized application.

Cloud Run then starts your container on demand to handle requests and ensures that all incoming requests are handled by dynamically adding and removing containers.

Cloud Run is serverless. That means that you, as a developer, can focus on building your application and not on building and maintaining the infrastructure that powers your application.

For some use cases, a container-based workflow is great, because it gives you a great amount of transparency and flexibility. If you build the container image, you have the power to decide exactly what file is added to your container image, and how it gets there.

However, building an application is hard enough already, let alone having to think about containerization and the responsibilities that come with that. Sometimes, you’re just looking for a way to turn source code into an HTTPS endpoint, and you want your vendor to make sure that your container image is secure, well-configured, and built in a consistent way.

With Cloud Run, you can do both. You can use a container-based workflow and a source-based workflow.

If you use the source-based approach, you’ll deploy your source code instead of a container image. Cloud Run then builds your source and packages the application into a container image for you. Cloud Run does this using Buildpacks - an open source project.

Cloud Run handles HTTPS serving for you. That means you only have to worry about handling web requests, and you can let Cloud Run take care of adding the encryption.

By default, your application is exposed on a unique subdomain of the global \*run.app domain You can also use your own, custom domain.

Cloud Run manages everything else: 

- Generating a valid SSL certificate 
- Configuring SSL termination correctly with secure settings 
- Handling incoming requests, decrypting them, and forwarding them to your application

The pricing model on Cloud Run is unique; you only pay for the system resources you use while a container is handling web requests, with a granularity of 100ms, and when it is starting or shutting down. You do not pay for anything if your container does not handle requests.

Additionally, there is a small fee for every one million requests you serve. The price of container time increases with CPU and memory. A container with more vCPU and memory is more expensive. Today, Cloud Run can allocate up to 4 vCPUs and 8 GB of memory. 

Most of the other compute products (such as Compute Engine), charge for servers as long as they are running, even if you are not using them. That means you’re often paying for idle server capacity.

You can use Cloud Run to run any binary, as long as it’s compiled for Linux 64-bit.

Now, this means you can use Cloud Run to run web applications written using popular languages, such as: Java Python Node.js PHP Go C++ And you can also run code written in less popular languages: Cobol Haskell Perl

As long as your app handles web requests, you should be able to run it and scale it automatically using Cloud Run.


## Create and Manage Cloud Resources
### Lab - Compute Engine: Windows

#### Overview
Compute Engine lets you create and run virtual machines on Google infrastructure. Compute Engine offers scale, performance, and value that allows you to easily launch large compute clusters on Google's infrastructure.

You can run your Windows applications on Compute Engine and take advantage of many benefits available to virtual machine instances, such as reliable [storage options](https://cloud.google.com/compute/docs/disks/), the speed of the [Google network](https://cloud.google.com/compute/docs/vpc), and [Autoscaling](https://cloud.google.com/compute/docs/autoscaler/).

#### Create a virtual machine instance
1. In the Cloud Console, on the **Navigation menu** ![Navigation menu](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D "Navigation menu"), click **Compute Engine > VM instances**, and then click **Create Instance**.
2. Select:
	- region:
	- zone: .
3. In the **Machine configuration** section, for **Series** select **E2**.
4. In the **Boot disk** section, click **Change** to begin configuring your boot disk.
5. Under **Operating system** select **Windows Server** and under **Version** select **Windows Server 2012 R2 Datacenter**, and then click **Select**. Leave all other settings as their defaults.
6. Click **Create** to create the instance.

#### Remote Desktop (RDP) into the Windows Server

##### Test the status of Windows Startup
After a short time, the Windows Server instance will be provisioned and listed on the VM Instances page with a green status icon![Green Status Icon](https://cdn.qwiklabs.com/zLABj4YctjgDvpZ2K07lk9smIYG2GsT91dK%2FC9AWNTM%3D).

The server instance may not be ready to accept RDP connections, as it takes a while for all OS components to initialize.

1. To see whether the server instance is ready for an RDP connection, run the following command at your Cloud Shell terminal command line:

```shell
gcloud compute instances get-serial-port-output instance-1
```

2. If prompted, type N and press ENTER.

Repeat the command until you see the following in the command output, which tells you that the OS components have initialized and the Windows Server is ready to accept your RDP connection.

```
Instance setup finished. instance-1 is ready to use.
```

##### RDP into the Windows Server
1. To set a password for logging into the RDP, run the following command in Cloud Shell. Be sure you replace `[instance]` with the VM Instance that you created, `[zone]` that you defined earlier and set `[username]` as **admin**.

```shell
gcloud compute reset-windows-password [instance] --zone [zone] --user [username]
```

2. If asked `Would you like to set or reset the password for [admin] (Y/n)?`, enter Y. Record the password for use in later steps to connect.
3. Connect to your server. There are different ways to connect to your server through RDP, depending on whether you are on Windows or not:

	- If you are using a Chromebook or other machine at a Google Cloud event there is likely an RDP app already installed on the computer. Click the icon as below, if it is present, in the lower left corner of the screen and enter the external IP of your VM.
	- If you are not on Windows but using Chrome, you can connect to your server through RDP directly from the browser using the [Spark View](https://chrome.google.com/webstore/detail/spark-view-faster-than-an/ddnnpdbioplhcagobicknkjkbhdefjkg?hl=en) extension. Click on **Add to Chrome**. Then, click **Launch app**.
4. Once launched, the **Spark View (RDP)** window opens. Use your Windows username **admin** and password you previously recorded in Step 2.
5. Add your VM instance's External IP as your Domain. Click Connect to confirm you want to connect.

If you are on a Macintosh, there are several freely accessible RDP Client packages available to install, such as [CoRD](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=0ahUKEwjthJbPzPDVAhVBZFAKHclnDRQQFgg_MAI&url=http%3A%2F%2Fcord.sourceforge.net%2F&usg=AFQjCNGyH4EJo932rqm3QgiuHfDRmQfFVA). After installing, connect as above to the External IP address of the Windows server. Once it has connected, it will open up a login page where you can specify Windows username **admin** and password from the output of above mentioned command to log in (ignore the Domain: field).

Once logged in, you should see the Windows desktop!

##### Copy and paste with the RDP client
Once you are securely logged into your instance, you may find yourself copying and pasting commands from the lab manual.

To paste, hold the **CTRL-V** keys (if you are a Mac user, using **CMND-V** will not work.) If you are in a Powershell window, be sure that you have clicked into the window or else the paste shortcut won't work.

If you are pasting into putty, **right click**.
 
### Lab Set Up Network and HTTP Load Balancers

#### Overview
In this hands-on lab you'll learn the differences between a network load balancer and an HTTP load balancer and how to set them up for your applications running on Compute Engine virtual machines (VMs).

There are several ways you can [load balance on Google Cloud](https://cloud.google.com/load-balancing/docs/load-balancing-overview#a_closer_look_at_cloud_load_balancers). This lab takes you through the set up of the following load balancers:

- [Network Load Balancer](https://cloud.google.com/compute/docs/load-balancing/network/)
- [HTTP(s) Load Balancer](https://cloud.google.com/compute/docs/load-balancing/http/)

#### Set the default region and zone for all resources
1. In Cloud Shell, set the default zone:

```shell
gcloud config set compute/zone 
```

2. Set the default region:

```shell
gcloud config set compute/region 
```

#### Create multiple web server instances
For this load balancing scenario, create three Compute Engine VM instances and install Apache on them, then add a firewall rule that allows HTTP traffic to reach the instances.

The code provided sets the zone to `<filled in at lab start>`. Setting the tags field lets you reference these instances all at once, such as with a firewall rule. These commands also install Apache on each instance and give each instance a unique home page.

1. Create a virtual machine www1 in your default zone.

```shell
  gcloud compute instances create www1 \
    --zone= \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www1</h3>" | tee /var/www/html/index.html'
```

2. Create a virtual machine www2 in your default zone.

```shell
  gcloud compute instances create www2 \
    --zone= \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www2</h3>" | tee /var/www/html/index.html'
```

3. Create a virtual machine www3 in your default zone.

```shell
  gcloud compute instances create www3 \
    --zone= \
    --tags=network-lb-tag \
    --machine-type=e2-small \
    --image-family=debian-11 \
    --image-project=debian-cloud \
    --metadata=startup-script='#!/bin/bash
      apt-get update
      apt-get install apache2 -y
      service apache2 restart
      echo "
<h3>Web Server: www3</h3>" | tee /var/www/html/index.html'
```

4. Create a firewall rule to allow external traffic to the VM instances:

```shell
gcloud compute firewall-rules create www-firewall-network-lb \
    --target-tags network-lb-tag --allow tcp:80
```

Now you need to get the external IP addresses of your instances and verify that they are running.

5. Run the following to list your instances. You'll see their IP addresses in the `EXTERNAL_IP` column:

```shell
gcloud compute instances list
```

6. Verify that each instance is running with `curl`, replacing **[IP_ADDRESS]** with the IP address for each of your VMs:

```shell
curl http://[IP_ADDRESS]
```

#### Configure the load balancing service
When you configure the load balancing service, your virtual machine instances will receive packets that are destined for the static external IP address you configure. Instances made with a Compute Engine image are automatically configured to handle this IP address.

**Note:** Learn more about how to set up network load balancing from the [External TCP/UDP Network Load Balancing overview Guide](https://cloud.google.com/compute/docs/load-balancing/network/).

1. Create a static external IP address for your load balancer:

```shell
   gcloud compute addresses create network-lb-ip-1 \
    --region  
```

2. Add a legacy HTTP health check resource:

```
gcloud compute http-health-checks create basic-check
```

3. Add a target pool in the same region as your instances. Run the following to create the target pool and use the health check, which is required for the service to function:

```shell
  gcloud compute target-pools create www-pool \
    --region  --http-health-check basic-check
```

4. Add the instances to the pool:

```shell
gcloud compute target-pools add-instances www-pool \
    --instances www1,www2,www3
```

5. Add a forwarding rule:

```shell
gcloud compute forwarding-rules create www-rule \
    --region   \
    --ports 80 \
    --address network-lb-ip-1 \
    --target-pool www-pool
```

#### Sending traffic to your instances
Now that the load balancing service is configured, you can start sending traffic to the forwarding rule and watch the traffic be dispersed to different instances.

1. Enter the following command to view the external IP address of the www-rule forwarding rule used by the load balancer:

```shell
gcloud compute forwarding-rules describe www-rule --region 
```

2. Access the external IP address

```shell
IPADDRESS=$(gcloud compute forwarding-rules describe www-rule --region  --format="json" | jq -r .IPAddress)
```

3. Show the external IP address

```shell
echo $IPADDRESS
```

4. Use `curl` command to access the external IP address, replacing `IP_ADDRESS` with an external IP address from the previous command:

```shell
while true; do curl -m1 $IPADDRESS; done
```

The response from the `curl` command alternates randomly among the three instances. If your response is initially unsuccessful, wait approximately 30 seconds for the configuration to be fully loaded and for your instances to be marked healthy before trying again.

5. Use **Ctrl** + **c** to stop running the command.

#### Create an HTTP load balancer
HTTP(S) Load Balancing is implemented on Google Front End (GFE). GFEs are distributed globally and operate together using Google's global network and control plane. You can configure URL rules to route some URLs to one set of instances and route other URLs to other instances.

Requests are always routed to the instance group that is closest to the user, if that group has enough capacity and is appropriate for the request. If the closest group does not have enough capacity, the request is sent to the closest group that **does** have capacity.

To set up a load balancer with a Compute Engine backend, your VMs need to be in an instance group. The managed instance group provides VMs running the backend servers of an external HTTP load balancer. For this lab, backends serve their own hostnames.

1. First, create the load balancer template:

```shell
gcloud compute instance-templates create lb-backend-template \
   --region= \
   --network=default \
   --subnet=default \
   --tags=allow-health-check \
   --machine-type=e2-medium \
   --image-family=debian-11 \
   --image-project=debian-cloud \
   --metadata=startup-script='#!/bin/bash
     apt-get update
     apt-get install apache2 -y
     a2ensite default-ssl
     a2enmod ssl
     vm_hostname="$(curl -H "Metadata-Flavor:Google" \
     http://169.254.169.254/computeMetadata/v1/instance/name)"
     echo "Page served from: $vm_hostname" | \
     tee /var/www/html/index.html
     systemctl restart apache2'
```

[Managed instance groups](https://cloud.google.com/compute/docs/instance-groups) (MIGs) let you operate apps on multiple identical VMs. You can make your workloads scalable and highly available by taking advantage of automated MIG services, including: autoscaling, autohealing, regional (multiple zone) deployment, and automatic updating.

2. Create a managed instance group based on the template:

```shell
gcloud compute instance-groups managed create lb-backend-group \
   --template=lb-backend-template --size=2 --zone= 
```

3. Create the `fw-allow-health-check` firewall rule.

```shell
gcloud compute firewall-rules create fw-allow-health-check \
  --network=default \
  --action=allow \
  --direction=ingress \
  --source-ranges=130.211.0.0/22,35.191.0.0/16 \
  --target-tags=allow-health-check \
  --rules=tcp:80
```

**Note:** The ingress rule allows traffic from the Google Cloud health checking systems (`130.211.0.0/22` and `35.191.0.0/16`). This lab uses the target tag `allow-health-check` to identify the VMs

4. Now that the instances are up and running, set up a global static external IP address that your customers use to reach your load balancer:

```shell
gcloud compute addresses create lb-ipv4-1 \
  --ip-version=IPV4 \
  --global
```

**Note the IPv4 address that was reserved:**

```shell
gcloud compute addresses describe lb-ipv4-1 \
  --format="get(address)" \
  --global
```

5. Create a health check for the load balancer:

```shell
gcloud compute health-checks create http http-basic-check \
  --port 80
```

**Note:** Google Cloud provides health checking mechanisms that determine whether backend instances respond properly to traffic. For more information, please refer to the [Creating health checks document](https://cloud.google.com/load-balancing/docs/health-checks).

6. Create a backend service:

```shell
gcloud compute backend-services create web-backend-service \
  --protocol=HTTP \
  --port-name=http \
  --health-checks=http-basic-check \
  --global
```

7. Add your instance group as the backend to the backend service:

```shell
gcloud compute backend-services add-backend web-backend-service \
  --instance-group=lb-backend-group \
  --instance-group-zone= \
  --global
```

8. Create a [URL map](https://cloud.google.com/load-balancing/docs/url-map-concepts) to route the incoming requests to the default backend service:

```shell
gcloud compute url-maps create web-map-http \
    --default-service web-backend-service
```

**Note:** URL map is a Google Cloud configuration resource used to route requests to backend services or backend buckets. For example, with an external HTTP(S) load balancer, you can use a single URL map to route requests to different destinations based on the rules configured in the URL map:

- Requests for https://example.com/video go to one backend service.
- Requests for https://example.com/audio go to a different backend service.
- Requests for https://example.com/images go to a Cloud Storage backend bucket.
- Requests for any other host and path combination go to a default backend service.

9. Create a target HTTP proxy to route requests to your URL map:

```shell
gcloud compute target-http-proxies create http-lb-proxy \
    --url-map web-map-http
```

10. Create a global forwarding rule to route incoming requests to the proxy:

```shell
gcloud compute forwarding-rules create http-content-rule \
    --address=lb-ipv4-1\
    --global \
    --target-http-proxy=http-lb-proxy \
    --ports=80
```

**Note:** A [forwarding rule](https://cloud.google.com/load-balancing/docs/using-forwarding-rules) and its corresponding IP address represent the frontend configuration of a Google Cloud load balancer. Learn more about the general understanding of forwarding rules from the [Forwarding rule overview Guide](https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts).

#### Testing traffic sent to your instances
1. In the Cloud Console, from the **Navigation menu**, go to **Network services** > **Load balancing**.
2. Click on the load balancer that you just created (`web-map-http`).
3. In the **Backend** section, click on the name of the backend and confirm that the VMs are **Healthy**. If they are not healthy, wait a few moments and try reloading the page.
4. When the VMs are healthy, test the load balancer using a web browser, going to `http://IP_ADDRESS/`, replacing `IP_ADDRESS` with the load balancer's IP address.

This may take three to five minutes. If you do not connect, wait a minute, and then reload the browser.

Your browser should render a page with content showing the name of the instance that served the page, along with its zone (for example, `Page served from: lb-backend-group-xxxx`).

# Infrastructure in Google Cloud

## Where do I store this stuff?

### Storage options in the cloud
Google Cloud offers relational and non-relational databases and worldwide object storage.

Choosing the right option to store and process data often depends on the data type that needs to be stored and the business need.

These include: 

- Cloud Storage
- Cloud SQL
- Cloud Spanner
- Firestore
- Cloud Bigtable

The goal of these products is to reduce the time and effort needed to store data. This means creating an elastic storage bucket directly in a web interface or through a command line.

There are three common cloud storage use cases.

1. The first is content storage and delivery.

	This is when content, such as images or videos, needs to be served to users wherever they are.

2. The second use case is storage for data analytics and general compute.

	Users can process or expose their data to analytics tools, like the analytics stack of products that Google Cloud offers, and do things like genomic sequencing or IoT data analysis.

3. The third use case is backup and archival storage. 

	Users can save storage costs by migrating infrequently accessed content to cheaper cloud storage options. Also, if anything happens to their data on-premises, it's critical to have a copy in the cloud for recovery purposes.

For users with databases, Google’s first priority is to help them migrate existing databases to the cloud and move them to the right service. This will usually be users moving MySQL or Postgre workloads to Cloud SQL.

The second priority is to help users innovate, build or rebuild for the cloud, offer mobile applications, and plan for future growth.

### Structured and unstructured data storage
Unstructured data is information stored in a non-tabular form such as documents, images, and audio files. Unstructured data is usually best suited to Cloud Storage.

It’s estimated that around 80 percent of all data is unstructured.

It’s far more difficult to process or analyze unstructured data using traditional methods because the data has no internal identifier to enable search functions to identify it.

Unstructured data often includes text and multimedia content, for example, email messages, documents, photos, videos, presentations, and web pages.

Organizations are focusing increasingly on mining unstructured data for insights that will provide them with a competitive edge.

Alternatively, there is structured data, which represents information stored in tables, rows, and columns.

Structured data is what most people are used to working with and typically fits within columns and rows in spreadsheets or relational databases.

You can expect this type of data to be organized and clearly defined and usually easy to capture, access, and analyze.

Examples of structured data include names, addresses, contact numbers, dates, and billing info.

The benefit of structured data is that it can be understood by programming languages and can be manipulated relatively quickly.

Structured data comes in two types: transactional workloads and analytical workloads.

Transactional workloads stem from Online Transaction Processing systems, which are used when fast data inserts and updates are required to build row-based records. This is usually to maintain a system snapshot. They require relatively standardized queries that affect only a few records.

So, if your data is transactional and you need to access it using SQL, Cloud SQL and Cloud Spanner are two options.

Cloud SQL works best for local to regional scalability, But Cloud Spanner is best to scale a database globally.

If the transactional data will be accessed without SQL, Firestore might be the best option. Firestore is a transactional NoSQL, document-oriented database.

Then there are analytical workloads, which stem from Online Analytical Processing systems, which are used when entire datasets need to be read. They often require complex queries, for example, aggregations.

If you have analytical workloads that require SQL commands, BigQuery may be the best option. BigQuery, Google’s data warehouse solution, lets you analyze petabyte-scale datasets.

Alternatively, Bigtable provides a scalable NoSQL solution for analytical workloads. It’s best for real-time, high-throughput applications that require only millisecond latency.

### Unstructured storage using Cloud Storage
Cloud Storage is a fully managed scalable service that has a wide variety of uses. A few examples include serving website content, storing data for archival and disaster recovery, and distributing large data objects to end users through Direct Download.

Cloud Storage’s primary use is whenever binary large-object storage (also known as a “BLOB”) is needed for online content such as videos and photos, for backup and archived data, and for storage of intermediate results in processing workflows.

Object storage is a computer data storage architecture that manages data as “objects” and not as a file and folder hierarchy (file storage), or as chunks of a disk (block storage).

These objects are stored in a packaged format that contains the binary form of the actual data itself, relevant associated metadata (such as date created, author, resource type, and permissions), and a globally unique identifier.

These unique keys are in the form of URLs, which means object storage interacts well with web technologies.

Data commonly stored as objects includes video, pictures, and audio recordings. 

Cloud Storage is Google’s object storage product. It allows customers to store any amount of data and to retrieve it as often as needed.

There are four primary storage classes in Cloud Storage, and stored data is managed and billed according to which class it belongs in.

The first is Standard Storage. Standard Storage is considered best for frequently accessed, or “hot,” data. It’s also great for data that is stored for only brief periods of time.

The second storage class is Nearline Storage. This is best for storing infrequently accessed data, like reading or modifying data once per month on average. Examples include data backups, long-tail multimedia content, or data archiving.

The third storage class is Coldline Storage. This is also a low-cost option for storing infrequently accessed data. However, as compared to Nearline Storage, Coldline Storage is meant for reading or modifying data, at most, once every 90 days.

The fourth storage class is Archive Storage. This is the lowest-cost option, used ideally for data archiving, online backup, and disaster recovery. It’s the best choice for data that you plan to access less than once a year, because it has higher costs for data access and operations and a 365-day minimum storage duration.

Although each of these four classes has differences, it’s worth noting that several characteristics apply across all these storage classes. These include: Unlimited storage with no minimum object size requirement, Worldwide accessibility and locations, Low latency and high durability, A uniform experience, which extends to security, tools, and APIs, and Geo-redundancy if data is stored in a multi-region or dual-region. So this means placing physical servers in geographically diverse data centers to protect against catastrophic events and natural disasters and load-balancing traffic for optimal performance.

Cloud Storage files are organized into buckets. A bucket needs a globally unique name and a specific geographic location for where it should be stored, and an ideal location for a bucket is where latency is minimized.

The storage objects offered by Cloud Storage are “immutable,” which means that you do not edit them, but instead a new version is created with every change made.

Administrators can either allow each new version to completely overwrite the older one or keep track of each change made to a particular object by enabling “versioning” within a bucket.

If you choose to use versioning, Cloud Storage will keep a detailed history of modifications -- that is, overwrites or deletes -- of all objects contained in that bucket. If you don’t turn on object versioning, by default new versions will always overwrite older versions.

With object versioning enabled, you can list the archived versions of an object, restore an object to an older state, or permanently delete a version of an object, as needed.

Cloud Storage also offers lifecycle management policies for your objects. For example, you could tell Cloud Storage to delete objects older than 365 days, or to delete objects created before January 1, 2013, or to keep only the 3 most recent versions of each object in a bucket that has versioning enabled.

Cloud Storage’s tight integration with other Google Cloud products and services means that there are many additional ways to move data into the service.

For example, you can import and export tables to and from both BigQuery and Cloud SQL. You can also store App Engine logs, Firestore backups, and objects used by App Engine applications like images. Cloud Storage can also store instance startup scripts, Compute Engine images, and objects used by Compute Engine applications.

### Lab - Cloud Storage: CLI/SDK

#### Overview
Cloud Storage allows world-wide storage and retrieval of any amount of data at any time. You can use Cloud Storage for a range of scenarios including serving website content, storing data for archival and disaster recovery, or distributing large data objects to users via direct download.

Throughout this lab you'll be able to verify your work in the console by going to **Navigation menu** > **Cloud Storage**.

#### Create a bucket
The Cloud Storage utility tool, [gsutil](https://cloud.google.com/storage/docs/gsutil), is installed and ready to use in Google Cloud. In this lab you use `gsutil` in Cloud Shell.

**Bucket naming rules**

- Do not include sensitive information in the bucket name, because the bucket namespace is global and publicly visible.
- Bucket names must contain only lowercase letters, numbers, dashes (-), underscores (`_`), and dots (.). Names containing dots require [verification](https://cloud.google.com/storage/docs/domain-name-verification).
- Bucket names must start and end with a number or letter.
- Bucket names must contain 3 to 63 characters. Names containing dots can contain up to 222 characters, but each dot-separated component can be no longer than 63 characters.
- Bucket names cannot be represented as an IP address in dotted-decimal notation (for example, 192.168.5.4).
- Bucket names cannot begin with the "goog" prefix.
- Bucket names cannot contain "google" or close misspellings of "google".
- Also, for DNS compliance and future compatibility, you should not use underscores (`_`) or have a period adjacent to another period or dash. For example, ".." or "-." or ".-" are not valid in DNS names.

Use the make bucket (`mb`) command to make a bucket, replacing `<YOUR_BUCKET_NAME>` with a unique name that follows the bucket naming rules:

```shell
gsutil mb gs://<YOUR-BUCKET-NAME>
```

This command is creating a bucket with default settings. To see what those default settings are, use the Cloud console **Navigation menu** > **Cloud Storage**, then click on your bucket name, and click on the **Configuration** tab.

**Note:** If the bucket name is already taken, either by you or someone else, the command returns:

`Creating gs://YOUR-BUCKET-NAME/...`  
`ServiceException: 409 Bucket YOUR-BUCKET-NAME already exists.`

Try again with a different bucket name.

#### Upload an object into your bucket
Use Cloud Shell to upload an object into a bucket.

1. To download this image (ada.jpg) into your bucket, enter this command into Cloud Shell:

```shell
curl https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg --output ada.jpg
```

2. Use the `gsutil cp` command to upload the image from the location where you saved it to the bucket you created:

```shell
gsutil cp ada.jpg gs://YOUR-BUCKET-NAME
```

3. Now remove the downloaded image:

```shell
rm ada.jpg
```

#### Download an object from your bucket
- Use the `gsutil cp` command to download the image you stored in your bucket to Cloud Shell:

```shell
gsutil cp -r gs://YOUR-BUCKET-NAME/ada.jpg .
```

#### Copy an object to a folder in the bucket
- Use the `gsutil cp` command to create a folder called `image-folder` and copy the image (ada.jpg) into it:

```shell
gsutil cp gs://YOUR-BUCKET-NAME/ada.jpg gs://YOUR-BUCKET-NAME/image-folder/
```

**Note:** Compared to local file systems, [folders in Cloud Storage](https://cloud.google.com/storage/docs/gsutil/addlhelp/HowSubdirectoriesWork) have limitations, but many of the same operations are supported.

#### List contents of a bucket or folder
- Use the `gsutil ls` command to list the contents of the bucket:

```shell
gsutil ls gs://YOUR-BUCKET-NAME
```

#### List details for an object
- Use the `gsutil ls` command, with the `-l` flag to get some details about the image file you uploaded to your bucket:

```shell
gsutil ls -l gs://YOUR-BUCKET-NAME/ada.jpg
```

Now you know the image's size and date of creation.

#### Make your object publicly accessible
- Use the `gsutil acl ch` command to grant all users read permission for the object stored in your bucket:

```shell
gsutil acl ch -u AllUsers:R gs://YOUR-BUCKET-NAME/ada.jpg
```

Validate that your image is publicly available.

- Go to **Navigation menu** > **Cloud Storage**, then click on the name of your bucket.

You should see your image with the **Public link** box. Click the **Copy URL** and open the URL in a new browser tab.

#### Remove public access
1. To remove this permission, use the command:

```shell
gsutil acl ch -d AllUsers gs://YOUR-BUCKET-NAME/ada.jpg
```

2. Verify that you've removed public access by clicking the **Refresh** button in the console. The checkmark will be removed.

#### Delete objects
1. Use the `gsutil rm` command to delete an object - the image file in your bucket:

```shell
gsutil rm gs://YOUR-BUCKET-NAME/ada.jpg
```

2. Refresh the console. The copy of the image file is no longer stored on Cloud Storage (though the copy you made in the `image-folder/` folder still exists).

### SQL managed services
A database is a collection of information that is organized so that it can easily be accessed and managed.

Computer applications run databases to get a fast answer to questions like: What’s this user’s name, given their sign-in information, so I can display it? What’s the cost of product Y so I can show it on my dynamic web page? These apps must be able to write data in and read data out of databases.

When a database is used, it’s usually run by a computer application. So when we say that “a database is useful for doing X,” it’s usually because it’s designed to make answering a question simple, fast, and efficient for the app.

Relational database management systems, abbreviated RDBMS, or just relational databases, are used extensively and are the kind of database you encounter most of the time. They’re organized based on the relational model of data.

They are very good when you have a well-structured data model and when you need transactions and the ability to join data across tables to retrieve complex combinations of your data.

Because they make use of the Structured Query Language, they are sometimes called SQL databases.

Google Cloud offers two managed relational database services, Cloud SQL and Cloud Spanner.

### Exploring Cloud SQL
Cloud SQL offers fully managed relational databases, including MySQL, PostgreSQL, and SQL Server as a service.

It’s designed to hand off mundane, but necessary and often time-consuming, tasks to Google—like applying patches and updates, managing backups, and configuring replications—so your focus can be on building great applications.

Cloud SQL: 

- Doesn't require any software installation or maintenance.
- Can scale up to 96 processor cores, 624 GB of RAM, and 64 TB of storage.
- Supports automatic replication scenarios, such as from a Cloud SQL primary instance, an external primary instance, and external MySQL instances.
- Supports managed backups, so backed-up data is securely stored and accessible if a restore is required. The cost of an instance covers seven backups.
- Encrypts customer data when on Google’s internal networks and when stored in database tables, temporary files, and backups.
- Includes a network firewall, which controls network access to each database instance.

### Lab - Cloud SQL for MySQL

#### Overview
In this lab you will learn how to create and connect to a Google Cloud SQL MySQL instance and perform basic SQL operations using the Cloud Console and the mysql client.

#### Create a Cloud SQL instance
1. From the **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) click on **SQL**.
2. Click **Create Instance**.
3. Create your instance with the following settings:
    
    - Click **choose MySQL**
    - Type "myinstance" for **Instance ID**
    - In the password field click on the **Generate** link and the eye icon to see the password. **Save** the password to use in the next section.
    - Leave all other fields at the default values.
    
4. Click **Create Instance**.

#### Connect to your instance using the mysql client in Cloud Shell
1. In the Cloud Console, click the Cloud Shell icon in the upper right corner.
2. At the Cloud Shell prompt, connect to your Cloud SQL instance by running the following:

```shell
gcloud sql connect myinstance --user=root
```

3. Enter your root password when prompted. **Note:** The cursor will not move.

You should now see the `mysql` prompt.

#### Create a database and upload data
1. Create a SQL database called `guestbook` on your Cloud SQL instance:

```mysql
CREATE DATABASE guestbook;
```

2. Insert the following sample data into the guestbook database:

```mysql
USE guestbook;
CREATE TABLE entries (guestName VARCHAR(255), content VARCHAR(255),
    entryID INT NOT NULL AUTO_INCREMENT, PRIMARY KEY(entryID));
    INSERT INTO entries (guestName, content) values ("first guest", "I got here!");
INSERT INTO entries (guestName, content) values ("second guest", "Me too!");
```

3. Now retrieve the data:

```mysql
SELECT * FROM entries;
```

### Cloud Spanner as a managed service
Cloud Spanner is a fully managed relational database service that scales horizontally, is strongly consistent, and speaks SQL.

Vertical scaling is where you make a single instance larger or smaller, while horizontal scaling is when you scale by adding and removing servers.

Cloud Spanner is especially suited for applications that require:

- An SQL relational database management system with joins and secondary indexes
- Built-in high availability
- Strong global consistency
- And high numbers of input/output operations per second, such as tens of thousands of reads/writes per second.

So how does Cloud Spanner work? Data is automatically and instantly copied across regions, which is called synchronous replication. As a result, queries always return consistent and ordered answers regardless of the region.

Google uses replication within and across regions to achieve availability, so if one region goes offline, a user’s data can still be served from another region.

### NoSQL managed services options
Google offers two managed NoSQL database options, Firestore and Cloud Bigtable.

Firestore is a fully managed, serverless NoSQL document store that supports ACID transactions.

Cloud Bigtable is a petabyte scale, sparse wide column NoSQL database that offers extremely low write latency.

### Firestore, a NoSQL document store
Firestore is a flexible, horizontally scalable, NoSQL cloud database for mobile, web, and server development.

With Firestore, incoming data is stored in a document structure, and these documents are then organized into collections. Documents can contain complex nested objects in addition to subcollections.

Firestore’s NoSQL queries can then be used to retrieve individual, specific documents or to retrieve all the documents in a collection that match your query parameters.

Queries can include multiple, chained filters and combine filtering and sorting options. They're also indexed by default, so query performance is proportional to the size of the result set, not the dataset.

Firestore uses data synchronization to update data on any connected device. However, it's also designed to make simple, one-time fetch queries efficiently.

It caches data that an app is actively using, so the app can write, read, listen to, and query data even if the device is offline. When the device comes back online, Firestore synchronizes any local changes back to Firestore.

Firestore leverages Google Cloud’s powerful infrastructure: automatic multi-region data replication, strong consistency guarantees, atomic batch operations, and real transaction support.

### Bigtable as a NoSQL option
Bigtable is Google's NoSQL big data database service. It's the same database that powers many core Google services, including Search, Analytics, Maps, and Gmail.

Bigtable is designed to handle massive workloads at consistent low latency and high throughput, so it's a great choice for both operational and analytical applications, including Internet of Things, user analytics, and financial data analysis.

When deciding which storage option is best, customers often choose Bigtable if:

- They’re working with more than 1TB of semi-structured or structured data.
- Data is fast with high throughput, or it’s rapidly changing.
- They’re working with NoSQL data. This usually means transactions where strong relational semantics are not required.
- Data is a time-series or has natural semantic ordering.
- They’re working with big data, running asynchronous batch or synchronous real-time processing on the data.
- Or they’re running machine learning algorithms on the data.

Bigtable can interact with other Google Cloud services and third-party clients. Using APIs, data can be read from and written to Bigtable through a data service layer like Managed VMs, the HBase REST Server, or a Java Server using the HBase client. Typically this is used to serve data to applications, dashboards, and data services.

Data can also be streamed in through various popular stream processing frameworks like Dataflow Streaming, Spark Streaming, and Storm.

And if streaming is not an option, data can also be read from and written to Bigtable through batch processes like Hadoop MapReduce, Dataflow, or Spark. Often, summarized or newly calculated data is written back to Bigtable or to a downstream database.

BigQuery is not mentioned in this module because it sits on the edge between data storage and data processing and is covered in more depth in other courses. The usual reason to store data in BigQuery is so you can use its big data analysis and interactive querying capabilities. It is not purely a data storage product.


## There’s an API for that!

### The purpose of APIs
Application developers structure the software they write so that it presents a clean, well-defined interface that hides unnecessary detail, and then they document that interface. That’s an application programming interface. The underlying implementation can change, as long as the interface doesn’t, and other pieces of software that use the API don’t have to know or care.

APIs are used to simplify the way different, disparate, software resources communicate. By using a universal structure of communications, we open up a wide range of opportunities.

Sometimes you do have to change an API, perhaps to add or deprecate a feature. To cleanly make this kind of change to the API, developers create versions. For example, version 2 of an API might contain calls that version 1 does not. This means that programs that consume the API can specify the API version they want to use in their calls.

REpresentational State Transfer, or REST, is currently the most popular architectural style for services. It outlines a key set of constraints and agreements that a service must comply with. If a service complies with these REST constraints, it’s said to be RESTful.

The web is HTTP-based and provides an architectural structure that scales well and stands the test of time. REST transfers the ideas that worked so well for the web and applies them to services.

APIs intended to be spread widely to consumers and deployed to devices with limited computing resources, like mobile, are well suited to a REST structure.

REST APIs use HTTP requests to perform GET, PUT, POST, and DELETE operations.

Having different software services leverage a universal communication channel ensures that applications can be updated or rewritten and still work with other applications, as long as they conform to the agreed-upon API standard.

One of the main reasons REST APIs work well with the cloud is due to their stateless nature. State information does not need to be stored or referenced for the API to run.

Also, authentication can be done through OAuth, and security can be used by leveraging tokens.

When deploying and managing APIs on your own, there are several issues to consider. These include the language or format you’ll use to describe the interface, how you’ll authenticate services and users who invoke your API, how you’ll ensure that your API scales to meet demand, and whether your infrastructure log details API invocations and provides monitoring metrics.

### Cloud Endpoints
Now that you have an understanding of what an API is, let’s explore Cloud Endpoints, which is a system to develop, deploy, and manage APIs on any Google Cloud backend.

Cloud Endpoints is a distributed API management system that uses a distributed Extensible Service Proxy, which is a service proxy that runs in its own Docker container. The goal is to help you create and maintain even the most demanding APIs with low latency and high performance.

Cloud Endpoints provides an API console, hosting, logging, monitoring, and other features to help you create, share, maintain, and secure your APIs.

You can use Cloud Endpoints with any APIs that support the OpenAPI Specification.

Cloud Endpoints supports applications running in App Engine, Google Kubernetes Engine, and Compute Engine.

Clients include Android, iOS, and Javascript.

Cloud Endpoints supports the Open API specification and gRPC API specification.

Cloud Endpoints also supports service-to-service authentication and user authentication with Firebase, Auth0, and Google authentication. 

The Extensible Service Proxy, Service Management, and Service Control together validate requests, log data, and handle high volumes of traffic.

Logging and Trace allow you to view detailed logs, trace lists, and metrics related to traffic volume, latency, size of requests and responses, and errors.

### Lab - Cloud Endpoints

#### Overview
In this lab you will deploy a sample API with [Google Cloud Endpoints](https://cloud.google.com/endpoints/docs/frameworks/about-cloud-endpoints-frameworks), which are a set of tools for generating APIs from within an App Engine application. The sample code will include:

- A REST API that you can query to find the name of an airport from its three-letter `IATA` code (for example, SFO, JFK, AMS).
- A script that uploads the API configuration to Cloud Endpoints.
- A script that deploys a Google App Engine flexible backend to host the sample API.

After you send some requests to the sample API, you can view the Cloud Endpoints Activity Graphs and Logs. These are tools that allow you to monitor your APIs and gain insights into their usage.

#### Getting the sample code
1. Enter the following command in Cloud Shell to get the sample API and scripts:

```shell
gsutil cp gs://spls/gsp164/endpoints-quickstart.zip .
unzip endpoints-quickstart.zip
```

2. Change to the directory that contains the sample code:

```shell
cd endpoints-quickstart
```

#### Deploying the Endpoints configuration
To publish a REST API to Endpoints, an OpenAPI configuration file that describes the API is required. The lab's sample API comes with a pre-configured OpenAPI file called `openapi.yaml`.

Endpoints uses Google `Service Management`, an infrastructure service of Google Cloud, to create and manage APIs and services. To use Endpoints to manage an API, you deploy the API's OpenAPI configuration to Service Management.

To deploy the Endpoints configuration...

1. In the `endpoints-qwikstart` directory, enter the following:

```shell
cd scripts
```

2. Run the following script, which is included in the sample:

```shell
./deploy_api.sh
```

Cloud Endpoints uses the `host` field in the OpenAPI configuration file to identify the service. The `deploy_api.sh` script sets the ID of your Cloud project as part of the name configured in the `host` field. (When you prepare an OpenAPI configuration file for your own service, you will need to do this manually.)

The script then deploys the OpenAPI configuration to Service Management using the command: `gcloud endpoints services deploy openapi.yaml`

As it is creating and configuring the service, Service Management outputs some information to the console. You can safely ignore the warnings about the paths in `openapi.yaml` not requiring an API key.

#### Deploying the API backend
So far you have deployed the OpenAPI configuration to Service Management, but you have not yet deployed the code that will serve the API backend. The `deploy_app.sh` script included in the lab sample creates an App Engine flexible environment to host the API backend, and then the script deploys the API to App Engine.

- To deploy the API backend, make sure you are in the `endpoints-quickstart/scripts` directory. Then, run the following script:

```shell
./deploy_app.sh
```

The script runs the following command to create an App Engine flexible environment in the us-central region: `gcloud app create --region="$REGION"`

**Note:** If you get an `ERROR: NOT_FOUND: Unable to retrieve P4SA: from GAIA` message, rerun the `deploy_app.sh` script.

The script goes on to run the `gcloud app deploy` command to deploy the sample API to App Engine.

#### Sending requests to the API
1. After deploying the sample API, you can send requests to it by running the following script:

```shell
./query_api.sh
```

The script echoes the `curl` command that it uses to send a request to the API, and then displays the result.

The API expects one query parameter, `iataCode`, that is set to a valid IATA airport code such as SEA or JFK.

2. To test, run this example in Cloud Shell:

```shell
./query_api.sh JFK
```

#### Tracking API activity
With APIs deployed with Cloud Endpoints, you can monitor critical operations metrics in the Cloud Console and gain insight into your users and usage with Cloud Logging:

1. Run this traffic generation script in Cloud Shell to populate the graphs and logs:

```shell
./generate_traffic.sh
```

2. In the Console, go to **Navigation menu > Endpoints > Services** and click **Airport Codes** service to look at the activity graphs for your service. It may take a few moments for the requests to be reflected in the graphs. You can do this while you wait for data to be displayed:

	- If the Permissions side panel is not open, click **Show Permissions Panel**. The Permissions panel allows you to control who has access to your API and the level of access.
	- Click the **Deployment history** tab. This tab displays a history of your API deployments, including the deployment time and who deployed the change.
	- Click the **Overview** tab. Here you'll see the traffic coming in. After the traffic generation script has been running for a minute, scroll down to see the three lines on the **Total latency** graph (50th, 95th, and 99th percentiles). This data provides a quick estimate of response times.
	
3. At the bottom of the Endpoints graphs, under Method, click the **View logs** link for GET/airportName. The Logs Viewer page displays the request logs for the API.

#### Add a quota to the API
**Note:** This is a beta release of Quotas. This feature might be changed in backward-incompatible ways and is not subject to any SLA or deprecation policy.

Cloud Endpoints lets you set quotas so you can control the rate at which applications can call your API. Quotas can be used to protect your API from excessive usage by a single client.

1. Deploy the Endpoints configuration that has a quota:

```shell
./deploy_api.sh ../openapi_with_ratelimit.yaml
```

2. Redeploy your app to use the new Endpoints configuration (this may take a few minutes):

```shell
./deploy_app.sh
```

3. In the Console, navigate to **Navigation menu** > **APIs & Services** > **Credentials**.
4. Click **Create credentials** and choose **API key**. A new API key is displayed on the screen.
5. Click the **Copy to clipboard** icon to copy it to your clipboard.
6. In Cloud Shell, type the following. Replace YOUR-API-KEY with the API key you just created:
7. Send your API a request using the API key variable you just created:

```shell
./query_api_with_key.sh $API_KEY
```

8. The API now has a limit of 5 requests per second. Run the following command to send traffic to the API and trigger the quota limit:

```shell
./generate_traffic_with_key.sh $API_KEY
```

9. After running the script for 5-10 seconds, enter CTRL+C in Cloud Shell to stop the script.
10. Send another authenticated request to the API:

```shell
./query_api_with_key.sh $API_KEY
```

### Apigee Edge
Another Google Cloud platform available for developing and managing API proxies is Apigee API Management.

Unlike Cloud Endpoints, Apigee API Management has a specific focus on business problems, like rate limiting, quotas, and analytics.

In fact, many Apigee API Management users provide a software service to other companies.

Backend services for Apigee API Management don't have to be in Google Cloud, and as a result, engineers also often use it to take apart legacy applications.

So, instead of replacing a large, important application in one move, they can use Apigee API Management to peel off its services individually.

This allows them to stand up microservices to implement each in turn, until the legacy application can finally be retired.

### Pub/Sub
Now let’s explore Pub/Sub, a Google Cloud asynchronous messaging service and API that supports distributed message-oriented architectures at scale.

One of the early stages in a data pipeline is data ingestion, which is where large amounts of streaming data are received.

Data, however, may not always come from a single, structured database. Instead, the data might stream from a thousand, or even a million, different events that are all happening asynchronously. A common example of this is data from IoT, or Internet of Things, applications.

These IoT devices present new challenges to data ingestion, which can be summarized in four points:

1. The first is that data can be streamed from many different methods and devices, many of which might not talk to each other and might be sending bad or delayed data.
2. The second is that it can be hard to distribute event messages to the right subscribers. Event messages are notifications. A method is needed to collect the streaming messages that come from IoT sensors and broadcast them to the subscribers as needed.
3. The third is that data can arrive quickly and at high volumes. Services must be able to support this.
4. And the fourth challenge is ensuring that services are reliable and secure, and perform as expected.

The name Pub/Sub is short for Publisher/Subscriber, or publish messages to subscribers.

Pub/Sub is a distributed messaging service that can receive messages from various device streams such as gaming events, IoT devices, and application streams.

Pub/Sub ensures at-least-once delivery of received messages to subscribing applications, with no provisioning required. Pub/Sub’s APIs are open, the service is global by default, and it offers end-to-end encryption.

Let’s explore the end-to-end Pub/Sub architecture.

- Upstream source data comes in from devices all over the globe and is ingested into Pub/Sub, which is the first point of contact within the system. Pub/Sub reads, stores, and broadcasts to any subscribers of this data topic that new messages are available.
- As a subscriber of Pub/Sub, Dataflow can ingest and transform those messages in an elastic streaming pipeline and output the results into an analytics data warehouse like BigQuery.
- Finally, you can connect a data visualization tool, like Looker or Looker Studio, to visualize and monitor the results of a pipeline, or an AI or ML tool such as Vertex AI to explore the data to uncover business insights or help with predictions.

A central element of Pub/Sub is the topic. A topic is a named resource to which messages are sent by publishers. You can think of a topic like a radio antenna. Whether your radio is playing music or it’s turned off, the antenna itself is always there. If music is being broadcast on a frequency that nobody’s listening to, the stream of music still exists. Similarly, a publisher can send data to a topic that has no subscriber to receive it.

Or a subscriber can be waiting for data from a topic that isn’t getting data sent to it, like listening to static from a bad radio frequency. Or you could have a fully operational pipeline where the publisher is sending data to a topic that an application is subscribed to. That means there can be zero, one, or more publishers, and zero, one or more subscribers related to a topic. And they’re completely decoupled, so they’re free to break without affecting their counterparts.

Pub/Sub is a good solution to buffer changes for lightly coupled architectures, like this one, that have many different sources and sinks.

Pub/Sub supports many different inputs and outputs, and you can even publish a Pub/Sub event from one topic to another.

The next task is to get these messages reliably into our data warehouse, and we’ll need a pipeline that can match Pub/Sub’s scale and elasticity to do it.

### Lab - Google Cloud Pub/Sub: Python

#### Overview
The Google Cloud Pub/Sub service allows applications to exchange messages reliably, quickly, and asynchronously. To accomplish this, a data producer publishes messages to a Cloud Pub/Sub topic. A subscriber client then creates a subscription to that topic and consumes messages from the subscription. Cloud Pub/Sub persists messages that could not be delivered reliably for up to seven days.

In this lab, you will learn how to get started publishing messages with Cloud Pub/Sub using the Python client library.

#### Create a virtual environment
Python virtual environments are used to isolate package installation from the system.

1. Install the `virtualenv` environment:

```shell
sudo apt-get install -y virtualenv
```

2. Build the virtual environment:

```shell
python3 -m venv venv
```

3. Activate the virtual environment.

```shell
source venv/bin/activate
```

#### Install the client library
1. Run the following to install the client library:

```shell
pip install --upgrade google-cloud-pubsub
```

2. Get the sample code by cloning a GitHub repository:

```shell
git clone https://github.com/googleapis/python-pubsub.git
```

3. Navigate to the directory:

```shell
cd python-pubsub/samples/snippets
```

#### Pub/Sub - the Basics
Google Cloud Pub/Sub is an asynchronous global messaging service. There are three terms in Pub/Sub that appear often: _topics_, _publishing_, and _subscribing_.

A topic is a shared string that allows applications to connect with one another through a common thread.

Publishers push (or publish) a message to a Cloud Pub/Sub topic. Subscribers will then make a _subscription_ to that thread, where they will either pull messages from the topic or configure webhooks for push subscriptions. Every subscriber must acknowledge each message within a configurable window of time.

In sum, a publisher creates and sends messages to a topic and a subscriber creates a subscription to a topic to receive messages from it.

##### Pub/Sub in Google CLoud
Pub/Sub comes preinstalled in the Cloud Shell, so there are no installations or configurations required to get started with this service. In this lab you use Python to create the topic, subscriber, and then view the message. You use a gcloud command to publish the message to the topic.

#### Create a topic
To publish data to Cloud Pub/Sub you create a topic and then configure a publisher to the topic.

1. 1. In Cloud Shell, your Project ID should automatically be stored in the environment variable `GOOGLE_CLOUD_PROJECT`:

```shell
echo $GOOGLE_CLOUD_PROJECT
```

2. Ensure the output is the same as the Project ID in your CONNECTION DETAILS.

`publisher.py` is a script that demonstrates how to perform basic operations on topics with the Cloud Pub/Sub API. View the content of publisher script:

```shell
cat publisher.py
```

**Note:** Alternatively, you can use the shell editors that are installed on Cloud Shell, such as nano or vim or use the Cloud Shell code editor to view `python-pubsub/samples/snippets/publisher.py`.

3. For information about the publisher script:

```shell
python publisher.py -h
```

4. Run the publisher script to create Pub/Sub Topic:

```shell
python publisher.py $GOOGLE_CLOUD_PROJECT create MyTopic
```

5. This command returns a list of all Pub/Sub topics in a given project:

```shell
python publisher.py $GOOGLE_CLOUD_PROJECT list
```

You can also view the topic you just made in the Cloud Console.

6. Navigate to **Navigation menu** > **Pub/Sub** > **Topics**.

#### Create a subscription
1. Create a Pub/Sub subscription for topic with `subscriber.py` script:

```shell
python subscriber.py $GOOGLE_CLOUD_PROJECT create MyTopic MySub
```

2. This command returns a list of subscribers in given project:

```shell
python subscriber.py $GOOGLE_CLOUD_PROJECT list-in-project
```

3. Check out the subscription you just made in the console. In the left pane, click **Subscriptions**. You should see the subscription name and other details.
4. For information about the `subscriber` script:

```shell
python subscriber.py -h
```

#### Publish messages
Now that you've set up `MyTopic` (the topic), a subscription to `MyTopic` (`MySub`), see if you can use gcloud commands to publish a message to `MyTopic`.

1. Publish the message "Hello" to `MyTopic`:

```shell
gcloud pubsub topics publish MyTopic --message "Hello"
```

#### View messages
Now that you've published messages to MyTopic, pull and view the messages using MySub.

1. Use MySub to pull the message from MyTopic:

```shell
python subscriber.py $GOOGLE_CLOUD_PROJECT receive MySub
```

## You can’t secure the cloud, right?

### Security in the cloud
Let's talk about the different fiver layers of protection Google provides to keep customers' data safe: 

- Hardware infrastructure
- Service deployment
- Storage services
- Internet communication
- Operational security

At the hardware infrastructure layer: 

Hardware design and provenance: Both the server boards and the networking equipment in Google data centers are custom designed by Google. Google also designs custom chips, including a hardware security chip that's currently being deployed on both servers and peripherals.

Secure boot stack: Google server machines use various technologies to ensure that they are booting the correct software stack, such as cryptographic signatures over the BIOS, bootloader, kernel, and base operating system image.

Premises security: Google designs and builds its own data centers, which incorporate multiple layers of physical security protections. Access to these data centers is limited to only a small fraction of Google employees. Google also hosts some servers in third-party data centers, where we ensure that there are Google-controlled physical security measures on top of the security layers provided by the data center operator.

At the service deployment layer: 

Encryption of inter-service communication: Google’s infrastructure provides cryptographic privacy and integrity for remote procedure call (“RPC”) data on the network. Google’s services communicate with each other using RPC calls. The infrastructure automatically encrypts all infrastructure RPC traffic which goes between data centers. Google has started to deploy hardware cryptographic accelerators that will allow it to extend this default encryption to all infrastructure RPC traffic inside Google data centers.

User identity: Google’s central identity service, which usually manifests to end users as the Google login page, goes beyond asking for a simple username and password. The service also intelligently challenges users for additional information based on risk factors such as whether they have logged in from the same device or a similar location in the past. Users also have the option of employing secondary factors when signing in, including devices based on the Universal 2nd Factor (U2F) open standard.

At the storage services layer: 

Encryption at rest: Most applications at Google access physical storage (in other words, “file storage”) indirectly by using storage services, and encryption (using centrally managed keys) is applied at the layer of these storage services. Google also enables hardware encryption support in hard drives and SSDs.

At the internet communication layer: 

Google Front End (GFE): Google services that want to make themselves available on the internet register themselves with an infrastructure service called the Google Front End, which ensures that all TLS connections are ended using a public-private key pair and an X.509 certificate from a Certified Authority (CA), and follows best practices such as supporting perfect forward secrecy. The GFE also applies protections against Denial of Service attacks.

Denial of Service (DoS) protection: The sheer scale of its infrastructure enables Google to simply absorb many DoS attacks. Google also has multi-tier, multi-layer DoS protections that further reduce the risk of any DoS impact on a service running behind a GFE.

Finally, at Google’s operational security layer: 

Intrusion detection: Rules and machine intelligence give Google’s operational security teams warnings of possible incidents. Google conducts Red Team exercises to measure and improve the effectiveness of its detection and response mechanisms.

Reducing insider risk: Google aggressively limits and actively monitors the activities of employees who have been granted administrative access to the infrastructure.

Employee U2F use: To guard against phishing attacks against Google employees, employee accounts require use of U2F-compatible security keys.

Software development practices: Google employs central source control and requires two-party review of new code. Google also provides its developers with libraries that prevent them from introducing certain classes of security bugs. Google also runs a Vulnerability Rewards Program where we pay anyone who can discover and inform us of bugs in our infrastructure or applications.

### The shared security model
Security responsibilities are shared between the customer and Google Cloud.

When a customer deploys an application to their on-premises infrastructure, they are responsible for the security of the entire stack: from the physical security of the hardware and the premises in which they are housed, through to the encryption of the data on disk, the integrity of the network, all the way up to securing the content stored in those applications.

But when they move an application to Google Cloud, Google handles many of the lower layers of security, like the physical security, disk encryption, and network integrity. The upper layers of the security stack, including the securing of data, remain the customer’s responsibility.

Google provides tools like the resource hierarchy and IAM to help them define and implement policies, but ultimately this part is their responsibility.

Data access is usually the customer’s responsibility. They control who or what has access to their data. Google Cloud provides tools that help them control this access, such as Identity and Access Management, but they must be properly configured to protect your data.

### Encryption options
Several encryption options are available on Google Cloud. These range from simple but with limited control, to greater control flexibility but with more complexity.

The simplest option is Google Cloud default encryption, followed by customer-managed encryption keys (CMEK), and the option that provides the most control: customer-supplied encryption keys (CSEK).

A fourth option is to encrypt your data locally before you store it in the cloud. This is often called client-side encryption.

Google Cloud will encrypt data in transit and at rest by default.

Data in transit is encrypted by using Transport Layer Security (TLS).

Data encrypted at rest is done with AES 256-bit keys.

The encryption happens automatically.

With customer-managed encryption keys, you manage your encryption keys that protect data on Google Cloud.

Cloud Key Management Service, or Cloud KMS, automates and simplifies the generation and management of encryption keys. 

The keys are managed by the customer and never leave the cloud.

Cloud KMS supports encryption, decryption, signing, and verification of data.

It supports both symmetric and asymmetric cryptographic keys and various popular algorithms.

Cloud KMS lets you both rotate keys manually and automate the rotation of keys on a time-based interval.

Cloud KMS also supports both symmetric keys and asymmetric keys for encryption and signing.

Customer-supplied encryption keys give users more control over their keys, but with greater management complexity.
  
With CSEK, users use their own AES 256-bit encryption keys. They are responsible for generating these keys.

Users are responsible for storing the keys and providing them as part of Google Cloud API calls.

Google Cloud will use the provided key to encrypt the data before saving it.

Google guarantees that the key only exists in-memory and is discarded after use.

### Authentication and authorization with IAM
When an organization node contains lots of folders, projects, and resources, it’s likely that a workforce might need to restrict access. To help with this task, administrators can use Identity and Access Management, or IAM. With IAM, administrators can apply policies that define who can do what on which resources.

The “who” part of an IAM policy can be a Google Account, a Google group, a service account, or Cloud Identity domain.

The “can do what” part of an IAM policy is defined by a role. An IAM role is a collection of permissions. For example, to manage virtual machine instances in a project, you need to create, delete, start, stop, and change virtual machines. So these permissions are grouped into a role to make them easier to understand and manage.

When a user, group, or service account is given a role on a specific element of the resource hierarchy, the resulting policy applies to the chosen element and to all the elements below it in the hierarchy.

When new Google Cloud customers start using the platform, it’s common to log into the Google Cloud console with a Gmail account, and then use Groups to collaborate with teammates who are in similar roles. Although this approach is easy to start with, it can be challenging later because the team’s identities are not centrally managed. This can be problematic if someone leaves the organization. With this setup, it’s not easy to immediately remove a user’s access to the team’s cloud resources.

With a tool called Cloud Identity, organizations can define policies and manage their users and groups by using the Google Admin console.

Admins can log in and manage Google Cloud resources by using the same usernames and passwords they already use in existing Active Directory or LDAP systems.

With Cloud Identity, when someone leaves an organization, an administrator can use the Google Admin console to disable their account and remove them from groups.

Cloud Identity is available in a free edition, and a premium edition that provides capabilities to manage mobile devices.

If you’re a Google Cloud and a Google Workspace customer, this functionality is already available to you in the Google Admin console.

There are three kinds of roles in IAM: basic, predefined, and custom.

The first role type is basic. Basic roles are broad in scope. When applied to a Google Cloud project, they affect all resources in that project. Basic roles include owner, editor, viewer, and billing administrator.

Project viewers can examine resources, but can’t modify them. Project editors can examine and modify a resource. And project owners can also examine and modify a resource. In addition, project owners can manage the associate roles and permissions, and set up billing.

Note: If several people are working together on a project that contains sensitive data, basic roles are probably too broad.

Fortunately, IAM provides other ways to assign permissions that are more specifically tailored to meet the needs of typical job roles. This brings us to the second type of role: predefined roles.

Specific Google Cloud services offer sets of predefined roles, and they even define where those roles can be applied.

But what if you need to assign a role that has even more specific permissions? You’d use a custom role.

Before you start creating custom roles, please note two important details. First, you must manage the permissions that comprise the custom role you’ve created. Because of this, some companies decide to stick with the predefined roles.

And second, custom roles can only be applied to either project or organization level. They can’t be applied to the folder level.

Service accounts are named with an email address, but instead of passwords, they use cryptographic keys to access resources.

So, if a service account has been granted Compute Engine’s Instance Admin role, this would allow an application that runs in a VM with that service account to create, modify, and delete other VMs.

Service accounts must be managed.

In addition to being an identity (a user), a service account is also a resource! So it can have IAM policies of its own attached to it.

### Lab - User Authentication: Identity-Aware Proxy
Identity-Aware Proxy, or IAP, is a resource that can be used to set up authentication to https-based applications without the use of VPNs.

IAP lets you establish a central authorization layer for applications over TLS, so you can use an application-level access control model instead of relying on network-level firewalls.

Only users and groups can access applications and resources protected by IAP through the proxy with the correct IAM role. The proxy provides a layer of protection between the outside world and an internal service.

When you grant a user access to an application or resource by IAP, they’re subject to the granular access controls implemented by the product in use, without requiring a VPN.

IAP performs authentication and authorization checks when a user tries to access a IAP-secured resource.

IAP secures authentication and authorization of external requests through TLS.

IAP doesn't protect against activities inside your VM, such as if someone uses SSH to access the VM. 

IAP also doesn’t protect against activities within a project, such as VM-to-VM communication within your project over the local network.

#### Overview
In this lab, you build a minimal web application with Google App Engine, then explore various ways to use Identity-Aware Proxy (IAP) to restrict access to the application and provide user identity information to it. Your app will:

- Display a welcome page
- Access user identity information provided by IAP
- Use cryptographic verification to prevent spoofing of user identity information

#### Introduction
Authenticating users of your web app is often necessary, and usually requires special programming in your app. For Google Cloud apps you can hand those responsibilities off to the [Identity-Aware Proxy](https://cloud.google.com/iap/) service. If you only need to restrict access to selected users there are no changes necessary to the application. Should the application need to know the user's identity (such as for keeping user preferences server-side) Identity-Aware Proxy can provide that with minimal application code.

Identity-Aware Proxy (IAP) is a Google Cloud service that intercepts web requests sent to your application, authenticates the user making the request using the Google Identity Service, and only lets the requests through if they come from a user you authorize. In addition, it can modify the request headers to include information about the authenticated user.

#### Deploy the application and protect it with IAP

##### Deploy to App Engine
1. Deploy the app to the App Engine Standard environment for Python.

```shell
gcloud app deploy
```

2. Select a region near to you that says it "supports standard".

**Note:** If you get a **Gaia propagation** related error message, re-run the `gcloud app deploy` command.

4. Enter that command:

```shell
gcloud app browse
```

##### Restrict access with IAP
1. In the cloud console window, click the **Navigation menu** ![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D) > **Security** > **Identity-Aware Proxy**.
2. Click **ENABLE API**.
3. Click **GO TO IDENTITY-AWARE PROXY**.
4. Click **CONFIGURE CONSENT SCREEN**.
5. Select **Internal** under User Type and click **Create**.
6. Fill in the required blanks with appropriate values:

|**Field**|**Value**|
|---|---|
| Application home page | _The URL you used to view your app. You can find this again by running the gcloud app browse command in cloud shell again._ 
| Authorized domains | _Click **+ ADD DOMAIN**The hostname portion of the application's URL, e.g. iap-example-999999.appspot.com. You can see this in the address bar of the Hello World web page you previously opened. Do not include the starting_ `https://` _or trailing_ `/` _from that URL._
| Developer Contact Information | _Enter at least one email_

7. Click **SAVE AND CONTINUE**.
8. For **Scopes**, click **SAVE AND CONTINUE**.
9. For **Summary**, click **BACK TO DASHBOARD**.

You might be prompted to create credentials. You do not need to create credentials for this lab, so you can simply close this browser tab.

10. In Cloud Shell, run this command to disable the Flex API:

```shell
gcloud services disable appengineflex.googleapis.com
```

**Note:** App Engine has its standard and flexible environments which are optimized for different application architectures. Currently, when enabling IAP for App Engine, if the Flex API is enabled, Google Cloud will look for a Flex Service Account. Your lab project comes with a multitude of APIs already enabled for the purpose of convenience. However, this creates a unique situation where the Flex API is enabled without a Service Account created.

11. Return to the Identity-Aware Proxy page and refresh it. You should now see a list of resources you can protect.

Click the toggle button in the IAP column in the **App Engine app** row to turn **IAP** on.

12. The domain will be protected by IAP. Click **TURN ON**.

##### Test that IAP is turned on
1. Open a browser tab and navigate to the URL for your app. A Sign in with Google screen opens and requires you to log in to access the app.
2. Sign in with the account you used to log into the console. You will see a screen denying you access.

	You have successfully protected your app with IAP, but you have not yet told IAP which accounts to allow through.

3. Return to the Identity-Aware Proxy page of the console, select the checkbox next to **App Engine app**, and see the App Engine sidebar to the right.

	Each email address (or Google Group address, or Workspace domain name) that should be allowed access needs to be added as a Member.

4. Click **ADD PRINCIPAL**.
5. Enter your **Student** email address.
6. Then, pick the **Cloud IAP** > **IAP-Secured Web App User** role to assign to that address.

	You may enter more addresses or Workspace domains in the same way.

7. Click **SAVE**.

##### Test access
Navigate back to your app and reload the page. You should now see your web app, since you already logged in with a user you authorized.

If you still see the "You don't have access" page, IAP did not recheck your authorization. In that case, do the following steps:

1. Open your web browser to the home page address with `/_gcp_iap/clear_login_cookie` added to the end of the URL, as in `https://iap-example-999999.appspot.com/_gcp_iap/clear_login_cookie`
2. You will see a new Sign in with Google screen, with your account already showing. Do not click the account. Instead, click Use another account, and re-enter your credentials.

**Note:** It takes a minute for the role change to take effect. If the page still shows the "You don't have access" message after following the previous steps, wait a minute and try refreshing the page.

#### Access user identity information
Once an app is protected with IAP, it can use the identity information that IAP provides in the web request headers it passes through. In this step, the application will get the logged-in user's email address and a persistent unique user ID assigned by the Google Identity Service to that user.

##### Examine the application files
The program has been changed to retrieve the user information that IAP provides in request headers, and the template now displays that data.

There are two lines in `main.py` that get the IAP-provided identity data:

```python
user_email = request.headers.get('X-Goog-Authenticated-User-Email')
user_id = request.headers.get('X-Goog-Authenticated-User-ID')
```

The **X-Goog-Authenticated-User-** headers are provided by IAP, and the names are case-insensitive, so they could be given in all lower or all upper case if preferred.

##### Turn off IAP
What happens to this app if IAP is disabled, or somehow bypassed (such as by other applications running in your same cloud project)? Turn off IAP to see.

1. In the cloud console window, click **Navigation menu** > **Security** > **Identity-Aware Proxy**.
2. Click the **IAP** toggle switch next to App Engine app to turn **IAP** off. Click **TURN OFF**.

	You will be warned that this will allow all users to access the app.

3. Refresh the application web page. You should see the same page, but without any user information:

	Since the application is now unprotected, a user could send a web request that appeared to have passed through IAP.

	There is no way for the application to know that IAP has been disabled or bypassed. For cases where that is a potential risk, Cryptographic Verification shows a solution.

#### Use Cryptographic Verification
If there is a risk of IAP being turned off or bypassed, your app can check to make sure the identity information it receives is valid. This uses a third web request header added by IAP, called `X-Goog-IAP-JWT-Assertion`. The value of the header is a cryptographically signed object that also contains the user identity data. Your application can verify the digital signature and use the data provided in this object to be certain that it was provided by IAP without alteration.

Digital signature verification requires several extra steps, such as retrieving the latest set of Google public keys. You can decide whether your application needs these extra steps based on the risk that someone might be able to turn off or bypass IAP, and the sensitivity of the application.

##### Examine the application files
- The new functionality is primarily in the `user()` function:

```python
def user():
    assertion = request.headers.get('X-Goog-IAP-JWT-Assertion')
    if assertion is None:
        return None, None
    info = jwt.decode(
        assertion,
        keys(),
        algorithms=['ES256'],
        audience=audience()
    )
    return info['email'], info['sub']
```

The `assertion` is the cryptographically signed data provided in the specified request header. The code uses a library to validate and decode that data. Validation uses the public keys that Google provides for checking data it signs, and knowing the audience that the data was prepared for (essentially, the Google Cloud project that is being protected). Helper functions `keys()` and `audience()` gather and return those values.

The signed object has two pieces of data we need: the verified email address, and the unique ID value (provided in the `sub`, for subscriber, standard field).

##### Test the Cryptographic Verification
If IAP is turned off or bypassed, the verified data would either be missing, or invalid, since it cannot have a valid signature unless it was created by the holder of Google's private keys.

### IAM authorization best practices
For starters, it’s a smart decision to leverage and understand the resource hierarchy.

Specifically: Use projects to group resources that share the same trust boundary.

Check the policy granted on each resource and ensure to recognize the inheritance.
  
Because of inheritance, use the principle of least privilege when you grant roles.

Finally, audit policies by using Cloud Audit Logs and audit the memberships of groups that are used in policies.

Next, we recommend granting roles to groups instead of individuals. This lets you update group memberships instead of changing an IAM policy. If you do this, make sure to audit memberships of groups used in policies and control the ownership of the Google group used in IAM policies.

You can also use multiple groups to get better control.

Some of those members also need a read_write role, which allows them to read and write to a Cloud Storage bucket, but others need the read_only role. Adding and removing individuals from all three groups controls their total access. Therefore, groups are associated with job roles and can exist for role assignment.

Here are some best practices to consider when you use service accounts.

Use caution when you grant the Service Account Users role, because it provides access to all the resources for which the service account has access.

Also, when you create a service account, give it a display name that clearly identifies its purpose.

Ideally use an established naming convention for your organization.

And for service account keys, establish key rotation policies and methods.

### Lab - Cloud IAM

#### Overview
Google Cloud's Identity and Access Management (IAM) service lets you create and manage permissions for Google Cloud resources. Cloud IAM unifies access control for Google Cloud services into a single system and provides a consistent set of operations.

#### The IAM console and project level roles
1. Return to the **Username 1** Cloud Console page.
2. Select **Navigation menu** > **IAM & Admin** > **IAM**. You are now in the "IAM & Admin" console.
3. Click **+GRANT ACCESS** button at the top of the page
4. Scroll down to **Basic** and mouse over.

There are four roles:

- Browser
- Editor
- Owner
- Viewer

These are _primitive roles_ in Google Cloud. Primitive roles set project-level permissions and unless otherwise specified, they control access and management to all Google Cloud services.

|   |   |
|---|---|
|**Role Name**|**Permissions**|
|roles/viewer|Permissions for read-only actions that do not affect state, such as viewing (but not modifying) existing resources or data.|
|roles/editor|All viewer permissions, plus permissions for actions that modify state, such as changing existing resources.|
|roles/owner|All editor permissions and permissions for the following actions:<br><br>- Manage roles and permissions for a project and all resources within the project.<br>- Set up billing for a project.|
|roles/browser|Read access to browse the hierarchy for a project, including the folder, organization, and Cloud IAM policy. This role doesn't include permission to view resources in the project.|

#### Remove project access
1. Select **Navigation menu** > **IAM & Admin** > **IAM**. Then click the pencil icon inline and to the right of **Username 2**.
2. Remove Project Viewer access for **Username 2** by clicking the trashcan icon next to the role name. Then click **SAVE**.

#### Add Storage permissions
1. In the Console, select **Navigation menu** > **IAM & Admin** > **IAM**.
2. Click **+GRANT ACCESS** button and paste the **Username 2** name into the **New principals** field.
3. In the **Select a role** field, select **Cloud Storage** > **Storage Object Viewer** from the drop-down menu.
4. Click **SAVE**.

## Lab - Cloud Storage: Cloud Console

### Overview
Cloud Storage allows world-wide storage and retrieval of any amount of data at any time. You can use Cloud Storage for a range of scenarios including serving website content, storing data for archival and disaster recovery, or distributing large data objects to users via direct download.

### Create a bucket
_Buckets_ are the basic containers that hold your data in Cloud Storage.

To create a bucket:

1. In the Cloud Console, go to **Navigation menu** > **Cloud Storage** > **Buckets**.
2. Click **+ Create**:
3. Enter your bucket information and click **Continue** to complete each step:
	- **Name your bucket:** Enter a unique name for your bucket.
	- Choose **Region** for **Location type** and `<filled in at lab start>` for **Location**.
	- Choose **Standard** for **default storage class**.
	- Choose **Uniform** for **Access control** and **uncheck** _Enforce public access prevention on this bucket_ to turn it off.
4. Leave the rest of the fields as their default values and click **Create**.

That's it — you've just created a Cloud Storage bucket!

### Upload an object into the bucket
To upload the image above into your new bucket:

1. Right-click on the image above and download it to your computer. Save the image as **kitten.png**, renaming it on download.
2. In the Cloud Storage browser page, click the name of the bucket that you created.
3. In the **Objects** tab, click **Upload files**.
4. In the file dialog, go to the file that you downloaded and select it.
5. Ensure the file is named **kitten.png**. If it is not, click the **three dot** icon for your file, select **Rename** from the dropdown, and rename the file to **kitten.png**.

### Share a bucket publicly
To allow public access to the bucket and create a publicly accessible URL for the image:

1. Click the **Permissions** tab above the list of files.
2. Ensure the view is set to **Principals**. Click **Grant Access** to view the **Add principals** pane.
3. In the **New principals** box, enter _allUsers_.
4. In the **Select a role** drop-down, select **Cloud Storage** > **Storage Object Viewer**.
5. Click **Save**.
6. In the **Are you sure you want to make this resource public?** window, click **Allow public access**.

### Create folders
1. In the **Objects** tab, click **Create folder**.
2. Enter **folder1** for **Name** and click **Create**.
3. Click **Upload files**.

### Delete a folder
1. Click the arrow next to **Bucket details** to return to the buckets level.
2. Select the bucket.
3. Click on the **Delete** button.
4. In the window that opens, type `DELETE` to confirm the deletion of the folder.
5. Click **Delete** to permanently delete the folder and all objects and subfolders in it.

## Lab - Cloud Monitoring

### Overview
Cloud Monitoring provides visibility into the performance, uptime, and overall health of cloud-powered applications. Cloud Monitoring collects metrics, events, and metadata from Google Cloud, Amazon Web Services, hosted uptime probes, application instrumentation, and a variety of common application components including Cassandra, Nginx, Apache Web Server, Elasticsearch, and many others. Cloud Monitoring ingests that data and generates insights via dashboards, charts, and alerts. Cloud Monitoring alerting helps you collaborate by integrating with Slack, PagerDuty, HipChat, Campfire, and more.

### Add Apache2 HTTP Server to your instance

#### Create a Monitoring Metrics Scope
Set up a Monitoring Metrics Scope that's tied to your Google Cloud Project. The following steps create a new account that has a free trial of Monitoring.

- In the Cloud Console, click **Navigation menu** ![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D) > **Monitoring**.

When the Monitoring **Overview** page opens, your metrics scope project is ready.

#### Install the Monitoring and Logging agents
Agents collect data and then send or stream info to Cloud Monitoring in the Cloud Console.

The _Cloud Monitoring agent_ is a collected-based daemon that gathers system and application metrics from virtual machine instances and sends them to Monitoring. By default, the Monitoring agent collects disk, CPU, network, and process metrics. Configuring the Monitoring agent allows third-party applications to get the full list of agent metrics. On the Google Cloud, Operations website, see [Cloud Monitoring Documentation](https://cloud.google.com/monitoring/docs#) for more information.

**Note:** It is best practice to run the Cloud Logging agent on all your VM instances.

1. Run the Monitoring agent install script command in the SSH terminal of your VM instance to install the Cloud Monitoring agent:

```shell
curl -sSO https://dl.google.com/cloudagents/add-google-cloud-ops-agent-repo.sh
```

```shell
sudo bash add-google-cloud-ops-agent-repo.sh --also-install
```

2. When asked if you want to continue, press **Y**.
3. Run the Logging agent install script command in the SSH terminal of your VM instance to install the Cloud Logging agent:

```shell
sudo systemctl status google-cloud-ops-agent"*"
```

Press **q** to exit the status.

```shell
sudo apt-get update
```

### Create an uptime check
Uptime checks verify that a resource is always accessible.

1. In the Cloud Console, in the left menu, click **Uptime checks**, and then click **Create Uptime Check**.
2. For **Protocol**, select **HTTP**.
3. For **Resource Type**, select **Instance**.
4. For **Instance**, select **lamp-1-vm**.
5. For **Check Frequency**, select **1 minute**.
6. Click **Continue**.
7. In Response Validation, accept the defaults and then click **Continue**.
8. In Alert & Notification, accept the defaults, and then click **Continue**.
9. For Title, type **Lamp Uptime Check**.
10. Click **Test** to verify that your uptime check can connect to the resource.

    When you see a green check mark everything can connect.

11. Click **Create**.

    The uptime check you configured takes a while for it to become active. Continue with the lab, you'll check for results later. While you wait, create an alerting policy for a different resource.

### Create an alerting policy
Use Cloud Monitoring to create one or more alerting policies.

1. In the left menu, click **Alerting**, and then click **+Create Policy**.
2. Click on **Select a metric** dropdown. Disable the **Show only active resources & metrics**.
3. Type **Network traffic** in filter by resource and metric name and click on **VM instance > Interface**. Select `Network traffic` (agent.googleapis.com/interface/traffic) and click **Apply**. Leave all other fields at the default value.
4. Click **Next**.
5. Set the **Threshold position** to `Above threshold`, **Threshold value** to `500` and **Advanced Options > Retest window** to `1 min`. Click **Next**.
6. Click on the drop down arrow next to **Notification Channels**, then click on **Manage Notification Channels**.

	A **Notification channels** page will open in a new tab.

7. Scroll down the page and click on **ADD NEW** for **Email**.
8. In the **Create Email Channel** dialog box, enter your personal email address in the **Email Address** field and a **Display name**.
9. Click on **Save**.
10. Go back to the previous **Create alerting policy** tab.
11. Click on **Notification Channels** again, then click on the **Refresh icon** to get the display name you mentioned in the previous step.
12. Click on **Notification Channels** again if necessary, select your **Display name** and click **OK**.
13. Add a message in documentation, which will be included in the emailed alert.
14. Mention the **Alert name** as `Inbound Traffic Alert`.
15. Click **Next**.
16. Review the alert and click **Create Policy**.

You've created an alert! While you wait for the system to trigger an alert, create a dashboard and chart, and then check out Cloud Logging.

### Create a dashboard and chart
You can display the metrics collected by Cloud Monitoring in your own charts and dashboards.

1. In the left menu select **Dashboards**, and then **+Create Dashboard**.
2. Name the dashboard `Cloud Monitoring LAMP Qwik Start Dashboard`.

#### Add the first chart
1. Click the **Line** option in the Chart library.
2. Name the chart title **CPU Load**.
3. Click on **Resource & Metric** dropdown. Disable the **Show only active resources & metrics**.
4. Type **CPU load (1m)** in filter by resource and metric name and click on **VM instance > Cpu**. Select `CPU load (1m)` and click **Apply**. Leave all other fields at the default value. Refresh the tab to view the graph.

#### Add the second chart
1. Click **+ Add Chart** and select **Line** option in the Chart library.
2. Name this chart **Received Packets**.
3. Click on **Resource & Metric** dropdown. Disable the **Show only active resources & metrics**.
4. Type **Received packets** in filter by resource and metric name and click on **VM instance > Instance**. Select `Received packets` and click **Apply**. Refresh the tab to view the graph.
5. Leave the other fields at their default values. You see the chart data.

### View your logs
Cloud Monitoring and Cloud Logging are closely integrated.

1. Select **Navigation menu** > **Logging** > **Logs Explorer**.
2. Select the logs you want to see, in this case, you select the logs for the lamp-1-vm instance you created at the start of this lab:
    
    - Click on **Resource**.
    - Select **VM Instance** > **lamp-1-vm** in the Resource drop-down menu.
    - Click **Apply**.
    - Leave the other fields with their default values.
    - Click the **Stream logs**.

You see the logs for your VM instance.

### Check the uptime check results and triggered alerts
1. In the Cloud Logging window, select **Navigation menu** > **Monitoring** > **Uptime checks**. This view provides a list of all active uptime checks, and the status of each in different locations.

    You will see Lamp Uptime Check listed. Since you have just restarted your instance, the regions are in a failed status. It may take up to 5 minutes for the regions to become active. Reload your browser window as necessary until the regions are active.

2. Click the name of the uptime check, `Lamp Uptime Check`.

#### Check if alerts have been triggered
1. In the left menu, click **Alerting**.
2. You see incidents and events listed in the Alerting window.
3. Check your email account. You should see Cloud Monitoring Alerts.

## Lab - Cloud Functions: Console

### Overview
A cloud function is a piece of code that runs in response to an event, such as an HTTP request, a message from a messaging service, or a file upload. Cloud events are _things_ that happen in your cloud environment. These might be things like changes to data in a database, files added to a storage system, or a new virtual machine instance being created.

Since cloud functions are event-driven, they only run when something happens. This makes them a good choice for tasks that need to be done quickly or that don't need to be running all the time.

### Create a function
In this step, you're going to create a cloud function using the console.

1. In the console, click the **Navigation menu (![Navigation Menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D))** > **Cloud Functions**.
2. Click **Create function**.
3. In the **Create function** dialog, enter the following values:

|   |   |
|---|---|
|**Field**|**Value**|
|Function name|GCFunction|
|Region|`<filled in at lab start>`|
|Trigger type|Select **HTTP** and click **Save**|
|Memory allocated (In Runtime, Build, Connections and Security Settings)|Keep it default|
|Autoscaling|Set the **Maximum number of instance** to **5** and then click **Next**|

### Deploy the function
1. Still in the **Create function** dialog, in Source code for **Inline editor** use the default `helloWorld` function implementation already provided for index.js.
2. At the bottom, click **Deploy** to deploy the function.
3. After you click **Deploy**, the console redirects to the **Cloud Functions Overview** page.

While the function is being deployed, the icon next to it is a small spinner. When it's deployed, the spinner is a green check mark.

### Test the function
Test the deployed function.

1. In the **Cloud Functions Overview** page, display the menu for your function, and click **Test function**.
2. In the Triggering event field, enter the following text between the brackets `{}` and click **Test the function**.

```
"message":"Hello World!"
```

In the **Output** field, you should see the message `Success: Hello World!`

In the **Logs** field, a status code of **200** indicates success. (It may take a minute for the logs to appear.)

### View logs
View logs from the Cloud Functions Overview page.

1. Click the blue arrow to go back to the **Cloud Functions Overview** page.
2. Display the menu for your function, and click **View logs**.

## Lab - Google Cloud Pub/Sub: Console

### Overview
Google Cloud Pub/Sub is a messaging service for exchanging event data among applications and services. A producer of data publishes messages to a Cloud Pub/Sub topic. A consumer creates a subscription to that topic. Subscribers either pull messages from a subscription or are configured as webhooks for push subscriptions. Every subscriber must acknowledge each message within a configurable window of time.

### Setting up Pub/Sub
You can use the Google Cloud Shell console to perform operations in Google Cloud Pub/Sub.

To use a Pub/Sub, you create a topic to hold data and a subscription to access data published to the topic.

1. Click **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **Pub/Sub** > **Topics**.
2. Click **Create topic**.
3. The topic must have a unique name. For this lab, name your topic `MyTopic`. In the **Create a topic** dialog:

	- For **Topic ID**, type `MyTopic`.
	- Leave other fields at their default value.
	- Click **CREATE**.

### Add a subscription
Now you'll make a subscription to access the topic.

1. Click **Topics** in the left panel to return to the **Topics** page. For the topic you just made click the three dot icon > **Create subscription**.
2. In the **Add subscription to topic** dialog:

	- Type a name for the subscription, such as `MySub`
	- Set the Delivery Type to **Pull**.
	- Leave all other options at the default values.
	- Click **Create**.

### Publish a message to the topic
1. Navigate back to **pub/sub** > **Topics** and open **MyTopics** page.
2. In the Topics details page, click **Messages** tab and then click **Publish Message**.
3. Enter `Hello World` in the **Message** field and click **Publish**.

### View the message
To view the message you'll use the subscription (`MySub`) to pull the message (`Hello World`) from the topic (`MyTopic`).

- Enter the following command in the command line.

```shell
gcloud pubsub subscriptions pull --auto-ack MySub
```

The message appears in the DATA field of the command output.

## Google Cloud Pub/Sub: Command Line

### Pub/Sub topics
Pub/Sub comes preinstalled in the Google Cloud Shell, so there are no installations or configurations required to get started with this service.

1. Run the following command to create a topic called `myTopic`:

```shell
gcloud pubsub topics create myTopic
```

2. To see the three topics you just created, run the following command:

```shell
gcloud pubsub topics list
```

3. Time to clean up. Delete `Test1` and `Test2` by running the following commands:

```shell
gcloud pubsub topics delete Test1
```

### Pub/Sub subscriptions
Now that you're comfortable creating, viewing, and deleting topics, time to work with subscriptions.

1. Run the following command to create a subscription called `mySubscription` to topic `myTopic`:

```shell
gcloud  pubsub subscriptions create --topic myTopic mySubscription
```

2. Run the following command to list the subscriptions to myTopic:

```shell
gcloud pubsub topics list-subscriptions myTopic
```

3. Now delete the `Test1` and `Test2` subscriptions. Run the following commands:

```shell
gcloud pubsub subscriptions delete Test1
```

### Pub/Sub publishing and pulling a single message
Next you'll learn how to publish a message to a Pub/Sub topic.

1. Run the following command to publish the message `"hello"` to the topic you created previously (`myTopic`):

```shell
gcloud pubsub topics publish myTopic --message "Hello"
```

Next, use the `pull` command to get the messages from your topic. The pull command is subscription based, meaning it should work because earlier you set up the subscription `mySubscription` to the topic `myTopic`.

3. Use the following command to pull the messages you just published from the Pub/Sub topic:

```shell
gcloud pubsub subscriptions pull mySubscription --auto-ack
```

What's going on here? You published 4 messages to your topic, but only 1 was outputted.

Now is an important time to note a couple features of the `pull` command that often trip developers up:

- **Using the pull command without any flags will output only one message, even if you are subscribed to a topic that has more held in it.**
- **Once an individual message has been outputted from a particular subscription-based pull command, you cannot access that message again with the pull command.**

### Pub/Sub pulling all messages from subscriptions
1. Add a `flag` to your command so you can output all three messages in one request.

You may have not noticed, but you have actually been using a flag this entire time: the `--auto-ack` part of the `pull` command is a flag that has been formatting your messages into the neat boxes that you see your pulled messages in.

`limit` is another flag that sets an upper limit on the number of messages to pull.

2. Wait a minute to let the topics get created. Run the pull command with the `limit` flag:

```shell
gcloud pubsub subscriptions pull mySubscription --auto-ack --limit=3
```


# Networking & Security in Google Cloud
## It helps to network

### Networking in the cloud
Computers communicate with each other on a network. 

The computers in a single location, like an office, are connected on a local area network (LAN).

Multiple locations can have their LANs connected to a wide area network, or WAN.

Most networks today are connected to the internet, which enables millions of personal computers, servers, smartphones, and other devices to communicate, provide, and consume IT services.

Google’s high-quality private network connects regional locations to more than 100 global network points of presence close to users.

Here’s an example network diagram for an application that bridges an organization's physical data center and Google Cloud. The web client, or end user, performs a Domain Name System lookup, which is served by Cloud DNS.

Content Delivery Networks, or CDNs, are locations within the Google network that are used to cache content closer to the users to improve application performance.

The user requests a page. If the CDN option was selected when Cloud Load Balancing was configured, then the request will go to the closest CDN location, which will serve that page without getting it from the servers if the CDN has the page stored.

For a page that the CDN doesn’t have, it will call Cloud Load Balancing. Cloud Load Balancing will pick an appropriate frontend server to serve the request, and return the page to the user.

In Google Cloud, a "network" is an isolated global resource holding network configuration. Instances are deployed in regional subnetworks, however the policy (firewall, routing, and so on), and access through VPN, are configured at the global network level.

Depending on the content of the page, the frontend Compute Engine server may have to talk to a Compute Engine backend server, which is regularly updated with data feeds from other sites.

The subnetworks are configured so that the frontend subnet cannot talk directly to the data center or colocation facility.

### Virtual Private Clouds (VPCs)
A Virtual Private Cloud, or VPC, is a secure, individual, private cloud-computing model hosted within a public cloud (like Google Cloud!).

On a VPC, customers can run code, store data, host websites, and do anything else they could do in an ordinary private cloud, but this private cloud is hosted remotely by a public cloud provider.

This means that VPCs combine the scalability and convenience of public cloud computing with the data isolation of private cloud computing.

VPC networks connect Google Cloud resources to each other and to the internet.

This includes tasks such as segmenting networks, using firewall rules to restrict access to instances, and creating static routes to forward traffic to specific destinations.

Here's something that tends to surprise many new Google Cloud users: Google VPC networks are global.

They can also have subnets, which is a segmented piece of the larger network, in any Google Cloud region worldwide. Subnets can span the zones that make up a region.

This architecture makes it easy to define network layouts with global scope. Resources can even be in different zones on the same subnet.

The size of a subnet can be increased by expanding the range of IP addresses allocated to it. And doing so doesn’t affect the already configured virtual machines.

For example, let’s take a VPC with one network that currently has one subnet defined in Google Cloud’s us-east1 region. If the VPC has two Compute Engine VMs attached to it, it means they’re neighbors on the same subnet, although they are in different zones! This capability can be used to build solutions that are resilient to disruptions but retain a simple network layout.

Google Cloud offers two types of VPC networks, determined by their subnet creation mode: auto subnet mode and custom subnet mode.

When an auto mode VPC network is created, one subnet from each region is automatically created within it. As new Google Cloud regions become available, new subnets in those regions are automatically added to auto mode VPC networks.

The automatically created subnets use a set of predefined IP ranges and default firewall rules can be applied.

In addition to the automatically created subnets, you can add more subnets manually to auto mode VPC networks, in the regions you choose, by using IP ranges outside a set of predefined IP ranges.

When you expand the IP range in an auto mode VPC network, the broadest prefix you can use is /16. Any prefix broader than /16 would conflict with the primary IP ranges of other automatically created subnets.

Due to its limited flexibility, an auto mode VPC network is better suited to isolated use cases, such as proof of concepts, and testing.

A custom mode network does not automatically create subnets.

This type of network provides you with complete control over its subnets and IP ranges. You decide which subnets to create, in regions you choose, and using IP ranges you specify.

These IP ranges cannot overlap between subnets of the same network.

Custom mode VPC networks are therefore a lot more flexible and are better suited to production environments.

While you can switch a network from auto mode to custom mode, this conversion is one way. Custom mode VPC networks cannot be changed to auto mode VPC networks.

### The basics of public and internal IP addresses
A Virtual Private Cloud (VPC) is composed of subnetworks, or subnets, and each subnet must be configured with a private IP CIDR address.

CIDR stands for Classless Inter-domain Routing. The CIDR range will determine what internal IP addresses will be used by virtual machines in the subnet.

Internal IP addresses are only used for communication within the VPC and cannot be routed to the internet.

Each octet in an IP address is represented by 8 binary bits. So a typical IPV4 address is 32-bits long.

The number at the end of the range determines how many bits will be static or frozen. This number determines how many IP addresses are available with a CIDR address.

The CIDR range determines how many IP addresses are available. A /16 range will provide 65,536 available IP addresses. Every time you add “1” to the last number, the number of available IP addresses is cut in half.
 
Public, or external IP addresses can be ephemeral or reserved. They are assigned from a pool of IP addresses associated with the region.

If you allocate a reserved IP address but don't attach it to a virtual machine, you will be billed for the IP address.

Virtual machines are unaware of their public IP address, which means that if you look at the operating system network configuration, the virtual machine will only display the internal IP address.

Private, or internal IP addresses, however, are allocated to VMs by a Dynamic Host Configuration Protocol (DHCP) service.

The lease for the IPs is renewed every 24 hours.

The name of the virtual machine is the hostname, and the hostname will be associated with the internal IP address through a network-scoped DNS service.

### The Google Cloud network
Google Cloud consists of regions, represented by the markers in blue, together with proposed future regions in white.

A region is a specific geographical location where you can run your resources.

The number on each region represents the zones within that region.

Points of presence, or PoPs, are represented by the dark gray dots. The PoPs are where the Google network is connected to the rest of the internet.

By operating an extensive global network of interconnection points, Google Cloud can bring its traffic closer to its peers, which reduces costs and provides users with a better experience.

Google’s global private network is represented by the blue lines. The network connects regions and PoPs and is composed of hundreds of thousands of miles of fiber optic cable and several submarine cable investments.

The last component that makes up the architecture is Google’s services themselves. https://cloud.google.com/about/locations/

Here are five of Google Cloud’s networking products available to users.

Google Cloud VPC is a comprehensive set of networking capabilities and infrastructure that’s managed by Google.

With Virtual Private Cloud, you can connect your Google Cloud resources in a Virtual Private Cloud and isolate them from each other for purposes of security, compliance, and development versus test versus production.

Cloud Load Balancing provides high performance, scalable load balancing for Google Cloud to ensure consistent performance for users.

Cloud CDN is a content delivery network that serves content to end users with high availability and high performance, usually by storing files close to the user. With Cloud CDN, Google’s global network provides low-latency, low-cost content delivery.

Cloud Interconnect lets you connect your own infrastructure to Google’s network edge with enterprise-grade connections. Google's partner network-service providers offer connections, and can offer higher service levels than standard internet connections.

Cloud DNS (domain name system) translates requests for domain names into IP addresses. Google provides the infrastructure to publish specific domain names in high-volume DNS services suitable for production applications.

### Routes and firewall rules in the cloud
Much like physical networks, VPCs have routing tables. A routing table is a data table of router locations and their IP addresses, stored in the memory of a router or a network host.

It lists the routes to particular network destinations, and sometimes, a metric value (number of “hops” needed to get to that address) which aids the router in choosing the most efficient route.

VPC routing tables are built-in so you don’t have to provision or manage a router.

They are used to forward traffic from one instance to another within the same network, across subnetworks, or even between Google Cloud zones, without requiring an external IP address.

Another thing you don’t have to provision or manage for Google Cloud is a firewall. VPCs provide a global distributed firewall, which can be controlled to restrict access to instances through both incoming and outgoing traffic.

It’s convenient to define firewall rules through metadata tags on Compute Engine instances. For example, you can tag all your web servers with “WEB” and write a firewall rule that says that traffic on ports 80 or 443 is allowed into all VMs with the “WEB” tag, no matter what their IP address happens to be.

### Multiple VPC networks
You’ll remember that VPCs belong to Google Cloud projects, but what if your company has several Google Cloud projects and the VPCs need to talk to each other?

With VPC peering, a relationship between two VPCs can be established to exchange traffic. It allows private RFC 1918 connectivity across two VPC networks, regardless of whether they belong to the same project or organization.

Now, remember that each VPC network will have firewall rules that define what traffic is allowed or denied between the networks. VPC peering is a decentralized or distributed approach to multi-project networking, because each VPC network can remain under the control of separate administrator groups and maintain its own global firewall and routing tables.

Historically, such projects would consider external IP addresses or VPNs to facilitate private communication between VPC networks.

However, VPC peering does not incur the network latency, security, and the cost disadvantages of using external IP addresses or VPNs.

Alternatively, to use the full power of Identity and Access Management (IAM) to control who and what in one project can interact with a VPC in another, then you can configure Shared VPC.

Shared VPC allows an organization to connect resources from multiple projects to a common VPC network. This allows the resources to communicate with each other securely and efficiently by using internal IPs from that network.

When you use Shared VPC, you designate a project as a host project and attach one or more other service projects to it.

The overall VPC network is called the Shared VPC network.

### Lab - Multiple VPC Networks

#### Overview
In this lab you create several VPC networks and VM instances and test connectivity across networks. Specifically, you create two custom mode networks (**managementnet** and **privatenet**) with firewall rules and VM instances.
![[Pasted image 20230608140356.png]]
#### Create custom mode VPC networks with firewall rules
Create two custom networks **managementnet** and **privatenet**, along with firewall rules to allow **SSH**, **ICMP**, and **RDP** ingress traffic.

##### Create the managementnet network
Create the **managementnet** network using the Cloud Console.

1. In the Cloud Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **VPC network** > **VPC networks**.
2. Notice the **default** and **mynetwork** networks with their subnets.

    Each Google Cloud project starts with the **default** network. In addition, the **mynetwork** network has been premade as part of your network diagram.

3. Click **Create VPC Network**.
4. Set the **Name** to `managementnet`.
5. For **Subnet creation mode**, click **Custom**.
6. Click **Done**.
7. Click **EQUIVALENT COMMAND LINE**.

    These commands illustrate that networks and subnets can be created using the Cloud Shell command line. You will create the **privatenet** network using these commands with similar parameters.

8. Click **Close**.
9. Click **Create**.

##### Create the privatenet network
Create the **privatenet** network using the Cloud Shell command line.

1. Run the following command to create the **privatenet** network:

```shell
gcloud compute networks create privatenet --subnet-mode=custom
```

2. Run the following command to create the **privatesubnet-us** subnet:

```shell
gcloud compute networks subnets create privatesubnet-us --network=privatenet --region=us-east1 --range=172.16.0.0/24
```

3. Run the following command to create the **privatesubnet-eu** subnet:

```shell
gcloud compute networks subnets create privatesubnet-eu --network=privatenet --region=europe-west1 --range=172.20.0.0/20
```

4. Run the following command to list the available VPC networks:

```shell
gcloud compute networks list
```

**Note:** **default** and **mynetwork** are auto mode networks, whereas, **managementnet** and **privatenet** are custom mode networks. Auto mode networks create subnets in each region automatically, while custom mode networks start with no subnets, giving you full control over subnet creation

5. Run the following command to list the available VPC subnets (sorted by VPC network):

```shell
gcloud compute networks subnets list --sort-by=NETWORK
```

6. In the Cloud Console, navigate to **Navigation menu** > **VPC network** > **VPC networks**.
7. You see that the same networks and subnets are listed in the Cloud Console.

##### Create the firewall rules for managementnet
Create firewall rules to allow **SSH**, **ICMP**, and **RDP** ingress traffic to VM instances on the **managementnet** network.

1. In the Cloud Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **VPC network** > **Firewall**.
2. Click **+ Create Firewall Rule**.
3. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|managementnet-allow-icmp-ssh-rdp|
|Network|managementnet|
|Targets|All instances in the network|
|Source filter|IPv4 Ranges|
|Source IPv4 ranges|0.0.0.0/0|
|Protocols and ports|Specified protocols and ports, and then _check_ tcp, _type:_ 22, 3389; and _check_ Other protocols, _type:_ icmp.|

**Note:** Make sure to include the **/0** in the **Source IPv4 ranges** to specify all networks.

4. Click **EQUIVALENT COMMAND LINE**.

    These commands illustrate that firewall rules can also be created using the Cloud Shell command line. You will create the **privatenet**'s firewall rules using these commands with similar parameters.

5. Click **Close**.
6. Click **Create**.

##### Create the firewall rules for privatenet
Create the firewall rules for **privatenet** network using the Cloud Shell command line.

1. In Cloud Shell, run the following command to create the **privatenet-allow-icmp-ssh-rdp** firewall rule:

```shell
gcloud compute firewall-rules create privatenet-allow-icmp-ssh-rdp --direction=INGRESS --priority=1000 --network=privatenet --action=ALLOW --rules=icmp,tcp:22,tcp:3389 --source-ranges=0.0.0.0/0
```

2. Run the following command to list all the firewall rules (sorted by VPC network):

```shell
gcloud compute firewall-rules list --sort-by=NETWORK
```

You can define multiple protocols and ports in one firewall rule (**privatenet** and **managementnet**), or spread them across multiple rules (**default** and **mynetwork**).

3. In the Cloud Console, navigate to **Navigation menu** > **VPC network** > **Firewall**.
4. You see that the same firewall rules are listed in the Cloud Console.

#### Create VM instances
Create two VM instances:

- **managementnet-us-vm** in **managementsubnet-us**
- **privatenet-us-vm** in **privatesubnet-us**

##### Create the managementnet-us-vm instance
Create the **managementnet-us-vm** instance using the Cloud Console.

1. From **Advanced options**, click **Networking, Disks, Security, Management, Sole-tenancy** dropdown.
2. Click **Networking**.
3. For **Network interfaces**, click the dropdown to edit.
4. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|managementnet|
|Subnetwork|managementsubnet-us|

5. Click **Done**.

##### Create the privatenet-us-vm instance
Create the **privatenet-us-vm** instance using the Cloud Shell command line.

1. In Cloud Shell, run the following command to create the **privatenet-us-vm** instance:

```shell
gcloud compute instances create privatenet-us-vm --zone="" --machine-type=e2-micro --subnet=privatesubnet-us
```

2. Run the following command to list all the VM instances (sorted by zone):

```shell
gcloud compute instances list --sort-by=ZONE
```

3. In the Cloud Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **Compute Engine** > **VM instances**.
4. You see that the VM instances are listed in the Cloud Console.
5. Click on **Column display options**, then select **Network**. Click **Ok**.

    There are three instances in **us-east1** and one instance in **europe-west1**. However, these instances are spread across three VPC networks (**managementnet**, **mynetwork** and **privatenet**), with no instance in the same zone and network as another. In the next section, you explore the effect this has on internal connectivity.

#### Explore the connectivity between VM instances
Explore the connectivity between the VM instances. Specifically, determine the effect of having VM instances in the same zone versus having instances in the same VPC network.

##### Ping the external IP addresses
Ping the external IP addresses of the VM instances to determine if you can reach the instances from the public internet.

1. In the Cloud Console, navigate to **Navigation menu** > **Compute Engine** > **VM instances**.
2. Note the external IP addresses for **mynet-eu-vm**, **managementnet-us-vm**, and **privatenet-us-vm**.
3. For **mynet-us-vm**, click **SSH** to launch a terminal and connect.
4. To test connectivity to **mynet-eu-vm**'s external IP, run the following command, replacing **mynet-eu-vm**'s external IP:

```shell
ping -c 3 <Enter mynet-eu-vm's external IP here>
```

This should work!

5. To test connectivity to **managementnet-us-vm**'s external IP, run the following command, replacing **managementnet-us-vm**'s external IP:

```shell
ping -c 3 <Enter managementnet-us-vm's external IP here>
```

This should work!

6. To test connectivity to **privatenet-us-vm**'s external IP, run the following command, replacing **privatenet-us-vm**'s external IP:

```shell
ping -c 3 <Enter privatenet-us-vm's external IP here>
```

This should work!

**Note:** You are able to ping the external IP address of all VM instances, even though they are either in a different zone or VPC network. This confirms public access to those instances is only controlled by the **ICMP** firewall rules that you established earlier.

##### Ping the internal IP addresses
Ping the internal IP addresses of the VM instances to determine if you can reach the instances from within a VPC network.

1. In the Cloud Console, navigate to **Navigation menu** > **Compute Engine** > **VM instances**.
2. Note the internal IP addresses for **mynet-eu-vm**, **managementnet-us-vm**, and **privatenet-us-vm**.
3. Return to the **SSH** terminal for **mynet-us-vm**.
4. To test connectivity to **mynet-eu-vm**'s internal IP, run the following command, replacing **mynet-eu-vm**'s internal IP:

```shell
ping -c 3 <Enter mynet-eu-vm's internal IP here>
```

**Note:** You are able to ping the internal IP address of **mynet-eu-vm** because it is on the same VPC network as the source of the ping (**mynet-us-vm**), even though both VM instances are in separate zones, regions and continents!

5. To test connectivity to **managementnet-us-vm**'s internal IP, run the following command, replacing **managementnet-us-vm**'s internal IP:

```shell
ping -c 3 <Enter managementnet-us-vm's internal IP here>
```

**Note:** This should not work as indicated by a 100% packet loss!

6. To test connectivity to **privatenet-us-vm**'s internal IP, run the following command, replacing **privatenet-us-vm**'s internal IP:

```shell
ping -c 3 <Enter privatenet-us-vm's internal IP here>
```

**Note:** This should not work either as indicated by a 100% packet loss! You are unable to ping the internal IP address of **managementnet-us-vm** and **privatenet-us-vm** because they are in separate VPC networks from the source of the ping (**mynet-us-vm**), even though they are all in the same zone **us-east1**.

VPC networks are by default isolated private networking domains. However, no internal IP address communication is allowed between networks, unless you set up mechanisms such as VPC peering or VPN.

#### Create a VM instance with multiple network interfaces
Every instance in a VPC network has a default network interface. You can create additional network interfaces attached to your VMs. Multiple network interfaces enable you to create configurations in which an instance connects directly to several VPC networks (up to 8 interfaces, depending on the instance's type).

##### Create the VM instance with multiple network interfaces
Create the **vm-appliance** instance with network interfaces in **privatesubnet-us**, **managementsubnet-us** and **mynetwork**. The CIDR ranges of these subnets do not overlap, which is a requirement for creating a VM with multiple network interface controllers (NICs).

1. In the Cloud Console, navigate to **Navigation menu** > **Compute Engine** > **VM instances**. 
2. Click **Create instance**.
3. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|vm-appliance|
|Region|us-east1|
|Zone|`<filled in at lab start>`|
|Series|E2|
|Machine type|e2-standard-4|

**Note:** The number of interfaces allowed in an instance is dependent on the instance's machine type and the number of vCPUs. The e2-standard-4 allows up to 4 network interfaces. Refer to [the Maximum number of network interfaces section of the Google Cloud Guide](https://cloud.google.com/vpc/docs/create-use-multiple-interfaces#max-interfaces) for more information.

4. From **Advanced options**, click **Networking, Disks, Security, Management, Sole-tenancy** dropdown.
5. Click **Networking**.
6. For **Network interfaces**, click the dropdown to edit.
7. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|privatenet|
|Subnetwork|privatesubnet-us|

8. Click **Done**.
9. Click **Add network interface**.
10. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|managementnet|
|Subnetwork|managementsubnet-us|

11. Click **Done**.
12. Click **Add network interface**.
13. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|mynetwork|
|Subnetwork|mynetwork|

14. Click **Done**.
15. Click **Create**.

##### Explore the network interface details
Explore the network interface details of **vm-appliance** within the Cloud Console and within the VM's terminal.

1. In the Cloud Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **Compute Engine** > **VM instances**.
2. Click **nic0** within the **Internal IP** address of **vm-appliance** to open the **Network interface details** page.
3. Verify that **nic0** is attached to **privatesubnet-us**, is assigned an internal IP address within that subnet (172.16.0.0/24), and has applicable firewall rules.
4. Click **nic0** and select **nic1**.
5. Verify that **nic1** is attached to **managementsubnet-us**, is assigned an internal IP address within that subnet (10.130.0.0/20), and has applicable firewall rules.
6. Click **nic1** and select **nic2**.
7. Verify that **nic2** is attached to **mynetwork**, is assigned an internal IP address within that subnet (10.128.0.0/20), and has applicable firewall rules.

**Note:** Each network interface has its own internal IP address so that the VM instance can communicate with those networks.

8. In the Cloud Console, navigate to **Navigation menu** > **Compute Engine** > **VM instances**.
9. For **vm-appliance**, click **SSH** to launch a terminal and connect.
10. Run the following, to list the network interfaces within the VM instance:

```shell
sudo ifconfig
```

**Note:** The **sudo ifconfig** command lists a Linux VM's network interfaces along with the internal IP addresses for each interface.

##### Explore the network interface connectivity
Demonstrate that the **vm-appliance** instance is connected to **privatesubnet-us**, **managementsubnet-us** and **mynetwork** by pinging VM instances on those subnets.

1. In the Cloud Console, navigate to **Navigation menu** > **Compute Engine** > **VM instances**.
2. Note the internal IP addresses for **privatenet-us-vm**, **managementnet-us-vm**, **mynet-us-vm**, and **mynet-eu-vm**.
3. Return to the **SSH** terminal for **vm-appliance**.
4. To test connectivity to **privatenet-us-vm**'s internal IP, run the following command, replacing **privatenet-us-vm**'s internal IP:

```shell
ping -c 3 <Enter privatenet-us-vm's internal IP here>
```

This works!

5. Repeat the same test by running the following:

```shell
ping -c 3 privatenet-us-vm
```

**Note:** You are able to ping **privatenet-us-vm** by its name because VPC networks have an internal DNS service that allows you to address instances by their DNS names rather than their internal IP addresses. When an internal DNS query is made with the instance hostname, it resolves to the primary interface (nic0) of the instance. Therefore, this only works for **privatenet-us-vm** in this case.

6. To test connectivity to **managementnet-us-vm**'s internal IP, run the following command, replacing **managementnet-us-vm**'s internal IP:

```shell
ping -c 3 <Enter managementnet-us-vm's internal IP here>
```

This works!

7. To test connectivity to **mynet-us-vm**'s internal IP, run the following command, replacing **mynet-us-vm**'s internal IP:

```shell
ping -c 3 <Enter mynet-us-vm's internal IP here>
```

This works!

8. To test connectivity to **mynet-eu-vm**'s internal IP, run the following command, replacing **mynet-eu-vm**'s internal IP:

```shell
ping -c 3 <Enter mynet-eu-vm's internal IP here>
```

**Note:** This does not work! In a multiple interface instance, every interface gets a route for the subnet that it is in. In addition, the instance gets a single default route that is associated with the primary interface eth0. Unless manually configured otherwise, any traffic leaving an instance for any destination other than a directly connected subnet will leave the instance via the default route on eth0.

9. To list the routes for **vm-appliance** instance, run the following command:

```shell
ip route
```

**Note:** The primary interface eth0 gets the default route (default via 172.16.0.1 dev eth0), and all three interfaces eth0, eth1 and eth2 get routes for their respective subnets. Since, the subnet of **mynet-eu-vm** (**10.132.0.0/20**) is not included in this routing table, the ping to that instance leaves **vm-appliance** on eth0 (which is on a different VPC network). You could change this behavior by configuring policy routing as documented in the [Configuring policy routing section of the Google Cloud Guide](https://cloud.google.com/vpc/docs/create-use-multiple-interfaces#configuring_policy_routing).


### Lab - VPC Networks: Controlling Access

#### Overview
In this lab, you create two nginx web servers and control external HTTP access to the web servers using tagged firewall rules. Then, you explore IAM roles and service accounts.

#### Create the web servers
Create two web servers (**blue** and **green**) in the **default** VPC network. Then, install **nginx** on the webservers and modify the welcome page to distinguish the servers.

##### Create the blue server
Create the **blue** server with a network tag.

1. Click **NETWORKING, DISKS, SECURITY, MANAGEMENT, SOLE-TENANCY**.  
2. Click **Networking**.  
3. For **Network tags**, type **web-server**.

**Note:** Networks use network tags to identify which VM instances are subject to certain firewall rules and network routes. Later in this lab, you create a firewall rule to allow HTTP access for VM instances with the **web-server** tag. Alternatively, you could check the **Allow HTTP traffic** checkbox, which would tag this instance as **http-server** and create the tagged firewall rule for tcp:80 for you.

##### Install nginx and customize the welcome page
Install nginx on both VM instances and modify the welcome page to distinguish the servers.

1. In the SSH terminal to blue, run the following command to install nginx:

```shell
sudo apt-get install nginx-light -y
```

2. Open the welcome page in the nano editor:

```shell
sudo nano /var/www/html/index.nginx-debian.html
```

3. Close the SSH terminal to **blue**:

```shell
exit
```

#### Create the firewall rule
Create the tagged firewall rule and test HTTP connectivity.

##### Create the tagged firewall rule
Create a firewall rule that applies to VM instances with the **web-server** network tag.

1. In the Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **VPC network** > **Firewall**.
2. Notice the **default-allow-internal** firewall rule.

**Note:** The **default-allow-internal** firewall rule allows traffic on all protocols/ports within the **default** network. You want to create a firewall rule to allow traffic from outside this network to only the **blue** server, by using the network tag **web-server**.

3. Click **Create Firewall Rule**.
4. Set the following values, leave all other values at their defaults and click **Create**:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|allow-http-web-server|
|Network|default|
|Targets|Specified target tags|
|Target tags|web-server|
|Source filter|IPv4 Ranges|
|Source IPv4 ranges|0.0.0.0/0|
|Protocols and ports|Specified protocols and ports, and then _check_ tcp, _type:_ 80; and _check_ Other protocols, _type:_ icmp.|

##### Create a test-vm
Create a **test-vm** instance using the Cloud Shell command line.

- Create a **test-vm** instance, in the us-central1-a zone:

```shell
gcloud compute instances create test-vm --machine-type=f1-micro --subnet=default --zone=us-central1-a
```

##### Test HTTP connectivity
From **test-vm** `curl` the internal and external IP addresses of **blue** and **green**.

1. To test HTTP connectivity to **blue**'s internal IP, run the following command, replacing **blue**'s internal IP:

```shell
curl <Enter blue's internal IP here>
```

**Note:** You are able to HTTP access both servers using their internal IP addresses. The connection on tcp:80 is allowed by the **default- allow-internal** firewall rule, as **test-vm** is on the same VPC network as the web servers **default** network.

2. To test HTTP connectivity to **green**'s external IP, run the following command, replacing **green**'s external IP:

```shell
curl -c 3 <Enter green's external IP here>
```

**Note:** This should not work! The request hangs.

**Note:** As expected, you are only able to HTTP access the external IP address of the **blue** server as the **allow-http-web-server** only applies to VM instances with the **web-server** tag.

You can verify the same behavior from your browser by opening a new tab and navigating to `http://[External IP of server]`.

#### Explore the Network and Security Admin roles
Cloud IAM lets you authorize who can take action on specific resources, giving you full control and visibility to manage cloud resources centrally. The following roles are used in conjunction with single-project networking to independently control administrative access to each VPC Network:

- **Network Admin**: Permissions to create, modify, and delete networking resources, except for firewall rules and SSL certificates.
- **Security Admin**: Permissions to create, modify, and delete firewall rules and SSL certificates.

Explore these roles by applying them to a service account, which is a special Google account that belongs to your VM instance, instead of to an individual end user. Rather than creating a new user, you will authorize **test-vm** to use the service account to demonstrate the permissions of the **Network Admin** and **Security Admin** roles.

##### Verify current permissions
Currently, **test-vm** uses the [Compute Engine default service account](https://cloud.google.com/compute/docs/access/service-accounts#compute_engine_default_service_account), which is enabled on all instances created by Cloud Shell command-line and the Cloud Console.

Try to list or delete the available firewall rules from **test-vm**.

1. Return to the **SSH** terminal of the **test-vm** instance.
2. Try to list the available firewall rules:

```shell
gcloud compute firewall-rules list
```

**Note:** This should not work!

3. Try to delete the **allow-http-web-server** firewall rule:

```shell
gcloud compute firewall-rules delete allow-http-web-server
```

**Note:** This should not work!

**Note:** The **Compute Engine default service account** does not have the right permissions to allow you to list or delete firewall rules. The same applies to other users who do not have the right roles.

##### Create a service account
Create a service account and apply the **Network Admin** role.

1. In the Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **IAM & admin** > **Service Accounts**.
2. Notice the **Compute Engine default service account**.
3. Click **Create service account**.
4. Set the **Service account** name to **Network-admin** and click **CREATE AND CONTINUE**.
5. For **Select a role**, select **Compute Engine** > **Compute Network Admin** and click **CONTINUE** then click **DONE**.
6. After creating the service account 'Network-admin', click on the three dots at the right corner and click **Manage Key** in the dropdown, then click on **Add Key** and select **Create new key** from the dropdown. Click **Create** to download your JSON output.
7. Click **Close**.

    A JSON key file download to your local computer. Find this key file, you will upload it into the VM in a later step.

8. Rename the JSON key file on your local machine to **credentials.json**

##### Authorize test-vm and verify permissions
Authorize **test-vm** to use the **Network-admin** service account.

1. Return to the **SSH** terminal of the **test-vm** instance.
2. To upload **credentials.json** through the SSH VM terminal, click on the **Upload file** icon in the upper-right corner.
3. Select **credentials.json** and upload it.
4. Click **Close** in the File Transfer window.

**Note**: If prompted, click **Retry** on the _Connection via Cloud Identity-Aware Proxy Failed_ dialog and re-upload the file.

5. Authorize the VM with the credentials you just uploaded:

```shell
gcloud auth activate-service-account --key-file credentials.json
```

**Note:** The image you are using has the Cloud SDK pre-installed; therefore, you don’t need to initialize the Cloud SDK. If you are attempting this lab in a different environment, make sure you have followed the [procedures regarding installing the Cloud SDK](https://cloud.google.com/sdk/downloads).

6. Try to list the available firewall rules:

```shell
gcloud compute firewall-rules list
```

This should work!

7. Try to delete the **allow-http-web-server** firewall rule:

```shell
gcloud compute firewall-rules delete allow-http-web-server
```

8. Enter **Y**, if asked to continue.

**Note:** This should not work!

**Note:** As expected, the **Network Admin** role has permissions to list but not modify/delete firewall rules.

##### Update service account and verify permissions
Update the **Network-admin** service account by providing it the **Security Admin** role.

1. In the Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **IAM & admin** > **IAM**.
2. Find the **Network-admin** account. Focus on the **Name** column to identify this account.
3. Click on the pencil icon for the **Network-admin** account.
4. Change **Role** to **Compute Engine > Compute Security Admin**.
5. Click **Save**.
6. Return to the **SSH** terminal of the **test-vm** instance.
7. Try to list the available firewall rules:

```shell
gcloud compute firewall-rules list
```

This should work!

8. Try to delete the **allow-http-web-server** firewall rule:

```shell
gcloud compute firewall-rules delete allow-http-web-server
```

9. Enter **Y**, if asked to continue.

This should work!

**Note:** As expected, the **Security Admin** role has permissions to list and delete firewall rules.

##### Verify the deletion of the firewall rule
Verify that you can no longer HTTP access the external IP of the **blue** server, because you deleted the **allow-http-web-server** firewall rule.

1. Return to the **SSH** terminal of the **test-vm** instance.
2. To test HTTP connectivity to **blue**'s external IP, run the following command, replacing **blue**'s external IP:

```shell
curl -c 3 <Enter blue's external IP here>
```

**Note:** This should not work!

3. Press **CTRL+c** to stop the HTTP request.

**Note:** Provide the **Security Admin** role to the right user or service account to avoid any unwanted changes to your firewall rules!

### Building hybrid clouds
Many Google Cloud customers want to connect their Google Virtual Private Clouds to other networks in their system, such as on-premises networks or networks in other clouds.

One option is to start with a virtual private network connection over the internet and use the IPsec VPN protocol to create a “tunnel” connection.

To make the connection dynamic, a Google Cloud feature called Cloud Router can be used. Cloud Router lets other networks and Google VPC exchange route information over the VPN by using the Border Gateway Protocol. With this method, if you add a new subnet to your Google VPC, your on-premises network will automatically get routes to it.

But using the internet to connect networks isn't always the best option for everyone, either because of security concerns or because of bandwidth reliability.

A second option is to consider “peering” with Google by using Direct Peering. Peering means putting a router in the same public data center as a Google point of presence and using it to exchange traffic between networks.

Google has more than 100 points of presence (PoPs) around the world.

Customers who aren’t already in a point of presence can contract with a partner in the Carrier Peering program to be connected.

Carrier Peering gives you direct access from your on-premises network through a service provider's network to Google Workspace and to Google Cloud products that can be exposed through one or more public IP addresses.

One downside of peering, though, is that it isn’t covered by a Google service level agreement.

If getting the highest uptimes for interconnection is important, then using Dedicated Interconnect would be a good solution. This option allows for one or more direct, private connections to Google.

If these connections have topologies that meet Google’s specifications, they can be covered by up to a 99.99% SLA.

Also, these connections can be backed up by a VPN for even greater reliability. 

And the final option we’ll explore is Partner Interconnect, which provides connectivity between an on-premises network and a VPC network through a supported service provider.

A Partner Interconnect connection is useful if a data center is in a physical location that can't reach a Dedicated Interconnect colocation facility, or if the data needs doesn’t warrant an entire 10 Gbps connection.

Depending on availability needs, Partner Interconnect can be configured to support mission-critical services or applications that can tolerate some downtime.

As with Dedicated Interconnect, if these connections have topologies that meet Google’s specifications, they can be covered by up to a 99.99% SLA, but note that Google is not responsible for any aspects of Partner Interconnect provided by the third-party service provider nor any issues outside of Google's network.

### Load balancing options
The job of a load balancer is to distribute user traffic across multiple instances of an application.

By spreading the load, load balancing reduces the risk that applications experience performance issues.

Cloud Load Balancing is a fully distributed, software-defined, managed service for all your traffic.

And because the load balancers don’t run in VMs that you have to manage, you don’t have to worry about scaling or managing them.

You can put Cloud Load Balancing in front of all of your traffic: HTTP(S), other TCP and SSL traffic, and UDP traffic too.

Cloud Load Balancing provides cross-region load balancing, including automatic multi-region failover, which gently moves traffic in fractions if backends become unhealthy.

Cloud Load Balancing reacts quickly to changes in users, traffic, network, backend health, and other related conditions.

And what if you anticipate a huge spike in demand? Say, your online game is already a hit; do you need to file a support ticket to warn Google of the incoming load? No. No so-called “pre-warming” is required.

Cloud VPC offers a suite of load-balancing options: If you need cross-regional load balancing for a web application, use Global HTTP(S) load balancing.

For Secure Sockets Layer (SSL) traffic that is not HTTP, use SSL Proxy load balancing.

If it’s other TCP traffic that does not use Secure Sockets Layer, use TCP Proxy load balancing.

Those two proxy services only work for specific port numbers, and they only work for TCP.

If you want to load balance UDP traffic, or traffic on any port number, you can still load balance across a Google Cloud region with Regional external load balancing.

Finally, what all those services have in common is that they’re intended for traffic coming into the Google network from the internet. But what if you want to load balance traffic inside your project, for example, between the presentation layer and the business layer of your application? For that, use Internal HTTP(S) load balancing. It accepts traffic on a Google Cloud internal IP address and load balances it across Compute Engine VMs.

### Lab - HTTP Load Balancer with Google Cloud Armor

#### Overview
Google Cloud HTTP(S) load balancing is implemented at the edge of Google's network in Google's points of presence (POP) around the world. User traffic directed to an HTTP(S) load balancer enters the POP closest to the user and is then load balanced over Google's global network to the closest backend that has sufficient capacity available.

Cloud Armor IP allowlist/denylist enable you to restrict or allow access to your HTTP(S) load balancer at the edge of the Google Cloud, as close as possible to the user and to malicious traffic. This prevents malicious users or traffic from consuming resources or entering your virtual private cloud (VPC) networks.

In this lab, you configure an HTTP Load Balancer with global backends, as shown in the diagram below. Then, you stress test the Load Balancer and denylist the stress test IP with Cloud Armor.

#### Configure HTTP and health check firewall rules
Configure firewall rules to allow HTTP traffic to the backends and TCP traffic from the Google Cloud health checker.

##### Create the HTTP firewall rule
Create a firewall rule to allow HTTP traffic to the backends.

1. In the Cloud Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **VPC network** > **Firewall**.
2. Notice the existing **ICMP**, **internal**, **RDP**, and **SSH** firewall rules.

    Each Google Cloud project starts with the **default** network and these firewall rules.

3. Click **Create Firewall Rule**.
4. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|default-allow-http|
|Network|default|
|Targets|Specified target tags|
|Target tags|http-server|
|Source filter|IPv4 Ranges|
|Source IPv4 ranges|0.0.0.0/0|
|Protocols and ports|Specified protocols and ports, and then _check_ TCP, _type:_ 80|

##### Create the health check firewall rules
Health checks determine which instances of a load balancer can receive new connections. For HTTP load balancing, the health check probes to your load balanced instances come from addresses in the ranges `130.211.0.0/22` and `35.191.0.0/16`. Your firewall rules must allow these connections.

1. Still in the **Firewall** page, click **Create Firewall Rule**.
2. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|default-allow-health-check|
|Network|default|
|Targets|Specified target tags|
|Target tags|http-server|
|Source filter|IPv4 Ranges|
|Source IPv4 ranges|`130.211.0.0/22`, `35.191.0.0/16`|
|Protocols and ports|Specified protocols and ports, and then _check_ TCP|

**Note:** Make sure to enter the two **Source IPv4 ranges** one-by-one and press SPACE in between them.

#### Configure instance templates and create instance groups
A managed instance group uses an instance template to create a group of identical instances. Use these to create the backends of the HTTP Load Balancer.

##### Configure the instance templates
An instance template is an API resource that you use to create VM instances and managed instance groups. Instance templates define the machine type, boot disk image, subnet, labels, and other instance properties. Create one instance template for `<filled in at lab start>` and one for **europe-west1**.

1. In the Cloud Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **Compute Engine** > **Instance templates**, and then click **Create instance template**.
2. For **Name**, type **`<filled in at lab start>`-template**.

    **NOTE**: An instance template name can not have "space" in the name, remove any extra space if required.

3. For **Series**, select **E2**.
4. For **Machine Type**, select **e2-micro**.
5. Click **Advanced Options**.
6. Click **Networking**. Set the following value and leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network tags|http-server|

7. Click **default** under **Network interfaces**. Set the following values and leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|default|
|Subnetwork|default (`____`)|

The network tag **http-server** ensures that the **HTTP** and **Health Check** firewall rules apply to these instances.

8. Click the **Management** tab.
9. Under **Metadata**, click **+ ADD ITEM** and specify the following:

|Key|Value|
|---|---|
|startup-script-url|gs://cloud-training/gcpnet/httplb/startup.sh|

The `startup-script-url` specifies a script that executes when instances are started. This script installs Apache and changes the welcome page to include the client IP and the name, region, and zone of the VM instance. Feel free to explore [this script](https://storage.googleapis.com/cloud-training/gcpnet/httplb/startup.sh).

10. Click **Create**.
11. Wait for the instance template to be created.

Now create another instance template for **subnet-b** by copying **`____`-template**:

1. Click on **`<filled in at lab start>`-template** and then click on the **+CREATE SIMILAR** option from the top.
2. For **Name**, type **europe-west1-template**.
3. Click **Advanced Options**.
4. Click **Networking**.
5. Ensure **http-server** is added as a **network tag**.
6. In **Network interfaces**, for **Subnetwork**, select **default (europe-west1)**.
7. Click **Done**.
8. Click **Create**.

##### Create the managed instance groups
1. Still in **Compute Engine**, click **Instance groups** in the left menu.
2. Click **Create instance group**.
3. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|`____`-mig (if required, remove extra space from the name)|
|Location|Multiple zones|
|Region|`____`|
|Instance template|`____`-template|
|Minimum number of instances|1|
|Maximum number of instances|2|
|Autoscaling signals > Click dropdown > Signal type|CPU utilization|
|Target CPU utilization|80, click **Done**.|
|Cool-down period|45|

Managed instance groups offer **autoscaling** capabilities that allow you to automatically add or remove instances from a managed instance group based on increases or decreases in load. Autoscaling helps your applications gracefully handle increases in traffic and reduces cost when the need for resources is lower. You just define the autoscaling policy and the autoscaler performs automatic scaling based on the measured load.

4. Click **Create**.

##### Verify the backends
Verify that VM instances are being created in both regions and access their HTTP sites.

1. Still in **Compute Engine**, click **VM instances** in the left menu.
2. Notice the instances that start with `____`-mig and `europe-west1-mig`.

    These instances are part of the managed instance groups.

3. Click on the **External IP** of an instance of `____`-mig.

    You should see the **Client IP** (your IP address), the **Hostname** (starts with `____`-mig) and the **Server Location** (a zone in `____`).

4. Click on the **External IP** of an instance of `europe-west1-mig`.

    You should see the **Client IP** (your IP address), the **Hostname** (starts with `europe-west1-mig`) and the **Server Location** (a zone in europe-west1).

**Note:** The **Hostname** and **Server Location** identifies where the HTTP Load Balancer sends traffic.

#### Configure the HTTP Load Balancer
Configure the HTTP Load Balancer to balance traffic between the two backends (**us-east1-mig** in us-east1 and **europe-west1-mig** in europe-west1), as illustrated in the network diagram:

![[Pasted image 20230608205148.png]]

##### Start the configuration
1. In the Cloud Console, click **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > click **Network Services** > **Load balancing**, and then click **Create load balancer**.
2. Under **HTTP(S) Load Balancing**, click on **Start configuration**.
3. Select **From Internet to my VMs or serverless services**, and click **Continue**.
4. Set the New HTTP(S) Load Balancer **Name** to `http-lb`.

##### Configure the frontend
The host and path rules determine how your traffic will be directed. For example, you could direct video traffic to one backend and static traffic to another backend. However, you are not configuring the Host and path rules in this lab.

1. Click on **Frontend configuration**.
2. Specify the following, leaving all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Protocol|HTTP|
|IP version|IPv4|
|IP address|Ephemeral|
|Port|80|

3. Click **Done**.
4. Click **Add Frontend IP and port**.
5. Specify the following, leaving all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Protocol|HTTP|
|IP version|IPv6|
|IP address|Auto-allocate|
|Port|80|

6. Click **Done**.

HTTP(S) load balancing supports both IPv4 and IPv6 addresses for client traffic. Client IPv6 requests are terminated at the global load balancing layer, then proxied over IPv4 to your backends.

##### Configure the backend
Backend services direct incoming traffic to one or more attached backends. Each backend is composed of an instance group and additional serving capacity metadata.

1. Click on **Backend configuration**.
2. For **Backend services & backend buckets**, click **Create a backend service**.
3. Set the following values, leave all other values at their defaults:

|Property|Value (select option as specified)|
|---|---|
|Name|http-backend|
|Instance group|`____`-mig|
|Port numbers|80|
|Balancing mode|Rate|
|Maximum RPS|50|
|Capacity|100|

This configuration means that the load balancer attempts to keep each instance of **us-east1-mig** at or below 50 requests per second (RPS).

4. Click **Done**.
5. Click **Add backend**.
6. Set the following values, leave all other values at their defaults:

|Property|Value (select option as specified)|
|---|---|
|Instance group|europe-west1-mig|
|Port numbers|80|
|Balancing mode|Utilization|
|Maximum backend utilization|80|
|Capacity|100|

This configuration means that the load balancer attempts to keep each instance of **europe-west1-mig** at or below 80% CPU utilization.

7. Click **Done**.
8. For **Health Check**, select **Create a health check**.
9. Set the following values, leave all other values at their defaults:

|Property|Value (select option as specified)|
|---|---|
|Name|http-health-check|
|Protocol|TCP|
|Port|80|

Health checks determine which instances receive new connections. This HTTP health check polls instances every 5 seconds, waits up to 5 seconds for a response and treats 2 successful or 2 failed attempts as healthy or unhealthy, respectively.

10. Click **Save**.
11. Check the **Enable Logging** box.
12. Set the **Sample Rate** to `1`.
13. Click **Create** to create the backend service.
14. Click **Ok**.

##### Review and create the HTTP Load Balancer
1. Click on **Review and finalize**.
2. Review the **Backend** and **Frontend** services.
3. Click on **Create**.
4. Wait for the load balancer to be created.
5. Click on the name of the load balancer (**http-lb**).
6. Note the IPv4 and IPv6 addresses of the load balancer for the next task. They will be referred to as `[LB_IP_v4]` and `[LB_IP_v6]`, respectively.

**Note:** The IPv6 address is the one in hexadecimal format.

#### Test the HTTP Load Balancer
Now that you created the HTTP Load Balancer for your backends, verify that traffic is forwarded to the backend service.

##### Access the HTTP Load Balancer
To test IPv4 access to the HTTP Load Balancer, open a new tab in your browser and navigate to `http://[LB_IP_v4]`. Make sure to replace `[LB_IP_v4]` with the IPv4 address of the load balancer.

**Note:** It might take up to 5 minutes to access the HTTP Load Balancer. In the meantime, you might get a 404 or 502 error. Keep trying until you see the page of one of the backends.

**Note:** Depending on your proximity to **us-east1** and **europe-west1**, your traffic is either forwarded to a **us-east1-mig** or **europe-west1-mig** instance.

If you have a local IPv6 address, try the IPv6 address of the HTTP Load Balancer by navigating to `http://[LB_IP_v6]`. Make sure to replace `[LB_IP_v6]` with the IPv6 address of the load balancer.

##### Stress test the HTTP Load Balancer
Create a new VM to simulate a load on the HTTP Load Balancer using `siege`. Then, determine if traffic is balanced across both backends when the load is high.

1. In the Console, navigate to **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **Compute Engine** > **VM instances**.
2. Click **Create instance**.
3. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|siege-vm|
|Region|us-central1|
|Zone|us-central1-a|
|Series|E2|

Given that **us-central1** is closer to **`____`** than to **europe-west1**, traffic should be forwarded only to **`____`-mig** (unless the load is too high).

4. Click **Create**.
5. Wait for the **siege-vm** instance to be created.
6. For **siege-vm**, click **SSH** to launch a terminal and connect.
7. Run the following command, to install siege:

```shell
sudo apt-get -y install siege
```

8. To store the IPv4 address of the HTTP Load Balancer in an environment variable, run the following command, replacing `[LB_IP_v4]` with the IPv4 address:

```shell
export LB_IP=[LB_IP_v4]
```

9. To simulate a load, run the following command:

```shell
siege -c 150 -t120s http://$LB_IP
```

10. In the Cloud Console, on the **Navigation menu** (![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)), click **Network Services** > **Load balancing**.
11. Click **Backends**.
12. Click **http-backend**.
13. Navigate to **http-lb**.
14. Click on the **Monitoring** tab.
15. Monitor the **Frontend Location (Total inbound traffic)** between North America and the two backends for 2 to 3 minutes.

At first, traffic should just be directed to **`____`-mig** but as the RPS increases, traffic is also directed to **europe-west1-mig**.

This demonstrates that by default traffic is forwarded to the closest backend but if the load is very high, traffic can be distributed across the backends.

16. Return to the **SSH** terminal of **siege-vm**.
17. Press **CTRL+C** to stop siege if it's still running.

#### Denylist the siege-vm
Use Cloud Armor to denylist the **siege-vm** from accessing the HTTP Load Balancer.

##### Create the security policy
Create a Cloud Armor security policy with a denylist rule for the **siege-vm**.

1. In the console, navigate to **Navigation menu** (![Navigatio menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D)) > **Compute Engine** > **VM instances**.
2. Note the **External IP** of the **siege-vm**. This will be referred to as `[SIEGE_IP]`.

**Note:** There are ways to identify the external IP address of a client trying to access your HTTP Load Balancer. For example, you could examine traffic captured by [VPC Flow Logs in BigQuery](https://cloud.google.com/vpc/docs/using-flow-logs#exporting_logs_to_bigquery_name_short_pubsub_name_short_and_custom_targets) to determine a high volume of incoming requests.

3. In the Cloud console, navigate to **Navigation menu** > **Network Security** > **Cloud Armor**.
4. Click **Create policy**.
5. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|denylist-siege|
|Default rule action|Allow|
6. Click **Next step**.
    
7. Click **Add rule**.
8. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Condition > Match|_Enter the SIEGE_IP_|
|Action|Deny|
|Deny status|403 (Forbidden)|
|Priority|1000|

9. Click **Done**.
10. Click **Next step**.
11. Click **Add Target**.
12. For **Type**, select **Load balancer backend service**.
13. For **Target**, select **http-backend**.
14. Click **Create policy**.

**Note:** Alternatively, you could set the default rule to **Deny** and only allowlist or allow traffic from authorized users/IP addresses.

##### Verify the security policy
Verify that the **siege-vm** cannot access the HTTP Load Balancer.

1. Return to the **SSH** terminal of **siege-vm**.
2. To access the load balancer, run the following:

```shell
curl http://$LB_IP
```

**Note:** It might take a couple of minutes for the security policy to take effect. If you are able to access the backends, keep trying until you get the **403 Forbidden error**.

3. Open a new tab in your browser and navigate to `http://[LB_IP_v4]`. Make sure to replace `[LB_IP_v4]` with the IPv4 address of the load balancer.

**Note:** You can access the HTTP Load Balancer from your browser because of the default rule to **allow** traffic; however, you cannot access it from the **siege-vm** because of the **deny** rule that you implemented.

4. Back in the SSH terminal of siege-vm, to simulate a load, run the following command:

```shell
siege -c 150 -t120s http://$LB_IP
```

The command will not generate any output.

Explore the security policy logs to determine if this traffic is also blocked.

5. In the console, navigate to **Navigation menu** > **Network Security** > **Cloud Armor**.
6. Click **denylist-siege**.
7. Click **Logs**.
8. Click **View policy logs**.
9. On the Logging page, make sure to clear all the text in the **Query preview**. Select resource to **Cloud HTTP Load Balancer** > **http-lb-forwarding-rule** > **http-lb** then click **Apply**.
10. Now click **Run Query**.
11. Expand a log entry in **Query results**.
12. Expand **httpRequest**.

The request should be from the **siege-vm** IP address. If not, expand another log entry.

13. Expand **jsonPayload**.
14. Expand **enforcedSecurityPolicy**.
15. Notice that the **configuredAction** is to `DENY` with the **name** `denylist-siege`.

Cloud Armor security policies create logs that can be explored to determine when traffic is denied and when it is allowed, along with the source of the traffic.


## Keeping an eye on things

### Introduction to Infrastructure as Code (IaC)
Creating an environment in Google Cloud can mean lots of work, like setting up a compute network and storage resources, and then monitoring their configurations. This process can be done manually by writing the commands you need to set up your environment the way you want. 

However, this is labor-intensive. If you want to change the environment, it requires updating commands. Or if you want to clone an environment, you must manually write new commands.

As the name implies, infrastructure as code, or IaC, is taking what a required infrastructure needs to look like and defining it as code.

You capture the code in a template file that is both human readable and machine consumable. 

IaC tools allow for the creation of entire architectures by using templates. The template is a configuration file that supplies the details of the infrastructure.

Rather than having to use a console or run commands manually to build all parts of the system, the template is used to automatically build the infrastructure.

The same template enables resources to be automatically updated and/or deleted as required.

Because templates are treated as code, they can be stored in repositories, tracked using version control systems, and shared with other users.

Templates can also be used for disaster recovery. If for any reason the infrastructure must be rebuilt, the templates can be used to automatically recover.

### Terraform
Terraform is an open source tool that lets you use templates to provision Google Cloud resources.

To use Terraform, you create a template file by using HashiCorp configuration language (HCL), which describes what the components of the environment should look like.

Terraform then uses that template to determine the actions needed to create the environment your template describes. If you need to change the environment, you can edit your template and then use Terraform to update the environment to match the change.

A deployment can be repeated as many times as required with consistent results, and you can delete an entire deployment with one command or click.

Terraform uses the underlying APIs of each Google Cloud service to deploy your resources. This enables you to deploy almost everything we have seen so far, from instances, instance templates, and groups, to VPC networks, firewall rules, VPN tunnels, Cloud Routers, and load balancers.

You can also store and version-control your Terraform templates in Cloud Source Repositories.

In addition to Terraform, Google Cloud also provides support for other third-party, open source IaC tools.

### Monitoring and managing services, applications, and infrastructure
Monitoring is the foundation of product reliability. It reveals what needs urgent attention and shows trends in application usage patterns, which can yield better capacity planning, and generally help improve an application client's experience and minimize their pain.

In Google's Site Reliability Engineering book, which is available at landing.google.com/sre/books, monitoring is defined as: "Collecting, processing, aggregating, and displaying real-time quantitative data about a system, such as query counts and types, error counts and types, processing times, and server lifetimes."

With monitoring, you can ensure continued system operations, uncover trend analyses over time, build dashboards, alert personnel when systems violate predefined service-level objectives (SLOs), compare systems and systems changed, and provide data for improved incident response–just to name a few tasks.

An application client normally only sees the public side of a product, and as a result, developers and business stakeholders both tend to think that the most important way to make the client happy is by spending the most time and effort on developing that part of the product.

However, to be truly reliable, even the best products must be deployed into environments with enough capacity to handle the anticipated client load.

Great products also need thorough testing, preferably automated, and a refined continuous integration/continuous development (CI/CD) release pipeline.

Blameless postmortems and root cause analyses are the DevOps team's way of letting the client know why an incident happened and why it is unlikely to happen again.

In this context, we are discussing a system or software failure, but the term “incident” can also be used to describe a breach of security. Transparency here is crucial to building trust.

### Google Cloud's operations suite
Google Cloud's operations suite provides powerful monitoring, logging, error reporting, and debugging for applications in the cloud. It equips you with insight into the health, performance, and availability of cloud-powered apps; enabling you to find and fix issues faster.

When DevOps personnel want to track exactly what's happening inside Google Cloud projects, they often first think of monitoring. As stated previously, monitoring starts with signal data.

Metrics take measurements and use math to align those measurements over time. For example, it might be taking raw CPU usage measurement values and averaging them to produce a single value per minute.

Google Cloud, by default, collects more than a thousand different streams of metric data, which can be incorporated into dashboards, alerts, and several other key tools.

When data scientists run massive, scalable queries in BigQuery, it’s important for them to know how many queries are currently in flight, how many bytes have been scanned and added to the bill, and data slot usage patterns.

It could also be critical to DevOps teams that run containerized applications in Cloud Run to know CPU and memory utilization, and app bill time.

And if those same DevOps teams want to enhance the signal metrics from their custom application wherever it's running, they could use the open source OpenTelementry and create their own metrics.

Workloads on Compute Engine will benefit from CPU and memory utilization data, along with uptime, disk throughput, and many other metrics.

Cloud monitoring provides visibility into the performance, uptime, and overall health of cloud-powered applications. It collects metrics, events, and metadata from projects, logs, services, systems, agents, custom code, and various common application components, including Cassandra, NGINX, Apache Web Server, and Elasticsearch.

Monitoring ingests that data and generates insights through dashboards, metrics explorer charts, and automated alerts.

Most log analysis starts with Google Cloud’s integrated Logs Explorer. Logging entries can also be exported to several destinations for alternative or further analysis.

Pub/Sub messages can be analyzed in near-real time by using custom code or stream processing technologies like Dataflow.

BigQuery allows analysts to examine logging data through SQL queries. 

And archived log files in Cloud Storage can be analyzed with several tools and techniques.

Log data can be exported as files to Cloud Storage, as messages through Pub/Sub, or into BigQuery tables.

Logs-based metrics can be created and integrated into Cloud Monitoring dashboards, alerts, and service SLOs.

Default log retention in Cloud Logging depends on the log type. Data access logs are retained by default for 30 days, but this is configurable for 3650 days. Admin logs are stored by default for 400 days. Export logs to Cloud Storage or BigQuery to extend retention.

The Google Cloud logs that are visible to you in Cloud Logging vary, depending on which Google Cloud resources you use in your Google Cloud project or organization.

Four main log categories are audit logs, agent logs, network logs, and service logs.

Cloud Audit Logs helps answer the question "Who did what, where, and when?" Admin activity tracks configuration changes. Data access tracks calls that read the configuration or metadata of resources and user-driven calls that create, modify, or read user-provided resource data. System events are non-human Google Cloud administrative actions that change the configuration of resources. Access Transparency provides you with logs that capture the actions Google personnel take when they access your content.

Agent logs use a Google-customized and packaged Fluentd agent that can be installed on any AWS or Google Cloud VM to ingest log data from Google Cloud instances–for example, Compute Engine, managed VMs, or containers, and AWS EC2 instances.

Network logs provide both network and security operations with in-depth network service telemetry. VPC Flow Logs records samples of VPC network flow and can be used for network monitoring, forensics, real-time security analysis, and expense optimization. Firewall Rules Logging lets you audit, verify, and analyze the effects of your firewall rules. NAT Gateway logs capture information on NAT network connections and errors. 

Service logs provide access to logs created by developers who deploy code to Google Cloud. For example, if they use Node.js to build a container and deploy it to Cloud Run, any logging to standard out or standard error will automatically be sent to Cloud Logging for easy, centralized viewing. Error Reporting counts, analyzes, and aggregates the crashes in your running cloud services. Crashes in most modern languages are “exceptions,” which are not caught and handled by the code itself.

Its management interface displays the results with sorting and filtering capabilities. A dedicated view shows the error details: time chart, occurrences, affected user count, first and last-seen dates, and a cleaned exception stack trace.

You can also create alerts to receive notifications on new errors.

Cloud Trace, based on the tools Google uses on its production services, is a tracing system that collects latency data from your distributed applications and displays it in the Google Cloud console.

Cloud Trace can capture traces from applications deployed on App Engine, Compute Engine VMs, and Kubernetes Engine containers.

Performance insights are provided in near-real time, and Cloud Trace automatically analyzes all of your application's traces to generate in-depth latency reports to surface performance degradations.

Cloud Trace continuously gathers and analyzes trace data to automatically identify recent changes to your application's performance.

Poorly performing code increases the latency and cost of applications and web services every day, but nobody knows or does anything about it.

Cloud Profiler changes this by using statistical techniques and extremely low-impact instrumentation that runs across all production application instances to provide a complete CPU and heap picture of an application without slowing it down.

With broad platform support that includes Compute Engine VMs, App Engine, and Kubernetes, Cloud Profiler lets developers analyze applications that run anywhere, including Google Cloud, other cloud platforms, or on-premises, with support for Java, Go, Python, and Node.js.

Cloud Profiler presents the call hierarchy and resource consumption of the relevant function in an interactive flame graph that helps developers understand which paths consume the most resources and the different ways in which their code is actually called.
 
## Lab - Securing Virtual Machines using BeyondCorp Enterprise (BCE)

### Overview
In this lab, you will explore how you can use BeyondCorp Enterprise (BCE) and Identity-Aware Proxy (IAP) TCP forwarding to enable administrative access to VM instances that do not have external IP addresses or do not permit direct access over the internet.

You can read more about BeyondCorp Enterprise (BCE) and the zero trust security model at the following [cloud documentation site:](https://cloud.google.com/beyondcorp-enterprise)

### Enable IAP TCP forwarding in your Google Cloud project
1. Open the **Navigation Menu** and select **APIs and Services > Library.**
2. Search for **IAP** and select **Cloud Identity-Aware Proxy API.**
3. Click **Enable.**

### Create Linux and Windows Instances
1. You will create three instances for this lab

    - Two for demonstration purposes (Linux and Windows)
    - One for testing connectivity (Windows)

2. Open the **Navigation Menu** and select **Compute Engine**
3. To create the **Linux Demo VM**. Click **Create instance** and use the following configuration to create a VM. Leave the rest as default.

    Name: **linux-iap**
    Zone: **us-east1-c**
    
    Click on **Advanced options** and select **Networking**. Under **network interfaces** click the defult network to edit. Then change the External IPV4 address to **None**.
    
    Click **Done**.

### Configure the required firewall rules for BCE
1. Open the **Navigation Menu** and select **VPC Network > Firewall** and click **Create Firewall Rule**
2. Configure the following settings:

	- Name: **allow-ingress-from-iap**
	- Direction of traffic: **Ingress**
	- Target: **All instances in the network**
	- Source filter: **IPv4 Ranges**
	- Source IPv4 Ranges: **35.235.240.0/20**
	- Protocols and ports: **Select TCP and enter 22, 3389** to allow both SSH and RDP respectively

3. Click **CREATE** to create the firewall rule.

### Grant permissions to use IAP TCP forwarding
1. Follow the following steps to configure the iap.tunnelResourceAccessor role by VM.
    - Open **Navigation Menu** and select **Security > Identity-Aware Proxy**, switch to the **SSH and TCP Resources** tab (safely ignore the Oauth Consent screen error in the HTTPS section).
    - Select the **linux-iap** and **windows-iap** VM instances
    - Click **Add principal**
    - Enter in the service account associated with your **Windows connectivity** VM.
    - Select **Cloud IAP > IAP-Secured Tunnel User** for the role.
    - Click **SAVE**.
    - From the top-right of the page click the "S" icon to open your profile and copy the email of the student account
    - Click **Add principal** again to add your student account
    - Enter in the student account you have copied
    - Select **Cloud IAP > IAP-Secured Tunnel User** for the role.
    - Click **SAVE**.

The IAP-Secured Tunnel User role will grant the windows-connectivity instance to connect to resources using IAP. Adding the student account will help verify the step was done correctly.

### Use IAP Desktop to Connect to the Windows and Linux Instances
It is possible to use IAP Desktop to connect to instances using a graphical user interface from an instance with Windows Desktop. You can read more about [IAP Desktop](https://github.com/GoogleCloudPlatform/iap-desktop) on the GitHub repository hosting the download for the tool.

To use IAP Desktop to connect to the instances in this lab:

1. RDP to the `windows-connectivity` instance by downloading the RDP file. Go to the **Compute Engine > VM Instances** page. Select the down arrow next to the **windows-connectivity** instance on the Compute Engine landing page and download the file.
2. Open the RDP file to connect to the instance via Remote Desktop Protocol. You will use the credentials below to connect to the instance once prompted:

	- Username: student
	- Password: Learn123!

3. Once connected to the **windows-connectivity** instance, locate and open the IAP Desktop application on the desktop of the instance.
4. Once the application opens, click on the sign in with Google button to log in. Use the username and password provided in the lab console to authenticate with **IAP Desktop**. Make sure you select the option to "See, edit, configure and delete Google Cloud data."
5. You will need to add the project to connect to Compute Engine instances within IAP Desktop after authentication. Select the lab project associated with your lab instance:

	Double click on the **windows-iap** instance in the IAP Desktop application to log into the the instance.

6. You may be prompted to provide credentials for the instance the first time you try to connect to it through IAP Desktop. Select "Generate new credentials" the first time logging into the instance.
7. After the credentials are created you will be taken to the desktop of the `windows-iap` instance and can see the end user experience.

### Demonstrate tunneling using SSH and RDP connections
1. You will testconnectivity to the RDP instance using an RDP client. This is because you need to connect to the instance via an IAP tunnel locally.
2. Go to the **Compute Engine > VM Instances** page.
3. For the **windows-connectivity** instance click the down arrow and select **Set windows password**. Copy the password and save it.

	Then click down arrow next to connect and click download the RDP file. Open the RDP file with your client and enter in your password.

4. Once you have connected to the **windows-connectivity** instance. Open the **Google Cloud Shell SDK**:

	Now from the command line enter the following command to see if you can connect to the **linux-iap instance**:

```shell
gcloud compute ssh linux-iap
```

Click **Y** when promopted to continue and to select the zone.

Make sure that you select the right zone for the instance when prompted.

Then **Accept** the Putty security alert.

You should receive a message that no external IP address was found and that it will use IAP tunneling.

Update Putty Settings to allow Tunnel connections locally. Click the top left corner of the Putty Window > Change Settings.

Allow local ports to accept connections from other hosts by checking the checkbox "Local ports accept connections from other hosts".

5. Close the Putty session and click **Apply**. Use the following command to create an encrypted tunnel to the RDP port of the VM instance:

```shell
gcloud compute start-iap-tunnel windows-iap 3389 --local-host-port=localhost:0  --zone=us-east1-c
```

Once you see the message about “Listening on port [XXX].” Copy the tunnel port number.

6. Return to the Google Cloud Console and go to the **Compute Engine > VM Instances** page.

Set and copy the password for the **windows-iap** instance.

Return to the RDP session now.

Leave gcloud running and open the Microsoft Windows **Remote Desktop Connection** app.

Enter the tunnel endpoint where the endpoint is the tunnel port number from the earlier step like so:

- localhost:endpoint

Click **Connect**.

Then enter the previous credentials you copied earlier You will be successfully RDPed into your instance now!

If prompted click **Yes**.

You were able to access the instance even without an external IP address using IAP

## Lab - Create an Internal Load Balancer

### Overview
Google Cloud offers Internal Load Balancing for your TCP/UDP-based traffic. Internal Load Balancing enables you to run and scale your services behind a private load balancing IP address that is accessible only to your internal virtual machine instances.

In this lab you create two managed instance groups in the same region. Then, you configure and test an Internal Load Balancer with the instances groups as the backends, as shown in this network diagram:

![[Pasted image 20230612104416.png]]

### Configure HTTP and health check firewall rules
Configure firewall rules to allow HTTP traffic to the backends and TCP traffic from the Google Cloud health checker.

#### Explore the my-internal-app network
The network `my-internal-app` with subnet-a and subnet-b along with firewall rules for RDP, SSH, and ICMP traffic have been configured for you.

1. In the Console, navigate to **Navigation menu** > **VPC network** > **VPC networks**.
2. Scroll down and notice the **my-internal-app** network with its subnets: **subnet-a** and **subnet-b**

    Each Google Cloud project starts with the **default** network. In addition, the **my-internal-app** network has been created for you, as part of your network diagram.
    
    You will create the managed instance groups in **subnet-a** and **subnet-b**. Both subnets are in the **us-central1** region because an Internal Load Balancer is a regional service. The managed instance groups will be in different zones, making your service immune to zonal failures.

#### Create the HTTP firewall rule
Create a firewall rule to allow HTTP traffic to the backends from the Load Balancer and the internet (to install Apache on the backends).

1. Still in **VPC network**, in the left pane click **Firewall**.
2. Notice the **app-allow-icmp** and **app-allow-ssh-rdp** firewall rules.

    These firewall rules have been created for you.

3. Click **Create Firewall Rule**.

4. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|app-allow-http|
|Network|my-internal-app|
|Targets|Specified target tags|
|Target tags|lb-backend|
|Source filter|IPv4 Ranges|
|Source IPv4 ranges|0.0.0.0/0|
|Protocols and ports|Specified protocols and ports, and then _check_ tcp, _type:_ 80|

**Note:** Make sure to include the **/0** in the **Source IPv4 ranges** to specify all networks.

5. Click **Create**.

#### Create the health check firewall rules
Health checks determine which instances of a Load Balancer can receive new connections. For Internal load balancing, the health check probes to your load balanced instances come from addresses in the ranges `130.211.0.0/22` and `35.191.0.0/16`. Your firewall rules must allow these connections.

1. Still in the **Firewall rules** page, click **Create Firewall Rule**.
2. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|app-allow-health-check|
|Targets|Specified target tags|
|Target tags|lb-backend|
|Source filter|IPv4 Ranges|
|Source IPv4 ranges|130.211.0.0/22 and 35.191.0.0/16|
|Protocols and ports|Specified protocols and ports, and then _check_ tcp|

**Note:** Make sure to enter the two **Source IPv4 ranges** one-by-one and pressing SPACE in between them.

3. Click **Create**.

### Configure instance templates and create instance groups
A managed instance group uses an instance template to create a group of identical instances. Use these to create the backends of the Internal Load Balancer.

#### Configure the instance templates
An instance template is an API resource that you can use to create VM instances and managed instance groups. Instance templates define the machine type, boot disk image, subnet, labels, and other instance properties. Create an instance template for both subnets of the **my-internal-app** network.

1. In the Console, navigate to **Navigation menu** > **Compute Engine** > **Instance templates**.
2. Click **Create instance template**.
3. For **Name**, type **instance-template-1**.
4. For **Series**, select **N1**.
5. Click **Advanced options**.
6. Click **Networking**.
7. For **Network tags**, specify **lb-backend**.

    **Note:** The network tag **lb-backend** ensures that the **HTTP** and **Health Check** firewall rules apply to these instances.

8. For **Network interfaces**, click the dropdown icon to edit.
9. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|my-internal-app|
|Subnetwork|subnet-a|

10. Click **Done**.
11. Click **Management**.
12. Under **Metadata**, click **Add item** and specify the following:

|Key 1|Value 1|
|---|---|
|startup-script-url|gs://cloud-training/gcpnet/ilb/startup.sh|

**Note:** The **startup-script-url** specifies a script that will be executed when instances are started. This script installs Apache and changes the welcome page to include the client IP and the name, region and zone of the VM instance. Feel free to explore [this script](https://storage.googleapis.com/cloud-training/gcpnet/ilb/startup.sh).

13. Click **Create**.
14. Wait for the instance template to be created.

#### Create the managed instance groups
Create a managed instance group in **subnet-a** (us-central1-a) and one **subnet-b** (us-central1-b).

1. Still in **Compute Engine**, in the left pane click **Instance groups**, and then click **Create Instance group**.
2. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|instance-group-1|
|Instance template|instance-template-1|
|Location|Single-zone|
|Region|us-central1|
|Zone|us-central1-a|
|Autoscaling > Minimum number of instances|1|
|Autoscaling > Maximum number of instances|5|
|Autoscaling > Autoscaling metrics (click the dropdown icon to edit) > Metric type|CPU utilization|
|Target CPU utilization|80|
|Cool-down period|45|

**Note:** Managed instance groups offer **autoscaling** capabilities that allow you to automatically add or remove instances from a managed instance group based on increases or decreases in load. Autoscaling helps your applications gracefully handle increases in traffic and reduces cost when the need for resources is lower. You just define the autoscaling policy and the autoscaler performs automatic scaling based on the measured load.

3. Click **Create**.

    Repeat the same procedure for **instance-group-2** in **us-central1-b**:

4. Click **Create Instance group**.
5. Set the following values, leave all other values at their defaults:

#### Verify the backends
Verify that VM instances are being created in both subnets and create a utility VM to access the backends' HTTP sites.

1. Still in **Compute Engine**, click **VM instances**.
2. Notice two instances that start with `instance-group-1` and `instance-group-2`.

    These instances are in separate zones and their internal IP addresses are part of the **subnet-a** and **subnet-b** CIDR blocks.

3. Click **Create instance**.
4. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|utility-vm|
|Region|us-central1|
|Zone|us-central1-f|
|Series|N1|
|Machine type|f1-micro (1 shared vCPU)|

5. Click **Advanced options**.
6. Click **Networking**.
7. For **Network interfaces**, click the dropdown icon to edit.
8. Set the following values, leave all other values at their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Network|my-internal-app|
|Subnetwork|subnet-a|
|Primary internal IP|Ephemeral (Custom)|
|Custom ephemeral IP address|10.10.20.50|

9. Click **Done** and then click **Create**.
10. Note that the internal IP addresses for the backends are `10.10.20.2` and `10.10.30.2`.

**Note:** If these IP addresses are different, replace them in the two **curl** commands below.

11. For **utility-vm**, click **SSH** to launch a terminal and connect.
12. To verify the welcome page for `instance-group-1-xxxx`, run the following command:

```shell
curl 10.10.20.2
```

**Note:** The **curl** commands demonstrate that each VM instance lists the Client IP and its own name and location. This will be useful when verifying that the Internal Load Balancer sends traffic to both backends.

14. Close the SSH terminal to **utility-vm**:

```shell
exit
```

### Configure the Internal Load Balancer
Configure the Internal Load Balancer to balance traffic between the two backends (**instance-group-1** in us-central1-a and **instance-group-2** in us-central1-b).

#### Start the configuration
1. In the Cloud Console, navigate to **Navigation menu** > **Network Services** > **Load balancing**, and then click **Create load balancer**.
2. Under **TCP Load Balancing**, click on **Start configuration**.
3. For **Internet facing or internal only**, select **Only between my VMs**.

**Note:** Choosing **Only between my VMs** makes this Load Balancer internal. This choice requires the backends to be in a single region (us-central1) and does not allow offloading TCP processing to the Load Balancer.

4. Click **Continue**.
5. For **Name**, type `my-ilb`.
6. For **Region**, select **us-central1**.
7. For **Network**, select **my-internal-app**.

#### Configure the regional backend service
The backend service monitors instance groups and prevents them from exceeding configured usage.

1. Click on **Backend configuration**.
2. Set the following values, leave all other values at their defaults:

|Property|Value (select option as specified)|
|---|---|
|Instance group|instance-group-1 (us-central1-a)|

3. Click **Add backend**.
4. For **Instance group**, select **instance-group-2 (us-central1-b)**.
5. For **Health Check**, select **Create a health check**.
6. Set the following values, leave all other values at their defaults:

|Property|Value (select option as specified)|
|---|---|
|Name|my-ilb-health-check|
|Protocol|TCP|
|Port|80|

**Note:** Health checks determine which instances can receive new connections. This HTTP health check polls instances every 5 seconds, waits up to 5 seconds for a response and treats 2 successful or 2 failed attempts as healthy or unhealthy, respectively.

7. Click **Save**.
8. Click **Done**.
9. Verify that there is a blue check mark next to **Backend configuration** in the Cloud Console. If not, double-check that you have completed all the steps above.

#### Configure the frontend
The frontend forwards traffic to the backend.

1. Click on **Frontend configuration**.
2. Specify the following, leaving all other values with their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Subnetwork|subnet-b|
|Internal IP|Under **IP address** select **Create IP address**|

3. Specify the following, leaving all other values with their defaults:

|Property|Value (type value or select option as specified)|
|---|---|
|Name|my-ilb-ip|
|Static IP address|Let me choose|
|Custom IP address|10.10.30.5|

4. Click **Reserve**.
5. In **Port number**, type `80`.
6. Click **Done** .

#### Review and create the Internal Load Balancer
1. Click on **Review and finalize**.
2. Review the **Backend** and **Frontend**.
3. Click on **Create**. Wait for the Load Balancer to be created, before moving to the next task.

### Test the Internal Load Balancer
Verify that the `my-ilb` IP address forwards traffic to **instance-group-1** in us-central1-a and **instance-group-2** in us-central1-b.

#### Access the Internal Load Balancer
1. In the Cloud Console, navigate to **Navigation menu** > **Compute Engine** > **VM instances**.
2. For **utility-vm**, click **SSH** to launch a terminal and connect.
3. To verify that the Internal Load Balancer forwards traffic, run the following command:

```shell
curl 10.10.30.5
```

**Note:** As expected, traffic is forwarded from the Internal Load Balancer (10.10.30.5) to the backend.

4. Run the same command a couple more times.

In the output, you should be able to see responses from **instance-group-1** in us-central1-a and **instance-group-2** in us-central1-b.


# Data, ML, and AI in Google

## You have the data, but what are you doing with it?

### Introduction to big data managed services in the cloud
Enterprise storage systems are leaving the terabyte behind as a measure of data size, with petabytes becoming the norm.

In this module, we’ll focus on three managed services that Google offers for the processing of data.
 
For companies that have already invested in Apache Hadoop and Apache Spark, and want to continue using these tools, Dataproc provides a great way to run open source software in Google Cloud.

However, companies looking for a streaming data solution might be more interested in Dataflow as a managed service. Dataflow is optimized for large-scale batch processing or long-running stream processing of structured and unstructured data.

The third managed service that we’ll look at is BigQuery, which provides a data analytics solution optimized for getting answers rapidly over petabyte-scale datasets. BigQuery allows for fast SQL on structured data.

### Leverage big data operations with Dataproc
Apache Hadoop and Apache Spark are open source technologies that often are the foundation of big data processing.

Apache Hadoop is a set of tools and technologies which enables a cluster of computers to store and process large volumes of data. It intelligently ties individual computers together in a cluster to distribute the storage and processing of data.

Apache Spark is a unified analytics engine for large-scale data processing and achieves high performance for both batch and stream data.

Dataproc is a managed Spark and Hadoop service that lets you use open source data tools for batch processing, querying, streaming, and machine learning.

Dataproc automation helps you create clusters quickly, manage them easily, and because clusters are typically run ephemerally, you save money as they are turned off when you don't need them.

Let’s look at the key features of Dataproc.

Cost effective: Dataproc is priced at 1 cent per virtual CPU per cluster per hour, on top of any other Google Cloud resources you use. In addition, Dataproc clusters can include preemptible instances that have lower compute prices. You use and pay for things only when you need them.

Fast and scalable: Dataproc clusters are quick to start, scale, and shut down, and each of these operations takes 90 seconds or less, on average. Clusters can be created and scaled quickly with many virtual machine types, disk sizes, number of nodes, and networking options.

Open source ecosystem: You can use Spark and Hadoop tools, libraries, and documentation with Dataproc. Dataproc provides frequent updates to native versions of Spark, Hadoop, Pig, and Hive, so learning new tools or APIs is not necessary, and you can move existing projects or ETL pipelines without redevelopment.

Fully managed: You can easily interact with clusters and Spark or Hadoop jobs, without the assistance of an administrator or special software, through the Google Cloud console, the Google Cloud SDK, or the Dataproc REST API. When you're done with a cluster, simply turn it off, so money isn’t spent on an idle cluster.

Image versioning: Dataproc’s image versioning feature lets you switch between different versions of Apache Spark, Apache Hadoop, and other tools.

Built-in integration: The built-in integration with Cloud Storage, BigQuery, and Cloud Bigtable ensures that data will not be lost. This, together with Cloud Logging and Cloud Monitoring, provides a complete data platform and not just a Spark or Hadoop cluster. For example, you can use Dataproc to effortlessly extract, transform, and load terabytes of raw log data directly into BigQuery for business reporting.

### Lab - Dataproc: Console

#### Overview
Cloud Dataproc is a fast, easy-to-use, fully-managed cloud service for running [Apache Spark](http://spark.apache.org/) and [Apache Hadoop](http://hadoop.apache.org/) clusters in a simpler, more cost-efficient way. Operations that used to take hours or days take seconds or minutes instead. Create Cloud Dataproc clusters quickly and resize them at any time, so you don't have to worry about your data pipelines outgrowing your clusters.

This lab shows you how to use the Google Cloud Console to create a Google Cloud Dataproc cluster, run a simple [Apache Spark](http://spark.apache.org/) job in the cluster, then modify the number of workers in the cluster.

#### Setup and requirements

##### Confirm Cloud Dataproc API is enabled
To create a Dataproc cluster in Google Cloud, the Cloud Dataproc API must be enabled. To confirm the API is enabled:

1. Click **Navigation menu** > **APIs & Services** > **Library**:
2. Type **Cloud Dataproc** in the **Search for APIs & Services** dialog. The console will display the Cloud Dataproc API in the search results.
3. Click on **Cloud Dataproc API** to display the status of the API. If the API is not already enabled, click the **Enable** button.

#### Create a cluster
1. In the Cloud Platform Console, select **Navigation menu** > **Dataproc** > **Clusters**, then click **Create cluster**.
2. Click **Create** for **Cluster on Compute Engine**.
3. Set the following fields for your cluster and accept the default values for all other fields:

**Note:** In the Configure nodes section ensure **both the Master node and Worker nodes** are set to the correct Machine Series and Machine Type

|Field|Value|
|---|---|
|Name|example-cluster|
|Region|`____`|
|Zone|`____`|
|Machine Series|E2|
|Machine Type|e2-standard-2|
|Max Worker Nodes|2|

**Note:** A Zone is a special multi-region namespace that is capable of deploying instances into all Google Compute zones globally. You can also specify distinct regions, such as `us-central1` or `europe-west1`, to isolate resources (including VM instances and Cloud Storage) and metadata storage locations utilized by Cloud Dataproc within the user-specified region.

4. Click **Create** to create the cluster.

Your new cluster will appear in the Clusters list. It may take a few minutes to create, the cluster Status shows as **Provisioning** until the cluster is ready to use, then changes to **Running**.

#### Submit a job
To run a sample Spark job:

1. Click **Jobs** in the left pane to switch to Dataproc's jobs view, then click **Submit job**.
2. Set the following fields to update Job. Accept the default values for all other fields:

|Field|Value|
|---|---|
|Region|`____`|
|Cluster|example-cluster|
|Job type|Spark|
|Main class or jar|org.apache.spark.examples.SparkPi|
|Jar files|file:///usr/lib/spark/examples/jars/spark-examples.jar|
|Arguments|1000 (This sets the number of tasks.)|

3. Click **Submit**.

**Note:** **How the job calculates Pi:** The Spark job estimates a value of Pi using the [Monte Carlo method](https://en.wikipedia.org/wiki/Monte_Carlo_method). It generates x,y points on a coordinate plane that models a circle enclosed by a unit square. The input argument (1000) determines the number of x,y pairs to generate; the more pairs generated, the greater the accuracy of the estimation. This estimation leverages Cloud Dataproc worker nodes to parallelize the computation. For more information, see [Estimating Pi using the Monte Carlo Method](https://academo.org/demos/estimating-pi-monte-carlo/) and see [JavaSparkPi.java on GitHub](https://github.com/Apache/spark/blob/master/examples/src/main/java/org/apache/spark/examples/JavaSparkPi.java).

Your job should appear in the **Jobs** list, which shows your project's jobs with its cluster, type, and current status. Job status displays as **Running**, and then **Succeeded** after it completes.

#### View the job output
To see your completed job's output:

1. Click the job ID in the **Jobs** list.
2. Check **Line wrapping** or scroll all the way to the right to see the calculated value of Pi.

Your job has successfully calculated a rough value for pi!

#### Update a cluster
To change the number of worker instances in your cluster:

1. Select **Clusters** in the left navigation pane to return to the Dataproc Clusters view.
2. Click **example-cluster** in the **Clusters** list. By default, the page displays an overview of your cluster's CPU usage.
3. Click **Configuration** to display your cluster's current settings.
4. Click **Edit**. The number of worker nodes is now editable.
5. Enter **4** in the **Worker nodes** field.
6. Click **Save**.

Your cluster is now updated. Check out the number of VM instances in the cluster.

1. To rerun the job with the updated cluster, you would click **Jobs** in the left pane, then click **SUBMIT JOB**.
2. Set the same fields you set in the **Submit a job** section:
3. Click **Submit**.

### Lab - Dataproc: Command Line

#### Create a cluster
1. In Cloud Shell, run the following command to set the Region:

```shell
gcloud config set dataproc/region us-east1
```

2. Run the following command to create a cluster called `example-cluster` with default Cloud Dataproc settings:

```shell
gcloud dataproc clusters create example-cluster --worker-boot-disk-size 500
```

When you see a "Created" message, you're ready to move on.

#### Submit a job
- Run this command to submit a sample Spark job that calculates a rough value for pi:

```shell
gcloud dataproc jobs submit spark --cluster example-cluster \
  --class org.apache.spark.examples.SparkPi \
  --jars file:///usr/lib/spark/examples/jars/spark-examples.jar -- 1000
```

The command specifies:

- That you want to run a [spark](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/spark) job on the `example-cluster` cluster
- The `class` containing the main method for the job's pi-calculating application
- The location of the jar file containing your job's code
- The parameters you want to pass to the job—in this case, the number of tasks, which is `1000`

**Note:** Parameters passed to the job must follow a double dash (--). See the [gcloud documentation](https://cloud.google.com/sdk/gcloud/reference/dataproc/jobs/submit/spark) for more information.

The job's running and final output is displayed in the terminal window:

#### Update a cluster
1. To change the number of workers in the cluster to four, run the following command:

```shell
gcloud dataproc clusters update example-cluster --num-workers 4
```

2. You can use the same command to decrease the number of worker nodes:

```shell
gcloud dataproc clusters update example-cluster --num-workers 2
```

### Build extract, terraform, and load pipelines using Dataflow
With Dataproc, you can migrate your original big data deployment with Apache Hadoop and Apache Spark to a fully-managed service provided by Google Cloud.

But how do you process both batch and streaming data if it's not Hadoop dependent? This is where Dataflow comes in.

Dataflow is a managed service offered by Google that’s optimized for large-scale batch processing or long-running stream processing. Dataflow creates a pipeline to process both streaming data and batch data.

“Process” in this case refers to the steps to extract, transform, and load data (ETL).

When building a data pipeline, data engineers often encounter challenges related to coding the pipeline design and implementing and serving the pipeline at scale.

During the pipeline design phase, you should consider a few questions: 

* Will the pipeline code be compatible with both batch and streaming data, or will it need to be refactored?
* Will the pipeline code software development kit, or SDK, that’s being used have all the transformations, mid-flight aggregations and windowing?
* Will it be able to handle late data?
* Are there existing templates or solutions that should be referenced?

Dataflow fully automates operational tasks like resource management and performance optimization. All resources are provided on demand, and scale to meet requirements.

Dataflow provides built-in support for fault-tolerant execution that’s consistent and correct regardless of data size, cluster size, processing pattern or pipeline complexity.

Through its integration with the Google Cloud console, Dataflow provides statistics such as pipeline throughput and lag and consolidated worker log inspection—all in near-real time. 

It also integrates with Cloud Storage, Pub/Sub, Datastore, Cloud Bigtable, and BigQuery for seamless data processing between platforms.

### Lab - Dataflow: Templates

#### Overview
In this lab, you will learn how to create a streaming pipeline using one of [Google's Cloud Dataflow templates](https://cloud.google.com/dataflow/docs/templates/provided-templates). More specifically, you will use the Cloud Pub/Sub to BigQuery template, which reads messages written in JSON from a Pub/Sub topic and pushes them to a BigQuery table. You can find the documentation for this template in the [Get started with Google-provided templates Guide](https://cloud.google.com/dataflow/docs/templates/provided-templates#cloudpubsubtobigquery).

#### Setup

##### Ensure that the Dataflow API is successfully enabled
To ensure access to the necessary API, restart the connection to the Dataflow API.

1. In the Cloud Console, enter "Dataflow API" in the top search bar. Click on the result for **Dataflow API**.
2. Click **Manage**.
3. Click **Disable API**.

If asked to confirm, click **Disable**.

4. Click **Enable**.

When the API has been enabled again, the page will show the option to disable.

#### Create a Cloud BigQuery dataset and table Using Cloud Shell
Let's first create a BigQuery dataset and table.

1. Run the following command to create a dataset called `taxirides`:

```shell
bq mk taxirides
```

Now that you have your dataset created, you'll use it in the following step to instantiate a BigQuery table.

2. Run the following command to do so:

```shell
bq mk \
--time_partitioning_field timestamp \
--schema ride_id:string,point_idx:integer,latitude:float,longitude:float,\
timestamp:timestamp,meter_reading:float,meter_increment:float,ride_status:string,\
passenger_count:integer -t taxirides.realtime
```

On its face, the `bq mk` command looks a bit complicated. However, with some assistance from the [BigQuery command-line documentation](https://cloud.google.com/bigquery/docs/reference/bq-cli-reference), we can break down what's going on here. For example, the documentation tells us a little bit more about **schema**:

- Either the path to a local JSON schema file or a comma-separated list of column definitions in the form `[FIELD]`:`[DATA_TYPE]`, `[FIELD]`:`[DATA_TYPE]`.

In this case, we are using the latter—a comma-separated list.

#### Create a Cloud BigQuery dataset and table using the Cloud Console
1. From the left-hand menu, in the Big Data section, click on **BigQuery**.
2. Then click **Done**.
3. Click on the three dots next to your project name under the **Explorer** section, then click **Create dataset**.
4. Input `taxirides` as your dataset ID:
5. Select **us (multiple regions in United States)** in Data location.
6. Leave all of the other default settings in place and click **CREATE DATASET**.
7. You should now see the `taxirides` dataset underneath your project ID in the left-hand console.
8. Click on the three dots next to `taxirides` dataset and select **Open**.
9. Then select **CREATE TABLE** in the right-hand side of the console.
10. In the **Destination** > **Table Name** input, enter `realtime`.
11. Under Schema, toggle the **Edit as text** slider and enter the following:

```shell
ride_id:string,point_idx:integer,latitude:float,longitude:float,timestamp:timestamp,
meter_reading:float,meter_increment:float,ride_status:string,passenger_count:integer
```

#### Run the pipeline
1. From the **Navigation menu**, find the Analytics section and click on **Dataflow**.
2. Click on **+ Create job from template** at the top of the screen.
3. Enter **iotflow** as the **Job name** for your Cloud Dataflow job and select for **Regional Endpoint**.
4. Under **Dataflow Template**, select the **Pub/Sub Topic to BigQuery** template.
5. Under **Input Pub/Sub topic**, click **Enter Topic Manually** and enter:

```shell
projects/pubsub-public-data/topics/taxirides-realtime
```

6. Under **BigQuery output table**, enter the name of the table that was created:

```shell
"filled in at lab start":taxirides.realtime
```

7. Add your bucket name as **Temporary Location** after `gs://`:

```shell
"filled in at lab start"/temp
```

8. Click the **Run job** button.

You'll watch your resources build and become ready for use.

Now, let's go view the data written to BigQuery by clicking on **BigQuery** found in the Navigation menu.

- When the BigQuery UI opens, you'll see the **taxirides** dataset added under your project name and **realtime** table underneath that.

#### Submit a query
You can submit queries using standard SQL.

1. In the BigQuery **Editor**, add the following to query the data in your project:

```sql
SELECT * FROM `"filled in at lab start".taxirides.realtime` LIMIT 1000
```

2. Now click **RUN**.

If you run into any issues or errors, run the query again (the pipeline takes a minute to start up.)

3. When the query runs successfully, you'll see the output in the **Query Results**.

Great work! You just pulled 1000 taxi rides from a Pub/Sub topic and pushed them to a BigQuery table.
 
### Lab - Dataflow: Python

#### Overview
In this lab you will set up your Python development environment, get the Cloud Dataflow SDK for Python, and run an example pipeline using the Cloud Console.

#### Install pip and the Cloud Dataflow SDK
1. The latest Cloud Dataflow SDK for Python requires a Python version >= 3.7.

To ensure you are running the process with the correct version, run the `Python3.9` Docker Image:

```shell
docker run -it -e DEVSHELL_PROJECT_ID=$DEVSHELL_PROJECT_ID python:3.9 /bin/bash
```

This command pulls a Docker container with the latest stable version of Python 3.9 and then opens up a command shell for you to run the following commands inside your container.

2. After the container is running, install the latest version of the Apache Beam for Python by running the following command from a virtual environment:

```shell
pip install 'apache-beam[gcp]'==2.42.0
```

You will see some warnings returned that are related to dependencies. It is safe to ignore them for this lab.

3. Run the `wordcount.py` example locally by running the following command:

```shell
python -m apache_beam.examples.wordcount --output OUTPUT_FILE
```

**Note:** You installed `google-cloud-dataflow` but are executing `wordcount` with `Apache_beam`. The reason for this is that Cloud Dataflow is a distribution of [Apache Beam](https://github.com/Apache/beam).

You may see a message similar to the following:

```
INFO:root:Missing pipeline option (runner). Executing pipeline using the default runner: DirectRunner.
INFO:oauth2client.client:Attempting refresh to obtain initial access_token
```

This message can be ignored.

4. You can now list the files that are on your local cloud environment to get the name of the `OUTPUT_FILE`:

```shell
ls
```

5. Copy the name of the `OUTPUT_FILE` and `cat` into it:

```shell
cat <file name>
```

Your results show each word in the file and how many times it appears.

#### Run an example pipeline remotely
1. Set the BUCKET environment variable to the bucket you created earlier:

```shell
BUCKET=gs://<bucket name provided earlier>
```

2. Now you'll run the `wordcount.py` example remotely:

```shell
python -m apache_beam.examples.wordcount --project $DEVSHELL_PROJECT_ID \
  --runner DataflowRunner \
  --staging_location $BUCKET/staging \
  --temp_location $BUCKET/temp \
  --output $BUCKET/results/output \
  --region "filled in at lab start"
```

In your output, wait until you see the message:

```
JOB_MESSAGE_DETAILED: Workers have started successfully.
```

#### Check that your job succeeded
1. Open the Navigation menu and click **Dataflow** from the list of services.

You should see your **wordcount** job with a **status** of **Running** at first.

2. Click on the name to watch the process. When all the boxes are checked off, you can continue watching the logs in Cloud Shell.

The process is complete when the status is **Succeeded**.

3. Click **Navigation menu** > **Cloud Storage** in the Cloud Console.
4. Click on the name of your bucket. In your bucket, you should see the **results** and **staging** directories.
5. Click on the **results** folder and you should see the output files that your job created:
6. Click on a file to see the word counts it contains.

### BigQuery, Google's Enterprise Data Warehouse
BigQuery is a fully-managed, serverless data warehouse. A data warehouse is a large store that contains terabytes and petabytes of data gathered from a wide range of sources within an organization, and it’s used to guide management decisions.

Being fully managed means that BigQuery takes care of the underlying infrastructure, so you can focus on using SQL queries to answer business questions without worrying about deployment, scalability, and security.

Let’s look at some key features of BigQuery. 

1. BigQuery provides two services in one: storage plus analytics. It’s a place to store petabytes of data. BigQuery is also a place to analyze data, with built-in features like machine learning, geospatial analysis, and business intelligence.
2. BigQuery is a fully managed serverless solution, which means that you use SQL queries to answer your organization's biggest questions in the frontend without worrying about infrastructure in the backend.
3. BigQuery has a flexible pay-as-you-go pricing model where you pay for the number of bytes of data your query processes and for any permanent table storage. If you prefer to have a fixed bill every month, you can also subscribe to flat-rate pricing where you have a reserved amount of resources for use.
4. Data in BigQuery is encrypted at rest by default without any action required from a customer. By encryption at rest, we mean that encryption is used to protect data that is stored on a disk, including solid-state drives or backup media.
5. BigQuery has built-in machine learning features, so you can write ML models directly in BigQuery by using SQL. Also, if you use other professional tools—such as Vertex AI from Google Cloud—to train your ML models, you can export datasets from BigQuery directly into Vertex AI for a seamless integration across the data-to-AI lifecycle.

So what does the typical architecture of a data warehouse solution look like?

The input data can be either real-time or batch data. If it's streaming data, which can be either structured or unstructured, high speed, and large volume, Pub/Sub is needed to digest the data. If it’s batch data, it can be directly uploaded to Cloud Storage.

After that, both pipelines lead to Dataflow to process the data. Dataflow is where we extract, transform, and load the data if needed.

BigQuery sits in the middle to link data processes by using Dataflow and data access through analytics, AI, and ML tools. The job of the analytics engine of BigQuery at the end of a data pipeline is to ingest all the processed data after ETL, store and analyze it, and then possibly output it for further use such as data visualization and machine learning.

BigQuery outputs usually feed into two buckets: business intelligence tools and AI/ML tools.

If you’re a business analyst or data analyst, you can connect to visualization tools like Looker, Looker Studio, Tableau, and other BI tools. If you prefer to work in spreadsheets, you can query both small or large BigQuery datasets directly from Google Sheets and even perform common operations like pivot tables.

Alternatively if you’re a data scientist or machine learning engineer, you can directly call the data from BigQuery through AutoML or Vertex AI Workbench. These AI/ML tools are part of Vertex AI, Google's unified ML platform.

BigQuery is like a common staging area for data analytics workloads. When your data is there, business analysts, BI developers, data scientists, and machine learning engineers can be granted access to your data for their own insights.

BigQuery can ingest datasets from various sources, including: 

* Internal data, which is data saved directly in BigQuery,
* External data. BigQuery also offers the option to query external data sources–like data stored in other Google Cloud storage services such as Cloud Storage, or in other Google Cloud database services, such as Spanner or Cloud SQL–and bypass BigQuery managed storage. This means that a raw CSV file in Cloud Storage or a Google Sheet can be used to write a query without being ingested by BigQuery first.
* Multi-cloud data, which is data stored in multiple cloud services, such as AWS or Azure
* Public datasets. If you don't have data of your own, you can analyze any of the public datasets available in the Cloud Marketplace.

After the data is stored in BigQuery, it’s fully managed and is automatically replicated, backed up, and set up to autoscale.

You can use three basic patterns to load data into BigQuery:

The first is a batch load, where source data is loaded into a BigQuery table in a single batch operation. This can be a one-time operation or it can be automated to occur on a schedule. A batch load operation can create a new table or append data into an existing table.

The second is streaming, where smaller batches of data are streamed continuously so that the data is available for querying in near-real time.

And the third is generated data, where SQL statements are used to insert rows into an existing table or to write the results of a query to a table.

Of course, the purpose of BigQuery is not to just store data; it’s for analyzing data and helping to make business decisions. BigQuery is optimized for running analytic queries over large datasets. It can perform queries on terabytes of data in seconds and petabytes in minutes. This performance lets you analyze large datasets efficiently and get insights in near real time.

Looker, Looker Studio, and many integrated partner tools can be used to draw analytics from BigQuery and build sophisticated interactive data visualizations.

BigQuery also has built-in capabilities for building machine learning models.

An ML model lets you solve certain kinds of problems at scale by using data examples, but without the need for custom code. Machine learning on large datasets requires extensive programming and knowledge of ML frameworks. These requirements restrict solution development to a small set of people within each company, and they exclude data analysts who understand the data but have limited machine learning knowledge and programming expertise.

BigQuery ML empowers data analysts to use machine learning through existing SQL tools and skills. Analysts can use BigQuery ML to build and evaluate ML models in BigQuery. Analysts no longer need to export small amounts of data to spreadsheets or other applications, and they no longer need to wait for limited resources from a data science team.

BigQuery ML functionality is available by using: 

* The BigQuery web UI 
* The bq command-line tool
* The BigQuery REST API
* An external tool such as a Jupyter notebook or business intelligence platform

### Lab - Dataprep

#### Overview
[Cloud Dataprep by Trifacta](https://cloud.google.com/dataprep/) is an intelligent data service for visually exploring, cleaning, and preparing data for analysis. Cloud Dataprep is serverless and works at any scale. There is no infrastructure to deploy or manage. Easy data preparation with clicks and no code!

In this lab you use Dataprep to manipulate a dataset. You import datasets, correct mismatched data, transform data, and join data.

#### Initialize Cloud Dataprep
1. Select **Navigation menu** > **Dataprep**.
2. Check to accept the Google Dataprep Terms of Service, then click **Accept**.
3. Check to authorize sharing your account information with Trifacta, then click **Agree and Continue**.
4. Click **Allow** to allow Trifacta to access project data.
5. Click your student username to sign in to Cloud Dataprep by Trifacta. Your username is the **Username** in the left panel in your lab.
6. Click **Allow** to grant Cloud Dataprep access to your Google Cloud lab account.
7. Check to agree to Trifacta Terms of Service, and then click **Accept**.
8. Click **Continue** on the **First time setup** screen to create the default storage location.

Dataprep opens.

#### Create a flow
Cloud Dataprep uses a `flow` workspace to access and manipulate datasets.

1. Click **Flows** icon, then the **Create** button, then select **Blank Flow** :
2. Click on **Untitled Flow**, then name and describe the flow.
3. Click **OK**.

#### Import datasets
In this section you import and add data to the FEC-2016 flow.

1. Click **Add Datasets**, then select the **Import Datasets** link.
2. In the left menu pane, select **Cloud Storage** to import datasets from Cloud Storage, then click on the pencil to edit the file path.
3. Type `gs://spls/gsp105` in the **Choose a file or folder** text box, then click **Go**.

You may have to widen the browser window to see the **Go** and **Cancel** buttons.

4. Click **us-fec/**.
5. Click the **+** icon next to `cn-2016.txt` to create a dataset shown in the right pane. Click on the title in the dataset in the right pane and rename it "Candidate Master 2016".
6. In the same way add the `itcont-2016-orig.txt` dataset, and rename it "Campaign Contributions 2016".
7. Both datasets are listed in the right pane; click **Import & Add to Flow**.

You see both datasets listed as a flow.

#### Prep the candidate file
1. By default, the Candidate Master 2016 dataset is selected. In the right pane, click **Edit Recipe**.

The Candidate Master 2016 Transformer page opens in the grid view. The Transformer page is where you build your transformation recipe and see the results applied to the sample. When you are satisfied with what you see, execute the job against your dataset.

2. Each of the column heads have a Name and value that specify the data type. To see data types, click the column icon:
3. Notice also that when you click the name of the column, a **Details** panel opens on the right.
4. Click **X** in the top right of the Details panel to close the **Details** panel.

In the following steps you explore data in the grid view and apply transformation steps to your recipe.

1. Column5 provides data from 1990-2064. Widen column5 (like you would on a spreadsheet) to separate each year. Click to select the tallest bin, which represents the year 2016.

This creates a step where these values are selected.

2. In the **Suggestions** panel on the right, in the **Keep rows** section, click **Add** to add this step to your recipe.

The Recipe panel on the right now has the following step:

`Keep rows where(DATE(2016, 1, 1) <= column5) && (column5 < DATE(2018, 1, 1))`

3. In Column6 (State), hover over and click on the mismatched (red) portion of the header to select the mismatched rows.

Scroll down to the bottom (highlighted in red) find the mismatched values and notice how most of these records have the value "P" in column7, and "US" in column6. The mismatch occurs because column6 is marked as a "State" column (indicated by the flag icon), but there are non-state (such as "US") values.

4. To correct the mismatch, click **X** in the top of the Suggestions panel to cancel the transformation, then click on the flag icon in Column6 and change it to a "String" column.

There is no longer a mismatch and the column marker is now green.

5. Filter on just the presidential candidates, which are those records that have the value "P" in column7. In the histogram for column7, hover over the two bins to see which is "H" and which is "P". Click the "P" bin.
6. In the right Suggestions panel, click **Add** to accept the step to the recipe.

#### Wrangle the Contributions file and join it to the Candidates file
On the Join page, you can add your current dataset to another dataset or recipe based on information that is common to both datasets.

Before you join the Contributions file to the Candidates file, clean up the Contributions file.

1. Click on **FEC-2016** (the dataset selector) at the top of the grid view page.
2. Click to select the grayed out **Campaign Contributions 2016**.
3. In the right pane, click **Add** > **Recipe**, then click **Edit Recipe**.
4. Click the **recipe** icon at the top right of the page, then click **Add New Step**.

Remove extra delimiters in the dataset.

5. Insert the following Wrangle language command in the Search box:

```
replacepatterns col: * with: '' on: `{start}"|"{end}` global: true
```

The Transformation Builder parses the Wrangle command and populates the Find and Replace transformation fields.

6. Click **Add** to add the transform to the recipe.
7. Add another new step to the recipe. Click **New Step**, then type "Join" in the Search box.
8. Click **Join datasets** to open the Joins page.
9. Click on "Candidate Master 2016" to join with Campaign Contributions 2016, then **Accept** in the bottom right.
10. On the right side, hover in the Join keys section, then click on the pencil (Edit icon).

Dataprep infers common keys. There are many common values that Dataprep suggests as Join Keys.

11. In the Add Key panel, in the Suggested join keys section, click **column2 = column11**.
12. Click **Save and Continue**.

Columns 2 and 11 open for your review.

13. Click **Next**, then check the checkbox to the left of the "Column" label to add all columns of both datasets to the joined dataset.
14. Click **Review**, and then **Add to Recipe** to return to the grid view.

#### Summary of data
Generate a useful summary by aggregating, averaging, and counting the contributions in Column 16 and grouping the candidates by IDs, names, and party affiliation in Columns 2, 24, 8 respectively.

1. At the top of the Recipe panel on the right, click on **New Step** and enter the following formula in the **Transformation** search box to preview the aggregated data.

```
pivot value:sum(column16),average(column16),countif(column16 > 0) group: column2,column24,column8
```

An initial sample of the joined and aggregated data is displayed, representing a summary table of US presidential candidates and their 2016 campaign contribution metrics.

2. Click **Add** to open a summary table of major US presidential candidates and their 2016 campaign contribution metrics.

#### Rename columns
You can make the data easier to interpret by renaming the columns.

1. Add each of the renaming and rounding steps individually to the recipe by clicking **New Step**, then enter:

```
rename type: manual mapping: [column24,'Candidate_Name'], [column2,'Candidate_ID'],[column8,'Party_Affiliation'], [sum_column16,'Total_Contribution_Sum'], [average_column16,'Average_Contribution_Sum'], [countif,'Number_of_Contributions']
```

2. Then click **Add**.
3. Add in this last **New Step** to round the Average Contribution amount:

```
set col: Average_Contribution_Sum value: round(Average_Contribution_Sum)
```

4. Then click **Add**.

## Let machines do the work

### Machine learning in the cloud
Artificial intelligence, or AI, is an umbrella term that includes anything related to computers mimicking human intelligence.

Machine learning is a toolset.

Deep learning is a subset of machine learning that adds layers in between input data and output results to make a machine learn at more depth. It’s a type of machine learning that works even when the data is unstructured, like images, speech, video, natural language text, and so on.

Image classification is a type of deep learning. A machine can learn how to classify images into categories when it is shown lots of examples.

The basic difference between machine learning and other techniques in AI is that in machine learning, machines learn. They don’t start out intelligent, they become intelligent.

So, how do machines become intelligent? Intelligence requires training. To train a machine learning model, examples are required. 

The first stage of ML is to train an ML model with examples. An example consists of an input and the correct answer for that input. This is called the label.

In the case of structured data–that is, rows and columns–an input can simply be a single row of data. In unstructured data, like images, an input could be a single image of a cloud that you want to classify as a rain cloud or not.

An important detail to emphasize is that a machine learning model is only as good as the data used to train it.

The basic reason why ML models need high-quality data is because they don’t have human general knowledge; data is the only thing they have access to.

After the model has been trained, it can be used to make predictions on data it has never seen before.

Algorithms, or ML models, are standard. That means that they exist independently of the use case.

ResNet, for example, is a standard algorithm for image classification. It’s not essential to understand how an image classification algorithm works, only that it’s the algorithm that we should use if we want to classify images of automotive parts.

When we use the same algorithm on different datasets, different features or inputs are relevant to the different use cases.

The logic is different, but machine learning doesn’t use logical rules. The image classification network isn’t a set of basic ‘if this, then that’ rules, but rather a function that learns how to differentiate between categories of images. So, although you start with the same standard algorithm, after training, the trained model that classifies leaves is different from the trained model that classifies parts.

And you can actually reuse the same code for other use cases that are focused on the same kind of task. However, you still have to train it separately for each use case.

Much of the excitement around ML is because the barriers to entry have fallen. You don’t need to be an astrophysicist to do machine learning! This is because of the convergence of several factors:

- The increasing availability of data 
- The increasing maturity and sophistication of ML algorithms 
- The increasing power and availability of computing hardware and software.

Google Cloud offers four options for building machine learning models.

The first option is BigQuery ML. You’ll remember from the previous module of this course that BigQuery ML is a tool for using SQL queries to create and execute machine learning models in BigQuery. If you already have your data in BigQuery and your problems fit the predefined ML models, this could be your best choice.

The second option is AutoML, which is a no-code solution, so you can build your own machine learning models on Vertex AI through a point-and-click interface.

The third option is custom training, through which you can code your own machine learning environment, the training, and the deployment, which provides you with flexibility and control over the ML pipeline.

And finally, there are pre-built APIs, which are application programming interfaces. This option lets you use machine learning models that have already been built and trained by Google, so you don’t have to build your own machine learning models if you don’t have enough training data or sufficient machine learning expertise in-house.

It’s called a deep neural network or DNN. The layers are meant to mimic our own human brains in the way we perceive stimuli.

The TensorFlow neural network playground at playground.tensorflow.org is a great interactive learning tool for understanding “how computers think” and shows how far ML has come that e can build these models at scale like in Google Photos.

### Building ML models with Vertex AI
Google’s solution to many of the production and ease-of-use challenges is Vertex AI, a unified platform that brings all the components of the machine learning ecosystem and workflow together.

So, what exactly does a unified platform mean? In the case of Vertex AI, it means having one digital experience to create, manage, and deploy models over time, and at scale.

For example, During the data readiness stage, users can upload data from wherever it’s stored: Cloud Storage, BigQuery, or a local machine.

Then, during the feature readiness stage, users can create features, which are the processed data that will be put into the model, and then share them with others by using the feature store.

After that, it’s time for training and hyperparameter tuning. This means that when the data is ready, users can experiment with different models and adjust hyperparameters.

And finally, during deployment and model monitoring, users can set up the pipeline to transform the model into production by automatically monitoring and performing continuous improvements.

And to refer back to the different options that we explored earlier, Vertex AI allows users to build machine learning models with either AutoML, a no-code solution, or Custom Training, a code-based solution.

AutoML is easy to use and lets data scientists spend more time turning business problems into ML solutions, but custom training enables data scientists to have full control over the development environment and process.

Being able to perform such a wide range of tasks in one unified platform has many benefits. This can be summarized with four Ss: 

It’s seamless. Vertex AI provides a smooth user experience from uploading and preparing data all the way to model training and production.

It’s scalable. The machine learning operations (MLOps) provided by Vertex AI helps to monitor and manage the ML production and therefore scale the storage and computing power automatically.

It’s sustainable. All of the artifacts and features created with Vertex AI can be reused and shared.

And it’s speedy. Vertex AI produces models that have 80% fewer lines of code than competitors.

### Lab - Vertex AI

#### Overview
In this lab, you will use [BigQuery](https://cloud.google.com/bigquery) for data processing and exploratory data analysis and the [Vertex AI](https://cloud.google.com/vertex-ai) platform to train and deploy a custom TensorFlow Regressor model to predict customer lifetime value. The goal of the lab is to introduce to Vertex AI through a high value real world use case - predictive CLV. You will start with a local BigQuery and TensorFlow workflow that you may already be familiar with and progress toward training and deploying your model in the cloud with Vertex AI.

Vertex AI is Google Cloud's next generation, unified platform for machine learning development and the successor to AI Platform announced at Google I/O in May 2021. By developing machine learning solutions on Vertex AI, you can leverage the latest ML pre-built components and AutoML to significantly enhance development productivity, the ability to scale your workflow and decision making with your data, and accelerate time to value.

#### Enable Google Cloud services
- In Cloud Shell, use `gcloud` to enable the services used in the lab:

```shell
gcloud services enable \
  compute.googleapis.com \
  iam.googleapis.com \
  iamcredentials.googleapis.com \
  monitoring.googleapis.com \
  logging.googleapis.com \
  notebooks.googleapis.com \
  aiplatform.googleapis.com \
  bigquery.googleapis.com \
  artifactregistry.googleapis.com \
  cloudbuild.googleapis.com \
  container.googleapis.com
```

#### Create Vertex AI custom service account for Vertex Tensorboard integration
1. Create custom service account:

```shell
SERVICE_ACCOUNT_ID=vertex-custom-training-sa
gcloud iam service-accounts create $SERVICE_ACCOUNT_ID  \
    --description="A custom service account for Vertex custom training with Tensorboard" \
    --display-name="Vertex AI Custom Training"
```

2. Grant it access to Cloud Storage for writing and retrieving Tensorboard logs:

```shell
PROJECT_ID=$(gcloud config get-value core/project)
gcloud projects add-iam-policy-binding $PROJECT_ID \
    --member=serviceAccount:$SERVICE_ACCOUNT_ID@$PROJECT_ID.iam.gserviceaccount.com \
    --role="roles/storage.admin"
```

3. Grant it access to your BigQuery data source to read data into your TensorFlow model:

```shell
gcloud projects add-iam-policy-binding $PROJECT_ID \
    --member=serviceAccount:$SERVICE_ACCOUNT_ID@$PROJECT_ID.iam.gserviceaccount.com \
    --role="roles/bigquery.admin"
```

4. Grant it access to Vertex AI for running model training, deployment, and explanation jobs:

```shell
gcloud projects add-iam-policy-binding $PROJECT_ID \
    --member=serviceAccount:$SERVICE_ACCOUNT_ID@$PROJECT_ID.iam.gserviceaccount.com \
    --role="roles/aiplatform.user"
```

#### Launch Vertex AI Workbench notebook
To create and launch a Vertex AI Workbench notebook:

1. In the **Navigation Menu** ![Navigation menu icon](https://cdn.qwiklabs.com/tkgw1TDgj4Q%2BYKQUW4jUFd0O5OEKlUMBRYbhlCrF0WY%3D), click **Vertex AI** > **Workbench**.
2. On the **Workbench** page, click **Enable Notebooks API** (if it isn't enabled yet), then click **New Notebook**.
3. In the **Customize instance** menu, select **TensorFlow Enterprise** and choose the latest version of **TensorFlow Enterprise 2.x (with LTS)** > **Without GPUs**.
4. Name the notebook.
5. Set **Region** to `<filled in at lab start>` and **Zone** to any zone within the designated region.
6. In the **Notebook properties**, click the pencil icon ![pencil icon](https://cdn.qwiklabs.com/zxK8nW520maN72Qq6D1Lt9gCeDh7QOMGWCwhny5S8sQ%3D) to edit the instance properties.
7. Click **Machine type** and then select **e2-standard-2** for Machine type.
8. Leave the remaining fields at their default and click **Create**.

After a few minutes, the **Workbench** page lists your instance, followed by **Open JupyterLab**.

9. Click **Open JupyterLab** to open JupyterLab in a new tab. If you get a message saying beatrix jupyterlab needs to be included in the build, just ignore it.

#### Clone the lab repository
Next you'll clone the `training-data-analyst` repo to your JupyterLab instance.

To clone the `training-data-analyst` repository in your JupyterLab instance:

1. In JupyterLab, click the **Terminal** icon to open a new terminal.
2. At the command-line prompt, type the following command and press **ENTER**:

```shell
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```

3. To confirm that you have cloned the repository, in the left panel, double click the `training-data-analyst` folder to see its contents.

It will take several minutes for the repo to clone.

#### Install lab dependencies
- Run the following to go to the `training-data-analyst/self-paced-labs/vertex-ai/vertex-ai-qwikstart` folder, then `pip3 install` `requirements.txt` to install lab dependencies:

```shell
cd training-data-analyst/self-paced-labs/vertex-ai/vertex-ai-qwikstart
pip3 install --user -r requirements.txt
```

##### Navigate to lab notebook
1. In your notebook, navigate to **training-data-analyst** > **self-paced-labs** > **vertex-ai** > **vertex-ai-qwikstart**, and open **lab_exercise.ipynb**.
2. Continue the lab in the notebook, and run each cell by clicking the **Run** icon at the top of the screen.

Alternatively, you can execute the code in a cell with **SHIFT + ENTER**.

Read the narrative and make sure you understand what's happening in each cell.
 
### AutoML
AutoML is a no-code solution to build ML models through Vertex AI. It allows users to train high-quality custom machine learning models with minimal effort or machine learning expertise.

To understand AutoML, which is short for automated machine learning, let’s briefly look at how it was built. If you've worked with ML models before, you know that training and deploying ML models can be incredibly time consuming, because you need to repeatedly add new data and features, try different models, and tune parameters to achieve the best result.

To solve this problem, when AutoML was first announced in January of 2018, the goal was to automate machine learning pipelines to save data scientists from manual work, such as tuning hyperparameters and comparing against multiple models.

But how could this be done? Well, machine learning is similar to human learning. It all starts with gathering the right information. For AutoML, two technologies are critical.

The first is known as transfer learning. With transfer learning, you build a knowledge base in the field.

Transfer learning is a powerful technique that lets people with smaller datasets, or less computational power, achieve state-of-the-art results by using pre-trained models that have been trained on similar, larger datasets.

Because the model learns through transfer learning, it doesn’t have to learn from the beginning, so it can generally reach higher accuracy with much less data and computation time than models that don’t use transfer learning.

The second technology is neural architect search. The goal of neural architect search is to find the optimal model for the relevant project.

AutoML is powered by the latest machine-learning research, so although a model performs training, the AutoML platform actually trains and evaluates multiple models and compares them to each other. This neural architecture search produces an ensemble of ML models and chooses the best one.

One of the biggest benefits is that it’s a no-code solution. That means it can train high-quality custom machine learning models with minimal effort and requires little machine learning expertise.

This allows data scientists to focus their time on tasks like defining business problems or evaluating and improving model results. Others might find AutoML useful to quickly prototype models and explore new datasets before investing in development. This might involve using it to identify the best features in a dataset, for example.

AutoML supports four types of data: image, tabular, text, and video.

For each data type, AutoML solves different types of problems, called objectives.

To get started, upload your data into AutoML. It can come from Cloud Storage, BigQuery, or even your local machine.

From there, inform AutoML of the problems you want to solve. Some problems might sound similar to those mentioned in pre-built APIs. However, the major difference is that pre-built APIs use pre-built machine learning models, but AutoML uses custom-built models.

In AutoML, you use your own data to train the machine learning model and then apply the trained model to predict your goal. But in pre-built APIs, the models are already trained with Google’s datasets. You use the training results to predict your data.

In reality, you may not be restricted to just one data type and one objective but rather need to combine different objectives to solve a business problem. AutoML is a powerful tool that can help across these different data types and objectives.

### Custom training
Custom training lets you code your own ML environment to control the entire ML development process, starting from data preparation to model deployment. If you want to code your machine learning model, you can use this option by building a custom training solution with Vertex AI Workbench.

Workbench is a single development environment for the entire data science workflow, from exploring, to training, and then deploying a machine learning model with code.

Before any coding begins, you must determine what environment you want your ML training code to use. There are two options: a pre-built container or a custom container.

So, if your ML training needs a platform like TensorFlow, Pytorch, scikit-learn, or XGboost, and Python code to work with the platform, a pre-built container is probably your best solution.

### Pre-built APIs
When using AutoML, you define a domain-specific labeled training dataset that is used to create the custom ML model you require. However, if you don’t need a domain-specific dataset, Google’s suite of pre-built ML APIs might meet your needs.

Good machine learning models require lots of high-quality training data. You should aim for hundreds of thousands of records to train a custom model. If you don't have that kind of data, pre-built APIs are a great place to start.

Pre-built APIs are offered as services. Often they can act as building blocks to create the application you want without the expense or complexity of creating your own models.

They save the time and effort of building, curating, and training a new dataset, so you can directly deal with predictions.

So, what are some of the pre-built APIs?

The Speech-to-Text API converts audio to text for data processing.

The Cloud Natural Language API recognizes parts of speech called entities and sentiment.

The Cloud Translation API converts text from one language to another.

The Text-to-Speech API converts text into high-quality voice audio.

The Vision API works with and recognizes content in static images.

And the Video Intelligence API recognizes motion and action in video.

### Lab - Cloud Natural Language API

#### Overview
"_Natural language_ is the language that humans use to communicate with each other. Natural language processing (NLP) is a field of computer science that is concerned with the interaction between computers and human language. NLP research has the goal of enabling computers to understand and process human language in a way that is similar humans.

The Cloud Natural Language API is a cloud-based service that provides natural language processing capabilities. It can be used to analyze text, identify entities, extract information, and answer questions.

##### Cloud Natural Language API features
**Entity Recognition:** Identify entities in text, such as people, places, and things.

**Sentiment Analysis:** Analyze the sentiment of text, such as whether it is positive, negative, or neutral.

**Information Extraction:** Extract information from text, such as dates, times, and price.

**Question Answering:** Answer questions about text.

**Integrated REST API:** Access via REST API. Text can be uploaded in the request or integrated with [Cloud Storage.](https://cloud.google.com/storage/)

#### Create an API key
1. First, you will set an environment variable with your PROJECT_ID which you will use throughout this lab:

```shell
export GOOGLE_CLOUD_PROJECT=$(gcloud config get-value core/project)
```

2. Next, create a new service account to access the Natural Language API:

```shell
gcloud iam service-accounts create my-natlang-sa \
  --display-name "my natural language service account"
```

3. Then, create credentials to log in as your new service account. Create these credentials and save it as a JSON file "~/key.json" by using the following command:

```shell
gcloud iam service-accounts keys create ~/key.json \
  --iam-account my-natlang-sa@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com
```

4. Finally, set the GOOGLE_APPLICATION_CREDENTIALS environment variable. The environment variable should be set to the full path of the credentials JSON file you created, which you can see in the output from the previous command:

```shell
export GOOGLE_APPLICATION_CREDENTIALS="/home/USER/key.json"
```

#### Make an entity analysis request
In order to perform next steps please connect to the instance provisioned for you via ssh. Open the navigation menu and select **Compute Engine**.

1. Click on the **SSH** button. You will be brought to an interactive shell. **Remain in this SSH session for the rest of the lab.**

Now you'll try out the Natural Language API's entity analysis with the following sentence:

_Michelangelo Caravaggio, Italian painter, is known for 'The Calling of Saint Matthew'_

2. Run the following `gcloud` command:

```shell
gcloud ml language analyze-entities --content="Michelangelo Caravaggio, Italian painter, is known for 'The Calling of Saint Matthew'." > result.json
```

3. Run the below command to preview the output of result.json file:

```shell
cat result.json
```

Read through your results. For each "entity" in the response, you'll see:

- The entity `name` and `type`, a person, location, event, etc.
- `metadata`, an associated Wikipedia URL if there is one.
- `salience`, and the indices of where this entity appeared in the text. Salience is a number in the `[0,1]` range that refers to the centrality of the entity to the text as a whole.
- `mentions`, which is the same entity mentioned in different ways.

You've sent your first request to the Cloud Natural Language API.

### Lab - Google Cloud Speech API

#### Overview
The Google Cloud Speech API enables easy integration of Google speech recognition technologies into developer applications. The Speech API allows you to send audio and receive a text transcription from the service. For more information, see [What is the Google Cloud Speech API?](https://cloud.google.com/speech/docs/)

#### Create an API key
Since you'll be using `curl` to send a request to the Speech API, you need to generate an API key to pass in our request URL.

1. To create an API key, click **Navigation menu** > **APIs & services** > **Credentials**.
2. Then click **Create credentials**.
3. In the drop down menu, select **API key**.
4. Copy the key you just generated and click **Close**.

To perform the next steps, connect using SSH to the instance provisioned for you.

1. In the **Navigation menu**, select **Compute Engine**. You should see a `linux-instance` listed in the **VM instances** window.
2. Click on the **SSH** button in line with the `linux-instance`. You will be brought to an interactive shell.
3. In the command line, enter in the following, replacing `<YOUR_API_KEY>` with the API key you copied from previously generated:

```shell
export API_KEY=<YOUR_API_KEY>
```

#### Create your Speech API request
1. Create `request.json` in the SSH command line. You'll use this to build your request to the speech API:

```shell
touch request.json
```

2. Open the `request.json`:

```shell
nano request.json
```

3. Add the following to your `request.json` file, using the `uri` value of the sample raw audio file:

```shell
{
  "config": {
      "encoding":"FLAC",
      "languageCode": "en-US"
  },
  "audio": {
      "uri":"gs://cloud-samples-tests/speech/brooklyn.flac"
  }
}
```

4. Press `control` + `x` and then `y` to save and click `Enter` to close the `request.json` file.

The request body has a `config` and `audio` object.

In `config`, you tell the Speech API how to process the request. The `encoding` parameter tells the API which type of audio encoding you're using while the file is being sent to the API. `FLAC` is the encoding type for .raw files. Learn more about encoding types in the [RecognitionConfig Guide](https://cloud.google.com/speech/reference/rest/v1/RecognitionConfig).

There are other parameters you can add to your `config` object, but `encoding` is the only required one.

In the `audio` object, you pass the API the uri of the audio file in Cloud Storage.

#### Call the Speech API
1. Pass your request body, along with the API key environment variable, to the Speech API with the following `curl` command (all in one single command line):

```shell
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}"
```

The `transcript` value will return the Speech API's text transcription of your audio file, and the `confidence` value indicates how sure the API is that it has accurately transcribed your audio.

You'll notice that you called the `syncrecognize` method in the request above. The Speech API supports both synchronous and asynchronous speech to text transcription. In this example you sent it a complete audio file, but you can also use the `syncrecognize` method to perform streaming speech to text transcription while the user is still speaking.

You created a Speech API request then called the Speech API.

2. Run the following command to save the response in a `result.json` file:

```shell
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json
```

### Lab - Video Intelligence

#### Overview
Google Cloud Video Intelligence makes videos searchable and discoverable by extracting metadata with an easy to use REST API. You can now search every moment of every video file in your catalog. It quickly annotates videos stored in [Cloud Storage](https://cloud.google.com/storage/), and helps you identify key entities (nouns) within your video; and when they occur within the video. Separate signal from noise by retrieving relevant information within the entire video, shot-by-shot, -or per frame.

#### Enable the Video Intelligence API
For this lab, the **Cloud Video Intelligence API** is enabled for you.

#### Set up authorization
This lab creates and uses a service account that is tied to your Google Cloud project for authorization.

1. In Cloud Shell, run the following command to create a new service account named `quickstart`:

```shell
gcloud iam service-accounts create quickstart
```

2. Create a service account key file, replacing `<your-project-123>` with your Project ID:

```shell
gcloud iam service-accounts keys create key.json --iam-account quickstart@<your-project-123>.iam.gserviceaccount.com
```

3. Now authenticate your service account, passing the location of your service account key file:

```shell
gcloud auth activate-service-account --key-file key.json
```

4. Obtain an authorization token using your service account:

```shell
gcloud auth print-access-token
```

The token will print in the output, and you'll be using it in a future step.

#### Make an annotate video request
1. Run this command to create a JSON request file with the following text, and save it as `request.json` :

```shell
cat > request.json <<EOF
{
   "inputUri":"gs://spls/gsp154/video/train.mp4",
   "features": [
       "LABEL_DETECTION"
   ]
}
EOF
```

**Note:** To make the process simpler, a public video of a train available to your project is used as the value for your `inputUri`. If preferred or running in a personal project, any video can be used in place by uploading it to Cloud Storage and providing its Cloud Storage URI (format: `gs://bucket/object`) for the value of `inputUri`.

2. Use `curl` to make a `videos:annotate` request passing the filename of the entity request:

```shell
curl -s -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer '$(gcloud auth print-access-token)'' \
    'https://videointelligence.googleapis.com/v1/videos:annotate' \
    -d @request.json
```

The Video Intelligence API creates an operation to process your request. You should now see a response that includes your operation name.

You will use this operation name, locations and projects in the future step.

3. Use this script to request information on the operation by calling the `v1.operations` endpoint. Replace the `PROJECTS`, `LOCATIONS` and `OPERATION_NAME` with the value you just received in the previous command:

```shell
curl -s -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer '$(gcloud auth print-access-token)'' \
    'https://videointelligence.googleapis.com/v1/projects/PROJECTS/locations/LOCATIONS/operations/OPERATION_NAME'
```

You'll now see information related to your operation. If the operation has completed, a `done` field is included and set to `true`:

4. After giving the request some time (about a minute, typically), re-run the command and the same request returns annotated results:

You've sent your first request to Cloud Video Intelligence API.