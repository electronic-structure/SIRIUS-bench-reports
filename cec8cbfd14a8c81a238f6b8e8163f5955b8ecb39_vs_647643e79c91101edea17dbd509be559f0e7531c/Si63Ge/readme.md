# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   71.76 s  →  72.00 s      (+0.34%)           1   →      1               
  ├ sirius::initialize                                                      2.90 s  →   3.03 s      (+4.66%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.86 s  →   3.71 s      (-3.88%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                66.88 ms →   2.71 ms    (-95.95%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       122.47 ms → 141.53 ms    (+15.56%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            52.31 ms →  62.13 ms    (+18.78%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          17.77 ms →  17.19 ms     (-3.31%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        4.99 ms →   5.24 ms     (+5.11%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  12.73 ms →  11.87 ms     (-6.76%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     12.66 ms →  11.80 ms     (-6.80%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.77 ms →   2.79 ms     (+0.77%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            492.64 μs → 495.02 μs     (+0.48%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               15.96 μs →  16.50 μs     (+3.34%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.63 s  →   3.46 s      (-4.53%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           7.29 ms →   7.07 ms     (-2.98%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.76 ms →   3.71 ms     (-1.36%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.50 ms →   3.33 ms     (-4.73%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.44 ms →   3.29 ms     (-4.24%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.88 ms →   2.74 ms     (-5.02%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            511.65 μs → 517.05 μs     (+1.06%)           1   →      1               
+ │   │     └ sirius::Unit_cell_symmetry|mag                               20.94 μs →  13.97 μs    (-33.29%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      213.51 ms → 213.47 ms     (-0.02%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.13 ms →  15.14 ms     (+0.03%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.23 ms →  13.23 ms     (+0.03%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.42 ms →  56.38 ms     (-0.07%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.15 ms →  45.11 ms     (-0.08%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.67 ms →  60.41 ms     (-0.43%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.31 ms →  93.01 ms     (-0.33%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.95 ms →  69.76 ms     (-0.27%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  95.03 ms → 102.80 ms     (+8.17%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.99 ms →   1.97 ms     (-0.64%)           1   →      1               
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs                 653.23 ms → 560.33 ms    (-14.22%)           2   →      2               
- ├ sirius::K_point_set::create_k_mesh                                     87.20 ms → 132.13 ms    (+51.53%)           1   →      1               
- │ ├ sirius::K_point::K_point                                              1.57 μs →   2.28 μs    (+45.21%)           4   →      4               
- │ └ sirius::K_point_set::initialize                                      87.13 ms → 132.06 ms    (+51.56%)           1   →      1               
  │   └ sirius::K_point::initialize                                        27.86 ms →  29.33 ms     (+5.28%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  10.83 ms →  10.80 ms     (-0.24%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                4.81 ms →   4.83 ms     (+0.32%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                              8.62 μs →   7.33 μs    (-14.99%)           1   →      1               
- │     └ sirius::K_point::update                                          14.18 ms →  15.65 ms    (+10.36%)           1   →      1               
- │       └ sirius::Beta_projectors                                        10.30 ms →  11.69 ms    (+13.51%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.29 ms →   8.29 ms     (-0.00%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.55 ms →   2.52 ms     (-1.21%)           2   →      2               
  ├ sirius::Potential                                                      55.51 ms →  53.86 ms     (-2.97%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.91 ms →   2.88 ms     (-0.93%)           6   →      6               
  │ └ sirius::Potential::update                                            37.49 ms →  35.94 ms     (-4.15%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        37.09 ms →  35.56 ms     (-4.15%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               32.71 ms →  26.37 ms    (-19.37%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.82 ms →   8.68 ms   (+127.36%)           1   →      1               
  ├ sirius::Density                                                        43.22 ms →  39.84 ms     (-7.83%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.83 ms →   2.83 ms     (-0.10%)           2   →      2               
  │ └ sirius::Density::update                                              37.41 ms →  34.03 ms     (-9.05%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               37.12 ms →  33.72 ms     (-9.17%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.58 μs →  76.49 μs     (-1.41%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               32.95 ms →  26.33 ms    (-20.10%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.74 ms →   7.01 ms    (+87.39%)           1   →      1               
  ├ sirius::Density::initial_density                                       66.23 ms →  61.69 ms     (-6.86%)           1   →      1               
+ │ ├ sirius::Simulation_context::make_periodic_function                   37.78 ms →  26.67 ms    (-29.40%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       5.19 ms →   8.43 ms    (+62.36%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  4.50 ms →   4.54 ms     (+0.90%)           1   →      1               
  ├ sirius::Potential::generate                                           373.65 ms → 369.40 ms     (-1.14%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           45.78 ms →  42.39 ms     (-7.41%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.65 ms →  10.87 ms   (+198.11%)           1   →      1               
- │ │ └ sirius::Periodic_function|inner                                     4.83 ms →   5.92 ms    (+22.53%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.82 ms →   4.64 ms     (-3.87%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.82 ms →   4.63 ms     (-3.97%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      802.63 μs → 769.15 μs     (-4.17%)           2   →      2               
  │ ├ sirius::Potential::xc                                                52.19 ms →  51.46 ms     (-1.40%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               51.00 ms →  50.30 ms     (-1.37%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.55 ms →   2.57 ms     (+0.80%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.95 ms →   4.59 ms     (-7.27%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       3.60 ms →   2.85 ms    (-20.94%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.05 ms → 269.74 ms     (+0.26%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                 162.00 ns → 231.00 ns    (+42.59%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.42 ms →   8.67 ms     (+3.05%)           1   →      1               
  │ ├ sirius::Local_operator                                                7.82 ms →   7.60 ms     (-2.78%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.75 ms →   2.73 ms     (-0.40%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     3.85 ms →   3.81 ms     (-0.93%)           1   →      1               
- │ ├ sirius::Non_local_operator                                          167.97 μs → 390.18 μs   (+132.30%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                      108.82 μs → 110.86 μs     (+1.88%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                       88.56 μs → 115.08 μs    (+29.95%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.29 s  →   1.31 s      (+0.94%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                57.13 ms →  71.62 ms    (+25.36%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 215.00 μs → 250.13 μs    (+16.34%)           1   →      1               
- │ │ └ sirius::Beta_projectors_base::prepare                              56.91 ms →  71.37 ms    (+25.39%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.24 s  →   1.24 s      (-0.19%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               79.38 ms → 106.79 ms    (+34.54%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    37.68 ms →  36.57 ms     (-2.96%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             6.91 ms →   6.65 ms     (-3.63%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  335.47 ms → 450.98 ms    (+34.43%)           1   →      1               
- │ │ │ ├ sirius::Local_operator::apply_h                                 247.58 ms → 384.29 ms    (+55.22%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             5.03 μs →   3.50 μs    (-30.43%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.89 μs →   2.56 μs    (-34.22%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           673.00 ns → 493.00 ns    (-26.75%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          640.00 ns → 879.00 ns    (+37.34%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.27 ms →   3.08 ms     (-5.82%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                              21.27 ms →  21.24 ms     (-0.12%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                                31.65 ms →  21.16 ms    (-33.16%)           2   →      2               
- │ │ ├ sirius::Band::set_subspace_mtrx                                     5.28 ms →  14.63 ms   (+177.19%)           2   →      2               
- │ │ │ └ sddk::inner                                                       5.07 ms →  14.42 ms   (+184.56%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              25.19 μs →  24.29 μs     (-3.59%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          252.30 ms → 112.12 ms    (-55.56%)           1   →      1               
  │ │ └ sddk::transform                                                     2.80 ms →   2.86 ms     (+1.89%)           1   →      1               
+ │ │   ├ sddk::transform|init                                             14.72 μs →  13.09 μs    (-11.04%)           1   →      1               
  │ │   └ sddk::transform|local                                            18.15 μs →  16.93 μs     (-6.70%)           1   →      1               
- │ └ sirius::Beta_projectors_base::dismiss                               404.00 ns → 451.00 ns    (+11.63%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     61.98 s  →  61.96 s      (-0.04%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.45 ms →   2.42 ms     (-1.19%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.24 s  →   3.25 s      (+0.28%)          19   →     19               
  │ │ ├ sirius::Hamiltonian0                                                5.12 ms →   5.17 ms     (+1.09%)          19   →     19               
  │ │ │ ├ sirius::Local_operator                                            4.52 ms →   4.34 ms     (-3.99%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              561.42 μs → 535.68 μs     (-4.58%)          19   →     19               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.98 ms →   2.69 ms     (-9.92%)          19   →     19               
- │ │ │ ├ sirius::Non_local_operator                                      153.94 μs → 275.22 μs    (+78.78%)          38   →     38               
  │ │ │ ├ sirius::D_operator::initialize                                  118.87 μs → 112.59 μs     (-5.28%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                   92.67 μs →  95.93 μs     (+3.52%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.02 s  →   2.03 s      (+0.22%)          19   →     19               
+ │ │ │ ├ sirius::Hamiltonian_k                                           220.37 μs → 187.65 μs    (-14.85%)          19   →     19               
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                             212.17 μs → 177.89 μs    (-16.16%)          19   →     19               
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           5.77 μs →   7.09 μs    (+22.72%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.96 s  →   1.97 s      (+0.49%)          19   →     19               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             71.08 ms →  78.78 ms    (+10.83%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.12 ms →   7.92 ms     (-2.54%)         114   →    114               
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            17.18 ms →  15.35 ms    (-10.64%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       455.21 μs → 480.78 μs     (+5.62%)          19   →     19               
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.16 ms →   7.26 ms    (-11.05%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.86 s  →   1.87 s      (+0.18%)          19   →     19               
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             47.31 ms →  55.29 ms    (+16.85%)         356   →    356               
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                            28.38 ms →  34.74 ms    (+22.41%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.93 μs →   1.80 μs     (-7.02%)         356   →    356               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.63 μs →   1.56 μs     (-3.98%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     391.62 ns → 429.79 ns     (+9.75%)         356   →    356               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    568.75 ns → 607.34 ns     (+6.79%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.76 ms →   2.96 ms     (+7.34%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.05 ms →   3.11 ms     (+1.81%)         356   →    356               
- │ │ │ │   │ └ sirius::Non_local_operator::apply                           6.55 ms →   7.23 ms    (+10.34%)         712   →    712               
  │ │ │ │   ├ sddk::orthogonalize                                           5.40 ms →   5.30 ms     (-1.95%)         356   →    356               
- │ │ │ │   │ ├ sddk::inner                                               673.62 μs → 773.39 μs    (+14.81%)         693   →    693               
  │ │ │ │   │ │ └ sddk::inner|local                                        23.35 μs →  23.79 μs     (+1.86%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 142.50 μs → 132.36 μs     (-7.12%)         356   →    356               
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                               2.06 ms →   1.80 ms    (-12.79%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             1.99 ms →   1.96 ms     (-1.39%)         337   →    337               
  │ │ │ │   │   ├ sddk::transform|init                                     18.71 μs →  18.68 μs     (-0.12%)         337   →    337               
  │ │ │ │   │   └ sddk::transform|local                                     7.77 μs →   7.84 μs     (+0.92%)        1.01 K →   1.01 K             
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.12 ms →   1.08 ms     (-2.96%)         356   →    356               
  │ │ │ │   │ └ sddk::inner                                                 1.05 ms →   1.01 ms     (-3.21%)         356   →    356               
  │ │ │ │   │   └ sddk::inner|local                                        22.80 μs →  23.12 μs     (+1.43%)         356   →    356               
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     42.46 ms →  34.50 ms    (-18.75%)         356   →    356               
- │ │ │ │   ├ sirius::residuals                                             2.02 ms →   2.37 ms    (+17.05%)         340   →    340               
  │ │ │ │   │ ├ sddk::transform                                             1.12 ms →   1.19 ms     (+6.18%)         337   →    337               
  │ │ │ │   │ │ ├ sddk::transform|init                                     15.97 μs →  16.36 μs     (+2.47%)         337   →    337               
  │ │ │ │   │ │ └ sddk::transform|local                                     9.91 μs →  10.13 μs     (+2.15%)         674   →    674               
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               835.21 μs →   1.09 ms    (+30.84%)         337   →    337               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       7.60 ms →   7.48 ms     (-1.63%)          54   →     54               
  │ │ │ │     └ sddk::transform                                             4.56 ms →   4.49 ms     (-1.63%)          89   →     89               
  │ │ │ │       ├ sddk::transform|init                                     11.17 μs →  10.58 μs     (-5.21%)          89   →     89               
  │ │ │ │       └ sddk::transform|local                                     9.23 μs →   8.95 μs     (-3.00%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           533.21 ns → 529.95 ns     (-0.61%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.88 μs →  19.38 μs     (-2.48%)          19   →     19               
- │ │ ├ sirius::K_point_set::find_band_occupancies                          1.52 ms →   1.69 ms    (+11.31%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         562.93 ms → 562.97 ms     (+0.01%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               409.58 ms → 391.44 ms     (-4.43%)          19   →     19               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.89 μs →  11.42 μs    (+44.72%)          19   →     19               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.27 μs →  10.61 μs    (+45.90%)          19   →     19               
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   20.55 ms →  46.58 ms   (+126.70%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.24 μs →  10.38 μs    (+43.44%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        3.49 ms →  24.21 ms   (+594.10%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          16.02 ms →  21.30 ms    (+32.96%)          19   →     19               
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       788.05 ns → 604.74 ns    (-23.26%)          19   →     19               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  125.01 ms →  93.08 ms    (-25.54%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.91 ms →   2.06 ms     (+7.88%)          19   →     19               
  │ │ │ │ └ sirius::Density::augment                                      229.20 ms → 208.86 ms     (-8.87%)          19   →     19               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           228.98 ms → 208.65 ms     (-8.88%)          19   →     19               
- │ │ │ ├ sirius::Field4D::symmetrize                                     124.56 ms → 144.50 ms    (+16.01%)          19   →     19               
- │ │ │ │ └ sirius::symmetrize_function|fpw                               124.55 ms → 144.50 ms    (+16.01%)          19   →     19               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             43.15 ms →  61.26 ms    (+41.96%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        67.95 ms →  69.94 ms     (+2.93%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.82 ms →  12.66 ms     (-1.27%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       24.12 ms →  23.62 ms     (-2.05%)          19   →     19               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   4.67 ms →   3.41 ms    (-26.98%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              130.60 ms → 134.89 ms     (+3.28%)          19   →     19               
+ │ │ │ ├ sirius::Density::mixer_input                                    802.42 μs → 290.27 μs    (-63.83%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function|inner                                   4.69 ms →   4.95 ms     (+5.70%)         229   →    229               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.65 ms →   4.82 ms     (+3.55%)         229   →    229               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.65 ms →   4.82 ms     (+3.55%)         229   →    229               
  │ │ │ └ sirius::Density::mixer_output                                     4.91 ms →   5.31 ms     (+8.20%)          19   →     19               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 4.31 ms →   4.61 ms     (+6.81%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       366.18 ms → 362.89 ms     (-0.90%)          19   →     19               
  │ │ │ ├ sirius::Potential::poisson                                       45.79 ms →  42.53 ms     (-7.12%)          19   →     19               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 3.63 ms →  11.11 ms   (+206.15%)          19   →     19               
- │ │ │ │ └ sirius::Periodic_function|inner                                 4.84 ms →   5.90 ms    (+21.98%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.82 ms →   4.64 ms     (-3.79%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.82 ms →   4.64 ms     (-3.79%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  777.27 μs → 788.50 μs     (+1.45%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            45.25 ms →  44.99 ms     (-0.59%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           44.06 ms →  43.81 ms     (-0.57%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            666.19 μs → 678.41 μs     (+1.83%)          38   →     38               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.78 ms →   4.63 ms     (-3.15%)          19   →     19               
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.62 ms →   3.25 ms    (-10.15%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.54 ms → 269.08 ms     (+0.20%)          19   →     19               
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             139.58 ns → 212.84 ns    (+52.49%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        94.29 ms →  96.21 ms     (+2.03%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  94.29 ms →  96.21 ms     (+2.03%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.29 ms →  13.26 ms     (-0.21%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          67.79 ms →  69.70 ms     (+2.82%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.58 ms →  12.60 ms     (+0.20%)          19   →     19               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.50 ms →   3.64 ms    (-19.19%)          19   →     19               
  │ │ ├ sirius::Periodic_function|inner                                     4.58 ms →   4.93 ms     (+7.68%)         133   →    133               
  │ │ │ └ sirius::Periodic_function|inner_local                             4.55 ms →   4.76 ms     (+4.50%)         133   →    133               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.55 ms →   4.76 ms     (+4.50%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.74 ms →   4.66 ms     (-1.54%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.73 ms →   4.54 ms     (-3.98%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.55 ms →   4.56 ms     (+0.33%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 74.60 μs →  73.50 μs     (-1.48%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          69.87 μs →  68.59 μs     (-1.82%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.69 ms →   5.63 ms     (-1.05%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.81 ms →   4.84 ms     (+0.73%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.79 ms →   4.79 ms     (-0.14%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.79 ms →   4.79 ms     (-0.14%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                5.04 ms →   4.74 ms     (-5.83%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.98 ms →   4.58 ms     (-7.97%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         5.09 ms →   4.77 ms     (-6.41%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 5.09 ms →   4.76 ms     (-6.44%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        5.09 ms →   4.76 ms     (-6.44%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.97 ms →   4.51 ms     (-9.13%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.96 ms →   4.51 ms     (-9.14%)           1   →      1               
  └ sirius::finalize                                                      756.78 ms → 751.46 ms     (-0.70%)           1   →      1               
```
