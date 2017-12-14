# GANs for Biological Image Synthesis
This codes implements the ICCV-2017 paper "GANs for Biological Image Synthesis". The paper and its supplementary materials is available on [arXiv](https://arxiv.org/abs/1708.04692).

This code contains the following pieces:
- implementation of [DCGAN](https://github.com/pytorch/examples/tree/master/dcgan), [WGAN](https://github.com/martinarjovsky/WassersteinGAN), [WGAN-GP](https://github.com/igul222/improved_wgan_training)
- implementation of green-on-red separable DCGAN, multi-channel DCGAN, star-shaped DCGAN (see our ICCV 2017 paper for details)
- implementation of the evaluation techniques: classifier two-samples test and reconstruction of the test set

The code is released under Apache v2 License allowing to use the code in any way you want.
For the license on the LIN dataset, please contact the authors of Dodgson et al. (2017).

As a teaser, we show our final results (animated interpolations that mimic the cell growth cycle) right away:
![lin_movie2.gif](http://www.di.ens.fr/sierra/research/biogans/lin_movie2.gif "Cell cycle reconstruction 2")
![lin_movie3.gif](http://www.di.ens.fr/sierra/research/biogans/lin_movie3.gif "Cell cycle reconstruction 3")
![lin_movie1.gif](http://www.di.ens.fr/sierra/research/biogans/lin_movie1.gif "Cell cycle reconstruction 1")

### Citation

If you are using this software please cite the following paper in any resulting publication:

Anton Osokin, Anatole Chessel, Rafael E. Carazo Salas and Federico Vaggi, GANs for Biological Image Synthesis, in proceedings of the International Conference on Computer Vision (ICCV), 2017.

>@InProceedings{osokin2017biogans,<br>
    author      = {Anton Osokin and Anatole Chessel and Rafael E. Carazo Salas and Federico Vaggi},<br>
    title       = {{GANs} for Biological Image Synthesis},<br>
    booktitle   = {Proceedings of the International Conference on Computer Vision (ICCV)},<br>
    year        = {2017} }

### Authors of Biogan research paper and code

* [Anton Osokin](http://www.di.ens.fr/~osokin/)
* [Anatole Chessel](https://scholar.google.com/citations?user=GC8aiVsAAAAJ&hl=en)
* [Rafael E. Carazo Salas](http://research-information.bristol.ac.uk/en/persons/rafael-e-carazo-salas(a7638b29-53e4-49ba-82b5-98b21d82f41f).html)
* [Federico Vaggi](https://scholar.google.it/citations?user=rgIbvJsAAAAJ&hl=en)

### Authors of modified Biogan code(GAN for yeast cells)

* [Anurag Arora](https://github.com/geekyspartan)
* [Renu Rani](https://github.com/techiepanda)


### Requirements

This software was written for python v3.6.1, [pytorch](http://pytorch.org/) v0.2.0 (earlier version won't work; later versions might face some backward compatibility issues, but should work), [torchvision](https://github.com/pytorch/vision)  v0.1.8 (comes with pytorch).
Many other python packages are required, but the standard [Anaconda](https://repo.continuum.io/archive/Anaconda3-4.4.0-Linux-x86_64.sh) installation should be sufficient.

We tested this code on Ubuntu 16.04 and Macbook, but in case of Macbook we encountered issues related to symbolic linking. So it's better to test and run this code on Linux environment only. Also GPU is preferred so that code can be run for enough iterations to get promissing images.

### Usage
This code is modified version of Biogan research paper by Anton Osokin, Anatole Chessel, Rafael E. Carazo Salas and Federico Vaggi, GANs for Biological Image Synthesis, in proceedings of the International Conference on Computer Vision (ICCV), 2017.

The modified code contains training and testing data to generate fake single channel images of yeast cell.

Note that rerunning all the experiements would require significant computational resources. We recommend using a cluster of GPU if you want to do that.

##### Preparations
Get the code
```
git clone https://github.com/geekyspartan/biogans.git
```
Mark the root folder for the code
```
cd biogans
export ROOT_BIOGANS=`pwd`
```
##### Generating fakes images of yeast cell
```
cd $ROOT_BIOGANS/experiments/models_6class_joint
./train_size-48-80_6class_wgangp-adam.sh
