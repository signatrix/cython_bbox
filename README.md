# cython_bbox

cython_bbox is widely used in object detection tasks. To my best knowledge, it was first implemented in [Faster-RCNN](https://github.com/rbgirshick/py-faster-rcnn). Since then, almost all object detection projects use the source code directly.

In order to use it in standalone code snippets or small projects, I make it a pypi module. The `cython_bbox.pyx` is totally borrowed from [Faster-RCNN](https://github.com/rbgirshick/py-faster-rcnn). Thanks [RBG](http://www.rossgirshick.info/)!

## build and publish

Install `cibuildwheel` to build wheels for different platforms and architectures:

```
pip install cibuildwheel
```

Example to create wheels for linux platforms in amd64 i386 and aarch64 architectures:

```
export CIBW_ARCHS_LINUX="auto aarch64"
export CIBW_BUILD="cp37-manylinux* cp38-manylinux* cp39-manylinux*"
cibuildwheel
```

Look for documentation to do it for other platforms as well.

Then install twine:

```
pip install twine
```

And publish the wheels:

```
TWINE_USERNAME=*** TWINE_PASSWORD=*** TWINE_REPOSITORY_URL=https://pypi.cartwatch.de/ twine upload wheelhouse/*
```

## install

```
pip install cython_bbox
```

## usage


```
from cython_bbox import bbox_overlaps
overlaps = bbox_overlaps(
        np.ascontiguousarray(dt, dtype=np.float32),
        np.ascontiguousarray(gt, dtype=np.float32)
    )

```
