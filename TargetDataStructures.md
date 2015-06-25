# Introduction #

As one of hopefully several articles on the internal data structures in CFAST, this wiki page describes the content of the data structures used to calculate target temperature and incident heat flux in CFAST.  These are of use largely to developers of the model.


# Details #

**XXTARG**: Real data for each target is contained in the array.  It has the following structure:

Two-dimension array (1:TRGXROW, 1:MXTRG)<br>
first index: index of values for each target as follows (names in parentheses are defined name for parameter in fltarget.fi):<br>
<br>
1  (TRGCENX): position of target center in X direction (user input from input data file)<br>
2  (TRGCENY): position of target center in Y direction (user input from input data file)<br>
3  (TRGCENZ): position of target center in Z direction (user input from input data file)<br>
4  (TRGNORMX): target normal vector, X component (user input from input data file)<br>
5  (TRGNORMY): target normal vector, Y component (user input from input data file)<br>
6  (TRGNORMZ): target normal vector, Z component (user input from input data file)<br>
7  (TRGK): target thermal conductivity (from thermal properties database)<br>
8  (TRGRHO): target density (from thermal properties database)<br>
9  (TRGCP): target heat capacity (from thermal properties database)<br>
10 (TRGL): target thickness (from thermal properties database)<br>
11: (TRGEMIS): target emissivity (from thermal properties database)<br>
12: (TRGTFLUXF): incident heat flux to front surface of target (calculated)<br>
13: (TRGTFLUXB): incident heat flux to back surface of target (calculated)<br>
14: (TRGNFLUXF): net heat flux to front surface of target (calculated)<br>
15: (TRGNFLUXB): net heat flux to back surface of target (calculated)<br>
16: (TRGTEMPF): front surface temperature of target (calculated)<br>
17 ... TRGTEMPF+TRGTNUM-2: internal temperatures within target (calculated)<br>
TRGTEMPB (TRGTEMPF+TRGTNUM-1): back surface temperature of target (calculated)<br>

second index: index of targets beginning with a value of 1<br>
<br>
<b>TGTARG</b>: local gas temperature surrounding the target.  Used to calculate convective heat transfer to the target.<br>
<br>
<b>CXTARG</b>: Character name of each target material that corresponds to short material name in thermal properties<br>
<br>
Vector dimensioned (1:MXTRG)<br>
first index: index of targets beginning with a value of 1. 1 to 1 correspondence with order in XXTARG<br>
<br>
<b>IXTARG</b>: Integer data for each target.<br>
<br>
Two-dimension array (1:TRGIROW,1:MXTRG)<br>
first index: index of values for each target as follows (names in parentheses are defined name for parameter in fltarget.fi):<br>
<br>
1 (TRGROOM): Compartment where the target is located (user input from the input data file)<br>
2 (TRGLAYER): Layer (within the compartment) where the target is located (calculated)<br>
3 (TRGWALL): compartment surface if target is located on a surface (currently unused and set to zero)<br>
4 (TRGMETH): calculation method (STEADY, IMPLICIT, EXPLICIT) (user input from the input data file)<br>
5 (TRGEQ): equation type for calculation (ODE, PDE) (user input from input data file)<br>
6 (TRGBACK): INT=1 or EXT=2 whether back face of target is internal to the compartment or outside the compartment (calculated)