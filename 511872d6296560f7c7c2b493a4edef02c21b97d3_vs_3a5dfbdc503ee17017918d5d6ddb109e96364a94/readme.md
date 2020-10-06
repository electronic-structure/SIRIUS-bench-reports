# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    8.41 s  →   7.71 s      (-8.29%)           1   →      1               
  ├ sirius::initialize                                                      2.92 s  →   2.92 s      (-0.18%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  1.97 s  →   1.90 s      (-3.16%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               365.64 μs → 400.49 μs     (+9.53%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       300.60 ms → 246.75 ms    (-17.91%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            95.35 ms →  77.40 ms    (-18.83%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          14.52 ms →  14.53 ms     (+0.08%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      249.93 μs → 231.27 μs     (-7.47%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  14.26 ms →  14.29 ms     (+0.21%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     14.23 ms →  14.27 ms     (+0.21%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.93 ms →   4.94 ms     (+0.23%)           1   →      1               
- │ │       ├ sirius::Unit_cell_symmetry|equiv                             45.50 μs →  51.83 μs    (+13.91%)           1   →      1               
- │ │       └ sirius::Unit_cell_symmetry|mag                               14.55 μs →  17.47 μs    (+20.07%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (-0.46%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.16 ms →   5.18 ms     (+0.42%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       34.54 μs →  32.72 μs     (-5.26%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.12 ms →   5.14 ms     (+0.46%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.10 ms →   5.12 ms     (+0.46%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.99 ms →   5.02 ms     (+0.52%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                             50.85 μs →  47.98 μs     (-5.65%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               17.30 μs →  17.55 μs     (+1.42%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      273.88 ms → 272.26 ms     (-0.59%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.38 ms →  21.36 ms     (-0.10%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.02 ms →  18.98 ms     (-0.22%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.50 ms →  80.38 ms     (-0.15%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.58 ms →  61.80 ms     (+0.35%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.77 ms →  96.61 ms     (-0.16%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.35 ms →   4.26 ms     (-2.05%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      3.04 ms →   2.96 ms     (-2.76%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.00 ms →   4.06 ms     (+1.72%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                304.41 μs → 284.83 μs     (-6.43%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  94.54 ms →  93.79 ms     (-0.79%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.90 ms →   5.90 ms     (+0.12%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            698.00 ns → 693.75 ns     (-0.61%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.82 ms →   5.83 ms     (+0.15%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.57 ms →   5.59 ms     (+0.25%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.54 ms →   4.57 ms     (+0.58%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              253.22 μs → 257.22 μs     (+1.58%)           1   →      1               
- │     ├ sddk::matrix_storage::matrix_storage                              2.78 μs →   3.19 μs    (+14.71%)           1   →      1               
  │     └ sirius::K_point::update                                         808.74 μs → 792.31 μs     (-2.03%)           1   →      1               
  │       └ sirius::Beta_projectors                                       664.16 μs → 649.28 μs     (-2.24%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                399.77 μs → 398.09 μs     (-0.42%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      260.30 μs → 247.04 μs     (-5.10%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       29.17 μs →  29.48 μs     (+1.07%)           2   →      2               
  ├ sirius::Potential                                                       2.03 ms →   2.05 ms     (+0.99%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.08 μs →  27.09 μs     (-3.51%)           6   →      6               
  │ └ sirius::Potential::update                                             1.76 ms →   1.79 ms     (+1.78%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.75 ms →   1.78 ms     (+1.80%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.31 ms →   1.36 ms     (+4.39%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 363.13 μs → 331.77 μs     (-8.63%)           1   →      1               
  ├ sirius::Density                                                         1.81 ms →   1.73 ms     (-4.41%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.98 μs →  28.42 μs     (-1.95%)           2   →      2               
  │ └ sirius::Density::update                                               1.75 ms →   1.67 ms     (-4.50%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.74 ms →   1.66 ms     (-4.53%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                19.56 μs →  19.14 μs     (-2.13%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.32 ms →   1.43 ms     (+8.20%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 382.75 μs → 196.61 μs    (-48.63%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.92 ms →   2.86 ms     (-1.79%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                    1.16 ms →   1.38 ms    (+18.51%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                     382.17 μs → 245.44 μs    (-35.78%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                261.32 μs → 252.28 μs     (-3.46%)           1   →      1               
  ├ sirius::Potential::generate                                            21.46 ms →  21.13 ms     (-1.56%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            1.93 ms →   1.98 ms     (+2.88%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   350.33 μs → 205.32 μs    (-41.39%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   264.76 μs → 263.52 μs     (-0.47%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           249.84 μs → 260.88 μs     (+4.42%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  249.51 μs → 260.52 μs     (+4.41%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.74 μs →  10.38 μs     (-3.40%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.07 ms →   2.05 ms     (-0.97%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.03 ms →   2.01 ms     (-0.92%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.00 μs →  28.37 μs     (-2.17%)           2   →      2               
+ │ │   └ sirius::Smooth_periodic_function::fft_transform                 223.33 μs → 195.45 μs    (-12.48%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     164.58 μs → 162.51 μs     (-1.26%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        17.25 ms →  16.88 ms     (-2.10%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                 139.00 ns → 200.00 ns    (+43.88%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  347.29 μs → 357.82 μs     (+3.03%)           1   →      1               
  │ ├ sirius::Local_operator                                              321.45 μs → 327.47 μs     (+1.87%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   27.54 μs →  25.73 μs     (-6.57%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   273.59 μs → 281.37 μs     (+2.84%)           1   →      1               
  │ ├ sirius::Non_local_operator                                          872.00 ns → 867.50 ns     (-0.52%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                        6.89 μs →   8.99 μs    (+30.38%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                        5.14 μs →   7.77 μs    (+51.12%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      48.33 ms →  47.37 ms     (-1.97%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                17.64 μs →  16.77 μs     (-4.93%)           1   →      1               
  │ │ └ sirius::Local_operator::prepare_k                                  16.40 μs →  15.20 μs     (-7.33%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 48.30 ms →  47.35 ms     (-1.97%)           1   →      1               
- │   ├ sddk::matrix_storage::matrix_storage                                5.15 μs →   5.86 μs    (+13.80%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   937.51 μs → 947.75 μs     (+1.09%)           1   →      1               
  │   ├ sirius::Band::initialize_subspace|kp|wf                            47.05 μs →  51.39 μs     (+9.22%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   17.57 ms →  17.11 ms     (-2.60%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.51 ms →   8.63 ms     (+1.43%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::remap_forward                             2.08 μs →   2.24 μs     (+7.81%)           1   →      1               
  │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.27 μs →   1.32 μs     (+4.66%)           1   →      1               
+ │   │ │ ├ sddk::matrix_storage::set_num_extra                           357.00 ns → 321.00 ns    (-10.08%)           1   →      1               
+ │   │ │ └ sddk::matrix_storage::remap_backward                          715.00 ns → 626.00 ns    (-12.45%)           1   →      1               
  │   │ ├ sirius::Beta_projectors_base::inner                               5.48 ms →   5.06 ms     (-7.66%)           1   →      1               
  │   │ └ sirius::Non_local_operator::apply                                 1.60 ms →   1.51 ms     (-5.62%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   280.13 μs → 279.78 μs     (-0.12%)           2   →      2               
  │   │ └ sddk::inner                                                     273.42 μs → 273.46 μs     (+0.01%)           2   →      2               
  │   │   └ sddk::inner|local                                             266.09 μs → 266.02 μs     (-0.02%)           2   →      2               
  │   ├ Eigensolver_lapack|zhegvx                                          28.72 ms →  27.92 ms     (-2.77%)           1   →      1               
  │   └ sddk::transform                                                   309.01 μs → 318.86 μs     (+3.19%)           1   →      1               
  │     ├ sddk::transform|init                                             64.46 μs →  65.96 μs     (+2.32%)           1   →      1               
  │     └ sddk::transform|local                                           232.38 μs → 241.53 μs     (+3.94%)           1   →      1               
+ ├ sirius::DFT_ground_state::scf_loop                                      2.90 s  →   2.27 s     (-21.67%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function                                     64.63 μs →  51.36 μs    (-20.54%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        102.25 ms → 102.71 ms     (+0.45%)          22   →     22               
- │ │ ├ sirius::Hamiltonian0                                              304.62 μs → 382.15 μs    (+25.45%)          22   →     22               
- │ │ │ ├ sirius::Local_operator                                          283.83 μs → 360.85 μs    (+27.14%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               31.91 μs →  31.70 μs     (-0.64%)          22   →     22               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               235.81 μs → 312.62 μs    (+32.57%)          22   →     22               
+ │ │ │ ├ sirius::Non_local_operator                                      926.77 ns → 832.93 ns    (-10.13%)          44   →     44               
  │ │ │ ├ sirius::D_operator::initialize                                    7.23 μs →   7.69 μs     (+6.32%)          22   →     22               
  │ │ │ └ sirius::Q_operator::initialize                                    5.43 μs →   5.53 μs     (+1.74%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.60 ms →  37.91 ms     (+0.84%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            20.46 μs →  19.35 μs     (-5.43%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              19.42 μs →  18.37 μs     (-5.38%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.46 ms →  33.62 ms     (+0.48%)          22   →     22               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             12.68 μs →  12.81 μs     (+1.01%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        887.99 ns → 961.43 ns     (+8.27%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           708.06 μs → 701.91 μs     (-0.87%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        11.39 μs →  10.61 μs     (-6.79%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       220.68 μs → 218.73 μs     (-0.88%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.73 ms →  32.90 ms     (+0.51%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.17 ms →   5.16 ms     (-0.25%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.28 ms →   4.27 ms     (-0.40%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.05 μs →   1.94 μs     (-5.51%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.74 μs →   1.67 μs     (-3.81%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     515.86 ns → 494.49 ns     (-4.14%)          87   →     87               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    401.15 ns → 370.24 ns     (-7.70%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       281.80 μs → 280.49 μs     (-0.47%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         275.47 μs → 275.31 μs     (-0.06%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         882.76 μs → 901.16 μs     (+2.08%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               139.50 μs → 141.45 μs     (+1.40%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       137.90 μs → 139.91 μs     (+1.46%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.36 μs →  32.71 μs     (+1.07%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             248.34 μs → 257.76 μs     (+3.79%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           469.61 μs → 476.93 μs     (+1.56%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     75.63 μs →  76.18 μs     (+0.72%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   130.71 μs → 132.95 μs     (+1.72%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             208.15 μs → 214.04 μs     (+2.83%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               192.86 μs → 198.54 μs     (+2.95%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       191.80 μs → 197.56 μs     (+3.00%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   992.11 μs →   1.01 ms     (+1.51%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           574.73 μs → 592.28 μs     (+3.05%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           423.36 μs → 435.87 μs     (+2.96%)          68   →     68               
  │ │ │ │   │ │ ├ sddk::transform|init                                     66.58 μs →  70.62 μs     (+6.06%)          68   →     68               
  │ │ │ │   │ │ └ sddk::transform|local                                   177.50 μs → 181.70 μs     (+2.37%)         136   →    136               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               293.19 μs → 303.66 μs     (+3.57%)          68   →     68               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     873.94 μs → 887.06 μs     (+1.50%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           529.83 μs → 538.18 μs     (+1.58%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     73.59 μs →  73.44 μs     (-0.21%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   350.59 μs → 357.31 μs     (+1.92%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.65 μs →  19.31 μs     (-6.53%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        199.52 μs → 205.31 μs     (+2.90%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          37.78 ms →  37.72 ms     (-0.17%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                28.60 ms →  29.67 ms     (+3.74%)          22   →     22               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.64 μs →   2.30 μs    (-12.62%)          22   →     22               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.31 μs →   2.04 μs    (-11.33%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  409.14 μs → 411.22 μs     (+0.51%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         383.96 μs → 386.07 μs     (+0.55%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.84 ms →   2.82 ms     (-0.48%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               139.25 μs → 139.46 μs     (+0.15%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       24.69 ms →  25.97 ms     (+5.19%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            24.66 ms →  25.96 ms     (+5.24%)          22   →     22               
- │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      3.87 ms →   4.47 ms    (+15.52%)          66   →     66               
+ │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       3.08 ms →   2.66 ms    (-13.69%)          66   →     66               
+ │ │ │ ├ sirius::Field4D::symmetrize                                       5.18 ms →   4.04 ms    (-21.98%)          22   →     22               
+ │ │ │ │ └ sirius::symmetrize_function|fpw                                 5.18 ms →   4.04 ms    (-21.98%)          22   →     22               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              1.79 ms → 744.13 μs    (-58.41%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.42 ms →   2.28 ms     (-5.76%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           941.76 μs → 989.69 μs     (+5.09%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.66 ms →   3.66 ms     (+0.05%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 343.52 μs → 346.63 μs     (+0.90%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                5.05 ms →   5.26 ms     (+4.28%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     22.00 μs →  21.99 μs     (-0.05%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 265.00 μs → 276.47 μs     (+4.33%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         261.25 μs → 275.58 μs     (+5.48%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                261.08 μs → 275.39 μs     (+5.48%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   187.77 μs → 194.00 μs     (+3.32%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               175.36 μs → 181.02 μs     (+3.23%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.14 ms →  14.21 ms     (+0.46%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        1.97 ms →   1.98 ms     (+0.66%)          22   →     22               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               394.50 μs → 208.05 μs    (-47.26%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               255.13 μs → 263.49 μs     (+3.28%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       250.38 μs → 262.07 μs     (+4.67%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              250.04 μs → 261.75 μs     (+4.68%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   11.16 μs →  10.74 μs     (-3.72%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.08 ms →   2.07 ms     (-0.48%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.02 ms →   2.01 ms     (-0.32%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             30.31 μs →  30.20 μs     (-0.36%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             204.03 μs → 200.81 μs     (-1.58%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 156.67 μs → 158.00 μs     (+0.85%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     9.86 ms →   9.92 ms     (+0.64%)          22   →     22               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             201.18 ns → 182.91 ns     (-9.08%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         4.03 ms →   3.89 ms     (-3.39%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   4.03 ms →   3.89 ms     (-3.39%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              628.34 μs → 626.29 μs     (-0.33%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.37 ms →   2.30 ms     (-3.23%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                               1.01 ms → 947.39 μs     (-5.76%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   238.80 μs → 240.65 μs     (+0.77%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   259.52 μs → 250.10 μs     (-3.63%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           257.35 μs → 248.09 μs     (-3.60%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  257.04 μs → 247.84 μs     (-3.58%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            246.39 μs → 260.48 μs     (+5.72%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    244.71 μs → 258.83 μs     (+5.77%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              236.51 μs → 238.95 μs     (+1.03%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 51.90 μs →  50.99 μs     (-1.76%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          50.19 μs →  49.27 μs     (-1.83%)          22   →     22               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                       194.35 μs → 197.13 μs     (+1.43%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     264.01 μs → 249.17 μs     (-5.62%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             262.42 μs → 245.46 μs     (-6.46%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    262.29 μs → 245.35 μs     (-6.46%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              255.26 μs → 258.14 μs     (+1.13%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      254.43 μs → 256.90 μs     (+0.97%)           3   →      3               
  ├ sirius::Stress|kin                                                    304.13 μs → 301.20 μs     (-0.96%)           1   →      1               
  ├ sirius::Stress|har                                                    609.29 μs → 582.53 μs     (-4.39%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.80 ms →   1.77 ms     (-1.54%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.40 ms →   3.38 ms     (-0.52%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    1.24 ms →   1.28 ms     (+3.25%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       211.86 μs → 216.08 μs     (+1.99%)           1   →      1               
+ ├ sirius::rho_core_ri_pseudo|values                                      22.44 μs →  18.99 μs    (-15.40%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      1.30 ms →   1.34 ms     (+2.41%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       265.51 μs → 256.87 μs     (-3.25%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               264.37 μs → 255.58 μs     (-3.32%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      264.19 μs → 255.42 μs     (-3.32%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                251.84 μs → 258.01 μs     (+2.45%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        250.80 μs → 256.97 μs     (+2.46%)           2   →      2               
  ├ sirius::Stress|us                                                     323.28 ms → 327.73 ms     (+1.38%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     193.91 μs → 193.24 μs     (-0.35%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             77.41 ms →  79.15 ms     (+2.24%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   602.76 μs → 608.58 μs     (+0.96%)           3   →      3               
- │ ├ sirius::Stress|us|phase_fac                                           1.29 ms →   1.50 ms    (+16.84%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.11 ms →  22.21 ms     (+0.45%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                            69.13 μs →  73.44 μs     (+6.22%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                1.28 ms →   1.36 ms     (+6.77%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.54 ms →  14.55 ms     (+0.10%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.95 ms →   5.95 ms     (+0.08%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.08 ms →   8.05 ms     (-0.35%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               329.70 μs → 331.69 μs     (+0.60%)          10   →     10               
+ │   ├ sirius::Beta_projectors_base::prepare                               6.90 μs →   5.48 μs    (-20.64%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            281.74 μs → 273.14 μs     (-3.05%)           9   →      9               
- │   └ sirius::Beta_projectors_base::dismiss                              71.00 ns →  90.00 ns    (+26.76%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.37 ms →   1.34 ms     (-2.22%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          25.59 ms →  25.73 ms     (+0.53%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     247.83 μs → 250.46 μs     (+1.06%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.16 ms →   4.26 ms     (+2.42%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.99 ms →   2.97 ms     (-0.58%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               340.06 μs → 343.51 μs     (+1.01%)           4   →      4               
- │   ├ sirius::Beta_projectors_base::prepare                               2.37 μs →   3.57 μs    (+50.61%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            292.73 μs → 272.59 μs     (-6.88%)           3   →      3               
  │   └ sirius::Beta_projectors_base::dismiss                              83.00 ns →  80.00 ns     (-3.61%)           1   →      1               
+ ├ sirius::Force::calc_forces_core                                         1.29 ms → 966.56 μs    (-25.04%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     213.94 μs → 212.35 μs     (-0.74%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       14.19 ms →  14.39 ms     (+1.41%)           1   →      1               
+ ├ sirius::Force::calc_forces_scf_corr                                     1.05 ms → 687.85 μs    (-34.36%)           1   →      1               
- ├ sirius::Force::hubbard_force                                            1.40 μs →   1.58 μs    (+13.19%)           1   →      1               
  └ sirius::finalize                                                      124.15 ms → 125.09 ms     (+0.75%)           1   →      1               
```
