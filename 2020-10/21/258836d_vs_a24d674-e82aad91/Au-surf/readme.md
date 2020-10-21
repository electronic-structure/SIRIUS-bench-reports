# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      144.62 s  →      112.35 s   (-22.31%) |       1   →       1              |      144.62 s  →      112.35 s   (-22.31%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.64 s    (-0.19%) |       1   →       1              |        2.65 s  →        2.64 s    (-0.19%) | 
  ├ sirius::Simulation_context::initialize                              |        2.14 s  →        2.08 s    (-2.46%) |       1   →       1              |        2.14 s  →        2.08 s    (-2.46%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       86.69 ms →       26.59 ms  (-69.33%) |       1   →       1              |       86.69 ms →       26.59 ms  (-69.33%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       42.75 ms →       47.00 ms   (+9.94%) |       1   →       1              |       42.75 ms →       47.00 ms   (+9.94%) | 
- │ │ ├ sirius::Atom_type::init                                         |       17.70 ms →       21.75 ms  (+22.89%) |       1   →       1              |       17.70 ms →       21.75 ms  (+22.89%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.99 ms →       25.18 ms   (+0.79%) |       1   →       1              |       24.99 ms →       25.18 ms   (+0.79%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.46 ms →       10.12 ms   (-3.23%) |       1   →       1              |       10.46 ms →       10.12 ms   (-3.23%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.50 ms →       15.03 ms   (+3.64%) |       1   →       1              |       14.50 ms →       15.03 ms   (+3.64%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.16 ms →       14.45 ms   (+2.02%) |       1   →       1              |       14.16 ms →       14.45 ms   (+2.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       13.93 ms →       14.20 ms   (+1.95%) |       1   →       1              |       13.93 ms →       14.20 ms   (+1.95%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      214.59 μs →      225.73 μs   (+5.19%) |       1   →       1              |      214.59 μs →      225.73 μs   (+5.19%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.44 μs →        2.36 μs   (-3.16%) |       1   →       1              |        2.44 μs →        2.36 μs   (-3.16%) | 
  │ └ sirius::Simulation_context::update                                |        1.95 s  →        1.96 s    (+0.26%) |       1   →       1              |        1.95 s  →        1.96 s    (+0.26%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.42 ms →       12.79 ms   (+2.96%) |       1   →       1              |       12.42 ms →       12.79 ms   (+2.96%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.93 ms →        8.19 ms   (+3.37%) |       1   →       1              |        7.93 ms →        8.19 ms   (+3.37%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.47 ms →        4.57 ms   (+2.24%) |       1   →       1              |        4.47 ms →        4.57 ms   (+2.24%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.17 ms →        4.15 ms   (-0.29%) |       1   →       1              |        4.17 ms →        4.15 ms   (-0.29%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.95 ms →        3.95 ms   (+0.02%) |       1   →       1              |        3.95 ms →        3.95 ms   (+0.02%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      215.13 μs →      202.68 μs   (-5.79%) |       1   →       1              |      215.13 μs →      202.68 μs   (-5.79%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.30 μs →        1.22 μs   (-6.46%) |       1   →       1              |        1.30 μs →        1.22 μs   (-6.46%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.79 ms →       14.95 ms   (-5.27%) |       2   →       2              |       31.57 ms →       29.91 ms   (-5.27%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.09 ms   (-1.31%) |       2   →       2              |        2.20 ms →        2.17 ms   (-1.31%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      959.36 μs →      951.43 μs   (-0.83%) |       1   →       1              |      959.36 μs →      951.43 μs   (-0.83%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.09 ms →        5.08 ms   (-0.13%) |       2   →       2              |       10.18 ms →       10.17 ms   (-0.13%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.64 ms   (-0.27%) |       2   →       2              |        7.30 ms →        7.28 ms   (-0.27%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.79 ms →       15.63 ms   (-0.98%) |       4   →       4              |       63.15 ms →       62.53 ms   (-0.98%) | 
  │   ├ sddk::Gvec::init                                                |      161.48 ms →      165.82 ms   (+2.68%) |       2   →       2              |      322.97 ms →      331.63 ms   (+2.68%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      126.15 ms →      131.82 ms   (+4.49%) |       2   →       2              |      252.30 ms →      263.64 ms   (+4.49%) | 
+ │   ├ sddk::Gvec_shells                                               |      144.98 ms →      122.53 ms  (-15.48%) |       1   →       1              |      144.98 ms →      122.53 ms  (-15.48%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.04 ms   (+1.66%) |       1   →       1              |        1.03 ms →        1.04 ms   (+1.66%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      220.22 ms →      219.16 ms   (-0.48%) |       1   →       1              |      220.22 ms →      219.16 ms   (-0.48%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       30.54 ms →       26.06 ms  (-14.68%) |       1   →       1              |       30.54 ms →       26.06 ms  (-14.68%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.01 μs →        1.76 μs  (-12.16%) |       2   →       2              |        4.01 μs →        3.53 μs  (-12.16%) | 
+ │ └ sirius::K_point_set::initialize                                   |       30.51 ms →       26.02 ms  (-14.73%) |       1   →       1              |       30.51 ms →       26.02 ms  (-14.73%) | 
+ │   └ sirius::K_point::initialize                                     |       30.45 ms →       25.95 ms  (-14.79%) |       1   →       1              |       30.45 ms →       25.95 ms  (-14.79%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       22.84 ms →       19.43 ms  (-14.93%) |       1   →       1              |       22.84 ms →       19.43 ms  (-14.93%) | 
+ │     │ └ sddk::Gvec::init                                            |        5.59 ms →        4.98 ms  (-10.89%) |       1   →       1              |        5.59 ms →        4.98 ms  (-10.89%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |       11.37 μs →       12.80 μs  (+12.52%) |       1   →       1              |       11.37 μs →       12.80 μs  (+12.52%) | 
  │     └ sirius::K_point::update                                       |        4.59 ms →        4.17 ms   (-9.25%) |       1   →       1              |        4.59 ms →        4.17 ms   (-9.25%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.71 ms   (-2.71%) |       1   →       1              |        1.76 ms →        1.71 ms   (-2.71%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      909.97 μs →      897.05 μs   (-1.42%) |       1   →       1              |      909.97 μs →      897.05 μs   (-1.42%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.25 ms →        1.51 ms  (-32.84%) |       2   →       2              |        4.49 ms →        3.02 ms  (-32.84%) | 
  ├ sirius::Potential                                                   |       95.71 ms →       87.91 ms   (-8.15%) |       1   →       1              |       95.71 ms →       87.91 ms   (-8.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.47 ms   (+0.12%) |       6   →       6              |       14.82 ms →       14.83 ms   (+0.12%) | 
  │ └ sirius::Potential::update                                         |       80.56 ms →       72.74 ms   (-9.71%) |       1   →       1              |       80.56 ms →       72.74 ms   (-9.71%) | 
  │   └ sirius::Potential::generate_local_potential                     |       80.38 ms →       72.56 ms   (-9.73%) |       1   →       1              |       80.38 ms →       72.56 ms   (-9.73%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.91 ms →       50.13 ms   (-7.01%) |       1   →       1              |       53.91 ms →       50.13 ms   (-7.01%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       26.27 ms →       13.27 ms  (-49.50%) |       1   →       1              |       26.27 ms →       13.27 ms  (-49.50%) | 
  ├ sirius::Density                                                     |       71.77 ms →       75.71 ms   (+5.48%) |       1   →       1              |       71.77 ms →       75.71 ms   (+5.48%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.79 ms →        5.25 ms   (+9.51%) |       2   →       2              |        9.59 ms →       10.50 ms   (+9.51%) | 
  │ └ sirius::Density::update                                           |       62.16 ms →       65.18 ms   (+4.86%) |       1   →       1              |       62.16 ms →       65.18 ms   (+4.86%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.98 ms →       64.99 ms   (+4.86%) |       1   →       1              |       61.98 ms →       64.99 ms   (+4.86%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.48 ms            |                   1              |                         3.48 ms            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.98 ms →       53.25 ms   (-1.36%) |       1   →       1              |       53.98 ms →       53.25 ms   (-1.36%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.79 ms →        6.90 ms  (-11.43%) |       1   →       1              |        7.79 ms →        6.90 ms  (-11.43%) | 
  ├ sirius::Density::initial_density                                    |       80.45 ms →       78.96 ms   (-1.85%) |       1   →       1              |       80.45 ms →       78.96 ms   (-1.85%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.06 ms →       53.35 ms   (+0.55%) |       1   →       1              |       53.06 ms →       53.35 ms   (+0.55%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.31 ms →        4.69 ms  (-11.59%) |       2   →       2              |       10.61 ms →        9.38 ms  (-11.59%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.08 ms →        4.13 ms  (-18.77%) |       1   →       1              |        5.08 ms →        4.13 ms  (-18.77%) | 
  ├ sirius::Potential::generate                                         |      191.84 ms →      187.78 ms   (-2.12%) |       1   →       1              |      191.84 ms →      187.78 ms   (-2.12%) | 
  │ ├ sirius::Potential::poisson                                        |       64.80 ms →       63.83 ms   (-1.50%) |       1   →       1              |       64.80 ms →       63.83 ms   (-1.50%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       10.08 ms →        8.71 ms  (-13.63%) |       1   →       1              |       10.08 ms →        8.71 ms  (-13.63%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.29 ms →        4.28 ms   (-0.15%) |       1   →       1              |        4.29 ms →        4.28 ms   (-0.15%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.08 ms →        4.27 ms   (+4.62%) |       1   →       1              |        4.08 ms →        4.27 ms   (+4.62%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        4.27 ms   (+4.63%) |       1   →       1              |        4.08 ms →        4.27 ms   (+4.63%) | 
  │ ├ sirius::Periodic_function::add                                    |      245.47 μs →      233.15 μs   (-5.02%) |       2   →       2              |      490.95 μs →      466.30 μs   (-5.02%) | 
  │ ├ sirius::Potential::xc                                             |      100.63 ms →       97.27 ms   (-3.33%) |       1   →       1              |      100.63 ms →       97.27 ms   (-3.33%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      100.63 ms →       96.22 ms   (-4.38%) |       1   →       1              |      100.63 ms →       96.22 ms   (-4.38%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.32 ms →        2.09 ms   (-9.93%) |       5   →       5              |       11.58 ms →       10.43 ms   (-9.93%) | 
+ │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.61 ms →        2.33 ms  (-10.53%) |       9   →       9              |       23.46 ms →       20.99 ms  (-10.53%) | 
  │ │   ├ sirius::gradient                                              |        7.60 ms →        7.73 ms   (+1.68%) |       1   →       1              |        7.60 ms →        7.73 ms   (+1.68%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.44 ms →        2.48 ms   (+1.54%) |       3   →       3              |        7.32 ms →        7.44 ms   (+1.54%) | 
  │ │   ├ sirius::dot                                                   |        2.86 ms →        2.84 ms   (-0.68%) |       1   →       1              |        2.86 ms →        2.84 ms   (-0.68%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.64 ms →        2.63 ms   (-0.32%) |       1   →       1              |        2.64 ms →        2.63 ms   (-0.32%) | 
  │ │   └ sirius::divergence                                            |       22.49 ms →       21.16 ms   (-5.91%) |       1   →       1              |       22.49 ms →       21.16 ms   (-5.91%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.46 ms →        2.64 ms   (+7.36%) |       1   →       1              |        2.46 ms →        2.64 ms   (+7.36%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.20 ms →        3.45 ms   (+7.58%) |       1   →       1              |        3.20 ms →        3.45 ms   (+7.58%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.17 ms →       22.18 ms   (+0.04%) |       1   →       1              |       22.17 ms →       22.18 ms   (+0.04%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      123.00 ns →      147.00 ns  (+19.51%) |       1   →       1              |      123.00 ns →      147.00 ns  (+19.51%) | 
  ├ sirius::Hamiltonian0                                                |       13.83 ms →       13.99 ms   (+1.13%) |       1   →       1              |       13.83 ms →       13.99 ms   (+1.13%) | 
  │ ├ sirius::Local_operator                                            |       13.51 ms →       13.67 ms   (+1.20%) |       1   →       1              |       13.51 ms →       13.67 ms   (+1.20%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.15 ms →        7.45 ms   (+4.32%) |       1   →       1              |        7.15 ms →        7.45 ms   (+4.32%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.89 ms →        4.77 ms   (-2.52%) |       1   →       1              |        4.89 ms →        4.77 ms   (-2.52%) | 
  │ ├ sirius::Non_local_operator                                        |       60.41 μs →       60.02 μs   (-0.64%) |       2   →       2              |      120.83 μs →      120.05 μs   (-0.64%) | 
  │ ├ sirius::D_operator::initialize                                    |       78.98 μs →       76.85 μs   (-2.69%) |       1   →       1              |       78.98 μs →       76.85 μs   (-2.69%) | 
  │ └ sirius::Q_operator::initialize                                    |       66.85 μs →       66.37 μs   (-0.72%) |       1   →       1              |       66.85 μs →       66.37 μs   (-0.72%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.18 s  →        2.46 s   (+13.14%) |       1   →       1              |        2.18 s  →        2.46 s   (+13.14%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.36 ms →        8.36 ms   (-0.08%) |       1   →       1              |        8.36 ms →        8.36 ms   (-0.08%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      244.31 μs →      238.57 μs   (-2.35%) |       1   →       1              |      244.31 μs →      238.57 μs   (-2.35%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.12 ms →        8.12 ms   (-0.01%) |       1   →       1              |        8.12 ms →        8.12 ms   (-0.01%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.17 s  →        2.45 s   (+13.20%) |       1   →       1              |        2.17 s  →        2.45 s   (+13.20%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       87.67 ms →       90.63 ms   (+3.37%) |       4   →       4              |      350.70 ms →      362.52 ms   (+3.37%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.17 ms →       25.08 ms   (-0.39%) |       1   →       1              |       25.17 ms →       25.08 ms   (-0.39%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.36 ms →       14.36 ms   (+0.01%) |       1   →       1              |       14.36 ms →       14.36 ms   (+0.01%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.19 s  →        1.20 s    (+0.39%) |       1   →       1              |        1.19 s  →        1.20 s    (+0.39%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      970.06 ms →      973.63 ms   (+0.37%) |       1   →       1              |      970.06 ms →      973.63 ms   (+0.37%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      302.39 ms →      303.83 ms   (+0.48%) |       1   →       1              |      302.39 ms →      303.83 ms   (+0.48%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      174.23 ms →      176.11 ms   (+1.08%) |       1   →       1              |      174.23 ms →      176.11 ms   (+1.08%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      174.22 ms →      176.11 ms   (+1.08%) |       1   →       1              |      174.22 ms →      176.11 ms   (+1.08%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      109.74 ms →      109.27 ms   (-0.43%) |       1   →       1              |      109.74 ms →      109.27 ms   (-0.43%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      172.84 ms →      175.80 ms   (+1.71%) |       1   →       1              |      172.84 ms →      175.80 ms   (+1.71%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      172.83 ms →      175.80 ms   (+1.71%) |       1   →       1              |      172.83 ms →      175.80 ms   (+1.71%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      163.11 ms →      161.86 ms   (-0.77%) |       1   →       1              |      163.11 ms →      161.86 ms   (-0.77%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      112.59 ms →      111.37 ms   (-1.08%) |       1   →       1              |      112.59 ms →      111.37 ms   (-1.08%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.74 ms →        3.74 ms   (-0.18%) |       1   →       1              |        3.74 ms →        3.74 ms   (-0.18%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       88.76 ms →       89.74 ms   (+1.10%) |       1   →       1              |       88.76 ms →       89.74 ms   (+1.10%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.23 ms →       12.01 ms   (+6.96%) |       1   →       1              |       11.23 ms →       12.01 ms   (+6.96%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.22 ms →       64.27 ms   (+0.08%) |       2   →       2              |      128.43 ms →      128.53 ms   (+0.08%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       58.32 ms →      190.19 ms (+226.14%) |       2   →       2              |      116.63 ms →      380.38 ms (+226.14%) | 
  │ │ │ ├ sddk::inner                                                   |       58.18 ms                             |       2                          |      116.36 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       19.89 μs                             |       2                          |       39.77 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.54 ms                             |       4                          |      102.16 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      689.52 μs                             |       4                          |        2.76 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        5.69 ms                             |       2                          |       11.38 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                       190.09 ms            |                   2              |                       380.18 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        32.00 ns            |                   2              |                        64.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                       188.55 ms            |                   2              |                       377.09 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        32.00 ns            |                   2              |                        64.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.13 ms →      115.34 ms   (-0.68%) |       1   →       1              |      116.13 ms →      115.34 ms   (-0.68%) | 
  │ │ ├ sddk::transform                                                 |       36.01 ms                             |       1                          |       36.01 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.41 μs                             |       1                          |       14.41 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.91 μs                             |       1                          |       18.91 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        36.51 ms            |                   1              |                        36.51 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.68 ms            |                   1              |                        35.68 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      560.00 ns →      551.00 ns   (-1.61%) |       1   →       1              |      560.00 ns →      551.00 ns   (-1.61%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      135.94 s  →      103.61 s   (-23.78%) |       1   →       1              |      135.94 s  →      103.61 s   (-23.78%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.16 ms →        2.17 ms   (+0.17%) |      31   →      31              |       67.07 ms →       67.18 ms   (+0.17%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.15 s  →        2.72 s   (-13.76%) |      43   →      38    (-11.63%) |      135.63 s  →      103.37 s   (-23.79%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        7.10 ms →        7.08 ms   (-0.33%) |      43   →      38    (-11.63%) |      305.38 ms →      268.98 ms  (-11.92%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        6.77 ms →        6.74 ms   (-0.34%) |      43   →      38    (-11.63%) |      291.02 ms →      256.30 ms  (-11.93%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.51 ms →        1.49 ms   (-1.69%) |      43   →      38    (-11.63%) |       65.14 ms →       56.59 ms  (-13.12%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.77 ms →        3.80 ms   (+0.73%) |      43   →      38    (-11.63%) |      162.26 ms →      144.44 ms  (-10.99%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       61.26 μs →       60.69 μs   (-0.93%) |      86   →      76    (-11.63%) |        5.27 ms →        4.61 ms  (-12.45%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |       79.79 μs →       81.75 μs   (+2.47%) |      43   →      38    (-11.63%) |        3.43 ms →        3.11 ms   (-9.45%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       68.21 μs →       68.56 μs   (+0.53%) |      43   →      38    (-11.63%) |        2.93 ms →        2.61 ms  (-11.16%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.48 s  →        2.06 s   (-16.66%) |      43   →      38    (-11.63%) |      106.48 s  →       78.42 s   (-26.35%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      213.69 μs →      211.47 μs   (-1.04%) |      43   →      38    (-11.63%) |        9.19 ms →        8.04 ms  (-12.55%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      205.45 μs →      203.83 μs   (-0.79%) |      43   →      38    (-11.63%) |        8.83 ms →        7.75 ms  (-12.32%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.38 μs →        5.55 μs  (-12.96%) |      43   →      38    (-11.63%) |      274.16 μs →      210.88 μs  (-23.08%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.46 s  →        2.06 s   (-16.34%) |      43   →      38    (-11.63%) |      105.88 s  →       78.28 s   (-26.07%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       68.95 ms →       61.43 ms  (-10.91%) |      43   →      38    (-11.63%) |        2.96 s  →        2.33 s   (-21.27%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.44 ms →        4.89 ms  (-10.04%) |     258   →     228    (-11.63%) |        1.40 s  →        1.12 s   (-20.50%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.00 ms →        1.63 ms  (-18.65%) |      43   →      38    (-11.63%) |       86.19 ms →       61.96 ms  (-28.11%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      417.15 μs →      417.43 μs   (+0.07%) |      43   →      38    (-11.63%) |       17.94 ms →       15.86 ms  (-11.57%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      939.90 μs →      956.94 μs   (+1.81%) |      43   →      38    (-11.63%) |       40.42 ms →       36.36 ms  (-10.03%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.37 s  →        1.97 s   (-16.66%) |      43   →      38    (-11.63%) |      101.79 s  →       74.97 s   (-26.35%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.30 ms →      211.14 ms   (-1.47%) |     208   →     201     (-3.37%) |       44.57 s  →       42.44 s    (-4.79%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.62 ms →      149.27 ms   (-1.55%) |     208   →     201     (-3.37%) |       31.54 s  →       30.00 s    (-4.86%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       26.62 ms →       26.79 ms   (+0.66%) |     208   →     201     (-3.37%) |        5.54 s  →        5.39 s    (-2.73%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      682.36 μs →      694.43 μs   (+1.77%) |     208   →     201     (-3.37%) |      141.93 ms →      139.58 ms   (-1.66%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.29 ms →        3.66 ms  (+11.26%) |      43   →      38    (-11.63%) |      141.48 ms →      139.10 ms   (-1.68%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.45 ms →       21.71 ms   (+1.20%) |     208   →     201     (-3.37%) |        4.46 s  →        4.36 s    (-2.21%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      676.42 μs →      691.52 μs   (+2.23%) |     208   →     201     (-3.37%) |      140.70 ms →      138.99 ms   (-1.21%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.26 ms →        3.64 ms  (+11.70%) |      43   →      38    (-11.63%) |      140.24 ms →      138.43 ms   (-1.29%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.34 ms →       33.39 ms   (-2.78%) |     208   →     201     (-3.37%) |        7.14 s  →        6.71 s    (-6.05%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.55 ms →       20.82 ms   (-3.39%) |     208   →     201     (-3.37%) |        4.48 s  →        4.18 s    (-6.65%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.65 ms   (-0.23%) |     208   →     201     (-3.37%) |      552.14 ms →      532.32 ms   (-3.59%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.41 ms →       22.10 ms   (-1.41%) |     208   →     201     (-3.37%) |        4.66 s  →        4.44 s    (-4.73%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.20 ms →        2.17 ms   (-1.35%) |     208   →     201     (-3.37%) |      457.56 ms →      436.20 ms   (-4.67%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.79 ms →       18.55 ms   (-1.30%) |     416   →     402     (-3.37%) |        7.82 s  →        7.46 s    (-4.62%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       55.54 ms →       56.57 ms   (+1.85%) |     208   →     201     (-3.37%) |       11.55 s  →       11.37 s    (-1.58%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.59 ms                             |     373                          |        3.95 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       20.05 μs                             |     373                          |        7.48 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.50 ms                             |     746                          |        3.35 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      116.17 μs                             |     746                          |       86.66 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.35 ms                             |     373                          |      502.03 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                        12.94 ms            |                 364              |                         4.71 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        80.58 ns            |                 364              |                        29.33 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         9.49 ms            |                 364              |                         3.45 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        36.90 ns            |                 364              |                        13.43 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.15 ms →        3.15 ms   (+0.03%) |     208   →     201     (-3.37%) |      654.98 ms →      633.11 ms   (-3.34%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.29 ms →       15.71 ms   (-3.53%) |     208   →     201     (-3.37%) |        3.39 s  →        3.16 s    (-6.78%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.55 ms                             |     165                          |        3.56 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       31.65 μs                             |     165                          |        5.22 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       56.02 μs                             |     495                          |       27.73 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        17.59 ms            |                 163              |                         2.87 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         5.83 ms            |                 489              |                         2.85 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.27 ms →       20.38 ms   (-8.51%) |     208   →     201     (-3.37%) |        4.63 s  →        4.10 s   (-11.59%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       18.24 ms                             |     208                          |        3.79 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       43.18 μs                             |     208                          |        8.98 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.96 ms                             |     416                          |        3.31 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      221.74 μs                             |     416                          |       92.24 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.82 ms                             |     208                          |      378.64 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        19.30 ms            |                 201              |                         3.88 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       119.80 ns            |                 201              |                        24.08 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        15.85 ms            |                 201              |                         3.19 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        20.72 ns            |                 201              |                         4.16 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      166.80 ms →       48.36 ms  (-71.01%) |     208   →     201     (-3.37%) |       34.69 s  →        9.72 s   (-71.98%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       19.61 ms →       16.16 ms  (-17.58%) |     207   →     196     (-5.31%) |        4.06 s  →        3.17 s   (-21.96%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.08 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.97 μs                             |     171                          |        3.07 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       55.95 μs                             |     342                          |       19.14 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        17.04 ms            |                 164              |                         2.79 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         8.05 ms            |                 328              |                         2.64 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.93 ms →        1.55 ms  (-46.97%) |     171   →     164     (-4.09%) |      501.05 ms →      254.83 ms  (-49.14%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.26 ms →       52.04 ms   (+1.52%) |      44   →      80    (+81.82%) |        2.26 s  →        4.16 s   (+84.58%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.85 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       13.86 μs                             |      45                          |      623.78 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       17.61 μs                             |      46                          |      809.99 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        33.19 ms            |                 122              |                         4.05 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        24.42 ms            |                 164              |                         4.00 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      544.91 ns →      506.63 ns   (-7.02%) |      43   →      38    (-11.63%) |       23.43 μs →       19.25 μs  (-17.84%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.81 μs →       22.82 μs   (+0.02%) |      43   →      38    (-11.63%) |      980.93 μs →      867.05 μs  (-11.61%) | 
! │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.43 ms →        3.59 ms   (+4.59%) |      43   →      38    (-11.63%) |      147.57 ms →      136.39 ms   (-7.58%) | 
+ │ │ ├ sirius::Density::generate                                       |      292.89 ms →      292.04 ms   (-0.29%) |      43   →      38    (-11.63%) |       12.59 s  →       11.10 s   (-11.89%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      288.95 ms →      288.10 ms   (-0.29%) |      43   →      38    (-11.63%) |       12.42 s  →       10.95 s   (-11.89%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       65.73 ms →       65.63 ms   (-0.16%) |      43   →      38    (-11.63%) |        2.83 s  →        2.49 s   (-11.77%) | 
! │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       65.13 μs →       68.98 μs   (+5.90%) |      43   →      38    (-11.63%) |        2.80 ms →        2.62 ms   (-6.41%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.24 ms →        1.16 ms   (-6.22%) |       2   →       2              |        2.48 ms →        2.32 ms   (-6.22%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       54.42 ms →       54.33 ms   (-0.16%) |      43   →      38    (-11.63%) |        2.34 s  →        2.06 s   (-11.77%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       59.79 ms →       59.76 ms   (-0.06%) |      43   →      38    (-11.63%) |        2.57 s  →        2.27 s   (-11.68%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.92 μs →        9.53 μs   (-3.89%) |      43   →      38    (-11.63%) |      426.50 μs →      362.24 μs  (-15.07%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.32 ms   (+0.19%) |      43   →      38    (-11.63%) |       99.54 ms →       88.13 ms  (-11.46%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       56.93 ms →       56.89 ms   (-0.06%) |      43   →      38    (-11.63%) |        2.45 s  →        2.16 s   (-11.68%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.44 ms →        5.48 ms   (+0.65%) |      43   →      38    (-11.63%) |      234.08 ms →      208.21 ms  (-11.05%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      519.84 ns →      784.71 ns  (+50.95%) |      43   →      38    (-11.63%) |       22.35 μs →       29.82 μs  (+33.40%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      105.15 ms →      104.80 ms   (-0.34%) |      43   →      38    (-11.63%) |        4.52 s  →        3.98 s   (-11.92%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.41 ms →        2.40 ms   (-0.47%) |      43   →      38    (-11.63%) |      103.80 ms →       91.30 ms  (-12.04%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       20.11 ms →       20.05 ms   (-0.30%) |      43   →      38    (-11.63%) |      864.83 ms →      761.95 ms  (-11.90%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.91 ms →       19.89 ms   (-0.10%) |      43   →      38    (-11.63%) |      855.99 ms →      755.68 ms  (-11.72%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      221.77 ns →      440.16 ns  (+98.48%) |      43   →      38    (-11.63%) |        9.54 μs →       16.73 μs  (+75.40%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.27 ms →        1.25 ms   (-1.04%) |      43   →      38    (-11.63%) |       54.45 ms →       47.62 ms  (-12.55%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.68 ms →        2.68 ms   (+0.10%) |      43   →      38    (-11.63%) |      115.12 ms →      101.84 ms  (-11.54%) | 
+ │ │ ├ sirius::Density::mix                                            |      143.56 ms →      125.75 ms  (-12.41%) |      43   →      38    (-11.63%) |        6.17 s  →        4.78 s   (-22.59%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      261.92 μs →      260.34 μs   (-0.60%) |      43   →      38    (-11.63%) |       11.26 ms →        9.89 ms  (-12.16%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        2.63 ms →        2.60 ms   (-1.18%) |      43   →      38    (-11.63%) |      113.03 ms →       98.70 ms  (-12.67%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.44 ms →        2.41 ms   (-1.25%) |      43   →      38    (-11.63%) |      104.80 ms →       91.45 ms  (-12.74%) | 
+ │ │ ├ sirius::Potential::generate                                     |      183.05 ms →      179.68 ms   (-1.84%) |      43   →      38    (-11.63%) |        7.87 s  →        6.83 s   (-13.26%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       65.14 ms →       64.29 ms   (-1.31%) |      43   →      38    (-11.63%) |        2.80 s  →        2.44 s   (-12.78%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.99 ms →        9.09 ms   (-9.04%) |      43   →      38    (-11.63%) |      429.70 ms →      345.40 ms  (-19.62%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.53 ms →        4.19 ms   (-7.52%) |      43   →      38    (-11.63%) |      194.64 ms →      159.07 ms  (-18.27%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms →        4.09 ms   (+0.30%) |      43   →      38    (-11.63%) |      175.36 ms →      155.43 ms  (-11.36%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.08 ms →        4.09 ms   (+0.31%) |      43   →      38    (-11.63%) |      175.32 ms →      155.41 ms  (-11.35%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      234.39 μs →      232.36 μs   (-0.87%) |      86   →      76    (-11.63%) |       20.16 ms →       17.66 ms  (-12.40%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       92.69 ms →       90.14 ms   (-2.74%) |      43   →      38    (-11.63%) |        3.99 s  →        3.43 s   (-14.05%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       92.68 ms →       89.11 ms   (-3.85%) |      43   →      38    (-11.63%) |        3.99 s  →        3.39 s   (-15.03%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.58 ms →        1.58 ms   (+0.45%) |     215   →     190    (-11.63%) |      339.12 ms →      301.03 ms  (-11.23%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.49 ms →        2.44 ms   (-1.79%) |     387   →     342    (-11.63%) |      962.52 ms →      835.37 ms  (-13.21%) | 
! │ │ │ │   ├ sirius::gradient                                          |        2.39 ms →        2.45 ms   (+2.41%) |      43   →      38    (-11.63%) |      102.83 ms →       93.06 ms   (-9.49%) | 
! │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      701.54 μs →      722.95 μs   (+3.05%) |     129   →     114    (-11.63%) |       90.50 ms →       82.42 ms   (-8.93%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.85 ms →        2.81 ms   (-1.48%) |      43   →      38    (-11.63%) |      122.50 ms →      106.65 ms  (-12.94%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.60 ms →        2.57 ms   (-1.24%) |      43   →      38    (-11.63%) |      112.00 ms →       97.75 ms  (-12.72%) | 
+ │ │ │ │   └ sirius::divergence                                        |       22.30 ms →       19.64 ms  (-11.93%) |      43   →      38    (-11.63%) |      958.88 ms →      746.30 ms  (-22.17%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.41 ms →        2.41 ms   (-0.03%) |      43   →      38    (-11.63%) |      103.80 ms →       91.71 ms  (-11.65%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.29 ms →        3.31 ms   (+0.52%) |      43   →      38    (-11.63%) |      141.61 ms →      125.80 ms  (-11.17%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.93 ms →       20.93 ms   (-0.01%) |      43   →      38    (-11.63%) |      899.86 ms →      795.17 ms  (-11.63%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      128.09 ns →      208.63 ns  (+62.88%) |      43   →      38    (-11.63%) |        5.51 μs →        7.93 μs  (+43.94%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      232.07 ns →      437.24 ns  (+88.41%) |      43   →      38    (-11.63%) |        9.98 μs →       16.62 μs  (+66.50%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.22 ms →        2.24 ms   (+0.91%) |      43   →      38    (-11.63%) |       95.57 ms →       85.22 ms  (-10.83%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.07 ms →        4.16 ms   (+2.31%) |     301   →     266    (-11.63%) |        1.23 s  →        1.11 s    (-9.59%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.91 ms →        3.94 ms   (+0.75%) |     301   →     266    (-11.63%) |        1.18 s  →        1.05 s   (-10.97%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.91 ms →        3.94 ms   (+0.75%) |     301   →     266    (-11.63%) |        1.18 s  →        1.05 s   (-10.97%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.21 ms →        4.26 ms   (+1.20%) |     129   →     114    (-11.63%) |      542.70 ms →      485.37 ms  (-10.56%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.04 ms →        4.09 ms   (+1.01%) |     129   →     114    (-11.63%) |      521.80 ms →      465.78 ms  (-10.74%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.38 ms →        4.02 ms   (-8.31%) |      43   →      38    (-11.63%) |      188.52 ms →      152.75 ms  (-18.97%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      100.06 μs →       98.57 μs   (-1.48%) |      43   →      38    (-11.63%) |        4.30 ms →        3.75 ms  (-12.94%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |       96.61 μs →       94.61 μs   (-2.07%) |      43   →      38    (-11.63%) |        4.15 ms →        3.60 ms  (-13.46%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.38 ms →        5.26 ms   (-2.20%) |       2   →       2              |       10.75 ms →       10.51 ms   (-2.20%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.00 ms →        3.95 ms   (-1.15%) |       6   →       6              |       23.97 ms →       23.69 ms   (-1.15%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.91 ms →        3.92 ms   (+0.48%) |       6   →       6              |       23.43 ms →       23.55 ms   (+0.48%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.91 ms →        3.92 ms   (+0.48%) |       6   →       6              |       23.43 ms →       23.55 ms   (+0.48%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.23 ms →        4.06 ms   (-4.15%) |       3   →       3              |       12.70 ms →       12.17 ms   (-4.15%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.10 ms →        4.05 ms   (-1.27%) |       3   →       3              |       12.29 ms →       12.14 ms   (-1.27%) | 
  ├ sirius::Periodic_function|inner                                     |        3.96 ms →        4.03 ms   (+1.70%) |       2   →       2              |        7.92 ms →        8.06 ms   (+1.70%) | 
  │ └ sirius::Periodic_function|inner_local                             |        3.95 ms →        4.02 ms   (+1.75%) |       2   →       2              |        7.90 ms →        8.04 ms   (+1.75%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.95 ms →        4.02 ms   (+1.75%) |       2   →       2              |        7.90 ms →        8.04 ms   (+1.75%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.02 ms →        4.11 ms   (+2.43%) |       1   →       1              |        4.02 ms →        4.11 ms   (+2.43%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.01 ms →        4.11 ms   (+2.54%) |       1   →       1              |        4.01 ms →        4.11 ms   (+2.54%) | 
+ └ sirius::finalize                                                    |      329.92 ms →      269.80 ms  (-18.22%) |       1   →       1              |      329.92 ms →      269.80 ms  (-18.22%) | 
  ====================================================================================================================================================================================================
```
