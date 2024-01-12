# Getting Started with NDP

This guide has been designed to introduce you to the main features of the National Data Platform (NDP) and demo the creation of an NDP project aimed to address a data challenge. By the end of this tutorial, you will accomplish the following:

- Explore the data catalog
- Launch a computing instance
- Execute a simple analysis

## The Challenge

The demonstration of this tutorial relies on the following *mock challenge*.

In recent years, the United States has found itself immersed in what the US Forest Service describes as a "wildfire crisis." The consequences have been particularly pronounced in the western region, where some of the most destructive wildfires in the country's history have affected vulnerable communities in states such as Washington, Colorado, Arizona, Oregon, and California. This crisis has not only incurred billions of dollars in damages and the loss of extensive wildlife habitat but, most significantly, has resulted in tragic human casualties. In response to this situation, the scientific community has underscored the need of addressing the crisis through the development of knowledge and tools that can facilitate more effective fire management actions.

Integral to fire management is the field of wildfire modeling, which allows for the prediction of fire behavior under diverse conditions. Such models play a pivotal role in identifying high-risk areas, conducting prescribed burns more efficiently, optimizing the allocation of fire response resources, designing suppression strategies, and enhancing community resilience to potential wildfire risks.

One critical aspect of refining wildfire modeling lies in the precision of modeling high-resolution 3D terrestrial vegetation fuels images. The use of terrestrial laser scans has become more prominent in collecting field images, enabling researchers to identify and classify different types of vegetation fuels in a given area. Therefore, an improved and precise classification of fuels significantly enhances the efficacy of current wildfire modeling approaches.

**Task**

In this *mock challenge*, the task requires to develop a model aimed at enhancing the classification of vegetation fuels. This task leverages on the openly accessible Terrestrial Light Detection and Ranging (LiDAR) data provided by the [Interagency Ecosystem LiDAR Monitoring (IntELiMon)](https://dmsdata.cr.usgs.gov/lidar-monitoring/viewer/) portal.

## Starting the project

To begin with the development of our modeling task, we will start by exploring the NDP's Catalog to identify our data source.

**Catalog**

One of the main features of NDP is the extensive data catalog. This catalog contains access to datasets, streaming data, as well as Open Knowledge Networks from different collaborative organizations. When exploring the catalog, one of the first things you will notice is that each dataset is associated with the collaborative organization sharing the data. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20214248.png?raw=true">

Data location is facilitated through the incorporation of a search engine. To start, you can type *IntELiMon* into the search engine, which is the data used for the *mock challenge* project:

**IMAGE**

Once you identify the dataset, you can click on *View More*. You will notice the following components:

- A description of the dataset
- A "View More" function, which provides information regarding all the files and metadata information that conforms the dataset. 
- A JupyterHub button, which allows the user to initiate a computing instance to start working directly with the dataset.

**Launching Computing Resources**

NDP allows users to explore and work on data by facilitating access to the NSF's cyberinfrastructure (CI) capabilities. For the case of the *mock challenge*, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data through [containarized](https://en.wikipedia.org/wiki/Containerization_(computing)) applications. 

To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button next to our dataset:

After we click, we will be redirected into a JupyterHub environment.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true">

Once we access the environment, we can log in to our user space by entering our username credentials, or by accessing through our institutional credentials (for the case of academic institutions) via [CI Logon](https://www.cilogon.org/). Once you log in, you will be redirected to the main site for resources reservation:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20182754.png?raw=true">

One of the main features of NDP is the automatic provision of a 50GB Persistent Volume to each user, allowing persist the user's work through different servers. Furthermore, the JupyterHub environment is provisioned with an user-friendly interface for resources request. 

Firstly, we have to select type and amount hardware, which highly depends on the kind of project we are working on. Take into consideration that increasing the number and complexity of resources, also increases the waiting time to get an allocation. In the main page, you can consult the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For our sample project, we are going to set up the following specifications:

- Region: Any
- GPU's: 1
- Cores: 1
- RAM: 16GB
- GPU type: NVIDIA-GeForce-GTX-1080-Ti

Secondly, we have the choice to mount a shared memory folder for the case of applications using pytorch. As this sample project does not use the pytorch library, we can omit the checkbox.

The next component we must select is an appropiate [Docker Image](https://docs.docker.com/get-started/overview/) for the project we are working on. This will allow our server to load all libraries and dependencies that we need to work on our project. As our project relies on the TensorFlow library, we are going to use the *CUDA* image, so make sure to have it selected. 

The final component of our resources allocation refers to the selection of the processor architecture. In this case, given the use of CUDA in our project, we must select an amd64 architecture. 

Once we make sure all the fields have the right selection, we can start our server. Once our server starts running, we will be redirected to JupyterLab, with our persisted workspace, which includes the folder with our project:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20203016.png?raw=true">

**Performing our jobs and obtaining our outputs**



## Acknowledgement

This tutorial recognizes the worked developed by Ivannia Gomez Moreno, whose project in developing a model for segmented vegetation fuels classification served as the sample project to demonstrate the features of NDP.
