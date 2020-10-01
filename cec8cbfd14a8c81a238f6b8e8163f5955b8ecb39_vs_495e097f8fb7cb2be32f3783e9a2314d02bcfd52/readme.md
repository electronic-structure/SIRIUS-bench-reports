# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 495e097f8fb7cb2be32f3783e9a2314d02bcfd52
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
! sirius                                                                  561.30 s  → 960.83 s     (+71.18%)           1   →      1               
  ├ sirius::initialize                                                      3.28 s  →   3.09 s      (-5.80%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                 13.86 s  →  13.89 s      (+0.19%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               254.69 μs → 266.01 μs     (+4.44%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       409.31 ms → 388.39 ms     (-5.11%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                           399.65 ms → 380.16 ms     (-4.88%)           1   →      1               
! │ │ └ sirius::Unit_cell::update                                           9.60 ms →   8.17 ms    (-14.88%)           1   →      1               
! │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      279.34 μs → 169.20 μs    (-39.43%)           1   →      1               
! │ │   └ sirius::Unit_cell::get_symmetry                                   9.29 ms →   7.96 ms    (-14.31%)           1   →      1               
! │ │     └ sirius::Unit_cell_symmetry                                      9.28 ms →   7.95 ms    (-14.33%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.74 ms →   4.80 ms     (+1.24%)           1   →      1               
! │ │       ├ sirius::Unit_cell_symmetry|equiv                             35.50 μs →  41.07 μs    (+15.68%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               12.90 μs →  13.88 μs     (+7.57%)           1   →      1               
  │ └ sirius::Simulation_context::update                                   13.41 s  →  13.44 s      (+0.23%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           4.90 ms →   4.96 ms     (+1.36%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       39.37 μs →  39.75 μs     (+0.96%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   4.84 ms →   4.90 ms     (+1.19%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      4.83 ms →   4.88 ms     (+1.10%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.73 ms →   4.78 ms     (+0.94%)           1   →      1               
! │   │     ├ sirius::Unit_cell_symmetry|equiv                             40.85 μs →  45.61 μs    (+11.66%)           1   →      1               
! │   │     └ sirius::Unit_cell_symmetry|mag                               12.46 μs →  14.14 μs    (+13.52%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                        3.07 s  →   3.10 s      (+0.70%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                          151.42 ms → 153.54 ms     (+1.40%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                               133.37 ms → 135.27 ms     (+1.42%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                     459.27 ms → 468.52 ms     (+2.01%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                     838.30 ms → 840.52 ms     (+0.27%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                               784.33 ms → 785.89 ms     (+0.20%)           4   →      4               
! │   ├ sddk::Gvec::init                                                    8.88 ms →   7.43 ms    (-16.32%)           2   →      2               
! │   │ └ sddk::Gvec::find_gvec_shells                                      6.12 ms →   4.70 ms    (-23.20%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   7.95 ms →   8.04 ms     (+1.24%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                723.30 μs → 765.64 μs     (+5.85%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 163.91 ms → 150.53 ms     (-8.16%)           1   →      1               
! ├ sirius::K_point_set::create_k_mesh                                     53.82 ms →  60.59 ms    (+12.58%)           1   →      1               
! │ ├ sirius::K_point::K_point                                              1.18 μs → 813.38 ns    (-30.89%)           8   →      8               
! │ └ sirius::K_point_set::initialize                                      53.70 ms →  60.50 ms    (+12.67%)           1   →      1               
! │   └ sirius::K_point::initialize                                         6.54 ms →   7.39 ms    (+12.84%)           8   →      8               
  │     ├ sirius::K_point::generate_gkvec                                   1.26 ms →   1.14 ms     (-9.13%)           8   →      8               
! │     │ └ sddk::Gvec::init                                              217.09 μs → 246.03 μs    (+13.33%)           8   →      8               
! │     ├ sddk::matrix_storage::matrix_storage                              2.49 μs →   2.83 μs    (+13.59%)          32   →     32               
! │     └ sirius::K_point::update                                           5.17 ms →   6.11 ms    (+18.30%)           8   →      8               
  │       ├ sirius::Beta_projectors                                       364.68 μs → 369.34 μs     (+1.28%)           8   →      8               
  │       │ └ sirius::Beta_projectors::generate_pw_coefs_t                253.38 μs → 260.99 μs     (+3.00%)           8   →      8               
! │       ├ sddk::matrix_storage::matrix_storage                            3.75 μs →   3.21 μs    (-14.57%)           8   →      8               
! │       ├ sirius::Non_local_operator                                     25.59 μs →  28.42 μs    (+11.07%)           8   →      8               
  │       ├ sirius::Q_operator::initialize                                 36.79 μs →  37.00 μs     (+0.59%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::prepare                           4.14 μs →   3.76 μs     (-9.17%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::generate                         42.37 μs →  38.32 μs     (-9.56%)           8   →      8               
  │       ├ sirius::Beta_projectors_base::inner                           129.10 μs → 123.42 μs     (-4.40%)           8   →      8               
! │       ├ sirius::Non_local_operator::apply                              80.49 μs →  69.24 μs    (-13.97%)           8   →      8               
! │       ├ sirius::Beta_projectors_base::dismiss                         545.38 ns → 625.88 ns    (+14.76%)           8   →      8               
  │       ├ sddk::inner                                                   121.00 μs → 117.31 μs     (-3.06%)           8   →      8               
! │       │ └ sddk::inner|local                                            25.20 μs →  22.41 μs    (-11.10%)           8   →      8               
! │       ├ Eigensolver_lapack|zheevd                                       3.67 ms →   4.60 ms    (+25.51%)           8   →      8               
  │       └ sddk::transform                                                58.93 μs →  64.30 μs     (+9.12%)           8   →      8               
! │         ├ sddk::transform|init                                          7.72 μs →   9.92 μs    (+28.41%)           8   →      8               
  │         └ sddk::transform|local                                        15.47 μs →  16.04 μs     (+3.66%)           8   →      8               
  ├ sirius::Smooth_periodic_function                                      447.00 μs → 451.86 μs     (+1.09%)           4   →      4               
  ├ sirius::Potential                                                       6.80 ms →   6.77 ms     (-0.38%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    473.72 μs → 482.53 μs     (+1.86%)           7   →      7               
  │ └ sirius::Potential::update                                             2.90 ms →   2.82 ms     (-2.50%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         2.86 ms →   2.79 ms     (-2.52%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                2.38 ms →   2.34 ms     (-1.70%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 398.29 μs → 366.54 μs     (-7.97%)           1   →      1               
  ├ sirius::Density                                                         3.73 ms →   3.56 ms     (-4.69%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    216.64 μs → 208.49 μs     (-3.76%)           3   →      3               
  │ └ sirius::Density::update                                               3.08 ms →   2.93 ms     (-4.94%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                3.04 ms →   2.89 ms     (-4.98%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                19.04 μs →  18.85 μs     (-0.97%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                2.70 ms →   2.57 ms     (-4.70%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 290.27 μs → 266.10 μs     (-8.33%)           1   →      1               
  ├ sirius::Density::initial_density                                      136.59 ms → 133.05 ms     (-2.59%)           1   →      1               
! │ ├ sirius::Simulation_context::make_periodic_function                    3.42 ms →   3.05 ms    (-10.93%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     255.05 μs → 248.58 μs     (-2.54%)           3   →      3               
  │ └ sirius::Periodic_function::integrate                                  1.07 ms →   1.14 ms     (+6.31%)           1   →      1               
  ├ sirius::Potential::generate                                           784.67 ms → 804.55 ms     (+2.53%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            4.14 ms →   3.94 ms     (-4.86%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                   372.97 μs → 293.94 μs    (-21.19%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     1.35 ms →   1.40 ms     (+3.84%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             1.34 ms →   1.40 ms     (+3.85%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    1.34 ms →   1.40 ms     (+3.84%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      135.44 μs → 125.01 μs     (-7.70%)           2   →      2               
  │ ├ sirius::Potential::xc                                                89.49 ms →  87.45 ms     (-2.28%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_magnetic                                  89.22 ms →  87.19 ms     (-2.27%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                272.79 μs → 273.40 μs     (+0.22%)          17   →     17               
  │ │   ├ sirius::Potential::xc_rg_magnetic|up_dn                         836.30 μs → 873.71 μs     (+4.47%)           1   →      1               
  │ │   ├ sirius::Potential::xc_rg_magnetic|grad1                           9.07 ms →   8.98 ms     (-0.93%)           1   →      1               
! │ │   │ ├ sirius::Smooth_periodic_function::fft_transform               285.20 μs → 245.01 μs    (-14.09%)           8   →      8               
  │ │   │ ├ sirius::gradient                                                1.70 ms →   1.72 ms     (+1.13%)           2   →      2               
  │ │   │ │ └ sirius::Smooth_periodic_function                            472.80 μs → 478.79 μs     (+1.27%)           6   →      6               
  │ │   │ └ sirius::dot                                                     1.13 ms →   1.19 ms     (+5.87%)           3   →      3               
  │ │   │   └ sirius::Smooth_periodic_function                            472.21 μs → 493.10 μs     (+4.42%)           3   →      3               
  │ │   ├ sirius::Potential::xc_rg_magnetic|libxc                          15.48 ms →  15.58 ms     (+0.61%)           2   →      2               
! │ │   ├ sirius::Smooth_periodic_function::fft_transform                 456.38 μs → 257.45 μs    (-43.59%)          16   →     16               
  │ │   └ sirius::divergence                                                3.67 ms →   3.67 ms     (-0.02%)           4   →      4               
  │ │     └ sirius::Smooth_periodic_function                              287.14 μs → 282.38 μs     (-1.66%)           4   →      4               
! │ ├ sirius::Smooth_periodic_function::fft_transform                     896.77 μs →   1.91 ms   (+112.67%)           2   →      2               
! │ ├ sirius::Potential::generate_D_operator_matrix                         4.62 ms →  11.71 ms   (+153.37%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 684.03 ms → 697.10 ms     (+1.91%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  930.11 μs → 980.91 μs     (+5.46%)           1   →      1               
  │ ├ sirius::Local_operator                                              776.87 μs → 840.72 μs     (+8.22%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   19.86 μs →  18.61 μs     (-6.29%)           2   →      2               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   235.05 μs → 254.47 μs     (+8.26%)           2   →      2               
  │ ├ sirius::Non_local_operator                                           32.23 μs →  29.80 μs     (-7.55%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       43.34 μs →  41.28 μs     (-4.76%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       34.68 μs →  31.91 μs     (-7.99%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      80.75 ms →  77.97 ms     (-3.45%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                25.80 μs →  26.86 μs     (+4.10%)           8   →      8               
  │ │ ├ sirius::Local_operator::prepare_k                                  21.89 μs →  22.21 μs     (+1.49%)           8   →      8               
  │ │ └ sirius::Beta_projectors_base::prepare                               2.51 μs →   2.41 μs     (-3.98%)           8   →      8               
  │ ├ sirius::Band::initialize_subspace|kp                                 10.06 ms →   9.72 ms     (-3.47%)           8   →      8               
  │ │ ├ sddk::matrix_storage::matrix_storage                                7.06 μs →   7.46 μs     (+5.53%)          32   →     32               
! │ │ ├ sirius::K_point::generate_atomic_wave_functions                   403.31 μs → 450.56 μs    (+11.71%)           8   →      8               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            66.23 μs →  66.11 μs     (-0.19%)           8   →      8               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    3.14 ms →   2.93 ms     (-6.66%)          16   →     16               
  │ │ │ ├ sirius::Local_operator::apply_h                                   2.56 ms →   2.36 ms     (-7.84%)          16   →     16               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             1.90 μs →   1.79 μs     (-5.73%)          16   →     16               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.33 μs →   1.30 μs     (-2.72%)          16   →     16               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           374.06 ns → 350.63 ns     (-6.27%)          16   →     16               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          347.44 ns → 351.87 ns     (+1.28%)          16   →     16               
  │ │ │ ├ sirius::Beta_projectors_base::generate                           43.35 μs →  39.65 μs     (-8.55%)          16   →     16               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             131.99 μs → 126.46 μs     (-4.19%)          16   →     16               
  │ │ │ ├ sirius::Non_local_operator::apply                                67.95 μs →  67.72 μs     (-0.33%)          32   →     32               
  │ │ │ ├ sddk::inner                                                     121.55 μs → 120.22 μs     (-1.09%)          16   →     16               
  │ │ │ │ └ sddk::inner|local                                              17.32 μs →  17.11 μs     (-1.22%)          16   →     16               
  │ │ │ └ sddk::transform                                                  58.24 μs →  63.10 μs     (+8.33%)          16   →     16               
  │ │ │   ├ sddk::transform|init                                            7.87 μs →   7.98 μs     (+1.35%)          16   →     16               
  │ │ │   └ sddk::transform|local                                           9.68 μs →   9.69 μs     (+0.14%)          16   →     16               
  │ │ ├ sirius::Band::set_subspace_mtrx                                   116.29 μs → 123.99 μs     (+6.63%)          32   →     32               
  │ │ │ └ sddk::inner                                                     113.45 μs → 120.97 μs     (+6.63%)          32   →     32               
  │ │ │   └ sddk::inner|local                                              15.36 μs →  14.89 μs     (-3.05%)          32   →     32               
  │ │ ├ Eigensolver_cuda|zhegvdx                                            1.18 ms →   1.18 ms     (-0.48%)          16   →     16               
  │ │ └ sddk::transform                                                    65.68 μs →  66.88 μs     (+1.82%)          16   →     16               
  │ │   ├ sddk::transform|init                                              7.88 μs →   8.09 μs     (+2.65%)          16   →     16               
  │ │   └ sddk::transform|local                                            10.25 μs →  10.94 μs     (+6.66%)          16   →     16               
  │ └ sirius::Beta_projectors_base::dismiss                               444.00 ns → 453.00 ns     (+2.03%)           8   →      8               
! ├ sirius::DFT_ground_state::scf_loop                                    541.61 s  → 942.62 s     (+74.04%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    434.11 μs → 437.57 μs     (+0.80%)          38   →     38               
  │ ├ sirius::Hubbard::compute_occupation_matrix                            6.45 s  →   6.43 s      (-0.29%)           1   →      1               
  │ │ └ sddk::inner                                                        62.42 ms →  56.44 ms     (-9.57%)          16   →     16               
  │ │   └ sddk::inner|local                                                62.42 ms →  56.44 ms     (-9.58%)          16   →     16               
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                          8.11 s  →  13.97 s     (+72.34%)          66   →     67       (+1.52%)
! │ │ ├ sirius::Hamiltonian0                                                3.90 ms →   4.63 ms    (+18.76%)          66   →     67       (+1.52%)
! │ │ │ ├ sirius::Local_operator                                            2.04 ms →   2.38 ms    (+16.48%)          66   →     67       (+1.52%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                               18.57 μs →  19.16 μs     (+3.15%)         132   →    134       (+1.52%)
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               212.72 μs → 213.13 μs     (+0.19%)         132   →    134       (+1.52%)
! │ │ │ ├ sirius::Non_local_operator                                      868.21 μs →   1.05 ms    (+21.16%)         132   →    134       (+1.52%)
! │ │ │ ├ sirius::D_operator::initialize                                   77.64 μs → 103.06 μs    (+32.74%)          66   →     67       (+1.52%)
  │ │ │ └ sirius::Q_operator::initialize                                   32.55 μs →  33.80 μs     (+3.85%)          66   →     67       (+1.52%)
! │ │ ├ sirius::Band::solve                                               666.65 ms →   2.83 s    (+324.40%)          66   →     67       (+1.52%)
! │ │ │ ├ sirius::Hamiltonian_k                                            36.08 μs →  52.52 μs    (+45.57%)         528   →    536       (+1.52%)
! │ │ │ │ ├ sirius::Local_operator::prepare_k                              32.90 μs →  48.85 μs    (+48.49%)         528   →    536       (+1.52%)
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                           2.35 μs →   2.67 μs    (+13.59%)         528   →    536       (+1.52%)
! │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     83.28 ms → 353.59 ms   (+324.59%)         528   →    536       (+1.52%)
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc              1.21 ms →   3.71 ms   (+207.78%)         528   →    536       (+1.52%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        970.17 ns → 923.72 ns     (-4.79%)        3.17 K →   3.22 K     (+1.52%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           916.68 μs →   1.00 ms     (+9.22%)         528   →    536       (+1.52%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        28.04 μs →  27.50 μs     (-1.90%)        1.06 K →   1.07 K     (+1.52%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       383.78 μs → 399.97 μs     (+4.22%)        1.06 K →   1.07 K     (+1.52%)
! │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              81.01 ms → 348.75 ms   (+330.47%)         528   →    536       (+1.52%)
! │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              6.59 ms →  30.00 ms   (+354.88%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ ├ sirius::Local_operator::apply_h                             5.49 ms →  25.46 ms   (+363.94%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.90 μs →   1.83 μs     (-3.63%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.53 μs →   1.53 μs     (-0.34%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     441.39 ns → 432.84 ns     (-1.94%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    406.41 ns → 433.22 ns     (+6.60%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                     49.44 μs →  46.97 μs     (-4.99%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       263.85 μs →   1.44 ms   (+444.57%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ ├ sirius::Non_local_operator::apply                          75.90 μs →  90.70 μs    (+19.49%)        7.96 K →   8.15 K     (+2.36%)
! │ │ │ │   │ ├ sddk::inner                                               301.44 μs →   1.36 ms   (+352.14%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │ │ └ sddk::inner|local                                        18.19 μs →  18.42 μs     (+1.28%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ └ sddk::transform                                           258.84 μs →   1.42 ms   (+447.57%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │   ├ sddk::transform|init                                      8.16 μs →   8.80 μs     (+7.81%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │   └ sddk::transform|local                                    10.31 μs →  10.66 μs     (+3.39%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   ├ sddk::orthogonalize                                         941.96 μs →   5.03 ms   (+434.38%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ ├ sddk::inner                                               280.87 μs →   1.43 ms   (+408.39%)        6.91 K →   7.08 K     (+2.49%)
  │ │ │ │   │ │ └ sddk::inner|local                                        16.64 μs →  17.33 μs     (+4.13%)        6.91 K →   7.08 K     (+2.49%)
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 248.40 μs →   1.38 ms   (+457.13%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ ├ sddk::orthogonalize|transform                              44.36 μs →  78.94 μs    (+77.96%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ └ sddk::transform                                           215.05 μs →   1.47 ms   (+585.57%)        2.92 K →   3.00 K     (+2.67%)
! │ │ │ │   │   ├ sddk::transform|init                                     16.28 μs →  18.83 μs    (+15.63%)        2.92 K →   3.00 K     (+2.67%)
! │ │ │ │   │   └ sddk::transform|local                                     7.16 μs →   8.21 μs    (+14.69%)        8.78 K →   9.01 K     (+2.67%)
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             331.85 μs →   1.51 ms   (+356.37%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   │ └ sddk::inner                                               315.30 μs →   1.47 ms   (+365.47%)        3.98 K →   4.08 K     (+2.36%)
  │ │ │ │   │   └ sddk::inner|local                                        16.88 μs →  17.40 μs     (+3.07%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   ├ Eigensolver_cuda|zheevdx                                      1.76 ms →   3.44 ms    (+94.82%)        3.98 K →   4.08 K     (+2.36%)
! │ │ │ │   ├ sirius::residuals                                           838.54 μs →   4.34 ms   (+417.37%)        3.98 K →   4.07 K     (+2.36%)
! │ │ │ │   │ ├ sddk::transform                                           272.42 μs →   1.48 ms   (+442.95%)        3.55 K →   3.64 K     (+2.59%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     12.46 μs →  12.80 μs     (+2.73%)        3.55 K →   3.64 K     (+2.59%)
  │ │ │ │   │ │ └ sddk::transform|local                                     9.74 μs →  10.06 μs     (+3.29%)        7.09 K →   7.28 K     (+2.59%)
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               607.50 μs →   3.31 ms   (+445.66%)        3.55 K →   3.64 K     (+2.59%)
! │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     404.71 μs →   2.44 ms   (+501.92%)        2.55 K →   2.58 K     (+0.90%)
! │ │ │ │     └ sddk::transform                                           244.18 μs →   1.53 ms   (+525.37%)        4.05 K →   4.08 K     (+0.74%)
  │ │ │ │       ├ sddk::transform|init                                      9.68 μs →   9.91 μs     (+2.38%)        4.05 K →   4.08 K     (+0.74%)
  │ │ │ │       └ sddk::transform|local                                     9.22 μs →   9.73 μs     (+5.53%)        5.54 K →   5.58 K     (+0.67%)
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           482.15 ns → 515.09 ns     (+6.83%)         528   →    536       (+1.52%)
! │ │ │ └ sirius::K_point_set::sync_band_energies                          18.54 μs →  21.78 μs    (+17.47%)          66   →     67       (+1.52%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                        532.64 μs → 501.25 μs     (-5.89%)          66   →     67       (+1.52%)
! │ │ ├ sirius::Density::generate                                         196.69 ms →   5.46 s   (+2677.53%)          66   →     67       (+1.52%)
! │ │ │ ├ sirius::Density::generate_valence                                26.69 ms →   5.29 s  (+19701.63%)          66   →     67       (+1.52%)
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                             1.70 μs →   2.09 μs    (+23.00%)        1.06 K →   1.07 K     (+1.52%)
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.45 μs →   1.85 μs    (+27.77%)        1.06 K →   1.07 K     (+1.52%)
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  408.49 μs →   4.26 ms   (+941.82%)         528   →    536       (+1.52%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         2.20 μs →   4.17 μs    (+89.56%)         528   →    536       (+1.52%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                       71.96 μs →  91.85 μs    (+27.64%)         528   →    536       (+1.52%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         149.62 μs →   2.02 ms  (+1250.07%)        1.06 K →   1.07 K     (+1.52%)
! │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       488.24 ns → 771.62 ns    (+58.04%)         528   →    536       (+1.52%)
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_om                              624.36 ms                                 536               
+ │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|1                             49.71 ms                                1.07 K             
+ │ │ │ │ │ │ └ sddk::inner                                                            49.71 ms                                1.07 K             
+ │ │ │ │ │ │   └ sddk::inner|local                                                    49.71 ms                                1.07 K             
+ │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|2                             60.52 μs                                1.07 K             
+ │ │ │ │ │ ├ sirius::Hubbard::compute_occupation_matrix|3                            262.33 ms                                1.07 K             
+ │ │ │ │ │ └ sirius::Hubbard::compute_occupation_matrix|4                             74.17 μs                                1.07 K             
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.03 ms →  27.02 ms  (+1230.11%)         528   →    536       (+1.52%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               140.55 μs →   1.84 ms  (+1208.89%)         132   →    134       (+1.52%)
! │ │ │ │ └ sirius::Density::augment                                        5.52 ms →   9.72 ms    (+76.16%)          66   →     67       (+1.52%)
! │ │ │ │   └ sirius::Density::generate_rho_aug                             5.31 ms →   9.50 ms    (+78.84%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::Field4D::symmetrize                                      24.86 ms →  24.78 ms     (-0.31%)          66   →     67       (+1.52%)
  │ │ │ │ ├ sirius::symmetrize_function|fpw                                12.69 ms →  12.41 ms     (-2.22%)          66   →     67       (+1.52%)
  │ │ │ │ │ ├ sddk::Gvec_shells::remap_forward                              2.17 ms →   2.18 ms     (+0.32%)          66   →     67       (+1.52%)
  │ │ │ │ │ ├ sirius::symmetrize_function|fpw|local                         8.34 ms →   8.04 ms     (-3.55%)          66   →     67       (+1.52%)
  │ │ │ │ │ └ sddk::Gvec_shells::remap_backward                             2.14 ms →   2.14 ms     (+0.33%)          66   →     67       (+1.52%)
  │ │ │ │ └ sirius::symmetrize_vector_function|vzpw                        12.16 ms →  12.37 ms     (+1.68%)          66   →     67       (+1.52%)
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              2.11 ms →   2.11 ms     (-0.14%)          66   →     67       (+1.52%)
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                             2.11 ms →   2.18 ms     (+3.32%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       21.56 ms →  21.18 ms     (-1.75%)          66   →     67       (+1.52%)
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 288.78 μs →   1.99 ms   (+589.51%)         132   →    134       (+1.52%)
  │ │ ├ sirius::Density::mix                                              109.57 ms → 117.41 ms     (+7.16%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::Density::mixer_input                                    540.96 μs → 578.53 μs     (+6.94%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::Periodic_function|inner                                   1.38 ms →   1.40 ms     (+1.53%)        1.87 K →   1.90 K     (+1.61%)
  │ │ │ │ └ sirius::Periodic_function|inner_local                           1.37 ms →   1.40 ms     (+1.60%)        1.87 K →   1.90 K     (+1.61%)
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  1.37 ms →   1.40 ms     (+1.61%)        1.87 K →   1.90 K     (+1.61%)
! │ │ │ └ sirius::Density::mixer_output                                     1.05 ms →   4.59 ms   (+335.94%)          66   →     67       (+1.52%)
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform               245.80 μs →   2.00 ms   (+712.67%)         132   →    134       (+1.52%)
  │ │ ├ sirius::Potential::generate                                       785.81 ms → 849.03 ms     (+8.04%)          66   →     67       (+1.52%)
! │ │ │ ├ sirius::Potential::poisson                                        4.01 ms →   5.58 ms    (+39.36%)          66   →     67       (+1.52%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               312.06 μs →   1.85 ms   (+491.38%)          66   →     67       (+1.52%)
  │ │ │ │ └ sirius::Periodic_function|inner                                 1.34 ms →   1.41 ms     (+5.18%)          66   →     67       (+1.52%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                         1.34 ms →   1.41 ms     (+5.28%)          66   →     67       (+1.52%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                1.34 ms →   1.41 ms     (+5.28%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::Periodic_function::add                                  124.06 μs → 135.51 μs     (+9.23%)         132   →    134       (+1.52%)
! │ │ │ ├ sirius::Potential::xc                                            87.67 ms → 128.07 ms    (+46.09%)          66   →     67       (+1.52%)
! │ │ │ │ └ sirius::Potential::xc_rg_magnetic                              87.41 ms → 127.85 ms    (+46.27%)          66   →     67       (+1.52%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                            227.67 μs → 220.83 μs     (-3.00%)        1.12 K →   1.14 K     (+1.52%)
! │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|up_dn                     837.31 μs → 999.60 μs    (+19.38%)          66   →     67       (+1.52%)
! │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|grad1                       8.19 ms →  22.47 ms   (+174.34%)          66   →     67       (+1.52%)
! │ │ │ │   │ ├ sirius::Smooth_periodic_function::fft_transform           254.29 μs →   2.01 ms   (+691.41%)         528   →    536       (+1.52%)
  │ │ │ │   │ ├ sirius::gradient                                            1.36 ms →   1.41 ms     (+3.86%)         132   →    134       (+1.52%)
  │ │ │ │   │ │ └ sirius::Smooth_periodic_function                        363.44 μs → 365.85 μs     (+0.66%)         396   →    402       (+1.52%)
  │ │ │ │   │ └ sirius::dot                                                 1.14 ms →   1.18 ms     (+3.22%)         198   →    201       (+1.52%)
  │ │ │ │   │   └ sirius::Smooth_periodic_function                        480.04 μs → 485.85 μs     (+1.21%)         198   →    201       (+1.52%)
  │ │ │ │   ├ sirius::Potential::xc_rg_magnetic|libxc                      15.83 ms →  16.15 ms     (+2.01%)         132   →    134       (+1.52%)
! │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform             346.46 μs →   1.89 ms   (+446.32%)        1.06 K →   1.07 K     (+1.52%)
  │ │ │ │   └ sirius::divergence                                            3.67 ms →   3.61 ms     (-1.49%)         264   →    268       (+1.52%)
  │ │ │ │     └ sirius::Smooth_periodic_function                          285.31 μs → 271.79 μs     (-4.74%)         264   →    268       (+1.52%)
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 356.36 μs →   2.01 ms   (+464.96%)         132   →    134       (+1.52%)
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     5.28 ms →  17.05 ms   (+223.03%)          66   →     67       (+1.52%)
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             687.60 ms → 693.72 ms     (+0.89%)          66   →     67       (+1.52%)
  │ │ ├ sirius::Field4D::symmetrize                                        24.75 ms →  24.22 ms     (-2.15%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::symmetrize_function|fpw                                  12.32 ms →  12.17 ms     (-1.24%)          66   →     67       (+1.52%)
  │ │ │ │ ├ sddk::Gvec_shells::remap_forward                                2.13 ms →   2.12 ms     (-0.66%)          66   →     67       (+1.52%)
  │ │ │ │ ├ sirius::symmetrize_function|fpw|local                           8.04 ms →   7.91 ms     (-1.59%)          66   →     67       (+1.52%)
  │ │ │ │ └ sddk::Gvec_shells::remap_backward                               2.10 ms →   2.10 ms     (-0.30%)          66   →     67       (+1.52%)
  │ │ │ └ sirius::symmetrize_vector_function|vzpw                          12.42 ms →  12.04 ms     (-3.04%)          66   →     67       (+1.52%)
  │ │ │   ├ sddk::Gvec_shells::remap_forward                                2.09 ms →   2.05 ms     (-1.96%)          66   →     67       (+1.52%)
  │ │ │   └ sddk::Gvec_shells::remap_backward                               2.14 ms →   2.10 ms     (-1.92%)          66   →     67       (+1.52%)
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                   358.84 μs →   1.68 ms   (+368.57%)         132   →    134       (+1.52%)
  │ │ ├ sirius::Periodic_function|inner                                     1.39 ms →   1.41 ms     (+0.89%)         726   →    737       (+1.52%)
  │ │ │ └ sirius::Periodic_function|inner_local                             1.39 ms →   1.41 ms     (+0.90%)         726   →    737       (+1.52%)
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    1.39 ms →   1.41 ms     (+0.90%)         726   →    737       (+1.52%)
  │ │ ├ sirius::Smooth_periodic_function|inner                              1.03 ms → 984.12 μs     (-4.18%)         198   →    201       (+1.52%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      1.03 ms → 983.43 μs     (-4.18%)         198   →    201       (+1.52%)
  │ │ ├ sirius::Periodic_function::integrate                                1.10 ms →   1.09 ms     (-1.12%)          66   →     67       (+1.52%)
  │ │ ├ sirius::Density::get_magnetisation                                  1.30 ms →   1.28 ms     (-1.46%)          66   →     67       (+1.52%)
  │ │ │ ├ sirius::Periodic_function::integrate                              1.10 ms →   1.09 ms     (-1.23%)          66   →     67       (+1.52%)
  │ │ │ └ sirius::Density::compute_atomic_mag_mom                         199.98 μs → 195.09 μs     (-2.44%)          66   →     67       (+1.52%)
! │ │ └ sirius::Hubbard::compute_occupation_matrix                          6.39 s  →   4.73 s     (-26.03%)          65   →     66       (+1.54%)
! │ │   └ sddk::inner                                                      60.63 ms →  48.20 ms    (-20.49%)        1.04 K →   1.06 K     (+1.54%)
! │ │     └ sddk::inner|local                                              60.62 ms →  48.20 ms    (-20.50%)        1.04 K →   1.06 K     (+1.54%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                        67.12 μs →  67.56 μs     (+0.65%)           4   →      4               
  │ ├ sirius::Periodic_function|inner                                       1.37 ms →   1.41 ms     (+3.13%)           9   →      9               
  │ │ └ sirius::Periodic_function|inner_local                               1.36 ms →   1.41 ms     (+3.08%)           9   →      9               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      1.36 ms →   1.41 ms     (+3.08%)           9   →      9               
  │ └ sirius::Smooth_periodic_function|inner                              986.76 μs → 980.10 μs     (-0.68%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      986.33 μs → 979.63 μs     (-0.68%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         1.33 ms →   1.37 ms     (+3.23%)           3   →      3               
  │ └ sirius::Periodic_function|inner_local                                 1.33 ms →   1.37 ms     (+3.23%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.33 ms →   1.37 ms     (+3.23%)           3   →      3               
  ├ sirius::Smooth_periodic_function|inner                                885.43 μs → 939.38 μs     (+6.09%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                        885.04 μs → 938.85 μs     (+6.08%)           1   →      1               
! └ sirius::finalize                                                        1.19 s  → 101.80 ms    (-91.46%)           1   →      1               
```
