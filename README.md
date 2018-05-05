# GRCS
Random quantum circuits for circuit sampling with superconducting qubits.

See:
https://arxiv.org/abs/1608.00263

The directory cz_v2 contains an improved rearrangement of the circuits in that paper. These are circuits for qubits in a 2D lattice, using controlled-phase (CZ) gates. The differences with the ones in the previous reference are:

1.- The cycles of two qubit gates (see Fig. 6) have been reordered. Cycles now alternate between horizontal and vertical gates. 

2.- Every CZ gate is followed by a non-diagonal single qubit gate if possible, to avoid the pattern CZ - T - CZ (see https://arxiv.org/abs/1804.04797). 

3.- A T gate follows a non-diagonal single qubit gate if possible. 

4.- We include a layer of Hadamards explicitly before measurement in the computational basis. 

The directory is_v2 contains the same circuits, except that CZ gates are replaced by ISWAP gates. This gate is harder to simulate classically with distributed implementations. 

In each directory, each tar file nxm.tar.gz contains circuits for qubits in an n times m lattice. The files inside are named nxm_maxcycle_id.txt where maxcycle is the index of the last clock cycle in the circuit, and id is a number identifying the particular instance. The first cycle of Hadamards is cycle 0. 

The first line in each file is the number of qubits. Qubits are row-major ordered. 
The following lines correspond to qubit gates. 

A single qubit gate is:
cycle gate qubit
where cycle is the cycle number, gate is 'h', 'x_1_2', 'y_1_2' or 't', and qubit is the qubit number. 

A two qubit gate is:
cycle gate qubit1 qubit2
where gate is 'cz' or 'is', and qubit1, qubit2 are the qubits in which the gate acts. 

For the gates, 'h' is Hadamard', 'x_1_2' ('y_1_2') is a pi/2 rotation around the x (y) axis, 't' is a T gate, 'cz' is a controlled-phase, and 'is' is ISWAP.
