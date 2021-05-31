# Detection-and-count-CBB
Detection and counting of the coffee berry borer (Hypothenemus hampei) using the YOLO family.

The files presented correspond to the weights obtained from the training of the two yolov5 models.
We present a folder with the data structure for training the CBB.yaml file of the project.
and the fitted models for CBB_yolov5m.pt and CBB_yolov5s.pt

You can use these trained and validated models for CBB detection using a GPU laptop with 2.0 GB ram or use google colab.
	#step 1. Create an environment in anaconda prompt
	conda create -name CBB_yolo
	#step2. activate env
	conda activate CBB_yolo
	cd c:/
	#Step3 
	install git
	#Step 4 
	clone repository yolov5
	git clone https://github.com/ultralytics/yolov5  
	cd yolov5
	pip install -r requirements.txt  # install

You need to move the CBB_yolov5s and CBB_yolov5m in this repo in directory c:\yolov5>weigth

	python detect.py --weights ./runs/train/exp15/weights/best_CBB_yolov5m.pt --img 5000 --conf 0.6 --source ./data/Broca2000/examp --save-txt #Example using three images
	python detect.py --weights ./runs/train/exp15/weights/best_CBB_yolov5s --img 5000 --conf 0.6 --source ./data/Broca2000/examp --save-txt #Example using three images

If you training custom data go to: https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data
you can use the adjusted models as weight

You can colab 

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

	!python detect.py --weights weights/best_CBBs.pt --img 3456 --conf 0.58 --source data/Broca2000/TAM_ORI/MANI --save-txt --device 0

NOTE: In the file yololv5>utils>general in line 434 max_det = 300 change by other number for example max_det =10000
This is important in case you do not change max_det the maximum detections the model can do is 300






