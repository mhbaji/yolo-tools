# yolo V4

* repo: https://github.com/AlexeyAB/darknet.git

## Improve Configuration
* change line batch to batch=64
* change line subdivisions to subdivisions=16
* change line max_batches to (classes*2000, but not less than number of training images and not less than 6000), f.e. max_batches=6000 if you train for 3 classes
* change line steps to 80% and 90% of max_batches, f.e. steps=4800,5400
* set network size width=416 height=416 or any value multiple of 32
* change line classes=80 to your number of objects in each of 3 [yolo]-layers
* change [filters=255] to filters=(classes + 5)x3 in the 3 [convolutional] before each [yolo] layer, keep in mind that it only has to be the last [convolutional] before each of the [yolo] layers
* If you train the model to distinguish Left and Right objects as separate classes (left/right hand, left/right-turn on road signs, ...) then for disabling flip data augmentation - add flip=0 in line 17

## Format .data
classes = 2 <br />
train  = data/train.txt <br />
valid  = data/test.txt <br />
names = data/obj.names <br />
backup = backup/ <br />

## create file train.txt and test.txt
> soon

## CLI to train
> ./darknet detector train data/obj.data yolo-obj.cfg yolov4.conv.137