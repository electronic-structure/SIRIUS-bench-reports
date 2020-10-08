# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   72.77 s  →  71.54 s      (-1.68%)           1   →      1               
  ├ sirius::initialize                                                      2.92 s  →   2.89 s      (-0.83%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.62 s  →   3.65 s      (+0.95%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               400.91 μs →   6.75 ms  (+1583.25%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       159.60 ms → 110.30 ms    (-30.89%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            71.24 ms →  46.70 ms    (-34.46%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          17.03 ms →  16.82 ms     (-1.21%)           1   →      1               
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        4.98 ms →   6.47 ms    (+29.92%)           1   →      1               
+ │ │   └ sirius::Unit_cell::get_symmetry                                  11.96 ms →  10.30 ms    (-13.88%)           1   →      1               
+ │ │     └ sirius::Unit_cell_symmetry                                     11.89 ms →  10.23 ms    (-14.01%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.80 ms →   2.76 ms     (-1.74%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            493.01 μs → 515.07 μs     (+4.48%)           1   →      1               
- │ │       └ sirius::Unit_cell_symmetry|mag                               15.26 μs →  17.13 μs    (+12.26%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.39 s  →   3.35 s      (-1.04%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           7.11 ms →   7.08 ms     (-0.45%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.72 ms →   3.67 ms     (-1.35%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.33 ms →   3.36 ms     (+0.91%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.29 ms →   3.32 ms     (+0.90%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.76 ms →   2.77 ms     (+0.46%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            495.93 μs → 515.85 μs     (+4.02%)           1   →      1               
+ │   │     └ sirius::Unit_cell_symmetry|mag                               17.86 μs →  14.38 μs    (-19.48%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      212.19 ms → 211.44 ms     (-0.35%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.14 ms →  15.33 ms     (+1.25%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.24 ms →  13.24 ms     (+0.00%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.31 ms →  56.40 ms     (+0.17%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.22 ms →  45.27 ms     (+0.12%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.68 ms →  60.40 ms     (-0.47%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   94.09 ms →  94.57 ms     (+0.51%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     70.55 ms →  70.63 ms     (+0.12%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 105.53 ms →  98.40 ms     (-6.75%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.99 ms →   1.99 ms     (+0.10%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 520.62 ms → 515.15 ms     (-1.05%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                    163.97 ms → 154.07 ms     (-6.04%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.18 μs →   1.91 μs    (-12.49%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                     163.91 ms → 154.01 ms     (-6.04%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.53 ms →  28.22 ms     (-1.09%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  10.86 ms →  10.88 ms     (+0.23%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                4.82 ms →   4.84 ms     (+0.44%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              7.80 μs →   7.76 μs     (-0.47%)           1   →      1               
  │     └ sirius::K_point::update                                          14.89 ms →  14.53 ms     (-2.46%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.97 ms →  10.58 ms     (-3.61%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.77 ms →   8.64 ms     (-1.48%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.59 ms →   2.53 ms     (-2.05%)           2   →      2               
  ├ sirius::Potential                                                      52.03 ms →  49.98 ms     (-3.94%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.90 ms →   2.91 ms     (+0.47%)           6   →      6               
  │ └ sirius::Potential::update                                            34.08 ms →  31.95 ms     (-6.24%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        33.64 ms →  31.54 ms     (-6.23%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.64 ms →  26.96 ms     (+1.19%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   6.47 ms →   4.05 ms    (-37.47%)           1   →      1               
  ├ sirius::Density                                                        42.33 ms →  38.46 ms     (-9.14%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.82 ms →   2.82 ms     (+0.06%)           2   →      2               
+ │ └ sirius::Density::update                                              36.55 ms →  32.68 ms    (-10.59%)           1   →      1               
+ │   └ sirius::Density::generate_pseudo_core_charge_density               36.33 ms →  32.46 ms    (-10.67%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.56 μs →  77.11 μs     (-0.58%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.68 ms →  27.28 ms     (+2.23%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   9.28 ms →   4.79 ms    (-48.42%)           1   →      1               
  ├ sirius::Density::initial_density                                       62.46 ms →  57.07 ms     (-8.63%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                   27.94 ms →  28.29 ms     (+1.25%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       7.58 ms →   5.10 ms    (-32.68%)           2   →      2               
+ │ └ sirius::Periodic_function::integrate                                  5.70 ms →   4.91 ms    (-13.83%)           1   →      1               
  ├ sirius::Potential::generate                                           372.14 ms → 364.57 ms     (-2.03%)           1   →      1               
+ │ ├ sirius::Potential::poisson                                           43.33 ms →  35.26 ms    (-18.63%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                    11.57 ms →   3.23 ms    (-72.10%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     6.09 ms →   5.61 ms     (-7.90%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.85 ms →   4.84 ms     (-0.06%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.84 ms →   4.84 ms     (+0.00%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      766.35 μs → 766.22 μs     (-0.02%)           2   →      2               
  │ ├ sirius::Potential::xc                                                53.28 ms →  53.40 ms     (+0.22%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.07 ms →  52.20 ms     (+0.24%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.55 ms →   2.54 ms     (-0.13%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.78 ms →   4.56 ms     (-4.57%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       3.08 ms →   3.72 ms    (+20.81%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.52 ms → 269.25 ms     (-0.10%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 228.00 ns →  80.00 ns    (-64.91%)           1   →      1               
+ ├ sirius::Hamiltonian0                                                    9.06 ms →   7.58 ms    (-16.33%)           1   →      1               
+ │ ├ sirius::Local_operator                                                8.20 ms →   7.05 ms    (-14.03%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.73 ms →   2.75 ms     (+0.43%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                     4.18 ms →   3.21 ms    (-23.14%)           1   →      1               
+ │ ├ sirius::Non_local_operator                                          290.35 μs → 122.64 μs    (-57.76%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                      111.50 μs → 114.25 μs     (+2.46%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       96.25 μs →  93.14 μs     (-3.23%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.30 s  →   1.27 s      (-1.87%)           1   →      1               
+ │ ├ sirius::Hamiltonian_k                                                76.93 ms →  56.97 ms    (-25.95%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 213.08 μs → 309.25 μs    (+45.14%)           1   →      1               
+ │ │ └ sirius::Beta_projectors_base::prepare                              76.72 ms →  56.66 ms    (-26.15%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.22 s  →   1.21 s      (-0.35%)           1   →      1               
+ │ │ ├ sddk::matrix_storage::matrix_storage                              109.95 ms →  76.68 ms    (-30.26%)           4   →      4               
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                    46.20 ms →  36.82 ms    (-20.30%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             6.51 ms →   7.03 ms     (+7.97%)           1   →      1               
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  512.79 ms → 312.42 ms    (-39.07%)           1   →      1               
+ │ │ │ ├ sirius::Local_operator::apply_h                                 422.61 ms → 244.22 ms    (-42.21%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.26 μs →   3.86 μs    (+18.31%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.30 μs →   2.79 μs    (+21.73%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           496.00 ns → 489.00 ns     (-1.41%)           1   →      1               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                          916.00 ns → 653.00 ns    (-28.71%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.00 ms →   3.13 ms     (+4.23%)           1   →      1               
+ │ │ │ ├ sirius::Beta_projectors_base::inner                              38.89 ms →  21.25 ms    (-45.36%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                                24.12 ms →  21.88 ms     (-9.27%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                     5.18 ms →   5.30 ms     (+2.36%)           2   →      2               
  │ │ │ └ sddk::inner                                                       4.97 ms →   5.09 ms     (+2.45%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              24.91 μs →  24.59 μs     (-1.27%)           2   →      2               
- │ │ ├ Eigensolver_cuda|zhegvdx                                           66.64 ms → 272.00 ms   (+308.16%)           1   →      1               
  │ │ └ sddk::transform                                                     2.81 ms →   2.82 ms     (+0.24%)           1   →      1               
- │ │   ├ sddk::transform|init                                             13.28 μs →  15.07 μs    (+13.51%)           1   →      1               
  │ │   └ sddk::transform|local                                            16.75 μs →  18.26 μs     (+9.00%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               605.00 ns → 390.00 ns    (-35.54%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     63.03 s  →  61.97 s      (-1.69%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.43 ms →   2.41 ms     (-0.56%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.26 s  →   3.25 s      (-0.25%)          19   →     19               
  │ │ ├ sirius::Hamiltonian0                                                5.32 ms →   5.67 ms     (+6.60%)          19   →     19               
  │ │ │ ├ sirius::Local_operator                                            4.53 ms →   4.88 ms     (+7.75%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              540.67 μs → 545.24 μs     (+0.85%)          19   →     19               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.67 ms →   3.22 ms    (+20.24%)          19   →     19               
  │ │ │ ├ sirius::Non_local_operator                                      251.58 μs → 257.03 μs     (+2.17%)          38   →     38               
  │ │ │ ├ sirius::D_operator::initialize                                  116.46 μs → 110.02 μs     (-5.53%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                   97.18 μs →  94.86 μs     (-2.38%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.03 s  →   2.03 s      (-0.12%)          19   →     19               
+ │ │ │ ├ sirius::Hamiltonian_k                                           214.72 μs → 177.20 μs    (-17.47%)          19   →     19               
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                             204.94 μs → 168.81 μs    (-17.63%)          19   →     19               
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                           7.08 μs →   6.00 μs    (-15.27%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.97 s  →   1.97 s      (-0.15%)          19   →     19               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             77.59 ms →  76.65 ms     (-1.21%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.18 ms →   8.24 ms     (+0.79%)         114   →    114               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            18.31 ms →  17.17 ms     (-6.23%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       473.78 μs → 459.63 μs     (-2.99%)          19   →     19               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.74 ms →   8.15 ms     (-6.73%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.87 s  →   1.87 s      (-0.04%)          19   →     19               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             52.55 ms →  50.31 ms     (-4.26%)         356   →    356               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            29.61 ms →  28.76 ms     (-2.90%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.87 μs →   2.01 μs     (+7.13%)         356   →    356               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.58 μs →   1.71 μs     (+8.14%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     447.65 ns → 434.01 ns     (-3.05%)         356   →    356               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    601.10 ns → 583.64 ns     (-2.90%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.96 ms →   2.77 ms     (-6.39%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.20 ms →   3.13 ms     (-2.04%)         356   →    356               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           8.38 ms →   7.82 ms     (-6.71%)         712   →    712               
  │ │ │ │   ├ sddk::orthogonalize                                           5.92 ms →   6.09 ms     (+2.95%)         356   →    356               
  │ │ │ │   │ ├ sddk::inner                                               896.98 μs → 941.59 μs     (+4.97%)         693   →    693               
  │ │ │ │   │ │ └ sddk::inner|local                                        24.75 μs →  23.97 μs     (-3.16%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 131.45 μs → 142.25 μs     (+8.22%)         356   →    356               
- │ │ │ │   │ ├ sddk::orthogonalize|transform                               1.89 ms →   2.12 ms    (+12.22%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             2.27 ms →   2.11 ms     (-7.12%)         337   →    337               
  │ │ │ │   │   ├ sddk::transform|init                                     19.71 μs →  19.10 μs     (-3.11%)         337   →    337               
  │ │ │ │   │   └ sddk::transform|local                                     8.22 μs →   7.98 μs     (-2.90%)        1.01 K →   1.01 K             
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.28 ms →   1.18 ms     (-8.23%)         356   →    356               
  │ │ │ │   │ └ sddk::inner                                                 1.21 ms →   1.11 ms     (-8.63%)         356   →    356               
  │ │ │ │   │   └ sddk::inner|local                                        24.06 μs →  23.36 μs     (-2.90%)         356   →    356               
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     36.38 ms →  38.61 ms     (+6.13%)         356   →    356               
+ │ │ │ │   ├ sirius::residuals                                             2.65 ms →   2.38 ms    (-10.22%)         340   →    340               
  │ │ │ │   │ ├ sddk::transform                                             1.25 ms →   1.18 ms     (-5.71%)         337   →    337               
  │ │ │ │   │ │ ├ sddk::transform|init                                     17.50 μs →  16.75 μs     (-4.28%)         337   →    337               
  │ │ │ │   │ │ └ sddk::transform|local                                    10.65 μs →  10.17 μs     (-4.51%)         674   →    674               
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.32 ms →   1.11 ms    (-16.12%)         337   →    337               
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       7.40 ms →   8.48 ms    (+14.51%)          54   →     54               
- │ │ │ │     └ sddk::transform                                             4.44 ms →   5.09 ms    (+14.71%)          89   →     89               
  │ │ │ │       ├ sddk::transform|init                                     11.73 μs →  11.09 μs     (-5.42%)          89   →     89               
  │ │ │ │       └ sddk::transform|local                                     9.78 μs →   9.34 μs     (-4.50%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           562.95 ns → 540.26 ns     (-4.03%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.40 μs →  19.29 μs     (-0.56%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.52 ms →   1.62 ms     (+6.38%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         568.17 ms → 569.72 ms     (+0.27%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               407.98 ms → 414.46 ms     (+1.59%)          19   →     19               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.79 μs →   7.79 μs     (-0.00%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.24 μs →   7.25 μs     (+0.04%)          19   →     19               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   39.67 ms →  35.18 ms    (-11.32%)          19   →     19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.02 μs →   7.23 μs     (+3.10%)          19   →     19               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        6.54 ms →   5.56 ms    (-14.91%)          19   →     19               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          32.09 ms →  28.58 ms    (-10.96%)          19   →     19               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       582.63 ns → 539.16 ns     (-7.46%)          19   →     19               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  106.24 ms → 110.83 ms     (+4.32%)          19   →     19               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.83 ms →   2.04 ms    (+11.48%)          19   →     19               
  │ │ │ │ └ sirius::Density::augment                                      229.24 ms → 230.60 ms     (+0.59%)          19   →     19               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           229.01 ms → 230.39 ms     (+0.60%)          19   →     19               
  │ │ │ ├ sirius::Field4D::symmetrize                                     132.87 ms → 127.61 ms     (-3.96%)          19   →     19               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               132.87 ms → 127.61 ms     (-3.96%)          19   →     19               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             51.00 ms →  44.16 ms    (-13.41%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        68.68 ms →  70.16 ms     (+2.14%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.55 ms →  12.65 ms     (+0.85%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.52 ms →  23.59 ms     (+0.29%)          19   →     19               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   3.79 ms →   4.06 ms     (+6.94%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              132.48 ms → 131.86 ms     (-0.47%)          19   →     19               
- │ │ │ ├ sirius::Density::mixer_input                                    393.29 μs → 545.15 μs    (+38.61%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function|inner                                   4.75 ms →   4.74 ms     (-0.07%)         229   →    229               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.62 ms →   4.62 ms     (-0.08%)         229   →    229               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.62 ms →   4.62 ms     (-0.08%)         229   →    229               
- │ │ │ └ sirius::Density::mixer_output                                     5.00 ms →   5.70 ms    (+14.01%)          19   →     19               
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 4.20 ms →   4.96 ms    (+18.16%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       363.93 ms → 355.84 ms     (-2.22%)          19   →     19               
+ │ │ │ ├ sirius::Potential::poisson                                       43.37 ms →  35.86 ms    (-17.32%)          19   →     19               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                11.55 ms →   4.18 ms    (-63.75%)          19   →     19               
+ │ │ │ │ └ sirius::Periodic_function|inner                                 6.10 ms →   5.24 ms    (-14.17%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.84 ms →   4.83 ms     (-0.18%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.84 ms →   4.83 ms     (-0.18%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  791.12 μs → 779.51 μs     (-1.47%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            45.16 ms →  45.01 ms     (-0.32%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.98 ms →  43.84 ms     (-0.34%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            679.81 μs → 677.93 μs     (-0.28%)          38   →     38               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.76 ms →   4.60 ms     (-3.24%)          19   →     19               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.43 ms →   3.49 ms     (+1.54%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.97 ms → 268.49 ms     (-0.18%)          19   →     19               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             237.53 ns → 238.74 ns     (+0.51%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        94.70 ms →  96.04 ms     (+1.41%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  94.70 ms →  96.04 ms     (+1.41%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.24 ms →  13.28 ms     (+0.31%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          68.36 ms →  69.55 ms     (+1.74%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.47 ms →  12.58 ms     (+0.86%)          19   →     19               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.79 ms →   4.15 ms     (+9.27%)          19   →     19               
  │ │ ├ sirius::Periodic_function|inner                                     4.72 ms →   4.63 ms     (-1.85%)         133   →    133               
  │ │ │ └ sirius::Periodic_function|inner_local                             4.55 ms →   4.55 ms     (-0.10%)         133   →    133               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.55 ms →   4.55 ms     (-0.10%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.74 ms →   4.75 ms     (+0.35%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.73 ms →   4.73 ms     (-0.05%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.53 ms →   4.54 ms     (+0.26%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 76.75 μs →  75.55 μs     (-1.56%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          71.73 μs →  70.65 μs     (-1.50%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.56 ms →   5.56 ms     (-0.02%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.79 ms →   4.59 ms     (-4.13%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.79 ms →   4.51 ms     (-5.72%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.79 ms →   4.51 ms     (-5.72%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.96 ms →   4.70 ms     (-5.15%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.95 ms →   4.70 ms     (-5.19%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.81 ms →   4.53 ms     (-5.95%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.81 ms →   4.52 ms     (-5.97%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.81 ms →   4.52 ms     (-5.97%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.96 ms →   4.71 ms     (-5.06%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.95 ms →   4.70 ms     (-5.14%)           1   →      1               
  └ sirius::finalize                                                      756.04 ms → 749.46 ms     (-0.87%)           1   →      1               
```
