# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                  421.49 s  →  71.22 s     (-83.10%)           1   →      1               
  ├ sirius::initialize                                                      3.09 s  →   2.91 s      (-5.92%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  2.83 s  →   3.48 s     (+23.14%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                25.08 ms →   1.15 ms    (-95.40%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       171.03 ms → 103.83 ms    (-39.29%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            76.71 ms →  42.94 ms    (-44.02%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          17.55 ms →  17.86 ms     (+1.79%)           1   →      1               
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.69 ms →   5.22 ms    (+41.37%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  13.85 ms →  12.59 ms     (-9.12%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     13.78 ms →  12.52 ms     (-9.09%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.76 ms →   2.74 ms     (-0.90%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            510.62 μs → 508.34 μs     (-0.45%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               17.27 μs →  15.96 μs     (-7.58%)           1   →      1               
- │ └ sirius::Simulation_context::update                                    2.58 s  →   3.27 s     (+26.76%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.90 ms →   6.96 ms     (+0.84%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.53 ms →   3.64 ms     (+3.22%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.37 ms →   3.28 ms     (-2.70%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.32 ms →   3.24 ms     (-2.60%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.78 ms →   2.72 ms     (-2.50%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            502.43 μs → 487.92 μs     (-2.89%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               14.62 μs →  13.49 μs     (-7.72%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      212.57 ms → 212.51 ms     (-0.03%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.17 ms →  15.13 ms     (-0.24%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.25 ms →  13.24 ms     (-0.10%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.38 ms →  56.41 ms     (+0.05%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.05 ms →  45.07 ms     (+0.06%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.20 ms →  60.34 ms     (+0.22%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   92.20 ms →  95.30 ms     (+3.37%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     70.27 ms →  71.47 ms     (+1.71%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  97.81 ms → 102.38 ms     (+4.67%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.97 ms →   1.99 ms     (+0.98%)           1   →      1               
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs                 580.45 ms → 469.59 ms    (-19.10%)           2   →      2               
- ├ sirius::K_point_set::create_k_mesh                                    172.14 ms → 236.65 ms    (+37.47%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              4.09 μs →   2.73 μs    (-33.36%)           4   →      4               
- │ └ sirius::K_point_set::initialize                                     172.06 ms → 236.58 ms    (+37.50%)           1   →      1               
+ │   └ sirius::K_point::initialize                                       171.76 ms →  29.26 ms    (-82.96%)           1   →      1               
+ │     ├ sirius::K_point::generate_gkvec                                  19.77 ms →  11.01 ms    (-44.31%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                5.32 ms →   4.95 ms     (-6.97%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                             15.08 μs →   7.35 μs    (-51.25%)           1   →      1               
+ │     └ sirius::K_point::update                                         149.05 ms →  15.34 ms    (-89.71%)           1   →      1               
+ │       └ sirius::Beta_projectors                                       145.61 ms →  11.38 ms    (-92.19%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                  8.57 ms →   8.24 ms     (-3.78%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      137.03 ms                                    1                          
  ├ sirius::Smooth_periodic_function                                        2.67 ms →   2.53 ms     (-5.13%)           2   →      2               
  ├ sirius::Potential                                                      54.38 ms →  51.78 ms     (-4.79%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.91 ms →   2.89 ms     (-0.62%)           6   →      6               
  │ └ sirius::Potential::update                                            36.43 ms →  33.84 ms     (-7.13%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        36.06 ms →  33.45 ms     (-7.23%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.56 ms →  25.64 ms     (-3.46%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   8.91 ms →   7.28 ms    (-18.30%)           1   →      1               
  ├ sirius::Density                                                        45.58 ms →  41.14 ms     (-9.74%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.78 ms →   2.81 ms     (+1.28%)           2   →      2               
+ │ └ sirius::Density::update                                              39.99 ms →  35.38 ms    (-11.54%)           1   →      1               
+ │   └ sirius::Density::generate_pseudo_core_charge_density               39.76 ms →  35.17 ms    (-11.55%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                76.75 μs →  78.35 μs     (+2.09%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               26.65 ms →  25.64 ms     (-3.81%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  12.69 ms →   9.16 ms    (-27.82%)           1   →      1               
  ├ sirius::Density::initial_density                                       64.21 ms →  59.43 ms     (-7.44%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                   27.81 ms →  25.98 ms     (-6.57%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       9.01 ms →   7.28 ms    (-19.20%)           2   →      2               
- │ └ sirius::Periodic_function::integrate                                  4.66 ms →   5.28 ms    (+13.38%)           1   →      1               
+ ├ sirius::Potential::generate                                             2.45 s  → 367.26 ms    (-85.00%)           1   →      1               
+ │ ├ sirius::Potential::poisson                                           44.98 ms →  39.68 ms    (-11.78%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                    14.21 ms →   8.95 ms    (-37.01%)           1   →      1               
- │ │ └ sirius::Periodic_function|inner                                     5.13 ms →   5.70 ms    (+10.97%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             5.13 ms →   4.84 ms     (-5.60%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    5.11 ms →   4.83 ms     (-5.47%)           1   →      1               
- │ ├ sirius::Periodic_function::add                                      603.68 μs → 749.30 μs    (+24.12%)           2   →      2               
  │ ├ sirius::Potential::xc                                                52.65 ms →  51.65 ms     (-1.90%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               51.47 ms →  50.44 ms     (-1.99%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.45 ms →   2.58 ms     (+5.25%)           2   →      2               
+ │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.24 ms →   4.24 ms    (-19.05%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       6.42 ms →   3.77 ms    (-41.38%)           1   →      1               
+ │ ├ sirius::Potential::generate_D_operator_matrix                         2.34 s  → 269.26 ms    (-88.50%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 213.00 ns → 167.00 ns    (-21.60%)           1   →      1               
- ├ sirius::Hamiltonian0                                                    5.56 ms →   7.59 ms    (+36.51%)           1   →      1               
- │ ├ sirius::Local_operator                                                5.40 ms →   7.04 ms    (+30.43%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function                                  596.98 μs →   2.74 ms   (+358.29%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                     4.52 ms →   3.24 ms    (-28.37%)           1   →      1               
- │ ├ sirius::Non_local_operator                                            2.27 μs → 138.80 μs  (+6023.80%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                       61.74 μs → 107.95 μs    (+74.85%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                       30.78 μs →  92.06 μs   (+199.13%)           1   →      1               
+ ├ sirius::Band::initialize_subspace                                       5.02 s  →   1.28 s     (-74.47%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                               187.71 μs →  58.06 ms (+30830.07%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 185.35 μs → 311.99 μs    (+68.32%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                                          57.74 ms                                   1               
+ │ ├ sirius::Band::initialize_subspace|kp                                  5.02 s  →   1.22 s     (-75.63%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               16.15 μs →  77.16 ms (+477621.93%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    42.90 ms →  43.69 ms     (+1.84%)           1   →      1               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                            17.92 ms →   8.73 ms    (-51.28%)           1   →      1               
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    4.39 s  → 311.65 ms    (-92.90%)           1   →      1               
+ │ │ │ ├ sirius::Local_operator::apply_h                                   2.01 s  → 244.15 ms    (-87.85%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             4.95 μs →   4.03 μs    (-18.46%)           1   →      1               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.08 μs →   2.95 μs     (-4.00%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           386.00 ns → 393.00 ns     (+1.81%)           1   →      1               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                            3.67 μs → 545.00 ns    (-85.13%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                                        3.17 ms                                   1               
+ │ │ │ ├ sirius::Beta_projectors_base::inner                             741.98 ms →  21.35 ms    (-97.12%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                               783.75 ms →  21.47 ms    (-97.26%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                   176.83 ms →   5.29 ms    (-97.01%)           2   →      2               
+ │ │ │ └ sddk::inner                                                     176.79 ms →   5.08 ms    (-97.12%)           2   →      2               
+ │ │ │   └ sddk::inner|local                                             176.78 ms →  25.45 μs    (-99.99%)           2   →      2               
  │ │ ├ Eigensolver_lapack|zhegvx                                          64.45 ms                                    1                          
  │ │ ├ Eigensolver_cuda|zhegvdx                                                      272.81 ms                                   1               
+ │ │ └ sddk::transform                                                   140.58 ms →   2.83 ms    (-97.99%)           1   →      1               
+ │ │   ├ sddk::transform|init                                             32.13 ms →  13.76 μs    (-99.96%)           1   →      1               
+ │ │   └ sddk::transform|local                                           108.44 ms →  18.83 μs    (-99.98%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                                           449.00 ns                                   1               
+ ├ sirius::DFT_ground_state::scf_loop                                    407.41 s  →  61.68 s     (-84.86%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.48 ms →   2.44 ms     (-1.63%)          19   →     19               
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                         21.43 s  →   3.23 s     (-84.91%)          19   →     19               
+ │ │ ├ sirius::Hamiltonian0                                                6.50 ms →   5.65 ms    (-13.09%)          19   →     19               
+ │ │ │ ├ sirius::Local_operator                                            6.33 ms →   4.95 ms    (-21.81%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              546.31 μs → 529.33 μs     (-3.11%)          19   →     19               
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 5.53 ms →   3.26 ms    (-41.15%)          19   →     19               
- │ │ │ ├ sirius::Non_local_operator                                        2.85 μs → 211.49 μs  (+7331.52%)          38   →     38               
- │ │ │ ├ sirius::D_operator::initialize                                   58.51 μs → 109.30 μs    (+86.82%)          19   →     19               
- │ │ │ └ sirius::Q_operator::initialize                                   31.01 μs →  94.28 μs   (+204.04%)          19   →     19               
+ │ │ ├ sirius::Band::solve                                                16.76 s  →   2.02 s     (-87.94%)          19   →     19               
- │ │ │ ├ sirius::Hamiltonian_k                                           151.27 μs → 224.14 μs    (+48.17%)          19   →     19               
- │ │ │ │ ├ sirius::Local_operator::prepare_k                             150.01 μs → 215.52 μs    (+43.67%)          19   →     19               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                                       5.82 μs                                  19               
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     15.26 s  →   1.95 s     (-87.20%)          19   →     19               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc              1.08 ms →  71.19 ms  (+6503.18%)          19   →     19               
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        178.29 μs →   8.30 ms  (+4554.67%)         114   →    114               
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            17.54 ms →  15.48 ms    (-11.76%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       435.65 μs → 456.46 μs     (+4.78%)          19   →     19               
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.48 ms →   7.28 ms    (-14.08%)          38   →     38               
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              15.24 s  →   1.86 s     (-87.80%)          19   →     19               
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            589.14 ms →  44.78 ms    (-92.40%)         356   →    356               
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                           190.90 ms →  27.35 ms    (-85.67%)         356   →    356               
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       3.71 μs →   2.03 μs    (-45.29%)         356   →    356               
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     3.24 μs →   1.72 μs    (-46.88%)         356   →    356               
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     868.89 ns → 466.21 ns    (-46.34%)         356   →    356               
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                      1.85 μs → 607.40 ns    (-67.18%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                                  2.64 ms                                 356               
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       115.42 ms →   3.05 ms    (-97.35%)         356   →    356               
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                         140.35 ms →   5.86 ms    (-95.83%)         712   →    712               
+ │ │ │ │   ├ sddk::orthogonalize                                         106.30 ms →   4.99 ms    (-95.31%)         356   →    356               
+ │ │ │ │   │ ├ sddk::inner                                                12.61 ms → 653.29 μs    (-94.82%)         693   →    693               
+ │ │ │ │   │ │ └ sddk::inner|local                                        12.61 ms →  25.00 μs    (-99.80%)         693   →    693               
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  93.64 μs → 136.05 μs    (+45.29%)         356   →    356               
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                              23.30 ms →   1.77 ms    (-92.42%)         356   →    356               
+ │ │ │ │   │ └ sddk::transform                                            61.63 ms →   1.91 ms    (-96.90%)         337   →    337               
+ │ │ │ │   │   ├ sddk::transform|init                                      3.30 ms →  19.53 μs    (-99.41%)         337   →    337               
+ │ │ │ │   │   └ sddk::transform|local                                    19.44 ms →   8.31 μs    (-99.96%)        1.01 K →   1.01 K             
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                              19.97 ms →   1.00 ms    (-94.97%)         356   →    356               
+ │ │ │ │   │ └ sddk::inner                                                19.87 ms → 936.41 μs    (-95.29%)         356   →    356               
+ │ │ │ │   │   └ sddk::inner|local                                        19.87 ms →  24.42 μs    (-99.88%)         356   →    356               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                    12.34 ms                                  356                          
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                                 45.51 ms                                 356               
+ │ │ │ │   ├ sirius::residuals                                            46.09 ms →   2.04 ms    (-95.58%)         340   →    340               
+ │ │ │ │   │ ├ sddk::transform                                            38.66 ms →   1.12 ms    (-97.12%)         337   →    337               
+ │ │ │ │   │ │ ├ sddk::transform|init                                      1.81 ms →  17.27 μs    (-99.05%)         337   →    337               
+ │ │ │ │   │ │ └ sddk::transform|local                                    18.42 ms →  10.75 μs    (-99.94%)         674   →    674               
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 7.81 ms → 856.92 μs    (-89.03%)         337   →    337               
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     262.68 ms →   6.66 ms    (-97.46%)          54   →     54               
+ │ │ │ │     └ sddk::transform                                           149.77 ms →   3.99 ms    (-97.34%)          89   →     89               
+ │ │ │ │       ├ sddk::transform|init                                      7.42 ms →  11.88 μs    (-99.84%)          89   →     89               
+ │ │ │ │       └ sddk::transform|local                                   102.16 ms →   9.94 μs    (-99.99%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                                       525.95 ns                                  19               
+ │ │ │ └ sirius::K_point_set::sync_band_energies                          30.76 μs →  18.65 μs    (-39.36%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.57 ms →   1.60 ms     (+1.87%)          19   →     19               
+ │ │ ├ sirius::Density::generate                                           1.92 s  → 561.51 ms    (-70.68%)          19   →     19               
+ │ │ │ ├ sirius::Density::generate_valence                                 1.76 s  → 419.18 ms    (-76.25%)          19   →     19               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.66 μs →   7.48 μs    (-13.58%)          19   →     19               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           8.01 μs →   6.87 μs    (-14.20%)          19   →     19               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  468.42 ms →  27.36 ms    (-94.16%)          19   →     19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                                     7.19 μs                                  19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                                    4.90 ms                                  19               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         467.26 ms →  21.44 ms    (-95.41%)          19   →     19               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                                   715.16 ns                                  19               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  737.56 ms → 118.29 ms    (-83.96%)          19   →     19               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 3.58 ms →   2.17 ms    (-39.26%)          19   →     19               
+ │ │ │ │ └ sirius::Density::augment                                      537.10 ms → 236.36 ms    (-55.99%)          19   →     19               
+ │ │ │ │   └ sirius::Density::generate_rho_aug                           536.89 ms → 236.15 ms    (-56.02%)          19   →     19               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                    152.68 ms                                   38                          
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                      64.29 ms                                   38                          
  │ │ │ ├ sirius::Field4D::symmetrize                                     120.38 ms → 115.28 ms     (-4.23%)          19   →     19               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               120.38 ms → 115.28 ms     (-4.23%)          19   →     19               
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             39.01 ms →  33.09 ms    (-15.17%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        67.90 ms →  68.95 ms     (+1.55%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.75 ms →  12.59 ms     (-1.23%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.80 ms →  23.67 ms     (-0.53%)          19   →     19               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   6.18 ms →   3.37 ms    (-45.41%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              132.63 ms → 131.64 ms     (-0.75%)          19   →     19               
+ │ │ │ ├ sirius::Density::mixer_input                                      1.01 ms → 337.05 μs    (-66.56%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function|inner                                   4.69 ms →   4.79 ms     (+2.00%)         229   →    229               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.60 ms →   4.65 ms     (+1.03%)         229   →    229               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.60 ms →   4.65 ms     (+1.03%)         229   →    229               
+ │ │ │ └ sirius::Density::mixer_output                                     6.92 ms →   5.61 ms    (-18.99%)          19   →     19               
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.13 ms →   4.90 ms    (-20.07%)          19   →     19               
+ │ │ ├ sirius::Potential::generate                                         2.46 s  → 360.09 ms    (-85.38%)          19   →     19               
+ │ │ │ ├ sirius::Potential::poisson                                       45.04 ms →  39.88 ms    (-11.46%)          19   →     19               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                14.26 ms →   9.41 ms    (-34.04%)          19   →     19               
  │ │ │ │ └ sirius::Periodic_function|inner                                 5.07 ms →   5.48 ms     (+8.14%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.82 ms →   4.83 ms     (+0.36%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.82 ms →   4.83 ms     (+0.37%)          19   →     19               
+ │ │ │ ├ sirius::Periodic_function::add                                    1.01 ms → 761.03 μs    (-24.53%)          38   →     38               
+ │ │ │ ├ sirius::Potential::xc                                            51.54 ms →  44.52 ms    (-13.62%)          19   →     19               
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           50.38 ms →  43.33 ms    (-13.98%)          19   →     19               
+ │ │ │ │   ├ sirius::Smooth_periodic_function                              1.33 ms → 689.73 μs    (-48.07%)          38   →     38               
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.52 ms →   4.15 ms    (-24.67%)          19   →     19               
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   5.58 ms →   3.87 ms    (-30.64%)          19   →     19               
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     2.36 s  → 268.91 ms    (-88.59%)          19   →     19               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             270.63 ns → 222.79 ns    (-17.68%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        95.05 ms →  95.15 ms     (+0.11%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  95.05 ms →  95.15 ms     (+0.11%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.08 ms →  13.24 ms     (+1.21%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          67.88 ms →  68.69 ms     (+1.19%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.72 ms →  12.59 ms     (-1.04%)          19   →     19               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     6.15 ms →   3.79 ms    (-38.37%)          19   →     19               
  │ │ ├ sirius::Periodic_function|inner                                     4.58 ms →   4.70 ms     (+2.71%)         133   →    133               
  │ │ │ └ sirius::Periodic_function|inner_local                             4.53 ms →   4.60 ms     (+1.52%)         133   →    133               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.53 ms →   4.60 ms     (+1.51%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.73 ms →   4.73 ms     (+0.11%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.72 ms →   4.73 ms     (+0.13%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.54 ms →   4.54 ms     (+0.06%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 76.01 μs →  74.27 μs     (-2.29%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          69.62 μs →  69.30 μs     (-0.46%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.17 ms →   5.61 ms     (+8.46%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.54 ms →   4.82 ms     (+6.18%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.53 ms →   4.82 ms     (+6.29%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.53 ms →   4.82 ms     (+6.32%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.72 ms →   5.08 ms     (+7.67%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.71 ms →   5.08 ms     (+7.83%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.86 ms →   4.79 ms     (-1.35%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.85 ms →   4.79 ms     (-1.36%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.85 ms →   4.79 ms     (-1.36%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  5.01 ms →   5.04 ms     (+0.52%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          5.01 ms →   5.03 ms     (+0.52%)           1   →      1               
- └ sirius::finalize                                                      121.62 ms → 763.45 ms   (+527.75%)           1   →      1               
```
