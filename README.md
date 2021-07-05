# Detection-and-count-CBB
Detection and counting of the coffee berry borer (Hypothenemus hampei) using the YOLO family.
(https://github.com/SVMendoza/Detection-and-count-CBB/exam1.jpg)

The files presented correspond to the weights obtained from the training of the two yolov5 models.
We present a folder with the data structure for training the CBB.yaml file of the project.
and the fitted models for CBB_yolov5m.pt and CBB_yolov5s.pt

You can use these trained and validated models for CBB detection using a GPU laptop with 2.0 GB ram with Anaconda or use google colab.
<p>In Anaconda </p>

	conda create -name CBB_yolo #step 1. Create an environment in anaconda prompt
	conda activate CBB_yolo #step2. activate env
	cd c:/ #Dir root
 	install git #Step3
	git clone https://github.com/ultralytics/yolov5  #Step 4 	clone repository yolov5
	cd yolov5
	pip install -r requirements.txt  # install

You need to move the CBB_yolov5s and CBB_yolov5m in this repo in directory c:\yolov5>weigth

	python detect.py --weights ./runs/train/exp15/weights/CBB_yolov5s.pt --img 3456 --conf 0.58 --source ./data/Broca2000/examp --save-txt 	#Example 
	python detect.py --weights ./runs/train/exp15/weights/CBB_yolov5m.pt --img 3456 --conf 0.73 --source ./data/Broca2000/examp --save-txt 	#Example 

If you training custom data go to: https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data
you can use the adjusted models as weight

You can colab see https://colab.research.google.com/github/ultralytics/yolov5/blob/master/tutorial.ipynb

	from google.colab import drive
	drive.mount('/content/drive')
	%cd /content/drive/MyDrive/CBB
	!git clone https://github.com/ultralytics/yolov5


	%cd /content/drive/MyDrive/CBB/Yolov5/yolov5/
	%pip install -qr requirements.txt 
	%pip install -qr requirements.txt 


	import torch
	from IPython.display import Image, clear_output  # to display images
	clear_output()
	print(f"Setup complete. Using torch {torch.__version__} ({torch.cuda.get_device_properties(0).name if torch.cuda.is_available() else 'CPU'})")

	!python detect.py --weights weights/CBB_yolov5s.pt --img 3456 --conf 0.58 --source data/Broca2000/TAM_ORI/MANI --save-txt --device 0
	!python detect.py --weights weights/CBB_yolov5m.pt --img 3456 --conf 0.73 --source data/Broca2000/TAM_ORI/MANI --save-txt --device 0
NOTE: In the file yololv5>utils>general in line 434 **max_det = 300** change by other number for example **max_det =10000**.
This is important in case you do not change **max_det** the maximum detections the model can do is 300


Citation: ***Vilchez-Mendoza S., Bagny Beilhe L., Bommel P., Cilas C., Ronin A., Carval D.: Detection and counting of coffee berry borer (Hypothenemus hampei): using computer vision algorithm. 28th International Conference on Coffee Science (ASIC). 29/2021.***

**Reference:**

<p>Redmon, and Farhadi. 2018. YOLOv3: An incremental improvement. p. 6, ArXiv e‐prints. Google Scholar</p>
<p>Tresson et al. 2019. CORIGAN: Assessing multiple species and interactions within images. Methods in Ecology and Evolution. 10. 11: 1888-1893. https://doi.org/10.1111/2041-210X.13281</p>
<p>Tresson URL: https://gitlab.com/ptresson/corigan</p>
<p>Jocher, et al. 2021. Ultralytics/yolov5: v5.0 - YOLOv5-P6 1280 models, AWS, Supervise.ly and YouTube integrations (Version v5.0). Zenodo. http://doi.org/10.5281/zenodo.4679653. URL: https://github.com/ultralytics/yolov5/tree/master</p>




