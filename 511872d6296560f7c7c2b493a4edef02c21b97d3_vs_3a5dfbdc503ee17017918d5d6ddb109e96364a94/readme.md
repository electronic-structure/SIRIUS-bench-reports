# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                  617.67 s  → 150.58 s     (-75.62%)           1   →      1               
  ├ sirius::initialize                                                      2.96 s  →   2.91 s      (-1.94%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  2.79 s  →   3.59 s     (+28.39%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                 1.54 ms → 896.24 μs    (-41.88%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       148.75 ms → 163.75 ms    (+10.09%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                            64.33 ms →  72.00 ms    (+11.92%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          20.04 ms →  19.66 ms     (-1.85%)           1   →      1               
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        5.18 ms →   3.75 ms    (-27.57%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  14.85 ms →  15.86 ms     (+6.81%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     14.78 ms →  15.79 ms     (+6.80%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                3.05 ms →   2.75 ms     (-9.72%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            510.04 μs → 520.44 μs     (+2.04%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               17.77 μs →  17.10 μs     (-3.81%)           1   →      1               
- │ └ sirius::Simulation_context::update                                    2.60 s  →   3.23 s     (+24.13%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.84 ms →   6.95 ms     (+1.67%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.53 ms →   3.60 ms     (+1.94%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.30 ms →   3.30 ms     (-0.18%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.26 ms →   3.25 ms     (-0.19%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.72 ms →   2.69 ms     (-1.13%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            502.63 μs → 527.42 μs     (+4.93%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               14.00 μs →  13.98 μs     (-0.11%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      212.24 ms → 212.90 ms     (+0.31%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.14 ms →  15.16 ms     (+0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.26 ms →  13.24 ms     (-0.16%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.31 ms →  56.30 ms     (-0.01%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.05 ms →  45.06 ms     (+0.01%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.27 ms →  60.18 ms     (-0.13%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   93.84 ms →  92.61 ms     (-1.32%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     71.68 ms →  69.28 ms     (-3.34%)           2   →      2               
+ │   ├ sddk::Gvec_shells                                                 113.26 ms → 100.72 ms    (-11.07%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.99 ms →   1.96 ms     (-1.49%)           1   →      1               
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs                 574.97 ms → 465.40 ms    (-19.06%)           2   →      2               
+ ├ sirius::K_point_set::create_k_mesh                                    172.36 ms → 147.66 ms    (-14.33%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              3.15 μs →   2.16 μs    (-31.53%)           4   →      4               
+ │ └ sirius::K_point_set::initialize                                     172.29 ms → 147.59 ms    (-14.34%)           1   →      1               
+ │   └ sirius::K_point::initialize                                       171.99 ms →  28.02 ms    (-83.71%)           1   →      1               
+ │     ├ sirius::K_point::generate_gkvec                                  19.35 ms →  11.10 ms    (-42.63%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                5.21 ms →   4.94 ms     (-5.30%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                             12.81 μs →  10.20 μs    (-20.40%)           1   →      1               
+ │     └ sirius::K_point::update                                         149.68 ms →  14.06 ms    (-90.60%)           1   →      1               
+ │       └ sirius::Beta_projectors                                       146.35 ms →  10.17 ms    (-93.05%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                  8.64 ms →   8.19 ms     (-5.22%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      137.70 ms                                    1                          
  ├ sirius::Smooth_periodic_function                                        2.52 ms →   2.57 ms     (+1.96%)           2   →      2               
  ├ sirius::Potential                                                      57.59 ms →  53.20 ms     (-7.62%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.89 ms →   2.90 ms     (+0.24%)           6   →      6               
+ │ └ sirius::Potential::update                                            39.83 ms →  35.24 ms    (-11.51%)           1   →      1               
+ │   └ sirius::Potential::generate_local_potential                        39.43 ms →  34.85 ms    (-11.61%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               32.30 ms →  26.82 ms    (-16.99%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   6.51 ms →   7.51 ms    (+15.27%)           1   →      1               
+ ├ sirius::Density                                                        45.32 ms →  40.23 ms    (-11.23%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.82 ms →   2.83 ms     (+0.28%)           2   →      2               
+ │ └ sirius::Density::update                                              39.65 ms →  34.44 ms    (-13.15%)           1   →      1               
+ │   └ sirius::Density::generate_pseudo_core_charge_density               39.35 ms →  34.13 ms    (-13.27%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                76.04 μs →  77.54 μs     (+1.98%)           1   →      1               
+ │     ├ sirius::Simulation_context::make_periodic_function               33.10 ms →  27.29 ms    (-17.57%)           1   →      1               
- │     └ sirius::Smooth_periodic_function::fft_transform                   5.77 ms →   6.46 ms    (+11.95%)           1   →      1               
+ ├ sirius::Density::initial_density                                       68.12 ms →  60.61 ms    (-11.02%)           1   →      1               
+ │ ├ sirius::Simulation_context::make_periodic_function                   37.16 ms →  28.26 ms    (-23.93%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                       6.42 ms →   7.09 ms    (+10.51%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  4.57 ms →   4.52 ms     (-1.10%)           1   →      1               
+ ├ sirius::Potential::generate                                             2.59 s  → 369.83 ms    (-85.73%)           1   →      1               
+ │ ├ sirius::Potential::poisson                                           47.59 ms →  42.42 ms    (-10.87%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.62 ms →  10.54 ms    (+87.70%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     4.92 ms →   5.18 ms     (+5.31%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.77 ms →   4.84 ms     (+1.45%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.76 ms →   4.83 ms     (+1.44%)           1   →      1               
- │ ├ sirius::Periodic_function::add                                      647.24 μs → 796.01 μs    (+22.99%)           2   →      2               
  │ ├ sirius::Potential::xc                                                53.21 ms →  51.47 ms     (-3.28%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               52.03 ms →  50.26 ms     (-3.40%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.44 ms →   2.55 ms     (+4.63%)           2   →      2               
+ │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.50 ms →   4.82 ms    (-12.35%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       6.32 ms →   3.57 ms    (-43.46%)           1   →      1               
+ │ ├ sirius::Potential::generate_D_operator_matrix                         2.48 s  → 269.37 ms    (-89.15%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                 218.00 ns → 252.00 ns    (+15.60%)           1   →      1               
- ├ sirius::Hamiltonian0                                                    5.60 ms →   7.81 ms    (+39.42%)           1   →      1               
- │ ├ sirius::Local_operator                                                5.42 ms →   7.06 ms    (+30.24%)           1   →      1               
- │ │ ├ sirius::Smooth_periodic_function                                  617.01 μs →   2.74 ms   (+344.38%)           1   →      1               
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                     4.51 ms →   3.30 ms    (-26.74%)           1   →      1               
- │ ├ sirius::Non_local_operator                                            2.60 μs → 228.51 μs  (+8692.23%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                       59.21 μs → 109.49 μs    (+84.93%)           1   →      1               
- │ └ sirius::Q_operator::initialize                                       35.62 μs →  93.75 μs   (+163.19%)           1   →      1               
+ ├ sirius::Band::initialize_subspace                                       4.99 s  →   1.28 s     (-74.38%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                               277.55 μs →  63.13 ms (+22645.88%)           1   →      1               
  │ │ ├ sirius::Local_operator::prepare_k                                 274.91 μs → 301.14 μs     (+9.54%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                                          62.83 ms                                   1               
+ │ ├ sirius::Band::initialize_subspace|kp                                  4.99 s  →   1.22 s     (-75.65%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               14.96 μs →  88.92 ms (+594229.66%)           4   →      4               
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                    41.15 ms →  47.13 ms    (+14.55%)           1   →      1               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                            17.65 ms →   7.78 ms    (-55.91%)           1   →      1               
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    4.37 s  → 382.28 ms    (-91.26%)           1   →      1               
+ │ │ │ ├ sirius::Local_operator::apply_h                                   2.01 s  → 311.86 ms    (-84.46%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             5.05 μs →   3.68 μs    (-27.06%)           1   →      1               
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           3.30 μs →   2.68 μs    (-18.71%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           389.00 ns → 393.00 ns     (+1.03%)           1   →      1               
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                            2.03 μs → 626.00 ns    (-69.15%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                                        7.83 ms                                   1               
+ │ │ │ ├ sirius::Beta_projectors_base::inner                             738.91 ms →  21.27 ms    (-97.12%)           1   →      1               
+ │ │ │ └ sirius::Non_local_operator::apply                               779.82 ms →  20.64 ms    (-97.35%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                   177.73 ms →   5.20 ms    (-97.07%)           2   →      2               
+ │ │ │ └ sddk::inner                                                     177.69 ms →   4.99 ms    (-97.19%)           2   →      2               
+ │ │ │   └ sddk::inner|local                                             177.68 ms →  24.79 μs    (-99.99%)           2   →      2               
  │ │ ├ Eigensolver_lapack|zhegvx                                          53.22 ms                                    1                          
  │ │ ├ Eigensolver_cuda|zhegvdx                                                      200.75 ms                                   1               
+ │ │ └ sddk::transform                                                   136.85 ms →   2.82 ms    (-97.94%)           1   →      1               
+ │ │   ├ sddk::transform|init                                             32.49 ms →  14.58 μs    (-99.96%)           1   →      1               
+ │ │   └ sddk::transform|local                                           104.34 ms →  18.18 μs    (-99.98%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                                           461.00 ns                                   1               
+ ├ sirius::DFT_ground_state::scf_loop                                    603.62 s  → 141.02 s     (-76.64%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.52 ms →   2.43 ms     (-3.60%)          19   →     19               
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                         17.75 s  →   2.35 s     (-86.78%)          34   →     60      (+76.47%)
+ │ │ ├ sirius::Hamiltonian0                                                6.68 ms →   5.14 ms    (-23.03%)          34   →     60      (+76.47%)
+ │ │ │ ├ sirius::Local_operator                                            6.51 ms →   4.39 ms    (-32.65%)          34   →     60      (+76.47%)
! │ │ │ │ ├ sirius::Smooth_periodic_function                              551.90 μs → 557.54 μs     (+1.02%)          34   →     60      (+76.47%)
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 5.68 ms →   2.69 ms    (-52.67%)          34   →     60      (+76.47%)
- │ │ │ ├ sirius::Non_local_operator                                        2.39 μs → 232.55 μs  (+9622.27%)          68   →    120      (+76.47%)
- │ │ │ ├ sirius::D_operator::initialize                                   61.64 μs → 124.12 μs   (+101.36%)          34   →     60      (+76.47%)
- │ │ │ └ sirius::Q_operator::initialize                                   31.96 μs →  96.87 μs   (+203.08%)          34   →     60      (+76.47%)
+ │ │ ├ sirius::Band::solve                                                12.90 s  →   1.11 s     (-91.42%)          34   →     60      (+76.47%)
- │ │ │ ├ sirius::Hamiltonian_k                                           155.65 μs → 209.90 μs    (+34.86%)          34   →     60      (+76.47%)
- │ │ │ │ ├ sirius::Local_operator::prepare_k                             154.31 μs → 200.63 μs    (+30.01%)          34   →     60      (+76.47%)
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                                       6.72 μs                                  60               
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     12.13 s  →   1.08 s     (-91.08%)          34   →     60      (+76.47%)
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc            638.08 μs →  42.69 ms  (+6589.76%)          34   →     60      (+76.47%)
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        104.95 μs →   2.70 ms  (+2475.91%)         204   →    360      (+76.47%)
! │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            17.25 ms →  17.47 ms     (+1.29%)          34   →     60      (+76.47%)
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       433.75 μs → 484.91 μs    (+11.80%)          34   →     60      (+76.47%)
! │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.33 ms →   8.29 ms     (-0.48%)          68   →    120      (+76.47%)
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              12.11 s  →   1.01 s     (-91.62%)          34   →     60      (+76.47%)
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            473.86 ms →  35.61 ms    (-92.48%)         637   →    946      (+48.51%)
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                           139.24 ms →  18.43 ms    (-86.76%)         637   →    946      (+48.51%)
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       3.62 μs →   1.85 μs    (-48.94%)         637   →    946      (+48.51%)
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     3.08 μs →   1.54 μs    (-49.96%)         637   →    946      (+48.51%)
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     821.46 ns → 399.98 ns    (-51.31%)         637   →    946      (+48.51%)
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                      1.50 μs → 505.32 ns    (-66.32%)         637   →    946      (+48.51%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                                  2.65 ms                                 946               
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        93.66 ms →   2.35 ms    (-97.49%)         637   →    946      (+48.51%)
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                         119.77 ms →   6.09 ms    (-94.92%)        1.27 K →   1.89 K    (+48.51%)
+ │ │ │ │   ├ sddk::orthogonalize                                          79.86 ms →   3.88 ms    (-95.14%)         637   →    946      (+48.51%)
+ │ │ │ │   │ ├ sddk::inner                                                 9.15 ms → 636.51 μs    (-93.05%)        1.24 K →   1.83 K    (+47.74%)
+ │ │ │ │   │ │ └ sddk::inner|local                                         9.15 ms →  20.89 μs    (-99.77%)        1.24 K →   1.83 K    (+47.74%)
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  69.07 μs →  92.03 μs    (+33.24%)         637   →    946      (+48.51%)
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                              17.17 ms →   1.40 ms    (-91.82%)         637   →    946      (+48.51%)
+ │ │ │ │   │ └ sddk::transform                                            47.32 ms →   1.23 ms    (-97.41%)         603   →    886      (+46.93%)
+ │ │ │ │   │   ├ sddk::transform|init                                      1.93 ms →  17.99 μs    (-99.07%)         603   →    886      (+46.93%)
+ │ │ │ │   │   └ sddk::transform|local                                    15.13 ms →   7.10 μs    (-99.95%)        1.81 K →   2.66 K    (+46.93%)
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                              15.17 ms → 911.82 μs    (-93.99%)         637   →    946      (+48.51%)
+ │ │ │ │   │ └ sddk::inner                                                15.07 ms → 843.67 μs    (-94.40%)         637   →    946      (+48.51%)
+ │ │ │ │   │   └ sddk::inner|local                                        15.06 ms →  19.80 μs    (-99.87%)         637   →    946      (+48.51%)
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                    13.62 ms                                  637                          
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                                 21.86 ms                                 946               
+ │ │ │ │   ├ sirius::residuals                                            40.32 ms →   1.61 ms    (-96.00%)         607   →    902      (+48.60%)
+ │ │ │ │   │ ├ sddk::transform                                            34.15 ms → 892.41 μs    (-97.39%)         604   →    899      (+48.84%)
+ │ │ │ │   │ │ ├ sddk::transform|init                                      1.38 ms →  15.35 μs    (-98.89%)         604   →    899      (+48.84%)
+ │ │ │ │   │ │ └ sddk::transform|local                                    16.39 ms →   9.30 μs    (-99.94%)        1.21 K →   1.80 K    (+48.84%)
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 6.34 ms → 628.12 μs    (-90.10%)         604   →    899      (+48.84%)
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     223.37 ms →   5.24 ms    (-97.66%)          69   →     95      (+37.68%)
+ │ │ │ │     └ sddk::transform                                           139.50 ms →   3.79 ms    (-97.28%)         104   →    130      (+25.00%)
+ │ │ │ │       ├ sddk::transform|init                                      7.24 ms →  10.43 μs    (-99.86%)         104   →    130      (+25.00%)
+ │ │ │ │       └ sddk::transform|local                                    98.96 ms →   9.76 μs    (-99.99%)         139   →    165      (+18.71%)
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                                       555.93 ns                                  60               
+ │ │ │ └ sirius::K_point_set::sync_band_energies                          29.26 μs →  20.05 μs    (-31.48%)          34   →     60      (+76.47%)
! │ │ ├ sirius::K_point_set::find_band_occupancies                          1.55 ms →   1.48 ms     (-4.47%)          34   →     60      (+76.47%)
+ │ │ ├ sirius::Density::generate                                           1.92 s  → 567.30 ms    (-70.52%)          34   →     60      (+76.47%)
+ │ │ │ ├ sirius::Density::generate_valence                                 1.78 s  → 394.54 ms    (-77.84%)          34   →     60      (+76.47%)
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.99 μs →   9.89 μs    (+10.08%)          34   →     60      (+76.47%)
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           8.29 μs →   9.04 μs     (+9.08%)          34   →     60      (+76.47%)
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  468.46 ms →  40.73 ms    (-91.31%)          34   →     60      (+76.47%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                                     7.72 μs                                  60               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                                    6.77 ms                                  60               
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         467.30 ms →  32.93 ms    (-92.95%)          34   →     60      (+76.47%)
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                                   789.70 ns                                  60               
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  739.34 ms → 105.06 ms    (-85.79%)          34   →     60      (+76.47%)
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 3.50 ms →   2.25 ms    (-35.81%)          34   →     60      (+76.47%)
+ │ │ │ │ └ sirius::Density::augment                                      555.54 ms → 206.03 ms    (-62.91%)          34   →     60      (+76.47%)
+ │ │ │ │   └ sirius::Density::generate_rho_aug                           555.37 ms → 205.81 ms    (-62.94%)          34   →     60      (+76.47%)
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                    161.64 ms                                   68                          
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                      59.67 ms                                   68                          
- │ │ │ ├ sirius::Field4D::symmetrize                                     111.21 ms → 144.76 ms    (+30.16%)          34   →     60      (+76.47%)
- │ │ │ │ └ sirius::symmetrize_function|fpw                               111.21 ms → 144.76 ms    (+30.16%)          34   →     60      (+76.47%)
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             29.01 ms →  61.31 ms   (+111.37%)          34   →     60      (+76.47%)
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        68.86 ms →  70.20 ms     (+1.95%)          34   →     60      (+76.47%)
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.64 ms →  12.60 ms     (-0.25%)          34   →     60      (+76.47%)
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.69 ms →  23.79 ms     (+0.42%)          34   →     60      (+76.47%)
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   9.33 ms →   4.21 ms    (-54.81%)          34   →     60      (+76.47%)
! │ │ ├ sirius::Density::mix                                              146.57 ms → 151.10 ms     (+3.09%)          34   →     60      (+76.47%)
! │ │ │ ├ sirius::Density::mixer_input                                      1.03 ms →   1.01 ms     (-2.11%)          34   →     60      (+76.47%)
! │ │ │ ├ sirius::Periodic_function|inner                                   4.71 ms →   4.66 ms     (-1.16%)         454   →    844      (+85.90%)
! │ │ │ │ └ sirius::Periodic_function|inner_local                           4.62 ms →   4.61 ms     (-0.24%)         454   →    844      (+85.90%)
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.62 ms →   4.61 ms     (-0.24%)         454   →    844      (+85.90%)
+ │ │ │ └ sirius::Density::mixer_output                                     6.87 ms →   5.01 ms    (-26.98%)          34   →     60      (+76.47%)
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.12 ms →   4.37 ms    (-28.62%)          34   →     60      (+76.47%)
+ │ │ ├ sirius::Potential::generate                                         2.61 s  → 361.99 ms    (-86.12%)          34   →     60      (+76.47%)
+ │ │ │ ├ sirius::Potential::poisson                                       47.43 ms →  41.83 ms    (-11.82%)          34   →     60      (+76.47%)
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 5.57 ms →  10.31 ms    (+84.90%)          34   →     60      (+76.47%)
! │ │ │ │ └ sirius::Periodic_function|inner                                 4.80 ms →   4.90 ms     (+2.04%)          34   →     60      (+76.47%)
! │ │ │ │   └ sirius::Periodic_function|inner_local                         4.79 ms →   4.82 ms     (+0.76%)          34   →     60      (+76.47%)
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.79 ms →   4.82 ms     (+0.76%)          34   →     60      (+76.47%)
+ │ │ │ ├ sirius::Periodic_function::add                                  960.30 μs → 761.81 μs    (-20.67%)          68   →    120      (+76.47%)
+ │ │ │ ├ sirius::Potential::xc                                            51.65 ms →  44.90 ms    (-13.07%)          34   →     60      (+76.47%)
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           50.47 ms →  43.71 ms    (-13.41%)          34   →     60      (+76.47%)
+ │ │ │ │   ├ sirius::Smooth_periodic_function                              1.32 ms → 657.77 μs    (-50.19%)          68   →    120      (+76.47%)
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               5.67 ms →   4.42 ms    (-21.97%)          34   →     60      (+76.47%)
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   5.50 ms →   3.63 ms    (-34.07%)          34   →     60      (+76.47%)
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                     2.50 s  → 268.69 ms    (-89.25%)          34   →     60      (+76.47%)
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential             245.24 ns → 130.92 ns    (-46.62%)          34   →     60      (+76.47%)
! │ │ ├ sirius::Field4D::symmetrize                                        98.63 ms →  96.42 ms     (-2.23%)          34   →     60      (+76.47%)
! │ │ │ └ sirius::symmetrize_function|fpw                                  98.62 ms →  96.42 ms     (-2.23%)          34   →     60      (+76.47%)
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                               15.86 ms →  13.27 ms    (-16.32%)          34   →     60      (+76.47%)
! │ │ │   ├ sirius::symmetrize_function|fpw|local                          68.78 ms →  69.93 ms     (+1.68%)          34   →     60      (+76.47%)
! │ │ │   └ sddk::Gvec_shells::remap_backward                              12.62 ms →  12.59 ms     (-0.22%)          34   →     60      (+76.47%)
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     9.32 ms →   3.91 ms    (-58.07%)          34   →     60      (+76.47%)
! │ │ ├ sirius::Periodic_function|inner                                     4.54 ms →   4.75 ms     (+4.76%)         238   →    420      (+76.47%)
! │ │ │ └ sirius::Periodic_function|inner_local                             4.53 ms →   4.56 ms     (+0.62%)         238   →    420      (+76.47%)
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.53 ms →   4.56 ms     (+0.61%)         238   →    420      (+76.47%)
! │ │ ├ sirius::Smooth_periodic_function|inner                              4.74 ms →   4.74 ms     (-0.04%)         102   →    180      (+76.47%)
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.72 ms →   4.73 ms     (+0.23%)         102   →    180      (+76.47%)
! │ │ ├ sirius::Periodic_function::integrate                                4.54 ms →   4.64 ms     (+2.25%)          34   →     60      (+76.47%)
! │ │ └ sirius::Density::get_magnetisation                                 75.55 μs →  75.98 μs     (+0.56%)          34   →     60      (+76.47%)
! │ │   └ sirius::Density::compute_atomic_mag_mom                          69.62 μs →  71.27 μs     (+2.38%)          34   →     60      (+76.47%)
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                         7.48 ms →   5.59 ms    (-25.31%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.62 ms →   4.57 ms     (-0.94%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.56 ms →   4.54 ms     (-0.54%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.56 ms →   4.54 ms     (-0.54%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.73 ms →   4.74 ms     (+0.17%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.73 ms →   4.73 ms     (+0.07%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.55 ms →   4.53 ms     (-0.29%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.54 ms →   4.53 ms     (-0.21%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.54 ms →   4.53 ms     (-0.21%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.71 ms →   4.75 ms     (+0.80%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.71 ms →   4.75 ms     (+0.79%)           1   →      1               
- └ sirius::finalize                                                      123.80 ms → 749.39 ms   (+505.34%)           1   →      1               
```
