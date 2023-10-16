# PKSS-Align: A New Registration Method

It is an implementation for the paper “PKSS-Align”. The source code will be released when the paper is accepted. The complied version and related exe file are released at first for testing.


## Introduction

This work is an improved version based on [KSS-ICP](https://github.com/vvvwo/KSS-ICP). It can be used to register point clouds with large difference of poses, different scales, noisy points, and defective parts at the same time. With a well designed GPU-based structure, the computational efficiency is improved obviously.

## Citation
If you find our work useful in your research, please consider citing:

    @article{lv2023kss,
         title={KSS-ICP: Point Cloud Registration Based on Kendall Shape Space},
         author={Lv, Chenlei and Lin, Weisi and Zhao, Baoquan},
         journal={IEEE Transactions on Image Processing},
         volume={32},
         pages={1681--1693},
         year={2023},
         publisher={IEEE}
    }

## Comparsions

In this part, we introduce some selected methods to estbalish comparsions in different registration tasks. Test datasets and codes of all selected methods are provided in this repository. Some registration instances and related quantitative anlayis reports are shown at the same time. We hope such data can help some ones who are focus on point cloud-based registration research work.  

### Selected Methods:

| Paper | Method | Type | Published | Code | Keywords | 
| ----------- | ---------- | ------------| ---------- | ------ | ------ |
| [pdf](https://www.cvl.iis.u-tokyo.ac.jp/class2004/wedenesday/report/besl.pdf) | ICP | Distance Metric | TPAMI1992 | [PCL](https://pointclouds.org/documentation/group__registration.html) | iterative closest point |
| [pdf](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=1f16244ce2e78881c7c96b33796a930ce73f7972) | NDT | Feature-based | IROS2003 | [PCL](https://pointclouds.org/documentation/group__registration.html) | normal distributions transform |
| [pdf](https://d1wqtxts1xzle7.cloudfront.net/57266988/%E9%85%8D%E5%87%861-s2.0-S0020025516300378-main-libre.pdf?1535550009=&response-content-disposition=inline%3B+filename%3DA_fast_and_robust_local_descriptor_for_3.pdf&Expires=1695559709&Signature=GfZiqp7Tdw7U-y2mFA0Qm2CVGMULmiKoecgzpeHe5xUAc9NZquvmf-fwND9X23l6KcBp9WSbuA4~o0o6xnX47~6031pWgIPlrnBiLVAensxI47G9UoDRxOHlRtjyQtGGN9~~-OdDUGQAeCDGN1GdNmgjTGnZkurPGiN8RAw3eFCorLrwrDAofJPw-hWdmwkfe~iMev866eK02-ujeiryPSb5Br3L-xRSwG7C9DmV2cZneJAm7bFo9f0c8zVb6HfRRHMHjOsFWDkKrnLJR8t~LOOeJz8JWhrXY73InpzzDA35GdkXgomhm7mJheMHuZyjsMjUMF1l5okvROvVrjryHw__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA) | FPFH | Feature-based | Information Sciences2016 | [PCL](https://pointclouds.org/documentation/group__registration.html) | local descriptor, FEATURE HISTOGRAMS |
| [arvix](https://arxiv.org/abs/1605.03344) | Go-ICP | Distance Metric | TPAMI2016 | [Official](https://github.com/yangjiaolong/Go-ICP) | ICP, Global Searching |
| [cvf](https://openaccess.thecvf.com/content_CVPR_2019/papers/Aoki_PointNetLK_Robust__Efficient_Point_Cloud_Registration_Using_PointNet_CVPR_2019_paper.pdf) | PointNetLK | Deep Learning | CVPR2019 | [Github](https://github.com/hmgoforth/PointNetLK) | PointNet, Lucas&Kanade|
| [arvix](https://arxiv.org/pdf/2007.07627.pdf) | Fast-ICP | Distance Metric | TPAMI2022 | [Official](https://github.com/yaoyx689/Fast-Robust-ICP) | Majorization-minimization, Welsch’s function|
| [arvix](https://arxiv.org/pdf/2007.07627.pdf) | Robust-ICP | Distance Metric | TPAMI2022 | [Official](https://github.com/yaoyx689/Fast-Robust-ICP) | Majorization-minimization, Welsch’s function|
| [cvf](https://openaccess.thecvf.com/content/CVPR2022/papers/Qin_Geometric_Transformer_for_Fast_and_Robust_Point_Cloud_Registration_CVPR_2022_paper.pdf) | Geo-Transformer | Deep Learning | CVPR2022  | [Official](https://github.com/qinzheng93/GeoTransformer) | Transformer, RANSAC |
| [cvf](https://openaccess.thecvf.com/content/CVPR2023/papers/Zhang_3D_Registration_With_Maximal_Cliques_CVPR_2023_paper.pdf) | Maximal Cliques | Feature-based | CVPR2023 | [Official](https://github.com/zhangxy0517/3D-Registration-with-Maximal-Cliques) | Maximal Cliques (**Best Student Paper**) |
| [pdf](https://aliexken.github.io/papers/2022_KSS.pdf) | KSS-ICP | Distance Metric | TIP2023 | [Official](https://github.com/vvvwo/KSS-ICP) | Kendall Shape Space |
<!-- | []() | | NR | | []() |  -->

### Visualization

<img width="1280" alt="image" src="https://github.com/vvvwo/PKSS-Align/assets/65271555/af1b4e05-3f15-4038-bb12-e78ef6c6bae1">

<img width="1051" alt="image" src="https://github.com/vvvwo/PKSS-Align/assets/65271555/84c2d085-27de-4c1c-ac55-9ad5ce878b10">

### Test Report:
We test selected methods and PKSS-Align in the two datasets: [ModelNet40](https://modelnet.cs.princeton.edu/) and [S3DIS](http://buildingparser.stanford.edu/dataset.html#Download).

The registration test datasets have been prepared ([here](https://share.weiyun.com/HEq6xgF8)), which contains different source point clouds with various influnece factors, template point clouds, and related ground truth transformations.

The quantitative anlaysis results are shown in following tables:

**Table1: Test Report on ModelNet40 with similarity transformations:**
| Method | Time | MSE | MSE(n) | GT_cos |
| ----------- | ---------- | ------------| ---------- | ------ |
| ICP | 1.981s | 0.01253 | 0.6915 | 0.4259 | 
| NDT | 3.719s | 0.01157 | 0.6735 | 0.4079 | 
| FPFH | 16.665s | 0.00106 | 0.2163 | 0.6837 | 
| Go-ICP | 33.101s | **0.00014** | 0.0885 | 0.7824 | 
| PointNetLK | 0.903s | 0.02621 | 0.7476 | 0.3871 | 
| Fast-ICP | 6.798s | 0.00808 | 0.5255 | 0.4668 | 
| Robust-ICP | 22.921s | 0.01207 | 0.4849 | 0.4838 | 
| Geo-Transformer | **0.563s** | 0.09309 | 0.8018 | 0.4776 | 
| Maximal-Cliques | 2.513s | 0.02898 | 0.4558 | 0.6688 | 
| []() |  | []() |
| KSS-ICP | 2.899s | 0.00033 | 0.1233 | 0.7648 | 
| PKSS-Align | 2.938s | 0.00051 | **0.0589** | **0.9026** | 
<!-- | []() | | NR | | []() |  -->

