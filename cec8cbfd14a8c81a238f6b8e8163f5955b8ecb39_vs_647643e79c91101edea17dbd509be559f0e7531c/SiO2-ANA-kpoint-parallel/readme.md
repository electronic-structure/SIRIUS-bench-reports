# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  131.62 s  → 132.44 s      (+0.62%)           1   →      1               
  ├ sirius::initialize                                                      2.78 s  →   2.76 s      (-0.81%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  2.96 s  →   3.04 s      (+2.89%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                15.88 ms →  89.26 ms   (+462.23%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       143.47 ms → 158.78 ms    (+10.66%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            58.00 ms →  67.79 ms    (+16.89%)           2   →      2               
+ │ │ └ sirius::Unit_cell::update                                          27.40 ms →  23.12 ms    (-15.62%)           1   →      1               
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        9.37 ms →   5.67 ms    (-39.52%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  17.98 ms →  17.41 ms     (-3.17%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     17.96 ms →  17.39 ms     (-3.17%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.15 ms →   4.15 ms     (+0.04%)           1   →      1               
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.61 ms →   2.34 ms    (-10.41%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              101.16 μs → 102.36 μs     (+1.18%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.75 s  →   2.75 s      (-0.05%)           1   →      1               
+ │   ├ sirius::Unit_cell::update                                          13.90 ms →  10.83 ms    (-22.09%)           1   →      1               
+ │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        7.17 ms →   4.42 ms    (-38.34%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.69 ms →   6.37 ms     (-4.76%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.66 ms →   6.36 ms     (-4.59%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.88 ms →   3.87 ms     (-0.10%)           1   →      1               
+ │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.62 ms →   2.32 ms    (-11.39%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              104.39 μs →  99.86 μs     (-4.34%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       69.50 ms →  62.70 ms     (-9.78%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.12 ms →   5.14 ms     (+0.27%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.46 ms →   4.51 ms     (+1.01%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      22.02 ms →  21.88 ms     (-0.63%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.85 ms →  14.88 ms     (+0.21%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.57 ms →  19.84 ms     (+1.37%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  174.92 ms → 172.30 ms     (-1.50%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    132.07 ms → 129.83 ms     (-1.70%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 189.28 ms → 171.78 ms     (-9.24%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.33 ms →   1.33 ms     (+0.04%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 295.89 ms → 307.12 ms     (+3.80%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     35.87 ms →  35.52 ms     (-0.96%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.99 μs →   2.68 μs    (-10.19%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      35.77 ms →  35.43 ms     (-0.96%)           1   →      1               
  │   └ sirius::K_point::initialize                                        35.68 ms →  35.34 ms     (-0.97%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.28 ms →  18.12 ms     (-0.86%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.23 ms →   8.17 ms     (-0.76%)           1   →      1               
- │     ├ sddk::matrix_storage::matrix_storage                              9.12 μs →  10.49 μs    (+15.06%)           1   →      1               
  │     └ sirius::K_point::update                                          12.47 ms →  12.44 ms     (-0.27%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.12 ms →   6.09 ms     (-0.50%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.50 ms →   3.48 ms     (-0.40%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.47 ms →   5.28 ms     (-3.55%)           2   →      2               
  ├ sirius::Potential                                                     158.05 ms → 163.59 ms     (+3.50%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.98 ms →   5.86 ms     (-2.07%)           6   →      6               
  │ └ sirius::Potential::update                                           121.41 ms → 127.69 ms     (+5.17%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       120.69 ms → 126.94 ms     (+5.18%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              106.20 ms → 114.63 ms     (+7.94%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  13.56 ms →  11.38 ms    (-16.07%)           1   →      1               
  ├ sirius::Density                                                       134.01 ms → 132.43 ms     (-1.17%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.32 ms →   5.29 ms     (-0.57%)           2   →      2               
  │ └ sirius::Density::update                                             123.09 ms → 121.58 ms     (-1.23%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              122.66 ms → 121.15 ms     (-1.23%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               104.66 μs → 104.59 μs     (-0.06%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              109.28 ms → 115.10 ms     (+5.33%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  12.82 ms →   5.48 ms    (-57.29%)           1   →      1               
  ├ sirius::Density::initial_density                                      176.21 ms → 175.49 ms     (-0.41%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                  108.52 ms → 123.12 ms    (+13.46%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                      12.10 ms →   5.07 ms    (-58.10%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                 10.55 ms →  10.03 ms     (-4.86%)           1   →      1               
  ├ sirius::Potential::generate                                           594.90 ms → 605.90 ms     (+1.85%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          137.82 ms → 138.64 ms     (+0.59%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                    18.94 ms →   5.47 ms    (-71.11%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    11.38 ms →  11.72 ms     (+3.01%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.95 ms →  10.40 ms     (-5.09%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.95 ms →  10.39 ms     (-5.09%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      591.43 μs → 564.30 μs     (-4.59%)           2   →      2               
  │ ├ sirius::Potential::xc                                                56.58 ms →  56.01 ms     (-1.01%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               54.16 ms →  53.61 ms     (-1.01%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.80 ms →   6.29 ms     (+8.53%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.60 ms →   5.21 ms     (-6.96%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.78 ms →   5.95 ms     (+2.91%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        92.68 ms →  93.56 ms     (+0.95%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 299.44 ms → 309.25 ms     (+3.27%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.42 ms →   8.52 ms     (+1.15%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.06 ms →   8.16 ms     (+1.15%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.81 ms →   4.75 ms     (-1.37%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.34 ms →   2.47 ms     (+5.73%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           63.05 μs →  59.10 μs     (-6.27%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       97.98 μs → 103.12 μs     (+5.25%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       75.03 μs →  78.65 μs     (+4.82%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.89 s  →   1.87 s      (-0.79%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                19.78 ms →  18.08 ms     (-8.57%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 215.81 μs → 179.83 μs    (-16.67%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              19.56 ms →  17.90 ms     (-8.48%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.87 s  →   1.85 s      (-0.71%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              132.38 ms → 129.91 ms     (-1.87%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    53.07 ms →  53.48 ms     (+0.78%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.49 ms →  21.65 ms     (+0.74%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  635.11 ms → 641.54 ms     (+1.01%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 298.11 ms → 302.84 ms     (+1.59%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.81 μs →   3.38 μs    (+20.25%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.64 μs →   2.52 μs    (+53.78%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           360.00 ns → 380.00 ns     (+5.56%)           1   →      1               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          634.00 ns → 578.00 ns     (-8.83%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.23 ms →   9.24 ms     (+0.09%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             120.81 ms → 121.13 ms     (+0.26%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               103.46 ms → 104.15 ms     (+0.67%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    38.37 ms →  38.47 ms     (+0.27%)           2   →      2               
  │ │ │ └ sddk::inner                                                      37.82 ms →  37.93 ms     (+0.30%)           2   →      2               
- │ │ │   └ sddk::inner|local                                              23.14 μs →  29.72 μs    (+28.43%)           2   →      2               
- │ │ ├ Eigensolver_cuda|zhegvdx                                           56.53 ms →  62.67 ms    (+10.85%)           1   →      1               
  │ │ └ sddk::transform                                                    31.54 ms →  31.55 ms     (+0.04%)           1   →      1               
- │ │   ├ sddk::transform|init                                             10.83 μs →  12.56 μs    (+15.99%)           1   →      1               
- │ │   └ sddk::transform|local                                            11.58 μs →  14.71 μs    (+26.98%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               510.00 ns → 452.00 ns    (-11.37%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    121.83 s  → 122.61 s      (+0.64%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.86 ms →   5.75 ms     (-1.82%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.85 s  →   4.70 s      (-3.16%)          25   →     26       (+4.00%)
- │ │ ├ sirius::Hamiltonian0                                                4.60 ms →   5.06 ms    (+10.02%)          25   →     26       (+4.00%)
- │ │ │ ├ sirius::Local_operator                                            4.22 ms →   4.69 ms    (+11.17%)          25   →     26       (+4.00%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                                1.01 ms → 927.27 μs     (-8.34%)          25   →     26       (+4.00%)
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.31 ms →   2.88 ms    (+24.46%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Non_local_operator                                       64.73 μs →  65.23 μs     (+0.77%)          50   →     52       (+4.00%)
  │ │ │ ├ sirius::D_operator::initialize                                   96.85 μs →  94.08 μs     (-2.86%)          25   →     26       (+4.00%)
  │ │ │ └ sirius::Q_operator::initialize                                   78.12 μs →  74.95 μs     (-4.05%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Band::solve                                                 2.87 s  →   2.73 s      (-4.74%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Hamiltonian_k                                           165.61 μs → 161.24 μs     (-2.64%)          25   →     26       (+4.00%)
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             158.64 μs → 154.86 μs     (-2.38%)          25   →     26       (+4.00%)
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           5.24 μs →   4.76 μs     (-9.25%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.70 s  →   2.58 s      (-4.54%)          25   →     26       (+4.00%)
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             97.06 ms →  94.45 ms     (-2.69%)          25   →     26       (+4.00%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.93 ms →   7.67 ms     (-3.21%)         150   →    156       (+4.00%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             5.95 ms →   5.94 ms     (-0.20%)          25   →     26       (+4.00%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       345.00 μs → 348.28 μs     (+0.95%)          25   →     26       (+4.00%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.32 ms →   2.31 ms     (-0.67%)          50   →     52       (+4.00%)
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.56 s  →   2.44 s      (-4.66%)          25   →     26       (+4.00%)
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            125.93 ms → 130.24 ms     (+3.42%)         278   →    271       (-2.52%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            50.28 ms →  52.05 ms     (+3.52%)         278   →    271       (-2.52%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.06 μs →   1.88 μs     (-8.86%)         278   →    271       (-2.52%)
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.69 μs →   1.50 μs    (-10.85%)         278   →    271       (-2.52%)
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     358.28 ns → 295.46 ns    (-17.53%)         278   →    271       (-2.52%)
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    568.17 ns → 407.90 ns    (-28.21%)         278   →    271       (-2.52%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.41 ms →   7.43 ms     (+0.24%)         278   →    271       (-2.52%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        22.82 ms →  23.95 ms     (+4.94%)         278   →    271       (-2.52%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          22.70 ms →  23.40 ms     (+3.07%)         556   →    542       (-2.52%)
  │ │ │ │   ├ sddk::orthogonalize                                          31.99 ms →  32.95 ms     (+3.02%)         278   →    271       (-2.52%)
  │ │ │ │   │ ├ sddk::inner                                                 4.72 ms →   4.88 ms     (+3.51%)         531   →    516       (-2.82%)
+ │ │ │ │   │ │ └ sddk::inner|local                                        26.38 μs →  21.20 μs    (-19.62%)         531   →    516       (-2.82%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 595.84 μs → 615.19 μs     (+3.25%)         278   →    271       (-2.52%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.34 ms →   9.75 ms     (+4.46%)         278   →    271       (-2.52%)
  │ │ │ │   │ └ sddk::transform                                            14.33 ms →  14.69 ms     (+2.55%)         253   →    245       (-3.16%)
  │ │ │ │   │   ├ sddk::transform|init                                     21.25 μs →  20.22 μs     (-4.84%)         253   →    245       (-3.16%)
+ │ │ │ │   │   └ sddk::transform|local                                     8.63 μs →   6.97 μs    (-19.23%)         759   →    735       (-3.16%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               8.99 ms →   9.27 ms     (+3.19%)         278   →    271       (-2.52%)
  │ │ │ │   │ └ sddk::inner                                                 8.74 ms →   9.03 ms     (+3.25%)         278   →    271       (-2.52%)
+ │ │ │ │   │   └ sddk::inner|local                                        26.97 μs →  21.36 μs    (-20.78%)         278   →    271       (-2.52%)
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     35.74 ms →  33.16 ms     (-7.21%)         278   →    271       (-2.52%)
  │ │ │ │   ├ sirius::residuals                                            13.39 ms →  13.91 ms     (+3.88%)         269   →    262       (-2.60%)
  │ │ │ │   │ ├ sddk::transform                                            12.11 ms →  12.61 ms     (+4.14%)         259   →    252       (-2.70%)
+ │ │ │ │   │ │ ├ sddk::transform|init                                     16.53 μs →  13.79 μs    (-16.57%)         259   →    252       (-2.70%)
+ │ │ │ │   │ │ └ sddk::transform|local                                    10.95 μs →   9.36 μs    (-14.59%)         518   →    504       (-2.70%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.57 ms →   1.62 ms     (+3.06%)         259   →    252       (-2.70%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      77.18 ms →  76.22 ms     (-1.25%)          52   →     53       (+1.92%)
  │ │ │ │     └ sddk::transform                                            50.56 ms →  50.27 ms     (-0.58%)          79   →     80       (+1.27%)
  │ │ │ │       ├ sddk::transform|init                                     11.60 μs →  10.72 μs     (-7.52%)          79   →     80       (+1.27%)
+ │ │ │ │       └ sddk::transform|local                                    10.11 μs →   9.02 μs    (-10.82%)         106   →    107       (+0.94%)
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                           485.28 ns → 434.46 ns    (-10.47%)          25   →     26       (+4.00%)
- │ │ │ └ sirius::K_point_set::sync_band_energies                          47.06 μs →  93.60 μs    (+98.90%)          25   →     26       (+4.00%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                        593.29 μs → 599.61 μs     (+1.06%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Density::generate                                         770.35 ms → 768.61 ms     (-0.23%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Density::generate_valence                               405.87 ms → 402.05 ms     (-0.94%)          25   →     26       (+4.00%)
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.23 μs →   3.81 μs    (-53.68%)          25   →     26       (+4.00%)
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.30 μs →   3.15 μs    (-56.90%)          25   →     26       (+4.00%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.21 ms → 100.33 ms     (+0.12%)          25   →     26       (+4.00%)
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.45 μs →  10.87 μs    (+45.95%)          25   →     26       (+4.00%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.12 ms     (+0.11%)          25   →     26       (+4.00%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.18 ms →  91.29 ms     (+0.13%)          25   →     26       (+4.00%)
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       507.20 ns → 530.50 ns     (+4.59%)          25   →     26       (+4.00%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  163.90 ms → 161.80 ms     (-1.28%)          25   →     26       (+4.00%)
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.64 ms     (-0.39%)          25   →     26       (+4.00%)
  │ │ │ │ └ sirius::Density::augment                                       88.25 ms →  88.28 ms     (+0.04%)          25   →     26       (+4.00%)
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.01 ms →  88.04 ms     (+0.03%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Field4D::symmetrize                                     271.66 ms → 274.51 ms     (+1.05%)          25   →     26       (+4.00%)
  │ │ │ │ └ sirius::symmetrize_function|fpw                               271.66 ms → 274.51 ms     (+1.05%)          25   →     26       (+4.00%)
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             24.55 ms →  24.37 ms     (-0.75%)          25   →     26       (+4.00%)
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       222.65 ms → 226.01 ms     (+1.51%)          25   →     26       (+4.00%)
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            23.27 ms →  22.97 ms     (-1.28%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       81.35 ms →  80.23 ms     (-1.37%)          25   →     26       (+4.00%)
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   7.89 ms →   8.23 ms     (+4.36%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Density::mix                                              229.26 ms → 215.11 ms     (-6.18%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Density::mixer_input                                    978.27 μs → 963.68 μs     (-1.49%)          25   →     26       (+4.00%)
+ │ │ │ ├ sirius::Periodic_function|inner                                  11.57 ms →  10.41 ms    (-10.08%)         319   →    334       (+4.70%)
+ │ │ │ │ └ sirius::Periodic_function|inner_local                          11.22 ms →   9.95 ms    (-11.31%)         319   →    334       (+4.70%)
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 11.22 ms →   9.95 ms    (-11.31%)         319   →    334       (+4.70%)
- │ │ │ └ sirius::Density::mixer_output                                     6.32 ms →   7.39 ms    (+16.85%)          25   →     26       (+4.00%)
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.47 ms →   6.55 ms    (+19.84%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Potential::generate                                       580.16 ms → 580.46 ms     (+0.05%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Potential::poisson                                      137.56 ms → 138.23 ms     (+0.49%)          25   →     26       (+4.00%)
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                19.32 ms →   5.93 ms    (-69.29%)          25   →     26       (+4.00%)
  │ │ │ │ └ sirius::Periodic_function|inner                                10.68 ms →  10.78 ms     (+0.91%)          25   →     26       (+4.00%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.37 ms →  10.56 ms     (+1.86%)          25   →     26       (+4.00%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.36 ms →  10.56 ms     (+1.87%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Periodic_function::add                                  578.22 μs → 561.28 μs     (-2.93%)          50   →     52       (+4.00%)
  │ │ │ ├ sirius::Potential::xc                                            49.20 ms →  49.68 ms     (+0.96%)          25   →     26       (+4.00%)
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           46.79 ms →  47.36 ms     (+1.23%)          25   →     26       (+4.00%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.05 ms →   2.98 ms     (-2.24%)          50   →     52       (+4.00%)
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.79 ms →   5.97 ms     (+3.03%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   7.03 ms →   6.87 ms     (-2.29%)          25   →     26       (+4.00%)
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    91.00 ms →  91.00 ms     (-0.00%)          25   →     26       (+4.00%)
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.86 ms → 292.27 ms     (-0.20%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Field4D::symmetrize                                       275.29 ms → 280.37 ms     (+1.85%)          25   →     26       (+4.00%)
  │ │ │ └ sirius::symmetrize_function|fpw                                 275.28 ms → 280.37 ms     (+1.85%)          25   →     26       (+4.00%)
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.26 ms →  27.21 ms     (-0.16%)          25   →     26       (+4.00%)
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         220.29 ms → 225.47 ms     (+2.35%)          25   →     26       (+4.00%)
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.94 ms →  23.93 ms     (-0.02%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.70 ms →   6.11 ms     (+7.18%)          25   →     26       (+4.00%)
  │ │ ├ sirius::Periodic_function|inner                                    11.45 ms →  10.32 ms     (-9.88%)         175   →    182       (+4.00%)
+ │ │ │ └ sirius::Periodic_function|inner_local                            11.00 ms →   9.82 ms    (-10.78%)         175   →    182       (+4.00%)
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                   11.00 ms →   9.82 ms    (-10.78%)         175   →    182       (+4.00%)
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.50 ms →  10.64 ms     (+1.40%)          75   →     78       (+4.00%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.18 ms →  10.17 ms     (-0.10%)          75   →     78       (+4.00%)
  │ │ ├ sirius::Periodic_function::integrate                               10.35 ms →  10.02 ms     (-3.17%)          25   →     26       (+4.00%)
- │ │ └ sirius::Density::get_magnetisation                                115.57 μs → 150.50 μs    (+30.22%)          25   →     26       (+4.00%)
- │ │   └ sirius::Density::compute_atomic_mag_mom                         110.85 μs → 145.75 μs    (+31.48%)          25   →     26       (+4.00%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.63 ms →   5.25 ms     (-6.71%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                      11.06 ms →  10.12 ms     (-8.45%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                              10.78 ms →  10.10 ms     (-6.32%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                     10.78 ms →  10.10 ms     (-6.32%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.28 ms →  10.37 ms     (+0.79%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.05 ms →  10.36 ms     (+3.10%)           3   →      3               
+ ├ sirius::Periodic_function|inner                                        11.38 ms →  10.09 ms    (-11.33%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                11.11 ms →  10.08 ms     (-9.28%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                       11.11 ms →  10.08 ms     (-9.28%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.16 ms →  10.35 ms     (+1.80%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.03 ms →  10.34 ms     (+3.06%)           1   →      1               
  └ sirius::finalize                                                      196.60 ms → 205.48 ms     (+4.52%)           1   →      1               
```
