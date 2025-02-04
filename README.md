# Efficient-Live-Portrait
## 📹 Video Demo for normal mode
 

https://github.com/user-attachments/assets/ac0e92d7-34e1-4402-a202-d06a2e806abe

## 📹 Video Demo for Face-ID mode
+ Single Face Image
  ![368220873_826368889022136_4472311944594836999_n](https://github.com/user-attachments/assets/25851766-a454-4f16-8d44-f63923cdabf2)

+ Through Face-ID adapter
   

https://github.com/user-attachments/assets/197a8d75-3c56-43f5-ac71-e7110d9e53d1


## Introduction
This repo is the optimize task by converted to ONNX and TensorRT models for [LivePortrait: Efficient Portrait Animation with Stitching and Retargeting Control](https://github.com/KwaiVGI/LivePortrait).
We are actively updating and improving this repository. If you find any bugs or have suggestions, welcome to raise issues or submit pull requests (PR) 💖.

Also we adding feature: 
+ Real-Time demo with ONNX models
+ TensorRT runtime with latest Tensorrt version. You should run on Colab, this still can't use on Window
+ Face-ID adapter for control Face animation in the Multiple Faces image you want to do
+ Coming soon for ControlNet Stable Diffusion. Stay tuned
## Features
[✅] 20/07/2024: TensorRT Engine code and Demo

[✅] 22/07/2024: Support Multiple Faces

[✅] 22/07/2024: Face-ID Adapter for Control Face Animation

[  ] Integrate X-pose TensorRT

[  ] Integrate SadTalker with Efficient Live Portrait for generate realistic video

[  ] Integrate Animate-Diff Lightning Motion module


## 🔥 Getting Started
### 1. Clone the code and prepare the environment
```bash
git clone https://github.com/aihacker111/Efficient-Live-Portrait
# create env using conda
conda create -n ELivePortrait python==3.10.14
conda activate ELivePortrait
# install dependencies with CPU
pip install -r requirements-cpu.txt
# install dependencies with GPU
pip install -r requirements-gpu.txt
# install dependencies with pip for mps
pip install -r requirements-mps.txt 
```

**Note:** make sure your system has [FFmpeg](https://ffmpeg.org/) installed!

### 2. Download pretrained weights

The pretrained weights is also automatic downloading
You don't need to download and put model into sources code
```text
pretrained_weights
|
├── landmarks
│   └── models
│       └── buffalo_l
│       |   ├── 2d106det.onnx
│       |    └── det_10g.onnx
|       └── landmark.onnx
└── live_portrait
      |
      ├── appearance_feature_extractor.onnx
      ├── motion_extractor.onnx
      ├── generator_warping.onnx
      ├── stitching_retargeting.onnx
      └── stitching_retargeting_eye.onnx
      └── stitching_retargeting_lip.onnx
      ├── appearance_feature_extractor_fp32.engine
      ├── motion_extractor_fp32.engine
      ├── generator_fp32.engine
      ├── stitching_fp32.engine
      └── stitching_eye_fp32.engine
      └── stitching_lip_fp32.engine
      ├── appearance_feature_extractor_fp16.engine
      ├── motion_extractor_fp16.engine
      ├── generator_fp16.engine
      ├── stitching_fp16.engine
      └── stitching_eye_fp16.engine
      └── stitching_lip_fp16.engine
      

```
### 3. Inference and Real-time Demo 🚀
#### Fast hands-on

+ TensorRT FP32 is seem slower than FP16 but result better than fp16, so be careful to use both of it, I'm not recommend using ONNX model because it's not still update and fix grid sample or speed
+ Also If you want to Quality Result. Please remove FP16, the speed can be slower than fp16 but result is better
```bash
python run_live_portrait.py -v 'path/to/your/video/driving/or/webcam/id' -i 'path/to/your/image/want/to/animation' -ref 'path/the/single/face/image/to/compute/face-id' -r '/use/it/when/you/want/to/run/real-time/' -e -fp16 
```
#### Colab Demo
 Follow in the colab folder
### 5. Inference speed evaluation 🚀🚀🚀

We'll release it soon
