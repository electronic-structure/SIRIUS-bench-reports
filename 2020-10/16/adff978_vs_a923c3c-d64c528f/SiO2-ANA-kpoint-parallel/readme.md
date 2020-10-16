# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      135.27 s  →      133.18 s    (-1.54%) |       1   →       1              |      135.27 s  →      133.18 s    (-1.54%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.72 s    (-1.36%) |       1   →       1              |        2.75 s  →        2.72 s    (-1.36%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        3.08 s    (+2.98%) |       1   →       1              |        2.99 s  →        3.08 s    (+2.98%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        1.70 ms →       36.48 ms (+2047.23%) |       1   →       1              |        1.70 ms →       36.48 ms (+2047.23%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      155.06 ms →      240.77 ms  (+55.27%) |       1   →       1              |      155.06 ms →      240.77 ms  (+55.27%) | 
- │ │ ├ sirius::Atom_type::init                                         |       64.96 ms →      107.57 ms  (+65.59%) |       2   →       2              |      129.92 ms →      215.14 ms  (+65.59%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.04 ms →       25.55 ms   (+2.04%) |       1   →       1              |       25.04 ms →       25.55 ms   (+2.04%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.27 ms →        6.33 ms   (+0.83%) |       1   →       1              |        6.27 ms →        6.33 ms   (+0.83%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.72 ms →       19.18 ms   (+2.47%) |       1   →       1              |       18.72 ms →       19.18 ms   (+2.47%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.70 ms →       19.16 ms   (+2.47%) |       1   →       1              |       18.70 ms →       19.16 ms   (+2.47%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.15 ms   (+0.08%) |       1   →       1              |        4.15 ms →        4.15 ms   (+0.08%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.36 ms →        2.35 ms   (-0.74%) |       1   →       1              |        2.36 ms →        2.35 ms   (-0.74%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.56 μs →      102.78 μs   (-2.64%) |       1   →       1              |      105.56 μs →      102.78 μs   (-2.64%) | 
  │ └ sirius::Simulation_context::update                                |        2.79 s  →        2.76 s    (-1.27%) |       1   →       1              |        2.79 s  →        2.76 s    (-1.27%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.82 ms →       10.84 ms   (+0.25%) |       1   →       1              |       10.82 ms →       10.84 ms   (+0.25%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.41 ms →        4.42 ms   (+0.40%) |       1   →       1              |        4.41 ms →        4.42 ms   (+0.40%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.38 ms →        6.39 ms   (+0.14%) |       1   →       1              |        6.38 ms →        6.39 ms   (+0.14%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.36 ms →        6.37 ms   (+0.15%) |       1   →       1              |        6.36 ms →        6.37 ms   (+0.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.85 ms →        3.89 ms   (+1.04%) |       1   →       1              |        3.85 ms →        3.89 ms   (+1.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-1.19%) |       1   →       1              |        2.34 ms →        2.32 ms   (-1.19%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      102.11 μs →       99.28 μs   (-2.77%) |       1   →       1              |      102.11 μs →       99.28 μs   (-2.77%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.64 ms →       62.73 ms   (+0.14%) |       2   →       2              |      125.27 ms →      125.45 ms   (+0.14%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.16 ms   (+0.23%) |       2   →       2              |       10.29 ms →       10.32 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.84 ms →        4.47 ms   (-7.75%) |       1   →       1              |        4.84 ms →        4.47 ms   (-7.75%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.80 ms →       21.79 ms   (-0.04%) |       2   →       2              |       43.59 ms →       43.58 ms   (-0.04%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.00 ms →       14.81 ms   (-1.28%) |       2   →       2              |       30.00 ms →       29.62 ms   (-1.28%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.77 ms →       19.81 ms   (+0.20%) |       4   →       4              |       79.07 ms →       79.23 ms   (+0.20%) | 
  │   ├ sddk::Gvec::init                                                |      174.42 ms →      174.68 ms   (+0.15%) |       2   →       2              |      348.85 ms →      349.36 ms   (+0.15%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.61 ms →      131.90 ms   (+0.22%) |       2   →       2              |      263.22 ms →      263.80 ms   (+0.22%) | 
  │   ├ sddk::Gvec_shells                                               |      198.29 ms →      194.82 ms   (-1.75%) |       1   →       1              |      198.29 ms →      194.82 ms   (-1.75%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.33 ms   (+0.54%) |       1   →       1              |        1.33 ms →        1.33 ms   (+0.54%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.31 ms →      293.70 ms   (-0.20%) |       2   →       2              |      588.61 ms →      587.41 ms   (-0.20%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.96 ms →       36.06 ms   (+0.27%) |       1   →       1              |       35.96 ms →       36.06 ms   (+0.27%) | 
  │ ├ sirius::K_point::K_point                                          |        2.46 μs →        2.41 μs   (-1.98%) |       4   →       4              |        9.83 μs →        9.63 μs   (-1.98%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.86 ms →       35.96 ms   (+0.28%) |       1   →       1              |       35.86 ms →       35.96 ms   (+0.28%) | 
  │   └ sirius::K_point::initialize                                     |       35.78 ms →       35.86 ms   (+0.25%) |       1   →       1              |       35.78 ms →       35.86 ms   (+0.25%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.23 ms →       18.06 ms   (-0.95%) |       1   →       1              |       18.23 ms →       18.06 ms   (-0.95%) | 
  │     │ └ sddk::Gvec::init                                            |        8.20 ms →        8.10 ms   (-1.11%) |       1   →       1              |        8.20 ms →        8.10 ms   (-1.11%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.65 μs →        9.56 μs   (-0.85%) |       1   →       1              |        9.65 μs →        9.56 μs   (-0.85%) | 
  │     └ sirius::K_point::update                                       |       12.75 ms →       12.75 ms   (-0.00%) |       1   →       1              |       12.75 ms →       12.75 ms   (-0.00%) | 
  │       └ sirius::Beta_projectors                                     |        6.46 ms →        6.31 ms   (-2.24%) |       1   →       1              |        6.46 ms →        6.31 ms   (-2.24%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.88 ms →        3.70 ms   (-4.50%) |       1   →       1              |        3.88 ms →        3.70 ms   (-4.50%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.20 ms →        5.58 ms   (+7.30%) |       2   →       2              |       10.41 ms →       11.17 ms   (+7.30%) | 
  ├ sirius::Potential                                                   |      159.89 ms →      158.07 ms   (-1.14%) |       1   →       1              |      159.89 ms →      158.07 ms   (-1.14%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.89 ms →        6.46 ms   (+9.78%) |       6   →       6              |       35.32 ms →       38.77 ms   (+9.78%) | 
  │ └ sirius::Potential::update                                         |      123.80 ms →      118.50 ms   (-4.28%) |       1   →       1              |      123.80 ms →      118.50 ms   (-4.28%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.04 ms →      117.75 ms   (-4.30%) |       1   →       1              |      123.04 ms →      117.75 ms   (-4.30%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      115.84 ms →      109.14 ms   (-5.79%) |       1   →       1              |      115.84 ms →      109.14 ms   (-5.79%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.31 ms →        7.68 ms  (+21.65%) |       1   →       1              |        6.31 ms →        7.68 ms  (+21.65%) | 
  ├ sirius::Density                                                     |      136.50 ms →      136.27 ms   (-0.17%) |       1   →       1              |      136.50 ms →      136.27 ms   (-0.17%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.15 ms →        5.27 ms   (+2.30%) |       2   →       2              |       10.30 ms →       10.54 ms   (+2.30%) | 
  │ └ sirius::Density::update                                           |      125.93 ms →      125.46 ms   (-0.37%) |       1   →       1              |      125.93 ms →      125.46 ms   (-0.37%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.50 ms →      125.03 ms   (-0.37%) |       1   →       1              |      125.50 ms →      125.03 ms   (-0.37%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.74 μs →      102.29 μs   (-0.44%) |       1   →       1              |      102.74 μs →      102.29 μs   (-0.44%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      119.80 ms →      110.98 ms   (-7.36%) |       1   →       1              |      119.80 ms →      110.98 ms   (-7.36%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.13 ms →       13.49 ms (+162.90%) |       1   →       1              |        5.13 ms →       13.49 ms (+162.90%) | 
  ├ sirius::Density::initial_density                                    |      175.51 ms →      179.95 ms   (+2.53%) |       1   →       1              |      175.51 ms →      179.95 ms   (+2.53%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      123.11 ms →      109.53 ms  (-11.03%) |       1   →       1              |      123.11 ms →      109.53 ms  (-11.03%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.01 ms →       12.81 ms (+155.87%) |       2   →       2              |       10.02 ms →       25.63 ms (+155.87%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.73 ms →       12.53 ms  (+28.82%) |       1   →       1              |        9.73 ms →       12.53 ms  (+28.82%) | 
  ├ sirius::Potential::generate                                         |      597.65 ms →      597.14 ms   (-0.08%) |       1   →       1              |      597.65 ms →      597.14 ms   (-0.08%) | 
  │ ├ sirius::Potential::poisson                                        |      137.16 ms →      138.54 ms   (+1.00%) |       1   →       1              |      137.16 ms →      138.54 ms   (+1.00%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.24 ms →       19.46 ms (+271.60%) |       1   →       1              |        5.24 ms →       19.46 ms (+271.60%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.91 ms →       10.83 ms   (+9.23%) |       1   →       1              |        9.91 ms →       10.83 ms   (+9.23%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.82 ms   (-0.08%) |       1   →       1              |        9.82 ms →        9.82 ms   (-0.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →        9.81 ms   (-0.08%) |       1   →       1              |        9.82 ms →        9.81 ms   (-0.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      553.65 μs →      557.45 μs   (+0.69%) |       2   →       2              |        1.11 ms →        1.11 ms   (+0.69%) | 
  │ ├ sirius::Potential::xc                                             |       54.24 ms →       55.90 ms   (+3.07%) |       1   →       1              |       54.24 ms →       55.90 ms   (+3.07%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.75 ms →       53.52 ms   (+3.42%) |       1   →       1              |       51.75 ms →       53.52 ms   (+3.42%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.77 ms →        5.74 ms   (-0.55%) |       2   →       2              |       11.53 ms →       11.47 ms   (-0.55%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.14 ms →        5.75 ms  (+11.91%) |       1   →       1              |        5.14 ms →        5.75 ms  (+11.91%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.77 ms →        5.85 ms   (+1.43%) |       1   →       1              |        5.77 ms →        5.85 ms   (+1.43%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.78 ms →       93.40 ms   (+0.67%) |       1   →       1              |       92.78 ms →       93.40 ms   (+0.67%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      305.17 ms →      300.89 ms   (-1.40%) |       1   →       1              |      305.17 ms →      300.89 ms   (-1.40%) | 
  ├ sirius::Hamiltonian0                                                |        8.43 ms →        8.41 ms   (-0.30%) |       1   →       1              |        8.43 ms →        8.41 ms   (-0.30%) | 
  │ ├ sirius::Local_operator                                            |        8.07 ms →        8.06 ms   (-0.09%) |       1   →       1              |        8.07 ms →        8.06 ms   (-0.09%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.78 ms   (+0.11%) |       1   →       1              |        4.77 ms →        4.78 ms   (+0.11%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.36 ms   (-0.13%) |       1   →       1              |        2.36 ms →        2.36 ms   (-0.13%) | 
  │ ├ sirius::Non_local_operator                                        |       63.89 μs →       62.34 μs   (-2.42%) |       2   →       2              |      127.78 μs →      124.69 μs   (-2.42%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.38 μs →       94.49 μs   (-3.95%) |       1   →       1              |       98.38 μs →       94.49 μs   (-3.95%) | 
  │ └ sirius::Q_operator::initialize                                    |       78.88 μs →       75.30 μs   (-4.55%) |       1   →       1              |       78.88 μs →       75.30 μs   (-4.55%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.88 s  →        1.85 s    (-1.35%) |       1   →       1              |        1.88 s  →        1.85 s    (-1.35%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.09 ms →       18.69 ms   (+3.30%) |       1   →       1              |       18.09 ms →       18.69 ms   (+3.30%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      183.82 μs →      188.43 μs   (+2.51%) |       1   →       1              |      183.82 μs →      188.43 μs   (+2.51%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       17.90 ms →       18.50 ms   (+3.32%) |       1   →       1              |       17.90 ms →       18.50 ms   (+3.32%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.86 s  →        1.83 s    (-1.40%) |       1   →       1              |        1.86 s  →        1.83 s    (-1.40%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      131.12 ms →      126.45 ms   (-3.56%) |       4   →       4              |      524.48 ms →      505.81 ms   (-3.56%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.26 ms →       54.24 ms   (+1.85%) |       1   →       1              |       53.26 ms →       54.24 ms   (+1.85%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.60 ms →       21.56 ms   (-0.19%) |       1   →       1              |       21.60 ms →       21.56 ms   (-0.19%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      640.49 ms →      634.43 ms   (-0.95%) |       1   →       1              |      640.49 ms →      634.43 ms   (-0.95%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      300.93 ms →      297.37 ms   (-1.18%) |       1   →       1              |      300.93 ms →      297.37 ms   (-1.18%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.20 μs →        2.92 μs   (-8.75%) |       1   →       1              |        3.20 μs →        2.92 μs   (-8.75%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.40 μs →        2.03 μs  (-15.22%) |       1   →       1              |        2.40 μs →        2.03 μs  (-15.22%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      457.00 ns →      358.00 ns  (-21.66%) |       1   →       1              |      457.00 ns →      358.00 ns  (-21.66%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      510.00 ns →      606.00 ns  (+18.82%) |       1   →       1              |      510.00 ns →      606.00 ns  (+18.82%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (-0.00%) |       1   →       1              |        9.22 ms →        9.22 ms   (-0.00%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.21 ms →      120.55 ms   (-0.55%) |       1   →       1              |      121.21 ms →      120.55 ms   (-0.55%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.55 ms →      103.63 ms   (-0.88%) |       2   →       2              |      209.09 ms →      207.26 ms   (-0.88%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.15 ms →       40.10 ms   (-0.12%) |       2   →       2              |       80.30 ms →       80.20 ms   (-0.12%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.61 ms →       39.57 ms   (-0.12%) |       2   →       2              |       79.22 ms →       79.13 ms   (-0.12%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.50 ns →       39.50 ns (+102.56%) |       2   →       2              |       39.00 ns →       79.00 ns (+102.56%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.15 ms →       39.09 ms   (-0.15%) |       2   →       2              |       78.30 ms →       78.18 ms   (-0.15%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       18.50 ns →       24.00 ns  (+29.73%) |       2   →       2              |       37.00 ns →       48.00 ns  (+29.73%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.87 ms →       56.83 ms   (-0.07%) |       1   →       1              |       56.87 ms →       56.83 ms   (-0.07%) | 
  │ │ └ sddk::wf_trans                                                  |       30.76 ms →       30.74 ms   (-0.07%) |       1   →       1              |       30.76 ms →       30.74 ms   (-0.07%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.76 ms →       30.74 ms   (-0.07%) |       1   →       1              |       30.76 ms →       30.74 ms   (-0.07%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      561.00 ns →      587.00 ns   (+4.63%) |       1   →       1              |      561.00 ns →      587.00 ns   (+4.63%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      125.47 s  →      123.37 s    (-1.68%) |       1   →       1              |      125.47 s  →      123.37 s    (-1.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.90 ms →        5.90 ms   (+0.02%) |      19   →      19              |      112.05 ms →      112.08 ms   (+0.02%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.79 s  →        4.56 s    (-4.91%) |      26   →      27     (+3.85%) |      124.55 s  →      123.00 s    (-1.25%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.49 ms →        5.24 ms  (+16.54%) |      26   →      27     (+3.85%) |      116.85 ms →      141.42 ms  (+21.02%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.13 ms →        4.88 ms  (+18.23%) |      26   →      27     (+3.85%) |      107.26 ms →      131.69 ms  (+22.78%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.02 ms →      954.69 μs   (-6.41%) |      26   →      27     (+3.85%) |       26.52 ms →       25.78 ms   (-2.81%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.21 ms →        3.04 ms  (+37.28%) |      26   →      27     (+3.85%) |       57.50 ms →       81.97 ms  (+42.56%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.44 μs →       64.87 μs   (+0.66%) |      52   →      54     (+3.85%) |        3.35 ms →        3.50 ms   (+4.53%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.32 μs →       86.29 μs   (-2.30%) |      26   →      27     (+3.85%) |        2.30 ms →        2.33 ms   (+1.46%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       79.43 μs →       76.44 μs   (-3.76%) |      26   →      27     (+3.85%) |        2.07 ms →        2.06 ms   (-0.06%) | 
  │ │ ├ sirius::Band::solve                                             |        2.80 s  →        2.58 s    (-8.07%) |      26   →      27     (+3.85%) |       72.87 s  →       69.57 s    (-4.54%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      151.52 μs →      149.65 μs   (-1.23%) |      26   →      27     (+3.85%) |        3.94 ms →        4.04 ms   (+2.57%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      144.42 μs →      143.04 μs   (-0.96%) |      26   →      27     (+3.85%) |        3.75 ms →        3.86 ms   (+2.85%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.19 μs →        4.81 μs   (-7.36%) |      26   →      27     (+3.85%) |      135.00 μs →      129.88 μs   (-3.79%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        2.43 s    (-7.31%) |      26   →      27     (+3.85%) |       68.16 s  →       65.61 s    (-3.75%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.93 ms →       92.78 ms   (-4.28%) |      26   →      27     (+3.85%) |        2.52 s  →        2.51 s    (-0.60%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.83 ms →        7.29 ms   (-6.92%) |     156   →     162     (+3.85%) |        1.22 s  →        1.18 s    (-3.34%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.92 ms →        5.92 ms   (+0.01%) |      26   →      27     (+3.85%) |      153.80 ms →      159.73 ms   (+3.86%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.40 μs →      350.65 μs   (+0.07%) |      26   →      27     (+3.85%) |        9.11 ms →        9.47 ms   (+3.92%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.29 ms →        2.29 ms   (-0.09%) |      52   →      54     (+3.85%) |      119.32 ms →      123.79 ms   (+3.75%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.48 s  →        2.30 s    (-7.55%) |      26   →      27     (+3.85%) |       64.56 s  →       61.98 s    (-4.00%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      130.45 ms →      133.50 ms   (+2.34%) |     271   →     274     (+1.11%) |       35.35 s  →       36.58 s    (+3.47%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       52.04 ms →       54.35 ms   (+4.43%) |     271   →     274     (+1.11%) |       14.10 s  →       14.89 s    (+5.59%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.88 μs →        1.86 μs   (-1.16%) |     271   →     274     (+1.11%) |      508.63 μs →      508.28 μs   (-0.07%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.61 μs →        1.55 μs   (-3.80%) |     271   →     274     (+1.11%) |      437.37 μs →      425.41 μs   (-2.73%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      349.49 ns →      408.24 ns  (+16.81%) |     271   →     274     (+1.11%) |       94.71 μs →      111.86 μs  (+18.10%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      407.67 ns →      460.87 ns  (+13.05%) |     271   →     274     (+1.11%) |      110.48 μs →      126.28 μs  (+14.30%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.43 ms →        7.45 ms   (+0.23%) |     271   →     274     (+1.11%) |        2.01 s  →        2.04 s    (+1.34%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.12 ms →       23.98 ms   (-0.57%) |     271   →     274     (+1.11%) |        6.54 s  →        6.57 s    (+0.53%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.42 ms →       23.85 ms   (+1.84%) |     542   →     548     (+1.11%) |       12.69 s  →       13.07 s    (+2.97%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.90 ms →       35.00 ms   (+0.28%) |     271   →     274     (+1.11%) |        9.46 s  →        9.59 s    (+1.39%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.06 ms →        6.07 ms   (+0.24%) |     516   →     521     (+0.97%) |        3.13 s  →        3.16 s    (+1.21%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       71.15 ns →       57.06 ns  (-19.80%) |     516   →     521     (+0.97%) |       36.71 μs →       29.73 μs  (-19.03%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.95 ms →        4.96 ms   (+0.33%) |     516   →     521     (+0.97%) |        2.55 s  →        2.58 s    (+1.30%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.89 ns →       37.23 ns  (-29.60%) |     516   →     521     (+0.97%) |       27.29 μs →       19.40 μs  (-28.92%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      622.81 μs →      643.49 μs   (+3.32%) |     271   →     274     (+1.11%) |      168.78 ms →      176.32 ms   (+4.46%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.76 ms →       10.04 ms   (+2.89%) |     271   →     274     (+1.11%) |        2.65 s  →        2.75 s    (+4.03%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.35 ms →       14.15 ms   (-1.39%) |     245   →     247     (+0.82%) |        3.52 s  →        3.50 s    (-0.59%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.78 ms →        4.72 ms   (-1.40%) |     735   →     741     (+0.82%) |        3.52 s  →        3.50 s    (-0.59%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.50 ms →       10.12 ms   (-3.62%) |     271   →     274     (+1.11%) |        2.85 s  →        2.77 s    (-2.55%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.23 ms →        9.93 ms   (-3.01%) |     271   →     274     (+1.11%) |        2.77 s  →        2.72 s    (-1.93%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       50.40 ns →       26.65 ns  (-47.13%) |     271   →     274     (+1.11%) |       13.66 μs →        7.30 μs  (-46.55%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.12 ms →        8.81 ms   (-3.35%) |     271   →     274     (+1.11%) |        2.47 s  →        2.41 s    (-2.28%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       71.10 ns →       49.03 ns  (-31.05%) |     271   →     274     (+1.11%) |       19.27 μs →       13.43 μs  (-30.29%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       34.32 ms →       18.25 ms  (-46.82%) |     271   →     274     (+1.11%) |        9.30 s  →        5.00 s   (-46.24%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.79 ms →       12.90 ms   (-6.46%) |     262   →     263     (+0.38%) |        3.61 s  →        3.39 s    (-6.11%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.44 ms →       11.36 ms   (-8.67%) |     252   →     255     (+1.19%) |        3.14 s  →        2.90 s    (-7.58%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.22 ms →        5.68 ms   (-8.67%) |     504   →     510     (+1.19%) |        3.13 s  →        2.90 s    (-7.58%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.63 ms →        1.69 ms   (+3.68%) |     252   →     255     (+1.19%) |      410.36 ms →      430.51 ms   (+4.91%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       75.01 ms →       52.05 ms  (-30.62%) |      53   →      89    (+67.92%) |        3.98 s  →        4.63 s   (+16.51%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.46 ms →       30.41 ms  (-38.51%) |      80   →     151    (+88.75%) |        3.96 s  →        4.59 s   (+16.06%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.97 ms →       21.56 ms  (-41.70%) |     107   →     213    (+99.07%) |        3.96 s  →        4.59 s   (+16.06%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      662.19 ns →      391.63 ns  (-40.86%) |      26   →      27     (+3.85%) |       17.22 μs →       10.57 μs  (-38.58%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.61 μs →       29.75 μs   (-2.82%) |      26   →      27     (+3.85%) |      795.97 μs →      803.30 μs   (+0.92%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      599.55 μs →      602.06 μs   (+0.42%) |      26   →      27     (+3.85%) |       15.59 ms →       16.26 ms   (+4.28%) | 
  │ │ ├ sirius::Density::generate                                       |      776.25 ms →      777.18 ms   (+0.12%) |      26   →      27     (+3.85%) |       20.18 s  →       20.98 s    (+3.97%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      403.05 ms →      400.21 ms   (-0.70%) |      26   →      27     (+3.85%) |       10.48 s  →       10.81 s    (+3.12%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.43 μs →        8.04 μs   (-4.63%) |      26   →      27     (+3.85%) |      219.29 μs →      217.18 μs   (-0.96%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.94 μs →        7.55 μs   (-4.81%) |      26   →      27     (+3.85%) |      206.35 μs →      203.98 μs   (-1.15%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.63 ms →      100.21 ms   (-0.42%) |      26   →      27     (+3.85%) |        2.62 s  →        2.71 s    (+3.41%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.44 μs →        7.53 μs   (+1.27%) |      26   →      27     (+3.85%) |      193.40 μs →      203.40 μs   (+5.17%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.13 ms   (+0.10%) |      26   →      27     (+3.85%) |      185.12 ms →      192.43 ms   (+3.95%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.60 ms →       91.18 ms   (-0.45%) |      26   →      27     (+3.85%) |        2.38 s  →        2.46 s    (+3.38%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      682.50 ns →      547.19 ns  (-19.83%) |      26   →      27     (+3.85%) |       17.74 μs →       14.77 μs  (-16.74%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.74 ms →      162.61 ms   (-0.69%) |      26   →      27     (+3.85%) |        4.26 s  →        4.39 s    (+3.13%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.43%) |      26   →      27     (+3.85%) |       42.91 ms →       44.37 ms   (+3.40%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.41 ms →       88.31 ms   (-0.12%) |      26   →      27     (+3.85%) |        2.30 s  →        2.38 s    (+3.72%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.19 ms →       88.08 ms   (-0.13%) |      26   →      27     (+3.85%) |        2.29 s  →        2.38 s    (+3.72%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.02 ms →      276.43 ms   (-1.28%) |      26   →      27     (+3.85%) |        7.28 s  →        7.46 s    (+2.51%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.02 ms →      276.43 ms   (-1.28%) |      26   →      27     (+3.85%) |        7.28 s  →        7.46 s    (+2.51%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       25.95 ms →       24.38 ms   (-6.05%) |      26   →      27     (+3.85%) |      674.78 ms →      658.33 ms   (-2.44%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.07 ms →      227.86 ms   (+0.79%) |      26   →      27     (+3.85%) |        5.88 s  →        6.15 s    (+4.67%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.81 ms →       23.01 ms  (-14.19%) |      26   →      27     (+3.85%) |      697.07 ms →      621.16 ms  (-10.89%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       83.57 ms →       80.49 ms   (-3.69%) |      26   →      27     (+3.85%) |        2.17 s  →        2.17 s    (+0.02%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.03 ms →       16.47 ms (+173.07%) |      26   →      27     (+3.85%) |      156.79 ms →      444.61 ms (+183.57%) | 
  │ │ ├ sirius::Density::mix                                            |      217.14 ms →      214.43 ms   (-1.25%) |      26   →      27     (+3.85%) |        5.65 s  →        5.79 s    (+2.55%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      956.25 μs →      956.33 μs   (+0.01%) |      26   →      27     (+3.85%) |       24.86 ms →       25.82 ms   (+3.86%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.61 ms →       10.33 ms   (-2.61%) |     334   →     349     (+4.49%) |        3.54 s  →        3.61 s    (+1.76%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.35 ms →        9.92 ms   (-4.11%) |     334   →     349     (+4.49%) |        3.46 s  →        3.46 s    (+0.20%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.35 ms →        9.92 ms   (-4.11%) |     334   →     349     (+4.49%) |        3.46 s  →        3.46 s    (+0.19%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.44 ms →        6.38 ms   (-0.93%) |      26   →      27     (+3.85%) |      167.32 ms →      172.13 ms   (+2.88%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.59 ms →        5.54 ms   (-0.80%) |      26   →      27     (+3.85%) |      145.23 ms →      149.60 ms   (+3.01%) | 
  │ │ ├ sirius::Potential::generate                                     |      586.48 ms →      579.40 ms   (-1.21%) |      26   →      27     (+3.85%) |       15.25 s  →       15.64 s    (+2.59%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.83 ms →      138.07 ms   (+0.17%) |      26   →      27     (+3.85%) |        3.58 s  →        3.73 s    (+4.02%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.15 ms →       19.31 ms (+274.91%) |      26   →      27     (+3.85%) |      133.92 ms →      521.38 ms (+289.33%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.34 ms →       10.26 ms   (-0.77%) |      26   →      27     (+3.85%) |      268.86 ms →      277.06 ms   (+3.05%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.99 ms →        9.97 ms   (-0.29%) |      26   →      27     (+3.85%) |      259.87 ms →      269.07 ms   (+3.54%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.99 ms →        9.97 ms   (-0.29%) |      26   →      27     (+3.85%) |      259.85 ms →      269.06 ms   (+3.54%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      553.99 μs →      557.76 μs   (+0.68%) |      52   →      54     (+3.85%) |       28.81 ms →       30.12 ms   (+4.55%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.98 ms →       48.95 ms   (-0.06%) |      26   →      27     (+3.85%) |        1.27 s  →        1.32 s    (+3.78%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.56 ms →       46.61 ms   (+0.11%) |      26   →      27     (+3.85%) |        1.21 s  →        1.26 s    (+3.96%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.09 ms →        2.98 ms   (-3.45%) |      52   →      54     (+3.85%) |      160.63 ms →      161.06 ms   (+0.27%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.29 ms →        5.43 ms   (+2.72%) |      26   →      27     (+3.85%) |      137.51 ms →      146.68 ms   (+6.67%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.44 ms →        6.44 ms   (+0.11%) |      26   →      27     (+3.85%) |      167.34 ms →      173.96 ms   (+3.96%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.00 ms →       90.89 ms   (-0.12%) |      26   →      27     (+3.85%) |        2.37 s  →        2.45 s    (+3.72%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      299.78 ms →      292.63 ms   (-2.39%) |      26   →      27     (+3.85%) |        7.79 s  →        7.90 s    (+1.37%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      283.76 ms →      283.01 ms   (-0.26%) |      26   →      27     (+3.85%) |        7.38 s  →        7.64 s    (+3.57%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      283.76 ms →      283.01 ms   (-0.26%) |      26   →      27     (+3.85%) |        7.38 s  →        7.64 s    (+3.57%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       29.10 ms →       27.17 ms   (-6.61%) |      26   →      27     (+3.85%) |      756.54 ms →      733.69 ms   (-3.02%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.18 ms →      227.81 ms   (+1.62%) |      26   →      27     (+3.85%) |        5.83 s  →        6.15 s    (+5.53%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       26.64 ms →       24.25 ms   (-8.97%) |      26   →      27     (+3.85%) |      692.61 ms →      654.72 ms   (-5.47%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.17 ms →        5.45 ms   (+5.48%) |      26   →      27     (+3.85%) |      134.36 ms →      147.17 ms   (+9.53%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.10 ms →       10.25 ms   (+1.50%) |     182   →     189     (+3.85%) |        1.84 s  →        1.94 s    (+5.41%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.81 ms   (-0.04%) |     182   →     189     (+3.85%) |        1.79 s  →        1.85 s    (+3.80%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →        9.81 ms   (-0.04%) |     182   →     189     (+3.85%) |        1.79 s  →        1.85 s    (+3.80%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.88 ms →       10.56 ms   (-2.93%) |      78   →      81     (+3.85%) |      848.55 ms →      855.39 ms   (+0.81%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.62 ms →       10.16 ms   (-4.35%) |      78   →      81     (+3.85%) |      828.61 ms →      823.03 ms   (-0.67%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.27 ms →        9.96 ms   (-3.08%) |      26   →      27     (+3.85%) |      267.09 ms →      268.81 ms   (+0.65%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      111.38 μs →      109.87 μs   (-1.36%) |      26   →      27     (+3.85%) |        2.90 ms →        2.97 ms   (+2.44%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.12 μs →      105.03 μs   (-1.03%) |      26   →      27     (+3.85%) |        2.76 ms →        2.84 ms   (+2.77%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.07 ms   (-0.85%) |       2   →       2              |       10.24 ms →       10.15 ms   (-0.85%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.08 ms →       10.51 ms   (+4.24%) |       6   →       6              |       60.50 ms →       63.06 ms   (+4.24%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.07 ms →       10.50 ms   (+4.24%) |       6   →       6              |       60.43 ms →       62.99 ms   (+4.24%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.07 ms →       10.50 ms   (+4.24%) |       6   →       6              |       60.43 ms →       62.99 ms   (+4.24%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.87 ms →       10.77 ms   (-0.95%) |       3   →       3              |       32.61 ms →       32.30 ms   (-0.95%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.86 ms →       10.72 ms   (-1.35%) |       3   →       3              |       32.58 ms →       32.15 ms   (-1.35%) | 
  ├ sirius::Periodic_function|inner                                     |       10.03 ms →       10.33 ms   (+2.98%) |       2   →       2              |       20.06 ms →       20.66 ms   (+2.98%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms →       10.32 ms   (+2.98%) |       2   →       2              |       20.05 ms →       20.64 ms   (+2.98%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms →       10.32 ms   (+2.98%) |       2   →       2              |       20.04 ms →       20.64 ms   (+2.98%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.91 ms →       10.77 ms   (-1.27%) |       1   →       1              |       10.91 ms →       10.77 ms   (-1.27%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.90 ms →       10.76 ms   (-1.25%) |       1   →       1              |       10.90 ms →       10.76 ms   (-1.25%) | 
+ └ sirius::finalize                                                    |      220.35 ms →      187.57 ms  (-14.87%) |       1   →       1              |      220.35 ms →      187.57 ms  (-14.87%) | 
  ====================================================================================================================================================================================================
```
