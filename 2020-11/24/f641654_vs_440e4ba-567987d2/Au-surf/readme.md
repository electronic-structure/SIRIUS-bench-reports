# Benchmark 440e4baa3b03646988c956603d0cb2cbea939e9f vs f641654ae8bc5cecb285c326c4cb5850ab38d32a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      118.61 s  →      122.79 s    (+3.52%) |       1   →       1              |      118.61 s  →      122.79 s    (+3.52%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.74 s    (-0.39%) |       1   →       1              |        2.75 s  →        2.74 s    (-0.39%) | 
  ├ sirius::Simulation_context::initialize                              |        2.02 s  →        2.07 s    (+2.40%) |       1   →       1              |        2.02 s  →        2.07 s    (+2.40%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      294.77 μs →       30.02 ms (+10085.74%) |       1   →       1              |      294.77 μs →       30.02 ms (+10085.74%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       82.69 ms →      102.13 ms  (+23.52%) |       1   →       1              |       82.69 ms →      102.13 ms  (+23.52%) | 
- │ │ ├ sirius::Atom_type::init                                         |       55.99 ms →       75.67 ms  (+35.16%) |       1   →       1              |       55.99 ms →       75.67 ms  (+35.16%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.64 ms →       26.40 ms   (-0.90%) |       1   →       1              |       26.64 ms →       26.40 ms   (-0.90%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.16 ms →       10.56 ms   (+3.91%) |       1   →       1              |       10.16 ms →       10.56 ms   (+3.91%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.44 ms →       15.81 ms   (-3.83%) |       1   →       1              |       16.44 ms →       15.81 ms   (-3.83%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.03 ms →       15.04 ms   (-6.17%) |       1   →       1              |       16.03 ms →       15.04 ms   (-6.17%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       15.80 ms →       14.82 ms   (-6.19%) |       1   →       1              |       15.80 ms →       14.82 ms   (-6.19%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      217.29 μs →      206.34 μs   (-5.04%) |       1   →       1              |      217.29 μs →      206.34 μs   (-5.04%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.51 μs →        2.50 μs   (-0.40%) |       1   →       1              |        2.51 μs →        2.50 μs   (-0.40%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.89 s    (-0.02%) |       1   →       1              |        1.89 s  →        1.89 s    (-0.02%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.74 ms →       13.06 ms   (+2.47%) |       1   →       1              |       12.74 ms →       13.06 ms   (+2.47%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.20 ms →        8.30 ms   (+1.14%) |       1   →       1              |        8.20 ms →        8.30 ms   (+1.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.52 ms →        4.74 ms   (+4.90%) |       1   →       1              |        4.52 ms →        4.74 ms   (+4.90%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.13 ms →        4.13 ms   (-0.21%) |       1   →       1              |        4.13 ms →        4.13 ms   (-0.21%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.94 ms →        3.93 ms   (-0.23%) |       1   →       1              |        3.94 ms →        3.93 ms   (-0.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      194.31 μs →      194.68 μs   (+0.19%) |       1   →       1              |      194.31 μs →      194.68 μs   (+0.19%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.13 μs →        1.13 μs   (-0.18%) |       1   →       1              |        1.13 μs →        1.13 μs   (-0.18%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       16.94 ms →       15.30 ms   (-9.66%) |       2   →       2              |       33.88 ms →       30.61 ms   (-9.66%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.08 ms →        1.09 ms   (+0.76%) |       2   →       2              |        2.17 ms →        2.18 ms   (+0.76%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      977.24 μs →      951.48 μs   (-2.64%) |       1   →       1              |      977.24 μs →      951.48 μs   (-2.64%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.07 ms →        5.05 ms   (-0.22%) |       2   →       2              |       10.13 ms →       10.11 ms   (-0.22%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.65 ms   (-0.10%) |       2   →       2              |        7.30 ms →        7.29 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.98 ms →       15.68 ms   (-1.84%) |       4   →       4              |       63.90 ms →       62.73 ms   (-1.84%) | 
  │   ├ sddk::Gvec::init                                                |      157.91 ms →      157.89 ms   (-0.01%) |       2   →       2              |      315.82 ms →      315.78 ms   (-0.01%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      124.69 ms →      125.04 ms   (+0.28%) |       2   →       2              |      249.39 ms →      250.08 ms   (+0.28%) | 
  │   ├ sddk::Gvec_shells                                               |      126.63 ms →      126.20 ms   (-0.34%) |       1   →       1              |      126.63 ms →      126.20 ms   (-0.34%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.05 ms →        1.03 ms   (-1.84%) |       1   →       1              |        1.05 ms →        1.03 ms   (-1.84%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      219.31 ms →      227.00 ms   (+3.51%) |       1   →       1              |      219.31 ms →      227.00 ms   (+3.51%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.95 ms →       25.76 ms   (-0.75%) |       1   →       1              |       25.95 ms →       25.76 ms   (-0.75%) | 
- │ ├ sirius::K_point::K_point                                          |        1.77 μs →        2.07 μs  (+16.84%) |       2   →       2              |        3.54 μs →        4.14 μs  (+16.84%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.92 ms →       25.72 ms   (-0.77%) |       1   →       1              |       25.92 ms →       25.72 ms   (-0.77%) | 
  │   └ sirius::K_point::initialize                                     |       25.85 ms →       25.65 ms   (-0.79%) |       1   →       1              |       25.85 ms →       25.65 ms   (-0.79%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.38 ms →       19.26 ms   (-0.63%) |       1   →       1              |       19.38 ms →       19.26 ms   (-0.63%) | 
  │     │ └ sddk::Gvec::init                                            |        4.93 ms →        4.79 ms   (-2.71%) |       1   →       1              |        4.93 ms →        4.79 ms   (-2.71%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.52 μs →       10.37 μs   (-1.45%) |       1   →       1              |       10.52 μs →       10.37 μs   (-1.45%) | 
  │     └ sirius::K_point::update                                       |        4.11 ms →        3.93 ms   (-4.36%) |       1   →       1              |        4.11 ms →        3.93 ms   (-4.36%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.56 ms   (-8.87%) |       1   →       1              |        1.72 ms →        1.56 ms   (-8.87%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      898.47 μs →      890.01 μs   (-0.94%) |       1   →       1              |      898.47 μs →      890.01 μs   (-0.94%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.50 ms →        1.46 ms   (-2.40%) |       2   →       2              |        3.00 ms →        2.93 ms   (-2.40%) | 
  ├ sirius::Potential                                                   |       89.92 ms →       94.24 ms   (+4.81%) |       1   →       1              |       89.92 ms →       94.24 ms   (+4.81%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.50 ms →        2.44 ms   (-2.34%) |       6   →       6              |       14.97 ms →       14.62 ms   (-2.34%) | 
  │ └ sirius::Potential::update                                         |       74.58 ms →       79.28 ms   (+6.29%) |       1   →       1              |       74.58 ms →       79.28 ms   (+6.29%) | 
  │   └ sirius::Potential::generate_local_potential                     |       74.41 ms →       79.11 ms   (+6.32%) |       1   →       1              |       74.41 ms →       79.11 ms   (+6.32%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       51.01 ms →       50.90 ms   (-0.20%) |       1   →       1              |       51.01 ms →       50.90 ms   (-0.20%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       14.39 ms →       19.42 ms  (+34.96%) |       1   →       1              |       14.39 ms →       19.42 ms  (+34.96%) | 
  ├ sirius::Density                                                     |       72.90 ms →       73.20 ms   (+0.42%) |       1   →       1              |       72.90 ms →       73.20 ms   (+0.42%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.86 ms →        5.17 ms   (+6.48%) |       2   →       2              |        9.72 ms →       10.34 ms   (+6.48%) | 
  │ └ sirius::Density::update                                           |       63.07 ms →       62.83 ms   (-0.38%) |       1   →       1              |       63.07 ms →       62.83 ms   (-0.38%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       62.90 ms →       62.66 ms   (-0.38%) |       1   →       1              |       62.90 ms →       62.66 ms   (-0.38%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        2.41 ms →        2.65 ms   (+9.92%) |       1   →       1              |        2.41 ms →        2.65 ms   (+9.92%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       48.89 ms →       50.02 ms   (+2.31%) |       1   →       1              |       48.89 ms →       50.02 ms   (+2.31%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.32 ms →        8.67 ms  (-15.95%) |       1   →       1              |       10.32 ms →        8.67 ms  (-15.95%) | 
  ├ sirius::Density::initial_density                                    |       79.50 ms →       79.07 ms   (-0.54%) |       1   →       1              |       79.50 ms →       79.07 ms   (-0.54%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       52.43 ms →       51.58 ms   (-1.61%) |       1   →       1              |       52.43 ms →       51.58 ms   (-1.61%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.35 ms →        5.70 ms   (+6.55%) |       2   →       2              |       10.71 ms →       11.41 ms   (+6.55%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.58 ms →        4.31 ms   (-5.94%) |       1   →       1              |        4.58 ms →        4.31 ms   (-5.94%) | 
  ├ sirius::Potential::generate                                         |      187.02 ms →      186.28 ms   (-0.40%) |       1   →       1              |      187.02 ms →      186.28 ms   (-0.40%) | 
  │ ├ sirius::Potential::poisson                                        |       63.76 ms →       63.76 ms   (+0.00%) |       1   →       1              |       63.76 ms →       63.76 ms   (+0.00%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.50 ms →        9.77 ms   (+2.80%) |       1   →       1              |        9.50 ms →        9.77 ms   (+2.80%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.40 ms →        4.20 ms   (-4.75%) |       1   →       1              |        4.40 ms →        4.20 ms   (-4.75%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.08 ms →        4.09 ms   (+0.12%) |       1   →       1              |        4.08 ms →        4.09 ms   (+0.12%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        4.09 ms   (+0.12%) |       1   →       1              |        4.08 ms →        4.09 ms   (+0.12%) | 
  │ ├ sirius::Periodic_function::add                                    |      251.44 μs →      239.00 μs   (-4.95%) |       2   →       2              |      502.89 μs →      478.00 μs   (-4.95%) | 
  │ ├ sirius::Potential::xc                                             |       96.71 ms →       96.09 ms   (-0.64%) |       1   →       1              |       96.71 ms →       96.09 ms   (-0.64%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       95.63 ms →       95.08 ms   (-0.57%) |       1   →       1              |       95.63 ms →       95.08 ms   (-0.57%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.01 ms →        1.97 ms   (-2.12%) |       5   →       5              |       10.07 ms →        9.86 ms   (-2.12%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.50 ms →        2.49 ms   (-0.29%) |       9   →       9              |       22.50 ms →       22.44 ms   (-0.29%) | 
  │ │   ├ sirius::gradient                                              |        7.68 ms →        7.50 ms   (-2.41%) |       1   →       1              |        7.68 ms →        7.50 ms   (-2.41%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.47 ms →        2.41 ms   (-2.45%) |       3   →       3              |        7.40 ms →        7.22 ms   (-2.45%) | 
  │ │   ├ sirius::dot                                                   |        2.85 ms →        2.81 ms   (-1.25%) |       1   →       1              |        2.85 ms →        2.81 ms   (-1.25%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.63 ms →        2.59 ms   (-1.58%) |       1   →       1              |        2.63 ms →        2.59 ms   (-1.58%) | 
  │ │   └ sirius::divergence                                            |       19.77 ms →       19.69 ms   (-0.43%) |       1   →       1              |       19.77 ms →       19.69 ms   (-0.43%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.46 ms →        2.43 ms   (-1.16%) |       1   →       1              |        2.46 ms →        2.43 ms   (-1.16%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.26 ms →        3.15 ms   (-3.29%) |       1   →       1              |        3.26 ms →        3.15 ms   (-3.29%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.17 ms →       22.25 ms   (+0.37%) |       1   →       1              |       22.17 ms →       22.25 ms   (+0.37%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |       57.00 ns →      200.00 ns (+250.88%) |       1   →       1              |       57.00 ns →      200.00 ns (+250.88%) | 
  ├ sirius::Hamiltonian0                                                |       14.36 ms →       14.06 ms   (-2.14%) |       1   →       1              |       14.36 ms →       14.06 ms   (-2.14%) | 
  │ ├ sirius::Local_operator                                            |       14.04 ms →       13.73 ms   (-2.19%) |       1   →       1              |       14.04 ms →       13.73 ms   (-2.19%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.15 ms →        7.06 ms   (-1.26%) |       1   →       1              |        7.15 ms →        7.06 ms   (-1.26%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.43 ms →        5.22 ms   (-3.83%) |       1   →       1              |        5.43 ms →        5.22 ms   (-3.83%) | 
  │ ├ sirius::Non_local_operator                                        |       58.53 μs →       59.99 μs   (+2.49%) |       2   →       2              |      117.06 μs →      119.98 μs   (+2.49%) | 
  │ ├ sirius::D_operator::initialize                                    |       81.43 μs →       80.31 μs   (-1.37%) |       1   →       1              |       81.43 μs →       80.31 μs   (-1.37%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.16 μs →       69.06 μs   (-0.16%) |       1   →       1              |       69.16 μs →       69.06 μs   (-0.16%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.48 s  →        2.45 s    (-1.36%) |       1   →       1              |        2.48 s  →        2.45 s    (-1.36%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.38 ms   (-0.37%) |       1   →       1              |        8.41 ms →        8.38 ms   (-0.37%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      252.07 μs →      225.19 μs  (-10.66%) |       1   →       1              |      252.07 μs →      225.19 μs  (-10.66%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.15 ms   (-0.06%) |       1   →       1              |        8.16 ms →        8.15 ms   (-0.06%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.47 s  →        2.44 s    (-1.36%) |       1   →       1              |        2.47 s  →        2.44 s    (-1.36%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.65 ms →       88.22 ms   (+1.82%) |       4   →       4              |      346.59 ms →      352.89 ms   (+1.82%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.84 ms →       25.20 ms   (-2.46%) |       1   →       1              |       25.84 ms →       25.20 ms   (-2.46%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.80 ms →       14.39 ms   (-2.75%) |       1   →       1              |       14.80 ms →       14.39 ms   (-2.75%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.22 s  →        1.20 s    (-1.32%) |       1   →       1              |        1.22 s  →        1.20 s    (-1.32%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      993.28 ms →      977.54 ms   (-1.58%) |       1   →       1              |      993.28 ms →      977.54 ms   (-1.58%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      319.05 ms →      308.10 ms   (-3.43%) |       1   →       1              |      319.05 ms →      308.10 ms   (-3.43%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      176.23 ms →      175.99 ms   (-0.13%) |       1   →       1              |      176.23 ms →      175.99 ms   (-0.13%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      176.23 ms →      175.99 ms   (-0.13%) |       1   →       1              |      176.23 ms →      175.99 ms   (-0.13%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      124.31 ms →      113.65 ms   (-8.57%) |       1   →       1              |      124.31 ms →      113.65 ms   (-8.57%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      172.27 ms →      175.90 ms   (+2.11%) |       1   →       1              |      172.27 ms →      175.90 ms   (+2.11%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      172.26 ms →      175.89 ms   (+2.11%) |       1   →       1              |      172.26 ms →      175.89 ms   (+2.11%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      171.41 ms →      163.24 ms   (-4.77%) |       1   →       1              |      171.41 ms →      163.24 ms   (-4.77%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      120.74 ms →      112.76 ms   (-6.61%) |       1   →       1              |      120.74 ms →      112.76 ms   (-6.61%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.73 ms →        3.73 ms   (+0.02%) |       1   →       1              |        3.73 ms →        3.73 ms   (+0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.95 ms →       89.62 ms   (-0.37%) |       1   →       1              |       89.95 ms →       89.62 ms   (-0.37%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.10 ms →       11.91 ms   (-1.53%) |       1   →       1              |       12.10 ms →       11.91 ms   (-1.53%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.18 ms →       64.20 ms   (+0.04%) |       2   →       2              |      128.35 ms →      128.40 ms   (+0.04%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      197.52 ms →      190.62 ms   (-3.50%) |       2   →       2              |      395.05 ms →      381.24 ms   (-3.50%) | 
  │ │ │ └ sddk::wf_inner                                                |      197.43 ms →      190.52 ms   (-3.50%) |       2   →       2              |      394.85 ms →      381.04 ms   (-3.50%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       36.00 ns →       27.50 ns  (-23.61%) |       2   →       2              |       72.00 ns →       55.00 ns  (-23.61%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      195.00 ms →      188.02 ms   (-3.58%) |       2   →       2              |      389.99 ms →      376.05 ms   (-3.58%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       23.50 ns →       16.00 ns  (-31.91%) |       2   →       2              |       47.00 ns →       32.00 ns  (-31.91%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      115.43 ms →      115.81 ms   (+0.33%) |       1   →       1              |      115.43 ms →      115.81 ms   (+0.33%) | 
  │ │ └ sddk::wf_trans                                                  |       38.08 ms →       35.82 ms   (-5.93%) |       1   →       1              |       38.08 ms →       35.82 ms   (-5.93%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.65 ms →       35.55 ms   (-0.30%) |       1   →       1              |       35.65 ms →       35.55 ms   (-0.30%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      475.00 ns →      591.00 ns  (+24.42%) |       1   →       1              |      475.00 ns →      591.00 ns  (+24.42%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      109.81 s  →      113.91 s    (+3.74%) |       1   →       1              |      109.81 s  →      113.91 s    (+3.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.19 ms →        2.13 ms   (-2.65%) |      29   →      29              |       63.38 ms →       61.70 ms   (-2.65%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.88 s  →        2.53 s   (-12.23%) |      38   →      45    (+18.42%) |      109.36 s  →      113.67 s    (+3.94%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.11 ms →        7.54 ms   (+6.03%) |      38   →      45    (+18.42%) |      270.36 ms →      339.48 ms  (+25.57%) | 
- │ │ │ ├ sirius::Local_operator                                        |        6.78 ms →        7.21 ms   (+6.29%) |      38   →      45    (+18.42%) |      257.73 ms →      324.39 ms  (+25.87%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms →        1.51 ms   (+0.63%) |      38   →      45    (+18.42%) |       56.87 ms →       67.77 ms  (+19.17%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.83 ms →        4.26 ms  (+11.26%) |      38   →      45    (+18.42%) |      145.55 ms →      191.77 ms  (+31.75%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       60.02 μs →       61.06 μs   (+1.73%) |      76   →      90    (+18.42%) |        4.56 ms →        5.50 ms  (+20.47%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       82.91 μs →       84.21 μs   (+1.56%) |      38   →      45    (+18.42%) |        3.15 ms →        3.79 ms  (+20.27%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       68.89 μs →       70.22 μs   (+1.93%) |      38   →      45    (+18.42%) |        2.62 ms →        3.16 ms  (+20.70%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.24 s  →        1.88 s   (-15.84%) |      38   →      45    (+18.42%) |       85.02 s  →       84.73 s    (-0.33%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      211.12 μs →      207.19 μs   (-1.86%) |      38   →      45    (+18.42%) |        8.02 ms →        9.32 ms  (+16.21%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      204.02 μs →      199.96 μs   (-1.99%) |      38   →      45    (+18.42%) |        7.75 ms →        9.00 ms  (+16.07%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.26 μs →        5.13 μs   (-2.45%) |      38   →      45    (+18.42%) |      199.83 μs →      230.83 μs  (+15.51%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.24 s  →        1.87 s   (-16.59%) |      38   →      45    (+18.42%) |       85.00 s  →       83.96 s    (-1.23%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       59.93 ms →       55.35 ms   (-7.64%) |      38   →      45    (+18.42%) |        2.28 s  →        2.49 s    (+9.37%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.68 ms →        3.94 ms  (-15.65%) |     228   →     270    (+18.42%) |        1.07 s  →        1.07 s    (-0.11%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.65 ms →        1.62 ms   (-2.01%) |      38   →      45    (+18.42%) |       62.71 ms →       72.77 ms  (+16.04%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.66 μs →      418.15 μs   (-0.83%) |      38   →      45    (+18.42%) |       16.02 ms →       18.82 ms  (+17.44%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      970.36 μs →      941.31 μs   (-2.99%) |      38   →      45    (+18.42%) |       36.87 ms →       42.36 ms  (+14.88%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.15 s  →        1.78 s   (-17.04%) |      38   →      45    (+18.42%) |       81.74 s  →       80.31 s    (-1.76%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.03 ms →      198.75 ms   (-7.14%) |     201   →     218     (+8.46%) |       43.02 s  →       43.33 s    (+0.71%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.39 ms →      140.56 ms   (-7.15%) |     201   →     218     (+8.46%) |       30.43 s  →       30.64 s    (+0.70%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       28.21 ms →       26.04 ms   (-7.71%) |     201   →     218     (+8.46%) |        5.67 s  →        5.68 s    (+0.10%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      714.49 μs →      648.28 μs   (-9.27%) |     201   →     218     (+8.46%) |      143.61 ms →      141.32 ms   (-1.59%) | 
+ │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.77 ms →        3.13 ms  (-16.90%) |      38   →      45    (+18.42%) |      143.13 ms →      140.85 ms   (-1.60%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       23.06 ms →       21.29 ms   (-7.64%) |     201   →     218     (+8.46%) |        4.63 s  →        4.64 s    (+0.18%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      718.69 μs →      644.25 μs  (-10.36%) |     201   →     218     (+8.46%) |      144.46 ms →      140.45 ms   (-2.78%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.79 ms →        3.11 ms  (-17.89%) |      38   →      45    (+18.42%) |      143.89 ms →      139.92 ms   (-2.76%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.33 ms →       31.97 ms   (-6.88%) |     201   →     218     (+8.46%) |        6.90 s  →        6.97 s    (+0.99%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.74 ms →       20.31 ms   (-6.59%) |     201   →     218     (+8.46%) |        4.37 s  →        4.43 s    (+1.31%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.64 ms →        2.62 ms   (-0.82%) |     201   →     218     (+8.46%) |      531.48 ms →      571.73 ms   (+7.57%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.49 ms →       21.00 ms   (-6.62%) |     201   →     218     (+8.46%) |        4.52 s  →        4.58 s    (+1.27%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.53 ms →        2.41 ms   (-4.83%) |     201   →     218     (+8.46%) |      508.05 ms →      524.39 ms   (+3.22%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.74 ms →       17.27 ms   (-7.84%) |     402   →     436     (+8.46%) |        7.53 s  →        7.53 s    (-0.05%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       86.14 ms →       77.78 ms   (-9.71%) |     201   →     218     (+8.46%) |       17.31 s  →       16.96 s    (-2.07%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       13.13 ms →       12.24 ms   (-6.76%) |     364   →     391     (+7.42%) |        4.78 s  →        4.79 s    (+0.16%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       84.46 ns →       75.75 ns  (-10.32%) |     364   →     391     (+7.42%) |       30.74 μs →       29.62 μs   (-3.66%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.69 ms →        8.57 ms  (-11.57%) |     364   →     391     (+7.42%) |        3.53 s  →        3.35 s    (-5.01%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.85 ns →       92.55 ns (+101.85%) |     364   →     391     (+7.42%) |       16.69 μs →       36.19 μs (+116.82%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       32.37 ms →       30.10 ms   (-7.01%) |     201   →     218     (+8.46%) |        6.51 s  →        6.56 s    (+0.86%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.69 ms →       15.25 ms   (-2.82%) |     201   →     218     (+8.46%) |        3.15 s  →        3.32 s    (+5.39%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |       17.63 ms →       13.19 ms  (-25.19%) |     163   →     173     (+6.13%) |        2.87 s  →        2.28 s   (-20.60%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.85 ms →        4.36 ms  (-25.47%) |     489   →     519     (+6.13%) |        2.86 s  →        2.26 s   (-20.90%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.74 ms →       20.78 ms   (-8.59%) |     201   →     218     (+8.46%) |        4.57 s  →        4.53 s    (-0.86%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       21.39 ms →       19.63 ms   (-8.24%) |     201   →     218     (+8.46%) |        4.30 s  →        4.28 s    (-0.48%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |      106.00 ns →      146.58 ns  (+38.29%) |     201   →     218     (+8.46%) |       21.30 μs →       31.95 μs  (+49.98%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       16.17 ms →       14.41 ms  (-10.92%) |     201   →     218     (+8.46%) |        3.25 s  →        3.14 s    (-3.39%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |      140.99 ns →       21.55 ns  (-84.72%) |     201   →     218     (+8.46%) |       28.34 μs →        4.70 μs  (-83.43%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       47.02 ms →       36.73 ms  (-21.88%) |     201   →     218     (+8.46%) |        9.45 s  →        8.01 s   (-15.28%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       16.33 ms →       14.14 ms  (-13.43%) |     196   →     214     (+9.18%) |        3.20 s  →        3.03 s    (-5.48%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       17.21 ms →       13.86 ms  (-19.44%) |     164   →     192    (+17.07%) |        2.82 s  →        2.66 s    (-5.69%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.04 ms →        6.59 ms  (-18.09%) |     328   →     384    (+17.07%) |        2.64 s  →        2.53 s    (-4.10%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.56 ms →        1.35 ms  (-13.83%) |     164   →     192    (+17.07%) |      256.36 ms →      258.62 ms   (+0.88%) | 
! │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       52.20 ms →       50.00 ms   (-4.20%) |      80   →      89    (+11.25%) |        4.18 s  →        4.45 s    (+6.57%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       33.28 ms →       32.58 ms   (-2.09%) |     122   →     133     (+9.02%) |        4.06 s  →        4.33 s    (+6.74%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       24.37 ms →       24.32 ms   (-0.22%) |     164   →     177     (+7.93%) |        4.00 s  →        4.30 s    (+7.69%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      552.39 ns →      562.38 ns   (+1.81%) |      38   →      45    (+18.42%) |       20.99 μs →       25.31 μs  (+20.56%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       31.20 μs →       24.15 μs  (-22.58%) |      38   →      45    (+18.42%) |        1.19 ms →        1.09 ms   (-8.31%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.53 ms →        3.47 ms   (-1.64%) |      38   →      45    (+18.42%) |      133.96 ms →      156.04 ms  (+16.48%) | 
- │ │ ├ sirius::Density::generate                                       |      298.33 ms →      297.23 ms   (-0.37%) |      38   →      45    (+18.42%) |       11.34 s  →       13.38 s   (+17.98%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      294.39 ms →      293.18 ms   (-0.41%) |      38   →      45    (+18.42%) |       11.19 s  →       13.19 s   (+17.93%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.05 ms →       68.37 ms   (-0.99%) |      38   →      45    (+18.42%) |        2.62 s  →        3.08 s   (+17.25%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       68.10 μs →       55.43 μs  (-18.59%) |      38   →      45    (+18.42%) |        2.59 ms →        2.49 ms   (-3.60%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.24 ms →        1.19 ms   (-4.45%) |       2   →       2              |        2.48 ms →        2.37 ms   (-4.45%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.75 ms →       57.17 ms   (-0.99%) |      38   →      45    (+18.42%) |        2.19 s  →        2.57 s   (+17.24%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.97 ms →       61.45 ms   (-0.84%) |      38   →      45    (+18.42%) |        2.35 s  →        2.77 s   (+17.43%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.95 μs →       10.27 μs   (-6.17%) |      38   →      45    (+18.42%) |      415.98 μs →      462.19 μs  (+11.11%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.32 ms   (+0.29%) |      38   →      45    (+18.42%) |       87.72 ms →      104.18 ms  (+18.76%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       59.11 ms →       58.60 ms   (-0.86%) |      38   →      45    (+18.42%) |        2.25 s  →        2.64 s   (+17.40%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.69 ms →        7.18 ms   (-6.64%) |      38   →      45    (+18.42%) |      292.06 ms →      322.89 ms  (+10.56%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      542.29 ns →      580.51 ns   (+7.05%) |      38   →      45    (+18.42%) |       20.61 μs →       26.12 μs  (+26.77%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.31 ms →      104.34 ms   (+0.02%) |      38   →      45    (+18.42%) |        3.96 s  →        4.70 s   (+18.45%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.45 ms →        2.41 ms   (-1.71%) |      38   →      45    (+18.42%) |       93.00 ms →      108.25 ms  (+16.39%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms →       20.04 ms   (-0.09%) |      38   →      45    (+18.42%) |      762.34 ms →      902.00 ms  (+18.32%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms →       19.87 ms   (-0.12%) |      38   →      45    (+18.42%) |      756.17 ms →      894.37 ms  (+18.28%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      241.74 ns →      236.09 ns   (-2.34%) |      38   →      45    (+18.42%) |        9.19 μs →       10.62 μs  (+15.65%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.25 ms   (-0.04%) |      38   →      45    (+18.42%) |       47.53 ms →       56.26 ms  (+18.37%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.69 ms →        2.80 ms   (+4.18%) |      38   →      45    (+18.42%) |      102.08 ms →      125.94 ms  (+23.37%) | 
- │ │ ├ sirius::Density::mix                                            |      102.06 ms →      106.58 ms   (+4.43%) |      38   →      45    (+18.42%) |        3.88 s  →        4.80 s   (+23.67%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      254.28 μs →      258.84 μs   (+1.79%) |      38   →      45    (+18.42%) |        9.66 ms →       11.65 ms  (+20.55%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        2.57 ms →        2.52 ms   (-1.84%) |      38   →      45    (+18.42%) |       97.59 ms →      113.44 ms  (+16.24%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.38 ms   (-1.57%) |      38   →      45    (+18.42%) |       92.05 ms →      107.30 ms  (+16.56%) | 
- │ │ ├ sirius::Potential::generate                                     |      180.34 ms →      179.78 ms   (-0.31%) |      38   →      45    (+18.42%) |        6.85 s  →        8.09 s   (+18.06%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       63.90 ms →       63.96 ms   (+0.09%) |      38   →      45    (+18.42%) |        2.43 s  →        2.88 s   (+18.53%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.79 ms →        9.77 ms   (-0.18%) |      38   →      45    (+18.42%) |      372.07 ms →      439.82 ms  (+18.21%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.24 ms →        4.25 ms   (+0.29%) |      38   →      45    (+18.42%) |      160.96 ms →      191.16 ms  (+18.76%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.12 ms →        4.10 ms   (-0.49%) |      38   →      45    (+18.42%) |      156.38 ms →      184.28 ms  (+17.84%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.11 ms →        4.09 ms   (-0.49%) |      38   →      45    (+18.42%) |      156.35 ms →      184.25 ms  (+17.84%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      230.84 μs →      229.44 μs   (-0.61%) |      76   →      90    (+18.42%) |       17.54 ms →       20.65 ms  (+17.70%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       91.15 ms →       90.46 ms   (-0.76%) |      38   →      45    (+18.42%) |        3.46 s  →        4.07 s   (+17.53%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       90.12 ms →       89.43 ms   (-0.77%) |      38   →      45    (+18.42%) |        3.42 s  →        4.02 s   (+17.51%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.63 ms →        1.59 ms   (-2.46%) |     190   →     225    (+18.42%) |      309.59 ms →      357.62 ms  (+15.51%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.45 ms →        2.44 ms   (-0.61%) |     342   →     405    (+18.42%) |      839.17 ms →      987.64 ms  (+17.69%) | 
- │ │ │ │   ├ sirius::gradient                                          |        2.47 ms →        2.47 ms   (-0.06%) |      38   →      45    (+18.42%) |       93.79 ms →      110.99 ms  (+18.34%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      728.45 μs →      727.58 μs   (-0.12%) |     114   →     135    (+18.42%) |       83.04 ms →       98.22 ms  (+18.28%) | 
- │ │ │ │   ├ sirius::dot                                               |        2.81 ms →        2.82 ms   (+0.14%) |      38   →      45    (+18.42%) |      106.85 ms →      126.70 ms  (+18.58%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms →        2.59 ms   (+0.30%) |      38   →      45    (+18.42%) |       97.98 ms →      116.38 ms  (+18.78%) | 
- │ │ │ │   └ sirius::divergence                                        |       19.84 ms →       19.89 ms   (+0.24%) |      38   →      45    (+18.42%) |      753.86 ms →      894.83 ms  (+18.70%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.45 ms →        2.44 ms   (-0.39%) |      38   →      45    (+18.42%) |       92.98 ms →      109.68 ms  (+17.96%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.34 ms →        3.40 ms   (+1.65%) |      38   →      45    (+18.42%) |      127.06 ms →      152.95 ms  (+20.37%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.92 ms →       20.95 ms   (+0.14%) |      38   →      45    (+18.42%) |      794.85 ms →      942.57 ms  (+18.58%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      247.03 ns →      199.51 ns  (-19.23%) |      38   →      45    (+18.42%) |        9.39 μs →        8.98 μs   (-4.36%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      419.00 ns →      233.49 ns  (-44.27%) |      38   →      45    (+18.42%) |       15.92 μs →       10.51 μs  (-34.01%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms →        2.24 ms   (+0.50%) |      38   →      45    (+18.42%) |       84.78 ms →      100.90 ms  (+19.02%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.30 ms →        4.24 ms   (-1.42%) |     266   →     315    (+18.42%) |        1.14 s  →        1.34 s   (+16.74%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.08 ms →        4.09 ms   (+0.19%) |     266   →     315    (+18.42%) |        1.09 s  →        1.29 s   (+18.65%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        4.09 ms   (+0.19%) |     266   →     315    (+18.42%) |        1.09 s  →        1.29 s   (+18.65%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.16 ms →        4.04 ms   (-2.89%) |     114   →     135    (+18.42%) |      473.74 ms →      544.81 ms  (+15.00%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.89 ms →        3.89 ms   (-0.09%) |     114   →     135    (+18.42%) |      443.84 ms →      525.10 ms  (+18.31%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.08 ms →        4.02 ms   (-1.48%) |      38   →      45    (+18.42%) |      154.94 ms →      180.77 ms  (+16.67%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      100.76 μs →      101.39 μs   (+0.62%) |      38   →      45    (+18.42%) |        3.83 ms →        4.56 ms  (+19.16%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       97.67 μs →       98.00 μs   (+0.35%) |      38   →      45    (+18.42%) |        3.71 ms →        4.41 ms  (+18.83%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.49 ms →        5.30 ms   (-3.38%) |       2   →       2              |       10.98 ms →       10.60 ms   (-3.38%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.53 ms →        4.18 ms   (-7.83%) |       6   →       6              |       27.18 ms →       25.05 ms   (-7.83%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.05 ms →        4.14 ms   (+2.27%) |       6   →       6              |       24.29 ms →       24.84 ms   (+2.27%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.05 ms →        4.14 ms   (+2.27%) |       6   →       6              |       24.29 ms →       24.84 ms   (+2.27%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.36 ms →        4.00 ms   (-8.20%) |       3   →       3              |       13.07 ms →       12.00 ms   (-8.20%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.85 ms →        3.97 ms   (+2.93%) |       3   →       3              |       11.56 ms →       11.90 ms   (+2.93%) | 
+ ├ sirius::Periodic_function|inner                                     |        4.73 ms →        4.09 ms  (-13.44%) |       2   →       2              |        9.46 ms →        8.19 ms  (-13.44%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.07 ms →        4.03 ms   (-0.85%) |       2   →       2              |        8.13 ms →        8.06 ms   (-0.85%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.07 ms →        4.03 ms   (-0.85%) |       2   →       2              |        8.13 ms →        8.06 ms   (-0.85%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.35 ms →        3.93 ms   (-9.46%) |       1   →       1              |        4.35 ms →        3.93 ms   (-9.46%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.86 ms →        3.88 ms   (+0.38%) |       1   →       1              |        3.86 ms →        3.88 ms   (+0.38%) | 
- └ sirius::finalize                                                    |      449.87 ms →      499.13 ms  (+10.95%) |       1   →       1              |      449.87 ms →      499.13 ms  (+10.95%) | 
  ====================================================================================================================================================================================================
```
