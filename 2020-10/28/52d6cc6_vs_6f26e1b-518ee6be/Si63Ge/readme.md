# Benchmark 6f26e1b85d392e75fe8ae23eb64d38742c01496b vs 52d6cc62f84d89d2fdc84536db65e2617fd3b399
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.97 s  →       72.50 s    (+0.72%) |       1   →       1              |       71.97 s  →       72.50 s    (+0.72%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.79 s    (+0.80%) |       1   →       1              |        2.77 s  →        2.79 s    (+0.80%) | 
  ├ sirius::Simulation_context::initialize                              |        3.74 s  →        3.90 s    (+4.14%) |       1   →       1              |        3.74 s  →        3.90 s    (+4.14%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       28.56 ms →       10.82 ms  (-62.13%) |       1   →       1              |       28.56 ms →       10.82 ms  (-62.13%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      138.61 ms →      174.00 ms  (+25.53%) |       1   →       1              |      138.61 ms →      174.00 ms  (+25.53%) | 
- │ │ ├ sirius::Atom_type::init                                         |       61.30 ms →       77.86 ms  (+27.02%) |       2   →       2              |      122.60 ms →      155.73 ms  (+27.02%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.93 ms →       18.18 ms  (+14.15%) |       1   →       1              |       15.93 ms →       18.18 ms  (+14.15%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.62 ms →        5.07 ms  (+39.91%) |       1   →       1              |        3.62 ms →        5.07 ms  (+39.91%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       12.25 ms →       13.06 ms   (+6.63%) |       1   →       1              |       12.25 ms →       13.06 ms   (+6.63%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       12.18 ms →       12.99 ms   (+6.64%) |       1   →       1              |       12.18 ms →       12.99 ms   (+6.64%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.77 ms   (+1.54%) |       1   →       1              |        2.73 ms →        2.77 ms   (+1.54%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      494.33 μs →      520.26 μs   (+5.25%) |       1   →       1              |      494.33 μs →      520.26 μs   (+5.25%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.00 μs →       17.32 μs   (+1.89%) |       1   →       1              |       17.00 μs →       17.32 μs   (+1.89%) | 
  │ └ sirius::Simulation_context::update                                |        3.52 s  →        3.66 s    (+3.87%) |       1   →       1              |        3.52 s  →        3.66 s    (+3.87%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.79 ms →        6.99 ms   (+2.94%) |       1   →       1              |        6.79 ms →        6.99 ms   (+2.94%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.44 ms →        3.64 ms   (+5.87%) |       1   →       1              |        3.44 ms →        3.64 ms   (+5.87%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.31 ms   (+0.57%) |       1   →       1              |        3.29 ms →        3.31 ms   (+0.57%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.25 ms →        3.27 ms   (+0.57%) |       1   →       1              |        3.25 ms →        3.27 ms   (+0.57%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.72 ms   (+0.50%) |       1   →       1              |        2.70 ms →        2.72 ms   (+0.50%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      509.98 μs →      513.79 μs   (+0.75%) |       1   →       1              |      509.98 μs →      513.79 μs   (+0.75%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.15 μs →       14.11 μs   (-0.25%) |       1   →       1              |       14.15 μs →       14.11 μs   (-0.25%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.12 ms →      213.00 ms   (-0.06%) |       2   →       2              |      426.24 ms →      426.00 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       16.36 ms →       15.59 ms   (-4.71%) |       2   →       2              |       32.72 ms →       31.18 ms   (-4.71%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.24 ms →       13.32 ms   (+0.59%) |       1   →       1              |       13.24 ms →       13.32 ms   (+0.59%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.53 ms →       56.76 ms   (+0.41%) |       2   →       2              |      113.07 ms →      113.53 ms   (+0.41%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.50 ms →       45.15 ms   (-0.78%) |       2   →       2              |       91.01 ms →       90.30 ms   (-0.78%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.38 ms →       60.31 ms   (-0.12%) |       4   →       4              |      241.54 ms →      241.24 ms   (-0.12%) | 
  │   ├ sddk::Gvec::init                                                |       92.78 ms →       93.96 ms   (+1.27%) |       2   →       2              |      185.56 ms →      187.92 ms   (+1.27%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       68.96 ms →       70.23 ms   (+1.84%) |       2   →       2              |      137.92 ms →      140.46 ms   (+1.84%) | 
- │   ├ sddk::Gvec_shells                                               |       95.40 ms →      116.39 ms  (+22.00%) |       1   →       1              |       95.40 ms →      116.39 ms  (+22.00%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.98 ms →        1.97 ms   (-0.70%) |       1   →       1              |        1.98 ms →        1.97 ms   (-0.70%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      605.75 ms →      657.52 ms   (+8.55%) |       2   →       2              |        1.21 s  →        1.32 s    (+8.55%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       88.64 ms →       28.27 ms  (-68.10%) |       1   →       1              |       88.64 ms →       28.27 ms  (-68.10%) | 
- │ ├ sirius::K_point::K_point                                          |        1.39 μs →        1.75 μs  (+26.40%) |       4   →       4              |        5.54 μs →        7.00 μs  (+26.40%) | 
+ │ └ sirius::K_point_set::initialize                                   |       88.56 ms →       28.20 ms  (-68.16%) |       1   →       1              |       88.56 ms →       28.20 ms  (-68.16%) | 
  │   └ sirius::K_point::initialize                                     |       28.26 ms →       27.93 ms   (-1.18%) |       1   →       1              |       28.26 ms →       27.93 ms   (-1.18%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.81 ms →       10.73 ms   (-0.78%) |       1   →       1              |       10.81 ms →       10.73 ms   (-0.78%) | 
  │     │ └ sddk::Gvec::init                                            |        4.84 ms →        4.81 ms   (-0.48%) |       1   →       1              |        4.84 ms →        4.81 ms   (-0.48%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        6.23 μs →        6.58 μs   (+5.57%) |       1   →       1              |        6.23 μs →        6.58 μs   (+5.57%) | 
  │     └ sirius::K_point::update                                       |       14.33 ms →       14.12 ms   (-1.43%) |       1   →       1              |       14.33 ms →       14.12 ms   (-1.43%) | 
  │       └ sirius::Beta_projectors                                     |       10.40 ms →       10.17 ms   (-2.21%) |       1   →       1              |       10.40 ms →       10.17 ms   (-2.21%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.54 ms →        8.25 ms   (-3.39%) |       1   →       1              |        8.54 ms →        8.25 ms   (-3.39%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.58 ms →        2.58 ms   (-0.19%) |       2   →       2              |        5.17 ms →        5.16 ms   (-0.19%) | 
  ├ sirius::Potential                                                   |       50.19 ms →       54.15 ms   (+7.88%) |       1   →       1              |       50.19 ms →       54.15 ms   (+7.88%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.92 ms   (+0.38%) |       6   →       6              |       17.44 ms →       17.51 ms   (+0.38%) | 
- │ └ sirius::Potential::update                                         |       32.20 ms →       36.07 ms  (+12.03%) |       1   →       1              |       32.20 ms →       36.07 ms  (+12.03%) | 
- │   └ sirius::Potential::generate_local_potential                     |       31.78 ms →       35.66 ms  (+12.21%) |       1   →       1              |       31.78 ms →       35.66 ms  (+12.21%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       27.09 ms →       30.82 ms  (+13.77%) |       1   →       1              |       27.09 ms →       30.82 ms  (+13.77%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.14 ms →        4.31 ms   (+4.18%) |       1   →       1              |        4.14 ms →        4.31 ms   (+4.18%) | 
- ├ sirius::Density                                                     |       37.58 ms →       42.07 ms  (+11.92%) |       1   →       1              |       37.58 ms →       42.07 ms  (+11.92%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.80 ms   (-0.43%) |       2   →       2              |        5.63 ms →        5.61 ms   (-0.43%) | 
- │ └ sirius::Density::update                                           |       31.81 ms →       36.31 ms  (+14.16%) |       1   →       1              |       31.81 ms →       36.31 ms  (+14.16%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       31.57 ms →       36.10 ms  (+14.32%) |       1   →       1              |       31.57 ms →       36.10 ms  (+14.32%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.10 μs →       78.21 μs   (+0.15%) |       1   →       1              |       78.10 μs →       78.21 μs   (+0.15%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.65 ms →       29.74 ms  (+11.57%) |       1   →       1              |       26.65 ms →       29.74 ms  (+11.57%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.53 ms →        5.98 ms  (+31.81%) |       1   →       1              |        4.53 ms →        5.98 ms  (+31.81%) | 
- ├ sirius::Density::initial_density                                    |       55.64 ms →       61.90 ms  (+11.26%) |       1   →       1              |       55.64 ms →       61.90 ms  (+11.26%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       27.61 ms →       32.79 ms  (+18.75%) |       1   →       1              |       27.61 ms →       32.79 ms  (+18.75%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.56 ms →        4.95 ms   (+8.47%) |       2   →       2              |        9.13 ms →        9.90 ms   (+8.47%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.29 ms →        5.73 ms   (+8.45%) |       1   →       1              |        5.29 ms →        5.73 ms   (+8.45%) | 
  ├ sirius::Potential::generate                                         |      363.59 ms →      370.05 ms   (+1.78%) |       1   →       1              |      363.59 ms →      370.05 ms   (+1.78%) | 
- │ ├ sirius::Potential::poisson                                        |       36.21 ms →       43.28 ms  (+19.53%) |       1   →       1              |       36.21 ms →       43.28 ms  (+19.53%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.86 ms →        4.07 ms  (-16.18%) |       1   →       1              |        4.86 ms →        4.07 ms  (-16.18%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.65 ms →        4.84 ms  (-14.37%) |       1   →       1              |        5.65 ms →        4.84 ms  (-14.37%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.84 ms →        4.83 ms   (-0.16%) |       1   →       1              |        4.84 ms →        4.83 ms   (-0.16%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.82 ms   (-0.16%) |       1   →       1              |        4.83 ms →        4.82 ms   (-0.16%) | 
  │ ├ sirius::Periodic_function::add                                    |      782.26 μs →      769.96 μs   (-1.57%) |       2   →       2              |        1.56 ms →        1.54 ms   (-1.57%) | 
  │ ├ sirius::Potential::xc                                             |       51.01 ms →       51.31 ms   (+0.60%) |       1   →       1              |       51.01 ms →       51.31 ms   (+0.60%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.83 ms →       50.11 ms   (+0.55%) |       1   →       1              |       49.83 ms →       50.11 ms   (+0.55%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.55 ms   (+0.25%) |       2   →       2              |        5.08 ms →        5.09 ms   (+0.25%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.10 ms →        4.69 ms  (+14.36%) |       1   →       1              |        4.10 ms →        4.69 ms  (+14.36%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.81 ms →        3.60 ms   (-5.64%) |       1   →       1              |        3.81 ms →        3.60 ms   (-5.64%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.64 ms →      268.99 ms   (-0.24%) |       1   →       1              |      269.64 ms →      268.99 ms   (-0.24%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      208.00 ns →      178.00 ns  (-14.42%) |       1   →       1              |      208.00 ns →      178.00 ns  (-14.42%) | 
- ├ sirius::Hamiltonian0                                                |        6.88 ms →        8.58 ms  (+24.72%) |       1   →       1              |        6.88 ms →        8.58 ms  (+24.72%) | 
- │ ├ sirius::Local_operator                                            |        6.30 ms →        7.50 ms  (+19.04%) |       1   →       1              |        6.30 ms →        7.50 ms  (+19.04%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.75 ms   (+0.84%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.84%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.80 ms →        3.78 ms  (+34.69%) |       1   →       1              |        2.80 ms →        3.78 ms  (+34.69%) | 
- │ ├ sirius::Non_local_operator                                        |      118.03 μs →      406.57 μs (+244.47%) |       2   →       2              |      236.05 μs →      813.13 μs (+244.47%) | 
+ │ ├ sirius::D_operator::initialize                                    |      146.07 μs →      100.43 μs  (-31.25%) |       1   →       1              |      146.07 μs →      100.43 μs  (-31.25%) | 
+ │ └ sirius::Q_operator::initialize                                    |      108.29 μs →       92.99 μs  (-14.13%) |       1   →       1              |      108.29 μs →       92.99 μs  (-14.13%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.27 s    (-0.04%) |       1   →       1              |        1.27 s  →        1.27 s    (-0.04%) | 
- │ ├ sirius::Hamiltonian_k                                             |       49.89 ms →       73.84 ms  (+48.00%) |       1   →       1              |       49.89 ms →       73.84 ms  (+48.00%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      343.76 μs →      254.85 μs  (-25.86%) |       1   →       1              |      343.76 μs →      254.85 μs  (-25.86%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       49.54 ms →       73.58 ms  (+48.52%) |       1   →       1              |       49.54 ms →       73.58 ms  (+48.52%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.20 s    (-2.00%) |       1   →       1              |        1.22 s  →        1.20 s    (-2.00%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       76.04 ms →      101.39 ms  (+33.34%) |       4   →       4              |      304.16 ms →      405.56 ms  (+33.34%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.13 ms →       36.16 ms  (-23.27%) |       1   →       1              |       47.13 ms →       36.16 ms  (-23.27%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.78 ms →        6.59 ms  (-15.23%) |       1   →       1              |        7.78 ms →        6.59 ms  (-15.23%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.69 ms →      451.32 ms  (+27.24%) |       1   →       1              |      354.69 ms →      451.32 ms  (+27.24%) | 
- │ │ │ ├ sirius::Local_operator::apply_h                               |      249.41 ms →      384.67 ms  (+54.23%) |       1   →       1              |      249.41 ms →      384.67 ms  (+54.23%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.92 μs →        3.61 μs   (-7.98%) |       1   →       1              |        3.92 μs →        3.61 μs   (-7.98%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.02 μs →        2.72 μs   (-9.72%) |       1   →       1              |        3.02 μs →        2.72 μs   (-9.72%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      459.00 ns →      450.00 ns   (-1.96%) |       1   →       1              |      459.00 ns →      450.00 ns   (-1.96%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      595.00 ns →        1.25 μs (+110.92%) |       1   →       1              |      595.00 ns →        1.25 μs (+110.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.29 ms →        3.05 ms   (-7.52%) |       1   →       1              |        3.29 ms →        3.05 ms   (-7.52%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       23.52 ms →       21.22 ms   (-9.78%) |       1   →       1              |       23.52 ms →       21.22 ms   (-9.78%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       39.22 ms →       21.17 ms  (-46.01%) |       2   →       2              |       78.43 ms →       42.35 ms  (-46.01%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.77 ms →       14.77 ms  (-11.93%) |       2   →       2              |       33.54 ms →       29.54 ms  (-11.93%) | 
+ │ │ │ └ sddk::wf_inner                                                |       16.56 ms →       14.56 ms  (-12.08%) |       2   →       2              |       33.12 ms →       29.12 ms  (-12.08%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       36.50 ns →       19.50 ns  (-46.58%) |       2   →       2              |       73.00 ns →       39.00 ns  (-46.58%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       16.43 ms →       14.44 ms  (-12.14%) |       2   →       2              |       32.86 ms →       28.87 ms  (-12.14%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.00 ns →       26.50 ns  (+20.45%) |       2   →       2              |       44.00 ns →       53.00 ns  (+20.45%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      211.28 ms →      111.20 ms  (-47.37%) |       1   →       1              |      211.28 ms →      111.20 ms  (-47.37%) | 
  │ │ └ sddk::wf_trans                                                  |        2.67 ms →        2.59 ms   (-2.96%) |       1   →       1              |        2.67 ms →        2.59 ms   (-2.96%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.67 ms →        2.59 ms   (-2.87%) |       1   →       1              |        2.67 ms →        2.59 ms   (-2.87%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      513.00 ns →      320.00 ns  (-37.62%) |       1   →       1              |      513.00 ns →      320.00 ns  (-37.62%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.48 s  →       62.85 s    (+0.60%) |       1   →       1              |       62.48 s  →       62.85 s    (+0.60%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.44 ms   (-0.38%) |      19   →      19              |       46.47 ms →       46.29 ms   (-0.38%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.96 s  →        2.98 s    (+0.58%) |      21   →      21              |       62.25 s  →       62.61 s    (+0.58%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.04 ms →        4.99 ms   (-1.02%) |      21   →      21              |      105.87 ms →      104.78 ms   (-1.02%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.38 ms →        4.25 ms   (-3.13%) |      21   →      21              |       92.03 ms →       89.15 ms   (-3.13%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      566.22 μs →      534.42 μs   (-5.62%) |      21   →      21              |       11.89 ms →       11.22 ms   (-5.62%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.77 ms →        2.58 ms   (-7.14%) |      21   →      21              |       58.27 ms →       54.11 ms   (-7.14%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      180.14 μs →      231.60 μs  (+28.57%) |      42   →      42              |        7.57 ms →        9.73 ms  (+28.57%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      122.57 μs →      115.49 μs   (-5.78%) |      21   →      21              |        2.57 ms →        2.43 ms   (-5.78%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       93.45 μs →       89.08 μs   (-4.68%) |      21   →      21              |        1.96 ms →        1.87 ms   (-4.68%) | 
  │ │ ├ sirius::Band::solve                                             |        1.75 s  →        1.76 s    (+0.01%) |      21   →      21              |       36.85 s  →       36.86 s    (+0.01%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      214.07 μs →      206.79 μs   (-3.40%) |      21   →      21              |        4.50 ms →        4.34 ms   (-3.40%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      204.34 μs →      197.91 μs   (-3.15%) |      21   →      21              |        4.29 ms →        4.16 ms   (-3.15%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.92 μs →        6.71 μs   (-3.02%) |      21   →      21              |      145.32 μs →      140.94 μs   (-3.02%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.62 s  →        1.63 s    (+0.78%) |      21   →      21              |       34.04 s  →       34.31 s    (+0.78%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       65.85 ms →       73.62 ms  (+11.81%) |      21   →      21              |        1.38 s  →        1.55 s   (+11.81%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.29 ms →        7.31 ms   (+0.30%) |     126   →     126              |      918.87 ms →      921.61 ms   (+0.30%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.83 ms →       15.52 ms   (-7.79%) |      21   →      21              |      353.37 ms →      325.84 ms   (-7.79%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      454.50 μs →      478.53 μs   (+5.29%) |      21   →      21              |        9.54 ms →       10.05 ms   (+5.29%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.56 ms →        7.05 ms   (-6.75%) |      42   →      42              |      317.66 ms →      296.22 ms   (-6.75%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.53 s  →        1.54 s    (+0.41%) |      21   →      21              |       32.13 s  →       32.26 s    (+0.41%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       47.56 ms →       59.39 ms  (+24.88%) |     361   →     361              |       17.17 s  →       21.44 s   (+24.88%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.75 ms →       36.08 ms  (+25.51%) |     361   →     361              |       10.38 s  →       13.03 s   (+25.51%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.07 μs →        1.94 μs   (-6.03%) |     361   →     361              |      745.48 μs →      700.51 μs   (-6.03%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.68 μs →        1.58 μs   (-5.71%) |     361   →     361              |      605.37 μs →      570.80 μs   (-5.71%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      396.51 ns →      414.00 ns   (+4.41%) |     361   →     361              |      143.14 μs →      149.46 μs   (+4.41%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      581.04 ns →      480.94 ns  (-17.23%) |     361   →     361              |      209.75 μs →      173.62 μs  (-17.23%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.76 ms →        3.23 ms  (+16.86%) |     361   →     361              |      997.84 ms →        1.17 s   (+16.86%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.22 ms →        3.49 ms   (+8.26%) |     361   →     361              |        1.16 s  →        1.26 s    (+8.26%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.40 ms →        8.28 ms  (+29.38%) |     722   →     722              |        4.62 s  →        5.98 s   (+29.38%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.22 ms →        6.35 ms   (+2.12%) |     361   →     361              |        2.25 s  →        2.29 s    (+2.12%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.02 ms →        1.19 ms  (+17.19%) |     701   →     701              |      713.18 ms →      835.78 ms  (+17.19%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       40.91 ns →       41.39 ns   (+1.18%) |     701   →     701              |       28.68 μs →       29.01 μs   (+1.18%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      856.22 μs →        1.03 ms  (+20.03%) |     701   →     701              |      600.21 ms →      720.41 ms  (+20.03%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       44.59 ns →       58.13 ns  (+30.36%) |     701   →     701              |       31.26 μs →       40.75 μs  (+30.36%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      135.73 μs →      146.50 μs   (+7.94%) |     361   →     361              |       49.00 ms →       52.89 ms   (+7.94%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.87 ms →        1.80 ms   (-4.13%) |     361   →     361              |      676.25 ms →      648.32 ms   (-4.13%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.37 ms →        2.22 ms   (-6.33%) |     340   →     340              |      805.52 ms →      754.53 ms   (-6.33%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      788.91 μs →      738.91 μs   (-6.34%) |    1.02 K →    1.02 K            |      804.69 ms →      753.68 ms   (-6.34%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.23 ms →        1.22 ms   (-0.94%) |     361   →     361              |      444.02 ms →      439.86 ms   (-0.94%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        1.19 ms →        1.17 ms   (-1.40%) |     361   →     361              |      428.74 ms →      422.72 ms   (-1.40%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.27 ns →       42.60 ns   (+3.23%) |     361   →     361              |       14.90 μs →       15.38 μs   (+3.23%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.02 ms →        1.01 ms   (-1.78%) |     361   →     361              |      369.60 ms →      363.01 ms   (-1.78%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.93 ns →       53.98 ns  (+22.88%) |     361   →     361              |       15.86 μs →       19.49 μs  (+22.88%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       30.83 ms →       18.56 ms  (-39.80%) |     361   →     361              |       11.13 s  →        6.70 s   (-39.80%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.16 ms →        2.71 ms  (+25.01%) |     346   →     346              |      749.03 ms →      936.36 ms  (+25.01%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.05 ms →        1.20 ms  (+13.56%) |     342   →     342              |      360.77 ms →      409.67 ms  (+13.56%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      526.00 μs →      597.46 μs  (+13.59%) |     684   →     684              |      359.78 ms →      408.66 ms  (+13.59%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.04 ms →        1.43 ms  (+37.54%) |     342   →     342              |      356.21 ms →      489.94 ms  (+37.54%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.27 ms →        4.94 ms  (+15.72%) |      90   →      90              |      384.40 ms →      444.85 ms  (+15.72%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.37 ms →        2.75 ms  (+16.00%) |     159   →     159              |      376.41 ms →      436.62 ms  (+16.00%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.65 ms →        1.91 ms  (+16.01%) |     228   →     228              |      376.09 ms →      436.31 ms  (+16.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      533.67 ns →      525.71 ns   (-1.49%) |      21   →      21              |       11.21 μs →       11.04 μs   (-1.49%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.88 μs →       20.47 μs   (-1.96%) |      21   →      21              |      438.54 μs →      429.94 μs   (-1.96%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.55 ms →        1.52 ms   (-1.67%) |      21   →      21              |       32.56 ms →       32.02 ms   (-1.67%) | 
  │ │ ├ sirius::Density::generate                                       |      561.56 ms →      565.80 ms   (+0.75%) |      21   →      21              |       11.79 s  →       11.88 s    (+0.75%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      403.37 ms →      395.85 ms   (-1.86%) |      21   →      21              |        8.47 s  →        8.31 s    (-1.86%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.44 μs →        7.57 μs   (+1.83%) |      21   →      21              |      156.15 μs →      159.01 μs   (+1.83%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.77 μs →        6.94 μs   (+2.60%) |      21   →      21              |      142.10 μs →      145.80 μs   (+2.60%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       25.64 ms →       39.02 ms  (+52.17%) |      21   →      21              |      538.49 ms →      819.42 ms  (+52.17%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.37 μs →       11.24 μs   (-1.16%) |      21   →      21              |      238.84 μs →      236.07 μs   (-1.16%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        4.68 ms →       22.66 ms (+383.66%) |      21   →      21              |       98.38 ms →      475.83 ms (+383.66%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       19.90 ms →       15.32 ms  (-23.03%) |      21   →      21              |      417.85 ms →      321.63 ms  (-23.03%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |        1.06 μs →      930.38 ns  (-12.60%) |      21   →      21              |       22.35 μs →       19.54 μs  (-12.60%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      120.42 ms →      100.50 ms  (-16.55%) |      21   →      21              |        2.53 s  →        2.11 s   (-16.55%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.14 ms →        2.07 ms  (-59.64%) |      21   →      21              |      107.92 ms →       43.56 ms  (-59.64%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      210.71 ms →      209.36 ms   (-0.64%) |      21   →      21              |        4.42 s  →        4.40 s    (-0.64%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      210.50 ms →      209.14 ms   (-0.64%) |      21   →      21              |        4.42 s  →        4.39 s    (-0.64%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      131.01 ms →      142.10 ms   (+8.47%) |      21   →      21              |        2.75 s  →        2.98 s    (+8.47%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      131.01 ms →      142.10 ms   (+8.47%) |      21   →      21              |        2.75 s  →        2.98 s    (+8.47%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       49.75 ms →       57.90 ms  (+16.39%) |      21   →      21              |        1.04 s  →        1.22 s   (+16.39%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.00 ms →       67.72 ms   (-0.41%) |      21   →      21              |        1.43 s  →        1.42 s    (-0.41%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.61 ms →       15.83 ms  (+25.48%) |      21   →      21              |      264.89 ms →      332.37 ms  (+25.48%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.54 ms →       23.62 ms   (+0.32%) |      21   →      21              |      494.44 ms →      496.01 ms   (+0.32%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.64 ms →        4.22 ms  (+15.99%) |      21   →      21              |       76.36 ms →       88.57 ms  (+15.99%) | 
  │ │ ├ sirius::Density::mix                                            |      134.37 ms →      135.72 ms   (+1.01%) |      21   →      21              |        2.82 s  →        2.85 s    (+1.01%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      496.59 μs →      863.03 μs  (+73.79%) |      21   →      21              |       10.43 ms →       18.12 ms  (+73.79%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.77 ms →        4.86 ms   (+1.81%) |     259   →     259              |        1.24 s  →        1.26 s    (+1.81%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.63 ms →        4.81 ms   (+3.81%) |     259   →     259              |        1.20 s  →        1.24 s    (+3.81%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.63 ms →        4.81 ms   (+3.81%) |     259   →     259              |        1.20 s  →        1.24 s    (+3.81%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        5.80 ms →        5.88 ms   (+1.39%) |      21   →      21              |      121.81 ms →      123.50 ms   (+1.39%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.08 ms →        5.09 ms   (+0.08%) |      21   →      21              |      106.70 ms →      106.79 ms   (+0.08%) | 
  │ │ ├ sirius::Potential::generate                                     |      356.61 ms →      363.61 ms   (+1.96%) |      21   →      21              |        7.49 s  →        7.64 s    (+1.96%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.81 ms →       43.61 ms  (+21.76%) |      21   →      21              |      752.09 ms →      915.76 ms  (+21.76%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.57 ms →        3.34 ms  (-26.92%) |      21   →      21              |       96.07 ms →       70.20 ms  (-26.92%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.62 ms →        6.09 ms   (+8.47%) |      21   →      21              |      117.93 ms →      127.92 ms   (+8.47%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.83 ms →        4.83 ms   (-0.09%) |      21   →      21              |      101.51 ms →      101.42 ms   (-0.09%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms →        4.83 ms   (-0.10%) |      21   →      21              |      101.49 ms →      101.39 ms   (-0.10%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      779.74 μs →      788.79 μs   (+1.16%) |      42   →      42              |       32.75 ms →       33.13 ms   (+1.16%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.76 ms →       44.99 ms   (+0.51%) |      21   →      21              |      939.90 ms →      944.70 ms   (+0.51%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.58 ms →       43.82 ms   (+0.56%) |      21   →      21              |      915.12 ms →      920.23 ms   (+0.56%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      683.96 μs →      674.94 μs   (-1.32%) |      42   →      42              |       28.73 ms →       28.35 ms   (-1.32%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.27 ms →        4.66 ms   (+9.05%) |      21   →      21              |       89.69 ms →       97.81 ms   (+9.05%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        3.44 ms  (-11.50%) |      21   →      21              |       81.60 ms →       72.21 ms  (-11.50%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.18 ms →      268.59 ms   (-0.22%) |      21   →      21              |        5.65 s  →        5.64 s    (-0.22%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      226.76 ns →      189.14 ns  (-16.59%) |      21   →      21              |        4.76 μs →        3.97 μs  (-16.59%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       93.61 ms →       99.87 ms   (+6.69%) |      21   →      21              |        1.97 s  →        2.10 s    (+6.69%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       93.60 ms →       99.87 ms   (+6.69%) |      21   →      21              |        1.97 s  →        2.10 s    (+6.69%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.20 ms →       16.06 ms  (+21.70%) |      21   →      21              |      277.14 ms →      337.27 ms  (+21.70%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       67.25 ms →       67.31 ms   (+0.08%) |      21   →      21              |        1.41 s  →        1.41 s    (+0.08%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.53 ms →       15.87 ms  (+26.69%) |      21   →      21              |      263.09 ms →      333.30 ms  (+26.69%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.89 ms →        3.59 ms   (-7.81%) |      21   →      21              |       81.73 ms →       75.34 ms   (-7.81%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.88 ms →        4.59 ms   (-6.11%) |     147   →     147              |      717.99 ms →      674.14 ms   (-6.11%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.56 ms   (-4.30%) |     147   →     147              |      700.20 ms →      670.08 ms   (-4.30%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.56 ms   (-4.30%) |     147   →     147              |      700.11 ms →      670.00 ms   (-4.30%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.54 ms →        4.77 ms   (+5.01%) |      63   →      63              |      286.07 ms →      300.40 ms   (+5.01%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.53 ms →        4.74 ms   (+4.57%) |      63   →      63              |      285.40 ms →      298.43 ms   (+4.57%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.53 ms   (+0.11%) |      21   →      21              |       95.06 ms →       95.17 ms   (+0.11%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.68 μs →       76.80 μs   (+1.48%) |      21   →      21              |        1.59 ms →        1.61 ms   (+1.48%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.89 μs →       72.01 μs   (+1.58%) |      21   →      21              |        1.49 ms →        1.51 ms   (+1.58%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.14 ms →        5.53 ms   (+7.54%) |       2   →       2              |       10.28 ms →       11.05 ms   (+7.54%) | 
  │ ├ sirius::Periodic_function|inner                                   |        5.04 ms →        4.66 ms   (-7.62%) |       6   →       6              |       30.26 ms →       27.95 ms   (-7.62%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        5.02 ms →        4.66 ms   (-7.19%) |       6   →       6              |       30.09 ms →       27.93 ms   (-7.19%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        5.02 ms →        4.65 ms   (-7.18%) |       6   →       6              |       30.09 ms →       27.93 ms   (-7.18%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.52 ms →        4.85 ms   (+7.34%) |       3   →       3              |       13.56 ms →       14.56 ms   (+7.34%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.51 ms →        4.85 ms   (+7.41%) |       3   →       3              |       13.53 ms →       14.54 ms   (+7.41%) | 
  ├ sirius::Periodic_function|inner                                     |        4.72 ms →        4.63 ms   (-1.90%) |       2   →       2              |        9.45 ms →        9.27 ms   (-1.90%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.72 ms →        4.63 ms   (-1.89%) |       2   →       2              |        9.43 ms →        9.25 ms   (-1.89%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.72 ms →        4.63 ms   (-1.89%) |       2   →       2              |        9.43 ms →        9.25 ms   (-1.89%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.51 ms →        4.83 ms   (+7.04%) |       1   →       1              |        4.51 ms →        4.83 ms   (+7.04%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.50 ms →        4.83 ms   (+7.28%) |       1   →       1              |        4.50 ms →        4.83 ms   (+7.28%) | 
+ └ sirius::finalize                                                    |      500.18 ms →      173.38 ms  (-65.34%) |       1   →       1              |      500.18 ms →      173.38 ms  (-65.34%) | 
  ====================================================================================================================================================================================================
```
