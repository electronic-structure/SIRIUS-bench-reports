# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 495e097f8fb7cb2be32f3783e9a2314d02bcfd52
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
! sirius                                                                  547.32 s  → 857.07 s     (+56.59%)           1   →      1               
! ├ sirius::initialize                                                      3.44 s  →   2.98 s     (-13.11%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                 13.91 s  →  13.95 s      (+0.31%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               258.68 μs → 264.62 μs     (+2.29%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       450.39 ms → 443.71 ms     (-1.48%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                           440.63 ms → 435.68 ms     (-1.12%)           1   →      1               
! │ │ └ sirius::Unit_cell::update                                           9.70 ms →   7.97 ms    (-17.81%)           1   →      1               
! │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      195.07 μs → 166.37 μs    (-14.72%)           1   →      1               
! │ │   └ sirius::Unit_cell::get_symmetry                                   9.47 ms →   7.77 ms    (-17.95%)           1   →      1               
! │ │     └ sirius::Unit_cell_symmetry                                      9.46 ms →   7.76 ms    (-17.98%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.73 ms →   4.81 ms     (+1.56%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                             31.36 μs →  29.10 μs     (-7.20%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               14.08 μs →  13.76 μs     (-2.32%)           1   →      1               
  │ └ sirius::Simulation_context::update                                   13.41 s  →  13.46 s      (+0.41%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           4.92 ms →   4.94 ms     (+0.30%)           1   →      1               
! │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       39.26 μs →  23.16 μs    (-41.02%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   4.86 ms →   4.90 ms     (+0.72%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      4.85 ms →   4.89 ms     (+0.82%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.78 ms →   4.79 ms     (+0.22%)           1   →      1               
! │   │     ├ sirius::Unit_cell_symmetry|equiv                             12.25 μs →  45.59 μs   (+272.29%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               13.42 μs →  12.45 μs     (-7.23%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                        3.07 s  →   3.10 s      (+0.97%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                          151.70 ms → 153.46 ms     (+1.16%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                               133.67 ms → 135.19 ms     (+1.14%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                     460.03 ms → 468.53 ms     (+1.85%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                     840.10 ms → 839.38 ms     (-0.09%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                               785.14 ms → 785.13 ms     (-0.00%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    7.35 ms →   7.36 ms     (+0.09%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      4.62 ms →   4.64 ms     (+0.50%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   7.87 ms →   7.99 ms     (+1.50%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                757.28 μs → 753.98 μs     (-0.44%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 161.59 ms → 170.03 ms     (+5.22%)           1   →      1               
! ├ sirius::K_point_set::create_k_mesh                                     62.74 ms →  49.74 ms    (-20.72%)           1   →      1               
! │ ├ sirius::K_point::K_point                                            843.75 ns → 702.50 ns    (-16.74%)           8   →      8               
! │ └ sirius::K_point_set::initialize                                      62.64 ms →  49.65 ms    (-20.73%)           1   →      1               
! │   └ sirius::K_point::initialize                                         7.66 ms →   6.05 ms    (-21.10%)           8   →      8               
  │     ├ sirius::K_point::generate_gkvec                                   1.21 ms →   1.15 ms     (-5.35%)           8   →      8               
! │     │ └ sddk::Gvec::init                                              237.69 μs → 212.51 μs    (-10.59%)           8   →      8               
  │     ├ sddk::matrix_storage::matrix_storage                              2.41 μs →   2.46 μs     (+2.01%)          32   →     32               
! │     └ sirius::K_point::update                                           6.33 ms →   4.76 ms    (-24.74%)           8   →      8               
  │       ├ sirius::Beta_projectors                                       339.68 μs → 361.96 μs     (+6.56%)           8   →      8               
  │       │ └ sirius::Beta_projectors::generate_pw_coefs_t                254.52 μs → 261.90 μs     (+2.90%)           8   →      8               
! │       ├ sddk::matrix_storage::matrix_storage                            3.04 μs →   3.60 μs    (+18.21%)           8   →      8               
  │       ├ sirius::Non_local_operator                                     25.49 μs →  27.14 μs     (+6.46%)           8   →      8               
! │       ├ sirius::Q_operator::initialize                                 31.66 μs →  35.44 μs    (+11.97%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::prepare                           3.39 μs →   3.49 μs     (+3.06%)           8   →      8               
! │       ├ sirius::Beta_projectors_base::generate                         37.12 μs →  41.02 μs    (+10.51%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::inner                           123.79 μs → 125.30 μs     (+1.22%)           8   →      8               
  │       ├ sirius::Non_local_operator::apply                              70.67 μs →  70.95 μs     (+0.40%)           8   →      8               
! │       ├ sirius::Beta_projectors_base::dismiss                         491.63 ns → 560.38 ns    (+13.98%)           8   →      8               
  │       ├ sddk::inner                                                   116.10 μs → 118.28 μs     (+1.88%)           8   →      8               
  │       │ └ sddk::inner|local                                            21.39 μs →  23.14 μs     (+8.16%)           8   →      8               
! │       ├ Eigensolver_lapack|zheevd                                       4.87 ms →   3.26 ms    (-33.16%)           8   →      8               
! │       └ sddk::transform                                                57.70 μs →  65.03 μs    (+12.71%)           8   →      8               
  │         ├ sddk::transform|init                                          7.81 μs →   8.52 μs     (+9.05%)           8   →      8               
! │         └ sddk::transform|local                                        14.44 μs →  16.76 μs    (+16.07%)           8   →      8               
  ├ sirius::Smooth_periodic_function                                      463.16 μs → 456.66 μs     (-1.40%)           4   →      4               
  ├ sirius::Potential                                                       6.61 ms →   6.84 ms     (+3.53%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    477.95 μs → 474.34 μs     (-0.76%)           7   →      7               
  │ └ sirius::Potential::update                                             2.70 ms →   2.95 ms     (+9.54%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         2.66 ms →   2.92 ms     (+9.67%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                2.22 ms →   2.43 ms     (+9.48%)           1   →      1               
! │     └ sirius::Smooth_periodic_function::fft_transform                 359.13 μs → 410.17 μs    (+14.21%)           1   →      1               
  ├ sirius::Density                                                         3.55 ms →   3.72 ms     (+4.81%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    209.10 μs → 214.55 μs     (+2.61%)           3   →      3               
  │ └ sirius::Density::update                                               2.92 ms →   3.07 ms     (+5.20%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                2.88 ms →   3.03 ms     (+5.25%)           1   →      1               
! │     ├ sirius::rho_core_ri_pseudo|values                                18.14 μs →  20.16 μs    (+11.08%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                2.57 ms →   2.67 ms     (+3.85%)           1   →      1               
! │     └ sirius::Smooth_periodic_function::fft_transform                 258.37 μs → 308.81 μs    (+19.52%)           1   →      1               
  ├ sirius::Density::initial_density                                      131.94 ms → 133.39 ms     (+1.10%)           1   →      1               
! │ ├ sirius::Simulation_context::make_periodic_function                    3.10 ms →   3.43 ms    (+10.52%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     249.03 μs → 266.24 μs     (+6.91%)           3   →      3               
  │ └ sirius::Periodic_function::integrate                                  1.07 ms →   1.11 ms     (+3.33%)           1   →      1               
  ├ sirius::Potential::generate                                           792.10 ms → 803.80 ms     (+1.48%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            3.88 ms →   4.19 ms     (+8.00%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   319.84 μs → 303.50 μs     (-5.11%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     1.34 ms →   1.40 ms     (+4.31%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             1.34 ms →   1.39 ms     (+4.38%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    1.34 ms →   1.39 ms     (+4.39%)           1   →      1               
! │ ├ sirius::Periodic_function::add                                      106.37 μs → 129.98 μs    (+22.20%)           2   →      2               
  │ ├ sirius::Potential::xc                                                86.64 ms →  88.40 ms     (+2.03%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_magnetic                                  86.39 ms →  88.13 ms     (+2.02%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                269.81 μs → 274.29 μs     (+1.66%)          17   →     17               
  │ │   ├ sirius::Potential::xc_rg_magnetic|up_dn                         862.02 μs → 911.37 μs     (+5.72%)           1   →      1               
  │ │   ├ sirius::Potential::xc_rg_magnetic|grad1                           9.16 ms →   9.18 ms     (+0.17%)           1   →      1               
  │ │   │ ├ sirius::Smooth_periodic_function::fft_transform               267.07 μs → 291.88 μs     (+9.29%)           8   →      8               
  │ │   │ ├ sirius::gradient                                                1.71 ms →   1.71 ms     (-0.09%)           2   →      2               
  │ │   │ │ └ sirius::Smooth_periodic_function                            474.21 μs → 472.77 μs     (-0.30%)           6   →      6               
  │ │   │ └ sirius::dot                                                     1.20 ms →   1.14 ms     (-4.92%)           3   →      3               
  │ │   │   └ sirius::Smooth_periodic_function                            496.65 μs → 471.89 μs     (-4.99%)           3   →      3               
  │ │   ├ sirius::Potential::xc_rg_magnetic|libxc                          15.49 ms →  15.75 ms     (+1.64%)           2   →      2               
  │ │   ├ sirius::Smooth_periodic_function::fft_transform                 263.68 μs → 279.85 μs     (+6.14%)          16   →     16               
  │ │   └ sirius::divergence                                                3.69 ms →   3.65 ms     (-1.06%)           4   →      4               
  │ │     └ sirius::Smooth_periodic_function                              283.24 μs → 290.68 μs     (+2.63%)           4   →      4               
! │ ├ sirius::Smooth_periodic_function::fft_transform                       3.18 ms →   1.29 ms    (-59.56%)           2   →      2               
! │ ├ sirius::Potential::generate_D_operator_matrix                         8.72 ms →  13.03 ms    (+49.40%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 686.00 ms → 695.06 ms     (+1.32%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  919.11 μs → 929.57 μs     (+1.14%)           1   →      1               
  │ ├ sirius::Local_operator                                              749.03 μs → 773.91 μs     (+3.32%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   18.84 μs →  18.39 μs     (-2.37%)           2   →      2               
! │ │ └ sirius::Smooth_periodic_function::fft_transform                   215.02 μs → 241.15 μs    (+12.15%)           2   →      2               
! │ ├ sirius::Non_local_operator                                           41.35 μs →  33.09 μs    (-19.98%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       40.20 μs →  43.67 μs     (+8.63%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       38.44 μs →  35.35 μs     (-8.04%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      85.44 ms →  89.59 ms     (+4.86%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                30.21 μs →  29.04 μs     (-3.87%)           8   →      8               
  │ │ ├ sirius::Local_operator::prepare_k                                  25.65 μs →  24.27 μs     (-5.35%)           8   →      8               
! │ │ └ sirius::Beta_projectors_base::prepare                               2.85 μs →   3.16 μs    (+11.00%)           8   →      8               
  │ ├ sirius::Band::initialize_subspace|kp                                 10.65 ms →  11.17 ms     (+4.88%)           8   →      8               
  │ │ ├ sddk::matrix_storage::matrix_storage                                7.26 μs →   7.43 μs     (+2.43%)          32   →     32               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                   386.45 μs → 361.64 μs     (-6.42%)           8   →      8               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            59.36 μs →  64.91 μs     (+9.34%)           8   →      8               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    3.34 ms →   3.65 ms     (+9.41%)          16   →     16               
! │ │ │ ├ sirius::Local_operator::apply_h                                   2.72 ms →   3.04 ms    (+12.04%)          16   →     16               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.22 μs →   2.10 μs     (-5.38%)          16   →     16               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.64 μs →   1.57 μs     (-4.45%)          16   →     16               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           502.44 ns → 514.75 ns     (+2.45%)          16   →     16               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          595.56 ns → 600.06 ns     (+0.76%)          16   →     16               
! │ │ │ ├ sirius::Beta_projectors_base::generate                           44.19 μs →  49.04 μs    (+10.99%)          16   →     16               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             133.40 μs → 135.69 μs     (+1.72%)          16   →     16               
  │ │ │ ├ sirius::Non_local_operator::apply                                79.17 μs →  72.53 μs     (-8.39%)          32   →     32               
  │ │ │ ├ sddk::inner                                                     127.72 μs → 123.34 μs     (-3.43%)          16   →     16               
  │ │ │ │ └ sddk::inner|local                                              22.93 μs →  23.33 μs     (+1.77%)          16   →     16               
  │ │ │ └ sddk::transform                                                  67.57 μs →  66.10 μs     (-2.17%)          16   →     16               
  │ │ │   ├ sddk::transform|init                                           10.22 μs →  10.81 μs     (+5.76%)          16   →     16               
  │ │ │   └ sddk::transform|local                                          13.12 μs →  13.13 μs     (+0.02%)          16   →     16               
  │ │ ├ sirius::Band::set_subspace_mtrx                                   126.45 μs → 118.19 μs     (-6.53%)          32   →     32               
  │ │ │ └ sddk::inner                                                     123.44 μs → 115.19 μs     (-6.68%)          32   →     32               
  │ │ │   └ sddk::inner|local                                              21.44 μs →  20.92 μs     (-2.42%)          32   →     32               
  │ │ ├ Eigensolver_cuda|zhegvdx                                            1.24 ms →   1.22 ms     (-1.78%)          16   →     16               
  │ │ └ sddk::transform                                                    74.80 μs →  72.84 μs     (-2.62%)          16   →     16               
  │ │   ├ sddk::transform|init                                              9.82 μs →   9.51 μs     (-3.13%)          16   →     16               
  │ │   └ sddk::transform|local                                            12.83 μs →  12.10 μs     (-5.69%)          16   →     16               
! │ └ sirius::Beta_projectors_base::dismiss                               435.75 ns → 509.63 ns    (+16.95%)           8   →      8               
! ├ sirius::DFT_ground_state::scf_loop                                    527.84 s  → 838.42 s     (+58.84%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    433.38 μs → 438.78 μs     (+1.25%)          38   →     38               
  │ ├ sirius::Hubbard::compute_occupation_matrix                            6.42 s  →   6.40 s      (-0.23%)           1   →      1               
  │ │ └ sddk::inner                                                        59.21 ms →  59.54 ms     (+0.57%)          16   →     16               
  │ │   └ sddk::inner|local                                                59.21 ms →  59.54 ms     (+0.57%)          16   →     16               
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                          8.02 s  →  13.42 s     (+67.29%)          65   →     62       (-4.62%)
  │ │ ├ sirius::Hamiltonian0                                                4.37 ms →   4.41 ms     (+0.88%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Local_operator                                            2.27 ms →   2.49 ms     (+9.67%)          65   →     62       (-4.62%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                               20.08 μs →  19.13 μs     (-4.75%)         130   →    124       (-4.62%)
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               209.49 μs → 229.98 μs     (+9.78%)         130   →    124       (-4.62%)
  │ │ │ ├ sirius::Non_local_operator                                        1.00 ms → 907.56 μs     (-9.28%)         130   →    124       (-4.62%)
  │ │ │ ├ sirius::D_operator::initialize                                   52.49 μs →  55.57 μs     (+5.86%)          65   →     62       (-4.62%)
  │ │ │ └ sirius::Q_operator::initialize                                   32.52 μs →  32.55 μs     (+0.10%)          65   →     62       (-4.62%)
! │ │ ├ sirius::Band::solve                                               678.68 ms →   2.05 s    (+201.67%)          65   →     62       (-4.62%)
! │ │ │ ├ sirius::Hamiltonian_k                                            35.66 μs →  52.75 μs    (+47.94%)         520   →    496       (-4.62%)
! │ │ │ │ ├ sirius::Local_operator::prepare_k                              32.46 μs →  49.16 μs    (+51.45%)         520   →    496       (-4.62%)
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                           2.37 μs →   2.63 μs    (+10.93%)         520   →    496       (-4.62%)
! │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     84.78 ms → 255.85 ms   (+201.77%)         520   →    496       (-4.62%)
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc              1.33 ms →   2.76 ms   (+107.07%)         520   →    496       (-4.62%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        908.52 ns → 910.92 ns     (+0.26%)        3.12 K →   2.98 K     (-4.62%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           915.92 μs → 936.24 μs     (+2.22%)         520   →    496       (-4.62%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        28.38 μs →  27.51 μs     (-3.07%)        1.04 K →    992       (-4.62%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       380.81 μs → 387.03 μs     (+1.63%)        1.04 K →    992       (-4.62%)
! │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              82.39 ms → 252.03 ms   (+205.88%)         520   →    496       (-4.62%)
! │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              6.57 ms →  19.32 ms   (+193.79%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ ├ sirius::Local_operator::apply_h                             5.39 ms →  15.93 ms   (+195.72%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.88 μs →   1.83 μs     (-2.98%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.53 μs →   1.53 μs     (-0.20%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     438.14 ns → 426.87 ns     (-2.57%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    447.34 ns → 405.71 ns     (-9.31%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                     48.88 μs →  41.99 μs    (-14.10%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       325.64 μs →   1.07 ms   (+229.61%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ ├ sirius::Non_local_operator::apply                          75.19 μs →  70.12 μs     (-6.74%)        7.93 K →   7.97 K     (+0.43%)
! │ │ │ │   │ ├ sddk::inner                                               309.16 μs →   1.01 ms   (+227.69%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ │ └ sddk::inner|local                                        18.58 μs →  18.50 μs     (-0.46%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ └ sddk::transform                                           268.96 μs →   1.03 ms   (+281.29%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │   ├ sddk::transform|init                                      8.31 μs →   8.68 μs     (+4.38%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │   └ sddk::transform|local                                    10.50 μs →  10.42 μs     (-0.79%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   ├ sddk::orthogonalize                                         959.59 μs →   3.80 ms   (+296.24%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ ├ sddk::inner                                               284.09 μs →   1.09 ms   (+281.94%)        6.89 K →   6.97 K     (+1.19%)
  │ │ │ │   │ │ └ sddk::inner|local                                        16.98 μs →  16.93 μs     (-0.28%)        6.89 K →   6.97 K     (+1.19%)
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 253.42 μs →   1.03 ms   (+306.30%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                              44.13 μs →  44.85 μs     (+1.63%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ └ sddk::transform                                           222.78 μs →   1.10 ms   (+392.52%)        2.93 K →   2.99 K     (+2.22%)
  │ │ │ │   │   ├ sddk::transform|init                                     16.46 μs →  17.64 μs     (+7.13%)        2.93 K →   2.99 K     (+2.22%)
  │ │ │ │   │   └ sddk::transform|local                                     7.37 μs →   7.97 μs     (+8.12%)        8.78 K →   8.97 K     (+2.22%)
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             335.50 μs →   1.15 ms   (+243.47%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   │ └ sddk::inner                                               318.29 μs →   1.12 ms   (+251.43%)        3.97 K →   3.98 K     (+0.43%)
  │ │ │ │   │   └ sddk::inner|local                                        17.32 μs →  17.35 μs     (+0.14%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   ├ Eigensolver_cuda|zheevdx                                      1.78 ms →   2.85 ms    (+60.57%)        3.97 K →   3.98 K     (+0.43%)
! │ │ │ │   ├ sirius::residuals                                           877.35 μs →   3.12 ms   (+256.19%)        3.96 K →   3.98 K     (+0.43%)
! │ │ │ │   │ ├ sddk::transform                                           301.60 μs →   1.01 ms   (+234.19%)        3.53 K →   3.55 K     (+0.51%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     12.72 μs →  12.68 μs     (-0.33%)        3.53 K →   3.55 K     (+0.51%)
  │ │ │ │   │ │ └ sddk::transform|local                                    10.01 μs →  10.08 μs     (+0.72%)        7.06 K →   7.10 K     (+0.51%)
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               621.57 μs →   2.44 ms   (+291.87%)        3.53 K →   3.55 K     (+0.51%)
! │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     414.62 μs →   1.80 ms   (+333.96%)        2.54 K →   2.49 K     (-1.81%)
! │ │ │ │     └ sddk::transform                                           249.72 μs →   1.11 ms   (+345.37%)        4.03 K →   3.99 K     (-1.09%)
  │ │ │ │       ├ sddk::transform|init                                      9.86 μs →   9.81 μs     (-0.46%)        4.03 K →   3.99 K     (-1.09%)
  │ │ │ │       └ sddk::transform|local                                     9.32 μs →   9.56 μs     (+2.58%)        5.53 K →   5.49 K     (-0.76%)
! │ │ │ ├ sirius::Beta_projectors_base::dismiss                           492.47 ns → 543.55 ns    (+10.37%)         520   →    496       (-4.62%)
  │ │ │ └ sirius::K_point_set::sync_band_energies                          18.99 μs →  19.48 μs     (+2.57%)          65   →     62       (-4.62%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                        538.33 μs → 500.76 μs     (-6.98%)          65   →     62       (-4.62%)
! │ │ ├ sirius::Density::generate                                         197.80 ms →   5.39 s   (+2625.79%)          65   →     62       (-4.62%)
! │ │ │ ├ sirius::Density::generate_valence                                28.41 ms →   5.21 s  (+18247.84%)          65   →     62       (-4.62%)
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                             1.78 μs →   2.05 μs    (+14.81%)        1.04 K →    992       (-4.62%)
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.52 μs →   1.78 μs    (+17.49%)        1.04 K →    992       (-4.62%)
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  463.68 μs →   3.39 ms   (+630.63%)         520   →    496       (-4.62%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         2.35 μs →   4.83 μs   (+105.65%)         520   →    496       (-4.62%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                      110.37 μs →  51.92 μs    (-52.96%)         520   →    496       (-4.62%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         157.95 μs →   1.61 ms   (+919.43%)        1.04 K →    992       (-4.62%)
! │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       515.95 ns → 885.97 ns    (+71.72%)         520   →    496       (-4.62%)
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_om                              617.87 ms                                 496               
+ │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|1                             49.38 ms                                 992               
+ │ │ │ │ │ │ └ sddk::inner                                                            49.38 ms                                 992               
+ │ │ │ │ │ │   └ sddk::inner|local                                                    49.38 ms                                 992               
+ │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|2                             76.03 μs                                 992               
+ │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|3                            259.38 ms                                 992               
+ │ │ │ │ │ └ sirius::Hubbard::compute_occupation_matrix|4                             91.33 μs                                 992               
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.17 ms →  26.03 ms  (+1099.45%)         520   →    496       (-4.62%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               172.76 μs →   1.47 ms   (+752.76%)         130   →    124       (-4.62%)
! │ │ │ │ └ sirius::Density::augment                                        5.51 ms →   9.88 ms    (+79.23%)          65   →     62       (-4.62%)
! │ │ │ │   └ sirius::Density::generate_rho_aug                             5.31 ms →   9.66 ms    (+81.90%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Field4D::symmetrize                                      24.47 ms →  25.40 ms     (+3.80%)          65   →     62       (-4.62%)
  │ │ │ │ ├ sirius::symmetrize_function|fpw                                12.40 ms →  12.75 ms     (+2.86%)          65   →     62       (-4.62%)
  │ │ │ │ │ ├ sddk::Gvec_shells::remap_forward                              2.18 ms →   2.21 ms     (+1.50%)          65   →     62       (-4.62%)
  │ │ │ │ │ ├ sirius::symmetrize_function|fpw|local                         8.02 ms →   8.32 ms     (+3.72%)          65   →     62       (-4.62%)
  │ │ │ │ │ └ sddk::Gvec_shells::remap_backward                             2.15 ms →   2.17 ms     (+1.11%)          65   →     62       (-4.62%)
  │ │ │ │ └ sirius::symmetrize_vector_function|vzpw                        12.07 ms →  12.65 ms     (+4.77%)          65   →     62       (-4.62%)
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              2.11 ms →   2.13 ms     (+1.07%)          65   →     62       (-4.62%)
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                             2.13 ms →   2.19 ms     (+2.81%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       21.39 ms →  21.42 ms     (+0.16%)          65   →     62       (-4.62%)
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 307.01 μs →   1.76 ms   (+474.10%)         130   →    124       (-4.62%)
  │ │ ├ sirius::Density::mix                                              110.44 ms → 116.38 ms     (+5.38%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Density::mixer_input                                    544.44 μs → 588.90 μs     (+8.17%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Periodic_function|inner                                   1.39 ms →   1.40 ms     (+0.69%)        1.84 K →   1.75 K     (-4.90%)
  │ │ │ │ └ sirius::Periodic_function|inner_local                           1.39 ms →   1.40 ms     (+0.77%)        1.84 K →   1.75 K     (-4.90%)
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  1.39 ms →   1.40 ms     (+0.77%)        1.84 K →   1.75 K     (-4.90%)
! │ │ │ └ sirius::Density::mixer_output                                     1.03 ms →   4.08 ms   (+295.29%)          65   →     62       (-4.62%)
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform               239.86 μs →   1.75 ms   (+629.53%)         130   →    124       (-4.62%)
  │ │ ├ sirius::Potential::generate                                       815.69 ms → 852.62 ms     (+4.53%)          65   →     62       (-4.62%)
! │ │ │ ├ sirius::Potential::poisson                                        3.92 ms →   5.48 ms    (+39.85%)          65   →     62       (-4.62%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               300.68 μs →   1.52 ms   (+405.09%)          65   →     62       (-4.62%)
  │ │ │ │ └ sirius::Periodic_function|inner                                 1.35 ms →   1.40 ms     (+3.96%)          65   →     62       (-4.62%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                         1.35 ms →   1.40 ms     (+4.05%)          65   →     62       (-4.62%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                1.35 ms →   1.40 ms     (+4.07%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Periodic_function::add                                  122.99 μs → 134.90 μs     (+9.69%)         130   →    124       (-4.62%)
! │ │ │ ├ sirius::Potential::xc                                            88.15 ms → 122.47 ms    (+38.93%)          65   →     62       (-4.62%)
! │ │ │ │ └ sirius::Potential::xc_rg_magnetic                              87.89 ms → 122.24 ms    (+39.08%)          65   →     62       (-4.62%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                            226.92 μs → 223.17 μs     (-1.65%)        1.10 K →   1.05 K     (-4.62%)
! │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|up_dn                     836.91 μs → 985.65 μs    (+17.77%)          65   →     62       (-4.62%)
! │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|grad1                       8.13 ms →  19.83 ms   (+143.84%)          65   →     62       (-4.62%)
! │ │ │ │   │ ├ sirius::Smooth_periodic_function::fft_transform           255.66 μs →   1.67 ms   (+554.72%)         520   →    496       (-4.62%)
  │ │ │ │   │ ├ sirius::gradient                                            1.34 ms →   1.42 ms     (+5.77%)         130   →    124       (-4.62%)
  │ │ │ │   │ │ └ sirius::Smooth_periodic_function                        359.12 μs → 369.43 μs     (+2.87%)         390   →    372       (-4.62%)
  │ │ │ │   │ └ sirius::dot                                                 1.13 ms →   1.20 ms     (+5.85%)         195   →    186       (-4.62%)
  │ │ │ │   │   └ sirius::Smooth_periodic_function                        473.90 μs → 488.43 μs     (+3.07%)         195   →    186       (-4.62%)
  │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|libxc                      15.83 ms →  16.32 ms     (+3.13%)         130   →    124       (-4.62%)
! │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform             386.91 μs →   1.65 ms   (+325.61%)        1.04 K →    992       (-4.62%)
  │ │ │ │   └ sirius::divergence                                            3.65 ms →   3.66 ms     (+0.40%)         260   →    248       (-4.62%)
  │ │ │ │     └ sirius::Smooth_periodic_function                          286.52 μs → 276.06 μs     (-3.65%)         260   →    248       (-4.62%)
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 419.70 μs →   1.66 ms   (+296.40%)         130   →    124       (-4.62%)
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     4.91 ms →  16.17 ms   (+229.21%)          65   →     62       (-4.62%)
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             717.32 ms → 704.60 ms     (-1.77%)          65   →     62       (-4.62%)
  │ │ ├ sirius::Field4D::symmetrize                                        25.61 ms →  24.64 ms     (-3.79%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::symmetrize_function|fpw                                  12.92 ms →  12.43 ms     (-3.75%)          65   →     62       (-4.62%)
  │ │ │ │ ├ sddk::Gvec_shells::remap_forward                                2.18 ms →   2.11 ms     (-3.21%)          65   →     62       (-4.62%)
  │ │ │ │ ├ sirius::symmetrize_function|fpw|local                           8.48 ms →   8.19 ms     (-3.46%)          65   →     62       (-4.62%)
  │ │ │ │ └ sddk::Gvec_shells::remap_backward                               2.20 ms →   2.08 ms     (-5.34%)          65   →     62       (-4.62%)
  │ │ │ └ sirius::symmetrize_vector_function|vzpw                          12.70 ms →  12.21 ms     (-3.82%)          65   →     62       (-4.62%)
  │ │ │   ├ sddk::Gvec_shells::remap_forward                                2.14 ms →   2.05 ms     (-4.45%)          65   →     62       (-4.62%)
  │ │ │   └ sddk::Gvec_shells::remap_backward                               2.17 ms →   2.07 ms     (-4.38%)          65   →     62       (-4.62%)
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                     1.46 ms →   1.67 ms    (+14.19%)         130   →    124       (-4.62%)
  │ │ ├ sirius::Periodic_function|inner                                     1.38 ms →   1.42 ms     (+3.06%)         715   →    682       (-4.62%)
  │ │ │ └ sirius::Periodic_function|inner_local                             1.38 ms →   1.42 ms     (+3.08%)         715   →    682       (-4.62%)
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    1.38 ms →   1.42 ms     (+3.08%)         715   →    682       (-4.62%)
  │ │ ├ sirius::Smooth_periodic_function|inner                              1.00 ms → 995.38 μs     (-0.85%)         195   →    186       (-4.62%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      1.00 ms → 994.61 μs     (-0.84%)         195   →    186       (-4.62%)
  │ │ ├ sirius::Periodic_function::integrate                                1.04 ms →   1.09 ms     (+4.22%)          65   →     62       (-4.62%)
  │ │ ├ sirius::Density::get_magnetisation                                  1.24 ms →   1.29 ms     (+3.76%)          65   →     62       (-4.62%)
  │ │ │ ├ sirius::Periodic_function::integrate                              1.04 ms →   1.09 ms     (+4.43%)          65   →     62       (-4.62%)
  │ │ │ └ sirius::Density::compute_atomic_mag_mom                         198.44 μs → 198.71 μs     (+0.13%)          65   →     62       (-4.62%)
! │ │ └ sirius::Hubbard::compute_occupation_matrix                          6.26 s  →   5.04 s     (-19.54%)          64   →     61       (-4.69%)
! │ │   └ sddk::inner                                                      66.48 ms →  49.28 ms    (-25.87%)        1.02 K →    976       (-4.69%)
! │ │     └ sddk::inner|local                                              66.48 ms →  49.28 ms    (-25.88%)        1.02 K →    976       (-4.69%)
! │ ├ sirius::Smooth_periodic_function::gather_f_pw                        65.79 μs →  76.53 μs    (+16.32%)           4   →      4               
  │ ├ sirius::Periodic_function|inner                                       1.32 ms →   1.43 ms     (+8.23%)           9   →      9               
  │ │ └ sirius::Periodic_function|inner_local                               1.32 ms →   1.43 ms     (+8.23%)           9   →      9               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      1.32 ms →   1.43 ms     (+8.23%)           9   →      9               
  │ └ sirius::Smooth_periodic_function|inner                              952.09 μs →   1.00 ms     (+5.31%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      951.63 μs →   1.00 ms     (+5.28%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         1.33 ms →   1.43 ms     (+7.80%)           3   →      3               
  │ └ sirius::Periodic_function|inner_local                                 1.33 ms →   1.43 ms     (+7.81%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.33 ms →   1.43 ms     (+7.81%)           3   →      3               
  ├ sirius::Smooth_periodic_function|inner                                950.28 μs →   1.00 ms     (+5.31%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                        949.75 μs → 999.93 μs     (+5.28%)           1   →      1               
! └ sirius::finalize                                                      852.19 ms → 484.76 ms    (-43.12%)           1   →      1               
```
