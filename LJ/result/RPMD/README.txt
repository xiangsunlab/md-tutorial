
N is the number of particles, P is the number of beads each particle

RPMD with thermostat 
ref: JCP, 133, 124104(2010)

1. folder prep/

step1: rescale velocities to reach the target temperature.
step2: relax RPMD, without rescaling velocitie.

2. folder traj/
equilibrium RPMD.



(1) init structure
LJ_{N}_eq_0.dat

(2) Cvv, velocity-velocity time correlation function
RPMD{P}_LJ_{N}_Cvv_0.dat   

(3) RDF, radial distribution function
RPMD{P}_LJ_{N}_RDF_0.dat 

(4) beta, kT, KE, SprPE, PE, TotE, Ethr
beta=1/kT, KE (kinetic energy), PE (potential energy), SprPE (potentail energy of harmonic spring), Ethr (accumulated thermal energy), TotE (KE+PE) along trajectory.
The total energy for TRPMD and CMD should include the accumulated thermal energy from the bath. 
Then the Hamiltonian energy = total energy + accumulated thermal energy. (Ehamil=TotE+Ethr)

RPMD{P}_energies.dat (step1, rescale kT)
RPMD{P}_energies_eq.dat (step2, relax)
RPMD{P}_LJ_{N}_STATIS_0.dat (eq RPMD)

(5) configures along trajectory, saved every STEPS_FOR_CONFIG
RPMD{P}_LJ_{N}_TRAJ_eq_0.dat

format:   for (a=0; a < N; a++) {   
              for (u=0; u<3; u++) {
                  for (k=0; k<nbeads; k++) {
                      outtraj << setw(12) << R_RP[k][a][u] << ", ";
                  }
              }
          }


(6) the final configure and velocities
FINAL_RPMD{P}_LJ_{N}_eq_0.dat   

format:    
       for (k=0; k< nbeads; k++) {
           for (a=0; a<N; a++) file << setprecision(12) << R_RP[k][a][0] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << R_RP[k][a][1] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << R_RP[k][a][2] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << V_RP[k][a][0] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << V_RP[k][a][1] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << V_RP[k][a][2] << endl;
      }
