Tf_Object_Detection
Description
This project provides a starting point for developing a custom object detection model using the COCO dataset for training and evaluation. The steps below guide you through the setup process.

Steps
Clone the TensorFlow Models repository from GitHub:
bash
Copy code
git clone https://github.com/tensorflow/models.git
Install Protocol Buffers. Protobuf is used to define the structure of the data that is passed between different components of the system, including defining the format of the input data, the output data, and the configuration parameters for the various models and algorithms used in the detection process.

Download the appropriate version of Protocol Buffers from the official website.

Add the path of the protobuf to the system variables.

Create a Conda virtual environment and activate it:


Copy code
conda create -n tf pip python=3.9
conda activate tf
Install Protobuf:

Copy code
conda install protobuf
Automate the process of compiling Protocol Buffer files by creating the use_protobuf.py file in the research directory with the following code:
python
Copy code
import os
import sys
args = sys.argv
directory = args[1]
protoc_path = args[2]
for file in os.listdir(directory):
if file.endswith(".proto"):
os.system(protoc_path+" "+directory+"/"+file+" --python_out=.")
Run the use_protobuf.py file using the following command:
bash
Copy code
cd /path/to/models/research
python use_protobuf.py object_detection/protos protoc
Copy the setup file from the research directory and run it:
bash
Copy code
cp object_detection/packages/tf2/setup.py .
python -m pip install .
Install NumPy:
bash
Copy code
conda install numpy
Test if everything is installed correctly by running the following command:
bash
Copy code
python object_detection/builders/model_builder_tf2_test.py
Output
Once you have completed the above steps, you should see the output similar to the one shown below:

markdown
Copy code
....
----------------------------------------------------------------------
Ran 4 tests in 0.010s

OK (skipped=1)
