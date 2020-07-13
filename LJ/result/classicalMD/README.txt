
N is the number of particles, P is the number of beads each particle

classical MD, time step=0.0025 \tau_{LJ}, steps=10.

(1) init structure
Ar{N}_eq_0.dat

(2) Cvv, velocity-velocity time correlation function
Ar_N{N}_Cvv_0.dat  

(3) RDF, radial distribution function
Ar_N{N}_RDF_0.dat

(4) KE (kinetic energy), PE (potential energy), Etot (KE+PE) along trajectory
Energy_N{N}_eq_0.dat  

(5) configures along trajectory, saved every STEPS_FOR_CONFIG
Ar_{N}_TRAJ_0.dat

format:   for (a=0; a < N; a++) {   
              for (u=0; u<3; u++) outtraj << setw(10) << R[a][u] << ", ";
          }

(6) many-body polarizability tensor (3*3, xx,xy,zy,yx,yy,yz,zx,zy,zz)
Pi_N{N}_eq_0.dat

(7) the final configure and velocities of each particle
FINAL_Ar.dat   

format:    for (a=0; a<N; a++) file << setprecision(12) << R[a][0] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << R[a][1] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << R[a][2] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << V[a][0] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << V[a][1] << endl;
           for (a=0; a<N; a++) file << setprecision(12) << V[a][2] << endl;
