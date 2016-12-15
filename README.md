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
