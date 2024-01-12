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

In this *mock challenge*, the task requires to develop a model aimed at enhancing the classification of vegetation fuels. This task leverages on the openly accessible Terrestrial Light Detection and Ranging (LiDAR) data provided by the [Interagency Ecosystem LiDAR Monitoring (IntELiMon)](https://dmsdata.cr.usgs.gov/lidar-monitoring/viewer/) portal, which is now accessible through the NDP catalog.

## Starting the project

To begin with the development of our modeling task, we will start by exploring the NDP's Catalog to identify our data source.

**Catalog**

One of the main features of NDP is the extensive data catalog. This catalog contains access to datasets, streaming data, as well as open knowledge networks from different science domains. This catalog is enriched by the several collaborating organizations that make the data accesible through the registration service, so researchers and learners can work on it to develop new analysis, modeling and applications. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20214248.png?raw=true">

Data location is facilitated through the incorporation of a search engine. To start, you can type *IntELiMon* into the search engine, which is the data used for the *mock challenge* project. Once we identify the dataset, we can click on *View More*, and get the following information:

- A description of the dataset
- A *View More* function, which provides information regarding all the files and metadata information that conforms the dataset. 
- A JupyterHub button, which allows the user to initiate a computing instance to start working directly with the dataset.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20215429.png?raw=true">

**Launching Computing Resources**

NDP allows users to explore and work on data by facilitating access to the NSF's cyberinfrastructure (CI) capabilities. For the case of the *mock challenge*, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data through [containarized](https://en.wikipedia.org/wiki/Containerization_(computing)) applications. 

To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button in our dataset, which will redirect us to the JupyterHub environment. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true">

Once we access the environment, we can log in to our user space by entering our username credentials, or by accessing through our institutional credentials (for the case of academic institutions) via [CI Logon](https://www.cilogon.org/). Once you log in, you will be redirected to the main site for resources reservation:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20182754.png?raw=true">

One of the main features of NDP is the provision of an user friendly interface which facilitates the creation of a pod. After providing the required specifications, the cluster (which works under the [Kubernetes](https://kubernetes.io/) system) orchestrates the creation of a pod, which operates on the allocated hardware resources such as CPU cores, GPUs, and memory. The pod encapsulates the applications contained in the provisioned images, leveraging the specified hardware. Additionally, the cluster associates a 50GB persistent volume (PV) with the pod, ensuring that the work that we develop is seamlessly stored and persists across various sessions. 

To initiate the creation of a pod, we begin by specifying the location, amount, and type of hardware (for the case of GPU). It's important to bear in mind that augmenting the quantity and intricacy of these resources can lead to an extended allocation waiting time. For real-time updates on the availability of resources, we can refer to the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For our sample project, we set up the following specifications:

- Region: Any
- GPU's: 1
- Cores: 1
- RAM: 16GB
- GPU type: NVIDIA-GeForce-GTX-1080-Ti

Secondly, we have the choice to mount a shared memory folder into our pod for the case of applications using pytorch. As this sample project does not use the pytorch library, we can omit the checkbox.

The next component we must select is an appropiate [Docker Image](https://docs.docker.com/get-started/overview/) for the project we are working on. This will allow our server to load all libraries and dependencies that we need to work on our project. As our project relies on the TensorFlow library, we are going to use the *CUDA* image, so make sure to have it selected. 

The final component of our resources allocation refers to the selection of the processor architecture. In this case, given the use of CUDA in our project, we must select an amd64 architecture. 

Once we make sure all the fields have the right selection, we can start our server. Behind the scenes, the cluster orchestrates the creation of a pod, a  which operates on the allocated hardware resources. The pod encapsulates the applications contained in the provisioned images, leveraging the specified hardware for efficient processing. Additionally, the cluster associates a persistent volume (PV) with the pod, ensuring that your work is seamlessly stored and persists across various sessions. This integration of resources and storage mechanisms optimizes the execution and longevity of your computing environment within the cluster.

Once our server starts running, we will be redirected to JupyterLab, with our persisted workspace, which includes the folder with our project:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20203016.png?raw=true">

**Performing our jobs and obtaining our outputs**

Once we get inside the JupyterLab environment, we can either interact.

For this sample, we are taking


## Acknowledgement

This tutorial recognizes the worked developed by Ivannia Gomez Moreno, whose project in developing a model for segmented vegetation fuels classification served as the sample project to demonstrate the features of NDP.
