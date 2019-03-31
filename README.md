<p align="center">
<br>
<a href="https://travis-ci.org/cdsgroup/resp"><img src="https://travis-ci.org/cdsgroup/resp.svg?branch=master"></a>
<a href="https://codecov.io/gh/cdsgroup/resp"> <img src="https://codecov.io/gh/cdsgroup/resp/branch/master/graph/badge.svg" /></a>
<a href="https://opensource.org/licenses/BSD-3-Clause"><img src="https://img.shields.io/badge/License-BSD%203--Clause-blue.svg" /></a>
<br>
<a href="#"> <img src="https://img.shields.io/github/release/cdsgroup/resp.svg" /></a>
<a href="#"> <img src="https://img.shields.io/github/commits-since/cdsgroup/resp/latest.svg" /></a>
<a href="#"> <img src="https://img.shields.io/github/release-date/cdsgroup/resp.svg" /></a>
<a href="#"> <img src="https://img.shields.io/github/commit-activity/y/cdsgroup/resp.svg" /></a>
<br>
</p>

Restrained Electrostatic Potential
==================================

## Installation
This RESP code is a plug-in to the Psi4 quantum chemistry package.
To install Psi4, go to the this website: https://admiring-tesla-08529a.netlify.com/installs/v13/ and
choose your preferred option (conda package recommended). If the RESP program was not installed by
default, execute `conda install resp -c psi4`. To test that the RESP plug-in works,
execute `python -c "import resp, sys; sys.exit(resp.test('long'))"`.
Two examples on how to use the plug-in are available in the file `resp/tests/test_resp.py`.

## Code
The following codes are available:
- `resp/espfit.py`: The restrained electrostatic potential (RESP) fitting procedure.
- `resp/driver.py`: Driver of the code.
- `resp/tests/test_resp.py` contains:
   - `test_resp_1`: Example for two-stage charge fitting for one conformer.
   - `test_resp_2`: Example for two-stage charge fitting for two conformers.

Helper programs:
- `resp/vdw_surface_helper.py`
- `resp/stage2_helper.py`

## RESP Method Summary
RESP charges result from fitting the classical electrostatic potential (ESP)
generated by atom-centered point charges to the quantum ESP computed outside
the van der Waals surface of the molecule. The fitted charges are restrained
by a hyperbolic term, which requires an iterative fitting procedure to compute
the charges.

The charges (**q**) are computed by solving the following equation:

**A** **q** = **B**.

The left-hand side contains the information about the classical ESP while the
right-hand side contains information about the quantum ESP.
A hyperbolic restraint term that depends on the charges is added to the diagonal
elements of matrix **A**. The charges and the diagonal elements of **A** are
changed iteratively until the charges converge.

## References:
- [[Bayly:93:10269-10280](https://pubs.acs.org/doi/abs/10.1021/j100142a004)] C. I. Bayly *et. al.* *J. Phys. Chem.* **97**, 10269 (1993)
