# Files

## `seedname.win`

INPUT. The master input file; contains the specification of the system
and any parameters for the run. For a description of input parameters,
see Chapter [Parameters](../parameters); for examples, see
Section [`seedname.win`](#seedname.win) and
the `wannier90` Tutorial.

### Units

The following are the dimensional quantities that are specified in the
master input file:

-   Direct lattice vectors

-   Positions (of atomic or projection) centres in real space

-   Energy windows

-   Positions of k-points in reciprocal space

-   Convergence thresholds for the minimisation of $\Omega$

-   `zona` (see Section [Projections](../projections))

-   `wannier_plot_cube`: cut-off radius for plotting WF in Gaussian cube
    format

Notes:

-   The units (either `ang` (default) or `bohr`) in which the lattice
    vectors, atomic positions or projection centres are given can be set
    in the first line of the blocks `unit_cell_cart`, `atoms_cart` and
    `projections`, respectively, in `seedname.win`.

-   Energy is always in eV.

-   Convergence thresholds are always in Å$^{2}$

-   Positions of k-points are always in crystallographic coordinates
    relative to the reciprocal lattice vectors.

-   `zona` is always in reciprocal Angstrom (Å$^{-1}$)

-   The keyword `length_unit` may be set to `ang` (default) or `bohr`,
    in order to set the units in which the quantities in the output file
    `seedname.wout` are written.

-   `wannier_plot_radius` is in Angstrom

The reciprocal lattice vectors
$\{\mathbf{B}_{1},\mathbf{B}_{2},\mathbf{B}_{3}\}$ are defined in terms
of the direct lattice vectors
$\{\mathbf{A}_{1},\mathbf{A}_{2},\mathbf{A}_{3}\}$ by the equation

$$
\mathbf{B}_{1} = \frac{2\pi}{\Omega}\mathbf{A}_{2}\times\mathbf{A}_{3}
\ \ \ \mathrm{etc.},
$$

where the cell volume is
$V=\mathbf{A}_{1}\cdot(\mathbf{A}_{2}\times\mathbf{A}_{3})$.

## `seedname.mmn`

INPUT. Written by the underlying electronic structure code. See
Chapter [Post-processing](../postproc)
for details.

## `seedname.amn`

INPUT. Written by the underlying electronic structure code. See
Chapter [Post-processing](../postproc)
for details.

## `seedname.dmn`

INPUT. Read if `site_symmetry = .true.` (symmetry-adapted mode). Written
by the underlying electronic structure code. See
Chapter [Post-processing](../postproc)
for details.

## `seedname.eig`

INPUT. Written by the underlying electronic structure code. See
Chapter [Post-processing](../postproc)
for details.

## `seedname.nnkp` {#sec:old-nnkp}

OUTPUT. Written by `wannier90` when `postproc_setup=.TRUE.` (or,
alternatively, when `wannier90` is run with the `-pp` command-line
option). See Chapter [Post-processing](../postproc) for details.

## `seedname.wout`

OUTPUT. The master output file. Here we give a description of the main
features of the output. The verbosity of the output is controlled by the
input parameter `iprint`. The higher the value, the more detail is given
in the output file. The default value is 1, which prints minimal
information.

### Header

The header provides some basic information about `wannier90`, the
authors, the code version and release, and the execution time of the
current run. The header looks like the following different (the string
might slightly change across different versions):


                 +---------------------------------------------------+
                 |                                                   |
                 |                   WANNIER90                       |
                 |                                                   |
                 +---------------------------------------------------+
                 |                                                   |
                 |        Welcome to the Maximally-Localized         |
                 |        Generalized Wannier Functions code         |
                 |            http://www.wannier.org                 |
                 |                                                   |
                 |  Wannier90 Developer Group:                       |
                 |    Giovanni Pizzi    (EPFL)                       |
                 |    Valerio Vitale    (Cambridge)                  |
                 |    David Vanderbilt  (Rutgers University)         |
                 |    Nicola Marzari    (EPFL)                       |
                 |    Ivo Souza         (Universidad del Pais Vasco) |
                 |    Arash A. Mostofi  (Imperial College London)    |
                 |    Jonathan R. Yates (University of Oxford)       |
                 |                                                   |
                 |  For the full list of Wannier90 3.x authors,      |
                 |  please check the code documentation and the      |
                 |  README on the GitHub page of the code            |
                 |                                                   |
                 |                                                   |
                 |  Please cite                                      |
                                           .
                                           .
                 |                                                   |
                 +---------------------------------------------------+
                 |    Execution started on 18Dec2018 at 18:39:42     |
                 +---------------------------------------------------+

### System information

This part of the output file presents information that `wannier90` has
read or inferred from the master input file `seedname.win`. This
includes real and reciprocal lattice vectors, atomic positions,
k-points, parameters for job control, disentanglement, localisation and
plotting.

                                        ------
                                        SYSTEM
                                        ------
     
                                  Lattice Vectors (Ang)
                        a_1     3.938486   0.000000   0.000000
                        a_2     0.000000   3.938486   0.000000
                        a_3     0.000000   0.000000   3.938486
     
                       Unit Cell Volume:      61.09251  (Ang^3)
     
                            Reciprocal-Space Vectors (Ang^-1)
                        b_1     1.595330   0.000000   0.000000
                        b_2     0.000000   1.595330   0.000000
                        b_3     0.000000   0.000000   1.595330
      
     *----------------------------------------------------------------------------*
     |   Site       Fractional Coordinate          Cartesian Coordinate (Ang)     |
     +----------------------------------------------------------------------------+
     | Ba   1   0.00000   0.00000   0.00000   |    0.00000   0.00000   0.00000    |
     | Ti   1   0.50000   0.50000   0.50000   |    1.96924   1.96924   1.96924    |
                                              .
                                              . 
     *----------------------------------------------------------------------------*
      
                                    ------------
                                    K-POINT GRID
                                    ------------
      
                 Grid size =  4 x  4 x  4      Total points =   64
      
     *---------------------------------- MAIN ------------------------------------*
     |  Number of Wannier Functions               :                 9             |
     |  Number of input Bloch states              :                 9             |
     |  Output verbosity (1=low, 5=high)          :                 1             |
     |  Length Unit                               :               Ang             |
     |  Post-processing setup (write *.nnkp)      :                 F             |
                                                  .
                                                  .
     *----------------------------------------------------------------------------*

### Nearest-neighbour k-points

This part of the output files provides information on the
$\mathrm{b}$-vectors and weights chosen to satisfy the condition of
Eq. [B1](../parameters/mjx-eqn:eq:B1).

     *---------------------------------- K-MESH ----------------------------------*
     +----------------------------------------------------------------------------+
     |                    Distance to Nearest-Neighbour Shells                    |
     |                    ------------------------------------                    |
     |          Shell             Distance (Ang^-1)          Multiplicity         |
     |          -----             -----------------          ------------         |
     |             1                   0.398833                      6            |
     |             2                   0.564034                     12            |
                                           .
                                           .
     +----------------------------------------------------------------------------+
     | The b-vectors are chosen automatically                                     |
     | The following shells are used:   1                                         |
     +----------------------------------------------------------------------------+
     |                        Shell   # Nearest-Neighbours                        |
     |                        -----   --------------------                        |
     |                          1               6                                 |
     +----------------------------------------------------------------------------+
     | Completeness relation is fully satisfied [Eq. (B1), PRB 56, 12847 (1997)]  |
     +----------------------------------------------------------------------------+

### Disentanglement

Then (if required) comes the part where $\Omega_{\mathrm{I}}$ is
minimised to disentangle the optimally-connected subspace of states for
the localisation procedure in the next step.

First, a summary of the energy windows that are being used is given:

     *------------------------------- DISENTANGLE --------------------------------*
     +----------------------------------------------------------------------------+
     |                              Energy  Windows                               |
     |                              ---------------                               |
     |                   Outer:    2.81739  to   38.00000  (eV)                   |
     |                   Inner:    2.81739  to   13.00000  (eV)                   |
     +----------------------------------------------------------------------------+

Then, each step of the iterative minimisation of $\Omega_{\mathrm{I}}$
is reported.

                       Extraction of optimally-connected subspace                  
                       ------------------------------------------                  
     +---------------------------------------------------------------------+<-- DIS
     |  Iter     Omega_I(i-1)      Omega_I(i)      Delta (frac.)    Time   |<-- DIS
     +---------------------------------------------------------------------+<-- DIS
           1       3.82493590       3.66268867       4.430E-02      0.36    <-- DIS
           2       3.66268867       3.66268867       6.911E-15      0.37    <-- DIS
                                           .
                                           .
                                       
                 <<<      Delta < 1.000E-10  over  3 iterations     >>>
                 <<< Disentanglement convergence criteria satisfied >>>

            Final Omega_I     3.66268867 (Ang^2)

     +----------------------------------------------------------------------------+

The first column gives the iteration number. For a description of the
minimisation procedure and expressions for $\Omega_{\mathrm{I}}^{(i)}$,
see the original paper [@souza-prb01]. The procedure is considered to be
converged when the fractional difference between
$\Omega_{\mathrm{I}}^{(i)}$ and $\Omega_{\mathrm{I}}^{(i-1)}$ is less
than `dis_conv_tol` over ` dis_conv_window` iterations. The final column
gives a running account of the wall time (in seconds) so far. Note that
at the end of each line of output, there are the characters "`<– DIS`".
This enables fast searching of the output using, for example, the Unix
command `grep`:

```bash
grep DIS wannier.wout | less
```

### Wannierisation

The next part of the output file provides information on the
minimisation of $\widetilde{\Omega}$. At each iteration, the centre and
spread of each WF is reported.

    *------------------------------- WANNIERISE ---------------------------------*
     +--------------------------------------------------------------------+<-- CONV
     | Iter  Delta Spread     RMS Gradient      Spread (Ang^2)      Time  |<-- CONV
     +--------------------------------------------------------------------+<-- CONV
     
     ------------------------------------------------------------------------------
     Initial State
      WF centre and spread    1  (  0.000000,  1.969243,  1.969243 )     1.52435832
      WF centre and spread    2  (  0.000000,  1.969243,  1.969243 )     1.16120620
                                          .
                                          .
          0     0.126E+02     0.0000000000       12.6297685260       0.29  <-- CONV
            O_D=      0.0000000 O_OD=      0.1491718 O_TOT=     12.6297685 <-- SPRD
     ------------------------------------------------------------------------------
     Cycle:      1
      WF centre and spread    1  (  0.000000,  1.969243,  1.969243 )     1.52414024
      WF centre and spread    2  (  0.000000,  1.969243,  1.969243 )     1.16059775
                                          .
                                          .
      Sum of centres and spreads ( 11.815458, 11.815458, 11.815458 )    12.62663472
     
          1    -0.313E-02     0.0697660962       12.6266347170       0.34  <-- CONV
            O_D=      0.0000000 O_OD=      0.1460380 O_TOT=     12.6266347 <-- SPRD
     Delta: O_D= -0.4530841E-18 O_OD= -0.3133809E-02 O_TOT= -0.3133809E-02 <-- DLTA
     ------------------------------------------------------------------------------
     Cycle:      2
      WF centre and spread    1  (  0.000000,  1.969243,  1.969243 )     1.52414866
      WF centre and spread    2  (  0.000000,  1.969243,  1.969243 )     1.16052405
                                          .
                                          .
       Sum of centres and spreads ( 11.815458, 11.815458, 11.815458 )    12.62646411
     
          2    -0.171E-03     0.0188848262       12.6264641055       0.38  <-- CONV
            O_D=      0.0000000 O_OD=      0.1458674 O_TOT=     12.6264641 <-- SPRD
     Delta: O_D= -0.2847260E-18 O_OD= -0.1706115E-03 O_TOT= -0.1706115E-03 <-- DLTA
     ------------------------------------------------------------------------------
                                          .
                                          .
     ------------------------------------------------------------------------------
     Final State
      WF centre and spread    1  (  0.000000,  1.969243,  1.969243 )     1.52416618
      WF centre and spread    2  (  0.000000,  1.969243,  1.969243 )     1.16048545
                                          .
                                          .
      Sum of centres and spreads ( 11.815458, 11.815458, 11.815458 )    12.62645344
     
             Spreads (Ang^2)       Omega I      =    12.480596753
            ================       Omega D      =     0.000000000
                                   Omega OD     =     0.145856689
        Final Spread (Ang^2)       Omega Total  =    12.626453441
     ------------------------------------------------------------------------------

It looks quite complicated, but things look more simple if one uses
`grep`:

```bash
grep CONV wannier.wout
```

gives

     +--------------------------------------------------------------------+<-- CONV
     | Iter  Delta Spread     RMS Gradient      Spread (Ang^2)      Time  |<-- CONV
     +--------------------------------------------------------------------+<-- CONV
          0     0.126E+02     0.0000000000       12.6297685260       0.29  <-- CONV
          1    -0.313E-02     0.0697660962       12.6266347170       0.34  <-- CONV
                                                       .
                                                       .
         50     0.000E+00     0.0000000694       12.6264534413       2.14  <-- CONV

The first column is the iteration number, the second is the change in
$\Omega$ from the previous iteration, the third is the root-mean-squared
gradient of $\Omega$ with respect to variations in the unitary matrices
$\mathbf{U}^{(\mathbf{k})}$, and the last is the time taken (in
seconds). Depending on the input parameters used, the procedure either
runs for `num_iter` iterations, or a convergence criterion is applied on
$\Omega$. See Section [2.8](#sec:wann_params){reference-type="ref"
reference="sec:wann_params"} for details.

Similarly, the command

```bash
grep SPRD wannier.wout
```

gives

            O_D=      0.0000000 O_OD=      0.1491718 O_TOT=     12.6297685 <-- SPRD
            O_D=      0.0000000 O_OD=      0.1460380 O_TOT=     12.6266347 <-- SPRD
                                                .
                                                .
            O_D=      0.0000000 O_OD=      0.1458567 O_TOT=     12.6264534 <-- SPRD         

which, for each iteration, reports the value of the diagonal and
off-diagonal parts of the non-gauge-invariant spread, as well as the
total spread, respectively. Recall from
Section [Methodology](../methodology)
that
$\Omega = \Omega_{\mathrm{I}}+ \Omega_{\mathrm{D}} + \Omega_{\mathrm{OD}}$.

#### Wannierisation with selective localization and constrained centres

For full details of the selectively localised Wannier function (SLWF)
method, the reader is referred to Ref. [@Marianetti]. When using the
SLWF method, only a few things change in the output file and in general
the same principles described above will apply. In particular, when
minimising the spread with respect to the degrees of freedom of only a
subset of functions, it is not possible to cast the total spread
functional $\Omega$ as a sum of a gauge-invariant part and a
gauge-dependent part. Instead, one has
$\Omega^{'} = \Omega_{\mathrm{IOD}} + \Omega_{\mathrm{D}}$, where

$$
\Omega^{'} = \sum_{n=1}^{J'<J} \left[\langle r^2 \rangle_n - \overline{\mathbf{r}}_{n}^{2}\right]
$$

and

$$
\Omega_{\mathrm{IOD}} = \sum_{n=1}^{J'<J} \left[\langle r^2_n \rangle- \sum_{\mathbf{R}} \vert\langle\mathbf{R}n\vert \mathbf{r} \vert n\mathbf{R}\rangle\vert^2 \right].
$$

The total number of Wannier functions is $J$, whereas $J'$ is the number
functions to be selectively localized (so-called *objective WFs*). The
information on the number of functions which are going to be selectively
localized (`Number of Objective Wannier Functions`) is given in the
`MAIN` section of the output file:

     *---------------------------------- MAIN ------------------------------------*
     |  Number of Wannier Functions               :                 4             |
     |  Number of Objective Wannier Functions     :                 1             |
     |  Number of input Bloch states              :                 4             |

Whether or not the selective localization procedure has been switched on
is reported in the `WANNIERISE` section as

     |  Perform selective localization            :                 T             |

The next part of the output file provides information on the
minimisation of the modified spread functional:

     *------------------------------- WANNIERISE ---------------------------------*
     +--------------------------------------------------------------------+<-- CONV
     | Iter  Delta Spread     RMS Gradient      Spread (Ang^2)      Time  |<-- CONV
     +--------------------------------------------------------------------+<-- CONV

     ------------------------------------------------------------------------------
     Initial State
      WF centre and spread    1  ( -0.857524,  0.857524,  0.857524 )     1.80463310
      WF centre and spread    2  (  0.857524, -0.857524,  0.857524 )     1.80463311
      WF centre and spread    3  (  0.857524,  0.857524, -0.857524 )     1.80463311
      WF centre and spread    4  ( -0.857524, -0.857524, -0.857524 )     1.80463311
      Sum of centres and spreads ( -0.000000, -0.000000,  0.000000 )     7.21853243

          0    -0.317E+01     0.0000000000       -3.1653368719       0.00  <-- CONV
           O_D=      0.0000000 O_IOD=     -3.1653369 O_TOT=     -3.1653369 <-- SPRD
     ------------------------------------------------------------------------------
     Cycle:      1
      WF centre and spread    1  ( -0.853260,  0.853260,  0.853260 )     1.70201498
      WF centre and spread    2  (  0.857352, -0.857352,  0.862454 )     1.84658331
      WF centre and spread    3  (  0.857352,  0.862454, -0.857352 )     1.84658331
      WF centre and spread    4  ( -0.862454, -0.857352, -0.857352 )     1.84658331
      Sum of centres and spreads ( -0.001010,  0.001010,  0.001010 )     7.24176492

          1    -0.884E-01     0.2093698260       -3.2536918930       0.00  <-- CONV
           O_IOD=     -3.2536919 O_D=      0.0000000 O_TOT=     -3.2536919 <-- SPRD
    Delta: O_IOD= -0.1245020E+00 O_D=  0.0000000E+00 O_TOT= -0.8835502E-01 <-- DLTA
     ------------------------------------------------------------------------------
                                          .
                                          .
     ------------------------------------------------------------------------------
     Final State
      WF centre and spread    1  ( -0.890189,  0.890189,  0.890189 )     1.42375495
      WF centre and spread    2  (  0.895973, -0.895973,  0.917426 )     2.14313664
      WF centre and spread    3  (  0.895973,  0.917426, -0.895973 )     2.14313664
      WF centre and spread    4  ( -0.917426, -0.895973, -0.895973 )     2.14313664
      Sum of centres and spreads ( -0.015669,  0.015669,  0.015669 )     7.85316486
     
             Spreads (Ang^2)       Omega IOD    =     1.423371553
            ================       Omega D      =     0.000383395
                                   Omega Rest   =     9.276919811
        Final Spread (Ang^2)       Omega Total  =     1.423754947
     ------------------------------------------------------------------------------

When comparing the output from an SLWF calculation with a standard
wannierisation (see
Sec. [Wannierisation](#wannierisation)), the only differences are in the
definition of the spread functional. Hence, during the minimization
`O_OD` is replaced by `O_IOD` and `O_TOT` now reflects the fact that the
new total spread functional is $\Omega^{'}$. The part on the final state
has one more item of information: the value of the difference between
the global spread functional and the new spread functional given by
`Omega Rest`

$$
\Omega_{R} = \sum_{n=1}^{J-J'} \left[\langle r^2 \rangle_n - \overline{\mathbf{r}}_{n}^{2} \right]
$$

If adding centre-constraints to the SLWFs, you will find the information
about the centres of the original projections and the desired centres in
the `SYSTEM` section

     *----------------------------------------------------------------------------*
     | Wannier#        Original Centres              Constrained centres          |
     +----------------------------------------------------------------------------+
     |    1     0.25000   0.25000   0.25000   |    0.00000   0.00000   0.00000    |
     *----------------------------------------------------------------------------*

As before one can check that the selective localization with constraints
is being used by looking at the `WANNIERISE` section:

     |  Perform selective localization            :                 T             |
     |  Use constrains in selective localization  :                 T             |
     |  Value of the Lagrange multiplier          :         0.100E+01             |
     *----------------------------------------------------------------------------*

which also gives the selected value for the Lagrange multiplier. The
output file for the minimisation section is modified as follows: both
`O_IOD` and `O_TOT` now take into account the factors coming from the
new term in the functional due to the constraints, which are implemented
by adding the following penalty functional to the spread functional,

$$
\lambda_c \sum_{n=1}^{J'} \left(\overline{\mathbf{r}}_n - \mathbf{r}_{0n} \right)^2,
$$

where $\mathbf{r}_{0n}$ is the desired centre for the $n^{\text{th}}$
Wannier function, see Ref. [@Marianetti] for details. The layout of the
output file at each iteration is unchanged.

          1    -0.884E-01     0.2093698260       -3.2536918930       0.00  <-- CONV

As regarding the final state, the only addition is the information on
the value of the penalty functional associated with the constraints
(`Penalty func`), which should be zero if the final centres of the
Wannier functions are at the target centres:

     Final State
      WF centre and spread    1  ( -1.412902,  1.412902,  1.412902 )     1.63408756
      WF centre and spread    2  (  1.239678, -1.239678,  1.074012 )     2.74801593
      WF centre and spread    3  (  1.239678,  1.074012, -1.239678 )     2.74801592
      WF centre and spread    4  ( -1.074012, -1.239678, -1.239678 )     2.74801592
      Sum of centres and spreads ( -0.007559,  0.007559,  0.007559 )     9.87813534

             Spreads (Ang^2)       Omega IOD_C   =    -4.261222001
            ================       Omega D       =     0.000000000
                                   Omega Rest    =     5.616913337
                                   Penalty func  =     0.000000000
        Final Spread (Ang^2)       Omega Total_C =    -4.261222001
     ------------------------------------------------------------------------------

### Plotting

After WF have been localised, `wannier90` enters its plotting routines
(if required). For example, if you have specified an interpolated
bandstucture:

     *---------------------------------------------------------------------------*
     |                               PLOTTING                                    |
     *---------------------------------------------------------------------------*
      
     Calculating interpolated band-structure

### Summary timings

At the very end of the run, a summary of the time taken for various
parts of the calculation is given. The level of detail is controlled by
the `timing_level` input parameter (set to 1 by default).

     *===========================================================================*
     |                             TIMING INFORMATION                            |
     *===========================================================================*
     |    Tag                                                Ncalls      Time (s)|
     |---------------------------------------------------------------------------|
     |kmesh: get                                        :         1         0.212|
     |overlap: read                                     :         1         0.060|
     |wann: main                                        :         1         1.860|
     |plot: main                                        :         1         0.168|
     *---------------------------------------------------------------------------*
     
     All done: wannier90 exiting

## `seedname.chk`

INPUT/OUTPUT. Information required to restart the calculation or enter
the plotting phase. If we have used disentanglement this file also
contains the rectangular matrices $\bf{U}^{{\rm dis}({\bf k})}$.

## `seedname.r2mn`

OUTPUT. Written if `write_r2mn = true`. The matrix elements
$\langle m|r^2|n\rangle$ (where $m$ and $n$ refer to MLWF)

## `seedname_band.dat`

OUTPUT. Written if `bands_plot=.TRUE.`; The raw data for the
interpolated band structure.

## `seedname_band.gnu`

OUTPUT. Written if `bands_plot=.TRUE.` and ` bands_plot_format=gnuplot`;
A `gnuplot` script to plot the interpolated band structure.

## `seedname_band.agr`

OUTPUT. Written if `bands_plot=.TRUE.` and ` bands_plot_format=xmgrace`;
A `grace` file to plot the interpolated band structure.

## `seedname_band.kpt`

OUTPUT. Written if `bands_plot=.TRUE.`; The k-points used for the
interpolated band structure, in units of the reciprocal lattice vectors.
This file can be used to generate a comparison band structure from a
first-principles code.

## `seedname.bxsf`

OUTPUT. Written if `fermi_surface_plot=.TRUE.`; A Fermi surface plot
file suitable for plotting with XCrySDen.

## `seedname_w.xsf`

OUTPUT. Written if `wannier_plot=.TRUE.` and
` wannier_plot_format=xcrysden`. Contains the ` w`$^{\mathrm{th}}$ WF in
real space in a format suitable for plotting with XCrySDen or VMD, for
example.

## `seedname_w.cube`

OUTPUT. Written if `wannier_plot=.TRUE.` and
` wannier_plot_format=cube`. Contains the ` w`$^{\mathrm{th}}$ WF in
real space in Gaussian cube format, suitable for plotting in XCrySDen,
VMD, gopenmol etc.

## `UNKp.s`

INPUT. Read if `wannier_plot`=`.TRUE.` and used to plot the MLWF. Read
if `transport_mode`=`lcr` and `tran_read_ht`=`.FALSE.` for use in
automated lcr transport calculations.

The periodic part of the Bloch states represented on a regular real
space grid, indexed by k-point `p` (from 1 to `num_kpts`) and spin `s`
('1' for 'up', '2' for 'down').

The name of the wavefunction file is assumed to have the form:

```fortran
    write(wfnname,200) p,spin
200 format ('UNK',i5.5,'.',i1)
```

The first line of each file should contain 5 integers: the number of
grid points in each direction (`ngx`, `ngy` and `ngz`), the k-point
number `ik` and the total number of bands `num_band` in the file. The
full file will be read by `wannier90` as:

```fortran
read(file_unit) ngx,ngy,ngz,ik,nbnd  
do loop_b=1,num_bands
  read(file_unit) (r_wvfn(nx,loop_b),nx=1,ngx*ngy*ngz)
end do
```

If `spinors`=`true` then `s`='NC', and the name of the wavefunction file
is assumed to have the form:

```fortran
    write(wfnname,200) p
200 format ('UNK',i5.5,'.NC')
```

and the file will be read by `wannier90` as:

```fortran
read(file_unit) ngx,ngy,ngz,ik,nbnd  
do loop_b=1,num_bands
  read(file_unit) (r_wvfn_nc(nx,loop_b,1),nx=1,ngx*ngy*ngz) ! up-spinor
  read(file_unit) (r_wvfn_nc(nx,loop_b,2),nx=1,ngx*ngy*ngz) ! down-spinor
end do  
```

All UNK files can be in formatted or unformatted style, this is
controlled by the logical keyword `wvfn_formatted`.

## `seedname_centres.xyz`

OUTPUT. Written if `write_xyz=.TRUE.`; xyz format atomic structure file
suitable for viewing with your favourite visualiser (`jmol`, `gopenmol`,
`vmd`, etc.).

## `seedname_hr.dat`

OUTPUT. Written if `write_hr=.TRUE.`. The first line gives the date and
time at which the file was created. The second line states the number of
Wannier functions `num_wann`. The third line gives the number of
Wigner-Seitz grid-points `nrpts`. The next block of `nrpts` integers
gives the degeneracy of each Wigner-Seitz grid point, with 15 entries
per line. Finally, the remaining `num_wann`$^2 \times$ `nrpts` lines
each contain, respectively, the components of the vector $\mathbf{R}$ in
terms of the lattice vectors $\{\mathbf{A}_{i}\}$, the indices $m$ and
$n$, and the real and imaginary parts of the Hamiltonian matrix element
$H_{mn}^{(\mathbf{R})}$ in the WF basis, e.g.,

     Created on 24May2007 at 23:32:09                            
            20
            17
        4   1   2    1    4    1    1    2    1    4    6    1    1   1   2
        1   2
        0   0  -2    1    1   -0.001013    0.000000
        0   0  -2    2    1    0.000270    0.000000
        0   0  -2    3    1   -0.000055    0.000000
        0   0  -2    4    1    0.000093    0.000000
        0   0  -2    5    1   -0.000055    0.000000
        .
        .
        .

## `seedname_r.dat`

OUTPUT. Written if `write_rmn = true`. The matrix elements
$\langle m\mathbf{0}|\mathbf{r}|n\mathbf{R}\rangle$ (where $n\mathbf{R}$
refers to MLWF $n$ in unit cell $\mathbf{R}$). The first line gives the
date and time at which the file was created. The second line states the
number of Wannier functions `num_wann`. The third line states the number
of $\mathbf{R}$ vectors `nrpts`. Similar to the case of the Hamiltonian
matrix above, the remaining `num_wann`$^2 \times$ `nrpts` lines each
contain, respectively, the components of the vector $\mathbf{R}$ in
terms of the lattice vectors $\{\mathbf{A}_{i}\}$, the indices $m$ and
$n$, and the real and imaginary parts of the position matrix element in
the WF basis.

## `seedname_tb.dat`

OUTPUT. Written if `write_tb=.TRUE.`. This file is essentially a
combination of `seedname_hr.dat` and `seedname_r.dat`, plus lattice
vectors. The first line gives the date and time at which the file was
created. The second to fourth lines are the lattice vectors in Angstrom
unit.

     written on 27Jan2020 at 18:08:42 
      -1.8050234585004898        0.0000000000000000        1.8050234585004898     
       0.0000000000000000        1.8050234585004898        1.8050234585004898     
      -1.8050234585004898        1.8050234585004898        0.0000000000000000 

The next part is the same as `seedname_hr.dat`. The fifth line states
the number of Wannier functions `num_wann`. The sixth line gives the
number of Wigner-Seitz grid-points `nrpts`. The next block of `nrpts`
integers gives the degeneracy of each Wigner-Seitz grid point, with 15
entries per line. Then, the next `num_wann`$^2 \times$ `nrpts` lines
each contain, respectively, the components of the vector $\mathbf{R}$ in
terms of the lattice vectors $\{\mathbf{A}_{i}\}$, the indices $m$ and
$n$, and the real and imaginary parts of the Hamiltonian matrix element
$H_{mn}^{(\mathbf{R})}$ in the WF basis, e.g.,

               7
              93
        4    6    2    2    2    1    2    2    1    1    2    6    2    2    2
        6    2    2    4    1    1    1    4    1    1    1    1    2    1    1
        1    2    2    1    1    2    4    2    1    2    1    1    1    1    2
        1    1    1    2    1    1    1    1    2    1    2    4    2    1    1
        2    2    1    1    1    2    1    1    1    1    4    1    1    1    4
        2    2    6    2    2    2    6    2    1    1    2    2    1    2    2
        2    6    4

       -3    1    1
        1    1    0.42351556E-02 -0.95722060E-07
        2    1    0.69481480E-07 -0.20318638E-06
        3    1    0.10966508E-06 -0.13983284E-06
        .
        .
        .

Finally, the last part is the same as `seedname_r.dat`. The
`num_wann`$^2 \times$ `nrpts` lines each contain, respectively, the
components of the vector $\mathbf{R}$ in terms of the lattice vectors
$\{\mathbf{A}_{i}\}$, the indices $m$ and $n$, and the real and
imaginary parts of the position matrix element in the WF basis (the
float numbers in columns 3 and 4 are the real and imaginary parts for
$\langle m\mathbf{0}|\mathbf{r}_x|n\mathbf{R}\rangle$, columns 5 and 6
for $\langle m\mathbf{0}|\mathbf{r}_y|n\mathbf{R}\rangle$, and columns 7
and 8 for $\langle m\mathbf{0}|\mathbf{r}_z|n\mathbf{R}\rangle$), e.g.

       -3    1    1
        1    1    0.32277552E-09  0.21174901E-08 -0.85436987E-09  0.26851510E-08  ...
        2    1   -0.18881883E-08  0.21786973E-08  0.31123076E-03  0.39228431E-08  ...
        3    1    0.31123242E-03 -0.35322230E-09  0.70867281E-09  0.10433480E-09  ...
        .
        .
        .

## `seedname.bvec`

OUTPUT. Written if `write_bvec = true`. This file contains
the matrix elements of bvector and their weights. The first line gives
the date and time at which the file was created. The second line states
the number of k-points and the total number of neighbours for each
k-point `nntot`. Then all the other lines contain the b-vector (x,y,z)
coordinate and weigths for each k-points and each of its neighbours.

## `seedname_wsvec.dat`

OUTPUT. Written if `write_hr = true` or
`write_rmn = true` or `write_tb = true`. The
first line gives the date and time at which the file was created and the
value of `use_ws_distance`. For each pair of Wannier functions
(identified by the components of the vector $\mathbf{R}$ separating
their unit cells and their indices) it gives: (i) the number of lattice
vectors of the periodic supercell $\mathbf{T}$ that bring the Wannier
function in $\mathbf{R}$ back in the Wigner-Seitz cell centred on the
other Wannier function and (ii) the set of superlattice vectors
$\mathbf{T}$ to make this transformation. These superlattice vectors
$\mathbf{T}$ should be added to the $\mathbf{R}$ vector to obtain the
correct centre of the Wannier function that underlies a given matrix
element (e.g. the Hamiltonian matrix elements in `seedname_hr.dat`) in
order to correctly interpolate in reciprocal space.

    ## written on 20Sep2016 at 18:12:37  with use_ws_distance=.true.
        0    0    0    1    1
        1
        0    0    0
        0    0    0    1    2
        1
        0    0    0
        0    0    0    1    3
        1
        0    0    0
        0    0    0    1    4
        1
        0    0    0
        0    0    0    1    5
        1
        0    0    0
        0    0    0    1    6
        2
        0   -1   -1
        1   -1   -1
        .
        .
        .  

## `seedname_qc.dat`

OUTPUT. Written if `transport = .TRUE.`. The first line
gives the date and time at which the file was created. In the subsequent
lines, the energy value in units of eV is written in the left column,
and the quantum conductance in units of $\frac{2e^2}{h}$
($\frac{e^2}{h}$ for a spin-polarized system) is written in the right
column.

     ## written on 14Dec2007 at 11:30:17
       -3.000000       8.999999
       -2.990000       8.999999
       -2.980000       8.999999
       -2.970000       8.999999
        .
        .
        .

## `seedname_dos.dat`

OUTPUT. Written if `transport = .TRUE.`. The first line
gives the date and time at which the file was created. In the subsequent
lines, the energy value in units of eV is written in the left column,
and the density of states in an arbitrary unit is written in the right
column.

     ## written on 14Dec2007 at 11:30:17
       -3.000000       6.801199
       -2.990000       6.717692
       -2.980000       6.640828
       -2.970000       6.569910
        .
        .
        .

## `seedname_htB.dat`

INPUT/OUTPUT. Read if `transport_mode = bulk` and
`tran_read_ht = .TRUE.`. Written if
`tran_write_ht = .TRUE.`. The first line gives the date and
time at which the file was created. The second line gives `tran_num_bb`.
The subsequent lines contain `tran_num_bb`$\times$`tran_num_bb` $H_{mn}$
matrix, where the indices $m$ and $n$ span all `tran_num_bb` WFs located
at $0^{\mathrm{th}}$ principal layer. Then `tran_num_bb` is recorded
again in the new line followed by $H_{mn}$, where $m^{\mathrm{th}}$ WF
is at $0^{\mathrm{th}}$ principal layer and $n^{\mathrm{th}}$ at
$1^{\mathrm{st}}$ principal layer. The $H_{mn}$ matrix is written in
such a way that $m$ is the fastest varying index.

     written on 14Dec2007 at 11:30:17
       150
       -1.737841   -2.941054    0.052673   -0.032926    0.010738   -0.009515
        0.011737   -0.016325    0.051863   -0.170897   -2.170467    0.202254
        .
        .
        .
       -0.057064   -0.571967   -0.691431    0.015155   -0.007859    0.000474
       -0.000107   -0.001141   -0.002126    0.019188   -0.686423  -10.379876
       150
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000000
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000000
        .
        .
        .
        0.000000    0.000000    0.000000    0.000000    0.000000   -0.001576
        0.000255   -0.000143   -0.001264    0.002278    0.000000    0.000000

## `seedname_htL.dat`

INPUT. Read if `transport_mode = lcr` and
`tran_read_ht = .TRUE.`. The file must be written in the
same way as in `seedname_htB.dat`. The first line can be any comment you
want. The second line gives `tran_num_ll`. `tran_num_ll` in
`seedname_htL.dat` must be equal to that in `seedname.win`. The code
will stop otherwise.

     Created by a WANNIER user
       105
        0.316879    0.000000   -2.762434    0.048956    0.000000   -0.016639
        0.000000    0.000000    0.000000    0.000000    0.000000   -2.809405
        .
        .
        .
        0.000000    0.078188    0.000000    0.000000   -2.086453   -0.001535
        0.007878   -0.545485  -10.525435
       105
        0.000000    0.000000    0.000315   -0.000294    0.000000    0.000085
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000021
        .
        .
        .
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000000
        0.000000    0.000000    0.000000

## `seedname_htR.dat`

INPUT. Read if `transport_mode = lcr` and
`tran_read_ht = .TRUE.` and
`tran_use_same_lead = .FALSE.`. The file must be written in
the same way as in `seedname_htL.dat`. `tran_num_rr` in
`seedname_htR.dat` must be equal to that in `seedname.win`.

## `seedname_htC.dat`

INPUT. Read if `transport_mode = lcr` and
`tran_read_ht = .TRUE.`. The first line can be any comment
you want. The second line gives `tran_num_cc`. The subsequent lines
contain `tran_num_cc`$\times$`tran_num_cc` $H_{mn}$ matrix, where the
indices $m$ and $n$ span all `tran_num_cc` WFs inside the central
conductor region. `tran_num_cc` in `seedname_htC.dat` must be equal to
that in `seedname.win`.

     Created by a WANNIER user
        99
      -10.499455   -0.541232    0.007684   -0.001624   -2.067078   -0.412188
        0.003217    0.076965    0.000522   -0.000414    0.000419   -2.122184
        .
        .
        .
       -0.003438    0.078545    0.024426    0.757343   -2.004899   -0.001632
        0.007807   -0.542983  -10.516896

## `seedname_htLC.dat`

INPUT. Read if `transport_mode = lcr` and
`tran_read_ht = .TRUE.`. The first line can be any comment
you want. The second line gives `tran_num_ll` and `tran_num_lc` in the
given order. The subsequent lines contain
`tran_num_ll`$\times$`tran_num_lc` $H_{mn}$ matrix. The index $m$ spans
`tran_num_ll` WFs in the surface principal layer of semi-infinite left
lead which is in contact with the conductor region. The index $n$ spans
`tran_num_lc` WFs in the conductor region which have a non-negligible
interaction with the WFs in the semi-infinite left lead. Note that
`tran_num_lc` can be different from `tran_num_cc`.

     Created by a WANNIER user
       105    99
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000000
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000000
        .
        .
        .
       -0.000003    0.000009    0.000290    0.000001   -0.000007   -0.000008
        0.000053   -0.000077   -0.000069

## `seedname_htCR.dat`

INPUT. Read if `transport_mode = lcr` and
`tran_read_ht = .TRUE.`. The first line can be any comment
you want. The second line gives `tran_num_cr` and `tran_num_rr` in the
given order. The subsequent lines contain
`tran_num_cr`$\times$`tran_num_rr` $H_{mn}$ matrix. The index $m$ spans
`tran_num_cr` WFs in the conductor region which have a non-negligible
interaction with the WFs in the semi-infinite right lead. The index $n$
spans `tran_num_rr` WFs in the surface principal layer of semi-infinite
right lead which is in contact with the conductor region. Note that
`tran_num_cr` can be different from `tran_num_cc`.

     Created by a WANNIER user
        99   105
       -0.000180    0.000023    0.000133   -0.000001    0.000194    0.000008
       -0.000879   -0.000028    0.000672   -0.000257   -0.000102   -0.000029
        .
        .
        .
        0.000000    0.000000    0.000000    0.000000    0.000000    0.000000
        0.000000    0.000000    0.000000

## `seedname.unkg` {#sec:files_unkg}

INPUT. Read if `transport_mode = lcr` and
`tran_read_ht = .FALSE.`. The first line is the number of
G-vectors at which the $\tilde{u}_{m\mathbf{k}}(\mathbf{G})$ are
subsequently printed. This number should always be 32 since 32 specific
$\tilde{u}_{m\mathbf{k}}$ are required. The following lines contain the
following in this order: The band index $m$, a counter on the number of
G-vectors, the integer co-efficient of the G-vector components $a,b,c$
(where $\mathbf{G}=a\mathbf{b}_1+b\mathbf{b}_2+c\mathbf{b}_3$), then the
real and imaginary parts of the corresponding
$\tilde{u}_{m\mathbf{k}}(\mathbf{G})$ at the $\Gamma$-point. We note
that the ordering in which the G-vectors and
$\tilde{u}_{m\mathbf{k}}(\mathbf{G})$ are printed is not important, but
the specific G-vectors are critical. The following example displays for
a single band, the complete set of $\tilde{u}_{m\mathbf{k}}(\mathbf{G})$
that are required. Note the G-vectors ($a,b,c$) needed.

          32
        1    1    0    0    0   0.4023306   0.0000000
        1    2    0    0    1  -0.0000325   0.0000000
        1    3    0    1    0  -0.3043665   0.0000000
        1    4    1    0    0  -0.3043665   0.0000000
        1    5    2    0    0   0.1447143   0.0000000
        1    6    1   -1    0   0.2345179   0.0000000
        1    7    1    1    0   0.2345179   0.0000000
        1    8    1    0   -1   0.0000246   0.0000000
        1    9    1    0    1   0.0000246   0.0000000
        1   10    0    2    0   0.1447143   0.0000000
        1   11    0    1   -1   0.0000246   0.0000000
        1   12    0    1    1   0.0000246   0.0000000
        1   13    0    0    2   0.0000338   0.0000000
        1   14    3    0    0  -0.0482918   0.0000000
        1   15    2   -1    0  -0.1152414   0.0000000
        1   16    2    1    0  -0.1152414   0.0000000
        1   17    2    0   -1  -0.0000117   0.0000000
        1   18    2    0    1  -0.0000117   0.0000000
        1   19    1   -2    0  -0.1152414   0.0000000
        1   20    1    2    0  -0.1152414   0.0000000
        1   21    1   -1   -1  -0.0000190   0.0000000
        1   22    1   -1    1  -0.0000190   0.0000000
        1   23    1    1   -1  -0.0000190   0.0000000
        1   24    1    1    1  -0.0000190   0.0000000
        1   25    1    0   -2  -0.0000257   0.0000000
        1   26    1    0    2  -0.0000257   0.0000000
        1   27    0    3    0  -0.0482918   0.0000000
        1   28    0    2   -1  -0.0000117   0.0000000
        1   29    0    2    1  -0.0000117   0.0000000
        1   30    0    1   -2  -0.0000257   0.0000000
        1   31    0    1    2  -0.0000257   0.0000000
        1   32    0    0    3   0.0000187   0.0000000
        2    1    0    0    0  -0.0000461   0.0000000
        .
        .
        .

## `seedname_u.mat`

OUTPUT. Written if `write_u_matrices = .TRUE.`. The first
line gives the date and time at which the file was created. The second
line states the number of kpoints `num_kpts` and the number of wannier
functions `num_wann` twice. The third line is empty. Then there are
`num_kpts` blocks of data, each of which starts with a line containing
the kpoint (in fractional coordinates of the reciprocal lattice vectors)
followed by `num_wann * num_wann` lines containing the matrix elements
(real and imaginary parts) of $\mathbf{U}^{(\mathbf{k})}$. The matrix
elements are in column-major order (ie, cycling over rows first and then
columns). There is an empty line between each block of data.

     written on 15Sep2016 at 16:33:46 
               64           8           8
    	 
       0.0000000000  +0.0000000000  +0.0000000000
       0.4468355787  +0.1394579978
      -0.0966033667  +0.4003934902
      -0.0007748974  +0.0011788678
      -0.0041177339  +0.0093821027
       .
       .
       .

       0.1250000000   0.0000000000  +0.0000000000
       0.4694005589  +0.0364941808
      +0.2287801742  -0.1135511138
      -0.4776782452  -0.0511719121
      +0.0142081014  +0.0006203139
       .
       .
       .

## `seedname_u_dis.mat`

OUTPUT. Written if `write_u_matrices = .TRUE.` and
disentanglement is enabled. The first line gives the date and time at
which the file was created. The second line states the number of kpoints
`num_kpts`, the number of wannier functions `num_bands` and the number
of `num_bands`. The third line is empty. Then there are `num_kpts`
blocks of data, each of which starts with a line containing the kpoint
(in fractional coordinates of the reciprocal lattice vectors) followed
by `num_wann * num_bands` lines containing the matrix elements (real and
imaginary parts) of $\mathbf{U}^{\mathrm{dis}(\mathbf{k})}$. The matrix
elements are in column-major order (ie, cycling over rows first and then
columns). There is an empty line between each block of data.

     written on 15Sep2016 at 16:33:46 
               64           8          16
    	    
       0.0000000000  +0.0000000000  +0.0000000000
       1.0000000000  +0.0000000000
      +0.0000000000  +0.0000000000
      +0.0000000000  +0.0000000000
      +0.0000000000  +0.0000000000
       .
       .
       .
       
       0.1250000000   0.0000000000  +0.0000000000
       1.0000000000  +0.0000000000
      +0.0000000000  +0.0000000000
      +0.0000000000  +0.0000000000
      +0.0000000000  +0.0000000000
       .
       .
       .
