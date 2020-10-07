# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  133.19 s  → 130.07 s      (-2.34%)           1   →      1               
  ├ sirius::initialize                                                      2.79 s  →   2.76 s      (-0.82%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.14 s  →   2.96 s      (-5.50%)           1   →      1               
  │ ├ sirius::Simulation_context::init_comm                               194.72 μs → 213.58 μs     (+9.69%)           1   →      1               
+ │ ├ sirius::Unit_cell::initialize                                       345.54 ms → 238.39 ms    (-31.01%)           1   →      1               
+ │ │ ├ sirius::Atom_type::init                                           161.12 ms → 107.14 ms    (-33.50%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          23.21 ms →  24.02 ms     (+3.49%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.31 ms →   6.27 ms     (-0.62%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  16.86 ms →  17.71 ms     (+5.02%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     16.84 ms →  17.69 ms     (+5.02%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.17 ms →   4.16 ms     (-0.09%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.35 ms →   2.35 ms     (-0.01%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              105.60 μs → 105.71 μs     (+0.10%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.75 s  →   2.69 s      (-2.36%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.87 ms →  10.89 ms     (+0.11%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.46 ms →   4.46 ms     (+0.06%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.39 ms →   6.39 ms     (+0.10%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.37 ms →   6.38 ms     (+0.09%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.87 ms →   3.87 ms     (+0.03%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.33 ms →   2.33 ms     (+0.08%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              101.23 μs → 102.36 μs     (+1.12%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       66.84 ms →  64.84 ms     (-3.00%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.43 ms →   5.13 ms     (-5.62%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.52 ms →   4.46 ms     (-1.30%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.66 ms →  21.68 ms     (+0.09%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.78 ms →  14.81 ms     (+0.14%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.67 ms →  19.81 ms     (+0.69%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  189.87 ms → 181.78 ms     (-4.26%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    144.43 ms → 138.70 ms     (-3.96%)           2   →      2               
+ │   ├ sddk::Gvec_shells                                                 209.96 ms → 165.95 ms    (-20.96%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.33 ms →   1.34 ms     (+1.19%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 292.36 ms → 295.45 ms     (+1.06%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     35.38 ms →  35.62 ms     (+0.68%)           1   →      1               
+ │ ├ sirius::K_point::K_point                                              2.73 μs →   2.45 μs    (-10.39%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      35.29 ms →  35.52 ms     (+0.64%)           1   →      1               
  │   └ sirius::K_point::initialize                                        35.21 ms →  35.42 ms     (+0.61%)           1   →      1               
  │     ├ sirius::K_point::generate_gkvec                                  18.05 ms →  18.20 ms     (+0.86%)           1   →      1               
  │     │ └ sddk::Gvec::init                                                8.12 ms →   8.21 ms     (+1.16%)           1   →      1               
+ │     ├ sddk::matrix_storage::matrix_storage                              9.20 μs →   7.24 μs    (-21.31%)           1   →      1               
  │     └ sirius::K_point::update                                          12.36 ms →  12.33 ms     (-0.23%)           1   →      1               
  │       └ sirius::Beta_projectors                                         6.08 ms →   6.09 ms     (+0.25%)           1   →      1               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                  3.48 ms →   3.49 ms     (+0.37%)           1   →      1               
  ├ sirius::Smooth_periodic_function                                        5.18 ms →   5.40 ms     (+4.12%)           2   →      2               
  ├ sirius::Potential                                                     155.26 ms → 155.27 ms     (+0.01%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.80 ms →   5.81 ms     (+0.18%)           6   →      6               
  │ └ sirius::Potential::update                                           119.74 ms → 119.72 ms     (-0.01%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       118.98 ms → 119.04 ms     (+0.05%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              106.55 ms → 111.86 ms     (+4.98%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  11.54 ms →   6.28 ms    (-45.62%)           1   →      1               
  ├ sirius::Density                                                       130.54 ms → 128.37 ms     (-1.66%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.12 ms →   5.29 ms     (+3.31%)           2   →      2               
  │ └ sirius::Density::update                                             120.02 ms → 117.52 ms     (-2.09%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              119.60 ms → 117.10 ms     (-2.09%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               103.03 μs → 104.44 μs     (+1.37%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              109.44 ms → 111.43 ms     (+1.82%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   9.59 ms →   5.11 ms    (-46.73%)           1   →      1               
  ├ sirius::Density::initial_density                                      163.79 ms → 168.12 ms     (+2.65%)           1   →      1               
  │ ├ sirius::Simulation_context::make_periodic_function                  109.48 ms → 111.88 ms     (+2.19%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       5.74 ms →   4.86 ms    (-15.23%)           2   →      2               
- │ └ sirius::Periodic_function::integrate                                  9.72 ms →  10.90 ms    (+12.15%)           1   →      1               
  ├ sirius::Potential::generate                                           583.68 ms → 584.58 ms     (+0.15%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          126.34 ms → 126.82 ms     (+0.38%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     7.00 ms →   5.20 ms    (-25.64%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.35 ms →  10.55 ms     (+1.98%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.33 ms →  10.53 ms     (+2.00%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.32 ms →  10.52 ms     (+1.98%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      561.60 μs → 558.85 μs     (-0.49%)           2   →      2               
  │ ├ sirius::Potential::xc                                                56.05 ms →  54.90 ms     (-2.05%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               53.68 ms →  52.60 ms     (-2.02%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.72 ms →   5.69 ms     (-0.48%)           2   →      2               
+ │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.93 ms →   5.11 ms    (-13.91%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.58 ms →   5.84 ms     (+4.74%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        93.62 ms →  93.50 ms     (-0.12%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 299.60 ms → 301.06 ms     (+0.49%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.38 ms →   8.42 ms     (+0.50%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.02 ms →   8.07 ms     (+0.57%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.72 ms →   4.74 ms     (+0.35%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.38 ms →   2.42 ms     (+1.92%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           63.41 μs →  63.95 μs     (+0.84%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       94.47 μs →  93.00 μs     (-1.55%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       75.92 μs →  74.36 μs     (-2.06%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       1.85 s  →   1.87 s      (+0.72%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                                18.70 ms →  18.69 ms     (-0.04%)           1   →      1               
  │ │ ├ sirius::Local_operator::prepare_k                                 199.66 μs → 193.38 μs     (-3.15%)           1   →      1               
  │ │ └ sirius::Beta_projectors_base::prepare                              18.50 ms →  18.50 ms     (-0.00%)           1   →      1               
  │ ├ sirius::Band::initialize_subspace|kp                                  1.83 s  →   1.85 s      (+0.73%)           1   →      1               
  │ │ ├ sddk::matrix_storage::matrix_storage                              128.25 ms → 131.13 ms     (+2.24%)           4   →      4               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    52.16 ms →  52.45 ms     (+0.55%)           1   →      1               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                            21.04 ms →  21.24 ms     (+0.93%)           1   →      1               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  637.02 ms → 636.79 ms     (-0.04%)           1   →      1               
  │ │ │ ├ sirius::Local_operator::apply_h                                 298.10 ms → 297.67 ms     (-0.14%)           1   →      1               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                             2.87 μs →   2.75 μs     (-4.28%)           1   →      1               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           1.96 μs →   1.87 μs     (-4.64%)           1   →      1               
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           484.00 ns → 400.00 ns    (-17.36%)           1   →      1               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                          513.00 ns → 515.00 ns     (+0.39%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            9.24 ms →   9.23 ms     (-0.10%)           1   →      1               
  │ │ │ ├ sirius::Beta_projectors_base::inner                             121.23 ms → 121.97 ms     (+0.61%)           1   →      1               
  │ │ │ └ sirius::Non_local_operator::apply                               104.21 ms → 103.94 ms     (-0.26%)           2   →      2               
  │ │ ├ sirius::Band::set_subspace_mtrx                                    38.45 ms →  38.59 ms     (+0.36%)           2   →      2               
  │ │ │ └ sddk::inner                                                      37.91 ms →  38.02 ms     (+0.29%)           2   →      2               
- │ │ │   └ sddk::inner|local                                              25.68 μs →  34.94 μs    (+36.06%)           2   →      2               
  │ │ ├ Eigensolver_cuda|zhegvdx                                           56.99 ms →  56.54 ms     (-0.79%)           1   →      1               
  │ │ └ sddk::transform                                                    31.56 ms →  31.61 ms     (+0.15%)           1   →      1               
  │ │   ├ sddk::transform|init                                             10.93 μs →  10.68 μs     (-2.25%)           1   →      1               
  │ │   └ sddk::transform|local                                            10.88 μs →  10.28 μs     (-5.53%)           1   →      1               
+ │ └ sirius::Beta_projectors_base::dismiss                               596.00 ns → 522.00 ns    (-12.42%)           1   →      1               
  ├ sirius::DFT_ground_state::scf_loop                                    123.31 s  → 120.34 s      (-2.41%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.81 ms →   5.69 ms     (-1.96%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          4.73 s  →   4.79 s      (+1.33%)          26   →     25       (-3.85%)
+ │ │ ├ sirius::Hamiltonian0                                                5.92 ms →   4.60 ms    (-22.38%)          26   →     25       (-3.85%)
+ │ │ │ ├ sirius::Local_operator                                            5.55 ms →   4.22 ms    (-23.93%)          26   →     25       (-3.85%)
  │ │ │ │ ├ sirius::Smooth_periodic_function                              939.98 μs → 921.63 μs     (-1.95%)          26   →     25       (-3.85%)
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 3.73 ms →   2.42 ms    (-35.17%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Non_local_operator                                       65.16 μs →  65.58 μs     (+0.64%)          52   →     50       (-3.85%)
  │ │ │ ├ sirius::D_operator::initialize                                   91.95 μs →  92.81 μs     (+0.93%)          26   →     25       (-3.85%)
  │ │ │ └ sirius::Q_operator::initialize                                   76.64 μs →  77.20 μs     (+0.72%)          26   →     25       (-3.85%)
  │ │ ├ sirius::Band::solve                                                 2.74 s  →   2.81 s      (+2.55%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Hamiltonian_k                                           160.98 μs → 159.09 μs     (-1.17%)          26   →     25       (-3.85%)
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             154.25 μs → 152.31 μs     (-1.26%)          26   →     25       (-3.85%)
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                           5.08 μs →   5.19 μs     (+2.04%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      2.59 s  →   2.69 s      (+4.09%)          26   →     25       (-3.85%)
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             95.14 ms →  98.60 ms     (+3.64%)          26   →     25       (-3.85%)
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                          7.73 ms →   8.18 ms     (+5.74%)         156   →    150       (-3.85%)
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             5.96 ms →   5.89 ms     (-1.13%)          26   →     25       (-3.85%)
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       351.45 μs → 346.96 μs     (-1.28%)          26   →     25       (-3.85%)
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                         2.32 ms →   2.30 ms     (-0.73%)          52   →     50       (-3.85%)
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               2.45 s  →   2.55 s      (+4.18%)          26   →     25       (-3.85%)
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                            130.22 ms → 126.65 ms     (-2.74%)         271   →    277       (+2.21%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            52.08 ms →  50.37 ms     (-3.29%)         271   →    277       (+2.21%)
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       1.77 μs →   2.04 μs    (+14.90%)         271   →    277       (+2.21%)
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                     1.44 μs →   1.70 μs    (+17.77%)         271   →    277       (+2.21%)
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                     315.61 ns → 403.95 ns    (+27.99%)         271   →    277       (+2.21%)
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                    438.74 ns → 598.15 ns    (+36.33%)         271   →    277       (+2.21%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      7.43 ms →   7.41 ms     (-0.27%)         271   →    277       (+2.21%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                        23.99 ms →  23.36 ms     (-2.64%)         271   →    277       (+2.21%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                          23.35 ms →  22.75 ms     (-2.58%)         542   →    554       (+2.21%)
  │ │ │ │   ├ sddk::orthogonalize                                          32.97 ms →  32.10 ms     (-2.64%)         271   →    277       (+2.21%)
  │ │ │ │   │ ├ sddk::inner                                                 4.88 ms →   4.74 ms     (-3.04%)         516   →    529       (+2.52%)
- │ │ │ │   │ │ └ sddk::inner|local                                        22.84 μs →  26.74 μs    (+17.05%)         516   →    529       (+2.52%)
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                                 618.66 μs → 593.34 μs     (-4.09%)         271   →    277       (+2.21%)
  │ │ │ │   │ ├ sddk::orthogonalize|transform                               9.76 ms →   9.37 ms     (-3.99%)         271   →    277       (+2.21%)
  │ │ │ │   │ └ sddk::transform                                            14.70 ms →  14.39 ms     (-2.11%)         245   →    252       (+2.86%)
- │ │ │ │   │   ├ sddk::transform|init                                     18.20 μs →  21.03 μs    (+15.53%)         245   →    252       (+2.86%)
- │ │ │ │   │   └ sddk::transform|local                                     7.28 μs →   8.77 μs    (+20.51%)         735   →    756       (+2.86%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               9.27 ms →   9.01 ms     (-2.78%)         271   →    277       (+2.21%)
  │ │ │ │   │ └ sddk::inner                                                 9.02 ms →   8.77 ms     (-2.81%)         271   →    277       (+2.21%)
- │ │ │ │   │   └ sddk::inner|local                                        22.54 μs →  26.84 μs    (+19.08%)         271   →    277       (+2.21%)
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                     34.16 ms →  34.86 ms     (+2.04%)         271   →    277       (+2.21%)
  │ │ │ │   ├ sirius::residuals                                            13.89 ms →  13.59 ms     (-2.16%)         262   →    268       (+2.29%)
  │ │ │ │   │ ├ sddk::transform                                            12.58 ms →  12.25 ms     (-2.61%)         252   →    259       (+2.78%)
- │ │ │ │   │ │ ├ sddk::transform|init                                     13.88 μs →  16.67 μs    (+20.04%)         252   →    259       (+2.78%)
- │ │ │ │   │ │ └ sddk::transform|local                                     9.66 μs →  11.09 μs    (+14.80%)         504   →    518       (+2.78%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals                 1.62 ms →   1.58 ms     (-2.44%)         252   →    259       (+2.78%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      76.23 ms →  77.17 ms     (+1.23%)          53   →     52       (-1.89%)
  │ │ │ │     └ sddk::transform                                            50.27 ms →  50.57 ms     (+0.60%)          80   →     79       (-1.25%)
- │ │ │ │       ├ sddk::transform|init                                      9.74 μs →  11.39 μs    (+16.84%)          80   →     79       (-1.25%)
- │ │ │ │       └ sddk::transform|local                                     8.70 μs →  10.12 μs    (+16.30%)         107   →    106       (-0.93%)
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                           445.38 ns → 448.24 ns     (+0.64%)          26   →     25       (-3.85%)
  │ │ │ └ sirius::K_point_set::sync_band_energies                          28.16 μs →  28.21 μs     (+0.17%)          26   →     25       (-3.85%)
  │ │ ├ sirius::K_point_set::find_band_occupancies                        600.61 μs → 611.07 μs     (+1.74%)          26   →     25       (-3.85%)
  │ │ ├ sirius::Density::generate                                         778.51 ms → 776.45 ms     (-0.26%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Density::generate_valence                               402.64 ms → 401.16 ms     (-0.37%)          26   →     25       (-3.85%)
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                             8.18 μs →   3.34 μs    (-59.17%)          26   →     25       (-3.85%)
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                           7.35 μs →   3.03 μs    (-58.69%)          26   →     25       (-3.85%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  100.43 ms → 100.38 ms     (-0.05%)          26   →     25       (-3.85%)
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         7.71 μs →  12.44 μs    (+61.47%)          26   →     25       (-3.85%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        7.12 ms →   7.13 ms     (+0.11%)          26   →     25       (-3.85%)
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          91.40 ms →  91.31 ms     (-0.09%)          26   →     25       (-3.85%)
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       580.38 ns → 559.12 ns     (-3.66%)          26   →     25       (-3.85%)
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  163.99 ms → 162.97 ms     (-0.62%)          26   →     25       (-3.85%)
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.63 ms →   1.64 ms     (+0.58%)          26   →     25       (-3.85%)
  │ │ │ │ └ sirius::Density::augment                                       88.28 ms →  88.23 ms     (-0.06%)          26   →     25       (-3.85%)
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.06 ms →  88.00 ms     (-0.07%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Field4D::symmetrize                                     286.36 ms → 280.73 ms     (-1.97%)          26   →     25       (-3.85%)
  │ │ │ │ └ sirius::symmetrize_function|fpw                               286.36 ms → 280.72 ms     (-1.97%)          26   →     25       (-3.85%)
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             29.61 ms →  25.37 ms    (-14.30%)          26   →     25       (-3.85%)
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       226.31 ms → 230.78 ms     (+1.98%)          26   →     25       (-3.85%)
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                            29.28 ms →  23.41 ms    (-20.07%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       80.17 ms →  81.94 ms     (+2.21%)          26   →     25       (-3.85%)
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   5.75 ms →   9.04 ms    (+57.34%)          26   →     25       (-3.85%)
  │ │ ├ sirius::Density::mix                                              213.05 ms → 217.28 ms     (+1.98%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Density::mixer_input                                    975.35 μs → 929.73 μs     (-4.68%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Periodic_function|inner                                  10.20 ms →  10.75 ms     (+5.38%)         334   →    319       (-4.49%)
  │ │ │ │ └ sirius::Periodic_function|inner_local                           9.93 ms →  10.30 ms     (+3.73%)         334   →    319       (-4.49%)
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                  9.93 ms →  10.30 ms     (+3.73%)         334   →    319       (-4.49%)
  │ │ │ └ sirius::Density::mixer_output                                     7.07 ms →   7.46 ms     (+5.47%)          26   →     25       (-3.85%)
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 6.23 ms →   6.66 ms     (+6.89%)          26   →     25       (-3.85%)
  │ │ ├ sirius::Potential::generate                                       572.76 ms → 567.19 ms     (-0.97%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Potential::poisson                                      126.44 ms → 126.62 ms     (+0.14%)          26   →     25       (-3.85%)
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 6.79 ms →   5.10 ms    (-24.94%)          26   →     25       (-3.85%)
  │ │ │ │ └ sirius::Periodic_function|inner                                10.69 ms →  10.32 ms     (-3.48%)          26   →     25       (-3.85%)
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.43 ms →   9.88 ms     (-5.25%)          26   →     25       (-3.85%)
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.43 ms →   9.88 ms     (-5.25%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Periodic_function::add                                  559.93 μs → 548.47 μs     (-2.05%)          52   →     50       (-3.85%)
  │ │ │ ├ sirius::Potential::xc                                            51.48 ms →  48.47 ms     (-5.85%)          26   →     25       (-3.85%)
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           49.15 ms →  46.20 ms     (-6.02%)          26   →     25       (-3.85%)
  │ │ │ │   ├ sirius::Smooth_periodic_function                              2.97 ms →   2.95 ms     (-0.77%)          52   →     50       (-3.85%)
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               8.00 ms →   5.18 ms    (-35.28%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   6.27 ms →   6.41 ms     (+2.23%)          26   →     25       (-3.85%)
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    90.91 ms →  90.94 ms     (+0.03%)          26   →     25       (-3.85%)
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             295.25 ms → 292.38 ms     (-0.97%)          26   →     25       (-3.85%)
  │ │ ├ sirius::Field4D::symmetrize                                       292.41 ms → 284.32 ms     (-2.77%)          26   →     25       (-3.85%)
  │ │ │ └ sirius::symmetrize_function|fpw                                 292.41 ms → 284.31 ms     (-2.77%)          26   →     25       (-3.85%)
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                               32.51 ms →  28.09 ms    (-13.60%)          26   →     25       (-3.85%)
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         225.80 ms → 228.75 ms     (+1.31%)          26   →     25       (-3.85%)
+ │ │ │   └ sddk::Gvec_shells::remap_backward                              30.32 ms →  23.72 ms    (-21.77%)          26   →     25       (-3.85%)
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.13 ms →   7.50 ms    (+46.10%)          26   →     25       (-3.85%)
  │ │ ├ sirius::Periodic_function|inner                                    10.17 ms →  10.72 ms     (+5.37%)         182   →    175       (-3.85%)
  │ │ │ └ sirius::Periodic_function|inner_local                             9.85 ms →  10.17 ms     (+3.18%)         182   →    175       (-3.85%)
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                    9.85 ms →  10.17 ms     (+3.18%)         182   →    175       (-3.85%)
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.50 ms →  10.27 ms     (-2.17%)          78   →     75       (-3.85%)
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.20 ms →   9.71 ms     (-4.89%)          78   →     75       (-3.85%)
  │ │ ├ sirius::Periodic_function::integrate                                9.96 ms →  10.03 ms     (+0.67%)          26   →     25       (-3.85%)
  │ │ └ sirius::Density::get_magnetisation                                109.89 μs → 111.52 μs     (+1.48%)          26   →     25       (-3.85%)
  │ │   └ sirius::Density::compute_atomic_mag_mom                         105.47 μs → 106.87 μs     (+1.32%)          26   →     25       (-3.85%)
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                         6.96 ms →   5.57 ms    (-19.90%)           2   →      2               
  │ ├ sirius::Periodic_function|inner                                      10.41 ms →  10.56 ms     (+1.45%)           6   →      6               
  │ │ └ sirius::Periodic_function|inner_local                              10.04 ms →  10.55 ms     (+5.03%)           6   →      6               
  │ │   └ sirius::Smooth_periodic_function|inner_local                     10.04 ms →  10.55 ms     (+5.03%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.75 ms →  10.11 ms     (-5.98%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.15 ms →  10.10 ms     (-0.50%)           3   →      3               
  ├ sirius::Periodic_function|inner                                        10.34 ms →  10.78 ms     (+4.30%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                10.08 ms →  10.78 ms     (+6.92%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.08 ms →  10.77 ms     (+6.92%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.70 ms →  10.02 ms     (-6.39%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.44 ms →  10.01 ms     (-4.06%)           1   →      1               
- └ sirius::finalize                                                      184.66 ms → 217.50 ms    (+17.78%)           1   →      1               
```
