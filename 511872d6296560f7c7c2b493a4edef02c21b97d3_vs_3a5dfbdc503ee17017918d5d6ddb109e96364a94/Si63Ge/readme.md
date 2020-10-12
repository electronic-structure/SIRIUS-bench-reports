# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   71.41 s  →  71.53 s      (+0.17%)           1   →      1               
+ ├ sirius::initialize                                                      2.92 s  →   2.48 s     (-15.13%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  3.61 s  →   4.15 s     (+15.11%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                 8.85 ms → 220.87 ms  (+2396.32%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       152.43 ms → 168.80 ms    (+10.74%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            67.20 ms →  75.00 ms    (+11.61%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          17.93 ms →  18.70 ms     (+4.33%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.65 ms →   3.63 ms     (-0.74%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  14.20 ms →  15.02 ms     (+5.77%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     14.12 ms →  14.96 ms     (+5.90%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.72 ms →   2.72 ms     (+0.19%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            526.45 μs → 524.38 μs     (-0.39%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               15.82 μs →  15.48 μs     (-2.17%)           1   →      1               
- │ └ sirius::Simulation_context::update                                    3.26 s  →   3.72 s     (+13.96%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           7.12 ms →   7.05 ms     (-1.01%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.74 ms →   3.69 ms     (-1.37%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.33 ms →   3.33 ms     (-0.12%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.29 ms →   3.27 ms     (-0.69%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.75 ms →   2.71 ms     (-1.63%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            504.60 μs → 519.58 μs     (+2.97%)           1   →      1               
- │   │     └ sirius::Unit_cell_symmetry|mag                               13.93 μs →  22.40 μs    (+60.84%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      212.48 ms → 211.63 ms     (-0.40%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.16 ms →  15.15 ms     (-0.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.35 ms →  13.24 ms     (-0.79%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.39 ms →  56.31 ms     (-0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.11 ms →  45.06 ms     (-0.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.31 ms →  60.40 ms     (+0.15%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.80 ms →  93.97 ms     (+0.18%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.94 ms →  69.85 ms     (-0.13%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  97.03 ms →  95.85 ms     (-1.21%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.97 ms →   2.02 ms     (+2.66%)           1   →      1               
- │   └ sirius::Augmentation_operator::generate_pw_coeffs                 464.78 ms → 717.19 ms    (+54.31%)           2   →      2               
+ ├ sirius::K_point_set::create_k_mesh                                    160.00 ms →  28.42 ms    (-82.24%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.21 μs →   1.75 μs    (-20.87%)           4   →      4               
+ │ └ sirius::K_point_set::initialize                                     159.93 ms →  28.36 ms    (-82.27%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.35 ms →  28.14 ms     (-0.76%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  10.93 ms →  10.76 ms     (-1.55%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                4.89 ms →   4.84 ms     (-0.91%)           1   →      1               
  │     ├ sddk::matrix_storage::matrix_storage                             10.83 μs →  10.40 μs     (-3.95%)           1   →      1               
  │     └ sirius::K_point::update                                          14.59 ms →  14.52 ms     (-0.50%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.55 ms →  10.52 ms     (-0.25%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.30 ms →   8.65 ms     (+4.18%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.60 ms →   2.54 ms     (-2.24%)           2   →      2               
  ├ sirius::Potential                                                      52.61 ms →  54.41 ms     (+3.40%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.92 ms →   2.89 ms     (-1.28%)           6   →      6               
  │ └ sirius::Potential::update                                            34.40 ms →  36.53 ms     (+6.20%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        34.01 ms →  36.14 ms     (+6.26%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               28.95 ms →  31.73 ms     (+9.61%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   4.49 ms →   3.84 ms    (-14.44%)           1   →      1               
  ├ sirius::Density                                                        42.32 ms →  41.40 ms     (-2.17%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.83 ms →   2.81 ms     (-0.47%)           2   →      2               
  │ └ sirius::Density::update                                              36.52 ms →  35.63 ms     (-2.44%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               36.31 ms →  35.34 ms     (-2.66%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                78.08 μs →  75.32 μs     (-3.53%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               29.23 ms →  32.04 ms     (+9.60%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   6.68 ms →   2.88 ms    (-56.88%)           1   →      1               
  ├ sirius::Density::initial_density                                       62.30 ms →  65.32 ms     (+4.86%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                   32.48 ms →  37.72 ms    (+16.13%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       5.40 ms →   4.33 ms    (-19.82%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  5.26 ms →   5.31 ms     (+0.88%)           1   →      1               
  ├ sirius::Potential::generate                                           371.67 ms → 373.55 ms     (+0.50%)           1   →      1               
  │ ├ sirius::Potential::poisson                                           42.72 ms →  44.86 ms     (+5.00%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     6.09 ms →   3.63 ms    (-40.41%)           1   →      1               
+ │ │ └ sirius::Periodic_function|inner                                     5.89 ms →   4.83 ms    (-17.96%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.85 ms →   4.82 ms     (-0.60%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.84 ms →   4.81 ms     (-0.57%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      780.66 μs → 722.85 μs     (-7.41%)           2   →      2               
  │ ├ sirius::Potential::xc                                                53.11 ms →  52.16 ms     (-1.78%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               51.89 ms →  50.97 ms     (-1.78%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.55 ms →   2.53 ms     (-0.58%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.56 ms →   4.28 ms     (-6.10%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.77 ms →   3.55 ms     (-5.86%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.09 ms → 270.11 ms     (+0.38%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 195.00 ns → 114.00 ns    (-41.54%)           1   →      1               
+ ├ sirius::Hamiltonian0                                                    7.72 ms →   6.84 ms    (-11.31%)           1   →      1               
  │ ├ sirius::Local_operator                                                7.02 ms →   6.33 ms     (-9.84%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.72 ms →   2.74 ms     (+0.52%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                     3.22 ms →   2.85 ms    (-11.54%)           1   →      1               
+ │ ├ sirius::Non_local_operator                                          207.07 μs →  73.79 μs    (-64.37%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                      112.07 μs → 157.30 μs    (+40.36%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                       91.94 μs → 115.56 μs    (+25.70%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.28 s  →   1.32 s      (+2.95%)           1   →      1               
+ │ ├ sirius::Hamiltonian_k                                                67.36 ms →  56.71 ms    (-15.82%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                 316.85 μs → 376.97 μs    (+18.97%)           1   →      1               
+ │ │ └ sirius::Beta_projectors_base::prepare                              67.04 ms →  56.33 ms    (-15.99%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.21 s  →   1.26 s      (+3.99%)           1   →      1               
+ │ │ ├ sddk::matrix_storage::matrix_storage                               90.35 ms →  81.27 ms    (-10.05%)           4   →      4               
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                    37.09 ms →  49.65 ms    (+33.86%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             7.29 ms →   7.38 ms     (+1.25%)           1   →      1               
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  382.72 ms → 311.68 ms    (-18.56%)           1   →      1               
+ │ │ │ ├ sirius::Local_operator::apply_h                                 289.74 ms → 244.64 ms    (-15.57%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.93 μs →   3.58 μs     (-8.81%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.03 μs →   2.61 μs    (-13.94%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           498.00 ns → 451.00 ns     (-9.44%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          453.00 ns → 582.00 ns    (+28.48%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.07 ms →   3.10 ms     (+1.08%)           1   →      1               
+ │ │ │ ├ sirius::Beta_projectors_base::inner                              38.53 ms →  21.29 ms    (-44.75%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                                25.66 ms →  21.30 ms    (-17.01%)           2   →      2               
- │ │ ├ sirius::Band::set_subspace_mtrx                                     5.38 ms →   6.47 ms    (+20.30%)           2   →      2               
- │ │ │ └ sddk::inner                                                       5.16 ms →   6.26 ms    (+21.33%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              23.19 μs →  24.62 μs     (+6.16%)           2   →      2               
- │ │ ├ Eigensolver_cuda|zhegvdx                                          200.60 ms → 273.06 ms    (+36.12%)           1   →      1               
- │ │ └ sddk::transform                                                     2.82 ms →   5.24 ms    (+86.00%)           1   →      1               
  │ │   ├ sddk::transform|init                                             13.08 μs →  12.04 μs     (-7.94%)           1   →      1               
+ │ │   └ sddk::transform|local                                            16.17 μs →  14.31 μs    (-11.51%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               460.00 ns → 414.00 ns    (-10.00%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     61.81 s  →  61.93 s      (+0.19%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.45 ms →   2.41 ms     (-1.25%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.24 s  →   3.25 s      (+0.33%)          19   →     19               
+ │ │ ├ sirius::Hamiltonian0                                                5.16 ms →   4.64 ms    (-10.05%)          19   →     19               
+ │ │ │ ├ sirius::Local_operator                                            4.50 ms →   4.01 ms    (-10.91%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              545.71 μs → 533.86 μs     (-2.17%)          19   →     19               
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.89 ms →   2.52 ms    (-13.00%)          19   →     19               
  │ │ │ ├ sirius::Non_local_operator                                      183.51 μs → 166.27 μs     (-9.39%)          38   →     38               
  │ │ │ ├ sirius::D_operator::initialize                                  117.13 μs → 121.06 μs     (+3.36%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                   98.09 μs →  98.66 μs     (+0.58%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.02 s  →   2.03 s      (+0.19%)          19   →     19               
  │ │ │ ├ sirius::Hamiltonian_k                                           217.53 μs → 215.56 μs     (-0.90%)          19   →     19               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             206.89 μs → 207.08 μs     (+0.09%)          19   →     19               
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                           7.61 μs →   5.62 μs    (-26.12%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.96 s  →   1.97 s      (+0.13%)          19   →     19               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             78.85 ms →  77.01 ms     (-2.32%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.97 ms →   8.03 ms     (+0.81%)         114   →    114               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            15.51 ms →  16.37 ms     (+5.51%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       481.47 μs → 457.20 μs     (-5.04%)          19   →     19               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         7.33 ms →   7.75 ms     (+5.78%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.86 s  →   1.87 s      (+0.18%)          19   →     19               
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             54.87 ms →  48.92 ms    (-10.84%)         356   →    356               
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                            34.51 ms →  28.91 ms    (-16.23%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.70 μs →   1.76 μs     (+3.54%)         356   →    356               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.44 μs →   1.49 μs     (+3.61%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     356.63 ns → 378.54 ns     (+6.14%)         356   →    356               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    469.59 ns → 536.45 ns    (+14.24%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      3.02 ms →   2.80 ms     (-7.49%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.20 ms →   3.12 ms     (-2.31%)         356   →    356               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           7.07 ms →   7.04 ms     (-0.34%)         712   →    712               
  │ │ │ │   ├ sddk::orthogonalize                                           5.47 ms →   5.71 ms     (+4.30%)         356   →    356               
- │ │ │ │   │ ├ sddk::inner                                               725.44 μs → 845.11 μs    (+16.50%)         693   →    693               
  │ │ │ │   │ │ └ sddk::inner|local                                        21.25 μs →  22.17 μs     (+4.32%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 133.17 μs → 134.58 μs     (+1.06%)         356   →    356               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               2.07 ms →   2.05 ms     (-0.87%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             1.95 ms →   1.97 ms     (+1.02%)         337   →    337               
  │ │ │ │   │   ├ sddk::transform|init                                     16.81 μs →  17.72 μs     (+5.36%)         337   →    337               
  │ │ │ │   │   └ sddk::transform|local                                     6.93 μs →   7.37 μs     (+6.33%)        1.01 K →   1.01 K             
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             993.44 μs →   1.31 ms    (+31.44%)         356   →    356               
- │ │ │ │   │ └ sddk::inner                                               924.46 μs →   1.24 ms    (+33.82%)         356   →    356               
  │ │ │ │   │   └ sddk::inner|local                                        20.83 μs →  21.55 μs     (+3.46%)         356   →    356               
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     34.37 ms →  40.17 ms    (+16.89%)         356   →    356               
  │ │ │ │   ├ sirius::residuals                                             2.57 ms →   2.44 ms     (-4.91%)         340   →    340               
  │ │ │ │   │ ├ sddk::transform                                             1.27 ms →   1.22 ms     (-4.00%)         337   →    337               
  │ │ │ │   │ │ ├ sddk::transform|init                                     14.57 μs →  15.18 μs     (+4.17%)         337   →    337               
  │ │ │ │   │ │ └ sddk::transform|local                                     8.97 μs →   9.55 μs     (+6.45%)         674   →    674               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.20 ms →   1.10 ms     (-8.65%)         337   →    337               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       8.10 ms →   7.39 ms     (-8.76%)          54   →     54               
  │ │ │ │     └ sddk::transform                                             4.87 ms →   4.44 ms     (-8.84%)          89   →     89               
  │ │ │ │       ├ sddk::transform|init                                     10.64 μs →  10.70 μs     (+0.54%)          89   →     89               
  │ │ │ │       └ sddk::transform|local                                     8.99 μs →   9.03 μs     (+0.49%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           541.00 ns → 546.42 ns     (+1.00%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.97 μs →  19.02 μs     (-4.75%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.57 ms →   1.52 ms     (-3.27%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         561.28 ms → 567.64 ms     (+1.13%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               410.12 ms → 419.48 ms     (+2.28%)          19   →     19               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.62 μs →   6.89 μs     (-9.51%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.07 μs →   6.43 μs     (-9.06%)          19   →     19               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   43.66 ms →  30.82 ms    (-29.40%)          19   →     19               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.21 μs →   6.10 μs    (-15.40%)          19   →     19               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                       23.45 ms →   4.71 ms    (-79.92%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          19.14 ms →  25.06 ms    (+30.95%)          19   →     19               
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       628.37 ns → 534.21 ns    (-14.98%)          19   →     19               
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                   95.72 ms → 115.01 ms    (+20.16%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 2.14 ms →   2.06 ms     (-3.66%)          19   →     19               
  │ │ │ │ └ sirius::Density::augment                                      222.61 ms → 239.08 ms     (+7.40%)          19   →     19               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           222.32 ms → 238.87 ms     (+7.45%)          19   →     19               
  │ │ │ ├ sirius::Field4D::symmetrize                                     123.25 ms → 120.05 ms     (-2.60%)          19   →     19               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               123.25 ms → 120.05 ms     (-2.60%)          19   →     19               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             42.48 ms →  39.11 ms     (-7.93%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        67.41 ms →  67.62 ms     (+0.30%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.71 ms →  12.68 ms     (-0.28%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.65 ms →  24.76 ms     (+4.66%)          19   →     19               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   4.25 ms →   3.35 ms    (-21.17%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              131.60 ms → 130.86 ms     (-0.56%)          19   →     19               
- │ │ │ ├ sirius::Density::mixer_input                                    633.99 μs →   1.09 ms    (+72.19%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function|inner                                   4.73 ms →   4.71 ms     (-0.49%)         229   →    229               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.62 ms →   4.62 ms     (-0.13%)         229   →    229               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.62 ms →   4.62 ms     (-0.13%)         229   →    229               
- │ │ │ └ sirius::Density::mixer_output                                     4.89 ms →   5.92 ms    (+21.16%)          19   →     19               
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 4.25 ms →   5.23 ms    (+23.07%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       363.64 ms → 365.41 ms     (+0.48%)          19   →     19               
  │ │ │ ├ sirius::Potential::poisson                                       43.25 ms →  44.82 ms     (+3.63%)          19   →     19               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 6.51 ms →   2.95 ms    (-54.68%)          19   →     19               
  │ │ │ │ └ sirius::Periodic_function|inner                                 5.95 ms →   5.43 ms     (-8.85%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.83 ms →   4.83 ms     (-0.10%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.83 ms →   4.83 ms     (-0.10%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  793.16 μs → 796.09 μs     (+0.37%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            45.03 ms →  44.72 ms     (-0.69%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.84 ms →  43.53 ms     (-0.71%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            675.78 μs → 657.33 μs     (-2.73%)          38   →     38               
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.59 ms →   4.10 ms    (-10.50%)          19   →     19               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.62 ms →   3.85 ms     (+6.26%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.68 ms → 269.04 ms     (+0.13%)          19   →     19               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             232.05 ns → 137.37 ns    (-40.80%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        93.88 ms →  93.95 ms     (+0.08%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  93.88 ms →  93.95 ms     (+0.08%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.28 ms →  13.29 ms     (+0.08%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          67.39 ms →  67.44 ms     (+0.07%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.59 ms →  12.60 ms     (+0.08%)          19   →     19               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.15 ms →   3.42 ms    (-17.75%)          19   →     19               
  │ │ ├ sirius::Periodic_function|inner                                     4.69 ms →   4.73 ms     (+0.85%)         133   →    133               
  │ │ │ └ sirius::Periodic_function|inner_local                             4.57 ms →   4.55 ms     (-0.43%)         133   →    133               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.57 ms →   4.55 ms     (-0.43%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.74 ms →   4.86 ms     (+2.50%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.72 ms →   4.72 ms     (+0.01%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.55 ms →   4.53 ms     (-0.30%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 73.17 μs →  73.12 μs     (-0.06%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          68.44 μs →  69.34 μs     (+1.32%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.75 ms →   5.71 ms     (-0.63%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.66 ms →   4.76 ms     (+2.24%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.52 ms →   4.67 ms     (+3.28%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.52 ms →   4.67 ms     (+3.28%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.77 ms →   4.81 ms     (+0.78%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.76 ms →   4.81 ms     (+0.94%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.52 ms →   4.77 ms     (+5.63%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.51 ms →   4.77 ms     (+5.69%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.51 ms →   4.77 ms     (+5.69%)           2   →      2               
- ├ sirius::Smooth_periodic_function|inner                                  4.70 ms →   5.24 ms    (+11.30%)           1   →      1               
- │ └ sirius::Smooth_periodic_function|inner_local                          4.70 ms →   5.23 ms    (+11.37%)           1   →      1               
  └ sirius::finalize                                                      749.22 ms → 752.00 ms     (+0.37%)           1   →      1               
```
