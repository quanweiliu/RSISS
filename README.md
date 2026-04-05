# From Pixels to Images: A Structural Survey of Deep Learning Paradigms in Remote Sensing Image Semantic Segmentation



This repository is our remote sensing image semantic segmentation survey. We split the remote sensing image semantic segmentation into four categories, i.e., pixel-level, patch-level, tile-level, and image-level semantic segmentation. 

Patch-level, and tile-level semantic segmentation methods domian this study area. We collect an array of papers and the corresponding codes here. It's noting that we designed a unified pipeline for these codes, which could help the beginners learning this techniques and  validating new datasets performance.  In addition, we also provide some supplementary materials, like experiments result and extra discussions related to remote sensing image semantic segmentation.

We hople this reposity has a little promotes to the remote sensing communities prosperous.

![Framework Image](framework.png)



## The patch-based classification repository
- refer to: https://github.com/quanweiliu/TilewiseSegFra


## The tile-based segmentation repository
- refer to: https://github.com/quanweiliu/PatchwiseClsFra


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
