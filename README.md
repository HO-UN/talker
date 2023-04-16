# talker
（一）用conda创建虚拟环境激活虚拟环境，执行以下命令：
(
conda create -n talker python=3.8
conda activate talker
）
（二）在虚拟环境安装依赖通过输入以下安装命令：
1、pip install -r requirements.txt
2、pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu113
3、conda install   安装ffmpeg包
4、下载模型文件到checkpoints文件夹
①方式谷歌下载
https://drive.google.com/drive/folders/1Wd88VDoLhVzYsQ30_qDVluQr_Xm46yHT
②百度云下载
https://pan.baidu.com/s/1nXuVNd0exUl37ISwWqbFGA?pwd=sadt
（三）在当前目录环境（即在该项目根目录下）进入虚拟环境，通过python inference.py调用，另外同时还需要传入以下参数：
--driven_audio 传入音频的目录
--source_image 传入视频或者图片的目录
--result_dir  生成结果保存目录
Eg:用我们这边环境调用的样例如下：
Python inferencepy --driven _audio E: SadTalker examples driven audio chinese news.wav-source image E: SadTalker examples source image ref videol3.mp4--result dir E: temp-still --enhancer gfpgan
 
六、测试运行：
（一）音频导入：音频导入到项目文件SadTalker/examples/driven_audio目录下
 
（二）导入图片：图片导入到项目文件SadTalker/examples/ref_video目录下
 
（三）Cmd打开命令板：进入到SadTalker目录下执行以下命令，如我们将项目放在E盘下执行以下命令，对应的文件命令上文部署有解释
 
高级配置inference.py：
模式	配置参数	说明
增强模式	--enhancer	通过人脸恢复网络使用gfpgan或RestoreFormer增强生成的人脸
背景增强剂	--background_enhancer	用于realesrgan增强完整视频。
静态模式	--still	使用与原始图像相同的姿势参数，减少头部运动。
表达模式	--expression_scale	较大的值将使表情运动更强。
保存路径	--result_dir	该文件将保存在较新的位置。
预处理	--preprocess	在裁剪后的输入图像中运行并生成结果。其他选择：resize，其中图像将调整为特定分辨率。full运行完整的图像动画，使用 with--still以获得更好的效果。
参考模式（眼睛）	--ref_eyeblink	一个视频路径，我们从这个参考视频中借用眨眼来提供更自然的眉毛运动。
参考头	--ref_pose	一个视频路径，我们从头部参考视频中借用姿势。
