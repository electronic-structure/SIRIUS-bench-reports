# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    7.68 s  →   8.06 s      (+4.86%)           1   →      1               
  ├ sirius::initialize                                                      2.87 s  →   2.89 s      (+0.43%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  1.92 s  →   2.29 s     (+19.20%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                44.12 ms → 376.42 μs    (-99.15%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       208.69 ms → 620.97 ms   (+197.56%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            64.48 ms → 201.39 ms   (+212.35%)           3   →      3               
- │ │ └ sirius::Unit_cell::update                                          15.23 ms →  16.77 ms    (+10.12%)           1   →      1               
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      292.51 μs → 260.73 μs    (-10.87%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  14.93 ms →  16.51 ms    (+10.54%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     14.90 ms →  16.48 ms    (+10.60%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.96 ms →   4.95 ms     (-0.22%)           1   →      1               
- │ │       ├ sirius::Unit_cell_symmetry|equiv                             48.23 μs →   2.98 ms  (+6068.12%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               16.72 μs →  15.73 μs     (-5.90%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (-0.05%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.17 ms →   5.15 ms     (-0.54%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       34.61 μs →  32.97 μs     (-4.74%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.14 ms →   5.11 ms     (-0.52%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.12 ms →   5.09 ms     (-0.51%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                5.01 ms →   4.98 ms     (-0.65%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                             49.38 μs →  54.16 μs     (+9.69%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               18.78 μs →  19.02 μs     (+1.31%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      274.14 ms → 272.56 ms     (-0.58%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.35 ms →  21.37 ms     (+0.13%)           2   →      2               
- │   ├ sirius::Radial_integrals|rho_pseudo                                19.04 ms →  22.23 ms    (+16.74%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.42 ms →  80.44 ms     (+0.02%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.67 ms →  61.70 ms     (+0.05%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                97.02 ms →  96.74 ms     (-0.28%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.28 ms →   4.23 ms     (-1.32%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      3.01 ms →   2.96 ms     (-1.63%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.13 ms →   4.05 ms     (-1.89%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                282.10 μs → 285.04 μs     (+1.04%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  93.93 ms →  93.89 ms     (-0.05%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.84 ms →   5.90 ms     (+1.00%)           1   →      1               
- │ ├ sirius::K_point::K_point                                            739.75 ns → 834.75 ns    (+12.84%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.77 ms →   5.83 ms     (+0.94%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.52 ms →   5.58 ms     (+0.97%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.52 ms →   4.56 ms     (+0.96%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              241.91 μs → 252.07 μs     (+4.20%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              2.58 μs →   2.74 μs     (+6.40%)           1   →      1               
  │     └ sirius::K_point::update                                         783.84 μs → 797.11 μs     (+1.69%)           1   →      1               
  │       └ sirius::Beta_projectors                                       640.54 μs → 654.43 μs     (+2.17%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                392.23 μs → 402.61 μs     (+2.65%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      244.63 μs → 247.32 μs     (+1.10%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       27.73 μs →  29.32 μs     (+5.74%)           2   →      2               
  ├ sirius::Potential                                                       2.09 ms →   2.17 ms     (+3.68%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     27.41 μs →  27.27 μs     (-0.50%)           6   →      6               
  │ └ sirius::Potential::update                                             1.83 ms →   1.90 ms     (+3.81%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.82 ms →   1.89 ms     (+3.84%)           1   →      1               
- │     ├ sirius::Simulation_context::make_periodic_function                1.23 ms →   1.43 ms    (+15.93%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 501.56 μs → 370.31 μs    (-26.17%)           1   →      1               
  ├ sirius::Density                                                         1.94 ms →   1.96 ms     (+1.31%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.56 μs →  28.83 μs     (+0.94%)           2   →      2               
  │ └ sirius::Density::update                                               1.87 ms →   1.90 ms     (+1.37%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.86 ms →   1.89 ms     (+1.40%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                20.84 μs →  19.78 μs     (-5.11%)           1   →      1               
- │     ├ sirius::Simulation_context::make_periodic_function                1.26 ms →   1.49 ms    (+18.74%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 571.86 μs → 363.01 μs    (-36.52%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.86 ms →   3.01 ms     (+5.46%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                    1.24 ms →   1.54 ms    (+23.62%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                     311.63 μs → 238.83 μs    (-23.36%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                252.88 μs → 252.70 μs     (-0.07%)           1   →      1               
  ├ sirius::Potential::generate                                            22.70 ms →  21.84 ms     (-3.80%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            2.06 ms →   2.11 ms     (+2.23%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   575.63 μs → 190.24 μs    (-66.95%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   268.03 μs → 263.42 μs     (-1.72%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           260.75 μs → 260.63 μs     (-0.05%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.46 μs → 260.33 μs     (-0.05%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.57 μs →  10.30 μs     (-2.53%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.09 ms →   2.05 ms     (-2.06%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.05 ms →   2.01 ms     (-1.99%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.29 μs →  29.37 μs     (+0.28%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 197.86 μs → 187.07 μs     (-5.45%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     163.72 μs → 160.72 μs     (-1.84%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        18.33 ms →  17.47 ms     (-4.71%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 160.00 ns → 174.00 ns     (+8.75%)           1   →      1               
+ ├ sirius::Hamiltonian0                                                  393.29 μs → 353.15 μs    (-10.21%)           1   →      1               
+ │ ├ sirius::Local_operator                                              366.98 μs → 326.93 μs    (-10.91%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   28.11 μs →  26.70 μs     (-5.03%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                   315.82 μs → 279.53 μs    (-11.49%)           1   →      1               
  │ ├ sirius::Non_local_operator                                          901.50 ns → 862.50 ns     (-4.33%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                        7.59 μs →   6.95 μs     (-8.43%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                        5.24 μs →   5.40 μs     (+3.03%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      50.00 ms →  49.57 ms     (-0.86%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                14.66 μs →  16.21 μs    (+10.55%)           1   →      1               
- │ │ └ sirius::Local_operator::prepare_k                                  13.14 μs →  14.73 μs    (+12.13%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 49.97 ms →  49.54 ms     (-0.87%)           1   →      1               
- │   ├ sddk::matrix_storage::matrix_storage                                5.40 μs →   6.39 μs    (+18.38%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   923.42 μs → 931.45 μs     (+0.87%)           1   →      1               
  │   ├ sirius::Band::initialize_subspace|kp|wf                            47.16 μs →  45.70 μs     (-3.11%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   18.31 ms →  17.58 ms     (-3.98%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.44 ms →   8.56 ms     (+1.38%)           1   →      1               
- │   │ │ ├ sddk::matrix_storage::remap_forward                             2.08 μs →   2.61 μs    (+25.79%)           1   →      1               
- │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.25 μs →   1.83 μs    (+46.25%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           407.00 ns → 382.00 ns     (-6.14%)           1   →      1               
- │   │ │ └ sddk::matrix_storage::remap_backward                          415.00 ns → 611.00 ns    (+47.23%)           1   →      1               
+ │   │ ├ sirius::Beta_projectors_base::inner                               5.98 ms →   4.83 ms    (-19.32%)           1   →      1               
- │   │ └ sirius::Non_local_operator::apply                                 1.70 ms →   1.90 ms    (+11.51%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   286.39 μs → 295.63 μs     (+3.23%)           2   →      2               
  │   │ └ sddk::inner                                                     279.44 μs → 288.99 μs     (+3.41%)           2   →      2               
  │   │   └ sddk::inner|local                                             271.50 μs → 281.60 μs     (+3.72%)           2   →      2               
  │   ├ Eigensolver_lapack|zhegvx                                          29.63 ms →  29.62 ms     (-0.04%)           1   →      1               
  │   └ sddk::transform                                                   319.63 μs → 332.69 μs     (+4.09%)           1   →      1               
+ │     ├ sddk::transform|init                                             69.24 μs →  61.28 μs    (-11.49%)           1   →      1               
- │     └ sddk::transform|local                                           232.67 μs → 258.95 μs    (+11.30%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.26 s  →   2.26 s      (+0.07%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function                                     69.74 μs →  52.52 μs    (-24.69%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        101.99 ms → 102.08 ms     (+0.09%)          22   →     22               
- │ │ ├ sirius::Hamiltonian0                                              300.90 μs → 371.98 μs    (+23.62%)          22   →     22               
- │ │ │ ├ sirius::Local_operator                                          280.21 μs → 350.88 μs    (+25.22%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               31.52 μs →  34.10 μs     (+8.19%)          22   →     22               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               230.80 μs → 300.13 μs    (+30.04%)          22   →     22               
  │ │ │ ├ sirius::Non_local_operator                                      853.20 ns → 859.82 ns     (+0.78%)          44   →     44               
  │ │ │ ├ sirius::D_operator::initialize                                    7.38 μs →   7.67 μs     (+3.94%)          22   →     22               
  │ │ │ └ sirius::Q_operator::initialize                                    5.33 μs →   5.63 μs     (+5.65%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.64 ms →  37.70 ms     (+0.16%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            19.35 μs →  19.55 μs     (+1.03%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              18.41 μs →  18.45 μs     (+0.21%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.62 ms →  33.80 ms     (+0.52%)          22   →     22               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             12.75 μs →  13.61 μs     (+6.72%)          22   →     22               
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        894.93 ns →   1.02 μs    (+14.20%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           704.19 μs → 698.65 μs     (-0.79%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.89 μs →  10.99 μs     (+0.89%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       219.61 μs → 217.46 μs     (-0.98%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.89 ms →  33.07 ms     (+0.55%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.18 ms →   5.24 ms     (+1.09%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.29 ms →   4.33 ms     (+0.93%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.00 μs →   2.16 μs     (+8.09%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.74 μs →   1.80 μs     (+3.31%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     555.64 ns → 577.15 ns     (+3.87%)          87   →     87               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    419.15 ns → 472.44 ns    (+12.71%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       286.42 μs → 292.08 μs     (+1.97%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         275.67 μs → 277.43 μs     (+0.64%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         892.04 μs → 889.32 μs     (-0.31%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               141.42 μs → 142.16 μs     (+0.53%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       139.90 μs → 140.56 μs     (+0.48%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.15 μs →  32.09 μs     (-0.20%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             251.78 μs → 249.52 μs     (-0.90%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           473.75 μs → 471.12 μs     (-0.56%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     75.66 μs →  75.92 μs     (+0.35%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   132.05 μs → 131.08 μs     (-0.74%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             214.07 μs → 210.14 μs     (-1.84%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               198.94 μs → 195.27 μs     (-1.84%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       197.93 μs → 194.24 μs     (-1.86%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   995.90 μs → 989.20 μs     (-0.67%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           579.73 μs → 579.19 μs     (-0.09%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           426.22 μs → 425.58 μs     (-0.15%)          68   →     68               
  │ │ │ │   │ │ ├ sddk::transform|init                                     67.33 μs →  70.70 μs     (+5.00%)          68   →     68               
  │ │ │ │   │ │ └ sddk::transform|local                                   178.52 μs → 176.42 μs     (-1.18%)         136   →    136               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               297.33 μs → 296.86 μs     (-0.16%)          68   →     68               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     888.70 μs → 903.40 μs     (+1.65%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           539.42 μs → 550.72 μs     (+2.09%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     74.74 μs →  75.30 μs     (+0.75%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   357.20 μs → 365.23 μs     (+2.25%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.58 μs →  20.14 μs     (-2.11%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        200.79 μs → 200.63 μs     (-0.08%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          37.26 ms →  37.06 ms     (-0.54%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                28.36 ms →  28.94 ms     (+2.05%)          22   →     22               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.50 μs →   2.75 μs     (+9.95%)          22   →     22               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.20 μs →   2.43 μs    (+10.61%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  410.31 μs → 408.41 μs     (-0.46%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         385.52 μs → 383.17 μs     (-0.61%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.84 ms →   2.83 ms     (-0.64%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               142.41 μs → 140.52 μs     (-1.33%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       24.50 ms →  25.23 ms     (+2.96%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            24.48 ms →  25.21 ms     (+2.98%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      3.86 ms →   4.08 ms     (+5.71%)          66   →     66               
+ │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       3.08 ms →   2.69 ms    (-12.49%)          66   →     66               
+ │ │ │ ├ sirius::Field4D::symmetrize                                       4.80 ms →   4.10 ms    (-14.60%)          22   →     22               
+ │ │ │ │ └ sirius::symmetrize_function|fpw                                 4.80 ms →   4.10 ms    (-14.60%)          22   →     22               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              1.49 ms → 786.36 μs    (-47.30%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.30 ms →   2.30 ms     (+0.03%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           980.05 μs → 985.44 μs     (+0.55%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.77 ms →   3.68 ms     (-2.47%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 333.51 μs → 341.97 μs     (+2.54%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                4.97 ms →   4.98 ms     (+0.20%)          22   →     22               
- │ │ │ ├ sirius::Density::mixer_input                                     21.89 μs →  24.98 μs    (+14.10%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 254.03 μs → 252.63 μs     (-0.55%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         252.34 μs → 250.23 μs     (-0.84%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                252.16 μs → 250.05 μs     (-0.83%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   190.87 μs → 196.16 μs     (+2.77%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               177.84 μs → 182.46 μs     (+2.60%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.57 ms →  14.72 ms     (+1.01%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        2.05 ms →   2.11 ms     (+3.31%)          22   →     22               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               569.10 μs → 208.62 μs    (-63.34%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               269.01 μs → 266.07 μs     (-1.09%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       262.36 μs → 264.64 μs     (+0.87%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              261.97 μs → 264.32 μs     (+0.90%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   10.59 μs →  10.70 μs     (+1.00%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.09 ms →   2.11 ms     (+0.88%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.03 ms →   2.05 ms     (+0.86%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             29.71 μs →  30.62 μs     (+3.07%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             201.40 μs → 200.20 μs     (-0.60%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 158.99 μs → 156.56 μs     (-1.53%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    10.19 ms →  10.26 ms     (+0.64%)          22   →     22               
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             144.86 ns → 176.14 ns    (+21.59%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.91 ms →   3.92 ms     (+0.38%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.91 ms →   3.92 ms     (+0.38%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              621.99 μs → 620.04 μs     (-0.31%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.30 ms →   2.31 ms     (+0.13%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             958.91 μs → 973.26 μs     (+1.50%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   236.92 μs → 240.95 μs     (+1.70%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   250.80 μs → 250.25 μs     (-0.22%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           247.87 μs → 248.03 μs     (+0.06%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  247.60 μs → 247.75 μs     (+0.06%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            263.42 μs → 258.95 μs     (-1.70%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    261.57 μs → 257.32 μs     (-1.62%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              242.15 μs → 239.08 μs     (-1.27%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 49.42 μs →  51.53 μs     (+4.28%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          47.62 μs →  49.69 μs     (+4.36%)          22   →     22               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                       192.90 μs → 188.59 μs     (-2.23%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     249.91 μs → 250.78 μs     (+0.35%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             245.64 μs → 247.45 μs     (+0.74%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    245.50 μs → 247.35 μs     (+0.75%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              260.15 μs → 250.96 μs     (-3.53%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      259.06 μs → 249.66 μs     (-3.63%)           3   →      3               
  ├ sirius::Stress|kin                                                    304.30 μs → 309.96 μs     (+1.86%)           1   →      1               
  ├ sirius::Stress|har                                                    576.99 μs → 578.37 μs     (+0.24%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.85 ms →   1.84 ms     (-0.97%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.66 ms →   3.64 ms     (-0.62%)           1   →      1               
- │ └ sirius::Simulation_context::make_periodic_function                    1.16 ms →   1.36 ms    (+17.29%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       215.72 μs → 214.44 μs     (-0.59%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      18.36 μs →  17.87 μs     (-2.68%)           1   →      1               
- ├ sirius::Simulation_context::make_periodic_function                      1.21 ms →   1.42 ms    (+17.13%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       244.56 μs → 249.81 μs     (+2.15%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               243.36 μs → 248.43 μs     (+2.08%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      243.13 μs → 248.30 μs     (+2.13%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                261.30 μs → 253.95 μs     (-2.81%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        260.04 μs → 252.58 μs     (-2.87%)           2   →      2               
  ├ sirius::Stress|us                                                     324.30 ms → 328.38 ms     (+1.26%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     196.34 μs → 193.56 μs     (-1.42%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             77.45 ms →  79.00 ms     (+2.00%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   605.76 μs → 587.06 μs     (-3.09%)           3   →      3               
- │ ├ sirius::Stress|us|phase_fac                                           1.23 ms →   1.58 ms    (+28.53%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.12 ms →  22.32 ms     (+0.90%)           9   →      9               
+ │ ├ sirius::Stress|us|prepare                                            69.96 μs →  57.56 μs    (-17.72%)          27   →     27               
+ │ └ sirius::Stress|us|gemm                                                1.41 ms →   1.22 ms    (-13.62%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.47 ms →  14.47 ms     (-0.03%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.83 ms →   5.94 ms     (+1.95%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.10 ms →   8.01 ms     (-1.13%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               342.23 μs → 329.79 μs     (-3.63%)          10   →     10               
- │   ├ sirius::Beta_projectors_base::prepare                               3.57 μs →   5.69 μs    (+59.32%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            271.09 μs → 274.12 μs     (+1.12%)           9   →      9               
  │   └ sirius::Beta_projectors_base::dismiss                              89.00 ns →  95.00 ns     (+6.74%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.21 ms →   1.21 ms     (-0.21%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          26.08 ms →  26.98 ms     (+3.44%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     248.04 μs → 250.78 μs     (+1.11%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.21 ms →   4.26 ms     (+1.00%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.98 ms →   2.96 ms     (-0.89%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               345.11 μs → 344.37 μs     (-0.21%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::prepare                               3.26 μs →   3.23 μs     (-1.07%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            280.32 μs → 269.44 μs     (-3.88%)           3   →      3               
  │   └ sirius::Beta_projectors_base::dismiss                              75.00 ns →  77.00 ns     (+2.67%)           1   →      1               
  ├ sirius::Force::calc_forces_core                                         1.18 ms →   1.15 ms     (-2.53%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     216.00 μs → 211.95 μs     (-1.88%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       14.50 ms →  15.77 ms     (+8.75%)           1   →      1               
  ├ sirius::Force::calc_forces_scf_corr                                   879.82 μs → 848.20 μs     (-3.59%)           1   →      1               
- ├ sirius::Force::hubbard_force                                          555.00 ns →   1.59 μs   (+187.39%)           1   →      1               
  └ sirius::finalize                                                      128.99 ms → 127.79 ms     (-0.94%)           1   →      1               
```
