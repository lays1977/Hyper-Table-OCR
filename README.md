# Hyper-Table-Recognition

A carefully-designed OCR pipeline for universal boarded table recognition and reconstruction.

This pipeline covers image preprocessing, table detection(optional), text OCR, table cell extraction, table reconstruction.

## Demo
![gif demo](https://upyun.mrxiao.net/img/demo.gif)

Demo Video (In English): [YouTube](https://youtu.be/v2pe6cAofcw)

[![Hyper Table Recognition: A carefully-designed Table OCR pipeline](https://res.cloudinary.com/marcomontalbano/image/upload/v1608561697/video_to_markdown/images/youtube--v2pe6cAofcw-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/v2pe6cAofcw "Hyper Table Recognition: A carefully-designed Table OCR pipeline")

Demo Video WIP (In Chinese): [Bilibili](https://www.bilibili.com/video/BV1K64y1Z7XB)

## Features

- Flexible modular architecture: by deriving from predefined abstract class, any module of this pipeline can be easily swapped to your preferred one.
- A simple yet highly legible web interface, allowing user to check returned images of all stages in the pipeline.
- A table reconstruction strategy based simply on coordinates of each cell, including identifying merged cell row & building table structure.
- More to explore...

## Installation

### Clone this repo
```bash
git clone https://github.com/MrZilinXiao/Hyper-Table-Recognition
cd Hyper-Table-Recognition
```

### Download weights
Download from here: [GoogleDrive](https://drive.google.com/file/d/10NynXURJP2y1M7ScB0lzXnWcXba30PhM/view?usp=sharing) MD5: (004fabb8f6112d6d43457c681b435631  models.zip)

Unzip it and make sure the directory layout matchs:
```bash
# ~/Hyper-Table-Recognition$ tree -L 1
.
├── models
├── app.py
├── config.yml
├── ...
```

### Install Dependencies

This project is developed and tested on:

- Ubuntu 18.04
- RTX 3070 with Driver 455.45.01 & CUDA 11.1 & cuDNN 8.0.4
- Python 3.8.3
- PyTorch 1.7.0+cu110
- Tensorflow 2.5.0
- PaddlePaddle 2.0.0-rc1
- mmdetection 2.7.0
- onnxruntime-gpu 1.6.0

An NVIDIA GPU device is compulsory for reasonable inference duration, while GPU with less than 6GB VRAM may experience `Out of Memory` exception when loading multiple models. You may comment some models in `web/__init__.py` if experiencing such situation.

No version-specific framework feature is used in this project, so this means you could still enjoy it with lower versions of these frameworks. However, at this time(19th Dec, 2020), users with RTX 3000 Series device may not get compiled binary of Tensorflow, onnxruntime-gpu, mmdetection, PaddlePaddle via `pip` or `conda`. Also, for maximum device utilization rate, we strongly recommend all users to install these deep learning library by building from source.

Some building tutorials for Ubuntu are as follows:

- Tensorflow: [https://gist.github.com/kmhofmann/e368a2ebba05f807fa1a90b3bf9a1e03](https://gist.github.com/kmhofmann/e368a2ebba05f807fa1a90b3bf9a1e03)
- PaddlePaddle: [https://www.paddlepaddle.org.cn/install/quick?docurl=/documentation/docs/zh/2.0-rc1/install/compile/linux-compile.html](https://www.paddlepaddle.org.cn/install/quick?docurl=/documentation/docs/zh/2.0-rc1/install/compile/linux-compile.html)
- mmdetection: [https://mmdetection.readthedocs.io/en/latest/get_started.html#installation](https://mmdetection.readthedocs.io/en/latest/get_started.html#installation)
- onnxruntime-gpu: [https://github.com/microsoft/onnxruntime/blob/master/BUILD.md](https://github.com/microsoft/onnxruntime/blob/master/BUILD.md)

Confirm all deep learning frameworks installation via:
```bash
python -c "import tensorflow as tf; print(tf.__version__); import torch; print(torch.__version__); import paddle; print(paddle.__version__); import onnxruntime as rt; print(rt.__version__); import mmdets; print(mmdet.__version__)"
```

Then install other necessary libraries via:
```bash
pip install -r requirements.txt
```

### Enjoy!

```bash 
python app.py
```

Visit [http://127.0.0.1:5000](http://127.0.0.1:5000) to see the main page!

## Performance
Inference time consumption is highly related with following factors:

- Complexity of table structure
- Number of OCR blocks
- Resolution of selected image

A typical inference time consumption is shown in Demo Video.

## Want to contribute?
WIP

## Authors

*This project is a participator of the 1st MegMeet Cup Technology Innovation Competition of Sichuan University. Huangwei Wu([@ndwuhuangwei](https://github.com/ndwuhuangwei)) is our team leader, while he, Zilin Xiao([@MrZilinXiao](https://github.com/MrZilinXiao)) and Ruinan Fan([@ruinanfan](https://github.com/ruinanfan)) all act as key developers of this project. It's impossible to complete this work without their effort.*

**Congratulations! This project earns a GRAND PRIZE(2 out of 72 participators) of the aforementioned competition!**
## Acknowledgement

- [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR): Multilingual, awesome, leading, and practical OCR tools supported by Baidu.
- [ChineseOCR_lite](https://github.com/ouyanghuiyu/chineseocr_lite): Super light OCR inference tool kit.
- [CascadeTabNet](https://github.com/DevashishPrasad/CascadeTabNet): An automatic table recognition method for interpretation of tabular data in document images.
- [pytorch-hed](https://github.com/sniklaus/pytorch-hed): An unofficial implementation of Holistically-Nested Edge Detection using PyTorch.
