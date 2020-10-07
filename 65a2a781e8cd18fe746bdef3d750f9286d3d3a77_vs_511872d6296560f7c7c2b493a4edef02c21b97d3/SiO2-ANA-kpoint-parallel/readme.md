# Benchmark 65a2a781e8cd18fe746bdef3d750f9286d3d3a77 vs 511872d6296560f7c7c2b493a4edef02c21b97d3
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  133.53 s  → 131.87 s      (-1.25%)           1   →      1               
  ├ sirius::initialize                                                      2.80 s  →   2.76 s      (-1.43%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  2.95 s  →   2.92 s      (-0.89%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               216.36 μs → 252.66 μs    (+16.78%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       229.04 ms → 155.76 ms    (-31.99%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                           102.95 ms →  66.51 ms    (-35.39%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          23.05 ms →  22.65 ms     (-1.74%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.59 ms →   6.28 ms     (-4.63%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  16.42 ms →  16.32 ms     (-0.61%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     16.40 ms →  16.30 ms     (-0.61%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.15 ms →   4.14 ms     (-0.03%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.34 ms →   2.34 ms     (+0.30%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              101.30 μs → 105.50 μs     (+4.16%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.68 s  →   2.73 s      (+1.73%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.93 ms →  10.86 ms     (-0.62%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.48 ms →   4.46 ms     (-0.54%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.41 ms →   6.37 ms     (-0.66%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.39 ms →   6.35 ms     (-0.62%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.90 ms →   3.88 ms     (-0.69%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.31 ms →   2.31 ms     (-0.03%)           1   →      1               
+ │   │     └ sirius::Unit_cell_symmetry|mag                              109.74 μs →  98.67 μs    (-10.09%)           1   →      1               
- │   ├ sirius::Radial_integrals|aug                                       63.22 ms →  93.32 ms    (+47.60%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.18 ms →   5.14 ms     (-0.80%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.50 ms →   4.53 ms     (+0.52%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.96 ms →  22.06 ms     (+0.45%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.82 ms →  15.04 ms     (+1.55%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.79 ms →  19.69 ms     (-0.47%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  173.75 ms → 172.47 ms     (-0.74%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    131.25 ms → 129.98 ms     (-0.97%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 184.10 ms → 183.22 ms     (-0.48%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.32 ms →   1.33 ms     (+0.45%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 294.00 ms → 291.38 ms     (-0.89%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     35.49 ms →  35.98 ms     (+1.39%)           1   →      1               
- │ ├ sirius::K_point::K_point                                              2.68 μs →   2.98 μs    (+11.26%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      35.39 ms →  35.89 ms     (+1.40%)           1   →      1               
  │   └ sirius::K_point::initialize                                        35.29 ms →  35.79 ms     (+1.42%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.07 ms →  18.30 ms     (+1.28%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.16 ms →   8.25 ms     (+1.12%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                              9.60 μs →   7.52 μs    (-21.64%)           1   →      1               
  │     └ sirius::K_point::update                                          12.39 ms →  12.42 ms     (+0.26%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.15 ms →   6.07 ms     (-1.23%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.53 ms →   3.45 ms     (-2.02%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.50 ms →   5.26 ms     (-4.25%)           2   →      2               
  ├ sirius::Potential                                                     159.04 ms → 158.49 ms     (-0.35%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      6.42 ms →   5.92 ms     (-7.78%)           6   →      6               
  │ └ sirius::Potential::update                                           119.70 ms → 122.20 ms     (+2.09%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       118.94 ms → 121.42 ms     (+2.09%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.35 ms → 106.85 ms     (-4.04%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   6.61 ms →  13.65 ms   (+106.65%)           1   →      1               
  ├ sirius::Density                                                       136.46 ms → 134.09 ms     (-1.74%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.18 ms →   5.20 ms     (+0.28%)           2   →      2               
  │ └ sirius::Density::update                                             125.83 ms → 123.42 ms     (-1.91%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              125.39 ms → 122.98 ms     (-1.92%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               105.22 μs → 105.15 μs     (-0.06%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              113.11 ms → 109.50 ms     (-3.19%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                  11.71 ms →  12.92 ms    (+10.34%)           1   →      1               
  ├ sirius::Density::initial_density                                      176.02 ms → 178.63 ms     (+1.48%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  111.40 ms → 109.95 ms     (-1.30%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                      11.07 ms →  11.02 ms     (-0.46%)           2   →      2               
- │ └ sirius::Periodic_function::integrate                                  9.85 ms →  10.90 ms    (+10.66%)           1   →      1               
  ├ sirius::Potential::generate                                           596.95 ms → 592.11 ms     (-0.81%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          138.46 ms → 137.22 ms     (-0.90%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                    17.03 ms →  18.95 ms    (+11.26%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.76 ms →  11.04 ms     (+2.56%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.35 ms →  10.70 ms     (+3.36%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.35 ms →  10.69 ms     (+3.37%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      568.03 μs → 551.96 μs     (-2.83%)           2   →      2               
  │ ├ sirius::Potential::xc                                                55.05 ms →  53.87 ms     (-2.14%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.69 ms →  51.49 ms     (-2.29%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.72 ms →   5.81 ms     (+1.41%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.49 ms →   5.20 ms     (-5.24%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       6.44 ms →   5.70 ms    (-11.51%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        92.77 ms →  92.66 ms     (-0.13%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 301.71 ms → 300.19 ms     (-0.50%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.65 ms →   8.40 ms     (-2.79%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.29 ms →   8.05 ms     (-2.93%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.75 ms →   4.81 ms     (+1.36%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.62 ms →   2.31 ms    (-11.53%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           62.60 μs →  62.48 μs     (-0.19%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       97.42 μs →  96.96 μs     (-0.47%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       76.31 μs →  76.68 μs     (+0.48%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.86 s  →   1.85 s      (-0.54%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.72 ms →  18.70 ms     (-0.08%)           1   →      1               
  │ │ ├ sirius::Local_operator::prepare_k                                 203.78 μs → 199.81 μs     (-1.95%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.51 ms →  18.50 ms     (-0.06%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.84 s  →   1.83 s      (-0.55%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              128.94 ms → 126.17 ms     (-2.15%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    53.25 ms →  52.31 ms     (-1.76%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.56 ms →  20.95 ms     (-2.83%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  634.94 ms → 634.90 ms     (-0.01%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 297.93 ms → 297.95 ms     (+0.01%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.90 μs →   3.52 μs     (-9.87%)           1   →      1               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.55 μs →   2.58 μs     (+1.21%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           481.00 ns → 462.00 ns     (-3.95%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          487.00 ns → 561.00 ns    (+15.20%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.23 ms →   9.23 ms     (-0.04%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             120.72 ms → 120.54 ms     (-0.15%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               103.51 ms → 103.57 ms     (+0.05%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    38.39 ms →  38.40 ms     (+0.02%)           2   →      2               
  │ │ │ └ sddk::inner                                                      37.84 ms →  37.84 ms     (-0.00%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              23.00 μs →  22.55 μs     (-1.96%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           56.79 ms →  56.42 ms     (-0.66%)           1   →      1               
  │ │ └ sddk::transform                                                    31.55 ms →  31.57 ms     (+0.08%)           1   →      1               
  │ │   ├ sddk::transform|init                                             11.32 μs →  11.15 μs     (-1.49%)           1   →      1               
  │ │   └ sddk::transform|local                                            11.82 μs →  12.80 μs     (+8.25%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               851.00 ns → 708.00 ns    (-16.80%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    123.80 s  → 122.16 s      (-1.32%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.79 ms →   5.83 ms     (+0.74%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.70 s  →   4.68 s      (-0.27%)          26   →     26               
  │ │ ├ sirius::Hamiltonian0                                                5.12 ms →   4.92 ms     (-3.86%)          26   →     26               
  │ │ │ ├ sirius::Local_operator                                            4.76 ms →   4.56 ms     (-4.29%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              933.41 μs → 990.62 μs     (+6.13%)          26   →     26               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.94 ms →   2.67 ms     (-9.15%)          26   →     26               
  │ │ │ ├ sirius::Non_local_operator                                       64.82 μs →  64.36 μs     (-0.71%)          52   →     52               
  │ │ │ ├ sirius::D_operator::initialize                                   90.31 μs →  91.92 μs     (+1.79%)          26   →     26               
  │ │ │ └ sirius::Q_operator::initialize                                   75.15 μs →  77.73 μs     (+3.43%)          26   →     26               
  │ │ ├ sirius::Band::solve                                                 2.72 s  →   2.72 s      (+0.10%)          26   →     26               
  │ │ │ ├ sirius::Hamiltonian_k                                           164.36 μs → 165.74 μs     (+0.84%)          26   →     26               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             158.85 μs → 159.51 μs     (+0.41%)          26   →     26               
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           3.97 μs →   4.62 μs    (+16.29%)          26   →     26               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.58 s  →   2.58 s      (-0.07%)          26   →     26               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             95.80 ms →  94.48 ms     (-1.38%)          26   →     26               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.70 ms →   7.60 ms     (-1.29%)         156   →    156               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             5.99 ms →   5.94 ms     (-0.83%)          26   →     26               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       350.19 μs → 349.45 μs     (-0.21%)          26   →     26               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.31 ms →   2.30 ms     (-0.53%)          52   →     52               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.44 s  →   2.44 s      (-0.02%)          26   →     26               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            126.93 ms → 126.65 ms     (-0.22%)         277   →    277               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            50.82 ms →  50.95 ms     (+0.27%)         277   →    277               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.68 μs →   1.80 μs     (+7.35%)         277   →    277               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.38 μs →   1.48 μs     (+6.80%)         277   →    277               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     363.73 ns → 343.22 ns     (-5.64%)         277   →    277               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    371.23 ns → 441.97 ns    (+19.06%)         277   →    277               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.42 ms →   7.42 ms     (-0.05%)         277   →    277               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        22.79 ms →  22.52 ms     (-1.22%)         277   →    277               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          22.94 ms →  22.87 ms     (-0.29%)         554   →    554               
  │ │ │ │   ├ sddk::orthogonalize                                          32.33 ms →  32.30 ms     (-0.09%)         277   →    277               
  │ │ │ │   │ ├ sddk::inner                                                 4.78 ms →   4.77 ms     (-0.21%)         528   →    528               
- │ │ │ │   │ │ └ sddk::inner|local                                        20.85 μs →  23.12 μs    (+10.90%)         528   →    528               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 600.66 μs → 602.40 μs     (+0.29%)         277   →    277               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.55 ms →   9.55 ms     (-0.02%)         277   →    277               
  │ │ │ │   │ └ sddk::transform                                            14.42 ms →  14.41 ms     (-0.07%)         251   →    251               
  │ │ │ │   │   ├ sddk::transform|init                                     18.34 μs →  18.48 μs     (+0.78%)         251   →    251               
- │ │ │ │   │   └ sddk::transform|local                                     6.74 μs →   7.79 μs    (+15.55%)         753   →    753               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               9.09 ms →   9.09 ms     (-0.06%)         277   →    277               
  │ │ │ │   │ └ sddk::inner                                                 8.85 ms →   8.84 ms     (-0.09%)         277   →    277               
- │ │ │ │   │   └ sddk::inner|local                                        20.16 μs →  23.15 μs    (+14.83%)         277   →    277               
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     33.27 ms →  33.50 ms     (+0.70%)         277   →    277               
  │ │ │ │   ├ sirius::residuals                                            13.63 ms →  13.67 ms     (+0.27%)         268   →    268               
  │ │ │ │   │ ├ sddk::transform                                            12.34 ms →  12.32 ms     (-0.13%)         258   →    259       (+0.39%)
- │ │ │ │   │ │ ├ sddk::transform|init                                     13.24 μs →  14.79 μs    (+11.68%)         258   →    259       (+0.39%)
  │ │ │ │   │ │ └ sddk::transform|local                                     9.27 μs →  10.01 μs     (+7.99%)         516   →    518       (+0.39%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.58 ms →   1.58 ms     (+0.04%)         258   →    259       (+0.39%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      76.22 ms →  76.22 ms     (+0.01%)          53   →     53               
  │ │ │ │     └ sddk::transform                                            50.26 ms →  50.26 ms     (+0.00%)          80   →     80               
  │ │ │ │       ├ sddk::transform|init                                      9.72 μs →  10.56 μs     (+8.56%)          80   →     80               
  │ │ │ │       └ sddk::transform|local                                     8.78 μs →   9.60 μs     (+9.38%)         107   →    107               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           444.54 ns → 426.88 ns     (-3.97%)          26   →     26               
+ │ │ │ └ sirius::K_point_set::sync_band_energies                          40.82 μs →  32.13 μs    (-21.28%)          26   →     26               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        610.99 μs → 595.24 μs     (-2.58%)          26   →     26               
  │ │ ├ sirius::Density::generate                                         772.48 ms → 773.05 ms     (+0.07%)          26   →     26               
  │ │ │ ├ sirius::Density::generate_valence                               401.67 ms → 401.49 ms     (-0.05%)          26   →     26               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.20 μs →   8.14 μs     (-0.73%)          26   →     26               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.63 μs →   7.27 μs     (-4.74%)          26   →     26               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.15 ms → 100.12 ms     (-0.04%)          26   →     26               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         6.66 μs →   7.55 μs    (+13.32%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.12 ms     (+0.00%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.13 ms →  91.09 ms     (-0.04%)          26   →     26               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       622.19 ns → 570.19 ns     (-8.36%)          26   →     26               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  161.07 ms → 162.03 ms     (+0.60%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.65 ms →   1.65 ms     (+0.07%)          26   →     26               
  │ │ │ │ └ sirius::Density::augment                                       88.26 ms →  88.25 ms     (-0.01%)          26   →     26               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.03 ms →  88.02 ms     (-0.01%)          26   →     26               
  │ │ │ ├ sirius::Field4D::symmetrize                                     274.78 ms → 269.40 ms     (-1.96%)          26   →     26               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               274.78 ms → 269.40 ms     (-1.96%)          26   →     26               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             24.14 ms →  24.07 ms     (-0.31%)          26   →     26               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       226.80 ms → 221.08 ms     (-2.52%)          26   →     26               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            22.66 ms →  23.06 ms     (+1.80%)          26   →     26               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       86.11 ms →  93.18 ms     (+8.21%)          26   →     26               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   6.13 ms →   5.36 ms    (-12.60%)          26   →     26               
  │ │ ├ sirius::Density::mix                                              217.56 ms → 212.43 ms     (-2.36%)          26   →     26               
  │ │ │ ├ sirius::Density::mixer_input                                    919.27 μs → 917.42 μs     (-0.20%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function|inner                                  10.57 ms →  10.21 ms     (-3.41%)         334   →    334               
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.07 ms →   9.98 ms     (-0.91%)         334   →    334               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.07 ms →   9.98 ms     (-0.91%)         334   →    334               
+ │ │ │ └ sirius::Density::mixer_output                                     8.26 ms →   7.29 ms    (-11.78%)          26   →     26               
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 7.45 ms →   6.47 ms    (-13.17%)          26   →     26               
  │ │ ├ sirius::Potential::generate                                       580.87 ms → 577.63 ms     (-0.56%)          26   →     26               
  │ │ │ ├ sirius::Potential::poisson                                      138.25 ms → 136.52 ms     (-1.25%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                17.23 ms →  18.86 ms     (+9.46%)          26   →     26               
  │ │ │ │ └ sirius::Periodic_function|inner                                10.75 ms →  10.56 ms     (-1.75%)          26   →     26               
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.37 ms →  10.33 ms     (-0.34%)          26   →     26               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.37 ms →  10.33 ms     (-0.34%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function::add                                  562.50 μs → 545.39 μs     (-3.04%)          52   →     52               
  │ │ │ ├ sirius::Potential::xc                                            49.67 ms →  48.82 ms     (-1.72%)          26   →     26               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           47.39 ms →  46.46 ms     (-1.95%)          26   →     26               
  │ │ │ │   ├ sirius::Smooth_periodic_function                              2.96 ms →   3.06 ms     (+3.40%)          52   →     52               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.85 ms →   5.29 ms     (-9.71%)          26   →     26               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.63 ms →   6.40 ms     (-3.36%)          26   →     26               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.92 ms →  90.91 ms     (-0.01%)          26   →     26               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.98 ms → 292.61 ms     (-0.13%)          26   →     26               
  │ │ ├ sirius::Field4D::symmetrize                                       280.43 ms → 276.89 ms     (-1.26%)          26   →     26               
  │ │ │ └ sirius::symmetrize_function|fpw                                 280.43 ms → 276.88 ms     (-1.26%)          26   →     26               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.23 ms →  27.24 ms     (+0.06%)          26   →     26               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         225.79 ms → 221.85 ms     (-1.75%)          26   →     26               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.61 ms →  23.99 ms     (+1.61%)          26   →     26               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.83 ms →   5.51 ms     (-5.54%)          26   →     26               
  │ │ ├ sirius::Periodic_function|inner                                    10.40 ms →  10.16 ms     (-2.32%)         182   →    182               
  │ │ │ └ sirius::Periodic_function|inner_local                             9.98 ms →   9.90 ms     (-0.87%)         182   →    182               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.98 ms →   9.90 ms     (-0.87%)         182   →    182               
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.72 ms →  10.41 ms     (-2.92%)          78   →     78               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.32 ms →  10.10 ms     (-2.07%)          78   →     78               
  │ │ ├ sirius::Periodic_function::integrate                               10.60 ms →   9.89 ms     (-6.78%)          26   →     26               
  │ │ └ sirius::Density::get_magnetisation                                119.44 μs → 126.46 μs     (+5.87%)          26   →     26               
  │ │   └ sirius::Density::compute_atomic_mag_mom                         114.26 μs → 121.71 μs     (+6.53%)          26   →     26               
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                         7.23 ms →   5.61 ms    (-22.29%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       9.96 ms →   9.72 ms     (-2.40%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               9.95 ms →   9.68 ms     (-2.73%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      9.95 ms →   9.68 ms     (-2.73%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.27 ms →  10.11 ms     (-1.55%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.25 ms →  10.08 ms     (-1.59%)           3   →      3               
  ├ sirius::Periodic_function|inner                                        10.05 ms →  10.33 ms     (+2.86%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                10.04 ms →  10.33 ms     (+2.85%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.04 ms →  10.32 ms     (+2.85%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.36 ms →  10.44 ms     (+0.87%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.35 ms →  10.44 ms     (+0.88%)           1   →      1               
- └ sirius::finalize                                                      175.59 ms → 227.64 ms    (+29.64%)           1   →      1               
```
