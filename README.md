# OA-Stereo: Self-Supervised Opti-Acoustic Stereo for Robust 3D Perception of Underwater Vehicles

This work has been accepted by **IEEE Robotics and Automation Letters (RA-L)**, 2025.

## Introduction
<div align="center">
    <img alt="image" src="https://github.com/user-attachments/assets/4fb909c1-7422-42fa-97be-db6e206e38c0" width="100%" />
    <img alt="image" src="https://github.com/user-attachments/assets/adf04fa7-bce6-470f-bb91-29fc7798c5ad" width="50%" />
</div>

Accurate 3D perception is essential for underwater vehicles in tasks such as seabed mapping, structural reconstruction, and environmental monitoring. However, optical cameras struggle in underwater environments due to light attenuation, scattering, and blurring, while forward-looking sonar suffers from both acoustic noise and lack of elevation angle. Existing methods exploring opti-acoustic stereo imaging predominantly rely on cross-modal matching, yet they remain constrained by sparse reconstruction and exhibit low robustness. To address these limitations, we propose OA-Stereo, a novel self-supervised opti-acoustic stereo framework that integrates calibrated optical and acoustic images for dense depth map estimation, enabling robust 3D perception under adverse optical, acoustic, and calibration conditions. Our key contributions include: (1) OA-StereoNet, a novel architecture that iteratively refines disparity estimation through fusion of optical and acoustic lookup information; and (2) SIGC Loss, a cross-modal self-supervised loss that improves training by promoting consistency between reconstructed and observed sonar images. Extensive experiments conducted on both simulated and real-world underwater datasets demonstrate that OA-Stereo achieves state-of-the-art accuracy and stability under degraded visual conditions, sonar noise, and extrinsic calibration errors.

## Software Architecture
* scripts: Scripts for running various training/visualization tasks.
* src: Core source code, including network architecture, datasets, loss functions, and general utility code.

## Environment Setup

Tested Environment: PyTorch 2.3.0, CUDA 12.1

Installation Process:

```bash
conda create -n oastereo python=3.10
conda activate oastereo
conda install pytorch==2.3.0 torchvision==0.18.0 pytorch-cuda=12.1 -c pytorch -c nvidia
pip install -r requirements.txt
```

## Datasets

### Dave Sonar Datasets:

A custom dataset collected based on the [DAVE project](https://github.com/Field-Robotics-Lab/DAVE), used for both training and model validation.  
**Download via Hugging Face**: [c237814486/dave_sonar](https://huggingface.co/datasets/c237814486/dave_sonar)

### Dataset Directory Structure:

```bash
├── datasets
    ├── dave_sonar
        ├── scene1
        │   ├── cam_depth.yaml
        │   ├── cam_left
        │   ├── cam_left.yaml
        │   ├── cam_right
        │   ├── cam_right.yaml
        │   ├── depthl
        │   ├── displ
        │   ├── sonar
        │   ├── sonar_view
        │   ├── sonar_view_origin
        │   └── sonar.yaml
        ├── scene2
        │   ├── cam_depth.yaml
        │   ├── cam_left
        │   ├── cam_left.yaml
        │   ├── cam_right
        │   ├── cam_right.yaml
        │   ├── depthl
        │   ├── displ
        │   ├── sonar
        │   ├── sonar_view
        │   ├── sonar_view_origin
        │   └── sonar.yaml
        ├── scene3
        │   ├── cam_depthl.yaml
        │   ├── cam_depthr.yaml
        │   ├── cam_depth.yaml
        │   ├── cam_left
        │   ├── cam_left.yaml
        │   ├── cam_right
        │   ├── cam_right.yaml
        │   ├── depthl
        │   ├── depthr
        │   ├── displ
        │   ├── sonar
        │   ├── sonar_view
        │   ├── sonar_view_origin
        │   └── sonar.yaml
        └── scene4
            ├── cam_depthl.yaml
            ├── cam_depthr.yaml
            ├── cam_depth.yaml
            ├── cam_left
            ├── cam_left.yaml
            ├── cam_right
            ├── cam_right.yaml
            ├── depthl
            ├── depthr
            ├── displ
            ├── sonar
            ├── sonar_view
            ├── sonar_view_origin
            └── sonar.yaml
```

## **Visualization, Validation, and Training**

- **Visualization**: Use the script `scripts/show.sh` to visualize stereo matching results.
- **Validation**: Use the script `scripts/valid.sh` to evaluate the model on validation datasets.
- **Training**: Use the script `scripts/train.sh` to train the model from scratch.

## Citation

If you find this work useful for your research, please consider citing:

```bibtex
@article{cao2025oa,
  title={OA-Stereo: Self-Supervised Opti-Acoustic Stereo for Robust 3D Perception of Underwater Vehicles},
  author={Cao, Yaozhong and Bai, Xuejian and Chu, Hongfei and Wang, Shuo and Tan, Min and Wang, Yu},
  journal={IEEE Robotics and Automation Letters},
  year={2025},
  publisher={IEEE}
}
Part of the code is adopted from previous works: [SAFT-Stereo](https://github.com/c237814486/SAFT-Stereo), [CoEx](https://github.com/antabangun/coex), [RAFT-Stereo](https://github.com/princeton-vl/RAFT-Stereo), [UWStereo](https://github.com/kskin/UWStereo), [Monodepth2](https://github.com/nianticlabs/monodepth2)
