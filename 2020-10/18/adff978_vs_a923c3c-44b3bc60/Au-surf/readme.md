# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      144.65 s  →      122.56 s   (-15.27%) |       1   →       1              |      144.65 s  →      122.56 s   (-15.27%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.68 s    (-2.50%) |       1   →       1              |        2.75 s  →        2.68 s    (-2.50%) | 
  ├ sirius::Simulation_context::initialize                              |        2.07 s  →        2.07 s    (-0.01%) |       1   →       1              |        2.07 s  →        2.07 s    (-0.01%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       26.73 ms →       74.30 ms (+177.98%) |       1   →       1              |       26.73 ms →       74.30 ms (+177.98%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      102.38 ms →       67.14 ms  (-34.42%) |       1   →       1              |      102.38 ms →       67.14 ms  (-34.42%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       76.12 ms →       42.09 ms  (-44.70%) |       1   →       1              |       76.12 ms →       42.09 ms  (-44.70%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.20 ms →       24.99 ms   (-4.63%) |       1   →       1              |       26.20 ms →       24.99 ms   (-4.63%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.43 ms →       10.13 ms   (-2.89%) |       1   →       1              |       10.43 ms →       10.13 ms   (-2.89%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.74 ms →       14.83 ms   (-5.79%) |       1   →       1              |       15.74 ms →       14.83 ms   (-5.79%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.33 ms →       14.41 ms   (-6.02%) |       1   →       1              |       15.33 ms →       14.41 ms   (-6.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       15.12 ms →       14.19 ms   (-6.10%) |       1   →       1              |       15.12 ms →       14.19 ms   (-6.10%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      204.91 μs →      204.20 μs   (-0.35%) |       1   →       1              |      204.91 μs →      204.20 μs   (-0.35%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.83 μs →        2.30 μs  (-18.75%) |       1   →       1              |        2.83 μs →        2.30 μs  (-18.75%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.87 s    (-0.77%) |       1   →       1              |        1.89 s  →        1.87 s    (-0.77%) | 
  │   ├ sirius::Unit_cell::update                                       |       13.11 ms →       13.00 ms   (-0.81%) |       1   →       1              |       13.11 ms →       13.00 ms   (-0.81%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.42 ms →        8.45 ms   (+0.38%) |       1   →       1              |        8.42 ms →        8.45 ms   (+0.38%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.67 ms →        4.53 ms   (-2.97%) |       1   →       1              |        4.67 ms →        4.53 ms   (-2.97%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.29 ms →        4.14 ms   (-3.52%) |       1   →       1              |        4.29 ms →        4.14 ms   (-3.52%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.07 ms →        3.94 ms   (-3.38%) |       1   →       1              |        4.07 ms →        3.94 ms   (-3.38%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      215.18 μs →      202.06 μs   (-6.10%) |       1   →       1              |      215.18 μs →      202.06 μs   (-6.10%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.17 μs →        1.15 μs   (-1.79%) |       1   →       1              |        1.17 μs →        1.15 μs   (-1.79%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.15 ms →       15.00 ms   (-1.02%) |       2   →       2              |       30.30 ms →       29.99 ms   (-1.02%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (+0.27%) |       2   →       2              |        2.19 ms →        2.20 ms   (+0.27%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      983.64 μs →      959.45 μs   (-2.46%) |       1   →       1              |      983.64 μs →      959.45 μs   (-2.46%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.07 ms →        5.06 ms   (-0.24%) |       2   →       2              |       10.15 ms →       10.12 ms   (-0.24%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.65 ms   (+0.02%) |       2   →       2              |        7.29 ms →        7.29 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.75 ms →       15.77 ms   (+0.14%) |       4   →       4              |       62.99 ms →       63.08 ms   (+0.14%) | 
  │   ├ sddk::Gvec::init                                                |      159.42 ms →      157.76 ms   (-1.04%) |       2   →       2              |      318.83 ms →      315.51 ms   (-1.04%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      126.11 ms →      124.63 ms   (-1.17%) |       2   →       2              |      252.22 ms →      249.27 ms   (-1.17%) | 
  │   ├ sddk::Gvec_shells                                               |      121.82 ms →      124.20 ms   (+1.95%) |       1   →       1              |      121.82 ms →      124.20 ms   (+1.95%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.05 ms →        1.03 ms   (-1.21%) |       1   →       1              |        1.05 ms →        1.03 ms   (-1.21%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      217.41 ms →      218.24 ms   (+0.38%) |       1   →       1              |      217.41 ms →      218.24 ms   (+0.38%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.06 ms →       25.64 ms   (-1.60%) |       1   →       1              |       26.06 ms →       25.64 ms   (-1.60%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.85 μs →        1.65 μs  (-10.68%) |       2   →       2              |        3.70 μs →        3.30 μs  (-10.68%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.02 ms →       25.61 ms   (-1.60%) |       1   →       1              |       26.02 ms →       25.61 ms   (-1.60%) | 
  │   └ sirius::K_point::initialize                                     |       25.96 ms →       25.55 ms   (-1.59%) |       1   →       1              |       25.96 ms →       25.55 ms   (-1.59%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.46 ms →       19.16 ms   (-1.54%) |       1   →       1              |       19.46 ms →       19.16 ms   (-1.54%) | 
  │     │ └ sddk::Gvec::init                                            |        4.95 ms →        4.91 ms   (-0.82%) |       1   →       1              |        4.95 ms →        4.91 ms   (-0.82%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.09 μs →       11.33 μs   (+2.20%) |       1   →       1              |       11.09 μs →       11.33 μs   (+2.20%) | 
  │     └ sirius::K_point::update                                       |        4.12 ms →        4.12 ms   (+0.10%) |       1   →       1              |        4.12 ms →        4.12 ms   (+0.10%) | 
  │       └ sirius::Beta_projectors                                     |        1.73 ms →        1.71 ms   (-1.12%) |       1   →       1              |        1.73 ms →        1.71 ms   (-1.12%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      912.92 μs →      906.03 μs   (-0.75%) |       1   →       1              |      912.92 μs →      906.03 μs   (-0.75%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.45 ms →        1.44 ms   (-0.59%) |       2   →       2              |        2.89 ms →        2.87 ms   (-0.59%) | 
  ├ sirius::Potential                                                   |       96.75 ms →       94.77 ms   (-2.05%) |       1   →       1              |       96.75 ms →       94.77 ms   (-2.05%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.42 ms   (-1.00%) |       6   →       6              |       14.69 ms →       14.54 ms   (-1.00%) | 
  │ └ sirius::Potential::update                                         |       81.72 ms →       79.88 ms   (-2.25%) |       1   →       1              |       81.72 ms →       79.88 ms   (-2.25%) | 
  │   └ sirius::Potential::generate_local_potential                     |       81.55 ms →       79.71 ms   (-2.25%) |       1   →       1              |       81.55 ms →       79.71 ms   (-2.25%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.82 ms →       50.05 ms   (-5.26%) |       1   →       1              |       52.82 ms →       50.05 ms   (-5.26%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       19.97 ms →       20.96 ms   (+4.95%) |       1   →       1              |       19.97 ms →       20.96 ms   (+4.95%) | 
  ├ sirius::Density                                                     |       75.46 ms →       74.98 ms   (-0.64%) |       1   →       1              |       75.46 ms →       74.98 ms   (-0.64%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.83 ms →        4.80 ms   (-0.53%) |       2   →       2              |        9.66 ms →        9.61 ms   (-0.53%) | 
  │ └ sirius::Density::update                                           |       65.69 ms →       65.26 ms   (-0.65%) |       1   →       1              |       65.69 ms →       65.26 ms   (-0.65%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.52 ms →       65.10 ms   (-0.64%) |       1   →       1              |       65.52 ms →       65.10 ms   (-0.64%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.13 ms →        3.08 ms   (-1.50%) |       1   →       1              |        3.13 ms →        3.08 ms   (-1.50%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.16 ms →       51.83 ms   (-2.50%) |       1   →       1              |       53.16 ms →       51.83 ms   (-2.50%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        7.98 ms →        8.85 ms  (+10.83%) |       1   →       1              |        7.98 ms →        8.85 ms  (+10.83%) | 
  ├ sirius::Density::initial_density                                    |       79.20 ms →       78.51 ms   (-0.87%) |       1   →       1              |       79.20 ms →       78.51 ms   (-0.87%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.03 ms →       51.67 ms   (-2.56%) |       1   →       1              |       53.03 ms →       51.67 ms   (-2.56%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.24 ms →        5.58 ms   (+6.52%) |       2   →       2              |       10.48 ms →       11.16 ms   (+6.52%) | 
  │ └ sirius::Periodic_function::integrate                              |        3.95 ms →        3.91 ms   (-1.02%) |       1   →       1              |        3.95 ms →        3.91 ms   (-1.02%) | 
  ├ sirius::Potential::generate                                         |      188.55 ms →      186.74 ms   (-0.96%) |       1   →       1              |      188.55 ms →      186.74 ms   (-0.96%) | 
  │ ├ sirius::Potential::poisson                                        |       64.42 ms →       63.76 ms   (-1.02%) |       1   →       1              |       64.42 ms →       63.76 ms   (-1.02%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.32 ms →        9.53 ms  (+14.47%) |       1   →       1              |        8.32 ms →        9.53 ms  (+14.47%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.43 ms →        4.15 ms   (-6.24%) |       1   →       1              |        4.43 ms →        4.15 ms   (-6.24%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.08 ms →        4.14 ms   (+1.33%) |       1   →       1              |        4.08 ms →        4.14 ms   (+1.33%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        4.14 ms   (+1.33%) |       1   →       1              |        4.08 ms →        4.14 ms   (+1.33%) | 
  │ ├ sirius::Periodic_function::add                                    |      251.08 μs →      242.18 μs   (-3.54%) |       2   →       2              |      502.15 μs →      484.36 μs   (-3.54%) | 
  │ ├ sirius::Potential::xc                                             |       96.62 ms →       96.49 ms   (-0.13%) |       1   →       1              |       96.62 ms →       96.49 ms   (-0.13%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       95.57 ms →       95.46 ms   (-0.11%) |       1   →       1              |       95.57 ms →       95.46 ms   (-0.11%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.99 ms →        2.04 ms   (+2.07%) |       5   →       5              |        9.97 ms →       10.18 ms   (+2.07%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.53 ms →        2.47 ms   (-2.07%) |       9   →       9              |       22.74 ms →       22.27 ms   (-2.07%) | 
  │ │   ├ sirius::gradient                                              |        7.54 ms →        7.53 ms   (-0.04%) |       1   →       1              |        7.54 ms →        7.53 ms   (-0.04%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.41 ms →        2.41 ms   (-0.03%) |       3   →       3              |        7.23 ms →        7.23 ms   (-0.03%) | 
  │ │   ├ sirius::dot                                                   |        2.82 ms →        2.87 ms   (+1.82%) |       1   →       1              |        2.82 ms →        2.87 ms   (+1.82%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.59 ms →        2.66 ms   (+2.84%) |       1   →       1              |        2.59 ms →        2.66 ms   (+2.84%) | 
  │ │   └ sirius::divergence                                            |       19.79 ms →       19.87 ms   (+0.40%) |       1   →       1              |       19.79 ms →       19.87 ms   (+0.40%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.43 ms   (+0.52%) |       1   →       1              |        2.42 ms →        2.43 ms   (+0.52%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.25 ms →        3.23 ms  (-24.11%) |       1   →       1              |        4.25 ms →        3.23 ms  (-24.11%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.20 ms →       22.23 ms   (+0.13%) |       1   →       1              |       22.20 ms →       22.23 ms   (+0.13%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      265.00 ns →      139.00 ns  (-47.55%) |       1   →       1              |      265.00 ns →      139.00 ns  (-47.55%) | 
  ├ sirius::Hamiltonian0                                                |       13.89 ms →       13.74 ms   (-1.08%) |       1   →       1              |       13.89 ms →       13.74 ms   (-1.08%) | 
  │ ├ sirius::Local_operator                                            |       13.56 ms →       13.42 ms   (-1.01%) |       1   →       1              |       13.56 ms →       13.42 ms   (-1.01%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.18 ms →        7.11 ms   (-0.88%) |       1   →       1              |        7.18 ms →        7.11 ms   (-0.88%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.92 ms →        4.88 ms   (-0.92%) |       1   →       1              |        4.92 ms →        4.88 ms   (-0.92%) | 
  │ ├ sirius::Non_local_operator                                        |       59.67 μs →       59.59 μs   (-0.14%) |       2   →       2              |      119.33 μs →      119.17 μs   (-0.14%) | 
  │ ├ sirius::D_operator::initialize                                    |       80.05 μs →       77.57 μs   (-3.09%) |       1   →       1              |       80.05 μs →       77.57 μs   (-3.09%) | 
+ │ └ sirius::Q_operator::initialize                                    |       78.02 μs →       68.19 μs  (-12.60%) |       1   →       1              |       78.02 μs →       68.19 μs  (-12.60%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.47 s  →        2.45 s    (-0.46%) |       1   →       1              |        2.47 s  →        2.45 s    (-0.46%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.39 ms   (-0.24%) |       1   →       1              |        8.41 ms →        8.39 ms   (-0.24%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      242.51 μs →      236.78 μs   (-2.37%) |       1   →       1              |      242.51 μs →      236.78 μs   (-2.37%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.17 ms →        8.16 ms   (-0.16%) |       1   →       1              |        8.17 ms →        8.16 ms   (-0.16%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.46 s  →        2.45 s    (-0.46%) |       1   →       1              |        2.46 s  →        2.45 s    (-0.46%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.80 ms →       87.90 ms   (+1.27%) |       4   →       4              |      347.18 ms →      351.59 ms   (+1.27%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.89 ms →       25.47 ms   (-1.61%) |       1   →       1              |       25.89 ms →       25.47 ms   (-1.61%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.74 ms →       14.70 ms   (-0.30%) |       1   →       1              |       14.74 ms →       14.70 ms   (-0.30%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.20 s    (-0.94%) |       1   →       1              |        1.21 s  →        1.20 s    (-0.94%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      988.01 ms →      978.60 ms   (-0.95%) |       1   →       1              |      988.01 ms →      978.60 ms   (-0.95%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      314.95 ms →      310.06 ms   (-1.55%) |       1   →       1              |      314.95 ms →      310.06 ms   (-1.55%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      174.76 ms →      177.20 ms   (+1.39%) |       1   →       1              |      174.76 ms →      177.20 ms   (+1.39%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      174.76 ms →      177.19 ms   (+1.39%) |       1   →       1              |      174.76 ms →      177.19 ms   (+1.39%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      121.75 ms →      114.44 ms   (-6.00%) |       1   →       1              |      121.75 ms →      114.44 ms   (-6.00%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      173.08 ms →      174.14 ms   (+0.61%) |       1   →       1              |      173.08 ms →      174.14 ms   (+0.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      173.08 ms →      174.13 ms   (+0.61%) |       1   →       1              |      173.08 ms →      174.13 ms   (+0.61%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      169.41 ms →      163.55 ms   (-3.45%) |       1   →       1              |      169.41 ms →      163.55 ms   (-3.45%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      118.86 ms →      113.11 ms   (-4.83%) |       1   →       1              |      118.86 ms →      113.11 ms   (-4.83%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.71 ms →        3.73 ms   (+0.59%) |       1   →       1              |        3.71 ms →        3.73 ms   (+0.59%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       91.57 ms →       89.53 ms   (-2.22%) |       1   →       1              |       91.57 ms →       89.53 ms   (-2.22%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       13.80 ms →       12.09 ms  (-12.37%) |       1   →       1              |       13.80 ms →       12.09 ms  (-12.37%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.19 ms →       64.23 ms   (+0.06%) |       2   →       2              |      128.38 ms →      128.45 ms   (+0.06%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      193.87 ms →      194.93 ms   (+0.55%) |       2   →       2              |      387.75 ms →      389.86 ms   (+0.55%) | 
  │ │ │ └ sddk::wf_inner                                                |      193.77 ms →      194.83 ms   (+0.55%) |       2   →       2              |      387.55 ms →      389.66 ms   (+0.55%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       33.50 ns →       34.00 ns   (+1.49%) |       2   →       2              |       67.00 ns →       68.00 ns   (+1.49%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      191.48 ms →      193.15 ms   (+0.87%) |       2   →       2              |      382.96 ms →      386.30 ms   (+0.87%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       23.00 ns →       33.00 ns  (+43.48%) |       2   →       2              |       46.00 ns →       66.00 ns  (+43.48%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.16 ms →      114.98 ms   (-1.02%) |       1   →       1              |      116.16 ms →      114.98 ms   (-1.02%) | 
  │ │ └ sddk::wf_trans                                                  |       38.61 ms →       38.54 ms   (-0.16%) |       1   →       1              |       38.61 ms →       38.54 ms   (-0.16%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.64 ms →       35.65 ms   (+0.04%) |       1   →       1              |       35.64 ms →       35.65 ms   (+0.04%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      563.00 ns →      433.00 ns  (-23.09%) |       1   →       1              |      563.00 ns →      433.00 ns  (-23.09%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      135.78 s  →      113.75 s   (-16.22%) |       1   →       1              |      135.78 s  →      113.75 s   (-16.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms →        2.13 ms   (-1.99%) |      31   →      31              |       67.41 ms →       66.07 ms   (-1.99%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.88 s  →        2.91 s    (+0.94%) |      47   →      39    (-17.02%) |      135.55 s  →      113.54 s   (-16.24%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        7.19 ms →        7.10 ms   (-1.25%) |      47   →      39    (-17.02%) |      337.90 ms →      276.89 ms  (-18.06%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        6.86 ms →        6.77 ms   (-1.32%) |      47   →      39    (-17.02%) |      322.35 ms →      263.96 ms  (-18.11%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.45 ms →        1.49 ms   (+2.87%) |      47   →      39    (-17.02%) |       68.13 ms →       58.16 ms  (-14.64%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.96 ms →        3.83 ms   (-3.35%) |      47   →      39    (-17.02%) |      186.29 ms →      149.40 ms  (-19.80%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       60.97 μs →       60.71 μs   (-0.43%) |      94   →      78    (-17.02%) |        5.73 ms →        4.74 ms  (-17.38%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       81.49 μs →       81.50 μs   (+0.01%) |      47   →      39    (-17.02%) |        3.83 ms →        3.18 ms  (-17.01%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       68.12 μs →       68.02 μs   (-0.15%) |      47   →      39    (-17.02%) |        3.20 ms →        2.65 ms  (-17.14%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.21 s  →        2.25 s    (+1.82%) |      47   →      39    (-17.02%) |      104.00 s  →       87.87 s   (-15.51%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      204.69 μs →      206.67 μs   (+0.97%) |      47   →      39    (-17.02%) |        9.62 ms →        8.06 ms  (-16.22%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.49 μs →      199.88 μs   (+1.21%) |      47   →      39    (-17.02%) |        9.28 ms →        7.80 ms  (-16.02%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.04 μs →        4.99 μs   (-0.99%) |      47   →      39    (-17.02%) |      236.70 μs →      194.47 μs  (-17.84%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.20 s  →        2.24 s    (+1.93%) |      47   →      39    (-17.02%) |      103.17 s  →       87.25 s   (-15.42%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       55.00 ms →       58.80 ms   (+6.91%) |      47   →      39    (-17.02%) |        2.58 s  →        2.29 s   (-11.29%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        3.80 ms →        4.50 ms  (+18.56%) |     282   →     234    (-17.02%) |        1.07 s  →        1.05 s    (-1.62%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.61 ms →        1.64 ms   (+1.96%) |      47   →      39    (-17.02%) |       75.79 ms →       64.12 ms  (-15.40%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      418.72 μs →      419.16 μs   (+0.10%) |      47   →      39    (-17.02%) |       19.68 ms →       16.35 ms  (-16.93%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      937.62 μs →      964.47 μs   (+2.86%) |      47   →      39    (-17.02%) |       44.07 ms →       37.61 ms  (-14.65%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.11 s  →        2.15 s    (+1.82%) |      47   →      39    (-17.02%) |       99.37 s  →       83.96 s   (-15.51%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      202.60 ms →      186.30 ms   (-8.05%) |     261   →     252     (-3.45%) |       52.88 s  →       46.95 s   (-11.22%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      143.52 ms →      130.82 ms   (-8.85%) |     261   →     252     (-3.45%) |       37.46 s  →       32.97 s   (-12.00%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       26.42 ms →       23.49 ms  (-11.10%) |     261   →     252     (-3.45%) |        6.89 s  →        5.92 s   (-14.16%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      571.65 μs →      569.63 μs   (-0.35%) |     261   →     252     (-3.45%) |      149.20 ms →      143.55 ms   (-3.79%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.16 ms →        3.67 ms  (+15.93%) |      47   →      39    (-17.02%) |      148.62 ms →      142.98 ms   (-3.80%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.62 ms →       19.01 ms  (-12.07%) |     261   →     252     (-3.45%) |        5.64 s  →        4.79 s   (-15.10%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      540.25 μs →      566.31 μs   (+4.82%) |     261   →     252     (-3.45%) |      141.00 ms →      142.71 ms   (+1.21%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        2.98 ms →        3.64 ms  (+22.05%) |      47   →      39    (-17.02%) |      140.22 ms →      142.01 ms   (+1.28%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.18 ms →       28.86 ms  (-13.01%) |     261   →     252     (-3.45%) |        8.66 s  →        7.27 s   (-16.01%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.24 ms →       17.72 ms  (-16.56%) |     261   →     252     (-3.45%) |        5.54 s  →        4.47 s   (-19.43%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.59 ms →        2.60 ms   (+0.25%) |     261   →     252     (-3.45%) |      677.24 ms →      655.52 ms   (-3.21%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       21.46 ms →       19.73 ms   (-8.03%) |     261   →     252     (-3.45%) |        5.60 s  →        4.97 s   (-11.20%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.62 ms →        2.09 ms  (-20.20%) |     261   →     252     (-3.45%) |      682.79 ms →      526.07 ms  (-22.95%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       17.50 ms →       16.56 ms   (-5.37%) |     522   →     504     (-3.45%) |        9.14 s  →        8.35 s    (-8.64%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       55.63 ms →       52.40 ms   (-5.82%) |     261   →     252     (-3.45%) |       14.52 s  →       13.20 s    (-9.07%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |       12.99 ms →       11.93 ms   (-8.21%) |     475   →     465     (-2.11%) |        6.17 s  →        5.55 s   (-10.14%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       84.29 ns →       79.00 ns   (-6.28%) |     475   →     465     (-2.11%) |       40.04 μs →       36.73 μs   (-8.25%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.29 ms →        8.43 ms   (-9.20%) |     475   →     465     (-2.11%) |        4.41 s  →        3.92 s   (-11.11%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       86.46 ns →       65.18 ns  (-24.61%) |     475   →     465     (-2.11%) |       41.07 μs →       30.31 μs  (-26.19%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        2.94 ms →        2.72 ms   (-7.63%) |     261   →     252     (-3.45%) |      767.77 ms →      684.74 ms  (-10.81%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       14.75 ms →       13.64 ms   (-7.54%) |     261   →     252     (-3.45%) |        3.85 s  →        3.44 s   (-10.73%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       17.43 ms →       16.60 ms   (-4.76%) |     214   →     213     (-0.47%) |        3.73 s  →        3.54 s    (-5.21%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.78 ms →        5.51 ms   (-4.61%) |     642   →     639     (-0.47%) |        3.71 s  →        3.52 s    (-5.06%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       20.35 ms →       18.51 ms   (-9.05%) |     261   →     252     (-3.45%) |        5.31 s  →        4.67 s   (-12.18%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |       19.10 ms →       17.51 ms   (-8.31%) |     261   →     252     (-3.45%) |        4.99 s  →        4.41 s   (-11.47%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       42.43 ns →       77.41 ns  (+82.44%) |     261   →     252     (-3.45%) |       11.07 μs →       19.51 μs  (+76.15%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       15.54 ms →       14.05 ms   (-9.57%) |     261   →     252     (-3.45%) |        4.06 s  →        3.54 s   (-12.69%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       49.92 ns →       89.23 ns  (+78.75%) |     261   →     252     (-3.45%) |       13.03 μs →       22.49 μs  (+72.58%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       67.86 ms →       42.25 ms  (-37.74%) |     261   →     252     (-3.45%) |       17.71 s  →       10.65 s   (-39.89%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       17.74 ms →       15.31 ms  (-13.71%) |     256   →     247     (-3.52%) |        4.54 s  →        3.78 s   (-16.74%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       18.47 ms →       15.63 ms  (-15.39%) |     219   →     214     (-2.28%) |        4.05 s  →        3.35 s   (-17.32%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.32 ms →        7.17 ms  (-13.87%) |     438   →     428     (-2.28%) |        3.64 s  →        3.07 s   (-15.84%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.53 ms →        1.38 ms  (-10.24%) |     219   →     214     (-2.28%) |      335.64 ms →      294.38 ms  (-12.29%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       66.56 ms →       51.65 ms  (-22.41%) |      66   →      91    (+37.88%) |        4.39 s  →        4.70 s    (+6.98%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       51.08 ms →       31.84 ms  (-37.66%) |      85   →     143    (+68.24%) |        4.34 s  →        4.55 s    (+4.88%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |       40.28 ms →       22.80 ms  (-43.39%) |     104   →     195    (+87.50%) |        4.19 s  →        4.45 s    (+6.14%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      757.70 ns →      778.13 ns   (+2.70%) |      47   →      39    (-17.02%) |       35.61 μs →       30.35 μs  (-14.78%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.24 μs →       33.68 μs  (+15.20%) |      47   →      39    (-17.02%) |        1.37 ms →        1.31 ms   (-4.41%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.43 ms →        3.45 ms   (+0.69%) |      47   →      39    (-17.02%) |      161.12 ms →      134.62 ms  (-16.45%) | 
+ │ │ ├ sirius::Density::generate                                       |      299.81 ms →      291.98 ms   (-2.61%) |      47   →      39    (-17.02%) |       14.09 s  →       11.39 s   (-19.19%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      295.74 ms →      288.01 ms   (-2.61%) |      47   →      39    (-17.02%) |       13.90 s  →       11.23 s   (-19.19%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.50 ms →       64.55 ms   (-7.12%) |      47   →      39    (-17.02%) |        3.27 s  →        2.52 s   (-22.93%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       56.70 μs →       68.16 μs  (+20.21%) |      47   →      39    (-17.02%) |        2.66 ms →        2.66 ms   (-0.25%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.16 ms →        1.18 ms   (+1.71%) |       2   →       2              |        2.32 ms →        2.36 ms   (+1.71%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       58.15 ms →       53.24 ms   (-8.44%) |      47   →      39    (-17.02%) |        2.73 s  →        2.08 s   (-24.03%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.20 ms →       60.13 ms   (-1.74%) |      47   →      39    (-17.02%) |        2.88 s  →        2.35 s   (-18.46%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.40 μs →        9.58 μs   (+1.88%) |      47   →      39    (-17.02%) |      442.01 μs →      373.66 μs  (-15.46%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.27 ms →        2.31 ms   (+1.40%) |      47   →      39    (-17.02%) |      106.92 ms →       89.96 ms  (-15.86%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.38 ms →       57.27 ms   (-1.90%) |      47   →      39    (-17.02%) |        2.74 s  →        2.23 s   (-18.59%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.93 ms →        5.81 ms  (-16.14%) |      47   →      39    (-17.02%) |      325.85 ms →      226.73 ms  (-30.42%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      606.98 ns →      535.05 ns  (-11.85%) |      47   →      39    (-17.02%) |       28.53 μs →       20.87 μs  (-26.85%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.24 ms →      104.07 ms   (-0.16%) |      47   →      39    (-17.02%) |        4.90 s  →        4.06 s   (-17.15%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.38 ms   (-0.66%) |      47   →      39    (-17.02%) |      112.76 ms →       92.95 ms  (-17.57%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.05 ms   (+0.03%) |      47   →      39    (-17.02%) |      942.29 ms →      782.13 ms  (-17.00%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.88 ms   (+0.01%) |      47   →      39    (-17.02%) |      934.48 ms →      775.51 ms  (-17.01%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      241.02 ns →      327.74 ns  (+35.98%) |      47   →      39    (-17.02%) |       11.33 μs →       12.78 μs  (+12.84%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.54%) |      47   →      39    (-17.02%) |       59.09 ms →       48.77 ms  (-17.47%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.81 ms →        2.72 ms   (-3.39%) |      47   →      39    (-17.02%) |      132.23 ms →      106.01 ms  (-19.83%) | 
+ │ │ ├ sirius::Density::mix                                            |      132.21 ms →      128.43 ms   (-2.86%) |      47   →      39    (-17.02%) |        6.21 s  →        5.01 s   (-19.39%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      258.90 μs →      258.65 μs   (-0.10%) |      47   →      39    (-17.02%) |       12.17 ms →       10.09 ms  (-17.10%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        2.95 ms →        2.99 ms   (+1.47%) |      47   →      39    (-17.02%) |      138.58 ms →      116.68 ms  (-15.81%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.75 ms →        2.80 ms   (+1.72%) |      47   →      39    (-17.02%) |      129.30 ms →      109.14 ms  (-15.59%) | 
+ │ │ ├ sirius::Potential::generate                                     |      180.65 ms →      179.93 ms   (-0.40%) |      47   →      39    (-17.02%) |        8.49 s  →        7.02 s   (-17.35%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       64.51 ms →       63.98 ms   (-0.82%) |      47   →      39    (-17.02%) |        3.03 s  →        2.50 s   (-17.70%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.52 ms →        9.53 ms  (+11.81%) |      47   →      39    (-17.02%) |      400.41 ms →      371.48 ms   (-7.22%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.17 ms →        4.22 ms   (+1.18%) |      47   →      39    (-17.02%) |      196.15 ms →      164.69 ms  (-16.04%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms →        4.09 ms   (+0.23%) |      47   →      39    (-17.02%) |      191.89 ms →      159.59 ms  (-16.83%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.08 ms →        4.09 ms   (+0.23%) |      47   →      39    (-17.02%) |      191.87 ms →      159.57 ms  (-16.83%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      235.91 μs →      232.51 μs   (-1.44%) |      94   →      78    (-17.02%) |       22.18 ms →       18.14 ms  (-18.22%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       90.76 ms →       90.66 ms   (-0.10%) |      47   →      39    (-17.02%) |        4.27 s  →        3.54 s   (-17.11%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       89.76 ms →       89.64 ms   (-0.13%) |      47   →      39    (-17.02%) |        4.22 s  →        3.50 s   (-17.13%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.58 ms →        1.59 ms   (+0.94%) |     235   →     195    (-17.02%) |      371.34 ms →      311.01 ms  (-16.24%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.49 ms →        2.47 ms   (-0.65%) |     423   →     351    (-17.02%) |        1.05 s  →      867.72 ms  (-17.56%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.39 ms →        2.44 ms   (+2.24%) |      47   →      39    (-17.02%) |      112.22 ms →       95.20 ms  (-15.16%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      701.58 μs →      719.18 μs   (+2.51%) |     141   →     117    (-17.02%) |       98.92 ms →       84.14 ms  (-14.94%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.82 ms   (+0.05%) |      47   →      39    (-17.02%) |      132.57 ms →      110.05 ms  (-16.98%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms →        2.59 ms   (+0.34%) |      47   →      39    (-17.02%) |      121.41 ms →      101.09 ms  (-16.74%) | 
+ │ │ │ │   └ sirius::divergence                                        |       19.94 ms →       19.78 ms   (-0.80%) |      47   →      39    (-17.02%) |      937.08 ms →      771.34 ms  (-17.69%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.43 ms →        2.44 ms   (+0.33%) |      47   →      39    (-17.02%) |      114.21 ms →       95.09 ms  (-16.74%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.33 ms →        3.35 ms   (+0.56%) |      47   →      39    (-17.02%) |      156.45 ms →      130.54 ms  (-16.56%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       21.03 ms →       20.93 ms   (-0.48%) |      47   →      39    (-17.02%) |      988.25 ms →      816.10 ms  (-17.42%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      314.09 ns →      549.69 ns  (+75.01%) |      47   →      39    (-17.02%) |       14.76 μs →       21.44 μs  (+45.22%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      242.30 ns →      508.05 ns (+109.68%) |      47   →      39    (-17.02%) |       11.39 μs →       19.81 μs  (+73.99%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.30 ms →        2.26 ms   (-1.70%) |      47   →      39    (-17.02%) |      107.89 ms →       88.00 ms  (-18.44%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.07 ms →        4.06 ms   (-0.40%) |     329   →     273    (-17.02%) |        1.34 s  →        1.11 s   (-17.36%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.99 ms →        3.93 ms   (-1.58%) |     329   →     273    (-17.02%) |        1.31 s  →        1.07 s   (-18.33%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.99 ms →        3.93 ms   (-1.58%) |     329   →     273    (-17.02%) |        1.31 s  →        1.07 s   (-18.33%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.36 ms →        4.15 ms   (-4.80%) |     141   →     117    (-17.02%) |      614.42 ms →      485.38 ms  (-21.00%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.26 ms →        4.05 ms   (-5.02%) |     141   →     117    (-17.02%) |      600.91 ms →      473.62 ms  (-21.18%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        3.99 ms →        3.96 ms   (-0.82%) |      47   →      39    (-17.02%) |      187.62 ms →      154.41 ms  (-17.70%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      114.30 μs →      101.56 μs  (-11.14%) |      47   →      39    (-17.02%) |        5.37 ms →        3.96 ms  (-26.27%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      111.06 μs →       98.11 μs  (-11.66%) |      47   →      39    (-17.02%) |        5.22 ms →        3.83 ms  (-26.70%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.26 ms →        5.40 ms   (+2.79%) |       2   →       2              |       10.52 ms →       10.81 ms   (+2.79%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.01 ms →        4.05 ms   (+0.91%) |       6   →       6              |       24.09 ms →       24.31 ms   (+0.91%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.97 ms →        3.94 ms   (-0.88%) |       6   →       6              |       23.85 ms →       23.64 ms   (-0.88%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.97 ms →        3.94 ms   (-0.88%) |       6   →       6              |       23.85 ms →       23.64 ms   (-0.88%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.29 ms →        4.07 ms   (-5.08%) |       3   →       3              |       12.88 ms →       12.22 ms   (-5.08%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.28 ms →        4.04 ms   (-5.44%) |       3   →       3              |       12.83 ms →       12.13 ms   (-5.44%) | 
  ├ sirius::Periodic_function|inner                                     |        4.17 ms →        4.07 ms   (-2.32%) |       2   →       2              |        8.33 ms →        8.14 ms   (-2.32%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.06 ms →        3.87 ms   (-4.68%) |       2   →       2              |        8.13 ms →        7.75 ms   (-4.68%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.06 ms →        3.87 ms   (-4.68%) |       2   →       2              |        8.13 ms →        7.75 ms   (-4.68%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.28 ms →        4.05 ms   (-5.29%) |       1   →       1              |        4.28 ms →        4.05 ms   (-5.29%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.27 ms →        4.04 ms   (-5.30%) |       1   →       1              |        4.27 ms →        4.04 ms   (-5.30%) | 
  └ sirius::finalize                                                    |      308.31 ms →      310.95 ms   (+0.86%) |       1   →       1              |      308.31 ms →      310.95 ms   (+0.86%) | 
  ====================================================================================================================================================================================================
```
