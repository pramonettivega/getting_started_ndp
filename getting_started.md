# Getting Started with NDP

This introductory guide aims to provide collaborators with a comprehensive overview of some of the key features of the National Data Platform (NDP). The exploration is complemented by a sample exploratory data analysis and model training. By the end of this tutorial, we will accomplish the following:

- Navigate the data catalog
- Initiate a computing instance
- Perform an analysis using the JupyterHub environment in a high-performance computing instance.

## What is NDP?

NDP is a federated and extensible data ecosystem to promote collaboration, innovation and equitable use of data on top of existing Cyberinfrastructure (CI) capabilities. 

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

To connect with Nautilus and launch a computational instance, we will start by clicking at the JupyterHub button attached to our dataset, which will redirect us to the JupyterHub environment. 

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

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20132537.png?raw=true">

## Performing our Analysis

We are going to execute the two notebooks provided in the example. The first one that we are going to open, is *pgml_eda.ipynb*. This notebook provides a simple exploratory data analysis over the Uniform Fuels QUIC-Fire simulation data. You can either run cell by cell, or go to the *Run* window in JupyteLab and select *Run All Cells*. The notebook should generate the following charts:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20172040.png?raw=true">

The second notebook, contains code that performs a model training, leveraging on predefined classes that you can explore on the *unet* directory. Running the notebook will perform the following tasks:

1. Load the relevant libraries and sets up de directories to store our results.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20175155.png?raw=true">

2. Set up the experiment, with the relevant metrics and parameters.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20180731.png?raw=true">

3. Start an experiment session in [MLflow](https://mlflow.org/) to save our model specifications and results.

To facilitate the tracking and history of our training sessions, another important feature of NDP is the integration with [MLflow](https://mlflow.org/). This integration enables the logging of various training iterations, saving each generated model, along with key hyperparameters, specified metrics and relevant visualitazionts. All this information can be consulted through the MLflow [dashboard](https://ndp.sdsc.edu/mlflow). In the following, you will see on the left side, the different experiments we have 

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20173255.png?raw=true">

By clicking on the name of the run, we can see the information that we saved for our experiment:

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20174233.png?raw=true">

4. Perform the training and testing of the model.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20183823.png?raw=true">

5. Produce the model and output images to store in the results directory.

6. Send the final products to MLflow.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-15%20184846.png?raw=true">

**NOTE:** If decided to run the notebook, take into consideration that the full training under the hardware specifications defined previously might take up to three hours.

After finishing our work in JupyterLab, it is important to stop our server. To do this, go to the *File* window in JupyterLab and select *Hub Control Panel*. This will redirect you to JupyterHub and display your running servers (in case you have more than one). Click on *Stop My Server* to stop the current server.

<img src="https://github.com/pramonettivega/images/blob/main/Screenshot%202024-01-16%20103042.png?raw=true">

## Supporting Documents

- [MLflow Getting Started Guide](https://mlflow.org/docs/latest/getting-started/index.html)
- [Introduction to Nautilus](https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Fnationalresearchplatform%2Eorg%3A443%2Fwp%2Dcontent%2Fuploads%2F2023%2F05%2FZihao%2Dand%2DZhuruis%2DNautilus%2DTutorial%2Epptx&wdSlideId=260&wdModeSwitchTime=1705034185009): This tutorial provides more details regarding the creation of pods and the execution of jobs in Nautilus.
  
## Closing Note 

This tutorial is part of the BETA version of NDP, and as such, it may contain some imperfections or errors. We welcome all valuable feedback to assist us in refining the content, enhancing the structure, and improving overall clarity.

Contact: pramonettivega@ucsd.edu
