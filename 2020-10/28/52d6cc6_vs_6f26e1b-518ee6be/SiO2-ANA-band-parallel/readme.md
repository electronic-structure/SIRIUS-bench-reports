# Benchmark 6f26e1b85d392e75fe8ae23eb64d38742c01496b vs 52d6cc62f84d89d2fdc84536db65e2617fd3b399
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      222.55 s  →      226.90 s    (+1.96%) |       1   →       1              |      222.55 s  →      226.90 s    (+1.96%) | 
  ├ sirius::initialize                                                  |        2.66 s  →        2.64 s    (-0.56%) |       1   →       1              |        2.66 s  →        2.64 s    (-0.56%) | 
  ├ sirius::Simulation_context::initialize                              |        2.88 s  →        2.95 s    (+2.42%) |       1   →       1              |        2.88 s  →        2.95 s    (+2.42%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       27.97 ms →       38.46 ms  (+37.50%) |       1   →       1              |       27.97 ms →       38.46 ms  (+37.50%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       79.60 ms →      178.70 ms (+124.51%) |       1   →       1              |       79.60 ms →      178.70 ms (+124.51%) | 
- │ │ ├ sirius::Atom_type::init                                         |       28.04 ms →       78.16 ms (+178.78%) |       2   →       2              |       56.07 ms →      156.32 ms (+178.78%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.42 ms →       22.30 ms   (-4.79%) |       1   →       1              |       23.42 ms →       22.30 ms   (-4.79%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.39 ms →        6.29 ms   (-1.49%) |       1   →       1              |        6.39 ms →        6.29 ms   (-1.49%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.99 ms →       15.96 ms   (-6.10%) |       1   →       1              |       16.99 ms →       15.96 ms   (-6.10%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.97 ms →       15.93 ms   (-6.11%) |       1   →       1              |       16.97 ms →       15.93 ms   (-6.11%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.19 ms   (+1.05%) |       1   →       1              |        4.14 ms →        4.19 ms   (+1.05%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.20%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.20%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      103.78 μs →      109.61 μs   (+5.62%) |       1   →       1              |      103.78 μs →      109.61 μs   (+5.62%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.69 s    (-1.47%) |       1   →       1              |        2.73 s  →        2.69 s    (-1.47%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.83 ms →       10.81 ms   (-0.15%) |       1   →       1              |       10.83 ms →       10.81 ms   (-0.15%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.43 ms   (-0.17%) |       1   →       1              |        4.44 ms →        4.43 ms   (-0.17%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.35 ms   (-0.20%) |       1   →       1              |        6.36 ms →        6.35 ms   (-0.20%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.32 ms   (-0.23%) |       1   →       1              |        6.34 ms →        6.32 ms   (-0.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.82 ms   (-0.41%) |       1   →       1              |        3.83 ms →        3.82 ms   (-0.41%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.14%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.14%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.60 μs →      106.96 μs   (+3.25%) |       1   →       1              |      103.60 μs →      106.96 μs   (+3.25%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.58 ms →       62.60 ms   (+0.03%) |       2   →       2              |      125.17 ms →      125.21 ms   (+0.03%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.27 ms   (+2.62%) |       2   →       2              |       10.27 ms →       10.53 ms   (+2.62%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.50 ms   (+0.69%) |       1   →       1              |        4.47 ms →        4.50 ms   (+0.69%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.13 ms →       21.77 ms   (-1.65%) |       2   →       2              |       44.26 ms →       43.54 ms   (-1.65%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.83 ms →       14.80 ms   (-0.19%) |       2   →       2              |       29.66 ms →       29.60 ms   (-0.19%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.36 ms →       19.83 ms   (+2.45%) |       4   →       4              |       77.43 ms →       79.32 ms   (+2.45%) | 
  │   ├ sddk::Gvec::init                                                |      172.23 ms →      175.39 ms   (+1.83%) |       2   →       2              |      344.45 ms →      350.77 ms   (+1.83%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.84 ms →      130.27 ms   (+1.11%) |       2   →       2              |      257.68 ms →      260.54 ms   (+1.11%) | 
  │   ├ sddk::Gvec_shells                                               |      180.40 ms →      179.23 ms   (-0.65%) |       1   →       1              |      180.40 ms →      179.23 ms   (-0.65%) | 
+ │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.68 ms →        1.32 ms  (-21.40%) |       1   →       1              |        1.68 ms →        1.32 ms  (-21.40%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      299.44 ms →      292.47 ms   (-2.33%) |       2   →       2              |      598.88 ms →      584.95 ms   (-2.33%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       81.45 ms →       74.97 ms   (-7.95%) |       1   →       1              |       81.45 ms →       74.97 ms   (-7.95%) | 
  │ ├ sirius::K_point::K_point                                          |        2.51 μs →        2.35 μs   (-6.62%) |       4   →       4              |       10.05 μs →        9.39 μs   (-6.62%) | 
  │ └ sirius::K_point_set::initialize                                   |       81.34 ms →       74.87 ms   (-7.96%) |       1   →       1              |       81.34 ms →       74.87 ms   (-7.96%) | 
  │   └ sirius::K_point::initialize                                     |       20.31 ms →       18.70 ms   (-7.96%) |       4   →       4              |       81.26 ms →       74.79 ms   (-7.96%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       15.66 ms →       14.08 ms  (-10.10%) |       4   →       4              |       62.65 ms →       56.32 ms  (-10.10%) | 
  │     │ └ sddk::Gvec::init                                            |        3.91 ms →        3.83 ms   (-2.14%) |       4   →       4              |       15.64 ms →       15.31 ms   (-2.14%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.49 μs →        8.57 μs   (+0.87%) |       4   →       4              |       33.97 μs →       34.27 μs   (+0.87%) | 
  │     └ sirius::K_point::update                                       |        3.32 ms →        3.32 ms   (+0.05%) |       4   →       4              |       13.26 ms →       13.27 ms   (+0.05%) | 
  │       └ sirius::Beta_projectors                                     |        1.78 ms →        1.80 ms   (+1.58%) |       4   →       4              |        7.10 ms →        7.21 ms   (+1.58%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      942.08 μs →      925.46 μs   (-1.76%) |       4   →       4              |        3.77 ms →        3.70 ms   (-1.76%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.33 ms →        5.38 ms   (+0.99%) |       2   →       2              |       10.66 ms →       10.77 ms   (+0.99%) | 
  ├ sirius::Potential                                                   |      158.14 ms →      157.64 ms   (-0.32%) |       1   →       1              |      158.14 ms →      157.64 ms   (-0.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.80 ms →        5.75 ms   (-0.77%) |       6   →       6              |       34.79 ms →       34.52 ms   (-0.77%) | 
  │ └ sirius::Potential::update                                         |      122.67 ms →      122.41 ms   (-0.21%) |       1   →       1              |      122.67 ms →      122.41 ms   (-0.21%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.93 ms →      121.66 ms   (-0.22%) |       1   →       1              |      121.93 ms →      121.66 ms   (-0.22%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.73 ms →      111.49 ms   (+2.54%) |       1   →       1              |      108.73 ms →      111.49 ms   (+2.54%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.32 ms →        9.26 ms  (-24.85%) |       1   →       1              |       12.32 ms →        9.26 ms  (-24.85%) | 
  ├ sirius::Density                                                     |      135.40 ms →      136.04 ms   (+0.48%) |       1   →       1              |      135.40 ms →      136.04 ms   (+0.48%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.14 ms →        5.17 ms   (+0.67%) |       2   →       2              |       10.27 ms →       10.34 ms   (+0.67%) | 
  │ └ sirius::Density::update                                           |      124.86 ms →      125.43 ms   (+0.46%) |       1   →       1              |      124.86 ms →      125.43 ms   (+0.46%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.36 ms →      125.02 ms   (+0.53%) |       1   →       1              |      124.36 ms →      125.02 ms   (+0.53%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      106.59 μs →      107.22 μs   (+0.59%) |       1   →       1              |      106.59 μs →      107.22 μs   (+0.59%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.96 ms →      112.93 ms   (+1.77%) |       1   →       1              |      110.96 ms →      112.93 ms   (+1.77%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.85 ms →       11.44 ms  (-11.00%) |       1   →       1              |       12.85 ms →       11.44 ms  (-11.00%) | 
  ├ sirius::Density::initial_density                                    |      176.84 ms →      173.71 ms   (-1.77%) |       1   →       1              |      176.84 ms →      173.71 ms   (-1.77%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.25 ms →      111.41 ms   (+1.05%) |       1   →       1              |      110.25 ms →      111.41 ms   (+1.05%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.94 ms →       10.29 ms  (-13.81%) |       2   →       2              |       23.88 ms →       20.58 ms  (-13.81%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.68 ms →        9.71 ms   (+0.26%) |       1   →       1              |        9.68 ms →        9.71 ms   (+0.26%) | 
  ├ sirius::Potential::generate                                         |      591.24 ms →      590.37 ms   (-0.15%) |       1   →       1              |      591.24 ms →      590.37 ms   (-0.15%) | 
  │ ├ sirius::Potential::poisson                                        |      138.06 ms →      137.32 ms   (-0.54%) |       1   →       1              |      138.06 ms →      137.32 ms   (-0.54%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       17.56 ms →       16.14 ms   (-8.08%) |       1   →       1              |       17.56 ms →       16.14 ms   (-8.08%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.31 ms →       11.06 ms   (+7.27%) |       1   →       1              |       10.31 ms →       11.06 ms   (+7.27%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.29 ms →       10.30 ms   (+0.09%) |       1   →       1              |       10.29 ms →       10.30 ms   (+0.09%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.29 ms →       10.30 ms   (+0.09%) |       1   →       1              |       10.29 ms →       10.30 ms   (+0.09%) | 
  │ ├ sirius::Periodic_function::add                                    |      530.59 μs →      554.97 μs   (+4.60%) |       2   →       2              |        1.06 ms →        1.11 ms   (+4.60%) | 
  │ ├ sirius::Potential::xc                                             |       53.41 ms →       53.36 ms   (-0.10%) |       1   →       1              |       53.41 ms →       53.36 ms   (-0.10%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.12 ms →       51.07 ms   (-0.09%) |       1   →       1              |       51.12 ms →       51.07 ms   (-0.09%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.64 ms →        5.59 ms   (-0.89%) |       2   →       2              |       11.29 ms →       11.19 ms   (-0.89%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.17 ms →        5.23 ms   (+1.20%) |       1   →       1              |        5.17 ms →        5.23 ms   (+1.20%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.69 ms →        5.96 ms   (+4.65%) |       1   →       1              |        5.69 ms →        5.96 ms   (+4.65%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.50 ms →       92.62 ms   (+0.13%) |       1   →       1              |       92.50 ms →       92.62 ms   (+0.13%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.18 ms →      298.67 ms   (-0.17%) |       1   →       1              |      299.18 ms →      298.67 ms   (-0.17%) | 
  ├ sirius::Hamiltonian0                                                |        8.54 ms →        8.67 ms   (+1.52%) |       1   →       1              |        8.54 ms →        8.67 ms   (+1.52%) | 
  │ ├ sirius::Local_operator                                            |        8.20 ms →        8.33 ms   (+1.54%) |       1   →       1              |        8.20 ms →        8.33 ms   (+1.54%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.66 ms →        4.72 ms   (+1.32%) |       1   →       1              |        4.66 ms →        4.72 ms   (+1.32%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.63 ms →        2.69 ms   (+2.57%) |       1   →       1              |        2.63 ms →        2.69 ms   (+2.57%) | 
  │ ├ sirius::Non_local_operator                                        |       61.95 μs →       64.07 μs   (+3.43%) |       2   →       2              |      123.89 μs →      128.14 μs   (+3.43%) | 
  │ ├ sirius::D_operator::initialize                                    |       91.64 μs →       91.40 μs   (-0.26%) |       1   →       1              |       91.64 μs →       91.40 μs   (-0.26%) | 
  │ └ sirius::Q_operator::initialize                                    |       66.87 μs →       66.81 μs   (-0.09%) |       1   →       1              |       66.87 μs →       66.81 μs   (-0.09%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.08 s  →        3.08 s    (+0.14%) |       1   →       1              |        3.08 s  →        3.08 s    (+0.14%) | 
  │ ├ sirius::Hamiltonian_k                                             |      379.95 μs →      376.76 μs   (-0.84%) |       4   →       4              |        1.52 ms →        1.51 ms   (-0.84%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      375.17 μs →      371.89 μs   (-0.87%) |       4   →       4              |        1.50 ms →        1.49 ms   (-0.87%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.08 μs →        3.13 μs   (+1.42%) |       4   →       4              |       12.34 μs →       12.52 μs   (+1.42%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      768.65 ms →      769.76 ms   (+0.14%) |       4   →       4              |        3.07 s  →        3.08 s    (+0.14%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.07 ms →       32.67 ms   (+1.85%) |      16   →      16              |      513.17 ms →      522.66 ms   (+1.85%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.60 ms →       14.49 ms   (-0.73%) |       4   →       4              |       58.38 ms →       57.96 ms   (-0.73%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.31 ms →        5.32 ms   (+0.19%) |       4   →       4              |       21.22 ms →       21.26 ms   (+0.19%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.01 ms →      350.00 ms   (-1.13%) |       4   →       4              |        1.42 s  →        1.40 s    (-1.13%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      257.36 ms →      253.39 ms   (-1.55%) |       4   →       4              |        1.03 s  →        1.01 s    (-1.55%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.45 ms →       61.28 ms   (-3.42%) |       4   →       4              |      253.81 ms →      245.13 ms   (-3.42%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       15.78 ms →       16.39 ms   (+3.84%) |       4   →       4              |       63.14 ms →       65.56 ms   (+3.84%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.78 ms →       16.39 ms   (+3.84%) |       4   →       4              |       63.13 ms →       65.55 ms   (+3.84%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.25 ms →       38.40 ms   (-6.90%) |       4   →       4              |      165.00 ms →      153.60 ms   (-6.90%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       15.92 ms →       16.13 ms   (+1.32%) |       4   →       4              |       63.68 ms →       64.52 ms   (+1.32%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.92 ms →       16.13 ms   (+1.33%) |       4   →       4              |       63.66 ms →       64.51 ms   (+1.33%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.32 ms →       52.21 ms   (-3.87%) |       4   →       4              |      217.26 ms →      208.85 ms   (-3.87%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.26 ms →       34.18 ms   (-5.76%) |       4   →       4              |      145.06 ms →      136.70 ms   (-5.76%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.97 ms →        1.95 ms   (-0.92%) |       4   →       4              |        7.88 ms →        7.80 ms   (-0.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.47 ms →       40.39 ms   (-0.18%) |       4   →       4              |      161.87 ms →      161.58 ms   (-0.18%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.30 ms →        7.23 ms   (-0.92%) |       4   →       4              |       29.19 ms →       28.92 ms   (-0.92%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.11 ms   (+0.10%) |       8   →       8              |      216.69 ms →      216.91 ms   (+0.10%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.94 ms →       15.62 ms   (+4.54%) |       8   →       8              |      119.55 ms →      124.98 ms   (+4.54%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.90 ms →       15.58 ms   (+4.54%) |       8   →       8              |      119.20 ms →      124.61 ms   (+4.54%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       31.63 ns →       55.87 ns  (+76.68%) |       8   →       8              |      253.00 ns →      447.00 ns  (+76.68%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.70 ms →       15.38 ms   (+4.65%) |       8   →       8              |      117.60 ms →      123.07 ms   (+4.65%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.62 ns →       25.25 ns  (+22.42%) |       8   →       8              |      165.00 ns →      202.00 ns  (+22.42%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      118.55 ms →      117.40 ms   (-0.97%) |       4   →       4              |      474.19 ms →      469.60 ms   (-0.97%) | 
- │ │ └ sddk::wf_trans                                                  |       23.48 ms →       26.71 ms  (+13.74%) |       4   →       4              |       93.92 ms →      106.83 ms  (+13.74%) | 
- │ │   └ sddk::wf_trans|pw                                             |       23.26 ms →       26.45 ms  (+13.70%) |       4   →       4              |       93.06 ms →      105.80 ms  (+13.70%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      422.75 ns →      428.25 ns   (+1.30%) |       4   →       4              |        1.69 μs →        1.71 μs   (+1.30%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      211.97 s  →      216.25 s    (+2.02%) |       1   →       1              |      211.97 s  →      216.25 s    (+2.02%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.71 ms →        5.72 ms   (+0.20%) |      19   →      19              |      108.46 ms →      108.68 ms   (+0.20%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        7.84 s  →        7.99 s    (+2.03%) |      27   →      27              |      211.57 s  →      215.85 s    (+2.03%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.49 ms →        4.52 ms   (+0.79%) |      27   →      27              |      121.11 ms →      122.07 ms   (+0.79%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.13 ms →        4.17 ms   (+0.89%) |      27   →      27              |      111.54 ms →      112.53 ms   (+0.89%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      959.43 μs →      984.69 μs   (+2.63%) |      27   →      27              |       25.90 ms →       26.59 ms   (+2.63%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.28 ms →        2.29 ms   (+0.40%) |      27   →      27              |       61.69 ms →       61.94 ms   (+0.40%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.28 μs →       64.44 μs   (+0.24%) |      54   →      54              |        3.47 ms →        3.48 ms   (+0.24%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       90.85 μs →       89.34 μs   (-1.66%) |      27   →      27              |        2.45 ms →        2.41 ms   (-1.66%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.43 μs →       65.60 μs   (+0.25%) |      27   →      27              |        1.77 ms →        1.77 ms   (+0.25%) | 
  │ │ ├ sirius::Band::solve                                             |        5.75 s  →        5.91 s    (+2.71%) |      27   →      27              |      155.27 s  →      159.48 s    (+2.71%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      336.29 μs →      352.97 μs   (+4.96%) |     108   →     108              |       36.32 ms →       38.12 ms   (+4.96%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      330.59 μs →      347.62 μs   (+5.15%) |     108   →     108              |       35.70 ms →       37.54 ms   (+5.15%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.03 μs →        3.96 μs   (-1.70%) |     108   →     108              |      434.92 μs →      427.51 μs   (-1.70%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.44 s  →        1.48 s    (+2.71%) |     108   →     108              |      155.24 s  →      159.44 s    (+2.71%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.94 ms →       11.94 ms   (+0.02%) |     108   →     108              |        1.29 s  →        1.29 s    (+0.02%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      700.71 ns →      743.05 ns   (+6.04%) |     648   →     648              |      454.06 μs →      481.50 μs   (+6.04%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.82 ms   (-0.26%) |     108   →     108              |      197.54 ms →      197.02 ms   (-0.26%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      353.81 μs →      353.74 μs   (-0.02%) |     108   →     108              |       38.21 ms →       38.20 ms   (-0.02%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      551.59 μs →      549.12 μs   (-0.45%) |     216   →     216              |      119.14 ms →      118.61 ms   (-0.45%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.41 s  →        1.45 s    (+2.75%) |     108   →     108              |      152.77 s  →      156.98 s    (+2.75%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       66.70 ms →       65.58 ms   (-1.68%) |     999   →    1.01 K   (+1.10%) |       66.63 s  →       66.23 s    (-0.60%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.58 ms →       41.61 ms   (-2.28%) |     999   →    1.01 K   (+1.10%) |       42.54 s  →       42.03 s    (-1.20%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.50 ms →        8.17 ms   (-3.94%) |     999   →    1.01 K   (+1.10%) |        8.49 s  →        8.25 s    (-2.88%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      209.29 μs →      224.69 μs   (+7.36%) |     999   →    1.01 K   (+1.10%) |      209.09 ms →      226.94 ms   (+8.54%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.92 ms →        2.08 ms   (+8.64%) |     108   →     108              |      207.11 ms →      225.01 ms   (+8.64%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.52 ms →        6.19 ms   (-5.04%) |     999   →    1.01 K   (+1.10%) |        6.52 s  →        6.26 s    (-4.00%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       79.69 μs →       80.26 μs   (+0.71%) |     999   →    1.01 K   (+1.10%) |       79.61 ms →       81.06 ms   (+1.82%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      715.58 μs →      728.18 μs   (+1.76%) |     108   →     108              |       77.28 ms →       78.64 ms   (+1.76%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.32 ms →        8.95 ms   (-3.98%) |     999   →    1.01 K   (+1.10%) |        9.31 s  →        9.04 s    (-2.92%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.87 ms →        5.54 ms   (-5.59%) |     999   →    1.01 K   (+1.10%) |        5.86 s  →        5.59 s    (-4.55%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.17%) |     999   →    1.01 K   (+1.10%) |        1.52 s  →        1.53 s    (+0.93%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.25 ms →        8.13 ms   (-1.50%) |     999   →    1.01 K   (+1.10%) |        8.24 s  →        8.21 s    (-0.42%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.24 ms →        1.19 ms   (-3.51%) |     999   →    1.01 K   (+1.10%) |        1.23 s  →        1.20 s    (-2.45%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.16 ms →        7.15 ms   (-0.20%) |    2.00 K →    2.02 K   (+1.10%) |       14.32 s  →       14.44 s    (+0.90%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       25.86 ms →       27.37 ms   (+5.84%) |     999   →    1.01 K   (+1.10%) |       25.83 s  →       27.64 s    (+7.01%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.88 ms →        1.88 ms   (+0.06%) |    1.89 K →    1.91 K   (+1.16%) |        3.55 s  →        3.59 s    (+1.22%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       71.24 ns →       64.41 ns   (-9.59%) |    1.89 K →    1.91 K   (+1.16%) |      134.65 μs →      123.15 μs   (-8.54%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.87 ms →        1.87 ms   (+0.12%) |    1.89 K →    1.91 K   (+1.16%) |        3.53 s  →        3.58 s    (+1.28%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       67.92 ns →       74.27 ns   (+9.36%) |    1.89 K →    1.91 K   (+1.16%) |      128.37 μs →      142.01 μs  (+10.63%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      789.28 μs →      791.62 μs   (+0.30%) |     999   →    1.01 K   (+1.10%) |      788.49 ms →      799.54 ms   (+1.40%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      728.00 μs →      688.31 μs   (-5.45%) |     999   →    1.01 K   (+1.10%) |      727.27 ms →      695.19 ms   (-4.41%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        4.96 ms →        5.36 ms   (+8.06%) |    3.89 K →    3.93 K   (+1.13%) |       19.27 s  →       21.06 s    (+9.28%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.37 ms →        3.64 ms   (+8.02%) |    5.67 K →    5.74 K   (+1.16%) |       19.08 s  →       20.85 s    (+9.28%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.17 ms →        5.23 ms   (+1.18%) |     999   →    1.01 K   (+1.10%) |        5.17 s  →        5.29 s    (+2.29%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.36 ms →        3.40 ms   (+1.07%) |     999   →    1.01 K   (+1.10%) |        3.36 s  →        3.43 s    (+2.18%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       50.69 ns →       85.35 ns  (+68.38%) |     999   →    1.01 K   (+1.10%) |       50.64 μs →       86.20 μs  (+70.24%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.35 ms →        3.39 ms   (+1.11%) |     999   →    1.01 K   (+1.10%) |        3.35 s  →        3.42 s    (+2.22%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       41.94 ns →       72.10 ns  (+71.93%) |     999   →    1.01 K   (+1.10%) |       41.89 μs →       72.82 μs  (+73.82%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       32.66 ms →       32.64 ms   (-0.04%) |     999   →    1.01 K   (+1.10%) |       32.62 s  →       32.97 s    (+1.06%) | 
- │ │ │ │   ├ sirius::residuals                                         |        9.97 ms →       10.90 ms   (+9.29%) |     969   →     978     (+0.93%) |        9.66 s  →       10.66 s   (+10.31%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        9.49 ms →       10.47 ms  (+10.24%) |     929   →     937     (+0.86%) |        8.82 s  →        9.81 s   (+11.18%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        4.71 ms →        5.21 ms  (+10.46%) |    1.86 K →    1.87 K   (+0.86%) |        8.76 s  →        9.76 s   (+11.41%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      639.03 μs →      639.77 μs   (+0.12%) |     929   →     937     (+0.86%) |      593.66 ms →      599.47 ms   (+0.98%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       36.02 ms →       40.57 ms  (+12.63%) |     356   →     349     (-1.97%) |       12.82 s  →       14.16 s   (+10.41%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       21.10 ms →       23.87 ms  (+13.11%) |     604   →     590     (-2.32%) |       12.75 s  →       14.08 s   (+10.49%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       14.86 ms →       16.88 ms  (+13.59%) |     852   →     831     (-2.46%) |       12.66 s  →       14.03 s   (+10.79%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      506.99 ns →      538.38 ns   (+6.19%) |     108   →     108              |       54.76 μs →       58.15 μs   (+6.19%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       24.07 μs →       23.27 μs   (-3.33%) |      27   →      27              |      649.99 μs →      628.37 μs   (-3.33%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      590.45 μs →      608.11 μs   (+2.99%) |      27   →      27              |       15.94 ms →       16.42 ms   (+2.99%) | 
  │ │ ├ sirius::Density::generate                                       |      887.95 ms →      889.04 ms   (+0.12%) |      27   →      27              |       23.97 s  →       24.00 s    (+0.12%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      525.88 ms →      521.25 ms   (-0.88%) |      27   →      27              |       14.20 s  →       14.07 s    (-0.88%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.58 ms →       23.27 ms   (-5.32%) |     108   →     108              |        2.65 s  →        2.51 s    (-5.32%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.93 μs →        6.00 μs   (+1.23%) |     108   →     108              |      640.38 μs →      648.25 μs   (+1.23%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.49 μs →       12.90 μs   (+3.27%) |       8   →       8              |       99.93 μs →      103.20 μs   (+3.27%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.47 ms →       19.16 ms   (-6.39%) |     108   →     108              |        2.21 s  →        2.07 s    (-6.39%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.01 ms →       30.01 ms   (+0.03%) |     108   →     108              |        3.24 s  →        3.24 s    (+0.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.46 μs →       11.08 μs   (-3.34%) |     108   →     108              |        1.24 ms →        1.20 ms   (-3.34%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.47 ms →        1.46 ms   (-0.27%) |     108   →     108              |      158.41 ms →      157.98 ms   (-0.27%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.05 ms →       28.06 ms   (+0.05%) |     108   →     108              |        3.03 s  →        3.03 s    (+0.05%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.92 ms →        3.93 ms   (+0.31%) |     108   →     108              |      423.38 ms →      424.69 ms   (+0.31%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      550.59 ns →      466.86 ns  (-15.21%) |     108   →     108              |       59.46 μs →       50.42 μs  (-15.21%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.39 ms →       42.74 ms   (+0.82%) |     108   →     108              |        4.58 s  →        4.62 s    (+0.82%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.27%) |      27   →      27              |       44.49 ms →       44.37 ms   (-0.27%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.85 ms →       88.94 ms   (+0.09%) |      27   →      27              |        2.40 s  →        2.40 s    (+0.09%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.62 ms →       88.70 ms   (+0.09%) |      27   →      27              |        2.39 s  →        2.39 s    (+0.09%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      270.59 ms →      268.95 ms   (-0.61%) |      27   →      27              |        7.31 s  →        7.26 s    (-0.61%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      270.59 ms →      268.95 ms   (-0.61%) |      27   →      27              |        7.31 s  →        7.26 s    (-0.61%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.54 ms →       24.38 ms   (-0.66%) |      27   →      27              |      662.62 ms →      658.23 ms   (-0.66%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      220.11 ms →      218.56 ms   (-0.70%) |      27   →      27              |        5.94 s  →        5.90 s    (-0.70%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.11 ms →       24.17 ms   (+0.24%) |      27   →      27              |      651.06 ms →      652.65 ms   (+0.24%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.52 ms →       80.88 ms   (+0.45%) |      27   →      27              |        2.17 s  →        2.18 s    (+0.45%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.34 ms →       14.35 ms  (+95.44%) |      27   →      27              |      198.29 ms →      387.53 ms  (+95.44%) | 
  │ │ ├ sirius::Density::mix                                            |      215.11 ms →      223.35 ms   (+3.83%) |      27   →      27              |        5.81 s  →        6.03 s    (+3.83%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      959.63 μs →      962.07 μs   (+0.25%) |      27   →      27              |       25.91 ms →       25.98 ms   (+0.25%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.31 ms →       10.97 ms   (+6.42%) |     349   →     349              |        3.60 s  →        3.83 s    (+6.42%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.98 ms →       10.87 ms   (+8.87%) |     349   →     349              |        3.48 s  →        3.79 s    (+8.87%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.98 ms →       10.87 ms   (+8.87%) |     349   →     349              |        3.48 s  →        3.79 s    (+8.87%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.55 ms →        6.12 ms   (-6.66%) |      27   →      27              |      176.94 ms →      165.15 ms   (-6.66%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.73 ms →        5.31 ms   (-7.44%) |      27   →      27              |      154.83 ms →      143.31 ms   (-7.44%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.81 ms →      578.75 ms   (-0.35%) |      27   →      27              |       15.68 s  →       15.63 s    (-0.35%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.90 ms →      137.09 ms   (-1.31%) |      27   →      27              |        3.75 s  →        3.70 s    (-1.31%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.04 ms →       16.05 ms  (-11.01%) |      27   →      27              |      487.07 ms →      433.46 ms  (-11.01%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       11.10 ms →       10.66 ms   (-4.03%) |      27   →      27              |      299.81 ms →      287.71 ms   (-4.03%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.39 ms →       10.37 ms   (-0.24%) |      27   →      27              |      280.66 ms →      279.99 ms   (-0.24%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.39 ms →       10.37 ms   (-0.24%) |      27   →      27              |      280.65 ms →      279.97 ms   (-0.24%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      552.91 μs →      552.16 μs   (-0.14%) |      54   →      54              |       29.86 ms →       29.82 ms   (-0.14%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.29 ms →       49.05 ms   (-0.49%) |      27   →      27              |        1.33 s  →        1.32 s    (-0.49%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.95 ms →       46.68 ms   (-0.56%) |      27   →      27              |        1.27 s  →        1.26 s    (-0.56%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.08 ms →        3.04 ms   (-1.11%) |      54   →      54              |      166.16 ms →      164.30 ms   (-1.11%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.33 ms →        5.26 ms   (-1.25%) |      27   →      27              |      143.88 ms →      142.08 ms   (-1.25%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.71 ms →        6.76 ms   (+0.70%) |      27   →      27              |      181.29 ms →      182.57 ms   (+0.70%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.92 ms →       90.92 ms   (+0.00%) |      27   →      27              |        2.45 s  →        2.45 s    (+0.00%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.60 ms →      292.53 ms   (-0.02%) |      27   →      27              |        7.90 s  →        7.90 s    (-0.02%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      273.28 ms →      272.25 ms   (-0.38%) |      27   →      27              |        7.38 s  →        7.35 s    (-0.38%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      273.28 ms →      272.25 ms   (-0.38%) |      27   →      27              |        7.38 s  →        7.35 s    (-0.38%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.33 ms →       27.01 ms   (-1.14%) |      27   →      27              |      737.78 ms →      729.36 ms   (-1.14%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      218.47 ms →      217.68 ms   (-0.36%) |      27   →      27              |        5.90 s  →        5.88 s    (-0.36%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.69 ms →       23.77 ms   (+0.33%) |      27   →      27              |      639.74 ms →      641.85 ms   (+0.33%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.63 ms →        5.61 ms   (-0.25%) |      27   →      27              |      151.89 ms →      151.52 ms   (-0.25%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.85 ms →       10.25 ms   (-5.58%) |     189   →     189              |        2.05 s  →        1.94 s    (-5.58%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.33 ms →        9.80 ms   (-5.08%) |     189   →     189              |        1.95 s  →        1.85 s    (-5.08%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.33 ms →        9.80 ms   (-5.08%) |     189   →     189              |        1.95 s  →        1.85 s    (-5.08%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.26 ms →       10.60 ms   (+3.33%) |      81   →      81              |      831.12 ms →      858.82 ms   (+3.33%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.82 ms →       10.17 ms   (+3.57%) |      81   →      81              |      795.70 ms →      824.14 ms   (+3.57%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.11 ms →        9.94 ms   (-1.72%) |      27   →      27              |      272.96 ms →      268.27 ms   (-1.72%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      114.41 μs →      113.62 μs   (-0.68%) |      27   →      27              |        3.09 ms →        3.07 ms   (-0.68%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      109.03 μs →      108.20 μs   (-0.76%) |      27   →      27              |        2.94 ms →        2.92 ms   (-0.76%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.03 ms →        5.32 ms   (+5.87%) |       2   →       2              |       10.06 ms →       10.65 ms   (+5.87%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.73 ms →        9.80 ms   (-8.61%) |       6   →       6              |       64.36 ms →       58.82 ms   (-8.61%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.72 ms →        9.72 ms   (-9.29%) |       6   →       6              |       64.29 ms →       58.32 ms   (-9.29%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.72 ms →        9.72 ms   (-9.29%) |       6   →       6              |       64.29 ms →       58.32 ms   (-9.29%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.30 ms →       10.15 ms   (-1.40%) |       3   →       3              |       30.89 ms →       30.46 ms   (-1.40%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.00 ms →       10.08 ms   (+0.81%) |       3   →       3              |       30.00 ms →       30.25 ms   (+0.81%) | 
  ├ sirius::Periodic_function|inner                                     |       10.42 ms →        9.78 ms   (-6.19%) |       2   →       2              |       20.85 ms →       19.56 ms   (-6.19%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.42 ms →        9.61 ms   (-7.73%) |       2   →       2              |       20.83 ms →       19.22 ms   (-7.73%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.42 ms →        9.61 ms   (-7.73%) |       2   →       2              |       20.83 ms →       19.22 ms   (-7.73%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.95 ms →       10.17 ms   (+2.25%) |       1   →       1              |        9.95 ms →       10.17 ms   (+2.25%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.94 ms →       10.06 ms   (+1.21%) |       1   →       1              |        9.94 ms →       10.06 ms   (+1.21%) | 
- └ sirius::finalize                                                    |      284.46 ms →      326.40 ms  (+14.74%) |       1   →       1              |      284.46 ms →      326.40 ms  (+14.74%) | 
  ====================================================================================================================================================================================================
```
