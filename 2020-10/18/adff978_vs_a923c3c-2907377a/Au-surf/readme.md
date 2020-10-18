# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      133.18 s  →      112.78 s   (-15.32%) |       1   →       1              |      133.18 s  →      112.78 s   (-15.32%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.69 s    (-1.26%) |       1   →       1              |        2.73 s  →        2.69 s    (-1.26%) | 
  ├ sirius::Simulation_context::initialize                              |        2.07 s  →        2.12 s    (+2.11%) |       1   →       1              |        2.07 s  →        2.12 s    (+2.11%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       33.51 ms →       40.31 ms  (+20.29%) |       1   →       1              |       33.51 ms →       40.31 ms  (+20.29%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       78.66 ms →      130.07 ms  (+65.37%) |       1   →       1              |       78.66 ms →      130.07 ms  (+65.37%) | 
- │ │ ├ sirius::Atom_type::init                                         |       52.81 ms →      105.08 ms  (+98.99%) |       1   →       1              |       52.81 ms →      105.08 ms  (+98.99%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.79 ms →       24.93 ms   (-3.33%) |       1   →       1              |       25.79 ms →       24.93 ms   (-3.33%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.32 ms →       10.04 ms   (-2.70%) |       1   →       1              |       10.32 ms →       10.04 ms   (-2.70%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.44 ms →       14.86 ms   (-3.75%) |       1   →       1              |       15.44 ms →       14.86 ms   (-3.75%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.67 ms →       14.07 ms   (-4.10%) |       1   →       1              |       14.67 ms →       14.07 ms   (-4.10%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.44 ms →       13.85 ms   (-4.08%) |       1   →       1              |       14.44 ms →       13.85 ms   (-4.08%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      218.70 μs →      204.93 μs   (-6.30%) |       1   →       1              |      218.70 μs →      204.93 μs   (-6.30%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.58 μs →        2.51 μs   (-2.98%) |       1   →       1              |        2.58 μs →        2.51 μs   (-2.98%) | 
  │ └ sirius::Simulation_context::update                                |        1.91 s  →        1.89 s    (-0.69%) |       1   →       1              |        1.91 s  →        1.89 s    (-0.69%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.75 ms →       12.61 ms   (-1.12%) |       1   →       1              |       12.75 ms →       12.61 ms   (-1.12%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.06 ms →        7.92 ms   (-1.70%) |       1   →       1              |        8.06 ms →        7.92 ms   (-1.70%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.68 ms →        4.67 ms   (-0.13%) |       1   →       1              |        4.68 ms →        4.67 ms   (-0.13%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.12 ms →        4.11 ms   (-0.17%) |       1   →       1              |        4.12 ms →        4.11 ms   (-0.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.91 ms →        3.90 ms   (-0.15%) |       1   →       1              |        3.91 ms →        3.90 ms   (-0.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      203.21 μs →      202.29 μs   (-0.45%) |       1   →       1              |      203.21 μs →      202.29 μs   (-0.45%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.40 μs →        1.26 μs   (-9.51%) |       1   →       1              |        1.40 μs →        1.26 μs   (-9.51%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       16.19 ms →       15.74 ms   (-2.79%) |       2   →       2              |       32.39 ms →       31.49 ms   (-2.79%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.14 ms →        1.09 ms   (-4.76%) |       2   →       2              |        2.29 ms →        2.18 ms   (-4.76%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      964.64 μs →      959.56 μs   (-0.53%) |       1   →       1              |      964.64 μs →      959.56 μs   (-0.53%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.14 ms →        5.07 ms   (-1.24%) |       2   →       2              |       10.27 ms →       10.14 ms   (-1.24%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.68 ms →        3.65 ms   (-0.90%) |       2   →       2              |        7.36 ms →        7.29 ms   (-0.90%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.71 ms →       16.01 ms   (+1.88%) |       4   →       4              |       62.85 ms →       64.02 ms   (+1.88%) | 
  │   ├ sddk::Gvec::init                                                |      160.18 ms →      161.50 ms   (+0.82%) |       2   →       2              |      320.36 ms →      323.01 ms   (+0.82%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.30 ms →      126.61 ms   (-0.54%) |       2   →       2              |      254.60 ms →      253.22 ms   (-0.54%) | 
- │   ├ sddk::Gvec_shells                                               |      115.61 ms →      130.70 ms  (+13.05%) |       1   →       1              |      115.61 ms →      130.70 ms  (+13.05%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.04 ms   (+0.27%) |       1   →       1              |        1.03 ms →        1.04 ms   (+0.27%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      219.99 ms →      219.58 ms   (-0.19%) |       1   →       1              |      219.99 ms →      219.58 ms   (-0.19%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.14 ms →       25.90 ms   (-0.94%) |       1   →       1              |       26.14 ms →       25.90 ms   (-0.94%) | 
  │ ├ sirius::K_point::K_point                                          |        1.89 μs →        1.93 μs   (+1.96%) |       2   →       2              |        3.79 μs →        3.86 μs   (+1.96%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.11 ms →       25.86 ms   (-0.94%) |       1   →       1              |       26.11 ms →       25.86 ms   (-0.94%) | 
  │   └ sirius::K_point::initialize                                     |       26.05 ms →       25.81 ms   (-0.95%) |       1   →       1              |       26.05 ms →       25.81 ms   (-0.95%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.68 ms →       19.39 ms   (-1.47%) |       1   →       1              |       19.68 ms →       19.39 ms   (-1.47%) | 
  │     │ └ sddk::Gvec::init                                            |        4.95 ms →        4.94 ms   (-0.04%) |       1   →       1              |        4.95 ms →        4.94 ms   (-0.04%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |       10.89 μs →       12.64 μs  (+16.09%) |       1   →       1              |       10.89 μs →       12.64 μs  (+16.09%) | 
  │     └ sirius::K_point::update                                       |        4.06 ms →        4.10 ms   (+1.13%) |       1   →       1              |        4.06 ms →        4.10 ms   (+1.13%) | 
  │       └ sirius::Beta_projectors                                     |        1.70 ms →        1.70 ms   (-0.40%) |       1   →       1              |        1.70 ms →        1.70 ms   (-0.40%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      894.07 μs →      886.79 μs   (-0.81%) |       1   →       1              |      894.07 μs →      886.79 μs   (-0.81%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.48 ms →        1.48 ms   (+0.19%) |       2   →       2              |        2.95 ms →        2.96 ms   (+0.19%) | 
  ├ sirius::Potential                                                   |       97.11 ms →       95.04 ms   (-2.14%) |       1   →       1              |       97.11 ms →       95.04 ms   (-2.14%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.65 ms   (+7.35%) |       6   →       6              |       14.79 ms →       15.88 ms   (+7.35%) | 
  │ └ sirius::Potential::update                                         |       81.99 ms →       78.81 ms   (-3.88%) |       1   →       1              |       81.99 ms →       78.81 ms   (-3.88%) | 
  │   └ sirius::Potential::generate_local_potential                     |       81.82 ms →       78.64 ms   (-3.88%) |       1   →       1              |       81.82 ms →       78.64 ms   (-3.88%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       57.45 ms →       49.94 ms  (-13.06%) |       1   →       1              |       57.45 ms →       49.94 ms  (-13.06%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       15.60 ms →       20.01 ms  (+28.26%) |       1   →       1              |       15.60 ms →       20.01 ms  (+28.26%) | 
  ├ sirius::Density                                                     |       75.69 ms →       75.48 ms   (-0.28%) |       1   →       1              |       75.69 ms →       75.48 ms   (-0.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.83 ms →        4.84 ms   (+0.21%) |       2   →       2              |        9.65 ms →        9.67 ms   (+0.21%) | 
  │ └ sirius::Density::update                                           |       65.93 ms →       65.69 ms   (-0.36%) |       1   →       1              |       65.93 ms →       65.69 ms   (-0.36%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.75 ms →       65.51 ms   (-0.36%) |       1   →       1              |       65.75 ms →       65.51 ms   (-0.36%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.08 ms →        3.08 ms   (+0.03%) |       1   →       1              |        3.08 ms →        3.08 ms   (+0.03%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       57.76 ms →       51.78 ms  (-10.35%) |       1   →       1              |       57.76 ms →       51.78 ms  (-10.35%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.65 ms →        9.39 ms (+157.43%) |       1   →       1              |        3.65 ms →        9.39 ms (+157.43%) | 
  ├ sirius::Density::initial_density                                    |       79.22 ms →       80.79 ms   (+1.98%) |       1   →       1              |       79.22 ms →       80.79 ms   (+1.98%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       57.65 ms →       51.61 ms  (-10.48%) |       1   →       1              |       57.65 ms →       51.61 ms  (-10.48%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.87 ms →        6.23 ms (+117.02%) |       2   →       2              |        5.75 ms →       12.47 ms (+117.02%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.03 ms →        4.86 ms  (+20.50%) |       1   →       1              |        4.03 ms →        4.86 ms  (+20.50%) | 
  ├ sirius::Potential::generate                                         |      187.28 ms →      187.81 ms   (+0.28%) |       1   →       1              |      187.28 ms →      187.81 ms   (+0.28%) | 
  │ ├ sirius::Potential::poisson                                        |       64.51 ms →       64.44 ms   (-0.11%) |       1   →       1              |       64.51 ms →       64.44 ms   (-0.11%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.34 ms →       10.41 ms (+211.57%) |       1   →       1              |        3.34 ms →       10.41 ms (+211.57%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.11 ms →        4.12 ms   (+0.20%) |       1   →       1              |        4.11 ms →        4.12 ms   (+0.20%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.05 ms →        4.09 ms   (+1.04%) |       1   →       1              |        4.05 ms →        4.09 ms   (+1.04%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.04 ms →        4.09 ms   (+1.04%) |       1   →       1              |        4.04 ms →        4.09 ms   (+1.04%) | 
  │ ├ sirius::Periodic_function::add                                    |      245.79 μs →      244.76 μs   (-0.42%) |       2   →       2              |      491.57 μs →      489.52 μs   (-0.42%) | 
  │ ├ sirius::Potential::xc                                             |       96.31 ms →       96.79 ms   (+0.50%) |       1   →       1              |       96.31 ms →       96.79 ms   (+0.50%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       95.27 ms →       95.70 ms   (+0.45%) |       1   →       1              |       95.27 ms →       95.70 ms   (+0.45%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.00 ms →        2.01 ms   (+0.66%) |       5   →       5              |       10.00 ms →       10.07 ms   (+0.66%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.44 ms →        2.50 ms   (+2.39%) |       9   →       9              |       21.96 ms →       22.49 ms   (+2.39%) | 
  │ │   ├ sirius::gradient                                              |        7.67 ms →        7.66 ms   (-0.09%) |       1   →       1              |        7.67 ms →        7.66 ms   (-0.09%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.46 ms →        2.46 ms   (-0.06%) |       3   →       3              |        7.39 ms →        7.38 ms   (-0.06%) | 
  │ │   ├ sirius::dot                                                   |        2.83 ms →        2.82 ms   (-0.26%) |       1   →       1              |        2.83 ms →        2.82 ms   (-0.26%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.61 ms →        2.59 ms   (-0.85%) |       1   →       1              |        2.61 ms →        2.59 ms   (-0.85%) | 
  │ │   └ sirius::divergence                                            |       19.85 ms →       19.86 ms   (+0.07%) |       1   →       1              |       19.85 ms →       19.86 ms   (+0.07%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.56 ms   (+5.67%) |       1   →       1              |        2.42 ms →        2.56 ms   (+5.67%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.22 ms →        3.24 ms   (+0.61%) |       1   →       1              |        3.22 ms →        3.24 ms   (+0.61%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.21 ms →       22.27 ms   (+0.30%) |       1   →       1              |       22.21 ms →       22.27 ms   (+0.30%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      401.00 ns →      222.00 ns  (-44.64%) |       1   →       1              |      401.00 ns →      222.00 ns  (-44.64%) | 
  ├ sirius::Hamiltonian0                                                |       13.83 ms →       14.17 ms   (+2.44%) |       1   →       1              |       13.83 ms →       14.17 ms   (+2.44%) | 
  │ ├ sirius::Local_operator                                            |       13.50 ms →       13.85 ms   (+2.59%) |       1   →       1              |       13.50 ms →       13.85 ms   (+2.59%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.22 ms →        7.57 ms   (+4.88%) |       1   →       1              |        7.22 ms →        7.57 ms   (+4.88%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.81 ms →        4.80 ms   (-0.37%) |       1   →       1              |        4.81 ms →        4.80 ms   (-0.37%) | 
  │ ├ sirius::Non_local_operator                                        |       59.96 μs →       58.53 μs   (-2.39%) |       2   →       2              |      119.92 μs →      117.06 μs   (-2.39%) | 
  │ ├ sirius::D_operator::initialize                                    |       79.31 μs →       81.36 μs   (+2.58%) |       1   →       1              |       79.31 μs →       81.36 μs   (+2.58%) | 
+ │ └ sirius::Q_operator::initialize                                    |       82.24 μs →       69.36 μs  (-15.66%) |       1   →       1              |       82.24 μs →       69.36 μs  (-15.66%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.47 s  →        2.49 s    (+0.92%) |       1   →       1              |        2.47 s  →        2.49 s    (+0.92%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.42 ms   (+0.11%) |       1   →       1              |        8.41 ms →        8.42 ms   (+0.11%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      261.49 μs →      249.01 μs   (-4.77%) |       1   →       1              |      261.49 μs →      249.01 μs   (-4.77%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.17 ms   (+0.27%) |       1   →       1              |        8.15 ms →        8.17 ms   (+0.27%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.46 s  →        2.48 s    (+0.92%) |       1   →       1              |        2.46 s  →        2.48 s    (+0.92%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.09 ms →       92.03 ms   (+2.15%) |       4   →       4              |      360.38 ms →      368.12 ms   (+2.15%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       26.07 ms →       25.70 ms   (-1.41%) |       1   →       1              |       26.07 ms →       25.70 ms   (-1.41%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       15.06 ms →       14.73 ms   (-2.21%) |       1   →       1              |       15.06 ms →       14.73 ms   (-2.21%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.20 s  →        1.20 s    (-0.23%) |       1   →       1              |        1.20 s  →        1.20 s    (-0.23%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      981.99 ms →      979.42 ms   (-0.26%) |       1   →       1              |      981.99 ms →      979.42 ms   (-0.26%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      309.87 ms →      308.27 ms   (-0.51%) |       1   →       1              |      309.87 ms →      308.27 ms   (-0.51%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      179.71 ms →      180.84 ms   (+0.62%) |       1   →       1              |      179.71 ms →      180.84 ms   (+0.62%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      179.71 ms →      180.83 ms   (+0.62%) |       1   →       1              |      179.71 ms →      180.83 ms   (+0.62%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      111.73 ms →      109.02 ms   (-2.42%) |       1   →       1              |      111.73 ms →      109.02 ms   (-2.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      179.97 ms →      177.73 ms   (-1.24%) |       1   →       1              |      179.97 ms →      177.73 ms   (-1.24%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      179.96 ms →      177.73 ms   (-1.24%) |       1   →       1              |      179.96 ms →      177.73 ms   (-1.24%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      161.43 ms →      162.67 ms   (+0.77%) |       1   →       1              |      161.43 ms →      162.67 ms   (+0.77%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      111.05 ms →      112.18 ms   (+1.02%) |       1   →       1              |      111.05 ms →      112.18 ms   (+1.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.74 ms →        3.73 ms   (-0.34%) |       1   →       1              |        3.74 ms →        3.73 ms   (-0.34%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.64 ms →       89.28 ms   (-0.40%) |       1   →       1              |       89.64 ms →       89.28 ms   (-0.40%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.12 ms →       11.61 ms   (-4.22%) |       1   →       1              |       12.12 ms →       11.61 ms   (-4.22%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.17 ms →       64.27 ms   (+0.15%) |       2   →       2              |      128.35 ms →      128.54 ms   (+0.15%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      193.42 ms →      196.02 ms   (+1.34%) |       2   →       2              |      386.85 ms →      392.04 ms   (+1.34%) | 
  │ │ │ └ sddk::wf_inner                                                |      193.32 ms →      195.92 ms   (+1.34%) |       2   →       2              |      386.64 ms →      391.84 ms   (+1.34%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       47.50 ns →       32.50 ns  (-31.58%) |       2   →       2              |       95.00 ns →       65.00 ns  (-31.58%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      191.22 ms →      194.41 ms   (+1.67%) |       2   →       2              |      382.43 ms →      388.83 ms   (+1.67%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       25.50 ns  (+13.33%) |       2   →       2              |       45.00 ns →       51.00 ns  (+13.33%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      115.33 ms →      116.11 ms   (+0.67%) |       1   →       1              |      115.33 ms →      116.11 ms   (+0.67%) | 
  │ │ └ sddk::wf_trans                                                  |       35.84 ms →       36.36 ms   (+1.44%) |       1   →       1              |       35.84 ms →       36.36 ms   (+1.44%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.67 ms →       35.65 ms   (-0.04%) |       1   →       1              |       35.67 ms →       35.65 ms   (-0.04%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      759.00 ns →      683.00 ns  (-10.01%) |       1   →       1              |      759.00 ns →      683.00 ns  (-10.01%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      124.37 s  →      103.83 s   (-16.51%) |       1   →       1              |      124.37 s  →      103.83 s   (-16.51%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.18 ms →        2.18 ms   (+0.32%) |      31   →      31              |       67.44 ms →       67.66 ms   (+0.32%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.76 s  →        2.73 s    (-1.15%) |      45   →      38    (-15.56%) |      124.08 s  →      103.57 s   (-16.53%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        7.98 ms →        7.07 ms  (-11.34%) |      45   →      38    (-15.56%) |      358.99 ms →      268.78 ms  (-25.13%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        7.64 ms →        6.74 ms  (-11.85%) |      45   →      38    (-15.56%) |      343.86 ms →      255.96 ms  (-25.56%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.53 ms →        1.58 ms   (+2.70%) |      45   →      38    (-15.56%) |       69.07 ms →       59.90 ms  (-13.27%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.60 ms →        3.68 ms  (-19.91%) |      45   →      38    (-15.56%) |      206.98 ms →      139.99 ms  (-32.37%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       60.97 μs →       60.29 μs   (-1.12%) |      90   →      76    (-15.56%) |        5.49 ms →        4.58 ms  (-16.50%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       82.68 μs →       83.83 μs   (+1.40%) |      45   →      38    (-15.56%) |        3.72 ms →        3.19 ms  (-14.38%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       70.43 μs →       69.86 μs   (-0.81%) |      45   →      38    (-15.56%) |        3.17 ms →        2.65 ms  (-16.24%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.09 s  →        2.06 s    (-1.05%) |      45   →      38    (-15.56%) |       93.86 s  →       78.43 s   (-16.44%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      216.69 μs →      213.97 μs   (-1.25%) |      45   →      38    (-15.56%) |        9.75 ms →        8.13 ms  (-16.61%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      209.60 μs →      206.89 μs   (-1.30%) |      45   →      38    (-15.56%) |        9.43 ms →        7.86 ms  (-16.65%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.18 μs →        5.18 μs   (+0.02%) |      45   →      38    (-15.56%) |      233.06 μs →      196.84 μs  (-15.54%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.08 s  →        2.06 s    (-0.70%) |      45   →      38    (-15.56%) |       93.42 s  →       78.34 s   (-16.14%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       56.04 ms →       61.06 ms   (+8.96%) |      45   →      38    (-15.56%) |        2.52 s  →        2.32 s    (-7.99%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.03 ms →        4.78 ms  (+18.59%) |     270   →     228    (-15.56%) |        1.09 s  →        1.09 s    (+0.14%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.64 ms →        1.65 ms   (+0.76%) |      45   →      38    (-15.56%) |       73.60 ms →       62.62 ms  (-14.92%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      419.01 μs →      417.68 μs   (-0.32%) |      45   →      38    (-15.56%) |       18.86 ms →       15.87 ms  (-15.82%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      959.33 μs →      972.90 μs   (+1.41%) |      45   →      38    (-15.56%) |       43.17 ms →       36.97 ms  (-14.36%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.99 s  →        1.97 s    (-0.98%) |      45   →      38    (-15.56%) |       89.74 s  →       75.04 s   (-16.38%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      194.63 ms →      211.99 ms   (+8.92%) |     245   →     201    (-17.96%) |       47.68 s  →       42.61 s   (-10.64%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      137.44 ms →      150.23 ms   (+9.31%) |     245   →     201    (-17.96%) |       33.67 s  →       30.20 s   (-10.32%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       25.60 ms →       27.40 ms   (+7.01%) |     245   →     201    (-17.96%) |        6.27 s  →        5.51 s   (-12.21%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      589.70 μs →      720.34 μs  (+22.15%) |     245   →     201    (-17.96%) |      144.48 ms →      144.79 ms   (+0.22%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.20 ms →        3.80 ms  (+18.75%) |      45   →      38    (-15.56%) |      143.93 ms →      144.33 ms   (+0.28%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.01 ms →       22.27 ms   (+5.98%) |     245   →     201    (-17.96%) |        5.15 s  →        4.48 s   (-13.05%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      585.23 μs →      713.98 μs  (+22.00%) |     245   →     201    (-17.96%) |      143.38 ms →      143.51 ms   (+0.09%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.17 ms →        3.76 ms  (+18.60%) |      45   →      38    (-15.56%) |      142.70 ms →      142.92 ms   (+0.16%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       31.27 ms →       33.91 ms   (+8.45%) |     245   →     201    (-17.96%) |        7.66 s  →        6.82 s   (-11.03%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       19.86 ms →       21.32 ms   (+7.31%) |     245   →     201    (-17.96%) |        4.87 s  →        4.28 s   (-11.97%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.61 ms →        2.65 ms   (+1.53%) |     245   →     201    (-17.96%) |      639.04 ms →      532.29 ms  (-16.70%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.60 ms →       22.11 ms   (+7.31%) |     245   →     201    (-17.96%) |        5.05 s  →        4.44 s   (-11.96%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.48 ms →        2.18 ms  (-12.22%) |     245   →     201    (-17.96%) |      607.10 ms →      437.19 ms  (-27.99%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       16.98 ms →       18.49 ms   (+8.90%) |     490   →     402    (-17.96%) |        8.32 s  →        7.43 s   (-10.66%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       52.24 ms →       56.21 ms   (+7.62%) |     245   →     201    (-17.96%) |       12.80 s  →       11.30 s   (-11.71%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |       12.29 ms →       12.79 ms   (+4.06%) |     445   →     364    (-18.20%) |        5.47 s  →        4.66 s   (-14.88%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       60.02 ns →       45.07 ns  (-24.91%) |     445   →     364    (-18.20%) |       26.71 μs →       16.40 μs  (-38.58%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        8.67 ms →        9.33 ms   (+7.60%) |     445   →     364    (-18.20%) |        3.86 s  →        3.40 s   (-11.99%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       70.03 ns →       36.91 ns  (-47.30%) |     445   →     364    (-18.20%) |       31.17 μs →       13.43 μs  (-56.89%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        2.93 ms →        3.18 ms   (+8.58%) |     245   →     201    (-17.96%) |      716.73 ms →      638.46 ms  (-10.92%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       14.34 ms →       15.65 ms   (+9.16%) |     245   →     201    (-17.96%) |        3.51 s  →        3.15 s   (-10.44%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |       15.48 ms →       17.53 ms  (+13.22%) |     200   →     163    (-18.50%) |        3.10 s  →        2.86 s    (-7.73%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.12 ms →        5.83 ms  (+13.70%) |     600   →     489    (-18.50%) |        3.07 s  →        2.85 s    (-7.33%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       19.61 ms →       20.28 ms   (+3.40%) |     245   →     201    (-17.96%) |        4.80 s  →        4.08 s   (-15.17%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |       18.27 ms →       19.21 ms   (+5.15%) |     245   →     201    (-17.96%) |        4.47 s  →        3.86 s   (-13.74%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       68.86 ns →      120.56 ns  (+75.08%) |     245   →     201    (-17.96%) |       16.87 μs →       24.23 μs  (+43.64%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       14.77 ms →       15.77 ms   (+6.77%) |     245   →     201    (-17.96%) |        3.62 s  →        3.17 s   (-12.41%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       27.39 ns →       20.84 ns  (-23.93%) |     245   →     201    (-17.96%) |        6.71 μs →        4.19 μs  (-37.59%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       67.98 ms →       47.66 ms  (-29.89%) |     245   →     201    (-17.96%) |       16.65 s  →        9.58 s   (-42.48%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       16.69 ms →       16.71 ms   (+0.15%) |     239   →     196    (-17.99%) |        3.99 s  →        3.28 s   (-17.87%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       17.10 ms →       17.68 ms   (+3.42%) |     208   →     164    (-21.15%) |        3.56 s  →        2.90 s   (-18.46%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        7.57 ms →        8.05 ms   (+6.27%) |     416   →     328    (-21.15%) |        3.15 s  →        2.64 s   (-16.21%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.42 ms →        1.55 ms   (+9.23%) |     208   →     164    (-21.15%) |      296.08 ms →      255.01 ms  (-13.87%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       63.31 ms →       52.35 ms  (-17.31%) |      60   →      80    (+33.33%) |        3.80 s  →        4.19 s   (+10.25%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       50.09 ms →       33.36 ms  (-33.40%) |      75   →     122    (+62.67%) |        3.76 s  →        4.07 s    (+8.34%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |       40.69 ms →       24.44 ms  (-39.95%) |      90   →     164    (+82.22%) |        3.66 s  →        4.01 s    (+9.43%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      593.36 ns →      543.24 ns   (-8.45%) |      45   →      38    (-15.56%) |       26.70 μs →       20.64 μs  (-22.69%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       40.09 μs →       24.44 μs  (-39.05%) |      45   →      38    (-15.56%) |        1.80 ms →      928.58 μs  (-48.53%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.50 ms →        3.57 ms   (+2.16%) |      45   →      38    (-15.56%) |      157.42 ms →      135.80 ms  (-13.73%) | 
+ │ │ ├ sirius::Density::generate                                       |      298.87 ms →      293.30 ms   (-1.86%) |      45   →      38    (-15.56%) |       13.45 s  →       11.15 s   (-17.13%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      294.91 ms →      289.39 ms   (-1.87%) |      45   →      38    (-15.56%) |       13.27 s  →       11.00 s   (-17.13%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.58 ms →       66.91 ms   (-3.84%) |      45   →      38    (-15.56%) |        3.13 s  →        2.54 s   (-18.80%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       60.23 μs →       71.13 μs  (+18.10%) |      45   →      38    (-15.56%) |        2.71 ms →        2.70 ms   (-0.27%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms →        1.21 ms   (+2.05%) |       2   →       2              |        2.36 ms →        2.41 ms   (+2.05%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       58.25 ms →       55.66 ms   (-4.43%) |      45   →      38    (-15.56%) |        2.62 s  →        2.12 s   (-19.30%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.31 ms →       59.88 ms   (-2.32%) |      45   →      38    (-15.56%) |        2.76 s  →        2.28 s   (-17.52%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.56 μs →        9.55 μs   (-0.06%) |      45   →      38    (-15.56%) |      430.01 μs →      362.90 μs  (-15.61%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (+0.14%) |      45   →      38    (-15.56%) |      103.79 ms →       87.76 ms  (-15.44%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.45 ms →       57.02 ms   (-2.45%) |      45   →      38    (-15.56%) |        2.63 s  →        2.17 s   (-17.62%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.01 ms →        5.59 ms  (-20.30%) |      45   →      38    (-15.56%) |      315.64 ms →      212.44 ms  (-32.70%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      819.02 ns →      771.68 ns   (-5.78%) |      45   →      38    (-15.56%) |       36.86 μs →       29.32 μs  (-20.44%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.15 ms →      104.32 ms   (+0.16%) |      45   →      38    (-15.56%) |        4.69 s  →        3.96 s   (-15.42%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.40 ms   (-0.60%) |      45   →      38    (-15.56%) |      108.75 ms →       91.28 ms  (-16.07%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.08 ms   (+0.16%) |      45   →      38    (-15.56%) |      902.15 ms →      763.01 ms  (-15.42%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms →       19.91 ms   (+0.12%) |      45   →      38    (-15.56%) |      894.87 ms →      756.60 ms  (-15.45%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      243.40 ns →      331.95 ns  (+36.38%) |      45   →      38    (-15.56%) |       10.95 μs →       12.61 μs  (+15.16%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.25 ms   (-0.11%) |      45   →      38    (-15.56%) |       56.47 ms →       47.63 ms  (-15.65%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.70 ms →        2.65 ms   (-1.81%) |      45   →      38    (-15.56%) |      121.57 ms →      100.81 ms  (-17.08%) | 
+ │ │ ├ sirius::Density::mix                                            |      131.81 ms →      128.35 ms   (-2.63%) |      45   →      38    (-15.56%) |        5.93 s  →        4.88 s   (-17.77%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      258.16 μs →      256.39 μs   (-0.68%) |      45   →      38    (-15.56%) |       11.62 ms →        9.74 ms  (-16.13%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.23 ms →        3.25 ms   (+0.62%) |      45   →      38    (-15.56%) |      145.46 ms →      123.60 ms  (-15.03%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.04 ms →        3.06 ms   (+0.85%) |      45   →      38    (-15.56%) |      136.66 ms →      116.38 ms  (-14.84%) | 
+ │ │ ├ sirius::Potential::generate                                     |      180.77 ms →      181.45 ms   (+0.38%) |      45   →      38    (-15.56%) |        8.13 s  →        6.90 s   (-15.24%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       64.73 ms →       65.57 ms   (+1.29%) |      45   →      38    (-15.56%) |        2.91 s  →        2.49 s   (-14.46%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.52 ms →       11.37 ms (+223.30%) |      45   →      38    (-15.56%) |      158.23 ms →      431.96 ms (+173.01%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.18 ms →        4.30 ms   (+2.82%) |      45   →      38    (-15.56%) |      188.21 ms →      163.41 ms  (-13.17%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms →        4.09 ms   (+0.38%) |      45   →      38    (-15.56%) |      183.56 ms →      155.60 ms  (-15.23%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.08 ms →        4.09 ms   (+0.38%) |      45   →      38    (-15.56%) |      183.54 ms →      155.58 ms  (-15.23%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      236.99 μs →      255.15 μs   (+7.67%) |      90   →      76    (-15.56%) |       21.33 ms →       19.39 ms   (-9.08%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       90.73 ms →       90.56 ms   (-0.18%) |      45   →      38    (-15.56%) |        4.08 s  →        3.44 s   (-15.71%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       89.68 ms →       89.50 ms   (-0.20%) |      45   →      38    (-15.56%) |        4.04 s  →        3.40 s   (-15.73%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.60 ms →        1.60 ms   (+0.18%) |     225   →     190    (-15.56%) |      359.87 ms →      304.44 ms  (-15.40%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.45 ms →        2.45 ms   (-0.04%) |     405   →     342    (-15.56%) |      991.62 ms →      837.06 ms  (-15.59%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.48 ms →        2.55 ms   (+2.84%) |      45   →      38    (-15.56%) |      111.45 ms →       96.78 ms  (-13.16%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      729.94 μs →      756.01 μs   (+3.57%) |     135   →     114    (-15.56%) |       98.54 ms →       86.18 ms  (-12.54%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.84 ms →        2.83 ms   (-0.46%) |      45   →      38    (-15.56%) |      127.82 ms →      107.45 ms  (-15.94%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.60 ms →        2.60 ms   (-0.01%) |      45   →      38    (-15.56%) |      117.00 ms →       98.80 ms  (-15.56%) | 
+ │ │ │ │   └ sirius::divergence                                        |       19.94 ms →       19.75 ms   (-0.92%) |      45   →      38    (-15.56%) |      897.08 ms →      750.56 ms  (-16.33%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.46 ms →        2.44 ms   (-1.07%) |      45   →      38    (-15.56%) |      110.76 ms →       92.54 ms  (-16.46%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.34 ms →        3.31 ms   (-0.80%) |      45   →      38    (-15.56%) |      150.28 ms →      125.89 ms  (-16.23%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.95 ms →       20.93 ms   (-0.10%) |      45   →      38    (-15.56%) |      942.63 ms →      795.17 ms  (-15.64%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      319.78 ns →      229.13 ns  (-28.35%) |      45   →      38    (-15.56%) |       14.39 μs →        8.71 μs  (-39.49%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      237.44 ns →      348.95 ns  (+46.96%) |      45   →      38    (-15.56%) |       10.69 μs →       13.26 μs  (+24.10%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.31 ms →        2.23 ms   (-3.74%) |      45   →      38    (-15.56%) |      104.06 ms →       84.59 ms  (-18.71%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.08 ms →        4.08 ms   (-0.02%) |     315   →     266    (-15.56%) |        1.28 s  →        1.08 s   (-15.57%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.91 ms →        3.93 ms   (+0.52%) |     315   →     266    (-15.56%) |        1.23 s  →        1.04 s   (-15.11%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.91 ms →        3.93 ms   (+0.52%) |     315   →     266    (-15.56%) |        1.23 s  →        1.04 s   (-15.11%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.46 ms →        4.20 ms   (-5.98%) |     135   →     114    (-15.56%) |      602.68 ms →      478.48 ms  (-20.61%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.22 ms →        4.07 ms   (-3.55%) |     135   →     114    (-15.56%) |      569.59 ms →      463.90 ms  (-18.55%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.04 ms →        4.12 ms   (+2.11%) |      45   →      38    (-15.56%) |      181.75 ms →      156.72 ms  (-13.77%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      159.06 μs →      104.39 μs  (-34.37%) |      45   →      38    (-15.56%) |        7.16 ms →        3.97 ms  (-44.58%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      155.58 μs →      100.42 μs  (-35.45%) |      45   →      38    (-15.56%) |        7.00 ms →        3.82 ms  (-45.49%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.51 ms →        5.46 ms   (-0.96%) |       2   →       2              |       11.03 ms →       10.92 ms   (-0.96%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.00 ms →        4.21 ms   (+5.01%) |       6   →       6              |       24.03 ms →       25.23 ms   (+5.01%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.98 ms →        4.06 ms   (+1.96%) |       6   →       6              |       23.89 ms →       24.36 ms   (+1.96%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.98 ms →        4.06 ms   (+1.96%) |       6   →       6              |       23.89 ms →       24.36 ms   (+1.96%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.33 ms →        4.26 ms   (-1.49%) |       3   →       3              |       12.98 ms →       12.79 ms   (-1.49%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.31 ms →        4.08 ms   (-5.51%) |       3   →       3              |       12.94 ms →       12.23 ms   (-5.51%) | 
  ├ sirius::Periodic_function|inner                                     |        3.92 ms →        3.95 ms   (+0.71%) |       2   →       2              |        7.85 ms →        7.91 ms   (+0.71%) | 
  │ └ sirius::Periodic_function|inner_local                             |        3.88 ms →        3.91 ms   (+0.71%) |       2   →       2              |        7.76 ms →        7.82 ms   (+0.71%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.88 ms →        3.91 ms   (+0.71%) |       2   →       2              |        7.76 ms →        7.82 ms   (+0.71%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.37 ms →        4.08 ms   (-6.63%) |       1   →       1              |        4.37 ms →        4.08 ms   (-6.63%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.36 ms →        4.04 ms   (-7.18%) |       1   →       1              |        4.36 ms →        4.04 ms   (-7.18%) | 
- └ sirius::finalize                                                    |      266.33 ms →      342.09 ms  (+28.45%) |       1   →       1              |      266.33 ms →      342.09 ms  (+28.45%) | 
  ====================================================================================================================================================================================================
```
