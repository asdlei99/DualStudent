# Dual Student: Breaking the Limits of the Teacher in Semi-supervised Learning


This is the PyTorch implementation for our paper [Dual Student: Breaking the Limits of the Teacher in Semi-supervised Learning](https://arxiv.org/abs/1909.01804). 
The style of code follows the official implementation of [Mean Teacher](https://github.com/CuriousAI/mean-teacher) (Code from their repository is inside the folder `./third_party/mean_teacher`). 

## Citation
If you use our method or code in your research, please cite:
```bibtex
@InProceedings{DualStudent_2019_ICCV,
　author = {Zhanghan Ke and Daoye Wang and Qiong Yan and Jimmy Ren and Rynson W.H. Lau},
　title = {Dual Student: Breaking the Limits of the Teacher in　Semi-supervised Learning},
　booktitle = {The IEEE International Conference on Computer Vision (ICCV)},
　year = {2019}
}
```

## Preparation
This code runs on Python 3 with PyTorch 0.3.1. If you use Anaconda 3:
1. Create a new python environment and switch to it:
    ```
    conda create -n dual_student python=3.5
    source activate dual_student
    ```

2. Install PyTorch 0.3.1:
    ```
    conda install pytorch=0.3.1 torchvision cudaXX -c pytorch
    ```
    \* Please replace ''cudaXX'' by your cuda version, e.g., ''cuda80'' for cuda 8.0.

3. Install other dependencies:
    ```
    pip install numpy scipy pandas tqdm matplotlib
    ```

4. Clone this repository by:
    ```
    git clone https://github.com/ZHKKKe/DualStudent.git
    ```

## Experiments

### Semi-supervised Learning with Dual Student
Running on the CIFAR benchmark with 1 GPU:
1. Switch to the project folder `./DualStudent` and prepare the CIFAR dataset by following commands:
    ```
    ./third_party/data-local/bin/prepare_cifar10.sh
    ./third_party/data-local/bin/prepare_cifar100.sh
    ```

2. We provide pre-trained models for experiments `CIFAR-10 with 1k labels` and `CIFAR-100 with 10k labels`.Please download them from [[link]](https://drive.google.com/drive/folders/1AjGfiw7U8grEhNBZVHXlk0h1W_u7sVKs?usp=sharing) and put them into `./checkpoints`. Then, you can run:
    ```
    python -m scripts.ds_cifar10_1000l_cnn13
    python -m scripts.ds_cifar100_10000l_cnn13
    ```
    \* Naming rule of script/model is ''`[method]_[dataset]_[labels number]_[model archtecture]`''.

3. If you want to train models yourselves, please comment following two lines on scripts as:

    ```
    # 'resume'  : './checkpoints/xxx',
    # 'validation': True,
    ```
    Then, you can run:
    ```
    python -m scripts.ds_cifar10_1000l_cnn13
    python -m scripts.ds_cifar100_10000l_cnn13
    ```

Please use `python dual_student.py --help` to check command line arguments.
