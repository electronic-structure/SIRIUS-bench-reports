# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  129.88 s  → 135.36 s      (+4.22%)           1   →      1               
  ├ sirius::initialize                                                      2.67 s  →   2.70 s      (+0.99%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  2.95 s  →   2.99 s      (+1.54%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                31.29 ms →  62.94 ms   (+101.17%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       156.71 ms → 158.66 ms     (+1.25%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                            67.04 ms →  67.37 ms     (+0.49%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          22.55 ms →  23.85 ms     (+5.76%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.24 ms →   5.63 ms     (-9.75%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  16.26 ms →  18.17 ms    (+11.72%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     16.24 ms →  18.15 ms    (+11.74%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.13 ms →   4.16 ms     (+0.60%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.32 ms →   2.32 ms     (-0.00%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              104.37 μs → 101.03 μs     (-3.20%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.72 s  →   2.73 s      (+0.38%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.88 ms →  10.82 ms     (-0.55%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.43 ms →   4.43 ms     (-0.11%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.42 ms →   6.36 ms     (-0.86%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.40 ms →   6.34 ms     (-0.85%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.90 ms →   3.86 ms     (-1.16%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.33 ms →   2.31 ms     (-0.44%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              100.87 μs → 100.54 μs     (-0.33%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       66.16 ms →  66.75 ms     (+0.90%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.18 ms →   5.16 ms     (-0.28%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.47 ms →   4.56 ms     (+2.01%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.80 ms →  21.87 ms     (+0.34%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.95 ms →  14.99 ms     (+0.31%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.55 ms →  19.76 ms     (+1.06%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  174.60 ms → 178.13 ms     (+2.02%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    132.14 ms → 133.27 ms     (+0.85%)           2   →      2               
- │   ├ sddk::Gvec_shells                                                 183.75 ms → 203.85 ms    (+10.94%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.31 ms →   1.33 ms     (+0.81%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 295.46 ms → 296.56 ms     (+0.37%)           2   →      2               
- ├ sirius::K_point_set::create_k_mesh                                     35.65 ms →  42.25 ms    (+18.52%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.62 μs →   2.29 μs    (-12.51%)           4   →      4               
- │ └ sirius::K_point_set::initialize                                      35.55 ms →  42.15 ms    (+18.56%)           1   →      1               
- │   └ sirius::K_point::initialize                                        35.46 ms →  42.05 ms    (+18.59%)           1   →      1               
- │     ├ sirius::K_point::generate_gkvec                                  18.15 ms →  24.40 ms    (+34.44%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.12 ms →   8.15 ms     (+0.41%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                             10.16 μs →  10.33 μs     (+1.64%)           1   →      1               
  │     └ sirius::K_point::update                                          12.42 ms →  12.52 ms     (+0.84%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.13 ms →   6.18 ms     (+0.87%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.55 ms →   3.55 ms     (-0.11%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.27 ms →   5.36 ms     (+1.76%)           2   →      2               
  ├ sirius::Potential                                                     158.77 ms → 159.26 ms     (+0.31%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.79 ms →   5.88 ms     (+1.60%)           6   →      6               
  │ └ sirius::Potential::update                                           123.29 ms → 123.21 ms     (-0.06%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       122.56 ms → 122.49 ms     (-0.06%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.26 ms → 106.27 ms     (-4.48%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                  10.40 ms →  15.29 ms    (+47.01%)           1   →      1               
  ├ sirius::Density                                                       136.21 ms → 137.53 ms     (+0.97%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.31 ms →   5.18 ms     (-2.46%)           2   →      2               
  │ └ sirius::Density::update                                             125.32 ms → 126.90 ms     (+1.26%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              124.88 ms → 126.46 ms     (+1.26%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               102.82 μs → 103.80 μs     (+0.96%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              112.52 ms → 108.92 ms     (-3.21%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                  11.81 ms →  16.98 ms    (+43.78%)           1   →      1               
  ├ sirius::Density::initial_density                                      180.19 ms → 179.89 ms     (-0.17%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  110.51 ms → 108.78 ms     (-1.56%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                      12.32 ms →  13.09 ms     (+6.26%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                 12.54 ms →  12.40 ms     (-1.12%)           1   →      1               
  ├ sirius::Potential::generate                                           594.96 ms → 592.59 ms     (-0.40%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          138.70 ms → 137.62 ms     (-0.77%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                    17.57 ms →  18.65 ms     (+6.15%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.32 ms →  10.18 ms     (-1.30%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             9.93 ms →   9.89 ms     (-0.35%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    9.92 ms →   9.89 ms     (-0.35%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      539.44 μs → 560.14 μs     (+3.84%)           2   →      2               
  │ ├ sirius::Potential::xc                                                55.18 ms →  53.80 ms     (-2.50%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.85 ms →  51.46 ms     (-2.62%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.67 ms →   5.68 ms     (+0.11%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.50 ms →   5.33 ms     (-3.03%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.74 ms →   5.82 ms     (+1.48%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        93.84 ms →  92.70 ms     (-1.22%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 299.07 ms → 300.13 ms     (+0.35%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.58 ms →   8.44 ms     (-1.57%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.22 ms →   8.09 ms     (-1.56%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.74 ms →   4.76 ms     (+0.37%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.55 ms →   2.41 ms     (-5.44%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           62.26 μs →  62.70 μs     (+0.72%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       94.72 μs →  95.44 μs     (+0.75%)           1   →      1               
+ │ └ sirius::Q_operator::initialize                                       83.32 μs →  74.52 μs    (-10.57%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.87 s  →   1.87 s      (+0.11%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.68 ms →  18.66 ms     (-0.09%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 189.44 μs → 168.09 μs    (-11.27%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.49 ms →  18.49 ms     (+0.03%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.85 s  →   1.86 s      (+0.12%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              131.30 ms → 131.64 ms     (+0.26%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    52.03 ms →  52.86 ms     (+1.61%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.06 ms →  21.73 ms     (+3.15%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  634.87 ms → 634.75 ms     (-0.02%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 297.92 ms → 297.77 ms     (-0.05%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             4.00 μs →   3.20 μs    (-19.90%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.05 μs →   2.33 μs    (-23.52%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           456.00 ns → 396.00 ns    (-13.16%)           1   →      1               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                          534.00 ns → 442.00 ns    (-17.23%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.23 ms →   9.23 ms     (+0.08%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             120.74 ms → 120.69 ms     (-0.04%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               103.47 ms → 103.51 ms     (+0.04%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    40.26 ms →  40.14 ms     (-0.30%)           2   →      2               
  │ │ │ └ sddk::wf_inner                                                   39.71 ms →  39.59 ms     (-0.31%)           2   →      2               
+ │ │ │   ├ sddk::wf_inner|scale                                           42.50 ns →  37.00 ns    (-12.94%)           2   →      2               
  │ │ │   ├ sddk::wf_inner|pw                                              39.23 ms →  39.11 ms     (-0.32%)           2   →      2               
  │ │ │   └ sddk::wf_inner|scale_back                                      26.00 ns →  26.50 ns     (+1.92%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           56.60 ms →  56.30 ms     (-0.53%)           1   →      1               
  │ │ └ sddk::wf_trans                                                     30.80 ms →  30.73 ms     (-0.23%)           1   →      1               
  │ │   └ sddk::wf_trans|pw                                                30.80 ms →  30.73 ms     (-0.23%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                               600.00 ns → 591.00 ns     (-1.50%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    120.19 s  → 125.64 s      (+4.53%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.80 ms →   5.80 ms     (-0.00%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.79 s  →   5.22 s      (+8.91%)          25   →     24       (-4.00%)
- │ │ ├ sirius::Hamiltonian0                                                4.84 ms →   5.34 ms    (+10.21%)          25   →     24       (-4.00%)
- │ │ │ ├ sirius::Local_operator                                            4.48 ms →   4.97 ms    (+10.91%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                              967.75 μs → 985.42 μs     (+1.83%)          25   →     24       (-4.00%)
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.61 ms →   3.09 ms    (+18.07%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Non_local_operator                                       64.13 μs →  64.76 μs     (+0.99%)          50   →     48       (-4.00%)
  │ │ │ ├ sirius::D_operator::initialize                                   87.11 μs →  87.67 μs     (+0.64%)          25   →     24       (-4.00%)
  │ │ │ └ sirius::Q_operator::initialize                                   77.10 μs →  79.71 μs     (+3.39%)          25   →     24       (-4.00%)
- │ │ ├ sirius::Band::solve                                                 2.83 s  →   3.22 s     (+13.98%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Hamiltonian_k                                           148.40 μs → 155.40 μs     (+4.72%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             141.95 μs → 147.70 μs     (+4.05%)          25   →     24       (-4.00%)
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           4.60 μs →   5.40 μs    (+17.24%)          25   →     24       (-4.00%)
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.67 s  →   3.12 s     (+16.64%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             98.03 ms → 100.29 ms     (+2.30%)          25   →     24       (-4.00%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.12 ms →   8.52 ms     (+4.89%)         150   →    144       (-4.00%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             5.98 ms →   5.94 ms     (-0.58%)          25   →     24       (-4.00%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       348.37 μs → 350.95 μs     (+0.74%)          25   →     24       (-4.00%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.32 ms →   2.31 ms     (-0.35%)          50   →     48       (-4.00%)
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.53 s  →   2.98 s     (+17.46%)          25   →     24       (-4.00%)
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            125.01 ms → 117.28 ms     (-6.18%)         276   →    290       (+5.07%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            50.06 ms →  46.38 ms     (-7.35%)         276   →    290       (+5.07%)
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.86 μs →   2.09 μs    (+12.09%)         276   →    290       (+5.07%)
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.59 μs →   1.77 μs    (+11.63%)         276   →    290       (+5.07%)
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     336.73 ns → 375.67 ns    (+11.56%)         276   →    290       (+5.07%)
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    389.47 ns → 474.13 ns    (+21.74%)         276   →    290       (+5.07%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.41 ms →   7.38 ms     (-0.40%)         276   →    290       (+5.07%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        22.37 ms →  20.89 ms     (-6.60%)         276   →    290       (+5.07%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          22.58 ms →  21.30 ms     (-5.65%)         552   →    580       (+5.07%)
  │ │ │ │   ├ sddk::orthogonalize                                          34.12 ms →  32.50 ms     (-4.74%)         276   →    290       (+5.07%)
  │ │ │ │   │ ├ sddk::wf_inner                                              5.91 ms →   5.60 ms     (-5.17%)         527   →    556       (+5.50%)
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                     68.79 ns →  31.12 ns    (-54.77%)         527   →    556       (+5.50%)
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                         4.80 ms →   4.49 ms     (-6.29%)         527   →    556       (+5.50%)
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                53.32 ns →  58.07 ns     (+8.91%)         527   →    556       (+5.50%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 606.80 μs → 554.59 μs     (-8.60%)         276   →    290       (+5.07%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.40 ms →   8.61 ms     (-8.32%)         276   →    290       (+5.07%)
  │ │ │ │   │ └ sddk::wf_trans                                             14.11 ms →  13.72 ms     (-2.75%)         251   →    266       (+5.98%)
  │ │ │ │   │   └ sddk::wf_trans|pw                                         4.70 ms →   4.57 ms     (-2.75%)         753   →    798       (+5.98%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                              10.26 ms →  10.51 ms     (+2.48%)         276   →    290       (+5.07%)
  │ │ │ │   │ └ sddk::wf_inner                                              9.99 ms →  10.15 ms     (+1.60%)         276   →    290       (+5.07%)
  │ │ │ │   │   ├ sddk::wf_inner|scale                                     50.67 ns →  54.13 ns     (+6.83%)         276   →    290       (+5.07%)
  │ │ │ │   │   ├ sddk::wf_inner|pw                                         8.87 ms →   9.04 ms     (+1.85%)         276   →    290       (+5.07%)
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                                69.26 ns →  42.13 ns    (-39.16%)         276   →    290       (+5.07%)
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     32.87 ms →  56.80 ms    (+72.78%)         276   →    290       (+5.07%)
  │ │ │ │   ├ sirius::residuals                                            13.37 ms →  14.33 ms     (+7.20%)         267   →    278       (+4.12%)
  │ │ │ │   │ ├ sddk::wf_trans                                             11.97 ms →  12.98 ms     (+8.43%)         259   →    271       (+4.63%)
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                         5.99 ms →   6.49 ms     (+8.43%)         518   →    542       (+4.63%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.57 ms →   1.49 ms     (-4.94%)         259   →    271       (+4.63%)
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      75.89 ms →  89.59 ms    (+18.06%)          52   →     50       (-3.85%)
- │ │ │ │     └ sddk::wf_trans                                             49.71 ms →  58.70 ms    (+18.08%)          79   →     76       (-3.80%)
- │ │ │ │       └ sddk::wf_trans|pw                                        37.05 ms →  43.74 ms    (+18.06%)         106   →    102       (-3.77%)
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                           898.96 ns →   1.15 μs    (+27.73%)          25   →     24       (-4.00%)
- │ │ │ └ sirius::K_point_set::sync_band_energies                          37.49 μs →  50.17 μs    (+33.83%)          25   →     24       (-4.00%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                        599.15 μs → 605.45 μs     (+1.05%)          25   →     24       (-4.00%)
  │ │ ├ sirius::Density::generate                                         766.49 ms → 781.37 ms     (+1.94%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Density::generate_valence                               401.99 ms → 402.62 ms     (+0.16%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.45 μs →   8.74 μs     (+3.38%)          25   →     24       (-4.00%)
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.96 μs →   7.78 μs     (-2.25%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.15 ms → 100.17 ms     (+0.02%)          25   →     24       (-4.00%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.07 μs →   7.58 μs     (+7.28%)          25   →     24       (-4.00%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.12 ms     (-0.02%)          25   →     24       (-4.00%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.13 ms →  91.13 ms     (+0.00%)          25   →     24       (-4.00%)
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       795.24 ns → 598.79 ns    (-24.70%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  161.95 ms → 163.48 ms     (+0.94%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.65 ms →   1.66 ms     (+0.68%)          25   →     24       (-4.00%)
  │ │ │ │ └ sirius::Density::augment                                       88.32 ms →  88.29 ms     (-0.03%)          25   →     24       (-4.00%)
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.09 ms →  88.05 ms     (-0.05%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Field4D::symmetrize                                     272.90 ms → 287.92 ms     (+5.51%)          25   →     24       (-4.00%)
  │ │ │ │ └ sirius::symmetrize_function|fpw                               272.89 ms → 287.92 ms     (+5.51%)          25   →     24       (-4.00%)
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             23.95 ms →  30.07 ms    (+25.57%)          25   →     24       (-4.00%)
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       224.05 ms → 227.47 ms     (+1.53%)          25   →     24       (-4.00%)
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                            23.69 ms →  29.19 ms    (+23.19%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       81.07 ms →  81.18 ms     (+0.14%)          25   →     24       (-4.00%)
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   6.96 ms →   6.06 ms    (-12.92%)          25   →     24       (-4.00%)
  │ │ ├ sirius::Density::mix                                              214.29 ms → 216.63 ms     (+1.09%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Density::mixer_input                                    947.83 μs → 932.21 μs     (-1.65%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Periodic_function|inner                                  10.59 ms →  10.78 ms     (+1.83%)         319   →    304       (-4.70%)
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.38 ms →  10.39 ms     (+0.03%)         319   →    304       (-4.70%)
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.38 ms →  10.39 ms     (+0.03%)         319   →    304       (-4.70%)
- │ │ │ └ sirius::Density::mixer_output                                     6.51 ms →   7.22 ms    (+10.87%)          25   →     24       (-4.00%)
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.70 ms →   6.40 ms    (+12.43%)          25   →     24       (-4.00%)
  │ │ ├ sirius::Potential::generate                                       579.64 ms → 579.76 ms     (+0.02%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Potential::poisson                                      138.56 ms → 138.13 ms     (-0.31%)          25   →     24       (-4.00%)
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                17.66 ms →  18.89 ms     (+6.96%)          25   →     24       (-4.00%)
  │ │ │ │ └ sirius::Periodic_function|inner                                10.20 ms →  10.61 ms     (+3.99%)          25   →     24       (-4.00%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.02 ms →   9.93 ms     (-0.96%)          25   →     24       (-4.00%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.02 ms →   9.93 ms     (-0.96%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Periodic_function::add                                  549.57 μs → 558.44 μs     (+1.61%)          50   →     48       (-4.00%)
  │ │ │ ├ sirius::Potential::xc                                            48.84 ms →  49.17 ms     (+0.69%)          25   →     24       (-4.00%)
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           46.50 ms →  46.81 ms     (+0.67%)          25   →     24       (-4.00%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.00 ms →   3.05 ms     (+1.54%)          50   →     48       (-4.00%)
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.34 ms →   5.55 ms     (+4.05%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.27 ms →   6.55 ms     (+4.46%)          25   →     24       (-4.00%)
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    91.06 ms →  91.01 ms     (-0.06%)          25   →     24       (-4.00%)
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.50 ms → 292.47 ms     (-0.01%)          25   →     24       (-4.00%)
  │ │ ├ sirius::Field4D::symmetrize                                       278.92 ms → 292.61 ms     (+4.91%)          25   →     24       (-4.00%)
  │ │ │ └ sirius::symmetrize_function|fpw                                 278.91 ms → 292.61 ms     (+4.91%)          25   →     24       (-4.00%)
- │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.24 ms →  32.84 ms    (+20.56%)          25   →     24       (-4.00%)
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         224.00 ms → 225.48 ms     (+0.66%)          25   →     24       (-4.00%)
- │ │ │   └ sddk::Gvec_shells::remap_backward                              23.87 ms →  30.48 ms    (+27.68%)          25   →     24       (-4.00%)
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.26 ms →   5.33 ms     (+1.40%)          25   →     24       (-4.00%)
  │ │ ├ sirius::Periodic_function|inner                                    10.14 ms →  10.19 ms     (+0.48%)         175   →    168       (-4.00%)
  │ │ │ └ sirius::Periodic_function|inner_local                             9.96 ms →   9.76 ms     (-2.05%)         175   →    168       (-4.00%)
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.96 ms →   9.75 ms     (-2.05%)         175   →    168       (-4.00%)
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.94 ms →  10.92 ms     (-0.22%)          75   →     72       (-4.00%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.78 ms →  10.57 ms     (-1.96%)          75   →     72       (-4.00%)
  │ │ ├ sirius::Periodic_function::integrate                                9.99 ms →   9.93 ms     (-0.59%)          25   →     24       (-4.00%)
+ │ │ └ sirius::Density::get_magnetisation                                161.01 μs → 142.42 μs    (-11.54%)          25   →     24       (-4.00%)
+ │ │   └ sirius::Density::compute_atomic_mag_mom                         156.12 μs → 137.42 μs    (-11.98%)          25   →     24       (-4.00%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.06 ms →   5.29 ms     (+4.73%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                      10.87 ms →   9.90 ms     (-8.90%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                              10.19 ms →   9.86 ms     (-3.24%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                     10.19 ms →   9.86 ms     (-3.23%)           6   →      6               
+ │ └ sirius::Smooth_periodic_function|inner                               11.82 ms →  10.60 ms    (-10.37%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.91 ms →  10.51 ms     (-3.64%)           3   →      3               
  ├ sirius::Periodic_function|inner                                        11.03 ms →  10.02 ms     (-9.15%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                10.08 ms →  10.01 ms     (-0.70%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.08 ms →  10.01 ms     (-0.70%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 11.82 ms →  10.90 ms     (-7.81%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.97 ms →  10.89 ms     (-0.76%)           1   →      1               
  └ sirius::finalize                                                      192.64 ms → 180.97 ms     (-6.06%)           1   →      1               
```
