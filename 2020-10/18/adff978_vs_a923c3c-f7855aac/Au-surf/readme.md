# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      188.01 s  →      172.03 s    (-8.50%) |       1   →       1              |      188.01 s  →      172.03 s    (-8.50%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.69 s    (-0.74%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.74%) | 
  ├ sirius::Simulation_context::initialize                              |        2.12 s  →        2.15 s    (+1.50%) |       1   →       1              |        2.12 s  →        2.15 s    (+1.50%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       56.07 ms →       99.16 ms  (+76.84%) |       1   →       1              |       56.07 ms →       99.16 ms  (+76.84%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       89.87 ms →       97.84 ms   (+8.87%) |       1   →       1              |       89.87 ms →       97.84 ms   (+8.87%) | 
- │ │ ├ sirius::Atom_type::init                                         |       64.07 ms →       71.41 ms  (+11.46%) |       1   →       1              |       64.07 ms →       71.41 ms  (+11.46%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.74 ms →       26.37 ms   (+2.44%) |       1   →       1              |       25.74 ms →       26.37 ms   (+2.44%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.11 ms →       10.15 ms   (+0.43%) |       1   →       1              |       10.11 ms →       10.15 ms   (+0.43%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.61 ms →       16.20 ms   (+3.78%) |       1   →       1              |       15.61 ms →       16.20 ms   (+3.78%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.20 ms →       15.78 ms   (+3.86%) |       1   →       1              |       15.20 ms →       15.78 ms   (+3.86%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.96 ms →       15.55 ms   (+3.91%) |       1   →       1              |       14.96 ms →       15.55 ms   (+3.91%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      219.47 μs →      219.51 μs   (+0.02%) |       1   →       1              |      219.47 μs →      219.51 μs   (+0.02%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.53 μs →        2.40 μs   (-4.87%) |       1   →       1              |        2.53 μs →        2.40 μs   (-4.87%) | 
  │ └ sirius::Simulation_context::update                                |        1.92 s  →        1.89 s    (-1.23%) |       1   →       1              |        1.92 s  →        1.89 s    (-1.23%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.96 ms →       12.44 ms   (-4.04%) |       1   →       1              |       12.96 ms →       12.44 ms   (-4.04%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.40 ms →        7.93 ms   (-5.62%) |       1   →       1              |        8.40 ms →        7.93 ms   (-5.62%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.54 ms →        4.49 ms   (-1.07%) |       1   →       1              |        4.54 ms →        4.49 ms   (-1.07%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.14 ms →        4.10 ms   (-0.79%) |       1   →       1              |        4.14 ms →        4.10 ms   (-0.79%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.92 ms →        3.90 ms   (-0.48%) |       1   →       1              |        3.92 ms →        3.90 ms   (-0.48%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      214.44 μs →      200.79 μs   (-6.36%) |       1   →       1              |      214.44 μs →      200.79 μs   (-6.36%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.27 μs →        1.20 μs   (-5.73%) |       1   →       1              |        1.27 μs →        1.20 μs   (-5.73%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.28 ms →       15.42 ms   (+0.94%) |       2   →       2              |       30.56 ms →       30.84 ms   (+0.94%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (+0.26%) |       2   →       2              |        2.19 ms →        2.20 ms   (+0.26%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      952.05 μs →      951.07 μs   (-0.10%) |       1   →       1              |      952.05 μs →      951.07 μs   (-0.10%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.15 ms →        5.08 ms   (-1.27%) |       2   →       2              |       10.30 ms →       10.17 ms   (-1.27%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.77 ms →        3.64 ms   (-3.32%) |       2   →       2              |        7.54 ms →        7.29 ms   (-3.32%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.55 ms →       15.76 ms   (+1.39%) |       4   →       4              |       62.19 ms →       63.06 ms   (+1.39%) | 
  │   ├ sddk::Gvec::init                                                |      160.56 ms →      156.42 ms   (-2.58%) |       2   →       2              |      321.12 ms →      312.84 ms   (-2.58%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.60 ms →      123.27 ms   (-3.39%) |       2   →       2              |      255.19 ms →      246.54 ms   (-3.39%) | 
  │   ├ sddk::Gvec_shells                                               |      126.25 ms →      127.40 ms   (+0.92%) |       1   →       1              |      126.25 ms →      127.40 ms   (+0.92%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.04 ms   (-0.86%) |       1   →       1              |        1.04 ms →        1.04 ms   (-0.86%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      220.47 ms →      223.03 ms   (+1.16%) |       1   →       1              |      220.47 ms →      223.03 ms   (+1.16%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.28 ms →       27.99 ms   (+6.50%) |       1   →       1              |       26.28 ms →       27.99 ms   (+6.50%) | 
+ │ ├ sirius::K_point::K_point                                          |        5.89 μs →        1.89 μs  (-67.89%) |       2   →       2              |       11.78 μs →        3.78 μs  (-67.89%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.23 ms →       27.95 ms   (+6.55%) |       1   →       1              |       26.23 ms →       27.95 ms   (+6.55%) | 
  │   └ sirius::K_point::initialize                                     |       26.18 ms →       27.91 ms   (+6.60%) |       1   →       1              |       26.18 ms →       27.91 ms   (+6.60%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.79 ms →       20.98 ms   (+5.97%) |       1   →       1              |       19.79 ms →       20.98 ms   (+5.97%) | 
  │     │ └ sddk::Gvec::init                                            |        5.29 ms →        5.38 ms   (+1.65%) |       1   →       1              |        5.29 ms →        5.38 ms   (+1.65%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.65 μs →       11.52 μs   (-1.06%) |       1   →       1              |       11.65 μs →       11.52 μs   (-1.06%) | 
  │     └ sirius::K_point::update                                       |        4.05 ms →        4.32 ms   (+6.70%) |       1   →       1              |        4.05 ms →        4.32 ms   (+6.70%) | 
  │       └ sirius::Beta_projectors                                     |        1.70 ms →        1.72 ms   (+1.06%) |       1   →       1              |        1.70 ms →        1.72 ms   (+1.06%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      896.25 μs →      907.70 μs   (+1.28%) |       1   →       1              |      896.25 μs →      907.70 μs   (+1.28%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.49 ms →        1.45 ms   (-2.75%) |       2   →       2              |        2.98 ms →        2.90 ms   (-2.75%) | 
  ├ sirius::Potential                                                   |       95.34 ms →       88.43 ms   (-7.25%) |       1   →       1              |       95.34 ms →       88.43 ms   (-7.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.44 ms   (-0.94%) |       6   →       6              |       14.80 ms →       14.66 ms   (-0.94%) | 
  │ └ sirius::Potential::update                                         |       80.21 ms →       73.42 ms   (-8.47%) |       1   →       1              |       80.21 ms →       73.42 ms   (-8.47%) | 
  │   └ sirius::Potential::generate_local_potential                     |       80.05 ms →       73.26 ms   (-8.48%) |       1   →       1              |       80.05 ms →       73.26 ms   (-8.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       51.08 ms →       50.05 ms   (-2.02%) |       1   →       1              |       51.08 ms →       50.05 ms   (-2.02%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       20.25 ms →       14.57 ms  (-28.07%) |       1   →       1              |       20.25 ms →       14.57 ms  (-28.07%) | 
  ├ sirius::Density                                                     |       75.33 ms →       74.99 ms   (-0.45%) |       1   →       1              |       75.33 ms →       74.99 ms   (-0.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.19 ms →        4.77 ms   (-7.98%) |       2   →       2              |       10.38 ms →        9.55 ms   (-7.98%) | 
  │ └ sirius::Density::update                                           |       64.83 ms →       65.33 ms   (+0.77%) |       1   →       1              |       64.83 ms →       65.33 ms   (+0.77%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       64.65 ms →       65.17 ms   (+0.80%) |       1   →       1              |       64.65 ms →       65.17 ms   (+0.80%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |        3.46 ms →        3.11 ms  (-10.08%) |       1   →       1              |        3.46 ms →        3.11 ms  (-10.08%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       51.73 ms →       51.65 ms   (-0.17%) |       1   →       1              |       51.73 ms →       51.65 ms   (-0.17%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        8.13 ms →        9.17 ms  (+12.89%) |       1   →       1              |        8.13 ms →        9.17 ms  (+12.89%) | 
  ├ sirius::Density::initial_density                                    |       80.25 ms →       80.34 ms   (+0.12%) |       1   →       1              |       80.25 ms →       80.34 ms   (+0.12%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       51.62 ms →       51.49 ms   (-0.26%) |       1   →       1              |       51.62 ms →       51.49 ms   (-0.26%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.86 ms →        6.13 ms   (+4.60%) |       2   →       2              |       11.73 ms →       12.26 ms   (+4.60%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.46 ms →        4.81 ms   (+7.84%) |       1   →       1              |        4.46 ms →        4.81 ms   (+7.84%) | 
  ├ sirius::Potential::generate                                         |      189.06 ms →      185.83 ms   (-1.71%) |       1   →       1              |      189.06 ms →      185.83 ms   (-1.71%) | 
  │ ├ sirius::Potential::poisson                                        |       64.10 ms →       63.97 ms   (-0.20%) |       1   →       1              |       64.10 ms →       63.97 ms   (-0.20%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.93 ms →        9.68 ms   (-2.53%) |       1   →       1              |        9.93 ms →        9.68 ms   (-2.53%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.11 ms →        4.35 ms   (+5.67%) |       1   →       1              |        4.11 ms →        4.35 ms   (+5.67%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.08 ms →        4.33 ms   (+6.16%) |       1   →       1              |        4.08 ms →        4.33 ms   (+6.16%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        4.33 ms   (+6.16%) |       1   →       1              |        4.08 ms →        4.33 ms   (+6.16%) | 
  │ ├ sirius::Periodic_function::add                                    |      251.91 μs →      227.35 μs   (-9.75%) |       2   →       2              |      503.82 μs →      454.70 μs   (-9.75%) | 
  │ ├ sirius::Potential::xc                                             |       98.11 ms →       95.34 ms   (-2.83%) |       1   →       1              |       98.11 ms →       95.34 ms   (-2.83%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       97.10 ms →       94.31 ms   (-2.87%) |       1   →       1              |       97.10 ms →       94.31 ms   (-2.87%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.00 ms →        1.98 ms   (-0.95%) |       5   →       5              |        9.99 ms →        9.90 ms   (-0.95%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.69 ms →        2.42 ms   (-9.98%) |       9   →       9              |       24.24 ms →       21.82 ms   (-9.98%) | 
  │ │   ├ sirius::gradient                                              |        7.54 ms →        7.50 ms   (-0.43%) |       1   →       1              |        7.54 ms →        7.50 ms   (-0.43%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.40 ms   (-0.62%) |       3   →       3              |        7.25 ms →        7.20 ms   (-0.62%) | 
  │ │   ├ sirius::dot                                                   |        2.85 ms →        2.82 ms   (-1.20%) |       1   →       1              |        2.85 ms →        2.82 ms   (-1.20%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.59 ms →        2.56 ms   (-1.26%) |       1   →       1              |        2.59 ms →        2.56 ms   (-1.26%) | 
  │ │   └ sirius::divergence                                            |       19.80 ms →       19.65 ms   (-0.76%) |       1   →       1              |       19.80 ms →       19.65 ms   (-0.76%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.45 ms →        2.43 ms   (-0.87%) |       1   →       1              |        2.45 ms →        2.43 ms   (-0.87%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.61 ms →        3.33 ms   (-7.56%) |       1   →       1              |        3.61 ms →        3.33 ms   (-7.56%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.20 ms →       22.18 ms   (-0.07%) |       1   →       1              |       22.20 ms →       22.18 ms   (-0.07%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      293.00 ns →      413.00 ns  (+40.96%) |       1   →       1              |      293.00 ns →      413.00 ns  (+40.96%) | 
  ├ sirius::Hamiltonian0                                                |       14.33 ms →       14.00 ms   (-2.30%) |       1   →       1              |       14.33 ms →       14.00 ms   (-2.30%) | 
  │ ├ sirius::Local_operator                                            |       14.01 ms →       13.68 ms   (-2.31%) |       1   →       1              |       14.01 ms →       13.68 ms   (-2.31%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.13 ms →        7.19 ms   (+0.81%) |       1   →       1              |        7.13 ms →        7.19 ms   (+0.81%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.44 ms →        5.05 ms   (-7.14%) |       1   →       1              |        5.44 ms →        5.05 ms   (-7.14%) | 
  │ ├ sirius::Non_local_operator                                        |       59.08 μs →       59.51 μs   (+0.73%) |       2   →       2              |      118.15 μs →      119.02 μs   (+0.73%) | 
  │ ├ sirius::D_operator::initialize                                    |       82.12 μs →       76.73 μs   (-6.57%) |       1   →       1              |       82.12 μs →       76.73 μs   (-6.57%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.38 μs →       67.75 μs   (-0.92%) |       1   →       1              |       68.38 μs →       67.75 μs   (-0.92%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.49 s  →        2.47 s    (-1.12%) |       1   →       1              |        2.49 s  →        2.47 s    (-1.12%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.42 ms →        8.41 ms   (-0.06%) |       1   →       1              |        8.42 ms →        8.41 ms   (-0.06%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      261.24 μs →      248.15 μs   (-5.01%) |       1   →       1              |      261.24 μs →      248.15 μs   (-5.01%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.16 ms   (+0.10%) |       1   →       1              |        8.15 ms →        8.16 ms   (+0.10%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.49 s  →        2.46 s    (-1.12%) |       1   →       1              |        2.49 s  →        2.46 s    (-1.12%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       89.89 ms →       89.06 ms   (-0.92%) |       4   →       4              |      359.55 ms →      356.25 ms   (-0.92%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.78 ms →       26.05 ms   (+1.05%) |       1   →       1              |       25.78 ms →       26.05 ms   (+1.05%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.78 ms →       15.07 ms   (+1.98%) |       1   →       1              |       14.78 ms →       15.07 ms   (+1.98%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.23 s  →        1.20 s    (-2.65%) |       1   →       1              |        1.23 s  →        1.20 s    (-2.65%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |        1.01 s  →      978.24 ms   (-2.96%) |       1   →       1              |        1.01 s  →      978.24 ms   (-2.96%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      337.03 ms →      303.83 ms   (-9.85%) |       1   →       1              |      337.03 ms →      303.83 ms   (-9.85%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      181.38 ms →      175.70 ms   (-3.13%) |       1   →       1              |      181.38 ms →      175.70 ms   (-3.13%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      181.37 ms →      175.69 ms   (-3.13%) |       1   →       1              |      181.37 ms →      175.69 ms   (-3.13%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      137.29 ms →      109.71 ms  (-20.09%) |       1   →       1              |      137.29 ms →      109.71 ms  (-20.09%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      178.78 ms →      173.13 ms   (-3.16%) |       1   →       1              |      178.78 ms →      173.13 ms   (-3.16%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      178.78 ms →      173.12 ms   (-3.16%) |       1   →       1              |      178.78 ms →      173.12 ms   (-3.16%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      161.74 ms →      169.70 ms   (+4.92%) |       1   →       1              |      161.74 ms →      169.70 ms   (+4.92%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      111.37 ms →      119.21 ms   (+7.03%) |       1   →       1              |      111.37 ms →      119.21 ms   (+7.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.69 ms →        3.74 ms   (+1.30%) |       1   →       1              |        3.69 ms →        3.74 ms   (+1.30%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       93.45 ms →       90.39 ms   (-3.27%) |       1   →       1              |       93.45 ms →       90.39 ms   (-3.27%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       15.74 ms →       12.64 ms  (-19.68%) |       1   →       1              |       15.74 ms →       12.64 ms  (-19.68%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.22 ms →       64.27 ms   (+0.09%) |       2   →       2              |      128.43 ms →      128.55 ms   (+0.09%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      194.35 ms →      192.35 ms   (-1.03%) |       2   →       2              |      388.69 ms →      384.71 ms   (-1.03%) | 
  │ │ │ └ sddk::wf_inner                                                |      194.25 ms →      192.26 ms   (-1.02%) |       2   →       2              |      388.49 ms →      384.51 ms   (-1.02%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       17.50 ns →       32.00 ns  (+82.86%) |       2   →       2              |       35.00 ns →       64.00 ns  (+82.86%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      192.56 ms →      190.74 ms   (-0.94%) |       2   →       2              |      385.11 ms →      381.48 ms   (-0.94%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       22.00 ns →       13.00 ns  (-40.91%) |       2   →       2              |       44.00 ns →       26.00 ns  (-40.91%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.29 ms →      115.30 ms   (-0.85%) |       1   →       1              |      116.29 ms →      115.30 ms   (-0.85%) | 
  │ │ └ sddk::wf_trans                                                  |       35.67 ms →       36.47 ms   (+2.26%) |       1   →       1              |       35.67 ms →       36.47 ms   (+2.26%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.65 ms →       35.63 ms   (-0.04%) |       1   →       1              |       35.65 ms →       35.63 ms   (-0.04%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      445.00 ns →      441.00 ns   (-0.90%) |       1   →       1              |      445.00 ns →      441.00 ns   (-0.90%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      179.10 s  →      163.17 s    (-8.90%) |       1   →       1              |      179.10 s  →      163.17 s    (-8.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        1.97 ms →        1.97 ms   (-0.15%) |      19   →      19              |       37.45 ms →       37.39 ms   (-0.15%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.75 s  →        2.72 s    (-1.33%) |      65   →      60     (-7.69%) |      178.91 s  →      162.94 s    (-8.92%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.21 ms →        7.17 ms   (-0.56%) |      65   →      60     (-7.69%) |      468.43 ms →      429.98 ms   (-8.21%) | 
  │ │ │ ├ sirius::Local_operator                                        |        6.88 ms →        6.83 ms   (-0.68%) |      65   →      60     (-7.69%) |      447.07 ms →      409.87 ms   (-8.32%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms →        1.46 ms   (-2.54%) |      65   →      60     (-7.69%) |       97.63 ms →       87.83 ms  (-10.04%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.93 ms →        3.91 ms   (-0.33%) |      65   →      60     (-7.69%) |      255.17 ms →      234.77 ms   (-7.99%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       59.94 μs →       61.49 μs   (+2.59%) |     130   →     120     (-7.69%) |        7.79 ms →        7.38 ms   (-5.30%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       82.05 μs →       82.64 μs   (+0.72%) |      65   →      60     (-7.69%) |        5.33 ms →        4.96 ms   (-7.03%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       68.93 μs →       70.35 μs   (+2.06%) |      65   →      60     (-7.69%) |        4.48 ms →        4.22 ms   (-5.79%) | 
  │ │ ├ sirius::Band::solve                                             |        2.13 s  →        2.10 s    (-1.66%) |      65   →      60     (-7.69%) |      138.52 s  →      125.74 s    (-9.22%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      217.85 μs →      214.86 μs   (-1.37%) |      65   →      60     (-7.69%) |       14.16 ms →       12.89 ms   (-8.96%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      210.57 μs →      206.79 μs   (-1.79%) |      65   →      60     (-7.69%) |       13.69 ms →       12.41 ms   (-9.35%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.98 μs →        5.71 μs  (+14.67%) |      65   →      60     (-7.69%) |      323.95 μs →      342.88 μs   (+5.85%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.11 s  →        2.07 s    (-2.04%) |      65   →      60     (-7.69%) |      137.44 s  →      124.28 s    (-9.57%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       47.84 ms →       49.17 ms   (+2.77%) |      65   →      60     (-7.69%) |        3.11 s  →        2.95 s    (-5.13%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        2.76 ms →        3.00 ms   (+8.67%) |     390   →     360     (-7.69%) |        1.08 s  →        1.08 s    (+0.31%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.58 ms →        1.58 ms   (-0.10%) |      65   →      60     (-7.69%) |      102.83 ms →       94.82 ms   (-7.79%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      418.58 μs →      420.71 μs   (+0.51%) |      65   →      60     (-7.69%) |       27.21 ms →       25.24 ms   (-7.22%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      906.55 μs →      905.70 μs   (-0.09%) |      65   →      60     (-7.69%) |       58.93 ms →       54.34 ms   (-7.78%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.04 s  →        2.00 s    (-2.18%) |      65   →      60     (-7.69%) |      132.66 s  →      119.79 s    (-9.70%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      222.49 ms →      222.91 ms   (+0.19%) |     325   →     307     (-5.54%) |       72.31 s  →       68.43 s    (-5.36%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      157.85 ms →      157.74 ms   (-0.07%) |     325   →     307     (-5.54%) |       51.30 s  →       48.43 s    (-5.61%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       29.17 ms →       28.48 ms   (-2.36%) |     325   →     307     (-5.54%) |        9.48 s  →        8.74 s    (-7.77%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      444.47 μs →      452.42 μs   (+1.79%) |     325   →     307     (-5.54%) |      144.45 ms →      138.89 ms   (-3.85%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.21 ms →        2.30 ms   (+4.13%) |      65   →      60     (-7.69%) |      143.77 ms →      138.19 ms   (-3.88%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       24.06 ms →       23.34 ms   (-3.00%) |     325   →     307     (-5.54%) |        7.82 s  →        7.17 s    (-8.37%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      425.88 μs →      456.23 μs   (+7.13%) |     325   →     307     (-5.54%) |      138.41 ms →      140.06 ms   (+1.19%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        2.11 ms →        2.32 ms   (+9.68%) |      65   →      60     (-7.69%) |      137.46 ms →      139.17 ms   (+1.24%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       36.18 ms →       35.53 ms   (-1.79%) |     325   →     307     (-5.54%) |       11.76 s  →       10.91 s    (-7.23%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       23.04 ms →       22.29 ms   (-3.25%) |     325   →     307     (-5.54%) |        7.49 s  →        6.84 s    (-8.61%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.63 ms →        2.67 ms   (+1.27%) |     325   →     307     (-5.54%) |      855.57 ms →      818.44 ms   (-4.34%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.72 ms →       23.71 ms   (-0.02%) |     325   →     307     (-5.54%) |        7.71 s  →        7.28 s    (-5.55%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.95 ms →        2.77 ms   (-6.10%) |     325   →     307     (-5.54%) |      958.84 ms →      850.53 ms  (-11.30%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.13 ms →       19.38 ms   (+1.32%) |     650   →     614     (-5.54%) |       12.44 s  →       11.90 s    (-4.29%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       60.58 ms →       60.22 ms   (-0.60%) |     325   →     307     (-5.54%) |       19.69 s  →       18.49 s    (-6.11%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       14.07 ms →       13.77 ms   (-2.15%) |     585   →     554     (-5.30%) |        8.23 s  →        7.63 s    (-7.34%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       47.25 ns →       64.73 ns  (+37.00%) |     585   →     554     (-5.30%) |       27.64 μs →       35.86 μs  (+29.74%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |       10.33 ms →       10.23 ms   (-0.90%) |     585   →     554     (-5.30%) |        6.04 s  →        5.67 s    (-6.15%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       62.33 ns →       63.07 ns   (+1.18%) |     585   →     554     (-5.30%) |       36.47 μs →       34.94 μs   (-4.18%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.28 ms →        3.30 ms   (+0.54%) |     325   →     307     (-5.54%) |        1.07 s  →        1.01 s    (-5.03%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.60 ms →       16.72 ms   (+0.71%) |     325   →     307     (-5.54%) |        5.40 s  →        5.13 s    (-4.87%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       19.20 ms →       19.07 ms   (-0.69%) |     260   →     247     (-5.00%) |        4.99 s  →        4.71 s    (-5.65%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        6.36 ms →        6.33 ms   (-0.44%) |     780   →     741     (-5.00%) |        4.96 s  →        4.69 s    (-5.42%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       21.96 ms →       21.48 ms   (-2.15%) |     325   →     307     (-5.54%) |        7.14 s  →        6.60 s    (-7.57%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       20.63 ms →       20.35 ms   (-1.36%) |     325   →     307     (-5.54%) |        6.71 s  →        6.25 s    (-6.82%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       82.09 ns →      113.61 ns  (+38.40%) |     325   →     307     (-5.54%) |       26.68 μs →       34.88 μs  (+30.74%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       17.07 ms →       16.89 ms   (-1.01%) |     325   →     307     (-5.54%) |        5.55 s  →        5.19 s    (-6.49%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       44.97 ns →       51.16 ns  (+13.77%) |     325   →     307     (-5.54%) |       14.61 μs →       15.71 μs   (+7.47%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       65.47 ms →       46.75 ms  (-28.60%) |     325   →     307     (-5.54%) |       21.28 s  →       14.35 s   (-32.56%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       19.51 ms →       17.65 ms   (-9.58%) |     321   →     299     (-6.85%) |        6.26 s  →        5.28 s   (-15.78%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       20.31 ms →       17.91 ms  (-11.82%) |     276   →     260     (-5.80%) |        5.60 s  →        4.66 s   (-16.93%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.73 ms →        8.44 ms   (-3.34%) |     552   →     520     (-5.80%) |        4.82 s  →        4.39 s    (-8.94%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.62 ms →        1.63 ms   (+0.43%) |     276   →     260     (-5.80%) |      447.35 ms →      423.24 ms   (-5.39%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       65.59 ms →       54.83 ms  (-16.41%) |      91   →     121    (+32.97%) |        5.97 s  →        6.63 s   (+11.15%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       50.41 ms →       35.55 ms  (-29.49%) |     117   →     182    (+55.56%) |        5.90 s  →        6.47 s    (+9.69%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       40.17 ms →       26.43 ms  (-34.19%) |     143   →     243    (+69.93%) |        5.74 s  →        6.42 s   (+11.83%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      686.72 ns →      591.48 ns  (-13.87%) |      65   →      60     (-7.69%) |       44.64 μs →       35.49 μs  (-20.49%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.99 μs →       27.46 μs  (-11.38%) |      65   →      60     (-7.69%) |        2.01 ms →        1.65 ms  (-18.20%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.55 ms →        3.57 ms   (+0.75%) |      65   →      60     (-7.69%) |      230.50 ms →      214.36 ms   (-7.00%) | 
  │ │ ├ sirius::Density::generate                                       |      298.98 ms →      298.16 ms   (-0.27%) |      65   →      60     (-7.69%) |       19.43 s  →       17.89 s    (-7.95%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      295.04 ms →      294.25 ms   (-0.27%) |      65   →      60     (-7.69%) |       19.18 s  →       17.66 s    (-7.94%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.09 ms →       66.89 ms   (-3.18%) |      65   →      60     (-7.69%) |        4.49 s  →        4.01 s   (-10.63%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       43.27 μs →       46.72 μs   (+7.98%) |      65   →      60     (-7.69%) |        2.81 ms →        2.80 ms   (-0.33%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms →        1.17 ms   (-0.22%) |       2   →       2              |        2.34 ms →        2.34 ms   (-0.22%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.82 ms →       55.63 ms   (-3.79%) |      65   →      60     (-7.69%) |        3.76 s  →        3.34 s   (-11.19%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.31 ms →       61.03 ms   (-0.46%) |      65   →      60     (-7.69%) |        3.99 s  →        3.66 s    (-8.12%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.60 μs →        9.26 μs   (-3.54%) |      65   →      60     (-7.69%) |      624.28 μs →      555.86 μs  (-10.96%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.28 ms →        2.31 ms   (+1.70%) |      65   →      60     (-7.69%) |      147.94 ms →      138.88 ms   (-6.12%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.49 ms →       58.17 ms   (-0.54%) |      65   →      60     (-7.69%) |        3.80 s  →        3.49 s    (-8.19%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.07 ms →        6.74 ms   (-4.63%) |      65   →      60     (-7.69%) |      459.61 ms →      404.63 ms  (-11.96%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      659.42 ns →      699.75 ns   (+6.12%) |      65   →      60     (-7.69%) |       42.86 μs →       41.98 μs   (-2.05%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.50 ms →      105.00 ms   (+0.48%) |      65   →      60     (-7.69%) |        6.79 s  →        6.30 s    (-7.25%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.43 ms →        2.44 ms   (+0.55%) |      65   →      60     (-7.69%) |      157.77 ms →      146.44 ms   (-7.18%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.08 ms →       20.04 ms   (-0.17%) |      65   →      60     (-7.69%) |        1.31 s  →        1.20 s    (-7.85%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.88 ms   (-0.01%) |      65   →      60     (-7.69%) |        1.29 s  →        1.19 s    (-7.70%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      253.11 ns →      487.22 ns  (+92.49%) |      65   →      60     (-7.69%) |       16.45 μs →       29.23 μs  (+77.69%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.16%) |      65   →      60     (-7.69%) |       81.63 ms →       75.23 ms   (-7.84%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.68 ms →        2.65 ms   (-1.17%) |      65   →      60     (-7.69%) |      174.49 ms →      159.19 ms   (-8.77%) | 
  │ │ ├ sirius::Density::mix                                            |       83.12 ms →       83.55 ms   (+0.52%) |      65   →      60     (-7.69%) |        5.40 s  →        5.01 s    (-7.21%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      276.62 μs →      272.34 μs   (-1.55%) |      65   →      60     (-7.69%) |       17.98 ms →       16.34 ms   (-9.12%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        2.65 ms →        2.91 ms   (+9.75%) |      65   →      60     (-7.69%) |      172.28 ms →      174.54 ms   (+1.31%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.44 ms →        2.71 ms  (+10.83%) |      65   →      60     (-7.69%) |      158.78 ms →      162.43 ms   (+2.30%) | 
  │ │ ├ sirius::Potential::generate                                     |      180.02 ms →      179.84 ms   (-0.10%) |      65   →      60     (-7.69%) |       11.70 s  →       10.79 s    (-7.79%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.21 ms →       63.78 ms   (-0.67%) |      65   →      60     (-7.69%) |        4.17 s  →        3.83 s    (-8.31%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.80 ms →        9.46 ms   (-3.46%) |      65   →      60     (-7.69%) |      636.84 ms →      567.51 ms  (-10.89%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.21 ms →        4.17 ms   (-0.97%) |      65   →      60     (-7.69%) |      273.95 ms →      250.44 ms   (-8.58%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.06 ms →        4.07 ms   (+0.12%) |      65   →      60     (-7.69%) |      264.12 ms →      244.10 ms   (-7.58%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.06 ms →        4.07 ms   (+0.12%) |      65   →      60     (-7.69%) |      264.09 ms →      244.08 ms   (-7.58%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      236.76 μs →      235.22 μs   (-0.65%) |     130   →     120     (-7.69%) |       30.78 ms →       28.23 ms   (-8.29%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       90.52 ms →       90.74 ms   (+0.24%) |      65   →      60     (-7.69%) |        5.88 s  →        5.44 s    (-7.47%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       89.49 ms →       89.73 ms   (+0.27%) |      65   →      60     (-7.69%) |        5.82 s  →        5.38 s    (-7.44%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.60 ms →        1.58 ms   (-1.24%) |     325   →     300     (-7.69%) |      519.66 ms →      473.73 ms   (-8.84%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.44 ms →        2.51 ms   (+2.71%) |     585   →     540     (-7.69%) |        1.43 s  →        1.35 s    (-5.19%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.42 ms →        2.37 ms   (-2.20%) |      65   →      60     (-7.69%) |      157.53 ms →      142.22 ms   (-9.72%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      708.07 μs →      694.18 μs   (-1.96%) |     195   →     180     (-7.69%) |      138.07 ms →      124.95 ms   (-9.50%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.85 ms →        2.81 ms   (-1.37%) |      65   →      60     (-7.69%) |      185.18 ms →      168.60 ms   (-8.95%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.62 ms →        2.57 ms   (-1.62%) |      65   →      60     (-7.69%) |      170.08 ms →      154.45 ms   (-9.19%) | 
  │ │ │ │   └ sirius::divergence                                        |       19.82 ms →       19.75 ms   (-0.34%) |      65   →      60     (-7.69%) |        1.29 s  →        1.19 s    (-8.01%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.45 ms →        2.43 ms   (-0.82%) |      65   →      60     (-7.69%) |      159.07 ms →      145.63 ms   (-8.45%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.27 ms →        3.34 ms   (+2.14%) |      65   →      60     (-7.69%) |      212.37 ms →      200.23 ms   (-5.72%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.99 ms →       20.96 ms   (-0.16%) |      65   →      60     (-7.69%) |        1.36 s  →        1.26 s    (-7.84%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      309.34 ns →      226.28 ns  (-26.85%) |      65   →      60     (-7.69%) |       20.11 μs →       13.58 μs  (-32.48%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      236.65 ns →      378.13 ns  (+59.79%) |      65   →      60     (-7.69%) |       15.38 μs →       22.69 μs  (+47.50%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.27 ms →        2.22 ms   (-2.05%) |      65   →      60     (-7.69%) |      147.46 ms →      133.33 ms   (-9.58%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.11 ms →        4.08 ms   (-0.82%) |     455   →     420     (-7.69%) |        1.87 s  →        1.71 s    (-8.45%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.94 ms →        3.93 ms   (-0.31%) |     455   →     420     (-7.69%) |        1.79 s  →        1.65 s    (-7.98%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.94 ms →        3.93 ms   (-0.31%) |     455   →     420     (-7.69%) |        1.79 s  →        1.65 s    (-7.98%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.38 ms →        4.21 ms   (-3.93%) |     195   →     180     (-7.69%) |      855.05 ms →      758.27 ms  (-11.32%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.25 ms →        4.03 ms   (-5.14%) |     195   →     180     (-7.69%) |      829.13 ms →      725.99 ms  (-12.44%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.01 ms →        4.03 ms   (+0.44%) |      65   →      60     (-7.69%) |      260.50 ms →      241.53 ms   (-7.28%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      115.46 μs →      108.18 μs   (-6.30%) |      65   →      60     (-7.69%) |        7.50 ms →        6.49 ms  (-13.51%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      112.09 μs →      104.93 μs   (-6.39%) |      65   →      60     (-7.69%) |        7.29 ms →        6.30 ms  (-13.59%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.27 ms →        5.73 ms   (+8.70%) |       2   →       2              |       10.54 ms →       11.46 ms   (+8.70%) | 
  │ ├ sirius::Periodic_function|inner                                   |        3.99 ms →        4.08 ms   (+2.39%) |       6   →       6              |       23.94 ms →       24.51 ms   (+2.39%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.91 ms →        3.88 ms   (-0.64%) |       6   →       6              |       23.44 ms →       23.29 ms   (-0.64%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.91 ms →        3.88 ms   (-0.64%) |       6   →       6              |       23.44 ms →       23.29 ms   (-0.64%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.27 ms →        4.14 ms   (-3.03%) |       3   →       3              |       12.80 ms →       12.41 ms   (-3.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.21 ms →        4.07 ms   (-3.43%) |       3   →       3              |       12.64 ms →       12.21 ms   (-3.43%) | 
  ├ sirius::Periodic_function|inner                                     |        4.14 ms →        4.10 ms   (-1.16%) |       2   →       2              |        8.29 ms →        8.19 ms   (-1.16%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.13 ms →        4.06 ms   (-1.77%) |       2   →       2              |        8.27 ms →        8.12 ms   (-1.77%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.13 ms →        4.06 ms   (-1.77%) |       2   →       2              |        8.27 ms →        8.12 ms   (-1.77%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.25 ms →        4.07 ms   (-4.23%) |       1   →       1              |        4.25 ms →        4.07 ms   (-4.23%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.21 ms →        4.05 ms   (-3.79%) |       1   →       1              |        4.21 ms →        4.05 ms   (-3.79%) | 
  └ sirius::finalize                                                    |      272.06 ms →      290.89 ms   (+6.92%) |       1   →       1              |      272.06 ms →      290.89 ms   (+6.92%) | 
  ====================================================================================================================================================================================================
```
