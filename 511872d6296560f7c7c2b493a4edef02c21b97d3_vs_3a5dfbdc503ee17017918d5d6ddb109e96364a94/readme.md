# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  123.87 s  → 132.24 s      (+6.76%)           1   →      1               
  ├ sirius::initialize                                                      3.11 s  →   3.03 s      (-2.57%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.93 s  →   3.84 s      (-2.38%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                61.81 ms → 427.51 μs    (-99.31%)           1   →      1               
  │ ├ sirius::Unit_cell::initialize                                       174.49 ms → 175.91 ms     (+0.82%)           1   →      1               
  │ │ ├ sirius::Atom_type::init                                            79.46 ms →  78.50 ms     (-1.21%)           2   →      2               
- │ │ └ sirius::Unit_cell::update                                          15.47 ms →  18.81 ms    (+21.55%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.86 ms →   3.97 ms     (+2.88%)           1   →      1               
- │ │   └ sirius::Unit_cell::get_symmetry                                  11.55 ms →  14.78 ms    (+27.95%)           1   →      1               
- │ │     └ sirius::Unit_cell_symmetry                                     11.49 ms →  14.70 ms    (+27.94%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.75 ms →   2.78 ms     (+0.82%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            473.23 μs → 519.00 μs     (+9.67%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               14.96 μs →  15.67 μs     (+4.76%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.60 s  →   3.62 s      (+0.54%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           7.12 ms →   7.15 ms     (+0.36%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.83 ms →   3.69 ms     (-3.59%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.25 ms →   3.40 ms     (+4.66%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.20 ms →   3.36 ms     (+5.12%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.69 ms →   2.78 ms     (+3.53%)           1   →      1               
- │   │     ├ sirius::Unit_cell_symmetry|equiv                            470.16 μs → 538.54 μs    (+14.54%)           1   →      1               
+ │   │     └ sirius::Unit_cell_symmetry|mag                               18.16 μs →  14.86 μs    (-18.16%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      212.47 ms → 210.78 ms     (-0.80%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.14 ms →  15.14 ms     (-0.01%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.53 ms →  13.26 ms     (-2.00%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.31 ms →  56.34 ms     (+0.06%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.10 ms →  45.16 ms     (+0.15%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.11 ms →  60.43 ms     (+0.54%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.03 ms →  94.48 ms     (+1.56%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     69.64 ms →  70.85 ms     (+1.74%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 107.27 ms →  96.80 ms     (-9.76%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  2.09 ms →   1.98 ms     (-5.40%)           1   →      1               
- │   └ sirius::Augmentation_operator::generate_pw_coeffs                 556.81 ms → 664.12 ms    (+19.27%)           2   →      2               
+ ├ sirius::K_point_set::create_k_mesh                                    140.94 ms →  89.25 ms    (-36.67%)           1   →      1               
  │ ├ sirius::K_point::K_point                                              1.90 μs →   1.78 μs     (-5.91%)           4   →      4               
+ │ └ sirius::K_point_set::initialize                                     140.87 ms →  89.19 ms    (-36.69%)           1   →      1               
  │   └ sirius::K_point::initialize                                        28.17 ms →  27.65 ms     (-1.84%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  11.16 ms →  10.83 ms     (-2.98%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                5.04 ms →   4.88 ms     (-3.20%)           1   →      1               
- │     ├ sddk::matrix_storage::matrix_storage                             10.34 μs →  11.41 μs    (+10.33%)           1   →      1               
  │     └ sirius::K_point::update                                          14.14 ms →  14.00 ms     (-1.03%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.17 ms →  10.12 ms     (-0.43%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.20 ms →   8.29 ms     (+1.06%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.58 ms →   2.58 ms     (+0.08%)           2   →      2               
  ├ sirius::Potential                                                      51.30 ms →  49.76 ms     (-3.01%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.90 ms →   2.94 ms     (+1.33%)           6   →      6               
  │ └ sirius::Potential::update                                            33.32 ms →  31.51 ms     (-5.43%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                        32.91 ms →  31.11 ms     (-5.46%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               24.08 ms →  26.14 ms     (+8.56%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   8.28 ms →   4.44 ms    (-46.37%)           1   →      1               
  ├ sirius::Density                                                        41.20 ms →  38.28 ms     (-7.08%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.82 ms →   2.82 ms     (-0.06%)           2   →      2               
  │ └ sirius::Density::update                                              35.42 ms →  32.50 ms     (-8.24%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density               35.20 ms →  32.27 ms     (-8.31%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.32 μs →  79.19 μs     (+2.42%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function               24.15 ms →  26.04 ms     (+7.82%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  10.68 ms →   5.87 ms    (-45.07%)           1   →      1               
  ├ sirius::Density::initial_density                                       60.53 ms →  56.49 ms     (-6.69%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                   25.13 ms →  26.33 ms     (+4.76%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       8.19 ms →   5.69 ms    (-30.49%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  5.40 ms →   5.09 ms     (-5.72%)           1   →      1               
  ├ sirius::Potential::generate                                           368.69 ms → 363.99 ms     (-1.27%)           1   →      1               
+ │ ├ sirius::Potential::poisson                                           41.59 ms →  36.50 ms    (-12.22%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                    12.50 ms →   5.49 ms    (-56.11%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     5.91 ms →   5.67 ms     (-4.07%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.85 ms →   4.84 ms     (-0.09%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.84 ms →   4.84 ms     (-0.04%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      786.33 μs → 777.04 μs     (-1.18%)           2   →      2               
  │ ├ sirius::Potential::xc                                                50.86 ms →  51.74 ms     (+1.72%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               49.66 ms →  50.53 ms     (+1.75%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.55 ms →   2.54 ms     (-0.51%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.07 ms →   4.41 ms     (+8.30%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.59 ms →   3.69 ms     (+2.71%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       269.66 ms → 269.13 ms     (-0.19%)           1   →      1               
+ │ └ sirius::Potential::generate_PAW_effective_potential                 169.00 ns →  77.00 ns    (-54.44%)           1   →      1               
- ├ sirius::Hamiltonian0                                                    6.50 ms →   8.06 ms    (+24.02%)           1   →      1               
- │ ├ sirius::Local_operator                                                5.93 ms →   7.29 ms    (+22.91%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.76 ms →   2.75 ms     (-0.41%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.36 ms →   3.60 ms    (+52.28%)           1   →      1               
- │ ├ sirius::Non_local_operator                                          105.62 μs → 248.83 μs   (+135.59%)           2   →      2               
+ │ ├ sirius::D_operator::initialize                                      153.04 μs → 103.47 μs    (-32.39%)           1   →      1               
+ │ └ sirius::Q_operator::initialize                                      115.17 μs →  95.18 μs    (-17.36%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.28 s  →   1.30 s      (+1.36%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                53.21 ms →  54.74 ms     (+2.88%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 370.78 μs → 315.43 μs    (-14.93%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              52.84 ms →  54.43 ms     (+3.00%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.23 s  →   1.24 s      (+1.30%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                               78.76 ms →  76.73 ms     (-2.58%)           4   →      4               
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                    37.22 ms →  55.50 ms    (+49.12%)           1   →      1               
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                             6.66 ms →   8.67 ms    (+30.10%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  313.40 ms → 336.35 ms     (+7.32%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 245.41 ms → 248.01 ms     (+1.06%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.79 μs →   3.74 μs     (-1.34%)           1   →      1               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.81 μs →   2.88 μs     (+2.67%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           425.00 ns → 419.00 ns     (-1.41%)           1   →      1               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          626.00 ns → 671.00 ns     (+7.19%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.18 ms →   3.18 ms     (-0.21%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                              21.29 ms →  21.41 ms     (+0.54%)           1   →      1               
- │ │ │ └ sirius::Non_local_operator::apply                                21.73 ms →  31.85 ms    (+46.55%)           2   →      2               
- │ │ ├ sirius::Band::set_subspace_mtrx                                     5.32 ms →  14.28 ms   (+168.32%)           2   →      2               
- │ │ │ └ sddk::inner                                                       5.11 ms →  14.07 ms   (+175.23%)           2   →      2               
  │ │ │   └ sddk::inner|local                                              25.60 μs →  27.43 μs     (+7.15%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          270.58 ms → 232.08 ms    (-14.23%)           1   →      1               
- │ │ └ sddk::transform                                                     2.82 ms →   5.22 ms    (+85.05%)           1   →      1               
  │ │   ├ sddk::transform|init                                             14.50 μs →  14.52 μs     (+0.14%)           1   →      1               
- │ │   └ sddk::transform|local                                            17.13 μs →  21.04 μs    (+22.83%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               562.00 ns → 416.00 ns    (-25.98%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    113.81 s  → 122.35 s      (+7.51%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.46 ms →   2.44 ms     (-1.09%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          2.52 s  →   2.49 s      (-1.33%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Hamiltonian0                                                5.03 ms →   5.00 ms     (-0.68%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Local_operator                                            4.33 ms →   4.23 ms     (-2.31%)          45   →     49       (+8.89%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                              558.52 μs → 560.46 μs     (+0.35%)          45   →     49       (+8.89%)
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.68 ms →   2.68 ms     (-0.34%)          45   →     49       (+8.89%)
- │ │ │ ├ sirius::Non_local_operator                                      201.11 μs → 237.25 μs    (+17.97%)          90   →     98       (+8.89%)
  │ │ │ ├ sirius::D_operator::initialize                                  123.72 μs → 118.78 μs     (-3.99%)          45   →     49       (+8.89%)
  │ │ │ └ sirius::Q_operator::initialize                                   95.05 μs →  96.17 μs     (+1.18%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Band::solve                                                 1.29 s  →   1.26 s      (-2.58%)          45   →     49       (+8.89%)
- │ │ │ ├ sirius::Hamiltonian_k                                           243.06 μs → 276.70 μs    (+13.84%)          45   →     49       (+8.89%)
- │ │ │ │ ├ sirius::Local_operator::prepare_k                             234.47 μs → 268.12 μs    (+14.35%)          45   →     49       (+8.89%)
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           6.29 μs →   6.29 μs     (-0.03%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.26 s  →   1.23 s      (-2.55%)          45   →     49       (+8.89%)
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             47.32 ms →  45.69 ms     (-3.45%)          45   →     49       (+8.89%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          3.36 ms →   3.20 ms     (-4.51%)         270   →    294       (+8.89%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            18.15 ms →  17.42 ms     (-3.98%)          45   →     49       (+8.89%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       454.64 μs → 460.17 μs     (+1.22%)          45   →     49       (+8.89%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.66 ms →   8.29 ms     (-4.22%)          90   →     98       (+8.89%)
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.19 s  →   1.16 s      (-2.44%)          45   →     49       (+8.89%)
! │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             36.43 ms →  34.66 ms     (-4.85%)         800   →    899      (+12.38%)
! │ │ │ │   │ ├ sirius::Local_operator::apply_h                            18.61 ms →  17.78 ms     (-4.46%)         800   →    899      (+12.38%)
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.91 μs →   1.99 μs     (+4.40%)         800   →    899      (+12.38%)
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.58 μs →   1.67 μs     (+5.88%)         800   →    899      (+12.38%)
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     444.57 ns → 468.99 ns     (+5.49%)         800   →    899      (+12.38%)
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    635.96 ns → 660.86 ns     (+3.91%)         800   →    899      (+12.38%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.89 ms →   2.75 ms     (-5.03%)         800   →    899      (+12.38%)
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         2.50 ms →   2.36 ms     (-5.48%)         800   →    899      (+12.38%)
! │ │ │ │   │ └ sirius::Non_local_operator::apply                           6.20 ms →   5.88 ms     (-5.26%)        1.60 K →   1.80 K    (+12.38%)
! │ │ │ │   ├ sddk::orthogonalize                                           3.87 ms →   3.64 ms     (-5.97%)         800   →    899      (+12.38%)
! │ │ │ │   │ ├ sddk::inner                                               569.91 μs → 513.72 μs     (-9.86%)        1.55 K →   1.75 K    (+12.48%)
! │ │ │ │   │ │ └ sddk::inner|local                                        23.18 μs →  23.18 μs     (+0.02%)        1.55 K →   1.75 K    (+12.48%)
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  89.45 μs →  83.96 μs     (-6.13%)         800   →    899      (+12.38%)
! │ │ │ │   │ ├ sddk::orthogonalize|transform                               1.43 ms →   1.35 ms     (-5.40%)         800   →    899      (+12.38%)
! │ │ │ │   │ └ sddk::transform                                             1.32 ms →   1.27 ms     (-3.43%)         755   →    850      (+12.58%)
! │ │ │ │   │   ├ sddk::transform|init                                     20.32 μs →  20.40 μs     (+0.41%)         755   →    850      (+12.58%)
! │ │ │ │   │   └ sddk::transform|local                                     8.05 μs →   8.17 μs     (+1.47%)        2.27 K →   2.55 K    (+12.58%)
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             923.51 μs → 881.45 μs     (-4.55%)         800   →    899      (+12.38%)
! │ │ │ │   │ └ sddk::inner                                               855.47 μs → 810.28 μs     (-5.28%)         800   →    899      (+12.38%)
! │ │ │ │   │   └ sddk::inner|local                                        22.09 μs →  21.77 μs     (-1.44%)         800   →    899      (+12.38%)
! │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     22.93 ms →  21.73 ms     (-5.23%)         800   →    899      (+12.38%)
+ │ │ │ │   ├ sirius::residuals                                             2.05 ms →   1.78 ms    (-12.91%)         762   →    856      (+12.34%)
+ │ │ │ │   │ ├ sddk::transform                                             1.04 ms → 917.50 μs    (-11.84%)         759   →    853      (+12.38%)
! │ │ │ │   │ │ ├ sddk::transform|init                                     17.78 μs →  17.57 μs     (-1.17%)         759   →    853      (+12.38%)
! │ │ │ │   │ │ └ sddk::transform|local                                    10.30 μs →  10.48 μs     (+1.78%)        1.52 K →   1.71 K    (+12.38%)
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               922.87 μs → 782.12 μs    (-15.25%)         759   →    853      (+12.38%)
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       6.62 ms →   5.36 ms    (-19.11%)          80   →     84       (+5.00%)
+ │ │ │ │     └ sddk::transform                                             4.57 ms →   3.74 ms    (-18.05%)         115   →    119       (+3.48%)
  │ │ │ │       ├ sddk::transform|init                                     10.77 μs →  11.15 μs     (+3.49%)         115   →    119       (+3.48%)
  │ │ │ │       └ sddk::transform|local                                     9.77 μs →  10.14 μs     (+3.76%)         150   →    154       (+2.67%)
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           540.58 ns → 584.04 ns     (+8.04%)          45   →     49       (+8.89%)
  │ │ │ └ sirius::K_point_set::sync_band_energies                          19.85 μs →  19.99 μs     (+0.66%)          45   →     49       (+8.89%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.54 ms →   1.46 ms     (-5.21%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Density::generate                                         565.76 ms → 567.73 ms     (+0.35%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Density::generate_valence                               394.03 ms → 401.66 ms     (+1.94%)          45   →     49       (+8.89%)
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.06 μs →   8.80 μs     (+9.20%)          45   →     49       (+8.89%)
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.15 μs →   7.65 μs     (+6.92%)          45   →     49       (+8.89%)
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   40.51 ms →  35.10 ms    (-13.36%)          45   →     49       (+8.89%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.32 μs →   7.60 μs     (+3.74%)          45   →     49       (+8.89%)
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        6.78 ms →   5.46 ms    (-19.49%)          45   →     49       (+8.89%)
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          32.67 ms →  28.61 ms    (-12.43%)          45   →     49       (+8.89%)
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       591.36 ns → 591.45 ns     (+0.02%)          45   →     49       (+8.89%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  105.41 ms → 110.42 ms     (+4.75%)          45   →     49       (+8.89%)
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.85 ms →   2.05 ms    (+10.53%)          45   →     49       (+8.89%)
  │ │ │ │ └ sirius::Density::augment                                      207.46 ms → 219.47 ms     (+5.79%)          45   →     49       (+8.89%)
  │ │ │ │   └ sirius::Density::generate_rho_aug                           207.23 ms → 219.25 ms     (+5.80%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Field4D::symmetrize                                     144.22 ms → 137.63 ms     (-4.57%)          45   →     49       (+8.89%)
  │ │ │ │ └ sirius::symmetrize_function|fpw                               144.22 ms → 137.63 ms     (-4.57%)          45   →     49       (+8.89%)
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             62.25 ms →  54.52 ms    (-12.42%)          45   →     49       (+8.89%)
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        68.73 ms →  69.87 ms     (+1.66%)          45   →     49       (+8.89%)
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.60 ms →  12.61 ms     (+0.03%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.73 ms →  24.21 ms     (+2.02%)          45   →     49       (+8.89%)
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   3.78 ms →   4.23 ms    (+12.00%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Density::mix                                              148.31 ms → 152.27 ms     (+2.67%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Density::mixer_input                                      1.01 ms → 938.61 μs     (-7.03%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Periodic_function|inner                                   4.67 ms →   4.89 ms     (+4.70%)         619   →    679       (+9.69%)
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.62 ms →   4.61 ms     (-0.25%)         619   →    679       (+9.69%)
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.62 ms →   4.61 ms     (-0.25%)         619   →    679       (+9.69%)
- │ │ │ └ sirius::Density::mixer_output                                     4.59 ms →   5.29 ms    (+15.24%)          45   →     49       (+8.89%)
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 3.86 ms →   4.62 ms    (+19.66%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Potential::generate                                       362.70 ms → 355.92 ms     (-1.87%)          45   →     49       (+8.89%)
+ │ │ │ ├ sirius::Potential::poisson                                       42.28 ms →  35.85 ms    (-15.20%)          45   →     49       (+8.89%)
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                13.21 ms →   4.91 ms    (-62.86%)          45   →     49       (+8.89%)
  │ │ │ │ └ sirius::Periodic_function|inner                                 5.93 ms →   5.61 ms     (-5.31%)          45   →     49       (+8.89%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.84 ms →   4.84 ms     (-0.06%)          45   →     49       (+8.89%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.84 ms →   4.84 ms     (-0.06%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Periodic_function::add                                  841.98 μs → 792.54 μs     (-5.87%)          90   →     98       (+8.89%)
  │ │ │ ├ sirius::Potential::xc                                            44.59 ms →  44.79 ms     (+0.46%)          45   →     49       (+8.89%)
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           43.41 ms →  43.62 ms     (+0.48%)          45   →     49       (+8.89%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                            663.39 μs → 664.68 μs     (+0.19%)          90   →     98       (+8.89%)
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.14 ms →   4.55 ms     (+9.94%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.87 ms →   3.68 ms     (-4.85%)          45   →     49       (+8.89%)
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.87 ms → 268.59 ms     (-0.10%)          45   →     49       (+8.89%)
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             164.60 ns → 138.08 ns    (-16.11%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Field4D::symmetrize                                        95.33 ms →  96.30 ms     (+1.02%)          45   →     49       (+8.89%)
  │ │ │ └ sirius::symmetrize_function|fpw                                  95.33 ms →  96.30 ms     (+1.02%)          45   →     49       (+8.89%)
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.57 ms →  13.27 ms     (-2.15%)          45   →     49       (+8.89%)
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          68.59 ms →  69.83 ms     (+1.80%)          45   →     49       (+8.89%)
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.54 ms →  12.57 ms     (+0.24%)          45   →     49       (+8.89%)
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     3.51 ms →   3.87 ms    (+10.33%)          45   →     49       (+8.89%)
  │ │ ├ sirius::Periodic_function|inner                                     4.81 ms →   4.67 ms     (-2.93%)         315   →    343       (+8.89%)
  │ │ │ └ sirius::Periodic_function|inner_local                             4.55 ms →   4.55 ms     (+0.03%)         315   →    343       (+8.89%)
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.55 ms →   4.55 ms     (+0.03%)         315   →    343       (+8.89%)
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.74 ms →   4.87 ms     (+2.90%)         135   →    147       (+8.89%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.73 ms →   4.87 ms     (+3.00%)         135   →    147       (+8.89%)
  │ │ ├ sirius::Periodic_function::integrate                                4.54 ms →   4.54 ms     (+0.00%)          45   →     49       (+8.89%)
  │ │ └ sirius::Density::get_magnetisation                                 75.22 μs →  75.56 μs     (+0.44%)          45   →     49       (+8.89%)
  │ │   └ sirius::Density::compute_atomic_mag_mom                          70.12 μs →  70.81 μs     (+0.98%)          45   →     49       (+8.89%)
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.83 ms →   5.73 ms     (-1.69%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.81 ms →   4.60 ms     (-4.40%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.81 ms →   4.54 ms     (-5.61%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.81 ms →   4.54 ms     (-5.65%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                5.02 ms →   4.71 ms     (-6.08%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        5.02 ms →   4.71 ms     (-6.10%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.80 ms →   4.54 ms     (-5.36%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.79 ms →   4.53 ms     (-5.36%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.79 ms →   4.53 ms     (-5.36%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.99 ms →   4.78 ms     (-4.26%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.99 ms →   4.78 ms     (-4.26%)           1   →      1               
  └ sirius::finalize                                                      749.31 ms → 746.51 ms     (-0.37%)           1   →      1               
```
