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
   * Create a conda python environment with 
        ``conda create -n origami python=3.6`` (where origami is the arbitrarily chosen project name)
   * Enter the python environment with ``conda activate origami``
   * Install the required python packages with ``pip install -r requirements.txt`` in the folder of the downloaded github repo

## Running the code

### Training Data Recording Phase
#### Python
* Enter the python environment with `conda activate origami`
* Start the jupyter notebook server with `jupyter notebook` and open the `udbclient.ipynb` notebook
* Run the first code cell in the jupyter notebook to record data
#### PureData
* Start the `udpclient.pd` patch on your computer; click the `listen ...` blocks and connect to the python server by clicking the `connect ...` block
* Deploy the `_main.pd` file to the Bela board by opening the browser GUI on `http://192.168.7.2/` and start it
* In the PureData patch on your computer:
 - Set a label in the number field close to the green start button
 - Start the transmission of the sensor data along with the labels by clicking the green button
   
### Training the ML model
* You can check whether data was recorded by running the cell that prints the variable `data_and_labels`. If there is no output, you need to run the recording again, probably you forgot to click `connect ...` in the `udpclient.pd` puredata patch
* In the jupyter notebook, run the cell that trains the model
* (Overfitted) training performance measures are printed
* You can replace the NearestCentroid classifier with any other sklearn classifier

### Predictions
* You can now run the last cell for predicting classes with the trained model
* In the `udpclient.pd`, click the green button to start sending sensor data. The labels will now be ignored, but a prediction will be sent back
* The python code should send back predictions to the pure data program
* All data during the prediction phase is being recorded

