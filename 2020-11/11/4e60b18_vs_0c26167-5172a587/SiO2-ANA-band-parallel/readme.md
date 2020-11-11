# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 4e60b1847c4444fb88c162c63a530351544e3d41
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      364.48 s  →      349.16 s    (-4.20%) |       1   →       1              |      364.48 s  →      349.16 s    (-4.20%) | 
  ├ sirius::initialize                                                  |        2.76 s  →        2.77 s    (+0.19%) |       1   →       1              |        2.76 s  →        2.77 s    (+0.19%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        2.94 s    (+0.58%) |       1   →       1              |        2.92 s  →        2.94 s    (+0.58%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      229.62 μs →       67.11 ms (+29128.83%) |       1   →       1              |      229.62 μs →       67.11 ms (+29128.83%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      176.59 ms →      123.98 ms  (-29.79%) |       1   →       1              |      176.59 ms →      123.98 ms  (-29.79%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       76.23 ms →       49.99 ms  (-34.42%) |       2   →       2              |      152.45 ms →       99.98 ms  (-34.42%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.06 ms →       23.93 ms   (-0.55%) |       1   →       1              |       24.06 ms →       23.93 ms   (-0.55%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.44 ms →        6.32 ms   (-1.83%) |       1   →       1              |        6.44 ms →        6.32 ms   (-1.83%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.58 ms →       17.57 ms   (-0.06%) |       1   →       1              |       17.58 ms →       17.57 ms   (-0.06%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.56 ms →       17.54 ms   (-0.09%) |       1   →       1              |       17.56 ms →       17.54 ms   (-0.09%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.13 ms   (-0.23%) |       1   →       1              |        4.14 ms →        4.13 ms   (-0.23%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (-0.01%) |       1   →       1              |        2.34 ms →        2.34 ms   (-0.01%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.81 μs →      105.38 μs   (+4.54%) |       1   →       1              |      100.81 μs →      105.38 μs   (+4.54%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.70 s    (+0.04%) |       1   →       1              |        2.70 s  →        2.70 s    (+0.04%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.98 ms →       10.93 ms   (-0.50%) |       1   →       1              |       10.98 ms →       10.93 ms   (-0.50%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.52 ms   (+1.62%) |       1   →       1              |        4.45 ms →        4.52 ms   (+1.62%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.50 ms →        6.38 ms   (-1.89%) |       1   →       1              |        6.50 ms →        6.38 ms   (-1.89%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.48 ms →        6.36 ms   (-1.90%) |       1   →       1              |        6.48 ms →        6.36 ms   (-1.90%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.97 ms →        3.87 ms   (-2.55%) |       1   →       1              |        3.97 ms →        3.87 ms   (-2.55%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-0.96%) |       1   →       1              |        2.34 ms →        2.32 ms   (-0.96%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.77 μs →      104.57 μs   (+3.77%) |       1   →       1              |      100.77 μs →      104.57 μs   (+3.77%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.39 ms →       62.71 ms   (-2.61%) |       2   →       2              |      128.78 ms →      125.42 ms   (-2.61%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.21 ms   (+1.33%) |       2   →       2              |       10.29 ms →       10.43 ms   (+1.33%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.53 ms →        4.58 ms   (+1.03%) |       1   →       1              |        4.53 ms →        4.58 ms   (+1.03%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.93 ms   (+0.56%) |       2   →       2              |       43.61 ms →       43.86 ms   (+0.56%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.83 ms   (+0.07%) |       2   →       2              |       29.64 ms →       29.67 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.79 ms →       19.91 ms   (+0.62%) |       4   →       4              |       79.16 ms →       79.65 ms   (+0.62%) | 
  │   ├ sddk::Gvec::init                                                |      174.08 ms →      173.00 ms   (-0.62%) |       2   →       2              |      348.15 ms →      346.00 ms   (-0.62%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.23 ms →      130.41 ms   (-0.62%) |       2   →       2              |      262.47 ms →      260.83 ms   (-0.62%) | 
  │   ├ sddk::Gvec_shells                                               |      188.55 ms →      179.69 ms   (-4.70%) |       1   →       1              |      188.55 ms →      179.69 ms   (-4.70%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.55%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.55%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.54 ms →      293.34 ms   (-0.74%) |       2   →       2              |      591.08 ms →      586.68 ms   (-0.74%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       78.65 ms →       77.39 ms   (-1.61%) |       1   →       1              |       78.65 ms →       77.39 ms   (-1.61%) | 
  │ ├ sirius::K_point::K_point                                          |        2.56 μs →        2.40 μs   (-6.13%) |       4   →       4              |       10.23 μs →        9.60 μs   (-6.13%) | 
  │ └ sirius::K_point_set::initialize                                   |       78.56 ms →       77.28 ms   (-1.63%) |       1   →       1              |       78.56 ms →       77.28 ms   (-1.63%) | 
  │   └ sirius::K_point::initialize                                     |       19.62 ms →       19.30 ms   (-1.62%) |       4   →       4              |       78.46 ms →       77.19 ms   (-1.62%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.06 ms →       14.56 ms   (-3.37%) |       4   →       4              |       60.25 ms →       58.22 ms   (-3.37%) | 
  │     │ └ sddk::Gvec::init                                            |        3.81 ms →        4.01 ms   (+5.10%) |       4   →       4              |       15.25 ms →       16.03 ms   (+5.10%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.40 μs →        8.75 μs   (+4.15%) |       4   →       4              |       33.62 μs →       35.01 μs   (+4.15%) | 
  │     └ sirius::K_point::update                                       |        3.26 ms →        3.36 ms   (+3.10%) |       4   →       4              |       13.03 ms →       13.44 ms   (+3.10%) | 
  │       └ sirius::Beta_projectors                                     |        1.77 ms →        1.76 ms   (-0.75%) |       4   →       4              |        7.08 ms →        7.03 ms   (-0.75%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      934.17 μs →      923.82 μs   (-1.11%) |       4   →       4              |        3.74 ms →        3.70 ms   (-1.11%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.42 ms →        5.28 ms   (-2.62%) |       2   →       2              |       10.84 ms →       10.56 ms   (-2.62%) | 
  ├ sirius::Potential                                                   |      155.34 ms →      156.53 ms   (+0.76%) |       1   →       1              |      155.34 ms →      156.53 ms   (+0.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.75 ms   (-2.07%) |       6   →       6              |       35.24 ms →       34.51 ms   (-2.07%) | 
  │ └ sirius::Potential::update                                         |      119.39 ms →      121.31 ms   (+1.60%) |       1   →       1              |      119.39 ms →      121.31 ms   (+1.60%) | 
  │   └ sirius::Potential::generate_local_potential                     |      118.66 ms →      120.60 ms   (+1.63%) |       1   →       1              |      118.66 ms →      120.60 ms   (+1.63%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.30 ms →      111.63 ms   (+2.13%) |       1   →       1              |      109.30 ms →      111.63 ms   (+2.13%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        8.48 ms →        8.04 ms   (-5.13%) |       1   →       1              |        8.48 ms →        8.04 ms   (-5.13%) | 
  ├ sirius::Density                                                     |      129.66 ms →      136.05 ms   (+4.93%) |       1   →       1              |      129.66 ms →      136.05 ms   (+4.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.40 ms →        5.13 ms   (-5.08%) |       2   →       2              |       10.81 ms →       10.26 ms   (-5.08%) | 
  │ └ sirius::Density::update                                           |      118.57 ms →      125.53 ms   (+5.87%) |       1   →       1              |      118.57 ms →      125.53 ms   (+5.87%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      118.12 ms →      125.11 ms   (+5.91%) |       1   →       1              |      118.12 ms →      125.11 ms   (+5.91%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      111.41 μs →      103.99 μs   (-6.65%) |       1   →       1              |      111.41 μs →      103.99 μs   (-6.65%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.75 ms →      112.26 ms   (+1.36%) |       1   →       1              |      110.75 ms →      112.26 ms   (+1.36%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.80 ms →       12.30 ms  (+81.01%) |       1   →       1              |        6.80 ms →       12.30 ms  (+81.01%) | 
  ├ sirius::Density::initial_density                                    |      164.20 ms →      175.69 ms   (+7.00%) |       1   →       1              |      164.20 ms →      175.69 ms   (+7.00%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      109.55 ms →      110.75 ms   (+1.09%) |       1   →       1              |      109.55 ms →      110.75 ms   (+1.09%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.39 ms →       11.60 ms  (+81.64%) |       2   →       2              |       12.78 ms →       23.21 ms  (+81.64%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.90 ms →        9.73 ms   (-1.70%) |       1   →       1              |        9.90 ms →        9.73 ms   (-1.70%) | 
  ├ sirius::Potential::generate                                         |      583.83 ms →      593.69 ms   (+1.69%) |       1   →       1              |      583.83 ms →      593.69 ms   (+1.69%) | 
  │ ├ sirius::Potential::poisson                                        |      126.78 ms →      138.22 ms   (+9.02%) |       1   →       1              |      126.78 ms →      138.22 ms   (+9.02%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.64 ms →       18.50 ms (+178.83%) |       1   →       1              |        6.64 ms →       18.50 ms (+178.83%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.32 ms →        9.86 ms   (-4.43%) |       1   →       1              |       10.32 ms →        9.86 ms   (-4.43%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.80 ms   (-0.78%) |       1   →       1              |        9.88 ms →        9.80 ms   (-0.78%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.80 ms   (-0.78%) |       1   →       1              |        9.88 ms →        9.80 ms   (-0.78%) | 
  │ ├ sirius::Periodic_function::add                                    |      560.84 μs →      545.67 μs   (-2.70%) |       2   →       2              |        1.12 ms →        1.09 ms   (-2.70%) | 
  │ ├ sirius::Potential::xc                                             |       55.69 ms →       53.66 ms   (-3.64%) |       1   →       1              |       55.69 ms →       53.66 ms   (-3.64%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.33 ms →       51.36 ms   (-3.69%) |       1   →       1              |       53.33 ms →       51.36 ms   (-3.69%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        6.24 ms →        5.59 ms  (-10.49%) |       2   →       2              |       12.48 ms →       11.17 ms  (-10.49%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.10 ms →        5.31 ms   (+4.29%) |       1   →       1              |        5.10 ms →        5.31 ms   (+4.29%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.73 ms →        5.88 ms   (+2.73%) |       1   →       1              |        5.73 ms →        5.88 ms   (+2.73%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.92 ms →       93.52 ms   (+0.64%) |       1   →       1              |       92.92 ms →       93.52 ms   (+0.64%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.25 ms →      299.98 ms   (-0.09%) |       1   →       1              |      300.25 ms →      299.98 ms   (-0.09%) | 
  ├ sirius::Hamiltonian0                                                |        8.90 ms →        8.35 ms   (-6.20%) |       1   →       1              |        8.90 ms →        8.35 ms   (-6.20%) | 
  │ ├ sirius::Local_operator                                            |        8.56 ms →        8.01 ms   (-6.48%) |       1   →       1              |        8.56 ms →        8.01 ms   (-6.48%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.68 ms   (-1.83%) |       1   →       1              |        4.77 ms →        4.68 ms   (-1.83%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.87 ms →        2.41 ms  (-15.95%) |       1   →       1              |        2.87 ms →        2.41 ms  (-15.95%) | 
  │ ├ sirius::Non_local_operator                                        |       62.77 μs →       63.23 μs   (+0.73%) |       2   →       2              |      125.55 μs →      126.46 μs   (+0.73%) | 
  │ ├ sirius::D_operator::initialize                                    |       93.35 μs →       95.86 μs   (+2.68%) |       1   →       1              |       93.35 μs →       95.86 μs   (+2.68%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.54 μs →       68.72 μs   (-1.18%) |       1   →       1              |       69.54 μs →       68.72 μs   (-1.18%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.23 s  →        4.04 s    (-4.51%) |       1   →       1              |        4.23 s  →        4.04 s    (-4.51%) | 
  │ ├ sirius::Hamiltonian_k                                             |      379.23 μs →      377.68 μs   (-0.41%) |       4   →       4              |        1.52 ms →        1.51 ms   (-0.41%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      374.11 μs →      372.69 μs   (-0.38%) |       4   →       4              |        1.50 ms →        1.49 ms   (-0.38%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.17 μs →        3.30 μs   (+4.26%) |       4   →       4              |       12.68 μs →       13.22 μs   (+4.26%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.06 s  →        1.01 s    (-4.51%) |       4   →       4              |        4.23 s  →        4.04 s    (-4.51%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.53 ms →       32.60 ms   (+0.23%) |      16   →      16              |      520.43 ms →      521.63 ms   (+0.23%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.60 ms →       14.53 ms   (-0.51%) |       4   →       4              |       58.41 ms →       58.11 ms   (-0.51%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.39 ms →        5.29 ms   (-1.98%) |       4   →       4              |       21.58 ms →       21.15 ms   (-1.98%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      358.57 ms →      354.51 ms   (-1.13%) |       4   →       4              |        1.43 s  →        1.42 s    (-1.13%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      260.25 ms →      258.15 ms   (-0.81%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.81%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.47 ms →       63.32 ms   (-1.79%) |       4   →       4              |      257.90 ms →      253.29 ms   (-1.79%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.58 ms →       16.31 ms   (-1.62%) |       4   →       4              |       66.31 ms →       65.23 ms   (-1.62%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.57 ms →       16.31 ms   (-1.62%) |       4   →       4              |       66.30 ms →       65.22 ms   (-1.62%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.36 ms →       40.61 ms   (-1.82%) |       4   →       4              |      165.44 ms →      162.42 ms   (-1.82%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.52 ms →       16.32 ms   (-1.20%) |       4   →       4              |       66.06 ms →       65.27 ms   (-1.20%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.51 ms →       16.31 ms   (-1.20%) |       4   →       4              |       66.05 ms →       65.25 ms   (-1.20%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.86 ms →       54.20 ms   (-1.20%) |       4   →       4              |      219.44 ms →      216.81 ms   (-1.20%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.87 ms →       36.18 ms   (-1.88%) |       4   →       4              |      147.49 ms →      144.71 ms   (-1.88%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.96 ms   (+0.19%) |       4   →       4              |        7.82 ms →        7.83 ms   (+0.19%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       42.13 ms →       40.20 ms   (-4.57%) |       4   →       4              |      168.50 ms →      160.80 ms   (-4.57%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.99 ms →        7.06 ms  (-21.49%) |       4   →       4              |       35.95 ms →       28.22 ms  (-21.49%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.10 ms →       27.08 ms   (-0.06%) |       8   →       8              |      216.80 ms →      216.66 ms   (-0.06%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.00 ms →       14.75 ms   (-7.80%) |       8   →       8              |      128.02 ms →      118.03 ms   (-7.80%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.95 ms →       14.71 ms   (-7.78%) |       8   →       8              |      127.62 ms →      117.68 ms   (-7.78%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       36.00 ns →       27.38 ns  (-23.96%) |       8   →       8              |      288.00 ns →      219.00 ns  (-23.96%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.77 ms →       14.53 ms   (-7.86%) |       8   →       8              |      126.12 ms →      116.21 ms   (-7.86%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       27.12 ns →       23.00 ns  (-15.21%) |       8   →       8              |      217.00 ns →      184.00 ns  (-15.21%) | 
+ │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      394.69 ms →      354.49 ms  (-10.19%) |       4   →       4              |        1.58 s  →        1.42 s   (-10.19%) | 
  │ │ └ sddk::wf_trans                                                  |       27.35 ms →       26.66 ms   (-2.51%) |       4   →       4              |      109.39 ms →      106.64 ms   (-2.51%) | 
  │ │   └ sddk::wf_trans|pw                                             |       27.25 ms →       26.56 ms   (-2.54%) |       4   →       4              |      108.99 ms →      106.22 ms   (-2.54%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      411.00 ns →      388.75 ns   (-5.41%) |       4   →       4              |        1.64 μs →        1.55 μs   (-5.41%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      352.61 s  →      337.43 s    (-4.31%) |       1   →       1              |      352.61 s  →      337.43 s    (-4.31%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.83 ms   (-0.30%) |      19   →      19              |      111.19 ms →      110.85 ms   (-0.30%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       13.04 s  →       12.48 s    (-4.28%) |      27   →      27              |      352.11 s  →      337.04 s    (-4.28%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.60 ms →        4.43 ms   (-3.62%) |      27   →      27              |      124.22 ms →      119.73 ms   (-3.62%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.24 ms →        4.08 ms   (-3.92%) |      27   →      27              |      114.53 ms →      110.03 ms   (-3.92%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      969.39 μs →      971.43 μs   (+0.21%) |      27   →      27              |       26.17 ms →       26.23 ms   (+0.21%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.38 ms →        2.22 ms   (-6.98%) |      27   →      27              |       64.32 ms →       59.83 ms   (-6.98%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.46 μs →       64.73 μs   (+0.42%) |      54   →      54              |        3.48 ms →        3.50 ms   (+0.42%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.84 μs →       94.17 μs   (-0.71%) |      27   →      27              |        2.56 ms →        2.54 ms   (-0.71%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.49 μs →       66.80 μs   (+0.46%) |      27   →      27              |        1.80 ms →        1.80 ms   (+0.46%) | 
  │ │ ├ sirius::Band::solve                                             |       10.93 s  →       10.38 s    (-5.00%) |      27   →      27              |      295.11 s  →      280.36 s    (-5.00%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      318.87 μs →      320.24 μs   (+0.43%) |     108   →     108              |       34.44 ms →       34.59 ms   (+0.43%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      313.61 μs →      314.66 μs   (+0.34%) |     108   →     108              |       33.87 ms →       33.98 ms   (+0.34%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.77 μs →        4.00 μs   (+5.97%) |     108   →     108              |      407.68 μs →      432.02 μs   (+5.97%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.73 s  →        2.60 s    (-5.00%) |     108   →     108              |      295.07 s  →      280.32 s    (-5.00%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.27 ms →       12.00 ms   (-2.19%) |     108   →     108              |        1.32 s  →        1.30 s    (-2.19%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      662.80 ns →      594.37 ns  (-10.32%) |     648   →     648              |      429.49 μs →      385.15 μs  (-10.32%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.85 ms   (+0.19%) |     108   →     108              |      198.93 ms →      199.30 ms   (+0.19%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      357.79 μs →      359.13 μs   (+0.38%) |     108   →     108              |       38.64 ms →       38.79 ms   (+0.38%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      551.69 μs →      552.82 μs   (+0.21%) |     216   →     216              |      119.16 ms →      119.41 ms   (+0.21%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.71 s  →        2.57 s    (-5.03%) |     108   →     108              |      292.57 s  →      277.84 s    (-5.03%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.26 ms →       70.70 ms   (+2.09%) |     965   →     932     (-3.42%) |       66.83 s  →       65.90 s    (-1.40%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.23 ms →       45.38 ms   (+2.61%) |     965   →     932     (-3.42%) |       42.68 s  →       42.30 s    (-0.90%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.79 ms →        8.89 ms   (+1.08%) |     965   →     932     (-3.42%) |        8.49 s  →        8.29 s    (-2.37%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      223.89 μs →      229.02 μs   (+2.29%) |     965   →     932     (-3.42%) |      216.06 ms →      213.45 ms   (-1.21%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.98 ms →        1.96 ms   (-1.22%) |     108   →     108              |      214.20 ms →      211.59 ms   (-1.22%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.94 ms →        6.91 ms   (-0.41%) |     965   →     932     (-3.42%) |        6.70 s  →        6.44 s    (-3.81%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       85.62 μs →       87.32 μs   (+1.99%) |     965   →     932     (-3.42%) |       82.62 ms →       81.38 ms   (-1.50%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      742.92 μs →      731.73 μs   (-1.51%) |     108   →     108              |       80.23 ms →       79.03 ms   (-1.51%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.86 ms →       10.01 ms   (+1.52%) |     965   →     932     (-3.42%) |        9.51 s  →        9.33 s    (-1.96%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.30 ms →        6.32 ms   (+0.17%) |     965   →     932     (-3.42%) |        6.08 s  →        5.89 s    (-3.25%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (+0.34%) |     965   →     932     (-3.42%) |        1.47 s  →        1.42 s    (-3.09%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.84 ms →        8.72 ms   (-1.39%) |     965   →     932     (-3.42%) |        8.53 s  →        8.13 s    (-4.76%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.65 ms →        1.24 ms  (-24.53%) |     965   →     932     (-3.42%) |        1.59 s  →        1.16 s   (-27.11%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.32 ms →        7.53 ms   (+2.78%) |    1.93 K →    1.86 K   (-3.42%) |       14.14 s  →       14.03 s    (-0.74%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       30.27 ms →       30.32 ms   (+0.15%) |     965   →     932     (-3.42%) |       29.21 s  →       28.26 s    (-3.27%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.10 ms →        2.00 ms   (-4.65%) |    1.82 K →    1.76 K   (-3.62%) |        3.82 s  →        3.51 s    (-8.11%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       72.15 ns →       44.00 ns  (-39.01%) |    1.82 K →    1.76 K   (-3.62%) |      131.45 μs →       77.27 μs  (-41.22%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.08 ms →        1.99 ms   (-4.47%) |    1.82 K →    1.76 K   (-3.62%) |        3.79 s  →        3.49 s    (-7.93%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       74.82 ns →       49.18 ns  (-34.26%) |    1.82 K →    1.76 K   (-3.62%) |      136.31 μs →       86.36 μs  (-36.64%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      972.65 μs →      964.57 μs   (-0.83%) |     965   →     932     (-3.42%) |      938.61 ms →      898.98 ms   (-4.22%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.55 ms →        1.52 ms   (-1.66%) |     965   →     932     (-3.42%) |        1.49 s  →        1.42 s    (-5.02%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.72 ms →        5.79 ms   (+1.12%) |    3.75 K →    3.62 K   (-3.52%) |       21.47 s  →       20.95 s    (-2.44%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.89 ms →        3.94 ms   (+1.47%) |    5.47 K →    5.27 K   (-3.62%) |       21.24 s  →       20.78 s    (-2.21%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.36 ms →        5.28 ms   (-1.56%) |     965   →     932     (-3.42%) |        5.18 s  →        4.92 s    (-4.92%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.65 ms →        3.53 ms   (-3.29%) |     965   →     932     (-3.42%) |        3.52 s  →        3.29 s    (-6.59%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       48.58 ns →       67.52 ns  (+38.97%) |     965   →     932     (-3.42%) |       46.88 μs →       62.92 μs  (+34.22%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.63 ms →        3.51 ms   (-3.24%) |     965   →     932     (-3.42%) |        3.50 s  →        3.27 s    (-6.55%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       40.63 ns →       69.23 ns  (+70.40%) |     965   →     932     (-3.42%) |       39.21 μs →       64.52 μs  (+64.57%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      172.61 ms →      165.83 ms   (-3.93%) |     965   →     932     (-3.42%) |      166.57 s  →      154.56 s    (-7.21%) | 
  │ │ │ │   ├ sirius::residuals                                         |       11.08 ms →       11.06 ms   (-0.21%) |     939   →     907     (-3.41%) |       10.41 s  →       10.03 s    (-3.61%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.56 ms →       10.58 ms   (+0.21%) |     893   →     861     (-3.58%) |        9.43 s  →        9.11 s    (-3.38%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.23 ms →        5.26 ms   (+0.47%) |    1.79 K →    1.72 K   (-3.58%) |        9.35 s  →        9.06 s    (-3.13%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      666.46 μs →      641.16 μs   (-3.80%) |     893   →     861     (-3.58%) |      595.15 ms →      552.04 ms   (-7.24%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.85 ms →       40.33 ms   (-1.28%) |     351   →     351              |       14.34 s  →       14.16 s    (-1.28%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       24.01 ms →       23.70 ms   (-1.29%) |     594   →     594              |       14.26 s  →       14.08 s    (-1.29%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       16.92 ms →       16.71 ms   (-1.23%) |     837   →     837              |       14.16 s  →       13.99 s    (-1.23%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      548.63 ns →      574.79 ns   (+4.77%) |     108   →     108              |       59.25 μs →       62.08 μs   (+4.77%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.70 μs →       22.57 μs   (-4.80%) |      27   →      27              |      640.01 μs →      609.28 μs   (-4.80%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      596.79 μs →      598.48 μs   (+0.28%) |      27   →      27              |       16.11 ms →       16.16 ms   (+0.28%) | 
  │ │ ├ sirius::Density::generate                                       |      913.27 ms →      891.20 ms   (-2.42%) |      27   →      27              |       24.66 s  →       24.06 s    (-2.42%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      534.55 ms →      523.94 ms   (-1.98%) |      27   →      27              |       14.43 s  →       14.15 s    (-1.98%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.22 ms →       24.44 ms   (-3.09%) |     108   →     108              |        2.72 s  →        2.64 s    (-3.09%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.59 μs →        6.16 μs  (+10.15%) |     108   →     108              |      603.84 μs →      665.16 μs  (+10.15%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.52 μs →       12.41 μs   (-0.89%) |       8   →       8              |      100.16 μs →       99.27 μs   (-0.89%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       21.09 ms →       20.34 ms   (-3.59%) |     108   →     108              |        2.28 s  →        2.20 s    (-3.59%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       31.05 ms →       29.81 ms   (-4.00%) |     108   →     108              |        3.35 s  →        3.22 s    (-4.00%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.04 μs →       11.47 μs   (+3.96%) |     108   →     108              |        1.19 ms →        1.24 ms   (+3.96%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.30%) |     108   →     108              |      157.68 ms →      158.15 ms   (+0.30%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       29.11 ms →       27.86 ms   (-4.31%) |     108   →     108              |        3.14 s  →        3.01 s    (-4.31%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.97 ms →        3.72 ms  (-25.13%) |     108   →     108              |      537.11 ms →      402.14 ms  (-25.13%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      541.81 ns →      514.92 ns   (-4.96%) |     108   →     108              |       58.52 μs →       55.61 μs   (-4.96%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.63 ms →       42.43 ms   (-0.48%) |     108   →     108              |        4.60 s  →        4.58 s    (-0.48%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.34%) |      27   →      27              |       44.15 ms →       44.30 ms   (+0.34%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.85 ms →       88.83 ms   (-0.02%) |      27   →      27              |        2.40 s  →        2.40 s    (-0.02%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.62 ms →       88.60 ms   (-0.02%) |      27   →      27              |        2.39 s  →        2.39 s    (-0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      281.46 ms →      272.51 ms   (-3.18%) |      27   →      27              |        7.60 s  →        7.36 s    (-3.18%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      281.46 ms →      272.50 ms   (-3.18%) |      27   →      27              |        7.60 s  →        7.36 s    (-3.18%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       30.02 ms →       24.54 ms  (-18.26%) |      27   →      27              |      810.56 ms →      662.55 ms  (-18.26%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      224.36 ms →      221.56 ms   (-1.25%) |      27   →      27              |        6.06 s  →        5.98 s    (-1.25%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       25.31 ms →       24.65 ms   (-2.63%) |      27   →      27              |      683.49 ms →      665.54 ms   (-2.63%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.17 ms →       80.96 ms   (-1.48%) |      27   →      27              |        2.22 s  →        2.19 s    (-1.48%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       11.49 ms →       10.21 ms  (-11.14%) |      27   →      27              |      310.17 ms →      275.62 ms  (-11.14%) | 
  │ │ ├ sirius::Density::mix                                            |      209.89 ms →      220.10 ms   (+4.87%) |      27   →      27              |        5.67 s  →        5.94 s    (+4.87%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      955.16 μs →      916.45 μs   (-4.05%) |      27   →      27              |       25.79 ms →       24.74 ms   (-4.05%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.44 ms →       10.40 ms   (-0.36%) |     335   →     464    (+38.51%) |        3.50 s  →        4.82 s   (+38.02%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.97 ms →       10.06 ms   (+0.87%) |     335   →     464    (+38.51%) |        3.34 s  →        4.67 s   (+39.71%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.97 ms →       10.06 ms   (+0.86%) |     335   →     464    (+38.51%) |        3.34 s  →        4.67 s   (+39.71%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        8.11 ms →        6.66 ms  (-17.81%) |      27   →      27              |      218.88 ms →      179.90 ms  (-17.81%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.28 ms →        5.75 ms  (-20.97%) |      27   →      27              |      196.45 ms →      155.26 ms  (-20.97%) | 
  │ │ ├ sirius::Potential::generate                                     |      568.86 ms →      584.04 ms   (+2.67%) |      27   →      27              |       15.36 s  →       15.77 s    (+2.67%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.43 ms →      138.50 ms   (+9.54%) |      27   →      27              |        3.41 s  →        3.74 s    (+9.54%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.34 ms →       18.37 ms (+150.42%) |      27   →      27              |      198.07 ms →      496.00 ms (+150.42%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.38 ms →       10.10 ms   (-2.69%) |      27   →      27              |      280.28 ms →      272.74 ms   (-2.69%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.05 ms →        9.86 ms   (-1.91%) |      27   →      27              |      271.43 ms →      266.23 ms   (-1.91%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.05 ms →        9.86 ms   (-1.91%) |      27   →      27              |      271.41 ms →      266.22 ms   (-1.91%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      566.82 μs →      553.38 μs   (-2.37%) |      54   →      54              |       30.61 ms →       29.88 ms   (-2.37%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.28 ms →       48.86 ms   (-0.86%) |      27   →      27              |        1.33 s  →        1.32 s    (-0.86%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.95 ms →       46.50 ms   (-0.96%) |      27   →      27              |        1.27 s  →        1.26 s    (-0.96%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        3.02 ms   (-0.44%) |      54   →      54              |      163.67 ms →      162.95 ms   (-0.44%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.37 ms →        5.32 ms   (-1.02%) |      27   →      27              |      145.11 ms →      143.63 ms   (-1.02%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.72 ms →        6.75 ms   (+0.41%) |      27   →      27              |      181.49 ms →      182.25 ms   (+0.41%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.01 ms →       90.83 ms   (-0.20%) |      27   →      27              |        2.46 s  →        2.45 s    (-0.20%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.00 ms →      296.72 ms   (+1.27%) |      27   →      27              |        7.91 s  →        8.01 s    (+1.27%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      285.96 ms →      277.65 ms   (-2.90%) |      27   →      27              |        7.72 s  →        7.50 s    (-2.90%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      285.96 ms →      277.65 ms   (-2.90%) |      27   →      27              |        7.72 s  →        7.50 s    (-2.90%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.79 ms →       27.15 ms  (-17.21%) |      27   →      27              |      885.27 ms →      732.96 ms  (-17.21%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.17 ms →      222.59 ms   (-1.15%) |      27   →      27              |        6.08 s  →        6.01 s    (-1.15%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.21 ms →       24.10 ms   (-0.45%) |      27   →      27              |      653.58 ms →      650.65 ms   (-0.45%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       12.10 ms →        5.70 ms  (-52.87%) |      27   →      27              |      326.70 ms →      153.96 ms  (-52.87%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.71 ms →       10.72 ms   (+0.13%) |     189   →     189              |        2.02 s  →        2.03 s    (+0.13%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.28 ms →       10.28 ms   (-0.01%) |     189   →     189              |        1.94 s  →        1.94 s    (-0.01%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.28 ms →       10.28 ms   (-0.01%) |     189   →     189              |        1.94 s  →        1.94 s    (-0.01%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.19 ms →       10.18 ms   (-0.14%) |      81   →      81              |      825.36 ms →      824.20 ms   (-0.14%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.81 ms →        9.76 ms   (-0.49%) |      81   →      81              |      794.32 ms →      790.47 ms   (-0.49%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.01 ms →       10.03 ms   (+0.16%) |      27   →      27              |      270.26 ms →      270.69 ms   (+0.16%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      177.22 μs →      113.75 μs  (-35.81%) |      27   →      27              |        4.78 ms →        3.07 ms  (-35.81%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      172.53 μs →      108.83 μs  (-36.92%) |      27   →      27              |        4.66 ms →        2.94 ms  (-36.92%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.32 ms →        5.19 ms   (-2.42%) |       2   →       2              |       10.63 ms →       10.37 ms   (-2.42%) | 
- │ ├ sirius::Periodic_function|inner                                   |       10.11 ms →       11.24 ms  (+11.20%) |       6   →       6              |       60.64 ms →       67.43 ms  (+11.20%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.08 ms →       10.29 ms   (+2.08%) |       6   →       6              |       60.50 ms →       61.76 ms   (+2.08%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.08 ms →       10.29 ms   (+2.08%) |       6   →       6              |       60.49 ms →       61.75 ms   (+2.08%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |        9.67 ms →       10.65 ms  (+10.09%) |       3   →       3              |       29.02 ms →       31.95 ms  (+10.09%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.63 ms →        9.96 ms   (+3.46%) |       3   →       3              |       28.88 ms →       29.88 ms   (+3.46%) | 
  ├ sirius::Periodic_function|inner                                     |       10.27 ms →       10.41 ms   (+1.39%) |       2   →       2              |       20.54 ms →       20.83 ms   (+1.39%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.26 ms →       10.17 ms   (-0.88%) |       2   →       2              |       20.53 ms →       20.35 ms   (-0.88%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.26 ms →       10.17 ms   (-0.88%) |       2   →       2              |       20.53 ms →       20.35 ms   (-0.88%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.65 ms →        9.71 ms   (-8.88%) |       1   →       1              |       10.65 ms →        9.71 ms   (-8.88%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.67 ms →        9.68 ms   (+0.10%) |       1   →       1              |        9.67 ms →        9.68 ms   (+0.10%) | 
  └ sirius::finalize                                                    |      343.98 ms →      340.53 ms   (-1.00%) |       1   →       1              |      343.98 ms →      340.53 ms   (-1.00%) | 
  ====================================================================================================================================================================================================
```
