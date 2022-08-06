# GreenRed_AppleClassification
This is my proposed project during the KPT-PACE Machine Learning workshop. This project objective to help colorblind people differentiate between green and red apple and also between rooten one and fresh one

To download this project to your Jetson Nano
'git clone https://github.com/Syukta8/GreenRed_AppleClassification.git'

It also can be download on your local machine to do the training beforehand. Input your data set inside '/data' folder.
To train your dataset, you need to make sure that all library inside 'train.py' are installed inside your docker(Jetson Nano) or environment(Local Machine)

To start training your dataset:
'python train.py --model-dir=models/apple --epochs=50 --batch-size=4 --workers=2 --lr=0.001 --arch=resnet34 data/apple'
