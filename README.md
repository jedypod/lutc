# LUTc
A minimal python tool for creating LUTs from images.

`lutc` can be used to generate an identity image for a 1D or 3D LUT. This image can be run through arbitrary image processing. A LUT can then be generated from the processed image.

# Examples
```
# Generate an identity image for a 1D LUT covering -0.1 to 1.2, with 4096 steps
$ lutc -s=-0.1,1.2,4096
> Generating 1D Identity LUT Image: identity_-0.1_1.2_4096.tif

# Generate an spi1d LUT from a processed image
$ lutc -s=-0.1,1.2,4096 -i identity_-0.1_1.2_4096.logc.tif
> Generating 1D LUT: identity_-0.1_1.2_4096.logc.spi1d

# Generate an identity image for a 65x65x65 cube LUT
$ lutc -c -s 65
> Generating 3D Identity LUT Image: identity_cube65.tif

# Generate a cube LUT from a processed identity image
$ lutc -c -s 65 -i identity_cube65_aces.tif
> Generating 3D LUT: identity_cube65_aces.cube
```

# Install
`lutc` requires [numpy](https://numpy.org) and [imageio](https://imageio.readthedocs.io/en/stable/), both of which can be installed using pip.

```
pip install numpy
pip install imageio
```

# Usage


```
usage: lutc [-h] [-s SHAPE] [-f FORMAT] [-c] [-i IMAGE] [-o OUTDIR]

LUTCreate: a minimal tool to genereate a 1d or 3d lut from an image.

optional arguments:
  -h, --help            show this help message and exit
  -s SHAPE, --shape SHAPE
                        Shape of the lut. Comma separated float or int values to specify min,max,size. use "-s=-0.1,1,1024" if negatives. If not specified the defaults will be used.                                                                         
  -f FORMAT, --format FORMAT
                        The LUT format to output. Supported formats: "spi", "cube", "cub"
  -c, --cube            Create a cube LUT instead of a 1D LUT.
  -i IMAGE, --image IMAGE
                        Source image to process into a LUT.
  -o OUTDIR, --outdir OUTDIR
                        Output directory for identity images, or lut files [default: current directory]
```