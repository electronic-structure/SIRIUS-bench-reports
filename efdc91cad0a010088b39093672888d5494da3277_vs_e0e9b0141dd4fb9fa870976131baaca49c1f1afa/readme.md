"
# Benchmark efdc91cad0a010088b39093672888d5494da3277 vs e0e9b0141dd4fb9fa870976131baaca49c1f1afa
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
! sirius                                                                    6.96 s  →   5.21 s     (-25.12%)           1   →      1               
- ├ extra::param                                                            1.00 ms                                    1                          
- │ ├ another::param                                                      550.00 μs                                    2                          
- │ └ final::param                                                        367.00 μs                                    3                          
! ├ sirius::initialize                                                      1.57 s  → 756.21 ms    (-51.80%)           1   →      1               
! ├ sirius::Simulation_context::initialize                                  1.63 s  → 780.57 ms    (-52.23%)           1   →      1               
! │ ├ sirius::Simulation_context::init_comm                               218.07 μs → 165.51 μs    (-24.10%)           1   →      1               
! │ ├ sirius::Unit_cell::initialize                                       812.63 ms →  48.64 ms    (-94.02%)           1   →      1               
! │ │ ├ sirius::Atom_type::init                                           268.41 ms →   9.62 ms    (-96.42%)           3   →      3               
! │ │ └ sirius::Unit_cell::update                                           7.36 ms →  19.75 ms   (+168.41%)           1   →      1               
! │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        2.19 ms →  12.37 ms   (+464.17%)           1   →      1               
! │ │   └ sirius::Unit_cell::get_symmetry                                   5.14 ms →   7.33 ms    (+42.50%)           1   →      1               
! │ │     └ sirius::Unit_cell_symmetry                                      5.12 ms →   7.30 ms    (+42.38%)           1   →      1               
! │ │       ├ sirius::Unit_cell_symmetry|spg                                5.07 ms →   7.21 ms    (+42.04%)           1   →      1               
! │ │       ├ sirius::Unit_cell_symmetry|equiv                             12.37 μs →  25.19 μs   (+103.55%)           1   →      1               
! │ │       └ sirius::Unit_cell_symmetry|mag                                9.19 μs →  16.37 μs    (+78.20%)           1   →      1               
! │ └ sirius::Simulation_context::update                                  811.83 ms → 730.40 ms    (-10.03%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           4.67 ms →   4.72 ms     (+1.25%)           1   →      1               
! │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       32.87 μs →  27.21 μs    (-17.22%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   4.62 ms →   4.68 ms     (+1.39%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      4.61 ms →   4.67 ms     (+1.38%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.58 ms →   4.64 ms     (+1.24%)           1   →      1               
! │   │     ├ sirius::Unit_cell_symmetry|equiv                              8.12 μs →   5.79 μs    (-28.74%)           1   →      1               
! │   │     └ sirius::Unit_cell_symmetry|mag                                6.72 μs →  15.63 μs   (+132.51%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       94.58 ms →  90.79 ms     (-4.00%)           2   →      2               
! │   ├ sirius::Radial_integrals|rho_core_pseudo                           13.30 ms →   9.21 ms    (-30.76%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 7.84 ms →   7.82 ms     (-0.20%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      40.19 ms →  39.89 ms     (-0.77%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      24.04 ms →  24.23 ms     (+0.80%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                14.07 ms →  14.16 ms     (+0.59%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    3.53 ms →   3.51 ms     (-0.49%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.68 ms →   2.69 ms     (+0.23%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.07 ms →   4.08 ms     (+0.32%)           1   →      1               
! │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                325.29 μs → 476.99 μs    (+46.64%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  56.75 ms →  57.97 ms     (+2.15%)           3   →      3               
+ ├ extra::param                                                                        1.00 ms                                   1               
+ │ ├ another::param                                                                  550.00 μs                                   2               
+ │ └ final::param                                                                    367.00 μs                                   3               
! ├ sirius::K_point_set::create_k_mesh                                     13.19 ms →   5.26 ms    (-60.13%)           1   →      1               
! │ ├ sirius::K_point::K_point                                            884.00 ns → 596.25 ns    (-32.55%)           4   →      4               
! │ └ sirius::K_point_set::initialize                                      13.11 ms →   5.20 ms    (-60.30%)           1   →      1               
! │   └ sirius::K_point::initialize                                         3.26 ms →   1.29 ms    (-60.39%)           4   →      4               
! │     ├ sirius::K_point::generate_gkvec                                 857.42 μs → 540.08 μs    (-37.01%)           4   →      4               
! │     │ └ sddk::Gvec::init                                              174.97 μs → 111.42 μs    (-36.32%)           4   →      4               
! │     ├ sddk::matrix_storage::matrix_storage                              3.81 μs →   2.34 μs    (-38.67%)           4   →      4               
! │     └ sirius::K_point::update                                           2.36 ms → 727.40 μs    (-69.24%)           4   →      4               
! │       └ sirius::Beta_projectors                                         2.25 ms → 650.87 μs    (-71.05%)           4   →      4               
! │         └ sirius::Beta_projectors::generate_pw_coefs_t                  1.98 ms → 452.88 μs    (-77.07%)           4   →      4               
! ├ sirius::Smooth_periodic_function                                      279.74 μs → 225.49 μs    (-19.39%)           2   →      2               
  ├ sirius::Potential                                                       2.49 ms →   2.28 ms     (-8.27%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    266.12 μs → 254.21 μs     (-4.48%)           6   →      6               
! │ └ sirius::Potential::update                                           733.30 μs → 640.36 μs    (-12.68%)           1   →      1               
! │   └ sirius::Potential::generate_local_potential                       719.21 μs → 626.45 μs    (-12.90%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              163.39 μs → 163.85 μs     (+0.28%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 378.58 μs → 386.30 μs     (+2.04%)           1   →      1               
! ├ sirius::Density                                                         2.96 ms → 877.63 μs    (-70.37%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    155.27 μs → 158.91 μs     (+2.34%)           2   →      2               
! │ └ sirius::Density::update                                               2.64 ms → 551.60 μs    (-79.13%)           1   →      1               
! │   └ sirius::Density::generate_pseudo_core_charge_density                2.63 ms → 532.81 μs    (-79.71%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                11.52 μs →  11.35 μs     (-1.48%)           1   →      1               
! │     ├ sirius::Simulation_context::make_periodic_function                1.07 ms → 150.11 μs    (-86.02%)           1   →      1               
! │     └ sirius::Smooth_periodic_function::fft_transform                   1.51 ms → 346.12 μs    (-77.13%)           1   →      1               
! ├ sirius::Density::initial_density                                        5.34 ms →   6.38 ms    (+19.48%)           1   →      1               
! │ ├ sirius::Simulation_context::make_periodic_function                  117.16 μs → 227.40 μs    (+94.09%)           1   →      1               
! │ ├ sirius::Smooth_periodic_function::fft_transform                     454.88 μs → 865.27 μs    (+90.22%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                875.28 μs → 876.12 μs     (+0.10%)           1   →      1               
  ├ sirius::Potential::generate                                            24.35 ms →  21.96 ms     (-9.78%)           1   →      1               
  │ ├ sirius::Potential::poisson                                            1.36 ms →   1.34 ms     (-1.40%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                   411.68 μs → 364.01 μs    (-11.58%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   912.28 μs → 934.59 μs     (+2.45%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           910.65 μs → 932.96 μs     (+2.45%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  910.36 μs → 932.80 μs     (+2.46%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       53.25 μs →  51.51 μs     (-3.26%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.70 ms →   2.74 ms     (+1.46%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.55 ms →   2.57 ms     (+0.58%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                222.08 μs → 234.55 μs     (+5.62%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 303.01 μs → 303.53 μs     (+0.17%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     271.67 μs → 253.30 μs     (-6.76%)           1   →      1               
! │ ├ sirius::Potential::generate_D_operator_matrix                        19.81 ms →  17.42 ms    (-12.08%)           1   →      1               
! │ └ sirius::Potential::generate_PAW_effective_potential                 221.00 ns → 140.00 ns    (-36.65%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  313.32 μs → 294.95 μs     (-5.86%)           1   →      1               
  │ ├ sirius::Local_operator                                              226.52 μs → 205.35 μs     (-9.35%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function                                   35.36 μs →  22.48 μs    (-36.41%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   125.52 μs → 129.13 μs     (+2.88%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           16.94 μs →  17.78 μs     (+5.00%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       20.69 μs →  21.85 μs     (+5.62%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       22.38 μs →  21.79 μs     (-2.64%)           1   →      1               
! ├ sirius::Band::initialize_subspace                                      39.26 ms →  33.87 ms    (-13.74%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                16.22 μs →  15.27 μs     (-5.85%)           4   →      4               
  │ │ ├ sirius::Local_operator::prepare_k                                  13.98 μs →  12.99 μs     (-7.02%)           4   →      4               
  │ │ └ sirius::Beta_projectors_base::prepare                               1.44 μs →   1.41 μs     (-2.08%)           4   →      4               
! │ ├ sirius::Band::initialize_subspace|kp                                  9.80 ms →   8.45 ms    (-13.75%)           4   →      4               
  │ │ ├ sddk::matrix_storage::matrix_storage                              153.52 μs → 158.71 μs     (+3.38%)          16   →     16               
! │ │ ├ sirius::K_point::generate_atomic_wave_functions                   235.33 μs → 203.80 μs    (-13.40%)           4   →      4               
! │ │ ├ sirius::Band::initialize_subspace|kp|wf                            51.71 μs →  31.31 μs    (-39.45%)           4   →      4               
! │ │ ├ sirius::Hamiltonian_k::apply_h_s                                    4.92 ms →   5.49 ms    (+11.57%)           4   →      4               
  │ │ │ ├ sirius::Local_operator::apply_h                                   3.74 ms →   3.71 ms     (-0.78%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             1.21 μs →   1.28 μs     (+6.24%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                         859.25 ns → 891.50 ns     (+3.75%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           190.50 ns → 190.00 ns     (-0.26%)           4   →      4               
! │ │ │ │ └ sddk::matrix_storage::remap_backward                          152.75 ns → 175.50 ns    (+14.89%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::generate                           32.15 μs →  31.36 μs     (-2.45%)           4   →      4               
! │ │ │ ├ sirius::Beta_projectors_base::inner                             334.63 μs → 267.34 μs    (-20.11%)           4   →      4               
! │ │ │ └ sirius::Non_local_operator::apply                               401.80 μs → 735.25 μs    (+82.99%)           8   →      8               
  │ │ ├ sirius::Band::set_subspace_mtrx                                   253.88 μs → 254.73 μs     (+0.33%)           8   →      8               
  │ │ │ └ sddk::inner                                                     252.43 μs → 253.29 μs     (+0.34%)           8   →      8               
  │ │ │   └ sddk::inner|local                                              12.65 μs →  12.56 μs     (-0.67%)           8   →      8               
! │ │ ├ Eigensolver_lapack|zhegvx                                           2.83 ms → 938.91 μs    (-66.79%)           4   →      4               
  │ │ └ sddk::transform                                                   166.47 μs → 166.04 μs     (-0.26%)           4   →      4               
  │ │   ├ sddk::transform|init                                              7.04 μs →   6.43 μs     (-8.67%)           4   →      4               
  │ │   └ sddk::transform|local                                            10.51 μs →   9.99 μs     (-4.96%)           4   →      4               
  │ └ sirius::Beta_projectors_base::dismiss                               280.50 ns → 280.50 ns                        4   →      4               
  ├ sirius::DFT_ground_state::scf_loop                                      3.11 s  →   3.07 s      (-1.48%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    237.56 μs → 236.74 μs     (-0.35%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        154.91 ms → 152.65 ms     (-1.46%)          20   →     20               
  │ │ ├ sirius::Hamiltonian0                                              277.00 μs → 280.02 μs     (+1.09%)          20   →     20               
  │ │ │ ├ sirius::Local_operator                                          199.29 μs → 201.72 μs     (+1.22%)          20   →     20               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               23.62 μs →  24.55 μs     (+3.94%)          20   →     20               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               121.30 μs → 123.91 μs     (+2.16%)          20   →     20               
  │ │ │ ├ sirius::Non_local_operator                                       16.43 μs →  16.58 μs     (+0.90%)          40   →     40               
  │ │ │ ├ sirius::D_operator::initialize                                   19.12 μs →  19.65 μs     (+2.80%)          20   →     20               
  │ │ │ └ sirius::Q_operator::initialize                                   17.95 μs →  17.66 μs     (-1.63%)          20   →     20               
  │ │ ├ sirius::Band::solve                                                77.64 ms →  75.80 ms     (-2.36%)          20   →     20               
  │ │ │ ├ sirius::Hamiltonian_k                                            34.38 μs →  33.10 μs     (-3.72%)          80   →     80               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                              31.75 μs →  30.55 μs     (-3.78%)          80   →     80               
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           1.81 μs →   1.70 μs     (-5.98%)          80   →     80               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     19.36 ms →  18.90 ms     (-2.37%)          80   →     80               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc            131.30 μs → 127.64 μs     (-2.79%)          80   →     80               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          6.34 μs →   6.53 μs     (+3.08%)         480   →    480               
! │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           645.07 μs → 532.81 μs    (-17.40%)          80   →     80               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                         8.37 μs →   8.40 μs     (+0.35%)          80   →     80               
! │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       190.47 μs → 153.35 μs    (-19.49%)         240   →    240               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              18.42 ms →  18.07 ms     (-1.87%)          80   →     80               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              2.70 ms →   2.74 ms     (+1.48%)         323   →    323               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             1.65 ms →   1.66 ms     (+0.20%)         323   →    323               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                     847.44 ns → 793.11 ns     (-6.41%)         323   →    323               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                   633.15 ns → 605.67 ns     (-4.34%)         323   →    323               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     179.95 ns → 180.59 ns     (+0.36%)         323   →    323               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    167.06 ns → 174.48 ns     (+4.44%)         323   →    323               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                     30.46 μs →  30.44 μs     (-0.05%)         323   →    323               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       137.99 μs → 135.14 μs     (-2.06%)         323   →    323               
! │ │ │ │   │ └ sirius::Non_local_operator::apply                         433.01 μs → 452.76 μs     (+4.56%)         646   →   1.29 K    (+99.85%)
! │ │ │ │   ├ sddk::orthogonalize                                         595.87 μs → 487.43 μs    (-18.20%)         323   →    323               
  │ │ │ │   │ ├ sddk::inner                                               121.01 μs → 121.87 μs     (+0.71%)         566   →    566               
  │ │ │ │   │ │ └ sddk::inner|local                                        12.81 μs →  12.02 μs     (-6.19%)         566   →    566               
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 192.93 μs →  81.40 μs    (-57.81%)         323   →    323               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                              79.61 μs →  74.71 μs     (-6.15%)         323   →    323               
  │ │ │ │   │ └ sddk::transform                                           145.86 μs → 154.49 μs     (+5.92%)         243   →    243               
  │ │ │ │   │   ├ sddk::transform|init                                      9.98 μs →   9.87 μs     (-1.16%)         243   →    243               
  │ │ │ │   │   └ sddk::transform|local                                     7.01 μs →   6.97 μs     (-0.56%)         729   →    729               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             196.92 μs → 184.07 μs     (-6.52%)         323   →    323               
  │ │ │ │   │ └ sddk::inner                                               134.57 μs → 131.68 μs     (-2.15%)         323   →    323               
  │ │ │ │   │   └ sddk::inner|local                                        13.11 μs →  12.13 μs     (-7.46%)         323   →    323               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                   708.81 μs → 698.65 μs     (-1.43%)         323   →    323               
  │ │ │ │   ├ sirius::residuals                                           221.93 μs → 222.84 μs     (+0.41%)         322   →    322               
  │ │ │ │   │ ├ sddk::transform                                           154.89 μs → 155.51 μs     (+0.40%)         251   →    251               
  │ │ │ │   │ │ ├ sddk::transform|init                                      8.61 μs →   8.51 μs     (-1.22%)         251   →    251               
  │ │ │ │   │ │ └ sddk::transform|local                                     7.68 μs →   7.61 μs     (-0.86%)         502   →    502               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                87.63 μs →  89.28 μs     (+1.89%)         251   →    251               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     299.09 μs → 312.19 μs     (+4.38%)         146   →    146               
  │ │ │ │     └ sddk::transform                                           198.68 μs → 208.01 μs     (+4.70%)         212   →    212               
  │ │ │ │       ├ sddk::transform|init                                      5.40 μs →   5.33 μs     (-1.28%)         212   →    212               
  │ │ │ │       └ sddk::transform|local                                     7.84 μs →   7.71 μs     (-1.57%)         278   →    278               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           327.58 ns → 326.96 ns     (-0.19%)          80   →     80               
  │ │ │ └ sirius::K_point_set::sync_band_energies                           5.31 μs →   5.06 μs     (-4.84%)          20   →     20               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        120.89 μs → 119.26 μs     (-1.35%)          20   →     20               
  │ │ ├ sirius::Density::generate                                          28.30 ms →  28.10 ms     (-0.70%)          20   →     20               
  │ │ │ ├ sirius::Density::generate_valence                                21.74 ms →  21.57 ms     (-0.81%)          20   →     20               
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                           877.44 ns → 771.86 ns    (-12.03%)          80   →     80               
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                         744.40 ns → 650.49 ns    (-12.62%)          80   →     80               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  197.67 μs → 212.81 μs     (+7.66%)          80   →     80               
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         1.23 μs →   1.09 μs    (-11.13%)          80   →     80               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                       62.43 μs →  61.59 μs     (-1.35%)          80   →     80               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                         110.93 μs → 109.74 μs     (-1.08%)          80   →     80               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       323.59 ns → 322.11 ns     (-0.46%)          80   →     80               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    1.19 ms →   1.17 ms     (-1.18%)          80   →     80               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                82.06 μs →  81.31 μs     (-0.91%)          20   →     20               
  │ │ │ │ └ sirius::Density::augment                                       15.76 ms →  15.58 ms     (-1.15%)          20   →     20               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            15.72 ms →  15.50 ms     (-1.41%)          20   →     20               
  │ │ │ ├ sirius::Field4D::symmetrize                                       3.19 ms →   3.07 ms     (-3.81%)          20   →     20               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 3.19 ms →   3.07 ms     (-3.80%)          20   →     20               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                            627.95 μs → 569.67 μs     (-9.28%)          20   →     20               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.05 ms →   1.98 ms     (-3.21%)          20   →     20               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           462.23 μs → 463.45 μs     (+0.26%)          20   →     20               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        2.73 ms →   2.85 ms     (+4.59%)          20   →     20               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 634.36 μs → 608.33 μs     (-4.10%)          20   →     20               
  │ │ ├ sirius::Density::mix                                               14.62 ms →  14.22 ms     (-2.74%)          20   →     20               
! │ │ │ ├ sirius::Density::mixer_input                                     61.46 μs →  74.52 μs    (+21.25%)          20   →     20               
  │ │ │ ├ sirius::Periodic_function|inner                                 934.48 μs → 926.53 μs     (-0.85%)         244   →    244               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         934.15 μs → 926.21 μs     (-0.85%)         244   →    244               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                934.00 μs → 926.05 μs     (-0.85%)         244   →    244               
  │ │ │ └ sirius::Density::mixer_output                                   295.37 μs → 286.57 μs     (-2.98%)          20   →     20               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               273.11 μs → 264.98 μs     (-2.98%)          20   →     20               
  │ │ ├ sirius::Potential::generate                                        20.20 ms →  20.11 ms     (-0.43%)          20   →     20               
  │ │ │ ├ sirius::Potential::poisson                                        1.29 ms →   1.30 ms     (+0.90%)          20   →     20               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               324.57 μs → 321.84 μs     (-0.84%)          20   →     20               
  │ │ │ │ └ sirius::Periodic_function|inner                               923.05 μs → 937.50 μs     (+1.57%)          20   →     20               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       922.60 μs → 937.16 μs     (+1.58%)          20   →     20               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              922.52 μs → 937.04 μs     (+1.57%)          20   →     20               
  │ │ │ ├ sirius::Periodic_function::add                                   39.76 μs →  39.06 μs     (-1.76%)          40   →     40               
  │ │ │ ├ sirius::Potential::xc                                             2.32 ms →   2.30 ms     (-0.87%)          20   →     20               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.13 ms →   2.12 ms     (-0.24%)          20   →     20               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            108.78 μs → 108.48 μs     (-0.27%)          40   →     40               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             285.34 μs → 279.48 μs     (-2.05%)          20   →     20               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 232.04 μs → 228.37 μs     (-1.58%)          20   →     20               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    16.14 ms →  16.07 ms     (-0.43%)          20   →     20               
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential             700.25 ns → 867.10 ns    (+23.83%)          20   →     20               
  │ │ ├ sirius::Field4D::symmetrize                                         4.10 ms →   4.23 ms     (+3.21%)          20   →     20               
  │ │ │ └ sirius::symmetrize_function|fpw                                   4.10 ms →   4.23 ms     (+3.22%)          20   →     20               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              532.01 μs → 532.70 μs     (+0.13%)          20   →     20               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           3.02 ms →   3.16 ms     (+4.62%)          20   →     20               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             451.51 μs → 449.57 μs     (-0.43%)          20   →     20               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   276.30 μs → 275.73 μs     (-0.21%)          20   →     20               
  │ │ ├ sirius::Periodic_function|inner                                   859.55 μs → 862.47 μs     (+0.34%)         140   →    140               
  │ │ │ └ sirius::Periodic_function|inner_local                           859.37 μs → 862.28 μs     (+0.34%)         140   →    140               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  858.99 μs → 861.85 μs     (+0.33%)         140   →    140               
  │ │ ├ sirius::Smooth_periodic_function|inner                            799.97 μs → 811.62 μs     (+1.46%)          60   →     60               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    799.79 μs → 811.45 μs     (+1.46%)          60   →     60               
  │ │ ├ sirius::Periodic_function::integrate                              701.60 μs → 705.16 μs     (+0.51%)          20   →     20               
  │ │ └ sirius::Density::get_magnetisation                                 31.45 μs →  31.95 μs     (+1.60%)          20   →     20               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          30.30 μs →  30.72 μs     (+1.39%)          20   →     20               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                        36.90 μs →  37.21 μs     (+0.84%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     778.97 μs → 809.23 μs     (+3.88%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             778.85 μs → 809.11 μs     (+3.89%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    778.78 μs → 809.05 μs     (+3.89%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              740.53 μs → 766.43 μs     (+3.50%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      740.38 μs → 766.30 μs     (+3.50%)           3   →      3               
! ├ sirius::Stress|kin                                                      1.29 ms →   1.62 ms    (+25.47%)           1   →      1               
  ├ sirius::Stress|har                                                    584.38 μs → 582.83 μs     (-0.26%)           1   →      1               
  ├ sirius::Stress|ewald                                                    2.67 ms →   2.67 ms     (+0.22%)           1   →      1               
  ├ sirius::Stress|vloc                                                     1.29 ms →   1.28 ms     (-0.65%)           1   →      1               
  │ └ sirius::Simulation_context::make_periodic_function                   84.19 μs →  78.84 μs     (-6.36%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       301.91 μs → 297.55 μs     (-1.44%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                       9.71 μs →   9.85 μs     (+1.43%)           1   →      1               
! ├ sirius::Simulation_context::make_periodic_function                     49.11 μs → 132.68 μs   (+170.16%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       940.44 μs → 940.78 μs     (+0.04%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               940.29 μs → 940.66 μs     (+0.04%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      940.08 μs → 940.45 μs     (+0.04%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                912.47 μs → 919.30 μs     (+0.75%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        912.08 μs → 918.89 μs     (+0.75%)           2   →      2               
  ├ sirius::Stress|us                                                     221.67 ms → 217.95 ms     (-1.68%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     279.62 μs → 271.81 μs     (-2.79%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             40.89 ms →  41.07 ms     (+0.44%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   647.28 μs → 650.72 μs     (+0.53%)           3   →      3               
! │ ├ sirius::Stress|us|phase_fac                                         107.84 μs → 121.89 μs    (+13.03%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         22.48 μs →  20.83 μs     (-7.33%)           9   →      9               
! │ ├ sirius::Stress|us|prepare                                           135.83 μs →  51.82 μs    (-61.85%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                6.45 ms →   6.39 ms     (-0.95%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  16.19 ms →  15.54 ms     (-4.04%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t           966.11 μs → 912.40 μs     (-5.56%)           4   →      4               
  │ └ sirius::Non_local_functor::add_k_point                                2.85 ms →   2.75 ms     (-3.32%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::prepare                             426.99 μs → 425.55 μs     (-0.34%)           8   →      8               
  │   ├ sirius::Beta_projectors_base::generate                             30.59 μs →  28.88 μs     (-5.58%)          40   →     40               
  │   ├ sirius::Beta_projectors_base::inner                               106.68 μs → 104.08 μs     (-2.44%)          40   →     40               
! │   └ sirius::Beta_projectors_base::dismiss                             523.25 ns → 376.00 ns    (-28.14%)           8   →      8               
! ├ sirius::Force::calc_forces_vloc                                         3.52 ms →   3.98 ms    (+13.09%)           1   →      1               
! ├ sirius::Force::calc_forces_us                                          62.82 ms →  54.08 ms    (-13.92%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     311.11 μs → 321.15 μs     (+3.23%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                       6.44 ms →   6.53 ms     (+1.39%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                1.15 ms →   1.18 ms     (+2.39%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::prepare                             142.94 μs → 144.58 μs     (+1.15%)           8   →      8               
  │   ├ sirius::Beta_projectors_base::generate                             56.01 μs →  57.31 μs     (+2.32%)          16   →     16               
  │   ├ sirius::Beta_projectors_base::inner                               106.04 μs → 105.98 μs     (-0.06%)          16   →     16               
  │   └ sirius::Beta_projectors_base::dismiss                             374.25 ns → 388.38 ns     (+3.77%)           8   →      8               
  ├ sirius::Force::calc_forces_core                                         3.30 ms →   3.06 ms     (-7.23%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     301.63 μs → 315.32 μs     (+4.54%)           1   →      1               
! ├ sirius::Force::calc_forces_ewald                                        3.29 ms →   3.63 ms    (+10.33%)           1   →      1               
  ├ sirius::Force::calc_forces_scf_corr                                     2.44 ms →   2.38 ms     (-2.26%)           1   →      1               
! ├ sirius::Force::hubbard_force                                          712.00 ns →   1.03 μs    (+44.94%)           1   →      1               
  └ sirius::finalize                                                      185.91 ms → 189.47 ms     (+1.91%)           1   →      1               
```
