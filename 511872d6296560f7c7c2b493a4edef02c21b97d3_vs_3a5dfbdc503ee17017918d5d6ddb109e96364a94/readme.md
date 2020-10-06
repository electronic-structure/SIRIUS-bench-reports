# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    8.11 s  →   8.06 s      (-0.55%)           1   →      1               
+ ├ sirius::initialize                                                      3.24 s  →   2.90 s     (-10.55%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  1.92 s  →   2.04 s      (+6.28%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               256.98 μs → 377.94 μs    (+47.07%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       258.33 ms → 370.11 ms    (+43.27%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            80.28 ms → 117.87 ms    (+46.83%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          17.47 ms →  16.47 ms     (-5.73%)           1   →      1               
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      300.19 μs → 246.24 μs    (-17.97%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  17.17 ms →  16.22 ms     (-5.51%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     17.14 ms →  16.19 ms     (-5.52%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.89 ms →   4.93 ms     (+0.80%)           1   →      1               
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                             62.49 μs →  53.98 μs    (-13.62%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               15.76 μs →  15.96 μs     (+1.25%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.63 s      (+0.48%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.26 ms →   5.24 ms     (-0.30%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       33.39 μs →  34.98 μs     (+4.77%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.22 ms →   5.20 ms     (-0.32%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.20 ms →   5.18 ms     (-0.29%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                5.09 ms →   5.07 ms     (-0.26%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                             50.88 μs →  50.80 μs     (-0.16%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               18.44 μs →  17.72 μs     (-3.89%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      271.94 ms → 271.53 ms     (-0.15%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.37 ms →  21.34 ms     (-0.13%)           2   →      2               
- │   ├ sirius::Radial_integrals|rho_pseudo                                19.18 ms →  22.29 ms    (+16.24%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.36 ms →  80.46 ms     (+0.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.66 ms →  61.66 ms     (+0.00%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.98 ms →  96.97 ms     (-0.01%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.28 ms →   4.31 ms     (+0.92%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.97 ms →   3.02 ms     (+1.39%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.08 ms →   4.13 ms     (+1.24%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                284.18 μs → 286.72 μs     (+0.89%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  94.01 ms →  95.55 ms     (+1.64%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.95 ms →   6.07 ms     (+1.99%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            752.25 ns → 740.75 ns     (-1.53%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.87 ms →   5.99 ms     (+1.97%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.63 ms →   5.74 ms     (+2.09%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.62 ms →   4.72 ms     (+2.26%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              264.69 μs → 269.64 μs     (+1.87%)           1   →      1               
- │     ├ sddk::matrix_storage::matrix_storage                              2.77 μs →   3.28 μs    (+18.50%)           1   →      1               
  │     └ sirius::K_point::update                                         784.98 μs → 795.86 μs     (+1.39%)           1   →      1               
  │       └ sirius::Beta_projectors                                       641.73 μs → 652.02 μs     (+1.60%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                385.69 μs → 384.61 μs     (-0.28%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      251.87 μs → 263.59 μs     (+4.65%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       29.58 μs →  29.15 μs     (-1.47%)           2   →      2               
  ├ sirius::Potential                                                       2.05 ms →   2.07 ms     (+1.03%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.10 μs →  27.20 μs     (-3.22%)           6   →      6               
  │ └ sirius::Potential::update                                             1.79 ms →   1.82 ms     (+1.77%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.77 ms →   1.81 ms     (+1.79%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.30 ms →   1.38 ms     (+5.95%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 389.84 μs → 340.20 μs    (-12.74%)           1   →      1               
+ ├ sirius::Density                                                         1.91 ms →   1.71 ms    (-10.45%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.35 μs →  29.22 μs     (+3.07%)           2   →      2               
+ │ └ sirius::Density::update                                               1.85 ms →   1.65 ms    (-10.88%)           1   →      1               
+ │   └ sirius::Density::generate_pseudo_core_charge_density                1.84 ms →   1.64 ms    (-10.91%)           1   →      1               
- │     ├ sirius::rho_core_ri_pseudo|values                                19.57 μs →  23.73 μs    (+21.21%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.33 ms →   1.40 ms     (+4.77%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 476.06 μs → 206.66 μs    (-56.59%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.84 ms →   2.90 ms     (+2.16%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                    1.15 ms →   1.40 ms    (+22.40%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                     339.38 μs → 245.11 μs    (-27.78%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                256.86 μs → 254.76 μs     (-0.81%)           1   →      1               
+ ├ sirius::Potential::generate                                            24.26 ms →  20.99 ms    (-13.46%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            2.02 ms →   1.89 ms     (-6.43%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   419.35 μs → 200.51 μs    (-52.18%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   268.71 μs → 269.24 μs     (+0.20%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           261.45 μs → 266.60 μs     (+1.97%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.93 μs → 266.31 μs     (+2.06%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       10.64 μs →  10.47 μs     (-1.56%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.09 ms →   2.08 ms     (-0.59%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.05 ms →   2.04 ms     (-0.63%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.51 μs →  28.89 μs     (-2.09%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 203.52 μs → 206.67 μs     (+1.55%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     162.19 μs → 162.47 μs     (+0.17%)           1   →      1               
+ │ ├ sirius::Potential::generate_D_operator_matrix                        19.94 ms →  16.82 ms    (-15.66%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 234.00 ns → 158.00 ns    (-32.48%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  368.48 μs → 347.45 μs     (-5.71%)           1   →      1               
  │ ├ sirius::Local_operator                                              342.15 μs → 316.87 μs     (-7.39%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   25.74 μs →  25.21 μs     (-2.06%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   293.58 μs → 271.26 μs     (-7.60%)           1   →      1               
+ │ ├ sirius::Non_local_operator                                          936.00 ns → 796.50 ns    (-14.90%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                        7.42 μs →   8.85 μs    (+19.19%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                        5.35 μs →   7.33 μs    (+37.07%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      46.29 ms →  47.98 ms     (+3.66%)           1   →      1               
+ │ ├ sirius::Hamiltonian_k                                                19.21 μs →  17.07 μs    (-11.13%)           1   →      1               
+ │ │ └ sirius::Local_operator::prepare_k                                  17.94 μs →  15.58 μs    (-13.18%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 46.26 ms →  47.96 ms     (+3.67%)           1   →      1               
  │   ├ sddk::matrix_storage::matrix_storage                                6.18 μs →   5.69 μs     (-7.94%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   935.11 μs → 943.46 μs     (+0.89%)           1   →      1               
  │   ├ sirius::Band::initialize_subspace|kp|wf                            48.79 μs →  50.02 μs     (+2.52%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   17.48 ms →  17.64 ms     (+0.86%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.86 ms →   8.64 ms     (-2.50%)           1   →      1               
- │   │ │ ├ sddk::matrix_storage::remap_forward                             2.17 μs →   2.65 μs    (+21.94%)           1   →      1               
- │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.30 μs →   1.75 μs    (+34.13%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           328.00 ns → 329.00 ns     (+0.30%)           1   →      1               
+ │   │ │ └ sddk::matrix_storage::remap_backward                          821.00 ns → 623.00 ns    (-24.12%)           1   →      1               
- │   │ ├ sirius::Beta_projectors_base::inner                               4.25 ms →   4.82 ms    (+13.60%)           1   →      1               
  │   │ └ sirius::Non_local_operator::apply                                 1.94 ms →   1.88 ms     (-3.03%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   285.22 μs → 299.79 μs     (+5.11%)           2   →      2               
  │   │ └ sddk::inner                                                     278.59 μs → 293.29 μs     (+5.28%)           2   →      2               
  │   │   └ sddk::inner|local                                             271.29 μs → 278.43 μs     (+2.63%)           2   →      2               
  │   ├ Eigensolver_lapack|zhegvx                                          26.47 ms →  27.97 ms     (+5.67%)           1   →      1               
  │   └ sddk::transform                                                   313.09 μs → 322.10 μs     (+2.88%)           1   →      1               
  │     ├ sddk::transform|init                                             63.82 μs →  65.58 μs     (+2.75%)           1   →      1               
  │     └ sddk::transform|local                                           237.46 μs → 240.52 μs     (+1.29%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.26 s  →   2.26 s      (+0.30%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     53.11 μs →  50.66 μs     (-4.61%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        101.84 ms → 102.00 ms     (+0.15%)          22   →     22               
- │ │ ├ sirius::Hamiltonian0                                              380.84 μs → 443.59 μs    (+16.47%)          22   →     22               
- │ │ │ ├ sirius::Local_operator                                          359.50 μs → 422.77 μs    (+17.60%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               31.36 μs →  32.92 μs     (+4.96%)          22   →     22               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               312.42 μs → 373.83 μs    (+19.66%)          22   →     22               
  │ │ │ ├ sirius::Non_local_operator                                      907.73 ns → 858.32 ns     (-5.44%)          44   →     44               
  │ │ │ ├ sirius::D_operator::initialize                                    7.30 μs →   7.20 μs     (-1.35%)          22   →     22               
  │ │ │ └ sirius::Q_operator::initialize                                    5.62 μs →   5.63 μs     (+0.26%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.58 ms →  37.51 ms     (-0.19%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            20.45 μs →  20.85 μs     (+1.94%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              19.21 μs →  19.83 μs     (+3.23%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.27 ms →  33.35 ms     (+0.22%)          22   →     22               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             14.10 μs →  13.06 μs     (-7.39%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          1.02 μs → 928.96 ns     (-8.91%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           695.04 μs → 700.58 μs     (+0.80%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.50 μs →  10.55 μs     (+0.52%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       216.12 μs → 218.30 μs     (+1.01%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.55 ms →  32.62 ms     (+0.21%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.14 ms →   5.14 ms     (-0.07%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.26 ms →   4.25 ms     (-0.26%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.06 μs →   1.99 μs     (-3.07%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.79 μs →   1.73 μs     (-3.46%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     509.46 ns → 497.37 ns     (-2.37%)          87   →     87               
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    445.33 ns → 384.31 ns    (-13.70%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       281.30 μs → 284.37 μs     (+1.09%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         273.10 μs → 275.27 μs     (+0.79%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         879.06 μs → 887.20 μs     (+0.93%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               139.77 μs → 140.11 μs     (+0.25%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       138.17 μs → 138.57 μs     (+0.29%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.07 μs →  32.24 μs     (+0.52%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             247.61 μs → 248.71 μs     (+0.44%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           465.29 μs → 474.25 μs     (+1.93%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     76.58 μs →  77.33 μs     (+0.97%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   128.90 μs → 131.67 μs     (+2.15%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             208.49 μs → 209.12 μs     (+0.31%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               193.33 μs → 193.87 μs     (+0.28%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       192.28 μs → 192.83 μs     (+0.29%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   989.42 μs → 995.54 μs     (+0.62%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           570.94 μs → 573.10 μs     (+0.38%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           420.15 μs → 422.77 μs     (+0.62%)          68   →     68               
  │ │ │ │   │ │ ├ sddk::transform|init                                     70.21 μs →  69.03 μs     (-1.68%)          68   →     68               
  │ │ │ │   │ │ └ sddk::transform|local                                   173.99 μs → 175.98 μs     (+1.14%)         136   →    136               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               292.40 μs → 292.44 μs     (+0.01%)          68   →     68               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     862.36 μs → 877.24 μs     (+1.72%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           522.03 μs → 531.27 μs     (+1.77%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     73.47 μs →  73.87 μs     (+0.55%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   344.69 μs → 351.70 μs     (+2.03%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.95 μs →  19.43 μs     (-2.62%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        205.80 μs → 204.92 μs     (-0.43%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          36.91 ms →  37.67 ms     (+2.05%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                27.32 ms →  29.73 ms     (+8.82%)          22   →     22               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.57 μs →   2.36 μs     (-8.17%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.28 μs →   2.08 μs     (-8.96%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  410.68 μs → 410.85 μs     (+0.04%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         384.97 μs → 385.07 μs     (+0.03%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.84 ms →   2.83 ms     (-0.20%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               139.72 μs → 138.10 μs     (-1.16%)          22   →     22               
- │ │ │ │ └ sirius::Density::augment                                       23.17 ms →  25.91 ms    (+11.84%)          22   →     22               
- │ │ │ │   └ sirius::Density::generate_rho_aug                            23.15 ms →  25.90 ms    (+11.87%)          22   →     22               
- │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      3.73 ms →   4.47 ms    (+19.97%)          66   →     66               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       2.71 ms →   2.72 ms     (+0.57%)          66   →     66               
+ │ │ │ ├ sirius::Field4D::symmetrize                                       5.58 ms →   3.94 ms    (-29.40%)          22   →     22               
+ │ │ │ │ └ sirius::symmetrize_function|fpw                                 5.58 ms →   3.94 ms    (-29.40%)          22   →     22               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              2.28 ms → 641.53 μs    (-71.86%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.35 ms →   2.34 ms     (-0.37%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           930.76 μs → 938.36 μs     (+0.82%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.67 ms →   3.65 ms     (-0.37%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 345.48 μs → 344.79 μs     (-0.20%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                5.25 ms →   5.21 ms     (-0.71%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     22.46 μs →  21.02 μs     (-6.41%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 277.21 μs → 277.57 μs     (+0.13%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         275.40 μs → 275.50 μs     (+0.04%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                275.21 μs → 275.31 μs     (+0.03%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   191.75 μs → 189.20 μs     (-1.33%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               179.14 μs → 177.25 μs     (-1.05%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.43 ms →  13.94 ms     (-3.34%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        2.03 ms →   1.89 ms     (-6.93%)          22   →     22               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               442.96 μs → 206.97 μs    (-53.27%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               265.15 μs → 265.99 μs     (+0.32%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       261.83 μs → 261.36 μs     (-0.18%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              261.44 μs → 261.01 μs     (-0.16%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   10.62 μs →  10.85 μs     (+2.11%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.07 ms →   2.07 ms     (-0.32%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.01 ms →   2.01 ms     (-0.24%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             30.95 μs →  30.38 μs     (-1.85%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             204.47 μs → 199.98 μs     (-2.20%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 159.45 μs → 156.51 μs     (-1.85%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    10.08 ms →   9.75 ms     (-3.28%)          22   →     22               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             191.95 ns → 172.95 ns     (-9.90%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.92 ms →   3.90 ms     (-0.59%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.92 ms →   3.90 ms     (-0.59%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              621.84 μs → 623.64 μs     (+0.29%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.28 ms →   2.28 ms     (-0.07%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                               1.00 ms → 977.51 μs     (-2.32%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   241.63 μs → 237.85 μs     (-1.57%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   251.21 μs → 248.79 μs     (-0.97%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           247.52 μs → 246.73 μs     (-0.32%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  247.24 μs → 246.46 μs     (-0.32%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            265.79 μs → 258.63 μs     (-2.69%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    256.73 μs → 257.22 μs     (+0.19%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              239.15 μs → 237.92 μs     (-0.51%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 51.29 μs →  51.77 μs     (+0.94%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          49.42 μs →  50.05 μs     (+1.28%)          22   →     22               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                       230.35 μs → 235.80 μs     (+2.36%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     257.34 μs → 254.79 μs     (-0.99%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             256.18 μs → 244.48 μs     (-4.57%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    256.04 μs → 244.38 μs     (-4.56%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              257.22 μs → 260.08 μs     (+1.11%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      256.14 μs → 257.64 μs     (+0.58%)           3   →      3               
  ├ sirius::Stress|kin                                                    302.30 μs → 304.74 μs     (+0.81%)           1   →      1               
  ├ sirius::Stress|har                                                    584.75 μs → 578.96 μs     (-0.99%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.79 ms →   1.79 ms     (+0.03%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.56 ms →   3.42 ms     (-3.89%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                    1.27 ms →   1.31 ms     (+3.13%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       214.91 μs → 211.21 μs     (-1.72%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      18.45 μs →  18.93 μs     (+2.63%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      1.30 ms →   1.31 ms     (+0.93%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       252.65 μs → 254.88 μs     (+0.88%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               251.27 μs → 253.40 μs     (+0.84%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      251.09 μs → 253.22 μs     (+0.85%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                257.85 μs → 255.72 μs     (-0.83%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        256.81 μs → 254.51 μs     (-0.90%)           2   →      2               
  ├ sirius::Stress|us                                                     327.38 ms → 330.98 ms     (+1.10%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                     224.98 μs → 195.35 μs    (-13.17%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             77.61 ms →  79.06 ms     (+1.86%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   614.01 μs → 581.27 μs     (-5.33%)           3   →      3               
- │ ├ sirius::Stress|us|phase_fac                                           1.27 ms →   1.41 ms    (+10.48%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.21 ms →  22.33 ms     (+0.51%)           9   →      9               
+ │ ├ sirius::Stress|us|prepare                                            56.91 μs →  50.90 μs    (-10.56%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                1.20 ms →   1.14 ms     (-4.31%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.53 ms →  14.55 ms     (+0.13%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             6.07 ms →   6.04 ms     (-0.45%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                7.98 ms →   7.98 ms     (-0.00%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               332.49 μs → 330.10 μs     (-0.72%)          10   →     10               
  │   ├ sirius::Beta_projectors_base::prepare                               3.98 μs →   3.65 μs     (-8.51%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            267.70 μs → 268.60 μs     (+0.34%)           9   →      9               
  │   └ sirius::Beta_projectors_base::dismiss                              90.00 ns →  95.00 ns     (+5.56%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.31 ms →   1.33 ms     (+1.18%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          25.92 ms →  24.82 ms     (-4.25%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     251.97 μs → 246.02 μs     (-2.36%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.25 ms →   4.12 ms     (-3.11%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.97 ms →   2.97 ms     (-0.05%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               343.43 μs → 343.49 μs     (+0.02%)           4   →      4               
+ │   ├ sirius::Beta_projectors_base::prepare                               3.10 μs →   2.76 μs    (-10.79%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            273.61 μs → 270.53 μs     (-1.13%)           3   →      3               
+ │   └ sirius::Beta_projectors_base::dismiss                             136.00 ns →  66.00 ns    (-51.47%)           1   →      1               
  ├ sirius::Force::calc_forces_core                                         1.15 ms →   1.06 ms     (-7.58%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     228.83 μs → 229.55 μs     (+0.31%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       14.73 ms →  14.16 ms     (-3.89%)           1   →      1               
+ ├ sirius::Force::calc_forces_scf_corr                                   876.29 μs → 780.34 μs    (-10.95%)           1   →      1               
  ├ sirius::Force::hubbard_force                                            1.45 μs →   1.42 μs     (-1.94%)           1   →      1               
  └ sirius::finalize                                                      124.25 ms → 126.43 ms     (+1.75%)           1   →      1               
```
