# Guia de Detecção de Objetos com YoloV5
<p>Esssa documentação fornece um conjunto completo de códigos para treinar e usar seu próprio modelo personalizado de detecção de objetos usando a API de Detecção de Objetos do Yolov5.

<img src="https://raw.githubusercontent.com/ultralytics/assets/main/yolov5/v70/splash.png">

## Steps
<br />
<b>Step 1.</b> Open the repo on google collab: <a href="https://colab.research.google.com/github/gusmendess/gusmendess/blob/main/Object_Detection_YoloV5.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>
<br/><br/>
<b>Step 2.</b> Make sure you are in a Python environment and connect to a Virtual GPU (NOTE: The available GPUs have different processing powers, choose the best available)
<pre>
<img src="https://i.imgur.com/BHvoxrE.jpg"> 
</pre> 
<br/>
<b>Step 3.</b> Clone repo and install requirements.txt in a Python>=3.8.0 environment, including PyTorch>=1.8.
<pre>
!git clone https://github.com/ultralytics/yolov5  # clone
%cd yolov5
%pip install -qr requirements.txt comet_ml  # install

import torch
import utils
display = utils.notebook_init()  # checks
</pre>
<br/>
<b>Step 4.</b> Connect to your Google Drive
<pre>
from google.colab import drive
drive.mount('/content/drive')
</pre>
<br/>
<b>Step 5.</b> Use the command below to extract the dataset present in your drive folder. You have to found the exactly location of the dataset.
<pre>
import zipfile
import os

#Caminho completo do arquivo ZIP e diretório de destino
caminho_zip = '/content/drive/MyDrive/yolov5/dataset.zip'
diretorio_destino = '/content'

#Extrair o arquivo ZIP
with zipfile.ZipFile(caminho_zip, 'r') as zip_ref:
    zip_ref.extractall(diretorio_destino)

print("ZIP file extracted successfully.")
</pre>
<b>Step 6.</b> 
Create a .yaml file with a structure similar to the example and use the command below to copy it from your drive to the yolov5 repository folder.

<img src="https://i.imgur.com/Qw0MCdo.jpg"> 

<pre>
import shutil

#Full path of the source folder and destination directory
pasta_origem = '/content/drive/MyDrive/yolov5/data/helm.yaml'
diretorio_destino = '/content/yolov5/data'

#Copy source folder to destination directory
shutil.copy(pasta_origem, diretorio_destino)

print("Folder copied successfully.")
</pre>
<b>Step 7.</b> 
Select an extension for real-time analysis of your training

<img src="https://i.imgur.com/6ivxbmC.jpg"> 

<pre>
#@title Select YOLOv5 🚀 logger {run: 'auto'}
logger = 'Comet' #@param ['Comet', 'ClearML', 'TensorBoard']

if logger == 'Comet':
  %pip install -q comet_ml
  import comet_ml; comet_ml.init()
elif logger == 'ClearML':
  %pip install -q clearml
  import clearml; clearml.browser_login()
elif logger == 'TensorBoard':
  %load_ext tensorboard
  %tensorboard --logdir runs/train

</pre>
<b>Step 8.</b> Start the training. Make sure to understand the parameters of the yolo's documentation (--img; --batch; --epochs; --data; --weights; etc...), this will completely influence the performance of your artificial intelligence.
<pre>
#@title
!python train.py --img 640 --batch 50 --epochs 80 --data /content/yolov5/data/helm.yaml --weights yolov5s.pt --cache

</pre>

<b>Step 9.</b> Start the detection. Make sure to understand the parameters of the yolo's documentation (--img; --source; --data; --weights; etc...), this will completely influence the performance of your object detection.
<pre>

!python detect.py --weights runs/train/exp/last.pt --conf 0.7 --source construction_site.mp4
#See the results in the folder "runs/detect/exp"
</pre>

</b> Remember that once you disconnect from google collab you lost all the files. Save the "last.pt" file of your training or the final detection to export later.
