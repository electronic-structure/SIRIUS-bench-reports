# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      144.26 s  →      122.97 s   (-14.76%) |       1   →       1              |      144.26 s  →      122.97 s   (-14.76%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.74 s    (+0.62%) |       1   →       1              |        2.72 s  →        2.74 s    (+0.62%) | 
  ├ sirius::Simulation_context::initialize                              |        2.12 s  →        2.12 s    (-0.40%) |       1   →       1              |        2.12 s  →        2.12 s    (-0.40%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       53.30 ms →       49.44 ms   (-7.24%) |       1   →       1              |       53.30 ms →       49.44 ms   (-7.24%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      111.55 ms →      102.87 ms   (-7.78%) |       1   →       1              |      111.55 ms →      102.87 ms   (-7.78%) | 
  │ │ ├ sirius::Atom_type::init                                         |       84.53 ms →       76.27 ms   (-9.77%) |       1   →       1              |       84.53 ms →       76.27 ms   (-9.77%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.95 ms →       26.53 ms   (-1.55%) |       1   →       1              |       26.95 ms →       26.53 ms   (-1.55%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.06 ms →       10.21 ms   (+1.58%) |       1   →       1              |       10.06 ms →       10.21 ms   (+1.58%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.87 ms →       16.29 ms   (-3.43%) |       1   →       1              |       16.87 ms →       16.29 ms   (-3.43%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.24 ms →       15.68 ms   (-3.44%) |       1   →       1              |       16.24 ms →       15.68 ms   (-3.44%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       16.03 ms →       15.45 ms   (-3.63%) |       1   →       1              |       16.03 ms →       15.45 ms   (-3.63%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      196.60 μs →      218.74 μs  (+11.26%) |       1   →       1              |      196.60 μs →      218.74 μs  (+11.26%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.21 μs →        2.45 μs  (+10.80%) |       1   →       1              |        2.21 μs →        2.45 μs  (+10.80%) | 
  │ └ sirius::Simulation_context::update                                |        1.91 s  →        1.92 s    (+0.39%) |       1   →       1              |        1.91 s  →        1.92 s    (+0.39%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.63 ms →       12.94 ms   (+2.46%) |       1   →       1              |       12.63 ms →       12.94 ms   (+2.46%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.91 ms →        8.32 ms   (+5.09%) |       1   →       1              |        7.91 ms →        8.32 ms   (+5.09%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.70 ms →        4.61 ms   (-1.95%) |       1   →       1              |        4.70 ms →        4.61 ms   (-1.95%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.26 ms →        4.16 ms   (-2.43%) |       1   →       1              |        4.26 ms →        4.16 ms   (-2.43%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.04 ms →        3.94 ms   (-2.54%) |       1   →       1              |        4.04 ms →        3.94 ms   (-2.54%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      214.93 μs →      214.41 μs   (-0.24%) |       1   →       1              |      214.93 μs →      214.41 μs   (-0.24%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.14 μs →        1.28 μs  (+12.26%) |       1   →       1              |        1.14 μs →        1.28 μs  (+12.26%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       16.90 ms →       20.50 ms  (+21.32%) |       2   →       2              |       33.80 ms →       41.00 ms  (+21.32%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.11 ms   (+1.63%) |       2   →       2              |        2.19 ms →        2.22 ms   (+1.63%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      962.00 μs →      953.24 μs   (-0.91%) |       1   →       1              |      962.00 μs →      953.24 μs   (-0.91%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.09 ms →        5.06 ms   (-0.52%) |       2   →       2              |       10.18 ms →       10.13 ms   (-0.52%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.67 ms →        3.65 ms   (-0.58%) |       2   →       2              |        7.34 ms →        7.30 ms   (-0.58%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.87 ms →       15.84 ms   (-0.15%) |       4   →       4              |       63.47 ms →       63.37 ms   (-0.15%) | 
  │   ├ sddk::Gvec::init                                                |      156.66 ms →      158.43 ms   (+1.13%) |       2   →       2              |      313.32 ms →      316.86 ms   (+1.13%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      123.57 ms →      125.40 ms   (+1.47%) |       2   →       2              |      247.15 ms →      250.79 ms   (+1.47%) | 
  │   ├ sddk::Gvec_shells                                               |      124.08 ms →      120.39 ms   (-2.97%) |       1   →       1              |      124.08 ms →      120.39 ms   (-2.97%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.02 ms   (-0.24%) |       1   →       1              |        1.03 ms →        1.02 ms   (-0.24%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      221.55 ms →      220.09 ms   (-0.65%) |       1   →       1              |      221.55 ms →      220.09 ms   (-0.65%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.26 ms →       25.64 ms   (-2.37%) |       1   →       1              |       26.26 ms →       25.64 ms   (-2.37%) | 
  │ ├ sirius::K_point::K_point                                          |        1.71 μs →        1.60 μs   (-6.55%) |       2   →       2              |        3.42 μs →        3.19 μs   (-6.55%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.23 ms →       25.60 ms   (-2.38%) |       1   →       1              |       26.23 ms →       25.60 ms   (-2.38%) | 
  │   └ sirius::K_point::initialize                                     |       26.17 ms →       25.55 ms   (-2.35%) |       1   →       1              |       26.17 ms →       25.55 ms   (-2.35%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.44 ms →       19.16 ms   (-1.45%) |       1   →       1              |       19.44 ms →       19.16 ms   (-1.45%) | 
  │     │ └ sddk::Gvec::init                                            |        5.02 ms →        4.93 ms   (-1.79%) |       1   →       1              |        5.02 ms →        4.93 ms   (-1.79%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        9.23 μs →        7.88 μs  (-14.61%) |       1   →       1              |        9.23 μs →        7.88 μs  (-14.61%) | 
  │     └ sirius::K_point::update                                       |        4.28 ms →        4.06 ms   (-5.30%) |       1   →       1              |        4.28 ms →        4.06 ms   (-5.30%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.70 ms   (-1.21%) |       1   →       1              |        1.72 ms →        1.70 ms   (-1.21%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      895.62 μs →      881.72 μs   (-1.55%) |       1   →       1              |      895.62 μs →      881.72 μs   (-1.55%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.48 ms →        1.45 ms   (-1.97%) |       2   →       2              |        2.96 ms →        2.90 ms   (-1.97%) | 
  ├ sirius::Potential                                                   |       96.89 ms →       94.61 ms   (-2.35%) |       1   →       1              |       96.89 ms →       94.61 ms   (-2.35%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.45 ms   (-0.73%) |       6   →       6              |       14.82 ms →       14.71 ms   (-0.73%) | 
  │ └ sirius::Potential::update                                         |       81.71 ms →       79.57 ms   (-2.61%) |       1   →       1              |       81.71 ms →       79.57 ms   (-2.61%) | 
  │   └ sirius::Potential::generate_local_potential                     |       81.53 ms →       79.41 ms   (-2.60%) |       1   →       1              |       81.53 ms →       79.41 ms   (-2.60%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       57.88 ms →       57.16 ms   (-1.26%) |       1   →       1              |       57.88 ms →       57.16 ms   (-1.26%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.90 ms →       13.45 ms   (-9.74%) |       1   →       1              |       14.90 ms →       13.45 ms   (-9.74%) | 
  ├ sirius::Density                                                     |       75.52 ms →       74.76 ms   (-1.00%) |       1   →       1              |       75.52 ms →       74.76 ms   (-1.00%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.81 ms →        4.81 ms   (-0.10%) |       2   →       2              |        9.63 ms →        9.62 ms   (-0.10%) | 
  │ └ sirius::Density::update                                           |       65.78 ms →       65.04 ms   (-1.12%) |       1   →       1              |       65.78 ms →       65.04 ms   (-1.12%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.58 ms →       64.85 ms   (-1.11%) |       1   →       1              |       65.58 ms →       64.85 ms   (-1.11%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.09 ms →        3.12 ms   (+1.02%) |       1   →       1              |        3.09 ms →        3.12 ms   (+1.02%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       57.92 ms →       58.07 ms   (+0.25%) |       1   →       1              |       57.92 ms →       58.07 ms   (+0.25%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        3.30 ms →        2.40 ms  (-27.10%) |       1   →       1              |        3.30 ms →        2.40 ms  (-27.10%) | 
  ├ sirius::Density::initial_density                                    |       80.61 ms →       80.41 ms   (-0.25%) |       1   →       1              |       80.61 ms →       80.41 ms   (-0.25%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       58.00 ms →       58.51 ms   (+0.87%) |       1   →       1              |       58.00 ms →       58.51 ms   (+0.87%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.91 ms →        2.61 ms  (-10.47%) |       2   →       2              |        5.82 ms →        5.21 ms  (-10.47%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.90 ms →        4.87 ms   (-0.60%) |       1   →       1              |        4.90 ms →        4.87 ms   (-0.60%) | 
  ├ sirius::Potential::generate                                         |      188.65 ms →      185.23 ms   (-1.82%) |       1   →       1              |      188.65 ms →      185.23 ms   (-1.82%) | 
  │ ├ sirius::Potential::poisson                                        |       64.68 ms →       63.32 ms   (-2.10%) |       1   →       1              |       64.68 ms →       63.32 ms   (-2.10%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.13 ms →        2.34 ms  (-25.40%) |       1   →       1              |        3.13 ms →        2.34 ms  (-25.40%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.31 ms →        4.15 ms   (-3.86%) |       1   →       1              |        4.31 ms →        4.15 ms   (-3.86%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.22 ms →        4.08 ms   (-3.18%) |       1   →       1              |        4.22 ms →        4.08 ms   (-3.18%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.22 ms →        4.08 ms   (-3.18%) |       1   →       1              |        4.22 ms →        4.08 ms   (-3.18%) | 
  │ ├ sirius::Periodic_function::add                                    |      234.78 μs →      239.67 μs   (+2.08%) |       2   →       2              |      469.56 μs →      479.35 μs   (+2.08%) | 
  │ ├ sirius::Potential::xc                                             |       97.41 ms →       95.54 ms   (-1.93%) |       1   →       1              |       97.41 ms →       95.54 ms   (-1.93%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       96.32 ms →       94.52 ms   (-1.87%) |       1   →       1              |       96.32 ms →       94.52 ms   (-1.87%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.02 ms →        1.97 ms   (-2.47%) |       5   →       5              |       10.11 ms →        9.86 ms   (-2.47%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.54 ms →        2.45 ms   (-3.72%) |       9   →       9              |       22.87 ms →       22.02 ms   (-3.72%) | 
  │ │   ├ sirius::gradient                                              |        7.72 ms →        7.47 ms   (-3.21%) |       1   →       1              |        7.72 ms →        7.47 ms   (-3.21%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.48 ms →        2.40 ms   (-3.24%) |       3   →       3              |        7.43 ms →        7.19 ms   (-3.24%) | 
  │ │   ├ sirius::dot                                                   |        2.94 ms →        2.80 ms   (-4.99%) |       1   →       1              |        2.94 ms →        2.80 ms   (-4.99%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.70 ms →        2.56 ms   (-5.36%) |       1   →       1              |        2.70 ms →        2.56 ms   (-5.36%) | 
  │ │   └ sirius::divergence                                            |       19.84 ms →       19.64 ms   (-0.98%) |       1   →       1              |       19.84 ms →       19.64 ms   (-0.98%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.49 ms →        2.43 ms   (-2.60%) |       1   →       1              |        2.49 ms →        2.43 ms   (-2.60%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.25 ms →        3.20 ms   (-1.52%) |       1   →       1              |        3.25 ms →        3.20 ms   (-1.52%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.27 ms →       22.15 ms   (-0.54%) |       1   →       1              |       22.27 ms →       22.15 ms   (-0.54%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      191.00 ns →      200.00 ns   (+4.71%) |       1   →       1              |      191.00 ns →      200.00 ns   (+4.71%) | 
  ├ sirius::Hamiltonian0                                                |       13.94 ms →       14.29 ms   (+2.49%) |       1   →       1              |       13.94 ms →       14.29 ms   (+2.49%) | 
  │ ├ sirius::Local_operator                                            |       13.61 ms →       13.97 ms   (+2.67%) |       1   →       1              |       13.61 ms →       13.97 ms   (+2.67%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.20 ms →        7.16 ms   (-0.60%) |       1   →       1              |        7.20 ms →        7.16 ms   (-0.60%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.96 ms →        5.35 ms   (+8.01%) |       1   →       1              |        4.96 ms →        5.35 ms   (+8.01%) | 
  │ ├ sirius::Non_local_operator                                        |       60.91 μs →       56.81 μs   (-6.73%) |       2   →       2              |      121.82 μs →      113.62 μs   (-6.73%) | 
  │ ├ sirius::D_operator::initialize                                    |       79.63 μs →       77.72 μs   (-2.40%) |       1   →       1              |       79.63 μs →       77.72 μs   (-2.40%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.86 μs →       67.21 μs   (-3.78%) |       1   →       1              |       69.86 μs →       67.21 μs   (-3.78%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.49 s  →        2.45 s    (-1.37%) |       1   →       1              |        2.49 s  →        2.45 s    (-1.37%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.41 ms   (-0.05%) |       1   →       1              |        8.41 ms →        8.41 ms   (-0.05%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      243.93 μs →      233.06 μs   (-4.46%) |       1   →       1              |      243.93 μs →      233.06 μs   (-4.46%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.17 ms →        8.17 ms   (+0.08%) |       1   →       1              |        8.17 ms →        8.17 ms   (+0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.48 s  →        2.44 s    (-1.38%) |       1   →       1              |        2.48 s  →        2.44 s    (-1.38%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.85 ms →       87.46 ms   (-3.73%) |       4   →       4              |      363.39 ms →      349.83 ms   (-3.73%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       26.42 ms →       25.93 ms   (-1.85%) |       1   →       1              |       26.42 ms →       25.93 ms   (-1.85%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.92 ms →       14.73 ms   (-1.27%) |       1   →       1              |       14.92 ms →       14.73 ms   (-1.27%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.20 s    (-0.28%) |       1   →       1              |        1.21 s  →        1.20 s    (-0.28%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      985.75 ms →      983.56 ms   (-0.22%) |       1   →       1              |      985.75 ms →      983.56 ms   (-0.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      309.64 ms →      313.11 ms   (+1.12%) |       1   →       1              |      309.64 ms →      313.11 ms   (+1.12%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      179.18 ms →      173.25 ms   (-3.31%) |       1   →       1              |      179.18 ms →      173.25 ms   (-3.31%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      179.17 ms →      173.25 ms   (-3.31%) |       1   →       1              |      179.17 ms →      173.25 ms   (-3.31%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      112.02 ms →      121.33 ms   (+8.31%) |       1   →       1              |      112.02 ms →      121.33 ms   (+8.31%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      175.30 ms →      172.91 ms   (-1.36%) |       1   →       1              |      175.30 ms →      172.91 ms   (-1.36%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      175.29 ms →      172.91 ms   (-1.36%) |       1   →       1              |      175.29 ms →      172.91 ms   (-1.36%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      169.23 ms →      163.69 ms   (-3.27%) |       1   →       1              |      169.23 ms →      163.69 ms   (-3.27%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      118.72 ms →      113.13 ms   (-4.71%) |       1   →       1              |      118.72 ms →      113.13 ms   (-4.71%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.73 ms →        3.71 ms   (-0.40%) |       1   →       1              |        3.73 ms →        3.71 ms   (-0.40%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.13 ms →       88.91 ms   (-1.35%) |       1   →       1              |       90.13 ms →       88.91 ms   (-1.35%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.47 ms →       11.23 ms   (-9.95%) |       1   →       1              |       12.47 ms →       11.23 ms   (-9.95%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.20 ms →       64.22 ms   (+0.03%) |       2   →       2              |      128.39 ms →      128.43 ms   (+0.03%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      191.88 ms →      191.75 ms   (-0.06%) |       2   →       2              |      383.75 ms →      383.51 ms   (-0.06%) | 
  │ │ │ └ sddk::wf_inner                                                |      191.77 ms →      191.65 ms   (-0.06%) |       2   →       2              |      383.55 ms →      383.30 ms   (-0.06%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       37.00 ns →       18.50 ns  (-50.00%) |       2   →       2              |       74.00 ns →       37.00 ns  (-50.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      190.26 ms →      190.00 ms   (-0.14%) |       2   →       2              |      380.53 ms →      379.99 ms   (-0.14%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       60.00 ns →       35.00 ns  (-41.67%) |       2   →       2              |      120.00 ns →       70.00 ns  (-41.67%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      114.51 ms →      117.50 ms   (+2.61%) |       1   →       1              |      114.51 ms →      117.50 ms   (+2.61%) | 
  │ │ └ sddk::wf_trans                                                  |       37.90 ms →       35.73 ms   (-5.71%) |       1   →       1              |       37.90 ms →       35.73 ms   (-5.71%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.68 ms →       35.65 ms   (-0.09%) |       1   →       1              |       35.68 ms →       35.65 ms   (-0.09%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      433.00 ns →      494.00 ns  (+14.09%) |       1   →       1              |      433.00 ns →      494.00 ns  (+14.09%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      135.36 s  →      114.08 s   (-15.72%) |       1   →       1              |      135.36 s  →      114.08 s   (-15.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.20 ms →        2.11 ms   (-4.31%) |      31   →      31              |       68.33 ms →       65.38 ms   (-4.31%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.88 s  →        2.92 s    (+1.51%) |      47   →      39    (-17.02%) |      135.14 s  →      113.83 s   (-15.77%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        7.11 ms →        7.53 ms   (+5.81%) |      47   →      39    (-17.02%) |      334.36 ms →      293.56 ms  (-12.20%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        6.78 ms →        7.19 ms   (+6.18%) |      47   →      39    (-17.02%) |      318.45 ms →      280.59 ms  (-11.89%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms →        1.51 ms   (+1.16%) |      47   →      39    (-17.02%) |       70.38 ms →       59.08 ms  (-16.06%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.81 ms →        4.21 ms  (+10.66%) |      47   →      39    (-17.02%) |      179.00 ms →      164.36 ms   (-8.18%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       62.44 μs →       58.56 μs   (-6.20%) |      94   →      78    (-17.02%) |        5.87 ms →        4.57 ms  (-22.17%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       83.23 μs →       83.90 μs   (+0.80%) |      47   →      39    (-17.02%) |        3.91 ms →        3.27 ms  (-16.36%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       69.47 μs →       70.32 μs   (+1.23%) |      47   →      39    (-17.02%) |        3.27 ms →        2.74 ms  (-16.00%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.20 s  →        2.26 s    (+2.56%) |      47   →      39    (-17.02%) |      103.58 s  →       88.15 s   (-14.90%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      205.33 μs →      208.37 μs   (+1.48%) |      47   →      39    (-17.02%) |        9.65 ms →        8.13 ms  (-15.79%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.57 μs →      201.32 μs   (+1.90%) |      47   →      39    (-17.02%) |        9.29 ms →        7.85 ms  (-15.45%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.58 μs →        5.30 μs   (-5.05%) |      47   →      39    (-17.02%) |      262.18 μs →      206.56 μs  (-21.21%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.19 s  →        2.25 s    (+2.62%) |      47   →      39    (-17.02%) |      102.85 s  →       87.58 s   (-14.84%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       54.70 ms →       59.47 ms   (+8.72%) |      47   →      39    (-17.02%) |        2.57 s  →        2.32 s    (-9.79%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        3.83 ms →        4.49 ms  (+17.35%) |     282   →     234    (-17.02%) |        1.08 s  →        1.05 s    (-2.63%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.62 ms →        1.63 ms   (+0.80%) |      47   →      39    (-17.02%) |       76.21 ms →       63.74 ms  (-16.36%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      419.75 μs →      418.16 μs   (-0.38%) |      47   →      39    (-17.02%) |       19.73 ms →       16.31 ms  (-17.33%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      946.15 μs →      962.04 μs   (+1.68%) |      47   →      39    (-17.02%) |       44.47 ms →       37.52 ms  (-15.63%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.11 s  →        2.16 s    (+2.50%) |      47   →      39    (-17.02%) |       99.07 s  →       84.26 s   (-14.95%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      202.37 ms →      187.54 ms   (-7.33%) |     261   →     252     (-3.45%) |       52.82 s  →       47.26 s   (-10.52%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      143.14 ms →      132.23 ms   (-7.62%) |     261   →     252     (-3.45%) |       37.36 s  →       33.32 s   (-10.81%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       26.32 ms →       24.05 ms   (-8.63%) |     261   →     252     (-3.45%) |        6.87 s  →        6.06 s   (-11.78%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      561.00 μs →      547.34 μs   (-2.44%) |     261   →     252     (-3.45%) |      146.42 ms →      137.93 ms   (-5.80%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.10 ms →        3.52 ms  (+13.45%) |      47   →      39    (-17.02%) |      145.86 ms →      137.31 ms   (-5.86%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.53 ms →       19.61 ms   (-8.94%) |     261   →     252     (-3.45%) |        5.62 s  →        4.94 s   (-12.08%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      549.93 μs →      546.66 μs   (-0.59%) |     261   →     252     (-3.45%) |      143.53 ms →      137.76 ms   (-4.02%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.04 ms →        3.52 ms  (+15.70%) |      47   →      39    (-17.02%) |      142.83 ms →      137.13 ms   (-4.00%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       32.67 ms →       29.79 ms   (-8.83%) |     261   →     252     (-3.45%) |        8.53 s  →        7.51 s   (-11.97%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       20.72 ms →       18.67 ms   (-9.88%) |     261   →     252     (-3.45%) |        5.41 s  →        4.71 s   (-12.99%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.62 ms →        2.60 ms   (-0.66%) |     261   →     252     (-3.45%) |      684.15 ms →      656.19 ms   (-4.09%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       21.28 ms →       19.56 ms   (-8.09%) |     261   →     252     (-3.45%) |        5.55 s  →        4.93 s   (-11.26%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.45 ms →        1.91 ms  (-22.02%) |     261   →     252     (-3.45%) |      639.91 ms →      481.82 ms  (-24.71%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       17.65 ms →       16.56 ms   (-6.18%) |     522   →     504     (-3.45%) |        9.21 s  →        8.35 s    (-9.42%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       55.54 ms →       52.28 ms   (-5.86%) |     261   →     252     (-3.45%) |       14.50 s  →       13.18 s    (-9.11%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       12.89 ms →       11.86 ms   (-8.02%) |     475   →     465     (-2.11%) |        6.12 s  →        5.51 s    (-9.95%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |      103.16 ns →       64.64 ns  (-37.34%) |     475   →     465     (-2.11%) |       49.00 μs →       30.06 μs  (-38.66%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.27 ms →        8.44 ms   (-9.00%) |     475   →     465     (-2.11%) |        4.40 s  →        3.92 s   (-10.91%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       90.42 ns →       83.90 ns   (-7.22%) |     475   →     465     (-2.11%) |       42.95 μs →       39.01 μs   (-9.17%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        2.95 ms →        2.74 ms   (-7.06%) |     261   →     252     (-3.45%) |      769.71 ms →      690.70 ms  (-10.26%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       14.78 ms →       13.64 ms   (-7.72%) |     261   →     252     (-3.45%) |        3.86 s  →        3.44 s   (-10.90%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       17.49 ms →       16.58 ms   (-5.20%) |     214   →     213     (-0.47%) |        3.74 s  →        3.53 s    (-5.65%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.78 ms →        5.51 ms   (-4.65%) |     642   →     639     (-0.47%) |        3.71 s  →        3.52 s    (-5.10%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       20.32 ms →       18.51 ms   (-8.92%) |     261   →     252     (-3.45%) |        5.30 s  →        4.66 s   (-12.06%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |       19.03 ms →       17.47 ms   (-8.23%) |     261   →     252     (-3.45%) |        4.97 s  →        4.40 s   (-11.39%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       58.55 ns →       71.48 ns  (+22.08%) |     261   →     252     (-3.45%) |       15.28 μs →       18.01 μs  (+17.87%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       15.47 ms →       13.97 ms   (-9.66%) |     261   →     252     (-3.45%) |        4.04 s  →        3.52 s   (-12.78%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       48.72 ns →       83.93 ns  (+72.26%) |     261   →     252     (-3.45%) |       12.72 μs →       21.15 μs  (+66.32%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       67.87 ms →       42.59 ms  (-37.25%) |     261   →     252     (-3.45%) |       17.72 s  →       10.73 s   (-39.41%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       17.17 ms →       15.25 ms  (-11.15%) |     256   →     247     (-3.52%) |        4.39 s  →        3.77 s   (-14.27%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       17.82 ms →       15.56 ms  (-12.64%) |     219   →     214     (-2.28%) |        3.90 s  →        3.33 s   (-14.64%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.32 ms →        7.17 ms  (-13.84%) |     438   →     428     (-2.28%) |        3.65 s  →        3.07 s   (-15.81%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.52 ms →        1.38 ms   (-9.04%) |     219   →     214     (-2.28%) |      332.04 ms →      295.14 ms  (-11.11%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       65.58 ms →       51.07 ms  (-22.14%) |      66   →      91    (+37.88%) |        4.33 s  →        4.65 s    (+7.36%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       50.28 ms →       31.50 ms  (-37.35%) |      85   →     143    (+68.24%) |        4.27 s  →        4.50 s    (+5.40%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |       40.30 ms →       22.84 ms  (-43.34%) |     104   →     195    (+87.50%) |        4.19 s  →        4.45 s    (+6.24%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      636.62 ns →      535.67 ns  (-15.86%) |      47   →      39    (-17.02%) |       29.92 μs →       20.89 μs  (-30.18%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       33.55 μs →       24.28 μs  (-27.64%) |      47   →      39    (-17.02%) |        1.58 ms →      946.97 μs  (-39.95%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.42 ms →        3.36 ms   (-1.71%) |      47   →      39    (-17.02%) |      160.58 ms →      130.97 ms  (-18.44%) | 
+ │ │ ├ sirius::Density::generate                                       |      298.19 ms →      292.08 ms   (-2.05%) |      47   →      39    (-17.02%) |       14.01 s  →       11.39 s   (-18.72%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      294.15 ms →      288.15 ms   (-2.04%) |      47   →      39    (-17.02%) |       13.83 s  →       11.24 s   (-18.71%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.68 ms →       65.08 ms   (-6.59%) |      47   →      39    (-17.02%) |        3.27 s  →        2.54 s   (-22.49%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       57.64 μs →       67.71 μs  (+17.47%) |      47   →      39    (-17.02%) |        2.71 ms →        2.64 ms   (-2.52%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms →        1.17 ms   (-0.68%) |       2   →       2              |        2.36 ms →        2.35 ms   (-0.68%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       58.26 ms →       53.74 ms   (-7.76%) |      47   →      39    (-17.02%) |        2.74 s  →        2.10 s   (-23.46%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.94 ms →       59.77 ms   (-1.91%) |      47   →      39    (-17.02%) |        2.86 s  →        2.33 s   (-18.61%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.66 μs →        9.39 μs   (-2.85%) |      47   →      39    (-17.02%) |      454.15 μs →      366.11 μs  (-19.39%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (-0.01%) |      47   →      39    (-17.02%) |      108.54 ms →       90.06 ms  (-17.03%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.09 ms →       56.92 ms   (-2.02%) |      47   →      39    (-17.02%) |        2.73 s  →        2.22 s   (-18.70%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.66 ms →        5.48 ms  (-17.63%) |      47   →      39    (-17.02%) |      312.85 ms →      213.82 ms  (-31.65%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      534.77 ns →      598.26 ns  (+11.87%) |      47   →      39    (-17.02%) |       25.13 μs →       23.33 μs   (-7.17%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.47 ms →      104.55 ms   (+0.08%) |      47   →      39    (-17.02%) |        4.91 s  →        4.08 s   (-16.96%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.41 ms   (-0.74%) |      47   →      39    (-17.02%) |      113.94 ms →       93.85 ms  (-17.63%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms →       20.06 ms   (+0.04%) |      47   →      39    (-17.02%) |      942.60 ms →      782.43 ms  (-16.99%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.90 ms   (+0.06%) |      47   →      39    (-17.02%) |      934.50 ms →      775.91 ms  (-16.97%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      230.38 ns →      258.18 ns  (+12.07%) |      47   →      39    (-17.02%) |       10.83 μs →       10.07 μs   (-7.01%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.26 ms   (+0.17%) |      47   →      39    (-17.02%) |       58.96 ms →       49.00 ms  (-16.88%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.78 ms →        2.67 ms   (-3.93%) |      47   →      39    (-17.02%) |      130.66 ms →      104.17 ms  (-20.28%) | 
+ │ │ ├ sirius::Density::mix                                            |      132.93 ms →      128.01 ms   (-3.71%) |      47   →      39    (-17.02%) |        6.25 s  →        4.99 s   (-20.10%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      266.98 μs →      269.79 μs   (+1.05%) |      47   →      39    (-17.02%) |       12.55 ms →       10.52 ms  (-16.15%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        2.65 ms →        3.26 ms  (+22.93%) |      47   →      39    (-17.02%) |      124.67 ms →      127.17 ms   (+2.01%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.46 ms →        3.07 ms  (+24.56%) |      47   →      39    (-17.02%) |      115.73 ms →      119.62 ms   (+3.36%) | 
+ │ │ ├ sirius::Potential::generate                                     |      180.93 ms →      179.69 ms   (-0.68%) |      47   →      39    (-17.02%) |        8.50 s  →        7.01 s   (-17.59%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       64.75 ms →       63.57 ms   (-1.83%) |      47   →      39    (-17.02%) |        3.04 s  →        2.48 s   (-18.54%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.29 ms →        2.47 ms  (-25.02%) |      47   →      39    (-17.02%) |      154.62 ms →       96.20 ms  (-37.78%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.22 ms →        4.22 ms   (-0.05%) |      47   →      39    (-17.02%) |      198.32 ms →      164.48 ms  (-17.07%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms →        4.10 ms   (+0.71%) |      47   →      39    (-17.02%) |      191.54 ms →      160.06 ms  (-16.44%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.07 ms →        4.10 ms   (+0.70%) |      47   →      39    (-17.02%) |      191.52 ms →      160.03 ms  (-16.44%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      234.31 μs →      232.36 μs   (-0.84%) |      94   →      78    (-17.02%) |       22.03 ms →       18.12 ms  (-17.71%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       90.91 ms →       90.80 ms   (-0.12%) |      47   →      39    (-17.02%) |        4.27 s  →        3.54 s   (-17.12%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       89.87 ms →       89.76 ms   (-0.12%) |      47   →      39    (-17.02%) |        4.22 s  →        3.50 s   (-17.12%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.63 ms   (+2.81%) |     235   →     195    (-17.02%) |      373.48 ms →      318.60 ms  (-14.69%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.50 ms →        2.48 ms   (-0.83%) |     423   →     351    (-17.02%) |        1.06 s  →      870.39 ms  (-17.71%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.44 ms →        2.47 ms   (+1.19%) |      47   →      39    (-17.02%) |      114.71 ms →       96.32 ms  (-16.03%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      720.38 μs →      729.63 μs   (+1.28%) |     141   →     117    (-17.02%) |      101.57 ms →       85.37 ms  (-15.96%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.81 ms   (-0.59%) |      47   →      39    (-17.02%) |      132.74 ms →      109.50 ms  (-17.51%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.59 ms →        2.58 ms   (-0.56%) |      47   →      39    (-17.02%) |      121.89 ms →      100.57 ms  (-17.49%) | 
+ │ │ │ │   └ sirius::divergence                                        |       19.78 ms →       19.63 ms   (-0.79%) |      47   →      39    (-17.02%) |      929.84 ms →      765.51 ms  (-17.67%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.44 ms →        2.42 ms   (-0.76%) |      47   →      39    (-17.02%) |      114.57 ms →       94.34 ms  (-17.65%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.32 ms →        3.36 ms   (+1.29%) |      47   →      39    (-17.02%) |      155.89 ms →      131.01 ms  (-15.95%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.93 ms →       20.94 ms   (+0.01%) |      47   →      39    (-17.02%) |      983.90 ms →      816.51 ms  (-17.01%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      201.74 ns →      468.59 ns (+132.27%) |      47   →      39    (-17.02%) |        9.48 μs →       18.27 μs  (+92.73%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      274.49 ns →      443.92 ns  (+61.73%) |      47   →      39    (-17.02%) |       12.90 μs →       17.31 μs  (+34.20%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.27 ms →        2.23 ms   (-1.52%) |      47   →      39    (-17.02%) |      106.51 ms →       87.04 ms  (-18.28%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.21 ms →        4.08 ms   (-3.16%) |     329   →     273    (-17.02%) |        1.39 s  →        1.11 s   (-19.64%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.93 ms →        3.91 ms   (-0.62%) |     329   →     273    (-17.02%) |        1.29 s  →        1.07 s   (-17.54%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.93 ms →        3.91 ms   (-0.62%) |     329   →     273    (-17.02%) |        1.29 s  →        1.07 s   (-17.54%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.31 ms →        4.22 ms   (-2.01%) |     141   →     117    (-17.02%) |      607.05 ms →      493.58 ms  (-18.69%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.08 ms →        4.05 ms   (-0.67%) |     141   →     117    (-17.02%) |      574.77 ms →      473.72 ms  (-17.58%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.03 ms →        4.00 ms   (-0.83%) |      47   →      39    (-17.02%) |      189.45 ms →      155.90 ms  (-17.71%) | 
! │ │ └ sirius::Density::get_magnetisation                              |      115.09 μs →      126.11 μs   (+9.58%) |      47   →      39    (-17.02%) |        5.41 ms →        4.92 ms   (-9.07%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      111.40 μs →      122.54 μs  (+10.01%) |      47   →      39    (-17.02%) |        5.24 ms →        4.78 ms   (-8.72%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.48 ms →        5.34 ms   (-2.52%) |       2   →       2              |       10.96 ms →       10.69 ms   (-2.52%) | 
- │ ├ sirius::Periodic_function|inner                                   |        3.93 ms →        4.35 ms  (+10.71%) |       6   →       6              |       23.60 ms →       26.12 ms  (+10.71%) | 
- │ │ └ sirius::Periodic_function|inner_local                           |        3.90 ms →        4.34 ms  (+11.51%) |       6   →       6              |       23.37 ms →       26.06 ms  (+11.51%) | 
- │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.90 ms →        4.34 ms  (+11.51%) |       6   →       6              |       23.37 ms →       26.06 ms  (+11.51%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |        4.08 ms →        4.53 ms  (+11.14%) |       3   →       3              |       12.23 ms →       13.60 ms  (+11.14%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        4.02 ms →        4.52 ms  (+12.55%) |       3   →       3              |       12.06 ms →       13.57 ms  (+12.55%) | 
- ├ sirius::Periodic_function|inner                                     |        3.88 ms →        4.35 ms  (+12.01%) |       2   →       2              |        7.76 ms →        8.70 ms  (+12.01%) | 
- │ └ sirius::Periodic_function|inner_local                             |        3.86 ms →        4.34 ms  (+12.42%) |       2   →       2              |        7.72 ms →        8.68 ms  (+12.42%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        3.86 ms →        4.34 ms  (+12.42%) |       2   →       2              |        7.72 ms →        8.68 ms  (+12.42%) | 
- ├ sirius::Smooth_periodic_function|inner                              |        4.05 ms →        4.53 ms  (+11.78%) |       1   →       1              |        4.05 ms →        4.53 ms  (+11.78%) | 
- │ └ sirius::Smooth_periodic_function|inner_local                      |        4.01 ms →        4.52 ms  (+12.78%) |       1   →       1              |        4.01 ms →        4.52 ms  (+12.78%) | 
  └ sirius::finalize                                                    |      296.21 ms →      277.58 ms   (-6.29%) |       1   →       1              |      296.21 ms →      277.58 ms   (-6.29%) | 
  ====================================================================================================================================================================================================
```
