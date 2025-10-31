NBody code (written by D. Hubber, adapted by D. Stamatellos)

"We use a fourth-order Hermite integration scheme (Makino & Aarseth 1992),
with a conservative time-step criterion so that energy is conserved to better than 1e-8"

Compilation

make nbody

Run

./nbody runID

where runID is the name given to the specific run.

The input file to be read and some other parameters are defined in nb.params.dat (needs to be in the folder of the run). In this file the units are set, the accuracy of the simulation (eta1, eta2), the run time of the simulation (in the units set) and the output interval. Sink-radius used to smooth gravity during close interactions.

nb.params.dat file

xxxxx       -Runid-
run_ic.dat  -Initial-conditions-file-
20000       -Simulation-run-time
10          -Output-snapshot-time-
au          -length-unit-
m_sun       -mass-unit-
yr          -time-unit-
km/s        -velocity-unit-
cgs         -energy-unit-
1.0         -rscale-
1.0         -mscale-
0.01        -eta1-timestep-parameter-
0.01        -eta2-timestep-parameter-
0.1         -sink-radius-


Sample input file (run_ic.dat)

6 sinks
id/pid/step/time(yr)/mass(Msun)/x/y/z/r(AU)/vx/vy/vz/v(km/s)
 1   150001         2  4.1176e+04  7.5341e-01  3.5100e+02  1.1500e+03  1.1300e+01 1.2024e+03  1.0100e+00  4.9100e-01  5.0500e-04 1.1230e+00
 2   136734    115502  4.1176e+04  2.2977e-01  3.2500e+02  1.1800e+03  1.1300e+01 1.2240e+03 -3.0900e+00 -7.9400e-01  8.8700e-03 3.1904e+00
 3    65173    147198  4.1176e+04  8.6431e-02 -3.7800e+03 -7.6600e+03  1.9600e+02 8.5441e+03 -5.9700e-01 -1.4300e+00  6.5400e-02 1.5510e+00
 4   149019    172208  4.1176e+04  6.6458e-02 -3.8900e+03 -6.1500e+03 -3.9500e+01 7.2771e+03 -6.7800e-01 -1.2700e+00 -4.3500e-03 1.4397e+00
 5     2459    296434  4.1176e+04  2.8663e-02 -4.7300e+03 -1.6500e+04 -3.5600e+02 1.7168e+04 -9.3800e-01 -3.2100e+00 -6.7500e-02 3.3449e+00
 6    23563    437414  4.1176e+04  7.5040e-03  3.0000e+03 -1.0500e+03 -3.3400e+01 3.1786e+03  6.5000e-01  1.9100e-01 -7.6700e-03 6.7752e-01


Notes
-id is the name of the body
-The file has to be at this format to be read properly by the code
-pid and step refer to info from the previous SPH run (not needed for independent simulations, can be set to 0). Time to be set to 0.



The code will run and output a file per each body
E.g. if we run ./nbody run1 then we have 6 files, run1.body.1.dat, run1.body.2.dat, ...
and at the end of simulation a run1.final.dat file.



Sample output files

run1.final.dat (Similar to the run_ic.dat formtt but also inlcudes the angular momentum (with respect to the star, assumed to be body1), and the angle with respect to the assumed disc midplane)

id/pid/step/time(yr)/mass(Msun)/x/y/z/r(AU)/vx/vy/vz(km/s)/v/lx/ly/lz/l/angle
1 0 0 3.0000e+05 7.5341e-01  0.0000e+00  0.0000e+00  0.0000e+00 0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00 0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00 -1.0000e+02
2 0 0 3.0000e+05 2.2977e-01 -4.7411e+01 -7.7671e+00  8.6870e-02 4.8043e+01  1.0094e+00 -3.1337e+00  2.7387e-03 3.2922e+00  5.7661e-02  4.9982e-02  3.5938e+01  3.5938e+01 1.2166e-01
3 0 0 3.0000e+05 8.6431e-02 -4.0276e+04 -9.1019e+04  2.0434e+03 9.9553e+04 -4.1195e-01 -2.1999e+00  4.0167e-02 2.2385e+00  7.2547e+01  6.7071e+01  4.4174e+03  4.4185e+03 1.2813e+00
4 0 0 3.0000e+05 6.6458e-02 -4.0734e+04 -8.9291e+04  1.5523e+03 9.8155e+04 -4.4739e-01 -2.2680e+00  2.2645e-02 2.3118e+00  9.9597e+01  1.5148e+01  3.4849e+03  3.4863e+03 1.6559e+00
5 0 0 3.0000e+05 2.8663e-02 -5.8897e+04 -2.0184e+05 -4.1549e+03 2.1030e+05 -7.5153e-01 -4.1061e+00 -6.8712e-02 4.1749e+00 -9.1481e+01 -2.6496e+01  2.5840e+03  2.5857e+03 2.1109e+00
6 0 0 3.0000e+05 7.5040e-03  8.7509e+03  4.6909e+03 -1.4908e+02 9.9300e+03  9.7111e-02 -6.5493e-01  2.9774e-03 6.6210e-01 -6.2787e-01 -3.0416e-01 -4.6426e+01  4.6431e+01 1.7914e+02


run1.body.1.dat (generated for each body in the simulation)

time - N/A - N/A - N/A - mass -  x  - y - z - vx - vy - vz - binding energy- semi major axis - eccentricity- period

4.117600e+04 0 0 0 7.5341e-01  3.5100e+02  1.1500e+03  1.1300e+01  1.0100e+00  4.9100e-01  5.0500e-04  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.119620e+04 0 0 0 7.5341e-01  3.5452e+02  1.1528e+03  1.1302e+01  6.4195e-01  7.8538e-01  6.8616e-04  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.121651e+04 0 0 0 7.5341e-01  3.5648e+02  1.1565e+03  1.1306e+01  2.7486e-01  9.1620e-01  1.0932e-03  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.123672e+04 0 0 0 7.5341e-01  3.5687e+02  1.1605e+03  1.1312e+01 -8.9195e-02  9.3500e-01  1.6512e-03  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.125715e+04 0 0 0 7.5341e-01  3.5568e+02  1.1643e+03  1.1321e+01 -4.6827e-01  8.4249e-01  2.3880e-03  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.127755e+04 0 0 0 7.5341e-01  3.5282e+02  1.1675e+03  1.1333e+01 -8.6551e-01  5.8657e-01  3.3812e-03  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.129762e+04 0 0 0 7.5341e-01  3.4836e+02  1.1689e+03  1.1350e+01 -1.2199e+00  1.4135e-02  4.7458e-03  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
4.131768e+04 0 0 0 7.5341e-01  3.4324e+02  1.1667e+03  1.1373e+01 -9.8168e-01 -1.1851e+00  6.0311e-03  0.0000e+00  0.0000e+00  0.0000e+00  0.0000e+00
