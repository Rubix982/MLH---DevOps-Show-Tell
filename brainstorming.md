# Why?

This is the content I wrote for myself when I was creating the presentation as a way of brainstorming the contents beforehand in a rough fashion.

# Content

1. Why even DevOps? What sets it apart from the Cloud? When to spot something that is actually DevOps, and something that is not? What are the growth aspects of this field?
    1. Definition. DevOps (a portmanteau of “development” and “operations”) is the combination of practices and tools designed to increase an organization's ability to deliver applications and services faster than traditional software development processes
    2. Definition. Cloud computing is the on-demand availability of computer system resources, especially data storage and computing power, without direct active management by the user.
    3. So is DevOps simply just getting in more and more tooling and trying out automation? Short answer, no, it isn't!
    4. As far as growth is related, https://www.marketsandmarkets.com/Market-Reports/devops-824.html, World Economic Forum, http://www3.weforum.org/docs/WEF_Future_of_Jobs_2020.pdf,
2. The DevOps Philosophy - Automation, Building, CI/CD
    1. Developer vs Operations team, natural conflicts, problems, discussions, issues, why did we need this area of expertise, and what does this mean for the future?
    2. What job does the operations do?
      1. Designing
        1. Parameters, Processes
        2. System Topology
        3. Environments, Staging, Development, Production, Testing, Sandbox            
      2. Deploying
        1. Networking and Infrastructure
        2. Planning
      3. Maintaining
        1. Custom/Product Code & Config
        2. Updating Software and OS
        3. Troubleshooting
      4. Monitoring
        1. Detecting Outrages
          2. Monitoring,
            1. Check out MLH's playlist, some notable ones,
              1. Introduction To Prometheus & Other Monitoring Tools, https://www.youtube.com/watch?v=RoqHLG-iYw0&list=PLPDgudJ_VDUfjmLIe9vasB6miSL1ggWkH&index=9&t=1s
                2. Introduction To Cloud Native Chaos Engineering, https://www.youtube.com/watch?v=4uxCP61gYnQ&list=PLPDgudJ_VDUfjmLIe9vasB6miSL1ggWkH&index=10&t=724s
                  3. Your Path to Non Code Contributions in Kubernetes, https://www.youtube.com/watch?v=-eE5i6fFZwc&list=PLPDgudJ_VDUfjmLIe9vasB6miSL1ggWkH&index=11&t=5s
    3. The CI/CD process, https://www.mabl.com/hubfs/CICDBlog.png
    1. The DevOps Checklist! https://faun.pub/the-must-know-checklist-for-devops-system-reliability-engineers-f74c1cbf259d
    2. A fun series over what CI is! https://www.youtube.com/watch?v=ymPOI4gWQFY&list=PL0zVEGEvSaeFFy32i5A4041qSTbYqtKqv (great guy to watch btw)
    3. The infrastructure for building resources, with "Pizza As A Service", https://miro.medium.com/max/2000/1*JacqOl2kjyTYzv31v0xITw.png
    4. Discussions more over the "Infrastructure" fall into their own category, the "Cloud" side of things. Again, it's still part of a CI/CD idea that we had before, but how will we exactly the continuous release be delivered to users will requiring answering the question of heavy infrastructure management. Think about what layer you'll be targeting, SaaS, PaaS, IaaS
    5. For all these, you can take your pick among AWS, Azure, GCP
3. Software Architecture - Reliability, Maintainability, Scalability, Architectural Considerations
    1. To move onto the ideas of containerization, we'll first move towards understanding the traditional architectural approach for software
    1. In the industry, usually, the two main approaches that are usually referenced are monoliths and microservices. We'll explore each architectural model and the implied trade-offs, cover good development practices. These practices are valid for both monolith and microservice architectures.
    2. Functional Requirements,
        1. Stakeholders
        2. Functionalities
        3. End Users
        4. Input and output process
        5. Engineering teams
    3. Available resources,
        1. Engineering resources
        2. Financial resources
        3. Timeframes
        4. Internal knowledge
    4. Monoliths,
        1. Everything is one unit
        2. Managed in a single repository
        3. Sharing existing resources (CPU & memory)
        4. Single programming language mostly
        5. Released using single binary
        6. https://video.udacity-data.com/topher/2020/December/5fdd2602_screenshot-2020-12-18-at-21.57.06/screenshot-2020-12-18-at-21.57.06.png
    5. Microservices,
        1. Managed in a separate repository
        2. Own allocated resources - each has their own
        3. API
        4. Language of choice
        5. Every "service" has its own binary
        6. https://video.udacity-data.com/topher/2020/December/5fdd26ac_screenshot-2020-12-18-at-22.01.07/screenshot-2020-12-18-at-22.01.07.png
4. Service Oriented Architecture - Microservices
    1. Different services, autonomy, business logic, integrating services, component reusability, better authentication and logic encapsulation, makes sense when you're working with large scale operations - you do not need a microservice in a simple project
    2. Best practices,
        1. Health checks - more on this if you read about Replication, Partition of data in Database. The book I'm reading, "Designing Data Intensive Applications" goes into deep detail why health checks are important, with dedicated chapters for Replication and Partitioning
        2. Metrics - Metrics are necessary to quantify the performance of the application. To fully understand how a service handles requests, it is mandatory to collect statistics on how the service operates. For example, the number of active users, handled requests, or the number of logins. Monitoring, Prometheus, Grafana
        3. Logs - Log aggregation provides valuable insights into what operations a service is performing at a point in time. It is the nucleus of any troubleshooting and debugging process. Usually, the logs are collected from STDOUT (standard out) and STDERR (standard error) through a passive logging mechanism. This means that any output or errors from the application are sent to the shell. Subsequently, these are collected by a logging tool, such as Fluentd or Splunk, and stored in backend storage. However, the application can send the logs directly to the backend storage. In this case, an active logging technique is used, as the log transmission is handled directly by the application, without a logging tool required.
        3. Tracing - Tracing is capable of creating a full picture of how different services are invoked to fulfill a single request.
        4. Resource Consumption - Resource consumption encapsulates the resources an application requires to be fully operational
5. Container Orchestration, Docker
    1. Why?
        1. In the past years, VMs (Virtual Machines) were the main mechanism to host an application. VMs encapsulate the code, configuration files, and dependencies necessary to execute the application.
        2. In essence, a VM is composed of an operating system (OS) with a set of pre-installed libraries and packages. During execution, an application utilizes an OS filesystem, resources, and packages.
        3. A set of VMs is managed through a hypervisor. A hypervisor provides the virtualization of the infrastructure which is composed of physical servers. As a result, a hypervisor is capable of creating, configuring, and managing multiple VMs on the available servers. For example, we are able to running applications A, B, and C on 3 separate VMs.
        4. https://video.udacity-data.com/topher/2020/December/5fde7a73_screenshot-2020-12-19-at-22.10.50/screenshot-2020-12-19-at-22.10.50.png
        5. The appearance of containers is unlocked by OS-level virtualization and as a result, multiple applications can run on the same OS. By nature, containers are lightweight, as these encapsulate only the application code and essential dependencies. Consequently, there is a better usage of available infrastructure and a more efficient pathway to release a product to consumers.
    2. So what does Docker consist of?
        1. Dockerfiles
            1. Set of instructions, operations, for packaging the application. Installing dependencies, compiling the code, or changing between users and permissions
            2. It has multiple "layers" where each layer is a single operation
            3. Dockerfiles are supposed to be lightweight and quick
            3. Docker instructions, 
                FROM -  to set the base image
                RUN - to execute a command
                COPY & ADD  - to copy files from host to the container
                CMD - to set the default command to execute when the container starts
                EXPOSE - to expose an application port
            4. Dockerfile example
        2. Docker images
            1. Format,
                1. A Docker image can be built from an existing Dockerfile using the `docker build` command. Below is the syntax for this command:
                # build an image
                # OPTIONS - optional;  define extra configuration
                # PATH - required;  sets the location of the Dockefile and  any referenced files 
                docker build [OPTIONS] PATH

                # Where OPTIONS can be:
                -t, --tag - set the name and tag of the image
                -f, --file - set the name of the Dockerfile
                --build-arg - set build-time variables

                # Find all valid options for this command 
                docker build --help
            2. docker build example with GitHub project
            3. Running docker images
        3. Docker registeries
            1. Storing, distributing, public docker image registry
            2. Available platforms such as DockerHub, Harbor, Google Container Registry
            3. Private image repositories available
            4. To tag an existing image on the local machine, the `docker tag` command is available. Below is the syntax for this command:
                # tag an image
                # SOURCE_IMAGE[:TAG]  - required and the tag is optional; define the name of an image on the current machine 
                # TARGET_IMAGE[:TAG] -  required and the tag is optional; define the repository, name, and version of an image
                docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
            5. Tagging,
                # tag the `python-helloworld` image, to be pushed 
                # in the `pixelpotato` repository, with the `python-helloworld` image name
                # and version `v1.0.0`
                docker tag python-helloworld pixelpotato/python-helloworld:v1.0.0
            6. Pushing the image,
                # push the `python-helloworld` application in version v1.0.0 
                # to the `pixelpotato` repository in DockerHub
                docker push pixelpotato/python-helloworld:v1.0.0
6. Problems At Different Layers - The Need For Innovation, K8s, Prometheus, Grafana
    1. A brief touch over why Kubernetes, and the basic framework structure - it's far too big to be covered easily
    2. So far, in this lesson, we have traversed the packaging of an application using Docker and its distribution through DockerHub. The next phase in the release process is the deployment of the service. However, running an application in production implies that hundreds and thousands of customers might consume the product at the same time. For this reason, it is paramount to build for scale. It is impossible to manually manage thousands of containers, keeping these are up to date with the latest code changes, in a healthy state, and accessible. As a result, a container orchestrator framework is necessary.
    3. Benefits,
        1. Portability
        2. Scalability
        3. Resilience
        4. Service Discovery
        5. Extensibility
        6. Operational Cost
        7. Architecture (if possible)
            1. Nodes (Pods)
            2. Control Plane, https://video.udacity-data.com/topher/2020/December/5fdfdecf_screenshot-2020-12-20-at-23.31.19/screenshot-2020-12-20-at-23.31.19.png
                1. Components,
                    1. kube-apiserver - the nucleus of the cluster that exposes the Kubernetes API, and handles and triggers any operations within the cluster
                    2. kube-scheduler - the mechanism that places the new workloads on a node with sufficient satisfactory resource requirements
                    3. kube-controller-manager - the component that handles controller processes. It ensures that the desired configuration is propagated to resources
                    4. etcd - the key-value store, used for backs-up and keeping manifests for the entire cluster
            3. Data Plane, https://video.udacity-data.com/topher/2020/December/5fdfe11d_screenshot-2020-12-20-at-23.41.02/screenshot-2020-12-20-at-23.41.02.png,
                1. Components,
                    The data plane consists of the compute used to host workloads. The components installed on a worker node are the,
                        1. kubelet - the agent that runs on every node and notifies the kube- apiserver that this node is part of the cluster
                        2. kube-proxy - a network proxy that ensures the reachability and accessibility of workloads places on this specific node
7. Distributed Data Problems - Replication, Partitioning, Transactions, and how DevOps can help
8. Open Source Platform As A Service,
    1. Heroku, CloudFoundary, etc services
9. DevOps Special Interest Groups (SIG), MLOps, CICD Foundation
    1. CICD Foundation, https://cd.foundation/, everything DevOps, GitHub https://github.com/cdfoundation
    2. MLOps,
        1. Special Interest Groups, MLOps, https://github.com/cdfoundation/sig-mlops
        2. An enterprise level tool, https://www.datarobot.com/platform/mlops/
        3. DeepLearning.AI has a specialization on MLOps! https://www.deeplearning.ai/program/machine-learning-engineering-for-production-mlops/, tagged "Explainable AI, Model Monitoring, Model Registries, MLOps, Machine Learning Engineering for Production" etc
    3. Cloud Native Tooling, CNCF (Cloud Native Cloud Foundation) open source projects
