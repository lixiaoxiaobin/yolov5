# yolov5
目标检测yolov5

#做了一个哆啦A梦的识别检测模型

#训练命令：
# 使用yolov5s模型训练coco128数据集5个epochs，batch size设为16
$ python train.py --batch 16 --epochs 5 --data ./data/coco128.yaml --weights ./weights/yolov5s.pt

有参：
--weights (⭐)指定权重，如果不加此参数会默认使用COCO预训的yolov5s.pt，--weights ''则会随机初始化权重
--cfg 指定模型文件
--data (⭐)指定数据文件
--hyp指定超参数文件
--epochs (⭐)指定epoch数，默认300
--batch-size (⭐)指定batch大小，默认16，官方推荐越大越好，用你GPU能承受最大的batch size，可简写为--batch
--img-size 指定训练图片大小，默认640，可简写为--img
--name 指定结果文件名，默认result.txt
--device 指定训练设备，如--device 0,1,2,3
--local_rank 分布式训练参数，不要自己修改！
--log-imgs W&B的图片数量，默认16，最大100
--workers 指定dataloader的workers数量，默认8
--project 训练结果存放目录，默认./runs/train/
--name 训练结果存放名，默认exp
无参：
--rect矩形训练
--resume 继续训练，默认从最后一次训练继续
--nosave 训练中途不存储模型，只存最后一个checkpoint
--notest 训练中途不在验证集上测试，训练完毕再测试
--noautoanchor 关闭自动锚点检测
--evolve超参数演变
--bucket使用gsutil bucket
--cache-images 使用缓存图片训练
--image-weights 训练中对图片加权重
--multi-scale 训练图片大小+/-50%变换
--single-cls 单类训练
--adam 使用torch.optim.Adam()优化器
--sync-bn 使用SyncBatchNorm，只在分布式训练可用
--log-artifacts 输出artifacts,即模型效果
--exist-ok 如训练结果存放路径重名，不覆盖已存在的文件夹
--quad 使用四分dataloader

#快速检测命令：
# 快速推理，--source 指定检测源，以下任意一种类型都支持：
$ python detect.py --source 0  # 本机默认摄像头
                            file.jpg  # 图片 
                            file.mp4  # 视频
                            path/  # 文件夹下所有媒体
                            path/*.jpg  # 文件夹下某类型媒体
                            rtsp://170.93.143.139/rtplive/470011e600ef003a004ee33696235daa  # rtsp视频流
                            http://112.50.243.8/PLTV/88888888/224/3221225900/1.m3u8  # http视频流
                            
#测试模型：
#python detect.py --weights ./runs/train/exp2/weights/best.pt --img 640 --conf 0.25 --source ../test.jpg
