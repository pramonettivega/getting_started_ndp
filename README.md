# Getting Started with NDP

This guide has been designed to introduce you to the main features of the National Data Platform (NDP) and allow you to work on your first project. By the end of this tutorial, you will accomplish the following:

- Explore the data catalog
- Launch a computing instance
- Execute a simple analysis

**What is NDP?**

NDP is a federated and extensible data ecosystem to promote collaboration, innovation, and equitable access and use of data on top of existing National Science Foundation's (NSF) cyberinfrastructure capabilities. 

**What services are included?**

NDP posseses a varied collection of integrated services to facilitate AI development in a single platform. The services that we are going to explore in this guide are the following:

- Data Catalog: A federated catalog with an extensive collection of datasets, streaming data, and Open Knowledge Networks from different sciences domains. The existence of this catalog is possible through the contributions of the different collaborative organizations.
- JupyterHub: To facilitate work and analysis on data, a [JupyterHub](https://jupyter.org/hub) is integrated when launching a computational instances. Furthermore, a persistent volume of 50GB is mounted within the hub, allowing users to persist their work through the process of their project. 

**Who can use NDP?**

NDP is committed to open and equitable data access. All individuals with an interest in developing AI to contribute to science and to develop solutions to current societal problems, are invited to use NDP.

## Getting Started

We are going to work on our first project with NDP. Our project will address the *Mock Data Challenge*, by training and evaluating a classification model to segment vegetation fuels using 3D images. Before going through the project itself, we are going to explore the data catalog and its main components, and go to the process of launching a computing instance from it.

**Catalog**

One of the main features of NDP is the extensive data catalog. This catalog contains access to datasets, streaming data, as well as Open Knowledge Networks from different collaborative organizations. When exploring the catalog, one of the first things you will notice is that each dataset is associated with the collaborative organization sharing the data. 

Data location is facilitated through the incorporation of a search engine. To start, you can type *name of the dataset* into the search engine, which is the dataset that we will use for our first project:

**IMAGE**

Once you identify the dataset, you can click on *View More*. You will notice the following components:

- A description of the dataset
- The associated metadata

**Launching Computing Resources**

NDP allows users to explore and work on data by facilitating access to the NSF's cyberinfrastructure (CI) capabilities. For the case of this analysis, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data through [containarized](https://en.wikipedia.org/wiki/Containerization_(computing)) applications.To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button next to our dataset:

After we click, we will be redirected into a JupyterHub environment.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true">

Click on the sign in button, and enter you username credentials, or access through your institutional log-in via CI Logon. Once you log in, you will be redirected to the main site for resources reservation:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20182754.png?raw=true">

Firstly, we have to select type and amount hardware, which highly depends on the kind of project we are working on. Take into consideration that increasing the number and complexity of resources, also increases the waiting time to get an allocation. In the main page, you can consult the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For our sample project, we are going to set up the following specifications

- Region: Any
- GPU's: 1
- Cores: 1
- RAM: 16GB
- GPU type: NVIDIA-GeForce-GTX-1080-Ti

Also, make sure 

The third component we must select is an appropiate [Docker Image](https://docs.docker.com/get-started/overview/) for the project we are working on. This will allow our server to load all libraries and dependencies that we need to work on our project. For this guide, we are going to use the *name of the image*, so make sure to have it selected. 

The fourth and final component refers to the selection of 

Make sure all the fields have the right selection, and launch JupyterLab. The space allocation might take a few minutes. Once we get into JupyterLab, we will have a 50 GB volume to work on our project. In this space, click on the Upload Files button to upload the notebook attached to this tutorial.
