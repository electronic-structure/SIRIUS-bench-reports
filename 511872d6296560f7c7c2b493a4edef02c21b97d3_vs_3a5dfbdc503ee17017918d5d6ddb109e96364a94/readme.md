# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                    8.98 s  →   7.72 s     (-13.98%)           1   →      1               
+ ├ sirius::initialize                                                      3.52 s  →   2.91 s     (-17.45%)           1   →      1               
+ ├ sirius::Simulation_context::initialize                                  2.41 s  →   1.88 s     (-21.85%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               851.39 μs →   5.01 ms   (+488.86%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       748.37 ms → 215.51 ms    (-71.20%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                           245.09 ms →  66.43 ms    (-72.90%)           3   →      3               
- │ │ └ sirius::Unit_cell::update                                          13.07 ms →  16.20 ms    (+23.95%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      250.15 μs → 238.95 μs     (-4.48%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  12.82 ms →  15.96 ms    (+24.51%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     12.79 ms →  15.93 ms    (+24.48%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.95 ms →   5.03 ms     (+1.61%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                             57.25 μs →  57.33 μs     (+0.14%)           1   →      1               
- │ │       └ sirius::Unit_cell_symmetry|mag                               11.74 μs →  17.07 μs    (+45.42%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (+0.19%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.20 ms →   5.16 ms     (-0.88%)           1   →      1               
- │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       32.31 μs →  35.74 μs    (+10.61%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.17 ms →   5.12 ms     (-0.96%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.15 ms →   5.10 ms     (-1.03%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                5.06 ms →   5.00 ms     (-1.11%)           1   →      1               
+ │   │     ├ sirius::Unit_cell_symmetry|equiv                             48.47 μs →  43.44 μs    (-10.39%)           1   →      1               
- │   │     └ sirius::Unit_cell_symmetry|mag                                8.58 μs →  15.65 μs    (+82.37%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      274.19 ms → 272.49 ms     (-0.62%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.28 ms →  21.80 ms     (+2.43%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.05 ms →  19.04 ms     (-0.07%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.26 ms →  80.38 ms     (+0.15%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.63 ms →  61.76 ms     (+0.21%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.72 ms →  96.99 ms     (+0.28%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.24 ms →   4.25 ms     (+0.25%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.96 ms →   2.99 ms     (+1.19%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.41 ms →   4.06 ms     (-7.87%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                282.96 μs → 305.27 μs     (+7.89%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  93.59 ms →  95.15 ms     (+1.67%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.85 ms →   5.84 ms     (-0.20%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            745.00 ns → 764.50 ns     (+2.62%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.78 ms →   5.77 ms     (-0.18%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.53 ms →   5.52 ms     (-0.22%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.50 ms →   4.51 ms     (+0.09%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              248.30 μs → 245.31 μs     (-1.21%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              2.92 μs →   2.75 μs     (-5.76%)           1   →      1               
  │     └ sirius::K_point::update                                         806.32 μs → 789.28 μs     (-2.11%)           1   →      1               
  │       └ sirius::Beta_projectors                                       662.12 μs → 647.96 μs     (-2.14%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                399.22 μs → 395.99 μs     (-0.81%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      258.98 μs → 248.01 μs     (-4.23%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       28.36 μs →  29.08 μs     (+2.53%)           2   →      2               
  ├ sirius::Potential                                                       2.09 ms →   2.13 ms     (+1.64%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.34 μs →  28.03 μs     (-1.07%)           6   →      6               
  │ └ sirius::Potential::update                                             1.83 ms →   1.87 ms     (+1.91%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.82 ms →   1.85 ms     (+1.91%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.17 ms →   1.22 ms     (+4.09%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 567.34 μs → 544.51 μs     (-4.03%)           1   →      1               
  ├ sirius::Density                                                         1.79 ms →   1.84 ms     (+3.13%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.15 μs →  28.78 μs     (+2.27%)           2   →      2               
  │ └ sirius::Density::update                                               1.73 ms →   1.78 ms     (+3.16%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.71 ms →   1.77 ms     (+3.14%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                20.60 μs →  20.46 μs     (-0.70%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.15 ms →   1.22 ms     (+6.18%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 534.80 μs → 517.73 μs     (-3.19%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.90 ms →   2.92 ms     (+0.74%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    1.16 ms →   1.22 ms     (+4.55%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     373.18 μs → 354.89 μs     (-4.90%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                258.84 μs → 253.88 μs     (-1.92%)           1   →      1               
  ├ sirius::Potential::generate                                            21.63 ms →  21.64 ms     (+0.01%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            2.10 ms →   2.05 ms     (-2.50%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   666.49 μs → 532.10 μs    (-20.16%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   262.49 μs → 269.57 μs     (+2.70%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           249.77 μs → 260.72 μs     (+4.38%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  249.49 μs → 260.38 μs     (+4.37%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.31 μs →  10.67 μs     (+3.46%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.06 ms →   2.06 ms     (-0.00%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.02 ms →   2.02 ms     (-0.34%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.34 μs →  29.54 μs     (+0.65%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 203.07 μs → 203.17 μs     (+0.05%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     159.36 μs → 164.99 μs     (+3.54%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        17.26 ms →  17.31 ms     (+0.28%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 212.00 ns → 139.00 ns    (-34.43%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  391.46 μs → 381.87 μs     (-2.45%)           1   →      1               
  │ ├ sirius::Local_operator                                              366.36 μs → 355.78 μs     (-2.89%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function                                   29.74 μs →  35.02 μs    (+17.75%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   316.07 μs → 299.83 μs     (-5.14%)           1   →      1               
  │ ├ sirius::Non_local_operator                                          937.00 ns → 897.50 ns     (-4.22%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                        7.09 μs →   7.19 μs     (+1.43%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                        5.56 μs →   5.54 μs     (-0.25%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      49.30 ms →  50.03 ms     (+1.48%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                13.93 μs →  14.33 μs     (+2.90%)           1   →      1               
  │ │ └ sirius::Local_operator::prepare_k                                  12.57 μs →  13.10 μs     (+4.17%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 49.28 ms →  50.01 ms     (+1.48%)           1   →      1               
+ │   ├ sddk::matrix_storage::matrix_storage                                7.55 μs →   5.54 μs    (-26.55%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   917.17 μs → 926.90 μs     (+1.06%)           1   →      1               
- │   ├ sirius::Band::initialize_subspace|kp|wf                            42.74 μs →  54.56 μs    (+27.67%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   18.00 ms →  17.85 ms     (-0.88%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.43 ms →   8.43 ms     (+0.06%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::remap_forward                             2.21 μs →   2.34 μs     (+6.06%)           1   →      1               
  │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.36 μs →   1.48 μs     (+8.98%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           374.00 ns → 382.00 ns     (+2.14%)           1   →      1               
- │   │ │ └ sddk::matrix_storage::remap_backward                          470.00 ns → 523.00 ns    (+11.28%)           1   →      1               
- │   │ ├ sirius::Beta_projectors_base::inner                               5.21 ms →   5.86 ms    (+12.55%)           1   →      1               
+ │   │ └ sirius::Non_local_operator::apply                                 1.98 ms →   1.57 ms    (-20.62%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   284.72 μs → 294.55 μs     (+3.45%)           2   →      2               
  │   │ └ sddk::inner                                                     277.82 μs → 287.95 μs     (+3.65%)           2   →      2               
  │   │   └ sddk::inner|local                                             270.40 μs → 280.03 μs     (+3.56%)           2   →      2               
  │   ├ Eigensolver_lapack|zhegvx                                          29.27 ms →  30.11 ms     (+2.88%)           1   →      1               
  │   └ sddk::transform                                                   312.09 μs → 320.75 μs     (+2.78%)           1   →      1               
  │     ├ sddk::transform|init                                             64.39 μs →  65.90 μs     (+2.34%)           1   →      1               
  │     └ sddk::transform|local                                           236.37 μs → 242.75 μs     (+2.70%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.30 s  →   2.29 s      (-0.49%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     69.89 μs →  65.69 μs     (-6.01%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        102.73 ms → 102.24 ms     (-0.48%)          22   →     22               
  │ │ ├ sirius::Hamiltonian0                                              333.85 μs → 327.36 μs     (-1.94%)          22   →     22               
  │ │ │ ├ sirius::Local_operator                                          313.31 μs → 306.45 μs     (-2.19%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               33.17 μs →  31.42 μs     (-5.27%)          22   →     22               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               262.93 μs → 258.75 μs     (-1.59%)          22   →     22               
  │ │ │ ├ sirius::Non_local_operator                                      827.20 ns → 869.66 ns     (+5.13%)          44   →     44               
  │ │ │ ├ sirius::D_operator::initialize                                    7.15 μs →   7.34 μs     (+2.65%)          22   →     22               
  │ │ │ └ sirius::Q_operator::initialize                                    5.57 μs →   5.50 μs     (-1.21%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                38.01 ms →  38.06 ms     (+0.14%)          22   →     22               
- │ │ │ ├ sirius::Hamiltonian_k                                            17.88 μs →  19.75 μs    (+10.46%)          22   →     22               
- │ │ │ │ └ sirius::Local_operator::prepare_k                              16.57 μs →  18.81 μs    (+13.50%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.77 ms →  33.82 ms     (+0.14%)          22   →     22               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             13.58 μs →  12.66 μs     (-6.75%)          22   →     22               
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          1.05 μs → 906.37 ns    (-13.37%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           696.15 μs → 708.10 μs     (+1.72%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.58 μs →  10.53 μs     (-0.48%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       216.67 μs → 220.84 μs     (+1.92%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              33.05 ms →  33.09 ms     (+0.11%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.18 ms →   5.17 ms     (-0.08%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.29 ms →   4.28 ms     (-0.23%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.05 μs →   2.05 μs     (-0.39%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.78 μs →   1.77 μs     (-0.21%)          87   →     87               
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     629.89 ns → 531.86 ns    (-15.56%)          87   →     87               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    421.28 ns → 472.41 ns    (+12.14%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       280.77 μs → 283.48 μs     (+0.97%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         277.24 μs → 278.26 μs     (+0.37%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         908.53 μs → 911.77 μs     (+0.36%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               143.83 μs → 144.31 μs     (+0.33%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       142.27 μs → 142.60 μs     (+0.23%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  33.56 μs →  32.83 μs     (-2.16%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             257.57 μs → 258.15 μs     (+0.23%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           480.00 μs → 483.45 μs     (+0.72%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     77.44 μs →  78.02 μs     (+0.75%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   133.52 μs → 134.46 μs     (+0.71%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             213.94 μs → 216.53 μs     (+1.21%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               198.69 μs → 201.08 μs     (+1.20%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       197.62 μs → 200.04 μs     (+1.23%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                     1.01 ms →   1.01 ms     (+0.14%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           588.61 μs → 591.84 μs     (+0.55%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           429.96 μs → 434.93 μs     (+1.15%)          68   →     68               
  │ │ │ │   │ │ ├ sddk::transform|init                                     66.63 μs →  67.02 μs     (+0.59%)          68   →     68               
  │ │ │ │   │ │ └ sddk::transform|local                                   180.77 μs → 182.96 μs     (+1.21%)         136   →    136               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               304.21 μs → 303.39 μs     (-0.27%)          68   →     68               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     891.25 μs → 893.78 μs     (+0.28%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           542.46 μs → 541.61 μs     (-0.16%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     76.24 μs →  74.62 μs     (-2.12%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   358.41 μs → 358.87 μs     (+0.13%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.50 μs →  20.71 μs     (+1.04%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        204.79 μs → 214.06 μs     (+4.53%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          37.41 ms →  37.16 ms     (-0.65%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                28.01 ms →  27.86 ms     (-0.54%)          22   →     22               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.42 μs →   2.69 μs    (+11.05%)          22   →     22               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.11 μs →   2.35 μs    (+11.26%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  419.42 μs → 419.12 μs     (-0.07%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         393.88 μs → 393.36 μs     (-0.13%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.83 ms →   2.85 ms     (+0.68%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               141.77 μs → 141.40 μs     (-0.26%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       24.02 ms →  23.92 ms     (-0.40%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            24.00 ms →  23.90 ms     (-0.40%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      3.62 ms →   3.61 ms     (-0.46%)          66   →     66               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       3.20 ms →   3.14 ms     (-1.76%)          66   →     66               
  │ │ │ ├ sirius::Field4D::symmetrize                                       5.36 ms →   5.28 ms     (-1.35%)          22   →     22               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 5.36 ms →   5.28 ms     (-1.35%)          22   →     22               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              1.99 ms →   1.98 ms     (-0.57%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.38 ms →   2.31 ms     (-2.79%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           961.62 μs → 966.89 μs     (+0.55%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.70 ms →   3.67 ms     (-0.80%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 334.13 μs → 347.54 μs     (+4.02%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                5.11 ms →   4.99 ms     (-2.44%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     24.34 μs →  24.10 μs     (-0.98%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 263.59 μs → 255.77 μs     (-2.97%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         261.33 μs → 250.91 μs     (-3.99%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                261.17 μs → 250.73 μs     (-3.99%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   190.74 μs → 194.08 μs     (+1.75%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               178.87 μs → 181.71 μs     (+1.59%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.46 ms →  14.44 ms     (-0.11%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        2.05 ms →   2.02 ms     (-1.28%)          22   →     22               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               634.64 μs → 558.29 μs    (-12.03%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               254.85 μs → 268.06 μs     (+5.18%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       250.20 μs → 263.58 μs     (+5.35%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              249.85 μs → 263.27 μs     (+5.37%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   10.87 μs →  10.81 μs     (-0.59%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.13 ms →   2.14 ms     (+0.44%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.07 ms →   2.08 ms     (+0.40%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             30.10 μs →  30.87 μs     (+2.54%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             201.10 μs → 200.66 μs     (-0.22%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 158.03 μs → 161.45 μs     (+2.16%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    10.04 ms →  10.04 ms     (-0.06%)          22   →     22               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             215.27 ns → 155.18 ns    (-27.91%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.98 ms →   3.91 ms     (-1.81%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.98 ms →   3.91 ms     (-1.81%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              622.52 μs → 626.99 μs     (+0.72%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.38 ms →   2.29 ms     (-3.73%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             955.20 μs → 967.48 μs     (+1.29%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   250.94 μs → 241.88 μs     (-3.61%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   264.69 μs → 250.12 μs     (-5.50%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           257.99 μs → 247.36 μs     (-4.12%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  257.73 μs → 247.08 μs     (-4.13%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            251.17 μs → 259.52 μs     (+3.33%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    245.42 μs → 256.77 μs     (+4.62%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              241.61 μs → 238.70 μs     (-1.20%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 51.24 μs →  51.20 μs     (-0.07%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          49.38 μs →  49.28 μs     (-0.21%)          22   →     22               
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                       247.35 μs → 196.05 μs    (-20.74%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     258.35 μs → 249.85 μs     (-3.29%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             256.21 μs → 247.25 μs     (-3.50%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    256.09 μs → 247.13 μs     (-3.50%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              252.91 μs → 255.66 μs     (+1.09%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      252.06 μs → 253.61 μs     (+0.61%)           3   →      3               
  ├ sirius::Stress|kin                                                    310.13 μs → 312.64 μs     (+0.81%)           1   →      1               
  ├ sirius::Stress|har                                                    610.20 μs → 580.30 μs     (-4.90%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.77 ms →   1.79 ms     (+1.36%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.53 ms →   3.50 ms     (-0.81%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    1.11 ms →   1.15 ms     (+3.69%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       216.52 μs → 212.91 μs     (-1.66%)           1   →      1               
+ ├ sirius::rho_core_ri_pseudo|values                                      22.94 μs →  19.17 μs    (-16.45%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      1.16 ms →   1.20 ms     (+3.31%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       256.46 μs → 256.73 μs     (+0.11%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               254.73 μs → 252.76 μs     (-0.77%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      254.52 μs → 252.59 μs     (-0.76%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                253.77 μs → 263.64 μs     (+3.89%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        251.46 μs → 253.15 μs     (+0.67%)           2   →      2               
  ├ sirius::Stress|us                                                     323.51 ms → 334.07 ms     (+3.27%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     194.05 μs → 197.29 μs     (+1.67%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             77.16 ms →  78.47 ms     (+1.69%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   633.74 μs → 582.13 μs     (-8.14%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           1.18 ms →   1.20 ms     (+1.32%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.09 ms →  23.92 ms     (+8.31%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                            71.82 μs →  70.24 μs     (-2.19%)          27   →     27               
+ │ └ sirius::Stress|us|gemm                                                1.45 ms →   1.21 ms    (-16.27%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.57 ms →  14.70 ms     (+0.91%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.70 ms →   5.85 ms     (+2.64%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.19 ms →   8.05 ms     (-1.71%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               342.20 μs → 333.93 μs     (-2.42%)          10   →     10               
+ │   ├ sirius::Beta_projectors_base::prepare                               5.12 μs →   3.60 μs    (-29.67%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            279.92 μs → 275.17 μs     (-1.70%)           9   →      9               
  │   └ sirius::Beta_projectors_base::dismiss                              87.00 ns →  82.00 ns     (-5.75%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.26 ms →   1.20 ms     (-5.27%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          26.21 ms →  26.27 ms     (+0.23%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     245.91 μs → 247.56 μs     (+0.67%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.16 ms →   4.24 ms     (+1.97%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.98 ms →   2.95 ms     (-1.06%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               342.60 μs → 345.71 μs     (+0.91%)           4   →      4               
+ │   ├ sirius::Beta_projectors_base::prepare                               3.56 μs →   3.12 μs    (-12.23%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            284.10 μs → 270.74 μs     (-4.70%)           3   →      3               
- │   └ sirius::Beta_projectors_base::dismiss                              40.00 ns →  64.00 ns    (+60.00%)           1   →      1               
  ├ sirius::Force::calc_forces_core                                         1.18 ms →   1.16 ms     (-1.64%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     211.82 μs → 209.90 μs     (-0.91%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       15.51 ms →  15.71 ms     (+1.29%)           1   →      1               
- ├ sirius::Force::calc_forces_scf_corr                                   736.07 μs → 868.99 μs    (+18.06%)           1   →      1               
- ├ sirius::Force::hubbard_force                                          584.00 ns →   1.29 μs   (+120.38%)           1   →      1               
  └ sirius::finalize                                                      123.49 ms → 128.40 ms     (+3.98%)           1   →      1               
```
