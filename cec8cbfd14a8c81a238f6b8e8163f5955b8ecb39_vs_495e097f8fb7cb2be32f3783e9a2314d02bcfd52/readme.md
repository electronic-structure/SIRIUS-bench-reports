# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 495e097f8fb7cb2be32f3783e9a2314d02bcfd52
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   45.76 s  →  46.18 s      (+0.92%)           1   →      1               
  ├ sirius::initialize                                                      2.99 s  →   3.17 s      (+6.34%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                 19.76 s  →  19.71 s      (-0.26%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               256.42 μs → 270.63 μs     (+5.54%)           1   →      1               
! │ ├ sirius::Unit_cell::initialize                                       367.75 ms → 235.62 ms    (-35.93%)           1   →      1               
! │ │ ├ sirius::Atom_type::init                                           117.78 ms →  73.79 ms    (-37.35%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          14.37 ms →  14.22 ms     (-1.04%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      275.88 μs → 253.65 μs     (-8.06%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  14.08 ms →  13.96 ms     (-0.90%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     14.06 ms →  13.94 ms     (-0.87%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.86 ms →   4.86 ms     (-0.10%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                             55.47 μs →  50.68 μs     (-8.63%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               18.43 μs →  16.83 μs     (-8.69%)           1   →      1               
  │ └ sirius::Simulation_context::update                                   19.36 s  →  19.42 s      (+0.34%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.06 ms →   5.06 ms     (-0.18%)           1   →      1               
! │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       77.08 μs →  58.13 μs    (-24.58%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   4.98 ms →   5.00 ms     (+0.21%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      4.96 ms →   4.97 ms     (+0.27%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.85 ms →   4.85 ms     (+0.14%)           1   →      1               
! │   │     ├ sirius::Unit_cell_symmetry|equiv                             50.97 μs →  61.42 μs    (+20.49%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               17.25 μs →  16.63 μs     (-3.60%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                        4.65 s  →   4.68 s      (+0.70%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                          239.64 ms → 242.47 ms     (+1.18%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                               211.53 ms → 214.07 ms     (+1.20%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                     690.67 ms → 705.22 ms     (+2.11%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                       1.59 s  →   1.59 s      (+0.08%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                               661.56 ms → 662.91 ms     (+0.20%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   10.84 ms →  10.99 ms     (+1.40%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      6.82 ms →   6.85 ms     (+0.34%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  11.48 ms →  11.29 ms     (-1.66%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                952.62 μs → 860.75 μs     (-9.64%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 691.17 ms → 676.25 ms     (-2.16%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                     26.65 ms →  25.89 ms     (-2.87%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            981.50 ns → 986.75 ns     (+0.53%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      26.58 ms →  25.81 ms     (-2.88%)           1   →      1               
  │   └ sirius::K_point::initialize                                         6.37 ms →   6.19 ms     (-2.87%)           4   →      4               
  │     ├ sirius::K_point::generate_gkvec                                   3.64 ms →   3.48 ms     (-4.42%)           4   →      4               
  │     │ └ sddk::Gvec::init                                              366.64 μs → 358.43 μs     (-2.24%)           4   →      4               
! │     ├ sddk::matrix_storage::matrix_storage                              4.80 μs →   3.93 μs    (-18.13%)           4   →      4               
  │     └ sirius::K_point::update                                           2.47 ms →   2.45 ms     (-0.65%)           4   →      4               
  │       └ sirius::Beta_projectors                                         2.27 ms →   2.26 ms     (-0.60%)           4   →      4               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                964.65 μs → 947.72 μs     (-1.75%)           4   →      4               
  │         └ sirius::Beta_projectors_base::generate                        1.30 ms →   1.31 ms     (+0.33%)           4   →      4               
  ├ sirius::Smooth_periodic_function                                      426.32 μs → 426.54 μs     (+0.05%)           2   →      2               
  ├ sirius::Potential                                                       8.03 ms →   7.54 ms     (-6.06%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    423.39 μs → 430.48 μs     (+1.67%)           6   →      6               
! │ └ sirius::Potential::update                                             5.35 ms →   4.81 ms    (-10.04%)           1   →      1               
! │   └ sirius::Potential::generate_local_potential                         5.31 ms →   4.77 ms    (-10.11%)           1   →      1               
! │     ├ sirius::Simulation_context::make_periodic_function                4.23 ms →   3.70 ms    (-12.54%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 911.75 μs → 904.75 μs     (-0.77%)           1   →      1               
  ├ sirius::Density                                                         6.25 ms →   5.76 ms     (-7.73%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    229.71 μs → 232.26 μs     (+1.11%)           2   →      2               
  │ └ sirius::Density::update                                               5.78 ms →   5.29 ms     (-8.45%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density                5.74 ms →   5.25 ms     (-8.52%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                66.42 μs →  68.39 μs     (+2.96%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                4.70 ms →   4.24 ms     (-9.84%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 904.45 μs → 886.76 μs     (-1.96%)           1   →      1               
  ├ sirius::Density::initial_density                                       12.26 ms →  11.80 ms     (-3.77%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                    5.77 ms →   5.23 ms     (-9.40%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     843.72 μs → 820.01 μs     (-2.81%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  1.23 ms →   1.26 ms     (+3.01%)           1   →      1               
  ├ sirius::Potential::generate                                            57.17 ms →  58.71 ms     (+2.70%)           1   →      1               
! │ ├ sirius::Potential::poisson                                            6.09 ms →   5.46 ms    (-10.37%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                   961.07 μs → 851.64 μs    (-11.39%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                     1.60 ms →   1.58 ms     (-1.24%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             1.60 ms →   1.58 ms     (-1.04%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    1.60 ms →   1.58 ms     (-1.01%)           1   →      1               
! │ ├ sirius::Periodic_function::add                                      160.72 μs → 143.63 μs    (-10.63%)           2   →      2               
  │ ├ sirius::Potential::xc                                                13.15 ms →  12.75 ms     (-3.04%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               12.89 ms →  12.54 ms     (-2.71%)           1   →      1               
! │ │   ├ sirius::Smooth_periodic_function                                550.43 μs → 494.17 μs    (-10.22%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 836.27 μs → 836.82 μs     (+0.07%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     773.10 μs → 765.21 μs     (-1.02%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        36.58 ms →  39.20 ms     (+7.17%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 141.00 ns → 149.00 ns     (+5.67%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  364.45 μs → 359.94 μs     (-1.24%)           1   →      1               
  │ ├ sirius::Local_operator                                              313.27 μs → 310.99 μs     (-0.73%)           1   →      1               
! │ │ ├ sirius::Smooth_periodic_function                                   32.54 μs →  37.38 μs    (+14.89%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   195.83 μs → 185.41 μs     (-5.32%)           1   →      1               
! │ ├ sirius::Non_local_operator                                          872.50 ns → 980.00 ns    (+12.32%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       25.33 μs →  23.23 μs     (-8.28%)           1   →      1               
! │ └ sirius::Q_operator::initialize                                       13.65 μs →  12.09 μs    (-11.43%)           1   →      1               
! ├ sirius::Band::initialize_subspace                                      96.58 ms → 109.17 ms    (+13.04%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                19.63 μs →  21.16 μs     (+7.82%)           4   →      4               
  │ │ └ sirius::Local_operator::prepare_k                                  18.83 μs →  20.35 μs     (+8.09%)           4   →      4               
! │ └ sirius::Band::initialize_subspace|kp                                 24.12 ms →  27.27 ms    (+13.05%)           4   →      4               
  │   ├ sddk::matrix_storage::matrix_storage                              861.13 ns → 913.87 ns     (+6.13%)          16   →     16               
  │   ├ sirius::K_point::generate_atomic_wave_functions                     1.60 ms →   1.69 ms     (+5.40%)           4   →      4               
  │   ├ sirius::Band::initialize_subspace|kp|wf                           195.74 μs → 207.52 μs     (+6.01%)           4   →      4               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   15.38 ms →  16.70 ms     (+8.58%)           4   →      4               
  │   │ ├ sirius::Local_operator::apply_h                                  11.83 ms →  11.73 ms     (-0.84%)           4   →      4               
  │   │ │ ├ sddk::matrix_storage::remap_forward                             2.05 μs →   2.19 μs     (+6.85%)           4   →      4               
  │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.39 μs →   1.46 μs     (+5.28%)           4   →      4               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           422.25 ns → 423.25 ns     (+0.24%)           4   →      4               
! │   │ │ └ sddk::matrix_storage::remap_backward                          805.00 ns → 628.25 ns    (-21.96%)           4   →      4               
! │   │ ├ sirius::Beta_projectors_base::inner                               1.92 ms →   3.36 ms    (+75.01%)           4   →      4               
  │   │ └ sirius::Non_local_operator::apply                               756.54 μs → 748.88 μs     (-1.01%)           8   →      8               
  │   ├ sirius::Band::set_subspace_mtrx                                   351.32 μs → 334.78 μs     (-4.71%)           8   →      8               
  │   │ └ sddk::inner                                                     344.59 μs → 328.13 μs     (-4.78%)           8   →      8               
  │   │   └ sddk::inner|local                                             340.70 μs → 325.02 μs     (-4.60%)           8   →      8               
! │   ├ Eigensolver_lapack|zhegvx                                           5.68 ms →   7.44 ms    (+30.93%)           4   →      4               
  │   └ sddk::transform                                                   441.23 μs → 444.03 μs     (+0.63%)           4   →      4               
  │     ├ sddk::transform|init                                            216.15 μs → 215.84 μs     (-0.14%)           4   →      4               
  │     └ sddk::transform|local                                           220.14 μs → 222.45 μs     (+1.05%)           4   →      4               
  ├ sirius::DFT_ground_state::scf_loop                                     11.62 s  →  11.52 s      (-0.86%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                    480.91 μs → 480.93 μs     (+0.00%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        579.51 ms → 574.49 ms     (-0.86%)          20   →     20               
  │ │ ├ sirius::Hamiltonian0                                              365.84 μs → 359.68 μs     (-1.68%)          20   →     20               
  │ │ │ ├ sirius::Local_operator                                          316.70 μs → 311.77 μs     (-1.55%)          20   →     20               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               33.24 μs →  34.08 μs     (+2.52%)          20   →     20               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               198.46 μs → 196.30 μs     (-1.09%)          20   →     20               
! │ │ │ ├ sirius::Non_local_operator                                      944.43 ns →   1.07 μs    (+13.14%)          40   →     40               
  │ │ │ ├ sirius::D_operator::initialize                                   25.16 μs →  23.77 μs     (-5.54%)          20   →     20               
  │ │ │ └ sirius::Q_operator::initialize                                   14.80 μs →  14.99 μs     (+1.31%)          20   →     20               
  │ │ ├ sirius::Band::solve                                               192.55 ms → 193.23 ms     (+0.35%)          20   →     20               
  │ │ │ ├ sirius::Hamiltonian_k                                            19.90 μs →  20.12 μs     (+1.11%)          80   →     80               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              18.94 μs →  19.21 μs     (+1.43%)          80   →     80               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     48.08 ms →  48.26 ms     (+0.36%)          80   →     80               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             13.99 μs →  14.26 μs     (+1.94%)          80   →     80               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        957.21 ns → 972.24 ns     (+1.57%)         480   →    480               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             1.78 ms →   1.80 ms     (+1.12%)          80   →     80               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        30.29 μs →  31.26 μs     (+3.20%)          80   →     80               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       548.35 μs → 553.97 μs     (+1.03%)         240   →    240               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              46.28 ms →  46.43 ms     (+0.33%)          80   →     80               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              7.37 ms →   7.39 ms     (+0.26%)         323   →    323               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             6.39 ms →   6.40 ms     (+0.17%)         323   →    323               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.31 μs →   2.21 μs     (-4.38%)         323   →    323               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.76 μs →   1.76 μs     (+0.10%)         323   →    323               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     541.65 ns → 539.16 ns     (-0.46%)         323   →    323               
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    612.53 ns → 908.14 ns    (+48.26%)         323   →    323               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       325.82 μs → 329.37 μs     (+1.09%)         323   →    323               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         294.55 μs → 296.54 μs     (+0.68%)         646   →    646               
  │ │ │ │   ├ sddk::orthogonalize                                           1.30 ms →   1.32 ms     (+1.12%)         323   →    323               
  │ │ │ │   │ ├ sddk::inner                                               197.95 μs → 199.22 μs     (+0.64%)         566   →    566               
  │ │ │ │   │ │ └ sddk::inner|local                                       196.35 μs → 197.57 μs     (+0.62%)         566   →    566               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  30.93 μs →  31.37 μs     (+1.41%)         323   →    323               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             254.22 μs → 255.45 μs     (+0.48%)         323   →    323               
  │ │ │ │   │ └ sddk::transform                                           879.44 μs → 893.40 μs     (+1.59%)         243   →    243               
  │ │ │ │   │   ├ sddk::transform|init                                    455.42 μs → 463.47 μs     (+1.77%)         243   →    243               
  │ │ │ │   │   └ sddk::transform|local                                   140.53 μs → 142.58 μs     (+1.45%)         729   →    729               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             279.38 μs → 281.61 μs     (+0.80%)         323   →    323               
  │ │ │ │   │ └ sddk::inner                                               258.71 μs → 260.35 μs     (+0.63%)         323   →    323               
  │ │ │ │   │   └ sddk::inner|local                                       257.51 μs → 259.19 μs     (+0.65%)         323   →    323               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                     1.07 ms →   1.07 ms     (-0.02%)         323   →    323               
  │ │ │ │   ├ sirius::residuals                                           936.16 μs → 938.30 μs     (+0.23%)         322   →    322               
  │ │ │ │   │ ├ sddk::transform                                           452.45 μs → 455.68 μs     (+0.71%)         251   →    251               
  │ │ │ │   │ │ ├ sddk::transform|init                                     66.29 μs →  65.32 μs     (-1.47%)         251   →    251               
  │ │ │ │   │ │ └ sddk::transform|local                                   191.75 μs → 193.93 μs     (+1.14%)         502   →    502               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               735.40 μs → 734.92 μs     (-0.07%)         251   →    251               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     965.16 μs → 962.96 μs     (-0.23%)         146   →    146               
  │ │ │ │     └ sddk::transform                                           577.92 μs → 577.77 μs     (-0.03%)         212   →    212               
  │ │ │ │       ├ sddk::transform|init                                     75.90 μs →  75.38 μs     (-0.69%)         212   →    212               
  │ │ │ │       └ sddk::transform|local                                   381.45 μs → 381.81 μs     (+0.09%)         278   →    278               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.81 μs →  18.75 μs     (-9.87%)          20   →     20               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        412.96 μs → 411.96 μs     (-0.24%)          20   →     20               
  │ │ ├ sirius::Density::generate                                         257.30 ms → 252.91 ms     (-1.71%)          20   →     20               
  │ │ │ ├ sirius::Density::generate_valence                               209.35 ms → 206.45 ms     (-1.38%)          20   →     20               
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                             5.27 μs →   3.55 μs    (-32.57%)          80   →     80               
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           4.68 μs →   3.15 μs    (-32.74%)          80   →     80               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  466.10 μs → 444.27 μs     (-4.68%)          80   →     80               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         413.28 μs → 394.06 μs     (-4.65%)          80   →     80               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    4.85 ms →   4.82 ms     (-0.71%)          80   →     80               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               172.04 μs → 172.67 μs     (+0.37%)          20   →     20               
  │ │ │ │ └ sirius::Density::augment                                      187.42 ms → 184.74 ms     (-1.43%)          20   →     20               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           187.29 ms → 184.61 ms     (-1.43%)          20   →     20               
! │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                     10.64 ms →  12.36 ms    (+16.17%)          60   →     60               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                      46.72 ms →  44.57 ms     (-4.58%)          60   →     60               
  │ │ │ ├ sirius::Field4D::symmetrize                                      18.08 ms →  17.59 ms     (-2.69%)          20   →     20               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                18.08 ms →  17.59 ms     (-2.69%)          20   →     20               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                              3.01 ms →   3.01 ms     (-0.05%)          20   →     20               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        12.00 ms →  11.51 ms     (-4.07%)          20   →     20               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                             2.99 ms →   2.99 ms     (+0.00%)          20   →     20               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       28.93 ms →  27.91 ms     (-3.52%)          20   →     20               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 944.61 μs → 956.07 μs     (+1.21%)          20   →     20               
  │ │ ├ sirius::Density::mix                                               40.69 ms →  41.14 ms     (+1.12%)          20   →     20               
  │ │ │ ├ sirius::Density::mixer_input                                    252.09 μs → 253.41 μs     (+0.53%)          20   →     20               
  │ │ │ ├ sirius::Periodic_function|inner                                   1.55 ms →   1.62 ms     (+3.93%)         244   →    244               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           1.55 ms →   1.61 ms     (+3.95%)         244   →    244               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  1.55 ms →   1.61 ms     (+3.95%)         244   →    244               
  │ │ │ └ sirius::Density::mixer_output                                     1.11 ms →   1.09 ms     (-2.17%)          20   →     20               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               848.12 μs → 829.60 μs     (-2.18%)          20   →     20               
  │ │ ├ sirius::Potential::generate                                        51.68 ms →  49.80 ms     (-3.64%)          20   →     20               
  │ │ │ ├ sirius::Potential::poisson                                        5.95 ms →   5.66 ms     (-4.97%)          20   →     20               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               925.26 μs → 899.79 μs     (-2.75%)          20   →     20               
  │ │ │ │ └ sirius::Periodic_function|inner                                 1.57 ms →   1.62 ms     (+2.84%)          20   →     20               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         1.57 ms →   1.62 ms     (+2.91%)          20   →     20               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                1.57 ms →   1.62 ms     (+2.92%)          20   →     20               
  │ │ │ ├ sirius::Periodic_function::add                                  151.55 μs → 141.47 μs     (-6.65%)          40   →     40               
  │ │ │ ├ sirius::Potential::xc                                            11.56 ms →  11.59 ms     (+0.23%)          20   →     20               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           11.32 ms →  11.37 ms     (+0.38%)          20   →     20               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            140.22 μs → 130.03 μs     (-7.27%)          40   →     40               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             858.29 μs → 861.09 μs     (+0.33%)          20   →     20               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 802.08 μs → 795.05 μs     (-0.88%)          20   →     20               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    32.80 ms →  31.23 ms     (-4.80%)          20   →     20               
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential             139.55 ns → 123.50 ns    (-11.50%)          20   →     20               
  │ │ ├ sirius::Field4D::symmetrize                                        18.24 ms →  17.87 ms     (-2.00%)          20   →     20               
  │ │ │ └ sirius::symmetrize_function|fpw                                  18.24 ms →  17.87 ms     (-2.00%)          20   →     20               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                                3.10 ms →   3.10 ms     (+0.27%)          20   →     20               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          12.00 ms →  11.62 ms     (-3.16%)          20   →     20               
  │ │ │   └ sddk::Gvec_shells::remap_backward                               3.06 ms →   3.07 ms     (+0.16%)          20   →     20               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   989.29 μs → 934.53 μs     (-5.54%)          20   →     20               
  │ │ ├ sirius::Periodic_function|inner                                     1.58 ms →   1.66 ms     (+5.04%)         140   →    140               
  │ │ │ └ sirius::Periodic_function|inner_local                             1.58 ms →   1.66 ms     (+5.05%)         140   →    140               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    1.58 ms →   1.66 ms     (+5.05%)         140   →    140               
  │ │ ├ sirius::Smooth_periodic_function|inner                              1.17 ms →   1.17 ms     (-0.00%)          60   →     60               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      1.17 ms →   1.17 ms     (-0.00%)          60   →     60               
  │ │ ├ sirius::Periodic_function::integrate                                1.25 ms →   1.29 ms     (+3.84%)          20   →     20               
  │ │ └ sirius::Density::get_magnetisation                                104.65 μs → 112.19 μs     (+7.20%)          20   →     20               
  │ │   └ sirius::Density::compute_atomic_mag_mom                         102.26 μs → 109.75 μs     (+7.33%)          20   →     20               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                        99.84 μs →  99.23 μs     (-0.60%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       1.54 ms →   1.61 ms     (+4.70%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               1.54 ms →   1.61 ms     (+4.71%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      1.54 ms →   1.61 ms     (+4.71%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                1.15 ms →   1.12 ms     (-2.33%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.14 ms →   1.12 ms     (-2.33%)           3   →      3               
  ├ sirius::Stress|kin                                                      5.09 ms →   5.05 ms     (-0.90%)           1   →      1               
  ├ sirius::Stress|har                                                      3.35 ms →   3.35 ms     (+0.05%)           1   →      1               
  ├ sirius::Stress|ewald                                                   10.92 ms →  10.94 ms     (+0.23%)           1   →      1               
  ├ sirius::Stress|vloc                                                    13.20 ms →  12.25 ms     (-7.17%)           1   →      1               
! │ └ sirius::Simulation_context::make_periodic_function                    4.58 ms →   4.11 ms    (-10.14%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       830.37 μs → 869.48 μs     (+4.71%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      72.51 μs →  74.49 μs     (+2.72%)           1   →      1               
! ├ sirius::Simulation_context::make_periodic_function                      4.51 ms →   4.00 ms    (-11.30%)           1   →      1               
  ├ sirius::Periodic_function|inner                                         1.55 ms →   1.63 ms     (+5.38%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                                 1.55 ms →   1.63 ms     (+5.38%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                        1.55 ms →   1.63 ms     (+5.37%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                  1.32 ms →   1.35 ms     (+2.80%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                          1.32 ms →   1.35 ms     (+2.79%)           2   →      2               
  ├ sirius::Stress|us                                                      10.66 s  →  10.96 s      (+2.79%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     789.83 μs → 802.94 μs     (+1.66%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             91.34 ms →  92.34 ms     (+1.09%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                     3.14 ms →   3.21 ms     (+2.14%)           3   →      3               
! │ ├ sirius::Stress|us|phase_fac                                           4.76 ms →   4.27 ms    (-10.31%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs          1.15 s  →   1.19 s      (+2.79%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                           509.16 μs → 523.83 μs     (+2.88%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                4.92 ms →   5.18 ms     (+5.30%)          27   →     27               
  ├ sirius::Stress|nonloc                                                 132.70 ms → 136.35 ms     (+2.75%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t            13.30 ms →  13.54 ms     (+1.79%)           4   →      4               
  │ └ sirius::Non_local_functor::add_k_point                               19.86 ms →  20.53 ms     (+3.39%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::inner                               346.92 μs → 365.41 μs     (+5.33%)          40   →     40               
  │   ├ sirius::Beta_projectors_base::prepare                              68.32 μs →  72.48 μs     (+6.09%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::generate                              1.15 ms →   1.21 ms     (+4.43%)          36   →     36               
! │   └ sirius::Beta_projectors_base::dismiss                              68.00 ns → 129.50 ns    (+90.44%)           4   →      4               
  ├ sirius::Force::calc_forces_vloc                                        11.05 ms →  10.93 ms     (-1.15%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          96.02 ms →  92.85 ms     (-3.30%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     862.83 μs → 892.32 μs     (+3.42%)           1   →      1               
  ├ sirius::Force::calc_forces_nonloc                                      38.49 ms →  39.65 ms     (+3.02%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                7.56 ms →   7.59 ms     (+0.39%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::inner                               350.89 μs → 357.76 μs     (+1.96%)          16   →     16               
! │   ├ sirius::Beta_projectors_base::prepare                               1.32 μs →   2.75 μs   (+108.92%)           4   →      4               
  │   ├ sirius::Beta_projectors_base::generate                              1.16 ms →   1.17 ms     (+1.32%)          12   →     12               
! │   └ sirius::Beta_projectors_base::dismiss                              39.25 ns → 107.25 ns   (+173.25%)           4   →      4               
! ├ sirius::Force::calc_forces_core                                        10.56 ms →   9.48 ms    (-10.16%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     852.04 μs → 853.09 μs     (+0.12%)           1   →      1               
  ├ sirius::Force::calc_forces_ewald                                       52.22 ms →  48.03 ms     (-8.03%)           1   →      1               
! ├ sirius::Force::calc_forces_scf_corr                                     8.56 ms →   7.61 ms    (-10.99%)           1   →      1               
! ├ sirius::Force::hubbard_force                                            2.20 μs →   1.67 μs    (-24.16%)           1   →      1               
  └ sirius::finalize                                                       89.13 ms →  87.06 ms     (-2.32%)           1   →      1               
```
