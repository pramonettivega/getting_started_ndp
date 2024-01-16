# Getting Started with NDP

This introductory guide aims to provide collaborators with a comprehensive overview of some of the key features of the National Data Platform (NDP). The exploration is complemented by a sample exploratory data analysis and model training. By the end of this tutorial, we will accomplish the following:

- Navigate the data catalog
- Initiate a computing instance
- Perform an analysis using the JupyterHub environment in a high-performance computing instance.

## What is NDP?

NDP is a federated and extensible data ecosystem that fosters collaboration, innovation and equitable data use, leveraging existing Cyberinfrastructure (CI) capabilities. 

## Who can use NDP?

NDP serves as an open-access platform with the goal of reducing barriers to data and technology access, especially for individuals lacking expertise or resources in the field of AI. The platform is designed to cater to both the scientific and academic communities, as well as non-experts interested in exploring AI training. By fostering inclusivity in its user base, NDP aims to enhance the significance of existing data repositories, contributing to advancements in science, societal well-being, and education.

## Catalog

One of the main features of NDP is the extensive data catalog,  which encompasses a variety of resources such as datasets, streaming data, and open knowledge networks spanning diverse scientific domains. This comprehensive catalog is further enriched by collaboration with various organizations and researchers that contribute to making data accessible through the registration service. This accessibility empowers researchers and learners to engage with the data, fostering the development of innovative analysis, modeling techniques, and applications.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20125934.png?raw=true">

Data location is facilitated through the incorporation of a search engine. As a starting point, we can type *Uniform Fuels* into the search engine, corresponding to the data utilized for the demonstration project. Once the dataset is identified, clicking on *View More* will open a window with the following information:

- A comprehensive description detailing the content of the dataset.
- A list of all supplementary files along with metadata information.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20215429.png?raw=true">

## Launching Computing Resources

NDP allows users to explore and work on data by facilitating access to the NSF's cyberinfrastructure (CI) capabilities. For the case of our demonstration dataset, we are going to connect with [Nautilus](https://nationalresearchplatform.org/nautilus/), a hypercluster which facilitates the work with Big Data through [containarized](https://en.wikipedia.org/wiki/Containerization_(computing)) applications. 

To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button in our dataset, which will redirect us to the JupyterHub environment. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-09%20211402.png?raw=true">

After accessing the environment, we can log in to our designated user space using either our username credentials or, in the case of members of institutions with federated access to NSF's infrastructure, by utilizing institutional credentials via  [CI Logon](https://www.cilogon.org/). Once you log in, you will be redirected to the main site for resources reservation:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20182754.png?raw=true">

One of the main features of NDP is the provision of an user friendly interface which facilitates the creation of a pod. After providing the required specifications, the cluster (which works under the [Kubernetes](https://kubernetes.io/) system) orchestrates the creation of a pod, which operates on the allocated hardware resources such as CPU cores, GPUs, and memory. The pod encapsulates the applications contained in the provisioned images, leveraging the specified hardware. Additionally, the cluster associates a 50GB persistent volume (PV) with the pod, ensuring that the work that we develop is seamlessly stored and persists across various sessions. 

To initiate the creation of a pod, we begin by specifying the location, amount, and type of hardware (for the case of GPU). It's important to bear in mind that augmenting the quantity and intricacy of these resources can lead to an extended allocation waiting time. For real-time updates on the availability of resources, we can refer to the [Available Resources Page](https://portal.nrp-nautilus.io/resources). For the purposes of this tutorial, we set up the following specifications:

- Region: Any
- GPU's: 1
- Cores: 1
- RAM: 16GB
- GPU type: NVIDIA-GeForce-GTX-1080-Ti

Secondly, we have the choice to mount a shared memory folder into our pod, particularly for applications utilizing PyTorch. Since our model training involves the use of the PyTorch library, we must select the checkbox for this feature.

The next component we must select is an appropiate [Docker Image](https://docs.docker.com/get-started/overview/) tailored for the specific requirements of the project we are working on. This ensures that the server loads all the necessary libraries and dependencies crucial for the project's execution. For this sample tutorial, we have provided an image which will create a directory within JupyterLab with the data and our sample Jupyter Notebooks once will launch our instance. Make sure to select the *Physics Guided Machine Learning Starter Code* image.

The final aspect of our resource allocation involves selecting the processor architecture. In this case, due to the utilization of CUDA in our example, we must choose an amd64 architecture. 

Once our server starts running, we will be redirected to JupyterLab, with our persisted workspace, which in this case includes the folder with our project. In this case, our workspace has set up the working files for our example: 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-11%20203016.png?raw=true">

## Performing our Analysis

In our analysis, we are going to perform a simple Machine Learning

JupyterLab offers a series of features so we can develop our projects in an interactive environment, allowing us to explore, edit and visualize our data. To set up our workspace, we can either load the files directly into our space, or we can create new files from JupyterLab. 

In this example, we have loaded into our space a Jupyter Notebook with the training code for our modeling task. Additionally, we have added a set of Python scripts which contain a series of helper functions and methods that contribute to the execution of our training. 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20034059.png?raw=true">

To facilitate the tracking and history of our training sessions, another important feature of NDP is the integration with [MLflow](https://mlflow.org/). This integration enables the logging of various training iterations, saving each generated model, along with key hyperparameters and specified metrics. All this information can be consulted through the MLflow [dashboard](https://ndp.sdsc.edu/mlflow):

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20010755.png?raw=true">

Once we finish running our training jobs, and our desired outputs have been generated inside of our volume, we can download our work to our local instances, by right clicking on the file(s) (in this case the output folder), and selecting the choice of downloading. For the case of our example, we compressed our outputs folder into a zip file, so it can be downloaded from JupyterLab

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-12%20035201.png?raw=true">

## Supporting Documents

- [MLflow Getting Started Guide](https://mlflow.org/docs/latest/getting-started/index.html)
- [Introduction to Nautilus](https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Fnationalresearchplatform%2Eorg%3A443%2Fwp%2Dcontent%2Fuploads%2F2023%2F05%2FZihao%2Dand%2DZhuruis%2DNautilus%2DTutorial%2Epptx&wdSlideId=260&wdModeSwitchTime=1705034185009): This tutorial provides more details regarding the creation of pods and the execution of jobs in Nautilus.
  
## Closing Note 

This tutorial is part of the BETA version of NDP, and as such, it may contain some imperfections or errors. We welcome all valuable feedback to assist us in refining the content, enhancing the structure, and improving overall clarity.

Contact: pramonettivega@ucsd.edu
