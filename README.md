# Image_Stitching
# FAR-Based Image Stitching Pipeline

This project implements an **image-stitching pipeline** using the **FAR (Feature-Aggregation Regression)** model for relative camera pose estimation. After obtaining rotation **R** and translation **t** between two images, the pipeline computes a **homography**, warps the second image, computes translation shifts, and blends the images to create a stitched panorama.

---

## Features
- FAR model inference for camera pose (R, t)
- Resize images to 540×720
- Compute homography using intrinsic matrix K and rotation R
- Warp the second image using perspective transform
- Compute translation shifts after warp
- Alpha-blending for smooth stitching
- Final panorama visualization


---

##  Dependencies

Install dependencies:

```bash
pip install torch torchvision opencv-python numpy matplotlib pillow
pip install yacs loguru einops scikit-image
pip install pytorch-lightning
pip install kornia timm tensorboard
pip install gdown

1. Clone FAR repository
git clone https://github.com/crockwell/far.git
cd far
2. Download pretrained FAR weights
cd mapfree_6dreg
wget https://fouheylab.eecs.umich.edu/~cnris/far/model_checkpoints/mapfree_6dreg/pretrained_models.zip --no-check-certificate
unzip pretrained_models.zip
3. Download LoFTR weights
pip install gdown
gdown https://drive.google.com/drive/folders/1xu2PQ6mZT5hmFGiYMBT9Zt8h1yO-3SlP -O etc/feature_matching_baselines/LoFTR/weights --folder
4. Resize input images
imgA = cv2.imread("/content/imgA.JPG")
imgB = cv2.imread("/content/imgB.JPG")

resA = cv2.resize(imgA, (720, 540))
resB = cv2.resize(imgB, (720, 540))
5. Run FAR model inference

Outputs:

Rotation matrix: R

Translation vector: t
6. Compute homography
H = K * R * K^{-1}

7. Warp image B
8. Compute translation shift
9. Alpha-Blending
Output

The final stitched result looks like a panorama created by:

i. Homography warp

ii. Shift correction

iii. Blending



