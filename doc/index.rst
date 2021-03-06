============================
Pandas-plink's documentation
============================

:Date: |today|
:Version: |version|

Read PLINK files into Pandas data frames with support of mapping multiple BED
files at once.

*******
Install
*******

The recommended way of installing it is via `conda`_::

  conda install -c conda-forge pandas-plink

An alternative way would be via pip::

  pip install pandas-plink

.. _conda: http://conda.pydata.org/docs/index.html

*****
Usage
*****

It is as simple as::

  from pandas_plink import read_plink
  (bim, fam, G) = read_plink('/path/to/data')

assuming that you have the files

  - `/path/to/data.bim`
  - `/path/to/data.fam`
  - `/path/to/data.bed`

The returned matrix ``G`` contains ``0``, ``1``, ``2``, or ``NaN``:

- ``0`` Homozygous for first allele in .bim file
- ``1`` Heterozygous
- ``2`` Homozygous for second allele in .bim file
- ``NaN`` Missing genotype

The matrix ``G`` is a `Dask`_ array instead of an usual `NumPy`_ array.
It allows for lazy-loading large datasets that would not be able to fit
in memory.

.. _Dask: https://dask.pydata.org/
.. _NumPy: http://www.numpy.org

*********
Functions
*********

.. automodule:: pandas_plink

  .. autofunction:: read_plink
  .. autofunction:: test
  .. autofunction:: example_file_prefix
