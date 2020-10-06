# Benchmark 511872d6296560f7c7c2b493a4edef02c21b97d3 vs 3a5dfbdc503ee17017918d5d6ddb109e96364a94
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                    8.20 s  →   8.27 s      (+0.82%)           1   →      1               
  ├ sirius::initialize                                                      2.91 s  →   2.96 s      (+1.56%)           1   →      1               
- ├ sirius::Simulation_context::initialize                                  2.09 s  →   2.44 s     (+16.37%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                               407.84 μs →  14.91 ms  (+3555.16%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       425.90 ms → 759.82 ms    (+78.40%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                           136.53 ms → 248.17 ms    (+81.77%)           3   →      3               
  │ │ └ sirius::Unit_cell::update                                          16.29 ms →  15.30 ms     (-6.11%)           1   →      1               
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                      280.08 μs → 250.55 μs    (-10.55%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  16.01 ms →  15.04 ms     (-6.03%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     15.97 ms →  15.00 ms     (-6.12%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.94 ms →   4.92 ms     (-0.47%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                             55.40 μs →  49.96 μs     (-9.81%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               17.16 μs →  17.86 μs     (+4.10%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    1.62 s  →   1.62 s      (-0.01%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           5.14 ms →   5.13 ms     (-0.32%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                       32.84 μs →  32.88 μs     (+0.12%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   5.11 ms →   5.09 ms     (-0.32%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      5.09 ms →   5.07 ms     (-0.31%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                4.98 ms →   4.97 ms     (-0.16%)           1   →      1               
+ │   │     ├ sirius::Unit_cell_symmetry|equiv                             49.85 μs →  41.03 μs    (-17.70%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                               18.05 μs →  17.93 μs     (-0.68%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      271.51 ms → 273.12 ms     (+0.59%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           21.26 ms →  21.26 ms     (-0.02%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                19.03 ms →  19.14 ms     (+0.59%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      80.40 ms →  80.34 ms     (-0.07%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      61.83 ms →  61.67 ms     (-0.26%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                97.07 ms →  96.67 ms     (-0.41%)           4   →      4               
  │   ├ sddk::Gvec::init                                                    4.29 ms →   4.24 ms     (-1.16%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                      2.96 ms →   2.98 ms     (+0.65%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                   4.05 ms →   4.13 ms     (+1.81%)           1   →      1               
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                282.84 μs → 317.20 μs    (+12.15%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                  93.92 ms →  94.12 ms     (+0.21%)           3   →      3               
  ├ sirius::K_point_set::create_k_mesh                                      5.93 ms →   5.86 ms     (-1.27%)           1   →      1               
  │ ├ sirius::K_point::K_point                                            769.50 ns → 785.75 ns     (+2.11%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                       5.86 ms →   5.79 ms     (-1.25%)           1   →      1               
  │   └ sirius::K_point::initialize                                         5.61 ms →   5.54 ms     (-1.29%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                   4.59 ms →   4.52 ms     (-1.38%)           1   →      1               
+ │     │ └ sddk::Gvec::init                                              273.59 μs → 245.70 μs    (-10.20%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                              3.33 μs →   2.72 μs    (-18.16%)           1   →      1               
  │     └ sirius::K_point::update                                         805.43 μs → 799.78 μs     (-0.70%)           1   →      1               
  │       └ sirius::Beta_projectors                                       662.69 μs → 658.54 μs     (-0.63%)           1   →      1               
  │         ├ sirius::Beta_projectors::generate_pw_coefs_t                403.04 μs → 392.61 μs     (-2.59%)           1   →      1               
  │         └ sirius::Beta_projectors_base::generate                      255.69 μs → 262.08 μs     (+2.50%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                       29.08 μs →  28.02 μs     (-3.62%)           2   →      2               
  ├ sirius::Potential                                                       2.18 ms →   2.01 ms     (-7.80%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     29.25 μs →  27.13 μs     (-7.24%)           6   →      6               
  │ └ sirius::Potential::update                                             1.91 ms →   1.75 ms     (-8.35%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                         1.90 ms →   1.74 ms     (-8.39%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.45 ms →   1.32 ms     (-9.28%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                 360.21 μs → 336.89 μs     (-6.48%)           1   →      1               
+ ├ sirius::Density                                                         1.88 ms →   1.67 ms    (-10.94%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                     28.67 μs →  28.57 μs     (-0.35%)           2   →      2               
+ │ └ sirius::Density::update                                               1.82 ms →   1.61 ms    (-11.30%)           1   →      1               
+ │   └ sirius::Density::generate_pseudo_core_charge_density                1.80 ms →   1.60 ms    (-11.37%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                19.59 μs →  19.53 μs     (-0.35%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function                1.48 ms →   1.36 ms     (-8.21%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                 293.69 μs → 206.37 μs    (-29.73%)           1   →      1               
  ├ sirius::Density::initial_density                                        2.93 ms →   2.77 ms     (-5.46%)           1   →      1               
+ │ ├ sirius::Simulation_context::make_periodic_function                    1.42 ms →   1.19 ms    (-16.65%)           1   →      1               
- │ ├ sirius::Smooth_periodic_function::fft_transform                     255.73 μs → 287.81 μs    (+12.54%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                258.01 μs → 260.50 μs     (+0.96%)           1   →      1               
  ├ sirius::Potential::generate                                            21.98 ms →  20.70 ms     (-5.83%)           1   →      1               
+ │ ├ sirius::Potential::poisson                                            2.12 ms →   1.82 ms    (-13.94%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   190.51 μs → 200.52 μs     (+5.25%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                   263.58 μs → 263.46 μs     (-0.05%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                           260.74 μs → 260.71 μs     (-0.01%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                  260.44 μs → 260.43 μs     (-0.00%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                       11.13 μs →  10.19 μs     (-8.49%)           2   →      2               
  │ ├ sirius::Potential::xc                                                 2.05 ms →   2.07 ms     (+0.81%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                                2.01 ms →   2.03 ms     (+0.81%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                 29.09 μs →  29.28 μs     (+0.66%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                 196.50 μs → 201.94 μs     (+2.77%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     161.98 μs → 163.88 μs     (+1.17%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        17.60 ms →  16.60 ms     (-5.68%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                 194.00 ns → 220.00 ns    (+13.40%)           1   →      1               
  ├ sirius::Hamiltonian0                                                  391.69 μs → 380.42 μs     (-2.88%)           1   →      1               
  │ ├ sirius::Local_operator                                              363.31 μs → 338.57 μs     (-6.81%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                   25.52 μs →  26.05 μs     (+2.07%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                   316.02 μs → 291.04 μs     (-7.90%)           1   →      1               
- │ ├ sirius::Non_local_operator                                          762.50 ns → 927.00 ns    (+21.57%)           2   →      2               
- │ ├ sirius::D_operator::initialize                                        9.34 μs →  10.36 μs    (+10.92%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                        7.15 μs →   7.82 μs     (+9.34%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                      49.97 ms →  48.83 ms     (-2.28%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                17.23 μs →  18.27 μs     (+6.08%)           1   →      1               
  │ │ └ sirius::Local_operator::prepare_k                                  15.83 μs →  16.86 μs     (+6.52%)           1   →      1               
  │ └ sirius::Band::initialize_subspace|kp                                 49.95 ms →  48.81 ms     (-2.28%)           1   →      1               
- │   ├ sddk::matrix_storage::matrix_storage                                5.73 μs →   6.97 μs    (+21.57%)           4   →      4               
  │   ├ sirius::K_point::generate_atomic_wave_functions                   934.01 μs → 945.95 μs     (+1.28%)           1   →      1               
+ │   ├ sirius::Band::initialize_subspace|kp|wf                            57.12 μs →  47.13 μs    (-17.47%)           1   →      1               
  │   ├ sirius::Hamiltonian_k::apply_h_s                                   18.13 ms →  18.38 ms     (+1.36%)           1   →      1               
  │   │ ├ sirius::Local_operator::apply_h                                   8.63 ms →   8.47 ms     (-1.81%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::remap_forward                             2.62 μs →   2.37 μs     (-9.73%)           1   →      1               
  │   │ │ │ └ sddk::matrix_storage::set_num_extra                           1.35 μs →   1.40 μs     (+3.94%)           1   →      1               
  │   │ │ ├ sddk::matrix_storage::set_num_extra                           376.00 ns → 373.00 ns     (-0.80%)           1   →      1               
- │   │ │ └ sddk::matrix_storage::remap_backward                          512.00 ns → 732.00 ns    (+42.97%)           1   →      1               
  │   │ ├ sirius::Beta_projectors_base::inner                               4.85 ms →   5.15 ms     (+6.22%)           1   →      1               
  │   │ └ sirius::Non_local_operator::apply                                 2.12 ms →   2.18 ms     (+2.60%)           2   →      2               
  │   ├ sirius::Band::set_subspace_mtrx                                   278.43 μs → 280.77 μs     (+0.84%)           2   →      2               
  │   │ └ sddk::inner                                                     271.78 μs → 274.19 μs     (+0.89%)           2   →      2               
  │   │   └ sddk::inner|local                                             264.24 μs → 266.78 μs     (+0.96%)           2   →      2               
  │   ├ Eigensolver_lapack|zhegvx                                          29.79 ms →  28.12 ms     (-5.61%)           1   →      1               
  │   └ sddk::transform                                                   308.64 μs → 313.02 μs     (+1.42%)           1   →      1               
  │     ├ sddk::transform|init                                             67.29 μs →  67.84 μs     (+0.81%)           1   →      1               
  │     └ sddk::transform|local                                           226.88 μs → 231.86 μs     (+2.19%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                      2.28 s  →   2.24 s      (-1.49%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function                                     68.68 μs →  51.39 μs    (-25.18%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                        102.98 ms → 101.42 ms     (-1.52%)          22   →     22               
- │ │ ├ sirius::Hamiltonian0                                              322.74 μs → 356.27 μs    (+10.39%)          22   →     22               
- │ │ │ ├ sirius::Local_operator                                          301.96 μs → 335.82 μs    (+11.22%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function                               32.73 μs →  33.09 μs     (+1.10%)          22   →     22               
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               252.62 μs → 286.49 μs    (+13.41%)          22   →     22               
  │ │ │ ├ sirius::Non_local_operator                                      816.89 ns → 857.93 ns     (+5.02%)          44   →     44               
  │ │ │ ├ sirius::D_operator::initialize                                    7.34 μs →   7.06 μs     (-3.76%)          22   →     22               
  │ │ │ └ sirius::Q_operator::initialize                                    5.39 μs →   5.48 μs     (+1.76%)          22   →     22               
  │ │ ├ sirius::Band::solve                                                37.89 ms →  37.76 ms     (-0.33%)          22   →     22               
  │ │ │ ├ sirius::Hamiltonian_k                                            18.96 μs →  18.15 μs     (-4.27%)          22   →     22               
  │ │ │ │ └ sirius::Local_operator::prepare_k                              17.99 μs →  17.08 μs     (-5.03%)          22   →     22               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                     33.73 ms →  33.45 ms     (-0.84%)          22   →     22               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             12.57 μs →  12.81 μs     (+1.91%)          22   →     22               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        912.33 ns → 928.83 ns     (+1.81%)         132   →    132               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           705.45 μs → 698.67 μs     (-0.96%)          22   →     22               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                        10.78 μs →  10.67 μs     (-1.07%)          22   →     22               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       220.12 μs → 217.84 μs     (-1.03%)          66   →     66               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter              33.01 ms →  32.73 ms     (-0.84%)          22   →     22               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                              5.18 ms →   5.13 ms     (-1.02%)          87   →     87               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                             4.30 ms →   4.24 ms     (-1.47%)          87   →     87               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       2.04 μs →   2.06 μs     (+0.98%)          87   →     87               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.75 μs →   1.78 μs     (+1.38%)          87   →     87               
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     498.41 ns → 579.68 ns    (+16.30%)          87   →     87               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    404.46 ns → 393.79 ns     (-2.64%)          87   →     87               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                       283.97 μs → 281.92 μs     (-0.72%)          87   →     87               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                         272.51 μs → 275.41 μs     (+1.06%)         174   →    174               
  │ │ │ │   ├ sddk::orthogonalize                                         893.11 μs → 893.57 μs     (+0.05%)          87   →     87               
  │ │ │ │   │ ├ sddk::inner                                               140.57 μs → 140.35 μs     (-0.16%)         152   →    152               
  │ │ │ │   │ │ └ sddk::inner|local                                       139.03 μs → 138.74 μs     (-0.21%)         152   →    152               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                  32.56 μs →  31.86 μs     (-2.15%)          87   →     87               
  │ │ │ │   │ ├ sddk::orthogonalize|transform                             255.50 μs → 254.04 μs     (-0.57%)          87   →     87               
  │ │ │ │   │ └ sddk::transform                                           471.33 μs → 475.16 μs     (+0.81%)          65   →     65               
  │ │ │ │   │   ├ sddk::transform|init                                     76.91 μs →  77.08 μs     (+0.21%)          65   →     65               
  │ │ │ │   │   └ sddk::transform|local                                   130.80 μs → 132.01 μs     (+0.93%)         195   →    195               
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                             213.02 μs → 213.33 μs     (+0.14%)          87   →     87               
  │ │ │ │   │ └ sddk::inner                                               197.78 μs → 197.97 μs     (+0.10%)          87   →     87               
  │ │ │ │   │   └ sddk::inner|local                                       196.66 μs → 196.83 μs     (+0.09%)          87   →     87               
  │ │ │ │   ├ Eigensolver_lapack|zheevx                                     1.01 ms →   1.00 ms     (-0.63%)          87   →     87               
  │ │ │ │   ├ sirius::residuals                                           588.83 μs → 589.33 μs     (+0.09%)          86   →     86               
  │ │ │ │   │ ├ sddk::transform                                           426.24 μs → 426.30 μs     (+0.01%)          69   →     69               
  │ │ │ │   │ │ ├ sddk::transform|init                                     66.83 μs →  68.84 μs     (+3.01%)          69   →     69               
  │ │ │ │   │ │ └ sddk::transform|local                                   178.73 μs → 177.69 μs     (-0.58%)         138   →    138               
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               297.86 μs → 298.13 μs     (+0.09%)          69   →     69               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi     890.02 μs → 873.51 μs     (-1.86%)          38   →     38               
  │ │ │ │     └ sddk::transform                                           541.82 μs → 529.30 μs     (-2.31%)          54   →     54               
  │ │ │ │       ├ sddk::transform|init                                     73.89 μs →  75.00 μs     (+1.51%)          54   →     54               
  │ │ │ │       └ sddk::transform|local                                   359.79 μs → 349.17 μs     (-2.95%)          70   →     70               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.11 μs →  21.08 μs     (+4.82%)          22   →     22               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        203.00 μs → 201.70 μs     (-0.64%)          22   →     22               
  │ │ ├ sirius::Density::generate                                          37.51 ms →  37.39 ms     (-0.31%)          22   →     22               
  │ │ │ ├ sirius::Density::generate_valence                                29.18 ms →  28.97 ms     (-0.73%)          22   →     22               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.51 μs →   3.03 μs    (+20.92%)          22   →     22               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.22 μs →   2.68 μs    (+21.02%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  414.67 μs → 418.97 μs     (+1.04%)          22   →     22               
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner                         389.64 μs → 393.30 μs     (+0.94%)          22   →     22               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                    2.85 ms →   2.83 ms     (-1.00%)          22   →     22               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               139.52 μs → 139.87 μs     (+0.25%)          22   →     22               
  │ │ │ │ └ sirius::Density::augment                                       25.36 ms →  25.13 ms     (-0.92%)          22   →     22               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            25.35 ms →  25.11 ms     (-0.95%)          22   →     22               
  │ │ │ │     ├ sirius::Density::generate_rho_aug|gemm                      4.21 ms →   4.25 ms     (+0.87%)          66   →     66               
  │ │ │ │     └ sirius::Density::generate_rho_aug|sum                       2.60 ms →   2.83 ms     (+8.59%)          66   →     66               
  │ │ │ ├ sirius::Field4D::symmetrize                                       4.28 ms →   4.39 ms     (+2.57%)          22   →     22               
  │ │ │ │ └ sirius::symmetrize_function|fpw                                 4.28 ms →   4.39 ms     (+2.57%)          22   →     22               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                            967.36 μs →   1.08 ms    (+11.25%)          22   →     22               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                         2.30 ms →   2.31 ms     (+0.39%)          22   →     22               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                           990.36 μs → 983.13 μs     (-0.73%)          22   →     22               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                        3.69 ms →   3.69 ms     (-0.04%)          22   →     22               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 347.91 μs → 335.81 μs     (-3.48%)          22   →     22               
  │ │ ├ sirius::Density::mix                                                5.23 ms →   4.92 ms     (-6.01%)          22   →     22               
  │ │ │ ├ sirius::Density::mixer_input                                     26.54 μs →  25.25 μs     (-4.87%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function|inner                                 274.22 μs → 255.14 μs     (-6.96%)         274   →    274               
  │ │ │ │ └ sirius::Periodic_function|inner_local                         250.14 μs → 250.12 μs     (-0.01%)         274   →    274               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                249.97 μs → 249.94 μs     (-0.01%)         274   →    274               
  │ │ │ └ sirius::Density::mixer_output                                   190.55 μs → 191.35 μs     (+0.42%)          22   →     22               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform               176.72 μs → 179.72 μs     (+1.69%)          22   →     22               
  │ │ ├ sirius::Potential::generate                                        14.75 ms →  13.72 ms     (-6.98%)          22   →     22               
+ │ │ │ ├ sirius::Potential::poisson                                        2.12 ms →   1.86 ms    (-12.19%)          22   →     22               
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               205.58 μs → 252.23 μs    (+22.69%)          22   →     22               
  │ │ │ │ └ sirius::Periodic_function|inner                               262.97 μs → 266.67 μs     (+1.41%)          22   →     22               
  │ │ │ │   └ sirius::Periodic_function|inner_local                       261.43 μs → 261.53 μs     (+0.04%)          22   →     22               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local              260.94 μs → 260.94 μs     (+0.00%)          22   →     22               
  │ │ │ ├ sirius::Periodic_function::add                                   10.85 μs →  10.65 μs     (-1.84%)          44   →     44               
  │ │ │ ├ sirius::Potential::xc                                             2.07 ms →   2.07 ms     (+0.06%)          22   →     22               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            2.01 ms →   2.01 ms     (+0.07%)          22   →     22               
  │ │ │ │   ├ sirius::Smooth_periodic_function                             30.42 μs →  29.90 μs     (-1.70%)          44   →     44               
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             201.59 μs → 204.93 μs     (+1.66%)          22   →     22               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 156.47 μs → 157.39 μs     (+0.59%)          22   →     22               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    10.31 ms →   9.54 ms     (-7.45%)          22   →     22               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             201.32 ns → 215.05 ns     (+6.82%)          22   →     22               
  │ │ ├ sirius::Field4D::symmetrize                                         3.93 ms →   3.93 ms     (+0.06%)          22   →     22               
  │ │ │ └ sirius::symmetrize_function|fpw                                   3.93 ms →   3.93 ms     (+0.06%)          22   →     22               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                              620.37 μs → 620.10 μs     (-0.04%)          22   →     22               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                           2.33 ms →   2.31 ms     (-0.74%)          22   →     22               
  │ │ │   └ sddk::Gvec_shells::remap_backward                             959.94 μs → 980.20 μs     (+2.11%)          22   →     22               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                   238.66 μs → 241.19 μs     (+1.06%)          22   →     22               
  │ │ ├ sirius::Periodic_function|inner                                   252.44 μs → 250.89 μs     (-0.61%)         154   →    154               
  │ │ │ └ sirius::Periodic_function|inner_local                           245.78 μs → 246.47 μs     (+0.28%)         154   →    154               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                  245.49 μs → 246.15 μs     (+0.27%)         154   →    154               
  │ │ ├ sirius::Smooth_periodic_function|inner                            262.55 μs → 260.43 μs     (-0.81%)          66   →     66               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                    256.87 μs → 256.36 μs     (-0.20%)          66   →     66               
  │ │ ├ sirius::Periodic_function::integrate                              238.74 μs → 239.15 μs     (+0.17%)          22   →     22               
  │ │ └ sirius::Density::get_magnetisation                                 51.45 μs →  52.20 μs     (+1.46%)          22   →     22               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          49.49 μs →  50.44 μs     (+1.92%)          22   →     22               
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                       251.68 μs → 199.46 μs    (-20.75%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                     249.83 μs → 249.06 μs     (-0.31%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                             246.67 μs → 245.53 μs     (-0.46%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                    246.53 μs → 245.41 μs     (-0.46%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                              253.61 μs → 253.55 μs     (-0.03%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                      252.12 μs → 252.11 μs     (-0.00%)           3   →      3               
  ├ sirius::Stress|kin                                                    301.88 μs → 304.06 μs     (+0.72%)           1   →      1               
  ├ sirius::Stress|har                                                    587.63 μs → 588.57 μs     (+0.16%)           1   →      1               
  ├ sirius::Stress|ewald                                                    1.79 ms →   1.78 ms     (-0.43%)           1   →      1               
  ├ sirius::Stress|vloc                                                     3.62 ms →   3.28 ms     (-9.31%)           1   →      1               
+ │ └ sirius::Simulation_context::make_periodic_function                    1.38 ms →   1.23 ms    (-10.58%)           2   →      2               
  ├ sirius::Smooth_periodic_function::fft_transform                       210.80 μs → 211.61 μs     (+0.39%)           1   →      1               
  ├ sirius::rho_core_ri_pseudo|values                                      18.35 μs →  18.54 μs     (+1.04%)           1   →      1               
  ├ sirius::Simulation_context::make_periodic_function                      1.42 ms →   1.32 ms     (-7.06%)           1   →      1               
  ├ sirius::Periodic_function|inner                                       251.68 μs → 253.09 μs     (+0.56%)           4   →      4               
  │ └ sirius::Periodic_function|inner_local                               248.57 μs → 251.65 μs     (+1.24%)           4   →      4               
  │   └ sirius::Smooth_periodic_function|inner_local                      248.40 μs → 251.50 μs     (+1.25%)           4   →      4               
  ├ sirius::Smooth_periodic_function|inner                                254.43 μs → 258.58 μs     (+1.63%)           2   →      2               
  │ └ sirius::Smooth_periodic_function|inner_local                        253.31 μs → 257.30 μs     (+1.58%)           2   →      2               
  ├ sirius::Stress|us                                                     333.01 ms → 326.86 ms     (-1.85%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                     195.11 μs → 188.65 μs     (-3.31%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv                             78.01 ms →  77.12 ms     (-1.14%)           1   →      1               
  │ ├ sirius::Augmentation_operator_gvec_deriv::prepare                   584.69 μs → 594.70 μs     (+1.71%)           3   →      3               
+ │ ├ sirius::Stress|us|phase_fac                                           1.58 ms →   1.30 ms    (-17.73%)           3   →      3               
  │ ├ sirius::Augmentation_operator_gvec_deriv::generate_pw_coeffs         23.67 ms →  22.29 ms     (-5.82%)           9   →      9               
  │ ├ sirius::Stress|us|prepare                                            71.58 μs →  73.93 μs     (+3.28%)          27   →     27               
  │ └ sirius::Stress|us|gemm                                                1.21 ms →   1.23 ms     (+1.46%)          27   →     27               
  ├ sirius::Stress|nonloc                                                  14.54 ms →  14.47 ms     (-0.48%)           1   →      1               
  │ ├ sirius::Beta_projectors_strain_deriv::generate_pw_coefs_t             5.81 ms →   5.96 ms     (+2.48%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                8.11 ms →   7.99 ms     (-1.58%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               337.67 μs → 331.98 μs     (-1.69%)          10   →     10               
- │   ├ sirius::Beta_projectors_base::prepare                               3.41 μs →   4.63 μs    (+35.79%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            278.15 μs → 268.95 μs     (-3.31%)           9   →      9               
- │   └ sirius::Beta_projectors_base::dismiss                              93.00 ns → 165.00 ns    (+77.42%)           1   →      1               
  ├ sirius::Force::calc_forces_vloc                                         1.21 ms →   1.21 ms     (-0.26%)           1   →      1               
  ├ sirius::Force::calc_forces_us                                          26.69 ms →  24.98 ms     (-6.39%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     248.14 μs → 246.46 μs     (-0.68%)           1   →      1               
- ├ sirius::Force::calc_forces_nonloc                                       4.17 ms →   4.61 ms    (+10.45%)           1   →      1               
  │ └ sirius::Non_local_functor::add_k_point                                2.98 ms →   2.95 ms     (-0.82%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::inner                               343.85 μs → 341.67 μs     (-0.63%)           4   →      4               
- │   ├ sirius::Beta_projectors_base::prepare                               3.58 μs →   4.12 μs    (+15.27%)           1   →      1               
  │   ├ sirius::Beta_projectors_base::generate                            277.95 μs → 269.29 μs     (-3.12%)           3   →      3               
- │   └ sirius::Beta_projectors_base::dismiss                             107.00 ns → 224.00 ns   (+109.35%)           1   →      1               
- ├ sirius::Force::calc_forces_core                                       944.62 μs →   1.05 ms    (+10.82%)           1   →      1               
  │ └ sirius::Smooth_periodic_function::fft_transform                     215.35 μs → 212.74 μs     (-1.21%)           1   →      1               
+ ├ sirius::Force::calc_forces_ewald                                       15.04 ms →  12.94 ms    (-13.95%)           1   →      1               
  ├ sirius::Force::calc_forces_scf_corr                                   770.56 μs → 776.94 μs     (+0.83%)           1   →      1               
  ├ sirius::Force::hubbard_force                                            1.46 μs →   1.57 μs     (+7.52%)           1   →      1               
  └ sirius::finalize                                                      123.69 ms → 124.59 ms     (+0.73%)           1   →      1               
```
