# Benchmark efdc91cad0a010088b39093672888d5494da3277 vs e0e9b0141dd4fb9fa870976131baaca49c1f1afa
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   46.77 s  →  46.97 s      (+0.44%)           1   →      1               
! ├ sirius::initialize                                                      2.97 s  →   3.67 s     (+23.56%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                 20.70 s  →  20.12 s      (-2.80%)           1   →      1               
! │ ├ sirius::Simulation_context::init_comm                               255.12 μs →  80.46 μs    (-68.46%)           1   →      1               
! │ ├ sirius::Unit_cell::initialize                                         1.32 s  → 696.31 ms    (-47.15%)           1   →      1               
! │ │ ├ sirius::Atom_type::init                                           433.36 ms → 226.71 ms    (-47.69%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          17.51 ms →  16.15 ms     (-7.76%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      272.17 μs → 285.26 μs     (+4.81%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  17.23 ms →  15.86 ms     (-7.97%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     17.21 ms →  15.82 ms     (-8.07%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.62 ms →   4.85 ms     (+4.91%)           1   →      1               
! │ │       ├ sirius::Unit_cell_symmetry|equiv                             31.55 μs →   2.07 ms  (+6471.82%)           1   →      1               
! │ │       └ sirius::Unit_cell_symmetry|mag                               17.79 μs →  23.32 μs    (+31.07%)           1   →      1               
  │ └ sirius::Simulation_context::update                                   19.33 s  →  19.39 s      (+0.30%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.04 ms →   5.07 ms     (+0.58%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       71.56 μs →  64.45 μs     (-9.95%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   4.97 ms →   5.00 ms     (+0.73%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      4.94 ms →   4.98 ms     (+0.70%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.82 ms →   4.86 ms     (+0.75%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                             63.47 μs →  58.30 μs     (-8.15%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               17.10 μs →  16.67 μs     (-2.50%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                        4.65 s  →   4.68 s      (+0.53%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                          239.71 ms → 240.96 ms     (+0.52%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                               211.83 ms → 212.84 ms     (+0.48%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                     692.87 ms → 694.62 ms     (+0.25%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                       1.59 s  →   1.59 s      (+0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                               661.77 ms → 663.00 ms     (+0.19%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   10.94 ms →  11.27 ms     (+3.04%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      6.87 ms →   7.17 ms     (+4.35%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  11.41 ms →  11.31 ms     (-0.90%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                898.26 μs → 954.91 μs     (+6.31%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 678.75 ms → 677.39 ms     (-0.20%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                     26.03 ms →  26.57 ms     (+2.06%)           1   →      1               
! │ ├ sirius::K_point::K_point                                            816.25 ns →   1.12 μs    (+36.94%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      25.96 ms →  26.49 ms     (+2.06%)           1   →      1               
  │   └ sirius::K_point::initialize                                         6.17 ms →   6.31 ms     (+2.25%)           4   →      4               
  │     ├ sirius::K_point::generate_gkvec                                   3.47 ms →   3.60 ms     (+3.65%)           4   →      4               
  │     │ └ sddk::Gvec::init                                              362.04 μs → 370.42 μs     (+2.31%)           4   →      4               
  │     ├ sddk::matrix_storage::matrix_storage                              3.93 μs →   3.79 μs     (-3.56%)           4   →      4               
  │     └ sirius::K_point::update                                           2.45 ms →   2.51 ms     (+2.69%)           4   →      4               
  │       └ sirius::Beta_projectors                                         2.25 ms →   2.31 ms     (+2.68%)           4   →      4               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                943.34 μs → 944.08 μs     (+0.08%)           4   →      4               
  │         └ sirius::Beta_projectors_base::generate                        1.30 ms →   1.36 ms     (+4.38%)           4   →      4               
! ├ sirius::Smooth_periodic_function                                      435.94 μs → 490.00 μs    (+12.40%)           2   →      2               
! ├ sirius::Potential                                                       7.95 ms →   9.18 ms    (+15.50%)           1   →      1               
! │ ├ sirius::Smooth_periodic_function                                    429.04 μs → 549.70 μs    (+28.12%)           6   →      6               
  │ └ sirius::Potential::update                                             5.24 ms →   5.76 ms     (+9.97%)           1   →      1               
! │   └ sirius::Potential::generate_local_potential                         5.20 ms →   5.72 ms    (+10.06%)           1   →      1               
! │     ├ sirius::Simulation_context::make_periodic_function                4.12 ms →   4.64 ms    (+12.59%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 907.25 μs → 892.39 μs     (-1.64%)           1   →      1               
  ├ sirius::Density                                                         6.26 ms →   6.45 ms     (+2.95%)           1   →      1               
! │ ├ sirius::Smooth_periodic_function                                    230.23 μs → 344.09 μs    (+49.45%)           2   →      2               
  │ └ sirius::Density::update                                               5.80 ms →   5.74 ms     (-0.91%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                5.76 ms →   5.70 ms     (-0.93%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                66.40 μs →  68.30 μs     (+2.86%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                4.78 ms →   4.70 ms     (-1.58%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 868.60 μs → 879.30 μs     (+1.23%)           1   →      1               
  ├ sirius::Density::initial_density                                       12.07 ms →  12.46 ms     (+3.19%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    5.68 ms →   5.80 ms     (+2.13%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     813.86 μs → 876.72 μs     (+7.72%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  1.21 ms →   1.27 ms     (+4.32%)           1   →      1               
  ├ sirius::Potential::generate                                            58.45 ms →  57.50 ms     (-1.62%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            5.75 ms →   6.02 ms     (+4.77%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   851.00 μs → 918.20 μs     (+7.90%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     1.50 ms →   1.60 ms     (+6.63%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             1.50 ms →   1.60 ms     (+6.50%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    1.50 ms →   1.60 ms     (+6.50%)           1   →      1               
! │ ├ sirius::Periodic_function::add                                      125.53 μs → 271.66 μs   (+116.42%)           2   →      2               
  │ ├ sirius::Potential::xc                                                12.44 ms →  12.91 ms     (+3.75%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               12.23 ms →  12.90 ms     (+5.48%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                501.64 μs → 530.05 μs     (+5.66%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 869.21 μs → 869.59 μs     (+0.04%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     758.69 μs → 819.52 μs     (+8.02%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        39.03 ms →  36.84 ms     (-5.61%)           1   →      1               
! │ └ sirius::Potential::generate_PAW_effective_potential                 137.00 ns → 449.00 ns   (+227.74%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  364.74 μs → 345.86 μs     (-5.18%)           1   →      1               
  │ ├ sirius::Local_operator                                              313.06 μs → 294.27 μs     (-6.00%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function                                   34.63 μs →  25.36 μs    (-26.76%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   188.04 μs → 181.08 μs     (-3.70%)           1   →      1               
  │ ├ sirius::Non_local_operator                                            1.08 μs →   1.06 μs     (-2.27%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       24.56 μs →  22.98 μs     (-6.42%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       14.32 μs →  15.66 μs     (+9.39%)           1   →      1               
! ├ sirius::Band::initialize_subspace                                     110.73 ms →  95.96 ms    (-13.33%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                22.31 μs →  23.02 μs     (+3.18%)           4   →      4               
  │ │ └ sirius::Local_operator::prepare_k                                  21.53 μs →  22.35 μs     (+3.82%)           4   →      4               
! │ └ sirius::Band::initialize_subspace|kp                                 27.66 ms →  23.96 ms    (-13.35%)           4   →      4               
  │   ├ sddk::matrix_storage::matrix_storage                              859.44 ns → 935.63 ns     (+8.86%)          16   →     16               
  │   ├ sirius::K_point::generate_atomic_wave_functions                     1.63 ms →   1.54 ms     (-5.75%)           4   →      4               
! │   ├ sirius::Band::initialize_subspace|kp|wf                           204.38 μs → 171.22 μs    (-16.23%)           4   →      4               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   16.37 ms →  15.34 ms     (-6.34%)           4   →      4               
  │   │ ├ sirius::Local_operator::apply_h                                  11.69 ms →  11.79 ms     (+0.81%)           4   →      4               
  │   │ │ ├ sddk::matrix_storage::remap_forward                             2.37 μs →   2.55 μs     (+7.87%)           4   →      4               
! │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.71 μs →   1.92 μs    (+12.42%)           4   →      4               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           401.50 ns → 419.00 ns     (+4.36%)           4   →      4               
! │   │ │ └ sddk::matrix_storage::remap_backward                          764.50 ns →   1.17 μs    (+53.04%)           4   →      4               
! │   │ ├ sirius::Beta_projectors_base::inner                               2.77 ms →   1.91 ms    (-30.97%)           4   →      4               
! │   │ └ sirius::Non_local_operator::apply                               903.35 μs → 761.49 μs    (-15.70%)           8   →      8               
  │   ├ sirius::Band::set_subspace_mtrx                                   355.33 μs → 346.72 μs     (-2.42%)           8   →      8               
  │   │ └ sddk::inner                                                     348.67 μs → 339.65 μs     (-2.59%)           8   →      8               
  │   │   └ sddk::inner|local                                             345.36 μs → 336.67 μs     (-2.52%)           8   →      8               
! │   ├ Eigensolver_lapack|zhegvx                                           8.17 ms →   5.60 ms    (-31.43%)           4   →      4               
! │   └ sddk::transform                                                   447.18 μs → 511.92 μs    (+14.48%)           4   →      4               
! │     ├ sddk::transform|init                                            214.39 μs → 286.94 μs    (+33.84%)           4   →      4               
  │     └ sddk::transform|local                                           227.26 μs → 220.13 μs     (-3.14%)           4   →      4               
! ├ sirius::DFT_ground_state::scf_loop                                     11.69 s  →  14.37 s     (+22.91%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    482.32 μs → 475.10 μs     (-1.50%)          19   →     19               
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                        581.98 ms → 896.30 ms    (+54.01%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Hamiltonian0                                              371.78 μs → 370.97 μs     (-0.22%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Local_operator                                          326.95 μs → 324.60 μs     (-0.72%)          20   →     16      (-20.00%)
! │ │ │ │ ├ sirius::Smooth_periodic_function                               35.73 μs →  33.15 μs     (-7.23%)          20   →     16      (-20.00%)
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               201.92 μs → 202.68 μs     (+0.38%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Non_local_operator                                      888.28 ns → 979.25 ns    (+10.24%)          40   →     32      (-20.00%)
! │ │ │ ├ sirius::D_operator::initialize                                   23.03 μs →  21.55 μs     (-6.42%)          20   →     16      (-20.00%)
! │ │ │ └ sirius::Q_operator::initialize                                   13.66 μs →  14.66 μs     (+7.30%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Band::solve                                               191.86 ms → 515.53 ms   (+168.71%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Hamiltonian_k                                            19.69 μs →  22.39 μs    (+13.67%)          80   →     64      (-20.00%)
! │ │ │ │ └ sirius::Local_operator::prepare_k                              18.95 μs →  21.43 μs    (+13.06%)          80   →     64      (-20.00%)
! │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     47.91 ms → 128.83 ms   (+168.88%)          80   →     64      (-20.00%)
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             13.71 μs →  15.43 μs    (+12.51%)          80   →     64      (-20.00%)
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        904.81 ns → 983.97 ns     (+8.75%)         480   →    384      (-20.00%)
! │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             1.78 ms →   1.62 ms     (-8.71%)          80   →     64      (-20.00%)
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        29.46 μs →  29.16 μs     (-1.03%)          80   →     64      (-20.00%)
! │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       548.59 μs → 496.55 μs     (-9.49%)         240   →    192      (-20.00%)
! │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              46.11 ms → 127.18 ms   (+175.81%)          80   →     64      (-20.00%)
! │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              7.34 ms →   6.38 ms    (-13.13%)         323   →    711     (+120.12%)
! │ │ │ │   │ ├ sirius::Local_operator::apply_h                             6.37 ms →   5.45 ms    (-14.50%)         323   →    711     (+120.12%)
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.46 μs →   2.64 μs     (+7.14%)         323   →    711     (+120.12%)
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.89 μs →   2.15 μs    (+13.93%)         323   →    711     (+120.12%)
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     561.47 ns → 685.58 ns    (+22.11%)         323   →    711     (+120.12%)
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    685.30 ns → 667.78 ns     (-2.56%)         323   →    711     (+120.12%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       321.53 μs → 310.30 μs     (-3.49%)         323   →    711     (+120.12%)
! │ │ │ │   │ └ sirius::Non_local_operator::apply                         292.70 μs → 283.14 μs     (-3.27%)         646   →   1.42 K   (+120.12%)
! │ │ │ │   ├ sddk::orthogonalize                                           1.30 ms →   1.50 ms    (+15.42%)         323   →    711     (+120.12%)
! │ │ │ │   │ ├ sddk::inner                                               195.83 μs → 205.26 μs     (+4.81%)         566   →   1.36 K   (+139.93%)
! │ │ │ │   │ │ └ sddk::inner|local                                       194.21 μs → 203.50 μs     (+4.78%)         566   →   1.36 K   (+139.93%)
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  31.79 μs →  24.07 μs    (-24.30%)         323   →    711     (+120.12%)
! │ │ │ │   │ ├ sddk::orthogonalize|transform                             253.15 μs → 169.77 μs    (-32.94%)         323   →    711     (+120.12%)
! │ │ │ │   │ └ sddk::transform                                           875.86 μs → 989.08 μs    (+12.93%)         243   →    647     (+166.26%)
! │ │ │ │   │   ├ sddk::transform|init                                    456.26 μs → 476.31 μs     (+4.39%)         243   →    647     (+166.26%)
! │ │ │ │   │   └ sddk::transform|local                                   139.09 μs → 170.09 μs    (+22.29%)         729   →   1.94 K   (+166.26%)
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             277.26 μs → 263.36 μs     (-5.01%)         323   →    711     (+120.12%)
! │ │ │ │   │ └ sddk::inner                                               256.35 μs → 239.77 μs     (-6.47%)         323   →    711     (+120.12%)
! │ │ │ │   │   └ sddk::inner|local                                       255.10 μs → 238.52 μs     (-6.50%)         323   →    711     (+120.12%)
! │ │ │ │   ├ Eigensolver_lapack|zheevx                                     1.08 ms →   1.21 ms    (+12.12%)         323   →    711     (+120.12%)
! │ │ │ │   ├ sirius::residuals                                           937.87 μs →   1.84 ms    (+96.69%)         322   →    688     (+113.66%)
! │ │ │ │   │ ├ sddk::transform                                           449.27 μs → 685.26 μs    (+52.53%)         251   →    688     (+174.10%)
! │ │ │ │   │ │ ├ sddk::transform|init                                     65.72 μs → 104.45 μs    (+58.94%)         251   →    688     (+174.10%)
! │ │ │ │   │ │ └ sddk::transform|local                                   190.46 μs → 289.07 μs    (+51.78%)         502   →   1.38 K   (+174.10%)
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               740.59 μs →   1.16 ms    (+56.27%)         251   →    688     (+174.10%)
! │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     946.41 μs → 630.32 μs    (-33.40%)         146   →    300     (+105.48%)
! │ │ │ │     └ sddk::transform                                           568.30 μs → 427.63 μs    (-24.75%)         212   →    300      (+41.51%)
! │ │ │ │       ├ sddk::transform|init                                     74.00 μs →  55.09 μs    (-25.56%)         212   →    300      (+41.51%)
  │ │ │ │       └ sddk::transform|local                                   375.60 μs → 370.46 μs     (-1.37%)         278   →    300       (+7.91%)
! │ │ │ └ sirius::K_point_set::sync_band_energies                          18.06 μs →  19.74 μs     (+9.34%)          20   →     16      (-20.00%)
! │ │ ├ sirius::K_point_set::find_band_occupancies                        404.48 μs → 407.27 μs     (+0.69%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Density::generate                                         260.21 ms → 254.16 ms     (-2.32%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Density::generate_valence                               211.65 ms → 207.46 ms     (-1.98%)          20   →     16      (-20.00%)
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.82 μs →   3.97 μs     (+3.78%)          80   →     64      (-20.00%)
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.47 μs →   3.48 μs     (+0.18%)          80   →     64      (-20.00%)
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  429.26 μs → 437.02 μs     (+1.81%)          80   →     64      (-20.00%)
! │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         379.71 μs → 386.87 μs     (+1.89%)          80   →     64      (-20.00%)
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    4.77 ms →   4.78 ms     (+0.34%)          80   →     64      (-20.00%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               164.70 μs → 170.03 μs     (+3.24%)          20   →     16      (-20.00%)
! │ │ │ │ └ sirius::Density::augment                                      190.21 ms → 185.91 ms     (-2.26%)          20   →     16      (-20.00%)
! │ │ │ │   └ sirius::Density::generate_rho_aug                           190.09 ms → 185.81 ms     (-2.25%)          20   →     16      (-20.00%)
! │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                     11.35 ms →  11.38 ms     (+0.27%)          60   →     48      (-20.00%)
! │ │ │ │     └ sirius::Density::generate_rho_aug|sum                      46.99 ms →  45.42 ms     (-3.33%)          60   →     48      (-20.00%)
! │ │ │ ├ sirius::Field4D::symmetrize                                      17.81 ms →  17.53 ms     (-1.57%)          20   →     16      (-20.00%)
! │ │ │ │ └ sirius::symmetrize_function|fpw                                17.81 ms →  17.53 ms     (-1.57%)          20   →     16      (-20.00%)
! │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              3.08 ms →   3.06 ms     (-0.82%)          20   →     16      (-20.00%)
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        11.65 ms →  11.35 ms     (-2.61%)          20   →     16      (-20.00%)
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                             3.00 ms →   3.04 ms     (+1.54%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                       28.97 ms →  28.23 ms     (-2.52%)          20   →     16      (-20.00%)
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   1.79 ms → 938.57 μs    (-47.56%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Density::mix                                               40.94 ms →  38.13 ms     (-6.88%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Density::mixer_input                                    267.18 μs → 254.02 μs     (-4.92%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Periodic_function|inner                                   1.54 ms →   1.53 ms     (-0.58%)         244   →    184      (-24.59%)
! │ │ │ │ └ sirius::Periodic_function|inner_local                           1.53 ms →   1.53 ms     (-0.45%)         244   →    184      (-24.59%)
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  1.53 ms →   1.52 ms     (-0.44%)         244   →    184      (-24.59%)
! │ │ │ └ sirius::Density::mixer_output                                     1.09 ms →   1.11 ms     (+1.16%)          20   →     16      (-20.00%)
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform               837.69 μs → 844.33 μs     (+0.79%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Potential::generate                                        51.33 ms →  51.52 ms     (+0.37%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Potential::poisson                                        5.95 ms →   5.90 ms     (-0.81%)          20   →     16      (-20.00%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               890.95 μs → 902.39 μs     (+1.28%)          20   →     16      (-20.00%)
! │ │ │ │ └ sirius::Periodic_function|inner                                 1.54 ms →   1.57 ms     (+1.74%)          20   →     16      (-20.00%)
! │ │ │ │   └ sirius::Periodic_function|inner_local                         1.54 ms →   1.57 ms     (+1.73%)          20   →     16      (-20.00%)
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                1.54 ms →   1.57 ms     (+1.76%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Periodic_function::add                                  152.01 μs → 261.52 μs    (+72.04%)          40   →     32      (-20.00%)
! │ │ │ ├ sirius::Potential::xc                                            11.05 ms →  11.08 ms     (+0.35%)          20   →     16      (-20.00%)
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           10.83 ms →  11.08 ms     (+2.37%)          20   →     16      (-20.00%)
! │ │ │ │   ├ sirius::Smooth_periodic_function                            126.05 μs → 137.04 μs     (+8.72%)          40   →     32      (-20.00%)
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             856.23 μs → 864.38 μs     (+0.95%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 796.89 μs → 805.29 μs     (+1.05%)          20   →     16      (-20.00%)
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    32.98 ms →  32.84 ms     (-0.43%)          20   →     16      (-20.00%)
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential             158.65 ns → 197.88 ns    (+24.72%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Field4D::symmetrize                                        18.39 ms →  17.91 ms     (-2.61%)          20   →     16      (-20.00%)
! │ │ │ └ sirius::symmetrize_function|fpw                                  18.39 ms →  17.91 ms     (-2.61%)          20   →     16      (-20.00%)
! │ │ │   ├ sddk::Gvec_shells::remap_forward                                3.19 ms →   3.14 ms     (-1.35%)          20   →     16      (-20.00%)
! │ │ │   ├ sirius::symmetrize_function|fpw|local                          12.04 ms →  11.60 ms     (-3.67%)          20   →     16      (-20.00%)
! │ │ │   └ sddk::Gvec_shells::remap_backward                               3.08 ms →   3.09 ms     (+0.22%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                   921.19 μs → 910.77 μs     (-1.13%)          20   →     16      (-20.00%)
! │ │ ├ sirius::Periodic_function|inner                                     1.59 ms →   1.58 ms     (-0.53%)         140   →    112      (-20.00%)
! │ │ │ └ sirius::Periodic_function|inner_local                             1.59 ms →   1.58 ms     (-0.51%)         140   →    112      (-20.00%)
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                    1.59 ms →   1.58 ms     (-0.51%)         140   →    112      (-20.00%)
! │ │ ├ sirius::Smooth_periodic_function|inner                              1.17 ms →   1.13 ms     (-3.97%)          60   →     48      (-20.00%)
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                      1.17 ms →   1.13 ms     (-3.98%)          60   →     48      (-20.00%)
! │ │ ├ sirius::Periodic_function::integrate                                1.25 ms →   1.26 ms     (+0.58%)          20   →     16      (-20.00%)
! │ │ └ sirius::Density::get_magnetisation                                105.11 μs → 108.94 μs     (+3.64%)          20   →     16      (-20.00%)
! │ │   └ sirius::Density::compute_atomic_mag_mom                         102.76 μs → 106.26 μs     (+3.41%)          20   →     16      (-20.00%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                       102.55 μs → 101.85 μs     (-0.68%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       1.58 ms →   1.54 ms     (-2.31%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               1.57 ms →   1.54 ms     (-2.25%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      1.57 ms →   1.54 ms     (-2.25%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                1.15 ms →   1.09 ms     (-5.10%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.15 ms →   1.09 ms     (-5.08%)           3   →      3               
  ├ sirius::Stress|kin                                                      5.04 ms →   4.81 ms     (-4.57%)           1   →      1               
  ├ sirius::Stress|har                                                      3.40 ms →   3.34 ms     (-1.86%)           1   →      1               
  ├ sirius::Stress|ewald                                                   10.86 ms →  10.89 ms     (+0.25%)           1   →      1               
  ├ sirius::Stress|vloc                                                    13.06 ms →  12.51 ms     (-4.24%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    4.51 ms →   4.23 ms     (-6.17%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       818.83 μs → 850.77 μs     (+3.90%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      72.50 μs →  70.58 μs     (-2.65%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      4.50 ms →   4.16 ms     (-7.53%)           1   →      1               
  ├ sirius::Periodic_function|inner                                         1.55 ms →   1.58 ms     (+1.70%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                                 1.55 ms →   1.58 ms     (+1.69%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.55 ms →   1.58 ms     (+1.69%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                  1.31 ms →   1.33 ms     (+0.84%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                          1.31 ms →   1.32 ms     (+0.81%)           2   →      2               
! ├ sirius::Stress|us                                                      10.66 s  →   8.09 s     (-24.17%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     797.08 μs → 814.02 μs     (+2.13%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             92.03 ms →  92.88 ms     (+0.93%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                     3.16 ms →   3.20 ms     (+1.09%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           4.75 ms →   4.81 ms     (+1.30%)           3   →      3               
! │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs          1.16 s  → 868.78 ms    (-24.79%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                           503.72 μs → 512.11 μs     (+1.66%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                5.04 ms →   5.01 ms     (-0.65%)          27   →     27               
  ├ sirius::Stress|nonloc                                                 136.18 ms → 128.42 ms     (-5.70%)           1   →      1               
! │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t            13.99 ms →  12.32 ms    (-11.99%)           4   →      4               
  │ └ sirius::Non_local_functor::add_k_point                               20.03 ms →  19.77 ms     (-1.32%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::inner                               351.08 μs → 350.43 μs     (-0.18%)          40   →     40               
! │   ├ sirius::Beta_projectors_base::prepare                              72.04 μs →   1.80 μs    (-97.50%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::generate                              1.17 ms →   1.15 ms     (-1.57%)          36   →     36               
! │   └ sirius::Beta_projectors_base::dismiss                              73.75 ns → 151.25 ns   (+105.08%)           4   →      4               
  ├ sirius::Force::calc_forces_vloc                                        10.22 ms →  10.41 ms     (+1.91%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          95.66 ms →  97.05 ms     (+1.44%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     917.40 μs → 857.07 μs     (-6.58%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                      39.00 ms →  36.31 ms     (-6.91%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                7.72 ms →   6.95 ms     (-9.96%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::inner                               341.95 μs → 354.32 μs     (+3.62%)          16   →     16               
! │   ├ sirius::Beta_projectors_base::prepare                               1.49 μs →   1.77 μs    (+18.75%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::generate                              1.16 ms →   1.17 ms     (+1.37%)          12   →     12               
! │   └ sirius::Beta_projectors_base::dismiss                             139.25 ns →  70.00 ns    (-49.73%)           4   →      4               
  ├ sirius::Force::calc_forces_core                                        10.22 ms →  10.22 ms     (+0.07%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     853.20 μs → 857.51 μs     (+0.51%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       52.47 ms →  53.08 ms     (+1.17%)           1   →      1               
  ├ sirius::Force::calc_forces_scf_corr                                     8.86 ms →   8.81 ms     (-0.52%)           1   →      1               
! ├ sirius::Force::hubbard_force                                            2.57 μs →   2.30 μs    (-10.32%)           1   →      1               
  └ sirius::finalize                                                       81.70 ms →  86.63 ms     (+6.03%)           1   →      1               
```
