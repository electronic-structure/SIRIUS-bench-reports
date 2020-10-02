# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 495e097f8fb7cb2be32f3783e9a2314d02bcfd52
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                  540.83 s  → 890.25 s     (+64.61%)           1   →      1               
+ ├ sirius::initialize                                                      3.35 s  →   3.00 s     (-10.51%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                 13.95 s  →  14.27 s      (+2.29%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               269.76 μs → 264.18 μs     (-2.07%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       420.06 ms → 754.25 ms    (+79.56%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                           410.56 ms → 742.25 ms    (+80.79%)           1   →      1               
- │ │ └ sirius::Unit_cell::update                                           9.44 ms →  11.94 ms    (+26.47%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      195.17 μs → 189.37 μs     (-2.97%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                   9.22 ms →  11.72 ms    (+27.13%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                      9.21 ms →  11.70 ms    (+27.15%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.76 ms →   4.74 ms     (-0.38%)           1   →      1               
- │ │       ├ sirius::Unit_cell_symmetry|equiv                             32.22 μs →  41.65 μs    (+29.29%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               14.37 μs →  14.59 μs     (+1.57%)           1   →      1               
  │ └ sirius::Simulation_context::update                                   13.49 s  →  13.48 s      (-0.09%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           4.92 ms →   4.96 ms     (+0.95%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       38.95 μs →  37.39 μs     (-3.99%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   4.86 ms →   4.90 ms     (+0.89%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      4.84 ms →   4.88 ms     (+0.84%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.76 ms →   4.79 ms     (+0.74%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                             31.88 μs →  31.64 μs     (-0.76%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               13.92 μs →  13.30 μs     (-4.49%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                        3.07 s  →   3.10 s      (+0.69%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                          152.96 ms → 154.03 ms     (+0.70%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                               133.54 ms → 135.75 ms     (+1.65%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                     459.01 ms → 470.81 ms     (+2.57%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                     838.56 ms → 840.64 ms     (+0.25%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                               784.00 ms → 786.56 ms     (+0.33%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    7.36 ms →   7.58 ms     (+2.99%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      4.64 ms →   4.86 ms     (+4.76%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   7.89 ms →   7.97 ms     (+0.97%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                757.83 μs → 725.53 μs     (-4.26%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 155.34 ms → 160.26 ms     (+3.17%)           1   →      1               
  ├ sirius::K_point_set::create_k_mesh                                     62.95 ms →  60.76 ms     (-3.48%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            764.25 ns → 730.75 ns     (-4.38%)           8   →      8               
  │ └ sirius::K_point_set::initialize                                      62.87 ms →  60.67 ms     (-3.49%)           1   →      1               
  │   └ sirius::K_point::initialize                                         7.69 ms →   7.42 ms     (-3.52%)           8   →      8               
+ │     ├ sirius::K_point::generate_gkvec                                   1.36 ms →   1.11 ms    (-18.33%)           8   →      8               
+ │     │ └ sddk::Gvec::init                                              253.07 μs → 212.75 μs    (-15.93%)           8   →      8               
- │     ├ sddk::matrix_storage::matrix_storage                              2.52 μs →   2.92 μs    (+15.55%)          32   →     32               
  │     └ sirius::K_point::update                                           6.21 ms →   6.17 ms     (-0.60%)           8   →      8               
  │       ├ sirius::Beta_projectors                                       325.07 μs → 339.16 μs     (+4.33%)           8   →      8               
  │       │ └ sirius::Beta_projectors::generate_pw_coefs_t                241.37 μs → 232.75 μs     (-3.57%)           8   →      8               
- │       ├ sddk::matrix_storage::matrix_storage                            3.17 μs →   3.89 μs    (+22.85%)           8   →      8               
  │       ├ sirius::Non_local_operator                                     28.01 μs →  26.85 μs     (-4.13%)           8   →      8               
  │       ├ sirius::Q_operator::initialize                                 37.38 μs →  34.56 μs     (-7.54%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::prepare                           3.68 μs →   3.55 μs     (-3.37%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::generate                         40.63 μs →  39.46 μs     (-2.90%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::inner                           122.74 μs → 123.39 μs     (+0.53%)           8   →      8               
  │       ├ sirius::Non_local_operator::apply                              71.78 μs →  73.52 μs     (+2.42%)           8   →      8               
+ │       ├ sirius::Beta_projectors_base::dismiss                         585.25 ns → 524.00 ns    (-10.47%)           8   →      8               
  │       ├ sddk::inner                                                   115.98 μs → 119.75 μs     (+3.25%)           8   →      8               
- │       │ └ sddk::inner|local                                            18.67 μs →  22.24 μs    (+19.10%)           8   →      8               
  │       ├ Eigensolver_lapack|zheevd                                       4.78 ms →   4.71 ms     (-1.50%)           8   →      8               
- │       └ sddk::transform                                                54.04 μs →  61.23 μs    (+13.31%)           8   →      8               
- │         ├ sddk::transform|init                                          6.87 μs →   7.92 μs    (+15.33%)           8   →      8               
- │         └ sddk::transform|local                                        12.96 μs →  14.60 μs    (+12.61%)           8   →      8               
  ├ sirius::Smooth_periodic_function                                      446.15 μs → 447.51 μs     (+0.30%)           4   →      4               
- ├ sirius::Potential                                                       6.79 ms →   8.13 ms    (+19.77%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    474.62 μs → 471.61 μs     (-0.63%)           7   →      7               
- │ └ sirius::Potential::update                                             2.90 ms →   4.22 ms    (+45.36%)           1   →      1               
- │   └ sirius::Potential::generate_local_potential                         2.87 ms →   4.18 ms    (+45.90%)           1   →      1               
- │     ├ sirius::Simulation_context::make_periodic_function                2.42 ms →   3.70 ms    (+52.60%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                 361.86 μs → 407.65 μs    (+12.65%)           1   →      1               
  ├ sirius::Density                                                         3.71 ms →   3.67 ms     (-1.07%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    210.89 μs → 211.96 μs     (+0.51%)           3   →      3               
  │ └ sirius::Density::update                                               3.07 ms →   3.03 ms     (-1.46%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                3.03 ms →   2.99 ms     (-1.45%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                17.77 μs →  18.55 μs     (+4.40%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                2.71 ms →   2.64 ms     (-2.87%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                 267.13 μs → 300.04 μs    (+12.32%)           1   →      1               
  ├ sirius::Density::initial_density                                      133.47 ms → 132.75 ms     (-0.54%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    3.36 ms →   3.37 ms     (+0.31%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     266.70 μs → 254.19 μs     (-4.69%)           3   →      3               
  │ └ sirius::Periodic_function::integrate                                  1.07 ms →   1.12 ms     (+4.34%)           1   →      1               
  ├ sirius::Potential::generate                                           790.03 ms → 804.06 ms     (+1.78%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            4.08 ms →   4.04 ms     (-0.86%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   320.60 μs → 318.71 μs     (-0.59%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     1.34 ms →   1.40 ms     (+4.48%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             1.34 ms →   1.40 ms     (+4.52%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    1.34 ms →   1.40 ms     (+4.52%)           1   →      1               
+ │ ├ sirius::Periodic_function::add                                      126.92 μs → 113.61 μs    (-10.48%)           2   →      2               
  │ ├ sirius::Potential::xc                                                87.32 ms →  87.25 ms     (-0.09%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_magnetic                                  87.04 ms →  86.98 ms     (-0.06%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                276.87 μs → 274.19 μs     (-0.97%)          17   →     17               
  │ │   ├ sirius::Potential::xc_rg_magnetic|up_dn                         866.75 μs → 880.15 μs     (+1.55%)           1   →      1               
  │ │   ├ sirius::Potential::xc_rg_magnetic|grad1                           9.05 ms →   9.08 ms     (+0.30%)           1   →      1               
  │ │   │ ├ sirius::Smooth_periodic_function::fft_transform               263.39 μs → 284.29 μs     (+7.93%)           8   →      8               
  │ │   │ ├ sirius::gradient                                                1.76 ms →   1.70 ms     (-3.55%)           2   →      2               
  │ │   │ │ └ sirius::Smooth_periodic_function                            492.61 μs → 472.22 μs     (-4.14%)           6   →      6               
  │ │   │ └ sirius::dot                                                     1.14 ms →   1.13 ms     (-0.45%)           3   →      3               
  │ │   │   └ sirius::Smooth_periodic_function                            476.86 μs → 471.13 μs     (-1.20%)           3   →      3               
  │ │   ├ sirius::Potential::xc_rg_magnetic|libxc                          15.57 ms →  15.62 ms     (+0.32%)           2   →      2               
  │ │   ├ sirius::Smooth_periodic_function::fft_transform                 277.31 μs → 257.90 μs     (-7.00%)          16   →     16               
  │ │   └ sirius::divergence                                                3.68 ms →   3.64 ms     (-1.12%)           4   →      4               
  │ │     └ sirius::Smooth_periodic_function                              284.29 μs → 284.40 μs     (+0.04%)           4   →      4               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     845.83 μs →   1.72 ms   (+103.21%)           2   →      2               
  │ ├ sirius::Potential::generate_D_operator_matrix                        12.70 ms →  12.56 ms     (-1.12%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 683.68 ms → 696.28 ms     (+1.84%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  849.49 μs → 932.48 μs     (+9.77%)           1   →      1               
- │ ├ sirius::Local_operator                                              682.33 μs → 766.82 μs    (+12.38%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   19.07 μs →  18.18 μs     (-4.67%)           2   →      2               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                   186.36 μs → 236.51 μs    (+26.91%)           2   →      2               
  │ ├ sirius::Non_local_operator                                           34.70 μs →  33.62 μs     (-3.09%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       47.47 μs →  52.19 μs     (+9.94%)           1   →      1               
+ │ └ sirius::Q_operator::initialize                                       41.24 μs →  36.47 μs    (-11.57%)           1   →      1               
+ ├ sirius::Band::initialize_subspace                                      98.89 ms →  79.23 ms    (-19.88%)           1   →      1               
+ │ ├ sirius::Hamiltonian_k                                                37.74 μs →  27.73 μs    (-26.54%)           8   →      8               
+ │ │ ├ sirius::Local_operator::prepare_k                                  33.53 μs →  23.00 μs    (-31.38%)           8   →      8               
  │ │ └ sirius::Beta_projectors_base::prepare                               2.64 μs →   2.62 μs     (-0.49%)           8   →      8               
+ │ ├ sirius::Band::initialize_subspace|kp                                 12.32 ms →   9.87 ms    (-19.87%)           8   →      8               
+ │ │ ├ sddk::matrix_storage::matrix_storage                                8.41 μs →   7.07 μs    (-15.90%)          32   →     32               
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                   428.57 μs → 363.69 μs    (-15.14%)           8   →      8               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                            68.77 μs →  59.38 μs    (-13.66%)           8   →      8               
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    3.47 ms →   3.06 ms    (-11.99%)          16   →     16               
  │ │ │ ├ sirius::Local_operator::apply_h                                   2.71 ms →   2.46 ms     (-9.28%)          16   →     16               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.13 μs →   1.92 μs    (-10.11%)          16   →     16               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.58 μs →   1.39 μs    (-12.08%)          16   →     16               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           448.94 ns → 374.13 ns    (-16.66%)          16   →     16               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                          424.63 ns → 346.88 ns    (-18.31%)          16   →     16               
  │ │ │ ├ sirius::Beta_projectors_base::generate                           51.78 μs →  48.65 μs     (-6.05%)          16   →     16               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             139.31 μs → 130.98 μs     (-5.97%)          16   →     16               
  │ │ │ ├ sirius::Non_local_operator::apply                                78.39 μs →  72.96 μs     (-6.93%)          32   →     32               
  │ │ │ ├ sddk::inner                                                     127.69 μs → 127.97 μs     (+0.21%)          16   →     16               
+ │ │ │ │ └ sddk::inner|local                                              22.34 μs →  17.25 μs    (-22.78%)          16   →     16               
+ │ │ │ └ sddk::transform                                                 188.38 μs →  60.33 μs    (-67.97%)          16   →     16               
+ │ │ │   ├ sddk::transform|init                                            9.50 μs →   8.04 μs    (-15.36%)          16   →     16               
+ │ │ │   └ sddk::transform|local                                          11.35 μs →   9.68 μs    (-14.74%)          16   →     16               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                   245.80 μs → 122.03 μs    (-50.35%)          32   →     32               
+ │ │ │ └ sddk::inner                                                     242.33 μs → 119.21 μs    (-50.81%)          32   →     32               
+ │ │ │   └ sddk::inner|local                                              19.36 μs →  15.05 μs    (-22.28%)          32   →     32               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                            1.59 ms →   1.17 ms    (-26.23%)          16   →     16               
+ │ │ └ sddk::transform                                                   162.78 μs →  67.14 μs    (-58.75%)          16   →     16               
+ │ │   ├ sddk::transform|init                                             10.42 μs →   7.93 μs    (-23.91%)          16   →     16               
+ │ │   └ sddk::transform|local                                            12.46 μs →  10.29 μs    (-17.46%)          16   →     16               
+ │ └ sirius::Beta_projectors_base::dismiss                               591.13 ns → 442.13 ns    (-25.21%)           8   →      8               
- ├ sirius::DFT_ground_state::scf_loop                                    521.78 s  → 870.45 s     (+66.82%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    428.46 μs → 437.50 μs     (+2.11%)          38   →     38               
  │ ├ sirius::Hubbard::compute_occupation_matrix                            6.37 s  →   6.36 s      (-0.10%)           1   →      1               
  │ │ └ sddk::inner                                                        58.47 ms →  59.31 ms     (+1.44%)          16   →     16               
  │ │   └ sddk::inner|local                                                58.46 ms →  59.31 ms     (+1.44%)          16   →     16               
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                          8.05 s  →  13.50 s     (+67.71%)          64   →     64               
  │ │ ├ sirius::Hamiltonian0                                                3.92 ms →   4.29 ms     (+9.44%)          64   →     64               
  │ │ │ ├ sirius::Local_operator                                            2.18 ms →   2.32 ms     (+6.19%)          64   →     64               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               19.67 μs →  18.71 μs     (-4.92%)         128   →    128               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               210.55 μs → 211.70 μs     (+0.54%)         128   →    128               
- │ │ │ ├ sirius::Non_local_operator                                      810.20 μs → 935.39 μs    (+15.45%)         128   →    128               
+ │ │ │ ├ sirius::D_operator::initialize                                   69.28 μs →  55.25 μs    (-20.25%)          64   →     64               
  │ │ │ └ sirius::Q_operator::initialize                                   34.24 μs →  32.51 μs     (-5.06%)          64   →     64               
- │ │ ├ sirius::Band::solve                                               674.59 ms →   1.97 s    (+191.43%)          64   →     64               
- │ │ │ ├ sirius::Hamiltonian_k                                            37.15 μs →  45.15 μs    (+21.56%)         512   →    512               
- │ │ │ │ ├ sirius::Local_operator::prepare_k                              33.94 μs →  41.58 μs    (+22.51%)         512   →    512               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           2.38 μs →   2.61 μs     (+9.77%)         512   →    512               
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     84.27 ms → 245.68 ms   (+191.54%)         512   →    512               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc              1.24 ms →   2.82 ms   (+128.00%)         512   →    512               
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          1.20 μs → 869.29 ns    (-27.28%)        3.07 K →   3.07 K             
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           925.17 μs → 934.75 μs     (+1.04%)         512   →    512               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        28.32 μs →  28.10 μs     (-0.78%)        1.02 K →   1.02 K             
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       376.93 μs → 387.43 μs     (+2.79%)        1.02 K →   1.02 K             
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              81.96 ms → 241.80 ms   (+195.00%)         512   →    512               
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              6.41 ms →  19.46 ms   (+203.59%)        3.95 K →   3.95 K             
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                             5.25 ms →  16.11 ms   (+207.03%)        3.95 K →   3.95 K             
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.90 μs →   1.90 μs     (+0.25%)        3.95 K →   3.95 K             
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.55 μs →   1.60 μs     (+3.08%)        3.95 K →   3.95 K             
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     434.34 ns → 449.68 ns     (+3.53%)        3.95 K →   3.95 K             
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    437.46 ns → 481.56 ns    (+10.08%)        3.95 K →   3.95 K             
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                     49.09 μs →  42.60 μs    (-13.21%)        3.95 K →   3.95 K             
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       316.90 μs →   1.06 ms   (+235.78%)        3.95 K →   3.95 K             
  │ │ │ │   │ ├ sirius::Non_local_operator::apply                          75.33 μs →  68.04 μs     (-9.68%)        7.90 K →   7.90 K             
- │ │ │ │   │ ├ sddk::inner                                               301.61 μs →   1.00 ms   (+232.79%)        3.95 K →   3.95 K             
  │ │ │ │   │ │ └ sddk::inner|local                                        18.39 μs →  18.78 μs     (+2.10%)        3.95 K →   3.95 K             
- │ │ │ │   │ └ sddk::transform                                           262.58 μs →   1.02 ms   (+288.55%)        3.95 K →   3.95 K             
  │ │ │ │   │   ├ sddk::transform|init                                      8.30 μs →   8.89 μs     (+7.12%)        3.95 K →   3.95 K             
  │ │ │ │   │   └ sddk::transform|local                                    10.53 μs →  10.84 μs     (+2.99%)        3.95 K →   3.95 K             
- │ │ │ │   ├ sddk::orthogonalize                                         944.80 μs →   3.72 ms   (+293.57%)        3.95 K →   3.95 K             
- │ │ │ │   │ ├ sddk::inner                                               278.23 μs →   1.07 ms   (+285.86%)        6.88 K →   6.88 K             
  │ │ │ │   │ │ └ sddk::inner|local                                        17.01 μs →  17.41 μs     (+2.34%)        6.88 K →   6.88 K             
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 248.44 μs →   1.03 ms   (+315.21%)        3.95 K →   3.95 K             
  │ │ │ │   │ ├ sddk::orthogonalize|transform                              45.28 μs →  44.71 μs     (-1.28%)        3.95 K →   3.95 K             
- │ │ │ │   │ └ sddk::transform                                           219.67 μs →   1.04 ms   (+372.76%)        2.93 K →   2.93 K             
- │ │ │ │   │   ├ sddk::transform|init                                     16.62 μs →  18.46 μs    (+11.06%)        2.93 K →   2.93 K             
- │ │ │ │   │   └ sddk::transform|local                                     7.44 μs →   8.34 μs    (+12.06%)        8.78 K →   8.78 K             
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             331.20 μs →   1.16 ms   (+249.05%)        3.95 K →   3.95 K             
- │ │ │ │   │ └ sddk::inner                                               314.22 μs →   1.12 ms   (+257.27%)        3.95 K →   3.95 K             
  │ │ │ │   │   └ sddk::inner|local                                        17.25 μs →  17.76 μs     (+2.95%)        3.95 K →   3.95 K             
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                      1.80 ms →   2.81 ms    (+55.89%)        3.95 K →   3.95 K             
- │ │ │ │   ├ sirius::residuals                                           862.98 μs →   3.04 ms   (+252.48%)        3.95 K →   3.95 K             
- │ │ │ │   │ ├ sddk::transform                                           295.19 μs → 968.11 μs   (+227.96%)        3.52 K →   3.52 K             
  │ │ │ │   │ │ ├ sddk::transform|init                                     12.63 μs →  13.18 μs     (+4.35%)        3.52 K →   3.52 K             
  │ │ │ │   │ │ └ sddk::transform|local                                     9.97 μs →  10.37 μs     (+4.02%)        7.03 K →   7.03 K             
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               612.21 μs →   2.39 ms   (+289.91%)        3.52 K →   3.52 K             
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     408.76 μs →   1.80 ms   (+339.51%)        2.52 K →   2.52 K             
- │ │ │ │     └ sddk::transform                                           245.43 μs →   1.12 ms   (+354.56%)        4.02 K →   4.02 K             
  │ │ │ │       ├ sddk::transform|init                                      9.84 μs →  10.04 μs     (+2.05%)        4.02 K →   4.02 K             
  │ │ │ │       └ sddk::transform|local                                     9.36 μs →   9.98 μs     (+6.62%)        5.51 K →   5.51 K             
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           535.86 ns → 535.91 ns     (+0.01%)         512   →    512               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.90 μs →  19.80 μs     (-0.49%)          64   →     64               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        523.30 μs → 502.88 μs     (-3.90%)          64   →     64               
- │ │ ├ sirius::Density::generate                                         196.58 ms →   5.33 s   (+2611.54%)          64   →     64               
- │ │ │ ├ sirius::Density::generate_valence                                26.97 ms →   5.15 s  (+19011.93%)          64   →     64               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             1.71 μs →   2.13 μs    (+24.64%)        1.02 K →   1.02 K             
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.47 μs →   1.87 μs    (+27.03%)        1.02 K →   1.02 K             
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  421.33 μs →   3.50 ms   (+731.12%)         512   →    512               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         2.27 μs →   4.53 μs    (+99.05%)         512   →    512               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                       94.44 μs →  51.75 μs    (-45.20%)         512   →    512               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         144.85 μs →   1.66 ms  (+1048.84%)        1.02 K →   1.02 K             
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       517.67 ns → 860.46 ns    (+66.22%)         512   →    512               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_om                              610.57 ms                                 512               
  │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|1                             50.08 ms                                1.02 K             
  │ │ │ │ │ │ └ sddk::inner                                                            50.08 ms                                1.02 K             
  │ │ │ │ │ │   └ sddk::inner|local                                                    50.07 ms                                1.02 K             
  │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|2                             56.54 μs                                1.02 K             
  │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|3                            255.09 ms                                1.02 K             
  │ │ │ │ │ └ sirius::Hubbard::compute_occupation_matrix|4                             57.64 μs                                1.02 K             
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.01 ms →  25.89 ms  (+1185.09%)         512   →    512               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               205.62 μs →   1.51 ms   (+636.67%)         128   →    128               
- │ │ │ │ └ sirius::Density::augment                                        5.74 ms →   9.96 ms    (+73.61%)          64   →     64               
- │ │ │ │   └ sirius::Density::generate_rho_aug                             5.54 ms →   9.74 ms    (+75.79%)          64   →     64               
  │ │ │ ├ sirius::Field4D::symmetrize                                      24.38 ms →  25.06 ms     (+2.79%)          64   →     64               
  │ │ │ │ ├ sirius::symmetrize_function|fpw                                12.34 ms →  12.64 ms     (+2.43%)          64   →     64               
  │ │ │ │ │ ├ sddk::Gvec_shells::remap_forward                              2.18 ms →   2.14 ms     (-1.85%)          64   →     64               
  │ │ │ │ │ ├ sirius::symmetrize_function|fpw|local                         7.96 ms →   8.31 ms     (+4.37%)          64   →     64               
  │ │ │ │ │ └ sddk::Gvec_shells::remap_backward                             2.15 ms →   2.14 ms     (-0.35%)          64   →     64               
  │ │ │ │ └ sirius::symmetrize_vector_function|vzpw                        12.04 ms →  12.42 ms     (+3.16%)          64   →     64               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              2.12 ms →   2.06 ms     (-2.75%)          64   →     64               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                             2.13 ms →   2.12 ms     (-0.24%)          64   →     64               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       21.42 ms →  20.67 ms     (-3.46%)          64   →     64               
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 298.36 μs →   1.72 ms   (+477.13%)         128   →    128               
  │ │ ├ sirius::Density::mix                                              110.18 ms → 115.89 ms     (+5.17%)          64   →     64               
- │ │ │ ├ sirius::Density::mixer_input                                    539.98 μs → 599.50 μs    (+11.02%)          64   →     64               
  │ │ │ ├ sirius::Periodic_function|inner                                   1.39 ms →   1.40 ms     (+1.07%)        1.81 K →   1.81 K             
  │ │ │ │ └ sirius::Periodic_function|inner_local                           1.39 ms →   1.40 ms     (+1.15%)        1.81 K →   1.81 K             
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  1.39 ms →   1.40 ms     (+1.15%)        1.81 K →   1.81 K             
- │ │ │ └ sirius::Density::mixer_output                                     1.04 ms →   3.90 ms   (+275.13%)          64   →     64               
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform               241.28 μs →   1.65 ms   (+584.50%)         128   →    128               
  │ │ ├ sirius::Potential::generate                                       785.27 ms → 846.03 ms     (+7.74%)          64   →     64               
- │ │ │ ├ sirius::Potential::poisson                                        4.06 ms →   5.19 ms    (+27.71%)          64   →     64               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               298.46 μs →   1.35 ms   (+351.57%)          64   →     64               
  │ │ │ │ └ sirius::Periodic_function|inner                                 1.35 ms →   1.41 ms     (+4.59%)          64   →     64               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         1.35 ms →   1.41 ms     (+4.69%)          64   →     64               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                1.35 ms →   1.41 ms     (+4.70%)          64   →     64               
- │ │ │ ├ sirius::Periodic_function::add                                  120.89 μs → 135.87 μs    (+12.39%)         128   →    128               
- │ │ │ ├ sirius::Potential::xc                                            88.30 ms → 120.33 ms    (+36.26%)          64   →     64               
- │ │ │ │ └ sirius::Potential::xc_rg_magnetic                              88.05 ms → 120.10 ms    (+36.41%)          64   →     64               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            228.00 μs → 221.21 μs     (-2.98%)        1.09 K →   1.09 K             
- │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|up_dn                     833.41 μs → 983.40 μs    (+18.00%)          64   →     64               
- │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|grad1                       8.20 ms →  19.43 ms   (+136.80%)          64   →     64               
- │ │ │ │   │ ├ sirius::Smooth_periodic_function::fft_transform           259.95 μs →   1.62 ms   (+522.79%)         512   →    512               
  │ │ │ │   │ ├ sirius::gradient                                            1.36 ms →   1.41 ms     (+4.15%)         128   →    128               
  │ │ │ │   │ │ └ sirius::Smooth_periodic_function                        363.27 μs → 365.12 μs     (+0.51%)         384   →    384               
  │ │ │ │   │ └ sirius::dot                                                 1.13 ms →   1.21 ms     (+7.10%)         192   →    192               
  │ │ │ │   │   └ sirius::Smooth_periodic_function                        479.74 μs → 485.35 μs     (+1.17%)         192   →    192               
  │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|libxc                      16.03 ms →  16.29 ms     (+1.67%)         128   →    128               
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform             368.72 μs →   1.56 ms   (+322.73%)        1.02 K →   1.02 K             
  │ │ │ │   └ sirius::divergence                                            3.65 ms →   3.63 ms     (-0.40%)         256   →    256               
  │ │ │ │     └ sirius::Smooth_periodic_function                          287.55 μs → 275.06 μs     (-4.34%)         256   →    256               
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 272.53 μs →   1.59 ms   (+483.95%)         128   →    128               
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     5.41 ms →  15.54 ms   (+187.14%)          64   →     64               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             686.41 ms → 701.22 ms     (+2.16%)          64   →     64               
  │ │ ├ sirius::Field4D::symmetrize                                        24.75 ms →  24.62 ms     (-0.53%)          64   →     64               
  │ │ │ ├ sirius::symmetrize_function|fpw                                  12.45 ms →  12.35 ms     (-0.77%)          64   →     64               
  │ │ │ │ ├ sddk::Gvec_shells::remap_forward                                2.16 ms →   2.09 ms     (-3.19%)          64   →     64               
  │ │ │ │ ├ sirius::symmetrize_function|fpw|local                           8.09 ms →   8.14 ms     (+0.61%)          64   →     64               
  │ │ │ │ └ sddk::Gvec_shells::remap_backward                               2.15 ms →   2.07 ms     (-3.40%)          64   →     64               
  │ │ │ └ sirius::symmetrize_vector_function|vzpw                          12.30 ms →  12.26 ms     (-0.27%)          64   →     64               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                                2.12 ms →   2.04 ms     (-3.65%)          64   →     64               
  │ │ │   └ sddk::Gvec_shells::remap_backward                               2.13 ms →   2.06 ms     (-3.06%)          64   →     64               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                   724.27 μs →   1.56 ms   (+115.02%)         128   →    128               
  │ │ ├ sirius::Periodic_function|inner                                     1.37 ms →   1.40 ms     (+2.29%)         704   →    704               
  │ │ │ └ sirius::Periodic_function|inner_local                             1.37 ms →   1.40 ms     (+2.31%)         704   →    704               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    1.37 ms →   1.40 ms     (+2.31%)         704   →    704               
  │ │ ├ sirius::Smooth_periodic_function|inner                            999.16 μs → 981.61 μs     (-1.76%)         192   →    192               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    998.34 μs → 980.93 μs     (-1.74%)         192   →    192               
  │ │ ├ sirius::Periodic_function::integrate                                1.06 ms →   1.09 ms     (+2.69%)          64   →     64               
  │ │ ├ sirius::Density::get_magnetisation                                  1.28 ms →   1.28 ms     (+0.29%)          64   →     64               
  │ │ │ ├ sirius::Periodic_function::integrate                              1.08 ms →   1.09 ms     (+0.54%)          64   →     64               
  │ │ │ └ sirius::Density::compute_atomic_mag_mom                         197.01 μs → 195.21 μs     (-0.91%)          64   →     64               
+ │ │ └ sirius::Hubbard::compute_occupation_matrix                          6.33 s  →   5.27 s     (-16.74%)          63   →     63               
+ │ │   └ sddk::inner                                                      59.87 ms →  52.06 ms    (-13.04%)        1.01 K →   1.01 K             
+ │ │     └ sddk::inner|local                                              59.87 ms →  52.06 ms    (-13.04%)        1.01 K →   1.01 K             
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                        68.59 μs →  65.77 μs     (-4.12%)           4   →      4               
  │ ├ sirius::Periodic_function|inner                                       1.28 ms →   1.33 ms     (+3.66%)           9   →      9               
  │ │ └ sirius::Periodic_function|inner_local                               1.28 ms →   1.33 ms     (+3.67%)           9   →      9               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      1.28 ms →   1.33 ms     (+3.67%)           9   →      9               
  │ └ sirius::Smooth_periodic_function|inner                              951.25 μs → 936.18 μs     (-1.58%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      950.65 μs → 935.74 μs     (-1.57%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         1.27 ms →   1.36 ms     (+6.97%)           3   →      3               
  │ └ sirius::Periodic_function|inner_local                                 1.27 ms →   1.36 ms     (+6.98%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.27 ms →   1.36 ms     (+6.98%)           3   →      3               
  ├ sirius::Smooth_periodic_function|inner                                989.49 μs → 996.92 μs     (+0.75%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                        989.10 μs → 996.12 μs     (+0.71%)           1   →      1               
- └ sirius::finalize                                                      527.86 ms →   1.17 s    (+120.87%)           1   →      1               
```
