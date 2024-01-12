# Getting Started with NDP

This introductory tutorial aims to provide learners with a comprehensive overview of some of the key features of the National Data Platform (NDP). The exploration is complemented by a sample demonstration of an NDP project designed to address a *mock data challenge*. By the end of this tutorial, we will accomplish the following:

- Navigate the data catalog
- Initiate a computing instance
- Showcase a sample project using the JupyterHub environment in a high-performance computing instance.

## The Challenge

The demonstration of this tutorial relies on the following *mock challenge*.

In recent years, the United States has found itself immersed in what the US Forest Service describes as a "wildfire crisis." The consequences have been particularly pronounced in the western region, where some of the most destructive wildfires in the country's history have affected vulnerable communities in states such as Washington, Colorado, Arizona, Oregon, and California. This crisis has not only incurred billions of dollars in damages and the loss of extensive wildlife habitat but, most significantly, has resulted in tragic human casualties. In response to this situation, the scientific community has underscored the need of addressing the crisis through the development of knowledge and tools that can facilitate more effective fire management actions.

Integral to fire management is the field of wildfire modeling, which allows for the prediction of fire behavior under diverse conditions. Such models play a pivotal role in identifying high-risk areas, conducting prescribed burns more efficiently, optimizing the allocation of fire response resources, designing suppression strategies, and enhancing community resilience to potential wildfire risks.

One critical aspect of refining wildfire modeling lies in the precision of modeling high-resolution 3D terrestrial vegetation fuels images. The use of terrestrial laser scans has become more prominent in collecting field images, enabling researchers to identify and classify different types of vegetation fuels in a given area. Therefore, an improved and precise classification of fuels significantly enhances the efficacy of current wildfire modeling approaches.

**Task**

In this *mock challenge*, participants are tasked with building a model to improve the classification of vegetation fuels by effectively segmenting them into live and dead categories. The challenge utilizes openly accessible Terrestrial Light Detection and Ranging (LiDAR) data sourced from the [Interagency Ecosystem LiDAR Monitoring (IntELiMon)](https://dmsdata.cr.usgs.gov/lidar-monitoring/viewer/) portal, which is now accessible through the NDP catalog. 

## Starting the project

Before starting to work on the steps of the project, we will start by formally joining the challenge. The *mock challenge* can be publicly located on the *Data Challenges* section inside of the NDP's Education Gateway. We can find it with the name of *Improving Vegetation Fuels Classification*.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20032053.png?raw=true">

By joining the challenge, our ow that we have formally joined the Data Challenge, we can start our process of developing a project. As a first step, we will explore the NDP's Catalog to identify our data source.

**Catalog**

One of the main features of NDP is the extensive data catalog. encompassing a wealth of resources such as datasets, streaming data, and open knowledge networks spanning diverse scientific domains. This comprehensive catalog is further enriched by collaboration with various organizations that contribute to making data accessible through the registration service. This accessibility empowers researchers and learners to engage with the data, fostering the development of innovative analysis, modeling techniques, and applications.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20214248.png?raw=true">

Data location is facilitated through the incorporation of a search engine. As a starting point, we can type *IntELiMon* into the search engine, corresponding to the data utilized for the mock challenge project. Once the dataset is identified, clicking on View More provides access to the following information:

- A comprehensive description detailing the content of the dataset.
- A list of all supplementary files along with metadata information.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20215429.png?raw=true">

**Launching Computing Resources**

NDP allows users to explore and work on data by facilitating access to the NSF's cyberinfrastructure (CI) capabilities. For the case of the *mock challenge*, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data through [containarized](https://en.wikipedia.org/wiki/Containerization_(computing)) applications. 

To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button in our dataset, which will redirect us to the JupyterHub environment. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true">

After accessing the environment, we can log in to our designated user space using either our username credentials or, in the case of members of institutions with federated access to NSF's infrastructure, by utilizing institutional credentials via  [CI Logon](https://www.cilogon.org/). Once you log in, you will be redirected to the main site for resources reservation:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20182754.png?raw=true">

One of the main features of NDP is the provision of an user friendly interface which facilitates the creation of a pod. After providing the required specifications, the cluster (which works under the [Kubernetes](https://kubernetes.io/) system) orchestrates the creation of a pod, which operates on the allocated hardware resources such as CPU cores, GPUs, and memory. The pod encapsulates the applications contained in the provisioned images, leveraging the specified hardware. Additionally, the cluster associates a 50GB persistent volume (PV) with the pod, ensuring that the work that we develop is seamlessly stored and persists across various sessions. 

To initiate the creation of a pod, we begin by specifying the location, amount, and type of hardware (for the case of GPU). It's important to bear in mind that augmenting the quantity and intricacy of these resources can lead to an extended allocation waiting time. For real-time updates on the availability of resources, we can refer to the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For our sample project, we set up the following specifications:

- Region: Any
- GPU's: 1
- Cores: 1
- RAM: 16GB
- GPU type: NVIDIA-GeForce-GTX-1080-Ti

Secondly, we have the choice to mount a shared memory folder into our pod, particularly for applications utilizing PyTorch. Since our sample project does not involve the use of the PyTorch library, the checkbox for this feature can be omitted.

The next component we must select is an appropiate [Docker Image](https://docs.docker.com/get-started/overview/) tailored for the specific requirements of the project. This ensures that the server loads all the necessary libraries and dependencies crucial for the project's execution. Given that our project relies on the TensorFlow library, we opt for the *CUDA* image to ensure compatibility and optimal performance.

The final aspect of our resource allocation involves selecting the processor architecture. In this case, due to the utilization of CUDA in our project, we must choose an amd64 architecture. 

Once our server starts running, we will be redirected to JupyterLab, with our persisted workspace, which in this case includes the folder with our project:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20203016.png?raw=true">

**Performing our jobs and obtaining our outputs**

JupyterLab offers a series of features so we can develop our projects in an interactive environment, allowing us to explore, edit and visualize our data. To set up our workspace, we can either load the files directly into our space, or we can create new files from JupyterLab. 

In this example, we have loaded into our space a Jupyter Notebook which contains the training code for our modeling task. Additionally, we have also added a set of Python scripts which contain a series of helper functions and methods that contribute to the execution of our training. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20034059.png?raw=true">

Another important feature of NDP, is the integration of [MLflow](https://mlflow.org/). This integration allows to keep track of the different training iterations we perform, by saving the generated model from each iteration, as well as the main hyperparamenters and the main metrics that we specify. All this information can be consulted through the MLflow [dashboard](https://ndp.sdsc.edu/mlflow):

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20010755.png?raw=true">

Once we finish running our training jobs, and our desired outputs have been generated inside of our volume, we can download our work to our local instances, by right clicking on the file(s) (in this case the output folder), and selecting the choice of downloading. 

## Supporting Documents

- [Mock Challenge Motivating Document](https://ieeexplore.ieee.org/document/10254841)
- [Wildfire Crisis](https://www.fs.usda.gov/managing-land/wildfire-crisis)
- [MLflow Getting Started Guide](https://mlflow.org/docs/latest/getting-started/index.html)

## Acknowledgement

This tutorial recognizes the worked developed by Ivannia Gomez Moreno, whose project in developing a model for segmented vegetation fuels classification served as the sample project to demonstrate the features of NDP.

**CLOSING NOTE:** This tutorial is part of the BETA version of NDP, and as such, it may contain some imperfections or errors. We welcome all valuable feedback to assist us in refining the content, enhancing the structure, and improving overall clarity.
