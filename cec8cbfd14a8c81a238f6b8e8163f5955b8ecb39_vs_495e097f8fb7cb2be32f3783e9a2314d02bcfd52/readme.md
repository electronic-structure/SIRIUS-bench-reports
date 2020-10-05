# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 495e097f8fb7cb2be32f3783e9a2314d02bcfd52
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    8.34 s  →   7.81 s      (-6.39%)           1   →      1               
+ ├ sirius::initialize                                                      3.52 s  →   2.90 s     (-17.53%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  1.87 s  →   1.99 s      (+6.26%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               673.36 μs →  73.06 ms (+10749.89%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       215.62 ms → 255.59 ms    (+18.54%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            66.06 ms →  79.81 ms    (+20.82%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          17.41 ms →  16.13 ms     (-7.36%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      230.09 μs → 246.47 μs     (+7.12%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  17.18 ms →  15.88 ms     (-7.56%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     17.16 ms →  15.86 ms     (-7.59%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.95 ms →   4.94 ms     (-0.25%)           1   →      1               
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                             68.47 μs →  47.98 μs    (-29.92%)           1   →      1               
- │ │       └ sirius::Unit_cell_symmetry|mag                                9.60 μs →  10.66 μs    (+11.02%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (+0.32%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.08 ms →   5.15 ms     (+1.44%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       33.32 μs →  35.48 μs     (+6.51%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.04 ms →   5.11 ms     (+1.41%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.03 ms →   5.09 ms     (+1.37%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.90 ms →   5.00 ms     (+2.12%)           1   →      1               
+ │   │     ├ sirius::Unit_cell_symmetry|equiv                             65.15 μs →  41.38 μs    (-36.48%)           1   →      1               
+ │   │     └ sirius::Unit_cell_symmetry|mag                               12.31 μs →   8.40 μs    (-31.70%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      273.06 ms → 273.55 ms     (+0.18%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.31 ms →  21.42 ms     (+0.52%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.01 ms →  19.04 ms     (+0.19%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.46 ms →  80.35 ms     (-0.13%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.52 ms →  61.82 ms     (+0.49%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.51 ms →  97.03 ms     (+0.54%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.21 ms →   4.27 ms     (+1.48%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.96 ms →   2.99 ms     (+0.84%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.05 ms →   4.15 ms     (+2.67%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                277.45 μs → 294.38 μs     (+6.10%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  94.14 ms →  93.54 ms     (-0.64%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.89 ms →   5.93 ms     (+0.71%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            677.75 ns → 720.75 ns     (+6.34%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.82 ms →   5.85 ms     (+0.65%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.58 ms →   5.59 ms     (+0.24%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.57 ms →   4.57 ms     (-0.02%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              260.60 μs → 256.03 μs     (-1.75%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              2.65 μs →   2.91 μs     (+9.83%)           1   →      1               
  │     └ sirius::K_point::update                                         791.51 μs → 803.44 μs     (+1.51%)           1   →      1               
  │       └ sirius::Beta_projectors                                       649.70 μs → 660.36 μs     (+1.64%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                396.42 μs → 405.01 μs     (+2.17%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      250.60 μs → 251.47 μs     (+0.35%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       28.66 μs →  29.49 μs     (+2.88%)           2   →      2               
  ├ sirius::Potential                                                       2.15 ms →   2.22 ms     (+3.18%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     27.77 μs →  28.69 μs     (+3.28%)           6   →      6               
  │ └ sirius::Potential::update                                             1.89 ms →   1.96 ms     (+3.40%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.88 ms →   1.95 ms     (+3.39%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.46 ms →   1.53 ms     (+4.84%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 328.54 μs → 329.73 μs     (+0.36%)           1   →      1               
  ├ sirius::Density                                                         1.79 ms →   1.89 ms     (+5.67%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.19 μs →  28.31 μs     (+0.43%)           2   →      2               
  │ └ sirius::Density::update                                               1.73 ms →   1.83 ms     (+5.79%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.72 ms →   1.82 ms     (+5.80%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                19.11 μs →  20.34 μs     (+6.47%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.47 ms →   1.59 ms     (+7.65%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 212.93 μs → 198.10 μs     (-6.96%)           1   →      1               
  ├ sirius::Density::initial_density                                        3.05 ms →   3.06 ms     (+0.40%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    1.58 ms →   1.58 ms     (-0.21%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     240.75 μs → 252.79 μs     (+5.00%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                251.69 μs → 252.53 μs     (+0.33%)           1   →      1               
  ├ sirius::Potential::generate                                            23.56 ms →  21.79 ms     (-7.50%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            2.13 ms →   2.11 ms     (-0.72%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   198.65 μs → 193.15 μs     (-2.77%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   263.67 μs → 263.51 μs     (-0.06%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           260.51 μs → 260.73 μs     (+0.08%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.32 μs → 260.37 μs     (+0.02%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.38 μs →  10.80 μs     (+4.08%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.04 ms →   2.08 ms     (+1.81%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.00 ms →   2.04 ms     (+1.87%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 28.54 μs →  29.28 μs     (+2.61%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 203.65 μs → 201.83 μs     (-0.90%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     166.48 μs → 162.67 μs     (-2.29%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        19.18 ms →  17.39 ms     (-9.33%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                 167.00 ns → 200.00 ns    (+19.76%)           1   →      1               
- ├ sirius::Hamiltonian0                                                  350.05 μs → 395.55 μs    (+13.00%)           1   →      1               
- │ ├ sirius::Local_operator                                              325.53 μs → 370.24 μs    (+13.74%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   23.91 μs →  24.66 μs     (+3.15%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                   282.17 μs → 324.52 μs    (+15.01%)           1   →      1               
  │ ├ sirius::Non_local_operator                                          932.50 ns → 900.50 ns     (-3.43%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                        7.28 μs →   6.80 μs     (-6.62%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                        6.00 μs →   5.93 μs     (-1.15%)           1   →      1               
- ├ sirius::Band::initialize_subspace                                      44.73 ms →  49.81 ms    (+11.36%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.95 μs →  18.37 μs     (-3.08%)           1   →      1               
  │ │ └ sirius::Local_operator::prepare_k                                  17.90 μs →  16.79 μs     (-6.19%)           1   →      1               
- │ └ sirius::Band::initialize_subspace|kp                                 44.70 ms →  49.78 ms    (+11.36%)           1   →      1               
  │   ├ sddk::matrix_storage::matrix_storage                                5.10 μs →   5.46 μs     (+7.11%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   948.03 μs → 935.59 μs     (-1.31%)           1   →      1               
  │   ├ sirius::Band::initialize_subspace|kp|wf                            45.48 μs →  44.10 μs     (-3.04%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   18.22 ms →  18.08 ms     (-0.78%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.45 ms →   8.51 ms     (+0.77%)           1   →      1               
- │   │ │ ├ sddk::matrix_storage::remap_forward                             1.54 μs →   2.41 μs    (+56.43%)           1   →      1               
- │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.05 μs →   1.47 μs    (+39.05%)           1   →      1               
+ │   │ │ ├ sddk::matrix_storage::set_num_extra                           393.00 ns → 331.00 ns    (-15.78%)           1   →      1               
- │   │ │ └ sddk::matrix_storage::remap_backward                          433.00 ns → 548.00 ns    (+26.56%)           1   →      1               
- │   │ ├ sirius::Beta_projectors_base::inner                               4.36 ms →   5.00 ms    (+14.65%)           1   →      1               
+ │   │ └ sirius::Non_local_operator::apply                                 2.51 ms →   2.08 ms    (-16.92%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   275.72 μs → 279.65 μs     (+1.42%)           2   →      2               
  │   │ └ sddk::inner                                                     269.31 μs → 273.11 μs     (+1.41%)           2   →      2               
  │   │   └ sddk::inner|local                                             260.37 μs → 265.40 μs     (+1.93%)           2   →      2               
- │   ├ Eigensolver_lapack|zhegvx                                          24.49 ms →  29.67 ms    (+21.14%)           1   →      1               
  │   └ sddk::transform                                                   305.69 μs → 330.80 μs     (+8.21%)           1   →      1               
  │     ├ sddk::transform|init                                             71.62 μs →  70.66 μs     (-1.33%)           1   →      1               
  │     └ sddk::transform|local                                           225.22 μs → 246.83 μs     (+9.59%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.29 s  →   2.28 s      (-0.51%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     66.42 μs →  66.35 μs     (-0.10%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        103.26 ms → 102.55 ms     (-0.69%)          22   →     22               
  │ │ ├ sirius::Hamiltonian0                                              309.01 μs → 307.98 μs     (-0.33%)          22   →     22               
  │ │ │ ├ sirius::Local_operator                                          287.26 μs → 287.57 μs     (+0.11%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               29.68 μs →  30.57 μs     (+2.97%)          22   →     22               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               241.94 μs → 240.28 μs     (-0.68%)          22   →     22               
  │ │ │ ├ sirius::Non_local_operator                                      693.93 ns → 661.77 ns     (-4.63%)          44   →     44               
+ │ │ │ ├ sirius::D_operator::initialize                                    8.52 μs →   7.25 μs    (-14.87%)          22   →     22               
+ │ │ │ └ sirius::Q_operator::initialize                                    6.47 μs →   5.66 μs    (-12.49%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.54 ms →  37.54 ms     (+0.01%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            18.83 μs →  20.67 μs     (+9.73%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              18.14 μs →  19.43 μs     (+7.11%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.64 ms →  33.41 ms     (-0.68%)          22   →     22               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             11.27 μs →  12.97 μs    (+15.11%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        850.81 ns → 921.42 ns     (+8.30%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           707.66 μs → 704.60 μs     (-0.43%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.06 μs →  10.88 μs     (+8.18%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       221.34 μs → 219.32 μs     (-0.91%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.91 ms →  32.69 ms     (-0.69%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.18 ms →   5.15 ms     (-0.55%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.30 ms →   4.28 ms     (-0.37%)          87   →     87               
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.61 μs →   2.02 μs    (+25.84%)          87   →     87               
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.42 μs →   1.70 μs    (+19.78%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     527.62 ns → 507.13 ns     (-3.88%)          87   →     87               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    438.26 ns → 402.54 ns     (-8.15%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       287.59 μs → 280.77 μs     (-2.37%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         273.47 μs → 270.02 μs     (-1.26%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         890.21 μs → 881.91 μs     (-0.93%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               142.39 μs → 139.90 μs     (-1.75%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       141.03 μs → 138.37 μs     (-1.89%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  30.29 μs →  32.33 μs     (+6.72%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             252.01 μs → 250.27 μs     (-0.69%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           471.61 μs → 465.52 μs     (-1.29%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     75.94 μs →  76.56 μs     (+0.81%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   131.29 μs → 129.01 μs     (-1.74%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             214.10 μs → 208.34 μs     (-2.69%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               199.20 μs → 193.39 μs     (-2.91%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       198.20 μs → 192.40 μs     (-2.93%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   991.74 μs → 995.98 μs     (+0.43%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           579.45 μs → 572.61 μs     (-1.18%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           422.54 μs → 412.52 μs     (-2.37%)          68   →     69       (+1.47%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     66.91 μs →  64.53 μs     (-3.56%)          68   →     69       (+1.47%)
  │ │ │ │   │ │ └ sddk::transform|local                                   176.95 μs → 173.02 μs     (-2.22%)         136   →    138       (+1.47%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               301.12 μs → 291.59 μs     (-3.17%)          68   →     69       (+1.47%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     900.11 μs → 872.28 μs     (-3.09%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           543.21 μs → 527.64 μs     (-2.87%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     74.47 μs →  73.60 μs     (-1.16%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   360.41 μs → 349.11 μs     (-3.14%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.20 μs →  20.14 μs     (+4.88%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        195.46 μs → 198.58 μs     (+1.60%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          38.15 ms →  37.48 ms     (-1.75%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                30.14 ms →  29.09 ms     (-3.48%)          22   →     22               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             1.82 μs →   2.53 μs    (+39.23%)          22   →     22               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.65 μs →   2.17 μs    (+31.53%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  418.03 μs → 414.82 μs     (-0.77%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         394.71 μs → 389.91 μs     (-1.21%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.89 ms →   2.84 ms     (-1.56%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               141.24 μs → 140.22 μs     (-0.72%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       26.28 ms →  25.39 ms     (-3.39%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            26.27 ms →  25.38 ms     (-3.40%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      4.39 ms →   4.28 ms     (-2.43%)          66   →     66               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       2.78 ms →   2.52 ms     (-9.16%)          66   →     66               
  │ │ │ ├ sirius::Field4D::symmetrize                                       3.98 ms →   4.37 ms     (+9.64%)          22   →     22               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 3.98 ms →   4.37 ms     (+9.61%)          22   →     22               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                            661.69 μs →   1.05 ms    (+58.00%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.30 ms →   2.33 ms     (+1.35%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           999.42 μs → 966.89 μs     (-3.25%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.68 ms →   3.67 ms     (-0.12%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 342.60 μs → 342.59 μs     (-0.00%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                5.26 ms →   5.00 ms     (-5.08%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     24.25 μs →  23.72 μs     (-2.19%)          22   →     22               
+ │ │ │ ├ sirius::Periodic_function|inner                                 281.77 μs → 253.23 μs    (-10.13%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         270.83 μs → 250.13 μs     (-7.64%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                270.66 μs → 249.99 μs     (-7.64%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   189.61 μs → 194.77 μs     (+2.73%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               177.55 μs → 183.08 μs     (+3.11%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.73 ms →  14.92 ms     (+1.29%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        2.11 ms →   2.14 ms     (+1.22%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               204.55 μs → 204.43 μs     (-0.06%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               263.44 μs → 262.49 μs     (-0.36%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       261.93 μs → 261.02 μs     (-0.35%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              261.72 μs → 260.44 μs     (-0.49%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   10.52 μs →  10.51 μs     (-0.09%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.07 ms →   2.07 ms     (+0.17%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.01 ms →   2.01 ms     (+0.13%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             28.81 μs →  29.73 μs     (+3.18%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             201.30 μs → 205.23 μs     (+1.96%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 158.22 μs → 156.36 μs     (-1.18%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    10.31 ms →  10.47 ms     (+1.56%)          22   →     22               
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             161.68 ns → 201.82 ns    (+24.82%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.93 ms →   3.91 ms     (-0.47%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.93 ms →   3.91 ms     (-0.48%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              619.85 μs → 620.68 μs     (+0.13%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.30 ms →   2.29 ms     (-0.38%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             987.50 μs → 976.89 μs     (-1.07%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   234.24 μs → 238.26 μs     (+1.72%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   254.04 μs → 256.51 μs     (+0.97%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           250.70 μs → 252.21 μs     (+0.60%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  250.42 μs → 251.91 μs     (+0.59%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            261.17 μs → 261.40 μs     (+0.09%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    259.14 μs → 256.92 μs     (-0.85%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              239.69 μs → 261.42 μs     (+9.06%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 50.57 μs →  51.37 μs     (+1.59%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          49.15 μs →  49.67 μs     (+1.05%)          22   →     22               
- │ ├ sirius::Smooth_periodic_function::gather_f_pw                       198.30 μs → 233.61 μs    (+17.80%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     246.47 μs → 246.12 μs     (-0.14%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             244.22 μs → 243.05 μs     (-0.48%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    244.11 μs → 242.93 μs     (-0.48%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              260.65 μs → 261.09 μs     (+0.17%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      259.34 μs → 252.75 μs     (-2.54%)           3   →      3               
  ├ sirius::Stress|kin                                                    294.61 μs → 310.67 μs     (+5.45%)           1   →      1               
  ├ sirius::Stress|har                                                    584.05 μs → 584.25 μs     (+0.03%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.78 ms →   1.78 ms     (-0.05%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.67 ms →   3.60 ms     (-1.94%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    1.43 ms →   1.39 ms     (-2.48%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       212.56 μs → 218.76 μs     (+2.92%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      18.96 μs →  19.57 μs     (+3.21%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      1.44 ms →   1.47 ms     (+2.55%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       248.23 μs → 253.73 μs     (+2.21%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               247.03 μs → 245.67 μs     (-0.55%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      246.88 μs → 245.53 μs     (-0.55%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                253.85 μs → 254.37 μs     (+0.21%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        252.77 μs → 252.43 μs     (-0.13%)           2   →      2               
  ├ sirius::Stress|us                                                     330.40 ms → 329.90 ms     (-0.15%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     191.28 μs → 222.86 μs    (+16.51%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             78.14 ms →  77.15 ms     (-1.26%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   653.90 μs → 613.75 μs     (-6.14%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           1.59 ms →   1.61 ms     (+1.80%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.34 ms →  23.61 ms     (+5.66%)           9   →      9               
+ │ ├ sirius::Stress|us|prepare                                            68.06 μs →  52.70 μs    (-22.57%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                1.21 ms →   1.18 ms     (-2.38%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.78 ms →  14.41 ms     (-2.53%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.86 ms →   5.74 ms     (-2.11%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.02 ms →   8.04 ms     (+0.24%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               329.25 μs → 332.92 μs     (+1.12%)          10   →     10               
- │   ├ sirius::Beta_projectors_base::prepare                               3.66 μs →   4.14 μs    (+12.94%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            275.03 μs → 273.82 μs     (-0.44%)           9   →      9               
  │   └ sirius::Beta_projectors_base::dismiss                              88.00 ns →  91.00 ns     (+3.41%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.27 ms →   1.30 ms     (+2.10%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          26.96 ms →  26.57 ms     (-1.47%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     244.74 μs → 255.05 μs     (+4.21%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.26 ms →   4.14 ms     (-2.85%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.93 ms →   2.99 ms     (+2.05%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               338.30 μs → 341.77 μs     (+1.03%)           4   →      4               
- │   ├ sirius::Beta_projectors_base::prepare                               3.08 μs →   3.58 μs    (+15.92%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            271.27 μs → 284.71 μs     (+4.95%)           3   →      3               
+ │   └ sirius::Beta_projectors_base::dismiss                              84.00 ns →  68.00 ns    (-19.05%)           1   →      1               
  ├ sirius::Force::calc_forces_core                                         1.17 ms →   1.14 ms     (-2.79%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     210.18 μs → 211.32 μs     (+0.54%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       14.61 ms →  15.84 ms     (+8.38%)           1   →      1               
  ├ sirius::Force::calc_forces_scf_corr                                   829.81 μs → 835.69 μs     (+0.71%)           1   →      1               
  ├ sirius::Force::hubbard_force                                            1.75 μs →   1.66 μs     (-5.36%)           1   →      1               
  └ sirius::finalize                                                      125.86 ms → 124.87 ms     (-0.79%)           1   →      1               
```
