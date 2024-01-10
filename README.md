# Getting Started with NDP

This guide has been designed to introduce you to the main services of the National Data Platform (NDP) and allow you to run your first jobs on high computing instances. By the end of this tutorial, you will accomplish the following:

- Explore the data catalog
- Launch a computing instance
- Execute a simple analysis

**What is NDP?**

The National Data Platform, or NDP, is a federated and extensible data ecosystem to promote collaboration, innovation, and equitable use of data on top of existing cyberinfrastructure capabilities.

**What services are included?**

- CKAN Catalog: A federated data catalog with an extensive collection of big datasets, streaming data, and Open Knowledge Networks.
- JupyterHub: Users can easily collaborate and develop their work through the JupyterHub Environment.
- ML Flow: Users can monitor the status of their training jobs, as well as their performance through the incorporation of ML Flow.

**Who can use NDP?**

NDP is committed to open and equitable data access. All individuals with an interest in developing AI to contribute to science and to develop solutions to current societal problems, are invited to use NDP.

**What do I need to know to use NDP?**

NDP collection of datasets varies on a range of topics and domains. The development of . Nonetheless, familiarity with JupyterHub and Python programming is fundamental to start working with NDP. Users can consult Open Learning Resources.

## Getting Started

**Catalog**

One of the main features of NDP is the extensive data catalog. This catalog contains datasets, open knowledge networks, as well as access to streaming data instances. For each data, NDP provides the
The catalog is powered by the [CKAN](https://ckan.org/) open-source data management system, allowing users to open

**Launching Computing Resources**

NDP allows users to explore and work on data by facilitating access to the National Science Foundation's cyberinfrastructure (CI) capabilities. For the case of this analysis, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data.

To connect with Nautilus and launch a computational instance, we will start by clicking at the Jupyter Hub button next to our dataset:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20204427.png?raw=true" width="200">

Once we have clicked, we will be redirected into the Nautilus' JupyterHub environment.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true">

Click on the sign in button, and enter you username credentials, or access through your institutional credential via CI Logon. Once you log in, you will be redirected to the main site for resources reservation.

The type and amount of resources that we reserve depends on the kind of project we are working on. Take into consideration that increasing the number and complexity of resources, also increases the waiting time to get a reservation. In the main page, you can consults the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For this guide, we are going to work with the default set up. 

The second component we must select is an appropiate Docker Image for the project we are working on. This will allow our server to load all the necessary libraries and dependencies to work on our project.
