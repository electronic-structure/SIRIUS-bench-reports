# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   71.67 s  →  71.82 s      (+0.21%)           1   →      1               
  ├ sirius::initialize                                                      2.90 s  →   2.92 s      (+0.47%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.64 s  →   3.68 s      (+1.23%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                 3.00 ms →   3.75 ms    (+25.26%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       148.07 ms → 137.09 ms     (-7.41%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                            61.46 ms →  58.53 ms     (-4.77%)           2   →      2               
+ │ │ └ sirius::Unit_cell::update                                          25.05 ms →  19.94 ms    (-20.39%)           1   →      1               
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.89 ms →   5.25 ms    (+35.06%)           1   →      1               
+ │ │   └ sirius::Unit_cell::get_symmetry                                  21.11 ms →  14.65 ms    (-30.62%)           1   →      1               
+ │ │     └ sirius::Unit_cell_symmetry                                     21.03 ms →  14.58 ms    (-30.67%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.81 ms →   2.73 ms     (-2.90%)           1   →      1               
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                              3.14 ms → 506.36 μs    (-83.88%)           1   →      1               
+ │ │       └ sirius::Unit_cell_symmetry|mag                               18.81 μs →  15.73 μs    (-16.37%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.44 s  →   3.45 s      (+0.35%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           7.00 ms →   6.98 ms     (-0.24%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.65 ms →   3.64 ms     (-0.15%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.30 ms →   3.30 ms     (-0.22%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.26 ms →   3.25 ms     (-0.23%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.70 ms →   2.71 ms     (+0.49%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            520.53 μs → 502.07 μs     (-3.55%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               14.87 μs →  14.29 μs     (-3.91%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      213.29 ms → 213.50 ms     (+0.10%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.22 ms →  15.14 ms     (-0.49%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.26 ms →  13.25 ms     (-0.07%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.41 ms →  56.34 ms     (-0.12%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.13 ms →  47.46 ms     (+5.15%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.32 ms →  60.44 ms     (+0.20%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.29 ms →  94.02 ms     (+0.79%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.88 ms →  70.40 ms     (+0.75%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 105.85 ms → 100.60 ms     (-4.96%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.95 ms →   1.98 ms     (+1.36%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 565.34 ms → 564.58 ms     (-0.13%)           2   →      2               
- ├ sirius::K_point_set::create_k_mesh                                     88.23 ms → 148.27 ms    (+68.04%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.51 μs →   1.72 μs    (-31.63%)           4   →      4               
- │ └ sirius::K_point_set::initialize                                      88.17 ms → 148.20 ms    (+68.09%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.52 ms →  28.67 ms     (+0.53%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  10.85 ms →  11.05 ms     (+1.81%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                4.93 ms →   4.96 ms     (+0.69%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                              7.88 μs →   7.75 μs     (-1.71%)           1   →      1               
  │     └ sirius::K_point::update                                          14.83 ms →  14.78 ms     (-0.35%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.91 ms →  10.82 ms     (-0.83%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.95 ms →   8.83 ms     (-1.27%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.51 ms →   2.57 ms     (+2.28%)           2   →      2               
  ├ sirius::Potential                                                      50.34 ms →  51.72 ms     (+2.75%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.93 ms →   2.91 ms     (-0.67%)           6   →      6               
  │ └ sirius::Potential::update                                            32.14 ms →  33.63 ms     (+4.64%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        31.75 ms →  33.22 ms     (+4.65%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.69 ms →  26.61 ms     (-0.31%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   4.51 ms →   6.09 ms    (+35.17%)           1   →      1               
  ├ sirius::Density                                                        37.66 ms →  39.98 ms     (+6.15%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.81 ms →   2.82 ms     (+0.40%)           2   →      2               
  │ └ sirius::Density::update                                              31.90 ms →  34.19 ms     (+7.18%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               31.67 ms →  33.98 ms     (+7.29%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.75 μs →  77.83 μs     (+0.10%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.95 ms →  26.56 ms     (-1.46%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   4.32 ms →   7.06 ms    (+63.15%)           1   →      1               
  ├ sirius::Density::initial_density                                       57.31 ms →  59.79 ms     (+4.34%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                   28.52 ms →  27.64 ms     (-3.11%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       4.55 ms →   6.51 ms    (+43.00%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  5.83 ms →   5.74 ms     (-1.66%)           1   →      1               
  ├ sirius::Potential::generate                                           363.30 ms → 365.70 ms     (+0.66%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           36.24 ms →  38.77 ms     (+6.97%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.87 ms →   7.13 ms    (+84.00%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     6.11 ms →   6.07 ms     (-0.57%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.86 ms →   4.84 ms     (-0.25%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.85 ms →   4.83 ms     (-0.25%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      802.38 μs → 764.91 μs     (-4.67%)           2   →      2               
  │ ├ sirius::Potential::xc                                                51.75 ms →  51.60 ms     (-0.29%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               50.55 ms →  50.38 ms     (-0.33%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.54 ms →   2.55 ms     (+0.50%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.84 ms →   5.00 ms     (+3.13%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.65 ms →   3.71 ms     (+1.61%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       268.63 ms → 268.63 ms     (-0.00%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                  61.00 ns → 205.00 ns   (+236.07%)           1   →      1               
- ├ sirius::Hamiltonian0                                                    6.36 ms →   8.59 ms    (+35.22%)           1   →      1               
- │ ├ sirius::Local_operator                                                5.87 ms →   7.53 ms    (+28.39%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.75 ms →   2.74 ms     (-0.40%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.35 ms →   3.73 ms    (+58.91%)           1   →      1               
- │ ├ sirius::Non_local_operator                                           75.04 μs → 394.06 μs   (+425.15%)           2   →      2               
+ │ ├ sirius::D_operator::initialize                                      123.12 μs → 110.11 μs    (-10.57%)           1   →      1               
+ │ └ sirius::Q_operator::initialize                                      128.92 μs →  92.02 μs    (-28.62%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.29 s  →   1.32 s      (+2.14%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                34.13 ms →  71.76 ms   (+110.26%)           1   →      1               
  │ │ ├ sirius::Local_operator::prepare_k                                 282.08 μs → 258.69 μs     (-8.29%)           1   →      1               
- │ │ └ sirius::Beta_projectors_base::prepare                              33.84 ms →  71.50 ms   (+111.27%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.25 s  →   1.24 s      (-0.81%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               83.64 ms → 106.53 ms    (+27.38%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    47.87 ms →  51.64 ms     (+7.87%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             7.33 ms →   7.35 ms     (+0.37%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  336.52 ms → 450.64 ms    (+33.91%)           1   →      1               
- │ │ │ ├ sirius::Local_operator::apply_h                                 247.29 ms → 357.83 ms    (+44.70%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.88 μs →   3.36 μs    (-13.38%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.92 μs →   2.49 μs    (-14.72%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           456.00 ns → 564.00 ns    (+23.68%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          629.00 ns →   1.21 μs    (+92.21%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.17 ms →   3.07 ms     (-2.99%)           1   →      1               
- │ │ │ ├ sirius::Beta_projectors_base::inner                              21.30 ms →  38.96 ms    (+82.87%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                                32.36 ms →  25.37 ms    (-21.61%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                    14.26 ms →   6.42 ms    (-54.97%)           2   →      2               
+ │ │ │ └ sddk::inner                                                      14.05 ms →   6.21 ms    (-55.80%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              25.02 μs →  26.36 μs     (+5.36%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          233.08 ms → 135.22 ms    (-41.99%)           1   →      1               
  │ │ └ sddk::transform                                                     2.82 ms →   2.83 ms     (+0.41%)           1   →      1               
  │ │   ├ sddk::transform|init                                             14.71 μs →  13.66 μs     (-7.18%)           1   →      1               
+ │ │   └ sddk::transform|local                                            19.60 μs →  16.36 μs    (-16.53%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               547.00 ns → 396.00 ns    (-27.61%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     62.11 s  →  62.10 s      (-0.02%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.43 ms →   2.44 ms     (+0.43%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.25 s  →   3.25 s      (-0.13%)          19   →     19               
  │ │ ├ sirius::Hamiltonian0                                                5.36 ms →   5.53 ms     (+3.15%)          19   →     19               
  │ │ │ ├ sirius::Local_operator                                            4.67 ms →   4.81 ms     (+3.01%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              545.91 μs → 549.14 μs     (+0.59%)          19   →     19               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 3.04 ms →   2.97 ms     (-2.05%)          19   →     19               
- │ │ │ ├ sirius::Non_local_operator                                      195.06 μs → 216.75 μs    (+11.12%)          38   →     38               
  │ │ │ ├ sirius::D_operator::initialize                                  117.40 μs → 111.19 μs     (-5.29%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                   97.82 μs →  93.59 μs     (-4.32%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.02 s  →   2.03 s      (+0.63%)          19   →     19               
  │ │ │ ├ sirius::Hamiltonian_k                                           201.15 μs → 199.64 μs     (-0.75%)          19   →     19               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             191.49 μs → 188.80 μs     (-1.41%)          19   →     19               
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           6.49 μs →   7.78 μs    (+19.92%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.95 s  →   1.97 s      (+0.97%)          19   →     19               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             71.09 ms →  79.56 ms    (+11.92%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.95 ms →   8.46 ms     (+6.40%)         114   →    114               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            16.26 ms →  15.41 ms     (-5.24%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       453.32 μs → 490.81 μs     (+8.27%)          19   →     19               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         7.69 ms →   7.29 ms     (-5.17%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.86 s  →   1.87 s      (+0.60%)          19   →     19               
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             45.47 ms →  56.23 ms    (+23.66%)         356   →    356               
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                            27.65 ms →  35.58 ms    (+28.68%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.06 μs →   2.06 μs     (-0.08%)         356   →    356               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.74 μs →   1.79 μs     (+2.54%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     470.53 ns → 473.94 ns     (+0.73%)         356   →    356               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    650.51 ns → 686.06 ns     (+5.46%)         356   →    356               
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.76 ms →   3.09 ms    (+11.86%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.06 ms →   3.30 ms     (+7.71%)         356   →    356               
- │ │ │ │   │ └ sirius::Non_local_operator::apply                           5.99 ms →   7.12 ms    (+18.91%)         712   →    712               
  │ │ │ │   ├ sddk::orthogonalize                                           5.25 ms →   5.02 ms     (-4.40%)         356   →    356               
  │ │ │ │   │ ├ sddk::inner                                               707.81 μs → 683.06 μs     (-3.50%)         693   →    693               
  │ │ │ │   │ │ └ sddk::inner|local                                        25.07 μs →  26.06 μs     (+3.95%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 131.14 μs → 132.85 μs     (+1.31%)         356   →    356               
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                               1.89 ms →   1.62 ms    (-14.05%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             1.96 ms →   2.04 ms     (+4.34%)         337   →    337               
  │ │ │ │   │   ├ sddk::transform|init                                     19.59 μs →  21.27 μs     (+8.56%)         337   →    337               
  │ │ │ │   │   └ sddk::transform|local                                     8.34 μs →   8.69 μs     (+4.23%)        1.01 K →   1.01 K             
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.12 ms → 962.96 μs    (-13.74%)         356   →    356               
+ │ │ │ │   │ └ sddk::inner                                                 1.05 ms → 891.77 μs    (-14.77%)         356   →    356               
  │ │ │ │   │   └ sddk::inner|local                                        24.43 μs →  25.35 μs     (+3.76%)         356   →    356               
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     44.43 ms →  34.26 ms    (-22.89%)         356   →    356               
- │ │ │ │   ├ sirius::residuals                                             2.07 ms →   2.41 ms    (+16.49%)         340   →    340               
- │ │ │ │   │ ├ sddk::transform                                             1.16 ms →   1.29 ms    (+11.24%)         337   →    337               
  │ │ │ │   │ │ ├ sddk::transform|init                                     17.37 μs →  18.16 μs     (+4.50%)         337   →    337               
  │ │ │ │   │ │ └ sddk::transform|local                                    10.72 μs →  11.11 μs     (+3.60%)         674   →    674               
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               858.18 μs →   1.05 ms    (+22.32%)         337   →    337               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       6.69 ms →   7.11 ms     (+6.25%)          54   →     54               
  │ │ │ │     └ sddk::transform                                             4.01 ms →   4.26 ms     (+6.31%)          89   →     89               
  │ │ │ │       ├ sddk::transform|init                                     12.02 μs →  12.36 μs     (+2.79%)          89   →     89               
  │ │ │ │       └ sddk::transform|local                                    10.07 μs →  10.55 μs     (+4.72%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           547.32 ns → 531.00 ns     (-2.98%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.80 μs →  19.71 μs     (-0.47%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.52 ms →   1.58 ms     (+4.07%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         570.31 ms → 566.42 ms     (-0.68%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               392.16 ms → 383.68 ms     (-2.16%)          19   →     19               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.95 μs →  12.38 μs    (+55.71%)          19   →     19               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.29 μs →  11.41 μs    (+56.57%)          19   →     19               
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   20.04 ms →  46.03 ms   (+129.71%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         6.87 μs →  10.82 μs    (+57.59%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        3.34 ms →  24.12 ms   (+621.66%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          15.63 ms →  20.85 ms    (+33.41%)          19   →     19               
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       677.74 ns → 607.16 ns    (-10.41%)          19   →     19               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  125.19 ms →  93.52 ms    (-25.30%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.93 ms →   1.91 ms     (-0.98%)          19   →     19               
  │ │ │ │ └ sirius::Density::augment                                      210.09 ms → 196.58 ms     (-6.43%)          19   →     19               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           209.86 ms → 196.35 ms     (-6.44%)          19   →     19               
  │ │ │ ├ sirius::Field4D::symmetrize                                     144.97 ms → 152.07 ms     (+4.90%)          19   →     19               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               144.96 ms → 152.06 ms     (+4.90%)          19   →     19               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             63.07 ms →  68.71 ms     (+8.95%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        68.65 ms →  70.11 ms     (+2.13%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.61 ms →  12.60 ms     (-0.12%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.58 ms →  23.58 ms     (+0.00%)          19   →     19               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   9.60 ms →   7.09 ms    (-26.11%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              138.99 ms → 130.79 ms     (-5.89%)          19   →     19               
- │ │ │ ├ sirius::Density::mixer_input                                    296.62 μs → 784.23 μs   (+164.39%)          19   →     19               
+ │ │ │ ├ sirius::Periodic_function|inner                                   5.39 ms →   4.63 ms    (-14.10%)         229   →    229               
+ │ │ │ │ └ sirius::Periodic_function|inner_local                           5.19 ms →   4.62 ms    (-11.11%)         229   →    229               
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  5.19 ms →   4.62 ms    (-11.11%)         229   →    229               
+ │ │ │ └ sirius::Density::mixer_output                                     5.97 ms →   5.24 ms    (-12.11%)          19   →     19               
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.23 ms →   4.62 ms    (-11.58%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       356.93 ms → 359.91 ms     (+0.84%)          19   →     19               
  │ │ │ ├ sirius::Potential::poisson                                       36.76 ms →  39.36 ms     (+7.09%)          19   →     19               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 4.45 ms →   8.18 ms    (+83.93%)          19   →     19               
  │ │ │ │ └ sirius::Periodic_function|inner                                 6.12 ms →   5.60 ms     (-8.49%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.87 ms →   4.83 ms     (-0.72%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.86 ms →   4.83 ms     (-0.72%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  775.23 μs → 801.04 μs     (+3.33%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            44.55 ms →  45.44 ms     (+2.00%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.37 ms →  44.27 ms     (+2.07%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            679.09 μs → 676.36 μs     (-0.40%)          38   →     38               
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.30 ms →   4.84 ms    (+12.48%)          19   →     19               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.87 ms →   3.76 ms     (-2.85%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.74 ms → 268.32 ms     (-0.16%)          19   →     19               
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             128.63 ns → 222.00 ns    (+72.59%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        97.25 ms →  96.38 ms     (-0.89%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  97.25 ms →  96.38 ms     (-0.89%)          19   →     19               
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                               15.96 ms →  13.24 ms    (-17.04%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          68.09 ms →  69.96 ms     (+2.75%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.57 ms →  12.56 ms     (-0.12%)          19   →     19               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.90 ms →   4.48 ms    (-24.07%)          19   →     19               
+ │ │ ├ sirius::Periodic_function|inner                                     5.38 ms →   4.65 ms    (-13.59%)         133   →    133               
+ │ │ │ └ sirius::Periodic_function|inner_local                             5.14 ms →   4.56 ms    (-11.29%)         133   →    133               
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                    5.14 ms →   4.56 ms    (-11.29%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.86 ms →   4.74 ms     (-2.55%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.75 ms →   4.73 ms     (-0.40%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.78 ms →   4.54 ms     (-4.93%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 77.26 μs →  77.27 μs     (+0.02%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          72.36 μs →  72.08 μs     (-0.39%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.61 ms →   5.61 ms     (+0.01%)           2   →      2               
+ │ ├ sirius::Periodic_function|inner                                       5.56 ms →   4.80 ms    (-13.69%)           6   →      6               
+ │ │ └ sirius::Periodic_function|inner_local                               5.54 ms →   4.80 ms    (-13.43%)           6   →      6               
+ │ │   └ sirius::Smooth_periodic_function|inner_local                      5.54 ms →   4.80 ms    (-13.43%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                5.11 ms →   4.98 ms     (-2.49%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        5.10 ms →   4.98 ms     (-2.51%)           3   →      3               
+ ├ sirius::Periodic_function|inner                                         5.50 ms →   4.93 ms    (-10.28%)           2   →      2               
+ │ └ sirius::Periodic_function|inner_local                                 5.49 ms →   4.78 ms    (-12.96%)           2   →      2               
+ │   └ sirius::Smooth_periodic_function|inner_local                        5.49 ms →   4.78 ms    (-12.96%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  5.14 ms →   5.01 ms     (-2.55%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          5.14 ms →   5.00 ms     (-2.58%)           1   →      1               
  └ sirius::finalize                                                      748.23 ms → 763.57 ms     (+2.05%)           1   →      1               
```
