# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.74 s  →       72.28 s    (+0.75%) |       1   →       1              |       71.74 s  →       72.28 s    (+0.75%) | 
  ├ sirius::initialize                                                  |        2.90 s  →        2.85 s    (-1.58%) |       1   →       1              |        2.90 s  →        2.85 s    (-1.58%) | 
  ├ sirius::Simulation_context::initialize                              |        3.84 s  →        3.50 s    (-8.95%) |       1   →       1              |        3.84 s  →        3.50 s    (-8.95%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       29.08 ms →       23.86 ms  (-17.94%) |       1   →       1              |       29.08 ms →       23.86 ms  (-17.94%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      145.47 ms →      140.73 ms   (-3.26%) |       1   →       1              |      145.47 ms →      140.73 ms   (-3.26%) | 
  │ │ ├ sirius::Atom_type::init                                         |       63.30 ms →       61.58 ms   (-2.72%) |       2   →       2              |      126.60 ms →      123.15 ms   (-2.72%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.77 ms →       17.48 ms   (-6.87%) |       1   →       1              |       18.77 ms →       17.48 ms   (-6.87%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.20 ms →        5.19 ms   (-0.04%) |       1   →       1              |        5.20 ms →        5.19 ms   (-0.04%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.51 ms →       12.21 ms   (-9.64%) |       1   →       1              |       13.51 ms →       12.21 ms   (-9.64%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.45 ms →       12.14 ms   (-9.68%) |       1   →       1              |       13.45 ms →       12.14 ms   (-9.68%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.73 ms   (+0.47%) |       1   →       1              |        2.72 ms →        2.73 ms   (+0.47%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      502.04 μs →      501.67 μs   (-0.07%) |       1   →       1              |      502.04 μs →      501.67 μs   (-0.07%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.62 μs →       16.30 μs   (-1.90%) |       1   →       1              |       16.62 μs →       16.30 μs   (-1.90%) | 
+ │ └ sirius::Simulation_context::update                                |        3.61 s  →        3.12 s   (-13.61%) |       1   →       1              |        3.61 s  →        3.12 s   (-13.61%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.98 ms →        6.98 ms   (-0.03%) |       1   →       1              |        6.98 ms →        6.98 ms   (-0.03%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.64 ms   (-0.28%) |       1   →       1              |        3.65 ms →        3.64 ms   (-0.28%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.27 ms →        3.30 ms   (+0.88%) |       1   →       1              |        3.27 ms →        3.30 ms   (+0.88%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.22 ms →        3.25 ms   (+1.00%) |       1   →       1              |        3.22 ms →        3.25 ms   (+1.00%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (+0.33%) |       1   →       1              |        2.70 ms →        2.70 ms   (+0.33%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      488.24 μs →      513.04 μs   (+5.08%) |       1   →       1              |      488.24 μs →      513.04 μs   (+5.08%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.58 μs →       13.99 μs   (-4.04%) |       1   →       1              |       14.58 μs →       13.99 μs   (-4.04%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.41 ms →      212.72 ms   (-0.32%) |       2   →       2              |      426.82 ms →      425.43 ms   (-0.32%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.19 ms   (+0.24%) |       2   →       2              |       30.30 ms →       30.37 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.26 ms   (+0.04%) |       1   →       1              |       13.26 ms →       13.26 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.30 ms →       56.28 ms   (-0.03%) |       2   →       2              |      112.60 ms →      112.56 ms   (-0.03%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.16 ms →       45.03 ms   (-0.29%) |       2   →       2              |       90.31 ms →       90.05 ms   (-0.29%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.43 ms →       60.28 ms   (-0.24%) |       4   →       4              |      241.70 ms →      241.12 ms   (-0.24%) | 
  │   ├ sddk::Gvec::init                                                |       93.81 ms →       92.85 ms   (-1.02%) |       2   →       2              |      187.62 ms →      185.70 ms   (-1.02%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.22 ms →       69.48 ms   (-1.05%) |       2   →       2              |      140.44 ms →      138.96 ms   (-1.05%) | 
  │   ├ sddk::Gvec_shells                                               |       93.61 ms →       98.81 ms   (+5.56%) |       1   →       1              |       93.61 ms →       98.81 ms   (+5.56%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.94 ms   (+0.39%) |       1   →       1              |        1.94 ms →        1.94 ms   (+0.39%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      659.23 ms →      419.42 ms  (-36.38%) |       2   →       2              |        1.32 s  →      838.84 ms  (-36.38%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       88.39 ms →      144.77 ms  (+63.78%) |       1   →       1              |       88.39 ms →      144.77 ms  (+63.78%) | 
- │ ├ sirius::K_point::K_point                                          |        1.91 μs →        2.55 μs  (+33.67%) |       4   →       4              |        7.64 μs →       10.21 μs  (+33.67%) | 
- │ └ sirius::K_point_set::initialize                                   |       88.31 ms →      144.68 ms  (+63.83%) |       1   →       1              |       88.31 ms →      144.68 ms  (+63.83%) | 
  │   └ sirius::K_point::initialize                                     |       28.28 ms →       28.78 ms   (+1.77%) |       1   →       1              |       28.28 ms →       28.78 ms   (+1.77%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.98 ms →       11.19 ms   (+1.93%) |       1   →       1              |       10.98 ms →       11.19 ms   (+1.93%) | 
  │     │ └ sddk::Gvec::init                                            |        4.92 ms →        5.10 ms   (+3.59%) |       1   →       1              |        4.92 ms →        5.10 ms   (+3.59%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.00 μs →        8.89 μs  (+11.19%) |       1   →       1              |        8.00 μs →        8.89 μs  (+11.19%) | 
  │     └ sirius::K_point::update                                       |       14.44 ms →       14.75 ms   (+2.12%) |       1   →       1              |       14.44 ms →       14.75 ms   (+2.12%) | 
  │       └ sirius::Beta_projectors                                     |       10.49 ms →       10.82 ms   (+3.14%) |       1   →       1              |       10.49 ms →       10.82 ms   (+3.14%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.58 ms →        8.84 ms   (+3.06%) |       1   →       1              |        8.58 ms →        8.84 ms   (+3.06%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.59 ms →        2.59 ms   (+0.18%) |       2   →       2              |        5.18 ms →        5.18 ms   (+0.18%) | 
  ├ sirius::Potential                                                   |       50.01 ms →       51.34 ms   (+2.65%) |       1   →       1              |       50.01 ms →       51.34 ms   (+2.65%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.95 ms   (+0.71%) |       6   →       6              |       17.55 ms →       17.67 ms   (+0.71%) | 
  │ └ sirius::Potential::update                                         |       31.82 ms →       33.14 ms   (+4.14%) |       1   →       1              |       31.82 ms →       33.14 ms   (+4.14%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.45 ms →       32.72 ms   (+4.05%) |       1   →       1              |       31.45 ms →       32.72 ms   (+4.05%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.57 ms →       24.10 ms   (-9.30%) |       1   →       1              |       26.57 ms →       24.10 ms   (-9.30%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.28 ms →        8.10 ms  (+89.38%) |       1   →       1              |        4.28 ms →        8.10 ms  (+89.38%) | 
  ├ sirius::Density                                                     |       38.31 ms →       39.07 ms   (+1.99%) |       1   →       1              |       38.31 ms →       39.07 ms   (+1.99%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.82 ms   (+0.26%) |       2   →       2              |        5.63 ms →        5.65 ms   (+0.26%) | 
  │ └ sirius::Density::update                                           |       32.54 ms →       33.29 ms   (+2.30%) |       1   →       1              |       32.54 ms →       33.29 ms   (+2.30%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       32.30 ms →       33.04 ms   (+2.28%) |       1   →       1              |       32.30 ms →       33.04 ms   (+2.28%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.66 μs →       77.23 μs   (-1.82%) |       1   →       1              |       78.66 μs →       77.23 μs   (-1.82%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.84 ms →       24.37 ms   (-9.20%) |       1   →       1              |       26.84 ms →       24.37 ms   (-9.20%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.07 ms →        8.29 ms  (+63.48%) |       1   →       1              |        5.07 ms →        8.29 ms  (+63.48%) | 
  ├ sirius::Density::initial_density                                    |       57.76 ms →       57.33 ms   (-0.74%) |       1   →       1              |       57.76 ms →       57.33 ms   (-0.74%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.84 ms →       25.22 ms   (-9.44%) |       1   →       1              |       27.84 ms →       25.22 ms   (-9.44%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.37 ms →        6.57 ms  (+22.33%) |       2   →       2              |       10.75 ms →       13.15 ms  (+22.33%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.57 ms →        5.32 ms   (-4.47%) |       1   →       1              |        5.57 ms →        5.32 ms   (-4.47%) | 
  ├ sirius::Potential::generate                                         |      363.08 ms →      366.02 ms   (+0.81%) |       1   →       1              |      363.08 ms →      366.02 ms   (+0.81%) | 
  │ ├ sirius::Potential::poisson                                        |       36.14 ms →       37.39 ms   (+3.47%) |       1   →       1              |       36.14 ms →       37.39 ms   (+3.47%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.56 ms →        8.95 ms  (+96.48%) |       1   →       1              |        4.56 ms →        8.95 ms  (+96.48%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.44 ms →        5.39 ms   (-0.94%) |       1   →       1              |        5.44 ms →        5.39 ms   (-0.94%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.69 ms →        4.64 ms   (-0.99%) |       1   →       1              |        4.69 ms →        4.64 ms   (-0.99%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.68 ms →        4.63 ms   (-1.05%) |       1   →       1              |        4.68 ms →        4.63 ms   (-1.05%) | 
  │ ├ sirius::Periodic_function::add                                    |      785.26 μs →      831.48 μs   (+5.88%) |       2   →       2              |        1.57 ms →        1.66 ms   (+5.88%) | 
  │ ├ sirius::Potential::xc                                             |       50.99 ms →       52.43 ms   (+2.82%) |       1   →       1              |       50.99 ms →       52.43 ms   (+2.82%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.80 ms →       51.23 ms   (+2.88%) |       1   →       1              |       49.80 ms →       51.23 ms   (+2.88%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.54 ms   (+0.23%) |       2   →       2              |        5.08 ms →        5.09 ms   (+0.23%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.24 ms →        4.04 ms   (-4.79%) |       1   →       1              |        4.24 ms →        4.04 ms   (-4.79%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.87 ms →        3.84 ms   (-0.75%) |       1   →       1              |        3.87 ms →        3.84 ms   (-0.75%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.12 ms →      269.32 ms   (+0.07%) |       1   →       1              |      269.12 ms →      269.32 ms   (+0.07%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      453.00 ns →      241.00 ns  (-46.80%) |       1   →       1              |      453.00 ns →      241.00 ns  (-46.80%) | 
- ├ sirius::Hamiltonian0                                                |        6.79 ms →        7.70 ms  (+13.32%) |       1   →       1              |        6.79 ms →        7.70 ms  (+13.32%) | 
- │ ├ sirius::Local_operator                                            |        6.35 ms →        7.21 ms  (+13.52%) |       1   →       1              |        6.35 ms →        7.21 ms  (+13.52%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.73 ms   (+0.16%) |       1   →       1              |        2.73 ms →        2.73 ms   (+0.16%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.90 ms →        3.33 ms  (+15.06%) |       1   →       1              |        2.90 ms →        3.33 ms  (+15.06%) | 
- │ ├ sirius::Non_local_operator                                        |       71.82 μs →      103.53 μs  (+44.15%) |       2   →       2              |      143.65 μs →      207.07 μs  (+44.15%) | 
  │ ├ sirius::D_operator::initialize                                    |      119.02 μs →      117.52 μs   (-1.26%) |       1   →       1              |      119.02 μs →      117.52 μs   (-1.26%) | 
+ │ └ sirius::Q_operator::initialize                                    |      107.92 μs →       90.51 μs  (-16.14%) |       1   →       1              |      107.92 μs →       90.51 μs  (-16.14%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.26 s  →        1.28 s    (+1.68%) |       1   →       1              |        1.26 s  →        1.28 s    (+1.68%) | 
- │ ├ sirius::Hamiltonian_k                                             |       36.47 ms →       61.23 ms  (+67.91%) |       1   →       1              |       36.47 ms →       61.23 ms  (+67.91%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      328.07 μs →      312.40 μs   (-4.78%) |       1   →       1              |      328.07 μs →      312.40 μs   (-4.78%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       36.13 ms →       60.91 ms  (+68.58%) |       1   →       1              |       36.13 ms →       60.91 ms  (+68.58%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.22 s    (-0.29%) |       1   →       1              |        1.22 s  →        1.22 s    (-0.29%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       80.36 ms →       77.80 ms   (-3.17%) |       4   →       4              |      321.42 ms →      311.22 ms   (-3.17%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       34.88 ms →       36.87 ms   (+5.71%) |       1   →       1              |       34.88 ms →       36.87 ms   (+5.71%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.91 ms →        6.88 ms   (-0.43%) |       1   →       1              |        6.91 ms →        6.88 ms   (-0.43%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      312.09 ms →      316.40 ms   (+1.38%) |       1   →       1              |      312.09 ms →      316.40 ms   (+1.38%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      244.34 ms →      246.61 ms   (+0.93%) |       1   →       1              |      244.34 ms →      246.61 ms   (+0.93%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.02 μs →        4.29 μs   (+6.87%) |       1   →       1              |        4.02 μs →        4.29 μs   (+6.87%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.05 μs →        3.35 μs  (+10.07%) |       1   →       1              |        3.05 μs →        3.35 μs  (+10.07%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      604.00 ns →      433.00 ns  (-28.31%) |       1   →       1              |      604.00 ns →      433.00 ns  (-28.31%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      685.00 ns →      692.00 ns   (+1.02%) |       1   →       1              |      685.00 ns →      692.00 ns   (+1.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.13 ms →        3.18 ms   (+1.56%) |       1   →       1              |        3.13 ms →        3.18 ms   (+1.56%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.33 ms →       21.32 ms   (-0.07%) |       1   →       1              |       21.33 ms →       21.32 ms   (-0.07%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       21.62 ms →       22.62 ms   (+4.63%) |       2   →       2              |       43.23 ms →       45.24 ms   (+4.63%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.61 ms →       14.91 ms  (-10.22%) |       2   →       2              |       33.22 ms →       29.82 ms  (-10.22%) | 
+ │ │ │ └ sddk::wf_inner                                                |       16.40 ms →       14.70 ms  (-10.36%) |       2   →       2              |       32.80 ms →       29.40 ms  (-10.36%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.50 ns →       21.50 ns            |       2   →       2              |       43.00 ns →       43.00 ns            | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       16.27 ms →       14.57 ms  (-10.42%) |       2   →       2              |       32.54 ms →       29.15 ms  (-10.42%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.00 ns →       28.50 ns  (+42.50%) |       2   →       2              |       40.00 ns →       57.00 ns  (+42.50%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.95 ms →      250.77 ms   (+0.33%) |       1   →       1              |      249.95 ms →      250.77 ms   (+0.33%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.61 ms   (+0.19%) |       1   →       1              |        2.60 ms →        2.61 ms   (+0.19%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        2.60 ms   (+0.20%) |       1   →       1              |        2.60 ms →        2.60 ms   (+0.20%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      474.00 ns →      501.00 ns   (+5.70%) |       1   →       1              |      474.00 ns →      501.00 ns   (+5.70%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.04 s  →       62.86 s    (+1.32%) |       1   →       1              |       62.04 s  →       62.86 s    (+1.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.45 ms   (+0.14%) |      19   →      19              |       46.55 ms →       46.62 ms   (+0.14%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        2.97 s    (-8.55%) |      19   →      21    (+10.53%) |       61.77 s  →       62.43 s    (+1.08%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        5.58 ms →        5.25 ms   (-6.02%) |      19   →      21    (+10.53%) |      106.04 ms →      110.15 ms   (+3.87%) | 
! │ │ │ ├ sirius::Local_operator                                        |        4.99 ms →        4.62 ms   (-7.37%) |      19   →      21    (+10.53%) |       94.79 ms →       97.05 ms   (+2.38%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      558.04 μs →      545.68 μs   (-2.21%) |      19   →      21    (+10.53%) |       10.60 ms →       11.46 ms   (+8.08%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.25 ms →        2.92 ms  (-10.19%) |      19   →      21    (+10.53%) |       61.75 ms →       61.29 ms   (-0.74%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      153.91 μs →      167.56 μs   (+8.87%) |      38   →      42    (+10.53%) |        5.85 ms →        7.04 ms  (+20.33%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      115.76 μs →      118.83 μs   (+2.65%) |      19   →      21    (+10.53%) |        2.20 ms →        2.50 ms  (+13.45%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       89.78 μs →       90.18 μs   (+0.44%) |      19   →      21    (+10.53%) |        1.71 ms →        1.89 ms  (+11.02%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.49%) |      19   →      21    (+10.53%) |       38.56 s  →       36.87 s    (-4.38%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      199.43 μs →      255.47 μs  (+28.10%) |      19   →      21    (+10.53%) |        3.79 ms →        5.36 ms  (+41.59%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      189.36 μs →      247.14 μs  (+30.52%) |      19   →      21    (+10.53%) |        3.60 ms →        5.19 ms  (+44.25%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.46 μs →        6.14 μs  (-17.74%) |      19   →      21    (+10.53%) |      141.82 μs →      128.94 μs   (-9.08%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.63 s   (-17.05%) |      19   →      21    (+10.53%) |       37.38 s  →       34.27 s    (-8.32%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.61 ms →       66.54 ms  (-13.14%) |      19   →      21    (+10.53%) |        1.46 s  →        1.40 s    (-4.00%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.11 ms →        7.54 ms   (-6.96%) |     114   →     126    (+10.53%) |      924.35 ms →      950.49 ms   (+2.83%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.33 ms →       18.46 ms   (+6.50%) |      19   →      21    (+10.53%) |      329.30 ms →      387.64 ms  (+17.72%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      460.20 μs →      452.64 μs   (-1.64%) |      19   →      21    (+10.53%) |        8.74 ms →        9.51 ms   (+8.71%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.77 ms →        8.44 ms   (+8.62%) |      38   →      42    (+10.53%) |      295.30 ms →      354.51 ms  (+20.05%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.49%) |      19   →      21    (+10.53%) |       35.42 s  →       32.30 s    (-8.80%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       49.68 ms →       50.13 ms   (+0.91%) |     356   →     361     (+1.40%) |       17.69 s  →       18.10 s    (+2.33%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.37 ms →       29.38 ms   (+3.56%) |     356   →     361     (+1.40%) |       10.10 s  →       10.61 s    (+5.01%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.20 μs →        2.10 μs   (-4.70%) |     356   →     361     (+1.40%) |      783.89 μs →      757.57 μs   (-3.36%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.89 μs →        1.76 μs   (-6.81%) |     356   →     361     (+1.40%) |      672.35 μs →      635.38 μs   (-5.50%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      459.25 ns →      483.81 ns   (+5.35%) |     356   →     361     (+1.40%) |      163.49 μs →      174.66 μs   (+6.83%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      642.65 ns →      687.32 ns   (+6.95%) |     356   →     361     (+1.40%) |      228.78 μs →      248.12 μs   (+8.45%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.91 ms →        2.93 ms   (+0.55%) |     356   →     361     (+1.40%) |        1.04 s  →        1.06 s    (+1.96%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.22 ms →        3.19 ms   (-0.89%) |     356   →     361     (+1.40%) |        1.15 s  →        1.15 s    (+0.51%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.58 ms →        7.31 ms   (-3.60%) |     712   →     722     (+1.40%) |        5.40 s  →        5.28 s    (-2.24%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.47 ms →        6.71 ms   (+3.74%) |     356   →     361     (+1.40%) |        2.30 s  →        2.42 s    (+5.20%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.04 ms →        1.08 ms   (+3.75%) |     693   →     701     (+1.15%) |      723.56 ms →      759.37 ms   (+4.95%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       52.74 ns →       45.76 ns  (-13.24%) |     693   →     701     (+1.15%) |       36.55 μs →       32.08 μs  (-12.24%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      883.05 μs →      920.59 μs   (+4.25%) |     693   →     701     (+1.15%) |      611.95 ms →      645.33 ms   (+5.45%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       46.47 ns →       44.48 ns   (-4.27%) |     693   →     701     (+1.15%) |       32.20 μs →       31.18 μs   (-3.17%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      132.57 μs →      132.97 μs   (+0.31%) |     356   →     361     (+1.40%) |       47.19 ms →       48.00 ms   (+1.71%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.11 ms →        2.02 ms   (-4.32%) |     356   →     361     (+1.40%) |      751.07 ms →      728.69 ms   (-2.98%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.31 ms →        2.60 ms  (+12.53%) |     337   →     340     (+0.89%) |      779.31 ms →      884.79 ms  (+13.54%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      770.01 μs →      866.59 μs  (+12.54%) |    1.01 K →    1.02 K   (+0.89%) |      778.48 ms →      883.92 ms  (+13.55%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.38 ms →        1.26 ms   (-9.11%) |     356   →     361     (+1.40%) |      492.06 ms →      453.51 ms   (-7.83%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        1.31 ms →        1.21 ms   (-7.79%) |     356   →     361     (+1.40%) |      467.03 ms →      436.71 ms   (-6.49%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       46.95 ns →       41.66 ns  (-11.27%) |     356   →     361     (+1.40%) |       16.71 μs →       15.04 μs  (-10.03%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.15 ms →        1.05 ms   (-9.05%) |     356   →     361     (+1.40%) |      409.20 ms →      377.40 ms   (-7.77%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       40.82 ns →       45.06 ns  (+10.38%) |     356   →     361     (+1.40%) |       14.53 μs →       16.27 μs  (+11.93%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       38.33 ms →       27.60 ms  (-28.01%) |     356   →     361     (+1.40%) |       13.65 s  →        9.96 s   (-27.00%) | 
  │ │ │ │   ├ sirius::residuals                                         |        2.58 ms →        2.65 ms   (+2.65%) |     340   →     346     (+1.76%) |      878.42 ms →      917.58 ms   (+4.46%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.32 ms →        1.20 ms   (-9.15%) |     337   →     342     (+1.48%) |      446.24 ms →      411.41 ms   (-7.80%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      660.64 μs →      600.03 μs   (-9.17%) |     674   →     684     (+1.48%) |      445.27 ms →      410.42 ms   (-7.83%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.16 ms →        1.38 ms  (+19.59%) |     337   →     342     (+1.48%) |      390.08 ms →      473.43 ms  (+21.37%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.54 ms →        4.93 ms  (-34.70%) |      54   →      90    (+66.67%) |      407.28 ms →      443.26 ms   (+8.84%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        4.53 ms →        2.73 ms  (-39.57%) |      89   →     159    (+78.65%) |      402.78 ms →      434.82 ms   (+7.96%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        3.25 ms →        1.91 ms  (-41.31%) |     124   →     228    (+83.87%) |      402.60 ms →      434.50 ms   (+7.92%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      360.32 ns →      797.10 ns (+121.22%) |      19   →      21    (+10.53%) |        6.85 μs →       16.74 μs (+144.51%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.92 μs →       19.56 μs   (-1.83%) |      19   →      21    (+10.53%) |      378.50 μs →      410.69 μs   (+8.50%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.50 ms →        1.54 ms   (+2.17%) |      19   →      21    (+10.53%) |       28.56 ms →       32.25 ms  (+12.93%) | 
! │ │ ├ sirius::Density::generate                                       |      571.32 ms →      563.22 ms   (-1.42%) |      19   →      21    (+10.53%) |       10.86 s  →       11.83 s    (+8.96%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      401.54 ms →      425.84 ms   (+6.05%) |      19   →      21    (+10.53%) |        7.63 s  →        8.94 s   (+17.21%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.42 μs →        8.22 μs   (-2.31%) |      19   →      21    (+10.53%) |      159.93 μs →      172.69 μs   (+7.98%) | 
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.83 μs →        7.74 μs   (-1.20%) |      19   →      21    (+10.53%) |      148.82 μs →      162.50 μs   (+9.20%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       38.56 ms →       28.13 ms  (-27.03%) |      19   →      21    (+10.53%) |      732.57 ms →      590.80 ms  (-19.35%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.91 μs →        8.04 μs   (+1.75%) |      19   →      21    (+10.53%) |      150.22 μs →      168.94 μs  (+12.46%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.30 ms →        5.21 ms  (-17.36%) |      19   →      21    (+10.53%) |      119.69 ms →      109.32 ms   (-8.66%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       31.21 ms →       21.89 ms  (-29.86%) |      19   →      21    (+10.53%) |      592.97 ms →      459.69 ms  (-22.48%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      603.95 ns →        1.14 μs  (+88.73%) |      19   →      21    (+10.53%) |       11.47 μs →       23.94 μs (+108.60%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      107.47 ms →      117.90 ms   (+9.71%) |      19   →      21    (+10.53%) |        2.04 s  →        2.48 s   (+21.26%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.18 ms →        2.31 ms   (+5.76%) |      19   →      21    (+10.53%) |       41.44 ms →       48.44 ms  (+16.90%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      216.68 ms →      248.49 ms  (+14.68%) |      19   →      21    (+10.53%) |        4.12 s  →        5.22 s   (+26.75%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      216.46 ms →      248.27 ms  (+14.70%) |      19   →      21    (+10.53%) |        4.11 s  →        5.21 s   (+26.77%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      140.72 ms →      109.75 ms  (-22.01%) |      19   →      21    (+10.53%) |        2.67 s  →        2.30 s   (-13.80%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      140.72 ms →      109.75 ms  (-22.01%) |      19   →      21    (+10.53%) |        2.67 s  →        2.30 s   (-13.80%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       57.11 ms →       26.71 ms  (-53.22%) |      19   →      21    (+10.53%) |        1.09 s  →      560.95 ms  (-48.30%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.31 ms →       69.80 ms   (-0.72%) |      19   →      21    (+10.53%) |        1.34 s  →        1.47 s    (+9.73%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.64 ms →       12.58 ms   (-0.48%) |      19   →      21    (+10.53%) |      240.24 ms →      264.26 ms  (+10.00%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.66 ms →       23.48 ms   (-0.77%) |      19   →      21    (+10.53%) |      449.48 ms →      492.98 ms   (+9.68%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.39 ms →        4.16 ms  (-22.92%) |      19   →      21    (+10.53%) |      102.48 ms →       87.31 ms  (-14.81%) | 
- │ │ ├ sirius::Density::mix                                            |      132.11 ms →      134.11 ms   (+1.52%) |      19   →      21    (+10.53%) |        2.51 s  →        2.82 s   (+12.20%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      754.26 μs →      940.38 μs  (+24.68%) |      19   →      21    (+10.53%) |       14.33 ms →       19.75 ms  (+37.80%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.86 ms →        4.68 ms   (-3.69%) |     229   →     259    (+13.10%) |        1.11 s  →        1.21 s    (+8.93%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.62 ms   (-3.99%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.59%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.61 ms   (-3.99%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.59%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.69 ms →        4.53 ms  (-20.40%) |      19   →      21    (+10.53%) |      108.11 ms →       95.11 ms  (-12.02%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.97 ms →        3.87 ms  (-22.27%) |      19   →      21    (+10.53%) |       94.50 ms →       81.19 ms  (-14.08%) | 
- │ │ ├ sirius::Potential::generate                                     |      356.99 ms →      357.78 ms   (+0.22%) |      19   →      21    (+10.53%) |        6.78 s  →        7.51 s   (+10.77%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       36.65 ms →       37.21 ms   (+1.53%) |      19   →      21    (+10.53%) |      696.34 ms →      781.45 ms  (+12.22%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.19 ms →        8.69 ms  (+67.52%) |      19   →      21    (+10.53%) |       98.56 ms →      182.49 ms  (+85.16%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.41 ms →        5.40 ms   (-0.18%) |      19   →      21    (+10.53%) |      102.84 ms →      113.45 ms  (+10.32%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (-0.00%) |      19   →      21    (+10.53%) |       88.01 ms →       97.27 ms  (+10.52%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (-0.01%) |      19   →      21    (+10.53%) |       87.99 ms →       97.24 ms  (+10.52%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      798.71 μs →      806.77 μs   (+1.01%) |      38   →      42    (+10.53%) |       30.35 ms →       33.88 ms  (+11.64%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       44.94 ms →       44.67 ms   (-0.60%) |      19   →      21    (+10.53%) |      853.83 ms →      938.07 ms   (+9.87%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.75 ms →       43.49 ms   (-0.59%) |      19   →      21    (+10.53%) |      831.32 ms →      913.38 ms   (+9.87%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      685.40 μs →      673.78 μs   (-1.70%) |      38   →      42    (+10.53%) |       26.05 ms →       28.30 ms   (+8.65%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.42 ms →        4.12 ms   (-6.86%) |      19   →      21    (+10.53%) |       84.03 ms →       86.50 ms   (+2.95%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.80 ms →        3.92 ms   (+2.96%) |      19   →      21    (+10.53%) |       72.25 ms →       82.22 ms  (+13.80%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.58 ms →      268.94 ms   (+0.14%) |      19   →      21    (+10.53%) |        5.10 s  →        5.65 s   (+10.68%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      302.58 ns →      239.52 ns  (-20.84%) |      19   →      21    (+10.53%) |        5.75 μs →        5.03 μs  (-12.51%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.48 ms →       96.25 ms   (-0.24%) |      19   →      21    (+10.53%) |        1.83 s  →        2.02 s   (+10.26%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.48 ms →       96.25 ms   (-0.24%) |      19   →      21    (+10.53%) |        1.83 s  →        2.02 s   (+10.26%) | 
! │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.43 ms →       13.36 ms   (-0.55%) |      19   →      21    (+10.53%) |      255.22 ms →      280.53 ms   (+9.92%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.84 ms →       69.15 ms   (-0.99%) |      19   →      21    (+10.53%) |        1.33 s  →        1.45 s    (+9.43%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.57 ms →       13.11 ms   (+4.28%) |      19   →      21    (+10.53%) |      238.88 ms →      275.33 ms  (+15.26%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.73 ms →        3.52 ms  (-25.49%) |      19   →      21    (+10.53%) |       89.83 ms →       73.97 ms  (-17.65%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.71 ms →        5.13 ms   (+8.77%) |     133   →     147    (+10.53%) |      626.71 ms →      753.46 ms  (+20.22%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.59 ms →        4.55 ms   (-0.89%) |     133   →     147    (+10.53%) |      610.68 ms →      668.93 ms   (+9.54%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.59 ms →        4.55 ms   (-0.89%) |     133   →     147    (+10.53%) |      610.59 ms →      668.85 ms   (+9.54%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.95 ms   (+0.00%) |      57   →      63    (+10.53%) |      282.15 ms →      311.85 ms  (+10.53%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.73 ms   (-4.39%) |      57   →      63    (+10.53%) |      281.70 ms →      297.70 ms   (+5.68%) | 
! │ │ ├ sirius::Periodic_function::integrate                            |        4.56 ms →        4.53 ms   (-0.52%) |      19   →      21    (+10.53%) |       86.60 ms →       95.22 ms   (+9.96%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       77.84 μs →       75.53 μs   (-2.96%) |      19   →      21    (+10.53%) |        1.48 ms →        1.59 ms   (+7.25%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.87 μs →       70.44 μs   (-3.34%) |      19   →      21    (+10.53%) |        1.38 ms →        1.48 ms   (+6.84%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.08 ms →        5.05 ms   (-0.70%) |       2   →       2              |       10.17 ms →       10.10 ms   (-0.70%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.56 ms →        4.74 ms   (+3.95%) |       6   →       6              |       27.37 ms →       28.45 ms   (+3.95%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.55 ms →        4.74 ms   (+4.05%) |       6   →       6              |       27.31 ms →       28.42 ms   (+4.05%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.55 ms →        4.74 ms   (+4.09%) |       6   →       6              |       27.30 ms →       28.42 ms   (+4.09%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.92 ms →        4.87 ms   (-0.99%) |       3   →       3              |       14.77 ms →       14.62 ms   (-0.99%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.92 ms →        4.87 ms   (-1.03%) |       3   →       3              |       14.75 ms →       14.60 ms   (-1.03%) | 
  ├ sirius::Periodic_function|inner                                     |        4.53 ms →        4.77 ms   (+5.29%) |       2   →       2              |        9.07 ms →        9.55 ms   (+5.29%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.77 ms   (+5.35%) |       2   →       2              |        9.06 ms →        9.54 ms   (+5.35%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.77 ms   (+5.35%) |       2   →       2              |        9.06 ms →        9.54 ms   (+5.35%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.98 ms →        4.95 ms   (-0.55%) |       1   →       1              |        4.98 ms →        4.95 ms   (-0.55%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.97 ms →        4.95 ms   (-0.48%) |       1   →       1              |        4.97 ms →        4.95 ms   (-0.48%) | 
+ └ sirius::finalize                                                    |      500.82 ms →      146.71 ms  (-70.71%) |       1   →       1              |      500.82 ms →      146.71 ms  (-70.71%) | 
  ====================================================================================================================================================================================================
```
