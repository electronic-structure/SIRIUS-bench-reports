# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.45 s  →       72.45 s    (+1.41%) |       1   →       1              |       71.45 s  →       72.45 s    (+1.41%) | 
  ├ sirius::initialize                                                  |        2.87 s  →        2.86 s    (-0.56%) |       1   →       1              |        2.87 s  →        2.86 s    (-0.56%) | 
  ├ sirius::Simulation_context::initialize                              |        3.57 s  →        3.82 s    (+6.95%) |       1   →       1              |        3.57 s  →        3.82 s    (+6.95%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       33.03 ms →       31.10 ms   (-5.85%) |       1   →       1              |       33.03 ms →       31.10 ms   (-5.85%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      132.76 ms →      183.44 ms  (+38.17%) |       1   →       1              |      132.76 ms →      183.44 ms  (+38.17%) | 
- │ │ ├ sirius::Atom_type::init                                         |       58.18 ms →       82.90 ms  (+42.47%) |       2   →       2              |      116.37 ms →      165.79 ms  (+42.47%) | 
  │ │ └ sirius::Unit_cell::update                                       |       16.30 ms →       17.54 ms   (+7.58%) |       1   →       1              |       16.30 ms →       17.54 ms   (+7.58%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.84 ms →        3.74 ms   (-2.59%) |       1   →       1              |        3.84 ms →        3.74 ms   (-2.59%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       12.37 ms →       13.73 ms  (+10.97%) |       1   →       1              |       12.37 ms →       13.73 ms  (+10.97%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       12.31 ms →       13.66 ms  (+10.99%) |       1   →       1              |       12.31 ms →       13.66 ms  (+10.99%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.82 ms →        2.74 ms   (-2.67%) |       1   →       1              |        2.82 ms →        2.74 ms   (-2.67%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      495.56 μs →      493.57 μs   (-0.40%) |       1   →       1              |      495.56 μs →      493.57 μs   (-0.40%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.39 μs →       15.84 μs   (+2.92%) |       1   →       1              |       15.39 μs →       15.84 μs   (+2.92%) | 
  │ └ sirius::Simulation_context::update                                |        3.32 s  →        3.41 s    (+2.53%) |       1   →       1              |        3.32 s  →        3.41 s    (+2.53%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.85 ms →        7.04 ms   (+2.69%) |       1   →       1              |        6.85 ms →        7.04 ms   (+2.69%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.49 ms →        3.65 ms   (+4.67%) |       1   →       1              |        3.49 ms →        3.65 ms   (+4.67%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.32 ms →        3.35 ms   (+0.93%) |       1   →       1              |        3.32 ms →        3.35 ms   (+0.93%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.28 ms   (+0.27%) |       1   →       1              |        3.27 ms →        3.28 ms   (+0.27%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.71 ms   (-0.61%) |       1   →       1              |        2.73 ms →        2.71 ms   (-0.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      502.86 μs →      522.81 μs   (+3.97%) |       1   →       1              |      502.86 μs →      522.81 μs   (+3.97%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       15.12 μs →       14.63 μs   (-3.23%) |       1   →       1              |       15.12 μs →       14.63 μs   (-3.23%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.23 ms →      211.82 ms   (-0.19%) |       2   →       2              |      424.46 ms →      423.65 ms   (-0.19%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.14 ms →       15.15 ms   (+0.11%) |       2   →       2              |       30.27 ms →       30.30 ms   (+0.11%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.28 ms   (+0.21%) |       1   →       1              |       13.25 ms →       13.28 ms   (+0.21%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.43 ms →       56.29 ms   (-0.25%) |       2   →       2              |      112.86 ms →      112.58 ms   (-0.25%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.03 ms →       45.08 ms   (+0.10%) |       2   →       2              |       90.07 ms →       90.16 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.15 ms →       60.30 ms   (+0.25%) |       4   →       4              |      240.58 ms →      241.19 ms   (+0.25%) | 
  │   ├ sddk::Gvec::init                                                |       94.73 ms →       93.17 ms   (-1.65%) |       2   →       2              |      189.47 ms →      186.35 ms   (-1.65%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.10 ms →       69.88 ms   (-1.72%) |       2   →       2              |      142.20 ms →      139.76 ms   (-1.72%) | 
+ │   ├ sddk::Gvec_shells                                               |      103.88 ms →       92.64 ms  (-10.82%) |       1   →       1              |      103.88 ms →       92.64 ms  (-10.82%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.95 ms   (+0.66%) |       1   →       1              |        1.94 ms →        1.95 ms   (+0.66%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      522.93 ms →      553.47 ms   (+5.84%) |       2   →       2              |        1.05 s  →        1.11 s    (+5.84%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      162.86 ms →      151.22 ms   (-7.14%) |       1   →       1              |      162.86 ms →      151.22 ms   (-7.14%) | 
- │ ├ sirius::K_point::K_point                                          |        1.56 μs →        2.56 μs  (+64.71%) |       4   →       4              |        6.23 μs →       10.25 μs  (+64.71%) | 
  │ └ sirius::K_point_set::initialize                                   |      162.77 ms →      151.14 ms   (-7.15%) |       1   →       1              |      162.77 ms →      151.14 ms   (-7.15%) | 
  │   └ sirius::K_point::initialize                                     |       29.45 ms →       28.16 ms   (-4.38%) |       1   →       1              |       29.45 ms →       28.16 ms   (-4.38%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.41 ms →       11.06 ms   (-3.09%) |       1   →       1              |       11.41 ms →       11.06 ms   (-3.09%) | 
  │     │ └ sddk::Gvec::init                                            |        5.29 ms →        4.98 ms   (-5.78%) |       1   →       1              |        5.29 ms →        4.98 ms   (-5.78%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.28 μs →        7.97 μs  (-29.35%) |       1   →       1              |       11.28 μs →        7.97 μs  (-29.35%) | 
  │     └ sirius::K_point::update                                       |       15.10 ms →       14.27 ms   (-5.51%) |       1   →       1              |       15.10 ms →       14.27 ms   (-5.51%) | 
  │       └ sirius::Beta_projectors                                     |       10.79 ms →       10.29 ms   (-4.63%) |       1   →       1              |       10.79 ms →       10.29 ms   (-4.63%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.57 ms →        8.31 ms   (-2.98%) |       1   →       1              |        8.57 ms →        8.31 ms   (-2.98%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms →        2.57 ms   (-0.28%) |       2   →       2              |        5.15 ms →        5.13 ms   (-0.28%) | 
  ├ sirius::Potential                                                   |       52.69 ms →       54.92 ms   (+4.23%) |       1   →       1              |       52.69 ms →       54.92 ms   (+4.23%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.95 ms →        2.91 ms   (-1.49%) |       6   →       6              |       17.71 ms →       17.45 ms   (-1.49%) | 
  │ └ sirius::Potential::update                                         |       34.43 ms →       36.89 ms   (+7.15%) |       1   →       1              |       34.43 ms →       36.89 ms   (+7.15%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.99 ms →       36.50 ms   (+7.37%) |       1   →       1              |       33.99 ms →       36.50 ms   (+7.37%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       24.15 ms →       32.10 ms  (+32.92%) |       1   →       1              |       24.15 ms →       32.10 ms  (+32.92%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.33 ms →        3.83 ms  (-58.94%) |       1   →       1              |        9.33 ms →        3.83 ms  (-58.94%) | 
  ├ sirius::Density                                                     |       42.47 ms →       42.33 ms   (-0.32%) |       1   →       1              |       42.47 ms →       42.33 ms   (-0.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.83 ms   (-0.02%) |       2   →       2              |        5.65 ms →        5.65 ms   (-0.02%) | 
  │ └ sirius::Density::update                                           |       36.68 ms →       36.54 ms   (-0.38%) |       1   →       1              |       36.68 ms →       36.54 ms   (-0.38%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.45 ms →       36.26 ms   (-0.52%) |       1   →       1              |       36.45 ms →       36.26 ms   (-0.52%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       75.75 μs →       78.27 μs   (+3.33%) |       1   →       1              |       75.75 μs →       78.27 μs   (+3.33%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       24.19 ms →       32.94 ms  (+36.20%) |       1   →       1              |       24.19 ms →       32.94 ms  (+36.20%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.89 ms →        2.90 ms  (-75.65%) |       1   →       1              |       11.89 ms →        2.90 ms  (-75.65%) | 
  ├ sirius::Density::initial_density                                    |       61.87 ms →       65.15 ms   (+5.30%) |       1   →       1              |       61.87 ms →       65.15 ms   (+5.30%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       25.13 ms →       36.91 ms  (+46.87%) |       1   →       1              |       25.13 ms →       36.91 ms  (+46.87%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        8.68 ms →        4.58 ms  (-47.19%) |       2   →       2              |       17.35 ms →        9.16 ms  (-47.19%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.73 ms →        5.31 ms   (-7.40%) |       1   →       1              |        5.73 ms →        5.31 ms   (-7.40%) | 
  ├ sirius::Potential::generate                                         |      370.44 ms →      373.59 ms   (+0.85%) |       1   →       1              |      370.44 ms →      373.59 ms   (+0.85%) | 
  │ ├ sirius::Potential::poisson                                        |       43.13 ms →       45.05 ms   (+4.45%) |       1   →       1              |       43.13 ms →       45.05 ms   (+4.45%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       14.31 ms →        2.91 ms  (-79.67%) |       1   →       1              |       14.31 ms →        2.91 ms  (-79.67%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.75 ms →        5.38 ms   (-6.54%) |       1   →       1              |        5.75 ms →        5.38 ms   (-6.54%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.65 ms →        4.58 ms   (-1.36%) |       1   →       1              |        4.65 ms →        4.58 ms   (-1.36%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.58 ms   (-1.30%) |       1   →       1              |        4.64 ms →        4.58 ms   (-1.30%) | 
  │ ├ sirius::Periodic_function::add                                    |      802.87 μs →      780.07 μs   (-2.84%) |       2   →       2              |        1.61 ms →        1.56 ms   (-2.84%) | 
  │ ├ sirius::Potential::xc                                             |       51.70 ms →       52.49 ms   (+1.53%) |       1   →       1              |       51.70 ms →       52.49 ms   (+1.53%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.49 ms →       51.28 ms   (+1.58%) |       1   →       1              |       50.49 ms →       51.28 ms   (+1.58%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.59 ms →        2.54 ms   (-1.82%) |       2   →       2              |        5.18 ms →        5.09 ms   (-1.82%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.65 ms →        4.11 ms  (-11.66%) |       1   →       1              |        4.65 ms →        4.11 ms  (-11.66%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.68 ms →        3.82 ms   (+3.77%) |       1   →       1              |        3.68 ms →        3.82 ms   (+3.77%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.94 ms →      269.25 ms   (+0.12%) |       1   →       1              |      268.94 ms →      269.25 ms   (+0.12%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      277.00 ns →      248.00 ns  (-10.47%) |       1   →       1              |      277.00 ns →      248.00 ns  (-10.47%) | 
+ ├ sirius::Hamiltonian0                                                |        8.38 ms →        6.77 ms  (-19.19%) |       1   →       1              |        8.38 ms →        6.77 ms  (-19.19%) | 
+ │ ├ sirius::Local_operator                                            |        7.32 ms →        6.34 ms  (-13.38%) |       1   →       1              |        7.32 ms →        6.34 ms  (-13.38%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.25%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.25%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.56 ms →        2.80 ms  (-21.23%) |       1   →       1              |        3.56 ms →        2.80 ms  (-21.23%) | 
+ │ ├ sirius::Non_local_operator                                        |      399.87 μs →       71.05 μs  (-82.23%) |       2   →       2              |      799.75 μs →      142.10 μs  (-82.23%) | 
- │ ├ sirius::D_operator::initialize                                    |      102.91 μs →      123.75 μs  (+20.25%) |       1   →       1              |      102.91 μs →      123.75 μs  (+20.25%) | 
  │ └ sirius::Q_operator::initialize                                    |       90.69 μs →       92.86 μs   (+2.40%) |       1   →       1              |       90.69 μs →       92.86 μs   (+2.40%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.28 s    (-1.32%) |       1   →       1              |        1.30 s  →        1.28 s    (-1.32%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       60.91 ms →       51.25 ms  (-15.86%) |       1   →       1              |       60.91 ms →       51.25 ms  (-15.86%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      227.95 μs →      300.79 μs  (+31.96%) |       1   →       1              |      227.95 μs →      300.79 μs  (+31.96%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       60.68 ms →       50.94 ms  (-16.05%) |       1   →       1              |       60.68 ms →       50.94 ms  (-16.05%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.23 s    (-0.61%) |       1   →       1              |        1.24 s  →        1.23 s    (-0.61%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.19 ms →       77.19 ms   (-1.28%) |       4   →       4              |      312.75 ms →      308.75 ms   (-1.28%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.31 ms →       43.85 ms  (-17.75%) |       1   →       1              |       53.31 ms →       43.85 ms  (-17.75%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.82 ms →        8.81 ms   (-0.10%) |       1   →       1              |        8.82 ms →        8.81 ms   (-0.10%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.39 ms →      313.55 ms   (-0.58%) |       1   →       1              |      315.39 ms →      313.55 ms   (-0.58%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.40 ms →      246.08 ms   (+0.28%) |       1   →       1              |      245.40 ms →      246.08 ms   (+0.28%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.13 μs →        3.58 μs  (-13.14%) |       1   →       1              |        4.13 μs →        3.58 μs  (-13.14%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.21 μs →        2.60 μs  (-18.93%) |       1   →       1              |        3.21 μs →        2.60 μs  (-18.93%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      460.00 ns →      603.00 ns  (+31.09%) |       1   →       1              |      460.00 ns →      603.00 ns  (+31.09%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      929.00 ns →      583.00 ns  (-37.24%) |       1   →       1              |      929.00 ns →      583.00 ns  (-37.24%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.22 ms →        3.13 ms   (-2.70%) |       1   →       1              |        3.22 ms →        3.13 ms   (-2.70%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.32 ms →       21.30 ms   (-0.07%) |       1   →       1              |       21.32 ms →       21.30 ms   (-0.07%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       22.70 ms →       21.50 ms   (-5.30%) |       2   →       2              |       45.40 ms →       43.00 ms   (-5.30%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.84 ms →       16.23 ms   (+9.39%) |       2   →       2              |       29.68 ms →       32.46 ms   (+9.39%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.63 ms →       16.02 ms   (+9.54%) |       2   →       2              |       29.25 ms →       32.04 ms   (+9.54%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |      126.50 ns →       19.00 ns  (-84.98%) |       2   →       2              |      253.00 ns →       38.00 ns  (-84.98%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.50 ms →       15.89 ms   (+9.61%) |       2   →       2              |       28.99 ms →       31.78 ms   (+9.61%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       21.00 ns →       23.50 ns  (+11.90%) |       2   →       2              |       42.00 ns →       47.00 ns  (+11.90%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.93 ms →      250.34 ms   (+0.16%) |       1   →       1              |      249.93 ms →      250.34 ms   (+0.16%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.61 ms   (+0.51%) |       1   →       1              |        2.60 ms →        2.61 ms   (+0.51%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.61 ms   (+0.52%) |       1   →       1              |        2.59 ms →        2.61 ms   (+0.52%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      485.00 ns →      479.00 ns   (-1.24%) |       1   →       1              |      485.00 ns →      479.00 ns   (-1.24%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.88 s  →       62.68 s    (+1.28%) |       1   →       1              |       61.88 s  →       62.68 s    (+1.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.44 ms   (-0.57%) |      19   →      19              |       46.68 ms →       46.42 ms   (-0.57%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.24 s  →        2.97 s    (-8.38%) |      19   →      21    (+10.53%) |       61.65 s  →       62.43 s    (+1.26%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        5.62 ms →        5.15 ms   (-8.30%) |      19   →      21    (+10.53%) |      106.77 ms →      108.21 ms   (+1.36%) | 
! │ │ │ ├ sirius::Local_operator                                        |        4.87 ms →        4.47 ms   (-8.36%) |      19   →      21    (+10.53%) |       92.60 ms →       93.80 ms   (+1.29%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      562.45 μs →      555.31 μs   (-1.27%) |      19   →      21    (+10.53%) |       10.69 ms →       11.66 ms   (+9.12%) | 
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.04 ms →        2.83 ms   (-6.82%) |      19   →      21    (+10.53%) |       57.77 ms →       59.50 ms   (+2.99%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      229.69 μs →      198.05 μs  (-13.78%) |      38   →      42    (+10.53%) |        8.73 ms →        8.32 ms   (-4.70%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      115.63 μs →      121.11 μs   (+4.74%) |      19   →      21    (+10.53%) |        2.20 ms →        2.54 ms  (+15.76%) | 
! │ │ │ └ sirius::Q_operator::initialize                                |       91.58 μs →       90.95 μs   (-0.69%) |      19   →      21    (+10.53%) |        1.74 ms →        1.91 ms   (+9.76%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.02 s  →        1.75 s   (-13.31%) |      19   →      21    (+10.53%) |       38.42 s  →       36.82 s    (-4.18%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      224.53 μs →      246.89 μs   (+9.96%) |      19   →      21    (+10.53%) |        4.27 ms →        5.18 ms  (+21.54%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      214.78 μs →      237.92 μs  (+10.77%) |      19   →      21    (+10.53%) |        4.08 ms →        5.00 ms  (+22.43%) | 
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.21 μs →        6.54 μs   (-9.26%) |      19   →      21    (+10.53%) |      136.90 μs →      137.29 μs   (+0.29%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.63 s   (-16.75%) |      19   →      21    (+10.53%) |       37.17 s  →       34.20 s    (-7.99%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       78.78 ms →       66.58 ms  (-15.48%) |      19   →      21    (+10.53%) |        1.50 s  →        1.40 s    (-6.59%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.96 ms →        7.23 ms   (-9.13%) |     114   →     126    (+10.53%) |      907.38 ms →      911.35 ms   (+0.44%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.57 ms →       16.79 ms   (+7.82%) |      19   →      21    (+10.53%) |      295.86 ms →      352.56 ms  (+19.17%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      497.38 μs →      464.33 μs   (-6.65%) |      19   →      21    (+10.53%) |        9.45 ms →        9.75 ms   (+3.18%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.07 ms →        7.45 ms   (+5.25%) |      38   →      42    (+10.53%) |      268.83 ms →      312.74 ms  (+16.33%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s  →        1.54 s   (-17.12%) |      19   →      21    (+10.53%) |       35.23 s  →       32.27 s    (-8.39%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.57 ms →       49.27 ms  (-11.33%) |     356   →     361     (+1.40%) |       19.78 s  →       17.79 s   (-10.09%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       34.78 ms →       29.63 ms  (-14.81%) |     356   →     361     (+1.40%) |       12.38 s  →       10.70 s   (-13.61%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.02 μs →        2.20 μs   (+8.41%) |     356   →     361     (+1.40%) |      720.87 μs →      792.46 μs   (+9.93%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.73 μs →        1.85 μs   (+6.75%) |     356   →     361     (+1.40%) |      615.51 μs →      666.26 μs   (+8.24%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      414.38 ns →      445.17 ns   (+7.43%) |     356   →     361     (+1.40%) |      147.52 μs →      160.71 μs   (+8.94%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      548.87 ns →      646.74 ns  (+17.83%) |     356   →     361     (+1.40%) |      195.40 μs →      233.47 μs  (+19.49%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.97 ms →        2.77 ms   (-6.79%) |     356   →     361     (+1.40%) |        1.06 s  →      999.66 ms   (-5.48%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.24 ms →        3.20 ms   (-1.00%) |     356   →     361     (+1.40%) |        1.15 s  →        1.16 s    (+0.39%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.28 ms →        6.83 ms   (-6.27%) |     712   →     722     (+1.40%) |        5.19 s  →        4.93 s    (-4.95%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.02 ms →        6.39 ms   (+6.19%) |     356   →     361     (+1.40%) |        2.14 s  →        2.31 s    (+7.68%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.02 ms →      939.36 μs   (-7.96%) |     693   →     701     (+1.15%) |      707.30 ms →      658.49 ms   (-6.90%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       56.50 ns →       42.41 ns  (-24.94%) |     693   →     701     (+1.15%) |       39.16 μs →       29.73 μs  (-24.07%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      859.79 μs →      775.37 μs   (-9.82%) |     693   →     701     (+1.15%) |      595.83 ms →      543.53 ms   (-8.78%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.49 ns →       49.50 ns   (+8.82%) |     693   →     701     (+1.15%) |       31.52 μs →       34.70 μs  (+10.07%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      139.56 μs →      135.96 μs   (-2.58%) |     356   →     361     (+1.40%) |       49.68 ms →       49.08 ms   (-1.21%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.75 ms →        2.17 ms  (+24.20%) |     356   →     361     (+1.40%) |      622.64 ms →      784.15 ms  (+25.94%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.26 ms →        2.39 ms   (+5.93%) |     337   →     340     (+0.89%) |      760.44 ms →      812.74 ms   (+6.88%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      751.34 μs →      795.97 μs   (+5.94%) |    1.01 K →    1.02 K   (+0.89%) |      759.60 ms →      811.89 ms   (+6.88%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.26 ms →        1.39 ms  (+10.56%) |     356   →     361     (+1.40%) |      446.82 ms →      500.93 ms  (+12.11%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.18 ms →        1.34 ms  (+13.44%) |     356   →     361     (+1.40%) |      421.69 ms →      485.08 ms  (+15.03%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       39.95 ns →       40.07 ns   (+0.29%) |     356   →     361     (+1.40%) |       14.22 μs →       14.46 μs   (+1.70%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.02 ms →        1.18 ms  (+15.66%) |     356   →     361     (+1.40%) |      363.06 ms →      425.82 ms  (+17.29%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.81 ns →       44.69 ns  (+15.14%) |     356   →     361     (+1.40%) |       13.82 μs →       16.13 μs  (+16.76%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       32.54 ms →       28.92 ms  (-11.12%) |     356   →     361     (+1.40%) |       11.58 s  →       10.44 s    (-9.88%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.67 ms →        2.32 ms  (-13.30%) |     340   →     346     (+1.76%) |      909.32 ms →      802.30 ms  (-11.77%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.34 ms →        1.09 ms  (-19.15%) |     337   →     342     (+1.48%) |      453.19 ms →      371.84 ms  (-17.95%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      670.97 μs →      542.18 μs  (-19.20%) |     674   →     684     (+1.48%) |      452.24 ms →      370.85 ms  (-18.00%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.24 ms →        1.17 ms   (-5.58%) |     337   →     342     (+1.48%) |      417.55 ms →      400.11 ms   (-4.18%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.53 ms →        4.71 ms  (-27.82%) |      54   →      90    (+66.67%) |      352.39 ms →      423.93 ms  (+20.30%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.91 ms →        2.62 ms  (-33.11%) |      89   →     159    (+78.65%) |      347.95 ms →      415.81 ms  (+19.50%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.80 ms →        1.82 ms  (-35.02%) |     124   →     228    (+83.87%) |      347.77 ms →      415.49 ms  (+19.47%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      386.42 ns →      525.00 ns  (+35.86%) |      19   →      21    (+10.53%) |        7.34 μs →       11.03 μs  (+50.16%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.59 μs →       19.96 μs   (+1.90%) |      19   →      21    (+10.53%) |      372.21 μs →      419.20 μs  (+12.63%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.54 ms →        1.58 ms   (+3.06%) |      19   →      21    (+10.53%) |       29.17 ms →       33.23 ms  (+13.91%) | 
- │ │ ├ sirius::Density::generate                                       |      564.60 ms →      562.03 ms   (-0.45%) |      19   →      21    (+10.53%) |       10.73 s  →       11.80 s   (+10.02%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      379.94 ms →      422.23 ms  (+11.13%) |      19   →      21    (+10.53%) |        7.22 s  →        8.87 s   (+22.83%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.37 μs →        7.90 μs   (-5.60%) |      19   →      21    (+10.53%) |      159.08 μs →      165.98 μs   (+4.34%) | 
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.82 μs →        7.43 μs   (-5.02%) |      19   →      21    (+10.53%) |      148.59 μs →      155.98 μs   (+4.97%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       45.46 ms →       24.43 ms  (-46.26%) |      19   →      21    (+10.53%) |      863.75 ms →      513.01 ms  (-40.61%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.56 μs →        8.14 μs   (+7.61%) |      19   →      21    (+10.53%) |      143.66 μs →      170.87 μs  (+18.94%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.93 ms →        4.29 ms  (-82.09%) |      19   →      21    (+10.53%) |      454.76 ms →       90.02 ms  (-80.20%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.46 ms →       19.08 ms   (-6.76%) |      19   →      21    (+10.53%) |      388.83 ms →      400.69 ms   (+3.05%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      741.37 ns →        1.09 μs  (+47.10%) |      19   →      21    (+10.53%) |       14.09 μs →       22.90 μs  (+62.59%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       94.04 ms →      121.29 ms  (+28.98%) |      19   →      21    (+10.53%) |        1.79 s  →        2.55 s   (+42.56%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.92 ms →        2.23 ms  (+16.08%) |      19   →      21    (+10.53%) |       36.45 ms →       46.76 ms  (+28.30%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      207.39 ms →      242.14 ms  (+16.75%) |      19   →      21    (+10.53%) |        3.94 s  →        5.08 s   (+29.04%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      207.17 ms →      241.92 ms  (+16.78%) |      19   →      21    (+10.53%) |        3.94 s  →        5.08 s   (+29.07%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      157.20 ms →      112.53 ms  (-28.42%) |      19   →      21    (+10.53%) |        2.99 s  →        2.36 s   (-20.88%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      157.19 ms →      112.53 ms  (-28.42%) |      19   →      21    (+10.53%) |        2.99 s  →        2.36 s   (-20.88%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       72.45 ms →       30.18 ms  (-58.35%) |      19   →      21    (+10.53%) |        1.38 s  →      633.70 ms  (-53.96%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.42 ms →       69.09 ms   (-3.26%) |      19   →      21    (+10.53%) |        1.36 s  →        1.45 s    (+6.92%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.67 ms →       12.61 ms   (-0.47%) |      19   →      21    (+10.53%) |      240.79 ms →      264.89 ms  (+10.01%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.64 ms →       23.58 ms   (-0.28%) |      19   →      21    (+10.53%) |      449.22 ms →      495.10 ms  (+10.21%) | 
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.81 ms →        3.69 ms   (-3.16%) |      19   →      21    (+10.53%) |       72.42 ms →       77.51 ms   (+7.03%) | 
- │ │ ├ sirius::Density::mix                                            |      133.79 ms →      134.24 ms   (+0.34%) |      19   →      21    (+10.53%) |        2.54 s  →        2.82 s   (+10.90%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      482.90 μs →      679.58 μs  (+40.73%) |      19   →      21    (+10.53%) |        9.18 ms →       14.27 ms  (+55.54%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.96 ms →        4.76 ms   (-4.04%) |     229   →     259    (+13.10%) |        1.14 s  →        1.23 s    (+8.53%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.83 ms →        4.62 ms   (-4.28%) |     229   →     259    (+13.10%) |        1.11 s  →        1.20 s    (+8.26%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.62 ms   (-4.28%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.26%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.03 ms →        6.16 ms   (+2.22%) |      19   →      21    (+10.53%) |      114.52 ms →      129.38 ms  (+12.98%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.30 ms →        5.41 ms   (+2.11%) |      19   →      21    (+10.53%) |      100.64 ms →      113.58 ms  (+12.86%) | 
- │ │ ├ sirius::Potential::generate                                     |      363.01 ms →      365.58 ms   (+0.71%) |      19   →      21    (+10.53%) |        6.90 s  →        7.68 s   (+11.31%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       42.90 ms →       45.10 ms   (+5.13%) |      19   →      21    (+10.53%) |      815.15 ms →      947.20 ms  (+16.20%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       14.10 ms →        2.94 ms  (-79.13%) |      19   →      21    (+10.53%) |      267.90 ms →       61.79 ms  (-76.93%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |        5.73 ms →        5.39 ms   (-5.94%) |      19   →      21    (+10.53%) |      108.90 ms →      113.22 ms   (+3.96%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (-0.07%) |      19   →      21    (+10.53%) |       88.04 ms →       97.25 ms  (+10.45%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (-0.07%) |      19   →      21    (+10.53%) |       88.03 ms →       97.23 ms  (+10.45%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      807.88 μs →      832.44 μs   (+3.04%) |      38   →      42    (+10.53%) |       30.70 ms →       34.96 ms  (+13.89%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       44.89 ms →       44.46 ms   (-0.95%) |      19   →      21    (+10.53%) |      852.94 ms →      933.73 ms   (+9.47%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.71 ms →       43.28 ms   (-0.99%) |      19   →      21    (+10.53%) |      830.47 ms →      908.83 ms   (+9.44%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      687.15 μs →      681.33 μs   (-0.85%) |      38   →      42    (+10.53%) |       26.11 ms →       28.62 ms   (+9.59%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.51 ms →        4.05 ms  (-10.19%) |      19   →      21    (+10.53%) |       85.77 ms →       85.14 ms   (-0.73%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.65 ms →        3.82 ms   (+4.72%) |      19   →      21    (+10.53%) |       69.37 ms →       80.30 ms  (+15.75%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.52 ms →      269.07 ms   (+0.20%) |      19   →      21    (+10.53%) |        5.10 s  →        5.65 s   (+10.75%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      329.63 ns →      222.48 ns  (-32.51%) |      19   →      21    (+10.53%) |        6.26 μs →        4.67 μs  (-25.40%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       97.71 ms →       95.29 ms   (-2.48%) |      19   →      21    (+10.53%) |        1.86 s  →        2.00 s    (+7.79%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       97.70 ms →       95.28 ms   (-2.48%) |      19   →      21    (+10.53%) |        1.86 s  →        2.00 s    (+7.79%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms →       13.34 ms   (+0.45%) |      19   →      21    (+10.53%) |      252.40 ms →      280.21 ms  (+11.02%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.20 ms →       68.75 ms   (-3.43%) |      19   →      21    (+10.53%) |        1.35 s  →        1.44 s    (+6.73%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.56 ms   (-0.23%) |      19   →      21    (+10.53%) |      239.12 ms →      263.68 ms  (+10.27%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.08 ms →        3.81 ms   (-6.73%) |      19   →      21    (+10.53%) |       77.51 ms →       79.91 ms   (+3.09%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.65 ms →        4.72 ms   (+1.50%) |     133   →     147    (+10.53%) |      618.09 ms →      693.40 ms  (+12.18%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.58 ms →        4.55 ms   (-0.56%) |     133   →     147    (+10.53%) |      609.18 ms →      669.53 ms   (+9.91%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.58 ms →        4.55 ms   (-0.56%) |     133   →     147    (+10.53%) |      609.09 ms →      669.44 ms   (+9.91%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.96 ms →        4.73 ms   (-4.62%) |      57   →      63    (+10.53%) |      282.75 ms →      298.09 ms   (+5.42%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.95 ms →        4.72 ms   (-4.57%) |      57   →      63    (+10.53%) |      282.17 ms →      297.60 ms   (+5.47%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.54 ms   (-0.20%) |      19   →      21    (+10.53%) |       86.40 ms →       95.30 ms  (+10.30%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       74.50 μs →       75.36 μs   (+1.15%) |      19   →      21    (+10.53%) |        1.42 ms →        1.58 ms  (+11.80%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.63 μs →       70.62 μs   (+1.43%) |      19   →      21    (+10.53%) |        1.32 ms →        1.48 ms  (+12.10%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.22 ms →        5.07 ms   (-2.82%) |       2   →       2              |       10.44 ms →       10.15 ms   (-2.82%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.67 ms →        4.64 ms   (-0.63%) |       6   →       6              |       28.01 ms →       27.83 ms   (-0.63%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.66 ms →        4.55 ms   (-2.44%) |       6   →       6              |       27.99 ms →       27.31 ms   (-2.44%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.66 ms →        4.55 ms   (-2.41%) |       6   →       6              |       27.98 ms →       27.30 ms   (-2.41%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.16 ms →        4.74 ms   (-8.16%) |       3   →       3              |       15.49 ms →       14.23 ms   (-8.16%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.06 ms →        4.73 ms   (-6.46%) |       3   →       3              |       15.18 ms →       14.20 ms   (-6.46%) | 
  ├ sirius::Periodic_function|inner                                     |        4.77 ms →        4.53 ms   (-5.00%) |       2   →       2              |        9.53 ms →        9.05 ms   (-5.00%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.76 ms →        4.52 ms   (-5.00%) |       2   →       2              |        9.52 ms →        9.05 ms   (-5.00%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.76 ms →        4.52 ms   (-5.00%) |       2   →       2              |        9.52 ms →        9.05 ms   (-5.00%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.23 ms →        4.75 ms   (-9.19%) |       1   →       1              |        5.23 ms →        4.75 ms   (-9.19%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.22 ms →        4.74 ms   (-9.19%) |       1   →       1              |        5.22 ms →        4.74 ms   (-9.19%) | 
  └ sirius::finalize                                                    |      156.09 ms →      145.07 ms   (-7.07%) |       1   →       1              |      156.09 ms →      145.07 ms   (-7.07%) | 
  ====================================================================================================================================================================================================
```
