# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 8465163e5150bf9c73ec5dac4bf03576202704b3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      353.60 s  →      351.36 s    (-0.64%) |       1   →       1              |      353.60 s  →      351.36 s    (-0.64%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.74 s    (+2.08%) |       1   →       1              |        2.69 s  →        2.74 s    (+2.08%) | 
  ├ sirius::Simulation_context::initialize                              |        2.98 s  →        2.87 s    (-3.66%) |       1   →       1              |        2.98 s  →        2.87 s    (-3.66%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       26.38 ms →        6.99 ms  (-73.51%) |       1   →       1              |       26.38 ms →        6.99 ms  (-73.51%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      120.15 ms →      136.42 ms  (+13.54%) |       1   →       1              |      120.15 ms →      136.42 ms  (+13.54%) | 
- │ │ ├ sirius::Atom_type::init                                         |       48.04 ms →       55.60 ms  (+15.74%) |       2   →       2              |       96.07 ms →      111.20 ms  (+15.74%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.00 ms →       25.15 ms   (+4.79%) |       1   →       1              |       24.00 ms →       25.15 ms   (+4.79%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.48 ms →        6.49 ms   (+0.08%) |       1   →       1              |        6.48 ms →        6.49 ms   (+0.08%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.48 ms →       18.61 ms   (+6.52%) |       1   →       1              |       17.48 ms →       18.61 ms   (+6.52%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.46 ms →       18.59 ms   (+6.52%) |       1   →       1              |       17.46 ms →       18.59 ms   (+6.52%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.14 ms   (+0.38%) |       1   →       1              |        4.13 ms →        4.14 ms   (+0.38%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-0.68%) |       1   →       1              |        2.34 ms →        2.32 ms   (-0.68%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.81 μs →      106.70 μs   (-0.10%) |       1   →       1              |      106.81 μs →      106.70 μs   (-0.10%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.68 s    (-1.22%) |       1   →       1              |        2.72 s  →        2.68 s    (-1.22%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.83 ms   (-0.14%) |       1   →       1              |       10.85 ms →       10.83 ms   (-0.14%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.48 ms →        4.46 ms   (-0.38%) |       1   →       1              |        4.48 ms →        4.46 ms   (-0.38%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.34 ms   (+0.00%) |       1   →       1              |        6.34 ms →        6.34 ms   (+0.00%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.32 ms   (+0.01%) |       1   →       1              |        6.32 ms →        6.32 ms   (+0.01%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        3.83 ms   (+0.09%) |       1   →       1              |        3.82 ms →        3.83 ms   (+0.09%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.12%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.12%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      101.31 μs →      101.19 μs   (-0.12%) |       1   →       1              |      101.31 μs →      101.19 μs   (-0.12%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.60 ms →       64.99 ms   (+3.81%) |       2   →       2              |      125.21 ms →      129.97 ms   (+3.81%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.28 ms   (+2.88%) |       2   →       2              |       10.26 ms →       10.56 ms   (+2.88%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.59 ms   (+2.72%) |       1   →       1              |        4.47 ms →        4.59 ms   (+2.72%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.77 ms   (-0.21%) |       2   →       2              |       43.63 ms →       43.54 ms   (-0.21%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.79 ms →       14.84 ms   (+0.36%) |       2   →       2              |       29.57 ms →       29.68 ms   (+0.36%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.53 ms →       19.60 ms   (+0.37%) |       4   →       4              |       78.12 ms →       78.42 ms   (+0.37%) | 
  │   ├ sddk::Gvec::init                                                |      184.11 ms →      172.67 ms   (-6.21%) |       2   →       2              |      368.21 ms →      345.34 ms   (-6.21%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      140.86 ms →      130.13 ms   (-7.62%) |       2   →       2              |      281.73 ms →      260.27 ms   (-7.62%) | 
+ │   ├ sddk::Gvec_shells                                               |      190.31 ms →      166.08 ms  (-12.73%) |       1   →       1              |      190.31 ms →      166.08 ms  (-12.73%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.31 ms   (+0.34%) |       1   →       1              |        1.31 ms →        1.31 ms   (+0.34%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.41 ms →      291.56 ms   (+0.05%) |       2   →       2              |      582.82 ms →      583.12 ms   (+0.05%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       75.15 ms →       73.80 ms   (-1.79%) |       1   →       1              |       75.15 ms →       73.80 ms   (-1.79%) | 
- │ ├ sirius::K_point::K_point                                          |        2.47 μs →        2.91 μs  (+17.97%) |       4   →       4              |        9.87 μs →       11.64 μs  (+17.97%) | 
  │ └ sirius::K_point_set::initialize                                   |       75.04 ms →       73.70 ms   (-1.79%) |       1   →       1              |       75.04 ms →       73.70 ms   (-1.79%) | 
  │   └ sirius::K_point::initialize                                     |       18.74 ms →       18.40 ms   (-1.79%) |       4   →       4              |       74.95 ms →       73.61 ms   (-1.79%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.14 ms →       13.86 ms   (-1.95%) |       4   →       4              |       56.56 ms →       55.45 ms   (-1.95%) | 
  │     │ └ sddk::Gvec::init                                            |        3.90 ms →        3.80 ms   (-2.66%) |       4   →       4              |       15.62 ms →       15.20 ms   (-2.66%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.73 μs →        8.61 μs   (-1.29%) |       4   →       4              |       34.91 μs →       34.46 μs   (-1.29%) | 
  │     └ sirius::K_point::update                                       |        3.30 ms →        3.25 ms   (-1.74%) |       4   →       4              |       13.21 ms →       12.98 ms   (-1.74%) | 
  │       └ sirius::Beta_projectors                                     |        1.78 ms →        1.75 ms   (-1.49%) |       4   →       4              |        7.12 ms →        7.01 ms   (-1.49%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      922.51 μs →      932.38 μs   (+1.07%) |       4   →       4              |        3.69 ms →        3.73 ms   (+1.07%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.36 ms →        5.36 ms   (-0.05%) |       2   →       2              |       10.72 ms →       10.72 ms   (-0.05%) | 
  ├ sirius::Potential                                                   |      159.15 ms →      154.54 ms   (-2.90%) |       1   →       1              |      159.15 ms →      154.54 ms   (-2.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.85 ms   (+0.73%) |       6   →       6              |       34.85 ms →       35.11 ms   (+0.73%) | 
  │ └ sirius::Potential::update                                         |      123.56 ms →      118.73 ms   (-3.91%) |       1   →       1              |      123.56 ms →      118.73 ms   (-3.91%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.80 ms →      117.98 ms   (-3.92%) |       1   →       1              |      122.80 ms →      117.98 ms   (-3.92%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.17 ms →      110.71 ms   (+2.35%) |       1   →       1              |      108.17 ms →      110.71 ms   (+2.35%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       13.71 ms →        6.39 ms  (-53.39%) |       1   →       1              |       13.71 ms →        6.39 ms  (-53.39%) | 
  ├ sirius::Density                                                     |      136.04 ms →      129.58 ms   (-4.75%) |       1   →       1              |      136.04 ms →      129.58 ms   (-4.75%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.10 ms →        5.12 ms   (+0.26%) |       2   →       2              |       10.21 ms →       10.23 ms   (+0.26%) | 
  │ └ sirius::Density::update                                           |      125.57 ms →      119.04 ms   (-5.20%) |       1   →       1              |      125.57 ms →      119.04 ms   (-5.20%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.13 ms →      118.63 ms   (-5.20%) |       1   →       1              |      125.13 ms →      118.63 ms   (-5.20%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.46 μs →      107.37 μs   (+1.82%) |       1   →       1              |      105.46 μs →      107.37 μs   (+1.82%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.23 ms →      111.78 ms   (+1.41%) |       1   →       1              |      110.23 ms →      111.78 ms   (+1.41%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       14.35 ms →        6.30 ms  (-56.07%) |       1   →       1              |       14.35 ms →        6.30 ms  (-56.07%) | 
  ├ sirius::Density::initial_density                                    |      178.32 ms →      162.89 ms   (-8.65%) |       1   →       1              |      178.32 ms →      162.89 ms   (-8.65%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      109.34 ms →      109.59 ms   (+0.23%) |       1   →       1              |      109.34 ms →      109.59 ms   (+0.23%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       12.99 ms →        5.33 ms  (-59.00%) |       2   →       2              |       25.98 ms →       10.65 ms  (-59.00%) | 
+ │ └ sirius::Periodic_function::integrate                              |       11.24 ms →        9.82 ms  (-12.63%) |       1   →       1              |       11.24 ms →        9.82 ms  (-12.63%) | 
  ├ sirius::Potential::generate                                         |      593.33 ms →      582.11 ms   (-1.89%) |       1   →       1              |      593.33 ms →      582.11 ms   (-1.89%) | 
  │ ├ sirius::Potential::poisson                                        |      138.65 ms →      126.62 ms   (-8.67%) |       1   →       1              |      138.65 ms →      126.62 ms   (-8.67%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.73 ms →        6.41 ms  (-67.51%) |       1   →       1              |       19.73 ms →        6.41 ms  (-67.51%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.64 ms →       10.26 ms   (-3.61%) |       1   →       1              |       10.64 ms →       10.26 ms   (-3.61%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.80 ms →        9.88 ms   (+0.82%) |       1   →       1              |        9.80 ms →        9.88 ms   (+0.82%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →        9.88 ms   (+0.82%) |       1   →       1              |        9.80 ms →        9.88 ms   (+0.82%) | 
  │ ├ sirius::Periodic_function::add                                    |      553.90 μs →      555.10 μs   (+0.22%) |       2   →       2              |        1.11 ms →        1.11 ms   (+0.22%) | 
  │ ├ sirius::Potential::xc                                             |       53.66 ms →       53.57 ms   (-0.16%) |       1   →       1              |       53.66 ms →       53.57 ms   (-0.16%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.33 ms →       51.26 ms   (-0.13%) |       1   →       1              |       51.33 ms →       51.26 ms   (-0.13%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.64 ms →        5.69 ms   (+0.86%) |       2   →       2              |       11.28 ms →       11.38 ms   (+0.86%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.37 ms →        5.25 ms   (-2.31%) |       1   →       1              |        5.37 ms →        5.25 ms   (-2.31%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.97 ms →        5.93 ms   (-0.60%) |       1   →       1              |        5.97 ms →        5.93 ms   (-0.60%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.58 ms →       93.55 ms   (+1.04%) |       1   →       1              |       92.58 ms →       93.55 ms   (+1.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.99 ms →      299.98 ms   (-0.00%) |       1   →       1              |      299.99 ms →      299.98 ms   (-0.00%) | 
  ├ sirius::Hamiltonian0                                                |        8.37 ms →        8.31 ms   (-0.62%) |       1   →       1              |        8.37 ms →        8.31 ms   (-0.62%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        7.97 ms   (-0.71%) |       1   →       1              |        8.03 ms →        7.97 ms   (-0.71%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms →        4.68 ms   (-1.60%) |       1   →       1              |        4.76 ms →        4.68 ms   (-1.60%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        2.37 ms   (+0.90%) |       1   →       1              |        2.35 ms →        2.37 ms   (+0.90%) | 
  │ ├ sirius::Non_local_operator                                        |       62.93 μs →       63.65 μs   (+1.14%) |       2   →       2              |      125.87 μs →      127.30 μs   (+1.14%) | 
  │ ├ sirius::D_operator::initialize                                    |       90.85 μs →       95.32 μs   (+4.92%) |       1   →       1              |       90.85 μs →       95.32 μs   (+4.92%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.39 μs →       68.49 μs   (-1.31%) |       1   →       1              |       69.39 μs →       68.49 μs   (-1.31%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.01 s  →        3.95 s    (-1.55%) |       1   →       1              |        4.01 s  →        3.95 s    (-1.55%) | 
  │ ├ sirius::Hamiltonian_k                                             |      379.25 μs →      380.41 μs   (+0.31%) |       4   →       4              |        1.52 ms →        1.52 ms   (+0.31%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      374.03 μs →      375.65 μs   (+0.43%) |       4   →       4              |        1.50 ms →        1.50 ms   (+0.43%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        3.49 μs →        2.98 μs  (-14.62%) |       4   →       4              |       13.95 μs →       11.91 μs  (-14.62%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.00 s  →      986.48 ms   (-1.55%) |       4   →       4              |        4.01 s  →        3.95 s    (-1.55%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       31.93 ms →       32.25 ms   (+1.03%) |      16   →      16              |      510.81 ms →      516.05 ms   (+1.03%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.56 ms →       14.75 ms   (+1.35%) |       4   →       4              |       58.23 ms →       59.02 ms   (+1.35%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.27 ms →        5.30 ms   (+0.64%) |       4   →       4              |       21.06 ms →       21.20 ms   (+0.64%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.44 ms →      360.57 ms   (+1.73%) |       4   →       4              |        1.42 s  →        1.44 s    (+1.73%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      258.03 ms →      261.75 ms   (+1.44%) |       4   →       4              |        1.03 s  →        1.05 s    (+1.44%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.81 ms →       64.96 ms   (+1.79%) |       4   →       4              |      255.25 ms →      259.83 ms   (+1.79%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       15.95 ms →       16.23 ms   (+1.80%) |       4   →       4              |       63.78 ms →       64.94 ms   (+1.80%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.94 ms →       16.23 ms   (+1.80%) |       4   →       4              |       63.78 ms →       64.93 ms   (+1.80%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.32 ms →       42.37 ms   (+2.54%) |       4   →       4              |      165.29 ms →      169.50 ms   (+2.54%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.12 ms →       15.98 ms   (-0.87%) |       4   →       4              |       64.48 ms →       63.92 ms   (-0.87%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.12 ms →       15.98 ms   (-0.87%) |       4   →       4              |       64.47 ms →       63.91 ms   (-0.87%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.34 ms →       56.49 ms   (+5.90%) |       4   →       4              |      213.37 ms →      225.95 ms   (+5.90%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.29 ms →       38.43 ms   (+8.89%) |       4   →       4              |      141.15 ms →      153.70 ms   (+8.89%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.96 ms   (+0.68%) |       4   →       4              |        7.78 ms →        7.83 ms   (+0.68%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.23 ms →       42.66 ms   (+6.04%) |       4   →       4              |      160.94 ms →      170.66 ms   (+6.04%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.07 ms →        9.49 ms  (+34.14%) |       4   →       4              |       28.29 ms →       37.95 ms  (+34.14%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.08 ms   (-0.06%) |       8   →       8              |      216.76 ms →      216.62 ms   (-0.06%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.83 ms →       15.24 ms   (+2.81%) |       8   →       8              |      118.61 ms →      121.95 ms   (+2.81%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.78 ms →       15.20 ms   (+2.82%) |       8   →       8              |      118.26 ms →      121.59 ms   (+2.82%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       31.88 ns →       19.87 ns  (-37.65%) |       8   →       8              |      255.00 ns →      159.00 ns  (-37.65%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.61 ms →       14.98 ms   (+2.55%) |       8   →       8              |      116.87 ms →      119.84 ms   (+2.55%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       24.75 ns  (+30.26%) |       8   →       8              |      152.00 ns →      198.00 ns  (+30.26%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      345.86 ms →      321.82 ms   (-6.95%) |       4   →       4              |        1.38 s  →        1.29 s    (-6.95%) | 
  │ │ └ sddk::wf_trans                                                  |       26.67 ms →       26.79 ms   (+0.48%) |       4   →       4              |      106.67 ms →      107.18 ms   (+0.48%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.45 ms →       26.58 ms   (+0.49%) |       4   →       4              |      105.80 ms →      106.32 ms   (+0.49%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      390.50 ns →      463.50 ns  (+18.69%) |       4   →       4              |        1.56 μs →        1.85 μs  (+18.69%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      341.93 s  →      339.82 s    (-0.62%) |       1   →       1              |      341.93 s  →      339.82 s    (-0.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.87 ms   (+2.17%) |      19   →      19              |      109.07 ms →      111.44 ms   (+2.17%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       12.64 s  →       12.56 s    (-0.68%) |      27   →      27              |      341.39 s  →      339.07 s    (-0.68%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.55 ms →        4.51 ms   (-0.80%) |      27   →      27              |      122.78 ms →      121.80 ms   (-0.80%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.19 ms →        4.15 ms   (-0.95%) |      27   →      27              |      113.14 ms →      112.06 ms   (-0.95%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      969.57 μs →      978.47 μs   (+0.92%) |      27   →      27              |       26.18 ms →       26.42 ms   (+0.92%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.33 ms →        2.28 ms   (-2.39%) |      27   →      27              |       63.00 ms →       61.50 ms   (-2.39%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.53 μs →       64.59 μs   (+0.09%) |      54   →      54              |        3.48 ms →        3.49 ms   (+0.09%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.28 μs →       95.34 μs   (+1.12%) |      27   →      27              |        2.55 ms →        2.57 ms   (+1.12%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.70 μs →       67.03 μs   (+2.03%) |      27   →      27              |        1.77 ms →        1.81 ms   (+2.03%) | 
  │ │ ├ sirius::Band::solve                                             |       10.55 s  →       10.52 s    (-0.28%) |      27   →      27              |      284.96 s  →      284.17 s    (-0.28%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      320.03 μs →      318.22 μs   (-0.57%) |     108   →     108              |       34.56 ms →       34.37 ms   (-0.57%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      314.63 μs →      312.74 μs   (-0.60%) |     108   →     108              |       33.98 ms →       33.78 ms   (-0.60%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.94 μs →        3.99 μs   (+1.28%) |     108   →     108              |      425.84 μs →      431.31 μs   (+1.28%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.64 s  →        2.63 s    (-0.28%) |     108   →     108              |      284.93 s  →      284.13 s    (-0.28%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.23 ms →       12.12 ms   (-0.90%) |     108   →     108              |        1.32 s  →        1.31 s    (-0.90%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      621.28 ns →      638.54 ns   (+2.78%) |     648   →     648              |      402.59 μs →      413.77 μs   (+2.78%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.85 ms   (+0.58%) |     108   →     108              |      198.34 ms →      199.49 ms   (+0.58%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      358.63 μs →      359.06 μs   (+0.12%) |     108   →     108              |       38.73 ms →       38.78 ms   (+0.12%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      549.15 μs →      551.25 μs   (+0.38%) |     216   →     216              |      118.62 ms →      119.07 ms   (+0.38%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.62 s  →        2.61 s    (-0.28%) |     108   →     108              |      282.43 s  →      281.64 s    (-0.28%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       71.15 ms →       69.52 ms   (-2.29%) |     924   →     963     (+4.22%) |       65.74 s  →       66.95 s    (+1.84%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       45.71 ms →       44.57 ms   (-2.49%) |     924   →     963     (+4.22%) |       42.23 s  →       42.92 s    (+1.63%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.90 ms →        8.99 ms   (+0.96%) |     924   →     963     (+4.22%) |        8.23 s  →        8.66 s    (+5.22%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      228.98 μs →      216.83 μs   (-5.30%) |     924   →     963     (+4.22%) |      211.57 ms →      208.81 ms   (-1.31%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.94 ms →        1.92 ms   (-1.36%) |     108   →     108              |      209.80 ms →      206.94 ms   (-1.36%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.96 ms →        7.03 ms   (+1.02%) |     924   →     963     (+4.22%) |        6.43 s  →        6.77 s    (+5.28%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       90.76 μs →       83.11 μs   (-8.43%) |     924   →     963     (+4.22%) |       83.87 ms →       80.04 ms   (-4.56%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      755.62 μs →      719.03 μs   (-4.84%) |     108   →     108              |       81.61 ms →       77.66 ms   (-4.84%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.09 ms →        9.96 ms   (-1.36%) |     924   →     963     (+4.22%) |        9.33 s  →        9.59 s    (+2.81%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.37 ms →        6.38 ms   (+0.14%) |     924   →     963     (+4.22%) |        5.89 s  →        6.15 s    (+4.36%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.01%) |     924   →     963     (+4.22%) |        1.41 s  →        1.46 s    (+4.21%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.77 ms →        8.75 ms   (-0.21%) |     924   →     963     (+4.22%) |        8.10 s  →        8.43 s    (+4.01%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.30 ms →        1.54 ms  (+18.03%) |     924   →     963     (+4.22%) |        1.20 s  →        1.48 s   (+23.01%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.56 ms →        7.32 ms   (-3.13%) |    1.85 K →    1.93 K   (+4.22%) |       13.97 s  →       14.11 s    (+0.96%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       30.49 ms →       29.95 ms   (-1.76%) |     924   →     963     (+4.22%) |       28.17 s  →       28.84 s    (+2.39%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.01 ms →        2.06 ms   (+2.51%) |    1.74 K →    1.82 K   (+4.48%) |        3.49 s  →        3.74 s    (+7.10%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       86.61 ns →       63.43 ns  (-26.77%) |    1.74 K →    1.82 K   (+4.48%) |      150.70 μs →      115.31 μs  (-23.48%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.00 ms →        2.04 ms   (+2.14%) |    1.74 K →    1.82 K   (+4.48%) |        3.48 s  →        3.71 s    (+6.72%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       66.49 ns →       72.85 ns   (+9.58%) |    1.74 K →    1.82 K   (+4.48%) |      115.68 μs →      132.45 μs  (+14.49%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      975.81 μs →      980.49 μs   (+0.48%) |     924   →     963     (+4.22%) |      901.65 ms →      944.21 ms   (+4.72%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.50 ms →        1.51 ms   (+0.39%) |     924   →     963     (+4.22%) |        1.39 s  →        1.45 s    (+4.63%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.83 ms →        5.67 ms   (-2.73%) |    3.59 K →    3.74 K   (+4.35%) |       20.90 s  →       21.21 s    (+1.50%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.97 ms →        3.84 ms   (-3.25%) |    5.22 K →    5.45 K   (+4.48%) |       20.74 s  →       20.97 s    (+1.09%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.27 ms →        5.40 ms   (+2.38%) |     924   →     963     (+4.22%) |        4.87 s  →        5.20 s    (+6.71%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.58 ms →        3.57 ms   (-0.07%) |     924   →     963     (+4.22%) |        3.30 s  →        3.44 s    (+4.15%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       65.81 ns →       55.53 ns  (-15.63%) |     924   →     963     (+4.22%) |       60.81 μs →       53.47 μs  (-12.07%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.56 ms →        3.55 ms   (-0.33%) |     924   →     963     (+4.22%) |        3.29 s  →        3.42 s    (+3.87%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.54 ns →       85.24 ns  (+95.78%) |     924   →     963     (+4.22%) |       40.23 μs →       82.09 μs (+104.04%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      172.75 ms →      162.35 ms   (-6.02%) |     924   →     963     (+4.22%) |      159.62 s  →      156.35 s    (-2.05%) | 
  │ │ │ │   ├ sirius::residuals                                         |       11.18 ms →       10.87 ms   (-2.77%) |     898   →     934     (+4.01%) |       10.04 s  →       10.16 s    (+1.12%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.68 ms →       10.29 ms   (-3.71%) |     855   →     894     (+4.56%) |        9.13 s  →        9.20 s    (+0.68%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.31 ms →        5.10 ms   (-4.03%) |    1.71 K →    1.79 K   (+4.56%) |        9.08 s  →        9.11 s    (+0.35%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      640.48 μs →      645.03 μs   (+0.71%) |     855   →     894     (+4.56%) |      547.61 ms →      576.66 ms   (+5.30%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.80 ms →       40.59 ms   (-0.51%) |     342   →     348     (+1.75%) |       13.95 s  →       14.13 s    (+1.24%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       24.10 ms →       23.90 ms   (-0.84%) |     576   →     588     (+2.08%) |       13.88 s  →       14.05 s    (+1.23%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       17.03 ms →       16.85 ms   (-1.08%) |     810   →     828     (+2.22%) |       13.79 s  →       13.95 s    (+1.12%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      464.17 ns →      573.41 ns  (+23.53%) |     108   →     108              |       50.13 μs →       61.93 μs  (+23.53%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       24.03 μs →       24.86 μs   (+3.45%) |      27   →      27              |      648.74 μs →      671.11 μs   (+3.45%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      599.81 μs →      604.36 μs   (+0.76%) |      27   →      27              |       16.19 ms →       16.32 ms   (+0.76%) | 
  │ │ ├ sirius::Density::generate                                       |      894.28 ms →      901.86 ms   (+0.85%) |      27   →      27              |       24.15 s  →       24.35 s    (+0.85%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      526.22 ms →      533.86 ms   (+1.45%) |      27   →      27              |       14.21 s  →       14.41 s    (+1.45%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.60 ms →       25.45 ms   (+3.48%) |     108   →     108              |        2.66 s  →        2.75 s    (+3.48%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.53 μs →        5.76 μs   (+4.30%) |     108   →     108              |      596.73 μs →      622.37 μs   (+4.30%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.69 μs →       12.23 μs   (-3.67%) |       8   →       8              |      101.55 μs →       97.82 μs   (-3.67%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.45 ms →       21.29 ms   (+4.10%) |     108   →     108              |        2.21 s  →        2.30 s    (+4.10%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.72 ms →       30.76 ms   (+3.52%) |     108   →     108              |        3.21 s  →        3.32 s    (+3.52%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.13 μs →       11.25 μs   (+1.10%) |     108   →     108              |        1.20 ms →        1.22 ms   (+1.10%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.28%) |     108   →     108              |      157.65 ms →      158.09 ms   (+0.28%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.78 ms →       28.81 ms   (+3.72%) |     108   →     108              |        3.00 s  →        3.11 s    (+3.72%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.64 ms →        4.67 ms  (+28.32%) |     108   →     108              |      393.23 ms →      504.59 ms  (+28.32%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      707.74 ns →      529.35 ns  (-25.21%) |     108   →     108              |       76.44 μs →       57.17 μs  (-25.21%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.59 ms →       42.65 ms   (+0.15%) |     108   →     108              |        4.60 s  →        4.61 s    (+0.15%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.67%) |      27   →      27              |       44.60 ms →       44.30 ms   (-0.67%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.94 ms →       88.94 ms   (-0.01%) |      27   →      27              |        2.40 s  →        2.40 s    (-0.01%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.70 ms →       88.70 ms   (-0.01%) |      27   →      27              |        2.39 s  →        2.39 s    (-0.01%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.82 ms →      276.13 ms   (+0.11%) |      27   →      27              |        7.45 s  →        7.46 s    (+0.11%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.82 ms →      276.13 ms   (+0.11%) |      27   →      27              |        7.45 s  →        7.46 s    (+0.11%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.18 ms →       24.40 ms   (+0.90%) |      27   →      27              |      652.87 ms →      658.75 ms   (+0.90%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.02 ms →      225.93 ms   (-0.04%) |      27   →      27              |        6.10 s  →        6.10 s    (-0.04%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.86 ms →       24.03 ms   (+0.73%) |      27   →      27              |      644.22 ms →      648.94 ms   (+0.73%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.04 ms →       81.41 ms   (+0.46%) |      27   →      27              |        2.19 s  →        2.20 s    (+0.46%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.62 ms →        6.87 ms   (-9.80%) |      27   →      27              |      205.66 ms →      185.51 ms   (-9.80%) | 
+ │ │ ├ sirius::Density::mix                                            |      207.70 ms →      157.01 ms  (-24.40%) |      27   →      27              |        5.61 s  →        4.24 s   (-24.40%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      971.66 μs →      959.72 μs   (-1.23%) |      27   →      27              |       26.23 ms →       25.91 ms   (-1.23%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.33 ms →       10.22 ms   (-1.03%) |     335   →     349     (+4.18%) |        3.46 s  →        3.57 s    (+3.10%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.07 ms →        9.94 ms   (-1.29%) |     335   →     349     (+4.18%) |        3.37 s  →        3.47 s    (+2.83%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.07 ms →        9.94 ms   (-1.29%) |     335   →     349     (+4.18%) |        3.37 s  →        3.47 s    (+2.83%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.05 ms →        6.49 ms   (-8.02%) |      27   →      27              |      190.42 ms →      175.15 ms   (-8.02%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.23 ms →        5.39 ms  (-13.44%) |      27   →      27              |      168.29 ms →      145.66 ms  (-13.44%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.66 ms →      569.09 ms   (-1.99%) |      27   →      27              |       15.68 s  →       15.37 s    (-1.99%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.99 ms →      126.20 ms   (-8.54%) |      27   →      27              |        3.73 s  →        3.41 s    (-8.54%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       19.33 ms →        6.09 ms  (-68.47%) |      27   →      27              |      521.83 ms →      164.52 ms  (-68.47%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.20 ms →       10.46 ms   (+2.57%) |      27   →      27              |      275.45 ms →      282.53 ms   (+2.57%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.98 ms →       10.19 ms   (+2.06%) |      27   →      27              |      269.49 ms →      275.05 ms   (+2.06%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.98 ms →       10.19 ms   (+2.06%) |      27   →      27              |      269.48 ms →      275.04 ms   (+2.06%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      551.95 μs →      561.75 μs   (+1.78%) |      54   →      54              |       29.81 ms →       30.33 ms   (+1.78%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.94 ms →       49.75 ms   (-0.38%) |      27   →      27              |        1.35 s  →        1.34 s    (-0.38%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.59 ms →       47.39 ms   (-0.42%) |      27   →      27              |        1.28 s  →        1.28 s    (-0.42%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.05 ms   (+0.83%) |      54   →      54              |      163.26 ms →      164.62 ms   (+0.83%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.42 ms →        5.52 ms   (+1.81%) |      27   →      27              |      146.28 ms →      148.93 ms   (+1.81%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.78 ms →        6.87 ms   (+1.44%) |      27   →      27              |      182.94 ms →      185.57 ms   (+1.44%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.90 ms   (+0.01%) |      27   →      27              |        2.45 s  →        2.45 s    (+0.01%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.66 ms →      292.94 ms   (+0.10%) |      27   →      27              |        7.90 s  →        7.91 s    (+0.10%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      279.19 ms →      279.10 ms   (-0.03%) |      27   →      27              |        7.54 s  →        7.54 s    (-0.03%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      279.19 ms →      279.10 ms   (-0.03%) |      27   →      27              |        7.54 s  →        7.54 s    (-0.03%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.41 ms →       27.34 ms   (-0.25%) |      27   →      27              |      740.16 ms →      738.28 ms   (-0.25%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.05 ms →      223.83 ms   (-0.10%) |      27   →      27              |        6.05 s  →        6.04 s    (-0.10%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.94 ms →       24.11 ms   (+0.71%) |      27   →      27              |      646.27 ms →      650.87 ms   (+0.71%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.58 ms →        5.49 ms   (-1.63%) |      27   →      27              |      150.59 ms →      148.13 ms   (-1.63%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.78 ms →       10.65 ms   (-1.20%) |     189   →     189              |        2.04 s  →        2.01 s    (-1.20%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.34 ms →       10.30 ms   (-0.44%) |     189   →     189              |        1.95 s  →        1.95 s    (-0.44%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.34 ms →       10.30 ms   (-0.44%) |     189   →     189              |        1.95 s  →        1.95 s    (-0.44%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.57 ms →       10.14 ms   (-4.05%) |      81   →      81              |      856.14 ms →      821.46 ms   (-4.05%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.27 ms →        9.81 ms   (-4.44%) |      81   →      81              |      831.69 ms →      794.74 ms   (-4.44%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.06 ms →       10.36 ms   (+2.91%) |      27   →      27              |      271.73 ms →      279.63 ms   (+2.91%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      111.42 μs →      142.99 μs  (+28.34%) |      27   →      27              |        3.01 ms →        3.86 ms  (+28.34%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.69 μs →      137.75 μs  (+29.11%) |      27   →      27              |        2.88 ms →        3.72 ms  (+29.11%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.23 ms →        5.06 ms   (-3.10%) |       2   →       2              |       10.45 ms →       10.13 ms   (-3.10%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.31 ms →       10.37 ms   (+0.59%) |       6   →       6              |       61.87 ms →       62.24 ms   (+0.59%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.29 ms →       10.32 ms   (+0.32%) |       6   →       6              |       61.73 ms →       61.93 ms   (+0.32%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.29 ms →       10.32 ms   (+0.32%) |       6   →       6              |       61.73 ms →       61.93 ms   (+0.32%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.21 ms →        9.80 ms   (-4.09%) |       3   →       3              |       30.64 ms →       29.39 ms   (-4.09%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.76 ms →        9.75 ms   (-0.08%) |       3   →       3              |       29.27 ms →       29.25 ms   (-0.08%) | 
  ├ sirius::Periodic_function|inner                                     |       10.12 ms →       10.45 ms   (+3.20%) |       2   →       2              |       20.25 ms →       20.89 ms   (+3.20%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.12 ms →       10.44 ms   (+3.18%) |       2   →       2              |       20.23 ms →       20.88 ms   (+3.18%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.12 ms →       10.44 ms   (+3.18%) |       2   →       2              |       20.23 ms →       20.88 ms   (+3.18%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.80 ms →       10.00 ms   (+2.04%) |       1   →       1              |        9.80 ms →       10.00 ms   (+2.04%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.62 ms →        9.99 ms   (+3.85%) |       1   →       1              |        9.62 ms →        9.99 ms   (+3.85%) | 
  └ sirius::finalize                                                    |      336.24 ms →      359.34 ms   (+6.87%) |       1   →       1              |      336.24 ms →      359.34 ms   (+6.87%) | 
  ====================================================================================================================================================================================================
```
