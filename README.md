About blahb
=====

The Better Looking Atlas of the Human Brain (Blahb) is a finely detailed anatomical segmentation of the [high-resolution version of the Colin 27 average brain](http://www.bic.mni.mcgill.ca/ServicesAtlases/Colin27Highres). It is intended to serve as a detailed, comprehensive neuroanatomical reference suitable specifically for generating appealing visualisations such as those featured by [neuroanatomist](http://neuroanatomist.org).

The segmentation was based upon an automatic segmentation of the whole brain and neocortex from the source image using [BrainVISA 4.2](http://brainvisa.info/). The automatic segmentation was then cleaned up and additional labels added using [Seg3D2](http://www.sci.utah.edu/cibc-software/seg3d.html).

blahb is designed to be extended and adapted as required and community contributions are welcome. The design philosophy is that any spatial feature of the brain which can be meaningfully and neatly segmented within the source image, should be. Thus different levels of granularity or systems of parcellation may coexist (e.g. lobes, gyri, sulci, brodmann areas, functional areas etc).

Tools have been created for automatically processing set of layers exported from Seg3D2 and producing a single multilayer image and an accompanying *labels.txt* file (see [*Using blahb*](#using-blahb) for more details). If you have any queries which are not addressed in this documentation, feel free to email me: *(Nat Noordanus)  n **at** natn.me*

About version 0.1.0
=====
This is the first release of blahb. To summarise, it includes  a nearly complete segmentation of the gyri of the right hemisphere, and the left temporal lobe, as well as the lobes of the left hemisphere. It also includes segmentations of many major subcortical structures, including the cerebellum, brainstem, midbrain, basal ganglia, hypothalamus and right thalamus. A complete list of structures can be seen in the *[labels.txt](https://raw.github.com/gnatters/blahb/releases/0.1.0/blahb_labels_0_1_0.txt)* available via the [*Getting blahb*](#getting-blahb) section.

Getting blahb
=====
Balhb is be available in three forms:

* three Seg3D2 projects (including layers for the right neocortex, left neocortex and subcortical regions respectively) from the [GitHub repository](https://github.com/gnatters/blahb)
* [a set of NIfTI files](https://raw.github.com/gnatters/blahb/releases/0.1.0/blahb_segments_0_1_0.zip) (one for each segment) which can be edited read or edited seperately
* [a single NIfTI file](https://raw.github.com/gnatters/blahb/releases/0.1.0/blahb_0_1_0.nii.gz) and an accompanying [labels](https://raw.github.com/gnatters/blahb/releases/0.1.0/blahb_labels_0_1_0.txt) file.

Using blahb
=====
Blahb is specifically intended for visualisation purposes, however it may also be useful in other contexts.

### Editing the segmentation
The recommended method for editing blahb is using Seg3D2, which allows many layers to be managed, edited and exported as individual nrrd image files. However you can also import the single label NIfTI files into another segmentation application of your choice.

### Compiling the atlas
Files of the nrrd format can be converted to any other fromat using the [Convert3D command line tool](http://www.itksnap.org/pmwiki/pmwiki.php?n=Convert3D.Convert3D), which is based on the [Insight Segmentation and Registration Toolkit (ITK)](http://www.itk.org/). The basic usage of the Convert3D (c3d) tool is:

    $ c3d input_image.nrrd -o output_image.nii

where the desired output format is indicated by the extension of the output path. There is also a [ruby module](https://gist.github.com/gnatters/5420859) which includes a batch_convert method for automating the conversion of whole directories of images.

Once the images have been converted to either .nii or .nii.gz and placed in a single directory, the [mlv_merge.py](https://gist.github.com/gnatters/5139065) tool can be used to compile a single atlas image. This tool requires Python 2.7+ and relies upon the [NiBabel package](http://nipy.sourceforge.net/nibabel/). The tool takes a directory of single (or multi-) label NIfTI files and combines them into a single multilabel image, in which all the original labels are represented, and any overlaps between different labels are also represented as new labels. This image is then written as a single NIfTI file (called *merged_image.nii.gz* by default). It also produces a *labels.txt* file which contains a key, pairing each label value in the multilabel image with its name (derived from the name of the original label file or files). An example compiled atlas is available via the [**Getting blahb section**](#getting-blahb)

For simply viewing NIfTI files, [Mango](http://ric.uthscsa.edu/mango/) or [ImageJ](http://rsb.info.nih.gov/ij/).

Contributing to blahb
=====
Blahb is a work in progress and is far from finished. Your contributions are welcome, particularly in the form of

* suggestions for labels to add to or parts of labels to cleanup or correct via the [GitHub issues tracker](https://github.com/gnatters/blahb/issues) or via email,
* label images for new or improved segmentations (preferably based on suggestions already submitted to the issue tracker),
* or if you're GitHub savvy, a pull request based on a fork from **the most recent version** of the master branch.

Please try to keep and contributions in the from of segmentation concise (edit few labels) and include a clear description of what you have done. This will make your work a lot easier to integrate.

Suggestions for larger contributions, collaborations or other ways to contribute are welcome via email.

Credits
=====
balhb was is the creation of Nat Noordanus (project maintainer).
Significant assistance with segmentation was given by Panos Dimitriou and [Lewis Hou](https://github.com/lewishou) with help from an award from the [PPLS](http://www.ppls.ed.ac.uk/) Teaching and Learning Initiative fund from The University of Edinburgh.

License
=====
[<img alt="Creative Commons Lience" style="float:left; padding:3px;" src="http://i.creativecommons.org/l/by-sa/3.0/88x31.png" />](http://creativecommons.org/licenses/by-sa/3.0/deed.en)
The Better Looking Atlas of the Human Brain (Blahb) by Nat Noordanus [et al](#credits). is licensed under a [Creative Commons Attribution-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/deed.en).

Citing blahb
=====
If you wish to cite blahb you may use the following APA format:
Noordanus, N. W., Dimitriou, P., Lewis, H. (2013). BLAHB: the Better Looking Atlas of the Human Brain (Version 0.1) [Digital Brain Atlas]. Available from https://github.com/gnatters/blahb
