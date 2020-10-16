# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.53 s  →       70.19 s    (-1.87%) |       1   →       1              |       71.53 s  →       70.19 s    (-1.87%) | 
  ├ sirius::initialize                                                  |        2.90 s  →        2.95 s    (+1.83%) |       1   →       1              |        2.90 s  →        2.95 s    (+1.83%) | 
  ├ sirius::Simulation_context::initialize                              |        3.64 s  →        3.76 s    (+3.28%) |       1   →       1              |        3.64 s  →        3.76 s    (+3.28%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       13.92 ms →       33.77 ms (+142.57%) |       1   →       1              |       13.92 ms →       33.77 ms (+142.57%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      135.55 ms →      165.89 ms  (+22.38%) |       1   →       1              |      135.55 ms →      165.89 ms  (+22.38%) | 
- │ │ ├ sirius::Atom_type::init                                         |       58.06 ms →       73.48 ms  (+26.56%) |       2   →       2              |      116.12 ms →      146.95 ms  (+26.56%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.35 ms →       18.84 ms   (-2.61%) |       1   →       1              |       19.35 ms →       18.84 ms   (-2.61%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.81 ms →        3.58 ms   (-6.14%) |       1   →       1              |        3.81 ms →        3.58 ms   (-6.14%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.46 ms →       15.19 ms   (-1.73%) |       1   →       1              |       15.46 ms →       15.19 ms   (-1.73%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.39 ms →       15.13 ms   (-1.70%) |       1   →       1              |       15.39 ms →       15.13 ms   (-1.70%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.74 ms   (+0.38%) |       1   →       1              |        2.73 ms →        2.74 ms   (+0.38%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      475.94 μs →      498.19 μs   (+4.68%) |       1   →       1              |      475.94 μs →      498.19 μs   (+4.68%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.82 μs →       16.66 μs   (-0.94%) |       1   →       1              |       16.82 μs →       16.66 μs   (-0.94%) | 
  │ └ sirius::Simulation_context::update                                |        3.44 s  →        3.51 s    (+2.04%) |       1   →       1              |        3.44 s  →        3.51 s    (+2.04%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.77 ms →        6.84 ms   (+0.94%) |       1   →       1              |        6.77 ms →        6.84 ms   (+0.94%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.43 ms →        3.42 ms   (-0.06%) |       1   →       1              |        3.43 ms →        3.42 ms   (-0.06%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.36 ms   (+1.77%) |       1   →       1              |        3.30 ms →        3.36 ms   (+1.77%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.29 ms   (+0.96%) |       1   →       1              |        3.26 ms →        3.29 ms   (+0.96%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.73 ms   (+0.32%) |       1   →       1              |        2.72 ms →        2.73 ms   (+0.32%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      502.80 μs →      520.38 μs   (+3.50%) |       1   →       1              |      502.80 μs →      520.38 μs   (+3.50%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.31 μs →       19.23 μs  (+34.33%) |       1   →       1              |       14.31 μs →       19.23 μs  (+34.33%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.06 ms →      212.15 ms   (-0.43%) |       2   →       2              |      426.12 ms →      424.29 ms   (-0.43%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       16.04 ms →       15.26 ms   (-4.87%) |       2   →       2              |       32.08 ms →       30.51 ms   (-4.87%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.47 ms →       13.45 ms   (-0.15%) |       1   →       1              |       13.47 ms →       13.45 ms   (-0.15%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.31 ms →       56.28 ms   (-0.06%) |       2   →       2              |      112.62 ms →      112.56 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.20 ms →       45.13 ms   (-0.15%) |       2   →       2              |       90.40 ms →       90.27 ms   (-0.15%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.41 ms →       60.30 ms   (-0.19%) |       4   →       4              |      241.66 ms →      241.20 ms   (-0.19%) | 
  │   ├ sddk::Gvec::init                                                |       93.61 ms →       93.11 ms   (-0.53%) |       2   →       2              |      187.21 ms →      186.22 ms   (-0.53%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.22 ms →       69.66 ms   (-0.81%) |       2   →       2              |      140.44 ms →      139.31 ms   (-0.81%) | 
  │   ├ sddk::Gvec_shells                                               |       95.63 ms →      101.40 ms   (+6.04%) |       1   →       1              |       95.63 ms →      101.40 ms   (+6.04%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.94 ms   (+0.05%) |       1   →       1              |        1.94 ms →        1.94 ms   (+0.05%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      569.09 ms →      611.08 ms   (+7.38%) |       2   →       2              |        1.14 s  →        1.22 s    (+7.38%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       87.53 ms →       87.96 ms   (+0.49%) |       1   →       1              |       87.53 ms →       87.96 ms   (+0.49%) | 
- │ ├ sirius::K_point::K_point                                          |        1.20 μs →        1.97 μs  (+65.18%) |       4   →       4              |        4.78 μs →        7.90 μs  (+65.18%) | 
  │ └ sirius::K_point_set::initialize                                   |       87.45 ms →       87.88 ms   (+0.49%) |       1   →       1              |       87.45 ms →       87.88 ms   (+0.49%) | 
  │   └ sirius::K_point::initialize                                     |       27.73 ms →       27.81 ms   (+0.28%) |       1   →       1              |       27.73 ms →       27.81 ms   (+0.28%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.91 ms →       10.87 ms   (-0.33%) |       1   →       1              |       10.91 ms →       10.87 ms   (-0.33%) | 
  │     │ └ sddk::Gvec::init                                            |        4.93 ms →        4.89 ms   (-0.86%) |       1   →       1              |        4.93 ms →        4.89 ms   (-0.86%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.28 μs →       10.35 μs   (+0.67%) |       1   →       1              |       10.28 μs →       10.35 μs   (+0.67%) | 
  │     └ sirius::K_point::update                                       |       13.99 ms →       14.13 ms   (+1.02%) |       1   →       1              |       13.99 ms →       14.13 ms   (+1.02%) | 
  │       └ sirius::Beta_projectors                                     |       10.10 ms →       10.20 ms   (+0.98%) |       1   →       1              |       10.10 ms →       10.20 ms   (+0.98%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.24 ms →        8.24 ms   (-0.09%) |       1   →       1              |        8.24 ms →        8.24 ms   (-0.09%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.58 ms   (+0.72%) |       2   →       2              |        5.12 ms →        5.15 ms   (+0.72%) | 
  ├ sirius::Potential                                                   |       49.61 ms →       52.09 ms   (+5.01%) |       1   →       1              |       49.61 ms →       52.09 ms   (+5.01%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.92 ms →        2.94 ms   (+0.53%) |       6   →       6              |       17.53 ms →       17.62 ms   (+0.53%) | 
  │ └ sirius::Potential::update                                         |       31.47 ms →       33.89 ms   (+7.70%) |       1   →       1              |       31.47 ms →       33.89 ms   (+7.70%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.06 ms →       33.48 ms   (+7.80%) |       1   →       1              |       31.06 ms →       33.48 ms   (+7.80%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.99 ms →       26.16 ms   (+0.67%) |       1   →       1              |       25.99 ms →       26.16 ms   (+0.67%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.56 ms →        6.79 ms  (+48.78%) |       1   →       1              |        4.56 ms →        6.79 ms  (+48.78%) | 
- ├ sirius::Density                                                     |       37.68 ms →       42.60 ms  (+13.06%) |       1   →       1              |       37.68 ms →       42.60 ms  (+13.06%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.82 ms   (-0.11%) |       2   →       2              |        5.65 ms →        5.65 ms   (-0.11%) | 
- │ └ sirius::Density::update                                           |       31.89 ms →       36.82 ms  (+15.44%) |       1   →       1              |       31.89 ms →       36.82 ms  (+15.44%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       31.67 ms →       36.61 ms  (+15.60%) |       1   →       1              |       31.67 ms →       36.61 ms  (+15.60%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       86.96 μs →       79.09 μs   (-9.05%) |       1   →       1              |       86.96 μs →       79.09 μs   (-9.05%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.94 ms →       26.25 ms   (+1.20%) |       1   →       1              |       25.94 ms →       26.25 ms   (+1.20%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.34 ms →        9.95 ms  (+86.39%) |       1   →       1              |        5.34 ms →        9.95 ms  (+86.39%) | 
- ├ sirius::Density::initial_density                                    |       54.46 ms →       61.24 ms  (+12.46%) |       1   →       1              |       54.46 ms →       61.24 ms  (+12.46%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.19 ms →       26.51 ms   (+1.21%) |       1   →       1              |       26.19 ms →       26.51 ms   (+1.21%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.88 ms →        7.71 ms  (+57.94%) |       2   →       2              |        9.77 ms →       15.43 ms  (+57.94%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.86 ms →        5.71 ms  (+17.40%) |       1   →       1              |        4.86 ms →        5.71 ms  (+17.40%) | 
  ├ sirius::Potential::generate                                         |      364.71 ms →      369.64 ms   (+1.35%) |       1   →       1              |      364.71 ms →      369.64 ms   (+1.35%) | 
- │ ├ sirius::Potential::poisson                                        |       37.45 ms →       42.40 ms  (+13.20%) |       1   →       1              |       37.45 ms →       42.40 ms  (+13.20%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.62 ms →       11.32 ms  (+71.16%) |       1   →       1              |        6.62 ms →       11.32 ms  (+71.16%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.75 ms →        5.90 ms   (+2.64%) |       1   →       1              |        5.75 ms →        5.90 ms   (+2.64%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.65 ms →        4.66 ms   (+0.13%) |       1   →       1              |        4.65 ms →        4.66 ms   (+0.13%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.65 ms   (+0.09%) |       1   →       1              |        4.64 ms →        4.65 ms   (+0.09%) | 
  │ ├ sirius::Periodic_function::add                                    |      774.83 μs →      807.32 μs   (+4.19%) |       2   →       2              |        1.55 ms →        1.61 ms   (+4.19%) | 
  │ ├ sirius::Potential::xc                                             |       51.63 ms →       51.56 ms   (-0.12%) |       1   →       1              |       51.63 ms →       51.56 ms   (-0.12%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.45 ms →       50.36 ms   (-0.17%) |       1   →       1              |       50.45 ms →       50.36 ms   (-0.17%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.54 ms   (-0.41%) |       2   →       2              |        5.10 ms →        5.08 ms   (-0.41%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.59 ms →        4.78 ms   (+4.36%) |       1   →       1              |        4.59 ms →        4.78 ms   (+4.36%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.89 ms →        3.60 ms  (+24.42%) |       1   →       1              |        2.89 ms →        3.60 ms  (+24.42%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.82 ms →      269.08 ms   (-0.27%) |       1   →       1              |      269.82 ms →      269.08 ms   (-0.27%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      322.00 ns →      200.00 ns  (-37.89%) |       1   →       1              |      322.00 ns →      200.00 ns  (-37.89%) | 
+ ├ sirius::Hamiltonian0                                                |        7.75 ms →        6.50 ms  (-16.12%) |       1   →       1              |        7.75 ms →        6.50 ms  (-16.12%) | 
+ │ ├ sirius::Local_operator                                            |        7.06 ms →        6.03 ms  (-14.65%) |       1   →       1              |        7.06 ms →        6.03 ms  (-14.65%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.76 ms   (+0.28%) |       1   →       1              |        2.75 ms →        2.76 ms   (+0.28%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.21 ms →        2.51 ms  (-21.84%) |       1   →       1              |        3.21 ms →        2.51 ms  (-21.84%) | 
+ │ ├ sirius::Non_local_operator                                        |      205.01 μs →       72.53 μs  (-64.62%) |       2   →       2              |      410.01 μs →      145.05 μs  (-64.62%) | 
  │ ├ sirius::D_operator::initialize                                    |      116.64 μs →      120.16 μs   (+3.02%) |       1   →       1              |      116.64 μs →      120.16 μs   (+3.02%) | 
- │ └ sirius::Q_operator::initialize                                    |       92.33 μs →      117.35 μs  (+27.11%) |       1   →       1              |       92.33 μs →      117.35 μs  (+27.11%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.29 s    (-0.54%) |       1   →       1              |        1.29 s  →        1.29 s    (-0.54%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       65.58 ms →       31.14 ms  (-52.51%) |       1   →       1              |       65.58 ms →       31.14 ms  (-52.51%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      318.43 μs →      286.34 μs  (-10.08%) |       1   →       1              |      318.43 μs →      286.34 μs  (-10.08%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       65.26 ms →       30.85 ms  (-52.72%) |       1   →       1              |       65.26 ms →       30.85 ms  (-52.72%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.26 s    (+2.24%) |       1   →       1              |        1.23 s  →        1.26 s    (+2.24%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.36 ms →       84.28 ms   (-6.73%) |       4   →       4              |      361.43 ms →      337.12 ms   (-6.73%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       44.17 ms →       46.77 ms   (+5.88%) |       1   →       1              |       44.17 ms →       46.77 ms   (+5.88%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        9.00 ms →        7.82 ms  (-13.08%) |       1   →       1              |        9.00 ms →        7.82 ms  (-13.08%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      384.11 ms →      334.55 ms  (-12.90%) |       1   →       1              |      384.11 ms →      334.55 ms  (-12.90%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      272.38 ms →      246.31 ms   (-9.57%) |       1   →       1              |      272.38 ms →      246.31 ms   (-9.57%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.24 μs →        4.07 μs   (-3.99%) |       1   →       1              |        4.24 μs →        4.07 μs   (-3.99%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.28 μs →        3.08 μs   (-6.07%) |       1   →       1              |        3.28 μs →        3.08 μs   (-6.07%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      478.00 ns →      469.00 ns   (-1.88%) |       1   →       1              |      478.00 ns →      469.00 ns   (-1.88%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      691.00 ns →      648.00 ns   (-6.22%) |       1   →       1              |      691.00 ns →      648.00 ns   (-6.22%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.05 ms →        3.22 ms   (+5.46%) |       1   →       1              |        3.05 ms →        3.22 ms   (+5.46%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       39.60 ms →       21.30 ms  (-46.22%) |       1   →       1              |       39.60 ms →       21.30 ms  (-46.22%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       34.52 ms →       31.84 ms   (-7.77%) |       2   →       2              |       69.03 ms →       63.67 ms   (-7.77%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.88 ms →       14.83 ms  (-12.16%) |       2   →       2              |       33.76 ms →       29.65 ms  (-12.16%) | 
+ │ │ │ └ sddk::wf_inner                                                |       16.67 ms →       14.62 ms  (-12.30%) |       2   →       2              |       33.34 ms →       29.24 ms  (-12.30%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       20.50 ns →       21.00 ns   (+2.44%) |       2   →       2              |       41.00 ns →       42.00 ns   (+2.44%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       16.54 ms →       14.49 ms  (-12.39%) |       2   →       2              |       33.08 ms →       28.98 ms  (-12.39%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       20.50 ns →       21.00 ns   (+2.44%) |       2   →       2              |       41.00 ns →       42.00 ns   (+2.44%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      182.30 ms →      231.18 ms  (+26.81%) |       1   →       1              |      182.30 ms →      231.18 ms  (+26.81%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.60 ms   (+0.10%) |       1   →       1              |        2.60 ms →        2.60 ms   (+0.10%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.59 ms   (+0.09%) |       1   →       1              |        2.59 ms →        2.59 ms   (+0.09%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      563.00 ns →      467.00 ns  (-17.05%) |       1   →       1              |      563.00 ns →      467.00 ns  (-17.05%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.97 s  →       60.47 s    (-2.41%) |       1   →       1              |       61.97 s  →       60.47 s    (-2.41%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.44 ms   (-1.10%) |      19   →      19              |       46.93 ms →       46.41 ms   (-1.10%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        3.17 s    (-2.56%) |      19   →      19              |       61.76 s  →       60.18 s    (-2.56%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.13 ms →        5.98 ms  (+16.62%) |      19   →      19              |       97.46 ms →      113.66 ms  (+16.62%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.35 ms →        5.20 ms  (+19.57%) |      19   →      19              |       82.68 ms →       98.85 ms  (+19.57%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      542.77 μs →      538.32 μs   (-0.82%) |      19   →      19              |       10.31 ms →       10.23 ms   (-0.82%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.74 ms →        3.46 ms  (+26.40%) |      19   →      19              |       51.98 ms →       65.70 ms  (+26.40%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |      239.94 μs →      243.31 μs   (+1.40%) |      38   →      38              |        9.12 ms →        9.25 ms   (+1.40%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      119.78 μs →      121.26 μs   (+1.23%) |      19   →      19              |        2.28 ms →        2.30 ms   (+1.23%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       94.92 μs →       93.12 μs   (-1.90%) |      19   →      19              |        1.80 ms →        1.77 ms   (-1.90%) | 
  │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.94 s    (-4.14%) |      19   →      19              |       38.54 s  →       36.94 s    (-4.14%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      209.43 μs →      203.83 μs   (-2.67%) |      19   →      19              |        3.98 ms →        3.87 ms   (-2.67%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      199.67 μs →      194.36 μs   (-2.66%) |      19   →      19              |        3.79 ms →        3.69 ms   (-2.66%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.95 μs →        7.04 μs   (+1.34%) |      19   →      19              |      131.99 μs →      133.75 μs   (+1.34%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.81 s    (-7.98%) |      19   →      19              |       37.30 s  →       34.32 s    (-7.98%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.85 ms →       77.64 ms   (-0.26%) |      19   →      19              |        1.48 s  →        1.48 s    (-0.26%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.22 ms →        8.18 ms   (-0.52%) |     114   →     114              |      937.63 ms →      932.80 ms   (-0.52%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.36 ms →       18.82 ms   (+8.42%) |      19   →      19              |      329.88 ms →      357.66 ms   (+8.42%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      473.35 μs →      467.15 μs   (-1.31%) |      19   →      19              |        8.99 ms →        8.88 ms   (-1.31%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.78 ms →        8.66 ms  (+11.30%) |      38   →      38              |      295.63 ms →      329.02 ms  (+11.30%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.70 s    (-8.59%) |      19   →      19              |       35.33 s  →       32.29 s    (-8.59%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.05 ms →       60.51 ms  (+20.90%) |     356   →     312    (-12.36%) |       17.82 s  →       18.88 s    (+5.96%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.59 ms →       33.25 ms  (+16.32%) |     356   →     312    (-12.36%) |       10.18 s  →       10.37 s    (+1.94%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.03 μs →        2.08 μs   (+2.51%) |     356   →     312    (-12.36%) |      723.35 μs →      649.86 μs  (-10.16%) | 
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.72 μs →        1.79 μs   (+3.78%) |     356   →     312    (-12.36%) |      613.23 μs →      557.77 μs   (-9.05%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      426.15 ns →      468.08 ns   (+9.84%) |     356   →     312    (-12.36%) |      151.71 μs →      146.04 μs   (-3.74%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      514.66 ns →      656.44 ns  (+27.55%) |     356   →     312    (-12.36%) |      183.22 μs →      204.81 μs  (+11.78%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.87 ms →        3.11 ms   (+8.64%) |     356   →     312    (-12.36%) |        1.02 s  →      971.51 ms   (-4.79%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.09 ms →        3.61 ms  (+16.57%) |     356   →     312    (-12.36%) |        1.10 s  →        1.13 s    (+2.17%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.74 ms →       10.26 ms  (+32.50%) |     712   →     624    (-12.36%) |        5.51 s  →        6.40 s   (+16.12%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.49 ms →        7.63 ms  (+17.47%) |     356   →     312    (-12.36%) |        2.31 s  →        2.38 s    (+2.95%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.11 ms →        1.36 ms  (+22.02%) |     693   →     605    (-12.70%) |      771.58 ms →      821.93 ms   (+6.53%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       58.37 ns →       59.52 ns   (+1.97%) |     693   →     605    (-12.70%) |       40.45 μs →       36.01 μs  (-10.97%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      952.78 μs →        1.19 ms  (+25.31%) |     693   →     605    (-12.70%) |      660.28 ms →      722.30 ms   (+9.39%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       48.43 ns →       45.38 ns   (-6.29%) |     693   →     605    (-12.70%) |       33.56 μs →       27.46 μs  (-18.19%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      131.72 μs →      161.79 μs  (+22.83%) |     356   →     312    (-12.36%) |       46.89 ms →       50.48 ms   (+7.65%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.90 ms →        2.25 ms  (+18.45%) |     356   →     312    (-12.36%) |      675.86 ms →      701.58 ms   (+3.81%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.42 ms →        2.74 ms  (+13.41%) |     337   →     293    (-13.06%) |      815.12 ms →      803.73 ms   (-1.40%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      805.47 μs →      913.51 μs  (+13.41%) |    1.01 K →     879    (-13.06%) |      814.33 ms →      802.98 ms   (-1.39%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.47 ms →        1.65 ms  (+12.87%) |     356   →     312    (-12.36%) |      521.55 ms →      515.93 ms   (-1.08%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.40 ms →        1.60 ms  (+14.50%) |     356   →     312    (-12.36%) |      496.93 ms →      498.68 ms   (+0.35%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.76 ns →       32.48 ns  (-20.33%) |     356   →     312    (-12.36%) |       14.51 μs →       10.13 μs  (-30.18%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.23 ms →        1.43 ms  (+15.99%) |     356   →     312    (-12.36%) |      439.48 ms →      446.76 ms   (+1.65%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       42.78 ns →       53.30 ns  (+24.59%) |     356   →     312    (-12.36%) |       15.23 μs →       16.63 μs   (+9.19%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       37.62 ms →       28.72 ms  (-23.66%) |     356   →     312    (-12.36%) |       13.39 s  →        8.96 s   (-33.10%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.68 ms →        3.60 ms  (+34.56%) |     340   →     299    (-12.06%) |      910.75 ms →        1.08 s   (+18.33%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.39 ms →        1.54 ms  (+11.10%) |     337   →     293    (-13.06%) |      467.35 ms →      451.45 ms   (-3.40%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      692.00 μs →      768.91 μs  (+11.11%) |     674   →     586    (-13.06%) |      466.41 ms →      450.58 ms   (-3.39%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.16 ms →        2.00 ms  (+72.53%) |     337   →     293    (-13.06%) |      391.53 ms →      587.32 ms  (+50.00%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.85 ms →        7.23 ms   (+5.51%) |      54   →      66    (+22.22%) |      369.84 ms →      476.95 ms  (+28.96%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.10 ms →        4.17 ms   (+1.54%) |      89   →     113    (+26.97%) |      365.34 ms →      471.00 ms  (+28.92%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.94 ms →        2.94 ms   (-0.09%) |     124   →     160    (+29.03%) |      365.17 ms →      470.78 ms  (+28.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      394.05 ns →      382.53 ns   (-2.93%) |      19   →      19              |        7.49 μs →        7.27 μs   (-2.93%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.69 μs →       19.62 μs   (-0.31%) |      19   →      19              |      374.02 μs →      372.84 μs   (-0.31%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.49 ms   (-1.35%) |      19   →      19              |       28.78 ms →       28.39 ms   (-1.35%) | 
  │ │ ├ sirius::Density::generate                                       |      572.17 ms →      570.15 ms   (-0.35%) |      19   →      19              |       10.87 s  →       10.83 s    (-0.35%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      400.58 ms →      422.15 ms   (+5.38%) |      19   →      19              |        7.61 s  →        8.02 s    (+5.38%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        9.19 μs →        8.14 μs  (-11.46%) |      19   →      19              |      174.58 μs →      154.57 μs  (-11.46%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.07 μs →        7.64 μs   (-5.34%) |      19   →      19              |      153.29 μs →      145.11 μs   (-5.34%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       39.45 ms →       31.87 ms  (-19.19%) |      19   →      19              |      749.47 ms →      605.61 ms  (-19.19%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.47 μs →        8.03 μs   (+7.47%) |      19   →      19              |      142.02 μs →      152.64 μs   (+7.47%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.34 ms →        4.88 ms  (-23.00%) |      19   →      19              |      120.47 ms →       92.76 ms  (-23.00%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       32.06 ms →       25.96 ms  (-19.01%) |      19   →      19              |      609.05 ms →      493.27 ms  (-19.01%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      530.11 ns →      554.53 ns   (+4.61%) |      19   →      19              |       10.07 μs →       10.54 μs   (+4.61%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      106.35 ms →      113.90 ms   (+7.11%) |      19   →      19              |        2.02 s  →        2.16 s    (+7.11%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.45 ms →        2.50 ms   (+2.37%) |      19   →      19              |       46.48 ms →       47.59 ms   (+2.37%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      211.60 ms →      234.65 ms  (+10.89%) |      19   →      19              |        4.02 s  →        4.46 s   (+10.89%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      211.38 ms →      234.43 ms  (+10.90%) |      19   →      19              |        4.02 s  →        4.45 s   (+10.90%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      142.28 ms →      119.45 ms  (-16.04%) |      19   →      19              |        2.70 s  →        2.27 s   (-16.04%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      142.28 ms →      119.45 ms  (-16.04%) |      19   →      19              |        2.70 s  →        2.27 s   (-16.04%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       58.65 ms →       36.93 ms  (-37.03%) |      19   →      19              |        1.11 s  →      701.71 ms  (-37.03%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.45 ms →       69.22 ms   (-1.75%) |      19   →      19              |        1.34 s  →        1.32 s    (-1.75%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.53 ms →       12.65 ms   (+0.95%) |      19   →      19              |      238.02 ms →      240.27 ms   (+0.95%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.73 ms →       23.66 ms   (-0.28%) |      19   →      19              |      450.82 ms →      449.56 ms   (-0.28%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.58 ms →        4.88 ms  (-12.51%) |      19   →      19              |      105.95 ms →       92.70 ms  (-12.51%) | 
  │ │ ├ sirius::Density::mix                                            |      132.22 ms →      130.87 ms   (-1.02%) |      19   →      19              |        2.51 s  →        2.49 s    (-1.02%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      780.26 μs →      821.39 μs   (+5.27%) |      19   →      19              |       14.82 ms →       15.61 ms   (+5.27%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.89 ms →        4.64 ms   (-5.03%) |     229   →     229              |        1.12 s  →        1.06 s    (-5.03%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.61 ms   (-4.26%) |     229   →     229              |        1.10 s  →        1.05 s    (-4.26%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.60 ms   (-4.26%) |     229   →     229              |        1.10 s  →        1.05 s    (-4.26%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.89 ms →        5.23 ms  (-24.11%) |      19   →      19              |      130.85 ms →       99.30 ms  (-24.11%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.12 ms →        4.56 ms  (-25.51%) |      19   →      19              |      116.32 ms →       86.65 ms  (-25.51%) | 
  │ │ ├ sirius::Potential::generate                                     |      357.83 ms →      363.51 ms   (+1.59%) |      19   →      19              |        6.80 s  →        6.91 s    (+1.59%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       37.24 ms →       43.06 ms  (+15.63%) |      19   →      19              |      707.60 ms →      818.18 ms  (+15.63%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        6.45 ms →       12.04 ms  (+86.82%) |      19   →      19              |      122.48 ms →      228.82 ms  (+86.82%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.74 ms →        5.86 ms   (+2.04%) |      19   →      19              |      109.10 ms →      111.33 ms   (+2.04%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.01%) |      19   →      19              |       88.02 ms →       88.02 ms   (+0.01%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.01%) |      19   →      19              |       88.00 ms →       88.01 ms   (+0.01%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      817.55 μs →      803.09 μs   (-1.77%) |      38   →      38              |       31.07 ms →       30.52 ms   (-1.77%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.43 ms →       45.29 ms   (-0.31%) |      19   →      19              |      863.17 ms →      860.47 ms   (-0.31%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.26 ms →       44.11 ms   (-0.34%) |      19   →      19              |      840.95 ms →      838.10 ms   (-0.34%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      675.36 μs →      678.77 μs   (+0.50%) |      38   →      38              |       25.66 ms →       25.79 ms   (+0.50%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.96 ms →        4.82 ms   (-2.63%) |      19   →      19              |       94.15 ms →       91.67 ms   (-2.63%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.39 ms →        3.65 ms   (+7.67%) |      19   →      19              |       64.38 ms →       69.31 ms   (+7.67%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.75 ms →      268.48 ms   (-0.10%) |      19   →      19              |        5.11 s  →        5.10 s    (-0.10%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      319.68 ns →      243.68 ns  (-23.77%) |      19   →      19              |        6.07 μs →        4.63 μs  (-23.77%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.61 ms →       95.74 ms   (-0.90%) |      19   →      19              |        1.84 s  →        1.82 s    (-0.90%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.61 ms →       95.74 ms   (-0.90%) |      19   →      19              |        1.84 s  →        1.82 s    (-0.90%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.47 ms →       13.31 ms   (-1.20%) |      19   →      19              |      255.93 ms →      252.85 ms   (-1.20%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.00 ms →       69.23 ms   (-1.10%) |      19   →      19              |        1.33 s  →        1.32 s    (-1.10%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.52 ms →       12.57 ms   (+0.44%) |      19   →      19              |      237.80 ms →      238.84 ms   (+0.44%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.73 ms →        3.91 ms  (-17.33%) |      19   →      19              |       89.78 ms →       74.22 ms  (-17.33%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.66 ms →        4.66 ms   (+0.16%) |     133   →     133              |      619.22 ms →      620.21 ms   (+0.16%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.55 ms   (-1.83%) |     133   →     133              |      616.49 ms →      605.19 ms   (-1.83%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.55 ms   (-1.84%) |     133   →     133              |      616.42 ms →      605.11 ms   (-1.84%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.72 ms   (-4.54%) |      57   →      57              |      281.97 ms →      269.16 ms   (-4.54%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.72 ms   (-4.41%) |      57   →      57              |      281.23 ms →      268.82 ms   (-4.41%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.52 ms →        4.53 ms   (+0.21%) |      19   →      19              |       85.93 ms →       86.11 ms   (+0.21%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.80 μs →       76.43 μs   (-0.49%) |      19   →      19              |        1.46 ms →        1.45 ms   (-0.49%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.22 μs →       71.48 μs   (+0.37%) |      19   →      19              |        1.35 ms →        1.36 ms   (+0.37%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.30 ms →        5.64 ms   (+6.49%) |       2   →       2              |       10.60 ms →       11.28 ms   (+6.49%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.63 ms →        4.54 ms   (-1.98%) |       6   →       6              |       27.78 ms →       27.23 ms   (-1.98%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.62 ms →        4.52 ms   (-2.15%) |       6   →       6              |       27.72 ms →       27.12 ms   (-2.15%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.62 ms →        4.52 ms   (-2.12%) |       6   →       6              |       27.71 ms →       27.12 ms   (-2.12%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.07 ms →        4.72 ms   (-6.85%) |       3   →       3              |       15.21 ms →       14.17 ms   (-6.85%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.06 ms →        4.71 ms   (-6.99%) |       3   →       3              |       15.19 ms →       14.13 ms   (-6.99%) | 
  ├ sirius::Periodic_function|inner                                     |        4.98 ms →        4.81 ms   (-3.44%) |       2   →       2              |        9.97 ms →        9.62 ms   (-3.44%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.79 ms →        4.81 ms   (+0.39%) |       2   →       2              |        9.58 ms →        9.62 ms   (+0.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        4.81 ms   (+0.39%) |       2   →       2              |        9.58 ms →        9.62 ms   (+0.39%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.15 ms →        4.92 ms   (-4.59%) |       1   →       1              |        5.15 ms →        4.92 ms   (-4.59%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.15 ms →        4.91 ms   (-4.60%) |       1   →       1              |        5.15 ms →        4.91 ms   (-4.60%) | 
  └ sirius::finalize                                                    |      150.30 ms →      147.84 ms   (-1.64%) |       1   →       1              |      150.30 ms →      147.84 ms   (-1.64%) | 
  ====================================================================================================================================================================================================
```
