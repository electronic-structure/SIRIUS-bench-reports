# Benchmark 16c96c9521ba11c164891eb65cdeac5a4e0e34b3 vs 0308c074b92841e183b2aa72e055c15d8e0ec6ab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      346.67 s  →      358.62 s    (+3.45%) |       1   →       1              |      346.67 s  →      358.62 s    (+3.45%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.72 s    (+0.10%) |       1   →       1              |        2.71 s  →        2.72 s    (+0.10%) | 
  ├ sirius::Simulation_context::initialize                              |        3.12 s  →        3.05 s    (-2.15%) |       1   →       1              |        3.12 s  →        3.05 s    (-2.15%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      178.27 ms →      182.56 ms   (+2.41%) |       1   →       1              |      178.27 ms →      182.56 ms   (+2.41%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      139.93 ms →      148.14 ms   (+5.87%) |       1   →       1              |      139.93 ms →      148.14 ms   (+5.87%) | 
  │ │ ├ sirius::Atom_type::init                                         |       58.02 ms →       61.76 ms   (+6.46%) |       2   →       2              |      116.04 ms →      123.53 ms   (+6.46%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.82 ms →       24.52 ms   (+2.92%) |       1   →       1              |       23.82 ms →       24.52 ms   (+2.92%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.37 ms →        6.48 ms   (+1.71%) |       1   →       1              |        6.37 ms →        6.48 ms   (+1.71%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.42 ms →       18.00 ms   (+3.34%) |       1   →       1              |       17.42 ms →       18.00 ms   (+3.34%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.40 ms →       17.98 ms   (+3.33%) |       1   →       1              |       17.40 ms →       17.98 ms   (+3.33%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.15 ms   (+0.42%) |       1   →       1              |        4.13 ms →        4.15 ms   (+0.42%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.34 ms   (-0.44%) |       1   →       1              |        2.35 ms →        2.34 ms   (-0.44%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.42 μs →      101.21 μs   (-1.18%) |       1   →       1              |      102.42 μs →      101.21 μs   (-1.18%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.67 s    (-2.18%) |       1   →       1              |        2.73 s  →        2.67 s    (-2.18%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.82 ms →       10.87 ms   (+0.44%) |       1   →       1              |       10.82 ms →       10.87 ms   (+0.44%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.45 ms   (-0.15%) |       1   →       1              |        4.45 ms →        4.45 ms   (-0.15%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.33 ms →        6.39 ms   (+0.86%) |       1   →       1              |        6.33 ms →        6.39 ms   (+0.86%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.31 ms →        6.37 ms   (+0.85%) |       1   →       1              |        6.31 ms →        6.37 ms   (+0.85%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        3.88 ms   (+1.72%) |       1   →       1              |        3.82 ms →        3.88 ms   (+1.72%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.57%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.57%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.79 μs →      100.52 μs   (+0.73%) |       1   →       1              |       99.79 μs →      100.52 μs   (+0.73%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.83 ms →       62.41 ms   (-2.23%) |       2   →       2              |      127.66 ms →      124.81 ms   (-2.23%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.15 ms   (+0.33%) |       2   →       2              |       10.27 ms →       10.31 ms   (+0.33%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.87 ms →        4.50 ms   (-7.48%) |       1   →       1              |        4.87 ms →        4.50 ms   (-7.48%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.74 ms →       21.75 ms   (+0.04%) |       2   →       2              |       43.48 ms →       43.50 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.78 ms   (-0.25%) |       2   →       2              |       29.64 ms →       29.57 ms   (-0.25%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.40 ms   (-1.94%) |       4   →       4              |       79.12 ms →       77.59 ms   (-1.94%) | 
  │   ├ sddk::Gvec::init                                                |      172.52 ms →      172.74 ms   (+0.13%) |       2   →       2              |      345.04 ms →      345.48 ms   (+0.13%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.27 ms →      129.04 ms   (-0.94%) |       2   →       2              |      260.55 ms →      258.08 ms   (-0.94%) | 
  │   ├ sddk::Gvec_shells                                               |      169.10 ms →      166.96 ms   (-1.26%) |       1   →       1              |      169.10 ms →      166.96 ms   (-1.26%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.33 ms   (-0.10%) |       1   →       1              |        1.33 ms →        1.33 ms   (-0.10%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      305.64 ms →      292.14 ms   (-4.42%) |       2   →       2              |      611.29 ms →      584.27 ms   (-4.42%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       75.73 ms →       75.05 ms   (-0.90%) |       1   →       1              |       75.73 ms →       75.05 ms   (-0.90%) | 
- │ ├ sirius::K_point::K_point                                          |        2.31 μs →        2.55 μs  (+10.30%) |       4   →       4              |        9.25 μs →       10.20 μs  (+10.30%) | 
  │ └ sirius::K_point_set::initialize                                   |       75.62 ms →       74.94 ms   (-0.90%) |       1   →       1              |       75.62 ms →       74.94 ms   (-0.90%) | 
  │   └ sirius::K_point::initialize                                     |       18.88 ms →       18.71 ms   (-0.90%) |       4   →       4              |       75.54 ms →       74.85 ms   (-0.90%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.29 ms →       14.17 ms   (-0.83%) |       4   →       4              |       57.17 ms →       56.69 ms   (-0.83%) | 
  │     │ └ sddk::Gvec::init                                            |        3.84 ms →        3.80 ms   (-1.03%) |       4   →       4              |       15.37 ms →       15.22 ms   (-1.03%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.61 μs →        8.92 μs   (+3.54%) |       4   →       4              |       34.44 μs →       35.66 μs   (+3.54%) | 
  │     └ sirius::K_point::update                                       |        3.29 ms →        3.27 ms   (-0.86%) |       4   →       4              |       13.18 ms →       13.06 ms   (-0.86%) | 
  │       └ sirius::Beta_projectors                                     |        1.79 ms →        1.77 ms   (-1.34%) |       4   →       4              |        7.16 ms →        7.06 ms   (-1.34%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      958.10 μs →      959.72 μs   (+0.17%) |       4   →       4              |        3.83 ms →        3.84 ms   (+0.17%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.41 ms →        5.23 ms   (-3.30%) |       2   →       2              |       10.82 ms →       10.47 ms   (-3.30%) | 
  ├ sirius::Potential                                                   |      159.10 ms →      156.02 ms   (-1.94%) |       1   →       1              |      159.10 ms →      156.02 ms   (-1.94%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.34 ms →        5.82 ms   (-8.14%) |       6   →       6              |       38.02 ms →       34.92 ms   (-8.14%) | 
  │ └ sirius::Potential::update                                         |      120.33 ms →      120.35 ms   (+0.02%) |       1   →       1              |      120.33 ms →      120.35 ms   (+0.02%) | 
  │   └ sirius::Potential::generate_local_potential                     |      119.61 ms →      119.60 ms   (-0.00%) |       1   →       1              |      119.61 ms →      119.60 ms   (-0.00%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.75 ms →      106.29 ms   (-4.89%) |       1   →       1              |      111.75 ms →      106.29 ms   (-4.89%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.94 ms →       12.44 ms  (+79.24%) |       1   →       1              |        6.94 ms →       12.44 ms  (+79.24%) | 
  ├ sirius::Density                                                     |      127.94 ms →      128.36 ms   (+0.32%) |       1   →       1              |      127.94 ms →      128.36 ms   (+0.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.09 ms →        5.15 ms   (+1.21%) |       2   →       2              |       10.19 ms →       10.31 ms   (+1.21%) | 
  │ └ sirius::Density::update                                           |      117.49 ms →      117.78 ms   (+0.25%) |       1   →       1              |      117.49 ms →      117.78 ms   (+0.25%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      117.03 ms →      117.35 ms   (+0.27%) |       1   →       1              |      117.03 ms →      117.35 ms   (+0.27%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       81.28 μs →       73.19 μs   (-9.95%) |       1   →       1              |       81.28 μs →       73.19 μs   (-9.95%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.16 ms →      106.70 ms   (-4.01%) |       1   →       1              |      111.16 ms →      106.70 ms   (-4.01%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.34 ms →       10.13 ms  (+89.58%) |       1   →       1              |        5.34 ms →       10.13 ms  (+89.58%) | 
  ├ sirius::Density::initial_density                                    |      165.44 ms →      163.63 ms   (-1.09%) |       1   →       1              |      165.44 ms →      163.63 ms   (-1.09%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.71 ms →      109.25 ms   (-2.20%) |       1   →       1              |      111.71 ms →      109.25 ms   (-2.20%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.89 ms →        6.09 ms  (+24.65%) |       2   →       2              |        9.78 ms →       12.19 ms  (+24.65%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.31 ms →        9.73 ms   (-5.66%) |       1   →       1              |       10.31 ms →        9.73 ms   (-5.66%) | 
  ├ sirius::Potential::generate                                         |      596.14 ms →      581.27 ms   (-2.50%) |       1   →       1              |      596.14 ms →      581.27 ms   (-2.50%) | 
  │ ├ sirius::Potential::poisson                                        |      127.31 ms →      126.13 ms   (-0.93%) |       1   →       1              |      127.31 ms →      126.13 ms   (-0.93%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.42 ms →        8.28 ms  (+29.01%) |       1   →       1              |        6.42 ms →        8.28 ms  (+29.01%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       11.34 ms →       10.32 ms   (-8.96%) |       1   →       1              |       11.34 ms →       10.32 ms   (-8.96%) | 
+ │ │   └ sirius::Periodic_function|inner_local                         |       11.32 ms →        9.81 ms  (-13.34%) |       1   →       1              |       11.32 ms →        9.81 ms  (-13.34%) | 
+ │ │     └ sirius::Smooth_periodic_function|inner_local                |       11.32 ms →        9.81 ms  (-13.34%) |       1   →       1              |       11.32 ms →        9.81 ms  (-13.34%) | 
  │ ├ sirius::Periodic_function::add                                    |      536.76 μs →      560.15 μs   (+4.36%) |       2   →       2              |        1.07 ms →        1.12 ms   (+4.36%) | 
  │ ├ sirius::Potential::xc                                             |       55.56 ms →       53.86 ms   (-3.05%) |       1   →       1              |       55.56 ms →       53.86 ms   (-3.05%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.25 ms →       51.49 ms   (-3.31%) |       1   →       1              |       53.25 ms →       51.49 ms   (-3.31%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        6.21 ms →        5.67 ms   (-8.66%) |       2   →       2              |       12.42 ms →       11.35 ms   (-8.66%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.17 ms →        5.34 ms   (+3.26%) |       1   →       1              |        5.17 ms →        5.34 ms   (+3.26%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.98 ms →        6.03 ms   (+0.89%) |       1   →       1              |        5.98 ms →        6.03 ms   (+0.89%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.52 ms →       92.73 ms   (-0.85%) |       1   →       1              |       93.52 ms →       92.73 ms   (-0.85%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      311.37 ms →      300.02 ms   (-3.64%) |       1   →       1              |      311.37 ms →      300.02 ms   (-3.64%) | 
  ├ sirius::Hamiltonian0                                                |        8.38 ms →        8.65 ms   (+3.19%) |       1   →       1              |        8.38 ms →        8.65 ms   (+3.19%) | 
  │ ├ sirius::Local_operator                                            |        8.04 ms →        8.29 ms   (+3.04%) |       1   →       1              |        8.04 ms →        8.29 ms   (+3.04%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.69 ms →        5.05 ms   (+7.83%) |       1   →       1              |        4.69 ms →        5.05 ms   (+7.83%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.45 ms →        2.33 ms   (-5.00%) |       1   →       1              |        2.45 ms →        2.33 ms   (-5.00%) | 
  │ ├ sirius::Non_local_operator                                        |       62.52 μs →       63.13 μs   (+0.98%) |       2   →       2              |      125.04 μs →      126.27 μs   (+0.98%) | 
- │ ├ sirius::D_operator::initialize                                    |       87.71 μs →       98.55 μs  (+12.36%) |       1   →       1              |       87.71 μs →       98.55 μs  (+12.36%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.66 μs →       73.34 μs   (+5.29%) |       1   →       1              |       69.66 μs →       73.34 μs   (+5.29%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.06 s  →        4.01 s    (-1.03%) |       1   →       1              |        4.06 s  →        4.01 s    (-1.03%) | 
  │ ├ sirius::Hamiltonian_k                                             |      378.90 μs →      382.92 μs   (+1.06%) |       4   →       4              |        1.52 ms →        1.53 ms   (+1.06%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      373.61 μs →      377.37 μs   (+1.01%) |       4   →       4              |        1.49 ms →        1.51 ms   (+1.01%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.47 μs →        3.69 μs   (+6.12%) |       4   →       4              |       13.90 μs →       14.75 μs   (+6.12%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.01 s  →        1.00 s    (-1.03%) |       4   →       4              |        4.06 s  →        4.01 s    (-1.03%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.78 ms →       32.78 ms   (+0.02%) |      16   →      16              |      524.44 ms →      524.53 ms   (+0.02%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.59 ms →       14.46 ms   (-0.90%) |       4   →       4              |       58.35 ms →       57.83 ms   (-0.90%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.34 ms →        5.34 ms   (-0.09%) |       4   →       4              |       21.37 ms →       21.35 ms   (-0.09%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      357.75 ms →      354.80 ms   (-0.82%) |       4   →       4              |        1.43 s  →        1.42 s    (-0.82%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      260.31 ms →      258.47 ms   (-0.71%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.71%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.22 ms →       63.74 ms   (-0.75%) |       4   →       4              |      256.87 ms →      254.94 ms   (-0.75%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.85 ms →       16.27 ms   (-3.44%) |       4   →       4              |       67.41 ms →       65.09 ms   (-3.44%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.85 ms →       16.27 ms   (-3.45%) |       4   →       4              |       67.40 ms →       65.08 ms   (-3.45%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.97 ms →       41.04 ms   (+0.16%) |       4   →       4              |      163.88 ms →      164.14 ms   (+0.16%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.59 ms →       16.26 ms   (-1.96%) |       4   →       4              |       66.36 ms →       65.06 ms   (-1.96%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.59 ms →       16.26 ms   (-1.96%) |       4   →       4              |       66.34 ms →       65.04 ms   (-1.96%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       55.14 ms →       54.22 ms   (-1.66%) |       4   →       4              |      220.56 ms →      216.89 ms   (-1.66%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       37.11 ms →       36.21 ms   (-2.44%) |       4   →       4              |      148.45 ms →      144.83 ms   (-2.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.96 ms   (+0.56%) |       4   →       4              |        7.81 ms →        7.85 ms   (+0.56%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.29 ms →       40.14 ms   (-2.78%) |       4   →       4              |      165.16 ms →      160.56 ms   (-2.78%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.17 ms →        6.98 ms  (-14.46%) |       4   →       4              |       32.66 ms →       27.94 ms  (-14.46%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.07 ms →       27.09 ms   (+0.07%) |       8   →       8              |      216.59 ms →      216.74 ms   (+0.07%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.30 ms →       15.02 ms   (-1.83%) |       8   →       8              |      122.40 ms →      120.16 ms   (-1.83%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.25 ms →       14.97 ms   (-1.85%) |       8   →       8              |      122.04 ms →      119.78 ms   (-1.85%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       25.75 ns →       22.50 ns  (-12.62%) |       8   →       8              |      206.00 ns →      180.00 ns  (-12.62%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.06 ms →       14.78 ms   (-1.86%) |       8   →       8              |      120.50 ms →      118.26 ms   (-1.86%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       37.75 ns →       26.75 ns  (-29.14%) |       8   →       8              |      302.00 ns →      214.00 ns  (-29.14%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      350.58 ms →      343.58 ms   (-2.00%) |       4   →       4              |        1.40 s  →        1.37 s    (-2.00%) | 
  │ │ └ sddk::wf_trans                                                  |       26.74 ms →       26.75 ms   (+0.03%) |       4   →       4              |      106.97 ms →      106.99 ms   (+0.03%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.57 ms →       26.50 ms   (-0.24%) |       4   →       4              |      106.26 ms →      106.01 ms   (-0.24%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      402.75 ns →      502.50 ns  (+24.77%) |       4   →       4              |        1.61 μs →        2.01 μs  (+24.77%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      334.80 s  →      346.88 s    (+3.61%) |       1   →       1              |      334.80 s  →      346.88 s    (+3.61%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.88 ms   (+0.61%) |      17   →      17              |       99.30 ms →       99.91 ms   (+0.61%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       12.86 s  →       12.38 s    (-3.73%) |      26   →      28     (+7.69%) |      334.24 s  →      346.53 s    (+3.68%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.48 ms →        4.47 ms   (-0.25%) |      26   →      28     (+7.69%) |      116.54 ms →      125.19 ms   (+7.42%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.12 ms →        4.11 ms   (-0.23%) |      26   →      28     (+7.69%) |      107.22 ms →      115.21 ms   (+7.45%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      974.02 μs →      977.84 μs   (+0.39%) |      26   →      28     (+7.69%) |       25.32 ms →       27.38 ms   (+8.11%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.26 ms →        2.25 ms   (-0.72%) |      26   →      28     (+7.69%) |       58.84 ms →       62.91 ms   (+6.92%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.73 μs →       64.80 μs   (+0.11%) |      52   →      56     (+7.69%) |        3.37 ms →        3.63 ms   (+7.81%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       92.53 μs →       93.65 μs   (+1.21%) |      26   →      28     (+7.69%) |        2.41 ms →        2.62 ms   (+9.00%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       67.42 μs →       65.99 μs   (-2.12%) |      26   →      28     (+7.69%) |        1.75 ms →        1.85 ms   (+5.41%) | 
  │ │ ├ sirius::Band::solve                                             |       10.83 s  →       10.38 s    (-4.11%) |      26   →      28     (+7.69%) |      281.53 s  →      290.73 s    (+3.27%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      331.81 μs →      317.07 μs   (-4.44%) |     104   →     112     (+7.69%) |       34.51 ms →       35.51 ms   (+2.91%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      326.38 μs →      311.66 μs   (-4.51%) |     104   →     112     (+7.69%) |       33.94 ms →       34.91 ms   (+2.84%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.95 μs →        3.86 μs   (-2.23%) |     104   →     112     (+7.69%) |      410.56 μs →      432.26 μs   (+5.29%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.71 s  →        2.60 s    (-4.11%) |     104   →     112     (+7.69%) |      281.49 s  →      290.69 s    (+3.27%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.06 ms →       11.99 ms   (-0.64%) |     104   →     112     (+7.69%) |        1.25 s  →        1.34 s    (+7.01%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      619.78 ns →      636.79 ns   (+2.74%) |     624   →     672     (+7.69%) |      386.75 μs →      427.93 μs  (+10.65%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.84 ms   (+0.54%) |     104   →     112     (+7.69%) |      190.84 ms →      206.63 ms   (+8.27%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      357.89 μs →      356.29 μs   (-0.45%) |     104   →     112     (+7.69%) |       37.22 ms →       39.90 ms   (+7.21%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.26 μs →      556.25 μs   (+1.09%) |     208   →     224     (+7.69%) |      114.45 ms →      124.60 ms   (+8.86%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.68 s  →        2.57 s    (-4.14%) |     104   →     112     (+7.69%) |      279.10 s  →      288.13 s    (+3.23%) | 
! │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.61 ms →       64.14 ms   (-6.52%) |     956   →    1.07 K  (+12.13%) |       65.59 s  →       68.76 s    (+4.82%) | 
! │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.93 ms →       40.77 ms   (-7.19%) |     956   →    1.07 K  (+12.13%) |       42.00 s  →       43.71 s    (+4.07%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.74 ms →        8.15 ms   (-6.76%) |     956   →    1.07 K  (+12.13%) |        8.36 s  →        8.74 s    (+4.55%) | 
+ │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      225.36 μs →      200.49 μs  (-11.04%) |     956   →    1.07 K  (+12.13%) |      215.44 ms →      214.92 ms   (-0.24%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.05 ms →        1.90 ms   (-7.50%) |     104   →     112     (+7.69%) |      213.65 ms →      212.83 ms   (-0.39%) | 
! │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.85 ms →        6.32 ms   (-7.75%) |     956   →    1.07 K  (+12.13%) |        6.55 s  →        6.78 s    (+3.44%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       85.75 μs →       76.66 μs  (-10.60%) |     956   →    1.07 K  (+12.13%) |       81.98 ms →       82.18 ms   (+0.25%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      765.73 μs →      710.77 μs   (-7.18%) |     104   →     112     (+7.69%) |       79.64 ms →       79.61 ms   (-0.04%) | 
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.80 ms →        8.96 ms   (-8.54%) |     956   →    1.07 K  (+12.13%) |        9.37 s  →        9.61 s    (+2.55%) | 
! │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.26 ms →        5.67 ms   (-9.54%) |     956   →    1.07 K  (+12.13%) |        5.99 s  →        6.07 s    (+1.43%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.51 ms   (-0.39%) |     956   →    1.07 K  (+12.13%) |        1.45 s  →        1.62 s   (+11.70%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.59 ms →        7.88 ms   (-8.22%) |     956   →    1.07 K  (+12.13%) |        8.21 s  →        8.45 s    (+2.91%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.42 ms →        1.15 ms  (-19.50%) |     956   →    1.07 K  (+12.13%) |        1.36 s  →        1.23 s    (-9.73%) | 
! │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.28 ms →        6.97 ms   (-4.15%) |    1.91 K →    2.14 K  (+12.13%) |       13.91 s  →       14.95 s    (+7.48%) | 
! │ │ │ │   ├ sddk::orthogonalize                                       |       29.39 ms →       27.35 ms   (-6.92%) |     956   →    1.07 K  (+12.13%) |       28.10 s  →       29.32 s    (+4.37%) | 
! │ │ │ │   │ ├ sddk::wf_inner                                          |        1.99 ms →        1.83 ms   (-8.21%) |    1.81 K →    2.03 K  (+12.39%) |        3.60 s  →        3.72 s    (+3.16%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |      101.94 ns →       44.59 ns  (-56.26%) |    1.81 K →    2.03 K  (+12.39%) |      184.30 μs →       90.61 μs  (-50.84%) | 
! │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.98 ms →        1.82 ms   (-8.14%) |    1.81 K →    2.03 K  (+12.39%) |        3.58 s  →        3.70 s    (+3.24%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       65.11 ns →       80.62 ns  (+23.83%) |    1.81 K →    2.03 K  (+12.39%) |      117.71 μs →      163.82 μs  (+39.17%) | 
! │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      936.99 μs →      883.57 μs   (-5.70%) |     956   →    1.07 K  (+12.13%) |      895.76 ms →      947.19 ms   (+5.74%) | 
! │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.44 ms →        1.32 ms   (-8.00%) |     956   →    1.07 K  (+12.13%) |        1.38 s  →        1.42 s    (+3.16%) | 
! │ │ │ │   │ └ sddk::wf_trans                                          |        5.59 ms →        5.20 ms   (-6.98%) |    3.72 K →    4.18 K  (+12.26%) |       20.78 s  →       21.70 s    (+4.42%) | 
! │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.80 ms →        3.53 ms   (-7.13%) |    5.42 K →    6.10 K  (+12.39%) |       20.59 s  →       21.49 s    (+4.38%) | 
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.28 ms →        5.06 ms   (-4.16%) |     956   →    1.07 K  (+12.13%) |        5.05 s  →        5.43 s    (+7.47%) | 
! │ │ │ │   │ └ sddk::wf_inner                                          |        3.49 ms →        3.26 ms   (-6.58%) |     956   →    1.07 K  (+12.13%) |        3.34 s  →        3.50 s    (+4.75%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       90.35 ns →       97.39 ns   (+7.80%) |     956   →    1.07 K  (+12.13%) |       86.37 μs →      104.40 μs  (+20.88%) | 
! │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.48 ms →        3.25 ms   (-6.59%) |     956   →    1.07 K  (+12.13%) |        3.32 s  →        3.48 s    (+4.75%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       48.80 ns →       91.29 ns  (+87.08%) |     956   →    1.07 K  (+12.13%) |       46.65 μs →       97.87 μs (+109.78%) | 
! │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      162.90 ms →      148.96 ms   (-8.56%) |     956   →    1.07 K  (+12.13%) |      155.73 s  →      159.69 s    (+2.54%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       11.37 ms →       10.01 ms  (-11.94%) |     929   →    1.04 K  (+12.38%) |       10.56 s  →       10.45 s    (-1.04%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       10.84 ms →        9.51 ms  (-12.25%) |     886   →     999    (+12.75%) |        9.60 s  →        9.50 s    (-1.06%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.38 ms →        4.72 ms  (-12.33%) |    1.77 K →    2.00 K  (+12.75%) |        9.54 s  →        9.43 s    (-1.15%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      659.92 μs →      581.09 μs  (-11.94%) |     886   →     999    (+12.75%) |      584.69 ms →      580.51 ms   (-0.71%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.80 ms →       38.42 ms   (-5.85%) |     344   →     376     (+9.30%) |       14.04 s  →       14.44 s    (+2.91%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       23.91 ms →       22.44 ms   (-6.12%) |     584   →     640     (+9.59%) |       13.96 s  →       14.36 s    (+2.88%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       16.83 ms →       15.78 ms   (-6.27%) |     824   →     904     (+9.71%) |       13.87 s  →       14.26 s    (+2.83%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      526.13 ns →      525.21 ns   (-0.17%) |     104   →     112     (+7.69%) |       54.72 μs →       58.82 μs   (+7.50%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.56 μs →       23.42 μs   (-0.56%) |      26   →      28     (+7.69%) |      612.44 μs →      655.88 μs   (+7.09%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      594.89 μs →      617.10 μs   (+3.73%) |      26   →      28     (+7.69%) |       15.47 ms →       17.28 ms  (+11.71%) | 
  │ │ ├ sirius::Density::generate                                       |      895.32 ms →      896.04 ms   (+0.08%) |      26   →      28     (+7.69%) |       23.28 s  →       25.09 s    (+7.78%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      531.50 ms →      524.96 ms   (-1.23%) |      26   →      28     (+7.69%) |       13.82 s  →       14.70 s    (+6.37%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.06 ms →       24.37 ms   (-2.74%) |     104   →     112     (+7.69%) |        2.61 s  →        2.73 s    (+4.75%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.51 μs →        5.58 μs   (+1.20%) |     104   →     112     (+7.69%) |      573.26 μs →      624.74 μs   (+8.98%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.39 μs →       11.61 μs   (-6.24%) |       8   →       8              |       99.09 μs →       92.90 μs   (-6.24%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.92 ms →       20.24 ms   (-3.26%) |     104   →     112     (+7.69%) |        2.18 s  →        2.27 s    (+4.18%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.54 ms →       29.85 ms   (-2.28%) |     104   →     112     (+7.69%) |        3.18 s  →        3.34 s    (+5.24%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.71 μs →       11.80 μs   (+0.82%) |     104   →     112     (+7.69%) |        1.22 ms →        1.32 ms   (+8.57%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.09%) |     104   →     112     (+7.69%) |      152.17 ms →      164.02 ms   (+7.79%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.60 ms →       27.90 ms   (-2.45%) |     104   →     112     (+7.69%) |        2.97 s  →        3.12 s    (+5.05%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.46 ms →        3.76 ms  (-15.80%) |     104   →     112     (+7.69%) |      464.22 ms →      420.92 ms   (-9.33%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      594.05 ns →      561.53 ns   (-5.47%) |     104   →     112     (+7.69%) |       61.78 μs →       62.89 μs   (+1.80%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.76 ms →       42.67 ms   (-0.20%) |     104   →     112     (+7.69%) |        4.45 s  →        4.78 s    (+7.48%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.31%) |      26   →      28     (+7.69%) |       42.84 ms →       46.00 ms   (+7.36%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.88 ms →       89.00 ms   (+0.14%) |      26   →      28     (+7.69%) |        2.31 s  →        2.49 s    (+7.84%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.65 ms →       88.77 ms   (+0.13%) |      26   →      28     (+7.69%) |        2.30 s  →        2.49 s    (+7.84%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      268.89 ms →      278.90 ms   (+3.72%) |      26   →      28     (+7.69%) |        6.99 s  →        7.81 s   (+11.70%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      268.89 ms →      278.90 ms   (+3.72%) |      26   →      28     (+7.69%) |        6.99 s  →        7.81 s   (+11.70%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.30 ms →       24.63 ms   (+1.37%) |      26   →      28     (+7.69%) |      631.82 ms →      689.72 ms   (+9.16%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      218.76 ms →      227.95 ms   (+4.20%) |      26   →      28     (+7.69%) |        5.69 s  →        6.38 s   (+12.22%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.00 ms →       24.53 ms   (+2.22%) |      26   →      28     (+7.69%) |      624.02 ms →      686.96 ms  (+10.09%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.28 ms →       81.54 ms   (+0.31%) |      26   →      28     (+7.69%) |        2.11 s  →        2.28 s    (+8.03%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       10.04 ms →        7.06 ms  (-29.68%) |      26   →      28     (+7.69%) |      261.06 ms →      197.70 ms  (-24.27%) | 
+ │ │ ├ sirius::Density::mix                                            |      155.09 ms →      106.72 ms  (-31.19%) |      26   →      28     (+7.69%) |        4.03 s  →        2.99 s   (-25.90%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      946.58 μs →      964.65 μs   (+1.91%) |      26   →      28     (+7.69%) |       24.61 ms →       27.01 ms   (+9.75%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.16 ms →       10.54 ms   (+3.69%) |     334   →     224    (-32.93%) |        3.39 s  →        2.36 s   (-30.46%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.81 ms →       10.21 ms   (+4.01%) |     334   →     224    (-32.93%) |        3.28 s  →        2.29 s   (-30.25%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.81 ms →       10.20 ms   (+4.01%) |     334   →     224    (-32.93%) |        3.28 s  →        2.29 s   (-30.24%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.36 ms →        7.20 ms  (+13.21%) |      26   →      28     (+7.69%) |      165.33 ms →      201.56 ms  (+21.92%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.29 ms →        6.14 ms  (+16.00%) |      26   →      28     (+7.69%) |      137.62 ms →      171.92 ms  (+24.92%) | 
  │ │ ├ sirius::Potential::generate                                     |      573.81 ms →      577.39 ms   (+0.62%) |      26   →      28     (+7.69%) |       14.92 s  →       16.17 s    (+8.36%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.71 ms →      126.16 ms   (-0.44%) |      26   →      28     (+7.69%) |        3.29 s  →        3.53 s    (+7.22%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.95 ms →        8.18 ms  (+37.49%) |      26   →      28     (+7.69%) |      154.60 ms →      228.92 ms  (+48.07%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.93 ms →       10.43 ms   (-4.51%) |      26   →      28     (+7.69%) |      284.08 ms →      292.14 ms   (+2.84%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.53 ms →       10.00 ms   (-5.09%) |      26   →      28     (+7.69%) |      273.86 ms →      279.90 ms   (+2.21%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.53 ms →       10.00 ms   (-5.09%) |      26   →      28     (+7.69%) |      273.83 ms →      279.89 ms   (+2.21%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      550.48 μs →      562.63 μs   (+2.21%) |      52   →      56     (+7.69%) |       28.62 ms →       31.51 ms  (+10.07%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.60 ms →       49.46 ms   (-0.29%) |      26   →      28     (+7.69%) |        1.29 s  →        1.38 s    (+7.38%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.26 ms →       47.08 ms   (-0.38%) |      26   →      28     (+7.69%) |        1.23 s  →        1.32 s    (+7.29%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.06 ms   (+0.61%) |      52   →      56     (+7.69%) |      157.95 ms →      171.14 ms   (+8.35%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.48 ms →        5.22 ms   (-4.63%) |      26   →      28     (+7.69%) |      142.37 ms →      146.21 ms   (+2.70%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.77 ms →        6.68 ms   (-1.40%) |      26   →      28     (+7.69%) |      176.06 ms →      186.95 ms   (+6.19%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.92 ms →       90.96 ms   (+0.05%) |      26   →      28     (+7.69%) |        2.36 s  →        2.55 s    (+7.75%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      297.42 ms →      301.71 ms   (+1.44%) |      26   →      28     (+7.69%) |        7.73 s  →        8.45 s    (+9.24%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      275.93 ms →      284.26 ms   (+3.02%) |      26   →      28     (+7.69%) |        7.17 s  →        7.96 s   (+10.95%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      275.93 ms →      284.26 ms   (+3.02%) |      26   →      28     (+7.69%) |        7.17 s  →        7.96 s   (+10.95%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       28.01 ms →       27.68 ms   (-1.19%) |      26   →      28     (+7.69%) |      728.20 ms →      774.91 ms   (+6.42%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      220.33 ms →      228.42 ms   (+3.68%) |      26   →      28     (+7.69%) |        5.73 s  →        6.40 s   (+11.65%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.81 ms →       24.34 ms   (+2.26%) |      26   →      28     (+7.69%) |      618.96 ms →      681.60 ms  (+10.12%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.57 ms →        6.12 ms   (+9.90%) |      26   →      28     (+7.69%) |      144.78 ms →      171.36 ms  (+18.36%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.52 ms →       10.84 ms   (+3.11%) |     182   →     196     (+7.69%) |        1.91 s  →        2.13 s   (+11.05%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |       10.12 ms →       10.38 ms   (+2.52%) |     182   →     196     (+7.69%) |        1.84 s  →        2.03 s   (+10.40%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.12 ms →       10.38 ms   (+2.52%) |     182   →     196     (+7.69%) |        1.84 s  →        2.03 s   (+10.40%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.82 ms →       10.34 ms   (-4.38%) |      78   →      84     (+7.69%) |      843.78 ms →      868.86 ms   (+2.97%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.42 ms →        9.86 ms   (-5.38%) |      78   →      84     (+7.69%) |      813.06 ms →      828.47 ms   (+1.89%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.27 ms →       10.15 ms   (-1.19%) |      26   →      28     (+7.69%) |      267.06 ms →      284.17 ms   (+6.41%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      113.11 μs →      110.66 μs   (-2.17%) |      26   →      28     (+7.69%) |        2.94 ms →        3.10 ms   (+5.36%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.93 μs →      105.56 μs   (-2.20%) |      26   →      28     (+7.69%) |        2.81 ms →        2.96 ms   (+5.33%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.17 ms →        5.11 ms   (-1.29%) |       2   →       2              |       10.35 ms →       10.21 ms   (-1.29%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.25 ms →       10.56 ms   (+3.05%) |       6   →       6              |       61.51 ms →       63.38 ms   (+3.05%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.24 ms →       10.11 ms   (-1.19%) |       6   →       6              |       61.41 ms →       60.68 ms   (-1.19%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.24 ms →       10.11 ms   (-1.19%) |       6   →       6              |       61.41 ms →       60.68 ms   (-1.19%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.55 ms →       10.11 ms   (-4.16%) |       3   →       3              |       31.64 ms →       30.32 ms   (-4.16%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.48 ms →        9.64 ms   (-8.01%) |       3   →       3              |       31.44 ms →       28.93 ms   (-8.01%) | 
  ├ sirius::Periodic_function|inner                                     |       10.29 ms →       10.50 ms   (+2.02%) |       2   →       2              |       20.58 ms →       21.00 ms   (+2.02%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.28 ms →       10.09 ms   (-1.87%) |       2   →       2              |       20.57 ms →       20.19 ms   (-1.87%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.28 ms →       10.09 ms   (-1.87%) |       2   →       2              |       20.57 ms →       20.18 ms   (-1.87%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.37 ms →       10.12 ms   (-2.45%) |       1   →       1              |       10.37 ms →       10.12 ms   (-2.45%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.36 ms →        9.60 ms   (-7.34%) |       1   →       1              |       10.36 ms →        9.60 ms   (-7.34%) | 
  └ sirius::finalize                                                    |      335.52 ms →      329.58 ms   (-1.77%) |       1   →       1              |      335.52 ms →      329.58 ms   (-1.77%) | 
  ====================================================================================================================================================================================================
```
