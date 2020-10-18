# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.29 s  →      128.66 s    (-3.48%) |       1   →       1              |      133.29 s  →      128.66 s    (-3.48%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.72 s    (+0.83%) |       1   →       1              |        2.70 s  →        2.72 s    (+0.83%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        2.90 s    (-0.73%) |       1   →       1              |        2.92 s  →        2.90 s    (-0.73%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       11.16 ms →      198.90 μs  (-98.22%) |       1   →       1              |       11.16 ms →      198.90 μs  (-98.22%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      137.99 ms →      156.16 ms  (+13.16%) |       1   →       1              |      137.99 ms →      156.16 ms  (+13.16%) | 
- │ │ ├ sirius::Atom_type::init                                         |       57.60 ms →       66.05 ms  (+14.67%) |       2   →       2              |      115.20 ms →      132.10 ms  (+14.67%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.72 ms →       23.98 ms   (+5.56%) |       1   →       1              |       22.72 ms →       23.98 ms   (+5.56%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.24 ms →        6.23 ms   (-0.26%) |       1   →       1              |        6.24 ms →        6.23 ms   (-0.26%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.44 ms →       17.72 ms   (+7.76%) |       1   →       1              |       16.44 ms →       17.72 ms   (+7.76%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.42 ms →       17.70 ms   (+7.77%) |       1   →       1              |       16.42 ms →       17.70 ms   (+7.77%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.15 ms   (+0.26%) |       1   →       1              |        4.14 ms →        4.15 ms   (+0.26%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-0.56%) |       1   →       1              |        2.34 ms →        2.32 ms   (-0.56%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.07 μs →      105.96 μs   (+4.84%) |       1   →       1              |      101.07 μs →      105.96 μs   (+4.84%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.70 s    (-1.03%) |       1   →       1              |        2.73 s  →        2.70 s    (-1.03%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.90 ms →       10.82 ms   (-0.69%) |       1   →       1              |       10.90 ms →       10.82 ms   (-0.69%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.48 ms →        4.41 ms   (-1.71%) |       1   →       1              |        4.48 ms →        4.41 ms   (-1.71%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.39 ms   (+0.02%) |       1   →       1              |        6.39 ms →        6.39 ms   (+0.02%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.37 ms   (+0.02%) |       1   →       1              |        6.37 ms →        6.37 ms   (+0.02%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.85 ms →        3.88 ms   (+0.82%) |       1   →       1              |        3.85 ms →        3.88 ms   (+0.82%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.32 ms   (-1.43%) |       1   →       1              |        2.35 ms →        2.32 ms   (-1.43%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       98.82 μs →      102.58 μs   (+3.81%) |       1   →       1              |       98.82 μs →      102.58 μs   (+3.81%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.64 ms →       62.55 ms   (-0.15%) |       2   →       2              |      125.28 ms →      125.10 ms   (-0.15%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.14 ms   (-0.27%) |       2   →       2              |       10.30 ms →       10.27 ms   (-0.27%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.49 ms   (+0.30%) |       1   →       1              |        4.47 ms →        4.49 ms   (+0.30%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.73 ms →       21.74 ms   (+0.02%) |       2   →       2              |       43.46 ms →       43.47 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.81 ms →       14.79 ms   (-0.13%) |       2   →       2              |       29.62 ms →       29.58 ms   (-0.13%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.77 ms →       19.73 ms   (-0.22%) |       4   →       4              |       79.08 ms →       78.91 ms   (-0.22%) | 
  │   ├ sddk::Gvec::init                                                |      174.67 ms →      175.88 ms   (+0.70%) |       2   →       2              |      349.33 ms →      351.77 ms   (+0.70%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.81 ms →      132.97 ms   (+0.88%) |       2   →       2              |      263.62 ms →      265.93 ms   (+0.88%) | 
  │   ├ sddk::Gvec_shells                                               |      168.69 ms →      168.47 ms   (-0.13%) |       1   →       1              |      168.69 ms →      168.47 ms   (-0.13%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.35 ms →        1.31 ms   (-3.07%) |       1   →       1              |        1.35 ms →        1.31 ms   (-3.07%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      297.26 ms →      292.16 ms   (-1.72%) |       2   →       2              |      594.51 ms →      584.31 ms   (-1.72%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.87 ms →       36.28 ms   (+1.15%) |       1   →       1              |       35.87 ms →       36.28 ms   (+1.15%) | 
  │ ├ sirius::K_point::K_point                                          |        2.43 μs →        2.39 μs   (-1.42%) |       4   →       4              |        9.72 μs →        9.58 μs   (-1.42%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.76 ms →       36.16 ms   (+1.12%) |       1   →       1              |       35.76 ms →       36.16 ms   (+1.12%) | 
  │   └ sirius::K_point::initialize                                     |       35.67 ms →       36.07 ms   (+1.11%) |       1   →       1              |       35.67 ms →       36.07 ms   (+1.11%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.16 ms →       18.89 ms   (+4.03%) |       1   →       1              |       18.16 ms →       18.89 ms   (+4.03%) | 
  │     │ └ sddk::Gvec::init                                            |        8.17 ms →        8.07 ms   (-1.23%) |       1   →       1              |        8.17 ms →        8.07 ms   (-1.23%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        6.80 μs →        6.87 μs   (+1.00%) |       1   →       1              |        6.80 μs →        6.87 μs   (+1.00%) | 
  │     └ sirius::K_point::update                                       |       12.61 ms →       12.34 ms   (-2.17%) |       1   →       1              |       12.61 ms →       12.34 ms   (-2.17%) | 
  │       └ sirius::Beta_projectors                                     |        6.35 ms →        6.04 ms   (-4.94%) |       1   →       1              |        6.35 ms →        6.04 ms   (-4.94%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.74 ms →        3.44 ms   (-7.94%) |       1   →       1              |        3.74 ms →        3.44 ms   (-7.94%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.18 ms →        5.26 ms   (+1.50%) |       2   →       2              |       10.37 ms →       10.52 ms   (+1.50%) | 
  ├ sirius::Potential                                                   |      158.72 ms →      159.51 ms   (+0.50%) |       1   →       1              |      158.72 ms →      159.51 ms   (+0.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.78 ms   (+0.07%) |       6   →       6              |       34.66 ms →       34.68 ms   (+0.07%) | 
  │ └ sirius::Potential::update                                         |      123.30 ms →      124.10 ms   (+0.64%) |       1   →       1              |      123.30 ms →      124.10 ms   (+0.64%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.53 ms →      123.41 ms   (+0.71%) |       1   →       1              |      122.53 ms →      123.41 ms   (+0.71%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      115.25 ms →      116.06 ms   (+0.70%) |       1   →       1              |      115.25 ms →      116.06 ms   (+0.70%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.39 ms →        6.44 ms   (+0.71%) |       1   →       1              |        6.39 ms →        6.44 ms   (+0.71%) | 
  ├ sirius::Density                                                     |      135.07 ms →      137.08 ms   (+1.49%) |       1   →       1              |      135.07 ms →      137.08 ms   (+1.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.16 ms →        5.17 ms   (+0.27%) |       2   →       2              |       10.32 ms →       10.35 ms   (+0.27%) | 
  │ └ sirius::Density::update                                           |      124.48 ms →      126.46 ms   (+1.59%) |       1   →       1              |      124.48 ms →      126.46 ms   (+1.59%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.05 ms →      126.04 ms   (+1.61%) |       1   →       1              |      124.05 ms →      126.04 ms   (+1.61%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.36 μs →      103.28 μs   (+0.90%) |       1   →       1              |      102.36 μs →      103.28 μs   (+0.90%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      118.36 ms →      120.34 ms   (+1.67%) |       1   →       1              |      118.36 ms →      120.34 ms   (+1.67%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.14 ms →        5.16 ms   (+0.40%) |       1   →       1              |        5.14 ms →        5.16 ms   (+0.40%) | 
  ├ sirius::Density::initial_density                                    |      175.73 ms →      176.22 ms   (+0.28%) |       1   →       1              |      175.73 ms →      176.22 ms   (+0.28%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      123.01 ms →      123.49 ms   (+0.39%) |       1   →       1              |      123.01 ms →      123.49 ms   (+0.39%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.98 ms →        5.09 ms   (+2.21%) |       2   →       2              |        9.97 ms →       10.19 ms   (+2.21%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.78 ms →       10.13 ms   (+3.57%) |       1   →       1              |        9.78 ms →       10.13 ms   (+3.57%) | 
  ├ sirius::Potential::generate                                         |      593.56 ms →      593.06 ms   (-0.08%) |       1   →       1              |      593.56 ms →      593.06 ms   (-0.08%) | 
  │ ├ sirius::Potential::poisson                                        |      138.53 ms →      138.44 ms   (-0.07%) |       1   →       1              |      138.53 ms →      138.44 ms   (-0.07%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.32 ms →        5.39 ms   (+1.29%) |       1   →       1              |        5.32 ms →        5.39 ms   (+1.29%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       12.00 ms →       10.87 ms   (-9.48%) |       1   →       1              |       12.00 ms →       10.87 ms   (-9.48%) | 
+ │ │   └ sirius::Periodic_function|inner_local                         |       11.98 ms →        9.89 ms  (-17.47%) |       1   →       1              |       11.98 ms →        9.89 ms  (-17.47%) | 
+ │ │     └ sirius::Smooth_periodic_function|inner_local                |       11.98 ms →        9.88 ms  (-17.49%) |       1   →       1              |       11.98 ms →        9.88 ms  (-17.49%) | 
  │ ├ sirius::Periodic_function::add                                    |      536.76 μs →      553.09 μs   (+3.04%) |       2   →       2              |        1.07 ms →        1.11 ms   (+3.04%) | 
  │ ├ sirius::Potential::xc                                             |       53.95 ms →       53.73 ms   (-0.40%) |       1   →       1              |       53.95 ms →       53.73 ms   (-0.40%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.58 ms →       51.46 ms   (-0.25%) |       1   →       1              |       51.58 ms →       51.46 ms   (-0.25%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.71 ms   (+0.24%) |       2   →       2              |       11.40 ms →       11.43 ms   (+0.24%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.47 ms →        5.23 ms   (-4.36%) |       1   →       1              |        5.47 ms →        5.23 ms   (-4.36%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.74 ms →        5.84 ms   (+1.78%) |       1   →       1              |        5.74 ms →        5.84 ms   (+1.78%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.78 ms →       92.71 ms   (-0.07%) |       1   →       1              |       92.78 ms →       92.71 ms   (-0.07%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.12 ms →      299.89 ms   (-0.08%) |       1   →       1              |      300.12 ms →      299.89 ms   (-0.08%) | 
  ├ sirius::Hamiltonian0                                                |        8.35 ms →        8.59 ms   (+2.77%) |       1   →       1              |        8.35 ms →        8.59 ms   (+2.77%) | 
  │ ├ sirius::Local_operator                                            |        8.00 ms →        8.24 ms   (+2.97%) |       1   →       1              |        8.00 ms →        8.24 ms   (+2.97%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.70 ms →        4.76 ms   (+1.19%) |       1   →       1              |        4.70 ms →        4.76 ms   (+1.19%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        2.57 ms   (+7.93%) |       1   →       1              |        2.38 ms →        2.57 ms   (+7.93%) | 
  │ ├ sirius::Non_local_operator                                        |       63.02 μs →       63.22 μs   (+0.31%) |       2   →       2              |      126.05 μs →      126.44 μs   (+0.31%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.62 μs →       95.31 μs   (-3.36%) |       1   →       1              |       98.62 μs →       95.31 μs   (-3.36%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.23 μs →       74.05 μs   (-2.87%) |       1   →       1              |       76.23 μs →       74.05 μs   (-2.87%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.86 s    (+0.54%) |       1   →       1              |        1.85 s  →        1.86 s    (+0.54%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.69 ms →       18.69 ms   (+0.02%) |       1   →       1              |       18.69 ms →       18.69 ms   (+0.02%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      187.03 μs →      189.76 μs   (+1.46%) |       1   →       1              |      187.03 μs →      189.76 μs   (+1.46%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.50 ms   (+0.00%) |       1   →       1              |       18.50 ms →       18.50 ms   (+0.00%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.85 s    (+0.55%) |       1   →       1              |        1.84 s  →        1.85 s    (+0.55%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      127.89 ms →      126.91 ms   (-0.76%) |       4   →       4              |      511.55 ms →      507.66 ms   (-0.76%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.62 ms →       52.33 ms   (-2.40%) |       1   →       1              |       53.62 ms →       52.33 ms   (-2.40%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.10 ms →       21.30 ms   (+0.98%) |       1   →       1              |       21.10 ms →       21.30 ms   (+0.98%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.62 ms →      639.16 ms   (+0.40%) |       1   →       1              |      636.62 ms →      639.16 ms   (+0.40%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.82 ms →      297.77 ms   (-0.02%) |       1   →       1              |      297.82 ms →      297.77 ms   (-0.02%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.84 μs →        3.55 μs   (-7.38%) |       1   →       1              |        3.84 μs →        3.55 μs   (-7.38%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.92 μs →        2.41 μs  (-17.22%) |       1   →       1              |        2.92 μs →        2.41 μs  (-17.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      335.00 ns →      340.00 ns   (+1.49%) |       1   →       1              |      335.00 ns →      340.00 ns   (+1.49%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      438.00 ns →      440.00 ns   (+0.46%) |       1   →       1              |      438.00 ns →      440.00 ns   (+0.46%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (-0.01%) |       1   →       1              |        9.22 ms →        9.22 ms   (-0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.75 ms →      121.96 ms   (+1.00%) |       1   →       1              |      120.75 ms →      121.96 ms   (+1.00%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.40 ms →      105.09 ms   (+0.67%) |       2   →       2              |      208.79 ms →      210.18 ms   (+0.67%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.26 ms →       40.44 ms   (+0.46%) |       2   →       2              |       80.52 ms →       80.89 ms   (+0.46%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.67 ms →       39.88 ms   (+0.53%) |       2   →       2              |       79.34 ms →       79.76 ms   (+0.53%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       17.00 ns →       20.50 ns  (+20.59%) |       2   →       2              |       34.00 ns →       41.00 ns  (+20.59%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.20 ms →       39.40 ms   (+0.50%) |       2   →       2              |       78.41 ms →       78.80 ms   (+0.50%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       18.50 ns →       30.00 ns  (+62.16%) |       2   →       2              |       37.00 ns →       60.00 ns  (+62.16%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.78 ms →       56.87 ms   (+0.16%) |       1   →       1              |       56.78 ms →       56.87 ms   (+0.16%) | 
  │ │ └ sddk::wf_trans                                                  |       30.73 ms →       31.00 ms   (+0.87%) |       1   →       1              |       30.73 ms →       31.00 ms   (+0.87%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.72 ms →       30.99 ms   (+0.88%) |       1   →       1              |       30.72 ms →       30.99 ms   (+0.88%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      551.00 ns →      399.00 ns  (-27.59%) |       1   →       1              |      551.00 ns →      399.00 ns  (-27.59%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.70 s  →      119.02 s    (-3.79%) |       1   →       1              |      123.70 s  →      119.02 s    (-3.79%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.73 ms   (-0.23%) |      19   →      19              |      109.04 ms →      108.78 ms   (-0.23%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.74 s  →        4.56 s    (-3.72%) |      26   →      26              |      123.21 s  →      118.63 s    (-3.72%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.09 ms →        4.45 ms  (-12.64%) |      26   →      26              |      132.34 ms →      115.61 ms  (-12.64%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.72 ms →        4.08 ms  (-13.60%) |      26   →      26              |      122.68 ms →      105.99 ms  (-13.60%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      956.00 μs →      956.83 μs   (+0.09%) |      26   →      26              |       24.86 ms →       24.88 ms   (+0.09%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.87 ms →        2.23 ms  (-22.23%) |      26   →      26              |       74.57 ms →       57.99 ms  (-22.23%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.79 μs →       64.62 μs   (-0.25%) |      52   →      52              |        3.37 ms →        3.36 ms   (-0.25%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       89.55 μs →       90.21 μs   (+0.74%) |      26   →      26              |        2.33 ms →        2.35 ms   (+0.74%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       81.18 μs →       79.72 μs   (-1.80%) |      26   →      26              |        2.11 ms →        2.07 ms   (-1.80%) | 
  │ │ ├ sirius::Band::solve                                             |        2.78 s  →        2.61 s    (-6.25%) |      26   →      26              |       72.30 s  →       67.79 s    (-6.25%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      157.71 μs →      153.20 μs   (-2.86%) |      26   →      26              |        4.10 ms →        3.98 ms   (-2.86%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      150.04 μs →      145.63 μs   (-2.94%) |      26   →      26              |        3.90 ms →        3.79 ms   (-2.94%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.85 μs →        5.71 μs   (-2.54%) |      26   →      26              |      152.21 μs →      148.34 μs   (-2.54%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.61 s  →        2.48 s    (-4.99%) |      26   →      26              |       67.91 s  →       64.52 s    (-4.99%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       97.08 ms →       94.82 ms   (-2.33%) |      26   →      26              |        2.52 s  →        2.47 s    (-2.33%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.76 ms →        7.62 ms   (-1.76%) |     156   →     156              |        1.21 s  →        1.19 s    (-1.76%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.90 ms →        5.93 ms   (+0.44%) |      26   →      26              |      153.38 ms →      154.05 ms   (+0.44%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.54 μs →      353.38 μs   (+1.10%) |      26   →      26              |        9.09 ms →        9.19 ms   (+1.10%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.30 ms   (-0.10%) |      52   →      52              |      119.76 ms →      119.64 ms   (-0.10%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.47 s  →        2.34 s    (-5.18%) |      26   →      26              |       64.30 s  →       60.97 s    (-5.18%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      129.65 ms →      137.80 ms   (+6.29%) |     271   →     262     (-3.32%) |       35.13 s  →       36.10 s    (+2.76%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       52.21 ms →       55.90 ms   (+7.07%) |     271   →     262     (-3.32%) |       14.15 s  →       14.65 s    (+3.52%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.97 μs →        2.17 μs  (+10.36%) |     271   →     262     (-3.32%) |      533.44 μs →      569.16 μs   (+6.70%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.69 μs →        1.86 μs  (+10.24%) |     271   →     262     (-3.32%) |      457.29 μs →      487.37 μs   (+6.58%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      400.56 ns →      453.36 ns  (+13.18%) |     271   →     262     (-3.32%) |      108.55 μs →      118.78 μs   (+9.42%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      557.24 ns →      605.79 ns   (+8.71%) |     271   →     262     (-3.32%) |      151.01 μs →      158.72 μs   (+5.10%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.43 ms →        7.45 ms   (+0.30%) |     271   →     262     (-3.32%) |        2.01 s  →        1.95 s    (-3.03%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.31 ms →       25.42 ms   (+9.04%) |     271   →     262     (-3.32%) |        6.32 s  →        6.66 s    (+5.42%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.34 ms →       24.51 ms   (+5.00%) |     542   →     524     (-3.32%) |       12.65 s  →       12.84 s    (+1.51%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.91 ms →       35.90 ms   (+2.84%) |     271   →     262     (-3.32%) |        9.46 s  →        9.41 s    (-0.58%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.06 ms →        6.23 ms   (+2.83%) |     516   →     498     (-3.49%) |        3.13 s  →        3.10 s    (-0.76%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       70.04 ns →       45.62 ns  (-34.86%) |     516   →     498     (-3.49%) |       36.14 μs →       22.72 μs  (-37.14%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.95 ms →        5.12 ms   (+3.49%) |     516   →     498     (-3.49%) |        2.55 s  →        2.55 s    (-0.12%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       63.00 ns →       39.86 ns  (-36.74%) |     516   →     498     (-3.49%) |       32.51 μs →       19.85 μs  (-38.94%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      621.15 μs →      652.28 μs   (+5.01%) |     271   →     262     (-3.32%) |      168.33 ms →      170.90 ms   (+1.52%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.77 ms →       10.32 ms   (+5.66%) |     271   →     262     (-3.32%) |        2.65 s  →        2.70 s    (+2.15%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.36 ms →       14.52 ms   (+1.14%) |     245   →     236     (-3.67%) |        3.52 s  →        3.43 s    (-2.57%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.79 ms →        4.84 ms   (+1.14%) |     735   →     708     (-3.67%) |        3.52 s  →        3.43 s    (-2.57%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.51 ms →       10.38 ms   (-1.20%) |     271   →     262     (-3.32%) |        2.85 s  →        2.72 s    (-4.49%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.24 ms →       10.18 ms   (-0.59%) |     271   →     262     (-3.32%) |        2.77 s  →        2.67 s    (-3.89%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       45.65 ns →       22.98 ns  (-49.67%) |     271   →     262     (-3.32%) |       12.37 μs →        6.02 μs  (-51.34%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.12 ms →        9.06 ms   (-0.66%) |     271   →     262     (-3.32%) |        2.47 s  →        2.37 s    (-3.96%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       71.60 ns →       56.07 ns  (-21.69%) |     271   →     262     (-3.32%) |       19.40 μs →       14.69 μs  (-24.29%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       34.18 ms →       18.50 ms  (-45.88%) |     271   →     262     (-3.32%) |        9.26 s  →        4.85 s   (-47.68%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.78 ms →       13.15 ms   (-4.59%) |     262   →     252     (-3.82%) |        3.61 s  →        3.31 s    (-8.23%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.45 ms →       11.72 ms   (-5.85%) |     252   →     242     (-3.97%) |        3.14 s  →        2.84 s    (-9.58%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.22 ms →        5.86 ms   (-5.85%) |     504   →     484     (-3.97%) |        3.14 s  →        2.84 s    (-9.59%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.64 ms →        1.72 ms   (+5.19%) |     252   →     242     (-3.97%) |      412.49 ms →      416.68 ms   (+1.02%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.93 ms →       53.76 ms  (-28.25%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+15.07%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.41 ms →       31.47 ms  (-36.31%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.65%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.94 ms →       22.32 ms  (-39.57%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.65%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      622.42 ns →      426.46 ns  (-31.48%) |      26   →      26              |       16.18 μs →       11.09 μs  (-31.48%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.31 μs →       28.75 μs   (-1.91%) |      26   →      26              |      762.09 μs →      747.53 μs   (-1.91%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      618.53 μs →      609.70 μs   (-1.43%) |      26   →      26              |       16.08 ms →       15.85 ms   (-1.43%) | 
  │ │ ├ sirius::Density::generate                                       |      764.43 ms →      764.11 ms   (-0.04%) |      26   →      26              |       19.88 s  →       19.87 s    (-0.04%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.30 ms →      402.10 ms   (-0.05%) |      26   →      26              |       10.46 s  →       10.45 s    (-0.05%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.39 μs →        9.09 μs   (+8.42%) |      26   →      26              |      218.09 μs →      236.45 μs   (+8.42%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.79 μs →        7.93 μs   (+1.80%) |      26   →      26              |      202.58 μs →      206.22 μs   (+1.80%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.34 ms →      100.37 ms   (+0.03%) |      26   →      26              |        2.61 s  →        2.61 s    (+0.03%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        8.07 μs →        7.21 μs  (-10.66%) |      26   →      26              |      209.89 μs →      187.52 μs  (-10.66%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.01%) |      26   →      26              |      185.08 ms →      185.05 ms   (-0.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.31 ms →       91.38 ms   (+0.07%) |      26   →      26              |        2.37 s  →        2.38 s    (+0.07%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      627.62 ns →      633.27 ns   (+0.90%) |      26   →      26              |       16.32 μs →       16.46 μs   (+0.90%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.80 ms →      163.10 ms   (-1.03%) |      26   →      26              |        4.28 s  →        4.24 s    (-1.03%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.66 ms   (+1.12%) |      26   →      26              |       42.70 ms →       43.18 ms   (+1.12%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.22 ms →       88.27 ms   (+0.06%) |      26   →      26              |        2.29 s  →        2.30 s    (+0.06%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.00 ms →       88.04 ms   (+0.04%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.04%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      270.24 ms →      269.01 ms   (-0.45%) |      26   →      26              |        7.03 s  →        6.99 s    (-0.45%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      270.23 ms →      269.01 ms   (-0.45%) |      26   →      26              |        7.03 s  →        6.99 s    (-0.45%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.13 ms →       23.99 ms   (-0.59%) |      26   →      26              |      627.40 ms →      623.67 ms   (-0.59%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      221.79 ms →      220.48 ms   (-0.59%) |      26   →      26              |        5.77 s  →        5.73 s    (-0.59%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.12 ms →       23.35 ms   (+1.00%) |      26   →      26              |      601.23 ms →      607.22 ms   (+1.00%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.47 ms →       81.37 ms   (+1.12%) |      26   →      26              |        2.09 s  →        2.12 s    (+1.12%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.83 ms →        8.02 ms   (+2.46%) |      26   →      26              |      203.57 ms →      208.57 ms   (+2.46%) | 
  │ │ ├ sirius::Density::mix                                            |      213.58 ms →      210.53 ms   (-1.43%) |      26   →      26              |        5.55 s  →        5.47 s    (-1.43%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      938.06 μs →      975.80 μs   (+4.02%) |      26   →      26              |       24.39 ms →       25.37 ms   (+4.02%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.30 ms →       10.76 ms   (+4.40%) |     334   →     320     (-4.19%) |        3.44 s  →        3.44 s    (+0.02%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.91 ms →       10.37 ms   (+4.60%) |     334   →     320     (-4.19%) |        3.31 s  →        3.32 s    (+0.21%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.91 ms →       10.37 ms   (+4.60%) |     334   →     320     (-4.19%) |        3.31 s  →        3.32 s    (+0.21%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.46 ms →        6.15 ms   (-4.80%) |      26   →      26              |      167.90 ms →      159.84 ms   (-4.80%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.61 ms →        5.32 ms   (-5.15%) |      26   →      26              |      145.96 ms →      138.44 ms   (-5.15%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.66 ms →      580.89 ms   (+0.38%) |      26   →      26              |       15.05 s  →       15.10 s    (+0.38%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.41 ms →      137.97 ms   (+1.15%) |      26   →      26              |        3.55 s  →        3.59 s    (+1.15%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.17 ms →        5.23 ms   (+1.17%) |      26   →      26              |      134.52 ms →      136.10 ms   (+1.17%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.17 ms →       10.24 ms   (+0.67%) |      26   →      26              |      264.35 ms →      266.13 ms   (+0.67%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.85 ms →       10.00 ms   (+1.57%) |      26   →      26              |      256.06 ms →      260.08 ms   (+1.57%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.85 ms →       10.00 ms   (+1.57%) |      26   →      26              |      256.05 ms →      260.07 ms   (+1.57%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      548.77 μs →      552.27 μs   (+0.64%) |      52   →      52              |       28.54 ms →       28.72 ms   (+0.64%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.84 ms →       48.82 ms   (-0.05%) |      26   →      26              |        1.27 s  →        1.27 s    (-0.05%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.49 ms →       46.49 ms   (-0.01%) |      26   →      26              |        1.21 s  →        1.21 s    (-0.01%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.99 ms →        2.99 ms   (-0.01%) |      52   →      52              |      155.58 ms →      155.56 ms   (-0.01%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.44 ms →        5.38 ms   (-1.14%) |      26   →      26              |      141.54 ms →      139.93 ms   (-1.14%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.46 ms →        6.54 ms   (+1.20%) |      26   →      26              |      167.99 ms →      170.00 ms   (+1.20%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.88 ms →       90.86 ms   (-0.02%) |      26   →      26              |        2.36 s  →        2.36 s    (-0.02%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.67 ms →      294.30 ms   (+0.21%) |      26   →      26              |        7.64 s  →        7.65 s    (+0.21%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      275.22 ms →      273.61 ms   (-0.59%) |      26   →      26              |        7.16 s  →        7.11 s    (-0.59%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      275.22 ms →      273.60 ms   (-0.59%) |      26   →      26              |        7.16 s  →        7.11 s    (-0.59%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.12 ms →       27.08 ms   (-0.15%) |      26   →      26              |      705.14 ms →      704.10 ms   (-0.15%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      220.43 ms →      218.72 ms   (-0.78%) |      26   →      26              |        5.73 s  →        5.69 s    (-0.78%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.88 ms →       24.01 ms   (+0.54%) |      26   →      26              |      620.85 ms →      624.20 ms   (+0.54%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.50 ms →        5.75 ms   (+4.53%) |      26   →      26              |      142.98 ms →      149.46 ms   (+4.53%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.37 ms →       10.46 ms   (+0.88%) |     182   →     182              |        1.89 s  →        1.90 s    (+0.88%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.79 ms →        9.90 ms   (+1.15%) |     182   →     182              |        1.78 s  →        1.80 s    (+1.15%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.79 ms →        9.90 ms   (+1.15%) |     182   →     182              |        1.78 s  →        1.80 s    (+1.15%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.62 ms →       10.63 ms   (+0.12%) |      78   →      78              |      828.16 ms →      829.14 ms   (+0.12%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.17 ms →       10.25 ms   (+0.80%) |      78   →      78              |      793.48 ms →      799.86 ms   (+0.80%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.09 ms →       10.05 ms   (-0.42%) |      26   →      26              |      262.45 ms →      261.34 ms   (-0.42%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      105.48 μs →      111.34 μs   (+5.56%) |      26   →      26              |        2.74 ms →        2.89 ms   (+5.56%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      100.44 μs →      106.14 μs   (+5.67%) |      26   →      26              |        2.61 ms →        2.76 ms   (+5.67%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.04 ms →        5.14 ms   (+1.91%) |       2   →       2              |       10.08 ms →       10.27 ms   (+1.91%) | 
- │ ├ sirius::Periodic_function|inner                                   |        9.76 ms →       10.80 ms  (+10.60%) |       6   →       6              |       58.58 ms →       64.79 ms  (+10.60%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.70 ms →        9.72 ms   (+0.16%) |       6   →       6              |       58.21 ms →       58.30 ms   (+0.16%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.70 ms →        9.72 ms   (+0.16%) |       6   →       6              |       58.21 ms →       58.30 ms   (+0.16%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |       10.17 ms →       11.21 ms  (+10.23%) |       3   →       3              |       30.52 ms →       33.64 ms  (+10.23%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.15 ms →       10.08 ms   (-0.63%) |       3   →       3              |       30.44 ms →       30.25 ms   (-0.63%) | 
  ├ sirius::Periodic_function|inner                                     |       10.02 ms →       10.01 ms   (-0.11%) |       2   →       2              |       20.04 ms →       20.01 ms   (-0.11%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.01 ms →        9.66 ms   (-3.46%) |       2   →       2              |       20.02 ms →       19.32 ms   (-3.46%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →        9.66 ms   (-3.46%) |       2   →       2              |       20.02 ms →       19.32 ms   (-3.46%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.48 ms →       10.10 ms   (-3.54%) |       1   →       1              |       10.48 ms →       10.10 ms   (-3.54%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.02 ms   (-4.24%) |       1   →       1              |       10.47 ms →       10.02 ms   (-4.24%) | 
- └ sirius::finalize                                                    |      177.30 ms →      222.39 ms  (+25.43%) |       1   →       1              |      177.30 ms →      222.39 ms  (+25.43%) | 
  ====================================================================================================================================================================================================
```
