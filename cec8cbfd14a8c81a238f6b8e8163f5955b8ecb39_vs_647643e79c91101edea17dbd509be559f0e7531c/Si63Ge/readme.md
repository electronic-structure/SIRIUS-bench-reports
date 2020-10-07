# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   71.67 s  →  72.28 s      (+0.85%)           1   →      1               
  ├ sirius::initialize                                                      2.90 s  →   2.98 s      (+2.74%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.62 s  →   3.92 s      (+8.23%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               453.44 μs →  26.58 ms  (+5761.91%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       114.63 ms → 373.75 ms   (+226.06%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            48.74 ms → 178.78 ms   (+266.84%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          17.06 ms →  16.09 ms     (-5.70%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.62 ms →   3.66 ms     (+0.99%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  13.35 ms →  12.34 ms     (-7.56%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     13.28 ms →  12.27 ms     (-7.64%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.75 ms →   2.77 ms     (+0.69%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            475.45 μs → 498.72 μs     (+4.89%)           1   →      1               
- │ │       └ sirius::Unit_cell_symmetry|mag                               15.81 μs →  17.78 μs    (+12.45%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.45 s  →   3.42 s      (-0.99%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.97 ms →   6.89 ms     (-1.16%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.64 ms →   3.55 ms     (-2.47%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.27 ms →   3.29 ms     (+0.57%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.23 ms →   3.24 ms     (+0.50%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.69 ms →   2.69 ms     (+0.03%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            497.08 μs → 510.06 μs     (+2.61%)           1   →      1               
- │   │     └ sirius::Unit_cell_symmetry|mag                               13.71 μs →  15.52 μs    (+13.16%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      213.02 ms → 214.62 ms     (+0.75%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.25 ms →  15.14 ms     (-0.69%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.25 ms →  13.26 ms     (+0.07%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.36 ms →  56.35 ms     (-0.02%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.21 ms →  45.19 ms     (-0.06%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.26 ms →  60.48 ms     (+0.35%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.33 ms →  93.89 ms     (+0.59%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.67 ms →  70.29 ms     (+0.89%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 106.37 ms → 104.22 ms     (-2.02%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.96 ms →   1.99 ms     (+1.64%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 569.89 ms → 553.69 ms     (-2.84%)           2   →      2               
- ├ sirius::K_point_set::create_k_mesh                                     87.21 ms → 144.59 ms    (+65.81%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.17 μs →   1.02 μs    (-52.82%)           4   →      4               
- │ └ sirius::K_point_set::initialize                                      87.14 ms → 144.51 ms    (+65.84%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.21 ms →  28.21 ms     (-0.00%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  11.05 ms →  11.06 ms     (+0.13%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                5.00 ms →   4.97 ms     (-0.47%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                             11.37 μs →  12.42 μs     (+9.24%)           1   →      1               
  │     └ sirius::K_point::update                                          14.26 ms →  14.25 ms     (-0.09%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.26 ms →  10.26 ms     (-0.08%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.33 ms →   8.29 ms     (-0.47%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.57 ms →   2.60 ms     (+1.01%)           2   →      2               
  ├ sirius::Potential                                                      49.61 ms →  50.12 ms     (+1.02%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.91 ms →   2.92 ms     (+0.13%)           6   →      6               
  │ └ sirius::Potential::update                                            31.52 ms →  32.03 ms     (+1.64%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        31.10 ms →  31.61 ms     (+1.64%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.66 ms →  26.75 ms     (+0.35%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   3.89 ms →   4.32 ms    (+10.93%)           1   →      1               
  ├ sirius::Density                                                        36.14 ms →  38.17 ms     (+5.61%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.81 ms →   2.84 ms     (+1.02%)           2   →      2               
  │ └ sirius::Density::update                                              30.38 ms →  32.35 ms     (+6.47%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               30.09 ms →  32.11 ms     (+6.71%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.43 μs →  77.02 μs     (-0.54%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.73 ms →  26.73 ms     (-0.00%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   2.93 ms →   4.97 ms    (+69.50%)           1   →      1               
  ├ sirius::Density::initial_density                                       56.17 ms →  57.27 ms     (+1.95%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                   27.85 ms →  29.18 ms     (+4.78%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       4.18 ms →   4.86 ms    (+16.44%)           2   →      2               
+ │ └ sirius::Periodic_function::integrate                                  6.00 ms →   4.92 ms    (-17.92%)           1   →      1               
  ├ sirius::Potential::generate                                           361.83 ms → 364.31 ms     (+0.68%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           34.67 ms →  37.11 ms     (+7.02%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.25 ms →   3.28 ms     (+0.84%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     5.65 ms →   5.12 ms     (-9.33%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.87 ms →   4.84 ms     (-0.63%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.86 ms →   4.83 ms     (-0.60%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      816.64 μs → 754.74 μs     (-7.58%)           2   →      2               
  │ ├ sirius::Potential::xc                                                50.84 ms →  51.57 ms     (+1.42%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               49.68 ms →  50.36 ms     (+1.37%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.56 ms →   2.56 ms     (-0.19%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.26 ms →   4.50 ms     (+5.43%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.92 ms →   3.62 ms     (-7.86%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.39 ms → 269.09 ms     (-0.11%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 312.00 ns → 137.00 ns    (-56.09%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    6.96 ms →   6.29 ms     (-9.62%)           1   →      1               
  │ ├ sirius::Local_operator                                                6.44 ms →   5.81 ms     (-9.74%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.76 ms →   2.75 ms     (-0.54%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.91 ms →   2.30 ms    (-21.09%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           73.44 μs →  72.71 μs     (-0.99%)           2   →      2               
+ │ ├ sirius::D_operator::initialize                                      173.40 μs → 124.32 μs    (-28.31%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                      109.87 μs → 137.87 μs    (+25.49%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.28 s  →   1.29 s      (+0.46%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                47.74 ms →  46.98 ms     (-1.60%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 354.47 μs → 300.96 μs    (-15.10%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              47.38 ms →  46.67 ms     (-1.50%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.24 s  →   1.24 s      (+0.54%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               78.95 ms →  93.75 ms    (+18.75%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    43.31 ms →  47.02 ms     (+8.57%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             8.54 ms →   8.75 ms     (+2.40%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  335.76 ms → 381.74 ms    (+13.70%)           1   →      1               
- │ │ │ ├ sirius::Local_operator::apply_h                                 247.59 ms → 289.81 ms    (+17.05%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.49 μs →   3.60 μs     (+3.21%)           1   →      1               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.50 μs →   2.63 μs     (+4.96%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           523.00 ns → 374.00 ns    (-28.49%)           1   →      1               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          649.00 ns → 647.00 ns     (-0.31%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.20 ms →   3.13 ms     (-2.22%)           1   →      1               
- │ │ │ ├ sirius::Beta_projectors_base::inner                              21.27 ms →  38.30 ms    (+80.02%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                                31.82 ms →  25.23 ms    (-20.72%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                    14.30 ms →   5.34 ms    (-62.66%)           2   →      2               
+ │ │ │ └ sddk::inner                                                      14.09 ms →   5.11 ms    (-63.75%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              25.35 μs →  26.20 μs     (+3.35%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          236.75 ms → 204.47 ms    (-13.63%)           1   →      1               
  │ │ └ sddk::transform                                                     2.84 ms →   2.84 ms     (+0.24%)           1   →      1               
  │ │   ├ sddk::transform|init                                             14.67 μs →  15.31 μs     (+4.35%)           1   →      1               
+ │ │   └ sddk::transform|local                                            19.02 μs →  16.69 μs    (-12.23%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                               402.00 ns → 421.00 ns     (+4.73%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     62.13 s  →  62.33 s      (+0.31%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.43 ms →   2.42 ms     (-0.36%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.26 s  →   3.25 s      (-0.25%)          19   →     19               
  │ │ ├ sirius::Hamiltonian0                                                5.18 ms →   5.33 ms     (+2.90%)          19   →     19               
  │ │ │ ├ sirius::Local_operator                                            4.47 ms →   4.65 ms     (+4.06%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              553.44 μs → 559.58 μs     (+1.11%)          19   →     19               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.84 ms →   2.84 ms     (+0.03%)          19   →     19               
  │ │ │ ├ sirius::Non_local_operator                                      214.47 μs → 195.05 μs     (-9.05%)          38   →     38               
  │ │ │ ├ sirius::D_operator::initialize                                  113.30 μs → 113.18 μs     (-0.10%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                   91.98 μs →  96.10 μs     (+4.47%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.03 s  →   2.03 s      (+0.16%)          19   →     19               
  │ │ │ ├ sirius::Hamiltonian_k                                           208.46 μs → 208.89 μs     (+0.21%)          19   →     19               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             199.47 μs → 198.62 μs     (-0.43%)          19   →     19               
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           6.30 μs →   7.17 μs    (+13.94%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.97 s  →   1.97 s      (+0.34%)          19   →     19               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             79.05 ms →  79.19 ms     (+0.17%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          8.13 ms →   7.99 ms     (-1.75%)         114   →    114               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            14.84 ms →  14.78 ms     (-0.40%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       485.40 μs → 491.60 μs     (+1.28%)          19   →     19               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         7.00 ms →   6.95 ms     (-0.65%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.86 s  →   1.87 s      (+0.36%)          19   →     19               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             54.98 ms →  55.79 ms     (+1.48%)         356   →    356               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            33.70 ms →  34.32 ms     (+1.85%)         356   →    356               
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.72 μs →   2.05 μs    (+19.52%)         356   →    356               
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.44 μs →   1.75 μs    (+21.00%)         356   →    356               
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     356.03 ns → 452.89 ns    (+27.21%)         356   →    356               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    498.83 ns → 606.13 ns    (+21.51%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.89 ms →   2.96 ms     (+2.70%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.16 ms →   3.22 ms     (+1.77%)         356   →    356               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           7.61 ms →   7.64 ms     (+0.35%)         712   →    712               
  │ │ │ │   ├ sddk::orthogonalize                                           5.71 ms →   5.38 ms     (-5.80%)         356   →    356               
+ │ │ │ │   │ ├ sddk::inner                                               883.79 μs → 744.34 μs    (-15.78%)         693   →    693               
- │ │ │ │   │ │ └ sddk::inner|local                                        22.00 μs →  24.67 μs    (+12.15%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 143.01 μs → 141.40 μs     (-1.12%)         356   →    356               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               1.87 ms →   1.72 ms     (-7.74%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             2.09 ms →   2.18 ms     (+4.35%)         337   →    337               
- │ │ │ │   │   ├ sddk::transform|init                                     17.40 μs →  19.84 μs    (+14.04%)         337   →    337               
- │ │ │ │   │   └ sddk::transform|local                                     7.31 μs →   8.22 μs    (+12.46%)        1.01 K →   1.01 K             
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.11 ms →   1.13 ms     (+1.82%)         356   →    356               
  │ │ │ │   │ └ sddk::inner                                                 1.04 ms →   1.06 ms     (+1.90%)         356   →    356               
- │ │ │ │   │   └ sddk::inner|local                                        21.29 μs →  24.19 μs    (+13.66%)         356   →    356               
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     33.83 ms →  34.07 ms     (+0.73%)         356   →    356               
+ │ │ │ │   ├ sirius::residuals                                             2.77 ms →   2.46 ms    (-11.45%)         340   →    340               
  │ │ │ │   │ ├ sddk::transform                                             1.33 ms →   1.28 ms     (-4.33%)         337   →    337               
- │ │ │ │   │ │ ├ sddk::transform|init                                     14.62 μs →  17.27 μs    (+18.10%)         337   →    337               
- │ │ │ │   │ │ └ sddk::transform|local                                     9.35 μs →  10.42 μs    (+11.44%)         674   →    674               
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.36 ms →   1.10 ms    (-18.73%)         337   →    337               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       7.90 ms →   7.35 ms     (-6.96%)          54   →     54               
  │ │ │ │     └ sddk::transform                                             4.75 ms →   4.41 ms     (-7.03%)          89   →     89               
  │ │ │ │       ├ sddk::transform|init                                     10.83 μs →  11.76 μs     (+8.62%)          89   →     89               
  │ │ │ │       └ sddk::transform|local                                     9.69 μs →   9.82 μs     (+1.26%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           543.63 ns → 534.11 ns     (-1.75%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.48 μs →  19.42 μs     (-0.29%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.56 ms →   1.59 ms     (+1.89%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         570.76 ms → 567.47 ms     (-0.58%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               403.97 ms → 438.66 ms     (+8.59%)          19   →     19               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.54 μs →  10.89 μs    (+44.46%)          19   →     19               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           6.91 μs →   9.97 μs    (+44.32%)          19   →     19               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   39.78 ms →  36.93 ms     (-7.17%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         6.70 μs →  10.59 μs    (+57.99%)          19   →     19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                       22.72 ms →  22.06 ms     (-2.91%)          19   →     19               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          16.02 ms →  13.82 ms    (-13.72%)          19   →     19               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       568.37 ns → 556.53 ns     (-2.08%)          19   →     19               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                   99.12 ms → 102.00 ms     (+2.90%)          19   →     19               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 2.15 ms →   2.60 ms    (+21.23%)          19   →     19               
- │ │ │ │ └ sirius::Density::augment                                      226.15 ms → 265.52 ms    (+17.41%)          19   →     19               
- │ │ │ │   └ sirius::Density::generate_rho_aug                           225.94 ms → 265.31 ms    (+17.43%)          19   →     19               
+ │ │ │ ├ sirius::Field4D::symmetrize                                     135.19 ms →  99.34 ms    (-26.52%)          19   →     19               
+ │ │ │ │ └ sirius::symmetrize_function|fpw                               135.19 ms →  99.33 ms    (-26.52%)          19   →     19               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             51.20 ms →  16.57 ms    (-67.63%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        69.10 ms →  69.47 ms     (+0.54%)          19   →     19               
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                            14.25 ms →  12.66 ms    (-11.19%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.79 ms →  23.54 ms     (-1.03%)          19   →     19               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   7.81 ms →   5.93 ms    (-24.08%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              138.80 ms → 131.94 ms     (-4.94%)          19   →     19               
  │ │ │ ├ sirius::Density::mixer_input                                    312.73 μs → 292.51 μs     (-6.47%)          19   →     19               
+ │ │ │ ├ sirius::Periodic_function|inner                                   5.38 ms →   4.77 ms    (-11.22%)         229   →    229               
+ │ │ │ │ └ sirius::Periodic_function|inner_local                           5.19 ms →   4.62 ms    (-10.92%)         229   →    229               
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  5.19 ms →   4.62 ms    (-10.92%)         229   →    229               
  │ │ │ └ sirius::Density::mixer_output                                     6.37 ms →   6.33 ms     (-0.51%)          19   →     19               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.61 ms →   5.57 ms     (-0.70%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       354.76 ms → 357.50 ms     (+0.77%)          19   →     19               
  │ │ │ ├ sirius::Potential::poisson                                       34.40 ms →  37.20 ms     (+8.12%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 3.24 ms →   3.30 ms     (+1.81%)          19   →     19               
  │ │ │ │ └ sirius::Periodic_function|inner                                 5.54 ms →   5.09 ms     (-8.10%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.86 ms →   4.83 ms     (-0.64%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.86 ms →   4.83 ms     (-0.64%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  804.06 μs → 751.48 μs     (-6.54%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            44.37 ms →  45.11 ms     (+1.68%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.20 ms →  43.93 ms     (+1.69%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            680.14 μs → 685.00 μs     (+0.71%)          38   →     38               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.22 ms →   4.64 ms     (+9.90%)          19   →     19               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.92 ms →   3.55 ms     (-9.44%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   269.07 ms → 268.72 ms     (-0.13%)          19   →     19               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             214.16 ns → 130.63 ns    (-39.00%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        99.51 ms →  98.42 ms     (-1.09%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  99.51 ms →  98.42 ms     (-1.09%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               15.97 ms →  16.10 ms     (+0.78%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          68.70 ms →  69.11 ms     (+0.60%)          19   →     19               
+ │ │ │   └ sddk::Gvec_shells::remap_backward                              14.21 ms →  12.59 ms    (-11.40%)          19   →     19               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.24 ms →   5.90 ms    (+39.32%)          19   →     19               
+ │ │ ├ sirius::Periodic_function|inner                                     5.36 ms →   4.73 ms    (-11.83%)         133   →    133               
+ │ │ │ └ sirius::Periodic_function|inner_local                             5.13 ms →   4.56 ms    (-11.12%)         133   →    133               
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                    5.13 ms →   4.56 ms    (-11.12%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.77 ms →   4.74 ms     (-0.62%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.75 ms →   4.73 ms     (-0.42%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.77 ms →   4.54 ms     (-4.84%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 77.22 μs →  76.74 μs     (-0.62%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          71.77 μs →  71.69 μs     (-0.11%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.60 ms →   5.62 ms     (+0.34%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       5.17 ms →   4.73 ms     (-8.53%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               5.14 ms →   4.70 ms     (-8.45%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      5.14 ms →   4.70 ms     (-8.44%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.76 ms →   4.83 ms     (+1.51%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.74 ms →   4.82 ms     (+1.82%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         5.19 ms →   4.80 ms     (-7.66%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 5.19 ms →   4.79 ms     (-7.66%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        5.19 ms →   4.79 ms     (-7.66%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.72 ms →   4.96 ms     (+5.01%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.71 ms →   4.96 ms     (+5.27%)           1   →      1               
  └ sirius::finalize                                                      763.63 ms → 747.89 ms     (-2.06%)           1   →      1               
```
