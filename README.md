# smartTextileOrigami

A project exploring e-textiles as interfaces for machine learning (ML) models. 

We use [puredata](https://puredata.info/) on a [Bela board](https://bela.io/) to record sensor data from smart textiles. The recorded sensor data is sent to a python program. The python program operates in three steps:
    * **Recording Training Data**: Training data for a machine learning model is recorded
    * **Training the ML model**
    * **Prediction Phase**: The trained ML model makes predictions using sensor data

## Installation (on OSX)

    * Install [puredata](https://puredata.info/)
    * Install python, we used the [anaconda distribution](https://www.anaconda.com/distribution/#download-section) 
    * Clone this github repo
    * Create a conda python environment with `conda create -n origami python=3.6` (where origami is the arbitrarily chosen project name)
    * Enter the python environment with `source activate origami`
    * Install the required python packages with `pip install -r requirements.txt`

## Running the code

### Training Data Recording Phase
    * Enter the python environment with `source activate origami`
    * Start the jupyter notebook server with `jupyter notebook` and open the `udbclient.ipynb` notebook
    * Run the first code cell in the jupyter notebook to record data
    * Start the `udpclient.pd` patch on your computer and click the `listen ...` blocks
    * Deploy the `_main.pd` file to the Bela board by opening the browser GUI on `http://192.168.7.2/` and start it
   
### Training the ML model
    * You can check whether data was recorded by running the cell that prints the variable `data_and_labels`
    * In the jupyter notebook, run the cell that trains the model
    * (Overfitted) training performance measures are printed
    * You can replace the NearestCentroid classifier with any other sklearn classifier

### Predictions
    * You can now run the last cell for predicting classes with the trained model
    * The python code should send back predictions to the pure data program
    * All data during the prediction phase is being recorded

