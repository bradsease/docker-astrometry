# docker-astrometry
Docker container for Astrometry.net.


## Usage

The docker container is directly executable and passes all command-line arguments directly to `solve-field`.
```
$ docker run bsease/astrometry:latest
```
To process images, you'll need to map in catalog files and a directory containing the target image
```
$ docker run -v /path/to/catalogs:/data \
             -v /path/to/work/dir:/work \
             bsease/astrometry:latest target_image.fits
```
The default configuration file is in /etc/astrometry.cfg. You can override it using docker:
```
$ docker run -v /path/to/catalogs:/data \
             -v /path/to/work/dir:/work \
             -v /path/to/atrometry.cfg:/etc/astrometry.cfg \
             bsease/astrometry:latest target_image.fits
```
or by using the `solve-field` command-line arguments.
```
$ docker run -v /path/to/catalogs:/data \
             -v /path/to/work/dir:/work \
             -v /path/to/atrometry.cf:/etc/astrometry.cfg \
             bsease/astrometry:latest target_image.fits \
             --config /work/astrometry.cfg
```
