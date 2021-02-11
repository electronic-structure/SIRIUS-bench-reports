# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      756.38 s  →      291.66 s   (-61.44%) |       1   →       1              |      756.38 s  →      291.66 s   (-61.44%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.71 s    (-0.60%) |       1   →       1              |        2.72 s  →        2.71 s    (-0.60%) | 
- ├ sirius::Simulation_context::initialize                              |        2.93 s  →        5.82 s   (+98.75%) |       1   →       1              |        2.93 s  →        5.82 s   (+98.75%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      518.24 μs →       37.18 ms (+7073.53%) |       1   →       1              |      518.24 μs →       37.18 ms (+7073.53%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      157.46 ms →        3.03 s  (+1826.34%) |       1   →       1              |      157.46 ms →        3.03 s  (+1826.34%) | 
- │ │ ├ sirius::Atom_type::init                                         |       67.51 ms →        1.50 s  (+2129.08%) |       2   →       2              |      135.02 ms →        3.01 s  (+2129.08%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.36 ms →       23.15 ms   (+3.52%) |       1   →       1              |       22.36 ms →       23.15 ms   (+3.52%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.02 ms →        6.33 ms   (+5.14%) |       1   →       1              |        6.02 ms →        6.33 ms   (+5.14%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.29 ms →       16.77 ms   (+2.94%) |       1   →       1              |       16.29 ms →       16.77 ms   (+2.94%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.27 ms →       16.74 ms   (+2.91%) |       1   →       1              |       16.27 ms →       16.74 ms   (+2.91%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.17 ms   (+0.11%) |       1   →       1              |        4.16 ms →        4.17 ms   (+0.11%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.36 ms   (+0.67%) |       1   →       1              |        2.35 ms →        2.36 ms   (+0.67%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.26 μs →      112.70 μs  (+11.30%) |       1   →       1              |      101.26 μs →      112.70 μs  (+11.30%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.70 s    (-1.05%) |       1   →       1              |        2.73 s  →        2.70 s    (-1.05%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.81 ms →       10.91 ms   (+0.85%) |       1   →       1              |       10.81 ms →       10.91 ms   (+0.85%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.46 ms   (+0.32%) |       1   →       1              |        4.44 ms →        4.46 ms   (+0.32%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.40 ms   (+1.07%) |       1   →       1              |        6.34 ms →        6.40 ms   (+1.07%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.38 ms   (+1.04%) |       1   →       1              |        6.32 ms →        6.38 ms   (+1.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.88 ms   (+1.35%) |       1   →       1              |        3.83 ms →        3.88 ms   (+1.35%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.01%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.01%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.06 μs →      113.72 μs  (+14.79%) |       1   →       1              |       99.06 μs →      113.72 μs  (+14.79%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.38 ms →       65.00 ms   (+0.95%) |       2   →       2              |      128.77 ms →      130.00 ms   (+0.95%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.13 ms   (+0.05%) |       2   →       2              |       10.26 ms →       10.26 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.47 ms   (-0.05%) |       1   →       1              |        4.48 ms →        4.47 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.74 ms   (-0.08%) |       2   →       2              |       43.51 ms →       43.48 ms   (-0.08%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.77 ms →       14.77 ms   (-0.01%) |       2   →       2              |       29.54 ms →       29.54 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.74 ms →       19.46 ms   (-1.43%) |       4   →       4              |       78.97 ms →       77.83 ms   (-1.43%) | 
  │   ├ sddk::Gvec::init                                                |      187.62 ms →      171.28 ms   (-8.71%) |       2   →       2              |      375.24 ms →      342.55 ms   (-8.71%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      141.07 ms →      128.92 ms   (-8.61%) |       2   →       2              |      282.13 ms →      257.83 ms   (-8.61%) | 
+ │   ├ sddk::Gvec_shells                                               |      195.20 ms →      163.68 ms  (-16.15%) |       1   →       1              |      195.20 ms →      163.68 ms  (-16.15%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.41%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.41%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.82 ms →      296.78 ms   (+1.35%) |       2   →       2              |      585.65 ms →      593.57 ms   (+1.35%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       83.58 ms →       75.84 ms   (-9.26%) |       1   →       1              |       83.58 ms →       75.84 ms   (-9.26%) | 
- │ ├ sirius::K_point::K_point                                          |        2.89 μs →        4.45 μs  (+54.04%) |       4   →       4              |       11.55 μs →       17.80 μs  (+54.04%) | 
  │ └ sirius::K_point_set::initialize                                   |       83.49 ms →       75.74 ms   (-9.29%) |       1   →       1              |       83.49 ms →       75.74 ms   (-9.29%) | 
  │   └ sirius::K_point::initialize                                     |       20.86 ms →       18.91 ms   (-9.33%) |       4   →       4              |       83.44 ms →       75.65 ms   (-9.33%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.90 ms →       14.37 ms   (-9.60%) |       4   →       4              |       63.58 ms →       57.48 ms   (-9.60%) | 
  │     │ └ sddk::Gvec::init                                            |        4.01 ms →        3.79 ms   (-5.52%) |       4   →       4              |       16.05 ms →       15.17 ms   (-5.52%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.17 μs →        8.89 μs   (-3.06%) |       4   →       4              |       36.69 μs →       35.57 μs   (-3.06%) | 
  │     └ sirius::K_point::update                                       |        3.48 ms →        3.26 ms   (-6.28%) |       4   →       4              |       13.90 ms →       13.03 ms   (-6.28%) | 
  │       └ sirius::Beta_projectors                                     |        1.77 ms →        1.78 ms   (+0.09%) |       4   →       4              |        7.10 ms →        7.10 ms   (+0.09%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      968.72 μs →      953.38 μs   (-1.58%) |       4   →       4              |        3.87 ms →        3.81 ms   (-1.58%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.25 ms →        5.20 ms   (-0.94%) |       2   →       2              |       10.49 ms →       10.39 ms   (-0.94%) | 
+ ├ sirius::Potential                                                   |      170.17 ms →      151.30 ms  (-11.09%) |       1   →       1              |      170.17 ms →      151.30 ms  (-11.09%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms →        5.73 ms   (-2.22%) |       6   →       5    (-16.67%) |       35.15 ms →       28.64 ms  (-18.51%) | 
  │ └ sirius::Potential::update                                         |      134.31 ms →      121.92 ms   (-9.22%) |       1   →       1              |      134.31 ms →      121.92 ms   (-9.22%) | 
  │   └ sirius::Potential::generate_local_potential                     |      133.51 ms →      121.18 ms   (-9.24%) |       1   →       1              |      133.51 ms →      121.18 ms   (-9.24%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.21 ms →      106.91 ms   (-5.57%) |       1   →       1              |      113.21 ms →      106.91 ms   (-5.57%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       19.76 ms →        9.99 ms  (-49.47%) |       1   →       1              |       19.76 ms →        9.99 ms  (-49.47%) | 
  ├ sirius::Density                                                     |      142.47 ms →      128.66 ms   (-9.69%) |       1   →       1              |      142.47 ms →      128.66 ms   (-9.69%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.17 ms →        5.18 ms   (+0.26%) |       2   →       2              |       10.34 ms →       10.37 ms   (+0.26%) | 
+ │ └ sirius::Density::update                                           |      131.86 ms →      118.02 ms  (-10.49%) |       1   →       1              |      131.86 ms →      118.02 ms  (-10.49%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |      131.44 ms →      117.61 ms  (-10.52%) |       1   →       1              |      131.44 ms →      117.61 ms  (-10.52%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       104.80 μs            |                   1              |                       104.80 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.88 ms →      109.34 ms   (-3.14%) |       1   →       1              |      112.88 ms →      109.34 ms   (-3.14%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       18.10 ms →        7.72 ms  (-57.34%) |       1   →       1              |       18.10 ms →        7.72 ms  (-57.34%) | 
  ├ sirius::Density::initial_density                                    |      176.49 ms →      164.29 ms   (-6.91%) |       1   →       1              |      176.49 ms →      164.29 ms   (-6.91%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.94 ms →      108.47 ms   (-2.23%) |       1   →       1              |      110.94 ms →      108.47 ms   (-2.23%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.66 ms →        6.37 ms  (-45.35%) |       2   →       2              |       23.33 ms →       12.75 ms  (-45.35%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.99 ms →        9.82 ms   (-1.73%) |       1   →       1              |        9.99 ms →        9.82 ms   (-1.73%) | 
  ├ sirius::Potential::generate                                         |      585.54 ms →      560.00 ms   (-4.36%) |       1   →       1              |      585.54 ms →      560.00 ms   (-4.36%) | 
  │ ├ sirius::Potential::poisson                                        |      139.64 ms →      126.33 ms   (-9.53%) |       1   →       1              |      139.64 ms →      126.33 ms   (-9.53%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.57 ms →        6.90 ms  (-64.73%) |       1   →       1              |       19.57 ms →        6.90 ms  (-64.73%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.69 ms →       11.27 ms   (+5.41%) |       1   →       1              |       10.69 ms →       11.27 ms   (+5.41%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.26 ms →       10.44 ms   (+1.75%) |       1   →       1              |       10.26 ms →       10.44 ms   (+1.75%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.26 ms →       10.44 ms   (+1.75%) |       1   →       1              |       10.26 ms →       10.44 ms   (+1.75%) | 
+ │ ├ sirius::Periodic_function::add                                    |      544.57 μs →      452.60 μs  (-16.89%) |       2   →       2              |        1.09 ms →      905.21 μs  (-16.89%) | 
+ │ ├ sirius::Potential::xc                                             |       51.89 ms →       32.42 ms  (-37.52%) |       1   →       1              |       51.89 ms →       32.42 ms  (-37.52%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.89 ms →       30.10 ms  (-41.99%) |       1   →       1              |       51.89 ms →       30.10 ms  (-41.99%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        5.69 ms →        5.56 ms   (-2.35%) |       2   →       1    (-50.00%) |       11.39 ms →        5.56 ms  (-51.18%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.21 ms                             |       1                          |        5.21 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                         8.52 ms            |                   2              |                        17.03 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.87 ms →        5.55 ms   (-5.45%) |       1   →       1              |        5.87 ms →        5.55 ms   (-5.45%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.63 ms →       93.67 ms   (+1.12%) |       1   →       1              |       92.63 ms →       93.67 ms   (+1.12%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.05 ms →      299.76 ms   (+2.29%) |       1   →       1              |      293.05 ms →      299.76 ms   (+2.29%) | 
- ├ sirius::Hamiltonian0                                                |        8.39 ms →       12.07 ms  (+43.82%) |       1   →       1              |        8.39 ms →       12.07 ms  (+43.82%) | 
  │ ├ sirius::Local_operator                                            |        8.04 ms →        8.12 ms   (+1.09%) |       1   →       1              |        8.04 ms →        8.12 ms   (+1.09%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.68 ms   (-1.85%) |       1   →       1              |        4.77 ms →        4.68 ms   (-1.85%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        2.52 ms   (+8.26%) |       1   →       1              |        2.33 ms →        2.52 ms   (+8.26%) | 
  │ ├ sirius::Non_local_operator                                        |       61.95 μs →       63.17 μs   (+1.95%) |       2   →       2              |      123.91 μs →      126.33 μs   (+1.95%) | 
- │ ├ sirius::D_operator::initialize                                    |       99.30 μs →        1.29 ms (+1203.10%) |       1   →       1              |       99.30 μs →        1.29 ms (+1203.10%) | 
- │ └ sirius::Q_operator::initialize                                    |       73.67 μs →        2.47 ms (+3247.71%) |       1   →       1              |       73.67 μs →        2.47 ms (+3247.71%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.97 s  →        4.05 s    (+1.85%) |       1   →       1              |        3.97 s  →        4.05 s    (+1.85%) | 
- │ ├ sirius::Hamiltonian_k                                             |      203.73 μs →      384.62 μs  (+88.79%) |       4   →       4              |      814.91 μs →        1.54 ms  (+88.79%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      198.40 μs →      377.93 μs  (+90.49%) |       4   →       4              |      793.58 μs →        1.51 ms  (+90.49%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        3.81 μs →        3.28 μs  (-13.84%) |       4   →       4              |       15.25 μs →       13.14 μs  (-13.84%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      992.84 ms →        1.01 s    (+1.76%) |       4   →       4              |        3.97 s  →        4.04 s    (+1.76%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.99 ms →       32.98 ms   (-0.02%) |      16   →      16              |      527.86 ms →      527.75 ms   (-0.02%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.55 ms →       14.44 ms   (-0.75%) |       4   →       4              |       58.20 ms →       57.77 ms   (-0.75%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.30 ms →        5.28 ms   (-0.40%) |       4   →       4              |       21.21 ms →       21.13 ms   (-0.40%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      355.95 ms →      354.63 ms   (-0.37%) |       4   →       4              |        1.42 s  →        1.42 s    (-0.37%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      259.45 ms →      257.73 ms   (-0.66%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.66%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.28 ms →       63.36 ms   (-1.44%) |       4   →       4              |      257.13 ms →      253.43 ms   (-1.44%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.46 ms →       16.76 ms   (+1.84%) |       4   →       4              |       65.84 ms →       67.05 ms   (+1.84%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.46 ms →       16.76 ms   (+1.84%) |       4   →       4              |       65.83 ms →       67.04 ms   (+1.84%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.30 ms →       40.08 ms   (-2.96%) |       4   →       4              |      165.20 ms →      160.31 ms   (-2.96%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.47 ms →       16.59 ms   (+0.73%) |       4   →       4              |       65.90 ms →       66.38 ms   (+0.73%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.47 ms →       16.59 ms   (+0.73%) |       4   →       4              |       65.89 ms →       66.37 ms   (+0.73%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.07 ms →       53.48 ms   (-1.08%) |       4   →       4              |      216.26 ms →      213.92 ms   (-1.08%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.98 ms →       35.45 ms   (-1.48%) |       4   →       4              |      143.94 ms →      141.80 ms   (-1.48%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.94 ms   (-0.38%) |       4   →       4              |        7.81 ms →        7.78 ms   (-0.38%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.20 ms →       40.69 ms   (+1.21%) |       4   →       4              |      160.82 ms →      162.76 ms   (+1.21%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        6.99 ms →        7.59 ms   (+8.70%) |       4   →       4              |       27.94 ms →       30.37 ms   (+8.70%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.15 ms →       27.11 ms   (-0.15%) |       8   →       8              |      217.19 ms →      216.87 ms   (-0.15%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.27 ms →       14.90 ms   (+4.44%) |       8   →       8              |      114.16 ms →      119.23 ms   (+4.44%) | 
  │ │ │ ├ sddk::inner                                                   |       14.21 ms                             |       8                          |      113.66 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       52.08 μs                             |       8                          |      416.68 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.85 ms            |                   8              |                       118.83 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        76.25 ns            |                   8              |                       610.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.67 ms            |                   8              |                       117.33 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       335.62 ns            |                   8              |                         2.68 μs            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      335.63 ms →      352.32 ms   (+4.97%) |       4   →       4              |        1.34 s  →        1.41 s    (+4.97%) | 
  │ │ ├ sddk::transform                                                 |       27.86 ms                             |       4                          |      111.45 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       34.78 μs                             |       4                          |      139.11 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |      937.41 μs                             |       4                          |        3.75 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       25.22 μs                             |       4                          |      100.88 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        26.67 ms            |                   4              |                       106.66 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        26.47 ms            |                   4              |                       105.89 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      400.50 ns →      377.00 ns   (-5.87%) |       4   →       4              |        1.60 μs →        1.51 μs   (-5.87%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      744.61 s  →      277.10 s   (-62.79%) |       1   →       1              |      744.61 s  →      277.10 s   (-62.79%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.33 ms   (-7.84%) |      19   →      18     (-5.26%) |      109.85 ms →       95.91 ms  (-12.69%) | 
  │ ├ sirius::Density                                                   |                       129.10 ms            |                   1              |                       129.10 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.20 ms            |                   2              |                        10.40 ms            | 
  │ │ └ sirius::Density::update                                         |                       118.42 ms            |                   1              |                       118.42 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       117.99 ms            |                   1              |                       117.99 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       129.46 μs            |                   1              |                       129.46 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       108.92 ms            |                   1              |                       108.92 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         8.48 ms            |                   1              |                         8.48 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       27.53 s  →       11.52 s   (-58.15%) |      27   →      24    (-11.11%) |      743.35 s  →      276.56 s   (-62.80%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.45 ms →        8.08 ms  (+81.60%) |      27   →      24    (-11.11%) |      120.09 ms →      193.84 ms  (+61.42%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.09 ms →        4.14 ms   (+1.24%) |      27   →      24    (-11.11%) |      110.37 ms →       99.33 ms  (-10.01%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      953.23 μs →      977.10 μs   (+2.50%) |      27   →      24    (-11.11%) |       25.74 ms →       23.45 ms   (-8.88%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        2.24 ms   (-0.37%) |      27   →      24    (-11.11%) |       60.63 ms →       53.69 ms  (-11.44%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.89 μs →       64.60 μs   (-0.45%) |      54   →      48    (-11.11%) |        3.50 ms →        3.10 ms  (-11.51%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       92.65 μs →        1.29 ms (+1295.72%) |      27   →      24    (-11.11%) |        2.50 ms →       31.03 ms (+1140.64%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       70.51 μs →        2.45 ms (+3378.02%) |      27   →      24    (-11.11%) |        1.90 ms →       58.86 ms (+2991.58%) | 
+ │ │ ├ sirius::Band::solve                                             |       25.41 s  →        9.41 s   (-62.97%) |      27   →      24    (-11.11%) |      686.16 s  →      225.84 s   (-67.09%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      202.07 μs →      322.19 μs  (+59.45%) |     108   →      96    (-11.11%) |       21.82 ms →       30.93 ms  (+41.73%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      195.58 μs →      315.28 μs  (+61.21%) |     108   →      96    (-11.11%) |       21.12 ms →       30.27 ms  (+43.29%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.89 μs →        3.74 μs  (-23.38%) |     108   →      96    (-11.11%) |      527.66 μs →      359.38 μs  (-31.89%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        6.35 s  →        2.35 s   (-62.99%) |     108   →      96    (-11.11%) |      686.13 s  →      225.72 s   (-67.10%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       16.81 ms →       12.00 ms  (-28.60%) |     108   →      96    (-11.11%) |        1.82 s  →        1.15 s   (-36.53%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      775.77 μs →      628.19 ns  (-99.92%) |     648   →     576    (-11.11%) |      502.70 ms →      361.84 μs  (-99.93%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.85 ms →        1.85 ms   (-0.11%) |     108   →      96    (-11.11%) |      200.04 ms →      177.62 ms  (-11.21%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      358.16 μs →      354.73 μs   (-0.96%) |     108   →      96    (-11.11%) |       38.68 ms →       34.05 ms  (-11.96%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      546.10 μs →      550.74 μs   (+0.85%) |     216   →     192    (-11.11%) |      117.96 ms →      105.74 ms  (-10.36%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        6.33 s  →        2.33 s   (-63.19%) |     108   →      96    (-11.11%) |      683.14 s  →      223.52 s   (-67.28%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.61 ms →       66.98 ms   (-3.78%) |     827   →     851     (+2.90%) |       57.57 s  →       57.00 s    (-0.99%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.26 ms →       42.56 ms   (-3.83%) |     827   →     851     (+2.90%) |       36.60 s  →       36.22 s    (-1.04%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.38 ms →        8.30 ms   (-0.97%) |     827   →     851     (+2.90%) |        6.93 s  →        7.06 s    (+1.91%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       65.21 μs →      251.54 μs (+285.71%) |     827   →     851     (+2.90%) |       53.93 ms →      214.06 ms (+296.90%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      483.56 μs →        2.21 ms (+357.69%) |     108   →      96    (-11.11%) |       52.22 ms →      212.47 ms (+306.84%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.00 ms →        6.36 ms   (-9.09%) |     827   →     851     (+2.90%) |        5.79 s  →        5.42 s    (-6.45%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       66.11 μs →       96.77 μs  (+46.38%) |     827   →     851     (+2.90%) |       54.67 ms →       82.35 ms  (+50.62%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      488.39 μs →      836.64 μs  (+71.30%) |     108   →      96    (-11.11%) |       52.75 ms →       80.32 ms  (+52.27%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.71 ms →        9.24 ms   (-4.78%) |     827   →     851     (+2.90%) |        8.03 s  →        7.86 s    (-2.02%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.04 ms →        5.77 ms   (-4.52%) |     827   →     851     (+2.90%) |        4.99 s  →        4.91 s    (-1.75%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.57%) |     827   →     851     (+2.90%) |        1.26 s  →        1.29 s    (+2.32%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.70 ms →        8.38 ms   (-3.68%) |     827   →     851     (+2.90%) |        7.19 s  →        7.13 s    (-0.89%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.29 ms →        1.33 ms   (+3.09%) |     827   →     851     (+2.90%) |        1.06 s  →        1.13 s    (+6.08%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.55 ms →        7.25 ms   (-4.06%) |    1.65 K →    1.70 K   (+2.90%) |       12.49 s  →       12.33 s    (-1.28%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       20.55 ms →       29.03 ms  (+41.24%) |     827   →     851     (+2.90%) |       17.00 s  →       24.70 s   (+45.34%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.27 ms                             |    1.55 K                        |        3.51 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.82 μs                             |    1.70 K                        |       55.86 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.94 ms            |                1.61 K            |                         3.12 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       129.74 ns            |                1.61 K            |                       208.36 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.94 ms            |                1.61 K            |                         3.11 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       237.63 ns            |                1.61 K            |                       381.63 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      976.51 μs →      967.33 μs   (-0.94%) |     827   →     851     (+2.90%) |      807.57 ms →      823.20 ms   (+1.93%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.55 ms →        1.51 ms   (-2.56%) |     827   →     851     (+2.90%) |        1.28 s  →        1.29 s    (+0.26%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.08 ms                             |    3.20 K                        |        9.84 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.75 μs                             |    3.20 K                        |       44.01 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      158.93 μs                             |    3.20 K                        |      508.58 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.14 μs                             |    4.64 K                        |       47.02 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.49 ms            |                3.31 K            |                        18.15 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.73 ms            |                4.82 K            |                        17.99 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.11 ms →        5.40 ms  (-11.53%) |     827   →     851     (+2.90%) |        5.05 s  →        4.60 s    (-8.96%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.26 ms                             |     827                          |        3.52 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.72 μs                             |    1.02 K                        |       28.22 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.60 ms            |                 851              |                         3.07 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       123.20 ns            |                 851              |                       104.84 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.59 ms            |                 851              |                         3.06 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       244.31 ns            |                 851              |                       207.91 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      718.73 ms →      139.87 ms  (-80.54%) |     827   →     851     (+2.90%) |      594.39 s  →      119.03 s   (-79.97%) | 
  │ │ │ │   ├ sirius::residuals                                         |        8.06 ms →        7.68 ms   (-4.64%) |     814   →     839     (+3.07%) |        6.56 s  →        6.45 s    (-1.71%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.35 ms                             |     752                          |        5.53 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       24.78 μs                             |     752                          |       18.63 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      274.99 μs                             |     752                          |      206.79 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       15.34 μs                             |    1.50 K                        |       23.07 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         7.28 ms            |                 755              |                         5.50 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.62 ms            |                1.51 K            |                         5.46 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      889.13 μs →      551.58 μs  (-37.96%) |     752   →     755     (+0.40%) |      668.63 ms →      416.45 ms  (-37.72%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       21.89 ms →       36.18 ms  (+65.27%) |     116   →     321   (+176.72%) |        2.54 s  →       11.61 s  (+357.35%) | 
  │ │ │ │     ├ sddk::transform                                         |       20.41 ms                             |     124                          |        2.53 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       26.57 μs                             |     124                          |        3.29 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.51 ms                             |     124                          |      187.72 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       20.13 μs                             |     132                          |        2.66 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        21.10 ms            |                 546              |                        11.52 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        14.85 ms            |                 771              |                        11.45 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      524.61 ns →      485.79 ns   (-7.40%) |     108   →      96    (-11.11%) |       56.66 μs →       46.64 μs  (-17.69%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.28 μs →        3.57 ms (+15917.19%) |      27   →      24    (-11.11%) |      601.56 μs →       85.65 ms (+14137.50%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      613.33 μs →       58.56 ms (+9447.81%) |      27   →      24    (-11.11%) |       16.56 ms →        1.41 s  (+8386.94%) | 
+ │ │ ├ sirius::Density::generate                                       |      905.18 ms →      904.04 ms   (-0.13%) |      27   →      24    (-11.11%) |       24.44 s  →       21.70 s   (-11.22%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      523.71 ms →      554.31 ms   (+5.84%) |      27   →      24    (-11.11%) |       14.14 s  →       13.30 s    (-5.92%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.43 ms →       23.88 ms   (-2.27%) |     108   →      96    (-11.11%) |        2.64 s  →        2.29 s   (-13.13%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        7.96 μs →        4.55 μs  (-42.89%) |     108   →      96    (-11.11%) |      859.61 μs →      436.36 μs  (-49.24%) | 
+ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.18 μs →       10.67 μs  (-24.74%) |       8   →       8              |      113.44 μs →       85.37 μs  (-24.74%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.37 ms →       19.75 ms   (-3.07%) |     108   →      96    (-11.11%) |        2.20 s  →        1.90 s   (-13.84%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.70 ms →       36.86 ms  (+24.10%) |     108   →      96    (-11.11%) |        3.21 s  →        3.54 s   (+10.31%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        8.87 μs →        9.45 μs   (+6.52%) |     108   →      96    (-11.11%) |      958.38 μs →      907.46 μs   (-5.31%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (+0.17%) |     108   →      96    (-11.11%) |      156.64 ms →      139.47 ms  (-10.96%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.77 ms →       28.14 ms   (+1.32%) |     108   →      96    (-11.11%) |        3.00 s  →        2.70 s    (-9.94%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.57 ms →        4.05 ms  (+13.50%) |     108   →      96    (-11.11%) |      385.54 ms →      388.96 ms   (+0.89%) | 
! │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      628.65 ns →      668.48 ns   (+6.34%) |     108   →      96    (-11.11%) |       67.89 μs →       64.17 μs   (-5.48%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.57 ms →       42.79 ms   (+0.53%) |     108   →      96    (-11.11%) |        4.60 s  →        4.11 s   (-10.64%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.71%) |      27   →      24    (-11.11%) |       44.27 ms →       39.63 ms  (-10.48%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.32 ms →       89.02 ms   (+0.79%) |      27   →      24    (-11.11%) |        2.38 s  →        2.14 s   (-10.41%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.09 ms →       88.77 ms   (+0.77%) |      27   →      24    (-11.11%) |        2.38 s  →        2.13 s   (-10.43%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      288.77 ms →      258.20 ms  (-10.59%) |      27   →      24    (-11.11%) |        7.80 s  →        6.20 s   (-20.52%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      288.77 ms →      258.19 ms  (-10.59%) |      27   →      24    (-11.11%) |        7.80 s  →        6.20 s   (-20.52%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.23 ms →       24.90 ms  (-11.80%) |      27   →      24    (-11.11%) |      762.26 ms →      597.58 ms  (-21.60%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      231.24 ms →      207.58 ms  (-10.23%) |      27   →      24    (-11.11%) |        6.24 s  →        4.98 s   (-20.21%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.48 ms →       24.45 ms  (-11.05%) |      27   →      24    (-11.11%) |      742.07 ms →      586.73 ms  (-20.93%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.36 ms →       81.29 ms   (-1.30%) |      27   →      24    (-11.11%) |        2.22 s  →        1.95 s   (-12.27%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.78 ms →        6.58 ms   (-2.87%) |      27   →      24    (-11.11%) |      182.94 ms →      157.95 ms  (-13.66%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                        10.72 ms            |                 216              |                         2.32 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                        10.26 ms            |                 216              |                         2.22 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                        10.26 ms            |                 216              |                         2.22 s             | 
+ │ │ ├ sirius::Density::mix                                            |      225.19 ms →      153.72 ms  (-31.74%) |      27   →      24    (-11.11%) |        6.08 s  →        3.69 s   (-39.32%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      974.99 μs →        1.10 ms  (+13.00%) |      27   →      24    (-11.11%) |       26.32 ms →       26.44 ms   (+0.45%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.04 ms →       10.18 ms   (-7.76%) |     349   →     304    (-12.89%) |        3.85 s  →        3.10 s   (-19.65%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.86 ms →        9.80 ms   (-9.75%) |     349   →     304    (-12.89%) |        3.79 s  →        2.98 s   (-21.39%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.86 ms →        9.80 ms   (-9.75%) |     349   →     304    (-12.89%) |        3.79 s  →        2.98 s   (-21.39%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.97 ms →        6.23 ms  (-10.66%) |      27   →      24    (-11.11%) |      188.20 ms →      149.45 ms  (-20.59%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.12 ms →        5.17 ms  (-15.51%) |      27   →      24    (-11.11%) |      165.30 ms →      124.13 ms  (-24.90%) | 
+ │ │ ├ sirius::Potential::generate                                     |      571.89 ms →      545.44 ms   (-4.62%) |      27   →      24    (-11.11%) |       15.44 s  →       13.09 s   (-15.22%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      139.19 ms →      126.12 ms   (-9.39%) |      27   →      24    (-11.11%) |        3.76 s  →        3.03 s   (-19.46%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.83 ms →        7.34 ms  (-60.99%) |      27   →      24    (-11.11%) |      508.38 ms →      176.28 ms  (-65.33%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |       10.58 ms →       11.03 ms   (+4.18%) |      27   →      24    (-11.11%) |      285.76 ms →      264.63 ms   (-7.39%) | 
! │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.34 ms →       10.68 ms   (+3.29%) |      27   →      24    (-11.11%) |      279.07 ms →      256.23 ms   (-8.18%) | 
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.34 ms →       10.68 ms   (+3.29%) |      27   →      24    (-11.11%) |      279.05 ms →      256.21 ms   (-8.18%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      546.77 μs →      463.19 μs  (-15.29%) |      54   →      48    (-11.11%) |       29.53 ms →       22.23 ms  (-24.70%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       46.41 ms →       27.70 ms  (-40.31%) |      27   →      24    (-11.11%) |        1.25 s  →      664.89 ms  (-46.94%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.41 ms →       25.30 ms  (-45.48%) |      27   →      24    (-11.11%) |        1.25 s  →      607.24 ms  (-51.54%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.99 ms →        1.21 ms  (-59.53%) |      54   →      24    (-55.56%) |      161.61 ms →       29.07 ms  (-82.01%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        5.42 ms                             |      27                          |      146.37 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                         8.44 ms            |                  48              |                       404.96 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.77 ms →        4.79 ms  (-29.21%) |      27   →      24    (-11.11%) |      182.73 ms →      114.99 ms  (-37.07%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.86 ms →       90.95 ms   (+0.10%) |      27   →      24    (-11.11%) |        2.45 s  →        2.18 s   (-11.02%) | 
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.29 ms →      293.63 ms   (+2.56%) |      27   →      24    (-11.11%) |        7.73 s  →        7.05 s    (-8.83%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      289.48 ms →      255.22 ms  (-11.84%) |      27   →      24    (-11.11%) |        7.82 s  →        6.13 s   (-21.63%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      289.48 ms →      255.21 ms  (-11.84%) |      27   →      24    (-11.11%) |        7.82 s  →        6.13 s   (-21.63%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       31.10 ms →       23.53 ms  (-24.33%) |      27   →      24    (-11.11%) |      839.66 ms →      564.79 ms  (-32.74%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.14 ms →      207.65 ms   (-8.58%) |      27   →      24    (-11.11%) |        6.13 s  →        4.98 s   (-18.74%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.49 ms →       22.88 ms  (-16.79%) |      27   →      24    (-11.11%) |      742.31 ms →      549.04 ms  (-26.04%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.55 ms →        5.59 ms   (+0.67%) |      27   →      24    (-11.11%) |      149.92 ms →      134.16 ms  (-10.51%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.71 ms                             |     189                          |        2.03 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.37 ms                             |     189                          |        1.96 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.37 ms                             |     189                          |        1.96 s                              | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.27 ms →       10.47 ms   (+1.99%) |      81   →      72    (-11.11%) |      831.57 ms →      753.85 ms   (-9.35%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.84 ms →       10.13 ms   (+3.02%) |      81   →      72    (-11.11%) |      796.75 ms →      729.60 ms   (-8.43%) | 
! │ │ ├ sirius::Periodic_function::integrate                            |        9.88 ms →       10.11 ms   (+2.34%) |      27   →      24    (-11.11%) |      266.85 ms →      242.75 ms   (-9.03%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      109.64 μs →       14.95 ms (+13536.88%) |      27   →      24    (-11.11%) |        2.96 ms →      358.84 ms (+12021.67%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      103.65 μs →       14.95 ms (+14318.32%) |      27   →      24    (-11.11%) |        2.80 ms →      358.68 ms (+12716.29%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.16 ms →        4.85 ms   (-5.98%) |       2   →       2              |       10.32 ms →        9.70 ms   (-5.98%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.44 ms →       10.53 ms   (+0.83%) |       6   →       6              |       62.64 ms →       63.16 ms   (+0.83%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.43 ms →       10.09 ms   (-3.32%) |       6   →       6              |       62.59 ms →       60.52 ms   (-3.32%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.43 ms →       10.09 ms   (-3.32%) |       6   →       6              |       62.59 ms →       60.51 ms   (-3.32%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.96 ms →       10.42 ms   (+4.67%) |       3   →       3              |       29.87 ms →       31.27 ms   (+4.67%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.95 ms →       10.09 ms   (+1.42%) |       3   →       3              |       29.85 ms →       30.28 ms   (+1.42%) | 
  ├ sirius::Periodic_function|inner                                     |       10.20 ms →       10.46 ms   (+2.55%) |       2   →       2              |       20.39 ms →       20.91 ms   (+2.55%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.05 ms →       10.13 ms   (+0.77%) |       2   →       2              |       20.10 ms →       20.25 ms   (+0.77%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.05 ms →       10.13 ms   (+0.77%) |       2   →       2              |       20.10 ms →       20.25 ms   (+0.77%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.64 ms →       10.43 ms   (+8.20%) |       1   →       1              |        9.64 ms →       10.43 ms   (+8.20%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.60 ms →       10.02 ms   (+4.44%) |       1   →       1              |        9.60 ms →       10.02 ms   (+4.44%) | 
+ └ sirius::finalize                                                    |      404.66 ms →      359.23 ms  (-11.23%) |       1   →       1              |      404.66 ms →      359.23 ms  (-11.23%) | 
  ====================================================================================================================================================================================================
```
