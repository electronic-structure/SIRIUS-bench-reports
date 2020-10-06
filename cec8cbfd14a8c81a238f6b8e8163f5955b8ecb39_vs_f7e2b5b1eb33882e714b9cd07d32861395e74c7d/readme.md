# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs f7e2b5b1eb33882e714b9cd07d32861395e74c7d
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    7.77 s  →   7.70 s      (-0.98%)           1   →      1               
  ├ sirius::initialize                                                      2.94 s  →   2.90 s      (-1.37%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  1.96 s  →   1.92 s      (-2.18%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                               476.18 μs → 231.71 μs    (-51.34%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       297.81 ms → 256.13 ms    (-13.99%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            94.46 ms →  80.09 ms    (-15.21%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          14.41 ms →  15.85 ms     (+9.93%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      248.91 μs → 241.79 μs     (-2.86%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  14.16 ms →  15.60 ms    (+10.16%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     14.13 ms →  15.57 ms    (+10.18%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.95 ms →   4.94 ms     (-0.29%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                             60.80 μs →  66.50 μs     (+9.38%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               16.01 μs →  16.57 μs     (+3.53%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (-0.07%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.12 ms →   5.14 ms     (+0.26%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       36.86 μs →  35.20 μs     (-4.50%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.09 ms →   5.10 ms     (+0.29%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.07 ms →   5.08 ms     (+0.29%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.97 ms →   4.97 ms     (-0.01%)           1   →      1               
- │   │     ├ sirius::Unit_cell_symmetry|equiv                             39.10 μs →  49.57 μs    (+26.77%)           1   →      1               
- │   │     └ sirius::Unit_cell_symmetry|mag                               15.98 μs →  18.82 μs    (+17.75%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      272.88 ms → 273.87 ms     (+0.36%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.37 ms →  21.36 ms     (-0.03%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.00 ms →  19.14 ms     (+0.73%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.31 ms →  80.37 ms     (+0.08%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.55 ms →  61.54 ms     (-0.03%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.87 ms →  96.58 ms     (-0.30%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.30 ms →   4.26 ms     (-1.05%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      3.01 ms →   2.97 ms     (-1.43%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.20 ms →   3.99 ms     (-4.89%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                285.75 μs → 301.50 μs     (+5.51%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  94.52 ms →  93.38 ms     (-1.20%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.85 ms →   5.88 ms     (+0.56%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            719.25 ns → 701.25 ns     (-2.50%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.77 ms →   5.79 ms     (+0.24%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.53 ms →   5.54 ms     (+0.17%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.51 ms →   4.52 ms     (+0.12%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              244.68 μs → 244.59 μs     (-0.03%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              2.89 μs →   2.97 μs     (+2.94%)           1   →      1               
  │     └ sirius::K_point::update                                         797.70 μs → 802.04 μs     (+0.54%)           1   →      1               
  │       └ sirius::Beta_projectors                                       654.38 μs → 658.37 μs     (+0.61%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                401.04 μs → 407.05 μs     (+1.50%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      249.65 μs → 247.19 μs     (-0.98%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       27.86 μs →  28.32 μs     (+1.66%)           2   →      2               
  ├ sirius::Potential                                                       2.04 ms →   2.09 ms     (+2.35%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.26 μs →  27.64 μs     (-2.18%)           6   →      6               
  │ └ sirius::Potential::update                                             1.77 ms →   1.83 ms     (+3.08%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.76 ms →   1.82 ms     (+3.13%)           1   →      1               
- │     ├ sirius::Simulation_context::make_periodic_function                1.19 ms →   1.33 ms    (+11.87%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 478.28 μs → 397.67 μs    (-16.85%)           1   →      1               
  ├ sirius::Density                                                         1.89 ms →   1.83 ms     (-3.23%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.57 μs →  28.70 μs     (+0.48%)           2   →      2               
  │ └ sirius::Density::update                                               1.83 ms →   1.77 ms     (-3.34%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.82 ms →   1.75 ms     (-3.37%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                20.24 μs →  19.69 μs     (-2.75%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.20 ms →   1.32 ms     (+9.88%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 583.62 μs → 404.35 μs    (-30.72%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.88 ms →   2.96 ms     (+2.95%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    1.24 ms →   1.16 ms     (-6.53%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     324.73 μs → 398.54 μs    (+22.73%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                256.73 μs → 264.55 μs     (+3.05%)           1   →      1               
  ├ sirius::Potential::generate                                            21.01 ms →  21.06 ms     (+0.24%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            2.01 ms →   1.99 ms     (-0.94%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   600.63 μs → 446.92 μs    (-25.59%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   267.83 μs → 256.97 μs     (-4.06%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           260.67 μs → 249.97 μs     (-4.10%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.38 μs → 249.57 μs     (-4.15%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.81 μs →  10.54 μs     (-2.55%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.04 ms →   2.05 ms     (+0.56%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.00 ms →   2.01 ms     (+0.51%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.11 μs →  28.28 μs     (-2.86%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 193.74 μs → 203.87 μs     (+5.23%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     159.54 μs → 160.89 μs     (+0.84%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        16.75 ms →  16.80 ms     (+0.32%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 287.00 ns → 203.00 ns    (-29.27%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  396.08 μs → 372.61 μs     (-5.93%)           1   →      1               
  │ ├ sirius::Local_operator                                              370.86 μs → 347.63 μs     (-6.26%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function                                   26.20 μs →  29.69 μs    (+13.30%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   324.72 μs → 297.79 μs     (-8.29%)           1   →      1               
+ │ ├ sirius::Non_local_operator                                            1.02 μs → 825.00 ns    (-19.32%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                        7.39 μs →   6.92 μs     (-6.39%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                        5.74 μs →   5.24 μs     (-8.73%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      48.70 ms →  49.52 ms     (+1.67%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                14.99 μs →  19.75 μs    (+31.76%)           1   →      1               
- │ │ └ sirius::Local_operator::prepare_k                                  13.70 μs →  18.50 μs    (+35.07%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 48.68 ms →  49.49 ms     (+1.66%)           1   →      1               
- │   ├ sddk::matrix_storage::matrix_storage                                5.04 μs →   5.59 μs    (+11.03%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   937.33 μs → 929.22 μs     (-0.86%)           1   →      1               
  │   ├ sirius::Band::initialize_subspace|kp|wf                            45.50 μs →  44.64 μs     (-1.89%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   17.61 ms →  18.09 ms     (+2.71%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.45 ms →   8.52 ms     (+0.86%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::remap_forward                             2.12 μs →   2.11 μs     (-0.38%)           1   →      1               
- │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.19 μs →   1.38 μs    (+15.64%)           1   →      1               
+ │   │ │ ├ sddk::matrix_storage::set_num_extra                           404.00 ns → 347.00 ns    (-14.11%)           1   →      1               
- │   │ │ └ sddk::matrix_storage::remap_backward                          576.00 ns → 761.00 ns    (+32.12%)           1   →      1               
  │   │ ├ sirius::Beta_projectors_base::inner                               4.97 ms →   4.93 ms     (-0.80%)           1   →      1               
- │   │ └ sirius::Non_local_operator::apply                                 1.90 ms →   2.12 ms    (+11.75%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   290.68 μs → 284.93 μs     (-1.98%)           2   →      2               
  │   │ ├ sddk::inner                                                     284.05 μs                                    2                          
  │   │ │ └ sddk::inner|local                                             276.84 μs                                    2                          
  │   │ └ sddk::wf_inner                                                              276.22 μs                                   2               
  │   │   ├ sddk::wf_inner|scale                                                       22.50 ns                                   2               
  │   │   ├ sddk::wf_inner|pw                                                         271.29 μs                                   2               
  │   │   └ sddk::wf_inner|scale_back                                                  29.50 ns                                   2               
  │   ├ Eigensolver_lapack|zhegvx                                          29.04 ms →  29.34 ms     (+1.04%)           1   →      1               
  │   ├ sddk::transform                                                   310.34 μs                                    1                          
  │   │ ├ sddk::transform|init                                             66.16 μs                                    1                          
  │   │ └ sddk::transform|local                                           232.46 μs                                    1                          
  │   └ sddk::wf_trans                                                                284.21 μs                                   1               
  │     └ sddk::wf_trans|pw                                                           276.43 μs                                   1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.24 s  →   2.25 s      (+0.37%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     66.08 μs →  68.92 μs     (+4.29%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        101.50 ms → 101.63 ms     (+0.12%)          22   →     22               
  │ │ ├ sirius::Hamiltonian0                                              342.30 μs → 364.81 μs     (+6.58%)          22   →     22               
  │ │ │ ├ sirius::Local_operator                                          319.37 μs → 343.72 μs     (+7.62%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               31.93 μs →  31.82 μs     (-0.35%)          22   →     22               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               269.80 μs → 295.75 μs     (+9.62%)          22   →     22               
  │ │ │ ├ sirius::Non_local_operator                                      918.95 ns → 856.16 ns     (-6.83%)          44   →     44               
+ │ │ │ ├ sirius::D_operator::initialize                                    8.44 μs →   7.51 μs    (-11.00%)          22   →     22               
+ │ │ │ └ sirius::Q_operator::initialize                                    6.48 μs →   5.66 μs    (-12.72%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.54 ms →  37.26 ms     (-0.74%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            19.42 μs →  18.70 μs     (-3.74%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              18.40 μs →  17.52 μs     (-4.79%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.45 ms →  33.12 ms     (-0.99%)          22   →     22               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             12.27 μs →  40.48 μs   (+229.91%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        878.69 ns → 944.85 ns     (+7.53%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           703.95 μs → 701.43 μs     (-0.36%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        11.20 μs →  10.95 μs     (-2.23%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       219.14 μs → 217.96 μs     (-0.54%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.72 ms →  32.36 ms     (-1.12%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.15 ms →   5.15 ms     (+0.09%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.26 ms →   4.27 ms     (+0.25%)          87   →     87               
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.08 μs →   2.30 μs    (+10.24%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.80 μs →   1.85 μs     (+2.81%)          87   →     87               
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     494.00 ns → 550.16 ns    (+11.37%)          87   →     87               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    416.18 ns → 596.22 ns    (+43.26%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       288.27 μs → 286.29 μs     (-0.69%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         273.39 μs → 271.42 μs     (-0.72%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         890.74 μs → 832.60 μs     (-6.53%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               143.19 μs                                  152                          
  │ │ │ │   │ │ └ sddk::inner|local                                       141.57 μs                                  152                          
  │ │ │ │   │ ├ sddk::wf_inner                                                        141.93 μs                                 152               
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                                104.70 ns                                 152               
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                                   139.59 μs                                 152               
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                            90.97 ns                                 152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.82 μs →  32.46 μs     (-1.08%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             248.33 μs → 248.62 μs     (+0.12%)          87   →     87               
  │ │ │ │   │ ├ sddk::transform                                           471.10 μs                                   65                          
  │ │ │ │   │ │ ├ sddk::transform|init                                     77.56 μs                                   65                          
  │ │ │ │   │ │ └ sddk::transform|local                                   130.51 μs                                  195                          
  │ │ │ │   │ └ sddk::wf_trans                                                        395.65 μs                                  65               
  │ │ │ │   │   └ sddk::wf_trans|pw                                                   131.17 μs                                 195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             211.13 μs → 209.93 μs     (-0.57%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               195.87 μs                                   87                          
  │ │ │ │   │ │ └ sddk::inner|local                                       194.77 μs                                   87                          
  │ │ │ │   │ └ sddk::wf_inner                                                        194.85 μs                                  87               
  │ │ │ │   │   ├ sddk::wf_inner|scale                                                169.95 ns                                  87               
  │ │ │ │   │   ├ sddk::wf_inner|pw                                                   193.29 μs                                  87               
  │ │ │ │   │   └ sddk::wf_inner|scale_back                                            22.68 ns                                  87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   996.13 μs → 997.50 μs     (+0.14%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           572.83 μs → 558.81 μs     (-2.45%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           418.27 μs                                   68                          
  │ │ │ │   │ │ ├ sddk::transform|init                                     66.84 μs                                   68                          
  │ │ │ │   │ │ └ sddk::transform|local                                   174.72 μs                                  136                          
  │ │ │ │   │ ├ sddk::wf_trans                                                        384.16 μs                                  68               
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                                   190.89 μs                                 136               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               296.06 μs → 293.38 μs     (-0.91%)          68   →     68               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     880.53 μs → 822.44 μs     (-6.60%)          38   →     38               
  │ │ │ │     ├ sddk::transform                                           530.79 μs                                   54                          
  │ │ │ │     │ ├ sddk::transform|init                                     74.38 μs                                   54                          
  │ │ │ │     │ └ sddk::transform|local                                   350.76 μs                                   70                          
  │ │ │ │     └ sddk::wf_trans                                                        491.64 μs                                  54               
  │ │ │ │       └ sddk::wf_trans|pw                                                   377.67 μs                                  70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.21 μs →  21.18 μs     (+4.81%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        205.65 μs → 202.41 μs     (-1.58%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          36.97 ms →  37.38 ms     (+1.13%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                27.37 ms →  28.21 ms     (+3.07%)          22   →     22               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.60 μs →   2.48 μs     (-4.40%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.31 μs →   2.16 μs     (-6.55%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  415.71 μs → 412.11 μs     (-0.87%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         390.22 μs → 386.84 μs     (-0.87%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.82 ms →   2.84 ms     (+0.82%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               140.19 μs → 140.86 μs     (+0.47%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       23.38 ms →  24.06 ms     (+2.91%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            23.37 ms →  24.04 ms     (+2.90%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      3.63 ms →   3.74 ms     (+3.13%)          66   →     66               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       2.92 ms →   3.00 ms     (+2.61%)          66   →     66               
  │ │ │ ├ sirius::Field4D::symmetrize                                       5.57 ms →   5.12 ms     (-8.07%)          22   →     22               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 5.56 ms →   5.12 ms     (-8.07%)          22   →     22               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              2.25 ms →   1.76 ms    (-21.85%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.35 ms →   2.37 ms     (+0.94%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           945.32 μs → 964.09 μs     (+1.99%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.69 ms →   3.72 ms     (+0.70%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 332.56 μs → 332.02 μs     (-0.16%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                4.99 ms →   5.01 ms     (+0.31%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     22.65 μs →  23.27 μs     (+2.76%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 257.15 μs → 254.61 μs     (-0.99%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         251.30 μs → 250.13 μs     (-0.46%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                251.10 μs → 249.99 μs     (-0.44%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   192.42 μs → 188.84 μs     (-1.86%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               180.20 μs → 177.45 μs     (-1.53%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.38 ms →  14.31 ms     (-0.53%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        2.03 ms →   1.99 ms     (-1.67%)          22   →     22               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               595.86 μs → 424.97 μs    (-28.68%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               267.69 μs → 258.22 μs     (-3.54%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       262.92 μs → 250.62 μs     (-4.68%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              262.61 μs → 250.24 μs     (-4.71%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   11.02 μs →  10.47 μs     (-4.95%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.08 ms →   2.08 ms     (+0.32%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.02 ms →   2.02 ms     (+0.29%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             30.92 μs →  30.33 μs     (-1.90%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             203.45 μs → 200.84 μs     (-1.28%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 159.36 μs → 157.26 μs     (-1.32%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    10.04 ms →   9.99 ms     (-0.47%)          22   →     22               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             191.41 ns → 146.27 ns    (-23.58%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.92 ms →   3.98 ms     (+1.56%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.92 ms →   3.98 ms     (+1.56%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              621.44 μs → 628.52 μs     (+1.14%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.30 ms →   2.34 ms     (+1.84%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             972.31 μs → 984.49 μs     (+1.25%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   243.94 μs → 240.35 μs     (-1.47%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   252.86 μs → 249.34 μs     (-1.39%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           250.79 μs → 247.32 μs     (-1.38%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  250.53 μs → 247.13 μs     (-1.36%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            260.98 μs → 259.35 μs     (-0.62%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    259.32 μs → 257.31 μs     (-0.77%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              240.47 μs → 238.68 μs     (-0.74%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 50.62 μs →  51.85 μs     (+2.43%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          48.52 μs →  49.76 μs     (+2.56%)          22   →     22               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                       247.05 μs → 247.40 μs     (+0.14%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     263.02 μs → 247.08 μs     (-6.06%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             261.23 μs → 245.04 μs     (-6.20%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    261.11 μs → 244.91 μs     (-6.20%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              270.86 μs → 264.92 μs     (-2.20%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      269.85 μs → 264.05 μs     (-2.15%)           3   →      3               
  ├ sirius::Stress|kin                                                    313.18 μs → 309.45 μs     (-1.19%)           1   →      1               
  ├ sirius::Stress|har                                                    609.15 μs → 632.75 μs     (+3.87%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.81 ms →   1.83 ms     (+0.93%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.63 ms →   3.61 ms     (-0.60%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    1.14 ms →   1.24 ms     (+8.80%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       216.08 μs → 215.83 μs     (-0.11%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      23.32 μs →  22.10 μs     (-5.24%)           1   →      1               
- ├ sirius::Simulation_context::make_periodic_function                      1.16 ms →   1.29 ms    (+10.49%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       254.45 μs → 266.00 μs     (+4.54%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               252.92 μs → 264.85 μs     (+4.72%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      252.75 μs → 264.70 μs     (+4.73%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                256.58 μs → 268.75 μs     (+4.74%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        255.55 μs → 267.75 μs     (+4.77%)           2   →      2               
  ├ sirius::Stress|us                                                     325.28 ms → 325.70 ms     (+0.13%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                     224.09 μs → 197.83 μs    (-11.72%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             79.07 ms →  78.94 ms     (-0.15%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   586.29 μs → 571.79 μs     (-2.47%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           1.21 ms →   1.25 ms     (+3.67%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.30 ms →  22.25 ms     (-0.23%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                            75.87 μs →  78.67 μs     (+3.68%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                1.36 ms →   1.43 ms     (+5.23%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.97 ms →  14.89 ms     (-0.58%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.85 ms →   5.87 ms     (+0.37%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.69 ms →   8.60 ms     (-1.05%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               349.47 μs → 350.93 μs     (+0.42%)          10   →     10               
- │   ├ sirius::Beta_projectors_base::prepare                               3.94 μs →   5.92 μs    (+50.05%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            326.52 μs → 313.94 μs     (-3.85%)           9   →      9               
  │   └ sirius::Beta_projectors_base::dismiss                              74.00 ns →  77.00 ns     (+4.05%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.30 ms →   1.31 ms     (+0.41%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          26.12 ms →  26.49 ms     (+1.40%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     264.90 μs → 256.67 μs     (-3.11%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.37 ms →   4.42 ms     (+1.05%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                3.18 ms →   3.13 ms     (-1.48%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               359.82 μs → 358.78 μs     (-0.29%)           4   →      4               
+ │   ├ sirius::Beta_projectors_base::prepare                               4.15 μs →   3.10 μs    (-25.11%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            322.72 μs → 311.57 μs     (-3.46%)           3   →      3               
+ │   └ sirius::Beta_projectors_base::dismiss                             148.00 ns → 117.00 ns    (-20.95%)           1   →      1               
+ ├ sirius::Force::calc_forces_core                                         1.21 ms →   1.03 ms    (-14.67%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     220.58 μs → 218.34 μs     (-1.01%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       14.20 ms →  15.00 ms     (+5.66%)           1   →      1               
+ ├ sirius::Force::calc_forces_scf_corr                                   951.27 μs → 726.27 μs    (-23.65%)           1   →      1               
  ├ sirius::Force::hubbard_force                                          486.00 ns → 440.00 ns     (-9.47%)           1   →      1               
  └ sirius::finalize                                                      126.33 ms → 126.59 ms     (+0.21%)           1   →      1               
```
