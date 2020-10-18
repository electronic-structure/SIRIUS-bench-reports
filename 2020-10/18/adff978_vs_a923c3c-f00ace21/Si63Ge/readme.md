# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.82 s  →       72.66 s    (+1.18%) |       1   →       1              |       71.82 s  →       72.66 s    (+1.18%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.90 s    (+1.35%) |       1   →       1              |        2.86 s  →        2.90 s    (+1.35%) | 
  ├ sirius::Simulation_context::initialize                              |        3.84 s  →        3.86 s    (+0.64%) |       1   →       1              |        3.84 s  →        3.86 s    (+0.64%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       51.72 ms →       21.60 ms  (-58.25%) |       1   →       1              |       51.72 ms →       21.60 ms  (-58.25%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      172.34 ms →      137.02 ms  (-20.49%) |       1   →       1              |      172.34 ms →      137.02 ms  (-20.49%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       76.46 ms →       58.99 ms  (-22.85%) |       2   →       2              |      152.93 ms →      117.98 ms  (-22.85%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.31 ms →       18.95 ms   (-1.89%) |       1   →       1              |       19.31 ms →       18.95 ms   (-1.89%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.98 ms →        5.20 ms   (+4.50%) |       1   →       1              |        4.98 ms →        5.20 ms   (+4.50%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.26 ms →       13.66 ms   (-4.20%) |       1   →       1              |       14.26 ms →       13.66 ms   (-4.20%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.20 ms →       13.59 ms   (-4.26%) |       1   →       1              |       14.20 ms →       13.59 ms   (-4.26%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.74 ms   (+0.34%) |       1   →       1              |        2.73 ms →        2.74 ms   (+0.34%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      495.78 μs →        2.45 ms (+394.63%) |       1   →       1              |      495.78 μs →        2.45 ms (+394.63%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.18 μs →       19.19 μs  (+18.64%) |       1   →       1              |       16.18 μs →       19.19 μs  (+18.64%) | 
  │ └ sirius::Simulation_context::update                                |        3.51 s  →        3.65 s    (+3.83%) |       1   →       1              |        3.51 s  →        3.65 s    (+3.83%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.99 ms →        6.82 ms   (-2.50%) |       1   →       1              |        6.99 ms →        6.82 ms   (-2.50%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.47 ms   (-4.65%) |       1   →       1              |        3.64 ms →        3.47 ms   (-4.65%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.30 ms   (+0.78%) |       1   →       1              |        3.28 ms →        3.30 ms   (+0.78%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.25 ms   (+0.62%) |       1   →       1              |        3.23 ms →        3.25 ms   (+0.62%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.72 ms   (+0.47%) |       1   →       1              |        2.71 ms →        2.72 ms   (+0.47%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      490.95 μs →      495.38 μs   (+0.90%) |       1   →       1              |      490.95 μs →      495.38 μs   (+0.90%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.95 μs →       14.82 μs   (+6.25%) |       1   →       1              |       13.95 μs →       14.82 μs   (+6.25%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.81 ms →      212.56 ms   (-0.12%) |       2   →       2              |      425.61 ms →      425.11 ms   (-0.12%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.27 ms →       15.29 ms   (+0.17%) |       2   →       2              |       30.54 ms →       30.59 ms   (+0.17%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.27 ms   (+0.06%) |       1   →       1              |       13.26 ms →       13.27 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.31 ms →       56.83 ms   (+0.92%) |       2   →       2              |      112.62 ms →      113.66 ms   (+0.92%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.23 ms →       45.17 ms   (-0.14%) |       2   →       2              |       90.46 ms →       90.33 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.35 ms →       60.37 ms   (+0.04%) |       4   →       4              |      241.41 ms →      241.50 ms   (+0.04%) | 
  │   ├ sddk::Gvec::init                                                |       93.67 ms →       93.13 ms   (-0.58%) |       2   →       2              |      187.35 ms →      186.26 ms   (-0.58%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.84 ms →       69.59 ms   (-0.36%) |       2   →       2              |      139.69 ms →      139.19 ms   (-0.36%) | 
  │   ├ sddk::Gvec_shells                                               |       94.00 ms →       92.36 ms   (-1.75%) |       1   →       1              |       94.00 ms →       92.36 ms   (-1.75%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.94 ms   (+0.11%) |       1   →       1              |        1.94 ms →        1.94 ms   (+0.11%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      602.48 ms →      667.11 ms  (+10.73%) |       2   →       2              |        1.20 s  →        1.33 s   (+10.73%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      146.48 ms →       28.24 ms  (-80.72%) |       1   →       1              |      146.48 ms →       28.24 ms  (-80.72%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.60 μs →        1.23 μs  (-23.66%) |       4   →       4              |        6.42 μs →        4.90 μs  (-23.66%) | 
+ │ └ sirius::K_point_set::initialize                                   |      146.40 ms →       28.16 ms  (-80.76%) |       1   →       1              |      146.40 ms →       28.16 ms  (-80.76%) | 
  │   └ sirius::K_point::initialize                                     |       28.29 ms →       27.89 ms   (-1.40%) |       1   →       1              |       28.29 ms →       27.89 ms   (-1.40%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.10 ms →       10.89 ms   (-1.89%) |       1   →       1              |       11.10 ms →       10.89 ms   (-1.89%) | 
  │     │ └ sddk::Gvec::init                                            |        4.96 ms →        4.94 ms   (-0.33%) |       1   →       1              |        4.96 ms →        4.94 ms   (-0.33%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        8.91 μs →        7.16 μs  (-19.63%) |       1   →       1              |        8.91 μs →        7.16 μs  (-19.63%) | 
  │     └ sirius::K_point::update                                       |       14.29 ms →       14.15 ms   (-0.97%) |       1   →       1              |       14.29 ms →       14.15 ms   (-0.97%) | 
  │       └ sirius::Beta_projectors                                     |       10.33 ms →       10.17 ms   (-1.56%) |       1   →       1              |       10.33 ms →       10.17 ms   (-1.56%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.37 ms →        8.23 ms   (-1.64%) |       1   →       1              |        8.37 ms →        8.23 ms   (-1.64%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.57 ms   (+0.74%) |       2   →       2              |        5.11 ms →        5.14 ms   (+0.74%) | 
  ├ sirius::Potential                                                   |       55.75 ms →       53.17 ms   (-4.64%) |       1   →       1              |       55.75 ms →       53.17 ms   (-4.64%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.95 ms →        2.97 ms   (+0.57%) |       6   →       6              |       17.69 ms →       17.79 ms   (+0.57%) | 
  │ └ sirius::Potential::update                                         |       37.49 ms →       34.86 ms   (-7.01%) |       1   →       1              |       37.49 ms →       34.86 ms   (-7.01%) | 
  │   └ sirius::Potential::generate_local_potential                     |       37.06 ms →       34.42 ms   (-7.12%) |       1   →       1              |       37.06 ms →       34.42 ms   (-7.12%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       32.66 ms →       29.96 ms   (-8.27%) |       1   →       1              |       32.66 ms →       29.96 ms   (-8.27%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        3.85 ms →        3.90 ms   (+1.48%) |       1   →       1              |        3.85 ms →        3.90 ms   (+1.48%) | 
  ├ sirius::Density                                                     |       42.72 ms →       39.32 ms   (-7.96%) |       1   →       1              |       42.72 ms →       39.32 ms   (-7.96%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.84 ms   (+0.32%) |       2   →       2              |        5.66 ms →        5.68 ms   (+0.32%) | 
  │ └ sirius::Density::update                                           |       36.92 ms →       33.50 ms   (-9.25%) |       1   →       1              |       36.92 ms →       33.50 ms   (-9.25%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.63 ms →       33.20 ms   (-9.36%) |       1   →       1              |       36.63 ms →       33.20 ms   (-9.36%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.35 μs →       78.87 μs   (+0.66%) |       1   →       1              |       78.35 μs →       78.87 μs   (+0.66%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       33.27 ms →       29.88 ms  (-10.21%) |       1   →       1              |       33.27 ms →       29.88 ms  (-10.21%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        2.93 ms →        2.92 ms   (-0.34%) |       1   →       1              |        2.93 ms →        2.92 ms   (-0.34%) | 
  ├ sirius::Density::initial_density                                    |       65.66 ms →       62.97 ms   (-4.09%) |       1   →       1              |       65.66 ms →       62.97 ms   (-4.09%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       37.61 ms →       34.45 ms   (-8.41%) |       1   →       1              |       37.61 ms →       34.45 ms   (-8.41%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.46 ms →        4.36 ms   (-2.21%) |       2   →       2              |        8.92 ms →        8.72 ms   (-2.21%) | 
- │ └ sirius::Periodic_function::integrate                              |        5.34 ms →        6.13 ms  (+14.84%) |       1   →       1              |        5.34 ms →        6.13 ms  (+14.84%) | 
  ├ sirius::Potential::generate                                         |      373.30 ms →      369.68 ms   (-0.97%) |       1   →       1              |      373.30 ms →      369.68 ms   (-0.97%) | 
  │ ├ sirius::Potential::poisson                                        |       45.55 ms →       41.42 ms   (-9.08%) |       1   →       1              |       45.55 ms →       41.42 ms   (-9.08%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.66 ms →        2.92 ms  (-20.29%) |       1   →       1              |        3.66 ms →        2.92 ms  (-20.29%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.64 ms →        5.64 ms  (+21.70%) |       1   →       1              |        4.64 ms →        5.64 ms  (+21.70%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.64 ms   (+0.22%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.22%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.62 ms →        4.63 ms   (+0.19%) |       1   →       1              |        4.62 ms →        4.63 ms   (+0.19%) | 
  │ ├ sirius::Periodic_function::add                                    |      796.40 μs →      816.83 μs   (+2.57%) |       2   →       2              |        1.59 ms →        1.63 ms   (+2.57%) | 
  │ ├ sirius::Potential::xc                                             |       51.57 ms →       51.73 ms   (+0.30%) |       1   →       1              |       51.57 ms →       51.73 ms   (+0.30%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.40 ms →       50.57 ms   (+0.34%) |       1   →       1              |       50.40 ms →       50.57 ms   (+0.34%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.59 ms →        2.56 ms   (-1.12%) |       2   →       2              |        5.18 ms →        5.12 ms   (-1.12%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.05 ms →        4.38 ms   (+7.93%) |       1   →       1              |        4.05 ms →        4.38 ms   (+7.93%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.85 ms →        3.94 ms   (+2.50%) |       1   →       1              |        3.85 ms →        3.94 ms   (+2.50%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.32 ms →      269.58 ms   (+0.10%) |       1   →       1              |      269.32 ms →      269.58 ms   (+0.10%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      314.00 ns →      222.00 ns  (-29.30%) |       1   →       1              |      314.00 ns →      222.00 ns  (-29.30%) | 
  ├ sirius::Hamiltonian0                                                |        6.76 ms →        7.44 ms   (+9.95%) |       1   →       1              |        6.76 ms →        7.44 ms   (+9.95%) | 
  │ ├ sirius::Local_operator                                            |        6.31 ms →        6.87 ms   (+9.02%) |       1   →       1              |        6.31 ms →        6.87 ms   (+9.02%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.74 ms   (+0.06%) |       1   →       1              |        2.74 ms →        2.74 ms   (+0.06%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.81 ms →        3.30 ms  (+17.47%) |       1   →       1              |        2.81 ms →        3.30 ms  (+17.47%) | 
- │ ├ sirius::Non_local_operator                                        |       71.06 μs →      106.14 μs  (+49.38%) |       2   →       2              |      142.11 μs →      212.28 μs  (+49.38%) | 
- │ ├ sirius::D_operator::initialize                                    |      139.52 μs →      157.87 μs  (+13.16%) |       1   →       1              |      139.52 μs →      157.87 μs  (+13.16%) | 
+ │ └ sirius::Q_operator::initialize                                    |      106.36 μs →       95.68 μs  (-10.05%) |       1   →       1              |      106.36 μs →       95.68 μs  (-10.05%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.29 s    (+0.25%) |       1   →       1              |        1.29 s  →        1.29 s    (+0.25%) | 
- │ ├ sirius::Hamiltonian_k                                             |       51.33 ms →       83.59 ms  (+62.84%) |       1   →       1              |       51.33 ms →       83.59 ms  (+62.84%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      372.30 μs →      359.94 μs   (-3.32%) |       1   →       1              |      372.30 μs →      359.94 μs   (-3.32%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       50.95 ms →       83.22 ms  (+63.33%) |       1   →       1              |       50.95 ms →       83.22 ms  (+63.33%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.21 s    (-2.34%) |       1   →       1              |        1.24 s  →        1.21 s    (-2.34%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       80.44 ms →      109.78 ms  (+36.47%) |       4   →       4              |      321.77 ms →      439.13 ms  (+36.47%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.00 ms →       37.45 ms  (-20.32%) |       1   →       1              |       47.00 ms →       37.45 ms  (-20.32%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.99 ms →        6.45 ms  (-19.30%) |       1   →       1              |        7.99 ms →        6.45 ms  (-19.30%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      314.09 ms →      512.53 ms  (+63.18%) |       1   →       1              |      314.09 ms →      512.53 ms  (+63.18%) | 
- │ │ │ ├ sirius::Local_operator::apply_h                               |      246.71 ms →      441.19 ms  (+78.83%) |       1   →       1              |      246.71 ms →      441.19 ms  (+78.83%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.26 μs →        3.44 μs  (-19.31%) |       1   →       1              |        4.26 μs →        3.44 μs  (-19.31%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.40 μs →        2.47 μs  (-27.22%) |       1   →       1              |        3.40 μs →        2.47 μs  (-27.22%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      458.00 ns →      409.00 ns  (-10.70%) |       1   →       1              |      458.00 ns →      409.00 ns  (-10.70%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      639.00 ns →        1.36 μs (+112.36%) |       1   →       1              |      639.00 ns →        1.36 μs (+112.36%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.18 ms →        2.98 ms   (-6.40%) |       1   →       1              |        3.18 ms →        2.98 ms   (-6.40%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.22 ms →       24.55 ms  (+15.67%) |       1   →       1              |       21.22 ms →       24.55 ms  (+15.67%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       21.47 ms →       21.88 ms   (+1.93%) |       2   →       2              |       42.94 ms →       43.77 ms   (+1.93%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.20 ms →        6.54 ms  (-59.65%) |       2   →       2              |       32.40 ms →       13.07 ms  (-59.65%) | 
+ │ │ │ └ sddk::wf_inner                                                |       15.99 ms →        6.33 ms  (-60.42%) |       2   →       2              |       31.98 ms →       12.66 ms  (-60.42%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       22.00 ns →       44.00 ns (+100.00%) |       2   →       2              |       44.00 ns →       88.00 ns (+100.00%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       15.86 ms →        6.20 ms  (-60.91%) |       2   →       2              |       31.72 ms →       12.40 ms  (-60.91%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       18.50 ns →       19.50 ns   (+5.41%) |       2   →       2              |       37.00 ns →       39.00 ns   (+5.41%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      250.28 ms →       64.84 ms  (-74.09%) |       1   →       1              |      250.28 ms →       64.84 ms  (-74.09%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.60 ms   (-0.15%) |       1   →       1              |        2.60 ms →        2.60 ms   (-0.15%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        2.59 ms   (-0.14%) |       1   →       1              |        2.60 ms →        2.59 ms   (-0.14%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      545.00 ns →      399.00 ns  (-26.79%) |       1   →       1              |      545.00 ns →      399.00 ns  (-26.79%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.00 s  →       62.93 s    (+1.50%) |       1   →       1              |       62.00 s  →       62.93 s    (+1.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.46 ms   (-0.44%) |      19   →      19              |       46.89 ms →       46.69 ms   (-0.44%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        2.99 s    (-8.20%) |      19   →      21    (+10.53%) |       61.79 s  →       62.70 s    (+1.47%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.54 ms →        4.35 ms  (-21.50%) |      19   →      21    (+10.53%) |      105.35 ms →       91.41 ms  (-13.23%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.80 ms →        3.72 ms  (-22.39%) |      19   →      21    (+10.53%) |       91.16 ms →       78.20 ms  (-14.22%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      542.07 μs →      533.66 μs   (-1.55%) |      19   →      21    (+10.53%) |       10.30 ms →       11.21 ms   (+8.81%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.14 ms →        2.15 ms  (-31.63%) |      19   →      21    (+10.53%) |       59.75 ms →       45.15 ms  (-24.43%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      236.38 μs →      159.42 μs  (-32.56%) |      38   →      42    (+10.53%) |        8.98 ms →        6.70 ms  (-25.46%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      107.33 μs →      134.05 μs  (+24.90%) |      19   →      21    (+10.53%) |        2.04 ms →        2.82 ms  (+38.05%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       89.58 μs →       94.03 μs   (+4.97%) |      19   →      21    (+10.53%) |        1.70 ms →        1.97 ms  (+16.02%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.17%) |      19   →      21    (+10.53%) |       38.54 s  →       36.99 s    (-4.03%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      224.82 μs →      238.02 μs   (+5.87%) |      19   →      21    (+10.53%) |        4.27 ms →        5.00 ms  (+17.01%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      216.34 μs →      228.08 μs   (+5.43%) |      19   →      21    (+10.53%) |        4.11 ms →        4.79 ms  (+16.52%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.19 μs →        7.28 μs  (+17.52%) |      19   →      21    (+10.53%) |      117.66 μs →      152.83 μs  (+29.89%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.64 s   (-16.63%) |      19   →      21    (+10.53%) |       37.32 s  →       34.39 s    (-7.86%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       72.11 ms →       72.09 ms   (-0.02%) |      19   →      21    (+10.53%) |        1.37 s  →        1.51 s   (+10.50%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.10 ms →        7.25 ms  (-10.45%) |     114   →     126    (+10.53%) |      922.96 ms →      913.49 ms   (-1.03%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.47 ms →       18.51 ms   (+5.94%) |      19   →      21    (+10.53%) |      331.96 ms →      388.68 ms  (+17.09%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      462.63 μs →      454.79 μs   (-1.70%) |      19   →      21    (+10.53%) |        8.79 ms →        9.55 ms   (+8.65%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.90 ms →        8.43 ms   (+6.68%) |      38   →      42    (+10.53%) |      300.32 ms →      354.11 ms  (+17.91%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.87 s  →        1.54 s   (-17.57%) |      19   →      21    (+10.53%) |       35.44 s  →       32.29 s    (-8.89%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       46.37 ms →       55.15 ms  (+18.95%) |     356   →     361     (+1.40%) |       16.51 s  →       19.91 s   (+20.62%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.15 ms →       30.83 ms   (+9.52%) |     356   →     361     (+1.40%) |       10.02 s  →       11.13 s   (+11.06%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.25 μs →        2.22 μs   (-1.38%) |     356   →     361     (+1.40%) |      800.32 μs →      800.34 μs   (+0.00%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.90 μs →        1.88 μs   (-0.87%) |     356   →     361     (+1.40%) |      676.35 μs →      679.88 μs   (+0.52%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      487.64 ns →      471.50 ns   (-3.31%) |     356   →     361     (+1.40%) |      173.60 μs →      170.21 μs   (-1.95%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      686.47 ns →      700.98 ns   (+2.11%) |     356   →     361     (+1.40%) |      244.38 μs →      253.05 μs   (+3.55%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.66 ms →        2.79 ms   (+4.79%) |     356   →     361     (+1.40%) |      948.24 ms →        1.01 s    (+6.27%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.10 ms →        3.28 ms   (+5.78%) |     356   →     361     (+1.40%) |        1.10 s  →        1.18 s    (+7.27%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.22 ms →        9.12 ms  (+46.62%) |     712   →     722     (+1.40%) |        4.43 s  →        6.58 s   (+48.68%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.01 ms →        6.91 ms  (+15.04%) |     356   →     361     (+1.40%) |        2.14 s  →        2.49 s   (+16.66%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      888.49 μs →        1.18 ms  (+32.41%) |     693   →     701     (+1.15%) |      615.72 ms →      824.71 ms  (+33.94%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       60.63 ns →       42.38 ns  (-30.10%) |     693   →     701     (+1.15%) |       42.02 μs →       29.71 μs  (-29.30%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      728.18 μs →        1.01 ms  (+39.00%) |     693   →     701     (+1.15%) |      504.63 ms →      709.55 ms  (+40.61%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.45 ns →       52.74 ns  (+16.05%) |     693   →     701     (+1.15%) |       31.50 μs →       36.97 μs  (+17.39%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      131.10 μs →      138.15 μs   (+5.38%) |     356   →     361     (+1.40%) |       46.67 ms →       49.87 ms   (+6.86%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.95 ms →        2.05 ms   (+5.08%) |     356   →     361     (+1.40%) |      694.87 ms →      740.40 ms   (+6.55%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.31 ms →        2.58 ms  (+11.64%) |     337   →     340     (+0.89%) |      779.02 ms →      877.45 ms  (+12.64%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      769.70 μs →      859.40 μs  (+11.65%) |    1.01 K →    1.02 K   (+0.89%) |      778.17 ms →      876.59 ms  (+12.65%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.45 ms →        1.52 ms   (+4.39%) |     356   →     361     (+1.40%) |      516.67 ms →      546.93 ms   (+5.86%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        1.38 ms →        1.47 ms   (+6.27%) |     356   →     361     (+1.40%) |      491.51 ms →      529.67 ms   (+7.76%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       39.54 ns →       40.42 ns   (+2.21%) |     356   →     361     (+1.40%) |       14.08 μs →       14.59 μs   (+3.64%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.22 ms →        1.31 ms   (+7.02%) |     356   →     361     (+1.40%) |      434.14 ms →      471.14 ms   (+8.52%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       44.81 ns →       47.22 ns   (+5.40%) |     356   →     361     (+1.40%) |       15.95 μs →       17.05 μs   (+6.88%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       42.59 ms →       21.78 ms  (-48.86%) |     356   →     361     (+1.40%) |       15.16 s  →        7.86 s   (-48.14%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.30 ms →        2.83 ms  (+22.66%) |     340   →     346     (+1.76%) |      783.23 ms →      977.70 ms  (+24.83%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.33 ms →        1.20 ms   (-9.82%) |     337   →     342     (+1.48%) |      447.48 ms →      409.52 ms   (-8.48%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      662.45 μs →      597.25 μs   (-9.84%) |     674   →     684     (+1.48%) |      446.49 ms →      408.52 ms   (-8.50%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      906.93 μs →        1.54 ms  (+69.63%) |     337   →     342     (+1.48%) |      305.63 ms →      526.15 ms  (+72.15%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.12 ms →        5.48 ms  (-10.36%) |      54   →      90    (+66.67%) |      330.31 ms →      493.48 ms  (+49.40%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.66 ms →        3.05 ms  (-16.62%) |      89   →     159    (+78.65%) |      325.71 ms →      485.20 ms  (+48.97%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.63 ms →        2.13 ms  (-18.99%) |     124   →     228    (+83.87%) |      325.53 ms →      484.89 ms  (+48.95%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      341.89 ns →      627.00 ns  (+83.39%) |      19   →      21    (+10.53%) |        6.50 μs →       13.17 μs (+102.69%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.58 μs →       19.59 μs   (+0.04%) |      19   →      21    (+10.53%) |      372.09 μs →      411.40 μs  (+10.57%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.52 ms   (+0.31%) |      19   →      21    (+10.53%) |       28.78 ms →       31.91 ms  (+10.87%) | 
- │ │ ├ sirius::Density::generate                                       |      564.14 ms →      569.40 ms   (+0.93%) |      19   →      21    (+10.53%) |       10.72 s  →       11.96 s   (+11.56%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      431.24 ms →      407.22 ms   (-5.57%) |      19   →      21    (+10.53%) |        8.19 s  →        8.55 s    (+4.37%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.25 μs →        8.35 μs   (+1.16%) |      19   →      21    (+10.53%) |      156.75 μs →      175.26 μs  (+11.81%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.70 μs →        7.82 μs   (+1.50%) |      19   →      21    (+10.53%) |      146.32 μs →      164.15 μs  (+12.19%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       28.12 ms →       33.11 ms  (+17.75%) |      19   →      21    (+10.53%) |      534.26 ms →      695.30 ms  (+30.14%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.84 μs →        8.49 μs   (+8.28%) |      19   →      21    (+10.53%) |      148.98 μs →      178.29 μs  (+19.68%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.17 ms →        5.30 ms   (+2.40%) |      19   →      21    (+10.53%) |       98.31 ms →      111.27 ms  (+13.18%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       21.90 ms →       26.76 ms  (+22.23%) |      19   →      21    (+10.53%) |      416.01 ms →      562.00 ms  (+35.09%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      767.11 ns →      808.29 ns   (+5.37%) |      19   →      21    (+10.53%) |       14.58 μs →       16.97 μs  (+16.46%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      117.78 ms →      113.13 ms   (-3.95%) |      19   →      21    (+10.53%) |        2.24 s  →        2.38 s    (+6.16%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        1.94 ms  (-13.95%) |      19   →      21    (+10.53%) |       42.80 ms →       40.71 ms   (-4.89%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      256.84 ms →      219.53 ms  (-14.53%) |      19   →      21    (+10.53%) |        4.88 s  →        4.61 s    (-5.53%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      256.63 ms →      219.30 ms  (-14.54%) |      19   →      21    (+10.53%) |        4.88 s  →        4.61 s    (-5.55%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      105.09 ms →      134.82 ms  (+28.30%) |      19   →      21    (+10.53%) |        2.00 s  →        2.83 s   (+41.80%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      105.08 ms →      134.82 ms  (+28.30%) |      19   →      21    (+10.53%) |        2.00 s  →        2.83 s   (+41.80%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       21.85 ms →       51.12 ms (+134.00%) |      19   →      21    (+10.53%) |      415.07 ms →        1.07 s  (+158.63%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.95 ms →       70.41 ms   (+0.65%) |      19   →      21    (+10.53%) |        1.33 s  →        1.48 s   (+11.24%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.63 ms →       12.64 ms   (+0.04%) |      19   →      21    (+10.53%) |      239.99 ms →      265.37 ms  (+10.58%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       24.26 ms →       23.59 ms   (-2.73%) |      19   →      21    (+10.53%) |      460.88 ms →      495.47 ms   (+7.50%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.55 ms →        3.75 ms   (+5.72%) |      19   →      21    (+10.53%) |       67.47 ms →       78.84 ms  (+16.85%) | 
- │ │ ├ sirius::Density::mix                                            |      133.64 ms →      134.88 ms   (+0.92%) |      19   →      21    (+10.53%) |        2.54 s  →        2.83 s   (+11.55%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |        1.05 ms →      675.99 μs  (-35.83%) |      19   →      21    (+10.53%) |       20.01 ms →       14.20 ms  (-29.07%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.93 ms →        4.70 ms   (-4.72%) |     229   →     259    (+13.10%) |        1.13 s  →        1.22 s    (+7.76%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.61 ms   (-4.08%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.48%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.61 ms   (-4.09%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.48%) | 
! │ │ │ └ sirius::Density::mixer_output                                 |        5.03 ms →        4.71 ms   (-6.30%) |      19   →      21    (+10.53%) |       95.48 ms →       98.88 ms   (+3.56%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.36 ms →        4.01 ms   (-8.03%) |      19   →      21    (+10.53%) |       82.91 ms →       84.28 ms   (+1.65%) | 
! │ │ ├ sirius::Potential::generate                                     |      365.67 ms →      361.55 ms   (-1.13%) |      19   →      21    (+10.53%) |        6.95 s  →        7.59 s    (+9.28%) | 
! │ │ │ ├ sirius::Potential::poisson                                    |       45.52 ms →       41.01 ms   (-9.91%) |      19   →      21    (+10.53%) |      864.94 ms →      861.24 ms   (-0.43%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.94 ms →        2.97 ms   (+0.84%) |      19   →      21    (+10.53%) |       55.89 ms →       62.28 ms  (+11.45%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.39 ms →        5.38 ms   (-0.21%) |      19   →      21    (+10.53%) |      102.47 ms →      113.02 ms  (+10.29%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.10%) |      19   →      21    (+10.53%) |       87.93 ms →       97.29 ms  (+10.64%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.10%) |      19   →      21    (+10.53%) |       87.91 ms →       97.26 ms  (+10.63%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      776.37 μs →      793.29 μs   (+2.18%) |      38   →      42    (+10.53%) |       29.50 ms →       33.32 ms  (+12.93%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.47 ms →       44.58 ms   (+0.25%) |      19   →      21    (+10.53%) |      844.93 ms →      936.19 ms  (+10.80%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.29 ms →       43.41 ms   (+0.27%) |      19   →      21    (+10.53%) |      822.54 ms →      911.55 ms  (+10.82%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      678.48 μs →      665.20 μs   (-1.96%) |      38   →      42    (+10.53%) |       25.78 ms →       27.94 ms   (+8.36%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        3.99 ms →        4.14 ms   (+3.75%) |      19   →      21    (+10.53%) |       75.84 ms →       86.96 ms  (+14.67%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.54 ms →        3.85 ms   (+9.03%) |      19   →      21    (+10.53%) |       67.17 ms →       80.95 ms  (+20.51%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.19 ms →      269.08 ms   (-0.04%) |      19   →      21    (+10.53%) |        5.11 s  →        5.65 s   (+10.48%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      319.53 ns →      261.33 ns  (-18.21%) |      19   →      21    (+10.53%) |        6.07 μs →        5.49 μs   (-9.60%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.34 ms →       97.52 ms   (+1.23%) |      19   →      21    (+10.53%) |        1.83 s  →        2.05 s   (+11.88%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.34 ms →       97.52 ms   (+1.23%) |      19   →      21    (+10.53%) |        1.83 s  →        2.05 s   (+11.88%) | 
! │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.59 ms →       13.37 ms   (-1.63%) |      19   →      21    (+10.53%) |      258.20 ms →      280.72 ms   (+8.72%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.51 ms →       70.37 ms   (+1.25%) |      19   →      21    (+10.53%) |        1.32 s  →        1.48 s   (+11.90%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.61 ms →       13.14 ms   (+4.19%) |      19   →      21    (+10.53%) |      239.63 ms →      275.95 ms  (+15.15%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.08 ms →        3.25 ms  (-20.42%) |      19   →      21    (+10.53%) |       77.49 ms →       68.16 ms  (-12.04%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.74 ms →        4.68 ms   (-1.14%) |     133   →     147    (+10.53%) |      630.23 ms →      688.65 ms   (+9.27%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.55 ms   (-0.26%) |     133   →     147    (+10.53%) |      606.31 ms →      668.43 ms  (+10.24%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.55 ms   (-0.25%) |     133   →     147    (+10.53%) |      606.24 ms →      668.35 ms  (+10.24%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.94 ms →        4.72 ms   (-4.31%) |      57   →      63    (+10.53%) |      281.47 ms →      297.67 ms   (+5.76%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.72 ms   (-4.35%) |      57   →      63    (+10.53%) |      281.09 ms →      297.17 ms   (+5.72%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.53 ms   (-0.05%) |      19   →      21    (+10.53%) |       86.06 ms →       95.07 ms  (+10.47%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       78.43 μs →       75.61 μs   (-3.59%) |      19   →      21    (+10.53%) |        1.49 ms →        1.59 ms   (+6.56%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       73.48 μs →       70.91 μs   (-3.50%) |      19   →      21    (+10.53%) |        1.40 ms →        1.49 ms   (+6.66%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.53 ms →        5.50 ms   (-0.50%) |       2   →       2              |       11.05 ms →       11.00 ms   (-0.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.53 ms   (-5.56%) |       6   →       6              |       28.80 ms →       27.20 ms   (-5.56%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.52 ms   (-5.70%) |       6   →       6              |       28.78 ms →       27.14 ms   (-5.70%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.52 ms   (-5.67%) |       6   →       6              |       28.77 ms →       27.14 ms   (-5.67%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.21 ms →        4.75 ms   (-8.76%) |       3   →       3              |       15.63 ms →       14.26 ms   (-8.76%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.20 ms →        4.72 ms   (-9.36%) |       3   →       3              |       15.61 ms →       14.15 ms   (-9.36%) | 
  ├ sirius::Periodic_function|inner                                     |        4.89 ms →        4.59 ms   (-6.20%) |       2   →       2              |        9.78 ms →        9.18 ms   (-6.20%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.89 ms →        4.52 ms   (-7.59%) |       2   →       2              |        9.77 ms →        9.03 ms   (-7.59%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.89 ms →        4.52 ms   (-7.58%) |       2   →       2              |        9.77 ms →        9.03 ms   (-7.58%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.16 ms →        4.70 ms   (-8.81%) |       1   →       1              |        5.16 ms →        4.70 ms   (-8.81%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.15 ms →        4.70 ms   (-8.81%) |       1   →       1              |        5.15 ms →        4.70 ms   (-8.81%) | 
- └ sirius::finalize                                                    |      143.92 ms →      170.47 ms  (+18.45%) |       1   →       1              |      143.92 ms →      170.47 ms  (+18.45%) | 
  ====================================================================================================================================================================================================
```
