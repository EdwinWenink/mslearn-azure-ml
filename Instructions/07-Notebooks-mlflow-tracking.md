---
lab:
    title: 'Track model training in notebooks with MLflow'
---

# Track model training in notebooks with MLflow

Often, you'll start a new data science project by experimenting and training multiple models. To track your work and keep an overview of the models you train and how they perform, you can use MLflow tracking.

In this exercise, you'll MLflow within a notebook running on a compute instance to log model training.

## Before you start

You'll need an [Azure subscription](https://azure.microsoft.com/free) in which you have administrative-level access.

## Provision an Azure Machine Learning workspace

An Azure Machine Learning *workspace* provides a central place for managing all resources and assets you need to train and manage your models. You can interact with the Azure Machine Learning workspace through the studio, Python SDK, and Azure CLI.

You'll use the Azure CLI to provision the workspace and necessary compute, and you'll use the Python SDK to train a classification model with Automated Machine Learning.

### Create the workspace and compute resources

To create the Azure Machine Learning workspace and a compute instance, you'll use the Azure CLI. All necessary commands are grouped in a Shell script for you to execute.
1. In a browser, open the Azure portal at `https://portal.azure.com/`, signing in with your Microsoft account.
1. Select the \[>_] (*Cloud Shell*) button at the top of the page to the right of the search box. This opens a Cloud Shell pane at the bottom of the portal.
1. Select **Bash** if asked. The first time you open the cloud shell, you will be asked to choose the type of shell you want to use (*Bash* or *PowerShell*).
1. Check that the correct subscription is specified and select **Create storage** if you are asked to create storage for your cloud shell. Wait for the storage to be created.
1. In the terminal, enter the following commands to clone this repo:

    ```azurecli
    rm -r azure-ml-labs -f
    git clone https://github.com/MicrosoftLearning/mslearn-azure-ml.git azure-ml-labs
    ```

    > Use `SHIFT + INSERT` to paste your copied code into the Cloud Shell. 

1. After the repo has been cloned, enter the following commands to change to the folder for this lab and run the **setup.sh** script it contains:

    ```azurecli
    cd azure-ml-labs/Labs/07
    ./setup.sh
    ```

    > Ignore any (error) messages that say that the extensions were not installed.

1. Wait for the script to complete - this typically takes around 5-10 minutes.

## Clone the lab materials

When you've created the workspace and necessary compute resources, you can open the Azure Machine Learning studio and clone the lab materials into the workspace.

1. In the Azure portal, navigate to the Azure Machine Learning workspace named **mlw-dp100-...**.
1. Select the Azure Machine Learning workspace, and in its **Overview** page, select **Launch studio**. Another tab will open in your browser to open the Azure Machine Learning studio.
1. Close any pop-ups that appear in the studio.
1. Within the Azure Machine Learning studio, navigate to the **Compute** page and verify that the compute instance you created in the previous section exist. The compute instance should be running.
1. In the **Compute instances** tab, find your compute instance, and select the **Terminal** application.
1. In the terminal, install the Python SDK and the MLflow library on the compute instance by running the following commands in the terminal:

    ``
    pip uninstall azure-ai-ml
    pip install azure-ai-ml
    pip install mlflow
    ```

    > Ignore any (error) messages that say that the packages couldn't be found and uninstalled.

1. Run the following command to clone a Git repository containing a notebook, data, and other files to your workspace:

    ```
    git clone https://github.com/MicrosoftLearning/mslearn-azure-ml.git azure-ml-labs
    ```

1. When the command has completed, in the **Files** pane, click **&#8635;** to refresh the view and verify that a new **Users/*your-user-name*/azure-ml-labs** folder has been created.

## Track model training with MLflow

Now that you have all the necessary resources, you can run the notebook to configure and use MLflow when training models in a notebook.

1. Open the **Labs/07/Track model training with MLflow.ipynb** notebook.

    > Select **Authenticate** and follow the necessary steps if a notification appears asking you to authenticate.

1. Verify that the notebook uses the **Python 3.8 - AzureML** kernel.
1. Run all cells in the notebook.
1. Review the new job that's created every time you train a model.

## Delete Azure resources

When you finish exploring Azure Machine Learning, you should delete the resources you've created to avoid unnecessary Azure costs.

1. Close the Azure Machine Learning studio tab and return to the Azure portal.
1. In the Azure portal, on the **Home** page, select **Resource groups**.
1. Select the **rg-dp100-...** resource group.
1. At the top of the **Overview** page for your resource group, select **Delete resource group**.
1. Enter the resource group name to confirm you want to delete it, and select **Delete**.
