# Benchmark 6f26e1b85d392e75fe8ae23eb64d38742c01496b vs 52d6cc62f84d89d2fdc84536db65e2617fd3b399
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      112.18 s  →      112.88 s    (+0.62%) |       1   →       1              |      112.18 s  →      112.88 s    (+0.62%) | 
  ├ sirius::initialize                                                  |        2.62 s  →        2.62 s    (+0.24%) |       1   →       1              |        2.62 s  →        2.62 s    (+0.24%) | 
  ├ sirius::Simulation_context::initialize                              |        2.12 s  →        2.09 s    (-1.59%) |       1   →       1              |        2.12 s  →        2.09 s    (-1.59%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       51.69 ms →        4.28 ms  (-91.72%) |       1   →       1              |       51.69 ms →        4.28 ms  (-91.72%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       93.61 ms →      103.73 ms  (+10.80%) |       1   →       1              |       93.61 ms →      103.73 ms  (+10.80%) | 
- │ │ ├ sirius::Atom_type::init                                         |       69.09 ms →       78.00 ms  (+12.90%) |       1   →       1              |       69.09 ms →       78.00 ms  (+12.90%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.47 ms →       25.66 ms   (+4.88%) |       1   →       1              |       24.47 ms →       25.66 ms   (+4.88%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.42 ms →       10.31 ms   (-1.06%) |       1   →       1              |       10.42 ms →       10.31 ms   (-1.06%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.02 ms →       15.33 ms   (+9.32%) |       1   →       1              |       14.02 ms →       15.33 ms   (+9.32%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.44 ms →       14.72 ms   (+9.53%) |       1   →       1              |       13.44 ms →       14.72 ms   (+9.53%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       13.21 ms →       14.50 ms   (+9.79%) |       1   →       1              |       13.21 ms →       14.50 ms   (+9.79%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      219.65 μs →      206.79 μs   (-5.86%) |       1   →       1              |      219.65 μs →      206.79 μs   (-5.86%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.89 μs →        2.51 μs  (-13.08%) |       1   →       1              |        2.89 μs →        2.51 μs  (-13.08%) | 
  │ └ sirius::Simulation_context::update                                |        1.92 s  →        1.92 s    (+0.27%) |       1   →       1              |        1.92 s  →        1.92 s    (+0.27%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.96 ms →       12.83 ms   (-1.03%) |       1   →       1              |       12.96 ms →       12.83 ms   (-1.03%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.42 ms →        8.24 ms   (-2.15%) |       1   →       1              |        8.42 ms →        8.24 ms   (-2.15%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.52 ms →        4.57 ms   (+1.06%) |       1   →       1              |        4.52 ms →        4.57 ms   (+1.06%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.11 ms →        4.15 ms   (+0.83%) |       1   →       1              |        4.11 ms →        4.15 ms   (+0.83%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.95 ms   (+1.36%) |       1   →       1              |        3.89 ms →        3.95 ms   (+1.36%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      213.94 μs →      194.65 μs   (-9.02%) |       1   →       1              |      213.94 μs →      194.65 μs   (-9.02%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.53 μs →        1.53 μs   (+0.33%) |       1   →       1              |        1.53 μs →        1.53 μs   (+0.33%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.40 ms →       15.00 ms   (-2.57%) |       2   →       2              |       30.79 ms →       30.00 ms   (-2.57%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.09 ms   (-0.20%) |       2   →       2              |        2.18 ms →        2.18 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      953.51 μs →      962.85 μs   (+0.98%) |       1   →       1              |      953.51 μs →      962.85 μs   (+0.98%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.14 ms →        5.18 ms   (+0.78%) |       2   →       2              |       10.27 ms →       10.35 ms   (+0.78%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.64 ms   (-0.41%) |       2   →       2              |        7.31 ms →        7.28 ms   (-0.41%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.91 ms →       15.84 ms   (-0.42%) |       4   →       4              |       63.62 ms →       63.36 ms   (-0.42%) | 
  │   ├ sddk::Gvec::init                                                |      162.09 ms →      158.48 ms   (-2.23%) |       2   →       2              |      324.18 ms →      316.97 ms   (-2.23%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.34 ms →      125.14 ms   (-2.50%) |       2   →       2              |      256.69 ms →      250.27 ms   (-2.50%) | 
  │   ├ sddk::Gvec_shells                                               |      120.11 ms →      121.40 ms   (+1.07%) |       1   →       1              |      120.11 ms →      121.40 ms   (+1.07%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.02 ms →        1.02 ms   (+0.05%) |       1   →       1              |        1.02 ms →        1.02 ms   (+0.05%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      218.40 ms →      217.94 ms   (-0.21%) |       1   →       1              |      218.40 ms →      217.94 ms   (-0.21%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.90 ms →       25.83 ms   (-0.26%) |       1   →       1              |       25.90 ms →       25.83 ms   (-0.26%) | 
  │ ├ sirius::K_point::K_point                                          |        1.76 μs →        1.76 μs   (+0.17%) |       2   →       2              |        3.51 μs →        3.52 μs   (+0.17%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.86 ms →       25.79 ms   (-0.27%) |       1   →       1              |       25.86 ms →       25.79 ms   (-0.27%) | 
  │   └ sirius::K_point::initialize                                     |       25.81 ms →       25.74 ms   (-0.29%) |       1   →       1              |       25.81 ms →       25.74 ms   (-0.29%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.35 ms →       19.22 ms   (-0.63%) |       1   →       1              |       19.35 ms →       19.22 ms   (-0.63%) | 
  │     │ └ sddk::Gvec::init                                            |        4.98 ms →        4.92 ms   (-1.29%) |       1   →       1              |        4.98 ms →        4.92 ms   (-1.29%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.16 μs →       10.84 μs   (+6.71%) |       1   →       1              |       10.16 μs →       10.84 μs   (+6.71%) | 
  │     └ sirius::K_point::update                                       |        4.12 ms →        4.04 ms   (-1.71%) |       1   →       1              |        4.12 ms →        4.04 ms   (-1.71%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.68 ms   (-4.93%) |       1   →       1              |        1.76 ms →        1.68 ms   (-4.93%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      986.16 μs →      909.52 μs   (-7.77%) |       1   →       1              |      986.16 μs →      909.52 μs   (-7.77%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.47 ms →        1.48 ms   (+0.27%) |       2   →       2              |        2.95 ms →        2.95 ms   (+0.27%) | 
  ├ sirius::Potential                                                   |       94.30 ms →       89.28 ms   (-5.33%) |       1   →       1              |       94.30 ms →       89.28 ms   (-5.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.44 ms   (-0.18%) |       6   →       6              |       14.67 ms →       14.65 ms   (-0.18%) | 
  │ └ sirius::Potential::update                                         |       79.29 ms →       74.29 ms   (-6.30%) |       1   →       1              |       79.29 ms →       74.29 ms   (-6.30%) | 
  │   └ sirius::Potential::generate_local_potential                     |       79.11 ms →       74.11 ms   (-6.32%) |       1   →       1              |       79.11 ms →       74.11 ms   (-6.32%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       57.56 ms →       58.36 ms   (+1.38%) |       1   →       1              |       57.56 ms →       58.36 ms   (+1.38%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.87 ms →        7.13 ms  (-44.65%) |       1   →       1              |       12.87 ms →        7.13 ms  (-44.65%) | 
  ├ sirius::Density                                                     |       75.70 ms →       75.93 ms   (+0.30%) |       1   →       1              |       75.70 ms →       75.93 ms   (+0.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.08 ms →        4.82 ms   (-5.10%) |       2   →       2              |       10.15 ms →        9.63 ms   (-5.10%) | 
  │ └ sirius::Density::update                                           |       65.43 ms →       66.27 ms   (+1.28%) |       1   →       1              |       65.43 ms →       66.27 ms   (+1.28%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.26 ms →       66.09 ms   (+1.29%) |       1   →       1              |       65.26 ms →       66.09 ms   (+1.29%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.38 ms →        3.13 ms   (-7.55%) |       1   →       1              |        3.38 ms →        3.13 ms   (-7.55%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       57.79 ms →       59.32 ms   (+2.66%) |       1   →       1              |       57.79 ms →       59.32 ms   (+2.66%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        2.78 ms →        2.39 ms  (-14.12%) |       1   →       1              |        2.78 ms →        2.39 ms  (-14.12%) | 
  ├ sirius::Density::initial_density                                    |       78.89 ms →       79.13 ms   (+0.30%) |       1   →       1              |       78.89 ms →       79.13 ms   (+0.30%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       57.93 ms →       58.72 ms   (+1.38%) |       1   →       1              |       57.93 ms →       58.72 ms   (+1.38%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.46 ms →        2.40 ms   (-2.51%) |       2   →       2              |        4.92 ms →        4.79 ms   (-2.51%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.36 ms →        4.07 ms   (-6.72%) |       1   →       1              |        4.36 ms →        4.07 ms   (-6.72%) | 
  ├ sirius::Potential::generate                                         |      186.10 ms →      186.11 ms   (+0.00%) |       1   →       1              |      186.10 ms →      186.11 ms   (+0.00%) | 
  │ ├ sirius::Potential::poisson                                        |       63.79 ms →       64.38 ms   (+0.92%) |       1   →       1              |       63.79 ms →       64.38 ms   (+0.92%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.69 ms →        2.37 ms  (-11.69%) |       1   →       1              |        2.69 ms →        2.37 ms  (-11.69%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.41 ms →        4.27 ms   (-3.24%) |       1   →       1              |        4.41 ms →        4.27 ms   (-3.24%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.21 ms →        4.21 ms   (-0.02%) |       1   →       1              |        4.21 ms →        4.21 ms   (-0.02%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.21 ms →        4.21 ms   (-0.03%) |       1   →       1              |        4.21 ms →        4.21 ms   (-0.03%) | 
  │ ├ sirius::Periodic_function::add                                    |      238.89 μs →      240.82 μs   (+0.81%) |       2   →       2              |      477.78 μs →      481.63 μs   (+0.81%) | 
  │ ├ sirius::Potential::xc                                             |       95.93 ms →       95.25 ms   (-0.72%) |       1   →       1              |       95.93 ms →       95.25 ms   (-0.72%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       94.84 ms →       94.15 ms   (-0.73%) |       1   →       1              |       94.84 ms →       94.15 ms   (-0.73%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.97 ms →        1.98 ms   (+0.57%) |       5   →       5              |        9.87 ms →        9.92 ms   (+0.57%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.46 ms →        2.38 ms   (-3.44%) |       9   →       9              |       22.14 ms →       21.38 ms   (-3.44%) | 
  │ │   ├ sirius::gradient                                              |        7.54 ms →        7.56 ms   (+0.20%) |       1   →       1              |        7.54 ms →        7.56 ms   (+0.20%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.42 ms   (+0.04%) |       3   →       3              |        7.27 ms →        7.27 ms   (+0.04%) | 
  │ │   ├ sirius::dot                                                   |        2.78 ms →        2.80 ms   (+0.82%) |       1   →       1              |        2.78 ms →        2.80 ms   (+0.82%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.56 ms →        2.57 ms   (+0.42%) |       1   →       1              |        2.56 ms →        2.57 ms   (+0.42%) | 
  │ │   └ sirius::divergence                                            |       19.63 ms →       19.52 ms   (-0.53%) |       1   →       1              |       19.63 ms →       19.52 ms   (-0.53%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.50 ms →        2.42 ms   (-3.34%) |       1   →       1              |        2.50 ms →        2.42 ms   (-3.34%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.18 ms →        3.29 ms   (+3.60%) |       1   →       1              |        3.18 ms →        3.29 ms   (+3.60%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.16 ms →       22.15 ms   (-0.05%) |       1   →       1              |       22.16 ms →       22.15 ms   (-0.05%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      131.00 ns →      124.00 ns   (-5.34%) |       1   →       1              |      131.00 ns →      124.00 ns   (-5.34%) | 
  ├ sirius::Hamiltonian0                                                |       13.79 ms →       14.00 ms   (+1.52%) |       1   →       1              |       13.79 ms →       14.00 ms   (+1.52%) | 
  │ ├ sirius::Local_operator                                            |       13.46 ms →       13.67 ms   (+1.56%) |       1   →       1              |       13.46 ms →       13.67 ms   (+1.56%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.11 ms →        7.10 ms   (-0.25%) |       1   →       1              |        7.11 ms →        7.10 ms   (-0.25%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.87 ms →        5.08 ms   (+4.26%) |       1   →       1              |        4.87 ms →        5.08 ms   (+4.26%) | 
  │ ├ sirius::Non_local_operator                                        |       60.26 μs →       59.72 μs   (-0.90%) |       2   →       2              |      120.53 μs →      119.45 μs   (-0.90%) | 
  │ ├ sirius::D_operator::initialize                                    |       79.67 μs →       80.96 μs   (+1.63%) |       1   →       1              |       79.67 μs →       80.96 μs   (+1.63%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.24 μs →       70.05 μs   (+1.18%) |       1   →       1              |       69.24 μs →       70.05 μs   (+1.18%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.47 s  →        2.46 s    (-0.58%) |       1   →       1              |        2.47 s  →        2.46 s    (-0.58%) | 
  │ ├ sirius::Hamiltonian_k                                             |        7.13 ms →        7.11 ms   (-0.21%) |       1   →       1              |        7.13 ms →        7.11 ms   (-0.21%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      248.83 μs →      242.87 μs   (-2.40%) |       1   →       1              |      248.83 μs →      242.87 μs   (-2.40%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        6.88 ms →        6.87 ms   (-0.14%) |       1   →       1              |        6.88 ms →        6.87 ms   (-0.14%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.47 s  →        2.45 s    (-0.58%) |       1   →       1              |        2.47 s  →        2.45 s    (-0.58%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.26 ms →       88.52 ms   (-1.93%) |       4   →       4              |      361.06 ms →      354.08 ms   (-1.93%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.29 ms →       25.19 ms   (-0.39%) |       1   →       1              |       25.29 ms →       25.19 ms   (-0.39%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.37 ms →       14.37 ms   (+0.02%) |       1   →       1              |       14.37 ms →       14.37 ms   (+0.02%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.20 s  →        1.21 s    (+0.88%) |       1   →       1              |        1.20 s  →        1.21 s    (+0.88%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      967.03 ms →      984.72 ms   (+1.83%) |       1   →       1              |      967.03 ms →      984.72 ms   (+1.83%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      298.48 ms →      314.31 ms   (+5.30%) |       1   →       1              |      298.48 ms →      314.31 ms   (+5.30%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      176.62 ms →      176.19 ms   (-0.24%) |       1   →       1              |      176.62 ms →      176.19 ms   (-0.24%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      176.61 ms →      176.19 ms   (-0.24%) |       1   →       1              |      176.61 ms →      176.19 ms   (-0.24%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      103.47 ms →      119.54 ms  (+15.54%) |       1   →       1              |      103.47 ms →      119.54 ms  (+15.54%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      176.93 ms →      177.44 ms   (+0.29%) |       1   →       1              |      176.93 ms →      177.44 ms   (+0.29%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      176.92 ms →      177.43 ms   (+0.29%) |       1   →       1              |      176.92 ms →      177.43 ms   (+0.29%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      156.35 ms →      159.07 ms   (+1.74%) |       1   →       1              |      156.35 ms →      159.07 ms   (+1.74%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      105.85 ms →      108.76 ms   (+2.75%) |       1   →       1              |      105.85 ms →      108.76 ms   (+2.75%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.72 ms →        3.72 ms   (+0.13%) |       1   →       1              |        3.72 ms →        3.72 ms   (+0.13%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.56 ms →       89.85 ms   (-0.78%) |       1   →       1              |       90.56 ms →       89.85 ms   (-0.78%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.74 ms →       12.04 ms   (-5.53%) |       1   →       1              |       12.74 ms →       12.04 ms   (-5.53%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       67.50 ms →       64.24 ms   (-4.82%) |       2   →       2              |      135.00 ms →      128.49 ms   (-4.82%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      200.49 ms →      191.89 ms   (-4.29%) |       2   →       2              |      400.98 ms →      383.77 ms   (-4.29%) | 
  │ │ │ └ sddk::wf_inner                                                |      200.39 ms →      191.79 ms   (-4.29%) |       2   →       2              |      400.77 ms →      383.57 ms   (-4.29%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       36.50 ns →       76.00 ns (+108.22%) |       2   →       2              |       73.00 ns →      152.00 ns (+108.22%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      198.91 ms →      190.10 ms   (-4.43%) |       2   →       2              |      397.82 ms →      380.19 ms   (-4.43%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       23.50 ns →       40.50 ns  (+72.34%) |       2   →       2              |       47.00 ns →       81.00 ns  (+72.34%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      117.06 ms →      117.63 ms   (+0.49%) |       1   →       1              |      117.06 ms →      117.63 ms   (+0.49%) | 
  │ │ └ sddk::wf_trans                                                  |       35.68 ms →       35.72 ms   (+0.10%) |       1   →       1              |       35.68 ms →       35.72 ms   (+0.10%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.67 ms →       35.70 ms   (+0.10%) |       1   →       1              |       35.67 ms →       35.70 ms   (+0.10%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      647.00 ns →      550.00 ns  (-14.99%) |       1   →       1              |      647.00 ns →      550.00 ns  (-14.99%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      103.39 s  →      104.15 s    (+0.74%) |       1   →       1              |      103.39 s  →      104.15 s    (+0.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms →        2.17 ms   (+0.03%) |      31   →      31              |       67.34 ms →       67.36 ms   (+0.03%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.71 s  →        2.73 s    (+0.76%) |      38   →      38              |      103.09 s  →      103.87 s    (+0.76%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.01 ms →        6.97 ms   (-0.50%) |      38   →      38              |      266.25 ms →      264.91 ms   (-0.50%) | 
  │ │ │ ├ sirius::Local_operator                                        |        6.67 ms →        6.65 ms   (-0.43%) |      38   →      38              |      253.59 ms →      252.51 ms   (-0.43%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.51 ms →        1.49 ms   (-1.32%) |      38   →      38              |       57.24 ms →       56.49 ms   (-1.32%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.72 ms →        3.70 ms   (-0.40%) |      38   →      38              |      141.28 ms →      140.72 ms   (-0.40%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       60.91 μs →       60.61 μs   (-0.50%) |      76   →      76              |        4.63 ms →        4.61 ms   (-0.50%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       82.27 μs →       79.05 μs   (-3.91%) |      38   →      38              |        3.13 ms →        3.00 ms   (-3.91%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       67.51 μs →       66.01 μs   (-2.21%) |      38   →      38              |        2.57 ms →        2.51 ms   (-2.21%) | 
  │ │ ├ sirius::Band::solve                                             |        2.05 s  →        2.07 s    (+0.70%) |      38   →      38              |       78.04 s  →       78.59 s    (+0.70%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      204.45 μs →      203.97 μs   (-0.24%) |      38   →      38              |        7.77 ms →        7.75 ms   (-0.24%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.08 μs →      196.99 μs   (-0.05%) |      38   →      38              |        7.49 ms →        7.49 ms   (-0.05%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.49 μs →        5.31 μs   (-3.37%) |      38   →      38              |      208.77 μs →      201.75 μs   (-3.37%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.05 s  →        2.07 s    (+0.81%) |      38   →      38              |       77.92 s  →       78.55 s    (+0.81%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       59.57 ms →       59.80 ms   (+0.39%) |      38   →      38              |        2.26 s  →        2.27 s    (+0.39%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.59 ms →        4.65 ms   (+1.34%) |     228   →     228              |        1.05 s  →        1.06 s    (+1.34%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.64 ms →        1.64 ms   (+0.03%) |      38   →      38              |       62.38 ms →       62.39 ms   (+0.03%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      419.81 μs →      417.46 μs   (-0.56%) |      38   →      38              |       15.95 ms →       15.86 ms   (-0.56%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      967.56 μs →      971.59 μs   (+0.42%) |      38   →      38              |       36.77 ms →       36.92 ms   (+0.42%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.97 s  →        1.98 s    (+0.84%) |      38   →      38              |       74.68 s  →       75.30 s    (+0.84%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      209.43 ms →      212.67 ms   (+1.55%) |     201   →     201              |       42.09 s  →       42.75 s    (+1.55%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      147.60 ms →      150.80 ms   (+2.17%) |     201   →     201              |       29.67 s  →       30.31 s    (+2.17%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       25.87 ms →       27.76 ms   (+7.32%) |     201   →     201              |        5.20 s  →        5.58 s    (+7.32%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      705.57 μs →      678.61 μs   (-3.82%) |     201   →     201              |      141.82 ms →      136.40 ms   (-3.82%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.72 ms →        3.58 ms   (-3.83%) |      38   →      38              |      141.35 ms →      135.94 ms   (-3.83%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       20.77 ms →       22.56 ms   (+8.59%) |     201   →     201              |        4.18 s  →        4.53 s    (+8.59%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      693.15 μs →      672.44 μs   (-2.99%) |     201   →     201              |      139.32 ms →      135.16 ms   (-2.99%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.65 ms →        3.54 ms   (-3.00%) |      38   →      38              |      138.79 ms →      134.62 ms   (-3.00%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       32.67 ms →       34.15 ms   (+4.53%) |     201   →     201              |        6.57 s  →        6.86 s    (+4.53%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       20.09 ms →       21.52 ms   (+7.12%) |     201   →     201              |        4.04 s  →        4.33 s    (+7.12%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.65 ms   (+0.18%) |     201   →     201              |      531.69 ms →      532.64 ms   (+0.18%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.22 ms →       22.26 ms   (+0.21%) |     201   →     201              |        4.47 s  →        4.47 s    (+0.21%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.30 ms →        2.33 ms   (+1.19%) |     201   →     201              |      462.71 ms →      468.23 ms   (+1.19%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.47 ms →       18.47 ms   (-0.03%) |     402   →     402              |        7.43 s  →        7.42 s    (-0.03%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       57.01 ms →       56.97 ms   (-0.06%) |     201   →     201              |       11.46 s  →       11.45 s    (-0.06%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       13.21 ms →       13.13 ms   (-0.61%) |     364   →     364              |        4.81 s  →        4.78 s    (-0.61%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       44.74 ns →       77.62 ns  (+73.47%) |     364   →     364              |       16.29 μs →       28.25 μs  (+73.47%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.56 ms →        9.52 ms   (-0.44%) |     364   →     364              |        3.48 s  →        3.47 s    (-0.44%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       36.14 ns →       46.07 ns  (+27.48%) |     364   →     364              |       13.16 μs →       16.77 μs  (+27.48%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.17 ms →        3.27 ms   (+3.12%) |     201   →     201              |      636.78 ms →      656.66 ms   (+3.12%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.65 ms →       15.65 ms   (+0.04%) |     201   →     201              |        3.15 s  →        3.15 s    (+0.04%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       17.58 ms →       17.58 ms   (+0.03%) |     163   →     163              |        2.87 s  →        2.87 s    (+0.03%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.83 ms →        5.83 ms   (-0.04%) |     489   →     489              |        2.85 s  →        2.85 s    (-0.04%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       20.58 ms →       20.56 ms   (-0.12%) |     201   →     201              |        4.14 s  →        4.13 s    (-0.12%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       19.53 ms →       19.45 ms   (-0.46%) |     201   →     201              |        3.93 s  →        3.91 s    (-0.46%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |      112.95 ns →      138.08 ns  (+22.25%) |     201   →     201              |       22.70 μs →       27.76 μs  (+22.25%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       15.92 ms →       15.92 ms   (+0.05%) |     201   →     201              |        3.20 s  →        3.20 s    (+0.05%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       20.15 ns →       26.44 ns  (+31.23%) |     201   →     201              |        4.05 μs →        5.32 μs  (+31.23%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       47.16 ms →       47.31 ms   (+0.32%) |     201   →     201              |        9.48 s  →        9.51 s    (+0.32%) | 
  │ │ │ │   ├ sirius::residuals                                         |       16.93 ms →       16.65 ms   (-1.61%) |     196   →     196              |        3.32 s  →        3.26 s    (-1.61%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       17.94 ms →       17.63 ms   (-1.72%) |     164   →     164              |        2.94 s  →        2.89 s    (-1.72%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.04 ms →        8.04 ms   (-0.02%) |     328   →     328              |        2.64 s  →        2.64 s    (-0.02%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.57 ms →        1.55 ms   (-1.29%) |     164   →     164              |      257.66 ms →      254.34 ms   (-1.29%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       52.25 ms →       52.36 ms   (+0.21%) |      80   →      80              |        4.18 s  →        4.19 s    (+0.21%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       33.31 ms →       33.41 ms   (+0.28%) |     122   →     122              |        4.06 s  →        4.08 s    (+0.28%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       24.39 ms →       24.24 ms   (-0.62%) |     164   →     164              |        4.00 s  →        3.97 s    (-0.62%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      566.50 ns →      583.34 ns   (+2.97%) |      38   →      38              |       21.53 μs →       22.17 μs   (+2.97%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.39 μs →       23.35 μs   (-0.14%) |      38   →      38              |      888.64 μs →      887.41 μs   (-0.14%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.49 ms →        3.52 ms   (+0.94%) |      38   →      38              |      132.63 ms →      133.87 ms   (+0.94%) | 
  │ │ ├ sirius::Density::generate                                       |      291.49 ms →      295.47 ms   (+1.36%) |      38   →      38              |       11.08 s  →       11.23 s    (+1.36%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      287.64 ms →      291.60 ms   (+1.37%) |      38   →      38              |       10.93 s  →       11.08 s    (+1.37%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.29 ms →       67.40 ms   (+6.51%) |      38   →      38              |        2.40 s  →        2.56 s    (+6.51%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       63.82 μs →       64.30 μs   (+0.75%) |      38   →      38              |        2.43 ms →        2.44 ms   (+0.75%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.16 ms →        1.17 ms   (+0.91%) |       2   →       2              |        2.31 ms →        2.33 ms   (+0.91%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       52.00 ms →       56.11 ms   (+7.89%) |      38   →      38              |        1.98 s  →        2.13 s    (+7.89%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.40 ms →       61.03 ms   (+1.05%) |      38   →      38              |        2.30 s  →        2.32 s    (+1.05%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.90 μs →       10.99 μs   (+0.88%) |      38   →      38              |      414.16 μs →      417.79 μs   (+0.88%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.32 ms →        2.31 ms   (-0.13%) |      38   →      38              |       87.98 ms →       87.87 ms   (-0.13%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       57.54 ms →       58.18 ms   (+1.11%) |      38   →      38              |        2.19 s  →        2.21 s    (+1.11%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.14 ms →        6.75 ms  (+10.00%) |      38   →      38              |      233.25 ms →      256.58 ms  (+10.00%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      812.55 ns →      781.37 ns   (-3.84%) |      38   →      38              |       30.88 μs →       29.69 μs   (-3.84%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.85 ms →      104.36 ms   (-0.47%) |      38   →      38              |        3.98 s  →        3.97 s    (-0.47%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.39 ms   (-0.44%) |      38   →      38              |       91.25 ms →       90.85 ms   (-0.44%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms →       20.07 ms   (+0.03%) |      38   →      38              |      762.24 ms →      762.47 ms   (+0.03%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms →       19.89 ms   (-0.03%) |      38   →      38              |      756.00 ms →      755.79 ms   (-0.03%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      283.97 ns →      316.68 ns  (+11.52%) |      38   →      38              |       10.79 μs →       12.03 μs  (+11.52%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.45%) |      38   →      38              |       47.76 ms →       47.54 ms   (-0.45%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.59 ms →        2.62 ms   (+0.99%) |      38   →      38              |       98.46 ms →       99.44 ms   (+0.99%) | 
  │ │ ├ sirius::Density::mix                                            |      125.90 ms →      127.46 ms   (+1.24%) |      38   →      38              |        4.78 s  →        4.84 s    (+1.24%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      257.59 μs →      259.20 μs   (+0.63%) |      38   →      38              |        9.79 ms →        9.85 ms   (+0.63%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        2.64 ms →        2.71 ms   (+2.73%) |      38   →      38              |      100.31 ms →      103.05 ms   (+2.73%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.45 ms →        2.52 ms   (+2.95%) |      38   →      38              |       93.00 ms →       95.74 ms   (+2.95%) | 
  │ │ ├ sirius::Potential::generate                                     |      182.73 ms →      183.75 ms   (+0.56%) |      38   →      38              |        6.94 s  →        6.98 s    (+0.56%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       63.91 ms →       65.41 ms   (+2.34%) |      38   →      38              |        2.43 s  →        2.49 s    (+2.34%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.70 ms →        3.08 ms  (+14.08%) |      38   →      38              |      102.71 ms →      117.18 ms  (+14.08%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.36 ms →        4.35 ms   (-0.25%) |      38   →      38              |      165.62 ms →      165.21 ms   (-0.25%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.24 ms →        4.26 ms   (+0.49%) |      38   →      38              |      161.13 ms →      161.92 ms   (+0.49%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.24 ms →        4.26 ms   (+0.49%) |      38   →      38              |      161.11 ms →      161.90 ms   (+0.49%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      229.97 μs →      229.95 μs   (-0.01%) |      76   →      76              |       17.48 ms →       17.48 ms   (-0.01%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       93.48 ms →       93.14 ms   (-0.36%) |      38   →      38              |        3.55 s  →        3.54 s    (-0.36%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       92.45 ms →       92.12 ms   (-0.35%) |      38   →      38              |        3.51 s  →        3.50 s    (-0.35%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.62 ms →        1.58 ms   (-2.67%) |     190   →     190              |      308.36 ms →      300.13 ms   (-2.67%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.42 ms →        2.47 ms   (+1.98%) |     342   →     342              |      827.09 ms →      843.49 ms   (+1.98%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.46 ms →        2.49 ms   (+1.10%) |      38   →      38              |       93.66 ms →       94.70 ms   (+1.10%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      725.26 μs →      723.35 μs   (-0.26%) |     114   →     114              |       82.68 ms →       82.46 ms   (-0.26%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.84 ms   (+0.70%) |      38   →      38              |      107.21 ms →      107.96 ms   (+0.70%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.59 ms →        2.60 ms   (+0.55%) |      38   →      38              |       98.32 ms →       98.86 ms   (+0.55%) | 
  │ │ │ │   └ sirius::divergence                                        |       22.70 ms →       22.06 ms   (-2.79%) |      38   →      38              |      862.51 ms →      838.40 ms   (-2.79%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.42 ms →        2.43 ms   (+0.30%) |      38   →      38              |       91.98 ms →       92.26 ms   (+0.30%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.42 ms →        3.30 ms   (-3.61%) |      38   →      38              |      130.01 ms →      125.31 ms   (-3.61%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.90 ms →       20.90 ms   (+0.02%) |      38   →      38              |      794.14 ms →      794.32 ms   (+0.02%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      182.42 ns →      197.74 ns   (+8.40%) |      38   →      38              |        6.93 μs →        7.51 μs   (+8.40%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.42 ns →      308.55 ns   (+9.64%) |      38   →      38              |       10.69 μs →       11.73 μs   (+9.64%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.20 ms →        2.24 ms   (+1.80%) |      38   →      38              |       83.64 ms →       85.14 ms   (+1.80%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.26 ms →        4.11 ms   (-3.54%) |     266   →     266              |        1.13 s  →        1.09 s    (-3.54%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.07 ms →        3.94 ms   (-3.06%) |     266   →     266              |        1.08 s  →        1.05 s    (-3.06%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.07 ms →        3.94 ms   (-3.06%) |     266   →     266              |        1.08 s  →        1.05 s    (-3.06%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.06 ms →        4.28 ms   (+5.39%) |     114   →     114              |      462.81 ms →      487.74 ms   (+5.39%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.87 ms →        4.08 ms   (+5.52%) |     114   →     114              |      441.27 ms →      465.62 ms   (+5.52%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.05 ms →        4.01 ms   (-1.18%) |      38   →      38              |      154.03 ms →      152.21 ms   (-1.18%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      135.44 μs →      100.66 μs  (-25.68%) |      38   →      38              |        5.15 ms →        3.82 ms  (-25.68%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      131.58 μs →       96.98 μs  (-26.30%) |      38   →      38              |        5.00 ms →        3.69 ms  (-26.30%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.33 ms →        5.32 ms   (-0.23%) |       2   →       2              |       10.66 ms →       10.64 ms   (-0.23%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.25 ms →        4.02 ms   (-5.55%) |       6   →       6              |       25.53 ms →       24.11 ms   (-5.55%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.16 ms →        3.91 ms   (-6.05%) |       6   →       6              |       24.96 ms →       23.45 ms   (-6.05%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.16 ms →        3.91 ms   (-6.05%) |       6   →       6              |       24.96 ms →       23.45 ms   (-6.05%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.06 ms →        4.08 ms   (+0.56%) |       3   →       3              |       12.18 ms →       12.25 ms   (+0.56%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.00 ms →        4.05 ms   (+1.14%) |       3   →       3              |       12.00 ms →       12.14 ms   (+1.14%) | 
  ├ sirius::Periodic_function|inner                                     |        4.11 ms →        3.90 ms   (-5.01%) |       2   →       2              |        8.21 ms →        7.80 ms   (-5.01%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.10 ms →        3.87 ms   (-5.48%) |       2   →       2              |        8.20 ms →        7.75 ms   (-5.48%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.10 ms →        3.87 ms   (-5.48%) |       2   →       2              |        8.20 ms →        7.75 ms   (-5.48%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.36 ms →        4.38 ms   (+0.33%) |       1   →       1              |        4.36 ms →        4.38 ms   (+0.33%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.21 ms →        4.08 ms   (-3.24%) |       1   →       1              |        4.21 ms →        4.08 ms   (-3.24%) | 
- └ sirius::finalize                                                    |      308.11 ms →      426.56 ms  (+38.44%) |       1   →       1              |      308.11 ms →      426.56 ms  (+38.44%) | 
  ====================================================================================================================================================================================================
```
