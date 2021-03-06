.. QuTiP 
   Copyright (C) 2011-2013, Paul D. Nation & Robert J. Johansson

.. _overview:

******************
Guide Overview
******************

The goal of this guide is to introduce you to the basic structures and functions that make up QuTiP. If you are familiar with the Quantum Optics Toolbox, then you should have no problem getting used to QuTiP. This guide is broken up into several sections, each highlighting a specific set of functionalities. In combination with the examples, this guide should provide a more or less complete overview.  In addition, :ref:`apidoc` for each function is located at the end of this guide.


.. _overview-org:

Organization
=============

QuTiP is designed to be a general toolbox for solving quantum optics like problems such as systems composed of two-level and harmonic oscillator components.  To this end, the QuTiP framework is built from a large (and ever growing) library of functions; from :func:`qutip.states.basis` to :func:`qutip.wigner`.  The general organization of QuTiP, highlighting the important functions available to the user, is shown in the :ref:`figure-qutip_org`


.. _figure-qutip_org:

.. figure:: qutip_org.png
   :align: center
   :figwidth: 100%
   
   QuTiP tree-diagram of user accessible functions and classes.
