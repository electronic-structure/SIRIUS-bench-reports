# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    7.92 s  →   8.32 s      (+5.03%)           1   →      1               
  ├ sirius::initialize                                                      3.13 s  →   3.41 s      (+8.71%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  1.95 s  →   1.92 s      (-1.52%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               223.67 μs → 251.06 μs    (+12.25%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       286.61 ms → 261.30 ms     (-8.83%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            91.21 ms →  81.52 ms    (-10.62%)           3   →      3               
- │ │ └ sirius::Unit_cell::update                                          12.95 ms →  16.70 ms    (+28.93%)           1   →      1               
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      246.72 μs → 219.73 μs    (-10.94%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  12.70 ms →  16.48 ms    (+29.72%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     12.67 ms →  16.45 ms    (+29.81%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.94 ms →   4.98 ms     (+0.79%)           1   →      1               
- │ │       ├ sirius::Unit_cell_symmetry|equiv                             26.76 μs →  45.45 μs    (+69.84%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               15.19 μs →  16.29 μs     (+7.26%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (-0.26%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.16 ms →   5.16 ms     (+0.05%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       35.25 μs →  32.83 μs     (-6.87%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.12 ms →   5.13 ms     (+0.10%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.10 ms →   5.11 ms     (+0.09%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                5.00 ms →   5.01 ms     (+0.20%)           1   →      1               
+ │   │     ├ sirius::Unit_cell_symmetry|equiv                             48.80 μs →  39.87 μs    (-18.31%)           1   →      1               
- │   │     └ sirius::Unit_cell_symmetry|mag                               17.24 μs →  19.13 μs    (+10.96%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      272.19 ms → 270.88 ms     (-0.48%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.27 ms →  21.24 ms     (-0.16%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.01 ms →  19.06 ms     (+0.27%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      82.21 ms →  80.37 ms     (-2.23%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.83 ms →  61.76 ms     (-0.12%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.91 ms →  96.75 ms     (-0.16%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.23 ms →   4.29 ms     (+1.42%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.94 ms →   3.01 ms     (+2.31%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.05 ms →   4.22 ms     (+4.19%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                281.60 μs → 285.03 μs     (+1.22%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  93.43 ms →  93.97 ms     (+0.58%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.84 ms →   5.93 ms     (+1.61%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            755.25 ns → 747.00 ns     (-1.09%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.77 ms →   5.86 ms     (+1.61%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.53 ms →   5.61 ms     (+1.57%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.51 ms →   4.58 ms     (+1.64%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              249.61 μs → 245.33 μs     (-1.72%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              2.96 μs →   2.83 μs     (-4.29%)           1   →      1               
  │     └ sirius::K_point::update                                         795.77 μs → 808.00 μs     (+1.54%)           1   →      1               
  │       └ sirius::Beta_projectors                                       651.74 μs → 665.10 μs     (+2.05%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                402.33 μs → 395.73 μs     (-1.64%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      245.41 μs → 265.39 μs     (+8.14%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       28.10 μs →  29.55 μs     (+5.17%)           2   →      2               
  ├ sirius::Potential                                                       1.96 ms →   1.89 ms     (-3.55%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.37 μs →  28.05 μs     (-1.11%)           6   →      6               
  │ └ sirius::Potential::update                                             1.69 ms →   1.62 ms     (-3.86%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.68 ms →   1.61 ms     (-3.87%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.25 ms →   1.16 ms     (-7.18%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 337.45 μs → 359.27 μs     (+6.47%)           1   →      1               
  ├ sirius::Density                                                         1.58 ms →   1.56 ms     (-1.38%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.51 μs →  28.44 μs     (-0.24%)           2   →      2               
  │ └ sirius::Density::update                                               1.52 ms →   1.50 ms     (-1.41%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.51 ms →   1.49 ms     (-1.42%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                21.21 μs →  19.77 μs     (-6.79%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.26 ms →   1.18 ms     (-6.91%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                 211.60 μs → 279.42 μs    (+32.05%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.78 ms →   2.77 ms     (-0.52%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    1.23 ms →   1.17 ms     (-4.51%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     281.72 μs → 293.52 μs     (+4.19%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                252.24 μs → 269.65 μs     (+6.90%)           1   →      1               
  ├ sirius::Potential::generate                                            20.33 ms →  20.63 ms     (+1.48%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            1.74 ms →   1.72 ms     (-1.18%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                   213.49 μs → 288.10 μs    (+34.94%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   263.52 μs → 272.92 μs     (+3.57%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           260.72 μs → 260.65 μs     (-0.03%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.39 μs → 260.34 μs     (-0.02%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.68 μs →  10.66 μs     (-0.21%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.06 ms →   2.05 ms     (-0.53%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.03 ms →   2.01 ms     (-0.62%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.53 μs →  28.86 μs     (-2.29%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 208.94 μs → 191.77 μs     (-8.22%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     160.42 μs → 159.97 μs     (-0.28%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        16.31 ms →  16.64 ms     (+2.05%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 218.00 ns → 188.00 ns    (-13.76%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  362.20 μs → 355.70 μs     (-1.79%)           1   →      1               
  │ ├ sirius::Local_operator                                              334.96 μs → 329.97 μs     (-1.49%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   26.39 μs →  27.55 μs     (+4.41%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   286.40 μs → 281.63 μs     (-1.67%)           1   →      1               
- │ ├ sirius::Non_local_operator                                          742.00 ns → 848.50 ns    (+14.35%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                        7.52 μs →   7.03 μs     (-6.59%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                        5.52 μs →   5.36 μs     (-2.92%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      46.27 ms →  47.66 ms     (+3.01%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                15.97 μs →  19.35 μs    (+21.12%)           1   →      1               
- │ │ └ sirius::Local_operator::prepare_k                                  14.80 μs →  18.16 μs    (+22.68%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 46.24 ms →  47.64 ms     (+3.01%)           1   →      1               
  │   ├ sddk::matrix_storage::matrix_storage                                6.55 μs →   6.03 μs     (-8.05%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   945.34 μs → 925.80 μs     (-2.07%)           1   →      1               
  │   ├ sirius::Band::initialize_subspace|kp|wf                            44.26 μs →  42.94 μs     (-2.98%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   17.47 ms →  18.05 ms     (+3.29%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.74 ms →   8.79 ms     (+0.68%)           1   →      1               
+ │   │ │ ├ sddk::matrix_storage::remap_forward                             2.42 μs →   2.06 μs    (-14.81%)           1   →      1               
+ │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.61 μs →   1.28 μs    (-20.05%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           393.00 ns → 390.00 ns     (-0.76%)           1   →      1               
+ │   │ │ └ sddk::matrix_storage::remap_backward                          645.00 ns → 529.00 ns    (-17.98%)           1   →      1               
- │   │ ├ sirius::Beta_projectors_base::inner                               4.34 ms →   5.68 ms    (+30.80%)           1   →      1               
+ │   │ └ sirius::Non_local_operator::apply                                 2.00 ms →   1.59 ms    (-20.60%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   289.78 μs → 295.56 μs     (+1.99%)           2   →      2               
  │   │ └ sddk::inner                                                     283.27 μs → 288.89 μs     (+1.98%)           2   →      2               
  │   │   └ sddk::inner|local                                             275.80 μs → 281.52 μs     (+2.07%)           2   →      2               
  │   ├ Eigensolver_lapack|zhegvx                                          26.45 ms →  27.30 ms     (+3.24%)           1   →      1               
  │   └ sddk::transform                                                   318.48 μs → 293.72 μs     (-7.78%)           1   →      1               
  │     ├ sddk::transform|init                                             66.56 μs →  61.08 μs     (-8.23%)           1   →      1               
  │     └ sddk::transform|local                                           238.06 μs → 221.21 μs     (-7.08%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.22 s  →   2.22 s      (-0.18%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     53.05 μs →  50.04 μs     (-5.67%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        100.52 ms → 100.37 ms     (-0.15%)          22   →     22               
  │ │ ├ sirius::Hamiltonian0                                              369.85 μs → 405.32 μs     (+9.59%)          22   →     22               
- │ │ │ ├ sirius::Local_operator                                          349.47 μs → 384.63 μs    (+10.06%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               30.91 μs →  31.47 μs     (+1.81%)          22   →     22               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               301.03 μs → 335.36 μs    (+11.41%)          22   →     22               
- │ │ │ ├ sirius::Non_local_operator                                      851.20 ns → 941.75 ns    (+10.64%)          44   →     44               
  │ │ │ ├ sirius::D_operator::initialize                                    7.39 μs →   7.30 μs     (-1.15%)          22   →     22               
  │ │ │ └ sirius::Q_operator::initialize                                    5.41 μs →   5.43 μs     (+0.37%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.56 ms →  37.53 ms     (-0.08%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            19.39 μs →  19.22 μs     (-0.87%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              18.37 μs →  18.26 μs     (-0.56%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.45 ms →  33.30 ms     (-0.46%)          22   →     22               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             13.38 μs →  13.24 μs     (-0.99%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          1.00 μs → 961.26 ns     (-4.11%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           700.26 μs → 702.09 μs     (+0.26%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.72 μs →  10.89 μs     (+1.53%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       218.28 μs → 218.89 μs     (+0.28%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.73 ms →  32.57 ms     (-0.47%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.16 ms →   5.14 ms     (-0.42%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.26 ms →   4.25 ms     (-0.26%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.15 μs →   1.94 μs     (-9.79%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.86 μs →   1.70 μs     (-8.30%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     503.36 ns → 516.74 ns     (+2.66%)          87   →     87               
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    450.40 ns → 325.23 ns    (-27.79%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       285.53 μs → 281.02 μs     (-1.58%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         274.95 μs → 272.22 μs     (-0.99%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         889.17 μs → 881.89 μs     (-0.82%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               140.62 μs → 138.60 μs     (-1.44%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       139.04 μs → 137.10 μs     (-1.40%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.41 μs →  31.91 μs     (-1.52%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             250.13 μs → 249.29 μs     (-0.33%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           473.27 μs → 470.20 μs     (-0.65%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     75.84 μs →  75.98 μs     (+0.18%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   131.83 μs → 130.79 μs     (-0.79%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             209.40 μs → 208.03 μs     (-0.65%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               194.37 μs → 193.12 μs     (-0.64%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       193.27 μs → 192.05 μs     (-0.63%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   992.54 μs → 991.63 μs     (-0.09%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           583.81 μs → 575.42 μs     (-1.44%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           427.27 μs → 424.57 μs     (-0.63%)          69   →     68       (-1.45%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     70.22 μs →  69.64 μs     (-0.81%)          69   →     68       (-1.45%)
  │ │ │ │   │ │ └ sddk::transform|local                                   177.56 μs → 176.60 μs     (-0.54%)         138   →    136       (-1.45%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               290.30 μs → 293.48 μs     (+1.10%)          69   →     68       (-1.45%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     871.96 μs → 871.31 μs     (-0.07%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           528.95 μs → 527.97 μs     (-0.18%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     74.34 μs →  72.73 μs     (-2.16%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   349.53 μs → 350.05 μs     (+0.15%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.61 μs →  19.81 μs     (-3.84%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        199.84 μs → 199.86 μs     (+0.01%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          37.16 ms →  37.02 ms     (-0.40%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                28.79 ms →  28.29 ms     (-1.75%)          22   →     22               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.63 μs →   2.53 μs     (-3.87%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.30 μs →   2.25 μs     (-2.31%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  409.01 μs → 408.40 μs     (-0.15%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         383.78 μs → 383.99 μs     (+0.05%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.81 ms →   2.82 ms     (+0.20%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               141.87 μs → 138.86 μs     (-2.12%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       25.04 ms →  24.24 ms     (-3.20%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            25.02 ms →  24.22 ms     (-3.21%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      4.18 ms →   3.94 ms     (-5.83%)          66   →     66               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       2.92 ms →   2.96 ms     (+1.07%)          66   →     66               
  │ │ │ ├ sirius::Field4D::symmetrize                                       4.37 ms →   4.70 ms     (+7.55%)          22   →     22               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 4.37 ms →   4.70 ms     (+7.55%)          22   →     22               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              1.06 ms →   1.39 ms    (+30.48%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.30 ms →   2.32 ms     (+0.58%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           985.63 μs → 978.61 μs     (-0.71%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.66 ms →   3.68 ms     (+0.42%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 329.75 μs → 340.00 μs     (+3.11%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                4.95 ms →   4.92 ms     (-0.57%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     23.00 μs →  21.16 μs     (-8.02%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 252.39 μs → 253.39 μs     (+0.40%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         250.38 μs → 250.05 μs     (-0.13%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                250.20 μs → 249.86 μs     (-0.14%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   192.21 μs → 193.75 μs     (+0.80%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               180.04 μs → 181.80 μs     (+0.98%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        13.24 ms →  13.23 ms     (-0.08%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        1.74 ms →   1.72 ms     (-0.85%)          22   →     22               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               230.96 μs → 299.37 μs    (+29.62%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               268.97 μs → 266.53 μs     (-0.91%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       264.76 μs → 262.79 μs     (-0.74%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              264.01 μs → 262.49 μs     (-0.58%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   10.54 μs →  10.72 μs     (+1.68%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.09 ms →   2.06 ms     (-1.14%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.03 ms →   2.01 ms     (-1.14%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             31.08 μs →  29.29 μs     (-5.76%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             204.00 μs → 199.15 μs     (-2.38%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 157.91 μs → 158.80 μs     (+0.56%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     9.18 ms →   9.21 ms     (+0.26%)          22   →     22               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             240.14 ns → 185.23 ns    (-22.87%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.92 ms →   3.93 ms     (+0.13%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.92 ms →   3.93 ms     (+0.13%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              621.82 μs → 617.99 μs     (-0.62%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.36 ms →   2.32 ms     (-1.72%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             922.53 μs → 971.72 μs     (+5.33%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   241.64 μs → 239.91 μs     (-0.72%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   249.54 μs → 252.92 μs     (+1.36%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           247.24 μs → 246.27 μs     (-0.39%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  246.92 μs → 246.01 μs     (-0.37%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            259.30 μs → 259.78 μs     (+0.19%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    257.33 μs → 256.16 μs     (-0.45%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              236.48 μs → 238.39 μs     (+0.81%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 52.37 μs →  51.68 μs     (-1.32%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          50.54 μs →  49.86 μs     (-1.34%)          22   →     22               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                       185.54 μs → 194.90 μs     (+5.04%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     247.25 μs → 259.30 μs     (+4.87%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             244.06 μs → 244.20 μs     (+0.06%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    243.93 μs → 244.08 μs     (+0.06%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              249.98 μs → 257.72 μs     (+3.10%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      248.51 μs → 256.09 μs     (+3.05%)           3   →      3               
  ├ sirius::Stress|kin                                                    351.67 μs → 341.29 μs     (-2.95%)           1   →      1               
  ├ sirius::Stress|har                                                    579.34 μs → 587.32 μs     (+1.38%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.75 ms →   1.79 ms     (+2.32%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.21 ms →   3.14 ms     (-2.05%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    1.17 ms →   1.14 ms     (-2.77%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       214.38 μs → 206.91 μs     (-3.49%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      18.71 μs →  18.88 μs     (+0.94%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      1.21 ms →   1.15 ms     (-5.45%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       250.20 μs → 251.31 μs     (+0.44%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               248.92 μs → 249.90 μs     (+0.40%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      248.73 μs → 249.70 μs     (+0.39%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                261.25 μs → 254.06 μs     (-2.75%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        259.93 μs → 252.75 μs     (-2.76%)           2   →      2               
  ├ sirius::Stress|us                                                     328.18 ms → 326.40 ms     (-0.54%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     195.37 μs → 192.59 μs     (-1.42%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             77.15 ms →  77.05 ms     (-0.13%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   563.54 μs → 581.73 μs     (+3.23%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           1.22 ms →   1.19 ms     (-2.02%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         23.57 ms →  22.22 ms     (-5.76%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                            68.06 μs →  67.38 μs     (-1.00%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                1.16 ms →   1.26 ms     (+8.29%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.48 ms →  14.52 ms     (+0.25%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.81 ms →   5.91 ms     (+1.69%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.05 ms →   8.00 ms     (-0.56%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               331.47 μs → 330.72 μs     (-0.23%)          10   →     10               
- │   ├ sirius::Beta_projectors_base::prepare                               3.98 μs →   4.81 μs    (+20.88%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            274.66 μs → 272.62 μs     (-0.74%)           9   →      9               
  │   └ sirius::Beta_projectors_base::dismiss                              93.00 ns →  98.00 ns     (+5.38%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.18 ms →   1.14 ms     (-2.88%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          24.16 ms →  23.69 ms     (-1.92%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     259.85 μs → 248.14 μs     (-4.51%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.18 ms →   4.15 ms     (-0.88%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.98 ms →   2.97 ms     (-0.27%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               344.27 μs → 345.05 μs     (+0.23%)           4   →      4               
- │   ├ sirius::Beta_projectors_base::prepare                               3.53 μs →   4.01 μs    (+13.61%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            281.27 μs → 275.48 μs     (-2.06%)           3   →      3               
  │   └ sirius::Beta_projectors_base::dismiss                             148.00 ns → 160.00 ns     (+8.11%)           1   →      1               
  ├ sirius::Force::calc_forces_core                                         1.14 ms →   1.06 ms     (-6.95%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     212.51 μs → 214.75 μs     (+1.06%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       13.02 ms →  12.66 ms     (-2.72%)           1   →      1               
  ├ sirius::Force::calc_forces_scf_corr                                   895.26 μs → 839.12 μs     (-6.27%)           1   →      1               
- ├ sirius::Force::hubbard_force                                          575.00 ns →   1.86 μs   (+224.35%)           1   →      1               
  └ sirius::finalize                                                      127.48 ms → 126.35 ms     (-0.89%)           1   →      1               
```
