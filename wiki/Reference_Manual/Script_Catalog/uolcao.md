# UOLCAO
> ### Unified olcao driver for running olcao jobs

Orchestrates SCF and post-SCF calculations by managing input
files, selecting the correct executable, and collecting
output. Supports checkpointing: completed calculations are
skipped on restart.


USAGE: uolcao [-scf $basis] [-pscf $basis] [
              [-dos  [$edge]]  | [-scfdos  [$edge]] |
              [-bond [$edge]]  | [-scfbond [$edge]] |
              [-dimo [$edge]]  | [-scfdimo [$edge]] |
              [-mtop [$edge]]  | [-scfmtop [$edge]] |
              [-optc [$edge]]  | [-scfoptc [$edge]] |
              [-pacs [$edge]]  | [-scfpacs [$edge]] |
              [-nlop [$edge]]  | [-scfnlop [$edge]] |
              [-sige [$edge]]  | [-scfsige [$edge]] |
              [-sybd [$edge]]  | [-scfsybd [$edge]] |
              [-force [$edge]] | [-scfforce [$edge]] |
              [-field [$edge]] | [-scffield [$edge]] |
              [-loen] ]
              [-serialxyz]
              [-valgrind]
              -help

| Variable  | Accepted Values          | Description |
|:--------: |:---------------:         |:-----------:|
|edge       | gs,1s,2s,2p,3s,3p,3d,... |Electron Orbitals |
|basis      | MB,FB,EB,NO              |Minimal, full, or extended basis respectively|

| Option       | Outputs      | Defaults              |  Description |
|:---------:   |:------------:|:-------:              |:-------------|
| -scf         | N/A          | FB                    | Controls the basis choice for the scf calculation, if NO is selected the scf calculation will be skipped.|
| -pscf        | N/A          | Operation Dependant   | Acts the same as -scf, but sets the basis for the post scf operation |
| -serialxyz   | N/A          | Not Set               | If set, optical property calculation will conserve memory at the cost of calculation time. Will calculate the x, y, and z components in series |
| -valgrind    | N/A          | Not Set               | Will run the programs in a valgrind environment with --leak-check included by default. |
| -dos/-scfdos | TDOS localization index plot and PDOS raw file | scf: FB; pscf: FB | Will run a density of states calculation using the potential for the requested edge |
|-bond/-scfbond| bond and Q\* raw files | scf: FB; pscf: MB | Will perform a bond order and Q\* calculation for the requested edge |
| -dim/-scfdimo| total dipole moment file | scf: MB; pscf: MB | Runs a dipole moment calculation using the potential for the requested basis |
|-mtop/-scfmtop| Polarization file | scf: FB; pscf: FB| Runs a polarization calculation using the potential for the requested edge.
|-optc/-scfoptc| distinct files that contain x,y,z decompositions such as the optical conductivity, epsilon1, epsilon2, energy loss function (ELF), refractive index, absorption coefficient, reflectivity, and the imaginary epsilon1. Also included will be a file that contains the total epsilon1, epsilon2, and ELF (without x,y,z decomposition). | scf: FB; pscf: FB | Will run a full optical properties suite of calculation using the potential for the requested edge. |
|-pacs/-scfpacs| tbd          | scf: FB; pscf: EB     | Will do a spectral calculation from an initial state to a final state. The type of calculation, and the potentials used depends on the case of the requested edge.  You MUST provide an edge for the -pacs option. PACS = Photo absorption cross section. |
|-nlop/scfnlop | tbd          | scf: FB; pscf: EB     | Will perform a nonlinear  optical properties calculationg using the potential for the requested edge. |
|-sige/-scfsige| tbd          | scf: FB; pscf: FB     | Will calculate the sigma(E) curve of optical transitions with energies of transition that are close to the Fermi energy. |
|-sybd/-scfsybd| tbd          | scf: FB; pscf: FB     | Will perform a symmetric band calculation using the potential for the requested edge. Should be done as a seperate post scf calculation because the used k-points should not usually be used to compute the scf |
|-force/-scfforce| tbd        | scf: FB; pscf: FB     | Experimental; In development
|-field/-scffield| field data | scf: FB; pscf: FB     | Will compute the complex wave function (or real in the case of gamma k-point), the square of the wave function (i.e., the charge density rho), the electronic potential function, the spin dependent wave function charge density, and potential, and the difference between the interacting and non-interacting system wave function, rho, and potential (also with spin dependency). Also computes 1-D axial profiles and charge centers. |
| -loen        | tbd          | N/A                   | Will quantify the local environment around each atom defined by a cutoff factor and some selected algorithm. Presently, the available algorithm is the bispectrum component.|


 

