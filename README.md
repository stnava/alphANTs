# alphANTs

beginner example

we assume you have defined ANTSPATH in your environment and can see something like:

```
/home/me/ants/bin/antsRegistrationSyNQuick.sh
```

when you type:

```
which antsRegistrationSyNQuick.sh
```

on command line.

then run (within the directory called alphANTs):

```
#  rigid registration
antsRegistrationSyNQuick.sh -d 2 -f data/r16slice.jpg -m data/r64slice.jpg -t r -o ./output/rigid
```


```
#  affine registration
antsRegistrationSyNQuick.sh -d 2 -f data/r16slice.jpg -m data/r64slice.jpg -t a -o ./output/affine
```


```
#  syn registration
antsRegistrationSyNQuick.sh -d 2 -f data/r16slice.jpg -m data/r64slice.jpg -t s -o ./output/syn
```

and compare the results.

you should then try to recreate all these example outputs yourself via direct
calls to the programs

```
antsRegistration
```

and

```
antsApplyTransforms
```

and compare different parameters, thinking about how they impact the output.

these examples extend very easily to 3D by changing  ` -d 2 ` to ` -d 3 ` but we
recommend starting your experiments in two dimensions in order to familiarize
yourself with how the algorithms perform.

for higher quality (though more computationally demanding) results,
one may switch from `antsRegistrationSyNQuick.sh` to `antsRegistrationSyN.sh`.

we encourage the user to rerun the experiments with their own data and with
both scripts.

finally, note that `ANTsR` is another level of access to these same programs and
allows one to employ R-based statistics.  We also supply Atropos for a variety
of segmentation tasks, random forest based segmentation via `mrvnrf` and Linda
and many other tools that enable one to build custom pipelines for imaging data.


Brief notes:

for help for any program, type:

```
programName -h
```

or

```
programName --help
```

Example of other programs:

```
CreateJacobianDeterminantImage 2 output/syn1Warp.nii.gz output/jac.nii.gz 1 0
ThresholdImage 2 data/r16slice.jpg output/mask.nii.gz 20 Inf
N3BiasFieldCorrection 2 data/r16slice.jpg output/r16n3.nii.gz
Atropos -d 2 -a output/r16n3.nii.gz -x output/mask.nii.gz -i kmeans[3] -c [10,0] -m [0.1,1x1] -o \
  [output/seg.nii.gz,output/seg_prob%02d.nii.gz] -v 1
ThresholdImage 2 output/seg.nii.gz output/csf.nii.gz 1 1
ImageMath 2 output/csflarge.nii.gz  GetLargestComponent output/csf.nii.gz
ImageMath 2 output/csfdil.nii.gz  MD output/csf.nii.gz 1 # dilation
ImageMath 2 output/csffill.nii.gz  FillHoles output/csfdil.nii.gz
LabelClustersUniquely 2 output/csf.nii.gz  output/csflab.nii.gz 2
```

Many more possibilities exist. See additional documentation, especially in
[ANTsR](http://stnava.github.io/ANTsR/) and in the [FAQ page](https://github.com/stnava/ANTsTutorial/blob/master/handout/antsGithubExamples.Rmd).
