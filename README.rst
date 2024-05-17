.. image:: https://img.shields.io/badge/tstn--045-lsst.io-brightgreen.svg
   :target: https://tstn-045.lsst.io
.. image:: https://github.com/lsst/tstn-045/workflows/CI/badge.svg
   :target: https://github.com/lsst/tstn-045/actions/

#################################################################################################
Replacing DDS with Apache Kafka as middleware technology for the Rubin Observatory Control System
#################################################################################################

TSTN-045
========

Once in operation, the Vera C. Rubin Observatory will execute a 10-year-long survey of the Southern sky known as the Legacy Survey of Space and Time (LSST).
The Rubin Observatory Control System (Rubin-OCS) is a distributed system with each component in charge of a particular sub-system e.g.; the mount, the m1m3 mirror support system, etc.
Each component is designed as an independent part of the system and they must work together during operations.
Communication between the components is done by means of a software middleware.

The software middleware is the backbone of the system, allowing components to communicate with each other in a seamless way.
The highly distributed nature of the Rubin-OCS places tight constraints in terms of latency, availability, and reliability for the middleware.
The baseline implementation of the Rubin-OCS adopts the Data Distribution Service (DDS) technology for the middleware.

In the Rubin-OCS, the middleware is encapsulated with a layer of abstraction known as the Service Abstraction Layer (SAL), which currently uses the ADLink-OpenSpliceDDS implementation of the Data Distribution Service (DDS) message passing system.

Recently we performed a study of using Apache Kafka to replace DDS as the middleware technology for the Rubin-OCS.
This study was motivated by the middleware-related challenges we faced while integrating the system as well as the recent announcements indicating that the adopted library may be deprecated during the lifespan of the project.
The study involved throughput and latency studies and a proof of concept of our core libraries.
Overall Kafka proved to be a suitable replacement for DDS.

Links
=====

- Live drafts: https://tstn-045.lsst.io
- GitHub: https://github.com/lsst/tstn-045

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst/tstn-045

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the `acronyms.tex` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
