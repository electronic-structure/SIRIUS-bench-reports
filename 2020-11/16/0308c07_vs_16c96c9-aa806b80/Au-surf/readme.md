# Benchmark 16c96c9521ba11c164891eb65cdeac5a4e0e34b3 vs 0308c074b92841e183b2aa72e055c15d8e0ec6ab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      119.39 s  →      302.64 s  (+153.49%) |       1   →       1              |      119.39 s  →      302.64 s  (+153.49%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.70 s    (-1.53%) |       1   →       1              |        2.75 s  →        2.70 s    (-1.53%) | 
  ├ sirius::Simulation_context::initialize                              |        2.14 s  →        2.18 s    (+2.03%) |       1   →       1              |        2.14 s  →        2.18 s    (+2.03%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      111.95 ms →       96.80 ms  (-13.53%) |       1   →       1              |      111.95 ms →       96.80 ms  (-13.53%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       73.80 ms →       87.21 ms  (+18.17%) |       1   →       1              |       73.80 ms →       87.21 ms  (+18.17%) | 
- │ │ ├ sirius::Atom_type::init                                         |       47.88 ms →       62.38 ms  (+30.28%) |       1   →       1              |       47.88 ms →       62.38 ms  (+30.28%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.86 ms →       24.77 ms   (-4.22%) |       1   →       1              |       25.86 ms →       24.77 ms   (-4.22%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.36 ms →       10.25 ms   (-1.12%) |       1   →       1              |       10.36 ms →       10.25 ms   (-1.12%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.47 ms →       14.49 ms   (-6.32%) |       1   →       1              |       15.47 ms →       14.49 ms   (-6.32%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.17 ms →       14.20 ms   (-6.44%) |       1   →       1              |       15.17 ms →       14.20 ms   (-6.44%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.96 ms →       13.96 ms   (-6.65%) |       1   →       1              |       14.96 ms →       13.96 ms   (-6.65%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      203.94 μs →      220.80 μs   (+8.27%) |       1   →       1              |      203.94 μs →      220.80 μs   (+8.27%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.78 μs →        2.72 μs   (-2.26%) |       1   →       1              |        2.78 μs →        2.72 μs   (-2.26%) | 
  │ └ sirius::Simulation_context::update                                |        1.90 s  →        1.94 s    (+2.16%) |       1   →       1              |        1.90 s  →        1.94 s    (+2.16%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.72 ms →       12.85 ms   (+1.05%) |       1   →       1              |       12.72 ms →       12.85 ms   (+1.05%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.28 ms →        8.40 ms   (+1.35%) |       1   →       1              |        8.28 ms →        8.40 ms   (+1.35%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.41 ms →        4.43 ms   (+0.44%) |       1   →       1              |        4.41 ms →        4.43 ms   (+0.44%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.12 ms →        4.14 ms   (+0.26%) |       1   →       1              |        4.12 ms →        4.14 ms   (+0.26%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.92 ms →        3.94 ms   (+0.46%) |       1   →       1              |        3.92 ms →        3.94 ms   (+0.46%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      202.13 μs →      194.29 μs   (-3.88%) |       1   →       1              |      202.13 μs →      194.29 μs   (-3.88%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.12 μs →        1.42 μs  (+26.38%) |       1   →       1              |        1.12 μs →        1.42 μs  (+26.38%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       19.05 ms →       20.07 ms   (+5.35%) |       2   →       2              |       38.11 ms →       40.15 ms   (+5.35%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.16 ms →        1.09 ms   (-6.17%) |       2   →       2              |        2.33 ms →        2.19 ms   (-6.17%) | 
+ │   ├ sirius::Radial_integrals|rho_pseudo                             |        1.23 ms →      950.17 μs  (-22.63%) |       1   →       1              |        1.23 ms →      950.17 μs  (-22.63%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.32 ms →        5.08 ms   (-4.57%) |       2   →       2              |       10.64 ms →       10.16 ms   (-4.57%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.88 ms →        3.64 ms   (-6.20%) |       2   →       2              |        7.76 ms →        7.28 ms   (-6.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.74 ms →       15.90 ms   (+1.04%) |       4   →       4              |       62.96 ms →       63.62 ms   (+1.04%) | 
  │   ├ sddk::Gvec::init                                                |      157.61 ms →      157.94 ms   (+0.21%) |       2   →       2              |      315.23 ms →      315.88 ms   (+0.21%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      125.20 ms →      125.26 ms   (+0.04%) |       2   →       2              |      250.41 ms →      250.52 ms   (+0.04%) | 
  │   ├ sddk::Gvec_shells                                               |      131.88 ms →      129.52 ms   (-1.79%) |       1   →       1              |      131.88 ms →      129.52 ms   (-1.79%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.03 ms   (-0.71%) |       1   →       1              |        1.04 ms →        1.03 ms   (-0.71%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      217.96 ms →      221.59 ms   (+1.66%) |       1   →       1              |      217.96 ms →      221.59 ms   (+1.66%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.80 ms →       27.48 ms   (+6.50%) |       1   →       1              |       25.80 ms →       27.48 ms   (+6.50%) | 
  │ ├ sirius::K_point::K_point                                          |        1.97 μs →        1.91 μs   (-2.82%) |       2   →       2              |        3.94 μs →        3.83 μs   (-2.82%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.76 ms →       27.44 ms   (+6.51%) |       1   →       1              |       25.76 ms →       27.44 ms   (+6.51%) | 
  │   └ sirius::K_point::initialize                                     |       25.71 ms →       27.38 ms   (+6.50%) |       1   →       1              |       25.71 ms →       27.38 ms   (+6.50%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.28 ms →       20.58 ms   (+6.76%) |       1   →       1              |       19.28 ms →       20.58 ms   (+6.76%) | 
  │     │ └ sddk::Gvec::init                                            |        4.97 ms →        5.26 ms   (+5.93%) |       1   →       1              |        4.97 ms →        5.26 ms   (+5.93%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |       10.40 μs →       12.18 μs  (+17.08%) |       1   →       1              |       10.40 μs →       12.18 μs  (+17.08%) | 
  │     └ sirius::K_point::update                                       |        4.09 ms →        4.26 ms   (+4.06%) |       1   →       1              |        4.09 ms →        4.26 ms   (+4.06%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.71 ms   (-0.50%) |       1   →       1              |        1.72 ms →        1.71 ms   (-0.50%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      907.16 μs →      894.21 μs   (-1.43%) |       1   →       1              |      907.16 μs →      894.21 μs   (-1.43%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.46 ms →        1.46 ms   (-0.13%) |       2   →       2              |        2.93 ms →        2.92 ms   (-0.13%) | 
  ├ sirius::Potential                                                   |       96.03 ms →       91.64 ms   (-4.58%) |       1   →       1              |       96.03 ms →       91.64 ms   (-4.58%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.50 ms →        2.48 ms   (-0.63%) |       6   →       6              |       14.99 ms →       14.89 ms   (-0.63%) | 
  │ └ sirius::Potential::update                                         |       80.71 ms →       76.39 ms   (-5.35%) |       1   →       1              |       80.71 ms →       76.39 ms   (-5.35%) | 
  │   └ sirius::Potential::generate_local_potential                     |       80.54 ms →       76.22 ms   (-5.36%) |       1   →       1              |       80.54 ms →       76.22 ms   (-5.36%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       50.03 ms →       51.71 ms   (+3.37%) |       1   →       1              |       50.03 ms →       51.71 ms   (+3.37%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       21.80 ms →       15.72 ms  (-27.89%) |       1   →       1              |       21.80 ms →       15.72 ms  (-27.89%) | 
+ ├ sirius::Density                                                     |       75.26 ms →       67.65 ms  (-10.12%) |       1   →       1              |       75.26 ms →       67.65 ms  (-10.12%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.85 ms →        4.84 ms   (-0.22%) |       2   →       2              |        9.71 ms →        9.69 ms   (-0.22%) | 
+ │ └ sirius::Density::update                                           |       65.44 ms →       57.85 ms  (-11.60%) |       1   →       1              |       65.44 ms →       57.85 ms  (-11.60%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.27 ms →       57.68 ms  (-11.63%) |       1   →       1              |       65.27 ms →       57.68 ms  (-11.63%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        2.38 ms →        2.40 ms   (+0.74%) |       1   →       1              |        2.38 ms →        2.40 ms   (+0.74%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       50.06 ms →       49.88 ms   (-0.38%) |       1   →       1              |       50.06 ms →       49.88 ms   (-0.38%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.56 ms →        4.14 ms  (-64.19%) |       1   →       1              |       11.56 ms →        4.14 ms  (-64.19%) | 
  ├ sirius::Density::initial_density                                    |       79.60 ms →       74.28 ms   (-6.68%) |       1   →       1              |       79.60 ms →       74.28 ms   (-6.68%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.44 ms →       53.21 ms   (-0.43%) |       1   →       1              |       53.44 ms →       53.21 ms   (-0.43%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.08 ms →        2.48 ms  (-51.17%) |       2   →       2              |       10.15 ms →        4.96 ms  (-51.17%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.39 ms →        4.28 ms   (-2.49%) |       1   →       1              |        4.39 ms →        4.28 ms   (-2.49%) | 
  ├ sirius::Potential::generate                                         |      198.49 ms →      182.83 ms   (-7.89%) |       1   →       1              |      198.49 ms →      182.83 ms   (-7.89%) | 
+ │ ├ sirius::Potential::poisson                                        |       64.74 ms →       58.11 ms  (-10.24%) |       1   →       1              |       64.74 ms →       58.11 ms  (-10.24%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.91 ms →        2.59 ms  (-70.95%) |       1   →       1              |        8.91 ms →        2.59 ms  (-70.95%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.59 ms →        4.13 ms   (-9.96%) |       1   →       1              |        4.59 ms →        4.13 ms   (-9.96%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.52 ms →        4.12 ms   (-8.92%) |       1   →       1              |        4.52 ms →        4.12 ms   (-8.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.52 ms →        4.12 ms   (-8.92%) |       1   →       1              |        4.52 ms →        4.12 ms   (-8.92%) | 
  │ ├ sirius::Periodic_function::add                                    |      234.36 μs →      237.85 μs   (+1.49%) |       2   →       2              |      468.72 μs →      475.71 μs   (+1.49%) | 
  │ ├ sirius::Potential::xc                                             |      107.35 ms →       98.20 ms   (-8.53%) |       1   →       1              |      107.35 ms →       98.20 ms   (-8.53%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      106.30 ms →       97.11 ms   (-8.65%) |       1   →       1              |      106.30 ms →       97.11 ms   (-8.65%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.00 ms →        2.04 ms   (+2.24%) |       5   →       5              |        9.98 ms →       10.21 ms   (+2.24%) | 
+ │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        3.65 ms →        2.67 ms  (-26.71%) |       9   →       9              |       32.81 ms →       24.05 ms  (-26.71%) | 
  │ │   ├ sirius::gradient                                              |        8.31 ms →        7.64 ms   (-8.00%) |       1   →       1              |        8.31 ms →        7.64 ms   (-8.00%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.68 ms →        2.45 ms   (-8.33%) |       3   →       3              |        8.03 ms →        7.36 ms   (-8.33%) | 
  │ │   ├ sirius::dot                                                   |        2.83 ms →        2.85 ms   (+0.48%) |       1   →       1              |        2.83 ms →        2.85 ms   (+0.48%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.60 ms →        2.65 ms   (+1.81%) |       1   →       1              |        2.60 ms →        2.65 ms   (+1.81%) | 
  │ │   └ sirius::divergence                                            |       19.62 ms →       19.72 ms   (+0.50%) |       1   →       1              |       19.62 ms →       19.72 ms   (+0.50%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.47 ms   (+2.36%) |       1   →       1              |        2.42 ms →        2.47 ms   (+2.36%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.38 ms →        3.28 ms   (-2.72%) |       1   →       1              |        3.38 ms →        3.28 ms   (-2.72%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.02 ms →       22.19 ms   (+0.81%) |       1   →       1              |       22.02 ms →       22.19 ms   (+0.81%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      215.00 ns →      225.00 ns   (+4.65%) |       1   →       1              |      215.00 ns →      225.00 ns   (+4.65%) | 
  ├ sirius::Hamiltonian0                                                |       14.34 ms →       13.83 ms   (-3.56%) |       1   →       1              |       14.34 ms →       13.83 ms   (-3.56%) | 
  │ ├ sirius::Local_operator                                            |       14.02 ms →       13.51 ms   (-3.67%) |       1   →       1              |       14.02 ms →       13.51 ms   (-3.67%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.19 ms →        7.24 ms   (+0.77%) |       1   →       1              |        7.19 ms →        7.24 ms   (+0.77%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.39 ms →        4.82 ms  (-10.62%) |       1   →       1              |        5.39 ms →        4.82 ms  (-10.62%) | 
  │ ├ sirius::Non_local_operator                                        |       60.20 μs →       61.83 μs   (+2.71%) |       2   →       2              |      120.40 μs →      123.67 μs   (+2.71%) | 
  │ ├ sirius::D_operator::initialize                                    |       79.43 μs →       78.72 μs   (-0.90%) |       1   →       1              |       79.43 μs →       78.72 μs   (-0.90%) | 
  │ └ sirius::Q_operator::initialize                                    |       67.67 μs →       68.04 μs   (+0.55%) |       1   →       1              |       67.67 μs →       68.04 μs   (+0.55%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.47 s  →        2.46 s    (-0.49%) |       1   →       1              |        2.47 s  →        2.46 s    (-0.49%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms →        8.45 ms   (+0.66%) |       1   →       1              |        8.40 ms →        8.45 ms   (+0.66%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      241.24 μs →      249.21 μs   (+3.30%) |       1   →       1              |      241.24 μs →      249.21 μs   (+3.30%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.20 ms   (+0.58%) |       1   →       1              |        8.15 ms →        8.20 ms   (+0.58%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.47 s  →        2.45 s    (-0.49%) |       1   →       1              |        2.47 s  →        2.45 s    (-0.49%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       87.17 ms →       89.76 ms   (+2.97%) |       4   →       4              |      348.67 ms →      359.04 ms   (+2.97%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.65 ms →       25.78 ms   (+0.52%) |       1   →       1              |       25.65 ms →       25.78 ms   (+0.52%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.80 ms →       14.85 ms   (+0.35%) |       1   →       1              |       14.80 ms →       14.85 ms   (+0.35%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.22 s  →        1.20 s    (-1.71%) |       1   →       1              |        1.22 s  →        1.20 s    (-1.71%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      992.45 ms →      975.36 ms   (-1.72%) |       1   →       1              |      992.45 ms →      975.36 ms   (-1.72%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      322.64 ms →      307.41 ms   (-4.72%) |       1   →       1              |      322.64 ms →      307.41 ms   (-4.72%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      175.72 ms →      181.70 ms   (+3.40%) |       1   →       1              |      175.72 ms →      181.70 ms   (+3.40%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      175.72 ms →      181.70 ms   (+3.40%) |       1   →       1              |      175.72 ms →      181.70 ms   (+3.40%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      128.54 ms →      107.23 ms  (-16.58%) |       1   →       1              |      128.54 ms →      107.23 ms  (-16.58%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      170.97 ms →      178.05 ms   (+4.14%) |       1   →       1              |      170.97 ms →      178.05 ms   (+4.14%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      170.97 ms →      178.04 ms   (+4.14%) |       1   →       1              |      170.97 ms →      178.04 ms   (+4.14%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      168.03 ms →      159.36 ms   (-5.16%) |       1   →       1              |      168.03 ms →      159.36 ms   (-5.16%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      117.56 ms →      108.89 ms   (-7.37%) |       1   →       1              |      117.56 ms →      108.89 ms   (-7.37%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.76 ms →        3.75 ms   (-0.42%) |       1   →       1              |        3.76 ms →        3.75 ms   (-0.42%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       93.35 ms →       90.34 ms   (-3.22%) |       1   →       1              |       93.35 ms →       90.34 ms   (-3.22%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       15.68 ms →       12.34 ms  (-21.29%) |       1   →       1              |       15.68 ms →       12.34 ms  (-21.29%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.56 ms →       64.22 ms   (-0.54%) |       2   →       2              |      129.12 ms →      128.43 ms   (-0.54%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      194.21 ms →      192.07 ms   (-1.10%) |       2   →       2              |      388.41 ms →      384.14 ms   (-1.10%) | 
  │ │ │ └ sddk::wf_inner                                                |      194.10 ms →      191.97 ms   (-1.10%) |       2   →       2              |      388.21 ms →      383.93 ms   (-1.10%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       34.50 ns →       51.50 ns  (+49.28%) |       2   →       2              |       69.00 ns →      103.00 ns  (+49.28%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      192.45 ms →      190.15 ms   (-1.20%) |       2   →       2              |      384.91 ms →      380.30 ms   (-1.20%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       32.00 ns →       33.50 ns   (+4.69%) |       2   →       2              |       64.00 ns →       67.00 ns   (+4.69%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      118.44 ms →      116.20 ms   (-1.89%) |       1   →       1              |      118.44 ms →      116.20 ms   (-1.89%) | 
  │ │ └ sddk::wf_trans                                                  |       35.67 ms →       37.12 ms   (+4.06%) |       1   →       1              |       35.67 ms →       37.12 ms   (+4.06%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.65 ms →       35.66 ms   (+0.01%) |       1   →       1              |       35.65 ms →       35.66 ms   (+0.01%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      454.00 ns →      475.00 ns   (+4.63%) |       1   →       1              |      454.00 ns →      475.00 ns   (+4.63%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      110.41 s  →      293.74 s  (+166.06%) |       1   →       1              |      110.41 s  →      293.74 s  (+166.06%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.13 ms →        2.17 ms   (+2.14%) |      29   →      29              |       61.72 ms →       63.04 ms   (+2.14%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.89 s  →        2.92 s    (+1.13%) |      38   →     100   (+163.16%) |      109.84 s  →      292.33 s  (+166.13%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.47 ms →        7.03 ms   (-5.93%) |      38   →     100   (+163.16%) |      283.95 ms →      702.89 ms (+147.54%) | 
- │ │ │ ├ sirius::Local_operator                                        |        7.13 ms →        6.69 ms   (-6.16%) |      38   →     100   (+163.16%) |      271.08 ms →      669.44 ms (+146.95%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.51 ms →        1.51 ms   (+0.01%) |      38   →     100   (+163.16%) |       57.55 ms →      151.45 ms (+163.18%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.16 ms →        3.72 ms  (-10.57%) |      38   →     100   (+163.16%) |      158.25 ms →      372.41 ms (+135.33%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       62.09 μs →       61.91 μs   (-0.28%) |      76   →     200   (+163.16%) |        4.72 ms →       12.38 ms (+162.42%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       83.62 μs →       83.28 μs   (-0.40%) |      38   →     100   (+163.16%) |        3.18 ms →        8.33 ms (+162.11%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       69.98 μs →       69.66 μs   (-0.46%) |      38   →     100   (+163.16%) |        2.66 ms →        6.97 ms (+161.96%) | 
- │ │ ├ sirius::Band::solve                                             |        2.24 s  →        2.33 s    (+3.82%) |      38   →     100   (+163.16%) |       85.17 s  →      232.69 s  (+173.22%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      204.92 μs →      204.28 μs   (-0.31%) |      38   →     100   (+163.16%) |        7.79 ms →       20.43 ms (+162.35%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.88 μs →      197.22 μs   (-0.33%) |      38   →     100   (+163.16%) |        7.52 ms →       19.72 ms (+162.29%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.29 μs →        5.12 μs   (-3.24%) |      38   →     100   (+163.16%) |      201.17 μs →      512.25 μs (+154.64%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.23 s  →        2.31 s    (+3.27%) |      38   →     100   (+163.16%) |       84.84 s  →      230.56 s  (+171.77%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       60.67 ms →       42.61 ms  (-29.77%) |      38   →     100   (+163.16%) |        2.31 s  →        4.26 s   (+84.81%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.65 ms →        1.80 ms  (-61.19%) |     228   →     600   (+163.16%) |        1.06 s  →        1.08 s    (+2.14%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.64 ms →        1.54 ms   (-6.30%) |      38   →     100   (+163.16%) |       62.38 ms →      153.82 ms (+146.58%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      417.71 μs →      417.26 μs   (-0.11%) |      38   →     100   (+163.16%) |       15.87 ms →       41.73 ms (+162.87%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      965.86 μs →      864.25 μs  (-10.52%) |      38   →     100   (+163.16%) |       36.70 ms →       86.43 ms (+135.47%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.15 s  →        2.24 s    (+4.25%) |      38   →     100   (+163.16%) |       81.55 s  →      223.73 s  (+174.34%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      213.25 ms →      267.82 ms  (+25.59%) |     201   →     445   (+121.39%) |       42.86 s  →      119.18 s  (+178.04%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      150.52 ms →      190.08 ms  (+26.28%) |     201   →     445   (+121.39%) |       30.25 s  →       84.58 s  (+179.58%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.65 ms →       33.62 ms  (+21.60%) |     201   →     445   (+121.39%) |        5.56 s  →       14.96 s  (+169.21%) | 
+ │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      699.41 μs →      323.38 μs  (-53.76%) |     201   →     445   (+121.39%) |      140.58 ms →      143.90 ms   (+2.36%) | 
+ │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.69 ms →        1.43 ms  (-61.26%) |      38   →     100   (+163.16%) |      140.11 ms →      142.85 ms   (+1.95%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.54 ms →       27.57 ms  (+22.32%) |     201   →     445   (+121.39%) |        4.53 s  →       12.27 s  (+170.82%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      735.16 μs →      323.98 μs  (-55.93%) |     201   →     445   (+121.39%) |      147.77 ms →      144.17 ms   (-2.43%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.87 ms →        1.43 ms  (-63.13%) |      38   →     100   (+163.16%) |      147.22 ms →      142.86 ms   (-2.97%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.94 ms →       42.87 ms  (+26.31%) |     201   →     445   (+121.39%) |        6.82 s  →       19.08 s  (+179.63%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.36 ms →       26.71 ms  (+25.05%) |     201   →     445   (+121.39%) |        4.29 s  →       11.88 s  (+176.85%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.76 ms   (+4.34%) |     201   →     445   (+121.39%) |      532.22 ms →        1.23 s  (+131.01%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.72 ms →       28.52 ms  (+25.52%) |     201   →     445   (+121.39%) |        4.57 s  →       12.69 s  (+177.90%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.77 ms →        3.20 ms  (+15.33%) |     201   →     445   (+121.39%) |      557.68 ms →        1.42 s  (+155.33%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.67 ms →       23.22 ms  (+24.35%) |     402   →     890   (+121.39%) |        7.51 s  →       20.66 s  (+175.29%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       86.30 ms →      112.24 ms  (+30.06%) |     201   →     445   (+121.39%) |       17.35 s  →       49.95 s  (+187.95%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |       13.16 ms →       16.77 ms  (+27.40%) |     364   →     790   (+117.03%) |        4.79 s  →       13.25 s  (+176.50%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       71.27 ns →       65.57 ns   (-8.01%) |     364   →     790   (+117.03%) |       25.94 μs →       51.80 μs  (+99.65%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.72 ms →       13.12 ms  (+34.92%) |     364   →     790   (+117.03%) |        3.54 s  →       10.36 s  (+192.83%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       42.85 ns →       66.00 ns  (+54.02%) |     364   →     790   (+117.03%) |       15.60 μs →       52.14 μs (+234.27%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       32.49 ms →       42.50 ms  (+30.80%) |     201   →     445   (+121.39%) |        6.53 s  →       18.91 s  (+189.57%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.68 ms →       20.86 ms  (+33.02%) |     201   →     445   (+121.39%) |        3.15 s  →        9.28 s  (+194.51%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |       17.60 ms →       24.63 ms  (+39.94%) |     163   →     345   (+111.66%) |        2.87 s  →        8.50 s  (+196.18%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.85 ms →        8.16 ms  (+39.57%) |     489   →    1.03 K (+111.66%) |        2.86 s  →        8.45 s  (+195.42%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.33 ms →       28.77 ms  (+28.83%) |     201   →     445   (+121.39%) |        4.49 s  →       12.80 s  (+185.21%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |       21.01 ms →       27.35 ms  (+30.15%) |     201   →     445   (+121.39%) |        4.22 s  →       12.17 s  (+188.14%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       71.08 ns →       74.65 ns   (+5.03%) |     201   →     445   (+121.39%) |       14.29 μs →       33.22 μs (+132.52%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       16.20 ms →       21.78 ms  (+34.45%) |     201   →     445   (+121.39%) |        3.26 s  →        9.69 s  (+197.66%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |      151.50 ns →      107.10 ns  (-29.31%) |     201   →     445   (+121.39%) |       30.45 μs →       47.66 μs  (+56.51%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       47.30 ms →       54.12 ms  (+14.42%) |     201   →     445   (+121.39%) |        9.51 s  →       24.08 s  (+153.32%) | 
- │ │ │ │   ├ sirius::residuals                                         |       16.29 ms →       17.86 ms   (+9.67%) |     196   →     434   (+121.43%) |        3.19 s  →        7.75 s  (+142.84%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |       17.15 ms →       19.10 ms  (+11.38%) |     164   →     357   (+117.68%) |        2.81 s  →        6.82 s  (+142.46%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.05 ms →        9.20 ms  (+14.32%) |     328   →     714   (+117.68%) |        2.64 s  →        6.57 s  (+148.86%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.58 ms →        1.79 ms  (+13.65%) |     164   →     357   (+117.68%) |      258.78 ms →      640.22 ms (+147.40%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.81 ms →       54.95 ms   (+6.05%) |      80   →     181   (+126.25%) |        4.14 s  →        9.95 s  (+139.94%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       33.03 ms →       37.12 ms  (+12.37%) |     122   →     262   (+114.75%) |        4.03 s  →        9.73 s  (+141.31%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       24.33 ms →       28.05 ms  (+15.28%) |     164   →     343   (+109.15%) |        3.99 s  →        9.62 s  (+141.10%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      549.45 ns →      864.72 ns  (+57.38%) |      38   →     100   (+163.16%) |       20.88 μs →       86.47 μs (+314.16%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       36.90 μs →       31.86 μs  (-13.67%) |      38   →     100   (+163.16%) |        1.40 ms →        3.19 ms (+127.19%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.53 ms →        3.49 ms   (-1.11%) |      38   →     100   (+163.16%) |      134.11 ms →      348.99 ms (+160.23%) | 
- │ │ ├ sirius::Density::generate                                       |      300.37 ms →      295.89 ms   (-1.49%) |      38   →     100   (+163.16%) |       11.41 s  →       29.59 s  (+159.23%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      296.39 ms →      292.06 ms   (-1.46%) |      38   →     100   (+163.16%) |       11.26 s  →       29.21 s  (+159.32%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.14 ms →       65.04 ms   (-3.13%) |      38   →     100   (+163.16%) |        2.55 s  →        6.50 s  (+154.92%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       64.60 μs →       26.38 μs  (-59.16%) |      38   →     100   (+163.16%) |        2.45 ms →        2.64 ms   (+7.47%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms →        1.16 ms   (-0.89%) |       2   →       2              |        2.34 ms →        2.32 ms   (-0.89%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.88 ms →       53.87 ms   (-3.60%) |      38   →     100   (+163.16%) |        2.12 s  →        5.39 s  (+153.69%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.53 ms →       60.95 ms   (-0.95%) |      38   →     100   (+163.16%) |        2.34 s  →        6.09 s  (+160.65%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.28 μs →       11.12 μs   (-1.42%) |      38   →     100   (+163.16%) |      428.68 μs →        1.11 ms (+159.41%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (+0.18%) |      38   →     100   (+163.16%) |       87.63 ms →      231.00 ms (+163.63%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.68 ms →       58.10 ms   (-0.98%) |      38   →     100   (+163.16%) |        2.23 s  →        5.81 s  (+160.58%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.21 ms →        6.64 ms   (-7.82%) |      38   →     100   (+163.16%) |      273.94 ms →      664.49 ms (+142.57%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      560.61 ns →      557.52 ns   (-0.55%) |      38   →     100   (+163.16%) |       21.30 μs →       55.75 μs (+161.71%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.60 ms →      104.16 ms   (-0.42%) |      38   →     100   (+163.16%) |        3.97 s  →       10.42 s  (+162.05%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.45 ms →        2.42 ms   (-1.23%) |      38   →     100   (+163.16%) |       92.95 ms →      241.60 ms (+159.93%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.06 ms   (+0.08%) |      38   →     100   (+163.16%) |      761.86 ms →        2.01 s  (+163.36%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms →       19.90 ms   (+0.08%) |      38   →     100   (+163.16%) |      755.64 ms →        1.99 s  (+163.36%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      256.16 ns →      462.49 ns  (+80.55%) |      38   →     100   (+163.16%) |        9.73 μs →       46.25 μs (+375.13%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.25 ms   (-0.14%) |      38   →     100   (+163.16%) |       47.60 ms →      125.10 ms (+162.80%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.73 ms →        2.57 ms   (-5.87%) |      38   →     100   (+163.16%) |      103.75 ms →      257.00 ms (+147.71%) | 
- │ │ ├ sirius::Density::mix                                            |      105.12 ms →       66.80 ms  (-36.45%) |      38   →     100   (+163.16%) |        3.99 s  →        6.68 s   (+67.23%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      283.47 μs →      254.23 μs  (-10.31%) |      38   →     100   (+163.16%) |       10.77 ms →       25.42 ms (+136.01%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        2.60 ms →        2.56 ms   (-1.50%) |      38   →     100   (+163.16%) |       98.74 ms →      255.95 ms (+159.20%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.46 ms →        2.43 ms   (-1.27%) |      38   →     100   (+163.16%) |       93.34 ms →      242.52 ms (+159.82%) | 
- │ │ ├ sirius::Potential::generate                                     |      184.06 ms →      174.73 ms   (-5.07%) |      38   →     100   (+163.16%) |        6.99 s  →       17.47 s  (+149.82%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       64.71 ms →       58.52 ms   (-9.57%) |      38   →     100   (+163.16%) |        2.46 s  →        5.85 s  (+137.97%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.28 ms →        2.84 ms  (-69.43%) |      38   →     100   (+163.16%) |      352.59 ms →      283.64 ms  (-19.55%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.44 ms →        4.25 ms   (-4.17%) |      38   →     100   (+163.16%) |      168.65 ms →      425.31 ms (+152.18%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.25 ms →        4.10 ms   (-3.53%) |      38   →     100   (+163.16%) |      161.48 ms →      409.95 ms (+153.88%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.25 ms →        4.10 ms   (-3.52%) |      38   →     100   (+163.16%) |      161.45 ms →      409.90 ms (+153.89%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      232.61 μs →      233.47 μs   (+0.37%) |      76   →     200   (+163.16%) |       17.68 ms →       46.69 ms (+164.13%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       93.96 ms →       90.89 ms   (-3.27%) |      38   →     100   (+163.16%) |        3.57 s  →        9.09 s  (+154.55%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       92.93 ms →       89.85 ms   (-3.31%) |      38   →     100   (+163.16%) |        3.53 s  →        8.99 s  (+154.45%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.61 ms   (+1.10%) |     190   →     500   (+163.16%) |      301.91 ms →      803.27 ms (+166.06%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.81 ms →        2.46 ms  (-12.37%) |     342   →     900   (+163.16%) |      961.02 ms →        2.22 s  (+130.60%) | 
- │ │ │ │   ├ sirius::gradient                                          |        2.47 ms →        2.41 ms   (-2.61%) |      38   →     100   (+163.16%) |       93.89 ms →      240.64 ms (+156.29%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      726.47 μs →      705.98 μs   (-2.82%) |     114   →     300   (+163.16%) |       82.82 ms →      211.79 ms (+155.74%) | 
- │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.84 ms   (+0.62%) |      38   →     100   (+163.16%) |      107.14 ms →      283.71 ms (+164.80%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.59 ms →        2.61 ms   (+0.54%) |      38   →     100   (+163.16%) |       98.47 ms →      260.53 ms (+164.57%) | 
- │ │ │ │   └ sirius::divergence                                        |       19.74 ms →       19.96 ms   (+1.13%) |      38   →     100   (+163.16%) |      749.97 ms →        2.00 s  (+166.13%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.44 ms →        2.46 ms   (+0.93%) |      38   →     100   (+163.16%) |       92.73 ms →      246.32 ms (+165.61%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.40 ms →        3.35 ms   (-1.22%) |      38   →     100   (+163.16%) |      129.04 ms →      335.44 ms (+159.95%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.97 ms →       20.94 ms   (-0.16%) |      38   →     100   (+163.16%) |      796.83 ms →        2.09 s  (+162.75%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      358.92 ns →      268.09 ns  (-25.31%) |      38   →     100   (+163.16%) |       13.64 μs →       26.81 μs  (+96.56%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      380.50 ns →      244.06 ns  (-35.86%) |      38   →     100   (+163.16%) |       14.46 μs →       24.41 μs  (+68.79%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.28 ms →        2.24 ms   (-1.67%) |      38   →     100   (+163.16%) |       86.67 ms →      224.29 ms (+158.77%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.16 ms →        4.25 ms   (+2.01%) |     266   →     700   (+163.16%) |        1.11 s  →        2.97 s  (+168.45%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        3.94 ms →        4.10 ms   (+3.95%) |     266   →     700   (+163.16%) |        1.05 s  →        2.87 s  (+173.56%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.94 ms →        4.09 ms   (+3.95%) |     266   →     700   (+163.16%) |        1.05 s  →        2.87 s  (+173.56%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.32 ms →        4.06 ms   (-6.07%) |     114   →     300   (+163.16%) |      492.46 ms →        1.22 s  (+147.19%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.08 ms →        3.89 ms   (-4.63%) |     114   →     300   (+163.16%) |      465.19 ms →        1.17 s  (+150.97%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.16 ms →        4.02 ms   (-3.45%) |      38   →     100   (+163.16%) |      158.15 ms →      401.82 ms (+154.07%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      108.06 μs →      100.08 μs   (-7.38%) |      38   →     100   (+163.16%) |        4.11 ms →       10.01 ms (+143.73%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      104.94 μs →       96.83 μs   (-7.73%) |      38   →     100   (+163.16%) |        3.99 ms →        9.68 ms (+142.82%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.44 ms →        5.50 ms   (+1.03%) |       2   →       2              |       10.88 ms →       11.00 ms   (+1.03%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.22 ms →        4.15 ms   (-1.65%) |       6   →       6              |       25.32 ms →       24.90 ms   (-1.65%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.01 ms →        4.14 ms   (+3.23%) |       6   →       6              |       24.07 ms →       24.85 ms   (+3.23%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.01 ms →        4.14 ms   (+3.23%) |       6   →       6              |       24.07 ms →       24.85 ms   (+3.23%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.22 ms →        4.07 ms   (-3.46%) |       3   →       3              |       12.66 ms →       12.22 ms   (-3.46%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.17 ms →        3.97 ms   (-4.94%) |       3   →       3              |       12.52 ms →       11.90 ms   (-4.94%) | 
  ├ sirius::Periodic_function|inner                                     |        4.03 ms →        4.10 ms   (+1.72%) |       2   →       2              |        8.06 ms →        8.20 ms   (+1.72%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.02 ms →        4.09 ms   (+1.74%) |       2   →       2              |        8.05 ms →        8.19 ms   (+1.74%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.02 ms →        4.09 ms   (+1.67%) |       2   →       2              |        8.04 ms →        8.18 ms   (+1.67%) | 
+ ├ sirius::Smooth_periodic_function|inner                              |        4.65 ms →        3.91 ms  (-15.97%) |       1   →       1              |        4.65 ms →        3.91 ms  (-15.97%) | 
+ │ └ sirius::Smooth_periodic_function|inner_local                      |        4.65 ms →        3.90 ms  (-15.99%) |       1   →       1              |        4.65 ms →        3.90 ms  (-15.99%) | 
  └ sirius::finalize                                                    |      481.58 ms →      444.31 ms   (-7.74%) |       1   →       1              |      481.58 ms →      444.31 ms   (-7.74%) | 
  ====================================================================================================================================================================================================
```
