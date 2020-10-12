# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  132.29 s  → 133.15 s      (+0.65%)           1   →      1               
  ├ sirius::initialize                                                      2.78 s  →   2.71 s      (-2.39%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  2.94 s  →   2.99 s      (+1.62%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               201.60 μs →  34.69 ms (+17106.58%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       184.00 ms → 185.02 ms     (+0.55%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                            79.46 ms →  80.80 ms     (+1.68%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          25.01 ms →  23.35 ms     (-6.64%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.29 ms →   5.66 ms     (-9.91%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  18.68 ms →  17.64 ms     (-5.54%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     18.66 ms →  17.62 ms     (-5.55%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.29 ms →   4.18 ms     (-2.41%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.34 ms →   2.29 ms     (-1.73%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              103.06 μs → 101.93 μs     (-1.10%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.72 s  →   2.73 s      (+0.47%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.87 ms →  10.84 ms     (-0.30%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.47 ms →   4.48 ms     (+0.06%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.36 ms →   6.33 ms     (-0.51%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.34 ms →   6.31 ms     (-0.51%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.84 ms →   3.82 ms     (-0.38%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.34 ms →   2.32 ms     (-0.75%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              100.21 μs → 100.17 μs     (-0.04%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       62.71 ms →  63.41 ms     (+1.12%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.13 ms →   5.14 ms     (+0.16%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.48 ms →   4.47 ms     (-0.21%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.68 ms →  21.92 ms     (+1.08%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.83 ms →  14.92 ms     (+0.59%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.83 ms →  19.67 ms     (-0.79%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  178.52 ms → 175.81 ms     (-1.52%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    135.70 ms → 133.09 ms     (-1.92%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 172.28 ms → 185.37 ms     (+7.60%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.33 ms →   1.34 ms     (+1.17%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 295.95 ms → 296.10 ms     (+0.05%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     35.35 ms →  35.34 ms     (-0.03%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              2.72 μs →   2.51 μs     (-7.79%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      35.26 ms →  35.24 ms     (-0.04%)           1   →      1               
  │   └ sirius::K_point::initialize                                        35.17 ms →  35.15 ms     (-0.06%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.07 ms →  18.03 ms     (-0.23%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.15 ms →   8.13 ms     (-0.25%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                             10.14 μs →   9.62 μs     (-5.18%)           1   →      1               
  │     └ sirius::K_point::update                                          12.27 ms →  12.33 ms     (+0.51%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.05 ms →   6.09 ms     (+0.69%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.43 ms →   3.48 ms     (+1.59%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.38 ms →   5.09 ms     (-5.50%)           2   →      2               
  ├ sirius::Potential                                                     159.17 ms → 159.65 ms     (+0.30%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.87 ms →   5.73 ms     (-2.38%)           6   →      6               
  │ └ sirius::Potential::update                                           123.19 ms → 124.54 ms     (+1.09%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       122.52 ms → 123.85 ms     (+1.08%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              115.30 ms → 111.20 ms     (-3.56%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   6.31 ms →  11.76 ms    (+86.32%)           1   →      1               
  ├ sirius::Density                                                       134.74 ms → 136.87 ms     (+1.58%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.23 ms →   5.11 ms     (-2.26%)           2   →      2               
  │ └ sirius::Density::update                                             124.01 ms → 126.37 ms     (+1.91%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              123.60 ms → 125.96 ms     (+1.91%)           1   →      1               
- │     ├ sirius::rho_core_ri_pseudo|values                               103.54 μs → 117.21 μs    (+13.20%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              117.76 ms → 112.78 ms     (-4.23%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   5.28 ms →  12.63 ms   (+139.29%)           1   →      1               
  ├ sirius::Density::initial_density                                      177.47 ms → 177.09 ms     (-0.22%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  122.02 ms → 111.36 ms     (-8.74%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       5.50 ms →  11.66 ms   (+112.16%)           2   →      2               
+ │ └ sirius::Periodic_function::integrate                                 11.68 ms →  10.05 ms    (-13.98%)           1   →      1               
  ├ sirius::Potential::generate                                           592.66 ms → 597.81 ms     (+0.87%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          137.71 ms → 139.73 ms     (+1.47%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.61 ms →  17.35 ms   (+209.00%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    11.35 ms →  11.29 ms     (-0.45%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.73 ms →  10.23 ms     (-4.62%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.72 ms →  10.22 ms     (-4.62%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      572.87 μs → 559.30 μs     (-2.37%)           2   →      2               
  │ ├ sirius::Potential::xc                                                53.83 ms →  56.54 ms     (+5.04%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               51.53 ms →  54.27 ms     (+5.32%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.72 ms →   5.58 ms     (-2.41%)           2   →      2               
- │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.47 ms →   6.44 ms    (+17.66%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.76 ms →   5.77 ms     (+0.15%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        92.68 ms →  92.66 ms     (-0.02%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 300.14 ms → 300.61 ms     (+0.16%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.66 ms →   9.34 ms     (+7.83%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.31 ms →   8.98 ms     (+8.15%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.75 ms →   4.69 ms     (-1.32%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.64 ms →   3.37 ms    (+28.00%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           63.98 μs →  63.39 μs     (-0.93%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       93.80 μs →  95.67 μs     (+2.00%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       75.32 μs →  75.29 μs     (-0.03%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.88 s  →   1.87 s      (-0.62%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.68 ms →  18.71 ms     (+0.13%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 177.84 μs → 200.75 μs    (+12.88%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.50 ms →  18.51 ms     (+0.01%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.87 s  →   1.85 s      (-0.63%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              131.98 ms → 131.16 ms     (-0.62%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    53.02 ms →  52.96 ms     (-0.11%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.86 ms →  21.52 ms     (-1.56%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  636.92 ms → 636.28 ms     (-0.10%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 297.74 ms → 298.01 ms     (+0.09%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.12 μs →   3.96 μs    (+26.80%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.10 μs →   3.05 μs    (+45.78%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           437.00 ns → 442.00 ns     (+1.14%)           1   →      1               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          481.00 ns → 524.00 ns     (+8.94%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.22 ms →   9.22 ms     (+0.04%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             121.53 ms → 120.44 ms     (-0.89%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               104.20 ms → 104.28 ms     (+0.08%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    38.55 ms →  38.46 ms     (-0.24%)           2   →      2               
  │ │ │ └ sddk::inner                                                      37.98 ms →  37.93 ms     (-0.16%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              28.01 μs →  29.14 μs     (+4.01%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           57.28 ms →  61.36 ms     (+7.12%)           1   →      1               
  │ │ └ sddk::transform                                                    31.54 ms →  31.56 ms     (+0.06%)           1   →      1               
- │ │   ├ sddk::transform|init                                             10.90 μs →  12.68 μs    (+16.33%)           1   →      1               
- │ │   └ sddk::transform|local                                            12.37 μs →  13.79 μs    (+11.45%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                               638.00 ns → 668.00 ns     (+4.70%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    122.52 s  → 123.43 s      (+0.74%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.79 ms →   5.74 ms     (-0.83%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.70 s  →   4.73 s      (+0.74%)          26   →     26               
- │ │ ├ sirius::Hamiltonian0                                                4.52 ms →   5.78 ms    (+27.92%)          26   →     26               
- │ │ │ ├ sirius::Local_operator                                            4.15 ms →   5.41 ms    (+30.33%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              969.39 μs → 992.14 μs     (+2.35%)          26   →     26               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.29 ms →   3.53 ms    (+53.81%)          26   →     26               
  │ │ │ ├ sirius::Non_local_operator                                       64.54 μs →  64.85 μs     (+0.47%)          52   →     52               
  │ │ │ ├ sirius::D_operator::initialize                                   92.88 μs →  93.43 μs     (+0.59%)          26   →     26               
  │ │ │ └ sirius::Q_operator::initialize                                   76.94 μs →  76.89 μs     (-0.06%)          26   →     26               
  │ │ ├ sirius::Band::solve                                                 2.72 s  →   2.76 s      (+1.32%)          26   →     26               
  │ │ │ ├ sirius::Hamiltonian_k                                           158.56 μs → 158.56 μs     (-0.00%)          26   →     26               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             152.35 μs → 152.75 μs     (+0.26%)          26   →     26               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           4.63 μs →   4.26 μs     (-7.86%)          26   →     26               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.59 s  →   2.61 s      (+0.61%)          26   →     26               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             96.45 ms →  94.39 ms     (-2.13%)          26   →     26               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.85 ms →   7.59 ms     (-3.30%)         156   →    156               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             5.97 ms →   5.98 ms     (+0.17%)          26   →     26               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       352.50 μs → 348.94 μs     (-1.01%)          26   →     26               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.30 ms →   2.31 ms     (+0.68%)          52   →     52               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.46 s  →   2.47 s      (+0.73%)          26   →     26               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            127.90 ms → 125.69 ms     (-1.73%)         277   →    283       (+2.17%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            50.85 ms →  49.94 ms     (-1.78%)         277   →    283       (+2.17%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.76 μs →   1.81 μs     (+2.31%)         277   →    283       (+2.17%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.42 μs →   1.49 μs     (+5.08%)         277   →    283       (+2.17%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     313.64 ns → 321.63 ns     (+2.55%)         277   →    283       (+2.17%)
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    431.77 ns → 466.17 ns     (+7.97%)         277   →    283       (+2.17%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.42 ms →   7.41 ms     (-0.14%)         277   →    283       (+2.17%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        23.62 ms →  22.96 ms     (-2.77%)         277   →    283       (+2.17%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          23.00 ms →  22.67 ms     (-1.39%)         554   →    566       (+2.17%)
  │ │ │ │   ├ sddk::orthogonalize                                          32.34 ms →  31.79 ms     (-1.72%)         277   →    283       (+2.17%)
  │ │ │ │   │ ├ sddk::inner                                                 4.79 ms →   4.70 ms     (-1.85%)         528   →    540       (+2.27%)
  │ │ │ │   │ │ └ sddk::inner|local                                        20.76 μs →  21.96 μs     (+5.76%)         528   →    540       (+2.27%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 606.78 μs → 592.17 μs     (-2.41%)         277   →    283       (+2.17%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.55 ms →   9.35 ms     (-2.03%)         277   →    283       (+2.17%)
  │ │ │ │   │ └ sddk::transform                                            14.41 ms →  14.17 ms     (-1.66%)         251   →    257       (+2.39%)
  │ │ │ │   │   ├ sddk::transform|init                                     16.79 μs →  17.60 μs     (+4.79%)         251   →    257       (+2.39%)
  │ │ │ │   │   └ sddk::transform|local                                     6.77 μs →   7.33 μs     (+8.35%)         753   →    771       (+2.39%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               9.10 ms →   8.94 ms     (-1.84%)         277   →    283       (+2.17%)
  │ │ │ │   │ └ sddk::inner                                                 8.86 ms →   8.69 ms     (-1.83%)         277   →    283       (+2.17%)
  │ │ │ │   │   └ sddk::inner|local                                        20.95 μs →  21.90 μs     (+4.55%)         277   →    283       (+2.17%)
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     33.34 ms →  33.56 ms     (+0.67%)         277   →    283       (+2.17%)
  │ │ │ │   ├ sirius::residuals                                            13.65 ms →  13.41 ms     (-1.76%)         268   →    274       (+2.24%)
  │ │ │ │   │ ├ sddk::transform                                            12.31 ms →  12.13 ms     (-1.46%)         259   →    264       (+1.93%)
- │ │ │ │   │ │ ├ sddk::transform|init                                     13.00 μs →  14.32 μs    (+10.17%)         259   →    264       (+1.93%)
  │ │ │ │   │ │ └ sddk::transform|local                                     9.03 μs →   9.67 μs     (+7.10%)         518   →    528       (+1.93%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.58 ms →   1.55 ms     (-1.53%)         259   →    264       (+1.93%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      76.20 ms →  76.21 ms     (+0.02%)          53   →     53               
  │ │ │ │     └ sddk::transform                                            50.25 ms →  50.26 ms     (+0.01%)          80   →     80               
  │ │ │ │       ├ sddk::transform|init                                     10.01 μs →  10.94 μs     (+9.27%)          80   →     80               
  │ │ │ │       └ sddk::transform|local                                     9.16 μs →   9.94 μs     (+8.58%)         107   →    107               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           386.65 ns → 414.27 ns     (+7.14%)          26   →     26               
- │ │ │ └ sirius::K_point_set::sync_band_energies                          38.53 μs →  57.73 μs    (+49.84%)          26   →     26               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        593.95 μs → 591.19 μs     (-0.47%)          26   →     26               
  │ │ ├ sirius::Density::generate                                         774.84 ms → 774.08 ms     (-0.10%)          26   →     26               
  │ │ │ ├ sirius::Density::generate_valence                               402.32 ms → 403.50 ms     (+0.29%)          26   →     26               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.01 μs →   7.81 μs     (-2.49%)          26   →     26               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.18 μs →   7.30 μs     (+1.73%)          26   →     26               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.32 ms → 100.40 ms     (+0.08%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.88 μs →   7.79 μs     (-1.13%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.12 ms     (+0.02%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.28 ms →  91.35 ms     (+0.08%)          26   →     26               
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       631.19 ns → 544.00 ns    (-13.81%)          26   →     26               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  163.20 ms → 163.24 ms     (+0.03%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.65 ms     (+0.47%)          26   →     26               
  │ │ │ │ └ sirius::Density::augment                                       88.29 ms →  88.28 ms     (-0.01%)          26   →     26               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.05 ms →  88.05 ms     (-0.01%)          26   →     26               
  │ │ │ ├ sirius::Field4D::symmetrize                                     274.06 ms → 269.44 ms     (-1.69%)          26   →     26               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               274.06 ms → 269.44 ms     (-1.69%)          26   →     26               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             25.83 ms →  24.30 ms     (-5.95%)          26   →     26               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       224.12 ms → 221.05 ms     (-1.37%)          26   →     26               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            22.92 ms →  22.91 ms     (-0.04%)          26   →     26               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       89.18 ms →  91.63 ms     (+2.75%)          26   →     26               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   5.68 ms →   5.92 ms     (+4.12%)          26   →     26               
  │ │ ├ sirius::Density::mix                                              214.15 ms → 214.09 ms     (-0.03%)          26   →     26               
  │ │ │ ├ sirius::Density::mixer_input                                    966.06 μs → 930.39 μs     (-3.69%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function|inner                                  10.25 ms →  10.32 ms     (+0.70%)         334   →    334               
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.00 ms →   9.99 ms     (-0.13%)         334   →    334               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.00 ms →   9.99 ms     (-0.13%)         334   →    334               
  │ │ │ └ sirius::Density::mixer_output                                     6.60 ms →   6.88 ms     (+4.27%)          26   →     26               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.74 ms →   6.07 ms     (+5.73%)          26   →     26               
  │ │ ├ sirius::Potential::generate                                       579.56 ms → 581.30 ms     (+0.30%)          26   →     26               
  │ │ │ ├ sirius::Potential::poisson                                      137.15 ms → 138.95 ms     (+1.31%)          26   →     26               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 5.37 ms →  17.27 ms   (+221.92%)          26   →     26               
  │ │ │ │ └ sirius::Periodic_function|inner                                10.75 ms →  10.63 ms     (-1.15%)          26   →     26               
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.56 ms →  10.45 ms     (-1.11%)          26   →     26               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.56 ms →  10.44 ms     (-1.11%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function::add                                  578.17 μs → 564.55 μs     (-2.36%)          52   →     52               
  │ │ │ ├ sirius::Potential::xc                                            49.51 ms →  49.40 ms     (-0.22%)          26   →     26               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           47.15 ms →  47.03 ms     (-0.25%)          26   →     26               
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.04 ms →   3.04 ms     (-0.09%)          52   →     52               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.47 ms →   5.44 ms     (-0.59%)          26   →     26               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.52 ms →   6.60 ms     (+1.25%)          26   →     26               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.99 ms →  91.00 ms     (+0.01%)          26   →     26               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.88 ms → 292.88 ms     (+0.00%)          26   →     26               
  │ │ ├ sirius::Field4D::symmetrize                                       279.17 ms → 276.22 ms     (-1.06%)          26   →     26               
  │ │ │ └ sirius::symmetrize_function|fpw                                 279.17 ms → 276.22 ms     (-1.06%)          26   →     26               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               28.45 ms →  27.54 ms     (-3.21%)          26   →     26               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         223.06 ms → 220.83 ms     (-1.00%)          26   →     26               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.84 ms →  24.02 ms     (+0.78%)          26   →     26               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     7.44 ms →   5.31 ms    (-28.58%)          26   →     26               
  │ │ ├ sirius::Periodic_function|inner                                    10.23 ms →  10.41 ms     (+1.77%)         182   →    182               
  │ │ │ └ sirius::Periodic_function|inner_local                             9.89 ms →  10.01 ms     (+1.29%)         182   →    182               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.89 ms →  10.01 ms     (+1.29%)         182   →    182               
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.56 ms →  10.70 ms     (+1.39%)          78   →     78               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.24 ms →  10.24 ms     (+0.08%)          78   →     78               
  │ │ ├ sirius::Periodic_function::integrate                                9.98 ms →  10.14 ms     (+1.68%)          26   →     26               
- │ │ └ sirius::Density::get_magnetisation                                123.16 μs → 201.73 μs    (+63.79%)          26   →     26               
- │ │   └ sirius::Density::compute_atomic_mag_mom                         118.61 μs → 197.25 μs    (+66.31%)          26   →     26               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.60 ms →   5.35 ms     (-4.51%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                      10.12 ms →   9.88 ms     (-2.31%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               9.69 ms →   9.87 ms     (+1.82%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      9.69 ms →   9.87 ms     (+1.82%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.47 ms →  10.20 ms     (-2.53%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.04 ms →  10.19 ms     (+1.50%)           3   →      3               
  ├ sirius::Periodic_function|inner                                        10.05 ms →  10.02 ms     (-0.27%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 9.98 ms →  10.01 ms     (+0.30%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        9.98 ms →  10.01 ms     (+0.30%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.61 ms →  10.43 ms     (-1.70%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.42 ms →  10.43 ms     (+0.08%)           1   →      1               
+ └ sirius::finalize                                                      231.21 ms → 189.36 ms    (-18.10%)           1   →      1               
```
