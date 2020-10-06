# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                    7.72 s  →   8.57 s     (+11.13%)           1   →      1               
  ├ sirius::initialize                                                      2.87 s  →   2.79 s      (-2.96%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  1.98 s  →   2.92 s     (+47.42%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               390.53 μs →  94.16 ms (+24010.95%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       328.11 ms → 310.17 ms     (-5.47%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                           102.25 ms →  97.77 ms     (-4.38%)           3   →      3               
+ │ │ └ sirius::Unit_cell::update                                          21.32 ms →  16.78 ms    (-21.27%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      231.23 μs → 250.07 μs     (+8.15%)           1   →      1               
+ │ │   └ sirius::Unit_cell::get_symmetry                                  21.08 ms →  16.48 ms    (-21.84%)           1   →      1               
+ │ │     └ sirius::Unit_cell_symmetry                                     21.05 ms →  16.45 ms    (-21.85%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.94 ms →   5.10 ms     (+3.34%)           1   →      1               
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.99 ms →  67.72 μs    (-97.74%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               15.90 μs →  16.09 μs     (+1.18%)           1   →      1               
- │ └ sirius::Simulation_context::update                                    1.61 s  →   2.47 s     (+53.29%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.20 ms →   5.16 ms     (-0.80%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       32.98 μs →  34.05 μs     (+3.24%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.17 ms →   5.08 ms     (-1.67%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.14 ms →   5.06 ms     (-1.64%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                5.03 ms →   4.95 ms     (-1.69%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                             51.61 μs →  52.95 μs     (+2.59%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               17.57 μs →  19.22 μs     (+9.40%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      270.84 ms → 272.48 ms     (+0.61%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.25 ms →  21.20 ms     (-0.24%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.02 ms →  19.05 ms     (+0.19%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.35 ms →  80.45 ms     (+0.12%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.58 ms →  61.47 ms     (-0.18%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                96.50 ms →  96.72 ms     (+0.23%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.23 ms →   4.27 ms     (+0.84%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.97 ms →   3.03 ms     (+1.98%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.07 ms →   3.97 ms     (-2.47%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                295.94 μs → 284.55 μs     (-3.85%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  93.48 ms →  94.99 ms     (+1.61%)           3   →      3               
+ ├ sirius::K_point_set::create_k_mesh                                      5.93 ms →   2.51 ms    (-57.65%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            770.50 ns → 831.50 ns     (+7.92%)           4   →      4               
+ │ └ sirius::K_point_set::initialize                                       5.86 ms →   2.44 ms    (-58.35%)           1   →      1               
+ │   └ sirius::K_point::initialize                                         5.61 ms →   2.19 ms    (-60.99%)           1   →      1               
+ │     ├ sirius::K_point::generate_gkvec                                   4.59 ms →   1.12 ms    (-75.56%)           1   →      1               
  │     │ └ sddk::Gvec::init                                              260.49 μs → 240.75 μs     (-7.58%)           1   →      1               
- │     ├ sddk::matrix_storage::matrix_storage                              2.34 μs →   9.91 μs   (+323.45%)           1   →      1               
- │     └ sirius::K_point::update                                         799.36 μs → 925.39 μs    (+15.77%)           1   →      1               
  │       └ sirius::Beta_projectors                                       655.48 μs → 691.58 μs     (+5.51%)           1   →      1               
- │         ├ sirius::Beta_projectors::generate_pw_coefs_t                392.54 μs → 560.49 μs    (+42.79%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      259.43 μs                                    1                          
- ├ sirius::Smooth_periodic_function                                       29.44 μs → 136.22 μs   (+362.77%)           2   →      2               
- ├ sirius::Potential                                                       2.00 ms →   2.96 ms    (+48.08%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function                                     27.43 μs → 157.35 μs   (+473.57%)           6   →      6               
  │ └ sirius::Potential::update                                             1.74 ms →   1.79 ms     (+3.01%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.73 ms →   1.78 ms     (+3.06%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.30 ms →   1.19 ms     (-8.69%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                 332.13 μs → 480.27 μs    (+44.60%)           1   →      1               
- ├ sirius::Density                                                         1.63 ms →   1.83 ms    (+11.66%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function                                     29.28 μs → 136.78 μs   (+367.11%)           2   →      2               
  │ └ sirius::Density::update                                               1.57 ms →   1.55 ms     (-1.50%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                1.56 ms →   1.54 ms     (-1.46%)           1   →      1               
- │     ├ sirius::rho_core_ri_pseudo|values                                19.65 μs →  22.15 μs    (+12.72%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function                1.32 ms →   1.18 ms    (-10.65%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                 205.99 μs → 321.32 μs    (+55.99%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.73 ms →   2.96 ms     (+8.26%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    1.18 ms →   1.18 ms     (+0.31%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     282.36 μs → 403.84 μs    (+43.02%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                253.23 μs → 246.66 μs     (-2.59%)           1   →      1               
+ ├ sirius::Potential::generate                                            23.27 ms →  20.32 ms    (-12.68%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            1.79 ms →   1.69 ms     (-5.56%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                   200.42 μs → 246.55 μs    (+23.02%)           1   →      1               
- │ │ └ sirius::Periodic_function|inner                                   263.47 μs → 318.23 μs    (+20.78%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           260.69 μs → 258.77 μs     (-0.74%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.42 μs → 258.49 μs     (-0.74%)           1   →      1               
- │ ├ sirius::Periodic_function::add                                       10.95 μs →  13.99 μs    (+27.72%)           2   →      2               
- │ ├ sirius::Potential::xc                                                 2.07 ms →   2.60 ms    (+25.61%)           1   →      1               
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.03 ms →   2.55 ms    (+25.86%)           1   →      1               
- │ │   ├ sirius::Smooth_periodic_function                                 28.61 μs → 135.62 μs   (+374.01%)           2   →      2               
- │ │   └ sirius::Smooth_periodic_function::fft_transform                 206.53 μs → 290.01 μs    (+40.43%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     159.69 μs → 274.83 μs    (+72.10%)           1   →      1               
+ │ ├ sirius::Potential::generate_D_operator_matrix                        19.20 ms →  15.69 ms    (-18.29%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 228.00 ns → 158.00 ns    (-30.70%)           1   →      1               
- ├ sirius::Hamiltonian0                                                  377.77 μs → 513.31 μs    (+35.88%)           1   →      1               
- │ ├ sirius::Local_operator                                              349.18 μs → 393.09 μs    (+12.58%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function                                   26.91 μs →  22.65 μs    (-15.82%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   300.89 μs → 316.91 μs     (+5.32%)           1   →      1               
- │ ├ sirius::Non_local_operator                                          905.50 ns →  25.85 μs  (+2754.94%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                        8.46 μs →  30.25 μs   (+257.61%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                        7.43 μs →  25.76 μs   (+246.66%)           1   →      1               
+ ├ sirius::Band::initialize_subspace                                      46.96 ms →  28.51 ms    (-39.28%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                17.66 μs →  27.72 μs    (+56.99%)           1   →      1               
- │ │ ├ sirius::Local_operator::prepare_k                                  16.48 μs →  22.98 μs    (+39.44%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                                           2.60 μs                                   1               
+ │ ├ sirius::Band::initialize_subspace|kp                                 46.94 ms →  28.48 ms    (-39.33%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                                1.54 μs → 858.04 μs (+55598.65%)           4   →      4               
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                   935.29 μs → 692.76 μs    (-25.93%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            43.19 μs →  47.15 μs     (+9.16%)           1   →      1               
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                   17.69 ms →   6.46 ms    (-63.51%)           1   →      1               
+ │ │ │ ├ sirius::Local_operator::apply_h                                   8.41 ms →   5.86 ms    (-30.39%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.29 μs →   2.39 μs     (+4.51%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.18 μs →   1.55 μs    (+30.88%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           345.00 ns → 290.00 ns    (-15.94%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          372.00 ns → 489.00 ns    (+31.45%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                                       57.52 μs                                   1               
+ │ │ │ ├ sirius::Beta_projectors_base::inner                               6.01 ms → 188.43 μs    (-96.87%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                                 1.57 ms → 159.64 μs    (-89.85%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                   291.31 μs → 159.64 μs    (-45.20%)           2   →      2               
+ │ │ │ └ sddk::inner                                                     284.97 μs → 153.91 μs    (-45.99%)           2   →      2               
+ │ │ │   └ sddk::inner|local                                             277.39 μs →  15.34 μs    (-94.47%)           2   →      2               
  │ │ ├ Eigensolver_lapack|zhegvx                                          27.19 ms                                    1                          
  │ │ ├ Eigensolver_cuda|zhegvdx                                                       16.33 ms                                   1               
+ │ │ └ sddk::transform                                                   337.72 μs →  99.07 μs    (-70.67%)           1   →      1               
+ │ │   ├ sddk::transform|init                                             67.46 μs →  10.27 μs    (-84.78%)           1   →      1               
+ │ │   └ sddk::transform|local                                           257.40 μs →  11.64 μs    (-95.48%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                                           414.00 ns                                   1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.24 s  →   2.30 s      (+2.76%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function                                    100.37 μs → 147.06 μs    (+46.52%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        100.78 ms → 103.21 ms     (+2.42%)          22   →     22               
- │ │ ├ sirius::Hamiltonian0                                              341.18 μs → 482.54 μs    (+41.43%)          22   →     22               
  │ │ │ ├ sirius::Local_operator                                          320.99 μs → 339.62 μs     (+5.80%)          22   →     22               
+ │ │ │ │ ├ sirius::Smooth_periodic_function                               32.24 μs →  28.30 μs    (-12.23%)          22   →     22               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               272.65 μs → 247.74 μs     (-9.14%)          22   →     22               
- │ │ │ ├ sirius::Non_local_operator                                      865.77 ns →  36.51 μs  (+4116.99%)          44   →     44               
- │ │ │ ├ sirius::D_operator::initialize                                    7.11 μs →  32.10 μs   (+351.55%)          22   →     22               
- │ │ │ └ sirius::Q_operator::initialize                                    5.50 μs →  27.15 μs   (+393.67%)          22   →     22               
- │ │ ├ sirius::Band::solve                                                37.69 ms →  43.42 ms    (+15.22%)          22   →     22               
- │ │ │ ├ sirius::Hamiltonian_k                                            18.49 μs →  31.54 μs    (+70.59%)          22   →     22               
- │ │ │ │ ├ sirius::Local_operator::prepare_k                              17.51 μs →  26.40 μs    (+50.76%)          22   →     22               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                                       3.70 μs                                  22               
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.63 ms →  38.37 ms    (+14.08%)          22   →     22               
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             12.37 μs → 648.52 μs  (+5142.58%)          22   →     22               
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        862.80 ns →  78.41 μs  (+8987.26%)         132   →    132               
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           702.84 μs →   1.14 ms    (+61.59%)          22   →     22               
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.75 μs →  13.21 μs    (+22.93%)          22   →     22               
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       219.25 μs → 341.64 μs    (+55.82%)          66   →     66               
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              32.91 ms →  36.39 ms    (+10.59%)          22   →     22               
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.20 ms →   4.13 ms    (-20.51%)          87   →     87               
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.31 ms →   3.57 ms    (-17.07%)          87   →     87               
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.10 μs →   1.77 μs    (-15.67%)          87   →     87               
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.82 μs →   1.46 μs    (-19.67%)          87   →     87               
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     554.29 ns → 398.93 ns    (-28.03%)          87   →     87               
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    518.85 ns → 620.21 ns    (+19.53%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                                 51.34 μs                                  87               
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       286.85 μs → 145.60 μs    (-49.24%)          87   →     87               
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                         274.11 μs → 173.29 μs    (-36.78%)         174   →    174               
+ │ │ │ │   ├ sddk::orthogonalize                                         888.07 μs → 447.60 μs    (-49.60%)          87   →     87               
+ │ │ │ │   │ ├ sddk::inner                                               140.71 μs → 109.25 μs    (-22.36%)         152   →    152               
+ │ │ │ │   │ │ └ sddk::inner|local                                       139.12 μs →  15.84 μs    (-88.61%)         152   →    152               
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.25 μs → 127.58 μs   (+295.61%)          87   →     87               
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                             248.81 μs →  52.07 μs    (-79.07%)          87   →     87               
+ │ │ │ │   │ └ sddk::transform                                           473.35 μs →  97.47 μs    (-79.41%)          65   →     65               
+ │ │ │ │   │   ├ sddk::transform|init                                     76.64 μs →  18.25 μs    (-76.19%)          65   →     65               
+ │ │ │ │   │   └ sddk::transform|local                                   131.59 μs →   7.99 μs    (-93.93%)         195   →    195               
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             210.43 μs → 130.46 μs    (-38.01%)          87   →     87               
+ │ │ │ │   │ └ sddk::inner                                               195.33 μs → 115.34 μs    (-40.95%)          87   →     87               
+ │ │ │ │   │   └ sddk::inner|local                                       194.29 μs →  17.28 μs    (-91.10%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   996.58 μs                                   87                          
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                                  4.13 ms                                  87               
+ │ │ │ │   ├ sirius::residuals                                           572.96 μs → 275.44 μs    (-51.93%)          86   →     86               
+ │ │ │ │   │ ├ sddk::transform                                           417.67 μs →  99.06 μs    (-76.28%)          68   →     68               
+ │ │ │ │   │ │ ├ sddk::transform|init                                     64.16 μs →  13.31 μs    (-79.26%)          68   →     68               
+ │ │ │ │   │ │ └ sddk::transform|local                                   175.77 μs →  10.89 μs    (-93.81%)         136   →    136               
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               296.63 μs → 183.36 μs    (-38.19%)          68   →     68               
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     879.51 μs → 156.01 μs    (-82.26%)          38   →     38               
+ │ │ │ │     └ sddk::transform                                           533.88 μs →  98.47 μs    (-81.56%)          54   →     54               
+ │ │ │ │       ├ sddk::transform|init                                     75.04 μs →  10.34 μs    (-86.22%)          54   →     54               
+ │ │ │ │       └ sddk::transform|local                                   352.56 μs →   9.56 μs    (-97.29%)          70   →     70               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                                       381.09 ns                                  22               
+ │ │ │ └ sirius::K_point_set::sync_band_energies                          20.61 μs →  16.59 μs    (-19.50%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        202.07 μs → 193.80 μs     (-4.09%)          22   →     22               
+ │ │ ├ sirius::Density::generate                                          37.10 ms →  26.47 ms    (-28.64%)          22   →     22               
+ │ │ │ ├ sirius::Density::generate_valence                                28.80 ms →  18.27 ms    (-36.56%)          22   →     22               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.94 μs →   2.39 μs    (-18.85%)          22   →     22               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.65 μs →   2.12 μs    (-19.95%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  410.06 μs → 427.82 μs     (+4.33%)          22   →     22               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                                     3.19 μs                                  22               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                                  200.16 μs                                  22               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         385.04 μs → 144.06 μs    (-62.59%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                                   562.86 ns                                  22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.87 ms →   2.78 ms     (-3.31%)          22   →     22               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               140.13 μs → 193.48 μs    (+38.08%)          22   →     22               
+ │ │ │ │ └ sirius::Density::augment                                       25.02 ms →  14.45 ms    (-42.25%)          22   →     22               
+ │ │ │ │   └ sirius::Density::generate_rho_aug                            25.00 ms →  14.43 ms    (-42.27%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      4.26 ms                                   66                          
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       2.81 ms                                   66                          
  │ │ │ ├ sirius::Field4D::symmetrize                                       4.30 ms →   4.39 ms     (+1.94%)          22   →     22               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 4.30 ms →   4.39 ms     (+1.95%)          22   →     22               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                            982.45 μs →   1.12 ms    (+13.55%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.30 ms →   2.22 ms     (-3.63%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           996.10 μs →   1.03 ms     (+3.57%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.67 ms →   3.37 ms     (-8.36%)          22   →     22               
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 321.83 μs → 447.05 μs    (+38.91%)          22   →     22               
- │ │ ├ sirius::Density::mix                                                4.97 ms →   5.69 ms    (+14.60%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     22.97 μs →  23.80 μs     (+3.59%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 253.51 μs → 270.86 μs     (+6.84%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         250.48 μs → 250.49 μs     (+0.00%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                250.30 μs → 250.35 μs     (+0.02%)         274   →    274               
- │ │ │ └ sirius::Density::mixer_output                                   191.53 μs → 314.63 μs    (+64.27%)          22   →     22               
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform               177.59 μs → 300.76 μs    (+69.35%)          22   →     22               
- │ │ ├ sirius::Potential::generate                                        13.42 ms →  19.78 ms    (+47.40%)          22   →     22               
  │ │ │ ├ sirius::Potential::poisson                                        1.79 ms →   1.74 ms     (-2.85%)          22   →     22               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               208.28 μs → 320.16 μs    (+53.72%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               263.00 μs → 281.16 μs     (+6.91%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       261.48 μs → 253.62 μs     (-3.00%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              261.16 μs → 253.38 μs     (-2.98%)          22   →     22               
- │ │ │ ├ sirius::Periodic_function::add                                   10.78 μs →  17.48 μs    (+62.07%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.11 ms →   2.17 ms     (+2.99%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.05 ms →   2.12 ms     (+3.25%)          22   →     22               
- │ │ │ │   ├ sirius::Smooth_periodic_function                             29.46 μs →  32.71 μs    (+11.03%)          44   →     44               
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             202.33 μs → 301.61 μs    (+49.07%)          22   →     22               
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 156.28 μs → 294.26 μs    (+88.29%)          22   →     22               
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     9.29 ms →  15.47 ms    (+66.56%)          22   →     22               
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             266.41 ns → 141.50 ns    (-46.89%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.94 ms →   3.85 ms     (-2.18%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.94 ms →   3.85 ms     (-2.17%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              621.75 μs → 603.05 μs     (-3.01%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.31 ms →   2.23 ms     (-3.47%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             979.46 μs → 995.66 μs     (+1.65%)          22   →     22               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                   240.59 μs → 377.08 μs    (+56.73%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   250.01 μs → 252.48 μs     (+0.99%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           247.53 μs → 246.73 μs     (-0.32%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  247.25 μs → 246.60 μs     (-0.26%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            258.12 μs → 254.58 μs     (-1.37%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    256.02 μs → 253.35 μs     (-1.04%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              238.10 μs → 243.76 μs     (+2.38%)          22   →     22               
+ │ │ └ sirius::Density::get_magnetisation                                 51.38 μs →  43.07 μs    (-16.17%)          22   →     22               
+ │ │   └ sirius::Density::compute_atomic_mag_mom                          49.57 μs →  41.80 μs    (-15.66%)          22   →     22               
- │ ├ sirius::Smooth_periodic_function::gather_f_pw                       186.30 μs → 236.91 μs    (+27.17%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     245.06 μs → 240.16 μs     (-2.00%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             244.13 μs → 237.03 μs     (-2.91%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    244.02 μs → 236.92 μs     (-2.91%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              245.64 μs → 245.68 μs     (+0.02%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      244.15 μs → 244.25 μs     (+0.04%)           3   →      3               
  ├ sirius::Stress|kin                                                    314.93 μs → 307.45 μs     (-2.38%)           1   →      1               
  ├ sirius::Stress|har                                                    586.36 μs → 581.83 μs     (-0.77%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.77 ms →   1.79 ms     (+1.27%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.31 ms →   3.04 ms     (-8.19%)           1   →      1               
+ │ └ sirius::Simulation_context::make_periodic_function                    1.24 ms →   1.09 ms    (-11.48%)           2   →      2               
- ├ sirius::Smooth_periodic_function::fft_transform                       215.95 μs → 361.06 μs    (+67.20%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      19.46 μs →  18.12 μs     (-6.87%)           1   →      1               
+ ├ sirius::Simulation_context::make_periodic_function                      1.28 ms →   1.12 ms    (-13.11%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       259.77 μs → 257.67 μs     (-0.81%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               244.48 μs → 242.46 μs     (-0.83%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      244.32 μs → 242.31 μs     (-0.82%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                259.48 μs → 266.04 μs     (+2.53%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        258.20 μs → 252.61 μs     (-2.16%)           2   →      2               
+ ├ sirius::Stress|us                                                     327.21 ms → 189.40 ms    (-42.12%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     196.21 μs → 325.76 μs    (+66.02%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             77.13 ms →  79.58 ms     (+3.17%)           1   →      1               
- │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   589.24 μs → 730.42 μs    (+23.96%)           3   →      3               
  │ ├ sirius::Stress|us|phase_fac                                           1.27 ms →   1.15 ms     (-9.47%)           3   →      3               
+ │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.35 ms →  35.85 μs    (-99.84%)           9   →      9               
+ │ ├ sirius::Stress|us|prepare                                            72.13 μs →  58.53 μs    (-18.85%)          27   →     27               
- │ └ sirius::Stress|us|gemm                                                1.30 ms →   3.77 ms   (+188.99%)          27   →     27               
+ ├ sirius::Stress|nonloc                                                  14.52 ms →  12.75 ms    (-12.20%)           1   →      1               
+ │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.88 ms →   5.07 ms    (-13.91%)           1   →      1               
+ │ └ sirius::Non_local_functor::add_k_point                                8.16 ms →   7.05 ms    (-13.63%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               340.15 μs                                   10                          
- │   ├ sirius::Beta_projectors_base::prepare                               3.69 μs →   1.58 ms (+42681.12%)           1   →      2     (+100.00%)
+ │   ├ sirius::Beta_projectors_base::generate                            275.15 μs →  53.74 μs    (-80.47%)           9   →     10      (+11.11%)
  │   ├ sirius::Beta_projectors_base::inner                                           116.83 μs                                  10               
- │   └ sirius::Beta_projectors_base::dismiss                              85.00 ns →   1.04 μs  (+1126.47%)           1   →      2     (+100.00%)
+ ├ sirius::Force::calc_forces_vloc                                         1.44 ms →   1.24 ms    (-13.97%)           1   →      1               
- ├ sirius::Force::calc_forces_us                                          23.97 ms →  79.68 ms   (+232.43%)           1   →      1               
- │ └ sirius::Smooth_periodic_function::fft_transform                     252.07 μs → 421.64 μs    (+67.27%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       4.17 ms →   4.24 ms     (+1.62%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.95 ms →   2.91 ms     (-1.42%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               340.77 μs                                    4                          
- │   ├ sirius::Beta_projectors_base::prepare                               2.92 μs → 364.89 μs (+12387.75%)           1   →      2     (+100.00%)
+ │   ├ sirius::Beta_projectors_base::generate                            276.43 μs → 175.64 μs    (-36.46%)           3   →      4      (+33.33%)
  │   ├ sirius::Beta_projectors_base::inner                                           176.12 μs                                   4               
- │   └ sirius::Beta_projectors_base::dismiss                              84.00 ns → 892.00 ns   (+961.90%)           1   →      2     (+100.00%)
- ├ sirius::Force::calc_forces_core                                         1.14 ms →   1.46 ms    (+28.51%)           1   →      1               
- │ └ sirius::Smooth_periodic_function::fft_transform                     211.89 μs → 403.95 μs    (+90.64%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       12.70 ms →  12.43 ms     (-2.12%)           1   →      1               
- ├ sirius::Force::calc_forces_scf_corr                                   689.06 μs → 938.22 μs    (+36.16%)           1   →      1               
+ ├ sirius::Force::hubbard_force                                            1.45 μs → 832.00 ns    (-42.78%)           1   →      1               
- └ sirius::finalize                                                      124.86 ms → 151.95 ms    (+21.70%)           1   →      1               
```
