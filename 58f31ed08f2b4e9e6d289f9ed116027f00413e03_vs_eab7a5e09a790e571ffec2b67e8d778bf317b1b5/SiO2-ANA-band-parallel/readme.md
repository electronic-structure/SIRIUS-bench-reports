# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                  241.25 s  → 277.02 s     (+14.83%)           1   →      1               
  ├ sirius::initialize                                                      2.72 s  →   2.70 s      (-0.81%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.00 s  →   2.90 s      (-3.51%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                64.10 ms →  34.48 ms    (-46.21%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       164.27 ms → 132.96 ms    (-19.06%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            70.36 ms →  54.22 ms    (-22.94%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          23.45 ms →  24.45 ms     (+4.23%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.29 ms →   6.35 ms     (+1.06%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  17.12 ms →  18.06 ms     (+5.44%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     17.10 ms →  18.04 ms     (+5.45%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.14 ms →   4.14 ms     (-0.04%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.35 ms →   2.33 ms     (-0.59%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              105.36 μs → 100.48 μs     (-4.63%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.73 s  →   2.68 s      (-1.78%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.88 ms →  10.71 ms     (-1.56%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.44 ms →   4.32 ms     (-2.52%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.41 ms →   6.36 ms     (-0.87%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.39 ms →   6.34 ms     (-0.87%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.91 ms →   3.85 ms     (-1.53%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.32 ms →   2.32 ms     (+0.20%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               99.43 μs →  99.98 μs     (+0.55%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       63.87 ms →  63.20 ms     (-1.05%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.15 ms →   5.24 ms     (+1.82%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.48 ms →   4.48 ms     (-0.01%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.77 ms →  22.28 ms     (+2.35%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.84 ms →  14.85 ms     (+0.10%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.91 ms →  19.86 ms     (-0.24%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  172.57 ms → 171.67 ms     (-0.52%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    129.95 ms → 129.18 ms     (-0.59%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 162.18 ms → 170.32 ms     (+5.02%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.32 ms →   1.32 ms     (-0.22%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 301.84 ms → 296.68 ms     (-1.71%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     75.52 ms →  76.56 ms     (+1.38%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              2.71 μs →   2.79 μs     (+2.95%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      75.41 ms →  76.46 ms     (+1.38%)           1   →      1               
  │   └ sirius::K_point::initialize                                        18.84 ms →  19.10 ms     (+1.39%)           4   →      4               
  │     ├ sirius::K_point::generate_gkvec                                  14.25 ms →  14.53 ms     (+1.91%)           4   →      4               
  │     │ └ sddk::Gvec::init                                                3.88 ms →   3.82 ms     (-1.58%)           4   →      4               
  │     ├ sddk::matrix_storage::matrix_storage                              9.47 μs →   8.89 μs     (-6.15%)           4   →      4               
  │     └ sirius::K_point::update                                           3.29 ms →   3.29 ms     (+0.24%)           4   →      4               
  │       └ sirius::Beta_projectors                                         1.77 ms →   1.80 ms     (+1.82%)           4   →      4               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                932.36 μs → 943.88 μs     (+1.24%)           4   →      4               
  ├ sirius::Smooth_periodic_function                                        5.27 ms →   5.47 ms     (+3.68%)           2   →      2               
  ├ sirius::Potential                                                     159.15 ms → 157.68 ms     (-0.92%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.83 ms →   6.12 ms     (+5.11%)           6   →      6               
  │ └ sirius::Potential::update                                           123.44 ms → 120.17 ms     (-2.65%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       122.68 ms → 119.45 ms     (-2.63%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              115.40 ms → 108.03 ms     (-6.39%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   6.36 ms →  10.50 ms    (+64.90%)           1   →      1               
  ├ sirius::Density                                                       137.14 ms → 130.34 ms     (-4.96%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.17 ms →   5.32 ms     (+2.76%)           2   →      2               
  │ └ sirius::Density::update                                             126.52 ms → 119.43 ms     (-5.60%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              126.08 ms → 119.01 ms     (-5.61%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               103.93 μs → 104.00 μs     (+0.07%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              120.50 ms → 110.64 ms     (-8.18%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   5.01 ms →   7.79 ms    (+55.38%)           1   →      1               
  ├ sirius::Density::initial_density                                      176.55 ms → 167.23 ms     (-5.28%)           1   →      1               
+ │ ├ sirius::Simulation_context::make_periodic_function                  123.85 ms → 109.75 ms    (-11.38%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       4.85 ms →   6.27 ms    (+29.24%)           2   →      2               
- │ └ sirius::Periodic_function::integrate                                  9.87 ms →  11.94 ms    (+20.95%)           1   →      1               
  ├ sirius::Potential::generate                                           593.72 ms → 587.99 ms     (-0.97%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          138.58 ms → 126.06 ms     (-9.04%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.18 ms →   7.66 ms    (+47.79%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.31 ms →  10.42 ms     (+1.12%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             9.88 ms →  10.30 ms     (+4.23%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    9.88 ms →  10.30 ms     (+4.23%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      544.63 μs → 571.65 μs     (+4.96%)           2   →      2               
  │ ├ sirius::Potential::xc                                                54.69 ms →  57.20 ms     (+4.58%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.30 ms →  54.81 ms     (+4.80%)           1   →      1               
- │ │   ├ sirius::Smooth_periodic_function                                  5.71 ms →   6.31 ms    (+10.40%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.44 ms →   5.15 ms     (-5.39%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.66 ms →   5.82 ms     (+2.83%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        92.63 ms →  92.63 ms     (+0.00%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 299.72 ms → 303.72 ms     (+1.34%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.40 ms →   8.39 ms     (-0.11%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.05 ms →   8.05 ms     (-0.02%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.76 ms →   4.77 ms     (+0.17%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.36 ms →   2.36 ms     (-0.30%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           62.95 μs →  62.81 μs     (-0.22%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       95.58 μs →  93.95 μs     (-1.70%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       75.21 μs →  69.70 μs     (-7.32%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       3.11 s  →   3.15 s      (+1.22%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                               372.63 μs → 380.20 μs     (+2.03%)           4   →      4               
  │ │ ├ sirius::Local_operator::prepare_k                                 367.87 μs → 375.43 μs     (+2.05%)           4   →      4               
  │ │ └ sirius::Beta_projectors_base::prepare                               3.03 μs →   3.06 μs     (+1.07%)           4   →      4               
  │ ├ sirius::Band::initialize_subspace|kp                                777.21 ms → 786.72 ms     (+1.22%)           4   →      4               
  │ │ ├ sddk::matrix_storage::matrix_storage                               33.08 ms →  32.97 ms     (-0.32%)          16   →     16               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    14.62 ms →  14.69 ms     (+0.50%)           4   →      4               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             5.30 ms →   5.58 ms     (+5.38%)           4   →      4               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  354.37 ms → 358.60 ms     (+1.19%)           4   →      4               
  │ │ │ ├ sirius::Local_operator::apply_h                                 257.73 ms → 261.28 ms     (+1.38%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                            62.98 ms →  64.64 ms     (+2.63%)           4   →      4               
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                          16.79 ms →  16.99 ms     (+1.24%)           4   →      4               
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                  16.78 ms →  16.99 ms     (+1.24%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                      39.68 ms →  41.26 ms     (+3.97%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                            16.63 ms →  16.77 ms     (+0.82%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                    16.63 ms →  16.76 ms     (+0.82%)           4   →      4               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                           54.04 ms →  55.86 ms     (+3.37%)           4   →      4               
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                     35.97 ms →  37.80 ms     (+5.08%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            1.95 ms →   1.95 ms     (-0.14%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::inner                              40.48 ms →  41.16 ms     (+1.68%)           4   →      4               
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                        7.31 ms →   7.97 ms     (+9.00%)           4   →      4               
  │ │ │ └ sirius::Non_local_operator::apply                                27.08 ms →  27.09 ms     (+0.02%)           8   →      8               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    15.19 ms →  15.52 ms     (+2.17%)           8   →      8               
  │ │ │ └ sddk::wf_inner                                                   15.14 ms →  15.47 ms     (+2.17%)           8   →      8               
- │ │ │   ├ sddk::wf_inner|scale                                           32.63 ns →  42.38 ns    (+29.89%)           8   →      8               
  │ │ │   ├ sddk::wf_inner|pw                                              14.95 ms →  15.28 ms     (+2.20%)           8   →      8               
  │ │ │   └ sddk::wf_inner|scale_back                                      23.87 ns →  22.13 ns     (-7.33%)           8   →      8               
  │ │ ├ Eigensolver_scalapack|pzhegvx                                     120.86 ms → 126.61 ms     (+4.76%)           4   →      4               
  │ │ └ sddk::wf_trans                                                     23.56 ms →  23.74 ms     (+0.77%)           4   →      4               
  │ │   └ sddk::wf_trans|pw                                                23.32 ms →  23.42 ms     (+0.43%)           4   →      4               
  │ └ sirius::Beta_projectors_base::dismiss                               453.25 ns → 461.50 ns     (+1.82%)           4   →      4               
- ├ sirius::DFT_ground_state::scf_loop                                    230.41 s  → 266.31 s     (+15.58%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.79 ms →   5.82 ms     (+0.61%)          19   →     19               
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                          8.85 s  →  10.23 s     (+15.60%)          26   →     26               
  │ │ ├ sirius::Hamiltonian0                                                4.52 ms →   4.64 ms     (+2.64%)          26   →     26               
  │ │ │ ├ sirius::Local_operator                                            4.16 ms →   4.29 ms     (+2.92%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              964.61 μs → 978.12 μs     (+1.40%)          26   →     26               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.31 ms →   2.42 ms     (+4.54%)          26   →     26               
  │ │ │ ├ sirius::Non_local_operator                                       64.80 μs →  64.69 μs     (-0.18%)          52   →     52               
  │ │ │ ├ sirius::D_operator::initialize                                   94.36 μs →  94.57 μs     (+0.22%)          26   →     26               
  │ │ │ └ sirius::Q_operator::initialize                                   66.62 μs →  66.02 μs     (-0.91%)          26   →     26               
- │ │ ├ sirius::Band::solve                                                 6.75 s  →   8.12 s     (+20.37%)          26   →     26               
  │ │ │ ├ sirius::Hamiltonian_k                                           334.01 μs → 348.68 μs     (+4.39%)         104   →    104               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             328.03 μs → 342.73 μs     (+4.48%)         104   →    104               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           4.36 μs →   4.09 μs     (-6.24%)         104   →    104               
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.69 s  →   2.03 s     (+20.37%)         104   →    104               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             11.83 ms →  11.94 ms     (+0.99%)         104   →    104               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        654.29 ns → 710.16 ns     (+8.54%)         624   →    624               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             1.83 ms →   1.83 ms     (+0.14%)         104   →    104               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       352.76 μs → 353.61 μs     (+0.24%)         104   →    104               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       549.25 μs → 549.62 μs     (+0.07%)         208   →    208               
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.66 s  →   2.01 s     (+20.64%)         104   →    104               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             69.17 ms →  70.66 ms     (+2.15%)         906   →    885       (-2.32%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            43.99 ms →  45.10 ms     (+2.50%)         906   →    885       (-2.32%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       8.36 ms →   8.83 ms     (+5.70%)         906   →    885       (-2.32%)
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                   237.66 μs → 244.71 μs     (+2.96%)         906   →    885       (-2.32%)
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc             2.05 ms →   2.06 ms     (+0.55%)         104   →    104               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 6.54 ms →   7.11 ms     (+8.62%)         906   →    885       (-2.32%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                      94.00 μs →  92.91 μs     (-1.16%)         906   →    885       (-2.32%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc             795.74 μs → 767.70 μs     (-3.52%)         104   →    104               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                      9.45 ms →  10.04 ms     (+6.22%)         906   →    885       (-2.32%)
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi                5.81 ms →   6.37 ms     (+9.67%)         906   →    885       (-2.32%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      1.52 ms →   1.52 ms     (+0.30%)         906   →    885       (-2.32%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         8.71 ms →   8.97 ms     (+3.08%)         906   →    885       (-2.32%)
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm                  1.32 ms →   1.54 ms    (+16.34%)         906   →    885       (-2.32%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           7.47 ms →   7.52 ms     (+0.74%)        1.81 K →   1.77 K     (-2.32%)
  │ │ │ │   ├ sddk::orthogonalize                                          28.02 ms →  28.44 ms     (+1.49%)         906   →    885       (-2.32%)
  │ │ │ │   │ ├ sddk::wf_inner                                              2.04 ms →   2.08 ms     (+2.12%)        1.71 K →   1.67 K     (-2.46%)
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                     76.82 ns →  54.22 ns    (-29.41%)        1.71 K →   1.67 K     (-2.46%)
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                         2.03 ms →   2.07 ms     (+1.80%)        1.71 K →   1.67 K     (-2.46%)
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                67.59 ns →  53.88 ns    (-20.28%)        1.71 K →   1.67 K     (-2.46%)
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                                 804.85 μs → 850.60 μs     (+5.69%)         906   →    885       (-2.32%)
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                                 782.68 μs → 819.01 μs     (+4.64%)         906   →    885       (-2.32%)
  │ │ │ │   │ └ sddk::wf_trans                                              5.40 ms →   5.47 ms     (+1.26%)        3.52 K →   3.44 K     (-2.39%)
  │ │ │ │   │   └ sddk::wf_trans|pw                                         3.67 ms →   3.72 ms     (+1.27%)        5.12 K →   5.00 K     (-2.46%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               5.46 ms →   5.69 ms     (+4.13%)         906   →    885       (-2.32%)
  │ │ │ │   │ └ sddk::wf_inner                                              3.74 ms →   3.98 ms     (+6.23%)         906   →    885       (-2.32%)
- │ │ │ │   │   ├ sddk::wf_inner|scale                                     44.24 ns →  69.95 ns    (+58.13%)         906   →    885       (-2.32%)
  │ │ │ │   │   ├ sddk::wf_inner|pw                                         3.73 ms →   3.95 ms     (+6.00%)         906   →    885       (-2.32%)
- │ │ │ │   │   └ sddk::wf_inner|scale_back                                66.83 ns → 103.74 ns    (+55.22%)         906   →    885       (-2.32%)
- │ │ │ │   ├ Eigensolver_scalapack|pzheevx                                65.54 ms → 105.71 ms    (+61.30%)         906   →    885       (-2.32%)
  │ │ │ │   ├ sirius::residuals                                            11.18 ms →  12.07 ms     (+7.93%)         886   →    866       (-2.26%)
  │ │ │ │   │ ├ sddk::wf_trans                                             10.83 ms →  11.77 ms     (+8.72%)         840   →    818       (-2.62%)
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                         5.37 ms →   5.83 ms     (+8.53%)        1.68 K →   1.64 K     (-2.62%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               657.83 μs → 683.77 μs     (+3.94%)         840   →    818       (-2.62%)
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      51.42 ms →  59.19 ms    (+15.12%)         209   →    203       (-2.87%)
- │ │ │ │     └ sddk::wf_trans                                             34.11 ms →  39.68 ms    (+16.31%)         314   →    302       (-3.82%)
- │ │ │ │       └ sddk::wf_trans|pw                                        25.42 ms →  29.69 ms    (+16.79%)         419   →    401       (-4.30%)
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           540.79 ns → 558.88 ns     (+3.35%)         104   →    104               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          21.97 μs →  20.82 μs     (-5.22%)          26   →     26               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        589.55 μs → 590.39 μs     (+0.14%)          26   →     26               
  │ │ ├ sirius::Density::generate                                         893.11 ms → 901.15 ms     (+0.90%)          26   →     26               
  │ │ │ ├ sirius::Density::generate_valence                               521.68 ms → 531.24 ms     (+1.83%)          26   →     26               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                            23.50 ms →  25.24 ms     (+7.44%)         104   →    104               
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           9.00 μs →   8.49 μs     (-5.72%)         104   →    104               
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                  15.48 μs →  15.27 μs     (-1.30%)           8   →      8               
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                      19.37 ms →  21.07 ms     (+8.76%)         104   →    104               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   29.85 ms →  30.52 ms     (+2.25%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         9.45 μs →   9.35 μs     (-1.11%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        1.45 ms →   1.45 ms     (+0.10%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          27.91 ms →  28.58 ms     (+2.40%)         104   →    104               
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    3.79 ms →   4.45 ms    (+17.37%)         104   →    104               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       572.16 ns → 609.16 ns     (+6.47%)         104   →    104               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                   42.88 ms →  42.60 ms     (-0.64%)         104   →    104               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.64 ms     (-0.14%)          26   →     26               
  │ │ │ │ └ sirius::Density::augment                                       88.83 ms →  88.96 ms     (+0.14%)          26   →     26               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.60 ms →  88.72 ms     (+0.13%)          26   →     26               
  │ │ │ ├ sirius::Field4D::symmetrize                                     279.21 ms → 277.49 ms     (-0.61%)          26   →     26               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               279.21 ms → 277.49 ms     (-0.62%)          26   →     26               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             24.76 ms →  24.21 ms     (-2.20%)          26   →     26               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       228.43 ms → 227.21 ms     (-0.53%)          26   →     26               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            24.26 ms →  24.35 ms     (+0.40%)          26   →     26               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       81.14 ms →  81.68 ms     (+0.66%)          26   →     26               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   7.49 ms →   7.16 ms     (-4.46%)          26   →     26               
  │ │ ├ sirius::Density::mix                                              218.45 ms → 218.58 ms     (+0.06%)          26   →     26               
  │ │ │ ├ sirius::Density::mixer_input                                    914.56 μs → 944.50 μs     (+3.27%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function|inner                                  10.75 ms →  10.69 ms     (-0.59%)         334   →    334               
  │ │ │ │ └ sirius::Periodic_function|inner_local                          10.39 ms →  10.46 ms     (+0.70%)         334   →    334               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 10.39 ms →  10.46 ms     (+0.70%)         334   →    334               
  │ │ │ └ sirius::Density::mixer_output                                     6.87 ms →   6.87 ms     (-0.01%)          26   →     26               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.06 ms →   6.02 ms     (-0.62%)          26   →     26               
  │ │ ├ sirius::Potential::generate                                       579.69 ms → 576.34 ms     (-0.58%)          26   →     26               
  │ │ │ ├ sirius::Potential::poisson                                      138.44 ms → 126.30 ms     (-8.77%)          26   →     26               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 5.07 ms →   8.10 ms    (+59.60%)          26   →     26               
  │ │ │ │ └ sirius::Periodic_function|inner                                10.25 ms →  10.44 ms     (+1.83%)          26   →     26               
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.09 ms →  10.18 ms     (+0.90%)          26   →     26               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.09 ms →  10.18 ms     (+0.89%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function::add                                  550.04 μs → 562.27 μs     (+2.22%)          52   →     52               
  │ │ │ ├ sirius::Potential::xc                                            48.95 ms →  49.83 ms     (+1.81%)          26   →     26               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           46.65 ms →  47.46 ms     (+1.73%)          26   →     26               
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.01 ms →   3.05 ms     (+1.48%)          52   →     52               
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.24 ms →   5.81 ms    (+10.83%)          26   →     26               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.51 ms →   6.75 ms     (+3.82%)          26   →     26               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.94 ms →  90.97 ms     (+0.04%)          26   →     26               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             292.48 ms → 300.02 ms     (+2.58%)          26   →     26               
  │ │ ├ sirius::Field4D::symmetrize                                       281.59 ms → 281.37 ms     (-0.08%)          26   →     26               
  │ │ │ └ sirius::symmetrize_function|fpw                                 281.59 ms → 281.36 ms     (-0.08%)          26   →     26               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.19 ms →  27.34 ms     (+0.54%)          26   →     26               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         226.70 ms → 226.24 ms     (-0.20%)          26   →     26               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.94 ms →  23.95 ms     (+0.07%)          26   →     26               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.55 ms →   5.71 ms     (+2.84%)          26   →     26               
  │ │ ├ sirius::Periodic_function|inner                                    10.31 ms →  10.31 ms     (+0.03%)         182   →    182               
  │ │ │ └ sirius::Periodic_function|inner_local                             9.86 ms →   9.91 ms     (+0.56%)         182   →    182               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.86 ms →   9.91 ms     (+0.56%)         182   →    182               
  │ │ ├ sirius::Smooth_periodic_function|inner                             11.01 ms →  11.09 ms     (+0.71%)          78   →     78               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.61 ms →  10.68 ms     (+0.69%)          78   →     78               
  │ │ ├ sirius::Periodic_function::integrate                               10.00 ms →  10.04 ms     (+0.40%)          26   →     26               
  │ │ └ sirius::Density::get_magnetisation                                112.57 μs → 117.40 μs     (+4.28%)          26   →     26               
  │ │   └ sirius::Density::compute_atomic_mag_mom                         107.40 μs → 112.29 μs     (+4.55%)          26   →     26               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.27 ms →   5.04 ms     (-4.28%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                      10.13 ms →  10.38 ms     (+2.49%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               9.65 ms →  10.32 ms     (+6.93%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      9.65 ms →  10.32 ms     (+6.92%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.90 ms →  10.79 ms     (-1.02%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.49 ms →  10.55 ms     (+0.62%)           3   →      3               
  ├ sirius::Periodic_function|inner                                        10.28 ms →  10.22 ms     (-0.58%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                10.28 ms →  10.01 ms     (-2.60%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.27 ms →  10.01 ms     (-2.60%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.99 ms →  10.89 ms     (-0.97%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.99 ms →  10.88 ms     (-0.96%)           1   →      1               
+ └ sirius::finalize                                                      337.81 ms → 281.19 ms    (-16.76%)           1   →      1               
```
