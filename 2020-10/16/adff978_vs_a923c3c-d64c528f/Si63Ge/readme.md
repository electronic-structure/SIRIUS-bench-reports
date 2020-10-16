# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.04 s  →       69.87 s    (-3.01%) |       1   →       1              |       72.04 s  →       69.87 s    (-3.01%) | 
  ├ sirius::initialize                                                  |        2.84 s  →        2.88 s    (+1.35%) |       1   →       1              |        2.84 s  →        2.88 s    (+1.35%) | 
+ ├ sirius::Simulation_context::initialize                              |        4.22 s  →        3.74 s   (-11.44%) |       1   →       1              |        4.22 s  →        3.74 s   (-11.44%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       62.24 ms →       13.65 ms  (-78.07%) |       1   →       1              |       62.24 ms →       13.65 ms  (-78.07%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      489.42 ms →      160.70 ms  (-67.17%) |       1   →       1              |      489.42 ms →      160.70 ms  (-67.17%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      235.23 ms →       71.45 ms  (-69.63%) |       2   →       2              |      470.47 ms →      142.90 ms  (-69.63%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.86 ms →       17.71 ms   (-6.09%) |       1   →       1              |       18.86 ms →       17.71 ms   (-6.09%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.58 ms →        3.62 ms   (+1.08%) |       1   →       1              |        3.58 ms →        3.62 ms   (+1.08%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.23 ms →       14.03 ms   (-7.88%) |       1   →       1              |       15.23 ms →       14.03 ms   (-7.88%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.16 ms →       13.96 ms   (-7.89%) |       1   →       1              |       15.16 ms →       13.96 ms   (-7.89%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.48%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.48%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      514.77 μs →      533.90 μs   (+3.72%) |       1   →       1              |      514.77 μs →      533.90 μs   (+3.72%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.60 μs →       15.25 μs   (-8.13%) |       1   →       1              |       16.60 μs →       15.25 μs   (-8.13%) | 
  │ └ sirius::Simulation_context::update                                |        3.62 s  →        3.51 s    (-2.96%) |       1   →       1              |        3.62 s  →        3.51 s    (-2.96%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.77 ms →        6.98 ms   (+3.15%) |       1   →       1              |        6.77 ms →        6.98 ms   (+3.15%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.42 ms →        3.65 ms   (+6.75%) |       1   →       1              |        3.42 ms →        3.65 ms   (+6.75%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.27 ms   (-0.27%) |       1   →       1              |        3.28 ms →        3.27 ms   (-0.27%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.22 ms   (-0.35%) |       1   →       1              |        3.23 ms →        3.22 ms   (-0.35%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (-0.20%) |       1   →       1              |        2.70 ms →        2.70 ms   (-0.20%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      496.18 μs →      488.62 μs   (-1.52%) |       1   →       1              |      496.18 μs →      488.62 μs   (-1.52%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.84 μs →       14.21 μs   (+2.67%) |       1   →       1              |       13.84 μs →       14.21 μs   (+2.67%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.07 ms →      211.56 ms   (-0.71%) |       2   →       2              |      426.13 ms →      423.11 ms   (-0.71%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.16 ms →       15.19 ms   (+0.24%) |       2   →       2              |       30.31 ms →       30.38 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.27 ms   (-0.07%) |       1   →       1              |       13.28 ms →       13.27 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.30 ms →       56.32 ms   (+0.03%) |       2   →       2              |      112.60 ms →      112.63 ms   (+0.03%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.18 ms →       45.13 ms   (-0.11%) |       2   →       2              |       90.36 ms →       90.27 ms   (-0.11%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.39 ms →       60.28 ms   (-0.19%) |       4   →       4              |      241.58 ms →      241.11 ms   (-0.19%) | 
  │   ├ sddk::Gvec::init                                                |       93.59 ms →       92.87 ms   (-0.77%) |       2   →       2              |      187.19 ms →      185.74 ms   (-0.77%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.94 ms →       69.18 ms   (-1.10%) |       2   →       2              |      139.89 ms →      138.35 ms   (-1.10%) | 
  │   ├ sddk::Gvec_shells                                               |       92.36 ms →       98.62 ms   (+6.77%) |       1   →       1              |       92.36 ms →       98.62 ms   (+6.77%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.94 ms   (-0.02%) |       1   →       1              |        1.94 ms →        1.94 ms   (-0.02%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      666.04 ms →      615.01 ms   (-7.66%) |       2   →       2              |        1.33 s  →        1.23 s    (-7.66%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       90.97 ms →       89.04 ms   (-2.13%) |       1   →       1              |       90.97 ms →       89.04 ms   (-2.13%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.79 μs →        1.20 μs  (-33.06%) |       4   →       4              |        7.16 μs →        4.79 μs  (-33.06%) | 
  │ └ sirius::K_point_set::initialize                                   |       90.89 ms →       88.96 ms   (-2.13%) |       1   →       1              |       90.89 ms →       88.96 ms   (-2.13%) | 
  │   └ sirius::K_point::initialize                                     |       28.17 ms →       28.07 ms   (-0.37%) |       1   →       1              |       28.17 ms →       28.07 ms   (-0.37%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.91 ms →       10.88 ms   (-0.24%) |       1   →       1              |       10.91 ms →       10.88 ms   (-0.24%) | 
  │     │ └ sddk::Gvec::init                                            |        4.91 ms →        4.90 ms   (-0.21%) |       1   →       1              |        4.91 ms →        4.90 ms   (-0.21%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.40 μs →        9.64 μs   (-7.23%) |       1   →       1              |       10.40 μs →        9.64 μs   (-7.23%) | 
  │     └ sirius::K_point::update                                       |       14.41 ms →       14.39 ms   (-0.08%) |       1   →       1              |       14.41 ms →       14.39 ms   (-0.08%) | 
  │       └ sirius::Beta_projectors                                     |       10.45 ms →       10.49 ms   (+0.31%) |       1   →       1              |       10.45 ms →       10.49 ms   (+0.31%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.50 ms →        8.64 ms   (+1.63%) |       1   →       1              |        8.50 ms →        8.64 ms   (+1.63%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms →        2.56 ms   (-0.54%) |       2   →       2              |        5.15 ms →        5.12 ms   (-0.54%) | 
  ├ sirius::Potential                                                   |       50.39 ms →       48.66 ms   (-3.45%) |       1   →       1              |       50.39 ms →       48.66 ms   (-3.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.96 ms →        2.89 ms   (-2.46%) |       6   →       6              |       17.78 ms →       17.35 ms   (-2.46%) | 
  │ └ sirius::Potential::update                                         |       32.00 ms →       30.72 ms   (-4.02%) |       1   →       1              |       32.00 ms →       30.72 ms   (-4.02%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.59 ms →       30.31 ms   (-4.06%) |       1   →       1              |       31.59 ms →       30.31 ms   (-4.06%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.49 ms →       24.17 ms   (-8.74%) |       1   →       1              |       26.49 ms →       24.17 ms   (-8.74%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.50 ms →        5.63 ms  (+25.04%) |       1   →       1              |        4.50 ms →        5.63 ms  (+25.04%) | 
  ├ sirius::Density                                                     |       35.72 ms →       37.92 ms   (+6.16%) |       1   →       1              |       35.72 ms →       37.92 ms   (+6.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.80 ms   (-0.88%) |       2   →       2              |        5.65 ms →        5.60 ms   (-0.88%) | 
  │ └ sirius::Density::update                                           |       29.94 ms →       32.19 ms   (+7.52%) |       1   →       1              |       29.94 ms →       32.19 ms   (+7.52%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       29.65 ms →       31.97 ms   (+7.83%) |       1   →       1              |       29.65 ms →       31.97 ms   (+7.83%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       91.29 μs →       86.91 μs   (-4.81%) |       1   →       1              |       91.29 μs →       86.91 μs   (-4.81%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.29 ms →       24.41 ms   (-7.15%) |       1   →       1              |       26.29 ms →       24.41 ms   (-7.15%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.92 ms →        7.18 ms (+146.13%) |       1   →       1              |        2.92 ms →        7.18 ms (+146.13%) | 
  ├ sirius::Density::initial_density                                    |       55.01 ms →       55.39 ms   (+0.70%) |       1   →       1              |       55.01 ms →       55.39 ms   (+0.70%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.74 ms →       25.30 ms   (-5.38%) |       1   →       1              |       26.74 ms →       25.30 ms   (-5.38%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.66 ms →        5.38 ms  (+15.48%) |       2   →       2              |        9.32 ms →       10.77 ms  (+15.48%) | 
- │ └ sirius::Periodic_function::integrate                              |        5.15 ms →        5.75 ms  (+11.57%) |       1   →       1              |        5.15 ms →        5.75 ms  (+11.57%) | 
  ├ sirius::Potential::generate                                         |      362.00 ms →      363.13 ms   (+0.31%) |       1   →       1              |      362.00 ms →      363.13 ms   (+0.31%) | 
  │ ├ sirius::Potential::poisson                                        |       34.60 ms →       35.17 ms   (+1.64%) |       1   →       1              |       34.60 ms →       35.17 ms   (+1.64%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.66 ms →        5.94 ms  (+62.26%) |       1   →       1              |        3.66 ms →        5.94 ms  (+62.26%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        5.37 ms →        6.11 ms  (+13.81%) |       1   →       1              |        5.37 ms →        6.11 ms  (+13.81%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.65 ms   (+0.15%) |       1   →       1              |        4.64 ms →        4.65 ms   (+0.15%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.64 ms   (+0.10%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.10%) | 
- │ ├ sirius::Periodic_function::add                                    |      760.89 μs →      845.92 μs  (+11.18%) |       2   →       2              |        1.52 ms →        1.69 ms  (+11.18%) | 
  │ ├ sirius::Potential::xc                                             |       51.62 ms →       51.29 ms   (-0.65%) |       1   →       1              |       51.62 ms →       51.29 ms   (-0.65%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.44 ms →       50.11 ms   (-0.66%) |       1   →       1              |       50.44 ms →       50.11 ms   (-0.66%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.53 ms   (-0.81%) |       2   →       2              |        5.10 ms →        5.05 ms   (-0.81%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.62 ms →        4.29 ms   (-7.07%) |       1   →       1              |        4.62 ms →        4.29 ms   (-7.07%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.84 ms →        3.97 ms  (+39.65%) |       1   →       1              |        2.84 ms →        3.97 ms  (+39.65%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      270.00 ms →      269.59 ms   (-0.15%) |       1   →       1              |      270.00 ms →      269.59 ms   (-0.15%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      324.00 ns →      238.00 ns  (-26.54%) |       1   →       1              |      324.00 ns →      238.00 ns  (-26.54%) | 
+ ├ sirius::Hamiltonian0                                                |        7.81 ms →        6.32 ms  (-19.07%) |       1   →       1              |        7.81 ms →        6.32 ms  (-19.07%) | 
+ │ ├ sirius::Local_operator                                            |        7.12 ms →        5.85 ms  (-17.90%) |       1   →       1              |        7.12 ms →        5.85 ms  (-17.90%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.79 ms   (+1.54%) |       1   →       1              |        2.75 ms →        2.79 ms   (+1.54%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.30 ms →        2.30 ms  (-30.51%) |       1   →       1              |        3.30 ms →        2.30 ms  (-30.51%) | 
+ │ ├ sirius::Non_local_operator                                        |      201.97 μs →       75.79 μs  (-62.48%) |       2   →       2              |      403.94 μs →      151.57 μs  (-62.48%) | 
  │ ├ sirius::D_operator::initialize                                    |      129.81 μs →      121.71 μs   (-6.24%) |       1   →       1              |      129.81 μs →      121.71 μs   (-6.24%) | 
- │ └ sirius::Q_operator::initialize                                    |       90.42 μs →      120.90 μs  (+33.71%) |       1   →       1              |       90.42 μs →      120.90 μs  (+33.71%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.27 s    (-1.22%) |       1   →       1              |        1.28 s  →        1.27 s    (-1.22%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       64.54 ms →       38.34 ms  (-40.61%) |       1   →       1              |       64.54 ms →       38.34 ms  (-40.61%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      322.52 μs →      280.97 μs  (-12.89%) |       1   →       1              |      322.52 μs →      280.97 μs  (-12.89%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       64.22 ms →       38.05 ms  (-40.75%) |       1   →       1              |       64.22 ms →       38.05 ms  (-40.75%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.23 s    (+0.87%) |       1   →       1              |        1.22 s  →        1.23 s    (+0.87%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.07 ms →       80.18 ms  (-10.99%) |       4   →       4              |      360.28 ms →      320.71 ms  (-10.99%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       39.64 ms →       39.32 ms   (-0.81%) |       1   →       1              |       39.64 ms →       39.32 ms   (-0.81%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.00 ms →        7.97 ms   (-0.31%) |       1   →       1              |        8.00 ms →        7.97 ms   (-0.31%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      380.62 ms →      313.08 ms  (-17.75%) |       1   →       1              |      380.62 ms →      313.08 ms  (-17.75%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      307.21 ms →      245.34 ms  (-20.14%) |       1   →       1              |      307.21 ms →      245.34 ms  (-20.14%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.57 μs →        4.02 μs  (-11.89%) |       1   →       1              |        4.57 μs →        4.02 μs  (-11.89%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.59 μs →        3.10 μs  (-13.60%) |       1   →       1              |        3.59 μs →        3.10 μs  (-13.60%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      522.00 ns →      395.00 ns  (-24.33%) |       1   →       1              |      522.00 ns →      395.00 ns  (-24.33%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      814.00 ns →      544.00 ns  (-33.17%) |       1   →       1              |      814.00 ns →      544.00 ns  (-33.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.13 ms →        3.19 ms   (+2.11%) |       1   →       1              |        3.13 ms →        3.19 ms   (+2.11%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       24.59 ms →       21.31 ms  (-13.33%) |       1   →       1              |       24.59 ms →       21.31 ms  (-13.33%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       22.83 ms →       21.59 ms   (-5.40%) |       2   →       2              |       45.65 ms →       43.19 ms   (-5.40%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        6.59 ms →       15.94 ms (+142.01%) |       2   →       2              |       13.17 ms →       31.87 ms (+142.01%) | 
- │ │ │ └ sddk::wf_inner                                                |        6.37 ms →       15.73 ms (+147.02%) |       2   →       2              |       12.73 ms →       31.45 ms (+147.02%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.50 ns →       19.50 ns   (-9.30%) |       2   →       2              |       43.00 ns →       39.00 ns   (-9.30%) | 
- │ │ │   ├ sddk::wf_inner|pw                                           |        6.22 ms →       15.60 ms (+150.99%) |       2   →       2              |       12.43 ms →       31.20 ms (+150.99%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       21.50 ns →       18.50 ns  (-13.95%) |       2   →       2              |       43.00 ns →       37.00 ns  (-13.95%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      200.72 ms →      249.95 ms  (+24.53%) |       1   →       1              |      200.72 ms →      249.95 ms  (+24.53%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.60 ms   (+0.16%) |       1   →       1              |        2.60 ms →        2.60 ms   (+0.16%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.60 ms   (+0.18%) |       1   →       1              |        2.59 ms →        2.60 ms   (+0.18%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      540.00 ns →      332.00 ns  (-38.52%) |       1   →       1              |      540.00 ns →      332.00 ns  (-38.52%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.98 s  →       60.26 s    (-2.77%) |       1   →       1              |       61.98 s  →       60.26 s    (-2.77%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.45 ms   (-0.97%) |      19   →      19              |       47.01 ms →       46.56 ms   (-0.97%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        3.00 s    (-7.62%) |      19   →      20     (+5.26%) |       61.75 s  →       60.05 s    (-2.75%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.36 ms →        5.15 ms   (-3.88%) |      19   →      20     (+5.26%) |      101.86 ms →      103.06 ms   (+1.18%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.64 ms →        4.50 ms   (-3.10%) |      19   →      20     (+5.26%) |       88.23 ms →       90.00 ms   (+2.00%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      549.89 μs →      556.62 μs   (+1.22%) |      19   →      20     (+5.26%) |       10.45 ms →       11.13 ms   (+6.55%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.87 ms →        2.94 ms   (+2.24%) |      19   →      20     (+5.26%) |       54.57 ms →       58.73 ms   (+7.62%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      212.65 μs →      183.97 μs  (-13.49%) |      38   →      40     (+5.26%) |        8.08 ms →        7.36 ms   (-8.93%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      120.28 μs →      111.81 μs   (-7.04%) |      19   →      20     (+5.26%) |        2.29 ms →        2.24 ms   (-2.15%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       92.31 μs →       92.19 μs   (-0.13%) |      19   →      20     (+5.26%) |        1.75 ms →        1.84 ms   (+5.13%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.79 s   (-11.63%) |      19   →      20     (+5.26%) |       38.51 s  →       35.82 s    (-6.98%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      216.35 μs →      273.02 μs  (+26.19%) |      19   →      20     (+5.26%) |        4.11 ms →        5.46 ms  (+32.83%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      207.06 μs →      264.57 μs  (+27.78%) |      19   →      20     (+5.26%) |        3.93 ms →        5.29 ms  (+34.50%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.84 μs →        6.11 μs  (-10.64%) |      19   →      20     (+5.26%) |      129.98 μs →      122.26 μs   (-5.94%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.63 s   (-17.15%) |      19   →      20     (+5.26%) |       37.29 s  →       32.53 s   (-12.79%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.15 ms →       68.30 ms  (-11.47%) |      19   →      20     (+5.26%) |        1.47 s  →        1.37 s    (-6.81%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.98 ms →        7.53 ms   (-5.68%) |     114   →     120     (+5.26%) |      909.61 ms →      903.12 ms   (-0.71%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.42 ms →       16.31 ms  (-11.42%) |      19   →      20     (+5.26%) |      349.95 ms →      326.30 ms   (-6.76%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      462.79 μs →      456.01 μs   (-1.47%) |      19   →      20     (+5.26%) |        8.79 ms →        9.12 ms   (+3.72%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.43 ms →        7.19 ms  (-14.75%) |      38   →      40     (+5.26%) |      320.31 ms →      287.42 ms  (-10.27%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.53 s   (-17.51%) |      19   →      20     (+5.26%) |       35.29 s  →       30.65 s   (-13.16%) | 
! │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       51.61 ms →       55.93 ms   (+8.36%) |     356   →     301    (-15.45%) |       18.37 s  →       16.83 s    (-8.38%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.86 ms →       34.52 ms  (+19.62%) |     356   →     301    (-15.45%) |       10.27 s  →       10.39 s    (+1.14%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.04 μs →        2.24 μs   (+9.90%) |     356   →     301    (-15.45%) |      725.09 μs →      673.78 μs   (-7.08%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.73 μs →        1.92 μs  (+10.90%) |     356   →     301    (-15.45%) |      615.38 μs →      577.03 μs   (-6.23%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      436.51 ns →      406.95 ns   (-6.77%) |     356   →     301    (-15.45%) |      155.40 μs →      122.49 μs  (-21.17%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      551.94 ns →      569.61 ns   (+3.20%) |     356   →     301    (-15.45%) |      196.49 μs →      171.45 μs  (-12.74%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.94 ms →        2.75 ms   (-6.41%) |     356   →     301    (-15.45%) |        1.05 s  →      828.45 ms  (-20.87%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.33 ms →        3.58 ms   (+7.58%) |     356   →     301    (-15.45%) |        1.18 s  →        1.08 s    (-9.04%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.24 ms →        7.53 ms   (-8.55%) |     712   →     602    (-15.45%) |        5.86 s  →        4.53 s   (-22.68%) | 
! │ │ │ │   ├ sddk::orthogonalize                                       |        6.49 ms →        7.06 ms   (+8.67%) |     356   →     301    (-15.45%) |        2.31 s  →        2.12 s    (-8.12%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.10 ms →        1.08 ms   (-1.45%) |     693   →     582    (-16.02%) |      761.87 ms →      630.59 ms  (-17.23%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       53.45 ns →       46.06 ns  (-13.84%) |     693   →     582    (-16.02%) |       37.04 μs →       26.80 μs  (-27.64%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      938.97 μs →      920.54 μs   (-1.96%) |     693   →     582    (-16.02%) |      650.70 ms →      535.75 ms  (-17.67%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.41 ns →       36.38 ns  (-19.87%) |     693   →     582    (-16.02%) |       31.47 μs →       21.18 μs  (-32.71%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      133.81 μs →      166.16 μs  (+24.18%) |     356   →     301    (-15.45%) |       47.64 ms →       50.02 ms   (+4.99%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.92 ms →        2.43 ms  (+26.63%) |     356   →     301    (-15.45%) |      684.44 ms →      732.82 ms   (+7.07%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |        2.42 ms →        2.52 ms   (+4.19%) |     337   →     281    (-16.62%) |      816.07 ms →      708.99 ms  (-13.12%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |      806.40 μs →      840.22 μs   (+4.19%) |    1.01 K →     843    (-16.62%) |      815.27 ms →      708.31 ms  (-13.12%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.44 ms →        1.36 ms   (-5.53%) |     356   →     301    (-15.45%) |      512.56 ms →      409.42 ms  (-20.12%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.37 ms →        1.31 ms   (-4.06%) |     356   →     301    (-15.45%) |      487.30 ms →      395.29 ms  (-18.88%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.40 ns →       50.93 ns  (+23.02%) |     356   →     301    (-15.45%) |       14.74 μs →       15.33 μs   (+4.02%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.21 ms →        1.15 ms   (-4.84%) |     356   →     301    (-15.45%) |      429.48 ms →      345.55 ms  (-19.54%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.19 ns →       44.58 ns   (+3.24%) |     356   →     301    (-15.45%) |       15.37 μs →       13.42 μs  (-12.71%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       35.86 ms →       33.54 ms   (-6.49%) |     356   →     301    (-15.45%) |       12.77 s  →       10.09 s   (-20.94%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.69 ms →        2.54 ms   (-5.46%) |     340   →     289    (-15.00%) |      914.83 ms →      735.15 ms  (-19.64%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.38 ms →        1.26 ms   (-8.97%) |     337   →     281    (-16.62%) |      466.63 ms →      354.19 ms  (-24.10%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      690.94 μs →      628.80 μs   (-8.99%) |     674   →     562    (-16.62%) |      465.69 ms →      353.39 ms  (-24.12%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.20 ms →        1.23 ms   (+2.41%) |     337   →     281    (-16.62%) |      403.42 ms →      344.49 ms  (-14.61%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.52 ms →        5.29 ms  (-29.65%) |      54   →      84    (+55.56%) |      406.35 ms →      444.68 ms   (+9.43%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        4.52 ms →        2.95 ms  (-34.59%) |      89   →     148    (+66.29%) |      401.89 ms →      437.15 ms   (+8.77%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        3.24 ms →        2.06 ms  (-36.39%) |     124   →     212    (+70.97%) |      401.73 ms →      436.87 ms   (+8.75%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      362.42 ns →      414.45 ns  (+14.36%) |      19   →      20     (+5.26%) |        6.89 μs →        8.29 μs  (+20.37%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.55 μs →       19.97 μs   (+2.14%) |      19   →      20     (+5.26%) |      371.38 μs →      399.30 μs   (+7.52%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.52 ms   (+0.05%) |      19   →      20     (+5.26%) |       28.78 ms →       30.32 ms   (+5.32%) | 
  │ │ ├ sirius::Density::generate                                       |      575.46 ms →      563.08 ms   (-2.15%) |      19   →      20     (+5.26%) |       10.93 s  →       11.26 s    (+3.00%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      411.66 ms →      404.28 ms   (-1.79%) |      19   →      20     (+5.26%) |        7.82 s  →        8.09 s    (+3.38%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.36 μs →        8.50 μs   (+1.63%) |      19   →      20     (+5.26%) |      158.93 μs →      170.02 μs   (+6.98%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.78 μs →        8.00 μs   (+2.80%) |      19   →      20     (+5.26%) |      147.91 μs →      160.06 μs   (+8.21%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       38.16 ms →       18.91 ms  (-50.43%) |      19   →      20     (+5.26%) |      724.96 ms →      378.30 ms  (-47.82%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.71 μs →        8.34 μs   (+8.19%) |      19   →      20     (+5.26%) |      146.51 μs →      166.85 μs  (+13.89%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.33 ms →        3.18 ms  (-49.82%) |      19   →      20     (+5.26%) |      120.26 ms →       63.53 ms  (-47.17%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       30.76 ms →       14.67 ms  (-52.31%) |      19   →      20     (+5.26%) |      584.43 ms →      293.38 ms  (-49.80%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      517.05 ns →      900.25 ns  (+74.11%) |      19   →      20     (+5.26%) |        9.82 μs →       18.00 μs  (+83.28%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      107.87 ms →      127.19 ms  (+17.91%) |      19   →      20     (+5.26%) |        2.05 s  →        2.54 s   (+24.12%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.13 ms →        2.07 ms   (-2.74%) |      19   →      20     (+5.26%) |       40.45 ms →       41.42 ms   (+2.38%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      224.56 ms →      220.83 ms   (-1.66%) |      19   →      20     (+5.26%) |        4.27 s  →        4.42 s    (+3.52%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      224.33 ms →      220.61 ms   (-1.66%) |      19   →      20     (+5.26%) |        4.26 s  →        4.41 s    (+3.52%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      131.61 ms →      131.76 ms   (+0.11%) |      19   →      20     (+5.26%) |        2.50 s  →        2.64 s    (+5.38%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      131.61 ms →      131.76 ms   (+0.11%) |      19   →      20     (+5.26%) |        2.50 s  →        2.64 s    (+5.38%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       47.96 ms →       48.37 ms   (+0.86%) |      19   →      20     (+5.26%) |      911.23 ms →      967.48 ms   (+6.17%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.30 ms →       70.36 ms   (+0.08%) |      19   →      20     (+5.26%) |        1.34 s  →        1.41 s    (+5.35%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.69 ms →       12.37 ms   (-2.49%) |      19   →      20     (+5.26%) |      241.12 ms →      247.48 ms   (+2.64%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       28.17 ms →       23.72 ms  (-15.82%) |      19   →      20     (+5.26%) |      535.26 ms →      474.31 ms  (-11.39%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.01 ms →        3.32 ms  (-17.37%) |      19   →      20     (+5.26%) |       76.27 ms →       66.34 ms  (-13.02%) | 
  │ │ ├ sirius::Density::mix                                            |      132.91 ms →      133.09 ms   (+0.14%) |      19   →      20     (+5.26%) |        2.53 s  →        2.66 s    (+5.41%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      939.34 μs →      284.48 μs  (-69.72%) |      19   →      20     (+5.26%) |       17.85 ms →        5.69 ms  (-68.12%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.84 ms →        4.85 ms   (+0.25%) |     229   →     244     (+6.55%) |        1.11 s  →        1.18 s    (+6.82%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.64 ms   (-3.58%) |     229   →     244     (+6.55%) |        1.10 s  →        1.13 s    (+2.74%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.64 ms   (-3.58%) |     229   →     244     (+6.55%) |        1.10 s  →        1.13 s    (+2.73%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        4.86 ms →        6.17 ms  (+26.97%) |      19   →      20     (+5.26%) |       92.27 ms →      123.32 ms  (+33.65%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.11 ms →        5.44 ms  (+32.40%) |      19   →      20     (+5.26%) |       78.08 ms →      108.81 ms  (+39.37%) | 
  │ │ ├ sirius::Potential::generate                                     |      355.43 ms →      355.85 ms   (+0.12%) |      19   →      20     (+5.26%) |        6.75 s  →        7.12 s    (+5.39%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       34.88 ms →       35.56 ms   (+1.93%) |      19   →      20     (+5.26%) |      662.74 ms →      711.11 ms   (+7.30%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.27 ms →        6.45 ms  (+50.96%) |      19   →      20     (+5.26%) |       81.14 ms →      128.93 ms  (+58.90%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.03 ms →        5.91 ms  (+17.50%) |      19   →      20     (+5.26%) |       95.62 ms →      118.27 ms  (+23.69%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.08%) |      19   →      20     (+5.26%) |       87.98 ms →       92.68 ms   (+5.35%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.08%) |      19   →      20     (+5.26%) |       87.96 ms →       92.66 ms   (+5.35%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      763.70 μs →      812.09 μs   (+6.34%) |      38   →      40     (+5.26%) |       29.02 ms →       32.48 ms  (+11.93%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.06 ms →       44.59 ms   (-1.05%) |      19   →      20     (+5.26%) |      856.13 ms →      891.71 ms   (+4.16%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.88 ms →       43.41 ms   (-1.06%) |      19   →      20     (+5.26%) |      833.63 ms →      868.24 ms   (+4.15%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      686.26 μs →      688.84 μs   (+0.38%) |      38   →      40     (+5.26%) |       26.08 ms →       27.55 ms   (+5.66%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.53 ms →        4.18 ms   (-7.72%) |      19   →      20     (+5.26%) |       86.01 ms →       83.54 ms   (-2.87%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        2.88 ms →        3.95 ms  (+37.16%) |      19   →      20     (+5.26%) |       54.67 ms →       78.93 ms  (+44.38%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.66 ms →      268.70 ms   (-0.36%) |      19   →      20     (+5.26%) |        5.12 s  →        5.37 s    (+4.89%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      308.53 ns →      235.50 ns  (-23.67%) |      19   →      20     (+5.26%) |        5.86 μs →        4.71 μs  (-19.65%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.35 ms →       96.64 ms   (+0.30%) |      19   →      20     (+5.26%) |        1.83 s  →        1.93 s    (+5.58%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.35 ms →       96.64 ms   (+0.30%) |      19   →      20     (+5.26%) |        1.83 s  →        1.93 s    (+5.58%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.55 ms →       13.45 ms   (-0.73%) |      19   →      20     (+5.26%) |      257.49 ms →      269.06 ms   (+4.49%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.57 ms →       70.01 ms   (+0.64%) |      19   →      20     (+5.26%) |        1.32 s  →        1.40 s    (+5.93%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.54 ms   (-0.37%) |      19   →      20     (+5.26%) |      239.23 ms →      250.90 ms   (+4.88%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.24 ms →        3.44 ms  (-18.97%) |      19   →      20     (+5.26%) |       80.57 ms →       68.72 ms  (-14.71%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.63 ms →        4.82 ms   (+4.18%) |     133   →     140     (+5.26%) |      615.18 ms →      674.62 ms   (+9.66%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.61 ms   (+0.92%) |     133   →     140     (+5.26%) |      606.90 ms →      644.72 ms   (+6.23%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.60 ms   (+0.92%) |     133   →     140     (+5.26%) |      606.82 ms →      644.63 ms   (+6.23%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        5.03 ms →        4.82 ms   (-4.20%) |      57   →      60     (+5.26%) |      286.59 ms →      289.01 ms   (+0.85%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        5.02 ms →        4.80 ms   (-4.35%) |      57   →      60     (+5.26%) |      286.21 ms →      288.15 ms   (+0.68%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.55 ms   (+0.51%) |      19   →      20     (+5.26%) |       86.00 ms →       90.99 ms   (+5.81%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       77.15 μs →       75.39 μs   (-2.28%) |      19   →      20     (+5.26%) |        1.47 ms →        1.51 ms   (+2.87%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.02 μs →       70.31 μs   (-2.38%) |      19   →      20     (+5.26%) |        1.37 ms →        1.41 ms   (+2.76%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.69 ms →        5.68 ms   (-0.14%) |       2   →       2              |       11.37 ms →       11.36 ms   (-0.14%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.69 ms   (-2.29%) |       6   →       6              |       28.80 ms →       28.14 ms   (-2.29%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.68 ms   (-2.33%) |       6   →       6              |       28.78 ms →       28.11 ms   (-2.33%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.79 ms →        4.68 ms   (-2.30%) |       6   →       6              |       28.77 ms →       28.11 ms   (-2.30%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.27 ms →        4.83 ms   (-8.32%) |       3   →       3              |       15.82 ms →       14.50 ms   (-8.32%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.27 ms →        4.82 ms   (-8.44%) |       3   →       3              |       15.81 ms →       14.47 ms   (-8.44%) | 
  ├ sirius::Periodic_function|inner                                     |        4.54 ms →        4.63 ms   (+2.01%) |       2   →       2              |        9.07 ms →        9.25 ms   (+2.01%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.62 ms   (+2.01%) |       2   →       2              |        9.06 ms →        9.25 ms   (+2.01%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.62 ms   (+2.01%) |       2   →       2              |        9.06 ms →        9.25 ms   (+2.01%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.91 ms →        4.82 ms   (-1.78%) |       1   →       1              |        4.91 ms →        4.82 ms   (-1.78%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.90 ms →        4.82 ms   (-1.77%) |       1   →       1              |        4.90 ms →        4.82 ms   (-1.77%) | 
- └ sirius::finalize                                                    |      206.88 ms →      555.67 ms (+168.59%) |       1   →       1              |      206.88 ms →      555.67 ms (+168.59%) | 
  ====================================================================================================================================================================================================
```
