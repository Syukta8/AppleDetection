# GreenRed_AppleClassification
This is my proposed project during the KPT-PACE Machine Learning workshop. This project objective to help colorblind people differentiate between green and red apple and also between fresh and rotten one

![Fresh apple](https://lzd-img-global.slatic.net/g/p/48778fdc015e4fb6f51de46bbcd8e9cd.jpg_720x720q80.jpg_.webp)

To download this project to your Jetson Nano
```
git clone https://github.com/Syukta8/GreenRed_AppleClassification.git
```

It also can be download on your local machine to do the training beforehand. Input your data set inside `/data` folder.
To train your dataset, you need to make sure that all library inside `train.py` are installed inside your docker(Jetson Nano) or environment(Local Machine)

To start training your dataset, run this:
```
python train.py --model-dir=models/apple --epochs=50 --batch-size=4 --workers=2 --lr=0.001 --arch=resnet34 data/apple
```
You can adjust the epoch, batch size, learning rate and pre-trained model accordingly. The model file will be save inside `/models/apple` with name `model_best.pth.tar`

After finish training, run the conversion file `onnx_export.py` to convert the tar format to onnx format:
```
python onnx_export.py --model-dir=models/apple
```
