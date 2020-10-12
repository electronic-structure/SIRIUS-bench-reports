# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  126.16 s  → 135.48 s      (+7.38%)           1   →      1               
  ├ sirius::initialize                                                      2.71 s  →   2.74 s      (+1.12%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  2.95 s  →   2.93 s      (-0.63%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                10.05 ms →  20.37 ms   (+102.63%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       159.96 ms → 155.71 ms     (-2.66%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                            68.45 ms →  65.71 ms     (-4.00%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          22.98 ms →  24.20 ms     (+5.31%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.58 ms →   6.22 ms     (-5.37%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  16.36 ms →  17.94 ms     (+9.65%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     16.34 ms →  17.92 ms     (+9.66%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.17 ms →   4.17 ms     (-0.11%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.35 ms →   2.30 ms     (-2.11%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              101.04 μs → 100.83 μs     (-0.21%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.74 s  →   2.71 s      (-0.89%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.82 ms →  10.79 ms     (-0.23%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.45 ms →   4.43 ms     (-0.43%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.33 ms →   6.33 ms     (-0.05%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.31 ms →   6.31 ms     (-0.05%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.82 ms →   3.83 ms     (+0.23%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.33 ms →   2.32 ms     (-0.54%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              100.14 μs → 100.87 μs     (+0.73%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       66.26 ms →  63.42 ms     (-4.30%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.15 ms →   5.20 ms     (+1.04%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.52 ms →   4.50 ms     (-0.44%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.97 ms →  21.81 ms     (-0.70%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      15.05 ms →  14.97 ms     (-0.56%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.79 ms →  19.82 ms     (+0.16%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  172.65 ms → 176.81 ms     (+2.41%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    130.34 ms → 132.17 ms     (+1.40%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 224.62 ms → 204.15 ms     (-9.11%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.31 ms →   1.31 ms     (+0.10%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 289.61 ms → 295.35 ms     (+1.98%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     36.52 ms →  35.60 ms     (-2.51%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.67 μs →   2.34 μs    (-12.31%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      36.41 ms →  35.50 ms     (-2.52%)           1   →      1               
  │   └ sirius::K_point::initialize                                        36.32 ms →  35.41 ms     (-2.51%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.90 ms →  17.99 ms     (-4.84%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.18 ms →   8.06 ms     (-1.46%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              9.36 μs →   9.88 μs     (+5.54%)           1   →      1               
  │     └ sirius::K_point::update                                          12.61 ms →  12.59 ms     (-0.14%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.34 ms →   6.35 ms     (+0.11%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.76 ms →   3.75 ms     (-0.46%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.14 ms →   5.17 ms     (+0.62%)           2   →      2               
  ├ sirius::Potential                                                     158.75 ms → 158.93 ms     (+0.12%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.78 ms →   5.78 ms     (+0.04%)           6   →      6               
  │ └ sirius::Potential::update                                           123.34 ms → 123.50 ms     (+0.13%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       122.59 ms → 122.76 ms     (+0.14%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              110.37 ms → 108.59 ms     (-1.61%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                  11.35 ms →  13.26 ms    (+16.87%)           1   →      1               
  ├ sirius::Density                                                       137.02 ms → 135.18 ms     (-1.35%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.11 ms →   5.14 ms     (+0.52%)           2   →      2               
  │ └ sirius::Density::update                                             126.53 ms → 124.63 ms     (-1.50%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              126.12 ms → 124.22 ms     (-1.51%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               102.98 μs → 103.49 μs     (+0.50%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.85 ms → 111.88 ms     (+0.03%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  13.73 ms →  11.75 ms    (-14.41%)           1   →      1               
  ├ sirius::Density::initial_density                                      178.01 ms → 175.76 ms     (-1.26%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  110.77 ms → 111.92 ms     (+1.04%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                      11.94 ms →  10.60 ms    (-11.24%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                 11.26 ms →  10.25 ms     (-8.95%)           1   →      1               
  ├ sirius::Potential::generate                                           596.03 ms → 592.80 ms     (-0.54%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          138.25 ms → 136.62 ms     (-1.17%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                    18.78 ms →  15.26 ms    (-18.73%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.24 ms →   9.91 ms     (-3.19%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             9.88 ms →   9.89 ms     (+0.04%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    9.88 ms →   9.88 ms     (+0.04%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      547.65 μs → 531.51 μs     (-2.95%)           2   →      2               
  │ ├ sirius::Potential::xc                                                54.04 ms →  54.29 ms     (+0.47%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               51.74 ms →  51.99 ms     (+0.47%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.56 ms →   5.69 ms     (+2.22%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.83 ms →   5.84 ms     (+0.09%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.97 ms →   5.89 ms     (-1.30%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        93.67 ms →  92.73 ms     (-1.00%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 301.68 ms → 300.83 ms     (-0.28%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.45 ms →   8.44 ms     (-0.10%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.08 ms →   8.09 ms     (+0.06%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.68 ms →   4.69 ms     (+0.14%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.48 ms →   2.48 ms     (+0.17%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           63.60 μs →  62.82 μs     (-1.22%)           2   →      2               
+ │ ├ sirius::D_operator::initialize                                      107.78 μs →  93.65 μs    (-13.11%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       74.10 μs →  74.97 μs     (+1.17%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.85 s  →   1.85 s      (+0.05%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.68 ms →  18.67 ms     (-0.06%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 184.33 μs → 165.84 μs    (-10.03%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.49 ms →  18.50 ms     (+0.04%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.83 s  →   1.83 s      (+0.05%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              125.68 ms → 128.94 ms     (+2.60%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    52.32 ms →  52.40 ms     (+0.16%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.00 ms →  21.54 ms     (+2.59%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  639.96 ms → 634.69 ms     (-0.82%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 298.13 ms → 297.87 ms     (-0.09%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.73 μs →   3.35 μs    (+22.69%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.95 μs →   2.46 μs    (+26.41%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           387.00 ns → 389.00 ns     (+0.52%)           1   →      1               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                          485.00 ns → 429.00 ns    (-11.55%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.26 ms →   9.21 ms     (-0.50%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             122.33 ms → 120.63 ms     (-1.39%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               105.10 ms → 103.47 ms     (-1.55%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    40.16 ms →  40.04 ms     (-0.31%)           2   →      2               
  │ │ │ └ sddk::wf_inner                                                   39.59 ms →  39.51 ms     (-0.20%)           2   →      2               
  │ │ │   ├ sddk::wf_inner|scale                                           19.50 ns →  19.50 ns                        2   →      2               
  │ │ │   ├ sddk::wf_inner|pw                                              39.11 ms →  39.03 ms     (-0.21%)           2   →      2               
  │ │ │   └ sddk::wf_inner|scale_back                                      19.50 ns →  18.50 ns     (-5.13%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           56.99 ms →  55.78 ms     (-2.13%)           1   →      1               
  │ │ └ sddk::wf_trans                                                     30.73 ms →  30.75 ms     (+0.05%)           1   →      1               
  │ │   └ sddk::wf_trans|pw                                                30.73 ms →  30.74 ms     (+0.04%)           1   →      1               
- │ └ sirius::Beta_projectors_base::dismiss                               469.00 ns → 602.00 ns    (+28.36%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    116.43 s  → 125.79 s      (+8.04%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.75 ms →   5.74 ms     (-0.19%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          5.04 s  →   5.23 s      (+3.63%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Hamiltonian0                                                6.12 ms →   6.08 ms     (-0.70%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Local_operator                                            5.76 ms →   5.71 ms     (-0.76%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                              972.62 μs → 920.83 μs     (-5.32%)          23   →     24       (+4.35%)
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 3.90 ms →   3.90 ms     (+0.17%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Non_local_operator                                       64.74 μs →  65.29 μs     (+0.85%)          46   →     48       (+4.35%)
  │ │ │ ├ sirius::D_operator::initialize                                   86.90 μs →  85.63 μs     (-1.46%)          23   →     24       (+4.35%)
  │ │ │ └ sirius::Q_operator::initialize                                   77.07 μs →  77.55 μs     (+0.63%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Band::solve                                                 3.04 s  →   3.23 s      (+6.42%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Hamiltonian_k                                           152.79 μs → 154.21 μs     (+0.93%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             146.91 μs → 146.83 μs     (-0.05%)          23   →     24       (+4.35%)
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           4.07 μs →   5.21 μs    (+28.01%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.85 s  →   3.13 s      (+9.82%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc            101.60 ms →  99.61 ms     (-1.96%)          23   →     24       (+4.35%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.54 ms →   8.33 ms     (-2.39%)         138   →    144       (+4.35%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             6.00 ms →   5.93 ms     (-1.20%)          23   →     24       (+4.35%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       351.57 μs → 348.66 μs     (-0.83%)          23   →     24       (+4.35%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.32 ms →   2.32 ms     (-0.13%)          46   →     48       (+4.35%)
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.70 s  →   2.99 s     (+10.42%)          23   →     24       (+4.35%)
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            126.07 ms → 117.50 ms     (-6.79%)         268   →    290       (+8.21%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            49.96 ms →  46.41 ms     (-7.11%)         268   →    290       (+8.21%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.93 μs →   2.10 μs     (+8.55%)         268   →    290       (+8.21%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.68 μs →   1.78 μs     (+6.02%)         268   →    290       (+8.21%)
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     349.21 ns → 416.60 ns    (+19.30%)         268   →    290       (+8.21%)
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    396.16 ns → 484.29 ns    (+22.25%)         268   →    290       (+8.21%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.44 ms →   7.39 ms     (-0.75%)         268   →    290       (+8.21%)
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        23.26 ms →  20.93 ms    (-10.01%)         268   →    290       (+8.21%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          22.70 ms →  21.38 ms     (-5.79%)         536   →    580       (+8.21%)
  │ │ │ │   ├ sddk::orthogonalize                                          34.42 ms →  32.54 ms     (-5.46%)         268   →    290       (+8.21%)
  │ │ │ │   │ ├ sddk::wf_inner                                              5.94 ms →   5.61 ms     (-5.48%)         513   →    556       (+8.38%)
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                     65.47 ns →  30.42 ns    (-53.53%)         513   →    556       (+8.38%)
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                         4.83 ms →   4.50 ms     (-6.73%)         513   →    556       (+8.38%)
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                52.02 ns →  59.45 ns    (+14.28%)         513   →    556       (+8.38%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 602.74 μs → 554.97 μs     (-7.93%)         268   →    290       (+8.21%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.30 ms →   8.63 ms     (-7.26%)         268   →    290       (+8.21%)
  │ │ │ │   │ └ sddk::wf_trans                                             14.38 ms →  13.73 ms     (-4.51%)         245   →    266       (+8.57%)
  │ │ │ │   │   └ sddk::wf_trans|pw                                         4.79 ms →   4.58 ms     (-4.51%)         735   →    798       (+8.57%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                              10.31 ms →  10.52 ms     (+1.98%)         268   →    290       (+8.21%)
  │ │ │ │   │ └ sddk::wf_inner                                             10.04 ms →  10.16 ms     (+1.15%)         268   →    290       (+8.21%)
- │ │ │ │   │   ├ sddk::wf_inner|scale                                     46.84 ns →  52.71 ns    (+12.52%)         268   →    290       (+8.21%)
  │ │ │ │   │   ├ sddk::wf_inner|pw                                         8.93 ms →   9.04 ms     (+1.29%)         268   →    290       (+8.21%)
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                                69.86 ns →  39.97 ns    (-42.78%)         268   →    290       (+8.21%)
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     33.62 ms →  57.26 ms    (+70.29%)         268   →    290       (+8.21%)
  │ │ │ │   ├ sirius::residuals                                            13.47 ms →  14.33 ms     (+6.40%)         259   →    278       (+7.34%)
  │ │ │ │   │ ├ sddk::wf_trans                                             12.14 ms →  12.99 ms     (+6.97%)         250   →    271       (+8.40%)
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                         6.07 ms →   6.49 ms     (+6.97%)         500   →    542       (+8.40%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.57 ms →   1.49 ms     (-5.13%)         250   →    271       (+8.40%)
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      77.94 ms →  89.59 ms    (+14.94%)          50   →     50               
- │ │ │ │     └ sddk::wf_trans                                             50.37 ms →  58.71 ms    (+16.55%)          77   →     76       (-1.30%)
- │ │ │ │       └ sddk::wf_trans|pw                                        37.29 ms →  43.74 ms    (+17.29%)         104   →    102       (-1.92%)
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                           626.57 ns → 772.96 ns    (+23.36%)          23   →     24       (+4.35%)
+ │ │ │ └ sirius::K_point_set::sync_band_energies                          82.78 μs →  34.74 μs    (-58.04%)          23   →     24       (+4.35%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                        603.20 μs → 602.06 μs     (-0.19%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Density::generate                                         791.50 ms → 784.87 ms     (-0.84%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Density::generate_valence                               410.94 ms → 401.73 ms     (-2.24%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.51 μs →   8.70 μs     (+2.25%)          23   →     24       (+4.35%)
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           8.04 μs →   7.76 μs     (-3.50%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.58 ms → 100.27 ms     (-0.31%)          23   →     24       (+4.35%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.43 μs →   7.67 μs     (+3.18%)          23   →     24       (+4.35%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.15 ms →   7.12 ms     (-0.43%)          23   →     24       (+4.35%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.51 ms →  91.20 ms     (-0.33%)          23   →     24       (+4.35%)
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       710.43 ns → 584.08 ns    (-17.79%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  162.53 ms → 164.38 ms     (+1.14%)          23   →     24       (+4.35%)
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.64 ms     (-0.10%)          23   →     24       (+4.35%)
  │ │ │ │ └ sirius::Density::augment                                       88.27 ms →  88.22 ms     (-0.06%)          23   →     24       (+4.35%)
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.04 ms →  87.99 ms     (-0.06%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Field4D::symmetrize                                     281.83 ms → 285.81 ms     (+1.41%)          23   →     24       (+4.35%)
  │ │ │ │ └ sirius::symmetrize_function|fpw                               281.83 ms → 285.81 ms     (+1.41%)          23   →     24       (+4.35%)
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             30.77 ms →  29.56 ms     (-3.94%)          23   →     24       (+4.35%)
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       225.53 ms → 225.78 ms     (+0.11%)          23   →     24       (+4.35%)
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                            24.33 ms →  29.30 ms    (+20.43%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       80.79 ms →  88.36 ms     (+9.38%)          23   →     24       (+4.35%)
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                  14.35 ms →   5.31 ms    (-62.96%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Density::mix                                              211.94 ms → 213.48 ms     (+0.73%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Density::mixer_input                                    927.75 μs → 973.93 μs     (+4.98%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Periodic_function|inner                                  10.53 ms →  10.57 ms     (+0.31%)         289   →    304       (+5.19%)
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.34 ms →  10.30 ms     (-0.36%)         289   →    304       (+5.19%)
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.34 ms →  10.30 ms     (-0.36%)         289   →    304       (+5.19%)
  │ │ │ └ sirius::Density::mixer_output                                     7.11 ms →   6.69 ms     (-5.86%)          23   →     24       (+4.35%)
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.27 ms →   5.86 ms     (-6.62%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Potential::generate                                       580.54 ms → 577.90 ms     (-0.46%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Potential::poisson                                      137.84 ms → 136.86 ms     (-0.71%)          23   →     24       (+4.35%)
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                18.16 ms →  15.36 ms    (-15.39%)          23   →     24       (+4.35%)
  │ │ │ │ └ sirius::Periodic_function|inner                                10.08 ms →  10.14 ms     (+0.63%)          23   →     24       (+4.35%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                         9.86 ms →   9.89 ms     (+0.26%)          23   →     24       (+4.35%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                9.86 ms →   9.89 ms     (+0.26%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Periodic_function::add                                  553.81 μs → 551.75 μs     (-0.37%)          46   →     48       (+4.35%)
  │ │ │ ├ sirius::Potential::xc                                            49.75 ms →  48.69 ms     (-2.13%)          23   →     24       (+4.35%)
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           47.38 ms →  46.39 ms     (-2.10%)          23   →     24       (+4.35%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.02 ms →   2.94 ms     (-2.62%)          46   →     48       (+4.35%)
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               6.28 ms →   5.60 ms    (-10.72%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.98 ms →   6.43 ms     (-7.93%)          23   →     24       (+4.35%)
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    91.12 ms →  90.95 ms     (-0.19%)          23   →     24       (+4.35%)
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.45 ms → 292.57 ms     (+0.04%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Field4D::symmetrize                                       289.85 ms → 291.78 ms     (+0.67%)          23   →     24       (+4.35%)
  │ │ │ └ sirius::symmetrize_function|fpw                                 289.85 ms → 291.78 ms     (+0.67%)          23   →     24       (+4.35%)
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               32.99 ms →  32.70 ms     (-0.88%)          23   →     24       (+4.35%)
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         228.38 ms → 224.45 ms     (-1.72%)          23   →     24       (+4.35%)
- │ │ │   └ sddk::Gvec_shells::remap_backward                              24.69 ms →  30.90 ms    (+25.18%)          23   →     24       (+4.35%)
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                    12.31 ms →   5.19 ms    (-57.83%)          23   →     24       (+4.35%)
  │ │ ├ sirius::Periodic_function|inner                                    10.00 ms →  10.09 ms     (+0.91%)         161   →    168       (+4.35%)
  │ │ │ └ sirius::Periodic_function|inner_local                             9.81 ms →   9.77 ms     (-0.41%)         161   →    168       (+4.35%)
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.81 ms →   9.77 ms     (-0.41%)         161   →    168       (+4.35%)
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.78 ms →  10.86 ms     (+0.73%)          69   →     72       (+4.35%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.60 ms →  10.58 ms     (-0.23%)          69   →     72       (+4.35%)
  │ │ ├ sirius::Periodic_function::integrate                                9.87 ms →   9.81 ms     (-0.56%)          23   →     24       (+4.35%)
  │ │ └ sirius::Density::get_magnetisation                                134.11 μs → 128.39 μs     (-4.27%)          23   →     24       (+4.35%)
  │ │   └ sirius::Density::compute_atomic_mag_mom                         129.07 μs → 123.47 μs     (-4.33%)          23   →     24       (+4.35%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.39 ms →   5.35 ms     (-0.80%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       9.90 ms →  10.11 ms     (+2.18%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               9.65 ms →  10.10 ms     (+4.65%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      9.65 ms →  10.10 ms     (+4.65%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.59 ms →  10.78 ms     (+1.87%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.49 ms →  10.78 ms     (+2.73%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         9.77 ms →  10.39 ms     (+6.28%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 9.64 ms →   9.98 ms     (+3.56%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        9.64 ms →   9.98 ms     (+3.56%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.57 ms →  10.75 ms     (+1.62%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.47 ms →  10.74 ms     (+2.55%)           1   →      1               
- └ sirius::finalize                                                      205.00 ms → 226.17 ms    (+10.33%)           1   →      1               
```
