# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  132.44 s  → 132.54 s      (+0.08%)           1   →      1               
  ├ sirius::initialize                                                      2.73 s  →   2.73 s      (+0.17%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  2.93 s  →   3.43 s     (+17.25%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                24.35 ms →  37.39 ms    (+53.57%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       171.51 ms → 668.09 ms   (+289.54%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            73.51 ms → 321.86 ms   (+337.83%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          24.39 ms →  24.29 ms     (-0.42%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.29 ms →   6.25 ms     (-0.65%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  18.06 ms →  18.00 ms     (-0.33%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     18.04 ms →  17.98 ms     (-0.33%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.15 ms →   4.17 ms     (+0.45%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.34 ms →   2.34 ms     (-0.17%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              105.38 μs → 102.11 μs     (-3.10%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.69 s  →   2.69 s      (-0.23%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.83 ms →  10.92 ms     (+0.82%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.41 ms →   4.48 ms     (+1.62%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.39 ms →   6.40 ms     (+0.22%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.37 ms →   6.39 ms     (+0.19%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.89 ms →   3.89 ms     (+0.07%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.32 ms →   2.33 ms     (+0.44%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              101.25 μs →  99.74 μs     (-1.49%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       62.86 ms →  63.34 ms     (+0.76%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.13 ms →   5.16 ms     (+0.54%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.46 ms →   4.53 ms     (+1.61%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.71 ms →  21.70 ms     (-0.04%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.81 ms →  14.82 ms     (+0.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.75 ms →  19.80 ms     (+0.27%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  175.56 ms → 172.10 ms     (-1.97%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    132.86 ms → 129.72 ms     (-2.36%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 183.25 ms → 181.30 ms     (-1.07%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.36 ms →   1.33 ms     (-2.38%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 291.56 ms → 296.27 ms     (+1.61%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     35.49 ms →  35.83 ms     (+0.95%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              2.70 μs →   2.68 μs     (-0.91%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      35.40 ms →  35.74 ms     (+0.94%)           1   →      1               
  │   └ sirius::K_point::initialize                                        35.32 ms →  35.65 ms     (+0.94%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.12 ms →  18.15 ms     (+0.16%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.20 ms →   8.16 ms     (-0.49%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              9.63 μs →   9.29 μs     (-3.53%)           1   →      1               
  │     └ sirius::K_point::update                                          12.34 ms →  12.45 ms     (+0.87%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.11 ms →   6.03 ms     (-1.33%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.52 ms →   3.44 ms     (-2.18%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.31 ms →   5.16 ms     (-2.83%)           2   →      2               
  ├ sirius::Potential                                                     158.68 ms → 159.75 ms     (+0.67%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.94 ms →   5.78 ms     (-2.63%)           6   →      6               
  │ └ sirius::Potential::update                                           122.30 ms → 124.32 ms     (+1.65%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       121.50 ms → 123.63 ms     (+1.75%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.61 ms → 109.17 ms     (-2.19%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   8.98 ms →  13.56 ms    (+50.92%)           1   →      1               
  ├ sirius::Density                                                       135.02 ms → 134.88 ms     (-0.11%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.54 ms →   5.12 ms     (-7.52%)           2   →      2               
  │ └ sirius::Density::update                                             123.66 ms → 124.37 ms     (+0.57%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              123.23 ms → 123.96 ms     (+0.60%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               109.13 μs → 104.19 μs     (-4.53%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              113.30 ms → 112.59 ms     (-0.62%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   9.36 ms →  10.81 ms    (+15.48%)           1   →      1               
  ├ sirius::Density::initial_density                                      174.43 ms → 174.03 ms     (-0.23%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  110.86 ms → 111.85 ms     (+0.89%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                      10.78 ms →   9.88 ms     (-8.33%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  9.75 ms →   9.81 ms     (+0.64%)           1   →      1               
  ├ sirius::Potential::generate                                           593.68 ms → 593.43 ms     (-0.04%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          137.28 ms → 138.55 ms     (+0.92%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                    15.47 ms →  17.11 ms    (+10.59%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.33 ms →  11.34 ms     (+9.83%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.31 ms →  11.32 ms     (+9.81%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.30 ms →  11.31 ms     (+9.82%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      565.17 μs → 557.90 μs     (-1.29%)           2   →      2               
  │ ├ sirius::Potential::xc                                                54.47 ms →  53.35 ms     (-2.07%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.04 ms →  51.02 ms     (-1.95%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.73 ms →   5.64 ms     (-1.63%)           2   →      2               
+ │ │   └ sirius::Smooth_periodic_function::fft_transform                   6.02 ms →   5.02 ms    (-16.64%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.92 ms →   5.72 ms     (-3.35%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        92.65 ms →  94.02 ms     (+1.48%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 300.82 ms → 299.33 ms     (-0.50%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.39 ms →   8.39 ms     (+0.06%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.04 ms →   8.03 ms     (-0.04%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.78 ms →   4.76 ms     (-0.41%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.33 ms →   2.36 ms     (+0.94%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           62.45 μs →  63.92 μs     (+2.37%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       95.87 μs →  96.41 μs     (+0.56%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       74.37 μs →  80.67 μs     (+8.47%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.86 s  →   1.87 s      (+0.56%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.71 ms →  18.68 ms     (-0.17%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 202.06 μs → 173.36 μs    (-14.20%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.51 ms →  18.51 ms     (-0.02%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.84 s  →   1.85 s      (+0.57%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              126.29 ms → 128.67 ms     (+1.88%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    53.32 ms →  52.50 ms     (-1.54%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.44 ms →  21.50 ms     (+0.26%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  638.12 ms → 637.92 ms     (-0.03%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 298.09 ms → 298.08 ms     (-0.00%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.68 μs →   3.23 μs    (-12.17%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.69 μs →   2.24 μs    (-16.59%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           374.00 ns → 437.00 ns    (+16.84%)           1   →      1               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                          627.00 ns → 502.00 ns    (-19.94%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.22 ms →   9.22 ms     (+0.08%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             120.88 ms → 121.45 ms     (+0.47%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               104.94 ms → 104.56 ms     (-0.37%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    38.49 ms →  38.35 ms     (-0.36%)           2   →      2               
  │ │ │ └ sddk::inner                                                      37.95 ms →  37.82 ms     (-0.34%)           2   →      2               
- │ │ │   └ sddk::inner|local                                              22.50 μs →  29.64 μs    (+31.73%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           56.62 ms →  60.90 ms     (+7.56%)           1   →      1               
  │ │ └ sddk::transform                                                    31.56 ms →  31.51 ms     (-0.16%)           1   →      1               
- │ │   ├ sddk::transform|init                                             11.44 μs →  13.26 μs    (+15.87%)           1   →      1               
- │ │   └ sddk::transform|local                                            11.35 μs →  13.08 μs    (+15.24%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                               530.00 ns → 547.00 ns     (+3.21%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    122.77 s  → 122.36 s      (-0.33%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.88 ms →   5.81 ms     (-1.12%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.71 s  →   4.69 s      (-0.36%)          26   →     26               
  │ │ ├ sirius::Hamiltonian0                                                5.24 ms →   5.24 ms     (-0.04%)          26   →     26               
  │ │ │ ├ sirius::Local_operator                                            4.87 ms →   4.88 ms     (+0.10%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function                                1.02 ms →   1.01 ms     (-0.95%)          26   →     26               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.96 ms →   2.97 ms     (+0.54%)          26   →     26               
  │ │ │ ├ sirius::Non_local_operator                                       65.17 μs →  64.61 μs     (-0.85%)          52   →     52               
  │ │ │ ├ sirius::D_operator::initialize                                   96.00 μs →  92.32 μs     (-3.83%)          26   →     26               
  │ │ │ └ sirius::Q_operator::initialize                                   76.89 μs →  75.59 μs     (-1.69%)          26   →     26               
  │ │ ├ sirius::Band::solve                                                 2.75 s  →   2.73 s      (-0.60%)          26   →     26               
  │ │ │ ├ sirius::Hamiltonian_k                                           162.93 μs → 162.18 μs     (-0.46%)          26   →     26               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             156.89 μs → 156.66 μs     (-0.14%)          26   →     26               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           4.43 μs →   4.10 μs     (-7.51%)          26   →     26               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.61 s  →   2.57 s      (-1.41%)          26   →     26               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             95.92 ms →  95.49 ms     (-0.45%)          26   →     26               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.67 ms →   7.81 ms     (+1.85%)         156   →    156               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             6.01 ms →   6.02 ms     (+0.14%)          26   →     26               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       352.07 μs → 348.16 μs     (-1.11%)          26   →     26               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.32 ms →   2.33 ms     (+0.31%)          52   →     52               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.47 s  →   2.43 s      (-1.47%)          26   →     26               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            125.28 ms → 129.87 ms     (+3.67%)         283   →    271       (-4.24%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            49.89 ms →  51.98 ms     (+4.19%)         283   →    271       (-4.24%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.75 μs →   1.72 μs     (-1.68%)         283   →    271       (-4.24%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.42 μs →   1.39 μs     (-1.94%)         283   →    271       (-4.24%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     323.06 ns → 307.23 ns     (-4.90%)         283   →    271       (-4.24%)
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    428.59 ns → 405.67 ns     (-5.35%)         283   →    271       (-4.24%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.41 ms →   7.43 ms     (+0.23%)         283   →    271       (-4.24%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        22.64 ms →  23.79 ms     (+5.05%)         283   →    271       (-4.24%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          22.66 ms →  23.33 ms     (+2.97%)         566   →    542       (-4.24%)
  │ │ │ │   ├ sddk::orthogonalize                                          31.80 ms →  32.95 ms     (+3.61%)         283   →    271       (-4.24%)
  │ │ │ │   │ ├ sddk::inner                                                 4.70 ms →   4.88 ms     (+3.88%)         540   →    516       (-4.44%)
  │ │ │ │   │ │ └ sddk::inner|local                                        21.63 μs →  21.03 μs     (-2.79%)         540   →    516       (-4.44%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 590.40 μs → 621.69 μs     (+5.30%)         283   →    271       (-4.24%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.35 ms →   9.75 ms     (+4.30%)         283   →    271       (-4.24%)
  │ │ │ │   │ └ sddk::transform                                            14.20 ms →  14.69 ms     (+3.46%)         257   →    245       (-4.67%)
  │ │ │ │   │   ├ sddk::transform|init                                     17.52 μs →  16.80 μs     (-4.13%)         257   →    245       (-4.67%)
  │ │ │ │   │   └ sddk::transform|local                                     7.25 μs →   6.68 μs     (-7.81%)         771   →    735       (-4.67%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               8.94 ms →   9.27 ms     (+3.67%)         283   →    271       (-4.24%)
  │ │ │ │   │ └ sddk::inner                                                 8.70 ms →   9.02 ms     (+3.72%)         283   →    271       (-4.24%)
  │ │ │ │   │   └ sddk::inner|local                                        21.87 μs →  20.75 μs     (-5.15%)         283   →    271       (-4.24%)
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     33.41 ms →  32.81 ms     (-1.80%)         283   →    271       (-4.24%)
  │ │ │ │   ├ sirius::residuals                                            13.39 ms →  13.88 ms     (+3.67%)         274   →    262       (-4.38%)
  │ │ │ │   │ ├ sddk::transform                                            12.12 ms →  12.58 ms     (+3.85%)         264   →    252       (-4.55%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     13.81 μs →  12.63 μs     (-8.52%)         264   →    252       (-4.55%)
  │ │ │ │   │ │ └ sddk::transform|local                                     9.41 μs →   9.13 μs     (-2.91%)         528   →    504       (-4.55%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.55 ms →   1.61 ms     (+3.98%)         264   →    252       (-4.55%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      76.22 ms →  76.23 ms     (+0.01%)          53   →     53               
  │ │ │ │     └ sddk::transform                                            50.26 ms →  50.27 ms     (+0.01%)          80   →     80               
  │ │ │ │       ├ sddk::transform|init                                      9.95 μs →  10.19 μs     (+2.42%)          80   →     80               
  │ │ │ │       └ sddk::transform|local                                     8.86 μs →   9.14 μs     (+3.15%)         107   →    107               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           457.85 ns → 443.35 ns     (-3.17%)          26   →     26               
- │ │ │ └ sirius::K_point_set::sync_band_energies                          29.11 μs →  60.10 μs   (+106.45%)          26   →     26               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        638.03 μs → 595.95 μs     (-6.60%)          26   →     26               
  │ │ ├ sirius::Density::generate                                         766.10 ms → 765.48 ms     (-0.08%)          26   →     26               
  │ │ │ ├ sirius::Density::generate_valence                               400.35 ms → 401.26 ms     (+0.23%)          26   →     26               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.87 μs →   8.07 μs     (+2.56%)          26   →     26               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.35 μs →   7.21 μs     (-1.95%)          26   →     26               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.30 ms → 100.26 ms     (-0.04%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.55 μs →   7.96 μs     (+5.33%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.12 ms     (+0.07%)          26   →     26               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.28 ms →  91.22 ms     (-0.08%)          26   →     26               
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       685.58 ns → 560.35 ns    (-18.27%)          26   →     26               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  161.91 ms → 162.20 ms     (+0.18%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.65 ms →   1.64 ms     (-0.35%)          26   →     26               
  │ │ │ │ └ sirius::Density::augment                                       88.30 ms →  88.29 ms     (-0.01%)          26   →     26               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.06 ms →  88.06 ms     (+0.00%)          26   →     26               
  │ │ │ ├ sirius::Field4D::symmetrize                                     272.37 ms → 271.88 ms     (-0.18%)          26   →     26               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               272.37 ms → 271.88 ms     (-0.18%)          26   →     26               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             23.93 ms →  24.22 ms     (+1.21%)          26   →     26               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       224.32 ms → 223.62 ms     (-0.31%)          26   →     26               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            22.92 ms →  22.85 ms     (-0.32%)          26   →     26               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       81.13 ms →  81.55 ms     (+0.52%)          26   →     26               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   8.65 ms →   7.17 ms    (-17.11%)          26   →     26               
  │ │ ├ sirius::Density::mix                                              213.75 ms → 213.31 ms     (-0.21%)          26   →     26               
  │ │ │ ├ sirius::Density::mixer_input                                    971.90 μs → 979.04 μs     (+0.74%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function|inner                                  10.26 ms →  10.25 ms     (-0.16%)         334   →    334               
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.00 ms →   9.96 ms     (-0.38%)         334   →    334               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.00 ms →   9.96 ms     (-0.38%)         334   →    334               
  │ │ │ └ sirius::Density::mixer_output                                     7.18 ms →   6.82 ms     (-5.06%)          26   →     26               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.32 ms →   5.97 ms     (-5.59%)          26   →     26               
  │ │ ├ sirius::Potential::generate                                       579.51 ms → 578.46 ms     (-0.18%)          26   →     26               
  │ │ │ ├ sirius::Potential::poisson                                      137.43 ms → 137.10 ms     (-0.24%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                15.54 ms →  16.50 ms     (+6.24%)          26   →     26               
  │ │ │ │ └ sirius::Periodic_function|inner                                10.60 ms →  10.65 ms     (+0.51%)          26   →     26               
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.43 ms →  10.30 ms     (-1.30%)          26   →     26               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.43 ms →  10.30 ms     (-1.30%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function::add                                  556.04 μs → 563.00 μs     (+1.25%)          52   →     52               
  │ │ │ ├ sirius::Potential::xc                                            49.91 ms →  48.88 ms     (-2.06%)          26   →     26               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           47.49 ms →  46.46 ms     (-2.16%)          26   →     26               
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.05 ms →   3.06 ms     (+0.40%)          52   →     52               
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               6.29 ms →   5.25 ms    (-16.49%)          26   →     26               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.45 ms →   6.34 ms     (-1.81%)          26   →     26               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.91 ms →  90.92 ms     (+0.01%)          26   →     26               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.37 ms → 292.74 ms     (+0.13%)          26   →     26               
  │ │ ├ sirius::Field4D::symmetrize                                       276.40 ms → 278.00 ms     (+0.58%)          26   →     26               
  │ │ │ └ sirius::symmetrize_function|fpw                                 276.40 ms → 278.00 ms     (+0.58%)          26   →     26               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               26.83 ms →  27.22 ms     (+1.44%)          26   →     26               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         221.99 ms → 223.29 ms     (+0.59%)          26   →     26               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.75 ms →  23.69 ms     (-0.23%)          26   →     26               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.33 ms →   5.50 ms     (+3.18%)          26   →     26               
  │ │ ├ sirius::Periodic_function|inner                                    10.16 ms →  10.21 ms     (+0.54%)         182   →    182               
  │ │ │ └ sirius::Periodic_function|inner_local                             9.88 ms →   9.79 ms     (-0.88%)         182   →    182               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.88 ms →   9.79 ms     (-0.87%)         182   →    182               
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.52 ms →  10.39 ms     (-1.31%)          78   →     78               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.25 ms →  10.14 ms     (-1.07%)          78   →     78               
  │ │ ├ sirius::Periodic_function::integrate                                9.93 ms →   9.88 ms     (-0.51%)          26   →     26               
  │ │ └ sirius::Density::get_magnetisation                                125.21 μs → 122.51 μs     (-2.16%)          26   →     26               
  │ │   └ sirius::Density::compute_atomic_mag_mom                         120.89 μs → 117.99 μs     (-2.39%)          26   →     26               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         7.12 ms →   7.43 ms     (+4.38%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                      10.19 ms →  10.05 ms     (-1.31%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                              10.11 ms →   9.83 ms     (-2.77%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                     10.11 ms →   9.83 ms     (-2.77%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.45 ms →  10.13 ms     (-3.06%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.44 ms →  10.11 ms     (-3.20%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         9.77 ms →   9.80 ms     (+0.29%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 9.65 ms →   9.78 ms     (+1.37%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        9.65 ms →   9.78 ms     (+1.37%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.20 ms →  10.14 ms     (-0.56%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.07 ms →  10.13 ms     (+0.62%)           1   →      1               
  └ sirius::finalize                                                      224.12 ms → 221.38 ms     (-1.23%)           1   →      1               
```
