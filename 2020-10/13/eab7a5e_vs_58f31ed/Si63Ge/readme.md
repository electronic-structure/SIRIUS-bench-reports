# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.88 s  →       81.22 s   (+13.00%) |       1   →       1              |       71.88 s  →       81.22 s   (+13.00%) | 
  ├ sirius::initialize                                                  |        2.94 s  →        2.95 s    (+0.25%) |       1   →       1              |        2.94 s  →        2.95 s    (+0.25%) | 
  ├ sirius::Simulation_context::initialize                              |        3.83 s  →        3.72 s    (-2.70%) |       1   →       1              |        3.83 s  →        3.72 s    (-2.70%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       23.98 ms →       34.74 ms  (+44.88%) |       1   →       1              |       23.98 ms →       34.74 ms  (+44.88%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      158.59 ms →      288.53 ms  (+81.93%) |       1   →       1              |      158.59 ms →      288.53 ms  (+81.93%) | 
- │ │ ├ sirius::Atom_type::init                                         |       66.73 ms →      135.14 ms (+102.54%) |       2   →       2              |      133.45 ms →      270.29 ms (+102.54%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       25.05 ms →       18.13 ms  (-27.63%) |       1   →       1              |       25.05 ms →       18.13 ms  (-27.63%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.99 ms →        3.79 ms  (-23.99%) |       1   →       1              |        4.99 ms →        3.79 ms  (-23.99%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       20.02 ms →       14.28 ms  (-28.64%) |       1   →       1              |       20.02 ms →       14.28 ms  (-28.64%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       19.94 ms →       14.22 ms  (-28.72%) |       1   →       1              |       19.94 ms →       14.22 ms  (-28.72%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.82 ms →        2.75 ms   (-2.29%) |       1   →       1              |        2.82 ms →        2.75 ms   (-2.29%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      514.30 μs →      843.30 μs  (+63.97%) |       1   →       1              |      514.30 μs →      843.30 μs  (+63.97%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.52 μs →       25.97 μs  (+48.26%) |       1   →       1              |       17.52 μs →       25.97 μs  (+48.26%) | 
  │ └ sirius::Simulation_context::update                                |        3.59 s  →        3.31 s    (-7.74%) |       1   →       1              |        3.59 s  →        3.31 s    (-7.74%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.09 ms →        7.02 ms   (-1.05%) |       1   →       1              |        7.09 ms →        7.02 ms   (-1.05%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.71 ms →        3.64 ms   (-1.87%) |       1   →       1              |        3.71 ms →        3.64 ms   (-1.87%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        3.34 ms   (+0.15%) |       1   →       1              |        3.33 ms →        3.34 ms   (+0.15%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.27 ms   (+0.11%) |       1   →       1              |        3.26 ms →        3.27 ms   (+0.11%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.72 ms   (+0.61%) |       1   →       1              |        2.71 ms →        2.72 ms   (+0.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      517.47 μs →      505.11 μs   (-2.39%) |       1   →       1              |      517.47 μs →      505.11 μs   (-2.39%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.55 μs →       14.37 μs   (-1.26%) |       1   →       1              |       14.55 μs →       14.37 μs   (-1.26%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      211.61 ms →      212.73 ms   (+0.53%) |       2   →       2              |      423.23 ms →      425.45 ms   (+0.53%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.21 ms   (+0.30%) |       2   →       2              |       30.34 ms →       30.43 ms   (+0.30%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.26 ms   (+0.09%) |       1   →       1              |       13.25 ms →       13.26 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.29 ms →       56.39 ms   (+0.18%) |       2   →       2              |      112.58 ms →      112.78 ms   (+0.18%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.02 ms →       45.20 ms   (+0.40%) |       2   →       2              |       90.05 ms →       90.40 ms   (+0.40%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.28 ms →       60.25 ms   (-0.06%) |       4   →       4              |      241.13 ms →      240.98 ms   (-0.06%) | 
  │   ├ sddk::Gvec::init                                                |       93.30 ms →       92.83 ms   (-0.51%) |       2   →       2              |      186.60 ms →      185.66 ms   (-0.51%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.90 ms →       69.54 ms   (-0.52%) |       2   →       2              |      139.80 ms →      139.08 ms   (-0.52%) | 
- │   ├ sddk::Gvec_shells                                               |       95.38 ms →      105.20 ms  (+10.30%) |       1   →       1              |       95.38 ms →      105.20 ms  (+10.30%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.94 ms   (-0.03%) |       1   →       1              |        1.94 ms →        1.94 ms   (-0.03%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      657.78 ms →      516.59 ms  (-21.47%) |       2   →       2              |        1.32 s  →        1.03 s   (-21.47%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       86.62 ms →      157.66 ms  (+82.01%) |       1   →       1              |       86.62 ms →      157.66 ms  (+82.01%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.08 μs →        1.84 μs  (-11.63%) |       4   →       4              |        8.32 μs →        7.35 μs  (-11.63%) | 
- │ └ sirius::K_point_set::initialize                                   |       86.54 ms →      157.58 ms  (+82.09%) |       1   →       1              |       86.54 ms →      157.58 ms  (+82.09%) | 
  │   └ sirius::K_point::initialize                                     |       28.34 ms →       28.28 ms   (-0.22%) |       1   →       1              |       28.34 ms →       28.28 ms   (-0.22%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.94 ms →       11.12 ms   (+1.61%) |       1   →       1              |       10.94 ms →       11.12 ms   (+1.61%) | 
  │     │ └ sddk::Gvec::init                                            |        4.89 ms →        4.96 ms   (+1.38%) |       1   →       1              |        4.89 ms →        4.96 ms   (+1.38%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.13 μs →        6.92 μs   (-2.93%) |       1   →       1              |        7.13 μs →        6.92 μs   (-2.93%) | 
  │     └ sirius::K_point::update                                       |       14.55 ms →       14.31 ms   (-1.65%) |       1   →       1              |       14.55 ms →       14.31 ms   (-1.65%) | 
  │       └ sirius::Beta_projectors                                     |       10.59 ms →       10.30 ms   (-2.72%) |       1   →       1              |       10.59 ms →       10.30 ms   (-2.72%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.73 ms →        8.26 ms   (-5.37%) |       1   →       1              |        8.73 ms →        8.26 ms   (-5.37%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.59 ms →        2.56 ms   (-0.92%) |       2   →       2              |        5.18 ms →        5.13 ms   (-0.92%) | 
  ├ sirius::Potential                                                   |       49.36 ms →       51.98 ms   (+5.31%) |       1   →       1              |       49.36 ms →       51.98 ms   (+5.31%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.90 ms   (-0.94%) |       6   →       6              |       17.55 ms →       17.39 ms   (-0.94%) | 
  │ └ sirius::Potential::update                                         |       31.19 ms →       33.97 ms   (+8.92%) |       1   →       1              |       31.19 ms →       33.97 ms   (+8.92%) | 
  │   └ sirius::Potential::generate_local_potential                     |       30.80 ms →       33.58 ms   (+9.05%) |       1   →       1              |       30.80 ms →       33.58 ms   (+9.05%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.23 ms →       24.09 ms   (-8.17%) |       1   →       1              |       26.23 ms →       24.09 ms   (-8.17%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.00 ms →        8.97 ms (+124.24%) |       1   →       1              |        4.00 ms →        8.97 ms (+124.24%) | 
- ├ sirius::Density                                                     |       38.06 ms →       42.70 ms  (+12.21%) |       1   →       1              |       38.06 ms →       42.70 ms  (+12.21%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.80 ms   (-0.87%) |       2   →       2              |        5.64 ms →        5.60 ms   (-0.87%) | 
- │ └ sirius::Density::update                                           |       32.27 ms →       36.97 ms  (+14.55%) |       1   →       1              |       32.27 ms →       36.97 ms  (+14.55%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       32.06 ms →       36.76 ms  (+14.67%) |       1   →       1              |       32.06 ms →       36.76 ms  (+14.67%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.31 μs →       77.20 μs   (+1.17%) |       1   →       1              |       76.31 μs →       77.20 μs   (+1.17%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.19 ms →       24.00 ms   (-8.34%) |       1   →       1              |       26.19 ms →       24.00 ms   (-8.34%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.47 ms →       12.38 ms (+126.40%) |       1   →       1              |        5.47 ms →       12.38 ms (+126.40%) | 
- ├ sirius::Density::initial_density                                    |       55.33 ms →       61.82 ms  (+11.74%) |       1   →       1              |       55.33 ms →       61.82 ms  (+11.74%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.61 ms →       25.17 ms   (-5.39%) |       1   →       1              |       26.61 ms →       25.17 ms   (-5.39%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.26 ms →        8.69 ms  (+65.20%) |       2   →       2              |       10.52 ms →       17.38 ms  (+65.20%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.54 ms →        5.71 ms  (+25.79%) |       1   →       1              |        4.54 ms →        5.71 ms  (+25.79%) | 
  ├ sirius::Potential::generate                                         |      362.95 ms →      369.40 ms   (+1.78%) |       1   →       1              |      362.95 ms →      369.40 ms   (+1.78%) | 
- │ ├ sirius::Potential::poisson                                        |       34.90 ms →       42.16 ms  (+20.82%) |       1   →       1              |       34.90 ms →       42.16 ms  (+20.82%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.17 ms →       13.21 ms (+216.87%) |       1   →       1              |        4.17 ms →       13.21 ms (+216.87%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.46 ms →        5.89 ms   (+7.90%) |       1   →       1              |        5.46 ms →        5.89 ms   (+7.90%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.88 ms →        4.68 ms   (-4.15%) |       1   →       1              |        4.88 ms →        4.68 ms   (-4.15%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.87 ms →        4.67 ms   (-4.21%) |       1   →       1              |        4.87 ms →        4.67 ms   (-4.21%) | 
  │ ├ sirius::Periodic_function::add                                    |      808.04 μs →      787.09 μs   (-2.59%) |       2   →       2              |        1.62 ms →        1.57 ms   (-2.59%) | 
  │ ├ sirius::Potential::xc                                             |       51.57 ms →       51.76 ms   (+0.37%) |       1   →       1              |       51.57 ms →       51.76 ms   (+0.37%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.38 ms →       50.57 ms   (+0.38%) |       1   →       1              |       50.38 ms →       50.57 ms   (+0.38%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.52 ms   (-0.40%) |       2   →       2              |        5.07 ms →        5.05 ms   (-0.40%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.17 ms →        4.63 ms  (+11.02%) |       1   →       1              |        4.17 ms →        4.63 ms  (+11.02%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.86 ms →        3.64 ms   (-5.48%) |       1   →       1              |        3.86 ms →        3.64 ms   (-5.48%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.62 ms →      268.85 ms   (-0.29%) |       1   →       1              |      269.62 ms →      268.85 ms   (-0.29%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      381.00 ns →      223.00 ns  (-41.47%) |       1   →       1              |      381.00 ns →      223.00 ns  (-41.47%) | 
- ├ sirius::Hamiltonian0                                                |        6.29 ms →        8.85 ms  (+40.69%) |       1   →       1              |        6.29 ms →        8.85 ms  (+40.69%) | 
- │ ├ sirius::Local_operator                                            |        5.84 ms →        8.37 ms  (+43.45%) |       1   →       1              |        5.84 ms →        8.37 ms  (+43.45%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.74 ms   (+0.27%) |       1   →       1              |        2.73 ms →        2.74 ms   (+0.27%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        4.07 ms  (+74.74%) |       1   →       1              |        2.33 ms →        4.07 ms  (+74.74%) | 
- │ ├ sirius::Non_local_operator                                        |       75.53 μs →      109.77 μs  (+45.33%) |       2   →       2              |      151.06 μs →      219.53 μs  (+45.33%) | 
+ │ ├ sirius::D_operator::initialize                                    |      135.55 μs →      103.65 μs  (-23.53%) |       1   →       1              |      135.55 μs →      103.65 μs  (-23.53%) | 
  │ └ sirius::Q_operator::initialize                                    |      104.96 μs →       94.77 μs   (-9.71%) |       1   →       1              |      104.96 μs →       94.77 μs   (-9.71%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.30 s    (+1.56%) |       1   →       1              |        1.28 s  →        1.30 s    (+1.56%) | 
- │ ├ sirius::Hamiltonian_k                                             |       39.61 ms →       58.14 ms  (+46.78%) |       1   →       1              |       39.61 ms →       58.14 ms  (+46.78%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      242.66 μs →      222.60 μs   (-8.27%) |       1   →       1              |      242.66 μs →      222.60 μs   (-8.27%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       39.37 ms →       57.92 ms  (+47.13%) |       1   →       1              |       39.37 ms →       57.92 ms  (+47.13%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.24 s    (+0.11%) |       1   →       1              |        1.24 s  →        1.24 s    (+0.11%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       82.53 ms →       78.99 ms   (-4.29%) |       4   →       4              |      330.12 ms →      315.95 ms   (-4.29%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       36.91 ms →       53.68 ms  (+45.45%) |       1   →       1              |       36.91 ms →       53.68 ms  (+45.45%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.09 ms →        8.83 ms   (+9.07%) |       1   →       1              |        8.09 ms →        8.83 ms   (+9.07%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      312.36 ms →      311.92 ms   (-0.14%) |       1   →       1              |      312.36 ms →      311.92 ms   (-0.14%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      244.31 ms →      243.97 ms   (-0.14%) |       1   →       1              |      244.31 ms →      243.97 ms   (-0.14%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.44 μs →        3.87 μs  (-12.81%) |       1   →       1              |        4.44 μs →        3.87 μs  (-12.81%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.20 μs →        2.95 μs   (-7.87%) |       1   →       1              |        3.20 μs →        2.95 μs   (-7.87%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      471.00 ns →      505.00 ns   (+7.22%) |       1   →       1              |      471.00 ns →      505.00 ns   (+7.22%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      558.00 ns →      863.00 ns  (+54.66%) |       1   →       1              |      558.00 ns →      863.00 ns  (+54.66%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.24 ms →        3.19 ms   (-1.67%) |       1   →       1              |        3.24 ms →        3.19 ms   (-1.67%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.30 ms →       21.22 ms   (-0.37%) |       1   →       1              |       21.30 ms →       21.22 ms   (-0.37%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       21.74 ms →       21.74 ms   (+0.01%) |       2   →       2              |       43.47 ms →       43.48 ms   (+0.01%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.66 ms →       16.17 ms   (-2.93%) |       2   →       2              |       33.32 ms →       32.34 ms   (-2.93%) | 
  │ │ │ └ sddk::wf_inner                                                |       16.44 ms →       15.96 ms   (-2.91%) |       2   →       2              |       32.88 ms →       31.92 ms   (-2.91%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       20.50 ns →       19.00 ns   (-7.32%) |       2   →       2              |       41.00 ns →       38.00 ns   (-7.32%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       16.29 ms →       15.83 ms   (-2.86%) |       2   →       2              |       32.59 ms →       31.65 ms   (-2.86%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       20.50 ns   (-8.89%) |       2   →       2              |       45.00 ns →       41.00 ns   (-8.89%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.84 ms →      250.47 ms   (+0.25%) |       1   →       1              |      249.84 ms →      250.47 ms   (+0.25%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.60 ms   (-0.12%) |       1   →       1              |        2.61 ms →        2.60 ms   (-0.12%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        2.60 ms   (-0.14%) |       1   →       1              |        2.60 ms →        2.60 ms   (-0.14%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      729.00 ns →      515.00 ns  (-29.36%) |       1   →       1              |      729.00 ns →      515.00 ns  (-29.36%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       62.11 s  →       71.47 s   (+15.06%) |       1   →       1              |       62.11 s  →       71.47 s   (+15.06%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.44 ms   (-0.45%) |      19   →      19              |       46.58 ms →       46.37 ms   (-0.45%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        3.10 s    (-4.61%) |      19   →      23    (+21.05%) |       61.67 s  →       71.22 s   (+15.48%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.36 ms →        6.01 ms  (+12.12%) |      19   →      23    (+21.05%) |      101.77 ms →      138.13 ms  (+35.72%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.65 ms →        5.22 ms  (+12.16%) |      19   →      23    (+21.05%) |       88.41 ms →      120.03 ms  (+35.77%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      540.68 μs →      564.32 μs   (+4.37%) |      19   →      23    (+21.05%) |       10.27 ms →       12.98 ms  (+26.35%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.04 ms →        3.39 ms  (+11.44%) |      19   →      23    (+21.05%) |       57.78 ms →       77.94 ms  (+34.90%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      204.44 μs →      253.98 μs  (+24.23%) |      38   →      46    (+21.05%) |        7.77 ms →       11.68 ms  (+50.38%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      118.42 μs →      111.97 μs   (-5.45%) |      19   →      23    (+21.05%) |        2.25 ms →        2.58 ms  (+14.46%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       93.20 μs →       90.02 μs   (-3.41%) |      19   →      23    (+21.05%) |        1.77 ms →        2.07 ms  (+16.92%) | 
- │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.87 s    (-7.69%) |      19   →      23    (+21.05%) |       38.49 s  →       43.01 s   (+11.74%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      194.97 μs →      196.41 μs   (+0.74%) |      19   →      23    (+21.05%) |        3.70 ms →        4.52 ms  (+21.95%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      186.56 μs →      185.63 μs   (-0.50%) |      19   →      23    (+21.05%) |        3.54 ms →        4.27 ms  (+20.45%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.03 μs →        8.20 μs  (+36.14%) |      19   →      23    (+21.05%) |      114.51 μs →      188.71 μs  (+64.80%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.75 s   (-10.75%) |      19   →      23    (+21.05%) |       37.25 s  →       40.25 s    (+8.04%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.64 ms →       70.11 ms   (-8.53%) |      19   →      23    (+21.05%) |        1.46 s  →        1.61 s   (+10.73%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.96 ms →        6.72 ms  (-15.61%) |     114   →     138    (+21.05%) |      907.30 ms →      926.85 ms   (+2.15%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.93 ms →       15.71 ms   (-7.21%) |      19   →      23    (+21.05%) |      321.66 ms →      361.32 ms  (+12.33%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      454.12 μs →      482.59 μs   (+6.27%) |      19   →      23    (+21.05%) |        8.63 ms →       11.10 ms  (+28.64%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.54 ms →        7.20 ms   (-4.54%) |      38   →      46    (+21.05%) |      286.46 ms →      331.02 ms  (+15.55%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.65 s   (-10.91%) |      19   →      23    (+21.05%) |       35.28 s  →       38.04 s    (+7.84%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       47.04 ms →       68.53 ms  (+45.68%) |     356   →     298    (-16.29%) |       16.75 s  →       20.42 s   (+21.94%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.10 ms →       44.05 ms  (+56.75%) |     356   →     298    (-16.29%) |       10.01 s  →       13.13 s   (+31.21%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.15 μs →        2.26 μs   (+5.49%) |     356   →     298    (-16.29%) |      763.83 μs →      674.50 μs  (-11.69%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.81 μs →        1.91 μs   (+5.50%) |     356   →     298    (-16.29%) |      645.36 μs →      569.91 μs  (-11.69%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      433.93 ns →      465.66 ns   (+7.31%) |     356   →     298    (-16.29%) |      154.48 μs →      138.77 μs  (-10.17%) | 
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      571.36 ns →      620.09 ns   (+8.53%) |     356   →     298    (-16.29%) |      203.40 μs →      184.79 μs   (-9.15%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.60 ms →        3.45 ms  (+32.82%) |     356   →     298    (-16.29%) |      924.93 ms →        1.03 s   (+11.18%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.12 ms →        3.79 ms  (+21.33%) |     356   →     298    (-16.29%) |        1.11 s  →        1.13 s    (+1.56%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.60 ms →        8.61 ms  (+30.45%) |     712   →     596    (-16.29%) |        4.70 s  →        5.13 s    (+9.19%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        6.26 ms →        6.24 ms   (-0.30%) |     356   →     298    (-16.29%) |        2.23 s  →        1.86 s   (-16.54%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      983.56 μs →        1.09 ms  (+10.39%) |     693   →     573    (-17.32%) |      681.61 ms →      622.12 ms   (-8.73%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       54.91 ns →       40.11 ns  (-26.96%) |     693   →     573    (-17.32%) |       38.05 μs →       22.98 μs  (-39.61%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      822.76 μs →      923.04 μs  (+12.19%) |     693   →     573    (-17.32%) |      570.17 ms →      528.90 ms   (-7.24%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.19 ns →       37.78 ns  (-16.40%) |     693   →     573    (-17.32%) |       31.32 μs →       21.65 μs  (-30.88%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      131.50 μs →      165.20 μs  (+25.63%) |     356   →     298    (-16.29%) |       46.81 ms →       49.23 ms   (+5.16%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.02 ms →        1.84 ms   (-9.22%) |     356   →     298    (-16.29%) |      720.37 ms →      547.43 ms  (-24.01%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |        2.31 ms →        2.33 ms   (+0.73%) |     337   →     275    (-18.40%) |      778.96 ms →      640.28 ms  (-17.80%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |      769.70 μs →      775.24 μs   (+0.72%) |    1.01 K →     825    (-18.40%) |      778.17 ms →      639.58 ms  (-17.81%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.52 ms →        1.45 ms   (-4.76%) |     356   →     298    (-16.29%) |      542.37 ms →      432.40 ms  (-20.28%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.46 ms →        1.35 ms   (-7.34%) |     356   →     298    (-16.29%) |      518.11 ms →      401.87 ms  (-22.43%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.02 ns →       33.27 ns  (-18.89%) |     356   →     298    (-16.29%) |       14.60 μs →        9.91 μs  (-32.11%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.29 ms →        1.19 ms   (-8.42%) |     356   →     298    (-16.29%) |      460.96 ms →      353.36 ms  (-23.34%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       40.64 ns →       70.12 ns  (+72.55%) |     356   →     298    (-16.29%) |       14.47 μs →       20.90 μs  (+44.44%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       40.97 ms →       47.19 ms  (+15.21%) |     356   →     298    (-16.29%) |       14.58 s  →       14.06 s    (-3.56%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.32 ms →        2.93 ms  (+26.47%) |     340   →     289    (-15.00%) |      787.31 ms →      846.39 ms   (+7.50%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.28 ms →        1.69 ms  (+31.54%) |     337   →     278    (-17.51%) |      432.25 ms →      469.03 ms   (+8.51%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      639.92 μs →      842.11 μs  (+31.60%) |     674   →     556    (-17.51%) |      431.30 ms →      468.21 ms   (+8.56%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      931.87 μs →        1.22 ms  (+31.01%) |     337   →     278    (-17.51%) |      314.04 ms →      339.39 ms   (+8.07%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.02 ms →        7.18 ms   (+2.32%) |      54   →      57     (+5.56%) |      378.83 ms →      409.17 ms   (+8.01%) | 
  │ │ │ │     └ sddk::wf_trans                                          |        4.21 ms →        4.45 ms   (+5.71%) |      89   →      91     (+2.25%) |      374.48 ms →      404.77 ms   (+8.09%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |        3.02 ms →        3.24 ms   (+7.22%) |     124   →     125     (+0.81%) |      374.32 ms →      404.58 ms   (+8.08%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      369.58 ns →      366.22 ns   (-0.91%) |      19   →      23    (+21.05%) |        7.02 μs →        8.42 μs  (+19.95%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.40 μs →       20.26 μs   (-0.66%) |      19   →      23    (+21.05%) |      387.55 μs →      466.02 μs  (+20.25%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.58 ms →        1.49 ms   (-6.00%) |      19   →      23    (+21.05%) |       30.07 ms →       34.22 ms  (+13.79%) | 
- │ │ ├ sirius::Density::generate                                       |      570.17 ms →      564.25 ms   (-1.04%) |      19   →      23    (+21.05%) |       10.83 s  →       12.98 s   (+19.80%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      413.71 ms →      381.55 ms   (-7.78%) |      19   →      23    (+21.05%) |        7.86 s  →        8.78 s   (+11.64%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.79 μs →        8.45 μs   (+8.54%) |      19   →      23    (+21.05%) |      147.97 μs →      194.41 μs  (+31.39%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.24 μs →        7.85 μs   (+8.46%) |      19   →      23    (+21.05%) |      137.52 μs →      180.57 μs  (+31.30%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       43.62 ms →       41.61 ms   (-4.60%) |      19   →      23    (+21.05%) |      828.73 ms →      957.04 ms  (+15.48%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.52 μs →        7.86 μs   (+4.49%) |      19   →      23    (+21.05%) |      142.87 μs →      180.71 μs  (+26.48%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.41 ms →       23.19 ms (+213.02%) |      19   →      23    (+21.05%) |      140.76 ms →      533.36 ms (+278.92%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       35.16 ms →       17.38 ms  (-50.57%) |      19   →      23    (+21.05%) |      668.13 ms →      399.77 ms  (-40.17%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      599.53 ns →      622.39 ns   (+3.81%) |      19   →      23    (+21.05%) |       11.39 μs →       14.31 μs  (+25.67%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      102.45 ms →       97.79 ms   (-4.55%) |      19   →      23    (+21.05%) |        1.95 s  →        2.25 s   (+15.55%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.80 ms →        2.06 ms  (+14.74%) |      19   →      23    (+21.05%) |       34.19 ms →       47.49 ms  (+38.89%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      226.85 ms →      195.43 ms  (-13.85%) |      19   →      23    (+21.05%) |        4.31 s  →        4.49 s    (+4.29%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      226.63 ms →      195.20 ms  (-13.87%) |      19   →      23    (+21.05%) |        4.31 s  →        4.49 s    (+4.26%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      128.80 ms →      153.97 ms  (+19.54%) |      19   →      23    (+21.05%) |        2.45 s  →        3.54 s   (+44.71%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      128.80 ms →      153.97 ms  (+19.54%) |      19   →      23    (+21.05%) |        2.45 s  →        3.54 s   (+44.71%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       45.01 ms →       70.31 ms  (+56.21%) |      19   →      23    (+21.05%) |      855.18 ms →        1.62 s   (+89.10%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.43 ms →       70.36 ms   (-0.10%) |      19   →      23    (+21.05%) |        1.34 s  →        1.62 s   (+20.94%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.71 ms →       12.64 ms   (-0.53%) |      19   →      23    (+21.05%) |      241.49 ms →      290.78 ms  (+20.41%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.71 ms →       23.71 ms   (+0.00%) |      19   →      23    (+21.05%) |      450.51 ms →      545.37 ms  (+21.06%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.94 ms →        5.02 ms  (+27.47%) |      19   →      23    (+21.05%) |       74.81 ms →      115.44 ms  (+54.31%) | 
- │ │ ├ sirius::Density::mix                                            |      133.63 ms →      138.17 ms   (+3.40%) |      19   →      23    (+21.05%) |        2.54 s  →        3.18 s   (+25.16%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      839.63 μs →      727.35 μs  (-13.37%) |      19   →      23    (+21.05%) |       15.95 ms →       16.73 ms   (+4.86%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.94 ms →        4.90 ms   (-0.81%) |     229   →     289    (+26.20%) |        1.13 s  →        1.42 s   (+25.18%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.87 ms   (+1.13%) |     229   →     289    (+26.20%) |        1.10 s  →        1.41 s   (+27.62%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.87 ms   (+1.12%) |     229   →     289    (+26.20%) |        1.10 s  →        1.41 s   (+27.62%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.59 ms →        5.58 ms  (-15.37%) |      19   →      23    (+21.05%) |      125.22 ms →      128.28 ms   (+2.45%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.84 ms →        4.92 ms  (-15.73%) |      19   →      23    (+21.05%) |      110.91 ms →      113.13 ms   (+2.01%) | 
- │ │ ├ sirius::Potential::generate                                     |      356.28 ms →      363.06 ms   (+1.90%) |      19   →      23    (+21.05%) |        6.77 s  →        8.35 s   (+23.36%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.85 ms →       42.88 ms  (+19.61%) |      19   →      23    (+21.05%) |      681.12 ms →      986.21 ms  (+44.79%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.03 ms →       13.91 ms (+176.55%) |      19   →      23    (+21.05%) |       95.54 ms →      319.84 ms (+234.77%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.42 ms →        5.91 ms   (+9.00%) |      19   →      23    (+21.05%) |      103.03 ms →      135.94 ms  (+31.94%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.68 ms   (+1.07%) |      19   →      23    (+21.05%) |       87.99 ms →      107.65 ms  (+22.35%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.68 ms   (+1.08%) |      19   →      23    (+21.05%) |       87.97 ms →      107.64 ms  (+22.36%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      797.70 μs →      778.88 μs   (-2.36%) |      38   →      46    (+21.05%) |       30.31 ms →       35.83 ms  (+18.20%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.62 ms →       45.03 ms   (+0.92%) |      19   →      23    (+21.05%) |      847.72 ms →        1.04 s   (+22.17%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.44 ms →       43.85 ms   (+0.94%) |      19   →      23    (+21.05%) |      825.38 ms →        1.01 s   (+22.19%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      682.20 μs →      679.14 μs   (-0.45%) |      38   →      46    (+21.05%) |       25.92 ms →       31.24 ms  (+20.51%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.17 ms →        4.58 ms   (+9.74%) |      19   →      23    (+21.05%) |       79.24 ms →      105.26 ms  (+32.84%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.83 ms →        3.64 ms   (-4.93%) |      19   →      23    (+21.05%) |       72.71 ms →       83.68 ms  (+15.08%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.00 ms →      268.52 ms   (-0.18%) |      19   →      23    (+21.05%) |        5.11 s  →        6.18 s   (+20.84%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      280.95 ns →      364.48 ns  (+29.73%) |      19   →      23    (+21.05%) |        5.34 μs →        8.38 μs  (+57.04%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.54 ms →       96.58 ms   (+0.05%) |      19   →      23    (+21.05%) |        1.83 s  →        2.22 s   (+21.11%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.54 ms →       96.58 ms   (+0.05%) |      19   →      23    (+21.05%) |        1.83 s  →        2.22 s   (+21.11%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.22 ms →       13.30 ms   (+0.62%) |      19   →      23    (+21.05%) |      251.11 ms →      305.87 ms  (+21.81%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.04 ms →       70.09 ms   (+0.06%) |      19   →      23    (+21.05%) |        1.33 s  →        1.61 s   (+21.13%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.65 ms →       12.56 ms   (-0.70%) |      19   →      23    (+21.05%) |      240.30 ms →      288.84 ms  (+20.20%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.93 ms →        4.60 ms  (+17.03%) |      19   →      23    (+21.05%) |       74.68 ms →      105.80 ms  (+41.67%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.68 ms →        4.63 ms   (-1.07%) |     133   →     161    (+21.05%) |      622.01 ms →      744.88 ms  (+19.75%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.58 ms →        4.62 ms   (+0.93%) |     133   →     161    (+21.05%) |      608.54 ms →      743.47 ms  (+22.17%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.62 ms   (+0.93%) |     133   →     161    (+21.05%) |      608.47 ms →      743.38 ms  (+22.17%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.97 ms →        4.98 ms   (+0.26%) |      57   →      69    (+21.05%) |      283.35 ms →      343.88 ms  (+21.36%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.96 ms →        4.94 ms   (-0.23%) |      57   →      69    (+21.05%) |      282.49 ms →      341.18 ms  (+20.78%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.56 ms   (+0.35%) |      19   →      23    (+21.05%) |       86.29 ms →      104.82 ms  (+21.48%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       76.07 μs →       75.39 μs   (-0.89%) |      19   →      23    (+21.05%) |        1.45 ms →        1.73 ms  (+19.97%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.04 μs →       70.51 μs   (-0.74%) |      19   →      23    (+21.05%) |        1.35 ms →        1.62 ms  (+20.15%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.13 ms →        5.24 ms   (+2.09%) |       2   →       2              |       10.27 ms →       10.48 ms   (+2.09%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.79 ms →        4.68 ms   (-2.33%) |       6   →       6              |       28.73 ms →       28.06 ms   (-2.33%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.79 ms →        4.59 ms   (-4.00%) |       6   →       6              |       28.71 ms →       27.56 ms   (-4.00%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.78 ms →        4.59 ms   (-3.98%) |       6   →       6              |       28.70 ms →       27.56 ms   (-3.98%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.18 ms →        4.99 ms   (-3.79%) |       3   →       3              |       15.55 ms →       14.97 ms   (-3.79%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.18 ms →        4.94 ms   (-4.65%) |       3   →       3              |       15.54 ms →       14.82 ms   (-4.65%) | 
  ├ sirius::Periodic_function|inner                                     |        4.88 ms →        4.60 ms   (-5.68%) |       2   →       2              |        9.76 ms →        9.20 ms   (-5.68%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.87 ms →        4.60 ms   (-5.57%) |       2   →       2              |        9.74 ms →        9.20 ms   (-5.57%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.87 ms →        4.60 ms   (-5.57%) |       2   →       2              |        9.74 ms →        9.20 ms   (-5.57%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.15 ms →        4.97 ms   (-3.39%) |       1   →       1              |        5.15 ms →        4.97 ms   (-3.39%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.14 ms →        4.97 ms   (-3.38%) |       1   →       1              |        5.14 ms →        4.97 ms   (-3.38%) | 
  └ sirius::finalize                                                    |      156.79 ms →      169.65 ms   (+8.20%) |       1   →       1              |      156.79 ms →      169.65 ms   (+8.20%) | 
  ====================================================================================================================================================================================================
```
