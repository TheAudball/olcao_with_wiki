## File Formats

Olcao is built around the skeleton file. However, there are many python scripts meant to convert other file types to .skl and conversly, .skl to those other files. Herein, any non-skeleton file types will be reffered to as the "converted filetype".

The conversion scripts all follow a `*2skl.py` or `skl2*.py` convention. Where * is some signifier as to the other filetype. Below is a table containing all of the conversion files accessible, as well as a list of some programs using the converted filetype.

| script    | input     | output    | Associated external program   |
|:------:   |:-----:    |:------:   |:-----------------------------:|
|dump2skl   |dump       |skl        | LAMMPS
|lmp2skl    |lamps file |skl        |
|pbd2skl    |pbd        |skl        |
|cif2skl    |cif        |skl        |
|struct2skl |structure  |skl        |
|vasp2skl   |vasp       |skl        |
|xyz2skl    |xyz        |skl        |
|skl2isaacs |skl        |isaacs     |
|skl2lmp    |skl        |lamps      |
|skl2pbd    |skl        |pbd        |
|skl2vasp   |skl        |vasp files |

## Options

Since each converted filetype is different, there is no unified options that remains true for all scripts. So a list of options will be given below for each conversion script. Detailed descriptions can be found in each scripts individual documentation page under Script Catalog.

#### Option List:

**dump2skl**
- -d/-dump [path]:      specifies the path to the LAMMPS dump file
- -a/-data [path]:      specifies the path to the LAMMPS data file
- -f/-frame [int]:      specifies the frame number of the desired frame
- -t/-timestep [int]:   Specifies the timestep number of the desired timestep
- -n/-name [string]:    Specifies a system name, will be printed in the .skl header
- -h/-help:             Prints the help text
- -np/-nonPeriodic:     Adds padding to ensure it acts like a non-periodic system

**lmp2skl**
Unknown script purpose

**
