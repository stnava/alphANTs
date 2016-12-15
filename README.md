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
