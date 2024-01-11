# Getting Started with NDP

This guide has been designed to introduce you to the main services of the National Data Platform (NDP) and allow you to run your first jobs on high computing instances. By the end of this tutorial, you will accomplish the following:

- Explore the data catalog
- Launch a computing instance
- Execute a simple analysis

**What is NDP?**

NDP is a federated and extensible data ecosystem to promote collaboration, innovation, and equitable use of data on top of existing National Science Foundation's (NSF) cyberinfrastructure capabilities.

**What services are included?**

NDP posseses a varied collection of integrated services to facilitate AI development in a single platform. The services that we are going to explore in this catalog are the following:

- Data Catalog: A federated catalog with an extensive collection of big datasets, streaming data, and Open Knowledge Networks from different sciences domains.
- JupyterHub: A [JupyterHub](https://jupyter.org/hub) Environment.
- MLflow: Users can monitor the status of their training jobs, as well as their performance through the incorporation of [MLflow](https://mlflow.org/).

**Who can use NDP?**

NDP is committed to open and equitable data access. All individuals with an interest in developing AI to contribute to science and to develop solutions to current societal problems, are invited to use NDP.

## Getting Started

We are going to work on our first project with NDP. Our project will address the *Mock Data Challenge*, by generating a classification model to segment vegetation fuels using 3D images. Before working the attached notebook, we are going to take a brief exploration into the main components of the platform to get you familiar with

**Catalog**

One of the main features of NDP is the extensive data catalog. This catalog contains datasets, open knowledge networks, as well as access to streaming data instances from different collaborative organizations. Organizations working in the different fields of science that are interested in making their data accessible for the development of AI atop of it are encouraged to register their data into NDP's catalog. To 

In this first example, we will take a look at the *name of the dataset*. 

**Launching Computing Resources**

NDP allows users to explore and work on data by facilitating access to the NSF's cyberinfrastructure (CI) capabilities. For the case of this analysis, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data through [containarized](https://en.wikipedia.org/wiki/Containerization_(computing)) applications.To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button next to our dataset:
<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20204427.png?raw=true" width="200">

After we click, we will be redirected into the Nautilus' JupyterHub environment.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true" width="100">

Click on the sign in button, and enter you username credentials, or access through your institutional log-in via CI Logon. Once you log in, you will be redirected to the main site for resources reservation:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-10%20235226.png?raw=true">

The type and amount of resources that we reserve depends on the kind of project we are working on. Take into consideration that increasing the number and complexity of resources, also increases the waiting time to get an allocation. In the main page, you can consult the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For our sample project, we are going to work with the default set up:

- Region: Any
- GPU's: 0
- Cores: 1
- RAM: 8GB
- GPU type: Any

The second component we must select is an appropiate [Docker Image](https://docs.docker.com/get-started/overview/) for the project we are working on. This will allow our server to load all the necessary libraries and dependencies to work on our project. For this guide, we are going to use the *name of the image*, so make sure to have it selected. 

Make sure all the fields have the right selection, and launch JupyterLab. The space allocation might take a few minutes. Once we get into JupyterLab, we will have a 50 GB volume to work on our project. In this space, click on the Upload Files button to upload the notebook attached to this tutorial.
