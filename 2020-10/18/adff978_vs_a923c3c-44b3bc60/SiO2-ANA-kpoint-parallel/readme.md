# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.39 s  →      128.90 s    (-3.37%) |       1   →       1              |      133.39 s  →      128.90 s    (-3.37%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.69 s    (-0.52%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.52%) | 
  ├ sirius::Simulation_context::initialize                              |        3.06 s  →        2.95 s    (-3.41%) |       1   →       1              |        3.06 s  →        2.95 s    (-3.41%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       32.01 ms →      353.57 μs  (-98.90%) |       1   →       1              |       32.01 ms →      353.57 μs  (-98.90%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      265.78 ms →      191.24 ms  (-28.05%) |       1   →       1              |      265.78 ms →      191.24 ms  (-28.05%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      120.56 ms →       84.24 ms  (-30.12%) |       2   →       2              |      241.12 ms →      168.49 ms  (-30.12%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.59 ms →       22.67 ms   (-7.79%) |       1   →       1              |       24.59 ms →       22.67 ms   (-7.79%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.26 ms →        5.75 ms   (-8.07%) |       1   →       1              |        6.26 ms →        5.75 ms   (-8.07%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.29 ms →       16.88 ms   (-7.72%) |       1   →       1              |       18.29 ms →       16.88 ms   (-7.72%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.27 ms →       16.86 ms   (-7.74%) |       1   →       1              |       18.27 ms →       16.86 ms   (-7.74%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.17 ms   (+0.60%) |       1   →       1              |        4.14 ms →        4.17 ms   (+0.60%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.72%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.72%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.78 μs →      101.87 μs   (+1.08%) |       1   →       1              |      100.78 μs →      101.87 μs   (+1.08%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.71 s    (-0.08%) |       1   →       1              |        2.71 s  →        2.71 s    (-0.08%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.83 ms →       10.84 ms   (+0.08%) |       1   →       1              |       10.83 ms →       10.84 ms   (+0.08%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.47 ms   (+0.34%) |       1   →       1              |        4.45 ms →        4.47 ms   (+0.34%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.34 ms   (-0.10%) |       1   →       1              |        6.35 ms →        6.34 ms   (-0.10%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.33 ms   (-0.09%) |       1   →       1              |        6.33 ms →        6.33 ms   (-0.09%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.84 ms →        3.84 ms   (-0.07%) |       1   →       1              |        3.84 ms →        3.84 ms   (-0.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.31 ms   (-0.07%) |       1   →       1              |        2.31 ms →        2.31 ms   (-0.07%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.56 μs →       98.99 μs   (-1.56%) |       1   →       1              |      100.56 μs →       98.99 μs   (-1.56%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |       84.11 ms →       62.80 ms  (-25.34%) |       2   →       2              |      168.22 ms →      125.59 ms  (-25.34%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.15 ms   (+0.27%) |       2   →       2              |       10.28 ms →       10.30 ms   (+0.27%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.07%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.74 ms →       21.98 ms   (+1.12%) |       2   →       2              |       43.48 ms →       43.97 ms   (+1.12%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.84 ms →       14.86 ms   (+0.19%) |       2   →       2              |       29.67 ms →       29.73 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.71 ms   (-0.35%) |       4   →       4              |       79.12 ms →       78.84 ms   (-0.35%) | 
  │   ├ sddk::Gvec::init                                                |      174.16 ms →      173.12 ms   (-0.60%) |       2   →       2              |      348.32 ms →      346.24 ms   (-0.60%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.33 ms →      130.72 ms   (-0.47%) |       2   →       2              |      262.66 ms →      261.43 ms   (-0.47%) | 
  │   ├ sddk::Gvec_shells                                               |      173.69 ms →      189.41 ms   (+9.05%) |       1   →       1              |      173.69 ms →      189.41 ms   (+9.05%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.34 ms   (+0.99%) |       1   →       1              |        1.32 ms →        1.34 ms   (+0.99%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.12 ms →      293.30 ms   (+0.40%) |       2   →       2              |      584.24 ms →      586.60 ms   (+0.40%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.69 ms →       35.67 ms   (-0.07%) |       1   →       1              |       35.69 ms →       35.67 ms   (-0.07%) | 
  │ ├ sirius::K_point::K_point                                          |        2.52 μs →        2.76 μs   (+9.34%) |       4   →       4              |       10.08 μs →       11.03 μs   (+9.34%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.59 ms →       35.56 ms   (-0.09%) |       1   →       1              |       35.59 ms →       35.56 ms   (-0.09%) | 
  │   └ sirius::K_point::initialize                                     |       35.50 ms →       35.46 ms   (-0.10%) |       1   →       1              |       35.50 ms →       35.46 ms   (-0.10%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.01 ms →       18.02 ms   (+0.07%) |       1   →       1              |       18.01 ms →       18.02 ms   (+0.07%) | 
  │     │ └ sddk::Gvec::init                                            |        8.08 ms →        8.07 ms   (-0.15%) |       1   →       1              |        8.08 ms →        8.07 ms   (-0.15%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.12 μs →        9.27 μs   (-8.38%) |       1   →       1              |       10.12 μs →        9.27 μs   (-8.38%) | 
  │     └ sirius::K_point::update                                       |       12.65 ms →       12.57 ms   (-0.63%) |       1   →       1              |       12.65 ms →       12.57 ms   (-0.63%) | 
  │       └ sirius::Beta_projectors                                     |        6.38 ms →        6.31 ms   (-1.02%) |       1   →       1              |        6.38 ms →        6.31 ms   (-1.02%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.76 ms →        3.69 ms   (-1.96%) |       1   →       1              |        3.76 ms →        3.69 ms   (-1.96%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms →        5.35 ms   (+2.33%) |       2   →       2              |       10.45 ms →       10.70 ms   (+2.33%) | 
  ├ sirius::Potential                                                   |      157.72 ms →      159.48 ms   (+1.12%) |       1   →       1              |      157.72 ms →      159.48 ms   (+1.12%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.80 ms   (-0.99%) |       6   →       6              |       35.13 ms →       34.78 ms   (-0.99%) | 
  │ └ sirius::Potential::update                                         |      121.85 ms →      123.97 ms   (+1.74%) |       1   →       1              |      121.85 ms →      123.97 ms   (+1.74%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.10 ms →      123.21 ms   (+1.74%) |       1   →       1              |      121.10 ms →      123.21 ms   (+1.74%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.44 ms →      106.48 ms   (-1.81%) |       1   →       1              |      108.44 ms →      106.48 ms   (-1.81%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       11.77 ms →       15.85 ms  (+34.61%) |       1   →       1              |       11.77 ms →       15.85 ms  (+34.61%) | 
  ├ sirius::Density                                                     |      134.05 ms →      135.29 ms   (+0.93%) |       1   →       1              |      134.05 ms →      135.29 ms   (+0.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.23 ms →        5.13 ms   (-1.94%) |       2   →       2              |       10.46 ms →       10.25 ms   (-1.94%) | 
  │ └ sirius::Density::update                                           |      123.32 ms →      124.77 ms   (+1.18%) |       1   →       1              |      123.32 ms →      124.77 ms   (+1.18%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      122.89 ms →      124.34 ms   (+1.18%) |       1   →       1              |      122.89 ms →      124.34 ms   (+1.18%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.39 μs →      107.14 μs   (+4.64%) |       1   →       1              |      102.39 μs →      107.14 μs   (+4.64%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.46 ms →      109.40 ms   (-1.84%) |       1   →       1              |      111.46 ms →      109.40 ms   (-1.84%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       10.86 ms →       14.38 ms  (+32.42%) |       1   →       1              |       10.86 ms →       14.38 ms  (+32.42%) | 
  ├ sirius::Density::initial_density                                    |      174.04 ms →      178.36 ms   (+2.48%) |       1   →       1              |      174.04 ms →      178.36 ms   (+2.48%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.16 ms →      109.08 ms   (-0.97%) |       1   →       1              |      110.16 ms →      109.08 ms   (-0.97%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.80 ms →       11.48 ms   (+6.29%) |       2   →       2              |       21.60 ms →       22.95 ms   (+6.29%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.08 ms →       10.85 ms   (+7.62%) |       1   →       1              |       10.08 ms →       10.85 ms   (+7.62%) | 
  ├ sirius::Potential::generate                                         |      591.44 ms →      592.84 ms   (+0.24%) |       1   →       1              |      591.44 ms →      592.84 ms   (+0.24%) | 
  │ ├ sirius::Potential::poisson                                        |      136.35 ms →      136.70 ms   (+0.25%) |       1   →       1              |      136.35 ms →      136.70 ms   (+0.25%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.57 ms →       19.76 ms  (+19.25%) |       1   →       1              |       16.57 ms →       19.76 ms  (+19.25%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.95 ms →        9.95 ms   (+0.00%) |       1   →       1              |        9.95 ms →        9.95 ms   (+0.00%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.93 ms   (+1.16%) |       1   →       1              |        9.82 ms →        9.93 ms   (+1.16%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms →        9.92 ms   (+1.15%) |       1   →       1              |        9.81 ms →        9.92 ms   (+1.15%) | 
  │ ├ sirius::Periodic_function::add                                    |      556.26 μs →      545.87 μs   (-1.87%) |       2   →       2              |        1.11 ms →        1.09 ms   (-1.87%) | 
  │ ├ sirius::Potential::xc                                             |       53.79 ms →       53.89 ms   (+0.18%) |       1   →       1              |       53.79 ms →       53.89 ms   (+0.18%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.44 ms →       51.49 ms   (+0.09%) |       1   →       1              |       51.44 ms →       51.49 ms   (+0.09%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.71 ms →        5.73 ms   (+0.26%) |       2   →       2              |       11.42 ms →       11.45 ms   (+0.26%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.29 ms →        5.41 ms   (+2.30%) |       1   →       1              |        5.29 ms →        5.41 ms   (+2.30%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.98 ms →        5.87 ms   (-1.92%) |       1   →       1              |        5.98 ms →        5.87 ms   (-1.92%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.65 ms →       92.68 ms   (+0.03%) |       1   →       1              |       92.65 ms →       92.68 ms   (+0.03%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.11 ms →      301.24 ms   (+0.38%) |       1   →       1              |      300.11 ms →      301.24 ms   (+0.38%) | 
  ├ sirius::Hamiltonian0                                                |        8.48 ms →        8.40 ms   (-1.04%) |       1   →       1              |        8.48 ms →        8.40 ms   (-1.04%) | 
  │ ├ sirius::Local_operator                                            |        8.13 ms →        8.05 ms   (-1.06%) |       1   →       1              |        8.13 ms →        8.05 ms   (-1.06%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.87 ms →        4.73 ms   (-2.88%) |       1   →       1              |        4.87 ms →        4.73 ms   (-2.88%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        2.40 ms   (+2.43%) |       1   →       1              |        2.35 ms →        2.40 ms   (+2.43%) | 
  │ ├ sirius::Non_local_operator                                        |       62.36 μs →       62.57 μs   (+0.32%) |       2   →       2              |      124.73 μs →      125.13 μs   (+0.32%) | 
  │ ├ sirius::D_operator::initialize                                    |       95.73 μs →       92.82 μs   (-3.04%) |       1   →       1              |       95.73 μs →       92.82 μs   (-3.04%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.34 μs →       75.64 μs   (+1.74%) |       1   →       1              |       74.34 μs →       75.64 μs   (+1.74%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.86 s    (+0.29%) |       1   →       1              |        1.85 s  →        1.86 s    (+0.29%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.67 ms →       18.70 ms   (+0.16%) |       1   →       1              |       18.67 ms →       18.70 ms   (+0.16%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      166.20 μs →      182.56 μs   (+9.85%) |       1   →       1              |      166.20 μs →      182.56 μs   (+9.85%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.51 ms   (+0.07%) |       1   →       1              |       18.50 ms →       18.51 ms   (+0.07%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.84 s    (+0.29%) |       1   →       1              |        1.84 s  →        1.84 s    (+0.29%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.58 ms →      128.22 ms   (+1.29%) |       4   →       4              |      506.32 ms →      512.87 ms   (+1.29%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.49 ms →       52.58 ms   (-1.70%) |       1   →       1              |       53.49 ms →       52.58 ms   (-1.70%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.63 ms →       21.07 ms   (-2.60%) |       1   →       1              |       21.63 ms →       21.07 ms   (-2.60%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.45 ms →      634.72 ms   (+0.04%) |       1   →       1              |      634.45 ms →      634.72 ms   (+0.04%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.81 ms →      297.78 ms   (-0.01%) |       1   →       1              |      297.81 ms →      297.78 ms   (-0.01%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.42 μs →        4.11 μs  (+19.91%) |       1   →       1              |        3.42 μs →        4.11 μs  (+19.91%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.23 μs →        3.08 μs  (+37.85%) |       1   →       1              |        2.23 μs →        3.08 μs  (+37.85%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      377.00 ns →      341.00 ns   (-9.55%) |       1   →       1              |      377.00 ns →      341.00 ns   (-9.55%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      511.00 ns →      513.00 ns   (+0.39%) |       1   →       1              |      511.00 ns →      513.00 ns   (+0.39%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.01%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.46 ms →      120.67 ms   (+0.18%) |       1   →       1              |      120.46 ms →      120.67 ms   (+0.18%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.46 ms →      103.50 ms   (+0.04%) |       2   →       2              |      206.91 ms →      207.00 ms   (+0.04%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.18 ms →       40.17 ms   (-0.03%) |       2   →       2              |       80.35 ms →       80.33 ms   (-0.03%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.61 ms →       39.62 ms   (+0.01%) |       2   →       2              |       79.23 ms →       79.24 ms   (+0.01%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       26.00 ns →       35.50 ns  (+36.54%) |       2   →       2              |       52.00 ns →       71.00 ns  (+36.54%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.14 ms →       39.14 ms   (+0.00%) |       2   →       2              |       78.28 ms →       78.28 ms   (+0.00%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       32.00 ns  (+42.22%) |       2   →       2              |       45.00 ns →       64.00 ns  (+42.22%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.60 ms →       56.53 ms   (-0.13%) |       1   →       1              |       56.60 ms →       56.53 ms   (-0.13%) | 
  │ │ └ sddk::wf_trans                                                  |       30.74 ms →       30.74 ms   (-0.02%) |       1   →       1              |       30.74 ms →       30.74 ms   (-0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.74 ms →       30.73 ms   (-0.02%) |       1   →       1              |       30.74 ms →       30.73 ms   (-0.02%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      604.00 ns →      712.00 ns  (+17.88%) |       1   →       1              |      604.00 ns →      712.00 ns  (+17.88%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.65 s  →      119.18 s    (-3.62%) |       1   →       1              |      123.65 s  →      119.18 s    (-3.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.83 ms   (-0.64%) |      19   →      19              |      111.44 ms →      110.73 ms   (-0.64%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.74 s  →        4.57 s    (-3.66%) |      26   →      26              |      123.33 s  →      118.82 s    (-3.66%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.90 ms →        4.71 ms   (-3.98%) |      26   →      26              |      127.43 ms →      122.36 ms   (-3.98%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.54 ms →        4.34 ms   (-4.34%) |      26   →      26              |      118.00 ms →      112.88 ms   (-4.34%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      982.60 μs →      954.55 μs   (-2.86%) |      26   →      26              |       25.55 ms →       24.82 ms   (-2.86%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.67 ms →        2.50 ms   (-6.37%) |      26   →      26              |       69.35 ms →       64.93 ms   (-6.37%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.10 μs →       64.79 μs   (+1.08%) |      52   →      52              |        3.33 ms →        3.37 ms   (+1.08%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       87.59 μs →       88.47 μs   (+1.00%) |      26   →      26              |        2.28 ms →        2.30 ms   (+1.00%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.75 μs →       77.99 μs   (+0.32%) |      26   →      26              |        2.02 ms →        2.03 ms   (+0.32%) | 
  │ │ ├ sirius::Band::solve                                             |        2.76 s  →        2.60 s    (-5.85%) |      26   →      26              |       71.79 s  →       67.59 s    (-5.85%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      156.64 μs →      157.24 μs   (+0.38%) |      26   →      26              |        4.07 ms →        4.09 ms   (+0.38%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      150.14 μs →      149.55 μs   (-0.40%) |      26   →      26              |        3.90 ms →        3.89 ms   (-0.40%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.64 μs →        5.68 μs  (+22.36%) |      26   →      26              |      120.68 μs →      147.67 μs  (+22.36%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.61 s  →        2.46 s    (-5.64%) |      26   →      26              |       67.81 s  →       63.99 s    (-5.64%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.04 ms →       96.72 ms   (+1.76%) |      26   →      26              |        2.47 s  →        2.51 s    (+1.76%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.69 ms →        7.73 ms   (+0.51%) |     156   →     156              |        1.20 s  →        1.21 s    (+0.51%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.98 ms →        5.97 ms   (-0.15%) |      26   →      26              |      155.44 ms →      155.20 ms   (-0.15%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      361.07 μs →      360.49 μs   (-0.16%) |      26   →      26              |        9.39 ms →        9.37 ms   (-0.16%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.31 ms   (+0.19%) |      52   →      52              |      119.69 ms →      119.91 ms   (+0.19%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.47 s  →        2.32 s    (-6.02%) |      26   →      26              |       64.26 s  →       60.39 s    (-6.02%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      126.28 ms →      136.35 ms   (+7.98%) |     278   →     262     (-5.76%) |       35.11 s  →       35.72 s    (+1.76%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.67 ms →       55.47 ms   (+9.48%) |     278   →     262     (-5.76%) |       14.08 s  →       14.53 s    (+3.18%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.87 μs →        2.06 μs   (+9.81%) |     278   →     262     (-5.76%) |      520.59 μs →      538.75 μs   (+3.49%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.61 μs →        1.78 μs  (+10.56%) |     278   →     262     (-5.76%) |      447.03 μs →      465.78 μs   (+4.19%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      333.86 ns →      366.71 ns   (+9.84%) |     278   →     262     (-5.76%) |       92.81 μs →       96.08 μs   (+3.52%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      390.27 ns →      432.56 ns  (+10.84%) |     278   →     262     (-5.76%) |      108.49 μs →      113.33 μs   (+4.46%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.45%) |     278   →     262     (-5.76%) |        2.06 s  →        1.95 s    (-5.33%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.57 ms →       24.61 ms   (+9.07%) |     278   →     262     (-5.76%) |        6.27 s  →        6.45 s    (+2.79%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.81 ms →       24.40 ms   (+7.00%) |     556   →     524     (-5.76%) |       12.68 s  →       12.79 s    (+0.84%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.20 ms →       35.85 ms   (+4.84%) |     278   →     262     (-5.76%) |        9.51 s  →        9.39 s    (-1.20%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.94 ms →        6.22 ms   (+4.74%) |     530   →     498     (-6.04%) |        3.15 s  →        3.10 s    (-1.58%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       86.75 ns →       49.03 ns  (-43.48%) |     530   →     498     (-6.04%) |       45.98 μs →       24.42 μs  (-46.89%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.82 ms →        5.10 ms   (+5.82%) |     530   →     498     (-6.04%) |        2.56 s  →        2.54 s    (-0.57%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.52 ns →       28.41 ns  (-45.89%) |     530   →     498     (-6.04%) |       27.83 μs →       14.15 μs  (-49.16%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      614.72 μs →      661.28 μs   (+7.57%) |     278   →     262     (-5.76%) |      170.89 ms →      173.26 ms   (+1.38%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.52 ms →       10.31 ms   (+8.29%) |     278   →     262     (-5.76%) |        2.65 s  →        2.70 s    (+2.06%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.06 ms →       14.50 ms   (+3.14%) |     252   →     236     (-6.35%) |        3.54 s  →        3.42 s    (-3.41%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.69 ms →        4.83 ms   (+3.14%) |     756   →     708     (-6.35%) |        3.54 s  →        3.42 s    (-3.41%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.30 ms →       10.38 ms   (+0.73%) |     278   →     262     (-5.76%) |        2.86 s  →        2.72 s    (-5.07%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.03 ms →       10.18 ms   (+1.46%) |     278   →     262     (-5.76%) |        2.79 s  →        2.67 s    (-4.38%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       52.18 ns →       26.84 ns  (-48.55%) |     278   →     262     (-5.76%) |       14.51 μs →        7.03 μs  (-51.51%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.92 ms →        9.06 ms   (+1.65%) |     278   →     262     (-5.76%) |        2.48 s  →        2.37 s    (-4.20%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       71.42 ns →       49.65 ns  (-30.49%) |     278   →     262     (-5.76%) |       19.85 μs →       13.01 μs  (-34.49%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.05 ms →       17.81 ms  (-46.10%) |     278   →     262     (-5.76%) |        9.19 s  →        4.67 s   (-49.20%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.43 ms →       13.14 ms   (-2.18%) |     269   →     252     (-6.32%) |        3.61 s  →        3.31 s    (-8.36%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.12 ms →       11.71 ms   (-3.37%) |     259   →     242     (-6.56%) |        3.14 s  →        2.83 s    (-9.71%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.06 ms →        5.85 ms   (-3.37%) |     518   →     484     (-6.56%) |        3.14 s  →        2.83 s    (-9.71%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.71 ms   (+8.01%) |     259   →     242     (-6.56%) |      411.22 ms →      415.02 ms   (+0.92%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.92 ms →       53.73 ms  (-28.28%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+15.03%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.40 ms →       31.45 ms  (-36.33%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.61%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       22.31 ms  (-39.59%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.61%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      641.50 ns →      458.85 ns  (-28.47%) |      26   →      26              |       16.68 μs →       11.93 μs  (-28.47%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.50 μs →       32.66 μs  (+10.72%) |      26   →      26              |      767.00 μs →      849.22 μs  (+10.72%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      595.38 μs →      615.88 μs   (+3.44%) |      26   →      26              |       15.48 ms →       16.01 ms   (+3.44%) | 
  │ │ ├ sirius::Density::generate                                       |      779.23 ms →      770.98 ms   (-1.06%) |      26   →      26              |       20.26 s  →       20.05 s    (-1.06%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.73 ms →      402.94 ms   (+0.05%) |      26   →      26              |       10.47 s  →       10.48 s    (+0.05%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.31 μs →        8.41 μs   (+1.26%) |      26   →      26              |      216.06 μs →      218.79 μs   (+1.26%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.79 μs →        7.92 μs   (+1.70%) |      26   →      26              |      202.45 μs →      205.88 μs   (+1.70%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.16 ms →      100.19 ms   (+0.04%) |      26   →      26              |        2.60 s  →        2.61 s    (+0.04%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.43 μs →        7.65 μs   (+2.97%) |      26   →      26              |      193.11 μs →      198.84 μs   (+2.97%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.05%) |      26   →      26              |      185.03 ms →      185.12 ms   (+0.05%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.12 ms →       91.17 ms   (+0.06%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.06%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      859.65 ns →      633.42 ns  (-26.32%) |      26   →      26              |       22.35 μs →       16.47 μs  (-26.32%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.79 ms →      162.65 ms   (-0.08%) |      26   →      26              |        4.23 s  →        4.23 s    (-0.08%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.09%) |      26   →      26              |       42.70 ms →       42.66 ms   (-0.09%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.36 ms →       88.27 ms   (-0.10%) |      26   →      26              |        2.30 s  →        2.30 s    (-0.10%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.13 ms →       88.05 ms   (-0.09%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.09%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.26 ms →      276.20 ms   (-0.39%) |      26   →      26              |        7.21 s  →        7.18 s    (-0.39%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.26 ms →      276.19 ms   (-0.39%) |      26   →      26              |        7.21 s  →        7.18 s    (-0.39%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       23.97 ms →       24.24 ms   (+1.12%) |      26   →      26              |      623.29 ms →      630.29 ms   (+1.12%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      229.31 ms →      226.07 ms   (-1.41%) |      26   →      26              |        5.96 s  →        5.88 s    (-1.41%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.78 ms →       24.68 ms   (+8.32%) |      26   →      26              |      592.38 ms →      641.65 ms   (+8.32%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       89.85 ms →       80.93 ms   (-9.93%) |      26   →      26              |        2.34 s  →        2.10 s    (-9.93%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.78 ms →        7.32 ms  (+26.53%) |      26   →      26              |      150.36 ms →      190.25 ms  (+26.53%) | 
  │ │ ├ sirius::Density::mix                                            |      217.53 ms →      214.23 ms   (-1.52%) |      26   →      26              |        5.66 s  →        5.57 s    (-1.52%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      966.30 μs →      966.69 μs   (+0.04%) |      26   →      26              |       25.12 ms →       25.13 ms   (+0.04%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.61 ms →       10.38 ms   (-2.18%) |     334   →     334              |        3.54 s  →        3.47 s    (-2.18%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms →       10.01 ms   (-3.76%) |     334   →     334              |        3.48 s  →        3.34 s    (-3.76%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms →       10.01 ms   (-3.76%) |     334   →     334              |        3.47 s  →        3.34 s    (-3.76%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.03 ms →        7.34 ms   (+4.32%) |      26   →      26              |      182.83 ms →      190.73 ms   (+4.32%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.18 ms →        6.49 ms   (+5.02%) |      26   →      26              |      160.58 ms →      168.64 ms   (+5.02%) | 
  │ │ ├ sirius::Potential::generate                                     |      577.28 ms →      579.14 ms   (+0.32%) |      26   →      26              |       15.01 s  →       15.06 s    (+0.32%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.29 ms →      137.09 ms   (+0.59%) |      26   →      26              |        3.54 s  →        3.56 s    (+0.59%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.77 ms →       19.37 ms  (+15.50%) |      26   →      26              |      435.94 ms →      503.49 ms  (+15.50%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.12 ms →       10.37 ms   (+2.52%) |      26   →      26              |      263.05 ms →      269.67 ms   (+2.52%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.83 ms →        9.99 ms   (+1.58%) |      26   →      26              |      255.67 ms →      259.71 ms   (+1.58%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.83 ms →        9.99 ms   (+1.58%) |      26   →      26              |      255.66 ms →      259.70 ms   (+1.58%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      567.33 μs →      549.33 μs   (-3.17%) |      52   →      52              |       29.50 ms →       28.57 ms   (-3.17%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.87 ms →       49.37 ms   (+1.03%) |      26   →      26              |        1.27 s  →        1.28 s    (+1.03%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.49 ms →       47.03 ms   (+1.16%) |      26   →      26              |        1.21 s  →        1.22 s    (+1.16%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.05 ms →        3.00 ms   (-1.67%) |      52   →      52              |      158.79 ms →      156.14 ms   (-1.67%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.35 ms →        5.77 ms   (+7.92%) |      26   →      26              |      139.04 ms →      150.04 ms   (+7.92%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.51 ms →        6.55 ms   (+0.69%) |      26   →      26              |      169.16 ms →      170.32 ms   (+0.69%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.93 ms →       90.98 ms   (+0.06%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.06%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.23 ms →      292.74 ms   (+0.18%) |      26   →      26              |        7.60 s  →        7.61 s    (+0.18%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      283.63 ms →      280.30 ms   (-1.18%) |      26   →      26              |        7.37 s  →        7.29 s    (-1.18%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      283.63 ms →      280.29 ms   (-1.18%) |      26   →      26              |        7.37 s  →        7.29 s    (-1.18%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.12 ms →       27.45 ms   (+1.23%) |      26   →      26              |      705.10 ms →      713.77 ms   (+1.23%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.88 ms →      225.08 ms   (-1.66%) |      26   →      26              |        5.95 s  →        5.85 s    (-1.66%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.81 ms →       23.92 ms   (+0.46%) |      26   →      26              |      619.04 ms →      621.89 ms   (+0.46%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.61 ms →        5.53 ms   (-1.49%) |      26   →      26              |      145.94 ms →      143.76 ms   (-1.49%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.11 ms →       10.34 ms   (+2.21%) |     182   →     182              |        1.84 s  →        1.88 s    (+2.21%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.82 ms →       10.06 ms   (+2.41%) |     182   →     182              |        1.79 s  →        1.83 s    (+2.41%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →       10.06 ms   (+2.41%) |     182   →     182              |        1.79 s  →        1.83 s    (+2.41%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.92 ms →       10.68 ms   (-2.19%) |      78   →      78              |      851.86 ms →      833.20 ms   (-2.19%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.64 ms →       10.40 ms   (-2.27%) |      78   →      78              |      830.11 ms →      811.23 ms   (-2.27%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.91 ms →       10.06 ms   (+1.49%) |      26   →      26              |      257.67 ms →      261.51 ms   (+1.49%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      112.15 μs →      115.61 μs   (+3.08%) |      26   →      26              |        2.92 ms →        3.01 ms   (+3.08%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.23 μs →      110.36 μs   (+2.92%) |      26   →      26              |        2.79 ms →        2.87 ms   (+2.92%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.11 ms →        5.06 ms   (-1.07%) |       2   →       2              |       10.22 ms →       10.12 ms   (-1.07%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.10 ms →       10.82 ms   (+7.06%) |       6   →       6              |       60.62 ms →       64.90 ms   (+7.06%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.09 ms →       10.77 ms   (+6.68%) |       6   →       6              |       60.56 ms →       64.60 ms   (+6.68%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.09 ms →       10.77 ms   (+6.68%) |       6   →       6              |       60.56 ms →       64.60 ms   (+6.68%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.87 ms →       11.16 ms   (+2.67%) |       3   →       3              |       32.61 ms →       33.49 ms   (+2.67%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.86 ms →       11.15 ms   (+2.66%) |       3   →       3              |       32.59 ms →       33.46 ms   (+2.66%) | 
  ├ sirius::Periodic_function|inner                                     |       10.02 ms →       10.34 ms   (+3.27%) |       2   →       2              |       20.03 ms →       20.68 ms   (+3.27%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.01 ms →       10.33 ms   (+3.28%) |       2   →       2              |       20.01 ms →       20.67 ms   (+3.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →       10.33 ms   (+3.27%) |       2   →       2              |       20.01 ms →       20.67 ms   (+3.27%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.87 ms →       10.74 ms   (-1.17%) |       1   →       1              |       10.87 ms →       10.74 ms   (-1.17%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.86 ms →       10.73 ms   (-1.20%) |       1   →       1              |       10.86 ms →       10.73 ms   (-1.20%) | 
- └ sirius::finalize                                                    |      174.17 ms →      200.41 ms  (+15.06%) |       1   →       1              |      174.17 ms →      200.41 ms  (+15.06%) | 
  ====================================================================================================================================================================================================
```
