# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs acded4f8dc8bf829fcf788e7dbd08a23ea769390
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      346.11 s  →      401.00 s   (+15.86%) |       1   →       1              |      346.11 s  →      401.00 s   (+15.86%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.69 s    (-0.69%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.69%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        2.96 s    (-0.52%) |       1   →       1              |        2.97 s  →        2.96 s    (-0.52%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       55.77 ms →       54.91 ms   (-1.56%) |       1   →       1              |       55.77 ms →       54.91 ms   (-1.56%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      149.38 ms →      135.25 ms   (-9.46%) |       1   →       1              |      149.38 ms →      135.25 ms   (-9.46%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       63.43 ms →       55.83 ms  (-11.98%) |       2   →       2              |      126.85 ms →      111.65 ms  (-11.98%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.45 ms →       23.53 ms   (+4.78%) |       1   →       1              |       22.45 ms →       23.53 ms   (+4.78%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.33 ms →        6.22 ms   (-1.70%) |       1   →       1              |        6.33 ms →        6.22 ms   (-1.70%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.08 ms →       17.26 ms   (+7.36%) |       1   →       1              |       16.08 ms →       17.26 ms   (+7.36%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.06 ms →       17.24 ms   (+7.37%) |       1   →       1              |       16.06 ms →       17.24 ms   (+7.37%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.15 ms   (+0.28%) |       1   →       1              |        4.14 ms →        4.15 ms   (+0.28%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (+0.20%) |       1   →       1              |        2.34 ms →        2.34 ms   (+0.20%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.53 μs →      101.89 μs   (-3.44%) |       1   →       1              |      105.53 μs →      101.89 μs   (-3.44%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.72 s    (-0.16%) |       1   →       1              |        2.72 s  →        2.72 s    (-0.16%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.78 ms →       10.87 ms   (+0.84%) |       1   →       1              |       10.78 ms →       10.87 ms   (+0.84%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.34 ms →        4.46 ms   (+2.62%) |       1   →       1              |        4.34 ms →        4.46 ms   (+2.62%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.40 ms →        6.38 ms   (-0.33%) |       1   →       1              |        6.40 ms →        6.38 ms   (-0.33%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.38 ms →        6.36 ms   (-0.33%) |       1   →       1              |        6.38 ms →        6.36 ms   (-0.33%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.87 ms   (-0.42%) |       1   →       1              |        3.89 ms →        3.87 ms   (-0.42%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (-0.18%) |       1   →       1              |        2.32 ms →        2.32 ms   (-0.18%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.87 μs →       99.80 μs   (-1.06%) |       1   →       1              |      100.87 μs →       99.80 μs   (-1.06%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.22 ms →       64.21 ms   (-0.02%) |       2   →       2              |      128.43 ms →      128.41 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.14 ms   (+0.21%) |       2   →       2              |       10.26 ms →       10.28 ms   (+0.21%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.51 ms   (+0.72%) |       1   →       1              |        4.48 ms →        4.51 ms   (+0.72%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.75 ms →       21.74 ms   (-0.06%) |       2   →       2              |       43.50 ms →       43.47 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       15.43 ms   (+4.15%) |       2   →       2              |       29.63 ms →       30.86 ms   (+4.15%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.81 ms →       19.73 ms   (-0.40%) |       4   →       4              |       79.23 ms →       78.92 ms   (-0.40%) | 
  │   ├ sddk::Gvec::init                                                |      172.78 ms →      171.84 ms   (-0.55%) |       2   →       2              |      345.57 ms →      343.67 ms   (-0.55%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.64 ms →      129.92 ms   (+0.21%) |       2   →       2              |      259.28 ms →      259.83 ms   (+0.21%) | 
  │   ├ sddk::Gvec_shells                                               |      180.04 ms →      163.00 ms   (-9.47%) |       1   →       1              |      180.04 ms →      163.00 ms   (-9.47%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.33 ms   (+1.95%) |       1   →       1              |        1.31 ms →        1.33 ms   (+1.95%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      296.14 ms →      296.19 ms   (+0.02%) |       2   →       2              |      592.28 ms →      592.37 ms   (+0.02%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.13 ms →       75.23 ms   (-1.18%) |       1   →       1              |       76.13 ms →       75.23 ms   (-1.18%) | 
  │ ├ sirius::K_point::K_point                                          |        2.54 μs →        2.56 μs   (+0.84%) |       4   →       4              |       10.16 μs →       10.25 μs   (+0.84%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.02 ms →       75.11 ms   (-1.20%) |       1   →       1              |       76.02 ms →       75.11 ms   (-1.20%) | 
  │   └ sirius::K_point::initialize                                     |       18.98 ms →       18.76 ms   (-1.20%) |       4   →       4              |       75.93 ms →       75.02 ms   (-1.20%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.32 ms →       14.09 ms   (-1.58%) |       4   →       4              |       57.28 ms →       56.37 ms   (-1.58%) | 
  │     │ └ sddk::Gvec::init                                            |        3.94 ms →        3.97 ms   (+0.97%) |       4   →       4              |       15.74 ms →       15.90 ms   (+0.97%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.85 μs →        9.18 μs   (+3.64%) |       4   →       4              |       35.41 μs →       36.70 μs   (+3.64%) | 
  │     └ sirius::K_point::update                                       |        3.34 ms →        3.34 ms   (-0.03%) |       4   →       4              |       13.37 ms →       13.37 ms   (-0.03%) | 
  │       └ sirius::Beta_projectors                                     |        1.79 ms →        1.77 ms   (-0.71%) |       4   →       4              |        7.14 ms →        7.09 ms   (-0.71%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      925.76 μs →      916.10 μs   (-1.04%) |       4   →       4              |        3.70 ms →        3.66 ms   (-1.04%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.37 ms   (+1.20%) |       2   →       2              |       10.62 ms →       10.75 ms   (+1.20%) | 
  ├ sirius::Potential                                                   |      158.65 ms →      155.12 ms   (-2.23%) |       1   →       1              |      158.65 ms →      155.12 ms   (-2.23%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.79 ms   (-0.34%) |       6   →       6              |       34.84 ms →       34.73 ms   (-0.34%) | 
  │ └ sirius::Potential::update                                         |      123.07 ms →      119.67 ms   (-2.76%) |       1   →       1              |      123.07 ms →      119.67 ms   (-2.76%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.33 ms →      118.94 ms   (-2.78%) |       1   →       1              |      122.33 ms →      118.94 ms   (-2.78%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      115.07 ms →      110.89 ms   (-3.63%) |       1   →       1              |      115.07 ms →      110.89 ms   (-3.63%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.39 ms →        7.17 ms  (+12.34%) |       1   →       1              |        6.39 ms →        7.17 ms  (+12.34%) | 
  ├ sirius::Density                                                     |      134.20 ms →      129.75 ms   (-3.32%) |       1   →       1              |      134.20 ms →      129.75 ms   (-3.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms →        5.17 ms   (-1.30%) |       2   →       2              |       10.47 ms →       10.34 ms   (-1.30%) | 
  │ └ sirius::Density::update                                           |      123.46 ms →      119.15 ms   (-3.49%) |       1   →       1              |      123.46 ms →      119.15 ms   (-3.49%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      122.97 ms →      118.72 ms   (-3.45%) |       1   →       1              |      122.97 ms →      118.72 ms   (-3.45%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.44 μs →      103.44 μs   (-1.90%) |       1   →       1              |      105.44 μs →      103.44 μs   (-1.90%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      117.34 ms →      112.11 ms   (-4.46%) |       1   →       1              |      117.34 ms →      112.11 ms   (-4.46%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.07 ms →        6.06 ms  (+19.46%) |       1   →       1              |        5.07 ms →        6.06 ms  (+19.46%) | 
  ├ sirius::Density::initial_density                                    |      174.38 ms →      165.47 ms   (-5.11%) |       1   →       1              |      174.38 ms →      165.47 ms   (-5.11%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.27 ms →      111.23 ms   (-9.03%) |       1   →       1              |      122.27 ms →      111.23 ms   (-9.03%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.97 ms →        5.76 ms  (+15.84%) |       2   →       2              |        9.94 ms →       11.52 ms  (+15.84%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.12 ms →        9.91 ms   (-2.06%) |       1   →       1              |       10.12 ms →        9.91 ms   (-2.06%) | 
  ├ sirius::Potential::generate                                         |      592.32 ms →      582.28 ms   (-1.70%) |       1   →       1              |      592.32 ms →      582.28 ms   (-1.70%) | 
  │ ├ sirius::Potential::poisson                                        |      137.91 ms →      126.91 ms   (-7.98%) |       1   →       1              |      137.91 ms →      126.91 ms   (-7.98%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.27 ms →        5.94 ms  (+12.73%) |       1   →       1              |        5.27 ms →        5.94 ms  (+12.73%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.86 ms →       10.57 ms   (-2.70%) |       1   →       1              |       10.86 ms →       10.57 ms   (-2.70%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.84 ms →       10.24 ms   (-5.57%) |       1   →       1              |       10.84 ms →       10.24 ms   (-5.57%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.84 ms →       10.24 ms   (-5.57%) |       1   →       1              |       10.84 ms →       10.24 ms   (-5.57%) | 
  │ ├ sirius::Periodic_function::add                                    |      557.75 μs →      548.53 μs   (-1.65%) |       2   →       2              |        1.12 ms →        1.10 ms   (-1.65%) | 
  │ ├ sirius::Potential::xc                                             |       53.79 ms →       54.64 ms   (+1.57%) |       1   →       1              |       53.79 ms →       54.64 ms   (+1.57%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.41 ms →       52.27 ms   (+1.68%) |       1   →       1              |       51.41 ms →       52.27 ms   (+1.68%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.71 ms →        5.65 ms   (-1.12%) |       2   →       2              |       11.42 ms →       11.29 ms   (-1.12%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.33 ms →        5.38 ms   (+1.00%) |       1   →       1              |        5.33 ms →        5.38 ms   (+1.00%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.92 ms →        5.86 ms   (-1.03%) |       1   →       1              |        5.92 ms →        5.86 ms   (-1.03%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.60 ms →       92.61 ms   (+0.01%) |       1   →       1              |       92.60 ms →       92.61 ms   (+0.01%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.62 ms →      299.80 ms   (+0.06%) |       1   →       1              |      299.62 ms →      299.80 ms   (+0.06%) | 
  ├ sirius::Hamiltonian0                                                |        8.42 ms →        8.75 ms   (+3.91%) |       1   →       1              |        8.42 ms →        8.75 ms   (+3.91%) | 
  │ ├ sirius::Local_operator                                            |        8.08 ms →        8.40 ms   (+4.06%) |       1   →       1              |        8.08 ms →        8.40 ms   (+4.06%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms →        4.73 ms   (-0.07%) |       1   →       1              |        4.73 ms →        4.73 ms   (-0.07%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        2.76 ms  (+13.73%) |       1   →       1              |        2.43 ms →        2.76 ms  (+13.73%) | 
  │ ├ sirius::Non_local_operator                                        |       63.03 μs →       61.75 μs   (-2.03%) |       2   →       2              |      126.06 μs →      123.51 μs   (-2.03%) | 
  │ ├ sirius::D_operator::initialize                                    |       95.54 μs →       97.80 μs   (+2.36%) |       1   →       1              |       95.54 μs →       97.80 μs   (+2.36%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.65 μs →       69.73 μs   (+0.11%) |       1   →       1              |       69.65 μs →       69.73 μs   (+0.11%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.12 s  →        4.18 s    (+1.31%) |       1   →       1              |        4.12 s  →        4.18 s    (+1.31%) | 
  │ ├ sirius::Hamiltonian_k                                             |      374.03 μs →      372.52 μs   (-0.40%) |       4   →       4              |        1.50 ms →        1.49 ms   (-0.40%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      369.14 μs →      367.73 μs   (-0.38%) |       4   →       4              |        1.48 ms →        1.47 ms   (-0.38%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.11 μs →        2.99 μs   (-3.77%) |       4   →       4              |       12.45 μs →       11.98 μs   (-3.77%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.03 s  →        1.04 s    (+1.31%) |       4   →       4              |        4.12 s  →        4.18 s    (+1.31%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       33.27 ms →       33.12 ms   (-0.47%) |      16   →      16              |      532.38 ms →      529.87 ms   (-0.47%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.67 ms →       14.57 ms   (-0.67%) |       4   →       4              |       58.68 ms →       58.28 ms   (-0.67%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.41 ms →        5.29 ms   (-2.16%) |       4   →       4              |       21.63 ms →       21.16 ms   (-2.16%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.39 ms →      356.75 ms   (+0.67%) |       4   →       4              |        1.42 s  →        1.43 s    (+0.67%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      258.00 ms →      259.62 ms   (+0.63%) |       4   →       4              |        1.03 s  →        1.04 s    (+0.63%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.23 ms →       63.14 ms   (-0.14%) |       4   →       4              |      252.91 ms →      252.56 ms   (-0.14%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.81 ms →       16.74 ms   (-0.40%) |       4   →       4              |       67.24 ms →       66.97 ms   (-0.40%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.81 ms →       16.74 ms   (-0.40%) |       4   →       4              |       67.23 ms →       66.96 ms   (-0.40%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       39.98 ms →       39.87 ms   (-0.29%) |       4   →       4              |      159.92 ms →      159.46 ms   (-0.29%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.64 ms →       16.60 ms   (-0.20%) |       4   →       4              |       66.55 ms →       66.42 ms   (-0.20%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.64 ms →       16.60 ms   (-0.21%) |       4   →       4              |       66.54 ms →       66.40 ms   (-0.21%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.12 ms →       55.88 ms   (+3.24%) |       4   →       4              |      216.49 ms →      223.50 ms   (+3.24%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.12 ms →       37.85 ms   (+4.79%) |       4   →       4              |      144.49 ms →      151.41 ms   (+4.79%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.91 ms   (-2.26%) |       4   →       4              |        7.81 ms →        7.64 ms   (-2.26%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.22 ms →       40.79 ms   (+1.42%) |       4   →       4              |      160.88 ms →      163.17 ms   (+1.42%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.12 ms →        7.66 ms   (+7.57%) |       4   →       4              |       28.47 ms →       30.62 ms   (+7.57%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.20 ms   (+0.40%) |       8   →       8              |      216.73 ms →      217.59 ms   (+0.40%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.77 ms →       15.58 ms   (+5.50%) |       8   →       8              |      118.17 ms →      124.67 ms   (+5.50%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.73 ms →       15.54 ms   (+5.54%) |       8   →       8              |      117.80 ms →      124.33 ms   (+5.54%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       33.38 ns →       20.62 ns  (-38.20%) |       8   →       8              |      267.00 ns →      165.00 ns  (-38.20%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.52 ms →       15.35 ms   (+5.70%) |       8   →       8              |      116.20 ms →      122.82 ms   (+5.70%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.75 ns →       30.25 ns  (+32.97%) |       8   →       8              |      182.00 ns →      242.00 ns  (+32.97%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      368.61 ms →      382.66 ms   (+3.81%) |       4   →       4              |        1.47 s  →        1.53 s    (+3.81%) | 
  │ │ └ sddk::wf_trans                                                  |       26.68 ms →       26.68 ms   (+0.00%) |       4   →       4              |      106.72 ms →      106.72 ms   (+0.00%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.46 ms →       26.57 ms   (+0.43%) |       4   →       4              |      105.84 ms →      106.29 ms   (+0.43%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      401.25 ns →      421.25 ns   (+4.98%) |       4   →       4              |        1.60 μs →        1.69 μs   (+4.98%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      334.33 s  →      389.19 s   (+16.41%) |       1   →       1              |      334.33 s  →      389.19 s   (+16.41%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.89 ms →        5.85 ms   (-0.76%) |      19   →      83   (+336.84%) |      111.96 ms →      485.39 ms (+333.53%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       12.84 s  →       12.13 s    (-5.52%) |      26   →      32    (+23.08%) |      333.90 s  →      388.25 s   (+16.28%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.46 ms →        4.67 ms   (+4.58%) |      26   →      32    (+23.08%) |      115.98 ms →      149.29 ms  (+28.71%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.10 ms →        4.31 ms   (+4.99%) |      26   →      32    (+23.08%) |      106.67 ms →      137.84 ms  (+29.21%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      983.40 μs →      974.45 μs   (-0.91%) |      26   →      32    (+23.08%) |       25.57 ms →       31.18 ms  (+21.96%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.23 ms →        2.43 ms   (+9.07%) |      26   →      32    (+23.08%) |       57.98 ms →       77.83 ms  (+34.23%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       64.49 μs →       64.51 μs   (+0.03%) |      52   →      64    (+23.08%) |        3.35 ms →        4.13 ms  (+23.12%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       94.85 μs →       94.38 μs   (-0.50%) |      26   →      32    (+23.08%) |        2.47 ms →        3.02 ms  (+22.47%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       65.76 μs →       66.02 μs   (+0.38%) |      26   →      32    (+23.08%) |        1.71 ms →        2.11 ms  (+23.55%) | 
- │ │ ├ sirius::Band::solve                                             |       10.73 s  →        9.70 s    (-9.58%) |      26   →      32    (+23.08%) |      278.96 s  →      310.44 s   (+11.28%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      316.03 μs →      345.12 μs   (+9.21%) |     104   →     128    (+23.08%) |       32.87 ms →       44.18 ms  (+34.41%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      310.85 μs →      339.52 μs   (+9.22%) |     104   →     128    (+23.08%) |       32.33 ms →       43.46 ms  (+34.43%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.86 μs →        4.11 μs   (+6.37%) |     104   →     128    (+23.08%) |      401.68 μs →      525.88 μs  (+30.92%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.68 s  →        2.42 s    (-9.58%) |     104   →     128    (+23.08%) |      278.93 s  →      310.39 s   (+11.28%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.16 ms →       12.38 ms   (+1.79%) |     104   →     128    (+23.08%) |        1.26 s  →        1.58 s   (+25.27%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      616.79 ns →      667.89 ns   (+8.28%) |     624   →     768    (+23.08%) |      384.88 μs →      512.94 μs  (+33.27%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.84 ms   (-0.09%) |     104   →     128    (+23.08%) |      191.36 ms →      235.29 ms  (+22.96%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      356.99 μs →      356.51 μs   (-0.14%) |     104   →     128    (+23.08%) |       37.13 ms →       45.63 ms  (+22.91%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.96 μs →      549.51 μs   (-0.26%) |     208   →     256    (+23.08%) |      114.60 ms →      140.68 ms  (+22.75%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.66 s  →        2.40 s    (-9.67%) |     104   →     128    (+23.08%) |      276.52 s  →      307.41 s   (+11.17%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.86 ms →       72.96 ms   (+5.96%) |     943   →     985     (+4.45%) |       64.93 s  →       71.87 s   (+10.68%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.09 ms →       46.89 ms   (+6.34%) |     943   →     985     (+4.45%) |       41.58 s  →       46.19 s   (+11.08%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.66 ms →        9.28 ms   (+7.15%) |     943   →     985     (+4.45%) |        8.16 s  →        9.14 s   (+11.93%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      229.74 μs →      222.25 μs   (-3.26%) |     943   →     985     (+4.45%) |      216.65 ms →      218.92 ms   (+1.05%) | 
+ │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.06 ms →        1.69 ms  (-17.93%) |     104   →     128    (+23.08%) |      214.75 ms →      216.92 ms   (+1.01%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.73 ms →        7.31 ms   (+8.61%) |     943   →     985     (+4.45%) |        6.35 s  →        7.20 s   (+13.44%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       87.74 μs →       82.78 μs   (-5.64%) |     943   →     985     (+4.45%) |       82.73 ms →       81.54 ms   (-1.44%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      773.25 μs →      618.14 μs  (-20.06%) |     104   →     128    (+23.08%) |       80.42 ms →       79.12 ms   (-1.61%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.68 ms →       10.49 ms   (+8.33%) |     943   →     985     (+4.45%) |        9.13 s  →       10.33 s   (+13.16%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.09 ms →        6.71 ms  (+10.22%) |     943   →     985     (+4.45%) |        5.74 s  →        6.61 s   (+15.13%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.48 ms   (-2.10%) |     943   →     985     (+4.45%) |        1.43 s  →        1.46 s    (+2.26%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.49 ms →        9.27 ms   (+9.15%) |     943   →     985     (+4.45%) |        8.00 s  →        9.13 s   (+14.01%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.22 ms →        1.68 ms  (+36.98%) |     943   →     985     (+4.45%) |        1.15 s  →        1.65 s   (+43.08%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.37 ms →        7.65 ms   (+3.84%) |    1.89 K →    1.97 K   (+4.45%) |       13.90 s  →       15.07 s    (+8.46%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       29.59 ms →       31.18 ms   (+5.36%) |     943   →     985     (+4.45%) |       27.91 s  →       30.71 s   (+10.05%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.94 ms →        2.11 ms   (+9.27%) |    1.78 K →    1.84 K   (+3.37%) |        3.45 s  →        3.90 s   (+12.95%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       80.92 ns →       67.42 ns  (-16.68%) |    1.78 K →    1.84 K   (+3.37%) |      144.19 μs →      124.19 μs  (-13.87%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.93 ms →        2.10 ms   (+9.01%) |    1.78 K →    1.84 K   (+3.37%) |        3.44 s  →        3.87 s   (+12.68%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       72.80 ns →       77.99 ns   (+7.14%) |    1.78 K →    1.84 K   (+3.37%) |      129.72 μs →      143.66 μs  (+10.75%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      965.34 μs →        1.03 ms   (+6.27%) |     943   →     985     (+4.45%) |      910.31 ms →        1.01 s   (+11.01%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.43 ms →        1.68 ms  (+16.83%) |     943   →     985     (+4.45%) |        1.35 s  →        1.65 s   (+22.03%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.65 ms →        5.91 ms   (+4.58%) |    3.67 K →    3.81 K   (+3.93%) |       20.73 s  →       22.53 s    (+8.68%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.84 ms →        4.04 ms   (+5.15%) |    5.35 K →    5.53 K   (+3.37%) |       20.52 s  →       22.31 s    (+8.69%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.24 ms →        5.38 ms   (+2.64%) |     943   →     985     (+4.45%) |        4.94 s  →        5.30 s    (+7.21%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.49 ms →        3.67 ms   (+5.00%) |     943   →     985     (+4.45%) |        3.29 s  →        3.61 s    (+9.68%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       65.01 ns →       46.66 ns  (-28.23%) |     943   →     985     (+4.45%) |       61.30 μs →       45.96 μs  (-25.03%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.48 ms →        3.65 ms   (+4.88%) |     943   →     985     (+4.45%) |        3.28 s  →        3.59 s    (+9.55%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       67.13 ns →       67.37 ns   (+0.36%) |     943   →     985     (+4.45%) |       63.30 μs →       66.36 μs   (+4.83%) | 
- │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      164.02 ms →      176.22 ms   (+7.44%) |     943   →     985     (+4.45%) |      154.67 s  →      173.58 s   (+12.22%) | 
- │ │ │ │   ├ sirius::residuals                                         |       10.86 ms →       11.85 ms   (+9.13%) |     918   →     958     (+4.36%) |        9.97 s  →       11.35 s   (+13.89%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |       10.43 ms →       11.25 ms   (+7.94%) |     872   →     917     (+5.16%) |        9.09 s  →       10.32 s   (+13.51%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.18 ms →        5.58 ms   (+7.91%) |    1.74 K →    1.83 K   (+5.16%) |        9.03 s  →       10.24 s   (+13.48%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      633.38 μs →      701.81 μs  (+10.80%) |     872   →     917     (+5.16%) |      552.30 ms →      643.56 ms  (+16.52%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       41.26 ms →       39.80 ms   (-3.54%) |     341   →     366     (+7.33%) |       14.07 s  →       14.57 s    (+3.54%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       24.21 ms →       24.00 ms   (-0.90%) |     578   →     604     (+4.50%) |       14.00 s  →       14.49 s    (+3.56%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       17.04 ms →       17.10 ms   (+0.39%) |     815   →     842     (+3.31%) |       13.88 s  →       14.40 s    (+3.71%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      577.81 ns →      545.15 ns   (-5.65%) |     104   →     128    (+23.08%) |       60.09 μs →       69.78 μs  (+16.12%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.38 μs →       23.18 μs   (-0.88%) |      26   →      32    (+23.08%) |      608.00 μs →      741.70 μs  (+21.99%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      599.27 μs →      593.74 μs   (-0.92%) |      26   →      32    (+23.08%) |       15.58 ms →       19.00 ms  (+21.94%) | 
- │ │ ├ sirius::Density::generate                                       |      904.26 ms →      904.00 ms   (-0.03%) |      26   →      32    (+23.08%) |       23.51 s  →       28.93 s   (+23.04%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      526.82 ms →      530.11 ms   (+0.62%) |      26   →      32    (+23.08%) |       13.70 s  →       16.96 s   (+23.84%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.81 ms →       24.94 ms   (+0.52%) |     104   →     128    (+23.08%) |        2.58 s  →        3.19 s   (+23.71%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.76 μs →        5.83 μs   (+1.20%) |     104   →     128    (+23.08%) |      599.18 μs →      746.29 μs  (+24.55%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.99 μs →       12.27 μs   (-5.60%) |       8   →       8              |      103.96 μs →       98.14 μs   (-5.60%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.69 ms →       20.83 ms   (+0.68%) |     104   →     128    (+23.08%) |        2.15 s  →        2.67 s   (+23.91%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.75 ms →       30.46 ms   (+2.37%) |     104   →     128    (+23.08%) |        3.09 s  →        3.90 s   (+25.99%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.39 μs →       11.34 μs   (-0.45%) |     104   →     128    (+23.08%) |        1.18 ms →        1.45 ms  (+22.53%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.41 ms   (-3.27%) |     104   →     128    (+23.08%) |      151.72 ms →      180.62 ms  (+19.05%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.80 ms →       28.56 ms   (+2.71%) |     104   →     128    (+23.08%) |        2.89 s  →        3.66 s   (+26.41%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.67 ms →        4.41 ms  (+20.20%) |     104   →     128    (+23.08%) |      381.41 ms →      564.23 ms  (+47.93%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      651.30 ns →      642.53 ns   (-1.35%) |     104   →     128    (+23.08%) |       67.73 μs →       82.24 μs  (+21.42%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.62 ms →       42.34 ms   (-0.65%) |     104   →     128    (+23.08%) |        4.43 s  →        5.42 s   (+22.28%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.43%) |      26   →      32    (+23.08%) |       42.73 ms →       52.81 ms  (+23.60%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       88.93 ms →       88.74 ms   (-0.22%) |      26   →      32    (+23.08%) |        2.31 s  →        2.84 s   (+22.81%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.70 ms →       88.51 ms   (-0.20%) |      26   →      32    (+23.08%) |        2.31 s  →        2.83 s   (+22.82%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      284.30 ms →      279.80 ms   (-1.59%) |      26   →      32    (+23.08%) |        7.39 s  →        8.95 s   (+21.13%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      284.30 ms →      279.79 ms   (-1.59%) |      26   →      32    (+23.08%) |        7.39 s  →        8.95 s   (+21.13%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.49 ms →       24.53 ms   (+0.17%) |      26   →      32    (+23.08%) |      636.63 ms →      784.90 ms  (+23.29%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      233.54 ms →      229.29 ms   (-1.82%) |      26   →      32    (+23.08%) |        6.07 s  →        7.34 s   (+20.84%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.46 ms →       24.23 ms   (-0.92%) |      26   →      32    (+23.08%) |      635.93 ms →      775.46 ms  (+21.94%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.40 ms →       81.43 ms   (-1.17%) |      26   →      32    (+23.08%) |        2.14 s  →        2.61 s   (+21.63%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.12 ms →        9.03 ms  (+26.78%) |      26   →      32    (+23.08%) |      185.09 ms →      288.81 ms  (+56.04%) | 
- │ │ ├ sirius::Density::mix                                            |      215.47 ms →      546.93 ms (+153.83%) |      26   →      32    (+23.08%) |        5.60 s  →       17.50 s  (+212.41%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      930.04 μs →      914.60 μs   (-1.66%) |      26   →      32    (+23.08%) |       24.18 ms →       29.27 ms  (+21.03%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.34 ms →       10.32 ms   (-0.25%) |     334   →    1.49 K (+345.81%) |        3.46 s  →       15.36 s  (+344.69%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.03 ms →        9.96 ms   (-0.79%) |     334   →    1.49 K (+345.81%) |        3.35 s  →       14.82 s  (+342.29%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.03 ms →        9.96 ms   (-0.79%) |     334   →    1.49 K (+345.81%) |        3.35 s  →       14.82 s  (+342.29%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        8.18 ms →        6.64 ms  (-18.80%) |      26   →      32    (+23.08%) |      212.77 ms →      212.63 ms   (-0.06%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.32 ms →        5.60 ms  (-23.56%) |      26   →      32    (+23.08%) |      190.43 ms →      179.16 ms   (-5.92%) | 
- │ │ ├ sirius::Potential::generate                                     |      578.95 ms →      568.42 ms   (-1.82%) |      26   →      32    (+23.08%) |       15.05 s  →       18.19 s   (+20.84%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      136.92 ms →      126.47 ms   (-7.63%) |      26   →      32    (+23.08%) |        3.56 s  →        4.05 s   (+13.68%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.21 ms →        6.36 ms  (+22.10%) |      26   →      32    (+23.08%) |      135.47 ms →      203.57 ms  (+50.27%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.25 ms →       10.35 ms   (+1.02%) |      26   →      32    (+23.08%) |      266.45 ms →      331.28 ms  (+24.33%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.96 ms →       10.11 ms   (+1.47%) |      26   →      32    (+23.08%) |      258.98 ms →      323.44 ms  (+24.89%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.96 ms →       10.11 ms   (+1.47%) |      26   →      32    (+23.08%) |      258.96 ms →      323.42 ms  (+24.89%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      558.12 μs →      548.14 μs   (-1.79%) |      52   →      64    (+23.08%) |       29.02 ms →       35.08 ms  (+20.88%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       49.38 ms →       49.20 ms   (-0.38%) |      26   →      32    (+23.08%) |        1.28 s  →        1.57 s   (+22.61%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.00 ms →       46.84 ms   (-0.35%) |      26   →      32    (+23.08%) |        1.22 s  →        1.50 s   (+22.65%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.11 ms →        3.05 ms   (-2.08%) |      52   →      64    (+23.08%) |      161.77 ms →      194.95 ms  (+20.51%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.31 ms →        5.51 ms   (+3.91%) |      26   →      32    (+23.08%) |      138.00 ms →      176.48 ms  (+27.88%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.64 ms →        6.77 ms   (+2.05%) |      26   →      32    (+23.08%) |      172.55 ms →      216.73 ms  (+25.60%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.87 ms →       91.10 ms   (+0.26%) |      26   →      32    (+23.08%) |        2.36 s  →        2.92 s   (+23.40%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.73 ms →      292.47 ms   (-0.09%) |      26   →      32    (+23.08%) |        7.61 s  →        9.36 s   (+22.97%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      287.23 ms →      284.89 ms   (-0.82%) |      26   →      32    (+23.08%) |        7.47 s  →        9.12 s   (+22.07%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      287.23 ms →      284.89 ms   (-0.82%) |      26   →      32    (+23.08%) |        7.47 s  →        9.12 s   (+22.07%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.07 ms →       27.43 ms   (+1.32%) |      26   →      32    (+23.08%) |      703.88 ms →      877.74 ms  (+24.70%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      232.32 ms →      229.59 ms   (-1.17%) |      26   →      32    (+23.08%) |        6.04 s  →        7.35 s   (+21.63%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.02 ms →       24.07 ms   (+0.21%) |      26   →      32    (+23.08%) |      624.51 ms →      770.21 ms  (+23.33%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.42 ms →        5.85 ms   (+8.04%) |      26   →      32    (+23.08%) |      140.86 ms →      187.30 ms  (+32.97%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.78 ms →       10.70 ms   (-0.72%) |     182   →     224    (+23.08%) |        1.96 s  →        2.40 s   (+22.19%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |       10.46 ms →       10.32 ms   (-1.34%) |     182   →     224    (+23.08%) |        1.90 s  →        2.31 s   (+21.43%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.46 ms →       10.32 ms   (-1.34%) |     182   →     224    (+23.08%) |        1.90 s  →        2.31 s   (+21.43%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.25 ms →       10.38 ms   (+1.26%) |      78   →      96    (+23.08%) |      799.50 ms →      996.37 ms  (+24.62%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.85 ms →        9.83 ms   (-0.20%) |      78   →      96    (+23.08%) |      768.06 ms →      943.43 ms  (+22.83%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |       10.02 ms →       10.03 ms   (+0.06%) |      26   →      32    (+23.08%) |      260.50 ms →      320.83 ms  (+23.16%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      112.68 μs →      166.30 μs  (+47.59%) |      26   →      32    (+23.08%) |        2.93 ms →        5.32 ms  (+81.64%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.97 μs →      160.73 μs  (+48.87%) |      26   →      32    (+23.08%) |        2.81 ms →        5.14 ms  (+83.22%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.06 ms →        5.32 ms   (+5.24%) |       2   →       2              |       10.12 ms →       10.65 ms   (+5.24%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.38 ms →       10.32 ms   (-0.60%) |       6   →       6              |       62.27 ms →       61.90 ms   (-0.60%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.32 ms →       10.09 ms   (-2.22%) |       6   →       6              |       61.94 ms →       60.57 ms   (-2.22%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.32 ms →       10.09 ms   (-2.22%) |       6   →       6              |       61.94 ms →       60.56 ms   (-2.22%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.80 ms →        9.70 ms   (-1.01%) |       3   →       3              |       29.40 ms →       29.11 ms   (-1.01%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.72 ms →        9.68 ms   (-0.47%) |       3   →       3              |       29.17 ms →       29.03 ms   (-0.47%) | 
  ├ sirius::Periodic_function|inner                                     |       10.13 ms →       10.22 ms   (+0.83%) |       2   →       2              |       20.27 ms →       20.44 ms   (+0.83%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.05 ms →       10.21 ms   (+1.62%) |       2   →       2              |       20.09 ms →       20.42 ms   (+1.62%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.05 ms →       10.21 ms   (+1.62%) |       2   →       2              |       20.09 ms →       20.42 ms   (+1.62%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.74 ms →        9.79 ms   (+0.45%) |       1   →       1              |        9.74 ms →        9.79 ms   (+0.45%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.64 ms →        9.78 ms   (+1.49%) |       1   →       1              |        9.64 ms →        9.78 ms   (+1.49%) | 
  └ sirius::finalize                                                    |      322.88 ms →      354.24 ms   (+9.71%) |       1   →       1              |      322.88 ms →      354.24 ms   (+9.71%) | 
  ====================================================================================================================================================================================================
```
