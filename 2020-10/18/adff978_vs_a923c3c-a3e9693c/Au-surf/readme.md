# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      188.34 s  →      170.37 s    (-9.54%) |       1   →       1              |      188.34 s  →      170.37 s    (-9.54%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.71 s    (+0.89%) |       1   →       1              |        2.69 s  →        2.71 s    (+0.89%) | 
  ├ sirius::Simulation_context::initialize                              |        2.12 s  →        2.06 s    (-2.83%) |       1   →       1              |        2.12 s  →        2.06 s    (-2.83%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       65.91 ms →       41.47 ms  (-37.07%) |       1   →       1              |       65.91 ms →       41.47 ms  (-37.07%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |       54.93 ms →       48.79 ms  (-11.18%) |       1   →       1              |       54.93 ms →       48.79 ms  (-11.18%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       29.55 ms →       22.90 ms  (-22.50%) |       1   →       1              |       29.55 ms →       22.90 ms  (-22.50%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.31 ms →       25.82 ms   (+2.02%) |       1   →       1              |       25.31 ms →       25.82 ms   (+2.02%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.47 ms →       10.32 ms   (-1.41%) |       1   →       1              |       10.47 ms →       10.32 ms   (-1.41%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.82 ms →       15.47 ms   (+4.43%) |       1   →       1              |       14.82 ms →       15.47 ms   (+4.43%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.06 ms →       14.71 ms   (+4.62%) |       1   →       1              |       14.06 ms →       14.71 ms   (+4.62%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       13.84 ms →       14.47 ms   (+4.56%) |       1   →       1              |       13.84 ms →       14.47 ms   (+4.56%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      205.31 μs →      221.67 μs   (+7.97%) |       1   →       1              |      205.31 μs →      221.67 μs   (+7.97%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.53 μs →        2.50 μs   (-1.27%) |       1   →       1              |        2.53 μs →        2.50 μs   (-1.27%) | 
  │ └ sirius::Simulation_context::update                                |        1.95 s  →        1.92 s    (-1.40%) |       1   →       1              |        1.95 s  →        1.92 s    (-1.40%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.85 ms →       12.91 ms   (+0.53%) |       1   →       1              |       12.85 ms →       12.91 ms   (+0.53%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.13 ms →        8.19 ms   (+0.78%) |       1   →       1              |        8.13 ms →        8.19 ms   (+0.78%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.70 ms →        4.70 ms   (+0.09%) |       1   →       1              |        4.70 ms →        4.70 ms   (+0.09%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.11 ms →        4.11 ms   (-0.09%) |       1   →       1              |        4.11 ms →        4.11 ms   (-0.09%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.91 ms →        3.90 ms   (-0.13%) |       1   →       1              |        3.91 ms →        3.90 ms   (-0.13%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      202.11 μs →      203.14 μs   (+0.51%) |       1   →       1              |      202.11 μs →      203.14 μs   (+0.51%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.28 μs →        1.17 μs   (-8.75%) |       1   →       1              |        1.28 μs →        1.17 μs   (-8.75%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.75 ms →       15.39 ms   (-2.31%) |       2   →       2              |       31.50 ms →       30.77 ms   (-2.31%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.09 ms   (-0.02%) |       2   →       2              |        2.18 ms →        2.18 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      969.16 μs →      959.40 μs   (-1.01%) |       1   →       1              |      969.16 μs →      959.40 μs   (-1.01%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.10 ms →        5.11 ms   (+0.39%) |       2   →       2              |       10.19 ms →       10.23 ms   (+0.39%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.64 ms   (+0.16%) |       2   →       2              |        7.28 ms →        7.29 ms   (+0.16%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.03 ms →       15.65 ms   (+4.08%) |       4   →       4              |       60.13 ms →       62.58 ms   (+4.08%) | 
  │   ├ sddk::Gvec::init                                                |      163.86 ms →      160.03 ms   (-2.34%) |       2   →       2              |      327.72 ms →      320.05 ms   (-2.34%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.12 ms →      125.94 ms   (-1.71%) |       2   →       2              |      256.25 ms →      251.88 ms   (-1.71%) | 
  │   ├ sddk::Gvec_shells                                               |      116.90 ms →      123.96 ms   (+6.04%) |       1   →       1              |      116.90 ms →      123.96 ms   (+6.04%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.04 ms   (-0.43%) |       1   →       1              |        1.04 ms →        1.04 ms   (-0.43%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      225.16 ms →      216.96 ms   (-3.64%) |       1   →       1              |      225.16 ms →      216.96 ms   (-3.64%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.72 ms →       25.91 ms   (-3.03%) |       1   →       1              |       26.72 ms →       25.91 ms   (-3.03%) | 
  │ ├ sirius::K_point::K_point                                          |        1.89 μs →        1.86 μs   (-1.27%) |       2   →       2              |        3.77 μs →        3.73 μs   (-1.27%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.68 ms →       25.87 ms   (-3.04%) |       1   →       1              |       26.68 ms →       25.87 ms   (-3.04%) | 
  │   └ sirius::K_point::initialize                                     |       26.63 ms →       25.81 ms   (-3.08%) |       1   →       1              |       26.63 ms →       25.81 ms   (-3.08%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.99 ms →       19.36 ms   (-3.16%) |       1   →       1              |       19.99 ms →       19.36 ms   (-3.16%) | 
  │     │ └ sddk::Gvec::init                                            |        4.94 ms →        4.93 ms   (-0.21%) |       1   →       1              |        4.94 ms →        4.93 ms   (-0.21%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.24 μs →       11.72 μs   (+4.28%) |       1   →       1              |       11.24 μs →       11.72 μs   (+4.28%) | 
  │     └ sirius::K_point::update                                       |        4.23 ms →        4.06 ms   (-4.01%) |       1   →       1              |        4.23 ms →        4.06 ms   (-4.01%) | 
  │       └ sirius::Beta_projectors                                     |        1.70 ms →        1.70 ms   (-0.08%) |       1   →       1              |        1.70 ms →        1.70 ms   (-0.08%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      890.04 μs →      900.20 μs   (+1.14%) |       1   →       1              |      890.04 μs →      900.20 μs   (+1.14%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.46 ms →        1.46 ms   (+0.24%) |       2   →       2              |        2.92 ms →        2.93 ms   (+0.24%) | 
  ├ sirius::Potential                                                   |       98.58 ms →       90.60 ms   (-8.09%) |       1   →       1              |       98.58 ms →       90.60 ms   (-8.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.45 ms   (-0.80%) |       6   →       6              |       14.81 ms →       14.69 ms   (-0.80%) | 
  │ └ sirius::Potential::update                                         |       83.40 ms →       75.58 ms   (-9.38%) |       1   →       1              |       83.40 ms →       75.58 ms   (-9.38%) | 
  │   └ sirius::Potential::generate_local_potential                     |       83.23 ms →       75.40 ms   (-9.41%) |       1   →       1              |       83.23 ms →       75.40 ms   (-9.41%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       57.20 ms →       57.72 ms   (+0.91%) |       1   →       1              |       57.20 ms →       57.72 ms   (+0.91%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       17.30 ms →        9.07 ms  (-47.59%) |       1   →       1              |       17.30 ms →        9.07 ms  (-47.59%) | 
  ├ sirius::Density                                                     |       74.90 ms →       75.06 ms   (+0.21%) |       1   →       1              |       74.90 ms →       75.06 ms   (+0.21%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.85 ms →        4.83 ms   (-0.44%) |       2   →       2              |        9.71 ms →        9.67 ms   (-0.44%) | 
  │ └ sirius::Density::update                                           |       65.08 ms →       65.28 ms   (+0.31%) |       1   →       1              |       65.08 ms →       65.28 ms   (+0.31%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       64.91 ms →       65.11 ms   (+0.31%) |       1   →       1              |       64.91 ms →       65.11 ms   (+0.31%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.07 ms →        3.09 ms   (+0.74%) |       1   →       1              |        3.07 ms →        3.09 ms   (+0.74%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       57.63 ms →       58.33 ms   (+1.22%) |       1   →       1              |       57.63 ms →       58.33 ms   (+1.22%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        2.93 ms →        2.43 ms  (-17.22%) |       1   →       1              |        2.93 ms →        2.43 ms  (-17.22%) | 
  ├ sirius::Density::initial_density                                    |       79.96 ms →       79.97 ms   (+0.02%) |       1   →       1              |       79.96 ms →       79.97 ms   (+0.02%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       57.54 ms →       58.12 ms   (+1.01%) |       1   →       1              |       57.54 ms →       58.12 ms   (+1.01%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.90 ms →        2.60 ms  (-10.20%) |       2   →       2              |        5.80 ms →        5.21 ms  (-10.20%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.84 ms →        4.60 ms   (-4.95%) |       1   →       1              |        4.84 ms →        4.60 ms   (-4.95%) | 
  ├ sirius::Potential::generate                                         |      186.38 ms →      188.12 ms   (+0.93%) |       1   →       1              |      186.38 ms →      188.12 ms   (+0.93%) | 
  │ ├ sirius::Potential::poisson                                        |       63.82 ms →       63.92 ms   (+0.16%) |       1   →       1              |       63.82 ms →       63.92 ms   (+0.16%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.76 ms →        2.30 ms  (-16.62%) |       1   →       1              |        2.76 ms →        2.30 ms  (-16.62%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.32 ms →        4.39 ms   (+1.59%) |       1   →       1              |        4.32 ms →        4.39 ms   (+1.59%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.27 ms →        4.04 ms   (-5.33%) |       1   →       1              |        4.27 ms →        4.04 ms   (-5.33%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.27 ms →        4.04 ms   (-5.33%) |       1   →       1              |        4.27 ms →        4.04 ms   (-5.33%) | 
  │ ├ sirius::Periodic_function::add                                    |      232.28 μs →      246.66 μs   (+6.19%) |       2   →       2              |      464.55 μs →      493.33 μs   (+6.19%) | 
  │ ├ sirius::Potential::xc                                             |       95.91 ms →       97.71 ms   (+1.88%) |       1   →       1              |       95.91 ms →       97.71 ms   (+1.88%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       94.87 ms →       96.61 ms   (+1.84%) |       1   →       1              |       94.87 ms →       96.61 ms   (+1.84%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.98 ms →        1.98 ms   (+0.20%) |       5   →       5              |        9.89 ms →        9.91 ms   (+0.20%) | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.39 ms →        2.68 ms  (+12.00%) |       9   →       9              |       21.53 ms →       24.11 ms  (+12.00%) | 
  │ │   ├ sirius::gradient                                              |        7.64 ms →        7.58 ms   (-0.75%) |       1   →       1              |        7.64 ms →        7.58 ms   (-0.75%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.44 ms →        2.43 ms   (-0.15%) |       3   →       3              |        7.31 ms →        7.30 ms   (-0.15%) | 
  │ │   ├ sirius::dot                                                   |        2.83 ms →        2.80 ms   (-0.81%) |       1   →       1              |        2.83 ms →        2.80 ms   (-0.81%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.57 ms →        2.58 ms   (+0.46%) |       1   →       1              |        2.57 ms →        2.58 ms   (+0.46%) | 
  │ │   └ sirius::divergence                                            |       19.87 ms →       19.53 ms   (-1.73%) |       1   →       1              |       19.87 ms →       19.53 ms   (-1.73%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.47 ms →        2.42 ms   (-2.16%) |       1   →       1              |        2.47 ms →        2.42 ms   (-2.16%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.39 ms →        3.23 ms   (-4.64%) |       1   →       1              |        3.39 ms →        3.23 ms   (-4.64%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.26 ms →       22.18 ms   (-0.38%) |       1   →       1              |       22.26 ms →       22.18 ms   (-0.38%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      208.00 ns →      139.00 ns  (-33.17%) |       1   →       1              |      208.00 ns →      139.00 ns  (-33.17%) | 
  ├ sirius::Hamiltonian0                                                |       14.19 ms →       13.87 ms   (-2.25%) |       1   →       1              |       14.19 ms →       13.87 ms   (-2.25%) | 
  │ ├ sirius::Local_operator                                            |       13.87 ms →       13.55 ms   (-2.31%) |       1   →       1              |       13.87 ms →       13.55 ms   (-2.31%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.13 ms →        7.10 ms   (-0.33%) |       1   →       1              |        7.13 ms →        7.10 ms   (-0.33%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.27 ms →        4.98 ms   (-5.47%) |       1   →       1              |        5.27 ms →        4.98 ms   (-5.47%) | 
  │ ├ sirius::Non_local_operator                                        |       60.14 μs →       59.75 μs   (-0.66%) |       2   →       2              |      120.29 μs →      119.49 μs   (-0.66%) | 
  │ ├ sirius::D_operator::initialize                                    |       79.91 μs →       80.60 μs   (+0.87%) |       1   →       1              |       79.91 μs →       80.60 μs   (+0.87%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.02 μs →       68.41 μs   (-0.88%) |       1   →       1              |       69.02 μs →       68.41 μs   (-0.88%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.49 s  →        2.45 s    (-1.27%) |       1   →       1              |        2.49 s  →        2.45 s    (-1.27%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.41 ms   (-0.02%) |       1   →       1              |        8.41 ms →        8.41 ms   (-0.02%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      252.46 μs →      248.22 μs   (-1.68%) |       1   →       1              |      252.46 μs →      248.22 μs   (-1.68%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.16 ms   (+0.03%) |       1   →       1              |        8.16 ms →        8.16 ms   (+0.03%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.48 s  →        2.45 s    (-1.28%) |       1   →       1              |        2.48 s  →        2.45 s    (-1.28%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       88.47 ms →       86.15 ms   (-2.62%) |       4   →       4              |      353.87 ms →      344.61 ms   (-2.62%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.83 ms →       25.30 ms   (-2.05%) |       1   →       1              |       25.83 ms →       25.30 ms   (-2.05%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.97 ms →       14.52 ms   (-3.00%) |       1   →       1              |       14.97 ms →       14.52 ms   (-3.00%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.22 s  →        1.21 s    (-0.95%) |       1   →       1              |        1.22 s  →        1.21 s    (-0.95%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |        1.00 s  →      990.71 ms   (-1.14%) |       1   →       1              |        1.00 s  →      990.71 ms   (-1.14%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      319.77 ms →      326.30 ms   (+2.04%) |       1   →       1              |      319.77 ms →      326.30 ms   (+2.04%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      177.58 ms →      171.01 ms   (-3.70%) |       1   →       1              |      177.58 ms →      171.01 ms   (-3.70%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      177.58 ms →      171.00 ms   (-3.70%) |       1   →       1              |      177.58 ms →      171.00 ms   (-3.70%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      123.77 ms →      136.94 ms  (+10.64%) |       1   →       1              |      123.77 ms →      136.94 ms  (+10.64%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      176.62 ms →      170.96 ms   (-3.20%) |       1   →       1              |      176.62 ms →      170.96 ms   (-3.20%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      176.62 ms →      170.96 ms   (-3.20%) |       1   →       1              |      176.62 ms →      170.96 ms   (-3.20%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      174.82 ms →      162.57 ms   (-7.00%) |       1   →       1              |      174.82 ms →      162.57 ms   (-7.00%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      124.29 ms →      112.20 ms   (-9.72%) |       1   →       1              |      124.29 ms →      112.20 ms   (-9.72%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.71 ms →        3.74 ms   (+0.79%) |       1   →       1              |        3.71 ms →        3.74 ms   (+0.79%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.01 ms →       89.62 ms   (-0.44%) |       1   →       1              |       90.01 ms →       89.62 ms   (-0.44%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.48 ms →       12.01 ms   (-3.77%) |       1   →       1              |       12.48 ms →       12.01 ms   (-3.77%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.19 ms →       64.25 ms   (+0.08%) |       2   →       2              |      128.38 ms →      128.49 ms   (+0.08%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      196.97 ms →      192.71 ms   (-2.16%) |       2   →       2              |      393.94 ms →      385.42 ms   (-2.16%) | 
  │ │ │ └ sddk::wf_inner                                                |      196.87 ms →      192.61 ms   (-2.16%) |       2   →       2              |      393.73 ms →      385.22 ms   (-2.16%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       25.00 ns →       36.00 ns  (+44.00%) |       2   →       2              |       50.00 ns →       72.00 ns  (+44.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      194.48 ms →      190.31 ms   (-2.14%) |       2   →       2              |      388.96 ms →      380.62 ms   (-2.14%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       29.50 ns →       24.50 ns  (-16.95%) |       2   →       2              |       59.00 ns →       49.00 ns  (-16.95%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.33 ms →      115.11 ms   (-1.05%) |       1   →       1              |      116.33 ms →      115.11 ms   (-1.05%) | 
  │ │ └ sddk::wf_trans                                                  |       37.23 ms →       37.03 ms   (-0.53%) |       1   →       1              |       37.23 ms →       37.03 ms   (-0.53%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.67 ms →       35.66 ms   (-0.02%) |       1   →       1              |       35.67 ms →       35.66 ms   (-0.02%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      847.00 ns →      648.00 ns  (-23.49%) |       1   →       1              |      847.00 ns →      648.00 ns  (-23.49%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      179.46 s  →      161.60 s    (-9.95%) |       1   →       1              |      179.46 s  →      161.60 s    (-9.95%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        1.98 ms →        1.99 ms   (+0.49%) |      19   →      19              |       37.68 ms →       37.86 ms   (+0.49%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.76 s  →        2.69 s    (-2.47%) |      65   →      60     (-7.69%) |      179.24 s  →      161.35 s    (-9.98%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        7.39 ms →        7.12 ms   (-3.61%) |      65   →      60     (-7.69%) |      480.31 ms →      427.35 ms  (-11.03%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        7.06 ms →        6.78 ms   (-3.86%) |      65   →      60     (-7.69%) |      458.62 ms →      406.99 ms  (-11.26%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.46 ms →        1.52 ms   (+4.05%) |      65   →      60     (-7.69%) |       95.22 ms →       91.46 ms   (-3.95%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.14 ms →        3.78 ms   (-8.58%) |      65   →      60     (-7.69%) |      268.99 ms →      227.00 ms  (-15.61%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.25 μs →       61.49 μs   (+0.39%) |     130   →     120     (-7.69%) |        7.96 ms →        7.38 ms   (-7.33%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       84.57 μs →       85.11 μs   (+0.63%) |      65   →      60     (-7.69%) |        5.50 ms →        5.11 ms   (-7.11%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       69.59 μs →       71.14 μs   (+2.22%) |      65   →      60     (-7.69%) |        4.52 ms →        4.27 ms   (-5.65%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.13 s  →        2.07 s    (-2.74%) |      65   →      60     (-7.69%) |      138.57 s  →      124.40 s   (-10.22%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      205.19 μs →      209.16 μs   (+1.94%) |      65   →      60     (-7.69%) |       13.34 ms →       12.55 ms   (-5.90%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.92 μs →      201.23 μs   (+1.67%) |      65   →      60     (-7.69%) |       12.86 ms →       12.07 ms   (-6.15%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.13 μs →        5.56 μs   (+8.33%) |      65   →      60     (-7.69%) |      333.55 μs →      333.55 μs   (+0.00%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.12 s  →        2.05 s    (-3.14%) |      65   →      60     (-7.69%) |      137.72 s  →      123.13 s   (-10.59%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       49.15 ms →       49.73 ms   (+1.17%) |      65   →      60     (-7.69%) |        3.20 s  →        2.98 s    (-6.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        2.85 ms →        2.94 ms   (+2.85%) |     390   →     360     (-7.69%) |        1.11 s  →        1.06 s    (-5.06%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.58 ms →        1.58 ms   (+0.10%) |      65   →      60     (-7.69%) |      102.81 ms →       95.00 ms   (-7.60%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      420.17 μs →      419.39 μs   (-0.19%) |      65   →      60     (-7.69%) |       27.31 ms →       25.16 ms   (-7.86%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      903.24 μs →      909.54 μs   (+0.70%) |      65   →      60     (-7.69%) |       58.71 ms →       54.57 ms   (-7.05%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.04 s  →        1.98 s    (-3.29%) |      65   →      60     (-7.69%) |      132.86 s  →      118.61 s   (-10.73%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      223.13 ms →      219.58 ms   (-1.59%) |     325   →     307     (-5.54%) |       72.52 s  →       67.41 s    (-7.04%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      158.47 ms →      154.79 ms   (-2.33%) |     325   →     307     (-5.54%) |       51.50 s  →       47.52 s    (-7.74%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       29.65 ms →       27.07 ms   (-8.71%) |     325   →     307     (-5.54%) |        9.64 s  →        8.31 s   (-13.77%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      434.82 μs →      457.12 μs   (+5.13%) |     325   →     307     (-5.54%) |      141.32 ms →      140.34 ms   (-0.69%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.16 ms →        2.33 ms   (+7.58%) |      65   →      60     (-7.69%) |      140.60 ms →      139.63 ms   (-0.69%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       24.55 ms →       21.97 ms  (-10.50%) |     325   →     307     (-5.54%) |        7.98 s  →        6.75 s   (-15.46%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      434.38 μs →      448.67 μs   (+3.29%) |     325   →     307     (-5.54%) |      141.17 ms →      137.74 ms   (-2.43%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        2.16 ms →        2.28 ms   (+5.71%) |      65   →      60     (-7.69%) |      140.23 ms →      136.84 ms   (-2.42%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       36.18 ms →       34.16 ms   (-5.59%) |     325   →     307     (-5.54%) |       11.76 s  →       10.49 s   (-10.82%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       23.04 ms →       20.92 ms   (-9.20%) |     325   →     307     (-5.54%) |        7.49 s  →        6.42 s   (-14.23%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.63 ms →        2.67 ms   (+1.42%) |     325   →     307     (-5.54%) |      855.17 ms →      819.29 ms   (-4.20%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.74 ms →       23.40 ms   (-1.43%) |     325   →     307     (-5.54%) |        7.72 s  →        7.18 s    (-6.89%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.97 ms →        2.45 ms  (-17.47%) |     325   →     307     (-5.54%) |      966.39 ms →      753.40 ms  (-22.04%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.13 ms →       19.35 ms   (+1.14%) |     650   →     614     (-5.54%) |       12.43 s  →       11.88 s    (-4.46%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       60.56 ms →       59.95 ms   (-1.01%) |     325   →     307     (-5.54%) |       19.68 s  →       18.40 s    (-6.49%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       14.07 ms →       13.62 ms   (-3.22%) |     585   →     554     (-5.30%) |        8.23 s  →        7.55 s    (-8.35%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       41.88 ns →       65.66 ns  (+56.78%) |     585   →     554     (-5.30%) |       24.50 μs →       36.37 μs  (+48.47%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |       10.33 ms →       10.08 ms   (-2.47%) |     585   →     554     (-5.30%) |        6.04 s  →        5.58 s    (-7.64%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       63.31 ns →       83.53 ns  (+31.94%) |     585   →     554     (-5.30%) |       37.03 μs →       46.28 μs  (+24.95%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.28 ms →        3.30 ms   (+0.73%) |     325   →     307     (-5.54%) |        1.07 s  →        1.01 s    (-4.85%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.60 ms →       16.72 ms   (+0.72%) |     325   →     307     (-5.54%) |        5.39 s  →        5.13 s    (-4.86%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       19.18 ms →       19.07 ms   (-0.57%) |     260   →     247     (-5.00%) |        4.99 s  →        4.71 s    (-5.54%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        6.36 ms →        6.33 ms   (-0.36%) |     780   →     741     (-5.00%) |        4.96 s  →        4.69 s    (-5.35%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       21.93 ms →       21.36 ms   (-2.61%) |     325   →     307     (-5.54%) |        7.13 s  →        6.56 s    (-8.01%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       20.60 ms →       20.24 ms   (-1.75%) |     325   →     307     (-5.54%) |        6.69 s  →        6.21 s    (-7.19%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       82.18 ns →      109.13 ns  (+32.79%) |     325   →     307     (-5.54%) |       26.71 μs →       33.50 μs  (+25.43%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       17.12 ms →       16.75 ms   (-2.18%) |     325   →     307     (-5.54%) |        5.56 s  →        5.14 s    (-7.60%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       47.82 ns →       49.90 ns   (+4.34%) |     325   →     307     (-5.54%) |       15.54 μs →       15.32 μs   (-1.43%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       66.44 ms →       46.16 ms  (-30.52%) |     325   →     307     (-5.54%) |       21.59 s  →       14.17 s   (-34.37%) | 
  │ │ │ │   ├ sirius::residuals                                         |       18.52 ms →       18.04 ms   (-2.60%) |     321   →     299     (-6.85%) |        5.95 s  →        5.40 s    (-9.27%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       19.15 ms →       18.38 ms   (-4.04%) |     276   →     260     (-5.80%) |        5.29 s  →        4.78 s    (-9.60%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.73 ms →        8.44 ms   (-3.29%) |     552   →     520     (-5.80%) |        4.82 s  →        4.39 s    (-8.90%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.62 ms →        1.61 ms   (-0.83%) |     276   →     260     (-5.80%) |      447.05 ms →      417.63 ms   (-6.58%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       65.67 ms →       55.00 ms  (-16.24%) |      91   →     121    (+32.97%) |        5.98 s  →        6.66 s   (+11.37%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       50.46 ms →       35.64 ms  (-29.37%) |     117   →     182    (+55.56%) |        5.90 s  →        6.49 s    (+9.87%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       40.16 ms →       26.42 ms  (-34.22%) |     143   →     243    (+69.93%) |        5.74 s  →        6.42 s   (+11.78%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      708.25 ns →      529.98 ns  (-25.17%) |      65   →      60     (-7.69%) |       46.04 μs →       31.80 μs  (-30.93%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       38.54 μs →       24.80 μs  (-35.65%) |      65   →      60     (-7.69%) |        2.51 ms →        1.49 ms  (-40.60%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.62 ms →        3.59 ms   (-0.94%) |      65   →      60     (-7.69%) |      235.57 ms →      215.41 ms   (-8.56%) | 
+ │ │ ├ sirius::Density::generate                                       |      301.41 ms →      291.81 ms   (-3.19%) |      65   →      60     (-7.69%) |       19.59 s  →       17.51 s   (-10.63%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      297.15 ms →      287.88 ms   (-3.12%) |      65   →      60     (-7.69%) |       19.31 s  →       17.27 s   (-10.57%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       68.38 ms →       63.06 ms   (-7.78%) |      65   →      60     (-7.69%) |        4.44 s  →        3.78 s   (-14.87%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       43.45 μs →       47.06 μs   (+8.30%) |      65   →      60     (-7.69%) |        2.82 ms →        2.82 ms   (-0.03%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms →        1.18 ms   (+1.04%) |       2   →       2              |        2.34 ms →        2.36 ms   (+1.04%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.10 ms →       51.86 ms   (-9.17%) |      65   →      60     (-7.69%) |        3.71 s  →        3.11 s   (-16.15%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       62.34 ms →       60.13 ms   (-3.54%) |      65   →      60     (-7.69%) |        4.05 s  →        3.61 s   (-10.96%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.70 μs →        9.20 μs   (-5.15%) |      65   →      60     (-7.69%) |      630.25 μs →      551.78 μs  (-12.45%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.28 ms →        2.32 ms   (+1.73%) |      65   →      60     (-7.69%) |      147.97 ms →      138.95 ms   (-6.09%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       59.51 ms →       57.27 ms   (-3.77%) |      65   →      60     (-7.69%) |        3.87 s  →        3.44 s   (-11.17%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        8.08 ms →        5.85 ms  (-27.67%) |      65   →      60     (-7.69%) |      525.26 ms →      350.72 ms  (-33.23%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      641.57 ns →      658.57 ns   (+2.65%) |      65   →      60     (-7.69%) |       41.70 μs →       39.51 μs   (-5.25%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.39 ms →      104.96 ms   (+0.55%) |      65   →      60     (-7.69%) |        6.79 s  →        6.30 s    (-7.19%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.41 ms   (-0.43%) |      65   →      60     (-7.69%) |      157.08 ms →      144.38 ms   (-8.09%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.05 ms   (-0.00%) |      65   →      60     (-7.69%) |        1.30 s  →        1.20 s    (-7.69%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.88 ms   (-0.02%) |      65   →      60     (-7.69%) |        1.29 s  →        1.19 s    (-7.71%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      240.86 ns →      513.15 ns (+113.05%) |      65   →      60     (-7.69%) |       15.66 μs →       30.79 μs  (+96.66%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.25 ms   (-0.16%) |      65   →      60     (-7.69%) |       81.50 ms →       75.11 ms   (-7.84%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.01 ms →        2.67 ms  (-11.16%) |      65   →      60     (-7.69%) |      195.49 ms →      160.31 ms  (-17.99%) | 
  │ │ ├ sirius::Density::mix                                            |       84.03 ms →       85.06 ms   (+1.23%) |      65   →      60     (-7.69%) |        5.46 s  →        5.10 s    (-6.55%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      263.05 μs →      263.77 μs   (+0.28%) |      65   →      60     (-7.69%) |       17.10 ms →       15.83 ms   (-7.44%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.51 ms →        2.80 ms  (-20.16%) |      65   →      60     (-7.69%) |      228.04 ms →      168.06 ms  (-26.30%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.30 ms →        2.61 ms  (-21.01%) |      65   →      60     (-7.69%) |      214.65 ms →      156.50 ms  (-27.09%) | 
  │ │ ├ sirius::Potential::generate                                     |      180.76 ms →      180.00 ms   (-0.42%) |      65   →      60     (-7.69%) |       11.75 s  →       10.80 s    (-8.08%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       63.85 ms →       64.23 ms   (+0.60%) |      65   →      60     (-7.69%) |        4.15 s  →        3.85 s    (-7.14%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.79 ms →        2.39 ms  (-14.28%) |      65   →      60     (-7.69%) |      181.29 ms →      143.44 ms  (-20.88%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.21 ms →        4.56 ms   (+8.25%) |      65   →      60     (-7.69%) |      273.69 ms →      273.49 ms   (-0.07%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.10 ms →        4.07 ms   (-0.73%) |      65   →      60     (-7.69%) |      266.59 ms →      244.28 ms   (-8.37%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.10 ms →        4.07 ms   (-0.73%) |      65   →      60     (-7.69%) |      266.56 ms →      244.25 ms   (-8.37%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      229.86 μs →      238.19 μs   (+3.62%) |     130   →     120     (-7.69%) |       29.88 ms →       28.58 ms   (-4.35%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       91.43 ms →       90.51 ms   (-1.01%) |      65   →      60     (-7.69%) |        5.94 s  →        5.43 s    (-8.62%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       90.42 ms →       89.47 ms   (-1.05%) |      65   →      60     (-7.69%) |        5.88 s  →        5.37 s    (-8.66%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.59 ms   (-0.06%) |     325   →     300     (-7.69%) |      517.33 ms →      477.24 ms   (-7.75%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.56 ms →        2.47 ms   (-3.69%) |     585   →     540     (-7.69%) |        1.50 s  →        1.33 s   (-11.09%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.37 ms →        2.43 ms   (+2.54%) |      65   →      60     (-7.69%) |      153.99 ms →      145.76 ms   (-5.34%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      697.19 μs →      715.85 μs   (+2.68%) |     195   →     180     (-7.69%) |      135.95 ms →      128.85 ms   (-5.22%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.83 ms →        2.82 ms   (-0.36%) |      65   →      60     (-7.69%) |      184.14 ms →      169.37 ms   (-8.02%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.60 ms →        2.59 ms   (-0.45%) |      65   →      60     (-7.69%) |      169.02 ms →      155.33 ms   (-8.10%) | 
  │ │ │ │   └ sirius::divergence                                        |       19.89 ms →       19.72 ms   (-0.85%) |      65   →      60     (-7.69%) |        1.29 s  →        1.18 s    (-8.47%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.44 ms →        2.43 ms   (-0.31%) |      65   →      60     (-7.69%) |      158.61 ms →      145.95 ms   (-7.98%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.44 ms →        3.25 ms   (-5.40%) |      65   →      60     (-7.69%) |      223.64 ms →      195.29 ms  (-12.68%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       21.04 ms →       20.98 ms   (-0.27%) |      65   →      60     (-7.69%) |        1.37 s  →        1.26 s    (-7.94%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      300.22 ns →      227.63 ns  (-24.18%) |      65   →      60     (-7.69%) |       19.51 μs →       13.66 μs  (-30.01%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      247.92 ns →      377.93 ns  (+52.44%) |      65   →      60     (-7.69%) |       16.11 μs →       22.68 μs  (+40.71%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.39 ms →        2.25 ms   (-6.05%) |      65   →      60     (-7.69%) |      155.45 ms →      134.80 ms  (-13.28%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.08 ms →        4.12 ms   (+0.96%) |     455   →     420     (-7.69%) |        1.86 s  →        1.73 s    (-6.81%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.93 ms →        3.92 ms   (-0.19%) |     455   →     420     (-7.69%) |        1.79 s  →        1.65 s    (-7.86%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.93 ms →        3.92 ms   (-0.19%) |     455   →     420     (-7.69%) |        1.79 s  →        1.65 s    (-7.87%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.39 ms →        4.28 ms   (-2.42%) |     195   →     180     (-7.69%) |      855.28 ms →      770.39 ms   (-9.93%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.22 ms →        4.06 ms   (-3.75%) |     195   →     180     (-7.69%) |      823.23 ms →      731.42 ms  (-11.15%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.03 ms →        4.02 ms   (-0.06%) |      65   →      60     (-7.69%) |      261.67 ms →      241.41 ms   (-7.74%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      155.19 μs →      125.60 μs  (-19.06%) |      65   →      60     (-7.69%) |       10.09 ms →        7.54 ms  (-25.29%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      151.85 μs →      122.17 μs  (-19.55%) |      65   →      60     (-7.69%) |        9.87 ms →        7.33 ms  (-25.74%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.52 ms →        5.32 ms   (-3.66%) |       2   →       2              |       11.03 ms →       10.63 ms   (-3.66%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.22 ms →        4.03 ms   (-4.62%) |       6   →       6              |       25.35 ms →       24.18 ms   (-4.62%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.90 ms →        3.96 ms   (+1.45%) |       6   →       6              |       23.40 ms →       23.74 ms   (+1.45%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.90 ms →        3.96 ms   (+1.45%) |       6   →       6              |       23.40 ms →       23.74 ms   (+1.45%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.59 ms →        4.17 ms   (-9.25%) |       3   →       3              |       13.78 ms →       12.50 ms   (-9.25%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.22 ms →        4.10 ms   (-2.74%) |       3   →       3              |       12.65 ms →       12.30 ms   (-2.74%) | 
  ├ sirius::Periodic_function|inner                                     |        4.22 ms →        4.13 ms   (-2.10%) |       2   →       2              |        8.44 ms →        8.27 ms   (-2.10%) | 
  │ └ sirius::Periodic_function|inner_local                             |        3.88 ms →        3.88 ms   (+0.08%) |       2   →       2              |        7.76 ms →        7.77 ms   (+0.08%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.88 ms →        3.88 ms   (+0.08%) |       2   →       2              |        7.76 ms →        7.77 ms   (+0.08%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.58 ms →        4.95 ms   (+8.10%) |       1   →       1              |        4.58 ms →        4.95 ms   (+8.10%) | 
- │ └ sirius::Smooth_periodic_function|inner_local                      |        4.25 ms →        4.94 ms  (+16.37%) |       1   →       1              |        4.25 ms →        4.94 ms  (+16.37%) | 
+ └ sirius::finalize                                                    |      300.89 ms →      268.30 ms  (-10.83%) |       1   →       1              |      300.89 ms →      268.30 ms  (-10.83%) | 
  ====================================================================================================================================================================================================
```
