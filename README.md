# GCMMA-MMA-Python

This repository contains the Python code of the Method of Moving Asymptotes ([Svanberg, 1987](https://onlinelibrary.wiley.com/doi/abs/10.1002/nme.1620240207)), originally developed and written in MATLAB by Krister Svanberg. The original MATLAB code was taken from http://www.smoptit.se/ under the GNU General Public License. 

If you opt to use this code, Krister Svanberg would appreciate it if you could send him an email sharing your application and intentions (the email address can be found on his website). When work is published, the authors must cite Krister Svanberg's academic work. The references can be found below. 

An example application of the code in topology optimization can be found [here](https://github.com/arjendeetman/TopOpt-MMA-Python).

## Installation and usage

The `mmapy` package is available on [PyPi](https://pypi.org/project/mmapy/). To install it, use the following command:

```bash
pip install mmapy
```

After installation, you can import the package in your Python script with:

```python
import mmapy
```

### Using `mmapy.mma`

The optimization routines live in `mmapy.mma` and are imported as:

```python
from mmapy import mmasub, gcmmasub
```

Both functions solve a subproblem of the Method of Moving Asymptotes. `mmasub`
implements the classic MMA algorithm, while `gcmmasub` provides the generalized
convex variant.

#### Argument shapes

Inputs are typically column vectors of shape `(n, 1)` for design variables and
`(m, 1)` for constraints. Jacobians are `(m, n)` matrices. In particular:

- `xval`, `xmin`, `xmax`, `xold1`, `xold2`, `low`, `upp` &mdash; arrays of
  shape `(n, 1)`.
- `f0val` is a scalar and `df0dx` has shape `(n, 1)`.
- `fval` has shape `(m, 1)` and `dfdx` has shape `(m, n)`.
- `a0` is a scalar and `a`, `c`, `d` are arrays of shape `(m, 1)`.

Optional parameters such as `move`, `asyinit`, `asydecr`, and `asyincr` control
the asymptote update strategy. The return values of `mmasub` are the updated
variables `(xmma, ymma, zmma, lam, xsi, eta, mu, zet, s, low, upp)` where each
array matches the shape of its corresponding input.

`gcmmasub` uses a similar signature with additional arguments `epsimin`, `raa0`
and `raa`, and also returns the approximated function values `f0app` and `fapp`.

Complete iterative examples are available in the `examples` directory.

## Cite

This repository is linked to Zenodo. To ensure accurate citation of this project and facilitate traceability in case of bugs or issues, please refer to the specific version used, including the DOI from Zenodo. You can find the corresponding DOI on the [Zenodo page](https://zenodo.org/doi/10.5281/zenodo.13197565). Additionally, cite the original work by Krister Svanberg. The relevant references are provided below.

## References

- Svanberg, K. (1987). The Method of Moving Asymptotes – A new method for structural optimization. International Journal 
for Numerical Methods in Engineering 24, 359-373. [doi:10.1002/nme.1620240207](https://onlinelibrary.wiley.com/doi/abs/10.1002/nme.1620240207)
 - Svanberg, K. (n.d.). MMA and GCMMA – two methods for nonlinear optimization. Retrieved August 3, 2017 from  
https://people.kth.se/~krille/mmagcmma.pdf 

## License
Original work written in MATLAB: Copyright (c) 2006-2009 Krister Svanberg\
Derived Python implementation: Copyright (c) 2020-2025 Arjen Deetman

GCMMA-MMA-Python is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License (file LICENSE) along with this file.  If not, see <http://www.gnu.org/licenses/>.
