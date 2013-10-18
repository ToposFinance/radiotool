.. radiotool documentation master file, created by
   sphinx-quickstart on Tue Apr  9 14:36:50 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

radiotool - tools for constructing audio
========================================

Radiotool is a python library that aims to make it easy to create
audio by piecing together bits of other audio files. This library was
originally written to enable my research in audio editing user
interfaces, but perhaps someone else might find it useful.

To perform the actual audio rendering, radiotool relies on
scikits.audiolab_, a python wrapper for libsndfile_.

.. _scikits.audiolab: https://pypi.python.org/pypi/scikits.audiolab/
.. _libsndfile: http://www.mega-nerd.com/libsndfile/

For now, ``radiotool`` consists of the ``composer`` module, but it
will likely grow in the future to cover other use cases.

Contents:

.. toctree::
   :maxdepth: 2

   composer/composition
   composer/tracks
   composer/segments
   composer/dynamics
   algorithms/retarget
   algorithms/novelty
   utils

.. currentmodule:: radiotool

Simple example
--------------

::

    from radiotool.composer import *
    comp = Composition()
    
    # create a track with a pre-existing wav file
    track = Track("test.wav")

    # create a segment of a track that:
    # 1. starts at the 0.0 mark of the composition
    # 2. begins playing at the 0.5 second mark of the track
    # 3. plays for 1.0 seconds
    segment = Segment(track, 0.0, 0.5, 1.0)

    # add segment to the composition
    comp.add_segment(segment)

    # output your composition as a numpy array
    arr_out = comp.build()

    # or export your composition as an audio file, composition.wav
    comp.export(filename="composition")

See the documentation for more detailed examples (coming soon!).

Composition
-----------

.. autosummary:: 
    radiotool.composer.Composition

Tracks
------

.. autosummary::
    radiotool.composer.Track
    radiotool.composer.Speech
    radiotool.composer.Song
    radiotool.composer.RawTrack

Segments
--------

.. autosummary::
    radiotool.composer.Segment
    radiotool.composer.TimeStretchSegment

Dynamics
--------

.. autosummary::
  radiotool.composer.Dynamic
  radiotool.composer.Volume
  radiotool.composer.Fade
  radiotool.composer.RawVolume

Algorithms
----------

.. autosummary::
  radiotool.algorithms.retarget
  radiotool.algorithms.novelty
  radiotool.algorithms.librosa_analysis

Utilities
---------

.. autosummary::
    radiotool.utils


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
