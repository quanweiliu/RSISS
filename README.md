# From Pixels to Images: A Structural Survey of Deep Learning Paradigms in Remote Sensing Image Semantic Segmentation



This repository is our remote sensing image semantic segmentation (RRSIS) survey. We split remote sensing image semantic segmentation into four categories: pixel-level, patch-level, tile-level, and image-level. 

Patch-level and tile-level semantic segmentation methods dominate this study area. We collect a set of papers and their corresponding code here. It's worth noting that we designed a unified pipeline for these codes, which could help beginners learn these techniques and validate the performance of new datasets.  In addition, we provide supplementary materials, such as experimental results and additional discussions related to remote sensing image semantic segmentation.

We hope this repository will contribute to the prosperity of the remote sensing community.

![Framework Image](framework.png)


## Experiments

To ensure a fair and rigorous quantitative comparison across all evaluated deep learning models, we established a standardized experimental environment and utilized a highly representative multimodal remote sensing benchmark dataset, complementing the macro-level qualitative analysis presented in our survey paper.

### Dataset Specifications

The empirical evaluations compiled in this repository were conducted on the Multimodal Oil Spill Dataset, commonly referred to as MOSD. This dataset was collected from the Gulf of Mexico, a region spanning parts of the United States, Mexico, and Cuba, located near 25 degrees North and 90 degrees West. The data captures the aftermath of the major environmental disaster on April 20, 2010, where over 780,000 cubic meters of crude oil were released into the ocean. 

The dataset contains 18 paired multimodal scenes with an average image dimension of 1502 by 594 pixels, consisting of two perfectly coregistered modalities:
* **Hyperspectral Imagery:** Acquired by the Airborne Visible and Infrared Imaging Spectrometer, capturing spectral information from 365 to 2500 nanometers across 224 original bands. Following common preprocessing practices, 31 noisy bands were removed, resulting in 193 highly usable spectral bands.
* **Synthetic Aperture Radar:** Simulated based on RADARSAT 2 observations from the Canadian Space Agency and rigorously resampled to match the exact spatial resolution of the hyperspectral data, forming a paired HSI and SAR multimodal dataset.

Ground truth reference maps were manually annotated using ENVI software following established rigorous annotation guidelines.

#### 1. Training and Evaluation Protocols

To support both patch-based and tile-based experimental evaluations, the data were preprocessed using distinct strategies tailored to the operational requirements of each segmentation paradigm.

#### 2. Protocols for Models at the Patch Level
For patch-based approaches, images were extracted pixel by pixel following prior studies. To rigorously address class imbalance during model optimization, 1000 random samples were selected from each minority class in area 1, while 2000 samples were explicitly allocated for the majority water class.

#### 3. Protocols for Models at the Tile Level
For tile-based architectures, the paired scene data were systematically cropped into fixed-size tiles of 128 by 128 pixels utilising a sliding window stride of 64 pixels. The entire MOSD dataset was then split into training, validation, and test sets following a three to one to two ratio. This exact partitioning yielded 1981 training subimages, 647 validation subimages, and 1201 test subimages. For this paradigm, the full partitioned dataset was utilized for training and testing without any further sampling.

#### 4. Hardware Environment
All representative models were implemented, trained, and tested under a unified computing environment to eliminate systemic hardware variations. The experiments were accelerated using an NVIDIA GeForce RTX 3090 graphics processing unit with 24 gigabytes of video memory, deployed on the PyTorch deep learning framework.


### The patch-based classification repository
- Refer to: https://github.com/quanweiliu/TilewiseSegFra

#### 1. Accuracy Benchmarks

The following table summarizes the quantitative accuracy metrics (Precision, Recall, F1, Kappa, mIoU) for both Patch-based and Tile-based segmentation models.

| Category | Model | Water | Oil | Accuracy | Precision | Recall | F1 | Kappa | mIoU |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Patch-based Unimodal HSI** | [SSRN](https://ieeexplore.ieee.org/abstract/document/8061020) | 89.02 | 89.88 | 89.03 | 64.21 | 89.45 | 68.62 | 39.26 | 58.40 |
| | [BASSNet](https://ieeexplore.ieee.org/abstract/document/7938656) | 78.82 | 93.21 | 79.41 | 58.37 | 86.01 | 58.33 | 23.20 | 47.75 |
| | [FDSSC](https://www.mdpi.com/2072-4292/10/7/1068) | 87.00 | 90.19 | 87.10 | 61.67 | 88.60 | 65.22 | 33.11 | 54.92 |
| | [DFFN](https://ieeexplore.ieee.org/abstract/document/8283837) | 97.92 | 34.88 | 95.23 | 70.58 | 66.40 | 67.88 | 35.83 | 59.42 |
| | [DHCNet](https://ieeexplore.ieee.org/abstract/document/8361481) | 89.73 | 57.15 | 88.29 | 60.28 | 73.45 | 62.82 | 27.37 | 53.97 |
| | [MDL](https://ieeexplore.ieee.org/abstract/document/9174822) | 89.34 | 91.52 | 89.40 | 63.69 | 90.43 | 68.39 | 38.59 | 58.06 |
| | [SPRN](https://ieeexplore.ieee.org/abstract/document/9454961) | 77.95 | 86.21 | 78.22 | 56.95 | 82.08 | 56.15 | 19.24 | 45.88 |
| | [SSFTTNet](https://ieeexplore.ieee.org/abstract/document/9684381) | 97.21 | 35.75 | 94.56 | 66.63 | 66.48 | 66.42 | 32.86 | 58.11 |
| | [FDGC](https://ieeexplore.ieee.org/abstract/document/9785802) | 90.68 | 90.02 | 90.61 | 65.10 | 90.35 | 70.24 | 41.90 | 59.99 |
| | [MAVHN](https://www.sciencedirect.com/science/article/pii/S0957417423015348) | 83.26 | 92.56 | 83.64 | 60.82 | 87.91 | 62.75 | 29.95 | 52.33 |
| | [VIT-DGCN](https://www.sciencedirect.com/science/article/pii/S1569843224001341) | 92.38 | 88.36 | 92.16 | 66.55 | 90.37 | 72.21 | 45.31 | 62.01 |
| | [KnowCL](https://arxiv.org/abs/2404.01673) | 94.84 | 76.54 | 94.05 | 69.36 | 85.69 | 74.23 | 48.88 | 64.44 |
| **Patch-based Unimodal SAR** | [BASSNet](https://ieeexplore.ieee.org/abstract/document/7938656) | 97.92 | 93.49 | 97.73 | 82.98 | 95.71 | 88.13 | 76.30 | 80.46 |
| | [DFFN](https://ieeexplore.ieee.org/abstract/document/8283837) | 95.73 | 97.36 | 95.81 | 75.04 | 96.54 | 81.99 | 64.21 | 72.57 |
| | [DHCNet](https://ieeexplore.ieee.org/abstract/document/8361481) | 98.06 | 97.28 | 98.03 | 84.43 | 97.67 | 89.83 | 79.69 | 82.80 |
| | [MDL](https://ieeexplore.ieee.org/abstract/document/9174822) | 98.21 | 97.94 | 98.19 | 85.27 | 98.07 | 90.55 | 81.14 | 83.86 |
| | [SPRN](https://ieeexplore.ieee.org/abstract/document/9454961) | 97.79 | 95.14 | 97.68 | 82.63 | 96.46 | 88.17 | 76.37 | 80.47 |
| | [SSFTTNet](https://ieeexplore.ieee.org/abstract/document/9684381) | 97.24 | 94.11 | 97.11 | 79.86 | 95.68 | 85.86 | 71.79 | 77.40 |
| | [FDGC](https://ieeexplore.ieee.org/abstract/document/9785802) | 98.25 | 98.01 | 98.24 | 85.51 | 98.13 | 90.74 | 81.50 | 84.13 |
| | [MAVHN](https://www.sciencedirect.com/science/article/pii/S0957417423015348) | 98.41 | 97.51 | 98.38 | 86.51 | 97.96 | 91.36 | 82.74 | 85.06 |
| | [VIT-DGCN](https://www.sciencedirect.com/science/article/pii/S1569843224001341) | 98.39 | 96.17 | 98.30 | 86.21 | 97.28 | 90.92 | 81.85 | 84.39 |
| | [KnowCL](https://arxiv.org/abs/2404.01673) | 97.82 | 98.07 | 97.83 | 82.74 | 97.95 | 88.72 | 77.48 | 81.24 |
| **Patch-based Multimodal (HSI-SAR)** | [MDL-M](https://ieeexplore.ieee.org/abstract/document/9174822) | 98.31 | 96.97 | 98.24 | 85.77 | 97.64 | 90.73 | 81.47 | 84.10 |
| | [MDL-L](https://ieeexplore.ieee.org/abstract/document/9174822) | 98.27 | 97.39 | 98.22 | 85.50 | 97.83 | 90.62 | 81.26 | 83.95 |
| | [MDL-ED](https://ieeexplore.ieee.org/abstract/document/9174822) | 97.98 | 98.49 | 98.00 | 84.09 | 98.23 | 89.77 | 79.58 | 82.71 |
| | [FustNet](https://openaccess.thecvf.com/content_CVPRW_2020/html/w6/Mohla_FusAtNet_Dual_Attention_Based_SpectroSpatial_Multimodal_Fusion_Network_for_Hyperspectral_CVPRW_2020_paper.html) | 97.97 | 97.22 | 97.93 | 83.84 | 97.59 | 89.38 | 78.80 | 82.16 |
| | [HCTNet](https://ieeexplore.ieee.org/abstract/document/9999457) | 98.00 | 65.39 | 96.57 | 78.57 | 81.69 | 79.88 | 59.77 | 70.48 |
| | [S2Net](https://ieeexplore.ieee.org/abstract/document/9583936) | 98.38 | 95.61 | 98.24 | 85.93 | 96.99 | 90.59 | 81.19 | 83.90 |
| | [SHNet](https://www.sciencedirect.com/science/article/pii/S2352938525001545) | 98.49 | 97.11 | 98.42 | 86.85 | 97.80 | 91.51 | 83.04 | 85.27 |
| | [MS2CANet](https://ieeexplore.ieee.org/abstract/document/10382694) | 98.22 | 97.65 | 98.19 | 85.30 | 97.93 | 90.52 | 81.06 | 83.80 |
| | [Cross-HL](https://ieeexplore.ieee.org/abstract/document/10462184) | 98.54 | 95.27 | 98.39 | 86.94 | 96.90 | 91.24 | 82.50 | 84.88 |
---

#### 2. Computational Complexity & Efficiency Benchmarks

The following table details the computational cost (FLOPs), exact parameter counts, and processing speeds (Training time / Test time) to help developers gauge hardware requirements.

| Category | Model | Training time (s) | Test time (s) | FLOPs | Parameters |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Patch-based Unimodal HSI** | SSRN | 873.71 | 1706.49 | 185.33M | 354.60K |
| | BASSNet | 30.76 | 230.27 | 254.11K | 15.33K |
| | FDSSC | 9756.06 | 5154.94 | 674.52M | 2.31M |
| | DFFN | 441.68 | 1465.10 | 481.25M | 431.57K |
| | DHCNet | 293.29 | 2680.94 | 188.34M | 631.27K |
| | MDL | 40.71 | 344.89 | 4.13M | 80.93K |
| | SPRN | 99.18 | 429.85 | 7.16M | 71.87K |
| | SSFTTNet | 35.90 | 253.22 | 22.80M | 147.58K |
| | FDGC | 116.71 | 1263.06 | 29.48M | 2.38M |
| | MAVHN | 252.63 | 902.22 | 89.27M | 362.31K |
| | ViGCN | 306.52 | 1591.65 | 18.22M | 244.81K |
| | KnowCL | 113.81 | 387.83 | 471.27M | 12.13M |
| **Patch-based Unimodal SAR** | BASSNet | 14.09 | 159.07 | 144.67K | 9.25K |
| | DFFN | 154.58 | 1078.85 | 479.99M | 430.56K |
| | DHCNet | 351.36 | 2183.60 | 188.34M | 631.27K |
| | MDL | 21.99 | 173.68 | 1.44M | 53.57K |
| | SPRN | 35.13 | 715.14 | 6.56M | 65.79K |
| | SSFTTNet | 35.78 | 217.13 | 1.03M | 23.16K |
| | FDGC | 34.46 | 240.75 | 24.65M | 2.37M |
| | MAVHN | 95.78 | 827.92 | 30.42M | 119.11K |
| | ViGCN | 45.65 | 384.94 | 15.86M | 212.04K |
| | KnowCL | 90.81 | 400.88 | 471.27M | 12.13M |
| **Patch-based Multimodal (HSI-SAR)** | MDL-M | 47.88 | 418.87 | 5.41M | 125.60K |
| | MDL-L | 52.63 | 385.99 | 5.57M | 134.50K |
| | MDL-ED | 195.47 | 448.27 | 11.22M | 216.71K |
| | FustNet | 735.17 | 3902.16 | 7.02G | 37.30M |
| | HCTNet | 33.84 | 224.95 | 11.13M | 384.07K |
| | S2Net | 57.46 | 422.20 | 32.08M | 326.96K |
| | SHNet | 56.86 | 399.78 | 13.16M | 4.07M |
| | MS2CANet | 112.42 | 728.75 | 39.04M | 781.93K |
| | Cross-HL | 242.02 | 937.53 | 131.75M | 548.58K |
---


<!-- ### Qualititive Performance Benchmarks for RSISS -->


### The tile-based segmentation repository
- Refer to: https://github.com/quanweiliu/PatchwiseClsFra


#### 1. Accuracy Benchmarks

The following table summarizes the quantitative accuracy metrics (Precision, Recall, F1, Kappa, mIoU) for both Patch-based and Tile-based segmentation models.


| Category | Model | Water | Oil | Accuracy | Precision | Recall | F1 | Kappa | mIoU |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Tile-based Unimodal HSI** | [Unet](https://link.springer.com/chapter/10.1007/978-3-319-24574-4_28) | 98.52 | 71.68 | 97.05 | 85.10 | 86.02 | 85.55 | 71.10 | 76.99 |
| | [Unet++](https://link.springer.com/chapter/10.1007/978-3-030-00889-5_1) | 98.53 | 64.19 | 96.42 | 81.36 | 85.89 | 83.44 | 66.90 | 74.35 |
| | [DeepLabV3](https://arxiv.org/abs/1412.7062) | 97.38 | 63.74 | 95.89 | 80.56 | 75.62 | 77.84 | 55.70 | 68.23 |
| | [DeepLabV3+](https://openaccess.thecvf.com/content_ECCV_2018/html/Liang-Chieh_Chen_Encoder-Decoder_with_Atrous_ECCV_2018_paper.html) | 98.34 | 62.97 | 96.22 | 80.65 | 84.16 | 82.29 | 64.59 | 72.99 |
| | [Linknet](https://ieeexplore.ieee.org/abstract/document/8305148) | 98.56 | 71.08 | 97.02 | 84.82 | 86.38 | 85.58 | 71.16 | 77.02 |
| | [MANet](https://ieeexplore.ieee.org/abstract/document/9487010) | 97.68 | 81.75 | 97.08 | 89.72 | 78.71 | 83.21 | 66.47 | 74.23 |
| | [segformer](https://proceedings.neurips.cc/paper/2021/hash/64f1f27bf1b4ec22924fd0acb550c235-Abstract.html) | 98.22 | 69.78 | 96.74 | 84.00 | 83.37 | 83.68 | 67.37 | 74.70 |
| | [unetformer](https://www.sciencedirect.com/science/article/pii/S0924271622001654) | 98.50 | 66.31 | 96.60 | 82.40 | 85.67 | 83.95 | 67.90 | 74.97 |
| | [A2FPN](https://www.tandfonline.com/doi/full/10.1080/01431161.2022.2030071) | 98.33 | 68.71 | 96.72 | 83.52 | 84.33 | 83.92 | 67.84 | 74.97 |
| | [BANet](https://www.mdpi.com/2072-4292/13/16/3065) | 98.18 | 65.87 | 96.41 | 82.03 | 82.92 | 82.47 | 64.93 | 73.23 |
| | [DCSwin](https://ieeexplore.ieee.org/document/9681903) | 98.47 | 61.99 | 96.18 | 80.23 | 85.31 | 82.54 | 65.10 | 73.26 |
| | [AMSUnet](https://www.sciencedirect.com/science/article/pii/S0010482523005851) | 98.57 | 67.41 | 96.73 | 82.99 | 86.35 | 84.57 | 69.15 | 75.74 |
| | [ABCNet](https://www.sciencedirect.com/science/article/pii/S0924271621002379) | 98.29 | 63.38 | 96.24 | 80.84 | 83.78 | 82.23 | 64.47 | 72.93 |
| | [MambaUnet](https://arxiv.org/abs/2402.05079) | 98.13 | 69.44 | 96.66 | 83.78 | 82.55 | 83.15 | 66.31 | 74.07 |
| **Tile-based Unimodal SAR** | [Unet](https://link.springer.com/chapter/10.1007/978-3-319-24574-4_28) | 99.63 | 94.84 | 99.38 | 97.23 | 96.57 | 96.90 | 93.79 | 94.12 |
| | [Unet++](https://link.springer.com/chapter/10.1007/978-3-030-00889-5_1) | 99.63 | 94.72 | 99.37 | 97.18 | 96.58 | 96.87 | 93.75 | 94.08 |
| | [DeepLabV3](https://arxiv.org/abs/1412.7062) | 98.99 | 82.55 | 98.12 | 90.77 | 90.56 | 90.67 | 81.33 | 84.00 |
| | [DeepLabV3+](https://openaccess.thecvf.com/content_ECCV_2018/html/Liang-Chieh_Chen_Encoder-Decoder_with_Atrous_ECCV_2018_paper.html) | 99.49 | 89.34 | 98.94 | 94.41 | 95.18 | 94.80 | 89.59 | 90.48 |
| | [Linknet](https://ieeexplore.ieee.org/abstract/document/8305148) | 99.63 | 94.28 | 99.35 | 96.96 | 96.58 | 96.77 | 93.53 | 93.89 |
| | [MANet](https://ieeexplore.ieee.org/abstract/document/9487010) | 99.48 | 91.90 | 99.08 | 95.69 | 95.18 | 95.43 | 90.86 | 91.55 |
| | [segformer](https://proceedings.neurips.cc/paper/2021/hash/64f1f27bf1b4ec22924fd0acb550c235-Abstract.html) | 99.49 | 89.35 | 98.94 | 94.42 | 95.14 | 94.77 | 89.55 | 90.44 |
| | [unetformer](https://www.sciencedirect.com/science/article/pii/S0924271622001654) | 99.56 | 88.30 | 98.94 | 93.93 | 95.79 | 94.84 | 89.68 | 90.55 |
| | [A2FPN](https://www.tandfonline.com/doi/full/10.1080/01431161.2022.2030071) | 99.50 | 88.64 | 98.91 | 94.07 | 95.28 | 94.66 | 89.33 | 90.26 |
| | [BANet](https://www.mdpi.com/2072-4292/13/16/3065) | 99.60 | 91.27 | 99.15 | 95.44 | 96.20 | 95.82 | 91.63 | 92.21 |
| | [DCSwin](https://ieeexplore.ieee.org/document/9681903) | 99.42 | 83.38 | 98.50 | 91.40 | 94.40 | 92.84 | 85.68 | 87.30 |
| | [AMSUnet](https://www.sciencedirect.com/science/article/pii/S0010482523005851) | 99.67 | 95.02 | 99.43 | 97.35 | 96.94 | 97.14 | 94.28 | 94.56 |
| | [ABCNet](https://www.sciencedirect.com/science/article/pii/S0924271621002379) | 99.64 | 90.89 | 99.16 | 95.27 | 96.54 | 95.89 | 91.78 | 92.35 |
| | [MambaUnet](https://arxiv.org/abs/2402.05079) | 99.53 | 88.70 | 98.93 | 94.11 | 95.47 | 94.78 | 89.55 | 90.45 |
| **Tile-based Multimodal (HSI-SAR)** | [ACNet](https://ieeexplore.ieee.org/abstract/document/8803025) | 99.77 | 95.34 | 99.53 | 97.80 | 97.55 | 97.67 | 95.35 | 95.54 |
| | [CMGF](https://www.sciencedirect.com/science/article/pii/S0924271621003294) | 99.76 | 93.64 | 99.44 | 97.67 | 96.70 | 97.18 | 94.36 | 94.63 |
| | [CMANet](https://www.mdpi.com/1424-8220/22/21/8520) | 99.79 | 95.33 | 99.55 | 98.00 | 97.56 | 97.78 | 95.55 | 95.73 |
| | [CANet](https://www.sciencedirect.com/science/article/pii/S0031320321006440) | 99.81 | 93.90 | 99.50 | 98.11 | 96.86 | 97.47 | 94.95 | 95.17 |
| | [SFAFMA](https://ieeexplore.ieee.org/abstract/document/10103760) | 99.78 | 92.74 | 99.41 | 97.82 | 96.26 | 97.03 | 94.05 | 94.36 |
| | [PCG](https://ieeexplore.ieee.org/abstract/document/9859353) | 99.74 | 93.86 | 99.43 | 97.51 | 96.80 | 97.15 | 94.31 | 94.59 |
| | [AsymFormer](https://openaccess.thecvf.com/content/CVPR2024W/USM/papers/Du_AsymFormer_Asymmetrical_Cross-Modal_Representation_Learning_for_Mobile_Platform_Real-Time_RGB-D_CVPRW_2024_paper.pdf) | 99.39 | 91.56 | 98.98 | 94.35 | 95.47 | 94.90 | 89.81 | 90.66 |
| | [DE_CCFNet](https://ieeexplore.ieee.org/document/10439005) | 99.74 | 95.48 | 99.51 | 97.55 | 97.61 | 97.58 | 95.16 | 95.36 |
---

#### 2. Computational Complexity & Efficiency Benchmarks

The following table details the computational cost (FLOPs), exact parameter counts, and processing speeds (Training time / Test time) to help developers gauge hardware requirements.

| Category | Model | Training time (s) | Test time (s) | FLOPs | Parameters |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Tile-based Unimodal HSI** | Unet | 2510.44 | 82.83 | 2.89G | 14.33M |
| | Unet++ | 1927.30 | 166.06 | 8.19G | 15.98M |
| | DeepLabV3 | 1917.15 | 170.59 | 8.55G | 15.90M |
| | DeepLabV3+ | 2118.92 | 170.99 | 2.47G | 12.33M |
| | Linknet | 2096.52 | 157.24 | 1.70G | 11.67M |
| | MANet | 1838.95 | 149.60 | 2.91G | 11.99M |
| | segformer | 2665.81 | 168.38 | 4.66G | 44.60M |
| | unetformer | 2336.80 | 120.03 | 1.64G | 11.68M |
| | A2FPN | 2771.07 | 169.59 | 5.40G | 22.83M |
| | BANet | 2638.09 | 121.09 | 1.77G | 12.67M |
| | DCSwin | 1915.28 | 137.96 | 7.18G | 45.61M |
| | AMSUnet | 1961.85 | 102.79 | 3.24G | 2.63M |
| | ABCNet | 2643.28 | 149.38 | 2.09G | 13.33M |
| | MambaUnet | 1499.67 | 42.23 | 1.67G | 12.89M |
| **Tile-based Unimodal SAR** | Unet | 352.53 | 3.59 | 2.72G | 14.33M |
| | Unet++ | 878.93 | 3.92 | 8.02G | 15.97M |
| | DeepLabV3 | 533.25 | 3.31 | 8.38G | 15.90M |
| | DeepLabV3+ | 260.52 | 3.07 | 2.30G | 12.33M |
| | Linknet | 256.80 | 3.04 | 1.53G | 11.66M |
| | MANet | 370.03 | 6.52 | 2.74G | 11.99M |
| | segformer | 1085.14 | 12.54 | 4.49G | 44.60M |
| | unetformer | 257.77 | 6.89 | 1.47G | 11.67M |
| | A2FPN | 268.28 | 4.85 | 5.23G | 22.82M |
| | BANet | 358.96 | 7.28 | 1.59G | 12.66M |
| | DCSwin | 1009.89 | 10.44 | 7.01G | 45.61M |
| | AMSUnet | 2587.56 | 13.90 | 3.07G | 2.62M |
| | ABCNet | 267.32 | 5.90 | 1.92G | 13.33M |
| | MambaUnet | 594.64 | 8.97 | 1.50G | 12.89M |
| **Tile-based Multimodal (HSI-SAR)** | [ACNet | 5387.42 | 70.13 | 18.14G | 117.20M |
| | CMGF | 3166.78 | 57.91 | 14.34G | 45.38M |
| | CMANet  | 7820.55 | 68.42 | 14.32G | 117.82M |
| | CANet  | 4947.74 | 64.87 | 18.77G | 127.88M |
| | SFAFMA  | 3408.60 | 24.68 | 14.05G | 87.49M |
| | PCGNet  | 3750.01 | 22.75 | 29.04G | 22.36M |
| | AsymFormer  | 3291.95 | 27.43 | 4.43G | 33.32M |
| | DE_CCFNet  | 3205.94 | 27.02 | 8.70G | 54.56M |
---


## Other useful materials

### Datasets
We have included a dataset table for easy updating and reference.


**Summary of unimodal RS datasets used for SS, where SemanticSeg is an abbreviation of semantic segmentation.**

| Type | Datasets | Image size | GSD(m) | Classes | Area (km²) | Labels | Task | Year |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| HSI | Indian Pines (IP) | 1 × 145 × 145 × 224(200) | 20 | 16 | 8.41 | 10,249 | Classification | 1992 |
| HSI | Washington DC | 1 × 1208 × 307 × 210(191) | 1.5-3.0 | 7 | 1.48 | 26,332 | Classification | 1995 |
| HSI | Kennedy Space Center (KSC) | 1 × 512 × 614 × 224(176) | 18 | 13 | 101.86 | 4,756 | Classification | 1996 |
| HSI | Cuprite | 1 × 250 × 191 × 224 | 20 | 30 | 19.1 | 47,750 | Classification | 1997 |
| HSI | Salinas Valley (SV) | 1 × 512 × 217 × 224(204) | 3.7 | 16 | 1.52 | 54,129 | Classification | 1998 |
| HSI | University of Pavia (UP) | 1 × 610 × 340 × 115(103) | 1.3 | 9 | 0.63 | 42,776 | Classification | 2001 |
| HSI | Center of Pavia | 1 × 1096 × 715 × 115(102) | 1.3 | 9 | 2.03 | 148,152 | Classification | 2001 |
| HSI | HOSD | 18 × Variable × 224 | 3.2-8.1 | 2 | - | 14.84M | SemanticSeg | 2010 |
| HSI | Hyrank Dioni | 1 × 250 × 1376 × 176 | 30 | 12 | 309.6 | 20,024 | Classification | 2017 |
| HSI | Hyrank Loukia | 1 × 249 × 945 × 176 | 30 | 14 | 211.78 | 13,503 | Classification | 2017 |
| HSI | Matiwan Village | 1 × 3750 × 1580 × 250 | 0.5 | 20 | 1.48 | 5.925M | Classification | 2017 |
| HSI | WHU-Hi HanChuan | 1 × 1217 × 303 × 270 | 0.109 | 16 | 0.0044 | 368,751 | Classification | 2018 |
| HSI | WHU-Hi HongHu | 1 × 940 × 475 × 270 | 0.043 | 22 | 0.00083 | 446,500 | Classification | 2018 |
| HSI | WHU-Hi LongKou | 1 × 550 × 400 × 270 | 0.463 | 9 | 0.047 | 220,000 | Classification | 2018 |
| HSI | Xiongan | 1 × 3750 × 1580 × 250 | 0.5 | 19 | 1.481 | 2,941,881 | Classification | 2020 |
| HSI | AeroRIT | 1 × 1973 × 3975 × 372 | 0.4 | 5 | 1.25 | 7.843M | SemanticSeg | 2020 |
| HSI | WHU-OHS | 7795 × 512 × 512 × 32 | 10 | 24 | 26.21 | 90M | SemanticSeg | 2024 |
| MSI | Zurich Summer | 20 × 1000 × 1150 × 4 | 0.61 | 8 | 8.56 | 23M | SemanticSeg | 2015 |
| MSI | RIT-18 | 3 × Variable × 6 | 0.047 | 18 | 0.46 | 209 M | SemanticSeg | 2017 |
| MSI | LandCoverNet | 8941 × 256 × 256 × 10 | 10 | 7 | 58596 | 585.96M | SemanticSeg | 2020 |
| MSI | MADOS | 6754 × 240 × 240 × 11 | 10 | 15 | 38903 | 389.03M | SemanticSeg | 2024 |
| SAR | OSI | 1112 × 1250 × 650 × 1 | 10 | 5 | 90350 | 903.2M | SemanticSeg | 2019 |
| SAR | SOS-G | 3877 × 256 × 256 × 1 | 12.5 | 2 | 39700.48 | 254.08M | SemanticSeg | 2022 |
| SAR | SOS-P | 4193 × 256 × 256 × 1 | 5 × 20 | 2 | 27479.24 | 274.79M | SemanticSeg | 2022 |
| HRI | SpaceNet1 | 6000 × Variable × 3 | 0.5 | 2 | 2544 | - | SemanticSeg | 2017 |
| HRI | SpaceNet2 | 24586 × 650 × 650 × 3 | 0.3 | 2 | 3011 | 10.39B | SemanticSeg | 2017 |
| HRI | INRIA | 360 × 1500 × 1500 × 3 | 0.3 | 2 | 810 | 810M | SemanticSeg | 2017 |
| HRI | DeepGlobe | 1146 × 2448 × 2448 × 3 | 0.5 | 7 | 1716.9 | 6.87B | SemanticSeg | 2018 |
| HRI | Zeebruges | 7 × 1000 × 1000 × 3 | 0.05 | 8 | 1.75 | 7M | SemanticSeg | 2018 |
| HRI | GID | 150 × 6800 × 7200 × 3 | 4 | 5 | 506 | 7.34B | SemanticSeg | 2020 |
| HRI | GID-Fine | 30000 × 56 × 56 × 3 | 4 | 15 | 506 | 94.08M | SemanticSeg | 2020 |
| HRI | UAVid | 300 1.5 Variable × 3 | - | 8 | - | 2.5B | SemanticSeg | 2020 |
| HRI | LandCover.ai | 33 × 9000 × 9500 × 3<br>8 × 4200 × 4700 × 3 | 0.25-0.5 | 4 | 216.27 | 2.98B | SemanticSeg | 2021 |
| HRI | LoveDA | 5987 × 1024 × 1024 × 3 | 0.3 | 7 | 536.15 | 12B | SemanticSeg | 2021 |
| HRI | FloodNet | 2343 × 4000 × 3000 × 3 | 0.015 | 9 | 6.3 | 28B | SemanticSeg | 2021 |

**Summary of multimodal RS datasets used for SS, where ReferringSeg and ReasoningSeg are abbreviations of referring segmentation and reasoning segmentation, respectively**
| Datasets | Type | Image size | GSD(m) | Classes | Area (km²) | Labels | Task | Year |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Trento | HSI | 1 × 166 × 600 × 63 | 1 | 6 | 0.1 | 30,414 | Classification | 2007 |
| Trento | LiDAR | 1 × 166 × 600 × 2 | 1 | 6 | 0.1 | 30,414 | Classification | 2007 |
| Berlin | HSI | 1 × 1723 × 476 × 224 | 30 | 8 | 738.13 | 464,671 | Classification | 2009 |
| Berlin | SAR | 1 × 1723 × 476 × 4 | 30 | 8 | 738.13 | 464,671 | Classification | 2009 |
| MUUFL Gulfport | HSI | 1 × 325 × 220 × 64(72) | 1 | 11 | 0.07 | 53,687 | Classification | 2010 |
| MUUFL Gulfport | LiDAR | 1 × 325 × 220 × 2 | 1 | 11 | 0.07 | 53,687 | Classification | 2010 |
| DFC 2013 | HSI | 1 × 1095 × 349 × 144 | 2.5 | 15 | 2.39 | 15,029 | Classification | 2012 |
| DFC 2013 | LiDAR | 1 × 1095 × 349 × 1 | 2.5 | 15 | 2.39 | 15,029 | Classification | 2012 |
| ISPRS Vaihingen | RGB | 33 × Variable × 3 | 0.09 | 6 | 1.34 | 168M | SemanticSeg | 2013 |
| ISPRS Vaihingen | LiDAR | 33 × Variable × 1 | 0.09 | 6 | 1.34 | 168M | SemanticSeg | 2013 |
| ISPRS Vaihingen | DSM | 33 × Variable × 1 | 0.09 | 6 | 1.34 | 168M | SemanticSeg | 2013 |
| ISPRS Potsdam | MSI | 38 × 6000 × 6000 × 4 | 0.05 | 6 | 3.42 | 1.37B | SemanticSeg | 2013 |
| ISPRS Potsdam | LiDAR | 38 × 6000 × 6000 × 1 | 0.05 | 6 | 3.42 | 1.37B | SemanticSeg | 2013 |
| ISPRS Potsdam | DSM | 38 × 6000 × 6000 × 1 | 0.05 | 6 | 3.42 | 1.37B | SemanticSeg | 2013 |
| DFC 2018 | HSI | 1 × 601 × 2384 × 48 | 1 | 20 | 1.43 | 2.02M | Classification | 2017 |
| DFC 2018 | LiDAR | 1 × 1202 × 4768 × 3 | 0.5 | 20 | 1.43 | 2.02M | Classification | 2017 |
| DFC 2018 | RGB | 1 × 1202 × 4768 × 3 | 0.5 | 20 | 1.43 | 2.02M | Classification | 2017 |
| Augsburg | HSI | 1 × 332 × 485 × 180 | 30 | 7 | 144.92 | 78,293 | Classification | 2021 |
| Augsburg | SAR | 1 × 332 × 485 × 4 | 30 | 7 | 144.92 | 78,293 | Classification | 2021 |
| Augsburg | LiDAR | 1 × 332 × 485 × 1 | 30 | 7 | 144.92 | 78,293 | Classification | 2021 |
| LCZ | MSI | 1 × 626 × 643 × 10 | 100 | 10 | 4025.18 | 30,087 | Classification | 2021 |
| LCZ | SAR | 1 × 626 × 643 × 4 | 100 | 10 | 4025.18 | 30,087 | Classification | 2021 |
| C2Seg-AB | HSI | 1 × 2465 × 811 × 242<br>1 × 886 × 1360 × 242 | 10 | 13 | 20<br>12.05 | 2M<br>1.21M | SemanticSeg | 2023 |
| C2Seg-AB | MSI | 1 × 2465 × 811 × 4<br>1 × 886 × 1360 × 4 | 10 | 13 | 20<br>12.05 | 2M<br>1.21M | SemanticSeg | 2023 |
| C2Seg-AB | SAR | 1 × 2465 × 811 × 2<br>1 × 886 × 1360 × 2 | 10 | 13 | 20<br>12.05 | 2M<br>1.21M | SemanticSeg | 2023 |
| C2Seg-BW | HSI | 1 × 13474 × 8706 × 116(330)<br>1 × 6225 × 8670 × 116(330) | 10 | 13 | 1173.05<br>539.71 | 117.31M<br>5397M | SemanticSeg | 2023 |
| C2Seg-BW | MSI | 1 × 13474 × 8706 × 4<br>1 × 6225 × 8670 × 4 | 10 | 13 | 1173.05<br>539.71 | 117.31M<br>5397M | SemanticSeg | 2023 |
| C2Seg-BW | SAR | 1 × 13474 × 8706 × 2<br>1 × 6225 × 8670 × 2 | 10 | 13 | 1173.05<br>539.71 | 117.31M<br>5397M | SemanticSeg | 2023 |
| MDAS | SAR | 1 × 888 × 1371 × 2 | 10 | 16 | 121.75 | - | SemanticSeg | 2023 |
| MDAS | Lidar | 1 × 29600 × 45700 × 1 | 0.25 | 16 | 121.75 | - | SemanticSeg | 2023 |
| MDAS | MSI | 1 × 888 × 1371 × 12 | 10 | 16 | 121.75 | - | SemanticSeg | 2023 |
| MDAS | HSI | 1 × 4036 × 6232 × 368 | 2.2 | 16 | 121.75 | - | SemanticSeg | 2023 |
| Ticino | RGB | 1502 × 256 × 362 × 3 | 1.86-2.64 | 8/10 | 1331.72 | - | SemanticSeg | 2024 |
| Ticino | PAN | 1502 × 96 × 192 × 1 | 5 | 8/10 | 1331.72 | - | SemanticSeg | 2024 |
| Ticino | HSI VNIR | 1502 × 96 × 192 × 60(63) | 5 | 8/10 | 1331.72 | - | SemanticSeg | 2024 |
| Ticino | HSI SWIR | 1502 × 96 × 192 × 122(171) | 5 | 8/10 | 1331.72 | - | SemanticSeg | 2024 |
| Ticino | DTM | 1502 × 101 × 203 × 1 | 5 | 8/10 | 1331.72 | - | SemanticSeg | 2024 |
| SZUTreeData-R1 | RGB | 1 × 6170 × 4810 × 3 | 0.05 | 20 | 0.07 | 492,631 | Classification | 2025 |
| SZUTreeData-R1 | HSI | 1 × 3085 × 2405 × 112 | 0.1 | 20 | 0.07 | 492,631 | Classification | 2025 |
| SZUTreeData-R1 | LiDAR | 1 × 3085 × 2405 × 1 | 0.1 | 20 | 0.07 | 492,631 | Classification | 2025 |
| SZUTreeData-R2 | RGB | 1 × 8080 × 4888 × 3 | 0.05 | 21 | 0.1 | 696,620 | Classification | 2025 |
| SZUTreeData-R2 | HSI | 1 × 4040 × 2444 × 112 | 0.1 | 21 | 0.1 | 696,620 | Classification | 2025 |
| SZUTreeData-R2 | LiDAR | 1 × 4040 × 2444 × 1 | 0.1 | 21 | 0.1 | 696,620 | Classification | 2025 |
| RefSegRS | Text | 4420 | 0.13 | 14 | 19.58 | - | ReferringSeg | 2024 |
| RefSegRS | RGB | 4420 × 512 × 512 × 3 | 0.13 | 14 | 19.58 | - | ReferringSeg | 2024 |
| RRSIS-D | Text | 17402 | 0.5-30 | 20 | - | - | ReferringSeg | 2024 |
| RRSIS-D | RGB | 17402 × 800 × 800 × 3 | 0.5-30 | 20 | - | - | ReferringSeg | 2024 |
| RISBench | Text | 52472 | 0.1-30 | 26 | - | - | ReferringSeg | 2025 |
| RISBench | RGB | 52472 × 512 × 512 × 3 | 0.1-30 | 26 | - | - | ReferringSeg | 2025 |
| EarthReason | Text | 5434 | 0.5-153 | 28 | - | - | ReasoningSeg | 2025 |
| EarthReason | RGB | 5434 × Variable × 3 | 0.5-153 | 28 | - | - | ReasoningSeg | 2025 |

### Future direction 
We summarized some poential and promsing directions for future study.

| Future developments | Description | Explanation |
| :--- | :--- | :--- | 
|DATA |      |
|MODEL |      |
|LEARNING STRATEGIES |      |
