# Benchmark 65a2a781e8cd18fe746bdef3d750f9286d3d3a77 vs 511872d6296560f7c7c2b493a4edef02c21b97d3
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                   71.82 s  →  72.40 s      (+0.81%)           1   →      1               
  ├ sirius::initialize                                                      3.00 s  →   3.03 s      (+1.02%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.79 s  →   3.84 s      (+1.40%)           1   →      1               
- │ ├ sirius::Simulation_context::init_comm                                 2.48 ms →   4.50 ms    (+81.86%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       167.14 ms → 136.32 ms    (-18.44%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                            75.67 ms →  60.43 ms    (-20.14%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          15.70 ms →  15.37 ms     (-2.09%)           1   →      1               
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        3.88 ms →   5.06 ms    (+30.30%)           1   →      1               
+ │ │   └ sirius::Unit_cell::get_symmetry                                  11.71 ms →  10.26 ms    (-12.44%)           1   →      1               
+ │ │     └ sirius::Unit_cell_symmetry                                     11.64 ms →  10.19 ms    (-12.51%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                2.71 ms →   2.75 ms     (+1.57%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                            504.90 μs → 493.51 μs     (-2.26%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                               15.90 μs →  16.36 μs     (+2.90%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    3.43 s  →   3.65 s      (+6.43%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                           6.93 ms →   7.04 ms     (+1.53%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        3.55 ms →   3.69 ms     (+4.01%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   3.35 ms →   3.31 ms     (-1.13%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      3.31 ms →   3.27 ms     (-1.16%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                2.76 ms →   2.72 ms     (-1.47%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                            497.08 μs → 515.74 μs     (+3.75%)           1   →      1               
+ │   │     └ sirius::Unit_cell_symmetry|mag                               29.79 μs →  13.80 μs    (-53.67%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                      212.81 ms → 212.68 ms     (-0.06%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                           15.18 ms →  15.14 ms     (-0.22%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                13.29 ms →  13.23 ms     (-0.41%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      56.40 ms →  56.38 ms     (-0.04%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      45.10 ms →  45.19 ms     (+0.20%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                60.42 ms →  60.44 ms     (+0.04%)           4   →      4               
  │   ├ sddk::Gvec::init                                                   94.18 ms →  94.20 ms     (+0.02%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                     70.39 ms →  70.57 ms     (+0.25%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                  97.04 ms →  96.16 ms     (-0.91%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.98 ms →   1.97 ms     (-0.30%)           1   →      1               
- │   └ sirius::Augmentation_operator::generate_pw_coeffs                 558.74 ms → 662.81 ms    (+18.63%)           2   →      2               
+ ├ sirius::K_point_set::create_k_mesh                                    151.82 ms →  82.52 ms    (-45.65%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              1.90 μs → 732.00 ns    (-61.39%)           4   →      4               
+ │ └ sirius::K_point_set::initialize                                     151.75 ms →  82.46 ms    (-45.66%)           1   →      1               
  │   └ sirius::K_point::initialize                                        27.82 ms →  28.76 ms     (+3.39%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  10.89 ms →  10.84 ms     (-0.49%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                4.87 ms →   4.89 ms     (+0.34%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                             11.75 μs →  10.51 μs    (-10.57%)           1   →      1               
  │     └ sirius::K_point::update                                          14.12 ms →  15.06 ms     (+6.68%)           1   →      1               
  │       └ sirius::Beta_projectors                                        10.18 ms →  11.03 ms     (+8.42%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  8.26 ms →   8.77 ms     (+6.19%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        2.56 ms →   2.59 ms     (+1.10%)           2   →      2               
  ├ sirius::Potential                                                      50.45 ms →  54.99 ms     (+8.98%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.94 ms →   2.91 ms     (-1.01%)           6   →      6               
- │ └ sirius::Potential::update                                            32.25 ms →  36.88 ms    (+14.36%)           1   →      1               
- │   └ sirius::Potential::generate_local_potential                        31.83 ms →  36.46 ms    (+14.55%)           1   →      1               
- │     ├ sirius::Simulation_context::make_periodic_function               26.51 ms →  32.05 ms    (+20.90%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   4.75 ms →   3.84 ms    (-19.16%)           1   →      1               
- ├ sirius::Density                                                        36.42 ms →  42.82 ms    (+17.55%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.82 ms →   2.85 ms     (+0.85%)           2   →      2               
- │ └ sirius::Density::update                                              30.63 ms →  36.98 ms    (+20.74%)           1   →      1               
- │   └ sirius::Density::generate_pseudo_core_charge_density               30.31 ms →  36.69 ms    (+21.07%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                                77.19 μs →  78.56 μs     (+1.77%)           1   →      1               
- │     ├ sirius::Simulation_context::make_periodic_function               26.20 ms →  32.93 ms    (+25.70%)           1   →      1               
  │     └ sirius::Smooth_periodic_function::fft_transform                   3.67 ms →   3.34 ms     (-9.03%)           1   →      1               
- ├ sirius::Density::initial_density                                       55.39 ms →  64.66 ms    (+16.73%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                   26.56 ms →  36.75 ms    (+38.39%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       4.96 ms →   4.42 ms    (-10.85%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                  5.26 ms →   5.36 ms     (+2.05%)           1   →      1               
  ├ sirius::Potential::generate                                           361.20 ms → 374.06 ms     (+3.56%)           1   →      1               
- │ ├ sirius::Potential::poisson                                           34.51 ms →  45.22 ms    (+31.05%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.02 ms →   2.89 ms    (-28.08%)           1   →      1               
- │ │ └ sirius::Periodic_function|inner                                     4.85 ms →   5.68 ms    (+17.28%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                             4.84 ms →   4.84 ms     (+0.06%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                    4.83 ms →   4.83 ms     (+0.05%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      765.60 μs → 791.36 μs     (+3.36%)           2   →      2               
  │ ├ sirius::Potential::xc                                                51.67 ms →  53.37 ms     (+3.29%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               50.43 ms →  52.19 ms     (+3.49%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  2.55 ms →   2.55 ms     (+0.26%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   4.85 ms →   4.90 ms     (+1.04%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       3.38 ms →   3.11 ms     (-7.98%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                       268.74 ms → 269.33 ms     (+0.22%)           1   →      1               
- │ └ sirius::Potential::generate_PAW_effective_potential                 212.00 ns → 276.00 ns    (+30.19%)           1   →      1               
- ├ sirius::Hamiltonian0                                                    6.92 ms →   8.47 ms    (+22.35%)           1   →      1               
- │ ├ sirius::Local_operator                                                6.48 ms →   7.37 ms    (+13.80%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    2.74 ms →   2.75 ms     (+0.37%)           1   →      1               
- │ │ └ sirius::Smooth_periodic_function::fft_transform                     3.00 ms →   3.57 ms    (+18.94%)           1   →      1               
- │ ├ sirius::Non_local_operator                                           74.80 μs → 409.91 μs   (+448.04%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                      122.88 μs → 115.10 μs     (-6.33%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                      104.23 μs → 100.12 μs     (-3.94%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.29 s  →   1.30 s      (+0.91%)           1   →      1               
- │ ├ sirius::Hamiltonian_k                                                51.27 ms →  68.60 ms    (+33.79%)           1   →      1               
+ │ │ ├ sirius::Local_operator::prepare_k                                 276.89 μs → 212.59 μs    (-23.22%)           1   →      1               
- │ │ └ sirius::Beta_projectors_base::prepare                              50.99 ms →  68.38 ms    (+34.11%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.24 s  →   1.23 s      (-0.45%)           1   →      1               
- │ │ ├ sddk::matrix_storage::matrix_storage                               77.10 ms →  92.02 ms    (+19.34%)           4   →      4               
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                    53.20 ms →  36.76 ms    (-30.91%)           1   →      1               
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                             8.66 ms →   6.96 ms    (-19.61%)           1   →      1               
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  336.57 ms → 383.89 ms    (+14.06%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 247.57 ms → 271.21 ms     (+9.55%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                             3.48 μs →   3.90 μs    (+11.99%)           1   →      1               
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           2.50 μs →   2.94 μs    (+17.47%)           1   →      1               
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           398.00 ns → 461.00 ns    (+15.83%)           1   →      1               
- │ │ │ │ └ sddk::matrix_storage::remap_backward                          657.00 ns → 770.00 ns    (+17.20%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            3.19 ms →   3.14 ms     (-1.55%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                              21.30 ms →  21.35 ms     (+0.22%)           1   →      1               
- │ │ │ └ sirius::Non_local_operator::apply                                32.23 ms →  44.07 ms    (+36.72%)           2   →      2               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                    14.26 ms →   5.35 ms    (-62.47%)           2   →      2               
+ │ │ │ └ sddk::inner                                                      14.05 ms →   5.14 ms    (-63.44%)           2   →      2               
+ │ │ │   └ sddk::inner|local                                              24.86 μs →  21.31 μs    (-14.26%)           2   →      2               
+ │ │ ├ Eigensolver_cuda|zhegvdx                                          231.69 ms → 204.55 ms    (-11.71%)           1   →      1               
+ │ │ └ sddk::transform                                                     5.23 ms →   2.83 ms    (-45.93%)           1   →      1               
+ │ │   ├ sddk::transform|init                                             19.14 μs →  14.99 μs    (-21.65%)           1   →      1               
- │ │   └ sddk::transform|local                                            17.81 μs →  20.46 μs    (+14.91%)           1   →      1               
  │ └ sirius::Beta_projectors_base::dismiss                               480.00 ns → 441.00 ns     (-8.12%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                     61.96 s  →  62.50 s      (+0.87%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      2.43 ms →   2.44 ms     (+0.18%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          3.25 s  →   3.26 s      (+0.41%)          19   →     19               
  │ │ ├ sirius::Hamiltonian0                                                5.37 ms →   5.56 ms     (+3.51%)          19   →     19               
  │ │ │ ├ sirius::Local_operator                                            4.71 ms →   4.73 ms     (+0.38%)          19   →     19               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              540.02 μs → 533.66 μs     (-1.18%)          19   →     19               
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.91 ms →   3.10 ms     (+6.70%)          19   →     19               
- │ │ │ ├ sirius::Non_local_operator                                      182.62 μs → 270.51 μs    (+48.12%)          38   →     38               
  │ │ │ ├ sirius::D_operator::initialize                                  122.78 μs → 115.38 μs     (-6.02%)          19   →     19               
  │ │ │ └ sirius::Q_operator::initialize                                   95.81 μs →  97.09 μs     (+1.34%)          19   →     19               
  │ │ ├ sirius::Band::solve                                                 2.04 s  →   2.04 s      (-0.07%)          19   →     19               
  │ │ │ ├ sirius::Hamiltonian_k                                           203.50 μs → 196.02 μs     (-3.68%)          19   →     19               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             192.35 μs → 185.78 μs     (-3.42%)          19   →     19               
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                           8.20 μs →   7.07 μs    (-13.86%)          19   →     19               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.97 s  →   1.97 s      (-0.17%)          19   →     19               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             77.12 ms →  77.70 ms     (+0.76%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.96 ms →   8.01 ms     (+0.69%)         114   →    114               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                            17.72 ms →  17.68 ms     (-0.22%)          19   →     19               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       464.03 μs → 482.41 μs     (+3.96%)          19   →     19               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         8.44 ms →   8.41 ms     (-0.42%)          38   →     38               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.87 s  →   1.87 s      (-0.21%)          19   →     19               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             52.74 ms →  52.42 ms     (-0.60%)         356   →    356               
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            29.45 ms →  29.34 ms     (-0.36%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.96 μs →   1.85 μs     (-5.57%)         356   →    356               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.66 μs →   1.55 μs     (-6.59%)         356   →    356               
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     460.93 ns → 447.50 ns     (-2.91%)         356   →    356               
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    670.50 ns → 588.92 ns    (-12.17%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      2.89 ms →   2.80 ms     (-3.11%)         356   →    356               
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         3.24 ms →   3.18 ms     (-1.78%)         356   →    356               
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           8.57 ms →   8.54 ms     (-0.35%)         712   →    712               
  │ │ │ │   ├ sddk::orthogonalize                                           5.91 ms →   6.24 ms     (+5.70%)         356   →    356               
  │ │ │ │   │ ├ sddk::inner                                               863.88 μs → 917.05 μs     (+6.15%)         693   →    693               
  │ │ │ │   │ │ └ sddk::inner|local                                        25.85 μs →  24.27 μs     (-6.08%)         693   →    693               
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 142.17 μs → 130.21 μs     (-8.41%)         356   →    356               
- │ │ │ │   │ ├ sddk::orthogonalize|transform                               2.00 ms →   2.27 ms    (+13.31%)         356   →    356               
  │ │ │ │   │ └ sddk::transform                                             2.19 ms →   2.17 ms     (-1.02%)         337   →    337               
+ │ │ │ │   │   ├ sddk::transform|init                                     23.89 μs →  19.32 μs    (-19.17%)         337   →    337               
  │ │ │ │   │   └ sddk::transform|local                                     8.71 μs →   8.17 μs     (-6.22%)        1.01 K →   1.01 K             
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               1.40 ms →   1.28 ms     (-8.95%)         356   →    356               
  │ │ │ │   │ └ sddk::inner                                                 1.33 ms →   1.21 ms     (-9.41%)         356   →    356               
  │ │ │ │   │   └ sddk::inner|local                                        25.27 μs →  23.18 μs     (-8.26%)         356   →    356               
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     36.03 ms →  35.94 ms     (-0.25%)         356   →    356               
  │ │ │ │   ├ sirius::residuals                                             2.64 ms →   2.71 ms     (+2.66%)         340   →    340               
  │ │ │ │   │ ├ sddk::transform                                             1.32 ms →   1.24 ms     (-5.63%)         337   →    337               
  │ │ │ │   │ │ ├ sddk::transform|init                                     18.27 μs →  17.00 μs     (-6.99%)         337   →    337               
  │ │ │ │   │ │ └ sddk::transform|local                                    11.12 μs →  10.48 μs     (-5.79%)         674   →    674               
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.19 ms →   1.38 ms    (+15.66%)         337   →    337               
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi       8.72 ms →   8.21 ms     (-5.92%)          54   →     54               
  │ │ │ │     └ sddk::transform                                             5.24 ms →   4.93 ms     (-6.01%)          89   →     89               
  │ │ │ │       ├ sddk::transform|init                                     12.35 μs →  12.24 μs     (-0.88%)          89   →     89               
  │ │ │ │       └ sddk::transform|local                                    10.47 μs →  10.30 μs     (-1.63%)         124   →    124               
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           589.89 ns → 563.16 ns     (-4.53%)          19   →     19               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          18.95 μs →  19.11 μs     (+0.82%)          19   →     19               
  │ │ ├ sirius::K_point_set::find_band_occupancies                          1.56 ms →   1.59 ms     (+1.77%)          19   →     19               
  │ │ ├ sirius::Density::generate                                         567.29 ms → 569.00 ms     (+0.30%)          19   →     19               
  │ │ │ ├ sirius::Density::generate_valence                               393.51 ms → 387.22 ms     (-1.60%)          19   →     19               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             7.69 μs →   8.28 μs     (+7.62%)          19   →     19               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.13 μs →   7.72 μs     (+8.23%)          19   →     19               
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   42.47 ms →  49.83 ms    (+17.31%)          19   →     19               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.04 μs →   7.05 μs     (+0.23%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.13 ms →   8.57 ms    (+20.18%)          19   →     19               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          34.29 ms →  40.06 ms    (+16.83%)          19   →     19               
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       538.84 ns → 660.63 ns    (+22.60%)          19   →     19               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  103.50 ms →  96.51 ms     (-6.75%)          19   →     19               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 2.37 ms →   1.98 ms    (-16.57%)          19   →     19               
  │ │ │ │ └ sirius::Density::augment                                      204.91 ms → 203.28 ms     (-0.80%)          19   →     19               
  │ │ │ │   └ sirius::Density::generate_rho_aug                           204.68 ms → 203.05 ms     (-0.80%)          19   →     19               
  │ │ │ ├ sirius::Field4D::symmetrize                                     145.52 ms → 153.55 ms     (+5.52%)          19   →     19               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               145.52 ms → 153.55 ms     (+5.52%)          19   →     19               
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             65.14 ms →  71.81 ms    (+10.24%)          19   →     19               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                        67.09 ms →  68.45 ms     (+2.03%)          19   →     19               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            12.65 ms →  12.64 ms     (-0.05%)          19   →     19               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       23.55 ms →  23.55 ms     (-0.01%)          19   →     19               
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   4.70 ms →   4.67 ms     (-0.62%)          19   →     19               
  │ │ ├ sirius::Density::mix                                              131.15 ms → 130.93 ms     (-0.17%)          19   →     19               
+ │ │ │ ├ sirius::Density::mixer_input                                    918.19 μs → 558.36 μs    (-39.19%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function|inner                                   4.65 ms →   4.69 ms     (+1.01%)         229   →    229               
  │ │ │ │ └ sirius::Periodic_function|inner_local                           4.61 ms →   4.62 ms     (+0.29%)         229   →    229               
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  4.61 ms →   4.62 ms     (+0.29%)         229   →    229               
- │ │ │ └ sirius::Density::mixer_output                                     5.03 ms →   5.58 ms    (+10.84%)          19   →     19               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 4.43 ms →   4.85 ms     (+9.40%)          19   →     19               
  │ │ ├ sirius::Potential::generate                                       354.94 ms → 366.49 ms     (+3.25%)          19   →     19               
- │ │ │ ├ sirius::Potential::poisson                                       34.93 ms →  45.37 ms    (+29.89%)          19   →     19               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 4.52 ms →   2.90 ms    (-35.89%)          19   →     19               
- │ │ │ │ └ sirius::Periodic_function|inner                                 4.99 ms →   5.64 ms    (+13.03%)          19   →     19               
  │ │ │ │   └ sirius::Periodic_function|inner_local                         4.83 ms →   4.83 ms     (+0.11%)          19   →     19               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local                4.83 ms →   4.83 ms     (+0.12%)          19   →     19               
  │ │ │ ├ sirius::Periodic_function::add                                  767.69 μs → 775.45 μs     (+1.01%)          38   →     38               
  │ │ │ ├ sirius::Potential::xc                                            45.27 ms →  45.89 ms     (+1.38%)          19   →     19               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           44.10 ms →  44.72 ms     (+1.41%)          19   →     19               
  │ │ │ │   ├ sirius::Smooth_periodic_function                            675.64 μs → 686.31 μs     (+1.58%)          38   →     38               
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               4.83 ms →   5.42 ms    (+12.29%)          19   →     19               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   3.57 ms →   3.70 ms     (+3.62%)          19   →     19               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                   268.24 ms → 268.56 ms     (+0.12%)          19   →     19               
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential             213.26 ns → 243.47 ns    (+14.17%)          19   →     19               
  │ │ ├ sirius::Field4D::symmetrize                                        93.51 ms →  94.51 ms     (+1.07%)          19   →     19               
  │ │ │ └ sirius::symmetrize_function|fpw                                  93.51 ms →  94.51 ms     (+1.07%)          19   →     19               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               13.29 ms →  13.27 ms     (-0.14%)          19   →     19               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                          67.00 ms →  68.03 ms     (+1.54%)          19   →     19               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              12.59 ms →  12.57 ms     (-0.15%)          19   →     19               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     4.32 ms →   3.95 ms     (-8.38%)          19   →     19               
  │ │ ├ sirius::Periodic_function|inner                                     4.66 ms →   4.74 ms     (+1.61%)         133   →    133               
  │ │ │ └ sirius::Periodic_function|inner_local                             4.57 ms →   4.56 ms     (-0.25%)         133   →    133               
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    4.57 ms →   4.56 ms     (-0.25%)         133   →    133               
  │ │ ├ sirius::Smooth_periodic_function|inner                              4.75 ms →   4.88 ms     (+2.80%)          57   →     57               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                      4.74 ms →   4.87 ms     (+2.74%)          57   →     57               
  │ │ ├ sirius::Periodic_function::integrate                                4.55 ms →   4.53 ms     (-0.29%)          19   →     19               
  │ │ └ sirius::Density::get_magnetisation                                 74.91 μs →  74.84 μs     (-0.09%)          19   →     19               
  │ │   └ sirius::Density::compute_atomic_mag_mom                          70.00 μs →  70.09 μs     (+0.12%)          19   →     19               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.69 ms →   5.25 ms     (-7.71%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                       4.89 ms →   4.87 ms     (-0.41%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                               4.88 ms →   4.86 ms     (-0.41%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                      4.88 ms →   4.86 ms     (-0.41%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                                4.98 ms →   4.99 ms     (+0.16%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.98 ms →   4.99 ms     (+0.16%)           3   →      3               
  ├ sirius::Periodic_function|inner                                         4.54 ms →   4.78 ms     (+5.14%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                 4.54 ms →   4.77 ms     (+5.14%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                        4.54 ms →   4.77 ms     (+5.14%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                  4.73 ms →   4.97 ms     (+4.97%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                          4.73 ms →   4.96 ms     (+4.92%)           1   →      1               
  └ sirius::finalize                                                      754.97 ms → 755.62 ms     (+0.09%)           1   →      1               
```
