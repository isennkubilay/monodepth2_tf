
# monodepth2_tf

Tensorflow implementation for the method in Self-Supervised Monocular Depth Prediction

> [arXiv 2018](https://arxiv.org/abs/1806.01260)

<p align="center">
  <img src="monodepth2_tf/resultsresult_2.png" alt="monodepth2_tf/results/result_2.png" width="600" />
</p>



```
@article{monodepth2,
  title     = {Digging into Self-Supervised Monocular Depth Prediction},
  author    = {Cl{\'{e}}ment Godard and
               Oisin {Mac Aodha} and
               Michael Firman and
               Gabriel J. Brostow},
  journal = {arXiv:1806.01260},
  year = {2018}
}
```

## Eval Result (with pretrained model link)
https://drive.google.com/file/d/13jYuDrHiK9uoRmu1rXUxSBv-yEx6tzWJ/view?usp=sharing
https://drive.google.com/file/d/1Bk9gMrzuF_QrDRv11ILrqv3xHvqxZR2a/view?usp=sharing



## Prerequisites
Tensorflow 1.13 cpu version and Ubuntu 18.04
I created fresh environment. I called this environment name 'stm'  
## Setup
Assuming a fresh [Anaconda](https://www.anaconda.com/download/) distribution, you can install the dependencies with:
```shell
conda create -n stm python=3.6
conda activate stm
conda install -c conda-forge opencv
conda install -c conda-forge matplotlib
conda install -c anaconda scikit-image
conda install -c conda-forge tensorflow 
```
##Setup Specs 
Ubuntu 18.04
Python 3.6
Tensorflow(cpu) 1.13
GeForce MX150
Intel® Core™ i7-8550U CPU @ 1.80GHz × 8 
15.5 GB
Gnome 3.28.2

## Preparing training data

For [KITTI](http://www.cvlibs.net/datasets/kitti/raw_data.php), first download the dataset
```bash
python monodepth2_tf/monodepth2.py--dataset_dir=/home/isen/ --dataset_name="kitti_raw_eigen" --save_root=/home/isen/kitti/formatted/data --seq_length=3 --img_width=416 --img_height=128 --num_threads=4
```

## Demonstration
<p align="center">
  <img src="results/prepare_train_data_result.png" alt="results/result_2.png" width="600" />
</p>


## Training

Set dataset/saved_log path at monodepth2_kitti.yml

```shell
python monodepth2.py train config/monodepth2_kitti.yml events.out.tfevents.1572969053.kubilay
```

## Testing
```
python monodepth_single.py --image_path ~/monodepth_tf/0000000003.png --checkpoint_path ~/monodepth_tf/utils/output_directory/events.out.tfevents.1572969053.kubilay
```

<p align="center">
  <img src="results/final_result_1.PNG" alt="example input output" width="600" />
</p>


## Reference Codes
- Monodepth2
  - https://github.com/nianticlabs/monodepth2

- SfmLearner
  - https://github.com/tinghuiz/SfMLearner
  
- MonoDepth-Pytorch
  - https://github.com/ClubAI/MonoDepth-PyTorch

## TODO
- [x] Self-Supervised Monocular Depth Prediction
- [x] Preparing Data
- [x] Testing part
- [ ] Evaluation 
