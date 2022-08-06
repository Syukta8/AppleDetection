# GreenRed_AppleClassification
This is my proposed project during the KPT-PACE Machine Learning workshop. This project objective to help colorblind people differentiate between green and red apple and also between fresh and rotten one. Please note that all the code below need to be run in terminal and to be safe, run inside your Docker or Environment

![Fresh apple](https://www.kindpng.com/picc/m/153-1533376_red-apple-and-green-apple-png-download-red.png)

***1) Download project to your Jetson Nano:***
```
git clone https://github.com/Syukta8/GreenRed_AppleClassification.git
```

It also can be download on your local machine to do the training beforehand. Input your data set inside `/data` folder. You can search the dataset on [Kaggle](https://www.kaggle.com/datasets?search=apple+fruit)
.To train your dataset, you need to make sure that all library inside `train.py` are installed inside your docker(Jetson Nano) or environment(Local Machine)

***2) To start training your dataset, run this:***
```
python train.py --model-dir=models/apple --epochs=50 --batch-size=4 --workers=2 --lr=0.001 --arch=resnet34 data/apple
```
You can adjust the epoch, batch size, learning rate and pre-trained model accordingly. The model file will be save inside `/models/apple` with name `model_best.pth.tar`

***3) After finish training, run the conversion file `onnx_export.py` to convert the tar format to onnx format:***
```
python onnx_export.py --model-dir=models/apple
```
You will find a file inside `/models/apple` with name `resnet34.onnx`. The file will depends on the pretrained model name that you use during the training.You can also download the file from my drive,


***4) To run the inference:***
>from image:
>```
>python imagenet.py --model=models/apple/resnet34.onnx --input_blob:input_0 --output_blob:output_0 --labels=data/apple/labels.txt image.jpg
>```
>from video
>```
>python imagenet.py --model=models/apple/resnet34.onnx --input_blob:input_0 --output_blob:output_0 --labels=data/apple/labels.txt video.mp4
>```
>from webcam
>```
>python imagenet.py --model=models/apple/resnet34.onnx --input_blob:input_0 --output_blob:output_0 --labels=data/apple/labels.txt /dev/video0
>```
To check which webcam available in your jetson, run `/dev/video*` in the terminal before running inference code.

**Please comment any improvement that can be add into the code.Thank you for using this programs.** 
