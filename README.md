# image-crowd-counter

![app icon](./img/appIcon.png)

A deep learning model automatically counts the number of people in any image.

No internet connection or login is required—completely ad-free.

<p float="left">
    <img src="./img/preview_1.jpg" alt="preview_1" width="200" />
    <img src="./img/preview_2.jpg" alt="preview_2" width="200" />
    <img src="./img/preview_3.jpg" alt="preview_3" width="200" />
    <img src="./img/preview_4.jpg" alt="preview_4" width="200" />
</p>

Counting people in a scene manually can be challenging.

Image Crowd Counter simplifies this by automating the counting process.

It functions entirely on-device, ensuring privacy and accessibility without the need for internet or login.

- Optimized for overhead views of crowds ranging from 10 to 500 people.
- This app may not function properly on older devices.

Contact: dev.jang1suh@gmail.com

---

This is a personal project to build an iOS app that includes a deep learning model running on mobile devices.

Recent deep learning models have become increasingly large, making it challenging to run them on mobile devices.

I wondered, "Which tasks are useful when run on mobile devices and can be solved with moderately sized models?"

I discovered the task of crowd counting, which I might sometimes want to solve using my mobile devices, without any registration or internet connection.

### Model
The model included in this app is **SASNet**, introduced in the following paper: [To Choose or to Fuse? Scale Selection for Crowd Counting](https://ojs.aaai.org/index.php/AAAI/article/view/16360) (AAAI 2021)

Their implementation and trained model is publicly open in [this repo](https://github.com/TencentYoutuResearch/CrowdCounting-SASNet) under the Apache License Version 2.0 ([license](./oss_licenses/license_SASNet.md)).

I converted their PyTorch model, which was already trained with the [SanghaiTech dataset](https://ieeexplore.ieee.org/document/7780439) part B, into the Core ML package format using [coremltools](https://github.com/apple/coremltools), and then wrote an iOS app with SwiftUI that provides the user interface for using the model.

The model accepts an input image with a size of 1024 x 768, so the app provides an image cropper that resizes images to that size.

### References
- TOCropViewController ([license](./oss_licenses/license_TOCropViewController.md)): https://github.com/TimOliver/TOCropViewController
- Camera: https://enebin.medium.com/swiftui만-써서-호다닥-카메라앱-만들기-intro-65fd95ba5327, https://betterprogramming.pub/effortless-swiftui-camera-d7a74abde37e
