# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                   71.57 s  →  81.58 s     (+13.98%)           1   →      1               
- ├ sirius::initialize                                                      2.59 s  →   2.95 s     (+13.99%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.81 s  →   3.66 s      (-3.90%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                               149.68 ms →   1.27 ms    (-99.15%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       145.24 ms → 149.75 ms     (+3.10%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                            63.29 ms →  67.09 ms     (+6.00%)           2   →      2               
+ │ │ └ sirius::Unit_cell::update                                          18.56 ms →  15.48 ms    (-16.61%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.58 ms →   3.59 ms     (+0.36%)           1   →      1               
+ │ │   └ sirius::Unit_cell::get_symmetry                                  14.93 ms →  11.82 ms    (-20.84%)           1   →      1               
+ │ │     └ sirius::Unit_cell_symmetry                                     14.86 ms →  11.75 ms    (-20.96%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.73 ms →   2.76 ms     (+1.13%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            501.96 μs → 507.11 μs     (+1.03%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               14.92 μs →  16.01 μs     (+7.32%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.31 s  →   3.41 s      (+3.03%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.72 ms →   6.88 ms     (+2.42%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.42 ms →   3.53 ms     (+3.37%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.26 ms →   3.28 ms     (+0.62%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.22 ms →   3.23 ms     (+0.37%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.69 ms →   2.71 ms     (+0.49%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            494.70 μs → 488.92 μs     (-1.17%)           1   →      1               
- │   │     └ sirius::Unit_cell_symmetry|mag                               13.46 μs →  14.92 μs    (+10.85%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      219.39 ms → 212.63 ms     (-3.08%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           16.06 ms →  15.26 ms     (-5.02%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.24 ms →  13.25 ms     (+0.05%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.31 ms →  56.31 ms     (+0.01%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.17 ms →  45.24 ms     (+0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.07 ms →  60.43 ms     (+0.59%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.57 ms →  93.00 ms     (-0.61%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.94 ms →  69.67 ms     (-0.37%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  91.97 ms →  99.01 ms     (+7.65%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.95 ms →   1.95 ms     (+0.15%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 510.02 ms → 560.58 ms     (+9.91%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                    146.63 ms → 146.99 ms     (+0.24%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              2.52 μs →   2.60 μs     (+2.92%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                     146.55 ms → 146.90 ms     (+0.24%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.13 ms →  28.00 ms     (-0.45%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  11.12 ms →  11.14 ms     (+0.23%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                5.01 ms →   4.98 ms     (-0.54%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                             10.60 μs →  11.11 μs     (+4.81%)           1   →      1               
  │     └ sirius::K_point::update                                          14.12 ms →  14.06 ms     (-0.42%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.16 ms →  10.14 ms     (-0.24%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.17 ms →   8.18 ms     (+0.14%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.55 ms →   2.54 ms     (-0.55%)           2   →      2               
  ├ sirius::Potential                                                      54.73 ms →  51.78 ms     (-5.40%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.89 ms →   2.94 ms     (+1.75%)           6   →      6               
  │ └ sirius::Potential::update                                            36.82 ms →  33.52 ms     (-8.95%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        36.44 ms →  33.13 ms     (-9.08%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               32.09 ms →  26.84 ms    (-16.37%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.80 ms →   5.77 ms    (+51.93%)           1   →      1               
  ├ sirius::Density                                                        42.93 ms →  42.10 ms     (-1.93%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.82 ms →   2.81 ms     (-0.21%)           2   →      2               
  │ └ sirius::Density::update                                              37.15 ms →  36.34 ms     (-2.20%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               36.88 ms →  36.12 ms     (-2.05%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                75.39 μs →  76.66 μs     (+1.69%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               33.16 ms →  26.46 ms    (-20.20%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.30 ms →   9.29 ms   (+181.40%)           1   →      1               
  ├ sirius::Density::initial_density                                       65.12 ms →  59.98 ms     (-7.89%)           1   →      1               
+ │ ├ sirius::Simulation_context::make_periodic_function                   37.03 ms →  26.71 ms    (-27.89%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       4.63 ms →   6.89 ms    (+48.83%)           2   →      2               
- │ └ sirius::Periodic_function::integrate                                  5.25 ms →   5.79 ms    (+10.25%)           1   →      1               
  ├ sirius::Potential::generate                                           372.30 ms → 368.79 ms     (-0.94%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           45.23 ms →  41.89 ms     (-7.37%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.26 ms →   9.96 ms   (+205.25%)           1   →      1               
- │ │ └ sirius::Periodic_function|inner                                     5.06 ms →   5.89 ms    (+16.49%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.63 ms →   4.65 ms     (+0.44%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.62 ms →   4.64 ms     (+0.37%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      763.71 μs → 776.57 μs     (+1.68%)           2   →      2               
  │ ├ sirius::Potential::xc                                                51.35 ms →  51.63 ms     (+0.55%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               50.17 ms →  50.43 ms     (+0.51%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.54 ms →   2.53 ms     (-0.24%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.56 ms →   4.99 ms     (+9.24%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.62 ms →   3.53 ms     (-2.56%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.18 ms → 268.77 ms     (-0.15%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 230.00 ns → 236.00 ns     (+2.61%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.37 ms →   8.58 ms     (+2.46%)           1   →      1               
  │ ├ sirius::Local_operator                                                7.35 ms →   7.38 ms     (+0.40%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.73 ms →   2.75 ms     (+0.46%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     3.56 ms →   3.58 ms     (+0.57%)           1   →      1               
- │ ├ sirius::Non_local_operator                                          384.90 μs → 461.75 μs    (+19.97%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                      107.34 μs → 119.00 μs    (+10.86%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       89.42 μs →  92.97 μs     (+3.97%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.30 s  →   1.31 s      (+0.45%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                58.16 ms →  80.07 ms    (+37.68%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 226.36 μs → 268.16 μs    (+18.47%)           1   →      1               
- │ │ └ sirius::Beta_projectors_base::prepare                              57.93 ms →  79.80 ms    (+37.76%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.24 s  →   1.23 s      (-1.30%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               80.47 ms → 111.10 ms    (+38.07%)           4   →      4               
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                    44.00 ms →  49.31 ms    (+12.08%)           1   →      1               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                             8.90 ms →   6.34 ms    (-28.78%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  314.43 ms → 512.68 ms    (+63.05%)           1   →      1               
- │ │ │ ├ sirius::Local_operator::apply_h                                 246.39 ms → 422.07 ms    (+71.30%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             4.09 μs →   3.45 μs    (-15.78%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.12 μs →   2.49 μs    (-20.13%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           593.00 ns → 450.00 ns    (-24.11%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          536.00 ns →   1.32 μs   (+146.08%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.26 ms →   3.00 ms     (-8.01%)           1   →      1               
- │ │ │ ├ sirius::Beta_projectors_base::inner                              21.35 ms →  39.13 ms    (+83.29%)           1   →      1               
- │ │ │ └ sirius::Non_local_operator::apply                                21.69 ms →  24.22 ms    (+11.64%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                    16.36 ms →   6.52 ms    (-60.13%)           2   →      2               
+ │ │ │ └ sddk::wf_inner                                                   16.15 ms →   6.31 ms    (-60.92%)           2   →      2               
  │ │ │   ├ sddk::wf_inner|scale                                           22.50 ns →  20.50 ns     (-8.89%)           2   →      2               
+ │ │ │   ├ sddk::wf_inner|pw                                              16.02 ms →   6.19 ms    (-61.38%)           2   →      2               
+ │ │ │   └ sddk::wf_inner|scale_back                                      21.50 ns →  18.50 ns    (-13.95%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          250.48 ms →  64.93 ms    (-74.08%)           1   →      1               
  │ │ └ sddk::wf_trans                                                      2.60 ms →   2.59 ms     (-0.23%)           1   →      1               
  │ │   └ sddk::wf_trans|pw                                                 2.59 ms →   2.59 ms     (-0.25%)           1   →      1               
- │ └ sirius::Beta_projectors_base::dismiss                               532.00 ns → 625.00 ns    (+17.48%)           1   →      1               
- ├ sirius::DFT_ground_state::scf_loop                                     62.06 s  →  71.83 s     (+15.74%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.45 ms →   2.44 ms     (-0.62%)          19   →     19               
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.25 s  →   3.11 s      (-4.28%)          19   →     23      (+21.05%)
+ │ │ ├ sirius::Hamiltonian0                                                6.00 ms →   4.98 ms    (-16.95%)          19   →     23      (+21.05%)
+ │ │ │ ├ sirius::Local_operator                                            5.35 ms →   4.34 ms    (-19.00%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sirius::Smooth_periodic_function                              527.77 μs → 560.95 μs     (+6.29%)          19   →     23      (+21.05%)
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 3.32 ms →   2.57 ms    (-22.50%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Non_local_operator                                      185.55 μs → 180.36 μs     (-2.80%)          38   →     46      (+21.05%)
! │ │ │ ├ sirius::D_operator::initialize                                  107.64 μs → 116.84 μs     (+8.55%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::Q_operator::initialize                                   90.59 μs →  92.14 μs     (+1.70%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Band::solve                                                 2.02 s  →   1.88 s      (-7.17%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Hamiltonian_k                                           207.06 μs → 210.61 μs     (+1.71%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sirius::Local_operator::prepare_k                             199.63 μs → 201.54 μs     (+0.96%)          19   →     23      (+21.05%)
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           5.27 μs →   6.55 μs    (+24.25%)          19   →     23      (+21.05%)
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.96 s  →   1.75 s     (-10.68%)          19   →     23      (+21.05%)
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             79.06 ms →  68.27 ms    (-13.65%)          19   →     23      (+21.05%)
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.99 ms →   6.57 ms    (-17.72%)         114   →    138      (+21.05%)
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            15.35 ms →  17.41 ms    (+13.40%)          19   →     23      (+21.05%)
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       482.22 μs → 465.20 μs     (-3.53%)          19   →     23      (+21.05%)
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         6.99 ms →   7.77 ms    (+11.14%)          38   →     46      (+21.05%)
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.86 s  →   1.66 s     (-10.96%)          19   →     23      (+21.05%)
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             55.08 ms →  62.41 ms    (+13.31%)         356   →    297      (-16.57%)
! │ │ │ │   │ ├ sirius::Local_operator::apply_h                            34.53 ms →  36.92 ms     (+6.92%)         356   →    297      (-16.57%)
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.00 μs →   2.17 μs     (+8.67%)         356   →    297      (-16.57%)
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.70 μs →   1.84 μs     (+8.58%)         356   →    297      (-16.57%)
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     471.96 ns → 374.82 ns    (-20.58%)         356   →    297      (-16.57%)
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    600.07 ns → 501.31 ns    (-16.46%)         356   →    297      (-16.57%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      3.01 ms →   2.87 ms     (-4.75%)         356   →    297      (-16.57%)
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.18 ms →   3.57 ms    (+12.34%)         356   →    297      (-16.57%)
- │ │ │ │   │ └ sirius::Non_local_operator::apply                           7.17 ms →   9.52 ms    (+32.74%)         712   →    594      (-16.57%)
- │ │ │ │   ├ sddk::orthogonalize                                           6.45 ms →   7.78 ms    (+20.52%)         356   →    297      (-16.57%)
- │ │ │ │   │ ├ sddk::wf_inner                                              1.06 ms →   1.22 ms    (+15.09%)         693   →    571      (-17.60%)
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                     58.22 ns →  40.64 ns    (-30.20%)         693   →    571      (-17.60%)
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                       896.10 μs →   1.06 ms    (+17.80%)         693   →    571      (-17.60%)
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                45.07 ns →  35.25 ns    (-21.79%)         693   →    571      (-17.60%)
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 116.81 μs → 178.06 μs    (+52.43%)         356   →    297      (-16.57%)
- │ │ │ │   │ ├ sddk::orthogonalize|transform                               1.88 ms →   2.83 ms    (+50.68%)         356   →    297      (-16.57%)
! │ │ │ │   │ └ sddk::wf_trans                                              2.53 ms →   2.62 ms     (+3.82%)         337   →    274      (-18.69%)
! │ │ │ │   │   └ sddk::wf_trans|pw                                       841.23 μs → 873.40 μs     (+3.82%)        1.01 K →    822      (-18.69%)
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.32 ms →   1.63 ms    (+23.89%)         356   →    297      (-16.57%)
- │ │ │ │   │ └ sddk::wf_inner                                              1.25 ms →   1.53 ms    (+22.93%)         356   →    297      (-16.57%)
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                     40.40 ns →  32.59 ns    (-19.34%)         356   →    297      (-16.57%)
- │ │ │ │   │   ├ sddk::wf_inner|pw                                         1.08 ms →   1.37 ms    (+25.98%)         356   →    297      (-16.57%)
- │ │ │ │   │   └ sddk::wf_inner|scale_back                                39.50 ns →  54.49 ns    (+37.94%)         356   →    297      (-16.57%)
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     32.82 ms →  51.93 ms    (+58.21%)         356   →    297      (-16.57%)
- │ │ │ │   ├ sirius::residuals                                             2.62 ms →   3.10 ms    (+18.29%)         340   →    288      (-15.29%)
- │ │ │ │   │ ├ sddk::wf_trans                                              1.34 ms →   1.73 ms    (+28.75%)         337   →    277      (-17.80%)
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                       671.00 μs → 864.31 μs    (+28.81%)         674   →    554      (-17.80%)
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.18 ms →   1.32 ms    (+12.34%)         337   →    277      (-17.80%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       6.97 ms →   7.56 ms     (+8.47%)          54   →     57       (+5.56%)
- │ │ │ │     └ sddk::wf_trans                                              4.18 ms →   4.69 ms    (+12.17%)          89   →     91       (+2.25%)
- │ │ │ │       └ sddk::wf_trans|pw                                         3.00 ms →   3.41 ms    (+13.78%)         124   →    125       (+0.81%)
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                           349.00 ns → 391.74 ns    (+12.25%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::K_point_set::sync_band_energies                          18.87 μs →  20.02 μs     (+6.12%)          19   →     23      (+21.05%)
! │ │ ├ sirius::K_point_set::find_band_occupancies                          1.52 ms →   1.49 ms     (-2.00%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Density::generate                                         566.10 ms → 571.60 ms     (+0.97%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Density::generate_valence                               390.46 ms → 389.60 ms     (-0.22%)          19   →     23      (+21.05%)
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.14 μs →   9.82 μs    (+37.43%)          19   →     23      (+21.05%)
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           6.66 μs →   9.28 μs    (+39.36%)          19   →     23      (+21.05%)
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   41.98 ms →  35.07 ms    (-16.46%)          19   →     23      (+21.05%)
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         6.21 μs →   7.37 μs    (+18.65%)          19   →     23      (+21.05%)
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                       23.17 ms →   5.44 ms    (-76.52%)          19   →     23      (+21.05%)
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          17.79 ms →  28.56 ms    (+60.55%)          19   →     23      (+21.05%)
! │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       528.68 ns → 542.48 ns     (+2.61%)          19   →     23      (+21.05%)
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                   97.53 ms → 110.66 ms    (+13.47%)          19   →     23      (+21.05%)
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 2.00 ms →   2.33 ms    (+16.58%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::Density::augment                                      212.81 ms → 199.43 ms     (-6.29%)          19   →     23      (+21.05%)
! │ │ │ │   └ sirius::Density::generate_rho_aug                           212.58 ms → 199.21 ms     (-6.29%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Field4D::symmetrize                                     147.06 ms → 153.59 ms     (+4.44%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::symmetrize_function|fpw                               147.06 ms → 153.59 ms     (+4.44%)          19   →     23      (+21.05%)
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             62.10 ms →  68.68 ms    (+10.59%)          19   →     23      (+21.05%)
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        71.71 ms →  71.63 ms     (-0.11%)          19   →     23      (+21.05%)
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.60 ms →  12.63 ms     (+0.29%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.58 ms →  23.60 ms     (+0.09%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   4.99 ms →   4.80 ms     (-3.86%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Density::mix                                              132.74 ms → 138.19 ms     (+4.11%)          19   →     23      (+21.05%)
+ │ │ │ ├ sirius::Density::mixer_input                                    961.13 μs → 660.49 μs    (-31.28%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Periodic_function|inner                                   4.89 ms →   4.91 ms     (+0.53%)         229   →    289      (+26.20%)
! │ │ │ │ └ sirius::Periodic_function|inner_local                           4.81 ms →   4.82 ms     (+0.26%)         229   →    289      (+26.20%)
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.81 ms →   4.82 ms     (+0.26%)         229   →    289      (+26.20%)
- │ │ │ └ sirius::Density::mixer_output                                     5.99 ms →   7.39 ms    (+23.42%)          19   →     23      (+21.05%)
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.22 ms →   6.63 ms    (+27.08%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Potential::generate                                       365.52 ms → 362.81 ms     (-0.74%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Potential::poisson                                       45.16 ms →  42.48 ms     (-5.94%)          19   →     23      (+21.05%)
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 3.25 ms →  10.73 ms   (+230.15%)          19   →     23      (+21.05%)
- │ │ │ │ └ sirius::Periodic_function|inner                                 5.09 ms →   5.90 ms    (+15.86%)          19   →     23      (+21.05%)
! │ │ │ │   └ sirius::Periodic_function|inner_local                         4.61 ms →   4.65 ms     (+0.72%)          19   →     23      (+21.05%)
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.61 ms →   4.65 ms     (+0.71%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Periodic_function::add                                  790.82 μs → 762.49 μs     (-3.58%)          38   →     46      (+21.05%)
! │ │ │ ├ sirius::Potential::xc                                            44.93 ms →  45.34 ms     (+0.91%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.75 ms →  44.15 ms     (+0.93%)          19   →     23      (+21.05%)
! │ │ │ │   ├ sirius::Smooth_periodic_function                            674.46 μs → 686.16 μs     (+1.73%)          38   →     46      (+21.05%)
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.60 ms →   5.03 ms     (+9.42%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.71 ms →   3.54 ms     (-4.48%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.71 ms → 268.50 ms     (-0.08%)          19   →     23      (+21.05%)
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             247.47 ns → 311.43 ns    (+25.85%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Field4D::symmetrize                                        98.42 ms →  97.85 ms     (-0.58%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::symmetrize_function|fpw                                  98.42 ms →  97.85 ms     (-0.58%)          19   →     23      (+21.05%)
! │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.56 ms →  13.28 ms     (-2.06%)          19   →     23      (+21.05%)
! │ │ │   ├ sirius::symmetrize_function|fpw|local                          71.64 ms →  71.35 ms     (-0.41%)          19   →     23      (+21.05%)
! │ │ │   └ sddk::Gvec_shells::remap_backward                              12.59 ms →  12.59 ms     (+0.00%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.36 ms →   4.69 ms     (+7.75%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Periodic_function|inner                                     4.79 ms →   4.64 ms     (-3.12%)         133   →    161      (+21.05%)
! │ │ │ └ sirius::Periodic_function|inner_local                             4.55 ms →   4.57 ms     (+0.40%)         133   →    161      (+21.05%)
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.55 ms →   4.57 ms     (+0.39%)         133   →    161      (+21.05%)
! │ │ ├ sirius::Smooth_periodic_function|inner                              5.02 ms →   4.96 ms     (-1.24%)          57   →     69      (+21.05%)
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                      5.01 ms →   4.94 ms     (-1.34%)          57   →     69      (+21.05%)
! │ │ ├ sirius::Periodic_function::integrate                                4.52 ms →   4.77 ms     (+5.44%)          19   →     23      (+21.05%)
! │ │ └ sirius::Density::get_magnetisation                                 75.19 μs →  75.68 μs     (+0.65%)          19   →     23      (+21.05%)
! │ │   └ sirius::Density::compute_atomic_mag_mom                          71.18 μs →  70.93 μs     (-0.35%)          19   →     23      (+21.05%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.12 ms →   5.57 ms     (+8.77%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.79 ms →   4.73 ms     (-1.17%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.79 ms →   4.73 ms     (-1.20%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.78 ms →   4.73 ms     (-1.21%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                5.20 ms →   5.07 ms     (-2.62%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        5.20 ms →   5.03 ms     (-3.27%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.75 ms →   4.80 ms     (+1.06%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.75 ms →   4.80 ms     (+1.04%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.75 ms →   4.80 ms     (+1.04%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.92 ms →   5.15 ms     (+4.81%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.91 ms →   5.15 ms     (+4.87%)           1   →      1               
+ └ sirius::finalize                                                      488.08 ms → 142.77 ms    (-70.75%)           1   →      1               
```
