# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 4abe991ed1b67a61e2f44af0d6336c92b3f43afd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       72.47 s  →     1038.99 s  (+1333.59%) |       1   →       1              |       72.47 s  →     1038.99 s  (+1333.59%) | 
  ├ sirius::initialize                                                  |        2.89 s  →        2.79 s    (-3.54%) |       1   →       1              |        2.89 s  →        2.79 s    (-3.54%) | 
  ├ sirius::Simulation_context::initialize                              |        3.59 s  →        3.67 s    (+2.15%) |       1   →       1              |        3.59 s  →        3.67 s    (+2.15%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       15.15 ms →       32.19 ms (+112.53%) |       1   →       1              |       15.15 ms →       32.19 ms (+112.53%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      155.58 ms →      127.51 ms  (-18.04%) |       1   →       1              |      155.58 ms →      127.51 ms  (-18.04%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       67.33 ms →       54.06 ms  (-19.70%) |       2   →       2              |      134.66 ms →      108.13 ms  (-19.70%) | 
  │ │ └ sirius::Unit_cell::update                                       |       20.82 ms →       19.31 ms   (-7.29%) |       1   →       1              |       20.82 ms →       19.31 ms   (-7.29%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.59 ms →        5.19 ms  (+44.70%) |       1   →       1              |        3.59 ms →        5.19 ms  (+44.70%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       17.17 ms →       14.06 ms  (-18.12%) |       1   →       1              |       17.17 ms →       14.06 ms  (-18.12%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       17.10 ms →       13.98 ms  (-18.21%) |       1   →       1              |       17.10 ms →       13.98 ms  (-18.21%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.80 ms   (+1.80%) |       1   →       1              |        2.75 ms →        2.80 ms   (+1.80%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      476.23 μs →      525.42 μs  (+10.33%) |       1   →       1              |      476.23 μs →      525.42 μs  (+10.33%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.51 μs →       17.51 μs   (+6.01%) |       1   →       1              |       16.51 μs →       17.51 μs   (+6.01%) | 
  │ └ sirius::Simulation_context::update                                |        3.23 s  →        3.41 s    (+5.81%) |       1   →       1              |        3.23 s  →        3.41 s    (+5.81%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.04 ms →        6.79 ms   (-3.68%) |       1   →       1              |        7.04 ms →        6.79 ms   (-3.68%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.41 ms   (-6.19%) |       1   →       1              |        3.64 ms →        3.41 ms   (-6.19%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.35 ms →        3.33 ms   (-0.78%) |       1   →       1              |        3.35 ms →        3.33 ms   (-0.78%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.31 ms →        3.28 ms   (-0.66%) |       1   →       1              |        3.31 ms →        3.28 ms   (-0.66%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.49%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.49%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      511.66 μs →      505.15 μs   (-1.27%) |       1   →       1              |      511.66 μs →      505.15 μs   (-1.27%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.98 μs →       14.18 μs   (-5.35%) |       1   →       1              |       14.98 μs →       14.18 μs   (-5.35%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      215.27 ms →      211.85 ms   (-1.59%) |       2   →       2              |      430.54 ms →      423.70 ms   (-1.59%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.18 ms   (+0.14%) |       2   →       2              |       30.31 ms →       30.35 ms   (+0.14%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.25 ms   (+0.04%) |       1   →       1              |       13.25 ms →       13.25 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.70 ms →       56.77 ms   (+0.12%) |       2   →       2              |      113.39 ms →      113.53 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.15 ms →       45.09 ms   (-0.13%) |       2   →       2              |       90.29 ms →       90.18 ms   (-0.13%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.37 ms →       60.33 ms   (-0.07%) |       4   →       4              |      241.46 ms →      241.30 ms   (-0.07%) | 
  │   ├ sddk::Gvec::init                                                |       92.81 ms →       92.50 ms   (-0.34%) |       2   →       2              |      185.63 ms →      184.99 ms   (-0.34%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.05 ms →       68.77 ms   (-0.41%) |       2   →       2              |      138.10 ms →      137.53 ms   (-0.41%) | 
+ │   ├ sddk::Gvec_shells                                               |      111.95 ms →       94.44 ms  (-15.64%) |       1   →       1              |      111.95 ms →       94.44 ms  (-15.64%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.97 ms →        1.96 ms   (-0.08%) |       1   →       1              |        1.97 ms →        1.96 ms   (-0.08%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      450.41 ms →      559.29 ms  (+24.17%) |       2   →       2              |      900.81 ms →        1.12 s   (+24.17%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      152.76 ms →      149.01 ms   (-2.45%) |       1   →       1              |      152.76 ms →      149.01 ms   (-2.45%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.17 μs →      780.50 ns  (-33.16%) |       4   →       4              |        4.67 μs →        3.12 μs  (-33.16%) | 
  │ └ sirius::K_point_set::initialize                                   |      152.68 ms →      148.93 ms   (-2.45%) |       1   →       1              |      152.68 ms →      148.93 ms   (-2.45%) | 
  │   └ sirius::K_point::initialize                                     |       28.17 ms →       28.56 ms   (+1.40%) |       1   →       1              |       28.17 ms →       28.56 ms   (+1.40%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.90 ms →       10.93 ms   (+0.31%) |       1   →       1              |       10.90 ms →       10.93 ms   (+0.31%) | 
  │     │ └ sddk::Gvec::init                                            |        4.86 ms →        4.90 ms   (+0.78%) |       1   →       1              |        4.86 ms →        4.90 ms   (+0.78%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.06 μs →        7.91 μs  (+12.10%) |       1   →       1              |        7.06 μs →        7.91 μs  (+12.10%) | 
  │     └ sirius::K_point::update                                       |       14.19 ms →       14.55 ms   (+2.54%) |       1   →       1              |       14.19 ms →       14.55 ms   (+2.54%) | 
  │       └ sirius::Beta_projectors                                     |       10.21 ms →       10.52 ms   (+3.04%) |       1   →       1              |       10.21 ms →       10.52 ms   (+3.04%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.26 ms →        8.59 ms   (+3.94%) |       1   →       1              |        8.26 ms →        8.59 ms   (+3.94%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.59 ms   (+1.18%) |       2   →       2              |        5.12 ms →        5.18 ms   (+1.18%) | 
  ├ sirius::Potential                                                   |       52.32 ms →       49.40 ms   (-5.59%) |       1   →       1              |       52.32 ms →       49.40 ms   (-5.59%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.95 ms   (+1.27%) |       6   →       6              |       17.45 ms →       17.67 ms   (+1.27%) | 
  │ └ sirius::Potential::update                                         |       34.28 ms →       31.11 ms   (-9.23%) |       1   →       1              |       34.28 ms →       31.11 ms   (-9.23%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.87 ms →       30.69 ms   (-9.40%) |       1   →       1              |       33.87 ms →       30.69 ms   (-9.40%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.60 ms →       24.63 ms   (-7.40%) |       1   →       1              |       26.60 ms →       24.63 ms   (-7.40%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.72 ms →        5.54 ms  (-17.59%) |       1   →       1              |        6.72 ms →        5.54 ms  (-17.59%) | 
  ├ sirius::Density                                                     |       40.04 ms →       37.31 ms   (-6.81%) |       1   →       1              |       40.04 ms →       37.31 ms   (-6.81%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.81 ms   (-0.12%) |       2   →       2              |        5.63 ms →        5.63 ms   (-0.12%) | 
  │ └ sirius::Density::update                                           |       34.26 ms →       31.54 ms   (-7.94%) |       1   →       1              |       34.26 ms →       31.54 ms   (-7.94%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.05 ms →       31.32 ms   (-8.00%) |       1   →       1              |       34.05 ms →       31.32 ms   (-8.00%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.41 μs →       78.02 μs   (-0.51%) |       1   →       1              |       78.41 μs →       78.02 μs   (-0.51%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.34 ms →       24.28 ms   (-7.84%) |       1   →       1              |       26.34 ms →       24.28 ms   (-7.84%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.34 ms →        6.67 ms   (-9.06%) |       1   →       1              |        7.34 ms →        6.67 ms   (-9.06%) | 
  ├ sirius::Density::initial_density                                    |       58.07 ms →       55.70 ms   (-4.08%) |       1   →       1              |       58.07 ms →       55.70 ms   (-4.08%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.68 ms →       25.16 ms   (-5.71%) |       1   →       1              |       26.68 ms →       25.16 ms   (-5.71%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.12 ms →        5.65 ms   (-7.75%) |       2   →       2              |       12.24 ms →       11.29 ms   (-7.75%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.72 ms →        5.78 ms   (+1.19%) |       1   →       1              |        5.72 ms →        5.78 ms   (+1.19%) | 
  ├ sirius::Potential::generate                                         |      366.46 ms →      362.04 ms   (-1.21%) |       1   →       1              |      366.46 ms →      362.04 ms   (-1.21%) | 
+ │ ├ sirius::Potential::poisson                                        |       39.26 ms →       34.82 ms  (-11.29%) |       1   →       1              |       39.26 ms →       34.82 ms  (-11.29%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.73 ms →        5.68 ms  (-26.51%) |       1   →       1              |        7.73 ms →        5.68 ms  (-26.51%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        6.13 ms →        6.09 ms   (-0.71%) |       1   →       1              |        6.13 ms →        6.09 ms   (-0.71%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.85 ms →        4.66 ms   (-3.92%) |       1   →       1              |        4.85 ms →        4.66 ms   (-3.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.65 ms   (-3.89%) |       1   →       1              |        4.83 ms →        4.65 ms   (-3.89%) | 
  │ ├ sirius::Periodic_function::add                                    |      762.04 μs →      760.39 μs   (-0.22%) |       2   →       2              |        1.52 ms →        1.52 ms   (-0.22%) | 
  │ ├ sirius::Potential::xc                                             |       51.80 ms →       51.62 ms   (-0.33%) |       1   →       1              |       51.80 ms →       51.62 ms   (-0.33%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.60 ms →       50.42 ms   (-0.35%) |       1   →       1              |       50.60 ms →       50.42 ms   (-0.35%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.55 ms   (+0.09%) |       2   →       2              |        5.09 ms →        5.10 ms   (+0.09%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.60 ms →        4.60 ms   (-0.08%) |       1   →       1              |        4.60 ms →        4.60 ms   (-0.08%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.68 ms →        3.72 ms   (+1.07%) |       1   →       1              |        3.68 ms →        3.72 ms   (+1.07%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.86 ms →      268.95 ms   (+0.03%) |       1   →       1              |      268.86 ms →      268.95 ms   (+0.03%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      145.00 ns →      138.00 ns   (-4.83%) |       1   →       1              |      145.00 ns →      138.00 ns   (-4.83%) | 
  ├ sirius::Hamiltonian0                                                |        7.35 ms →        6.62 ms   (-9.92%) |       1   →       1              |        7.35 ms →        6.62 ms   (-9.92%) | 
  │ ├ sirius::Local_operator                                            |        6.79 ms →        6.16 ms   (-9.36%) |       1   →       1              |        6.79 ms →        6.16 ms   (-9.36%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.74 ms   (-0.55%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.55%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.21 ms →        2.68 ms  (-16.36%) |       1   →       1              |        3.21 ms →        2.68 ms  (-16.36%) | 
+ │ ├ sirius::Non_local_operator                                        |      116.22 μs →       71.75 μs  (-38.26%) |       2   →       2              |      232.43 μs →      143.50 μs  (-38.26%) | 
+ │ ├ sirius::D_operator::initialize                                    |      133.26 μs →      109.31 μs  (-17.97%) |       1   →       1              |      133.26 μs →      109.31 μs  (-17.97%) | 
- │ └ sirius::Q_operator::initialize                                    |       99.20 μs →      129.30 μs  (+30.34%) |       1   →       1              |       99.20 μs →      129.30 μs  (+30.34%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.30 s    (+0.23%) |       1   →       1              |        1.30 s  →        1.30 s    (+0.23%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       59.35 ms →       35.23 ms  (-40.64%) |       1   →       1              |       59.35 ms →       35.23 ms  (-40.64%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      433.56 μs →      289.49 μs  (-33.23%) |       1   →       1              |      433.56 μs →      289.49 μs  (-33.23%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       58.91 ms →       34.93 ms  (-40.70%) |       1   →       1              |       58.91 ms →       34.93 ms  (-40.70%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.27 s    (+2.19%) |       1   →       1              |        1.24 s  →        1.27 s    (+2.19%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       76.15 ms →       84.17 ms  (+10.53%) |       4   →       4              |      304.62 ms →      336.70 ms  (+10.53%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       55.37 ms →       53.66 ms   (-3.09%) |       1   →       1              |       55.37 ms →       53.66 ms   (-3.09%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.89 ms →        6.59 ms  (-25.84%) |       1   →       1              |        8.89 ms →        6.59 ms  (-25.84%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      337.39 ms →      314.23 ms   (-6.86%) |       1   →       1              |      337.39 ms →      314.23 ms   (-6.86%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.64 ms →      246.05 ms   (-0.64%) |       1   →       1              |      247.64 ms →      246.05 ms   (-0.64%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.06 μs →        3.69 μs   (-9.07%) |       1   →       1              |        4.06 μs →        3.69 μs   (-9.07%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.17 μs →        2.76 μs  (-12.67%) |       1   →       1              |        3.17 μs →        2.76 μs  (-12.67%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      476.00 ns →      423.00 ns  (-11.13%) |       1   →       1              |      476.00 ns →      423.00 ns  (-11.13%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        2.21 μs →      654.00 ns  (-70.37%) |       1   →       1              |        2.21 μs →      654.00 ns  (-70.37%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.09 ms →        3.15 ms   (+1.97%) |       1   →       1              |        3.09 ms →        3.15 ms   (+1.97%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.38 ms →       21.30 ms   (-0.38%) |       1   →       1              |       21.38 ms →       21.30 ms   (-0.38%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       32.62 ms →       21.85 ms  (-33.03%) |       2   →       2              |       65.24 ms →       43.69 ms  (-33.03%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.60 ms →       18.22 ms  (+16.80%) |       2   →       2              |       31.19 ms →       36.43 ms  (+16.80%) | 
- │ │ │ └ sddk::wf_inner                                                |       15.39 ms →       18.01 ms  (+17.02%) |       2   →       2              |       30.78 ms →       36.01 ms  (+17.02%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       21.00 ns            |       2   →       2              |       42.00 ns →       42.00 ns            | 
- │ │ │   ├ sddk::wf_inner|pw                                           |       15.25 ms →       17.87 ms  (+17.18%) |       2   →       2              |       30.51 ms →       35.75 ms  (+17.18%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.00 ns →       76.50 ns (+282.50%) |       2   →       2              |       40.00 ns →      153.00 ns (+282.50%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      237.24 ms →      253.91 ms   (+7.03%) |       1   →       1              |      237.24 ms →      253.91 ms   (+7.03%) | 
  │ │ └ sddk::wf_trans                                                  |        2.67 ms →        2.62 ms   (-1.64%) |       1   →       1              |        2.67 ms →        2.62 ms   (-1.64%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.66 ms →        2.62 ms   (-1.64%) |       1   →       1              |        2.66 ms →        2.62 ms   (-1.64%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      390.00 ns →      536.00 ns  (+37.44%) |       1   →       1              |      390.00 ns →      536.00 ns  (+37.44%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       62.90 s  →     1029.45 s  (+1536.76%) |       1   →       1              |       62.90 s  →     1029.45 s  (+1536.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.46 ms   (-0.17%) |      19   →      19              |       46.85 ms →       46.77 ms   (-0.17%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.98 s  →       10.29 s  (+245.03%) |      21   →     100   (+376.19%) |       62.64 s  →     1029.21 s  (+1542.98%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.61 ms →        4.89 ms  (-12.90%) |      21   →     100   (+376.19%) |      117.78 ms →      488.54 ms (+314.78%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.77 ms →        4.21 ms  (-11.63%) |      21   →     100   (+376.19%) |      100.10 ms →      421.26 ms (+320.83%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      537.23 μs →      553.08 μs   (+2.95%) |      21   →     100   (+376.19%) |       11.28 ms →       55.31 ms (+390.24%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.18 ms →        2.51 ms  (-21.05%) |      21   →     100   (+376.19%) |       66.85 ms →      251.35 ms (+275.96%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      282.48 μs →      201.48 μs  (-28.67%) |      42   →     200   (+376.19%) |       11.86 ms →       40.30 ms (+239.64%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      112.16 μs →      113.82 μs   (+1.48%) |      21   →     100   (+376.19%) |        2.36 ms →       11.38 ms (+383.25%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       87.64 μs →       89.01 μs   (+1.56%) |      21   →     100   (+376.19%) |        1.84 ms →        8.90 ms (+383.63%) | 
- │ │ ├ sirius::Band::solve                                             |        1.76 s  →        9.13 s  (+419.44%) |      21   →     100   (+376.19%) |       36.91 s  →      912.98 s  (+2373.53%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      231.55 μs →      198.84 μs  (-14.13%) |      21   →     100   (+376.19%) |        4.86 ms →       19.88 ms (+308.92%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      223.02 μs →      190.26 μs  (-14.69%) |      21   →     100   (+376.19%) |        4.68 ms →       19.03 ms (+306.24%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.57 μs →        6.35 μs   (-3.35%) |      21   →     100   (+376.19%) |      138.01 μs →      635.16 μs (+360.24%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        9.11 s  (+455.58%) |      21   →     100   (+376.19%) |       34.43 s  →      910.76 s  (+2545.62%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       73.58 ms →       35.74 ms  (-51.42%) |      21   →     100   (+376.19%) |        1.55 s  →        3.57 s  (+131.34%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.16 ms →        1.51 ms  (-78.92%) |     126   →     600   (+376.19%) |      902.18 ms →      905.49 ms   (+0.37%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.28 ms →       17.90 ms   (+9.91%) |      21   →     100   (+376.19%) |      341.96 ms →        1.79 s  (+423.40%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      477.79 μs →      464.64 μs   (-2.75%) |      21   →     100   (+376.19%) |       10.03 ms →       46.46 ms (+363.08%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.45 ms →        8.05 ms   (+8.13%) |      42   →     200   (+376.19%) |      312.72 ms →        1.61 s  (+414.93%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        9.04 s  (+486.94%) |      21   →     100   (+376.19%) |       32.35 s  →      904.16 s  (+2694.96%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       59.25 ms →      272.79 ms (+360.43%) |     361   →    1.98 K (+449.31%) |       21.39 s  →      540.95 s  (+2429.20%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       36.68 ms →      201.09 ms (+448.24%) |     361   →    1.98 K (+449.31%) |       13.24 s  →      398.76 s  (+2911.51%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.05 μs →        2.35 μs  (+14.42%) |     361   →    1.98 K (+449.31%) |      740.71 μs →        4.66 ms (+528.53%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.69 μs →        1.97 μs  (+16.77%) |     361   →    1.98 K (+449.31%) |      609.27 μs →        3.91 ms (+541.44%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      483.84 ns →      388.93 ns  (-19.62%) |     361   →    1.98 K (+449.31%) |      174.67 μs →      771.25 μs (+341.55%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      558.25 ns →      614.41 ns  (+10.06%) |     361   →    1.98 K (+449.31%) |      201.53 μs →        1.22 ms (+504.57%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.12 ms →        4.59 ms  (+46.92%) |     361   →    1.98 K (+449.31%) |        1.13 s  →        9.10 s  (+707.02%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.40 ms →       11.72 ms (+244.66%) |     361   →    1.98 K (+449.31%) |        1.23 s  →       23.23 s  (+1793.27%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.01 ms →       27.69 ms (+245.53%) |     722   →    3.97 K (+449.31%) |        5.79 s  →      109.81 s  (+1798.00%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.27 ms →       25.32 ms (+304.08%) |     361   →    1.98 K (+449.31%) |        2.26 s  →       50.22 s  (+2119.63%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.12 ms →        3.44 ms (+208.44%) |     701   →    3.87 K (+451.50%) |      782.52 ms →       13.31 s  (+1601.06%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       41.82 ns →       43.83 ns   (+4.81%) |     701   →    3.87 K (+451.50%) |       29.31 μs →      169.44 μs (+478.03%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      953.43 μs →        3.27 ms (+242.54%) |     701   →    3.87 K (+451.50%) |      668.36 ms →       12.63 s  (+1789.10%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       50.91 ns →       56.09 ns  (+10.18%) |     701   →    3.87 K (+451.50%) |       35.69 μs →      216.83 μs (+507.63%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      138.34 μs →      663.18 μs (+379.40%) |     361   →    1.98 K (+449.31%) |       49.94 ms →        1.32 s  (+2533.37%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.85 ms →        9.32 ms (+402.84%) |     361   →    1.98 K (+449.31%) |      669.05 ms →       18.48 s  (+2662.15%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.23 ms →        9.08 ms (+306.65%) |     340   →    1.88 K (+453.82%) |      759.13 ms →       17.10 s  (+2152.13%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      743.33 μs →        3.03 ms (+307.03%) |    1.02 K →    5.65 K (+453.82%) |      758.20 ms →       17.09 s  (+2154.20%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.25 ms →        4.73 ms (+279.14%) |     361   →    1.98 K (+449.31%) |      450.51 ms →        9.38 s  (+1982.65%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.20 ms →        4.54 ms (+278.96%) |     361   →    1.98 K (+449.31%) |      432.95 ms →        9.01 s  (+1981.65%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.70 ns →       51.48 ns  (+23.44%) |     361   →    1.98 K (+449.31%) |       15.05 μs →      102.09 μs (+578.09%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.03 ms →        4.37 ms (+323.14%) |     361   →    1.98 K (+449.31%) |      373.05 ms →        8.67 s  (+2224.33%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       49.69 ns →       61.00 ns  (+22.76%) |     361   →    1.98 K (+449.31%) |       17.94 μs →      120.96 μs (+574.35%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.86 ms →      128.66 ms (+582.24%) |     361   →    1.98 K (+449.31%) |        6.81 s  →      255.13 s  (+3647.58%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.84 ms →       14.13 ms (+398.24%) |     346   →    1.88 K (+444.51%) |      981.47 ms →       26.63 s  (+2612.95%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.29 ms →        8.05 ms (+523.83%) |     342   →    1.88 K (+450.58%) |      441.34 ms →       15.16 s  (+3334.69%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      643.66 μs →        4.02 ms (+525.10%) |     684   →    3.77 K (+450.58%) |      440.26 ms →       15.15 s  (+3341.72%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.46 ms →        5.77 ms (+294.62%) |     342   →    1.88 K (+450.58%) |      500.06 ms →       10.86 s  (+2072.70%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.02 ms →       11.88 ms (+136.47%) |      90   →    1.84 K (+1940.00%) |      451.97 ms →       21.80 s  (+4724.07%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.79 ms →        6.04 ms (+116.75%) |     159   →    3.57 K (+2146.54%) |      443.26 ms →       21.58 s  (+4769.32%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.94 ms →        4.06 ms (+109.25%) |     228   →    5.31 K (+2228.07%) |      442.92 ms →       21.58 s  (+4771.49%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      537.00 ns →      500.80 ns   (-6.74%) |      21   →     100   (+376.19%) |       11.28 μs →       50.08 μs (+344.09%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.07 μs →       19.83 μs   (-1.20%) |      21   →     100   (+376.19%) |      421.42 μs →        1.98 ms (+370.47%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.04 ms  (-31.42%) |      21   →     100   (+376.19%) |       31.88 ms →      104.09 ms (+226.55%) | 
- │ │ ├ sirius::Density::generate                                       |      566.11 ms →      564.32 ms   (-0.32%) |      21   →     100   (+376.19%) |       11.89 s  →       56.43 s  (+374.69%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      394.87 ms →      404.47 ms   (+2.43%) |      21   →     100   (+376.19%) |        8.29 s  →       40.45 s  (+387.77%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.59 μs →        7.78 μs   (+2.40%) |      21   →     100   (+376.19%) |      159.48 μs →      777.62 μs (+387.61%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.98 μs →        7.11 μs   (+1.80%) |      21   →     100   (+376.19%) |      146.64 μs →      710.86 μs (+384.75%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       40.72 ms →       33.64 ms  (-17.40%) |      21   →     100   (+376.19%) |      855.11 ms →        3.36 s  (+293.35%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.94 μs →       10.75 μs   (-1.76%) |      21   →     100   (+376.19%) |      229.84 μs →        1.08 ms (+367.80%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.08 ms →        5.28 ms  (-77.13%) |      21   →     100   (+376.19%) |      484.65 ms →      527.88 ms   (+8.92%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       16.56 ms →       27.32 ms  (+64.91%) |      21   →     100   (+376.19%) |      347.83 ms →        2.73 s  (+685.30%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      882.90 ns →      608.11 ns  (-31.12%) |      21   →     100   (+376.19%) |       18.54 μs →       60.81 μs (+227.98%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       98.80 ms →      110.54 ms  (+11.87%) |      21   →     100   (+376.19%) |        2.07 s  →       11.05 s  (+432.73%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.06 ms →        2.16 ms   (+4.59%) |      21   →     100   (+376.19%) |       43.34 ms →      215.85 ms (+398.05%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      216.04 ms →      223.07 ms   (+3.25%) |      21   →     100   (+376.19%) |        4.54 s  →       22.31 s  (+391.69%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      215.82 ms →      222.85 ms   (+3.26%) |      21   →     100   (+376.19%) |        4.53 s  →       22.28 s  (+391.70%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      141.92 ms →      131.67 ms   (-7.22%) |      21   →     100   (+376.19%) |        2.98 s  →       13.17 s  (+341.79%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      141.92 ms →      131.67 ms   (-7.22%) |      21   →     100   (+376.19%) |        2.98 s  →       13.17 s  (+341.79%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       60.19 ms →       49.11 ms  (-18.41%) |      21   →     100   (+376.19%) |        1.26 s  →        4.91 s  (+288.51%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.51 ms →       69.28 ms   (+1.13%) |      21   →     100   (+376.19%) |        1.44 s  →        6.93 s  (+381.58%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.57 ms →       12.64 ms   (+0.58%) |      21   →     100   (+376.19%) |      263.98 ms →        1.26 s  (+378.94%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.51 ms →       23.62 ms   (+0.45%) |      21   →     100   (+376.19%) |      493.70 ms →        2.36 s  (+378.33%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.81 ms →        4.56 ms  (-21.54%) |      21   →     100   (+376.19%) |      121.99 ms →      455.77 ms (+273.61%) | 
- │ │ ├ sirius::Density::mix                                            |      137.70 ms →       84.80 ms  (-38.41%) |      21   →     100   (+376.19%) |        2.89 s  →        8.48 s  (+193.26%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      300.33 μs →      811.76 μs (+170.29%) |      21   →     100   (+376.19%) |        6.31 ms →       81.18 ms (+1187.08%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.95 ms →        4.74 ms   (-4.31%) |     259   →     818   (+215.83%) |        1.28 s  →        3.87 s  (+202.23%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.64 ms   (-3.76%) |     259   →     818   (+215.83%) |        1.25 s  →        3.79 s  (+203.96%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.64 ms   (-3.75%) |     259   →     818   (+215.83%) |        1.25 s  →        3.79 s  (+203.97%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        4.94 ms →        5.59 ms  (+13.08%) |      21   →     100   (+376.19%) |      103.77 ms →      558.77 ms (+438.47%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.24 ms →        4.81 ms  (+13.32%) |      21   →     100   (+376.19%) |       89.07 ms →      480.63 ms (+439.63%) | 
- │ │ ├ sirius::Potential::generate                                     |      359.15 ms →      355.20 ms   (-1.10%) |      21   →     100   (+376.19%) |        7.54 s  →       35.52 s  (+370.96%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       39.00 ms →       35.38 ms   (-9.28%) |      21   →     100   (+376.19%) |      818.98 ms →        3.54 s  (+332.00%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.53 ms →        6.33 ms  (-15.99%) |      21   →     100   (+376.19%) |      158.22 ms →      632.91 ms (+300.03%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        6.09 ms →        5.90 ms   (-3.04%) |      21   →     100   (+376.19%) |      127.88 ms →      590.43 ms (+361.71%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.84 ms →        5.01 ms   (+3.61%) |      21   →     100   (+376.19%) |      101.63 ms →      501.40 ms (+393.37%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.84 ms →        5.01 ms   (+3.61%) |      21   →     100   (+376.19%) |      101.60 ms →      501.30 ms (+393.40%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      796.37 μs →      776.58 μs   (-2.48%) |      42   →     200   (+376.19%) |       33.45 ms →      155.32 ms (+364.36%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       45.01 ms →       44.74 ms   (-0.60%) |      21   →     100   (+376.19%) |      945.17 ms →        4.47 s  (+373.32%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.84 ms →       43.56 ms   (-0.63%) |      21   →     100   (+376.19%) |      920.55 ms →        4.36 s  (+373.18%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      674.72 μs →      651.07 μs   (-3.50%) |      42   →     200   (+376.19%) |       28.34 ms →      130.21 ms (+359.50%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.57 ms →        4.70 ms   (+2.87%) |      21   →     100   (+376.19%) |       95.99 ms →      470.22 ms (+389.84%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.64 ms →        3.63 ms   (-0.15%) |      21   →     100   (+376.19%) |       76.40 ms →      363.25 ms (+375.46%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.48 ms →      268.49 ms   (+0.00%) |      21   →     100   (+376.19%) |        5.64 s  →       26.85 s  (+376.21%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      187.81 ns →      232.73 ns  (+23.92%) |      21   →     100   (+376.19%) |        3.94 μs →       23.27 μs (+490.09%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       97.19 ms →       95.41 ms   (-1.84%) |      21   →     100   (+376.19%) |        2.04 s  →        9.54 s  (+367.42%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       97.19 ms →       95.40 ms   (-1.84%) |      21   →     100   (+376.19%) |        2.04 s  →        9.54 s  (+367.42%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.96 ms →       13.26 ms  (-16.91%) |      21   →     100   (+376.19%) |      335.22 ms →        1.33 s  (+295.67%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.08 ms →       68.84 ms   (+1.12%) |      21   →     100   (+376.19%) |        1.43 s  →        6.88 s  (+381.52%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.53 ms →       12.67 ms   (+1.16%) |      21   →     100   (+376.19%) |      263.09 ms →        1.27 s  (+381.71%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.78 ms →        4.09 ms  (-29.19%) |      21   →     100   (+376.19%) |      121.41 ms →      409.38 ms (+237.19%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.75 ms →        4.85 ms   (+2.19%) |     147   →     700   (+376.19%) |      698.21 ms →        3.40 s  (+386.63%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.77 ms   (+4.45%) |     147   →     700   (+376.19%) |      671.18 ms →        3.34 s  (+397.38%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.77 ms   (+4.45%) |     147   →     700   (+376.19%) |      671.11 ms →        3.34 s  (+397.36%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.75 ms →        4.57 ms   (-3.73%) |      63   →     300   (+376.19%) |      299.22 ms →        1.37 s  (+358.45%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.74 ms →        4.56 ms   (-3.82%) |      63   →     300   (+376.19%) |      298.78 ms →        1.37 s  (+358.01%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.55 ms   (+0.51%) |      21   →     100   (+376.19%) |       95.13 ms →      455.31 ms (+378.64%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       76.02 μs →      105.01 μs  (+38.14%) |      21   →     100   (+376.19%) |        1.60 ms →       10.50 ms (+557.81%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.12 μs →      100.09 μs  (+40.74%) |      21   →     100   (+376.19%) |        1.49 ms →       10.01 ms (+570.17%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.11 ms →        5.18 ms   (+1.50%) |       2   →       2              |       10.22 ms →       10.37 ms   (+1.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.66 ms →        5.01 ms   (+7.54%) |       6   →       6              |       27.93 ms →       30.04 ms   (+7.54%) | 
- │ │ └ sirius::Periodic_function|inner_local                           |        4.54 ms →        5.00 ms  (+10.09%) |       6   →       6              |       27.26 ms →       30.02 ms  (+10.09%) | 
- │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        5.00 ms  (+10.09%) |       6   →       6              |       27.26 ms →       30.01 ms  (+10.09%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.78 ms →        4.82 ms   (+0.89%) |       3   →       3              |       14.34 ms →       14.47 ms   (+0.89%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms →        4.82 ms   (+1.60%) |       3   →       3              |       14.23 ms →       14.46 ms   (+1.60%) | 
  ├ sirius::Periodic_function|inner                                     |        4.82 ms →        4.72 ms   (-2.02%) |       2   →       2              |        9.64 ms →        9.45 ms   (-2.02%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.54 ms →        4.72 ms   (+3.89%) |       2   →       2              |        9.09 ms →        9.44 ms   (+3.89%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.54 ms →        4.72 ms   (+3.89%) |       2   →       2              |        9.09 ms →        9.44 ms   (+3.89%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.73 ms →        4.54 ms   (-4.20%) |       1   →       1              |        4.73 ms →        4.54 ms   (-4.20%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.73 ms →        4.53 ms   (-4.28%) |       1   →       1              |        4.73 ms →        4.53 ms   (-4.28%) | 
  └ sirius::finalize                                                    |      150.52 ms →      152.70 ms   (+1.45%) |       1   →       1              |      150.52 ms →      152.70 ms   (+1.45%) | 
  ====================================================================================================================================================================================================
```
