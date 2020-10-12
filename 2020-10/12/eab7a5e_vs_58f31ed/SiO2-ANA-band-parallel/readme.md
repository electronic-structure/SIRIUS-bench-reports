# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                  237.44 s  → 315.03 s     (+32.67%)           1   →      1               
  ├ sirius::initialize                                                      2.75 s  →   2.73 s      (-0.71%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  2.90 s  →   3.06 s      (+5.30%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                 8.05 ms →  34.15 ms   (+324.31%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       156.82 ms → 254.74 ms    (+62.44%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            67.01 ms → 115.21 ms    (+71.92%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          22.72 ms →  24.25 ms     (+6.74%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.38 ms →   6.22 ms     (-2.45%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  16.30 ms →  17.99 ms    (+10.34%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     16.28 ms →  17.97 ms    (+10.36%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.14 ms →   4.16 ms     (+0.60%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.33 ms →   2.32 ms     (-0.32%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              101.54 μs → 100.95 μs     (-0.58%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.68 s  →   2.71 s      (+1.10%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.81 ms →  10.85 ms     (+0.35%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.43 ms →   4.46 ms     (+0.67%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.35 ms →   6.35 ms     (+0.09%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.33 ms →   6.33 ms     (+0.10%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.83 ms →   3.85 ms     (+0.32%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.32 ms →   2.32 ms     (-0.31%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              100.64 μs → 100.90 μs     (+0.25%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       62.53 ms →  66.98 ms     (+7.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.15 ms →   5.20 ms     (+0.94%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.50 ms →   4.53 ms     (+0.68%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.88 ms →  22.07 ms     (+0.83%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.83 ms →  15.11 ms     (+1.93%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.80 ms →  19.85 ms     (+0.27%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  174.06 ms → 172.21 ms     (-1.06%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    130.94 ms → 129.46 ms     (-1.13%)           2   →      2               
- │   ├ sddk::Gvec_shells                                                 162.74 ms → 194.14 ms    (+19.30%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.31 ms →   1.32 ms     (+0.66%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 295.21 ms → 293.72 ms     (-0.50%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     75.37 ms →  76.06 ms     (+0.91%)           1   →      1               
- │ ├ sirius::K_point::K_point                                              2.41 μs →   3.10 μs    (+28.78%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      75.27 ms →  75.94 ms     (+0.90%)           1   →      1               
  │   └ sirius::K_point::initialize                                        18.80 ms →  18.97 ms     (+0.90%)           4   →      4               
  │     ├ sirius::K_point::generate_gkvec                                  14.22 ms →  14.32 ms     (+0.72%)           4   →      4               
  │     │ └ sddk::Gvec::init                                                3.93 ms →   3.99 ms     (+1.33%)           4   →      4               
  │     ├ sddk::matrix_storage::matrix_storage                              8.88 μs →   9.44 μs     (+6.21%)           4   →      4               
  │     └ sirius::K_point::update                                           3.28 ms →   3.32 ms     (+1.02%)           4   →      4               
  │       └ sirius::Beta_projectors                                         1.76 ms →   1.78 ms     (+1.27%)           4   →      4               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                933.98 μs → 925.59 μs     (-0.90%)           4   →      4               
  ├ sirius::Smooth_periodic_function                                        5.17 ms →   5.34 ms     (+3.40%)           2   →      2               
  ├ sirius::Potential                                                     155.60 ms → 159.63 ms     (+2.59%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.72 ms →   5.88 ms     (+2.82%)           6   →      6               
  │ └ sirius::Potential::update                                           120.57 ms → 123.63 ms     (+2.54%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       119.84 ms → 122.88 ms     (+2.54%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              111.73 ms → 111.66 ms     (-0.06%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   7.23 ms →  10.34 ms    (+43.11%)           1   →      1               
  ├ sirius::Density                                                       130.13 ms → 136.78 ms     (+5.11%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.08 ms →   5.30 ms     (+4.17%)           2   →      2               
  │ └ sirius::Density::update                                             119.67 ms → 125.91 ms     (+5.22%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              119.24 ms → 125.48 ms     (+5.23%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               102.98 μs → 103.92 μs     (+0.91%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              112.83 ms → 112.85 ms     (+0.02%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   5.87 ms →  12.07 ms   (+105.51%)           1   →      1               
  ├ sirius::Density::initial_density                                      166.80 ms → 176.34 ms     (+5.72%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  111.38 ms → 112.45 ms     (+0.96%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       5.51 ms →  10.94 ms    (+98.39%)           2   →      2               
+ │ └ sirius::Periodic_function::integrate                                 11.87 ms →   9.78 ms    (-17.64%)           1   →      1               
  ├ sirius::Potential::generate                                           581.88 ms → 594.61 ms     (+2.19%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          126.48 ms → 138.29 ms     (+9.34%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.86 ms →  18.05 ms   (+207.72%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.90 ms →  10.01 ms     (-8.19%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.20 ms →   9.81 ms     (-3.76%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.20 ms →   9.81 ms     (-3.77%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      560.77 μs → 555.52 μs     (-0.94%)           2   →      2               
  │ ├ sirius::Potential::xc                                                55.15 ms →  54.79 ms     (-0.65%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.86 ms →  52.46 ms     (-0.76%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.63 ms →   5.69 ms     (+1.05%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.93 ms →   5.44 ms     (-8.18%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.80 ms →   6.10 ms     (+5.10%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        92.59 ms →  92.74 ms     (+0.16%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 299.42 ms → 300.22 ms     (+0.27%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.46 ms →   9.23 ms     (+9.14%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.12 ms →   8.89 ms     (+9.51%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.73 ms →   4.82 ms     (+1.88%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.47 ms →   3.15 ms    (+27.50%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           63.39 μs →  62.31 μs     (-1.69%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       93.33 μs →  95.52 μs     (+2.35%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       68.47 μs →  68.99 μs     (+0.76%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       3.10 s  →   3.37 s      (+8.91%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                               368.13 μs → 380.09 μs     (+3.25%)           4   →      4               
  │ │ ├ sirius::Local_operator::prepare_k                                 363.31 μs → 374.97 μs     (+3.21%)           4   →      4               
  │ │ └ sirius::Beta_projectors_base::prepare                               3.17 μs →   3.33 μs     (+5.02%)           4   →      4               
  │ ├ sirius::Band::initialize_subspace|kp                                773.86 ms → 842.84 ms     (+8.91%)           4   →      4               
  │ │ ├ sddk::matrix_storage::matrix_storage                               33.33 ms →  34.72 ms     (+4.16%)          16   →     16               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    14.44 ms →  14.59 ms     (+1.06%)           4   →      4               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             5.32 ms →   5.43 ms     (+2.09%)           4   →      4               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  354.60 ms → 370.13 ms     (+4.38%)           4   →      4               
  │ │ │ ├ sirius::Local_operator::apply_h                                 258.26 ms → 267.26 ms     (+3.48%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                            63.05 ms →  68.44 ms     (+8.56%)           4   →      4               
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                          16.86 ms →  16.30 ms     (-3.30%)           4   →      4               
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                  16.85 ms →  16.30 ms     (-3.30%)           4   →      4               
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                      39.70 ms →  45.70 ms    (+15.13%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                            16.63 ms →  16.11 ms     (-3.11%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                    16.63 ms →  16.11 ms     (-3.11%)           4   →      4               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                           54.56 ms →  58.79 ms     (+7.75%)           4   →      4               
- │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                     36.53 ms →  40.79 ms    (+11.65%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            1.91 ms →   1.95 ms     (+1.70%)           4   →      4               
- │ │ │ ├ sirius::Beta_projectors_base::inner                              40.21 ms →  46.77 ms    (+16.33%)           4   →      4               
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                        7.04 ms →  13.62 ms    (+93.44%)           4   →      4               
  │ │ │ └ sirius::Non_local_operator::apply                                27.09 ms →  27.06 ms     (-0.12%)           8   →      8               
- │ │ ├ sirius::Band::set_subspace_mtrx                                    14.75 ms →  17.16 ms    (+16.34%)           8   →      8               
- │ │ │ └ sddk::wf_inner                                                   14.71 ms →  17.12 ms    (+16.38%)           8   →      8               
  │ │ │   ├ sddk::wf_inner|scale                                           28.88 ns →  26.75 ns     (-7.36%)           8   →      8               
- │ │ │   ├ sddk::wf_inner|pw                                              14.52 ms →  16.92 ms    (+16.51%)           8   →      8               
  │ │ │   └ sddk::wf_inner|scale_back                                      24.00 ns →  25.00 ns     (+4.17%)           8   →      8               
- │ │ ├ Eigensolver_scalapack|pzhegvx                                     118.97 ms → 159.45 ms    (+34.02%)           4   →      4               
  │ │ └ sddk::wf_trans                                                     23.50 ms →  24.27 ms     (+3.27%)           4   →      4               
  │ │   └ sddk::wf_trans|pw                                                23.36 ms →  23.89 ms     (+2.28%)           4   →      4               
  │ └ sirius::Beta_projectors_base::dismiss                               469.25 ns → 423.75 ns     (-9.70%)           4   →      4               
- ├ sirius::DFT_ground_state::scf_loop                                    226.71 s  → 303.89 s     (+34.04%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.69 ms →   5.81 ms     (+2.09%)          19   →     19               
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                          8.70 s  →  11.67 s     (+34.11%)          26   →     26               
- │ │ ├ sirius::Hamiltonian0                                                4.62 ms →   5.26 ms    (+13.62%)          26   →     26               
- │ │ │ ├ sirius::Local_operator                                            4.27 ms →   4.90 ms    (+14.78%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              994.33 μs → 954.67 μs     (-3.99%)          26   →     26               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.38 ms →   3.05 ms    (+28.12%)          26   →     26               
  │ │ │ ├ sirius::Non_local_operator                                       64.65 μs →  64.70 μs     (+0.07%)          52   →     52               
  │ │ │ ├ sirius::D_operator::initialize                                   94.85 μs →  93.74 μs     (-1.17%)          26   →     26               
  │ │ │ └ sirius::Q_operator::initialize                                   65.86 μs →  66.41 μs     (+0.83%)          26   →     26               
- │ │ ├ sirius::Band::solve                                                 6.61 s  →   9.54 s     (+44.43%)          26   →     26               
  │ │ │ ├ sirius::Hamiltonian_k                                           335.11 μs → 343.05 μs     (+2.37%)         104   →    104               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             329.35 μs → 337.05 μs     (+2.34%)         104   →    104               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           4.09 μs →   4.36 μs     (+6.59%)         104   →    104               
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.65 s  →   2.39 s     (+44.43%)         104   →    104               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             12.16 ms →  12.01 ms     (-1.27%)         104   →    104               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        670.55 ns → 700.69 ns     (+4.49%)         624   →    624               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             1.84 ms →   1.83 ms     (-0.50%)         104   →    104               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       353.87 μs → 352.67 μs     (-0.34%)         104   →    104               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       550.86 μs → 548.37 μs     (-0.45%)         208   →    208               
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.63 s  →   2.36 s     (+45.07%)         104   →    104               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             71.34 ms →  74.78 ms     (+4.82%)         881   →    868       (-1.48%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            45.71 ms →  47.92 ms     (+4.83%)         881   →    868       (-1.48%)
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       8.78 ms →   9.97 ms    (+13.53%)         881   →    868       (-1.48%)
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                   240.17 μs → 241.87 μs     (+0.71%)         881   →    868       (-1.48%)
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc             2.02 ms →   2.00 ms     (-0.78%)         104   →    104               
- │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 6.92 ms →   8.24 ms    (+19.05%)         881   →    868       (-1.48%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                      92.54 μs →  94.26 μs     (+1.86%)         881   →    868       (-1.48%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc             761.10 μs → 763.95 μs     (+0.37%)         104   →    104               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                     10.08 ms →  11.20 ms    (+11.11%)         881   →    868       (-1.48%)
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi                6.33 ms →   7.47 ms    (+17.95%)         881   →    868       (-1.48%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      1.49 ms →   1.53 ms     (+2.51%)         881   →    868       (-1.48%)
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         8.89 ms →  10.13 ms    (+13.97%)         881   →    868       (-1.48%)
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm                  1.30 ms →   2.60 ms    (+99.85%)         881   →    868       (-1.48%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           7.61 ms →   7.59 ms     (-0.30%)        1.76 K →   1.74 K     (-1.48%)
  │ │ │ │   ├ sddk::orthogonalize                                          28.66 ms →  31.52 ms     (+9.99%)         881   →    868       (-1.48%)
- │ │ │ │   │ ├ sddk::wf_inner                                              2.07 ms →   2.49 ms    (+20.27%)        1.66 K →   1.63 K     (-1.57%)
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                     71.72 ns →  69.38 ns     (-3.25%)        1.66 K →   1.63 K     (-1.57%)
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                         2.06 ms →   2.47 ms    (+19.67%)        1.66 K →   1.63 K     (-1.57%)
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                56.22 ns →  60.99 ns     (+8.49%)        1.66 K →   1.63 K     (-1.57%)
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                                 848.50 μs → 957.57 μs    (+12.85%)         881   →    868       (-1.48%)
- │ │ │ │   │ ├ sddk::orthogonalize|trtri                                 793.84 μs →   1.11 ms    (+39.46%)         881   →    868       (-1.48%)
  │ │ │ │   │ └ sddk::wf_trans                                              5.54 ms →   5.97 ms     (+7.77%)        3.42 K →   3.37 K     (-1.52%)
  │ │ │ │   │   └ sddk::wf_trans|pw                                         3.78 ms →   4.04 ms     (+6.71%)        4.97 K →   4.90 K     (-1.57%)
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               5.51 ms →   6.35 ms    (+15.26%)         881   →    868       (-1.48%)
- │ │ │ │   │ └ sddk::wf_inner                                              3.82 ms →   4.72 ms    (+23.45%)         881   →    868       (-1.48%)
- │ │ │ │   │   ├ sddk::wf_inner|scale                                     51.32 ns →  66.80 ns    (+30.17%)         881   →    868       (-1.48%)
- │ │ │ │   │   ├ sddk::wf_inner|pw                                         3.81 ms →   4.68 ms    (+22.90%)         881   →    868       (-1.48%)
- │ │ │ │   │   └ sddk::wf_inner|scale_back                                65.70 ns →  75.33 ns    (+14.67%)         881   →    868       (-1.48%)
- │ │ │ │   ├ Eigensolver_scalapack|pzheevx                                63.67 ms → 143.41 ms   (+125.22%)         881   →    868       (-1.48%)
- │ │ │ │   ├ sirius::residuals                                            11.05 ms →  13.04 ms    (+17.97%)         863   →    852       (-1.27%)
- │ │ │ │   │ ├ sddk::wf_trans                                             10.73 ms →  12.79 ms    (+19.24%)         816   →    804       (-1.47%)
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                         5.33 ms →   6.28 ms    (+17.74%)        1.63 K →   1.61 K     (-1.47%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               651.74 μs → 697.00 μs     (+6.94%)         816   →    804       (-1.47%)
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      51.32 ms →  60.44 ms    (+17.77%)         209   →    203       (-2.87%)
- │ │ │ │     └ sddk::wf_trans                                             34.05 ms →  40.52 ms    (+19.00%)         314   →    302       (-3.82%)
- │ │ │ │       └ sddk::wf_trans|pw                                        25.39 ms →  30.26 ms    (+19.18%)         419   →    401       (-4.30%)
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           573.87 ns → 521.92 ns     (-9.05%)         104   →    104               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.12 μs →  20.70 μs     (+2.88%)          26   →     26               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        593.37 μs → 584.21 μs     (-1.54%)          26   →     26               
  │ │ ├ sirius::Density::generate                                         897.03 ms → 923.41 ms     (+2.94%)          26   →     26               
  │ │ │ ├ sirius::Density::generate_valence                               523.75 ms → 557.05 ms     (+6.36%)          26   →     26               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                            24.13 ms →  27.74 ms    (+14.98%)         104   →    104               
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           8.37 μs →   8.69 μs     (+3.82%)         104   →    104               
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                  15.39 μs →  15.15 μs     (-1.58%)           8   →      8               
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                      20.01 ms →  23.62 ms    (+18.04%)         104   →    104               
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   29.64 ms →  33.88 ms    (+14.31%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         9.47 μs →   9.43 μs     (-0.49%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        1.41 ms →   1.46 ms     (+3.01%)         104   →    104               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          27.74 ms →  31.94 ms    (+15.12%)         104   →    104               
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    3.61 ms →   7.81 ms   (+116.35%)         104   →    104               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       618.35 ns → 592.77 ns     (-4.14%)         104   →    104               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                   42.82 ms →  42.51 ms     (-0.72%)         104   →    104               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.65 ms     (+0.56%)          26   →     26               
  │ │ │ │ └ sirius::Density::augment                                       88.91 ms →  88.83 ms     (-0.09%)          26   →     26               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.68 ms →  88.60 ms     (-0.09%)          26   →     26               
  │ │ │ ├ sirius::Field4D::symmetrize                                     281.20 ms → 274.57 ms     (-2.36%)          26   →     26               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               281.20 ms → 274.57 ms     (-2.36%)          26   →     26               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             24.26 ms →  24.87 ms     (+2.52%)          26   →     26               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       230.92 ms → 223.35 ms     (-3.28%)          26   →     26               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            24.22 ms →  24.66 ms     (+1.81%)          26   →     26               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       81.10 ms →  81.38 ms     (+0.35%)          26   →     26               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   7.40 ms →   6.82 ms     (-7.85%)          26   →     26               
  │ │ ├ sirius::Density::mix                                              218.86 ms → 218.58 ms     (-0.13%)          26   →     26               
  │ │ │ ├ sirius::Density::mixer_input                                    928.15 μs → 955.74 μs     (+2.97%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function|inner                                  10.75 ms →  10.74 ms     (-0.12%)         334   →    334               
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.37 ms →  10.36 ms     (-0.08%)         334   →    334               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.37 ms →  10.36 ms     (-0.08%)         334   →    334               
  │ │ │ └ sirius::Density::mixer_output                                     6.74 ms →   6.77 ms     (+0.48%)          26   →     26               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.93 ms →   5.95 ms     (+0.25%)          26   →     26               
  │ │ ├ sirius::Potential::generate                                       568.44 ms → 581.00 ms     (+2.21%)          26   →     26               
  │ │ │ ├ sirius::Potential::poisson                                      126.52 ms → 138.22 ms     (+9.25%)          26   →     26               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 5.88 ms →  17.63 ms   (+199.53%)          26   →     26               
  │ │ │ │ └ sirius::Periodic_function|inner                                10.44 ms →  10.25 ms     (-1.85%)          26   →     26               
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.10 ms →   9.93 ms     (-1.70%)          26   →     26               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.10 ms →   9.93 ms     (-1.70%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function::add                                  545.84 μs → 550.04 μs     (+0.77%)          52   →     52               
  │ │ │ ├ sirius::Potential::xc                                            49.06 ms →  49.19 ms     (+0.26%)          26   →     26               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           46.70 ms →  46.88 ms     (+0.39%)          26   →     26               
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.05 ms →   3.01 ms     (-1.50%)          52   →     52               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.21 ms →   5.63 ms     (+7.91%)          26   →     26               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.75 ms →   6.90 ms     (+2.21%)          26   →     26               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.85 ms →  91.19 ms     (+0.37%)          26   →     26               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.87 ms → 293.12 ms     (+0.08%)          26   →     26               
  │ │ ├ sirius::Field4D::symmetrize                                       284.87 ms → 279.71 ms     (-1.81%)          26   →     26               
  │ │ │ └ sirius::symmetrize_function|fpw                                 284.87 ms → 279.71 ms     (-1.81%)          26   →     26               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.28 ms →  27.55 ms     (+1.01%)          26   →     26               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         229.95 ms → 223.72 ms     (-2.71%)          26   →     26               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.85 ms →  24.66 ms     (+3.42%)          26   →     26               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.66 ms →   5.69 ms     (+0.53%)          26   →     26               
  │ │ ├ sirius::Periodic_function|inner                                    10.48 ms →  10.40 ms     (-0.75%)         182   →    182               
  │ │ │ └ sirius::Periodic_function|inner_local                             9.82 ms →   9.89 ms     (+0.76%)         182   →    182               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.82 ms →   9.89 ms     (+0.76%)         182   →    182               
  │ │ ├ sirius::Smooth_periodic_function|inner                             11.07 ms →  11.16 ms     (+0.80%)          78   →     78               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.61 ms →  10.72 ms     (+1.02%)          78   →     78               
  │ │ ├ sirius::Periodic_function::integrate                               10.04 ms →  10.09 ms     (+0.49%)          26   →     26               
- │ │ └ sirius::Density::get_magnetisation                                111.08 μs → 144.12 μs    (+29.75%)          26   →     26               
- │ │   └ sirius::Density::compute_atomic_mag_mom                         105.96 μs → 138.24 μs    (+30.46%)          26   →     26               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.07 ms →   5.32 ms     (+4.96%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       9.80 ms →  10.20 ms     (+4.05%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               9.66 ms →  10.10 ms     (+4.53%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      9.66 ms →  10.10 ms     (+4.53%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.61 ms →  10.88 ms     (+2.53%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.48 ms →  10.51 ms     (+0.23%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         9.76 ms →  10.44 ms     (+6.94%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 9.67 ms →  10.02 ms     (+3.62%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        9.67 ms →  10.02 ms     (+3.62%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.59 ms →  10.94 ms     (+3.33%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.47 ms →  10.93 ms     (+4.40%)           1   →      1               
  └ sirius::finalize                                                      332.56 ms → 309.86 ms     (-6.83%)           1   →      1               
```
