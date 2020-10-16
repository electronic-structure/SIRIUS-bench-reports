# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      285.38 s  →      220.84 s   (-22.62%) |       1   →       1              |      285.38 s  →      220.84 s   (-22.62%) | 
  ├ sirius::initialize                                                  |        2.67 s  →        2.69 s    (+0.68%) |       1   →       1              |        2.67 s  →        2.69 s    (+0.68%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        2.92 s    (-1.69%) |       1   →       1              |        2.97 s  →        2.92 s    (-1.69%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       23.63 ms →       22.31 ms   (-5.59%) |       1   →       1              |       23.63 ms →       22.31 ms   (-5.59%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      188.76 ms →      157.54 ms  (-16.54%) |       1   →       1              |      188.76 ms →      157.54 ms  (-16.54%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       83.09 ms →       66.61 ms  (-19.84%) |       2   →       2              |      166.19 ms →      133.21 ms  (-19.84%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.49 ms →       24.24 ms   (+7.78%) |       1   →       1              |       22.49 ms →       24.24 ms   (+7.78%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.43 ms →        6.43 ms   (+0.00%) |       1   →       1              |        6.43 ms →        6.43 ms   (+0.00%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       16.02 ms →       17.77 ms  (+10.91%) |       1   →       1              |       16.02 ms →       17.77 ms  (+10.91%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       16.00 ms →       17.75 ms  (+10.93%) |       1   →       1              |       16.00 ms →       17.75 ms  (+10.93%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.17 ms   (+0.71%) |       1   →       1              |        4.14 ms →        4.17 ms   (+0.71%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.64%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.64%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.23 μs →      102.73 μs   (-3.30%) |       1   →       1              |      106.23 μs →      102.73 μs   (-3.30%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.69 s    (-0.72%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.72%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.80 ms →       10.90 ms   (+0.89%) |       1   →       1              |       10.80 ms →       10.90 ms   (+0.89%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.44 ms   (+0.32%) |       1   →       1              |        4.43 ms →        4.44 ms   (+0.32%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.33 ms →        6.42 ms   (+1.33%) |       1   →       1              |        6.33 ms →        6.42 ms   (+1.33%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.31 ms →        6.40 ms   (+1.37%) |       1   →       1              |        6.31 ms →        6.40 ms   (+1.37%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.90 ms   (+1.95%) |       1   →       1              |        3.83 ms →        3.90 ms   (+1.95%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.80%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.80%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      106.34 μs →       99.40 μs   (-6.53%) |       1   →       1              |      106.34 μs →       99.40 μs   (-6.53%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |       78.13 ms →       62.58 ms  (-19.90%) |       2   →       2              |      156.25 ms →      125.15 ms  (-19.90%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.19 ms →        5.15 ms   (-0.91%) |       2   →       2              |       10.39 ms →       10.29 ms   (-0.91%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.64 ms →        4.47 ms   (-3.68%) |       1   →       1              |        4.64 ms →        4.47 ms   (-3.68%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.52 ms →       21.74 ms   (-3.43%) |       2   →       2              |       45.03 ms →       43.49 ms   (-3.43%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.32 ms →       14.81 ms   (-3.30%) |       2   →       2              |       30.64 ms →       29.63 ms   (-3.30%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.59 ms →       19.86 ms   (+1.36%) |       4   →       4              |       78.38 ms →       79.44 ms   (+1.36%) | 
  │   ├ sddk::Gvec::init                                                |      171.95 ms →      178.93 ms   (+4.06%) |       2   →       2              |      343.90 ms →      357.86 ms   (+4.06%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.27 ms →      135.54 ms   (+4.85%) |       2   →       2              |      258.54 ms →      271.08 ms   (+4.85%) | 
  │   ├ sddk::Gvec_shells                                               |      172.18 ms →      169.77 ms   (-1.40%) |       1   →       1              |      172.18 ms →      169.77 ms   (-1.40%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.33 ms   (+1.06%) |       1   →       1              |        1.31 ms →        1.33 ms   (+1.06%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.61 ms →      297.90 ms   (+0.78%) |       2   →       2              |      591.22 ms →      595.81 ms   (+0.78%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       77.88 ms →       77.91 ms   (+0.04%) |       1   →       1              |       77.88 ms →       77.91 ms   (+0.04%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.80 μs →        1.91 μs  (-31.86%) |       4   →       4              |       11.19 μs →        7.63 μs  (-31.86%) | 
  │ └ sirius::K_point_set::initialize                                   |       77.78 ms →       77.81 ms   (+0.04%) |       1   →       1              |       77.78 ms →       77.81 ms   (+0.04%) | 
  │   └ sirius::K_point::initialize                                     |       19.43 ms →       19.43 ms   (-0.01%) |       4   →       4              |       77.73 ms →       77.73 ms   (-0.01%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.76 ms →       14.85 ms   (+0.56%) |       4   →       4              |       59.06 ms →       59.39 ms   (+0.56%) | 
  │     │ └ sddk::Gvec::init                                            |        3.92 ms →        3.86 ms   (-1.54%) |       4   →       4              |       15.66 ms →       15.42 ms   (-1.54%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.11 μs →        8.46 μs   (-7.19%) |       4   →       4              |       36.44 μs →       33.82 μs   (-7.19%) | 
  │     └ sirius::K_point::update                                       |        3.35 ms →        3.27 ms   (-2.56%) |       4   →       4              |       13.41 ms →       13.07 ms   (-2.56%) | 
  │       └ sirius::Beta_projectors                                     |        1.78 ms →        1.79 ms   (+0.51%) |       4   →       4              |        7.13 ms →        7.16 ms   (+0.51%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      920.36 μs →      935.35 μs   (+1.63%) |       4   →       4              |        3.68 ms →        3.74 ms   (+1.63%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.33 ms →        5.28 ms   (-0.92%) |       2   →       2              |       10.67 ms →       10.57 ms   (-0.92%) | 
  ├ sirius::Potential                                                   |      160.41 ms →      156.11 ms   (-2.68%) |       1   →       1              |      160.41 ms →      156.11 ms   (-2.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.75 ms   (-1.07%) |       6   →       6              |       34.86 ms →       34.48 ms   (-1.07%) | 
  │ └ sirius::Potential::update                                         |      124.81 ms →      120.92 ms   (-3.11%) |       1   →       1              |      124.81 ms →      120.92 ms   (-3.11%) | 
  │   └ sirius::Potential::generate_local_potential                     |      124.05 ms →      120.21 ms   (-3.09%) |       1   →       1              |      124.05 ms →      120.21 ms   (-3.09%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.42 ms →      111.34 ms   (-0.07%) |       1   →       1              |      111.42 ms →      111.34 ms   (-0.07%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.73 ms →        8.01 ms  (-31.66%) |       1   →       1              |       11.73 ms →        8.01 ms  (-31.66%) | 
  ├ sirius::Density                                                     |      134.10 ms →      129.44 ms   (-3.48%) |       1   →       1              |      134.10 ms →      129.44 ms   (-3.48%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.26 ms →        5.19 ms   (-1.28%) |       2   →       2              |       10.52 ms →       10.39 ms   (-1.28%) | 
  │ └ sirius::Density::update                                           |      123.25 ms →      118.78 ms   (-3.63%) |       1   →       1              |      123.25 ms →      118.78 ms   (-3.63%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      122.83 ms →      118.37 ms   (-3.63%) |       1   →       1              |      122.83 ms →      118.37 ms   (-3.63%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      103.82 μs →      101.95 μs   (-1.80%) |       1   →       1              |      103.82 μs →      101.95 μs   (-1.80%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.62 ms →      112.72 ms   (+0.08%) |       1   →       1              |      112.62 ms →      112.72 ms   (+0.08%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.64 ms →        5.12 ms  (-46.90%) |       1   →       1              |        9.64 ms →        5.12 ms  (-46.90%) | 
  ├ sirius::Density::initial_density                                    |      174.56 ms →      163.38 ms   (-6.41%) |       1   →       1              |      174.56 ms →      163.38 ms   (-6.41%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.58 ms →      110.20 ms   (-1.24%) |       1   →       1              |      111.58 ms →      110.20 ms   (-1.24%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.44 ms →        5.47 ms  (-47.65%) |       2   →       2              |       20.88 ms →       10.93 ms  (-47.65%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.80 ms →        9.86 ms   (+0.53%) |       1   →       1              |        9.80 ms →        9.86 ms   (+0.53%) | 
  ├ sirius::Potential::generate                                         |      593.84 ms →      581.09 ms   (-2.15%) |       1   →       1              |      593.84 ms →      581.09 ms   (-2.15%) | 
  │ ├ sirius::Potential::poisson                                        |      136.29 ms →      126.51 ms   (-7.18%) |       1   →       1              |      136.29 ms →      126.51 ms   (-7.18%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       15.81 ms →        5.34 ms  (-66.24%) |       1   →       1              |       15.81 ms →        5.34 ms  (-66.24%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.20 ms →       10.63 ms   (+4.17%) |       1   →       1              |       10.20 ms →       10.63 ms   (+4.17%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.87 ms   (-0.02%) |       1   →       1              |        9.88 ms →        9.87 ms   (-0.02%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.87 ms   (-0.02%) |       1   →       1              |        9.88 ms →        9.87 ms   (-0.02%) | 
  │ ├ sirius::Periodic_function::add                                    |      546.09 μs →      557.20 μs   (+2.03%) |       2   →       2              |        1.09 ms →        1.11 ms   (+2.03%) | 
  │ ├ sirius::Potential::xc                                             |       54.96 ms →       54.24 ms   (-1.31%) |       1   →       1              |       54.96 ms →       54.24 ms   (-1.31%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.61 ms →       51.98 ms   (-1.19%) |       1   →       1              |       52.61 ms →       51.98 ms   (-1.19%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.63 ms →        5.65 ms   (+0.19%) |       2   →       2              |       11.27 ms →       11.29 ms   (+0.19%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.83 ms →        5.37 ms   (-7.97%) |       1   →       1              |        5.83 ms →        5.37 ms   (-7.97%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.18 ms →        5.97 ms   (-3.35%) |       1   →       1              |        6.18 ms →        5.97 ms   (-3.35%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.08 ms →       92.57 ms   (-0.55%) |       1   →       1              |       93.08 ms →       92.57 ms   (-0.55%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.88 ms →      299.36 ms   (-0.51%) |       1   →       1              |      300.88 ms →      299.36 ms   (-0.51%) | 
  ├ sirius::Hamiltonian0                                                |        8.80 ms →        8.32 ms   (-5.47%) |       1   →       1              |        8.80 ms →        8.32 ms   (-5.47%) | 
  │ ├ sirius::Local_operator                                            |        8.46 ms →        7.98 ms   (-5.65%) |       1   →       1              |        8.46 ms →        7.98 ms   (-5.65%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.72 ms   (-0.51%) |       1   →       1              |        4.75 ms →        4.72 ms   (-0.51%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.79 ms →        2.34 ms  (-15.97%) |       1   →       1              |        2.79 ms →        2.34 ms  (-15.97%) | 
  │ ├ sirius::Non_local_operator                                        |       63.16 μs →       63.49 μs   (+0.52%) |       2   →       2              |      126.31 μs →      126.97 μs   (+0.52%) | 
  │ ├ sirius::D_operator::initialize                                    |       93.68 μs →       93.70 μs   (+0.02%) |       1   →       1              |       93.68 μs →       93.70 μs   (+0.02%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.77 μs →       68.63 μs   (-1.63%) |       1   →       1              |       69.77 μs →       68.63 μs   (-1.63%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.42 s  →        3.09 s    (-9.69%) |       1   →       1              |        3.42 s  →        3.09 s    (-9.69%) | 
- │ ├ sirius::Hamiltonian_k                                             |      365.34 μs →      629.98 μs  (+72.44%) |       4   →       4              |        1.46 ms →        2.52 ms  (+72.44%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      360.50 μs →      625.03 μs  (+73.38%) |       4   →       4              |        1.44 ms →        2.50 ms  (+73.38%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.14 μs →        3.24 μs   (+3.13%) |       4   →       4              |       12.56 μs →       12.96 μs   (+3.13%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      854.91 ms →      771.80 ms   (-9.72%) |       4   →       4              |        3.42 s  →        3.09 s    (-9.72%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.89 ms →       33.08 ms   (+0.59%) |      16   →      16              |      526.20 ms →      529.31 ms   (+0.59%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.46 ms →       14.63 ms   (+1.18%) |       4   →       4              |       57.84 ms →       58.53 ms   (+1.18%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.31 ms →        5.45 ms   (+2.58%) |       4   →       4              |       21.24 ms →       21.79 ms   (+2.58%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      386.54 ms →      353.91 ms   (-8.44%) |       4   →       4              |        1.55 s  →        1.42 s    (-8.44%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      275.49 ms →      257.49 ms   (-6.53%) |       4   →       4              |        1.10 s  →        1.03 s    (-6.53%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       73.57 ms →       63.06 ms  (-14.28%) |       4   →       4              |      294.27 ms →      252.23 ms  (-14.28%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.72 ms →       16.83 ms   (+0.68%) |       4   →       4              |       66.87 ms →       67.33 ms   (+0.68%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.72 ms →       16.83 ms   (+0.67%) |       4   →       4              |       66.86 ms →       67.32 ms   (+0.67%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       50.32 ms →       39.84 ms  (-20.82%) |       4   →       4              |      201.30 ms →      159.38 ms  (-20.82%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       17.98 ms →       16.50 ms   (-8.22%) |       4   →       4              |       71.93 ms →       66.02 ms   (-8.22%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       17.98 ms →       16.50 ms   (-8.22%) |       4   →       4              |       71.91 ms →       66.01 ms   (-8.22%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       59.88 ms →       52.92 ms  (-11.63%) |       4   →       4              |      239.54 ms →      211.68 ms  (-11.63%) | 
+ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       41.85 ms →       34.93 ms  (-16.54%) |       4   →       4              |      167.40 ms →      139.71 ms  (-16.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.96 ms →        1.94 ms   (-0.66%) |       4   →       4              |        7.83 ms →        7.78 ms   (-0.66%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       54.88 ms →       40.15 ms  (-26.85%) |       4   →       4              |      219.53 ms →      160.59 ms  (-26.85%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       21.71 ms →        7.05 ms  (-67.55%) |       4   →       4              |       86.86 ms →       28.18 ms  (-67.55%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.08 ms →       27.14 ms   (+0.22%) |       8   →       8              |      216.68 ms →      217.15 ms   (+0.22%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       18.53 ms →       15.02 ms  (-18.95%) |       8   →       8              |      148.27 ms →      120.17 ms  (-18.95%) | 
+ │ │ │ └ sddk::wf_inner                                                |       18.49 ms →       14.98 ms  (-19.00%) |       8   →       8              |      147.93 ms →      119.83 ms  (-19.00%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       31.38 ns →       23.88 ns  (-23.90%) |       8   →       8              |      251.00 ns →      191.00 ns  (-23.90%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       18.28 ms →       14.80 ms  (-19.04%) |       8   →       8              |      146.22 ms →      118.39 ms  (-19.04%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       43.62 ns  (+93.89%) |       8   →       8              |      180.00 ns →      349.00 ns  (+93.89%) | 
+ │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      160.94 ms →      118.52 ms  (-26.35%) |       4   →       4              |      643.74 ms →      474.09 ms  (-26.35%) | 
  │ │ └ sddk::wf_trans                                                  |       24.34 ms →       23.54 ms   (-3.30%) |       4   →       4              |       97.36 ms →       94.15 ms   (-3.30%) | 
  │ │   └ sddk::wf_trans|pw                                             |       24.01 ms →       23.38 ms   (-2.64%) |       4   →       4              |       96.03 ms →       93.50 ms   (-2.64%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      518.25 ns →      360.50 ns  (-30.44%) |       4   →       4              |        2.07 μs →        1.44 μs  (-30.44%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      274.23 s  →      210.16 s   (-23.36%) |       1   →       1              |      274.23 s  →      210.16 s   (-23.36%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.75 ms   (-0.36%) |      19   →      19              |      109.73 ms →      109.33 ms   (-0.36%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       10.53 s  →        7.77 s   (-26.24%) |      26   →      27     (+3.85%) |      273.80 s  →      209.73 s   (-23.40%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.28 ms →        4.46 ms  (-15.50%) |      26   →      27     (+3.85%) |      137.34 ms →      120.51 ms  (-12.25%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.92 ms →        4.10 ms  (-16.68%) |      26   →      27     (+3.85%) |      128.05 ms →      110.79 ms  (-13.48%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      954.00 μs →      974.84 μs   (+2.18%) |      26   →      27     (+3.85%) |       24.80 ms →       26.32 ms   (+6.11%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.08 ms →        2.24 ms  (-27.31%) |      26   →      27     (+3.85%) |       80.14 ms →       60.50 ms  (-24.51%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.68 μs →       64.82 μs   (+0.21%) |      52   →      54     (+3.85%) |        3.36 ms →        3.50 ms   (+4.06%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.77 μs →       95.58 μs   (+1.93%) |      26   →      27     (+3.85%) |        2.44 ms →        2.58 ms   (+5.85%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.60 μs →       66.19 μs   (-0.62%) |      26   →      27     (+3.85%) |        1.73 ms →        1.79 ms   (+3.21%) | 
+ │ │ ├ sirius::Band::solve                                             |        8.37 s  →        5.68 s   (-32.11%) |      26   →      27     (+3.85%) |      217.72 s  →      153.49 s   (-29.50%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      346.85 μs →      325.25 μs   (-6.23%) |     104   →     108     (+3.85%) |       36.07 ms →       35.13 ms   (-2.62%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      341.21 μs →      319.61 μs   (-6.33%) |     104   →     108     (+3.85%) |       35.49 ms →       34.52 ms   (-2.73%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.06 μs →        4.11 μs   (+1.19%) |     104   →     108     (+3.85%) |      421.92 μs →      443.38 μs   (+5.09%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.09 s  →        1.42 s   (-32.12%) |     104   →     108     (+3.85%) |      217.68 s  →      153.45 s   (-29.51%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.15 ms →       12.16 ms   (+0.03%) |     104   →     108     (+3.85%) |        1.26 s  →        1.31 s    (+3.87%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      708.04 ns →      695.62 ns   (-1.75%) |     624   →     648     (+3.85%) |      441.82 μs →      450.76 μs   (+2.02%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (+0.28%) |     104   →     108     (+3.85%) |      189.92 ms →      197.77 ms   (+4.13%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.24 μs →      354.81 μs   (-0.12%) |     104   →     108     (+3.85%) |       36.95 ms →       38.32 ms   (+3.72%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      546.60 μs →      550.00 μs   (+0.62%) |     208   →     216     (+3.85%) |      113.69 ms →      118.80 ms   (+4.49%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.07 s  →        1.40 s   (-32.48%) |     104   →     108     (+3.85%) |      215.29 s  →      150.96 s   (-29.88%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       73.13 ms →       68.20 ms   (-6.74%) |     932   →     974     (+4.51%) |       68.16 s  →       66.43 s    (-2.54%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       46.32 ms →       43.58 ms   (-5.91%) |     932   →     974     (+4.51%) |       43.17 s  →       42.45 s    (-1.67%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        9.85 ms →        8.58 ms  (-12.90%) |     932   →     974     (+4.51%) |        9.18 s  →        8.35 s    (-8.98%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      228.73 μs →      215.14 μs   (-5.94%) |     932   →     974     (+4.51%) |      213.18 ms →      209.55 ms   (-1.70%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.03 ms →        1.92 ms   (-5.36%) |     104   →     108     (+3.85%) |      211.36 ms →      207.73 ms   (-1.72%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        8.08 ms →        6.64 ms  (-17.80%) |     932   →     974     (+4.51%) |        7.53 s  →        6.47 s   (-14.09%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       88.80 μs →       82.69 μs   (-6.88%) |     932   →     974     (+4.51%) |       82.76 ms →       80.54 ms   (-2.68%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      772.20 μs →      722.38 μs   (-6.45%) |     104   →     108     (+3.85%) |       80.31 ms →       78.02 ms   (-2.85%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       11.08 ms →        9.61 ms  (-13.24%) |     932   →     974     (+4.51%) |       10.32 s  →        9.36 s    (-9.33%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        7.53 ms →        6.08 ms  (-19.34%) |     932   →     974     (+4.51%) |        7.02 s  →        5.92 s   (-15.71%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.51 ms   (-0.10%) |     932   →     974     (+4.51%) |        1.41 s  →        1.48 s    (+4.40%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       10.67 ms →        8.36 ms  (-21.66%) |     932   →     974     (+4.51%) |        9.94 s  →        8.14 s   (-18.13%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        3.49 ms →        1.20 ms  (-65.60%) |     932   →     974     (+4.51%) |        3.25 s  →        1.17 s   (-64.04%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.30 ms →        7.36 ms   (+0.81%) |    1.86 K →    1.95 K   (+4.51%) |       13.61 s  →       14.34 s    (+5.36%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       30.68 ms →       26.35 ms  (-14.13%) |     932   →     974     (+4.51%) |       28.60 s  →       25.66 s   (-10.26%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        2.58 ms →        1.88 ms  (-27.02%) |    1.76 K →    1.84 K   (+4.55%) |        4.54 s  →        3.46 s   (-23.70%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       80.32 ns →       84.61 ns   (+5.34%) |    1.76 K →    1.84 K   (+4.55%) |      141.36 μs →      155.69 μs  (+10.13%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.56 ms →        1.88 ms  (-26.61%) |    1.76 K →    1.84 K   (+4.55%) |        4.50 s  →        3.45 s   (-23.28%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       67.81 ns →       65.70 ns   (-3.11%) |    1.76 K →    1.84 K   (+4.55%) |      119.34 μs →      120.89 μs   (+1.30%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      950.35 μs →      777.20 μs  (-18.22%) |     932   →     974     (+4.51%) |      885.72 ms →      756.99 ms  (-14.53%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.22 ms →      737.35 μs  (-39.64%) |     932   →     974     (+4.51%) |        1.14 s  →      718.18 ms  (-36.92%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |        5.68 ms →        5.07 ms  (-10.63%) |    3.62 K →    3.79 K   (+4.53%) |       20.58 s  →       19.22 s    (-6.58%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.84 ms →        3.45 ms   (-9.97%) |    5.28 K →    5.52 K   (+4.55%) |       20.26 s  →       19.07 s    (-5.88%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.17 ms →        5.18 ms  (-16.00%) |     932   →     974     (+4.51%) |        5.75 s  →        5.05 s   (-12.21%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        4.52 ms →        3.44 ms  (-23.96%) |     932   →     974     (+4.51%) |        4.22 s  →        3.35 s   (-20.54%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       69.28 ns →       56.70 ns  (-18.16%) |     932   →     974     (+4.51%) |       64.57 μs →       55.23 μs  (-14.47%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        4.49 ms →        3.43 ms  (-23.68%) |     932   →     974     (+4.51%) |        4.18 s  →        3.34 s   (-20.24%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       61.98 ns →       44.71 ns  (-27.86%) |     932   →     974     (+4.51%) |       57.76 μs →       43.55 μs  (-24.61%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       97.66 ms →       32.72 ms  (-66.50%) |     932   →     974     (+4.51%) |       91.02 s  →       31.87 s   (-64.99%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       11.71 ms →        9.69 ms  (-17.27%) |     907   →     946     (+4.30%) |       10.62 s  →        9.16 s   (-13.72%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       11.14 ms →        9.25 ms  (-16.91%) |     864   →     903     (+4.51%) |        9.62 s  →        8.36 s   (-13.15%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.48 ms →        4.60 ms  (-16.05%) |    1.73 K →    1.81 K   (+4.51%) |        9.47 s  →        8.31 s   (-12.26%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      682.45 μs →      624.75 μs   (-8.46%) |     864   →     903     (+4.51%) |      589.64 ms →      564.15 ms   (-4.32%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.16 ms →       36.68 ms  (-31.01%) |     209   →     348    (+66.51%) |       11.11 s  →       12.76 s   (+14.88%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       35.28 ms →       21.58 ms  (-38.82%) |     314   →     588    (+87.26%) |       11.08 s  →       12.69 s   (+14.57%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       26.21 ms →       15.24 ms  (-41.84%) |     419   →     828    (+97.61%) |       10.98 s  →       12.62 s   (+14.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      568.86 ns →      601.30 ns   (+5.70%) |     104   →     108     (+3.85%) |       59.16 μs →       64.94 μs   (+9.77%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.26 μs →       21.20 μs   (-4.78%) |      26   →      27     (+3.85%) |      578.88 μs →      572.43 μs   (-1.11%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      601.19 μs →      592.91 μs   (-1.38%) |      26   →      27     (+3.85%) |       15.63 ms →       16.01 ms   (+2.42%) | 
  │ │ ├ sirius::Density::generate                                       |      947.65 ms →      895.29 ms   (-5.53%) |      26   →      27     (+3.85%) |       24.64 s  →       24.17 s    (-1.89%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      568.94 ms →      523.39 ms   (-8.01%) |      26   →      27     (+3.85%) |       14.79 s  →       14.13 s    (-4.47%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       27.44 ms →       24.15 ms  (-12.01%) |     104   →     108     (+3.85%) |        2.85 s  →        2.61 s    (-8.63%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.37 μs →        9.17 μs   (+9.62%) |     104   →     108     (+3.85%) |      870.12 μs →      990.51 μs  (+13.84%) | 
- │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.44 μs →       16.76 μs  (+16.07%) |       8   →       8              |      115.52 μs →      134.09 μs  (+16.07%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       23.32 ms →       20.01 ms  (-14.20%) |     104   →     108     (+3.85%) |        2.43 s  →        2.16 s   (-10.90%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       36.60 ms →       29.61 ms  (-19.10%) |     104   →     108     (+3.85%) |        3.81 s  →        3.20 s   (-15.98%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.32 μs →        9.61 μs   (+3.08%) |     104   →     108     (+3.85%) |      969.30 μs →        1.04 ms   (+7.04%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (+0.08%) |     104   →     108     (+3.85%) |      150.93 ms →      156.86 ms   (+3.93%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       34.67 ms →       27.68 ms  (-20.15%) |     104   →     108     (+3.85%) |        3.61 s  →        2.99 s   (-17.08%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |       10.54 ms →        3.55 ms  (-66.30%) |     104   →     108     (+3.85%) |        1.10 s  →      383.54 ms  (-65.00%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      575.63 ns →      512.07 ns  (-11.04%) |     104   →     108     (+3.85%) |       59.87 μs →       55.30 μs   (-7.62%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.74 ms →       42.68 ms   (-0.12%) |     104   →     108     (+3.85%) |        4.44 s  →        4.61 s    (+3.72%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.43%) |      26   →      27     (+3.85%) |       42.58 ms →       44.41 ms   (+4.29%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.87 ms →       88.88 ms   (+0.01%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.86%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.63 ms →       88.65 ms   (+0.02%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.87%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      285.40 ms →      276.15 ms   (-3.24%) |      26   →      27     (+3.85%) |        7.42 s  →        7.46 s    (+0.48%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      285.40 ms →      276.15 ms   (-3.24%) |      26   →      27     (+3.85%) |        7.42 s  →        7.46 s    (+0.48%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       25.41 ms →       24.26 ms   (-4.51%) |      26   →      27     (+3.85%) |      660.64 ms →      655.08 ms   (-0.84%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      233.83 ms →      225.86 ms   (-3.41%) |      26   →      27     (+3.85%) |        6.08 s  →        6.10 s    (+0.31%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.39 ms →       24.25 ms   (-0.60%) |      26   →      27     (+3.85%) |      634.22 ms →      654.66 ms   (+3.22%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.78 ms →       80.74 ms   (-0.05%) |      26   →      27     (+3.85%) |        2.10 s  →        2.18 s    (+3.80%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.95 ms →       11.40 ms  (+27.44%) |      26   →      27     (+3.85%) |      232.63 ms →      307.87 ms  (+32.34%) | 
  │ │ ├ sirius::Density::mix                                            |      211.29 ms →      215.22 ms   (+1.86%) |      26   →      27     (+3.85%) |        5.49 s  →        5.81 s    (+5.78%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      912.07 μs →      928.71 μs   (+1.82%) |      26   →      27     (+3.85%) |       23.71 ms →       25.08 ms   (+5.74%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.71 ms →       10.33 ms   (-3.58%) |     320   →     349     (+9.06%) |        3.43 s  →        3.60 s    (+5.16%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms →        9.93 ms   (-4.52%) |     320   →     349     (+9.06%) |        3.33 s  →        3.47 s    (+4.14%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms →        9.93 ms   (-4.52%) |     320   →     349     (+9.06%) |        3.33 s  →        3.47 s    (+4.14%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        8.59 ms →        6.45 ms  (-24.89%) |      26   →      27     (+3.85%) |      223.41 ms →      174.25 ms  (-22.00%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.74 ms →        5.65 ms  (-27.03%) |      26   →      27     (+3.85%) |      201.14 ms →      152.42 ms  (-24.22%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.97 ms →      568.91 ms   (-2.08%) |      26   →      27     (+3.85%) |       15.11 s  →       15.36 s    (+1.69%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.68 ms →      126.60 ms   (-7.38%) |      26   →      27     (+3.85%) |        3.55 s  →        3.42 s    (-3.81%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.34 ms →        5.22 ms  (-68.08%) |      26   →      27     (+3.85%) |      424.95 ms →      140.84 ms  (-66.86%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.23 ms →       10.34 ms   (+1.08%) |      26   →      27     (+3.85%) |      266.02 ms →      279.22 ms   (+4.96%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.86 ms →        9.94 ms   (+0.80%) |      26   →      27     (+3.85%) |      256.48 ms →      268.48 ms   (+4.68%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.86 ms →        9.94 ms   (+0.80%) |      26   →      27     (+3.85%) |      256.47 ms →      268.46 ms   (+4.68%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      543.79 μs →      559.25 μs   (+2.84%) |      52   →      54     (+3.85%) |       28.28 ms →       30.20 ms   (+6.80%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       50.34 ms →       49.51 ms   (-1.65%) |      26   →      27     (+3.85%) |        1.31 s  →        1.34 s    (+2.13%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       48.00 ms →       47.18 ms   (-1.71%) |      26   →      27     (+3.85%) |        1.25 s  →        1.27 s    (+2.07%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.00 ms →        3.04 ms   (+1.36%) |      52   →      54     (+3.85%) |      155.77 ms →      163.97 ms   (+5.26%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        6.57 ms →        5.47 ms  (-16.79%) |      26   →      27     (+3.85%) |      170.87 ms →      147.65 ms  (-13.59%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.24 ms →        6.69 ms   (-7.69%) |      26   →      27     (+3.85%) |      188.32 ms →      180.52 ms   (-4.14%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.27 ms →       90.86 ms   (-0.45%) |      26   →      27     (+3.85%) |        2.37 s  →        2.45 s    (+3.38%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.07 ms →      292.83 ms   (-0.08%) |      26   →      27     (+3.85%) |        7.62 s  →        7.91 s    (+3.76%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      288.21 ms →      279.54 ms   (-3.01%) |      26   →      27     (+3.85%) |        7.49 s  →        7.55 s    (+0.72%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      288.20 ms →      279.53 ms   (-3.01%) |      26   →      27     (+3.85%) |        7.49 s  →        7.55 s    (+0.72%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.46 ms →       27.40 ms   (-0.24%) |      26   →      27     (+3.85%) |      713.96 ms →      739.67 ms   (+3.60%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      232.49 ms →      224.60 ms   (-3.39%) |      26   →      27     (+3.85%) |        6.04 s  →        6.06 s    (+0.32%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.46 ms →       23.74 ms   (-2.92%) |      26   →      27     (+3.85%) |      635.91 ms →      641.11 ms   (+0.82%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.49 ms →        5.60 ms  (-13.58%) |      26   →      27     (+3.85%) |      168.63 ms →      151.33 ms  (-10.26%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.43 ms →       10.20 ms   (-2.12%) |     182   →     189     (+3.85%) |        1.90 s  →        1.93 s    (+1.64%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.09 ms →        9.90 ms   (-1.87%) |     182   →     189     (+3.85%) |        1.84 s  →        1.87 s    (+1.91%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.09 ms →        9.90 ms   (-1.87%) |     182   →     189     (+3.85%) |        1.84 s  →        1.87 s    (+1.91%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.07 ms →       10.53 ms   (-4.88%) |      78   →      81     (+3.85%) |      863.54 ms →      852.98 ms   (-1.22%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.68 ms →       10.26 ms   (-3.94%) |      78   →      81     (+3.85%) |      832.96 ms →      830.93 ms   (-0.24%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.02 ms →        9.95 ms   (-0.67%) |      26   →      27     (+3.85%) |      260.45 ms →      268.66 ms   (+3.15%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      142.55 μs →      110.14 μs  (-22.73%) |      26   →      27     (+3.85%) |        3.71 ms →        2.97 ms  (-19.76%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      137.48 μs →      104.65 μs  (-23.88%) |      26   →      27     (+3.85%) |        3.57 ms →        2.83 ms  (-20.95%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.63 ms →        5.14 ms   (-8.57%) |       2   →       2              |       11.25 ms →       10.29 ms   (-8.57%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.08 ms →       10.29 ms   (+2.09%) |       6   →       6              |       60.49 ms →       61.75 ms   (+2.09%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.07 ms →       10.28 ms   (+2.08%) |       6   →       6              |       60.43 ms →       61.68 ms   (+2.08%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.07 ms →       10.28 ms   (+2.08%) |       6   →       6              |       60.43 ms →       61.68 ms   (+2.08%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.79 ms →       10.41 ms   (-3.52%) |       3   →       3              |       32.37 ms →       31.23 ms   (-3.52%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.78 ms →       10.40 ms   (-3.50%) |       3   →       3              |       32.34 ms →       31.21 ms   (-3.50%) | 
  ├ sirius::Periodic_function|inner                                     |        9.85 ms →        9.98 ms   (+1.26%) |       2   →       2              |       19.71 ms →       19.96 ms   (+1.26%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.82 ms →        9.97 ms   (+1.50%) |       2   →       2              |       19.64 ms →       19.94 ms   (+1.50%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.82 ms →        9.97 ms   (+1.50%) |       2   →       2              |       19.64 ms →       19.94 ms   (+1.50%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.57 ms →       10.43 ms   (-1.30%) |       1   →       1              |       10.57 ms →       10.43 ms   (-1.30%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.43 ms   (-0.39%) |       1   →       1              |       10.47 ms →       10.43 ms   (-0.39%) | 
  └ sirius::finalize                                                    |      318.11 ms →      309.14 ms   (-2.82%) |       1   →       1              |      318.11 ms →      309.14 ms   (-2.82%) | 
  ====================================================================================================================================================================================================
```
