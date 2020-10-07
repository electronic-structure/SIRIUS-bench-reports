# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  133.52 s  → 124.81 s      (-6.53%)           1   →      1               
  ├ sirius::initialize                                                      2.78 s  →   2.91 s      (+4.75%)           1   →      1               
+ ├ sirius::Simulation_context::initialize                                  3.40 s  →   2.93 s     (-13.96%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                41.86 ms → 246.49 μs    (-99.41%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       557.09 ms → 192.74 ms    (-65.40%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                           266.14 ms →  84.06 ms    (-68.42%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          24.73 ms →  24.54 ms     (-0.79%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.24 ms →   6.29 ms     (+0.86%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  18.46 ms →  18.20 ms     (-1.37%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     18.43 ms →  18.18 ms     (-1.37%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.16 ms →   4.16 ms     (+0.00%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.36 ms →   2.34 ms     (-0.89%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              101.44 μs → 106.54 μs     (+5.02%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.76 s  →   2.69 s      (-2.45%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.76 ms →  10.79 ms     (+0.23%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.38 ms →   4.38 ms     (+0.13%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.36 ms →   6.37 ms     (+0.28%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.34 ms →   6.35 ms     (+0.27%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.84 ms →   3.84 ms     (+0.10%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.33 ms →   2.34 ms     (+0.40%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               99.50 μs → 103.96 μs     (+4.49%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       62.74 ms →  63.76 ms     (+1.63%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.15 ms →   5.15 ms     (-0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.47 ms →   4.46 ms     (-0.03%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.75 ms →  21.76 ms     (+0.01%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.80 ms →  14.81 ms     (+0.05%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.34 ms →  19.89 ms     (+2.81%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  173.53 ms → 174.08 ms     (+0.32%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    130.68 ms → 131.29 ms     (+0.46%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 178.34 ms → 184.65 ms     (+3.54%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.32 ms →   1.33 ms     (+0.34%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 299.23 ms → 293.80 ms     (-1.81%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     35.58 ms →  35.43 ms     (-0.41%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              2.79 μs →   2.69 μs     (-3.48%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      35.48 ms →  35.34 ms     (-0.41%)           1   →      1               
  │   └ sirius::K_point::initialize                                        35.39 ms →  35.25 ms     (-0.41%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.16 ms →  18.10 ms     (-0.35%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.22 ms →   8.17 ms     (-0.66%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              9.66 μs →  10.23 μs     (+5.86%)           1   →      1               
  │     └ sirius::K_point::update                                          12.44 ms →  12.34 ms     (-0.77%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.14 ms →   6.07 ms     (-1.17%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.52 ms →   3.49 ms     (-0.79%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.26 ms →   5.23 ms     (-0.41%)           2   →      2               
  ├ sirius::Potential                                                     159.69 ms → 159.79 ms     (+0.07%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.92 ms →   5.77 ms     (-2.59%)           6   →      6               
  │ └ sirius::Potential::update                                           123.39 ms → 124.45 ms     (+0.86%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       122.60 ms → 123.74 ms     (+0.93%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.35 ms → 110.86 ms     (-0.44%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                  10.33 ms →  12.00 ms    (+16.15%)           1   →      1               
  ├ sirius::Density                                                       136.04 ms → 131.40 ms     (-3.42%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.24 ms →   5.21 ms     (-0.57%)           2   →      2               
  │ └ sirius::Density::update                                             125.28 ms → 120.70 ms     (-3.66%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              124.85 ms → 120.25 ms     (-3.69%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               103.47 μs → 102.42 μs     (-1.02%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.93 ms → 111.13 ms     (-0.72%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  12.34 ms →   8.57 ms    (-30.55%)           1   →      1               
  ├ sirius::Density::initial_density                                      176.42 ms → 174.49 ms     (-1.09%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  111.06 ms → 111.19 ms     (+0.12%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                      11.11 ms →  10.69 ms     (-3.77%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                 10.30 ms →   9.88 ms     (-4.14%)           1   →      1               
  ├ sirius::Potential::generate                                           608.05 ms → 605.79 ms     (-0.37%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          138.18 ms → 140.43 ms     (+1.63%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                    17.73 ms →  20.23 ms    (+14.08%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.51 ms →  10.29 ms     (-2.12%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.24 ms →  10.23 ms     (-0.11%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.23 ms →  10.22 ms     (-0.11%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      565.26 μs → 557.47 μs     (-1.38%)           2   →      2               
  │ ├ sirius::Potential::xc                                                56.87 ms →  53.47 ms     (-5.98%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               54.40 ms →  51.19 ms     (-5.89%)           1   →      1               
+ │ │   ├ sirius::Smooth_periodic_function                                  6.33 ms →   5.64 ms    (-10.91%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.24 ms →   5.21 ms     (-0.54%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.86 ms →   6.06 ms     (+3.39%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        93.64 ms →  93.58 ms     (-0.06%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 310.95 ms → 309.77 ms     (-0.38%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.68 ms →   8.39 ms     (-3.35%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.32 ms →   8.04 ms     (-3.38%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    5.09 ms →   4.71 ms     (-7.38%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.33 ms →   2.40 ms     (+2.75%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           63.63 μs →  63.30 μs     (-0.52%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       99.37 μs →  93.62 μs     (-5.79%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       74.89 μs →  76.47 μs     (+2.11%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.86 s  →   1.86 s      (-0.01%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.68 ms →  18.71 ms     (+0.18%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 174.93 μs → 197.48 μs    (+12.89%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.50 ms →  18.51 ms     (+0.06%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.84 s  →   1.84 s      (-0.01%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              126.91 ms → 129.02 ms     (+1.66%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    53.40 ms →  53.26 ms     (-0.25%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.59 ms →  21.61 ms     (+0.08%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  636.85 ms → 636.97 ms     (+0.02%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 297.77 ms → 297.89 ms     (+0.04%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.06 μs →   3.64 μs    (+18.93%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.13 μs →   2.65 μs    (+24.18%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           423.00 ns → 381.00 ns     (-9.93%)           1   →      1               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          590.00 ns → 562.00 ns     (-4.75%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.21 ms →   9.23 ms     (+0.17%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             121.44 ms → 121.46 ms     (+0.01%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               104.19 ms → 104.18 ms     (-0.01%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    38.42 ms →  38.44 ms     (+0.06%)           2   →      2               
  │ │ │ └ sddk::inner                                                      37.88 ms →  37.87 ms     (-0.02%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              25.09 μs →  24.02 μs     (-4.27%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           56.82 ms →  56.85 ms     (+0.05%)           1   →      1               
  │ │ └ sddk::transform                                                    31.56 ms →  31.53 ms     (-0.09%)           1   →      1               
  │ │   ├ sddk::transform|init                                             12.12 μs →  11.17 μs     (-7.87%)           1   →      1               
  │ │   └ sddk::transform|local                                            12.24 μs →  11.72 μs     (-4.28%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               683.00 ns → 585.00 ns    (-14.35%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    123.28 s  → 114.98 s      (-6.73%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.89 ms →   5.72 ms     (-2.88%)          19   →     19               
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.72 s  →   4.98 s      (+5.65%)          26   →     23      (-11.54%)
- │ │ ├ sirius::Hamiltonian0                                                4.99 ms →   6.08 ms    (+21.84%)          26   →     23      (-11.54%)
- │ │ │ ├ sirius::Local_operator                                            4.62 ms →   5.71 ms    (+23.48%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Smooth_periodic_function                              967.67 μs → 956.44 μs     (-1.16%)          26   →     23      (-11.54%)
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.76 ms →   3.86 ms    (+39.67%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Non_local_operator                                       64.48 μs →  64.71 μs     (+0.35%)          52   →     46      (-11.54%)
! │ │ │ ├ sirius::D_operator::initialize                                   92.60 μs →  91.82 μs     (-0.84%)          26   →     23      (-11.54%)
! │ │ │ └ sirius::Q_operator::initialize                                   74.90 μs →  76.95 μs     (+2.73%)          26   →     23      (-11.54%)
! │ │ ├ sirius::Band::solve                                                 2.73 s  →   3.00 s      (+9.99%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Hamiltonian_k                                           167.01 μs → 163.16 μs     (-2.31%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Local_operator::prepare_k                             161.51 μs → 156.17 μs     (-3.31%)          26   →     23      (-11.54%)
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           3.85 μs →   5.34 μs    (+38.60%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.61 s  →   2.80 s      (+7.45%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             96.23 ms → 102.49 ms     (+6.51%)          26   →     23      (-11.54%)
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.59 ms →   8.71 ms    (+14.86%)         156   →    138      (-11.54%)
! │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             5.98 ms →   5.99 ms     (+0.18%)          26   →     23      (-11.54%)
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       349.19 μs → 348.47 μs     (-0.21%)          26   →     23      (-11.54%)
! │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.31 ms →   2.32 ms     (+0.28%)          52   →     46      (-11.54%)
! │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.47 s  →   2.66 s      (+7.61%)          26   →     23      (-11.54%)
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            125.74 ms → 125.43 ms     (-0.25%)         283   →    268       (-5.30%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            49.75 ms →  49.83 ms     (+0.16%)         283   →    268       (-5.30%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.88 μs →   1.96 μs     (+4.02%)         283   →    268       (-5.30%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.57 μs →   1.57 μs     (-0.12%)         283   →    268       (-5.30%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     293.76 ns → 285.81 ns     (-2.71%)         283   →    268       (-5.30%)
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    461.18 ns → 442.37 ns     (-4.08%)         283   →    268       (-5.30%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.41 ms →   7.41 ms     (-0.01%)         283   →    268       (-5.30%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        23.23 ms →  22.91 ms     (-1.38%)         283   →    268       (-5.30%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          22.67 ms →  22.63 ms     (-0.15%)         566   →    536       (-5.30%)
  │ │ │ │   ├ sddk::orthogonalize                                          31.74 ms →  32.43 ms     (+2.16%)         283   →    268       (-5.30%)
  │ │ │ │   │ ├ sddk::inner                                                 4.69 ms →   4.76 ms     (+1.48%)         540   →    513       (-5.00%)
  │ │ │ │   │ │ └ sddk::inner|local                                        20.74 μs →  22.02 μs     (+6.15%)         540   →    513       (-5.00%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 595.70 μs → 591.74 μs     (-0.67%)         283   →    268       (-5.30%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.35 ms →   9.29 ms     (-0.60%)         283   →    268       (-5.30%)
  │ │ │ │   │ └ sddk::transform                                            14.15 ms →  14.70 ms     (+3.86%)         257   →    245       (-4.67%)
  │ │ │ │   │   ├ sddk::transform|init                                     17.64 μs →  18.83 μs     (+6.72%)         257   →    245       (-4.67%)
  │ │ │ │   │   └ sddk::transform|local                                     6.73 μs →   6.96 μs     (+3.36%)         771   →    735       (-4.67%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               8.93 ms →   9.08 ms     (+1.75%)         283   →    268       (-5.30%)
  │ │ │ │   │ └ sddk::inner                                                 8.68 ms →   8.84 ms     (+1.77%)         283   →    268       (-5.30%)
  │ │ │ │   │   └ sddk::inner|local                                        20.90 μs →  21.84 μs     (+4.48%)         283   →    268       (-5.30%)
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     33.45 ms →  33.42 ms     (-0.07%)         283   →    268       (-5.30%)
  │ │ │ │   ├ sirius::residuals                                            13.41 ms →  13.62 ms     (+1.59%)         274   →    259       (-5.47%)
  │ │ │ │   │ ├ sddk::transform                                            12.12 ms →  12.30 ms     (+1.49%)         264   →    250       (-5.30%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     13.46 μs →  13.62 μs     (+1.18%)         264   →    250       (-5.30%)
  │ │ │ │   │ │ └ sddk::transform|local                                     9.07 μs →   9.31 μs     (+2.62%)         528   →    500       (-5.30%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.56 ms →   1.57 ms     (+0.98%)         264   →    250       (-5.30%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      76.25 ms →  79.23 ms     (+3.91%)          53   →     50       (-5.66%)
  │ │ │ │     └ sddk::transform                                            50.28 ms →  51.21 ms     (+1.85%)          80   →     77       (-3.75%)
  │ │ │ │       ├ sddk::transform|init                                      9.73 μs →   9.53 μs     (-1.98%)          80   →     77       (-3.75%)
  │ │ │ │       └ sddk::transform|local                                     8.61 μs →   8.40 μs     (-2.43%)         107   →    104       (-2.80%)
! │ │ │ ├ sirius::Beta_projectors_base::dismiss                           418.12 ns → 453.39 ns     (+8.44%)          26   →     23      (-11.54%)
- │ │ │ └ sirius::K_point_set::sync_band_energies                          29.08 μs →  65.58 μs   (+125.56%)          26   →     23      (-11.54%)
! │ │ ├ sirius::K_point_set::find_band_occupancies                        601.57 μs → 617.22 μs     (+2.60%)          26   →     23      (-11.54%)
! │ │ ├ sirius::Density::generate                                         766.54 ms → 780.00 ms     (+1.76%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Density::generate_valence                               402.75 ms → 405.10 ms     (+0.58%)          26   →     23      (-11.54%)
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.99 μs →   3.84 μs    (-51.95%)          26   →     23      (-11.54%)
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.32 μs →   3.22 μs    (-56.02%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.38 ms → 100.28 ms     (-0.10%)          26   →     23      (-11.54%)
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.45 μs →  11.01 μs    (+47.87%)          26   →     23      (-11.54%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.13 ms     (+0.16%)          26   →     23      (-11.54%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.37 ms →  91.22 ms     (-0.16%)          26   →     23      (-11.54%)
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       487.54 ns → 557.00 ns    (+14.25%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  162.90 ms → 163.37 ms     (+0.29%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.64 ms     (-0.12%)          26   →     23      (-11.54%)
! │ │ │ │ └ sirius::Density::augment                                       88.43 ms →  88.28 ms     (-0.17%)          26   →     23      (-11.54%)
! │ │ │ │   └ sirius::Density::generate_rho_aug                            88.19 ms →  88.04 ms     (-0.17%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Field4D::symmetrize                                     270.82 ms → 279.70 ms     (+3.28%)          26   →     23      (-11.54%)
! │ │ │ │ └ sirius::symmetrize_function|fpw                               270.81 ms → 279.70 ms     (+3.28%)          26   →     23      (-11.54%)
! │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             24.30 ms →  24.47 ms     (+0.67%)          26   →     23      (-11.54%)
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       221.80 ms → 230.48 ms     (+3.92%)          26   →     23      (-11.54%)
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                            23.55 ms →  23.57 ms     (+0.06%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                       81.60 ms →  81.90 ms     (+0.37%)          26   →     23      (-11.54%)
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   7.78 ms →   9.72 ms    (+24.90%)          26   →     23      (-11.54%)
+ │ │ ├ sirius::Density::mix                                              232.80 ms → 207.88 ms    (-10.70%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Density::mixer_input                                    973.00 μs → 932.51 μs     (-4.16%)          26   →     23      (-11.54%)
+ │ │ │ ├ sirius::Periodic_function|inner                                  11.77 ms →  10.17 ms    (-13.59%)         334   →    289      (-13.47%)
+ │ │ │ │ └ sirius::Periodic_function|inner_local                          11.34 ms →   9.96 ms    (-12.13%)         334   →    289      (-13.47%)
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 11.34 ms →   9.96 ms    (-12.13%)         334   →    289      (-13.47%)
! │ │ │ └ sirius::Density::mixer_output                                     6.91 ms →   6.89 ms     (-0.24%)          26   →     23      (-11.54%)
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.06 ms →   6.09 ms     (+0.49%)          26   →     23      (-11.54%)
! │ │ ├ sirius::Potential::generate                                       580.52 ms → 591.28 ms     (+1.85%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Potential::poisson                                      138.45 ms → 137.98 ms     (-0.34%)          26   →     23      (-11.54%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                18.15 ms →  17.00 ms     (-6.31%)          26   →     23      (-11.54%)
! │ │ │ │ └ sirius::Periodic_function|inner                                10.75 ms →  10.93 ms     (+1.65%)          26   →     23      (-11.54%)
! │ │ │ │   └ sirius::Periodic_function|inner_local                        10.32 ms →  10.72 ms     (+3.90%)          26   →     23      (-11.54%)
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.32 ms →  10.72 ms     (+3.90%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Periodic_function::add                                  563.83 μs → 563.93 μs     (+0.02%)          52   →     46      (-11.54%)
! │ │ │ ├ sirius::Potential::xc                                            49.42 ms →  49.45 ms     (+0.07%)          26   →     23      (-11.54%)
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           47.05 ms →  47.13 ms     (+0.18%)          26   →     23      (-11.54%)
! │ │ │ │   ├ sirius::Smooth_periodic_function                              2.98 ms →   2.99 ms     (+0.40%)          52   →     46      (-11.54%)
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.48 ms →   5.99 ms     (+9.40%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.54 ms →   6.97 ms     (+6.52%)          26   →     23      (-11.54%)
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.97 ms →  90.95 ms     (-0.02%)          26   →     23      (-11.54%)
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.69 ms → 303.48 ms     (+3.69%)          26   →     23      (-11.54%)
! │ │ ├ sirius::Field4D::symmetrize                                       276.66 ms → 282.57 ms     (+2.14%)          26   →     23      (-11.54%)
! │ │ │ └ sirius::symmetrize_function|fpw                                 276.65 ms → 282.57 ms     (+2.14%)          26   →     23      (-11.54%)
! │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.16 ms →  27.23 ms     (+0.25%)          26   →     23      (-11.54%)
! │ │ │   ├ sirius::symmetrize_function|fpw|local                         221.79 ms → 227.59 ms     (+2.62%)          26   →     23      (-11.54%)
! │ │ │   └ sddk::Gvec_shells::remap_backward                              23.91 ms →  23.99 ms     (+0.35%)          26   →     23      (-11.54%)
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.59 ms →   5.89 ms     (+5.45%)          26   →     23      (-11.54%)
+ │ │ ├ sirius::Periodic_function|inner                                    11.68 ms →  10.13 ms    (-13.23%)         182   →    161      (-11.54%)
+ │ │ │ └ sirius::Periodic_function|inner_local                            11.18 ms →   9.78 ms    (-12.51%)         182   →    161      (-11.54%)
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                   11.18 ms →   9.78 ms    (-12.51%)         182   →    161      (-11.54%)
! │ │ ├ sirius::Smooth_periodic_function|inner                             10.67 ms →  10.38 ms     (-2.78%)          78   →     69      (-11.54%)
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.30 ms →  10.14 ms     (-1.56%)          78   →     69      (-11.54%)
! │ │ ├ sirius::Periodic_function::integrate                               10.47 ms →   9.85 ms     (-5.94%)          26   →     23      (-11.54%)
+ │ │ └ sirius::Density::get_magnetisation                                166.65 μs → 130.54 μs    (-21.67%)          26   →     23      (-11.54%)
+ │ │   └ sirius::Density::compute_atomic_mag_mom                         161.88 μs → 125.67 μs    (-22.37%)          26   →     23      (-11.54%)
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                         7.04 ms →   5.59 ms    (-20.50%)           2   →      2               
+ │ ├ sirius::Periodic_function|inner                                      11.38 ms →  10.10 ms    (-11.25%)           6   →      6               
+ │ │ └ sirius::Periodic_function|inner_local                              11.34 ms →  10.09 ms    (-11.02%)           6   →      6               
+ │ │   └ sirius::Smooth_periodic_function|inner_local                     11.34 ms →  10.09 ms    (-11.02%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.47 ms →  10.47 ms     (+0.04%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.46 ms →  10.47 ms     (+0.02%)           3   →      3               
+ ├ sirius::Periodic_function|inner                                        11.43 ms →  10.03 ms    (-12.30%)           2   →      2               
+ │ └ sirius::Periodic_function|inner_local                                11.42 ms →  10.02 ms    (-12.30%)           2   →      2               
+ │   └ sirius::Smooth_periodic_function|inner_local                       11.42 ms →  10.02 ms    (-12.30%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.64 ms →  10.42 ms     (-2.09%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.64 ms →  10.41 ms     (-2.11%)           1   →      1               
+ └ sirius::finalize                                                      243.93 ms → 192.66 ms    (-21.02%)           1   →      1               
```
