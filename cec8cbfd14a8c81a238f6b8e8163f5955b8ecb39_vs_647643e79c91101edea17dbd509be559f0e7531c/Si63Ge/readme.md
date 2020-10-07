# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   71.51 s  →  71.64 s      (+0.18%)           1   →      1               
  ├ sirius::initialize                                                      2.95 s  →   2.94 s      (-0.37%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.72 s  →   3.64 s      (-2.20%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                 6.80 ms →   3.73 ms    (-45.19%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       153.02 ms → 121.19 ms    (-20.80%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            67.58 ms →  50.39 ms    (-25.44%)           2   →      2               
- │ │ └ sirius::Unit_cell::update                                          17.76 ms →  20.32 ms    (+14.42%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.60 ms →   3.84 ms     (+6.54%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  14.10 ms →  16.42 ms    (+16.47%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     14.03 ms →  16.35 ms    (+16.53%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.76 ms →   2.74 ms     (-0.79%)           1   →      1               
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                              1.03 ms → 494.46 μs    (-52.13%)           1   →      1               
+ │ │       └ sirius::Unit_cell_symmetry|mag                               17.68 μs →  15.65 μs    (-11.46%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.47 s  →   3.41 s      (-1.82%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.88 ms →   7.19 ms     (+4.48%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.52 ms →   3.68 ms     (+4.35%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.31 ms →   3.46 ms     (+4.56%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.27 ms →   3.42 ms     (+4.36%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.73 ms →   2.79 ms     (+2.15%)           1   →      1               
- │   │     ├ sirius::Unit_cell_symmetry|equiv                            503.42 μs → 584.84 μs    (+16.17%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               15.25 μs →  14.48 μs     (-5.08%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      213.76 ms → 212.45 ms     (-0.61%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.14 ms →  15.17 ms     (+0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.25 ms →  13.36 ms     (+0.80%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.42 ms →  56.48 ms     (+0.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.17 ms →  45.15 ms     (-0.04%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.36 ms →  60.23 ms     (-0.22%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   92.93 ms →  93.58 ms     (+0.69%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.44 ms →  69.97 ms     (+0.76%)           2   →      2               
- │   ├ sddk::Gvec_shells                                                  95.86 ms → 145.44 ms    (+51.72%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.98 ms →   1.97 ms     (-0.54%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 559.27 ms → 512.46 ms     (-8.37%)           2   →      2               
+ ├ sirius::K_point_set::create_k_mesh                                    145.51 ms → 129.76 ms    (-10.82%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.29 μs →   1.40 μs    (-38.98%)           4   →      4               
+ │ └ sirius::K_point_set::initialize                                     145.45 ms → 129.70 ms    (-10.83%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.14 ms →  28.32 ms     (+0.62%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  11.06 ms →  10.81 ms     (-2.28%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                4.90 ms →   4.84 ms     (-1.32%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                             10.38 μs →  10.12 μs     (-2.49%)           1   →      1               
  │     └ sirius::K_point::update                                          14.21 ms →  14.61 ms     (+2.75%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.25 ms →  10.82 ms     (+5.57%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.28 ms →   8.72 ms     (+5.42%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.54 ms →   2.53 ms     (-0.67%)           2   →      2               
  ├ sirius::Potential                                                      54.82 ms →  52.87 ms     (-3.56%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.93 ms →   2.89 ms     (-1.31%)           6   →      6               
  │ └ sirius::Potential::update                                            36.61 ms →  34.90 ms     (-4.66%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        36.21 ms →  34.50 ms     (-4.71%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               31.82 ms →  26.19 ms    (-17.70%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.83 ms →   7.79 ms   (+103.26%)           1   →      1               
  ├ sirius::Density                                                        42.35 ms →  39.05 ms     (-7.79%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.84 ms →   2.83 ms     (-0.57%)           2   →      2               
  │ └ sirius::Density::update                                              36.53 ms →  33.26 ms     (-8.95%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               36.23 ms →  32.95 ms     (-9.05%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.99 μs →  77.38 μs     (-0.78%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               32.36 ms →  26.26 ms    (-18.85%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.48 ms →   6.30 ms    (+81.20%)           1   →      1               
  ├ sirius::Density::initial_density                                       64.94 ms →  60.72 ms     (-6.50%)           1   →      1               
+ │ ├ sirius::Simulation_context::make_periodic_function                   36.94 ms →  26.30 ms    (-28.80%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       4.29 ms →   8.14 ms    (+89.89%)           2   →      2               
+ │ └ sirius::Periodic_function::integrate                                  5.72 ms →   4.53 ms    (-20.84%)           1   →      1               
  ├ sirius::Potential::generate                                           372.58 ms → 368.88 ms     (-0.99%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           45.11 ms →  41.38 ms     (-8.27%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     2.87 ms →  10.60 ms   (+269.60%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     5.68 ms →   5.39 ms     (-5.20%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.84 ms →   4.65 ms     (-3.93%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.83 ms →   4.63 ms     (-4.11%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      787.34 μs → 844.76 μs     (+7.29%)           2   →      2               
  │ ├ sirius::Potential::xc                                                51.54 ms →  51.04 ms     (-0.98%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               50.37 ms →  49.87 ms     (-0.99%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.55 ms →   2.59 ms     (+1.23%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.26 ms →   4.15 ms     (-2.58%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.74 ms →   3.95 ms     (+5.59%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.25 ms → 269.47 ms     (+0.08%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 241.00 ns → 265.00 ns     (+9.96%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    7.51 ms →   7.28 ms     (-3.01%)           1   →      1               
  │ ├ sirius::Local_operator                                                7.12 ms →   6.71 ms     (-5.69%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.75 ms →   2.73 ms     (-0.41%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     3.35 ms →   3.13 ms     (-6.52%)           1   →      1               
- │ ├ sirius::Non_local_operator                                           62.43 μs → 114.85 μs    (+83.97%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                      107.35 μs → 154.56 μs    (+43.98%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       90.66 μs →  99.08 μs     (+9.29%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.29 s  →   1.28 s      (-0.50%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                60.69 ms →  57.22 ms     (-5.71%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 207.02 μs → 352.24 μs    (+70.15%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              60.48 ms →  56.87 ms     (-5.97%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.22 s  →   1.22 s      (-0.25%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               77.07 ms →  91.78 ms    (+19.10%)           4   →      4               
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                    45.34 ms →  37.13 ms    (-18.10%)           1   →      1               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                             8.87 ms →   7.24 ms    (-18.35%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  336.42 ms → 382.51 ms    (+13.70%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 247.76 ms → 271.21 ms     (+9.47%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             4.05 μs →   3.87 μs     (-4.49%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.71 μs →   2.99 μs    (+10.56%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           504.00 ns → 492.00 ns     (-2.38%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          556.00 ns → 795.00 ns    (+42.99%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.24 ms →   3.06 ms     (-5.43%)           1   →      1               
- │ │ │ ├ sirius::Beta_projectors_base::inner                              21.28 ms →  39.46 ms    (+85.41%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                                32.05 ms →  34.36 ms     (+7.23%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                     5.26 ms →   5.23 ms     (-0.68%)           2   →      2               
  │ │ │ └ sddk::inner                                                       5.06 ms →   5.02 ms     (-0.69%)           2   →      2               
- │ │ │   └ sddk::inner|local                                              19.80 μs →  25.19 μs    (+27.20%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          248.68 ms → 201.45 ms    (-18.99%)           1   →      1               
  │ │ └ sddk::transform                                                     2.82 ms →   2.82 ms     (+0.20%)           1   →      1               
- │ │   ├ sddk::transform|init                                             12.82 μs →  14.81 μs    (+15.53%)           1   →      1               
  │ │   └ sddk::transform|local                                            17.97 μs →  17.96 μs     (-0.01%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                               376.00 ns → 389.00 ns     (+3.46%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     61.76 s  →  62.02 s      (+0.41%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.44 ms →   2.43 ms     (-0.66%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.23 s  →   3.25 s      (+0.42%)          19   →     19               
- │ │ ├ sirius::Hamiltonian0                                                4.77 ms →   5.48 ms    (+15.02%)          19   →     19               
- │ │ │ ├ sirius::Local_operator                                            4.20 ms →   4.78 ms    (+13.62%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              552.19 μs → 555.36 μs     (+0.57%)          19   →     19               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.65 ms →   3.04 ms    (+14.88%)          19   →     19               
- │ │ │ ├ sirius::Non_local_operator                                      121.98 μs → 211.22 μs    (+73.16%)          38   →     38               
+ │ │ │ ├ sirius::D_operator::initialize                                  129.06 μs → 109.28 μs    (-15.33%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                  103.67 μs →  96.56 μs     (-6.86%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.02 s  →   2.03 s      (+0.34%)          19   →     19               
+ │ │ │ ├ sirius::Hamiltonian_k                                           235.01 μs → 207.36 μs    (-11.77%)          19   →     19               
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                             225.67 μs → 197.92 μs    (-12.30%)          19   →     19               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           6.34 μs →   6.19 μs     (-2.45%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.95 s  →   1.96 s      (+0.46%)          19   →     19               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             71.35 ms →  71.41 ms     (+0.09%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.01 ms →   7.99 ms     (-0.21%)         114   →    114               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            15.60 ms →  16.04 ms     (+2.82%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       454.11 μs → 453.96 μs     (-0.03%)          19   →     19               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         7.36 ms →   7.57 ms     (+2.82%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.86 s  →   1.86 s      (+0.44%)          19   →     19               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             44.54 ms →  46.26 ms     (+3.86%)         356   →    356               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            27.33 ms →  28.09 ms     (+2.77%)         356   →    356               
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.77 μs →   2.08 μs    (+17.51%)         356   →    356               
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.49 μs →   1.81 μs    (+20.87%)         356   →    356               
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     342.74 ns → 474.26 ns    (+38.37%)         356   →    356               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    425.59 ns → 677.70 ns    (+59.24%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.74 ms →   2.80 ms     (+2.19%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.08 ms →   3.12 ms     (+1.13%)         356   →    356               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           5.68 ms →   6.11 ms     (+7.62%)         712   →    712               
- │ │ │ │   ├ sddk::orthogonalize                                           4.80 ms →   5.47 ms    (+14.00%)         356   →    356               
- │ │ │ │   │ ├ sddk::inner                                               697.95 μs → 819.44 μs    (+17.41%)         693   →    693               
- │ │ │ │   │ │ └ sddk::inner|local                                        20.14 μs →  25.18 μs    (+25.04%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 131.99 μs → 129.38 μs     (-1.98%)         356   →    356               
- │ │ │ │   │ ├ sddk::orthogonalize|transform                               1.53 ms →   1.87 ms    (+22.03%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             1.87 ms →   1.97 ms     (+5.64%)         337   →    337               
- │ │ │ │   │   ├ sddk::transform|init                                     15.89 μs →  20.41 μs    (+28.47%)         337   →    337               
- │ │ │ │   │   └ sddk::transform|local                                     6.51 μs →   8.53 μs    (+31.10%)        1.01 K →   1.01 K             
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.01 ms →   1.08 ms     (+7.14%)         356   →    356               
  │ │ │ │   │ └ sddk::inner                                               939.17 μs →   1.01 ms     (+7.55%)         356   →    356               
- │ │ │ │   │   └ sddk::inner|local                                        19.88 μs →  24.41 μs    (+22.73%)         356   →    356               
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     45.57 ms →  43.64 ms     (-4.25%)         356   →    356               
  │ │ │ │   ├ sirius::residuals                                             2.24 ms →   2.06 ms     (-7.87%)         340   →    340               
  │ │ │ │   │ ├ sddk::transform                                             1.15 ms →   1.16 ms     (+0.33%)         337   →    337               
- │ │ │ │   │ │ ├ sddk::transform|init                                     13.25 μs →  17.63 μs    (+33.06%)         337   →    337               
- │ │ │ │   │ │ └ sddk::transform|local                                     8.56 μs →  10.88 μs    (+27.04%)         674   →    674               
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.04 ms → 855.44 μs    (-17.50%)         337   →    337               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       6.55 ms →   7.06 ms     (+7.80%)          54   →     54               
  │ │ │ │     └ sddk::transform                                             3.92 ms →   4.23 ms     (+7.78%)          89   →     89               
- │ │ │ │       ├ sddk::transform|init                                     10.09 μs →  11.88 μs    (+17.70%)          89   →     89               
- │ │ │ │       └ sddk::transform|local                                     8.45 μs →  10.41 μs    (+23.30%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           508.84 ns → 537.84 ns     (+5.70%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.26 μs →  18.77 μs     (-2.56%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.58 ms →   1.51 ms     (-4.16%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         561.41 ms → 564.53 ms     (+0.56%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               403.62 ms → 390.54 ms     (-3.24%)          19   →     19               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.42 μs →   7.52 μs     (+1.46%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           6.88 μs →   6.89 μs     (+0.16%)          19   →     19               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   24.07 ms →  22.42 ms     (-6.86%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.22 μs →  10.70 μs    (+48.12%)          19   →     19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        4.23 ms →   3.95 ms     (-6.61%)          19   →     19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          18.78 ms →  17.43 ms     (-7.19%)          19   →     19               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       779.58 ns → 750.68 ns     (-3.71%)          19   →     19               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  121.59 ms → 123.50 ms     (+1.57%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 2.10 ms →   1.98 ms     (-5.56%)          19   →     19               
  │ │ │ │ └ sirius::Density::augment                                      227.83 ms → 214.85 ms     (-5.70%)          19   →     19               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           227.61 ms → 214.62 ms     (-5.71%)          19   →     19               
- │ │ │ ├ sirius::Field4D::symmetrize                                     130.73 ms → 146.51 ms    (+12.07%)          19   →     19               
- │ │ │ │ └ sirius::symmetrize_function|fpw                               130.72 ms → 146.51 ms    (+12.07%)          19   →     19               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             48.97 ms →  62.20 ms    (+27.03%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        68.42 ms →  71.06 ms     (+3.86%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.69 ms →  12.61 ms     (-0.64%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.49 ms →  23.52 ms     (+0.12%)          19   →     19               
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   3.57 ms →   3.96 ms    (+10.92%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              131.25 ms → 133.26 ms     (+1.53%)          19   →     19               
- │ │ │ ├ sirius::Density::mixer_input                                    394.88 μs →   1.07 ms   (+171.68%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function|inner                                   4.77 ms →   4.92 ms     (+3.16%)         229   →    229               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.62 ms →   4.82 ms     (+4.15%)         229   →    229               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.62 ms →   4.82 ms     (+4.16%)         229   →    229               
  │ │ │ └ sirius::Density::mixer_output                                     5.61 ms →   5.45 ms     (-2.87%)          19   →     19               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 4.96 ms →   4.77 ms     (-3.92%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       365.10 ms → 362.01 ms     (-0.85%)          19   →     19               
  │ │ │ ├ sirius::Potential::poisson                                       44.99 ms →  41.37 ms     (-8.04%)          19   →     19               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 2.88 ms →  10.75 ms   (+273.27%)          19   →     19               
  │ │ │ │ └ sirius::Periodic_function|inner                                 5.52 ms →   5.23 ms     (-5.27%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.84 ms →   4.63 ms     (-4.30%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.84 ms →   4.63 ms     (-4.30%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  790.94 μs → 816.35 μs     (+3.21%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            44.38 ms →  44.57 ms     (+0.43%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.21 ms →  43.38 ms     (+0.38%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            682.59 μs → 692.33 μs     (+1.43%)          38   →     38               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.20 ms →   4.21 ms     (+0.17%)          19   →     19               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.84 ms →   3.85 ms     (+0.40%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.92 ms → 269.20 ms     (+0.11%)          19   →     19               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             240.74 ns → 242.53 ns     (+0.74%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        94.38 ms →  96.90 ms     (+2.67%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  94.38 ms →  96.90 ms     (+2.67%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.27 ms →  13.27 ms     (+0.04%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          67.84 ms →  70.43 ms     (+3.82%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.65 ms →  12.58 ms     (-0.57%)          19   →     19               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.66 ms →   3.45 ms     (-5.81%)          19   →     19               
  │ │ ├ sirius::Periodic_function|inner                                     4.74 ms →   5.04 ms     (+6.21%)         133   →    133               
  │ │ │ └ sirius::Periodic_function|inner_local                             4.56 ms →   4.75 ms     (+4.20%)         133   →    133               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.56 ms →   4.75 ms     (+4.21%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.74 ms →   4.54 ms     (-4.06%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.73 ms →   4.54 ms     (-4.09%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.53 ms →   4.53 ms     (-0.03%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 75.52 μs →  76.40 μs     (+1.16%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          70.33 μs →  71.34 μs     (+1.44%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.86 ms →   5.60 ms     (-4.45%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.68 ms →   4.75 ms     (+1.36%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.66 ms →   4.74 ms     (+1.70%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.66 ms →   4.74 ms     (+1.70%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.81 ms →   4.58 ms     (-4.80%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.70 ms →   4.57 ms     (-2.79%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.54 ms →   4.74 ms     (+4.30%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.54 ms →   4.73 ms     (+4.30%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.54 ms →   4.73 ms     (+4.31%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.74 ms →   4.52 ms     (-4.63%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.73 ms →   4.51 ms     (-4.72%)           1   →      1               
  └ sirius::finalize                                                      753.45 ms → 758.08 ms     (+0.62%)           1   →      1               
```
