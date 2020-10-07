# Benchmark cec8cbfd14a8c81a238f6b8e8163f5955b8ecb39 vs 647643e79c91101edea17dbd509be559f0e7531c
```diff
  ================================================================================================================================================
                                                                                      Mean                                    #
  ------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                  229.71 s  → 218.62 s      (-4.83%)           1   →      1               
  ├ sirius::initialize                                                      2.72 s  →   2.77 s      (+1.82%)           1   →      1               
  ├ sirius::Simulation_context::initialize                                  3.02 s  →   3.13 s      (+3.48%)           1   →      1               
+ │ ├ sirius::Simulation_context::init_comm                                11.19 ms →   7.85 ms    (-29.82%)           1   →      1               
- │ ├ sirius::Unit_cell::initialize                                       277.71 ms → 309.99 ms    (+11.62%)           1   →      1               
- │ │ ├ sirius::Atom_type::init                                           126.86 ms → 143.23 ms    (+12.90%)           2   →      2               
  │ │ └ sirius::Unit_cell::update                                          23.91 ms →  23.45 ms     (-1.93%)           1   →      1               
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                        6.24 ms →   6.44 ms     (+3.26%)           1   →      1               
  │ │   └ sirius::Unit_cell::get_symmetry                                  17.63 ms →  16.96 ms     (-3.80%)           1   →      1               
  │ │     └ sirius::Unit_cell_symmetry                                     17.61 ms →  16.94 ms     (-3.80%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|spg                                4.14 ms →   4.15 ms     (+0.35%)           1   →      1               
  │ │       ├ sirius::Unit_cell_symmetry|equiv                              2.32 ms →   2.35 ms     (+1.47%)           1   →      1               
  │ │       └ sirius::Unit_cell_symmetry|mag                              102.53 μs → 102.27 μs     (-0.25%)           1   →      1               
  │ └ sirius::Simulation_context::update                                    2.68 s  →   2.76 s      (+2.93%)           1   →      1               
  │   ├ sirius::Unit_cell::update                                          10.84 ms →  10.86 ms     (+0.19%)           1   →      1               
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                        4.46 ms →   4.46 ms     (+0.04%)           1   →      1               
  │   │ └ sirius::Unit_cell::get_symmetry                                   6.35 ms →   6.37 ms     (+0.26%)           1   →      1               
  │   │   └ sirius::Unit_cell_symmetry                                      6.33 ms →   6.35 ms     (+0.28%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|spg                                3.82 ms →   3.86 ms     (+1.10%)           1   →      1               
  │   │     ├ sirius::Unit_cell_symmetry|equiv                              2.34 ms →   2.31 ms     (-1.36%)           1   →      1               
  │   │     └ sirius::Unit_cell_symmetry|mag                              100.89 μs → 100.53 μs     (-0.35%)           1   →      1               
  │   ├ sirius::Radial_integrals|aug                                       64.51 ms →  63.91 ms     (-0.93%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_core_pseudo                            5.14 ms →   5.13 ms     (-0.25%)           2   →      2               
  │   ├ sirius::Radial_integrals|rho_pseudo                                 4.47 ms →   4.46 ms     (-0.12%)           1   →      1               
  │   ├ sirius::Radial_integrals|vloc                                      21.89 ms →  21.90 ms     (+0.07%)           2   →      2               
  │   ├ sirius::Radial_integrals|beta                                      14.82 ms →  14.79 ms     (-0.23%)           2   →      2               
  │   ├ sirius::Radial_integrals|atomic_wfs                                19.66 ms →  19.74 ms     (+0.40%)           4   →      4               
  │   ├ sddk::Gvec::init                                                  172.99 ms → 172.15 ms     (-0.48%)           2   →      2               
  │   │ └ sddk::Gvec::find_gvec_shells                                    130.41 ms → 129.57 ms     (-0.64%)           2   →      2               
  │   ├ sddk::Gvec_shells                                                 175.62 ms → 181.25 ms     (+3.21%)           1   →      1               
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx                  1.32 ms →   1.33 ms     (+0.62%)           1   →      1               
  │   └ sirius::Augmentation_operator::generate_pw_coeffs                 293.56 ms → 301.50 ms     (+2.70%)           2   →      2               
  ├ sirius::K_point_set::create_k_mesh                                     74.05 ms →  74.43 ms     (+0.51%)           1   →      1               
- │ ├ sirius::K_point::K_point                                              2.36 μs →   3.03 μs    (+28.47%)           4   →      4               
  │ └ sirius::K_point_set::initialize                                      73.95 ms →  74.34 ms     (+0.52%)           1   →      1               
  │   └ sirius::K_point::initialize                                        18.48 ms →  18.57 ms     (+0.52%)           4   →      4               
  │     ├ sirius::K_point::generate_gkvec                                  13.93 ms →  13.99 ms     (+0.44%)           4   →      4               
  │     │ └ sddk::Gvec::init                                                3.87 ms →   3.85 ms     (-0.39%)           4   →      4               
  │     ├ sddk::matrix_storage::matrix_storage                              8.32 μs →   8.72 μs     (+4.78%)           4   →      4               
  │     └ sirius::K_point::update                                           3.25 ms →   3.29 ms     (+1.15%)           4   →      4               
  │       └ sirius::Beta_projectors                                         1.75 ms →   1.78 ms     (+1.53%)           4   →      4               
  │         └ sirius::Beta_projectors::generate_pw_coefs_t                923.50 μs → 939.51 μs     (+1.73%)           4   →      4               
  ├ sirius::Smooth_periodic_function                                        5.21 ms →   5.20 ms     (-0.23%)           2   →      2               
  ├ sirius::Potential                                                     155.30 ms → 160.10 ms     (+3.09%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.72 ms →   5.77 ms     (+1.02%)           6   →      6               
  │ └ sirius::Potential::update                                           120.31 ms → 124.72 ms     (+3.67%)           1   →      1               
  │   └ sirius::Potential::generate_local_potential                       119.61 ms → 124.00 ms     (+3.67%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              108.23 ms → 115.11 ms     (+6.35%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                  10.51 ms →   8.00 ms    (-23.92%)           1   →      1               
  ├ sirius::Density                                                       130.32 ms → 132.02 ms     (+1.31%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.08 ms →   5.16 ms     (+1.53%)           2   →      2               
  │ └ sirius::Density::update                                             119.87 ms → 121.41 ms     (+1.28%)           1   →      1               
  │   └ sirius::Density::generate_pseudo_core_charge_density              119.44 ms → 121.00 ms     (+1.31%)           1   →      1               
  │     ├ sirius::rho_core_ri_pseudo|values                               103.69 μs → 103.25 μs     (-0.43%)           1   →      1               
  │     ├ sirius::Simulation_context::make_periodic_function              110.33 ms → 115.33 ms     (+4.54%)           1   →      1               
+ │     └ sirius::Smooth_periodic_function::fft_transform                   8.58 ms →   5.11 ms    (-40.42%)           1   →      1               
  ├ sirius::Density::initial_density                                      167.17 ms → 178.68 ms     (+6.89%)           1   →      1               
- │ ├ sirius::Simulation_context::make_periodic_function                  110.03 ms → 123.61 ms    (+12.35%)           1   →      1               
+ │ ├ sirius::Smooth_periodic_function::fft_transform                       6.24 ms →   5.51 ms    (-11.68%)           2   →      2               
  │ └ sirius::Periodic_function::integrate                                 11.75 ms →  11.60 ms     (-1.31%)           1   →      1               
  ├ sirius::Potential::generate                                           582.82 ms → 602.85 ms     (+3.44%)           1   →      1               
  │ ├ sirius::Potential::poisson                                          127.16 ms → 137.48 ms     (+8.12%)           1   →      1               
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                     8.05 ms →   5.28 ms    (-34.41%)           1   →      1               
  │ │ └ sirius::Periodic_function|inner                                    10.75 ms →  10.90 ms     (+1.36%)           1   →      1               
  │ │   └ sirius::Periodic_function|inner_local                            10.73 ms →  10.50 ms     (-2.14%)           1   →      1               
  │ │     └ sirius::Smooth_periodic_function|inner_local                   10.73 ms →  10.50 ms     (-2.14%)           1   →      1               
  │ ├ sirius::Periodic_function::add                                      560.18 μs → 586.68 μs     (+4.73%)           2   →      2               
  │ ├ sirius::Potential::xc                                                53.65 ms →  53.94 ms     (+0.53%)           1   →      1               
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                               51.37 ms →  51.62 ms     (+0.49%)           1   →      1               
  │ │   ├ sirius::Smooth_periodic_function                                  5.62 ms →   5.66 ms     (+0.70%)           2   →      2               
  │ │   └ sirius::Smooth_periodic_function::fft_transform                   5.23 ms →   5.30 ms     (+1.46%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function::fft_transform                       5.77 ms →   5.75 ms     (-0.34%)           1   →      1               
  │ ├ sirius::Potential::generate_D_operator_matrix                        93.50 ms →  93.39 ms     (-0.12%)           1   →      1               
  │ └ sirius::Potential::generate_PAW_effective_potential                 300.31 ms → 309.75 ms     (+3.14%)           1   →      1               
  ├ sirius::Hamiltonian0                                                    8.41 ms →   8.40 ms     (-0.07%)           1   →      1               
  │ ├ sirius::Local_operator                                                8.06 ms →   8.06 ms     (+0.02%)           1   →      1               
  │ │ ├ sirius::Smooth_periodic_function                                    4.72 ms →   4.71 ms     (-0.23%)           1   →      1               
  │ │ └ sirius::Smooth_periodic_function::fft_transform                     2.43 ms →   2.44 ms     (+0.40%)           1   →      1               
  │ ├ sirius::Non_local_operator                                           64.52 μs →  62.50 μs     (-3.13%)           2   →      2               
  │ ├ sirius::D_operator::initialize                                       96.76 μs →  94.31 μs     (-2.54%)           1   →      1               
  │ └ sirius::Q_operator::initialize                                       68.48 μs →  68.13 μs     (-0.50%)           1   →      1               
  ├ sirius::Band::initialize_subspace                                       3.21 s  →   3.13 s      (-2.59%)           1   →      1               
  │ ├ sirius::Hamiltonian_k                                               204.88 μs → 201.46 μs     (-1.67%)           4   →      4               
  │ │ ├ sirius::Local_operator::prepare_k                                 199.98 μs → 196.31 μs     (-1.84%)           4   →      4               
- │ │ └ sirius::Beta_projectors_base::prepare                               3.18 μs →   3.54 μs    (+11.33%)           4   →      4               
  │ ├ sirius::Band::initialize_subspace|kp                                802.87 ms → 782.10 ms     (-2.59%)           4   →      4               
  │ │ ├ sddk::matrix_storage::matrix_storage                               32.18 ms →  33.09 ms     (+2.83%)          16   →     16               
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                    14.51 ms →  14.83 ms     (+2.21%)           4   →      4               
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                             5.34 ms →   5.50 ms     (+3.11%)           4   →      4               
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                  364.67 ms → 360.35 ms     (-1.18%)           4   →      4               
  │ │ │ ├ sirius::Local_operator::apply_h                                 265.63 ms → 263.69 ms     (-0.73%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                            70.86 ms →  68.74 ms     (-2.99%)           4   →      4               
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                          16.29 ms →  16.97 ms     (+4.16%)           4   →      4               
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                  16.29 ms →  16.97 ms     (+4.16%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                      48.15 ms →  45.38 ms     (-5.76%)           4   →      4               
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                            16.10 ms →  16.72 ms     (+3.88%)           4   →      4               
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                    16.09 ms →  16.72 ms     (+3.88%)           4   →      4               
  │ │ │ │ └ sddk::matrix_storage::remap_backward                           53.49 ms →  53.20 ms     (-0.55%)           4   →      4               
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                     35.46 ms →  35.19 ms     (-0.78%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::generate                            1.93 ms →   1.95 ms     (+0.92%)           4   →      4               
  │ │ │ ├ sirius::Beta_projectors_base::inner                              42.80 ms →  40.31 ms     (-5.82%)           4   →      4               
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                        9.66 ms →   7.14 ms    (-26.07%)           4   →      4               
  │ │ │ └ sirius::Non_local_operator::apply                                27.13 ms →  27.18 ms     (+0.19%)           8   →      8               
+ │ │ ├ sirius::Band::set_subspace_mtrx                                    20.89 ms →  14.14 ms    (-32.33%)           8   →      8               
+ │ │ │ └ sddk::inner                                                      20.84 ms →  14.08 ms    (-32.42%)           8   →      8               
  │ │ │   └ sddk::inner|local                                              51.80 μs →  49.11 μs     (-5.20%)           8   →      8               
  │ │ ├ Eigensolver_scalapack|pzhegvx                                     127.79 ms → 119.07 ms     (-6.82%)           4   →      4               
  │ │ └ sddk::transform                                                    27.66 ms →  27.97 ms     (+1.12%)           4   →      4               
  │ │   ├ sddk::transform|init                                             25.20 μs →  25.10 μs     (-0.40%)           4   →      4               
+ │ │   ├ sddk::transform|mpi                                               1.23 ms → 956.35 μs    (-22.00%)           4   →      4               
  │ │   └ sddk::transform|local                                            22.30 μs →  23.53 μs     (+5.52%)           4   →      4               
  │ └ sirius::Beta_projectors_base::dismiss                               386.75 ns → 418.00 ns     (+8.08%)           4   →      4               
  ├ sirius::DFT_ground_state::scf_loop                                    218.73 s  → 207.57 s      (-5.10%)           1   →      1               
  │ ├ sirius::Smooth_periodic_function                                      5.66 ms →   5.68 ms     (+0.38%)          19   →     19               
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                          8.40 s  →   7.97 s      (-5.11%)          26   →     26               
  │ │ ├ sirius::Hamiltonian0                                                5.00 ms →   4.61 ms     (-7.70%)          26   →     26               
  │ │ │ ├ sirius::Local_operator                                            4.64 ms →   4.25 ms     (-8.36%)          26   →     26               
  │ │ │ │ ├ sirius::Smooth_periodic_function                              976.58 μs → 964.04 μs     (-1.28%)          26   →     26               
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                 2.78 ms →   2.40 ms    (-13.62%)          26   →     26               
  │ │ │ ├ sirius::Non_local_operator                                       64.67 μs →  64.85 μs     (+0.28%)          52   →     52               
  │ │ │ ├ sirius::D_operator::initialize                                   90.54 μs →  92.95 μs     (+2.66%)          26   →     26               
  │ │ │ └ sirius::Q_operator::initialize                                   69.98 μs →  69.21 μs     (-1.10%)          26   →     26               
  │ │ ├ sirius::Band::solve                                                 6.29 s  →   5.87 s      (-6.72%)          26   →     26               
  │ │ │ ├ sirius::Hamiltonian_k                                           197.60 μs → 197.26 μs     (-0.17%)         104   →    104               
  │ │ │ │ ├ sirius::Local_operator::prepare_k                             192.62 μs → 191.72 μs     (-0.47%)         104   →    104               
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                           3.67 μs →   4.10 μs    (+11.75%)         104   →    104               
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                      1.57 s  →   1.47 s      (-6.72%)         104   →    104               
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc             11.83 ms →  11.97 ms     (+1.15%)         104   →    104               
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                        562.33 ns → 622.58 ns    (+10.72%)         624   →    624               
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                             1.84 ms →   1.85 ms     (+0.48%)         104   →    104               
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                       352.92 μs → 351.77 μs     (-0.32%)         104   →    104               
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                       549.72 μs → 553.68 μs     (+0.72%)         208   →    208               
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter               1.55 s  →   1.44 s      (-6.83%)         104   →    104               
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                             71.24 ms →  69.35 ms     (-2.65%)         910   →    905       (-0.55%)
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                            45.39 ms →  44.04 ms     (-2.98%)         910   →    905       (-0.55%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                       9.01 ms →   8.30 ms     (-7.89%)         910   →    905       (-0.55%)
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                   231.32 μs → 229.08 μs     (-0.97%)         910   →    905       (-0.55%)
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc             2.01 ms →   1.98 ms     (-1.59%)         104   →    104               
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 7.48 ms →   6.77 ms     (-9.49%)         910   →    905       (-0.55%)
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                      87.16 μs →  88.08 μs     (+1.06%)         910   →    905       (-0.55%)
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc             743.53 μs → 746.96 μs     (+0.46%)         104   →    104               
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                     10.35 ms →   9.60 ms     (-7.22%)         910   →    905       (-0.55%)
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi                6.73 ms →   5.95 ms    (-11.48%)         910   →    905       (-0.55%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                      1.52 ms →   1.53 ms     (+0.42%)         910   →    905       (-0.55%)
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                         9.32 ms →   8.62 ms     (-7.59%)         910   →    905       (-0.55%)
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm                  1.99 ms →   1.27 ms    (-36.21%)         910   →    905       (-0.55%)
  │ │ │ │   │ └ sirius::Non_local_operator::apply                           7.49 ms →   7.57 ms     (+1.10%)        1.82 K →   1.81 K     (-0.55%)
  │ │ │ │   ├ sddk::orthogonalize                                          18.30 ms →  17.38 ms     (-5.06%)         910   →    905       (-0.55%)
+ │ │ │ │   │ ├ sddk::inner                                                 2.19 ms →   1.97 ms    (-10.16%)        1.72 K →   1.71 K     (-0.58%)
  │ │ │ │   │ │ └ sddk::inner|local                                        34.35 μs →  34.69 μs     (+0.99%)        1.72 K →   1.71 K     (-0.58%)
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                                 841.89 μs → 792.73 μs     (-5.84%)         910   →    905       (-0.55%)
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                                 932.48 μs → 760.57 μs    (-18.44%)         910   →    905       (-0.55%)
  │ │ │ │   │ └ sddk::transform                                             2.78 ms →   2.71 ms     (-2.64%)        3.54 K →   3.52 K     (-0.57%)
  │ │ │ │   │   ├ sddk::transform|init                                     13.58 μs →  14.10 μs     (+3.87%)        3.54 K →   3.52 K     (-0.57%)
+ │ │ │ │   │   ├ sddk::transform|mpi                                     234.14 μs → 148.40 μs    (-36.62%)        3.54 K →   3.52 K     (-0.57%)
  │ │ │ │   │   └ sddk::transform|local                                     9.78 μs →   9.32 μs     (-4.79%)        5.15 K →   5.12 K     (-0.58%)
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                               5.69 ms →   5.37 ms     (-5.71%)         910   →    905       (-0.55%)
  │ │ │ │   │ └ sddk::inner                                                 3.95 ms →   3.64 ms     (-7.68%)         910   →    905       (-0.55%)
  │ │ │ │   │   └ sddk::inner|local                                        28.96 μs →  28.92 μs     (-0.15%)         910   →    905       (-0.55%)
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                                70.39 ms →  62.57 ms    (-11.12%)         910   →    905       (-0.55%)
  │ │ │ │   ├ sirius::residuals                                             5.69 ms →   5.57 ms     (-2.20%)         893   →    886       (-0.78%)
  │ │ │ │   │ ├ sddk::transform                                             5.01 ms →   4.94 ms     (-1.35%)         845   →    840       (-0.59%)
  │ │ │ │   │ │ ├ sddk::transform|init                                     19.28 μs →  19.17 μs     (-0.58%)         845   →    840       (-0.59%)
+ │ │ │ │   │ │ ├ sddk::transform|mpi                                     349.48 μs → 191.59 μs    (-45.18%)         845   →    840       (-0.59%)
  │ │ │ │   │ │ └ sddk::transform|local                                    10.80 μs →  10.62 μs     (-1.64%)        1.69 K →   1.68 K     (-0.59%)
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals               713.89 μs → 689.71 μs     (-3.39%)         845   →    840       (-0.59%)
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi      25.48 ms →  24.99 ms     (-1.95%)         210   →    210               
  │ │ │ │     └ sddk::transform                                            16.83 ms →  16.50 ms     (-1.97%)         316   →    316               
  │ │ │ │       ├ sddk::transform|init                                     12.45 μs →  12.46 μs     (+0.02%)         316   →    316               
+ │ │ │ │       ├ sddk::transform|mpi                                       1.18 ms → 849.01 μs    (-28.18%)         316   →    316               
  │ │ │ │       └ sddk::transform|local                                    11.47 μs →  11.08 μs     (-3.36%)         422   →    422               
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                           652.34 ns → 451.63 ns    (-30.77%)         104   →    104               
  │ │ │ └ sirius::K_point_set::sync_band_energies                          20.23 μs →  19.83 μs     (-1.98%)          26   →     26               
  │ │ ├ sirius::K_point_set::find_band_occupancies                        600.22 μs → 604.24 μs     (+0.67%)          26   →     26               
  │ │ ├ sirius::Density::generate                                         904.17 ms → 895.63 ms     (-0.94%)          26   →     26               
  │ │ │ ├ sirius::Density::generate_valence                               542.85 ms → 524.46 ms     (-3.39%)          26   →     26               
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                            26.63 ms →  24.17 ms     (-9.24%)         104   →    104               
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                           8.32 μs →   6.31 μs    (-24.19%)         104   →    104               
+ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                  15.72 μs →  12.35 μs    (-21.44%)           8   →      8               
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                      22.58 ms →  20.11 ms    (-10.94%)         104   →    104               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                   31.60 ms →  29.86 ms     (-5.52%)         104   →    104               
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                         9.62 μs →  11.88 μs    (+23.47%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                        1.45 ms →   1.46 ms     (+0.87%)         104   →    104               
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                          29.65 ms →  27.89 ms     (-5.96%)         104   →    104               
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    5.52 ms →   3.75 ms    (-32.19%)         104   →    104               
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       485.77 ns → 508.88 ns     (+4.76%)         104   →    104               
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                   42.70 ms →  42.67 ms     (-0.08%)         104   →    104               
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 1.64 ms →   1.64 ms     (-0.37%)          26   →     26               
  │ │ │ │ └ sirius::Density::augment                                       88.88 ms →  89.04 ms     (+0.18%)          26   →     26               
  │ │ │ │   └ sirius::Density::generate_rho_aug                            88.65 ms →  88.80 ms     (+0.16%)          26   →     26               
  │ │ │ ├ sirius::Field4D::symmetrize                                     267.63 ms → 278.39 ms     (+4.02%)          26   →     26               
  │ │ │ │ └ sirius::symmetrize_function|fpw                               267.63 ms → 278.39 ms     (+4.02%)          26   →     26               
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                             24.59 ms →  24.49 ms     (-0.40%)          26   →     26               
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                       217.23 ms → 228.19 ms     (+5.05%)          26   →     26               
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                            24.06 ms →  23.94 ms     (-0.49%)          26   →     26               
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                       80.61 ms →  81.76 ms     (+1.43%)          26   →     26               
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform                   9.49 ms →   7.44 ms    (-21.60%)          26   →     26               
  │ │ ├ sirius::Density::mix                                              221.07 ms → 213.46 ms     (-3.44%)          26   →     26               
  │ │ │ ├ sirius::Density::mixer_input                                    953.45 μs → 961.56 μs     (+0.85%)          26   →     26               
+ │ │ │ ├ sirius::Periodic_function|inner                                  11.61 ms →  10.28 ms    (-11.46%)         320   →    334       (+4.37%)
+ │ │ │ │ └ sirius::Periodic_function|inner_local                          11.25 ms →   9.99 ms    (-11.20%)         320   →    334       (+4.37%)
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local                 11.25 ms →   9.99 ms    (-11.21%)         320   →    334       (+4.37%)
  │ │ │ └ sirius::Density::mixer_output                                     6.55 ms →   6.34 ms     (-3.21%)          26   →     26               
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform                 5.72 ms →   5.49 ms     (-4.04%)          26   →     26               
  │ │ ├ sirius::Potential::generate                                       571.41 ms → 579.47 ms     (+1.41%)          26   →     26               
  │ │ │ ├ sirius::Potential::poisson                                      127.46 ms → 137.47 ms     (+7.86%)          26   →     26               
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 7.87 ms →   5.17 ms    (-34.24%)          26   →     26               
  │ │ │ │ └ sirius::Periodic_function|inner                                10.82 ms →  10.77 ms     (-0.54%)          26   →     26               
  │ │ │ │   └ sirius::Periodic_function|inner_local                        10.64 ms →  10.48 ms     (-1.50%)          26   →     26               
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local               10.64 ms →  10.48 ms     (-1.50%)          26   →     26               
  │ │ │ ├ sirius::Periodic_function::add                                  553.84 μs → 567.16 μs     (+2.41%)          52   →     52               
  │ │ │ ├ sirius::Potential::xc                                            49.93 ms →  49.45 ms     (-0.95%)          26   →     26               
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                           47.59 ms →  47.09 ms     (-1.04%)          26   →     26               
  │ │ │ │   ├ sirius::Smooth_periodic_function                              3.03 ms →   3.04 ms     (+0.21%)          52   →     52               
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform               6.03 ms →   5.34 ms    (-11.42%)          26   →     26               
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform                   7.10 ms →   6.61 ms     (-6.94%)          26   →     26               
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                    91.38 ms →  90.92 ms     (-0.51%)          26   →     26               
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential             293.16 ms → 292.57 ms     (-0.20%)          26   →     26               
  │ │ ├ sirius::Field4D::symmetrize                                       272.65 ms → 282.72 ms     (+3.69%)          26   →     26               
  │ │ │ └ sirius::symmetrize_function|fpw                                 272.65 ms → 282.72 ms     (+3.69%)          26   →     26               
  │ │ │   ├ sddk::Gvec_shells::remap_forward                               27.53 ms →  27.19 ms     (-1.23%)          26   →     26               
  │ │ │   ├ sirius::symmetrize_function|fpw|local                         217.52 ms → 228.09 ms     (+4.86%)          26   →     26               
  │ │ │   └ sddk::Gvec_shells::remap_backward                              23.83 ms →  23.62 ms     (-0.88%)          26   →     26               
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                     5.70 ms →   5.67 ms     (-0.51%)          26   →     26               
  │ │ ├ sirius::Periodic_function|inner                                    11.64 ms →  10.53 ms     (-9.55%)         182   →    182               
+ │ │ │ └ sirius::Periodic_function|inner_local                            11.11 ms →   9.97 ms    (-10.25%)         182   →    182               
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                   11.11 ms →   9.97 ms    (-10.25%)         182   →    182               
  │ │ ├ sirius::Smooth_periodic_function|inner                             10.68 ms →  10.71 ms     (+0.30%)          78   →     78               
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                     10.28 ms →  10.34 ms     (+0.56%)          78   →     78               
  │ │ ├ sirius::Periodic_function::integrate                               10.45 ms →  10.09 ms     (-3.41%)          26   →     26               
+ │ │ └ sirius::Density::get_magnetisation                                147.74 μs → 113.02 μs    (-23.50%)          26   →     26               
+ │ │   └ sirius::Density::compute_atomic_mag_mom                         142.22 μs → 107.81 μs    (-24.20%)          26   →     26               
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                         5.11 ms →   5.14 ms     (+0.46%)           2   →      2               
+ │ ├ sirius::Periodic_function|inner                                      11.45 ms →  10.03 ms    (-12.45%)           6   →      6               
+ │ │ └ sirius::Periodic_function|inner_local                              11.09 ms →   9.82 ms    (-11.43%)           6   →      6               
+ │ │   └ sirius::Smooth_periodic_function|inner_local                     11.09 ms →   9.82 ms    (-11.43%)           6   →      6               
  │ └ sirius::Smooth_periodic_function|inner                               10.51 ms →  10.32 ms     (-1.79%)           3   →      3               
  │   └ sirius::Smooth_periodic_function|inner_local                       10.25 ms →  10.07 ms     (-1.78%)           3   →      3               
+ ├ sirius::Periodic_function|inner                                        11.38 ms →  10.24 ms    (-10.04%)           2   →      2               
  │ └ sirius::Periodic_function|inner_local                                11.30 ms →  10.23 ms     (-9.48%)           2   →      2               
  │   └ sirius::Smooth_periodic_function|inner_local                       11.30 ms →  10.23 ms     (-9.46%)           2   →      2               
  ├ sirius::Smooth_periodic_function|inner                                 10.56 ms →  10.36 ms     (-1.98%)           1   →      1               
  │ └ sirius::Smooth_periodic_function|inner_local                         10.34 ms →  10.35 ms     (+0.09%)           1   →      1               
  └ sirius::finalize                                                      329.11 ms → 325.59 ms     (-1.07%)           1   →      1               
```
