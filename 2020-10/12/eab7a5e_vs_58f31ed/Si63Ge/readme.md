# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.37 s  →       80.96 s   (+13.43%) |       1   →       1              |       71.37 s  →       80.96 s   (+13.43%) | 
- ├ sirius::initialize                                                  |        2.52 s  →        2.85 s   (+12.81%) |       1   →       1              |        2.52 s  →        2.85 s   (+12.81%) | 
+ ├ sirius::Simulation_context::initialize                              |        3.77 s  →        3.25 s   (-13.71%) |       1   →       1              |        3.77 s  →        3.25 s   (-13.71%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      148.07 ms →       33.98 ms  (-77.05%) |       1   →       1              |      148.07 ms →       33.98 ms  (-77.05%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      136.68 ms →      141.90 ms   (+3.81%) |       1   →       1              |      136.68 ms →      141.90 ms   (+3.81%) | 
  │ │ ├ sirius::Atom_type::init                                         |       60.28 ms →       63.17 ms   (+4.80%) |       2   →       2              |      120.55 ms →      126.34 ms   (+4.80%) | 
  │ │ └ sirius::Unit_cell::update                                       |       16.04 ms →       15.47 ms   (-3.60%) |       1   →       1              |       16.04 ms →       15.47 ms   (-3.60%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.45 ms →        3.58 ms  (-44.50%) |       1   →       1              |        6.45 ms →        3.58 ms  (-44.50%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |        9.55 ms →       11.81 ms  (+23.76%) |       1   →       1              |        9.55 ms →       11.81 ms  (+23.76%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |        9.49 ms →       11.75 ms  (+23.85%) |       1   →       1              |        9.49 ms →       11.75 ms  (+23.85%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.74 ms   (+0.81%) |       1   →       1              |        2.72 ms →        2.74 ms   (+0.81%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      505.57 μs →      498.60 μs   (-1.38%) |       1   →       1              |      505.57 μs →      498.60 μs   (-1.38%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       14.66 μs →       24.95 μs  (+70.12%) |       1   →       1              |       14.66 μs →       24.95 μs  (+70.12%) | 
+ │ └ sirius::Simulation_context::update                                |        3.39 s  →        3.03 s   (-10.72%) |       1   →       1              |        3.39 s  →        3.03 s   (-10.72%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.76 ms →        7.02 ms   (+3.96%) |       1   →       1              |        6.76 ms →        7.02 ms   (+3.96%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.42 ms →        3.65 ms   (+6.67%) |       1   →       1              |        3.42 ms →        3.65 ms   (+6.67%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.30 ms   (+0.23%) |       1   →       1              |        3.29 ms →        3.30 ms   (+0.23%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.23 ms   (+0.23%) |       1   →       1              |        3.23 ms →        3.23 ms   (+0.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.69 ms →        2.70 ms   (+0.36%) |       1   →       1              |        2.69 ms →        2.70 ms   (+0.36%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      500.30 μs →      497.10 μs   (-0.64%) |       1   →       1              |      500.30 μs →      497.10 μs   (-0.64%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.97 μs →       13.88 μs   (-0.67%) |       1   →       1              |       13.97 μs →       13.88 μs   (-0.67%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.09 ms →      212.86 ms   (+0.36%) |       2   →       2              |      424.18 ms →      425.71 ms   (+0.36%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.16 ms   (+0.04%) |       2   →       2              |       30.30 ms →       30.32 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.27 ms →       13.25 ms   (-0.12%) |       1   →       1              |       13.27 ms →       13.25 ms   (-0.12%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.42 ms →       56.39 ms   (-0.05%) |       2   →       2              |      112.84 ms →      112.78 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.17 ms →       45.18 ms   (+0.02%) |       2   →       2              |       90.34 ms →       90.36 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.44 ms →       60.36 ms   (-0.13%) |       4   →       4              |      241.75 ms →      241.43 ms   (-0.13%) | 
  │   ├ sddk::Gvec::init                                                |       95.27 ms →       93.13 ms   (-2.24%) |       2   →       2              |      190.53 ms →      186.26 ms   (-2.24%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.62 ms →       69.85 ms   (-1.10%) |       2   →       2              |      141.24 ms →      139.70 ms   (-1.10%) | 
  │   ├ sddk::Gvec_shells                                               |       97.44 ms →       95.57 ms   (-1.91%) |       1   →       1              |       97.44 ms →       95.57 ms   (-1.91%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.38%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.38%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      566.46 ms →      372.94 ms  (-34.16%) |       2   →       2              |        1.13 s  →      745.88 ms  (-34.16%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |      151.66 ms →      522.10 ms (+244.25%) |       1   →       1              |      151.66 ms →      522.10 ms (+244.25%) | 
  │ ├ sirius::K_point::K_point                                          |        2.36 μs →        2.43 μs   (+2.82%) |       4   →       4              |        9.45 μs →        9.71 μs   (+2.82%) | 
- │ └ sirius::K_point_set::initialize                                   |      151.58 ms →      522.02 ms (+244.39%) |       1   →       1              |      151.58 ms →      522.02 ms (+244.39%) | 
  │   └ sirius::K_point::initialize                                     |       28.63 ms →       28.21 ms   (-1.47%) |       1   →       1              |       28.63 ms →       28.21 ms   (-1.47%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.37 ms →       10.92 ms   (-3.97%) |       1   →       1              |       11.37 ms →       10.92 ms   (-3.97%) | 
  │     │ └ sddk::Gvec::init                                            |        5.15 ms →        4.93 ms   (-4.13%) |       1   →       1              |        5.15 ms →        4.93 ms   (-4.13%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.17 μs →        9.44 μs  (+31.76%) |       1   →       1              |        7.17 μs →        9.44 μs  (+31.76%) | 
  │     └ sirius::K_point::update                                       |       14.37 ms →       14.47 ms   (+0.65%) |       1   →       1              |       14.37 ms →       14.47 ms   (+0.65%) | 
  │       └ sirius::Beta_projectors                                     |       10.32 ms →       10.60 ms   (+2.70%) |       1   →       1              |       10.32 ms →       10.60 ms   (+2.70%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.26 ms →        8.73 ms   (+5.67%) |       1   →       1              |        8.26 ms →        8.73 ms   (+5.67%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.54 ms   (-0.41%) |       2   →       2              |        5.11 ms →        5.09 ms   (-0.41%) | 
  ├ sirius::Potential                                                   |       52.44 ms →       51.52 ms   (-1.76%) |       1   →       1              |       52.44 ms →       51.52 ms   (-1.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.89 ms   (-1.53%) |       6   →       6              |       17.60 ms →       17.33 ms   (-1.53%) | 
  │ └ sirius::Potential::update                                         |       34.26 ms →       33.57 ms   (-2.01%) |       1   →       1              |       34.26 ms →       33.57 ms   (-2.01%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.87 ms →       33.17 ms   (-2.09%) |       1   →       1              |       33.87 ms →       33.17 ms   (-2.09%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.62 ms →       26.73 ms   (+0.44%) |       1   →       1              |       26.62 ms →       26.73 ms   (+0.44%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.74 ms →        5.91 ms  (-12.23%) |       1   →       1              |        6.74 ms →        5.91 ms  (-12.23%) | 
  ├ sirius::Density                                                     |       39.87 ms →       39.88 ms   (+0.02%) |       1   →       1              |       39.87 ms →       39.88 ms   (+0.02%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.82 ms   (-0.79%) |       2   →       2              |        5.68 ms →        5.64 ms   (-0.79%) | 
  │ └ sirius::Density::update                                           |       34.05 ms →       34.10 ms   (+0.15%) |       1   →       1              |       34.05 ms →       34.10 ms   (+0.15%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       33.78 ms →       33.89 ms   (+0.33%) |       1   →       1              |       33.78 ms →       33.89 ms   (+0.33%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       75.94 μs →       77.73 μs   (+2.35%) |       1   →       1              |       75.94 μs →       77.73 μs   (+2.35%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.77 ms →       26.72 ms   (-0.20%) |       1   →       1              |       26.77 ms →       26.72 ms   (-0.20%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.63 ms →        6.80 ms   (+2.57%) |       1   →       1              |        6.63 ms →        6.80 ms   (+2.57%) | 
  ├ sirius::Density::initial_density                                    |       60.15 ms →       60.63 ms   (+0.80%) |       1   →       1              |       60.15 ms →       60.63 ms   (+0.80%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.58 ms →       26.99 ms   (-2.13%) |       1   →       1              |       27.58 ms →       26.99 ms   (-2.13%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.03 ms →        7.62 ms   (+8.40%) |       2   →       2              |       14.06 ms →       15.24 ms   (+8.40%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.94 ms →        4.79 ms   (-2.88%) |       1   →       1              |        4.94 ms →        4.79 ms   (-2.88%) | 
  ├ sirius::Potential::generate                                         |      367.78 ms →      365.69 ms   (-0.57%) |       1   →       1              |      367.78 ms →      365.69 ms   (-0.57%) | 
  │ ├ sirius::Potential::poisson                                        |       40.53 ms →       38.45 ms   (-5.14%) |       1   →       1              |       40.53 ms →       38.45 ms   (-5.14%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.21 ms →        7.55 ms  (-18.04%) |       1   →       1              |        9.21 ms →        7.55 ms  (-18.04%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.15 ms →        4.98 ms   (-3.26%) |       1   →       1              |        5.15 ms →        4.98 ms   (-3.26%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.63 ms   (+0.04%) |       1   →       1              |        4.63 ms →        4.63 ms   (+0.04%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.62 ms →        4.62 ms   (+0.03%) |       1   →       1              |        4.62 ms →        4.62 ms   (+0.03%) | 
  │ ├ sirius::Periodic_function::add                                    |      812.27 μs →      756.77 μs   (-6.83%) |       2   →       2              |        1.62 ms →        1.51 ms   (-6.83%) | 
  │ ├ sirius::Potential::xc                                             |       51.72 ms →       51.22 ms   (-0.96%) |       1   →       1              |       51.72 ms →       51.22 ms   (-0.96%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.51 ms →       50.06 ms   (-0.87%) |       1   →       1              |       50.51 ms →       50.06 ms   (-0.87%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.56 ms   (+1.13%) |       2   →       2              |        5.06 ms →        5.11 ms   (+1.13%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.58 ms →        4.38 ms   (-4.43%) |       1   →       1              |        4.58 ms →        4.38 ms   (-4.43%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.59 ms →        4.16 ms  (+15.89%) |       1   →       1              |        3.59 ms →        4.16 ms  (+15.89%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.94 ms →      268.96 ms   (+0.01%) |       1   →       1              |      268.94 ms →      268.96 ms   (+0.01%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      160.00 ns →      292.00 ns  (+82.50%) |       1   →       1              |      160.00 ns →      292.00 ns  (+82.50%) | 
  ├ sirius::Hamiltonian0                                                |        8.48 ms →        8.43 ms   (-0.60%) |       1   →       1              |        8.48 ms →        8.43 ms   (-0.60%) | 
  │ ├ sirius::Local_operator                                            |        7.37 ms →        7.37 ms   (-0.00%) |       1   →       1              |        7.37 ms →        7.37 ms   (-0.00%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.75 ms   (+0.64%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.64%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.57 ms →        3.56 ms   (-0.13%) |       1   →       1              |        3.57 ms →        3.56 ms   (-0.13%) | 
  │ ├ sirius::Non_local_operator                                        |      417.23 μs →      395.38 μs   (-5.24%) |       2   →       2              |      834.46 μs →      790.76 μs   (-5.24%) | 
  │ ├ sirius::D_operator::initialize                                    |      125.67 μs →      113.69 μs   (-9.53%) |       1   →       1              |      125.67 μs →      113.69 μs   (-9.53%) | 
  │ └ sirius::Q_operator::initialize                                    |       92.02 μs →       92.65 μs   (+0.69%) |       1   →       1              |       92.02 μs →       92.65 μs   (+0.69%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.28 s    (-1.13%) |       1   →       1              |        1.29 s  →        1.28 s    (-1.13%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       75.56 ms →       66.19 ms  (-12.40%) |       1   →       1              |       75.56 ms →       66.19 ms  (-12.40%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      270.94 μs →      230.03 μs  (-15.10%) |       1   →       1              |      270.94 μs →      230.03 μs  (-15.10%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       75.28 ms →       65.95 ms  (-12.39%) |       1   →       1              |       75.28 ms →       65.95 ms  (-12.39%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.21 s    (-0.43%) |       1   →       1              |        1.22 s  →        1.21 s    (-0.43%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      102.52 ms →       88.01 ms  (-14.15%) |       4   →       4              |      410.08 ms →      352.04 ms  (-14.15%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.42 ms →       46.60 ms   (-3.76%) |       1   →       1              |       48.42 ms →       46.60 ms   (-3.76%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.61 ms →        8.00 ms   (+5.11%) |       1   →       1              |        7.61 ms →        8.00 ms   (+5.11%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      450.99 ms →      382.02 ms  (-15.29%) |       1   →       1              |      450.99 ms →      382.02 ms  (-15.29%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      384.27 ms →      288.54 ms  (-24.91%) |       1   →       1              |      384.27 ms →      288.54 ms  (-24.91%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        2.92 μs →        3.90 μs  (+33.76%) |       1   →       1              |        2.92 μs →        3.90 μs  (+33.76%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.27 μs →        3.01 μs  (+32.42%) |       1   →       1              |        2.27 μs →        3.01 μs  (+32.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      507.00 ns →      512.00 ns   (+0.99%) |       1   →       1              |      507.00 ns →      512.00 ns   (+0.99%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      791.00 ns →      798.00 ns   (+0.88%) |       1   →       1              |      791.00 ns →      798.00 ns   (+0.88%) | 
- │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.03 ms →       21.43 ms (+607.07%) |       1   →       1              |        3.03 ms →       21.43 ms (+607.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.23 ms →       21.28 ms   (+0.23%) |       1   →       1              |       21.23 ms →       21.28 ms   (+0.23%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.21 ms →       25.36 ms  (+19.58%) |       2   →       2              |       42.42 ms →       50.72 ms  (+19.58%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.87 ms →       16.97 ms  (+14.12%) |       2   →       2              |       29.74 ms →       33.94 ms  (+14.12%) | 
- │ │ │ └ sddk::wf_inner                                                |       14.64 ms →       16.76 ms  (+14.50%) |       2   →       2              |       29.27 ms →       33.52 ms  (+14.50%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       22.50 ns →       21.00 ns   (-6.67%) |       2   →       2              |       45.00 ns →       42.00 ns   (-6.67%) | 
- │ │ │   ├ sddk::wf_inner|pw                                           |       14.49 ms →       16.63 ms  (+14.76%) |       2   →       2              |       28.98 ms →       33.26 ms  (+14.76%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       31.00 ns →       27.50 ns  (-11.29%) |       2   →       2              |       62.00 ns →       55.00 ns  (-11.29%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      107.61 ms →      179.63 ms  (+66.93%) |       1   →       1              |      107.61 ms →      179.63 ms  (+66.93%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.60 ms   (-0.18%) |       1   →       1              |        2.61 ms →        2.60 ms   (-0.18%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        2.60 ms   (-0.20%) |       1   →       1              |        2.60 ms →        2.60 ms   (-0.20%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      505.00 ns →      727.00 ns  (+43.96%) |       1   →       1              |      505.00 ns →      727.00 ns  (+43.96%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       61.98 s  →       71.41 s   (+15.20%) |       1   →       1              |       61.98 s  →       71.41 s   (+15.20%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.45 ms   (+0.68%) |      19   →      19              |       46.29 ms →       46.60 ms   (+0.68%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        3.09 s    (-4.77%) |      19   →      23    (+21.05%) |       61.74 s  →       71.17 s   (+15.28%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.20 ms →        5.49 ms   (+5.72%) |      19   →      23    (+21.05%) |       98.73 ms →      126.35 ms  (+27.97%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.41 ms →        4.73 ms   (+7.34%) |      19   →      23    (+21.05%) |       83.80 ms →      108.88 ms  (+29.94%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      542.15 μs →      558.63 μs   (+3.04%) |      19   →      23    (+21.05%) |       10.30 ms →       12.85 ms  (+24.73%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.71 ms →        2.95 ms   (+8.68%) |      19   →      23    (+21.05%) |       51.54 ms →       67.80 ms  (+31.56%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      250.68 μs →      236.15 μs   (-5.80%) |      38   →      46    (+21.05%) |        9.53 ms →       10.86 ms  (+14.04%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      117.23 μs →      115.43 μs   (-1.54%) |      19   →      23    (+21.05%) |        2.23 ms →        2.65 ms  (+19.19%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       90.80 μs →       93.94 μs   (+3.46%) |      19   →      23    (+21.05%) |        1.73 ms →        2.16 ms  (+25.24%) | 
- │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.87 s    (-7.61%) |      19   →      23    (+21.05%) |       38.50 s  →       43.06 s   (+11.84%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      212.20 μs →      209.51 μs   (-1.27%) |      19   →      23    (+21.05%) |        4.03 ms →        4.82 ms  (+19.51%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      205.02 μs →      199.12 μs   (-2.88%) |      19   →      23    (+21.05%) |        3.90 ms →        4.58 ms  (+17.57%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.15 μs →        7.63 μs  (+48.16%) |      19   →      23    (+21.05%) |       97.83 μs →      175.46 μs  (+79.35%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.75 s   (-10.71%) |      19   →      23    (+21.05%) |       37.33 s  →       40.35 s    (+8.09%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.08 ms →       70.01 ms   (-9.17%) |      19   →      23    (+21.05%) |        1.46 s  →        1.61 s    (+9.95%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.11 ms →        6.71 ms  (-17.23%) |     114   →     138    (+21.05%) |      924.81 ms →      926.60 ms   (+0.19%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.79 ms →       15.75 ms  (-16.15%) |      19   →      23    (+21.05%) |      356.94 ms →      362.32 ms   (+1.51%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      480.23 μs →      484.55 μs   (+0.90%) |      19   →      23    (+21.05%) |        9.12 ms →       11.14 ms  (+22.14%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.69 ms →        7.24 ms  (-16.69%) |      38   →      46    (+21.05%) |      330.05 ms →      332.86 ms   (+0.85%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.66 s   (-10.98%) |      19   →      23    (+21.05%) |       35.34 s  →       38.08 s    (+7.76%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       54.60 ms →       67.12 ms  (+22.93%) |     356   →     298    (-16.29%) |       19.44 s  →       20.00 s    (+2.91%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       30.39 ms →       42.76 ms  (+40.68%) |     356   →     298    (-16.29%) |       10.82 s  →       12.74 s   (+17.76%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.87 μs →        2.12 μs  (+13.58%) |     356   →     298    (-16.29%) |      665.73 μs →      632.92 μs   (-4.93%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.80 μs  (+13.24%) |     356   →     298    (-16.29%) |      565.30 μs →      535.84 μs   (-5.21%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      396.86 ns →      426.68 ns   (+7.51%) |     356   →     298    (-16.29%) |      141.28 μs →      127.15 μs  (-10.00%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      530.01 ns →      545.58 ns   (+2.94%) |     356   →     298    (-16.29%) |      188.68 μs →      162.58 μs  (-13.83%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.12 ms →        3.23 ms   (+3.49%) |     356   →     298    (-16.29%) |        1.11 s  →      963.66 ms  (-13.37%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.25 ms →        3.76 ms  (+15.77%) |     356   →     298    (-16.29%) |        1.16 s  →        1.12 s    (-3.09%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.91 ms →        8.68 ms   (-2.61%) |     712   →     596    (-16.29%) |        6.34 s  →        5.17 s   (-18.48%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.02 ms →        6.83 ms  (+13.30%) |     356   →     298    (-16.29%) |        2.14 s  →        2.03 s    (-5.16%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.07 ms →        1.25 ms  (+16.77%) |     693   →     573    (-17.32%) |      742.18 ms →      716.57 ms   (-3.45%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.54 ns →       40.23 ns  (-21.94%) |     693   →     573    (-17.32%) |       35.72 μs →       23.05 μs  (-35.45%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      909.14 μs →        1.09 ms  (+19.64%) |     693   →     573    (-17.32%) |      630.03 ms →      623.27 ms   (-1.07%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       46.99 ns →       37.19 ns  (-20.85%) |     693   →     573    (-17.32%) |       32.56 μs →       21.31 μs  (-34.56%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      119.58 μs →      173.65 μs  (+45.21%) |     356   →     298    (-16.29%) |       42.57 ms →       51.75 ms  (+21.56%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.71 ms →        2.02 ms  (+18.38%) |     356   →     298    (-16.29%) |      608.30 ms →      602.79 ms   (-0.91%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |        2.23 ms →        2.41 ms   (+8.09%) |     337   →     275    (-18.40%) |      750.05 ms →      661.55 ms  (-11.80%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |      741.10 μs →      801.06 μs   (+8.09%) |    1.01 K →     825    (-18.40%) |      749.25 ms →      660.87 ms  (-11.80%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.33 ms →        1.50 ms  (+13.19%) |     356   →     298    (-16.29%) |      472.50 ms →      447.69 ms   (-5.25%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.26 ms →        1.40 ms  (+11.42%) |     356   →     298    (-16.29%) |      447.26 ms →      417.16 ms   (-6.73%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.30 ns →       33.18 ns  (-17.67%) |     356   →     298    (-16.29%) |       14.35 μs →        9.89 μs  (-31.09%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.10 ms →        1.23 ms  (+12.32%) |     356   →     298    (-16.29%) |      389.84 ms →      366.52 ms   (-5.98%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.75 ns →       64.17 ns  (+65.59%) |     356   →     298    (-16.29%) |       13.80 μs →       19.12 μs  (+38.61%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.49 ms →       47.68 ms  (+42.37%) |     356   →     298    (-16.29%) |       11.92 s  →       14.21 s   (+19.17%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.85 ms →        3.21 ms  (+12.38%) |     340   →     289    (-15.00%) |      969.70 ms →      926.27 ms   (-4.48%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.47 ms →        1.83 ms  (+24.20%) |     337   →     278    (-17.51%) |      496.98 ms →      509.20 ms   (+2.46%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      735.97 μs →      914.35 μs  (+24.24%) |     674   →     556    (-17.51%) |      496.04 ms →      508.38 ms   (+2.49%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.29 ms →        1.35 ms   (+4.88%) |     337   →     278    (-17.51%) |      434.20 ms →      375.68 ms  (-13.48%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.13 ms →        7.99 ms  (+12.12%) |      54   →      57     (+5.56%) |      384.82 ms →      455.44 ms  (+18.35%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.27 ms →        4.96 ms  (+15.96%) |      89   →      91     (+2.25%) |      380.44 ms →      451.06 ms  (+18.56%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        3.07 ms →        3.61 ms  (+17.62%) |     124   →     125     (+0.81%) |      380.26 ms →      450.88 ms  (+18.57%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      410.84 ns →      396.09 ns   (-3.59%) |      19   →      23    (+21.05%) |        7.81 μs →        9.11 μs  (+16.71%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.15 μs →       20.31 μs   (+6.10%) |      19   →      23    (+21.05%) |      363.76 μs →      467.19 μs  (+28.43%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.48 ms   (-2.50%) |      19   →      23    (+21.05%) |       28.85 ms →       34.05 ms  (+18.02%) | 
- │ │ ├ sirius::Density::generate                                       |      570.23 ms →      564.65 ms   (-0.98%) |      19   →      23    (+21.05%) |       10.83 s  →       12.99 s   (+19.87%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      436.49 ms →      386.48 ms  (-11.46%) |      19   →      23    (+21.05%) |        8.29 s  →        8.89 s    (+7.18%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.57 μs →        8.04 μs   (+6.10%) |      19   →      23    (+21.05%) |      143.90 μs →      184.82 μs  (+28.44%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.13 μs →        7.42 μs   (+4.09%) |      19   →      23    (+21.05%) |      135.48 μs →      170.71 μs  (+26.00%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       36.88 ms →       43.48 ms  (+17.91%) |      19   →      23    (+21.05%) |      700.72 ms →        1.00 s   (+42.73%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        6.20 μs →        7.68 μs  (+23.73%) |      19   →      23    (+21.05%) |      117.87 μs →      176.54 μs  (+49.77%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.96 ms →       23.62 ms (+296.02%) |      19   →      23    (+21.05%) |      113.32 ms →      543.27 ms (+379.40%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       29.87 ms →       18.84 ms  (-36.95%) |      19   →      23    (+21.05%) |      567.62 ms →      433.23 ms  (-23.68%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      493.89 ns →      683.09 ns  (+38.31%) |      19   →      23    (+21.05%) |        9.38 μs →       15.71 μs  (+67.42%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      108.93 ms →       96.10 ms  (-11.77%) |      19   →      23    (+21.05%) |        2.07 s  →        2.21 s    (+6.80%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.47 ms →        2.07 ms  (-16.02%) |      19   →      23    (+21.05%) |       46.84 ms →       47.62 ms   (+1.66%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      257.30 ms →      200.25 ms  (-22.17%) |      19   →      23    (+21.05%) |        4.89 s  →        4.61 s    (-5.79%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      257.10 ms →      200.03 ms  (-22.20%) |      19   →      23    (+21.05%) |        4.88 s  →        4.60 s    (-5.82%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      105.31 ms →      149.39 ms  (+41.86%) |      19   →      23    (+21.05%) |        2.00 s  →        3.44 s   (+71.72%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      105.31 ms →      149.39 ms  (+41.86%) |      19   →      23    (+21.05%) |        2.00 s  →        3.44 s   (+71.72%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       21.91 ms →       65.59 ms (+199.41%) |      19   →      23    (+21.05%) |      416.25 ms →        1.51 s  (+262.44%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.08 ms →       70.49 ms   (+0.59%) |      19   →      23    (+21.05%) |        1.33 s  →        1.62 s   (+21.76%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.66 ms →       12.65 ms   (-0.02%) |      19   →      23    (+21.05%) |      240.47 ms →      291.05 ms  (+21.03%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.62 ms →       23.68 ms   (+0.24%) |      19   →      23    (+21.05%) |      448.79 ms →      544.59 ms  (+21.35%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.81 ms →        5.10 ms   (+6.04%) |      19   →      23    (+21.05%) |       91.36 ms →      117.28 ms  (+28.37%) | 
- │ │ ├ sirius::Density::mix                                            |      132.99 ms →      137.69 ms   (+3.53%) |      19   →      23    (+21.05%) |        2.53 s  →        3.17 s   (+25.33%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      796.09 μs →      763.13 μs   (-4.14%) |      19   →      23    (+21.05%) |       15.13 ms →       17.55 ms  (+16.04%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.87 ms →        4.85 ms   (-0.44%) |     229   →     289    (+26.20%) |        1.12 s  →        1.40 s   (+25.65%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.81 ms   (+0.15%) |     229   →     289    (+26.20%) |        1.10 s  →        1.39 s   (+26.39%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.80 ms →        4.81 ms   (+0.14%) |     229   →     289    (+26.20%) |        1.10 s  →        1.39 s   (+26.38%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        4.78 ms →        5.73 ms  (+20.03%) |      19   →      23    (+21.05%) |       90.78 ms →      131.90 ms  (+45.30%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.11 ms →        4.91 ms  (+19.45%) |      19   →      23    (+21.05%) |       78.02 ms →      112.82 ms  (+44.60%) | 
- │ │ ├ sirius::Potential::generate                                     |      360.42 ms →      360.13 ms   (-0.08%) |      19   →      23    (+21.05%) |        6.85 s  →        8.28 s   (+20.95%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       40.14 ms →       39.47 ms   (-1.67%) |      19   →      23    (+21.05%) |      762.57 ms →      907.70 ms  (+19.03%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.11 ms →        8.51 ms   (-6.65%) |      19   →      23    (+21.05%) |      173.16 ms →      195.67 ms  (+13.00%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.97 ms →        4.98 ms   (+0.21%) |      19   →      23    (+21.05%) |       94.43 ms →      114.55 ms  (+21.31%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.62 ms →        4.63 ms   (+0.20%) |      19   →      23    (+21.05%) |       87.84 ms →      106.54 ms  (+21.29%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms →        4.63 ms   (+0.19%) |      19   →      23    (+21.05%) |       87.82 ms →      106.52 ms  (+21.29%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      785.01 μs →      788.21 μs   (+0.41%) |      38   →      46    (+21.05%) |       29.83 ms →       36.26 ms  (+21.55%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       45.15 ms →       45.40 ms   (+0.55%) |      19   →      23    (+21.05%) |      857.93 ms →        1.04 s   (+21.72%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.97 ms →       44.22 ms   (+0.57%) |      19   →      23    (+21.05%) |      835.45 ms →        1.02 s   (+21.74%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      670.94 μs →      675.40 μs   (+0.67%) |      38   →      46    (+21.05%) |       25.50 ms →       31.07 ms  (+21.86%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.58 ms →        4.65 ms   (+1.60%) |      19   →      23    (+21.05%) |       86.95 ms →      106.94 ms  (+22.99%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.67 ms →        3.61 ms   (-1.71%) |      19   →      23    (+21.05%) |       69.82 ms →       83.07 ms  (+18.98%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.45 ms →      268.62 ms   (+0.06%) |      19   →      23    (+21.05%) |        5.10 s  →        6.18 s   (+21.13%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      271.58 ns →      314.52 ns  (+15.81%) |      19   →      23    (+21.05%) |        5.16 μs →        7.23 μs  (+40.19%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.35 ms →       96.42 ms   (+0.08%) |      19   →      23    (+21.05%) |        1.83 s  →        2.22 s   (+21.14%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.35 ms →       96.42 ms   (+0.08%) |      19   →      23    (+21.05%) |        1.83 s  →        2.22 s   (+21.14%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.30 ms →       13.24 ms   (-0.49%) |      19   →      23    (+21.05%) |      252.78 ms →      304.51 ms  (+20.46%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.81 ms →       69.96 ms   (+0.21%) |      19   →      23    (+21.05%) |        1.33 s  →        1.61 s   (+21.31%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.60 ms   (+0.03%) |      19   →      23    (+21.05%) |      239.25 ms →      289.69 ms  (+21.08%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.62 ms →        4.56 ms   (-1.24%) |      19   →      23    (+21.05%) |       87.78 ms →      104.94 ms  (+19.55%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.56 ms →        4.58 ms   (+0.34%) |     133   →     161    (+21.05%) |      606.97 ms →      737.26 ms  (+21.47%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.57 ms   (+0.24%) |     133   →     161    (+21.05%) |      605.89 ms →      735.20 ms  (+21.34%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.55 ms →        4.57 ms   (+0.24%) |     133   →     161    (+21.05%) |      605.81 ms →      735.11 ms  (+21.34%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.94 ms →        4.94 ms   (+0.08%) |      57   →      69    (+21.05%) |      281.51 ms →      341.06 ms  (+21.15%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.93 ms   (+0.08%) |      57   →      69    (+21.05%) |      280.97 ms →      340.38 ms  (+21.15%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.52 ms →        4.54 ms   (+0.46%) |      19   →      23    (+21.05%) |       85.85 ms →      104.40 ms  (+21.61%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       74.51 μs →       76.18 μs   (+2.24%) |      19   →      23    (+21.05%) |        1.42 ms →        1.75 ms  (+23.76%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.73 μs →       71.12 μs   (+0.55%) |      19   →      23    (+21.05%) |        1.34 ms →        1.64 ms  (+21.72%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.30 ms →        5.22 ms   (-1.56%) |       2   →       2              |       10.60 ms →       10.44 ms   (-1.56%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.81 ms →        4.59 ms   (-4.63%) |       6   →       6              |       28.88 ms →       27.54 ms   (-4.63%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.81 ms →        4.56 ms   (-5.20%) |       6   →       6              |       28.86 ms →       27.36 ms   (-5.20%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.81 ms →        4.56 ms   (-5.17%) |       6   →       6              |       28.85 ms →       27.36 ms   (-5.17%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.17 ms →        4.95 ms   (-4.32%) |       3   →       3              |       15.51 ms →       14.84 ms   (-4.32%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.17 ms →        4.94 ms   (-4.39%) |       3   →       3              |       15.50 ms →       14.82 ms   (-4.39%) | 
  ├ sirius::Periodic_function|inner                                     |        4.78 ms →        4.78 ms   (-0.10%) |       2   →       2              |        9.57 ms →        9.56 ms   (-0.10%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.78 ms →        4.77 ms   (-0.14%) |       2   →       2              |        9.56 ms →        9.55 ms   (-0.14%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.78 ms →        4.77 ms   (-0.15%) |       2   →       2              |        9.56 ms →        9.54 ms   (-0.15%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.92 ms →        5.31 ms   (+8.11%) |       1   →       1              |        4.92 ms →        5.31 ms   (+8.11%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.91 ms →        5.31 ms   (+8.19%) |       1   →       1              |        4.91 ms →        5.31 ms   (+8.19%) | 
- └ sirius::finalize                                                    |      153.43 ms →      505.70 ms (+229.60%) |       1   →       1              |      153.43 ms →      505.70 ms (+229.60%) | 
  ====================================================================================================================================================================================================
```
