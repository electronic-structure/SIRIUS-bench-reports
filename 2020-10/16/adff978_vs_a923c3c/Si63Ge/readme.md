# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.55 s  →       72.80 s    (+1.75%) |       1   →       1              |       71.55 s  →       72.80 s    (+1.75%) | 
  ├ sirius::initialize                                                  |        2.93 s  →        2.89 s    (-1.39%) |       1   →       1              |        2.93 s  →        2.89 s    (-1.39%) | 
  ├ sirius::Simulation_context::initialize                              |        3.48 s  →        3.71 s    (+6.63%) |       1   →       1              |        3.48 s  →        3.71 s    (+6.63%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      242.29 μs →       36.61 ms (+15011.11%) |       1   →       1              |      242.29 μs →       36.61 ms (+15011.11%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      133.22 ms →      122.62 ms   (-7.95%) |       1   →       1              |      133.22 ms →      122.62 ms   (-7.95%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       57.82 ms →       52.00 ms  (-10.07%) |       2   →       2              |      115.64 ms →      104.00 ms  (-10.07%) | 
  │ │ └ sirius::Unit_cell::update                                       |       17.47 ms →       18.54 ms   (+6.13%) |       1   →       1              |       17.47 ms →       18.54 ms   (+6.13%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.96 ms →        5.23 ms   (+5.44%) |       1   →       1              |        4.96 ms →        5.23 ms   (+5.44%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       12.46 ms →       13.24 ms   (+6.22%) |       1   →       1              |       12.46 ms →       13.24 ms   (+6.22%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       12.39 ms →       13.17 ms   (+6.29%) |       1   →       1              |       12.39 ms →       13.17 ms   (+6.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.74 ms →        2.76 ms   (+0.82%) |       1   →       1              |        2.74 ms →        2.76 ms   (+0.82%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      520.91 μs →      966.32 μs  (+85.51%) |       1   →       1              |      520.91 μs →      966.32 μs  (+85.51%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.72 μs →       16.84 μs   (+0.72%) |       1   →       1              |       16.72 μs →       16.84 μs   (+0.72%) | 
  │ └ sirius::Simulation_context::update                                |        3.23 s  →        3.35 s    (+3.74%) |       1   →       1              |        3.23 s  →        3.35 s    (+3.74%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.78 ms →        6.78 ms   (-0.02%) |       1   →       1              |        6.78 ms →        6.78 ms   (-0.02%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.42 ms →        3.43 ms   (+0.19%) |       1   →       1              |        3.42 ms →        3.43 ms   (+0.19%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.30 ms   (+0.28%) |       1   →       1              |        3.29 ms →        3.30 ms   (+0.28%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.25 ms →        3.26 ms   (+0.30%) |       1   →       1              |        3.25 ms →        3.26 ms   (+0.30%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.72 ms   (+0.14%) |       1   →       1              |        2.71 ms →        2.72 ms   (+0.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      502.32 μs →      509.31 μs   (+1.39%) |       1   →       1              |      502.32 μs →      509.31 μs   (+1.39%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.95 μs →       13.78 μs   (-1.24%) |       1   →       1              |       13.95 μs →       13.78 μs   (-1.24%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.94 ms →      226.17 ms   (+6.21%) |       2   →       2              |      425.87 ms →      452.34 ms   (+6.21%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.27 ms   (+0.65%) |       2   →       2              |       30.33 ms →       30.53 ms   (+0.65%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.45 ms   (+1.33%) |       1   →       1              |       13.28 ms →       13.45 ms   (+1.33%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.33 ms →       56.61 ms   (+0.49%) |       2   →       2              |      112.67 ms →      113.22 ms   (+0.49%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.11 ms →       45.19 ms   (+0.19%) |       2   →       2              |       90.21 ms →       90.38 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.41 ms →       60.39 ms   (-0.04%) |       4   →       4              |      241.65 ms →      241.55 ms   (-0.04%) | 
  │   ├ sddk::Gvec::init                                                |       93.48 ms →       92.50 ms   (-1.05%) |       2   →       2              |      186.96 ms →      185.00 ms   (-1.05%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.98 ms →       69.15 ms   (-1.18%) |       2   →       2              |      139.95 ms →      138.30 ms   (-1.18%) | 
  │   ├ sddk::Gvec_shells                                               |      101.10 ms →       97.62 ms   (-3.44%) |       1   →       1              |      101.10 ms →       97.62 ms   (-3.44%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.98 ms →        1.95 ms   (-1.52%) |       1   →       1              |        1.98 ms →        1.95 ms   (-1.52%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      469.96 ms →      517.94 ms  (+10.21%) |       2   →       2              |      939.92 ms →        1.04 s   (+10.21%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      234.87 ms →      153.15 ms  (-34.79%) |       1   →       1              |      234.87 ms →      153.15 ms  (-34.79%) | 
  │ ├ sirius::K_point::K_point                                          |        2.45 μs →        2.57 μs   (+4.71%) |       4   →       4              |        9.81 μs →       10.28 μs   (+4.71%) | 
+ │ └ sirius::K_point_set::initialize                                   |      234.79 ms →      153.06 ms  (-34.81%) |       1   →       1              |      234.79 ms →      153.06 ms  (-34.81%) | 
  │   └ sirius::K_point::initialize                                     |       28.20 ms →       28.13 ms   (-0.27%) |       1   →       1              |       28.20 ms →       28.13 ms   (-0.27%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.87 ms →       11.11 ms   (+2.23%) |       1   →       1              |       10.87 ms →       11.11 ms   (+2.23%) | 
  │     │ └ sddk::Gvec::init                                            |        4.88 ms →        5.01 ms   (+2.81%) |       1   →       1              |        4.88 ms →        5.01 ms   (+2.81%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        6.55 μs →        8.33 μs  (+27.07%) |       1   →       1              |        6.55 μs →        8.33 μs  (+27.07%) | 
  │     └ sirius::K_point::update                                       |       14.54 ms →       14.17 ms   (-2.54%) |       1   →       1              |       14.54 ms →       14.17 ms   (-2.54%) | 
  │       └ sirius::Beta_projectors                                     |       10.73 ms →       10.19 ms   (-5.07%) |       1   →       1              |       10.73 ms →       10.19 ms   (-5.07%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.30 ms →        8.26 ms   (-0.43%) |       1   →       1              |        8.30 ms →        8.26 ms   (-0.43%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.54 ms →        2.56 ms   (+0.90%) |       2   →       2              |        5.08 ms →        5.12 ms   (+0.90%) | 
  ├ sirius::Potential                                                   |       53.01 ms →       52.89 ms   (-0.22%) |       1   →       1              |       53.01 ms →       52.89 ms   (-0.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.92 ms   (-0.23%) |       6   →       6              |       17.58 ms →       17.54 ms   (-0.23%) | 
  │ └ sirius::Potential::update                                         |       34.91 ms →       34.75 ms   (-0.43%) |       1   →       1              |       34.91 ms →       34.75 ms   (-0.43%) | 
  │   └ sirius::Potential::generate_local_potential                     |       34.49 ms →       34.36 ms   (-0.36%) |       1   →       1              |       34.49 ms →       34.36 ms   (-0.36%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       24.07 ms →       26.47 ms   (+9.97%) |       1   →       1              |       24.07 ms →       26.47 ms   (+9.97%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.91 ms →        7.37 ms  (-25.59%) |       1   →       1              |        9.91 ms →        7.37 ms  (-25.59%) | 
  ├ sirius::Density                                                     |       39.92 ms →       39.18 ms   (-1.86%) |       1   →       1              |       39.92 ms →       39.18 ms   (-1.86%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.87 ms →        2.84 ms   (-1.09%) |       2   →       2              |        5.74 ms →        5.67 ms   (-1.09%) | 
  │ └ sirius::Density::update                                           |       34.04 ms →       33.36 ms   (-2.00%) |       1   →       1              |       34.04 ms →       33.36 ms   (-2.00%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       33.73 ms →       33.05 ms   (-2.00%) |       1   →       1              |       33.73 ms →       33.05 ms   (-2.00%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.16 μs →       78.17 μs   (+2.64%) |       1   →       1              |       76.16 μs →       78.17 μs   (+2.64%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       24.23 ms →       26.34 ms   (+8.74%) |       1   →       1              |       24.23 ms →       26.34 ms   (+8.74%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.14 ms →        6.31 ms  (-30.94%) |       1   →       1              |        9.14 ms →        6.31 ms  (-30.94%) | 
  ├ sirius::Density::initial_density                                    |       59.86 ms →       59.99 ms   (+0.22%) |       1   →       1              |       59.86 ms →       59.99 ms   (+0.22%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       25.14 ms →       26.56 ms   (+5.66%) |       1   →       1              |       25.14 ms →       26.56 ms   (+5.66%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        8.26 ms →        7.66 ms   (-7.31%) |       2   →       2              |       16.52 ms →       15.31 ms   (-7.31%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.61 ms →        4.50 ms   (-2.45%) |       1   →       1              |        4.61 ms →        4.50 ms   (-2.45%) | 
  ├ sirius::Potential::generate                                         |      369.51 ms →      367.05 ms   (-0.67%) |       1   →       1              |      369.51 ms →      367.05 ms   (-0.67%) | 
  │ ├ sirius::Potential::poisson                                        |       40.60 ms →       39.94 ms   (-1.63%) |       1   →       1              |       40.60 ms →       39.94 ms   (-1.63%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       12.71 ms →        9.30 ms  (-26.84%) |       1   →       1              |       12.71 ms →        9.30 ms  (-26.84%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.98 ms →        5.01 ms   (+0.65%) |       1   →       1              |        4.98 ms →        5.01 ms   (+0.65%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.64 ms   (+0.04%) |       1   →       1              |        4.64 ms →        4.64 ms   (+0.04%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.63 ms   (+0.05%) |       1   →       1              |        4.63 ms →        4.63 ms   (+0.05%) | 
  │ ├ sirius::Periodic_function::add                                    |      801.78 μs →      745.92 μs   (-6.97%) |       2   →       2              |        1.60 ms →        1.49 ms   (-6.97%) | 
  │ ├ sirius::Potential::xc                                             |       53.42 ms →       51.54 ms   (-3.53%) |       1   →       1              |       53.42 ms →       51.54 ms   (-3.53%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.20 ms →       50.37 ms   (-3.50%) |       1   →       1              |       52.20 ms →       50.37 ms   (-3.50%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.58 ms   (+1.07%) |       2   →       2              |        5.10 ms →        5.16 ms   (+1.07%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.78 ms →        4.66 ms   (-2.43%) |       1   →       1              |        4.78 ms →        4.66 ms   (-2.43%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.87 ms →        3.08 ms  (-20.52%) |       1   →       1              |        3.87 ms →        3.08 ms  (-20.52%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.57 ms →      269.59 ms   (+0.38%) |       1   →       1              |      268.57 ms →      269.59 ms   (+0.38%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      296.00 ns →      381.00 ns  (+28.72%) |       1   →       1              |      296.00 ns →      381.00 ns  (+28.72%) | 
+ ├ sirius::Hamiltonian0                                                |        8.76 ms →        6.33 ms  (-27.74%) |       1   →       1              |        8.76 ms →        6.33 ms  (-27.74%) | 
+ │ ├ sirius::Local_operator                                            |        8.25 ms →        5.87 ms  (-28.81%) |       1   →       1              |        8.25 ms →        5.87 ms  (-28.81%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.77 ms →        2.77 ms   (+0.02%) |       1   →       1              |        2.77 ms →        2.77 ms   (+0.02%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.87 ms →        2.35 ms  (-39.31%) |       1   →       1              |        3.87 ms →        2.35 ms  (-39.31%) | 
+ │ ├ sirius::Non_local_operator                                        |      117.88 μs →       74.11 μs  (-37.13%) |       2   →       2              |      235.75 μs →      148.22 μs  (-37.13%) | 
  │ ├ sirius::D_operator::initialize                                    |      114.35 μs →      110.73 μs   (-3.16%) |       1   →       1              |      114.35 μs →      110.73 μs   (-3.16%) | 
- │ └ sirius::Q_operator::initialize                                    |       91.60 μs →      116.44 μs  (+27.11%) |       1   →       1              |       91.60 μs →      116.44 μs  (+27.11%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+0.44%) |       1   →       1              |        1.28 s  →        1.29 s    (+0.44%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       74.74 ms →       34.23 ms  (-54.20%) |       1   →       1              |       74.74 ms →       34.23 ms  (-54.20%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      225.22 μs →      307.43 μs  (+36.50%) |       1   →       1              |      225.22 μs →      307.43 μs  (+36.50%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       74.52 ms →       33.92 ms  (-54.48%) |       1   →       1              |       74.52 ms →       33.92 ms  (-54.48%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.21 s  →        1.26 s    (+3.82%) |       1   →       1              |        1.21 s  →        1.26 s    (+3.82%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      102.85 ms →       81.50 ms  (-20.76%) |       4   →       4              |      411.42 ms →      325.99 ms  (-20.76%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.54 ms →       54.75 ms  (+45.84%) |       1   →       1              |       37.54 ms →       54.75 ms  (+45.84%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.07 ms →        7.42 ms   (+4.96%) |       1   →       1              |        7.07 ms →        7.42 ms   (+4.96%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      447.93 ms →      337.31 ms  (-24.70%) |       1   →       1              |      447.93 ms →      337.31 ms  (-24.70%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      375.90 ms →      248.68 ms  (-33.84%) |       1   →       1              |      375.90 ms →      248.68 ms  (-33.84%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.98 μs →        3.65 μs   (-8.29%) |       1   →       1              |        3.98 μs →        3.65 μs   (-8.29%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.05 μs →        2.69 μs  (-11.89%) |       1   →       1              |        3.05 μs →        2.69 μs  (-11.89%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      375.00 ns →      520.00 ns  (+38.67%) |       1   →       1              |      375.00 ns →      520.00 ns  (+38.67%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      935.00 ns →      605.00 ns  (-35.29%) |       1   →       1              |      935.00 ns →      605.00 ns  (-35.29%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.06 ms →        3.14 ms   (+2.37%) |       1   →       1              |        3.06 ms →        3.14 ms   (+2.37%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       24.56 ms →       21.33 ms  (-13.16%) |       1   →       1              |       24.56 ms →       21.33 ms  (-13.16%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.18 ms →       32.06 ms  (+44.51%) |       2   →       2              |       44.37 ms →       64.11 ms  (+44.51%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.54 ms →       14.75 ms  (-10.80%) |       2   →       2              |       33.08 ms →       29.51 ms  (-10.80%) | 
+ │ │ │ └ sddk::wf_inner                                                |       16.31 ms →       14.54 ms  (-10.85%) |       2   →       2              |       32.63 ms →       29.09 ms  (-10.85%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       37.50 ns →       18.50 ns  (-50.67%) |       2   →       2              |       75.00 ns →       37.00 ns  (-50.67%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       16.18 ms →       14.41 ms  (-10.94%) |       2   →       2              |       32.36 ms →       28.82 ms  (-10.94%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       29.00 ns →       23.50 ns  (-18.97%) |       2   →       2              |       58.00 ns →       47.00 ns  (-18.97%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      112.30 ms →      232.91 ms (+107.40%) |       1   →       1              |      112.30 ms →      232.91 ms (+107.40%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.61 ms   (-0.04%) |       1   →       1              |        2.61 ms →        2.61 ms   (-0.04%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.61 ms   (-0.05%) |       1   →       1              |        2.61 ms →        2.61 ms   (-0.05%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      658.00 ns →      416.00 ns  (-36.78%) |       1   →       1              |      658.00 ns →      416.00 ns  (-36.78%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.95 s  →       63.11 s    (+1.87%) |       1   →       1              |       61.95 s  →       63.11 s    (+1.87%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.48 ms →        2.44 ms   (-1.66%) |      19   →      19              |       47.09 ms →       46.31 ms   (-1.66%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        2.99 s    (-7.94%) |      19   →      21    (+10.53%) |       61.71 s  →       62.79 s    (+1.75%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        5.44 ms →        5.41 ms   (-0.51%) |      19   →      21    (+10.53%) |      103.39 ms →      113.69 ms   (+9.96%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.70 ms →        4.78 ms   (+1.76%) |      19   →      21    (+10.53%) |       89.21 ms →      100.34 ms  (+12.48%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      563.37 μs →      531.79 μs   (-5.61%) |      19   →      21    (+10.53%) |       10.70 ms →       11.17 ms   (+4.33%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.89 ms →        3.00 ms   (+3.86%) |      19   →      21    (+10.53%) |       54.96 ms →       63.08 ms  (+14.79%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      234.13 μs →      161.25 μs  (-31.13%) |      38   →      42    (+10.53%) |        8.90 ms →        6.77 ms  (-23.88%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      109.96 μs →      136.01 μs  (+23.68%) |      19   →      21    (+10.53%) |        2.09 ms →        2.86 ms  (+36.70%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       89.85 μs →       95.21 μs   (+5.96%) |      19   →      21    (+10.53%) |        1.71 ms →        2.00 ms  (+17.11%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.02 s  →        1.76 s   (-12.85%) |      19   →      21    (+10.53%) |       38.45 s  →       37.04 s    (-3.67%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      204.41 μs →      232.98 μs  (+13.97%) |      19   →      21    (+10.53%) |        3.88 ms →        4.89 ms  (+25.97%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      195.43 μs →      223.88 μs  (+14.56%) |      19   →      21    (+10.53%) |        3.71 ms →        4.70 ms  (+26.61%) | 
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.62 μs →        6.44 μs   (-2.71%) |      19   →      21    (+10.53%) |      125.77 μs →      135.25 μs   (+7.54%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.64 s   (-16.42%) |      19   →      21    (+10.53%) |       37.29 s  →       34.45 s    (-7.63%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       79.19 ms →       73.03 ms   (-7.78%) |      19   →      21    (+10.53%) |        1.50 s  →        1.53 s    (+1.93%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.34 ms →        7.74 ms   (-7.20%) |     114   →     126    (+10.53%) |      951.12 ms →      975.49 ms   (+2.56%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.42 ms →       18.39 ms  (+19.23%) |      19   →      21    (+10.53%) |      293.06 ms →      386.20 ms  (+31.78%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      489.42 μs →      460.99 μs   (-5.81%) |      19   →      21    (+10.53%) |        9.30 ms →        9.68 ms   (+4.11%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.01 ms →        8.37 ms  (+19.41%) |      38   →      42    (+10.53%) |      266.43 ms →      351.63 ms  (+31.98%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.26%) |      19   →      21    (+10.53%) |       35.34 s  →       32.32 s    (-8.55%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.16 ms →       54.71 ms   (-0.82%) |     356   →     361     (+1.40%) |       19.64 s  →       19.75 s    (+0.58%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       36.07 ms →       30.96 ms  (-14.17%) |     356   →     361     (+1.40%) |       12.84 s  →       11.18 s   (-12.97%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.05 μs →        1.92 μs   (-6.29%) |     356   →     361     (+1.40%) |      729.68 μs →      693.36 μs   (-4.98%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.77 μs →        1.60 μs   (-9.65%) |     356   →     361     (+1.40%) |      629.58 μs →      576.81 μs   (-8.38%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      436.12 ns →      409.26 ns   (-6.16%) |     356   →     361     (+1.40%) |      155.26 μs →      147.74 μs   (-4.84%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      599.45 ns →      533.99 ns  (-10.92%) |     356   →     361     (+1.40%) |      213.41 μs →      192.77 μs   (-9.67%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.88 ms →        2.84 ms   (-1.55%) |     356   →     361     (+1.40%) |        1.03 s  →        1.02 s    (-0.17%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.29 ms →        3.32 ms   (+0.88%) |     356   →     361     (+1.40%) |        1.17 s  →        1.20 s    (+2.30%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.45 ms →        8.79 ms  (+36.28%) |     712   →     722     (+1.40%) |        4.59 s  →        6.34 s   (+38.19%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        5.75 ms →        6.89 ms  (+19.76%) |     356   →     361     (+1.40%) |        2.05 s  →        2.49 s   (+21.44%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      938.34 μs →        1.23 ms  (+30.75%) |     693   →     701     (+1.15%) |      650.27 ms →      860.04 ms  (+32.26%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       57.42 ns →       46.00 ns  (-19.89%) |     693   →     701     (+1.15%) |       39.79 μs →       32.25 μs  (-18.97%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      776.24 μs →        1.06 ms  (+36.99%) |     693   →     701     (+1.15%) |      537.94 ms →      745.44 ms  (+38.57%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       44.26 ns →       46.22 ns   (+4.42%) |     693   →     701     (+1.15%) |       30.68 μs →       32.40 μs   (+5.63%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      132.27 μs →      136.28 μs   (+3.03%) |     356   →     361     (+1.40%) |       47.09 ms →       49.20 ms   (+4.48%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.72 ms →        2.06 ms  (+19.85%) |     356   →     361     (+1.40%) |      611.16 ms →      742.74 ms  (+21.53%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.19 ms →        2.45 ms  (+11.97%) |     337   →     340     (+0.89%) |      738.26 ms →      834.01 ms  (+12.97%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      729.42 μs →      816.91 μs  (+11.99%) |    1.01 K →    1.02 K   (+0.89%) |      737.44 ms →      833.25 ms  (+12.99%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.18 ms →        1.36 ms  (+15.73%) |     356   →     361     (+1.40%) |      419.14 ms →      491.88 ms  (+17.35%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.11 ms →        1.32 ms  (+19.12%) |     356   →     361     (+1.40%) |      393.59 ms →      475.44 ms  (+20.80%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.85 ns →       40.12 ns   (-1.79%) |     356   →     361     (+1.40%) |       14.54 μs →       14.48 μs   (-0.41%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |      941.97 μs →        1.15 ms  (+22.49%) |     356   →     361     (+1.40%) |      335.34 ms →      416.53 ms  (+24.21%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.58 ns →       44.72 ns  (+15.92%) |     356   →     361     (+1.40%) |       13.73 μs →       16.14 μs  (+17.55%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.91 ms →       22.48 ms  (-33.70%) |     356   →     361     (+1.40%) |       12.07 s  →        8.12 s   (-32.77%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.35 ms →        2.85 ms  (+21.26%) |     340   →     346     (+1.76%) |      799.86 ms →      987.03 ms  (+23.40%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.25 ms →        1.27 ms   (+1.57%) |     337   →     342     (+1.48%) |      421.96 ms →      434.93 ms   (+3.07%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      624.65 μs →      634.51 μs   (+1.58%) |     674   →     684     (+1.48%) |      421.01 ms →      434.00 ms   (+3.09%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      981.50 μs →        1.48 ms  (+50.75%) |     337   →     342     (+1.48%) |      330.77 ms →      506.03 ms  (+52.99%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.59 ms →        5.30 ms  (-19.50%) |      54   →      90    (+66.67%) |      355.76 ms →      477.30 ms  (+34.16%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.95 ms →        2.95 ms  (-25.26%) |      89   →     159    (+78.65%) |      351.51 ms →      469.36 ms  (+33.53%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.83 ms →        2.06 ms  (-27.39%) |     124   →     228    (+83.87%) |      351.34 ms →      469.07 ms  (+33.51%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      354.21 ns →      550.29 ns  (+55.36%) |      19   →      21    (+10.53%) |        6.73 μs →       11.56 μs  (+71.71%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.63 μs →       19.44 μs   (-0.99%) |      19   →      21    (+10.53%) |      373.04 μs →      408.22 μs   (+9.43%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.55 ms   (+2.18%) |      19   →      21    (+10.53%) |       28.75 ms →       32.47 ms  (+12.94%) | 
- │ │ ├ sirius::Density::generate                                       |      567.29 ms →      570.71 ms   (+0.60%) |      19   →      21    (+10.53%) |       10.78 s  →       11.98 s   (+11.19%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      377.35 ms →      392.19 ms   (+3.93%) |      19   →      21    (+10.53%) |        7.17 s  →        8.24 s   (+14.87%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.53 μs →        8.44 μs   (-1.04%) |      19   →      21    (+10.53%) |      162.13 μs →      177.33 μs   (+9.38%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.93 μs →        7.96 μs   (+0.37%) |      19   →      21    (+10.53%) |      150.66 μs →      167.14 μs  (+10.94%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       41.48 ms →       49.25 ms  (+18.73%) |      19   →      21    (+10.53%) |      788.20 ms →        1.03 s   (+31.23%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.64 μs →        8.27 μs   (+8.16%) |      19   →      21    (+10.53%) |      145.21 μs →      173.59 μs  (+19.54%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.12 ms →        8.70 ms  (-62.37%) |      19   →      21    (+10.53%) |      439.22 ms →      182.69 ms  (-58.41%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       17.30 ms →       39.49 ms (+128.24%) |      19   →      21    (+10.53%) |      328.73 ms →      829.27 ms (+152.27%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      674.32 ns →      819.67 ns  (+21.56%) |      19   →      21    (+10.53%) |       12.81 μs →       17.21 μs  (+34.35%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       97.97 ms →       97.38 ms   (-0.60%) |      19   →      21    (+10.53%) |        1.86 s  →        2.04 s    (+9.86%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.02 ms →        1.89 ms   (-6.37%) |      19   →      21    (+10.53%) |       38.43 ms →       39.78 ms   (+3.49%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      198.08 ms →      201.45 ms   (+1.70%) |      19   →      21    (+10.53%) |        3.76 s  →        4.23 s   (+12.41%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      197.86 ms →      201.23 ms   (+1.70%) |      19   →      21    (+10.53%) |        3.76 s  →        4.23 s   (+12.41%) | 
! │ │ │ ├ sirius::Field4D::symmetrize                                   |      160.48 ms →      150.45 ms   (-6.25%) |      19   →      21    (+10.53%) |        3.05 s  →        3.16 s    (+3.62%) | 
! │ │ │ │ └ sirius::symmetrize_function|fpw                             |      160.48 ms →      150.44 ms   (-6.25%) |      19   →      21    (+10.53%) |        3.05 s  →        3.16 s    (+3.62%) | 
! │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       75.38 ms →       67.95 ms   (-9.87%) |      19   →      21    (+10.53%) |        1.43 s  →        1.43 s    (-0.38%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.80 ms →       69.21 ms   (-3.61%) |      19   →      21    (+10.53%) |        1.36 s  →        1.45 s    (+6.53%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.65 ms →       12.64 ms   (-0.06%) |      19   →      21    (+10.53%) |      240.27 ms →      265.41 ms  (+10.46%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.66 ms →       23.63 ms   (-0.13%) |      19   →      21    (+10.53%) |      449.49 ms →      496.14 ms  (+10.38%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.79 ms →        4.45 ms  (-23.26%) |      19   →      21    (+10.53%) |      110.06 ms →       93.35 ms  (-15.18%) | 
- │ │ ├ sirius::Density::mix                                            |      133.75 ms →      134.95 ms   (+0.90%) |      19   →      21    (+10.53%) |        2.54 s  →        2.83 s   (+11.52%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      856.45 μs →      292.44 μs  (-65.85%) |      19   →      21    (+10.53%) |       16.27 ms →        6.14 ms  (-62.26%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.91 ms →        4.76 ms   (-3.03%) |     229   →     259    (+13.10%) |        1.12 s  →        1.23 s    (+9.67%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.84 ms →        4.62 ms   (-4.56%) |     229   →     259    (+13.10%) |        1.11 s  →        1.20 s    (+7.94%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.84 ms →        4.62 ms   (-4.56%) |     229   →     259    (+13.10%) |        1.11 s  →        1.20 s    (+7.94%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.98 ms →        5.25 ms  (-12.20%) |      19   →      21    (+10.53%) |      113.71 ms →      110.35 ms   (-2.96%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.27 ms →        4.50 ms  (-14.58%) |      19   →      21    (+10.53%) |      100.09 ms →       94.50 ms   (-5.59%) | 
- │ │ ├ sirius::Potential::generate                                     |      361.63 ms →      360.27 ms   (-0.37%) |      19   →      21    (+10.53%) |        6.87 s  →        7.57 s   (+10.11%) | 
! │ │ │ ├ sirius::Potential::poisson                                    |       41.43 ms →       40.27 ms   (-2.80%) |      19   →      21    (+10.53%) |      787.16 ms →      845.69 ms   (+7.44%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       13.86 ms →        9.57 ms  (-30.96%) |      19   →      21    (+10.53%) |      263.33 ms →      200.94 ms  (-23.69%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.64 ms →        4.98 ms   (+7.33%) |      19   →      21    (+10.53%) |       88.20 ms →      104.63 ms  (+18.63%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.62 ms →        4.63 ms   (+0.09%) |      19   →      21    (+10.53%) |       87.81 ms →       97.14 ms  (+10.62%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms →        4.62 ms   (+0.08%) |      19   →      21    (+10.53%) |       87.80 ms →       97.12 ms  (+10.61%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      777.40 μs →      772.44 μs   (-0.64%) |      38   →      42    (+10.53%) |       29.54 ms →       32.44 ms   (+9.82%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       45.38 ms →       44.95 ms   (-0.95%) |      19   →      21    (+10.53%) |      862.19 ms →      943.89 ms   (+9.48%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.19 ms →       43.77 ms   (-0.94%) |      19   →      21    (+10.53%) |      839.54 ms →      919.17 ms   (+9.49%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      688.82 μs →      668.09 μs   (-3.01%) |      38   →      42    (+10.53%) |       26.18 ms →       28.06 ms   (+7.20%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.90 ms →        4.59 ms   (-6.26%) |      19   →      21    (+10.53%) |       93.09 ms →       96.45 ms   (+3.60%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.80 ms →        2.98 ms  (-21.50%) |      19   →      21    (+10.53%) |       72.25 ms →       62.68 ms  (-13.24%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.04 ms →      269.08 ms   (+0.39%) |      19   →      21    (+10.53%) |        5.09 s  →        5.65 s   (+10.96%) | 
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      321.05 ns →      300.48 ns   (-6.41%) |      19   →      21    (+10.53%) |        6.10 μs →        6.31 μs   (+3.44%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       98.24 ms →       96.91 ms   (-1.35%) |      19   →      21    (+10.53%) |        1.87 s  →        2.04 s    (+9.03%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       98.24 ms →       96.91 ms   (-1.35%) |      19   →      21    (+10.53%) |        1.87 s  →        2.04 s    (+9.03%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.48 ms →       14.60 ms   (+8.26%) |      19   →      21    (+10.53%) |      256.15 ms →      306.52 ms  (+19.66%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.55 ms →       69.10 ms   (-3.42%) |      19   →      21    (+10.53%) |        1.36 s  →        1.45 s    (+6.75%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.59 ms   (+0.02%) |      19   →      21    (+10.53%) |      239.19 ms →      264.42 ms  (+10.55%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.65 ms →        4.35 ms   (-6.57%) |      19   →      21    (+10.53%) |       88.42 ms →       91.31 ms   (+3.27%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.59 ms →        4.74 ms   (+3.16%) |     133   →     147    (+10.53%) |      610.55 ms →      696.13 ms  (+14.02%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.55 ms   (-0.53%) |     133   →     147    (+10.53%) |      608.35 ms →      668.80 ms   (+9.94%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.55 ms   (-0.53%) |     133   →     147    (+10.53%) |      608.26 ms →      668.73 ms   (+9.94%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.72 ms   (-4.68%) |      57   →      63    (+10.53%) |      282.41 ms →      297.54 ms   (+5.36%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.95 ms →        4.71 ms   (-4.67%) |      57   →      63    (+10.53%) |      281.87 ms →      296.98 ms   (+5.36%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.54 ms   (-0.08%) |      19   →      21    (+10.53%) |       86.41 ms →       95.43 ms  (+10.44%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       75.77 μs →      142.25 μs  (+87.74%) |      19   →      21    (+10.53%) |        1.44 ms →        2.99 ms (+107.50%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.83 μs →      137.14 μs  (+93.62%) |      19   →      21    (+10.53%) |        1.35 ms →        2.88 ms (+114.00%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.69 ms →        5.13 ms   (-9.74%) |       2   →       2              |       11.38 ms →       10.27 ms   (-9.74%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.78 ms   (-0.41%) |       6   →       6              |       28.81 ms →       28.70 ms   (-0.41%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.78 ms   (-0.41%) |       6   →       6              |       28.80 ms →       28.68 ms   (-0.41%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.78 ms   (-0.38%) |       6   →       6              |       28.78 ms →       28.68 ms   (-0.38%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.19 ms →        4.98 ms   (-4.03%) |       3   →       3              |       15.57 ms →       14.95 ms   (-4.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.19 ms →        4.98 ms   (-4.09%) |       3   →       3              |       15.56 ms →       14.93 ms   (-4.09%) | 
  ├ sirius::Periodic_function|inner                                     |        4.78 ms →        4.96 ms   (+3.86%) |       2   →       2              |        9.55 ms →        9.92 ms   (+3.86%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.77 ms →        4.77 ms   (-0.03%) |       2   →       2              |        9.54 ms →        9.54 ms   (-0.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.77 ms →        4.77 ms   (-0.02%) |       2   →       2              |        9.54 ms →        9.54 ms   (-0.02%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.15 ms →        5.10 ms   (-1.12%) |       1   →       1              |        5.15 ms →        5.10 ms   (-1.12%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.15 ms →        5.09 ms   (-1.11%) |       1   →       1              |        5.15 ms →        5.09 ms   (-1.11%) | 
- └ sirius::finalize                                                    |      146.92 ms →      194.23 ms  (+32.20%) |       1   →       1              |      146.92 ms →      194.23 ms  (+32.20%) | 
  ====================================================================================================================================================================================================
```
