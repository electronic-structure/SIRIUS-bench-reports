# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 495e097f8fb7cb2be32f3783e9a2314d02bcfd52
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   31.52 s  →  31.09 s      (-1.39%)           1   →      1               
  ├ sirius::initialize                                                      2.96 s  →   3.00 s      (+1.46%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                 19.43 s  →  19.04 s      (-2.04%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               257.00 μs → 255.28 μs     (-0.67%)           1   →      1               
! │ ├ sirius::Unit_cell::initialize                                       797.06 ms → 265.38 ms    (-66.70%)           1   →      1               
! │ │ ├ sirius::Atom_type::init                                           259.92 ms →  83.12 ms    (-68.02%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          17.25 ms →  15.96 ms     (-7.45%)           1   →      1               
! │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      289.19 μs → 247.94 μs    (-14.26%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  16.86 ms →  15.64 ms     (-7.25%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     16.83 ms →  15.61 ms     (-7.25%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.98 ms →   4.86 ms     (-2.42%)           1   →      1               
! │ │       ├ sirius::Unit_cell_symmetry|equiv                             60.72 μs →  48.69 μs    (-19.81%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               17.73 μs →  18.27 μs     (+2.99%)           1   →      1               
  │ └ sirius::Simulation_context::update                                   18.60 s  →  18.73 s      (+0.69%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.18 ms →   5.11 ms     (-1.32%)           1   →      1               
! │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       82.95 μs →  72.44 μs    (-12.67%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.03 ms →   4.97 ms     (-1.06%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.01 ms →   4.95 ms     (-1.10%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.90 ms →   4.83 ms     (-1.48%)           1   →      1               
! │   │     ├ sirius::Unit_cell_symmetry|equiv                             48.40 μs →  64.52 μs    (+33.28%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               15.48 μs →  16.68 μs     (+7.72%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                        4.65 s  →   4.69 s      (+0.73%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                          239.17 ms → 242.04 ms     (+1.20%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                               211.20 ms → 214.23 ms     (+1.43%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                     690.31 ms → 710.07 ms     (+2.86%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                       1.59 s  →   1.59 s      (+0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                               661.32 ms → 662.69 ms     (+0.21%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   10.90 ms →  11.08 ms     (+1.62%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      6.72 ms →   6.88 ms     (+2.41%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  11.45 ms →  11.52 ms     (+0.66%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.08 ms →   1.06 ms     (-2.13%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 148.54 ms → 149.26 ms     (+0.49%)           3   →      3               
! ├ sirius::K_point_set::create_k_mesh                                     15.95 ms →  13.39 ms    (-16.02%)           1   →      1               
! │ ├ sirius::K_point::K_point                                            794.75 ns → 875.25 ns    (+10.13%)           4   →      4               
! │ └ sirius::K_point_set::initialize                                      15.88 ms →  13.31 ms    (-16.17%)           1   →      1               
! │   └ sirius::K_point::initialize                                         3.70 ms →   3.06 ms    (-17.19%)           4   →      4               
  │     ├ sirius::K_point::generate_gkvec                                   1.31 ms →   1.22 ms     (-7.13%)           4   →      4               
  │     │ └ sddk::Gvec::init                                              363.66 μs → 355.80 μs     (-2.16%)           4   →      4               
  │     ├ sddk::matrix_storage::matrix_storage                              7.51 μs →   7.68 μs     (+2.26%)           4   →      4               
! │     └ sirius::K_point::update                                           2.21 ms →   1.66 ms    (-24.61%)           4   →      4               
! │       └ sirius::Beta_projectors                                         1.89 ms →   1.37 ms    (-27.51%)           4   →      4               
! │         └ sirius::Beta_projectors::generate_pw_coefs_t                  1.56 ms →   1.03 ms    (-33.94%)           4   →      4               
  ├ sirius::Smooth_periodic_function                                      499.70 μs → 489.90 μs     (-1.96%)           2   →      2               
  ├ sirius::Potential                                                       8.37 ms →   8.51 ms     (+1.65%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    563.96 μs → 554.13 μs     (-1.74%)           6   →      6               
  │ └ sirius::Potential::update                                             4.73 ms →   4.94 ms     (+4.44%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         4.69 ms →   4.90 ms     (+4.51%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                4.07 ms →   4.32 ms     (+6.14%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 452.91 μs → 422.97 μs     (-6.61%)           1   →      1               
  ├ sirius::Density                                                         5.67 ms →   5.90 ms     (+4.17%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    340.20 μs → 339.46 μs     (-0.22%)           2   →      2               
  │ └ sirius::Density::update                                               4.98 ms →   5.21 ms     (+4.65%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                4.94 ms →   5.17 ms     (+4.73%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                67.23 μs →  66.93 μs     (-0.44%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                4.50 ms →   4.74 ms     (+5.19%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 322.12 μs → 320.00 μs     (-0.66%)           1   →      1               
! ├ sirius::Density::initial_density                                       14.01 ms →  11.97 ms    (-14.57%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    5.70 ms →   5.97 ms     (+4.83%)           1   →      1               
! │ ├ sirius::Smooth_periodic_function::fft_transform                       1.77 ms → 517.80 μs    (-70.75%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  1.22 ms →   1.26 ms     (+3.41%)           1   →      1               
! ├ sirius::Potential::generate                                            44.22 ms →  55.86 ms    (+26.33%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            6.40 ms →   6.46 ms     (+0.91%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     1.67 ms →   1.57 ms     (-6.16%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     1.51 ms →   1.58 ms     (+4.97%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             1.51 ms →   1.58 ms     (+4.92%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    1.51 ms →   1.58 ms     (+4.92%)           1   →      1               
! │ ├ sirius::Periodic_function::add                                      147.17 μs → 124.31 μs    (-15.53%)           2   →      2               
  │ ├ sirius::Potential::xc                                                13.88 ms →  14.45 ms     (+4.10%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               13.67 ms →  14.24 ms     (+4.16%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                490.87 μs → 483.34 μs     (-1.53%)           2   →      2               
! │ │   └ sirius::Smooth_periodic_function::fft_transform                   2.36 ms →   1.64 ms    (-30.38%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       2.18 ms →   2.13 ms     (-2.34%)           1   →      1               
! │ ├ sirius::Potential::generate_D_operator_matrix                        21.23 ms →  32.35 ms    (+52.35%)           1   →      1               
! │ └ sirius::Potential::generate_PAW_effective_potential                 154.00 ns → 209.00 ns    (+35.71%)           1   →      1               
! ├ sirius::Hamiltonian0                                                  507.74 μs →   3.46 ms   (+582.06%)           1   →      1               
! │ ├ sirius::Local_operator                                              340.34 μs →   3.28 ms   (+863.56%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function                                   24.71 μs →  29.44 μs    (+19.11%)           1   →      1               
! │ │ └ sirius::Smooth_periodic_function::fft_transform                   209.81 μs →   3.15 ms  (+1399.26%)           1   →      1               
! │ ├ sirius::Non_local_operator                                           27.68 μs →  33.66 μs    (+21.63%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       50.50 μs →  54.28 μs     (+7.50%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       45.26 μs →  45.19 μs     (-0.15%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      67.02 ms →  66.98 ms     (-0.06%)           1   →      1               
! │ ├ sirius::Hamiltonian_k                                                60.85 μs →  48.14 μs    (-20.89%)           4   →      4               
! │ │ ├ sirius::Local_operator::prepare_k                                  56.87 μs →  44.52 μs    (-21.72%)           4   →      4               
  │ │ └ sirius::Beta_projectors_base::prepare                               2.45 μs →   2.42 μs     (-1.53%)           4   →      4               
  │ ├ sirius::Band::initialize_subspace|kp                                 16.69 ms →  16.69 ms     (+0.02%)           4   →      4               
! │ │ ├ sddk::matrix_storage::matrix_storage                              485.47 μs → 669.62 μs    (+37.93%)          16   →     16               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                     1.28 ms →   1.30 ms     (+1.04%)           4   →      4               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                           194.98 μs → 195.83 μs     (+0.44%)           4   →      4               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    7.11 ms →   6.42 ms     (-9.79%)           4   →      4               
! │ │ │ ├ sirius::Local_operator::apply_h                                   6.59 ms →   5.86 ms    (-11.12%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.28 μs →   2.32 μs     (+1.68%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.66 μs →   1.60 μs     (-3.66%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           361.75 ns → 373.00 ns     (+3.11%)           4   →      4               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          492.50 ns → 491.75 ns     (-0.15%)           4   →      4               
! │ │ │ ├ sirius::Beta_projectors_base::generate                           51.67 μs →  77.31 μs    (+49.62%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             161.85 μs → 147.76 μs     (-8.71%)           4   →      4               
  │ │ │ └ sirius::Non_local_operator::apply                               143.28 μs → 156.74 μs     (+9.39%)           8   →      8               
  │ │ ├ sirius::Band::set_subspace_mtrx                                   122.48 μs → 123.99 μs     (+1.23%)           8   →      8               
  │ │ │ └ sddk::inner                                                     116.90 μs → 118.49 μs     (+1.36%)           8   →      8               
! │ │ │   └ sddk::inner|local                                              23.16 μs →  17.62 μs    (-23.94%)           8   →      8               
  │ │ ├ Eigensolver_cuda|zhegvdx                                            4.95 ms →   4.92 ms     (-0.63%)           4   →      4               
! │ │ └ sddk::transform                                                    81.72 μs →  73.18 μs    (-10.45%)           4   →      4               
! │ │   ├ sddk::transform|init                                             10.76 μs →   9.30 μs    (-13.54%)           4   →      4               
  │ │   └ sddk::transform|local                                            13.31 μs →  12.26 μs     (-7.89%)           4   →      4               
  │ └ sirius::Beta_projectors_base::dismiss                               461.25 ns → 433.50 ns     (-6.02%)           4   →      4               
  ├ sirius::DFT_ground_state::scf_loop                                      7.40 s  →   7.38 s      (-0.29%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    505.83 μs → 499.62 μs     (-1.23%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        368.63 ms → 367.61 ms     (-0.28%)          20   →     20               
! │ │ ├ sirius::Hamiltonian0                                                1.27 ms →   1.66 ms    (+31.14%)          20   →     20               
! │ │ │ ├ sirius::Local_operator                                          581.41 μs → 894.26 μs    (+53.81%)          20   →     20               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               27.93 μs →  28.72 μs     (+2.81%)          20   →     20               
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               445.97 μs → 756.09 μs    (+69.54%)          20   →     20               
! │ │ │ ├ sirius::Non_local_operator                                      276.41 μs → 329.74 μs    (+19.30%)          40   →     40               
! │ │ │ ├ sirius::D_operator::initialize                                   80.44 μs →  55.06 μs    (-31.55%)          20   →     20               
  │ │ │ └ sirius::Q_operator::initialize                                   42.68 μs →  41.66 μs     (-2.40%)          20   →     20               
  │ │ ├ sirius::Band::solve                                               170.05 ms → 172.13 ms     (+1.23%)          20   →     20               
! │ │ │ ├ sirius::Hamiltonian_k                                            42.92 μs →  47.77 μs    (+11.29%)          80   →     80               
! │ │ │ │ ├ sirius::Local_operator::prepare_k                              39.41 μs →  43.51 μs    (+10.41%)          80   →     80               
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                           2.47 μs →   3.08 μs    (+24.54%)          80   →     80               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     42.45 ms →  42.96 ms     (+1.22%)          80   →     80               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc            184.06 μs → 195.86 μs     (+6.41%)          80   →     80               
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                         11.90 μs →  13.67 μs    (+14.86%)         480   →    480               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             2.03 ms →   1.99 ms     (-1.79%)          80   →     80               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        28.32 μs →  27.92 μs     (-1.40%)          80   →     80               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       607.92 μs → 588.69 μs     (-3.16%)         240   →    240               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              40.05 ms →  40.59 ms     (+1.36%)          80   →     80               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.09 ms →   4.98 ms     (-2.27%)         323   →    323               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.61 ms →   4.43 ms     (-4.01%)         323   →    323               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.89 μs →   2.01 μs     (+6.19%)         323   →    323               
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.51 μs →   1.66 μs    (+10.35%)         323   →    323               
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     407.18 ns → 496.19 ns    (+21.86%)         323   →    323               
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    394.89 ns → 490.86 ns    (+24.30%)         323   →    323               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                     54.55 μs →  51.57 μs     (-5.46%)         323   →    323               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       137.51 μs → 143.90 μs     (+4.65%)         323   →    323               
! │ │ │ │   │ └ sirius::Non_local_operator::apply                         136.92 μs → 169.15 μs    (+23.54%)         646   →    646               
! │ │ │ │   ├ sddk::orthogonalize                                         483.22 μs → 534.85 μs    (+10.69%)         323   →    323               
! │ │ │ │   │ ├ sddk::inner                                               118.93 μs → 135.37 μs    (+13.82%)         566   →    566               
! │ │ │ │   │ │ └ sddk::inner|local                                        15.32 μs →  17.18 μs    (+12.15%)         566   →    566               
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  79.37 μs → 135.35 μs    (+70.53%)         323   →    323               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                              50.83 μs →  48.67 μs     (-4.24%)         323   →    323               
! │ │ │ │   │ └ sddk::transform                                           186.07 μs → 144.73 μs    (-22.22%)         243   →    243               
! │ │ │ │   │   ├ sddk::transform|init                                     15.71 μs →  18.00 μs    (+14.56%)         243   →    243               
! │ │ │ │   │   └ sddk::transform|local                                     6.93 μs →   7.99 μs    (+15.32%)         729   →    729               
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             127.06 μs → 171.57 μs    (+35.03%)         323   →    323               
! │ │ │ │   │ └ sddk::inner                                               106.93 μs → 136.33 μs    (+27.50%)         323   →    323               
! │ │ │ │   │   └ sddk::inner|local                                        16.24 μs →  17.90 μs    (+10.22%)         323   →    323               
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                      3.55 ms →   3.62 ms     (+2.08%)         323   →    323               
! │ │ │ │   ├ sirius::residuals                                           506.24 μs → 598.93 μs    (+18.31%)         322   →    322               
! │ │ │ │   │ ├ sddk::transform                                           188.73 μs → 238.54 μs    (+26.39%)         251   →    251               
! │ │ │ │   │ │ ├ sddk::transform|init                                     11.53 μs →  13.24 μs    (+14.88%)         251   →    251               
! │ │ │ │   │ │ └ sddk::transform|local                                     9.06 μs →  10.35 μs    (+14.26%)         502   →    502               
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               391.27 μs → 459.18 μs    (+17.35%)         251   →    251               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     326.58 μs → 296.48 μs     (-9.22%)         146   →    146               
! │ │ │ │     └ sddk::transform                                           213.56 μs → 191.34 μs    (-10.41%)         212   →    212               
! │ │ │ │       ├ sddk::transform|init                                      9.29 μs →  10.32 μs    (+11.09%)         212   →    212               
! │ │ │ │       └ sddk::transform|local                                     9.26 μs →  10.20 μs    (+10.12%)         278   →    278               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           518.33 ns → 533.24 ns     (+2.88%)          80   →     80               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          15.19 μs →  13.96 μs     (-8.08%)          20   →     20               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        371.15 μs → 370.55 μs     (-0.16%)          20   →     20               
  │ │ ├ sirius::Density::generate                                          78.14 ms →  77.07 ms     (-1.37%)          20   →     20               
  │ │ │ ├ sirius::Density::generate_valence                                31.06 ms →  30.35 ms     (-2.31%)          20   →     20               
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.28 μs →   2.02 μs    (-11.67%)          80   →     80               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.97 μs →   1.80 μs     (-8.47%)          80   →     80               
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  326.04 μs → 547.73 μs    (+67.99%)          80   →     80               
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         2.14 μs →   3.18 μs    (+48.72%)          80   →     80               
! │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                      110.76 μs → 211.95 μs    (+91.35%)          80   →     80               
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         135.69 μs → 252.39 μs    (+86.00%)          80   →     80               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       502.37 ns → 533.30 ns     (+6.16%)          80   →     80               
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    1.85 ms →   2.16 ms    (+16.57%)          80   →     80               
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               297.93 μs → 337.65 μs    (+13.33%)          20   →     20               
! │ │ │ │ └ sirius::Density::augment                                       21.32 ms →  18.43 ms    (-13.53%)          20   →     20               
! │ │ │ │   └ sirius::Density::generate_rho_aug                            21.17 ms →  18.29 ms    (-13.62%)          20   →     20               
  │ │ │ ├ sirius::Field4D::symmetrize                                      18.34 ms →  17.93 ms     (-2.27%)          20   →     20               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                18.34 ms →  17.93 ms     (-2.27%)          20   →     20               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              3.13 ms →   3.04 ms     (-3.04%)          20   →     20               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        12.05 ms →  11.79 ms     (-2.14%)          20   →     20               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                             3.09 ms →   3.02 ms     (-2.00%)          20   →     20               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       28.20 ms →  27.68 ms     (-1.84%)          20   →     20               
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 528.92 μs →   1.11 ms   (+110.36%)          20   →     20               
  │ │ ├ sirius::Density::mix                                               42.09 ms →  41.07 ms     (-2.41%)          20   →     20               
  │ │ │ ├ sirius::Density::mixer_input                                    280.44 μs → 254.56 μs     (-9.23%)          20   →     20               
  │ │ │ ├ sirius::Periodic_function|inner                                   1.58 ms →   1.59 ms     (+0.61%)         244   →    244               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           1.58 ms →   1.59 ms     (+0.61%)         244   →    244               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  1.58 ms →   1.59 ms     (+0.61%)         244   →    244               
! │ │ │ └ sirius::Density::mixer_output                                   785.44 μs → 679.99 μs    (-13.43%)          20   →     20               
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform               504.02 μs → 427.93 μs    (-15.10%)          20   →     20               
  │ │ ├ sirius::Potential::generate                                        40.22 ms →  37.33 ms     (-7.18%)          20   →     20               
  │ │ │ ├ sirius::Potential::poisson                                        5.46 ms →   5.60 ms     (+2.55%)          20   →     20               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               550.42 μs → 582.11 μs     (+5.76%)          20   →     20               
  │ │ │ │ └ sirius::Periodic_function|inner                                 1.56 ms →   1.61 ms     (+2.84%)          20   →     20               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         1.56 ms →   1.61 ms     (+2.83%)          20   →     20               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                1.56 ms →   1.61 ms     (+2.83%)          20   →     20               
  │ │ │ ├ sirius::Periodic_function::add                                  142.07 μs → 133.53 μs     (-6.01%)          40   →     40               
  │ │ │ ├ sirius::Potential::xc                                            11.89 ms →  12.05 ms     (+1.40%)          20   →     20               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           11.68 ms →  11.85 ms     (+1.44%)          20   →     20               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            119.89 μs → 118.03 μs     (-1.55%)          40   →     40               
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             768.24 μs → 554.12 μs    (-27.87%)          20   →     20               
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 658.04 μs → 375.20 μs    (-42.98%)          20   →     20               
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    21.68 ms →  18.79 ms    (-13.33%)          20   →     20               
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential             416.45 ns → 485.25 ns    (+16.52%)          20   →     20               
  │ │ ├ sirius::Field4D::symmetrize                                        18.59 ms →  17.32 ms     (-6.84%)          20   →     20               
  │ │ │ └ sirius::symmetrize_function|fpw                                  18.59 ms →  17.32 ms     (-6.84%)          20   →     20               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                                3.18 ms →   3.01 ms     (-5.30%)          20   →     20               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          12.20 ms →  11.22 ms     (-8.05%)          20   →     20               
  │ │ │   └ sddk::Gvec_shells::remap_backward                               3.13 ms →   3.01 ms     (-3.94%)          20   →     20               
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                   575.58 μs →   3.15 ms   (+447.80%)          20   →     20               
  │ │ ├ sirius::Periodic_function|inner                                     1.59 ms →   1.64 ms     (+2.92%)         140   →    140               
  │ │ │ └ sirius::Periodic_function|inner_local                             1.59 ms →   1.64 ms     (+2.91%)         140   →    140               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    1.59 ms →   1.64 ms     (+2.92%)         140   →    140               
  │ │ ├ sirius::Smooth_periodic_function|inner                              1.18 ms →   1.15 ms     (-2.91%)          60   →     60               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      1.18 ms →   1.15 ms     (-2.90%)          60   →     60               
  │ │ ├ sirius::Periodic_function::integrate                                1.25 ms →   1.27 ms     (+1.60%)          20   →     20               
! │ │ └ sirius::Density::get_magnetisation                                 94.50 μs → 108.38 μs    (+14.69%)          20   →     20               
! │ │   └ sirius::Density::compute_atomic_mag_mom                          92.69 μs → 106.21 μs    (+14.58%)          20   →     20               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                        97.67 μs → 104.55 μs     (+7.04%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       1.54 ms →   1.62 ms     (+5.13%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               1.54 ms →   1.62 ms     (+5.14%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      1.54 ms →   1.62 ms     (+5.15%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                1.13 ms →   1.13 ms     (+0.09%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.13 ms →   1.13 ms     (+0.10%)           3   →      3               
  ├ sirius::Stress|kin                                                      5.04 ms →   5.51 ms     (+9.21%)           1   →      1               
  ├ sirius::Stress|har                                                      3.36 ms →   3.36 ms     (-0.23%)           1   →      1               
  ├ sirius::Stress|ewald                                                   10.76 ms →  11.04 ms     (+2.57%)           1   →      1               
  ├ sirius::Stress|vloc                                                    12.63 ms →  13.15 ms     (+4.10%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    4.30 ms →   4.56 ms     (+6.23%)           2   →      2               
! ├ sirius::Smooth_periodic_function::fft_transform                        21.54 ms →  14.92 ms    (-30.74%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      75.64 μs →  70.80 μs     (-6.41%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      4.34 ms →   4.59 ms     (+5.71%)           1   →      1               
  ├ sirius::Periodic_function|inner                                         1.57 ms →   1.66 ms     (+5.49%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                                 1.57 ms →   1.66 ms     (+5.49%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.57 ms →   1.66 ms     (+5.50%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                  1.33 ms →   1.35 ms     (+1.56%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                          1.33 ms →   1.35 ms     (+1.57%)           2   →      2               
  ├ sirius::Stress|us                                                     812.73 ms → 739.13 ms     (-9.06%)           1   →      1               
! │ ├ sirius::Smooth_periodic_function::fft_transform                      43.73 ms →  18.13 ms    (-58.54%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             92.90 ms →  93.79 ms     (+0.96%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                     3.49 ms →   3.61 ms     (+3.55%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           4.44 ms →   4.70 ms     (+5.75%)           3   →      3               
! │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         43.14 μs →  47.67 μs    (+10.51%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                           486.87 μs → 492.40 μs     (+1.14%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                               23.65 ms →  21.79 ms     (-7.87%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  97.41 ms →  95.64 ms     (-1.81%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t            12.38 ms →  12.65 ms     (+2.20%)           4   →      4               
  │ └ sirius::Non_local_functor::add_k_point                               11.33 ms →  10.85 ms     (-4.24%)           4   →      4               
! │   ├ sirius::Beta_projectors_base::prepare                               1.22 ms → 851.46 μs    (-30.29%)           8   →      8               
! │   ├ sirius::Beta_projectors_base::generate                             84.86 μs →  60.23 μs    (-29.03%)          40   →     40               
! │   ├ sirius::Beta_projectors_base::inner                               232.96 μs → 288.49 μs    (+23.84%)          40   →     40               
  │   └ sirius::Beta_projectors_base::dismiss                             976.12 ns → 973.00 ns     (-0.32%)           8   →      8               
  ├ sirius::Force::calc_forces_vloc                                         9.90 ms →  10.62 ms     (+7.25%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                         244.90 ms → 223.86 ms     (-8.59%)           1   →      1               
! │ └ sirius::Smooth_periodic_function::fft_transform                       1.53 ms →   3.14 ms   (+105.63%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                      21.04 ms →  22.80 ms     (+8.34%)           1   →      1               
! │ └ sirius::Non_local_functor::add_k_point                                3.04 ms →   3.51 ms    (+15.57%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::prepare                             139.51 μs → 138.40 μs     (-0.79%)           8   →      8               
  │   ├ sirius::Beta_projectors_base::generate                             74.61 μs →  72.04 μs     (-3.44%)          16   →     16               
  │   ├ sirius::Beta_projectors_base::inner                               104.68 μs →  98.92 μs     (-5.50%)          16   →     16               
! │   └ sirius::Beta_projectors_base::dismiss                             700.38 ns → 776.38 ns    (+10.85%)           8   →      8               
! ├ sirius::Force::calc_forces_core                                        11.22 ms →   8.69 ms    (-22.53%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     298.61 μs → 290.85 μs     (-2.60%)           1   →      1               
! ├ sirius::Force::calc_forces_ewald                                       50.14 ms →  55.34 ms    (+10.37%)           1   →      1               
! ├ sirius::Force::calc_forces_scf_corr                                     7.98 ms →  13.94 ms    (+74.73%)           1   →      1               
! ├ sirius::Force::hubbard_force                                          837.00 ns →   1.19 μs    (+41.82%)           1   →      1               
  └ sirius::finalize                                                      116.20 ms → 119.55 ms     (+2.89%)           1   →      1               
```
