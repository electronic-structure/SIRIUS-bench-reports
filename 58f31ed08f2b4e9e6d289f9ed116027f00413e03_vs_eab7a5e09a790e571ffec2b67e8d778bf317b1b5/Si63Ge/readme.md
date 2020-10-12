# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                   72.51 s  →  81.63 s     (+12.57%)           1   →      1               
+ ├ sirius::initialize                                                      3.42 s  →   2.92 s     (-14.40%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.89 s  →   3.85 s      (-1.16%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               217.32 μs →   1.01 ms   (+366.08%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       136.38 ms → 161.00 ms    (+18.05%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            59.64 ms →  70.91 ms    (+18.91%)           2   →      2               
- │ │ └ sirius::Unit_cell::update                                          17.02 ms →  19.06 ms    (+11.98%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        4.98 ms →   5.00 ms     (+0.22%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  11.94 ms →  13.98 ms    (+17.14%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     11.88 ms →  13.92 ms    (+17.17%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.68 ms →   2.75 ms     (+2.75%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            500.53 μs → 503.45 μs     (+0.58%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               14.42 μs →  15.12 μs     (+4.88%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.70 s  →   3.63 s      (-1.92%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.97 ms →   6.90 ms     (-0.94%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.62 ms →   3.54 ms     (-2.21%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.31 ms →   3.30 ms     (-0.13%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.26 ms →   3.26 ms     (-0.24%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.71 ms →   2.71 ms     (-0.12%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            514.77 μs → 506.10 μs     (-1.69%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               13.69 μs →  14.41 μs     (+5.33%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      211.48 ms → 212.41 ms     (+0.44%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.15 ms →  15.15 ms     (-0.02%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.26 ms →  13.25 ms     (-0.10%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.27 ms →  56.33 ms     (+0.10%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.19 ms →  45.08 ms     (-0.25%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.55 ms →  60.36 ms     (-0.31%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.08 ms →  92.62 ms     (-0.49%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.66 ms →  69.26 ms     (-0.56%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  93.24 ms →  92.32 ms     (-0.99%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.95 ms →   1.94 ms     (-0.06%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 653.99 ms → 664.45 ms     (+1.60%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     88.84 ms →  88.07 ms     (-0.86%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              1.43 μs →   1.47 μs     (+2.66%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      88.76 ms →  87.99 ms     (-0.86%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.36 ms →  27.76 ms     (-2.11%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  11.02 ms →  10.97 ms     (-0.46%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                5.01 ms →   4.89 ms     (-2.35%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              7.26 μs →   7.57 μs     (+4.38%)           1   →      1               
  │     └ sirius::K_point::update                                          14.48 ms →  14.00 ms     (-3.28%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.55 ms →  10.09 ms     (-4.30%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.67 ms →   8.24 ms     (-4.89%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.54 ms →   2.58 ms     (+1.56%)           2   →      2               
  ├ sirius::Potential                                                      53.35 ms →  54.62 ms     (+2.38%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.90 ms →   2.92 ms     (+0.38%)           6   →      6               
  │ └ sirius::Potential::update                                            35.32 ms →  36.54 ms     (+3.45%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        34.93 ms →  36.13 ms     (+3.44%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               29.66 ms →  31.74 ms     (+6.99%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   4.69 ms →   3.84 ms    (-18.11%)           1   →      1               
  ├ sirius::Density                                                        41.00 ms →  42.11 ms     (+2.70%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.83 ms →   2.84 ms     (+0.20%)           2   →      2               
  │ └ sirius::Density::update                                              35.20 ms →  36.29 ms     (+3.10%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               34.93 ms →  36.00 ms     (+3.09%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                78.25 μs →  78.73 μs     (+0.60%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               29.89 ms →  32.29 ms     (+8.04%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   4.63 ms →   3.32 ms    (-28.39%)           1   →      1               
  ├ sirius::Density::initial_density                                       61.37 ms →  65.96 ms     (+7.48%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                   34.06 ms →  37.37 ms     (+9.73%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       4.23 ms →   5.01 ms    (+18.57%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  5.18 ms →   4.88 ms     (-5.65%)           1   →      1               
  ├ sirius::Potential::generate                                           371.21 ms → 373.88 ms     (+0.72%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           42.69 ms →  44.78 ms     (+4.89%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.80 ms →   3.32 ms    (-12.73%)           1   →      1               
+ │ │ └ sirius::Periodic_function|inner                                     5.91 ms →   5.05 ms    (-14.60%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.88 ms →   4.63 ms     (-5.00%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.87 ms →   4.63 ms     (-4.99%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      828.77 μs → 786.15 μs     (-5.14%)           2   →      2               
  │ ├ sirius::Potential::xc                                                52.10 ms →  53.56 ms     (+2.81%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               50.93 ms →  52.40 ms     (+2.89%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.54 ms →   2.59 ms     (+2.17%)           2   →      2               
- │ │   └ sirius::Smooth_periodic_function::fft_transform                   3.34 ms →   4.38 ms    (+31.35%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.47 ms →   3.28 ms     (-5.64%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.93 ms → 269.29 ms     (-0.24%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 284.00 ns → 302.00 ns     (+6.34%)           1   →      1               
- ├ sirius::Hamiltonian0                                                    6.86 ms →   8.82 ms    (+28.59%)           1   →      1               
- │ ├ sirius::Local_operator                                                6.36 ms →   8.35 ms    (+31.24%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.73 ms →   2.74 ms     (+0.11%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.86 ms →   3.99 ms    (+39.58%)           1   →      1               
- │ ├ sirius::Non_local_operator                                           80.35 μs → 103.72 μs    (+29.09%)           2   →      2               
+ │ ├ sirius::D_operator::initialize                                      152.13 μs → 110.60 μs    (-27.30%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       99.85 μs →  91.80 μs     (-8.06%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.27 s  →   1.28 s      (+0.77%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                53.36 ms →  67.23 ms    (+25.99%)           1   →      1               
  │ │ ├ sirius::Local_operator::prepare_k                                 292.51 μs → 273.47 μs     (-6.51%)           1   →      1               
- │ │ └ sirius::Beta_projectors_base::prepare                              53.06 ms →  66.95 ms    (+26.17%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.22 s  →   1.22 s      (-0.34%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               76.19 ms → 105.52 ms    (+38.49%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    37.23 ms →  36.08 ms     (-3.10%)           1   →      1               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                             7.31 ms →   6.16 ms    (-15.73%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  314.06 ms → 451.88 ms    (+43.88%)           1   →      1               
- │ │ │ ├ sirius::Local_operator::apply_h                                 246.34 ms → 377.10 ms    (+53.08%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             4.35 μs →   4.25 μs     (-2.37%)           1   →      1               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.37 μs →   3.34 μs     (-1.01%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           604.00 ns → 471.00 ns    (-22.02%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          464.00 ns →   1.36 μs   (+193.53%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.16 ms →   3.05 ms     (-3.41%)           1   →      1               
- │ │ │ ├ sirius::Beta_projectors_base::inner                              21.30 ms →  24.55 ms    (+15.28%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                                21.61 ms →  23.56 ms     (+9.03%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    16.16 ms →  14.76 ms     (-8.65%)           2   →      2               
  │ │ │ └ sddk::wf_inner                                                   15.95 ms →  14.55 ms     (-8.78%)           2   →      2               
- │ │ │   ├ sddk::wf_inner|scale                                           38.00 ns → 144.50 ns   (+280.26%)           2   →      2               
  │ │ │   ├ sddk::wf_inner|pw                                              15.82 ms →  14.43 ms     (-8.80%)           2   →      2               
- │ │ │   └ sddk::wf_inner|scale_back                                      18.50 ns →  26.00 ns    (+40.54%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          256.91 ms → 112.52 ms    (-56.20%)           1   →      1               
  │ │ └ sddk::wf_trans                                                      2.62 ms →   2.59 ms     (-0.88%)           1   →      1               
  │ │   └ sddk::wf_trans|pw                                                 2.61 ms →   2.59 ms     (-0.90%)           1   →      1               
- │ └ sirius::Beta_projectors_base::dismiss                               489.00 ns →  12.33 μs  (+2422.09%)           1   →      1               
- ├ sirius::DFT_ground_state::scf_loop                                     62.21 s  →  71.80 s     (+15.42%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.44 ms →   2.45 ms     (+0.60%)          19   →     19               
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.26 s  →   3.10 s      (-4.72%)          19   →     23      (+21.05%)
- │ │ ├ sirius::Hamiltonian0                                                4.93 ms →   5.44 ms    (+10.33%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Local_operator                                            4.23 ms →   4.61 ms     (+8.85%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sirius::Smooth_periodic_function                              534.84 μs → 563.36 μs     (+5.33%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.61 ms →   2.81 ms     (+7.77%)          19   →     23      (+21.05%)
- │ │ │ ├ sirius::Non_local_operator                                      203.38 μs → 280.85 μs    (+38.09%)          38   →     46      (+21.05%)
! │ │ │ ├ sirius::D_operator::initialize                                  117.82 μs → 106.36 μs     (-9.73%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::Q_operator::initialize                                   93.30 μs →  91.15 μs     (-2.30%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Band::solve                                                 2.03 s  →   1.88 s      (-7.71%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Hamiltonian_k                                           223.69 μs → 202.64 μs     (-9.41%)          19   →     23      (+21.05%)
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                             215.15 μs → 192.76 μs    (-10.41%)          19   →     23      (+21.05%)
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           6.21 μs →   7.50 μs    (+20.70%)          19   →     23      (+21.05%)
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.97 s  →   1.76 s     (-10.88%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             77.13 ms →  69.99 ms     (-9.26%)          19   →     23      (+21.05%)
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.01 ms →   6.57 ms    (-17.90%)         114   →    138      (+21.05%)
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            18.26 ms →  15.31 ms    (-16.14%)          19   →     23      (+21.05%)
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       460.24 μs → 495.23 μs     (+7.60%)          19   →     23      (+21.05%)
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.29 ms →   6.97 ms    (-15.95%)          38   →     46      (+21.05%)
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.87 s  →   1.66 s     (-11.11%)          19   →     23      (+21.05%)
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             51.22 ms →  68.61 ms    (+33.96%)         356   →    298      (-16.29%)
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                            29.09 ms →  44.28 ms    (+52.23%)         356   →    298      (-16.29%)
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.14 μs →   2.15 μs     (+0.69%)         356   →    298      (-16.29%)
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.83 μs →   1.82 μs     (-0.15%)         356   →    298      (-16.29%)
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     487.59 ns → 435.95 ns    (-10.59%)         356   →    298      (-16.29%)
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    656.73 ns → 610.46 ns     (-7.05%)         356   →    298      (-16.29%)
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.80 ms →   3.08 ms    (+10.09%)         356   →    298      (-16.29%)
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.17 ms →   3.71 ms    (+16.90%)         356   →    298      (-16.29%)
! │ │ │ │   │ └ sirius::Non_local_operator::apply                           8.07 ms →   8.77 ms     (+8.58%)         712   →    596      (-16.29%)
! │ │ │ │   ├ sddk::orthogonalize                                           6.75 ms →   6.55 ms     (-3.02%)         356   →    298      (-16.29%)
! │ │ │ │   │ ├ sddk::wf_inner                                              1.11 ms →   1.14 ms     (+2.62%)         693   →    573      (-17.32%)
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                     56.74 ns →  40.23 ns    (-29.11%)         693   →    573      (-17.32%)
! │ │ │ │   │ │ ├ sddk::wf_inner|pw                                       946.23 μs → 975.22 μs     (+3.06%)         693   →    573      (-17.32%)
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                                48.07 ns →  34.00 ns    (-29.28%)         693   →    573      (-17.32%)
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 116.27 μs → 174.98 μs    (+50.50%)         356   →    298      (-16.29%)
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                               2.34 ms →   1.94 ms    (-16.92%)         356   →    298      (-16.29%)
! │ │ │ │   │ └ sddk::wf_trans                                              2.26 ms →   2.43 ms     (+7.52%)         337   →    275      (-18.40%)
! │ │ │ │   │   └ sddk::wf_trans|pw                                       751.39 μs → 807.91 μs     (+7.52%)        1.01 K →    825      (-18.40%)
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.42 ms →   1.46 ms     (+3.13%)         356   →    298      (-16.29%)
! │ │ │ │   │ └ sddk::wf_inner                                              1.35 ms →   1.36 ms     (+0.98%)         356   →    298      (-16.29%)
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                     40.21 ns →  33.30 ns    (-17.19%)         356   →    298      (-16.29%)
! │ │ │ │   │   ├ sddk::wf_inner|pw                                         1.18 ms →   1.20 ms     (+1.15%)         356   →    298      (-16.29%)
- │ │ │ │   │   └ sddk::wf_inner|scale_back                                40.16 ns →  64.92 ns    (+61.65%)         356   →    298      (-16.29%)
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     36.53 ms →  47.07 ms    (+28.86%)         356   →    298      (-16.29%)
- │ │ │ │   ├ sirius::residuals                                             2.73 ms →   3.07 ms    (+12.27%)         340   →    289      (-15.00%)
- │ │ │ │   │ ├ sddk::wf_trans                                              1.36 ms →   1.79 ms    (+31.34%)         337   →    278      (-17.51%)
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                       678.17 μs → 891.15 μs    (+31.41%)         674   →    556      (-17.51%)
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.28 ms →   1.27 ms     (-0.86%)         337   →    278      (-17.51%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       7.19 ms →   7.27 ms     (+1.09%)          54   →     57       (+5.56%)
  │ │ │ │     └ sddk::wf_trans                                              4.31 ms →   4.50 ms     (+4.46%)          89   →     91       (+2.25%)
  │ │ │ │       └ sddk::wf_trans|pw                                         3.09 ms →   3.28 ms     (+5.95%)         124   →    125       (+0.81%)
! │ │ │ ├ sirius::Beta_projectors_base::dismiss                           350.53 ns → 369.96 ns     (+5.54%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::K_point_set::sync_band_energies                          19.61 μs →  20.15 μs     (+2.75%)          19   →     23      (+21.05%)
! │ │ ├ sirius::K_point_set::find_band_occupancies                          1.52 ms →   1.48 ms     (-2.75%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Density::generate                                         571.17 ms → 568.06 ms     (-0.55%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Density::generate_valence                               400.35 ms → 380.12 ms     (-5.05%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.89 μs →   8.31 μs     (-6.47%)          19   →     23      (+21.05%)
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           8.35 μs →   7.71 μs     (-7.70%)          19   →     23      (+21.05%)
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   38.21 ms →  42.95 ms    (+12.40%)          19   →     23      (+21.05%)
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.44 μs →   7.61 μs     (+2.27%)          19   →     23      (+21.05%)
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        6.39 ms →  23.43 ms   (+266.52%)          19   →     23      (+21.05%)
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          30.76 ms →  18.45 ms    (-40.02%)          19   →     23      (+21.05%)
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       520.11 ns → 628.65 ns    (+20.87%)          19   →     23      (+21.05%)
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  108.06 ms →  96.70 ms    (-10.51%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.88 ms →   2.00 ms     (+6.65%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::Density::augment                                      210.02 ms → 199.44 ms     (-5.04%)          19   →     23      (+21.05%)
! │ │ │ │   └ sirius::Density::generate_rho_aug                           209.79 ms → 199.22 ms     (-5.04%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Field4D::symmetrize                                     142.64 ms → 155.43 ms     (+8.97%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::symmetrize_function|fpw                               142.64 ms → 155.43 ms     (+8.97%)          19   →     23      (+21.05%)
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             58.61 ms →  72.04 ms    (+22.90%)          19   →     23      (+21.05%)
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        70.75 ms →  70.07 ms     (-0.96%)          19   →     23      (+21.05%)
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.63 ms →  12.67 ms     (+0.33%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.60 ms →  24.03 ms     (+1.82%)          19   →     23      (+21.05%)
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   4.58 ms →   8.47 ms    (+84.91%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Density::mix                                              132.68 ms → 137.13 ms     (+3.36%)          19   →     23      (+21.05%)
+ │ │ │ ├ sirius::Density::mixer_input                                    917.83 μs → 745.88 μs    (-18.73%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Periodic_function|inner                                   4.89 ms →   4.89 ms     (-0.01%)         229   →    289      (+26.20%)
! │ │ │ │ └ sirius::Periodic_function|inner_local                           4.81 ms →   4.82 ms     (+0.24%)         229   →    289      (+26.20%)
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.81 ms →   4.82 ms     (+0.24%)         229   →    289      (+26.20%)
- │ │ │ └ sirius::Density::mixer_output                                     4.83 ms →   6.11 ms    (+26.65%)          19   →     23      (+21.05%)
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 4.20 ms →   5.37 ms    (+27.83%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Potential::generate                                       362.69 ms → 365.20 ms     (+0.69%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Potential::poisson                                       42.35 ms →  45.09 ms     (+6.48%)          19   →     23      (+21.05%)
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 3.47 ms →   3.38 ms     (-2.46%)          19   →     23      (+21.05%)
+ │ │ │ │ └ sirius::Periodic_function|inner                                 5.96 ms →   5.23 ms    (-12.35%)          19   →     23      (+21.05%)
! │ │ │ │   └ sirius::Periodic_function|inner_local                         4.63 ms →   4.64 ms     (+0.30%)          19   →     23      (+21.05%)
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.63 ms →   4.64 ms     (+0.30%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Periodic_function::add                                  785.69 μs → 760.75 μs     (-3.17%)          38   →     46      (+21.05%)
! │ │ │ ├ sirius::Potential::xc                                            44.49 ms →  45.38 ms     (+2.00%)          19   →     23      (+21.05%)
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.31 ms →  44.20 ms     (+2.05%)          19   →     23      (+21.05%)
! │ │ │ │   ├ sirius::Smooth_periodic_function                            685.56 μs → 685.21 μs     (-0.05%)          38   →     46      (+21.05%)
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.10 ms →   5.04 ms    (+22.79%)          19   →     23      (+21.05%)
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.90 ms →   3.35 ms    (-14.19%)          19   →     23      (+21.05%)
! │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.98 ms → 268.44 ms     (-0.20%)          19   →     23      (+21.05%)
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             270.11 ns → 321.30 ns    (+18.96%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Field4D::symmetrize                                        97.04 ms →  95.82 ms     (-1.26%)          19   →     23      (+21.05%)
! │ │ │ └ sirius::symmetrize_function|fpw                                  97.04 ms →  95.82 ms     (-1.26%)          19   →     23      (+21.05%)
! │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.48 ms →  13.27 ms     (-1.57%)          19   →     23      (+21.05%)
! │ │ │   ├ sirius::symmetrize_function|fpw|local                          70.36 ms →  69.31 ms     (-1.50%)          19   →     23      (+21.05%)
! │ │ │   └ sddk::Gvec_shells::remap_backward                              12.58 ms →  12.61 ms     (+0.24%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.24 ms →   4.12 ms     (-2.85%)          19   →     23      (+21.05%)
! │ │ ├ sirius::Periodic_function|inner                                     4.68 ms →   4.65 ms     (-0.76%)         133   →    161      (+21.05%)
! │ │ │ └ sirius::Periodic_function|inner_local                             4.60 ms →   4.57 ms     (-0.77%)         133   →    161      (+21.05%)
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.60 ms →   4.57 ms     (-0.78%)         133   →    161      (+21.05%)
! │ │ ├ sirius::Smooth_periodic_function|inner                              4.94 ms →   4.95 ms     (+0.03%)          57   →     69      (+21.05%)
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.93 ms →   4.94 ms     (+0.23%)          57   →     69      (+21.05%)
! │ │ ├ sirius::Periodic_function::integrate                                4.52 ms →   4.53 ms     (+0.25%)          19   →     23      (+21.05%)
! │ │ └ sirius::Density::get_magnetisation                                 72.31 μs →  79.34 μs     (+9.72%)          19   →     23      (+21.05%)
! │ │   └ sirius::Density::compute_atomic_mag_mom                          68.35 μs →  74.46 μs     (+8.95%)          19   →     23      (+21.05%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.43 ms →   5.26 ms     (-3.14%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.85 ms →   4.55 ms     (-6.03%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.84 ms →   4.55 ms     (-6.12%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.84 ms →   4.55 ms     (-6.10%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                5.24 ms →   4.94 ms     (-5.72%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        5.23 ms →   4.93 ms     (-5.76%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.77 ms →   4.86 ms     (+1.95%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.76 ms →   4.54 ms     (-4.64%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.76 ms →   4.54 ms     (-4.65%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  5.26 ms →   4.92 ms     (-6.44%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          5.25 ms →   4.91 ms     (-6.44%)           1   →      1               
- └ sirius::finalize                                                      156.95 ms → 235.34 ms    (+49.94%)           1   →      1               
```
