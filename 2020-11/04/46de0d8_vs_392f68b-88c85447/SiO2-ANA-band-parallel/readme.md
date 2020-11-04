# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 46de0d896d343d7768c9da756627e739ed0717b7
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      222.87 s  →      222.14 s    (-0.33%) |       1   →       1              |      222.87 s  →      222.14 s    (-0.33%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.64 s    (-0.37%) |       1   →       1              |        2.65 s  →        2.64 s    (-0.37%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.95 s    (+0.73%) |       1   →       1              |        2.93 s  →        2.95 s    (+0.73%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        2.61 ms →        5.96 ms (+128.31%) |       1   →       1              |        2.61 ms →        5.96 ms (+128.31%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      176.05 ms →      168.33 ms   (-4.38%) |       1   →       1              |      176.05 ms →      168.33 ms   (-4.38%) | 
  │ │ ├ sirius::Atom_type::init                                         |       76.55 ms →       72.89 ms   (-4.78%) |       2   →       2              |      153.11 ms →      145.78 ms   (-4.78%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.86 ms →       22.47 ms   (-1.72%) |       1   →       1              |       22.86 ms →       22.47 ms   (-1.72%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.38 ms →        6.30 ms   (-1.19%) |       1   →       1              |        6.38 ms →        6.30 ms   (-1.19%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.45 ms →       16.13 ms   (-1.95%) |       1   →       1              |       16.45 ms →       16.13 ms   (-1.95%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.43 ms →       16.10 ms   (-1.97%) |       1   →       1              |       16.43 ms →       16.10 ms   (-1.97%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.19 ms →        4.18 ms   (-0.21%) |       1   →       1              |        4.19 ms →        4.18 ms   (-0.21%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (-0.14%) |       1   →       1              |        2.34 ms →        2.34 ms   (-0.14%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      109.43 μs →      111.81 μs   (+2.18%) |       1   →       1              |      109.43 μs →      111.81 μs   (+2.18%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.73 s    (+1.00%) |       1   →       1              |        2.70 s  →        2.73 s    (+1.00%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.78 ms →       10.86 ms   (+0.81%) |       1   →       1              |       10.78 ms →       10.86 ms   (+0.81%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.37 ms →        4.46 ms   (+1.98%) |       1   →       1              |        4.37 ms →        4.46 ms   (+1.98%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.37 ms →        6.38 ms   (+0.02%) |       1   →       1              |        6.37 ms →        6.38 ms   (+0.02%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.35 ms →        6.36 ms   (+0.02%) |       1   →       1              |        6.35 ms →        6.36 ms   (+0.02%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.86 ms   (+0.84%) |       1   →       1              |        3.83 ms →        3.86 ms   (+0.84%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.32 ms   (-1.20%) |       1   →       1              |        2.35 ms →        2.32 ms   (-1.20%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      110.14 μs →      108.27 μs   (-1.70%) |       1   →       1              |      110.14 μs →      108.27 μs   (-1.70%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.55 ms →       62.63 ms   (+0.12%) |       2   →       2              |      125.10 ms →      125.25 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.14 ms   (+0.03%) |       2   →       2              |       10.27 ms →       10.27 ms   (+0.03%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.47 ms   (+0.20%) |       1   →       1              |        4.46 ms →        4.47 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.25 ms →       21.80 ms   (-2.04%) |       2   →       2              |       44.51 ms →       43.60 ms   (-2.04%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.78 ms →       14.79 ms   (+0.06%) |       2   →       2              |       29.56 ms →       29.58 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.71 ms →       19.64 ms   (-0.39%) |       4   →       4              |       78.86 ms →       78.55 ms   (-0.39%) | 
  │   ├ sddk::Gvec::init                                                |      172.72 ms →      179.87 ms   (+4.14%) |       2   →       2              |      345.44 ms →      359.74 ms   (+4.14%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.69 ms →      136.00 ms   (+4.87%) |       2   →       2              |      259.37 ms →      272.00 ms   (+4.87%) | 
  │   ├ sddk::Gvec_shells                                               |      179.16 ms →      181.41 ms   (+1.26%) |       1   →       1              |      179.16 ms →      181.41 ms   (+1.26%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (-0.08%) |       1   →       1              |        1.32 ms →        1.32 ms   (-0.08%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      290.09 ms →      292.17 ms   (+0.71%) |       2   →       2              |      580.19 ms →      584.33 ms   (+0.71%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.83 ms →       74.80 ms   (-2.65%) |       1   →       1              |       76.83 ms →       74.80 ms   (-2.65%) | 
  │ ├ sirius::K_point::K_point                                          |        2.75 μs →        2.55 μs   (-7.16%) |       4   →       4              |       11.01 μs →       10.22 μs   (-7.16%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.73 ms →       74.70 ms   (-2.65%) |       1   →       1              |       76.73 ms →       74.70 ms   (-2.65%) | 
  │   └ sirius::K_point::initialize                                     |       19.16 ms →       18.65 ms   (-2.63%) |       4   →       4              |       76.63 ms →       74.61 ms   (-2.63%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.59 ms →       14.09 ms   (-3.44%) |       4   →       4              |       58.37 ms →       56.36 ms   (-3.44%) | 
  │     │ └ sddk::Gvec::init                                            |        3.81 ms →        3.84 ms   (+0.64%) |       4   →       4              |       15.25 ms →       15.34 ms   (+0.64%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.20 μs →        8.58 μs   (+4.60%) |       4   →       4              |       32.82 μs →       34.33 μs   (+4.60%) | 
  │     └ sirius::K_point::update                                       |        3.26 ms →        3.27 ms   (+0.41%) |       4   →       4              |       13.04 ms →       13.09 ms   (+0.41%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.77 ms   (+0.47%) |       4   →       4              |        7.05 ms →        7.08 ms   (+0.47%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      927.88 μs →      923.21 μs   (-0.50%) |       4   →       4              |        3.71 ms →        3.69 ms   (-0.50%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.19 ms →        5.17 ms   (-0.39%) |       2   →       2              |       10.37 ms →       10.33 ms   (-0.39%) | 
  ├ sirius::Potential                                                   |      159.50 ms →      160.98 ms   (+0.93%) |       1   →       1              |      159.50 ms →      160.98 ms   (+0.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.73 ms   (-0.98%) |       6   →       6              |       34.75 ms →       34.41 ms   (-0.98%) | 
  │ └ sirius::Potential::update                                         |      124.05 ms →      125.87 ms   (+1.47%) |       1   →       1              |      124.05 ms →      125.87 ms   (+1.47%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.34 ms →      125.18 ms   (+1.48%) |       1   →       1              |      123.34 ms →      125.18 ms   (+1.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.28 ms →      106.27 ms   (-4.50%) |       1   →       1              |      111.28 ms →      106.27 ms   (-4.50%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       11.18 ms →       17.97 ms  (+60.78%) |       1   →       1              |       11.18 ms →       17.97 ms  (+60.78%) | 
  ├ sirius::Density                                                     |      136.21 ms →      134.31 ms   (-1.39%) |       1   →       1              |      136.21 ms →      134.31 ms   (-1.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.08 ms →        5.06 ms   (-0.37%) |       2   →       2              |       10.16 ms →       10.13 ms   (-0.37%) | 
  │ └ sirius::Density::update                                           |      125.78 ms →      123.92 ms   (-1.48%) |       1   →       1              |      125.78 ms →      123.92 ms   (-1.48%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.36 ms →      123.48 ms   (-1.50%) |       1   →       1              |      125.36 ms →      123.48 ms   (-1.50%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      104.76 μs →      105.25 μs   (+0.48%) |       1   →       1              |      104.76 μs →      105.25 μs   (+0.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.37 ms →      109.02 ms   (-2.98%) |       1   →       1              |      112.37 ms →      109.02 ms   (-2.98%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       12.46 ms →       13.91 ms  (+11.59%) |       1   →       1              |       12.46 ms →       13.91 ms  (+11.59%) | 
  ├ sirius::Density::initial_density                                    |      174.30 ms →      176.20 ms   (+1.09%) |       1   →       1              |      174.30 ms →      176.20 ms   (+1.09%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.23 ms →      109.36 ms   (-1.68%) |       1   →       1              |      111.23 ms →      109.36 ms   (-1.68%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.43 ms →       11.73 ms  (+12.42%) |       2   →       2              |       20.86 ms →       23.45 ms  (+12.42%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.32 ms →       11.50 ms  (+11.39%) |       1   →       1              |       10.32 ms →       11.50 ms  (+11.39%) | 
  ├ sirius::Potential::generate                                         |      591.95 ms →      591.26 ms   (-0.12%) |       1   →       1              |      591.95 ms →      591.26 ms   (-0.12%) | 
  │ ├ sirius::Potential::poisson                                        |      136.96 ms →      136.95 ms   (-0.01%) |       1   →       1              |      136.96 ms →      136.95 ms   (-0.01%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       15.22 ms →       18.45 ms  (+21.27%) |       1   →       1              |       15.22 ms →       18.45 ms  (+21.27%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.41 ms →       10.17 ms   (-2.30%) |       1   →       1              |       10.41 ms →       10.17 ms   (-2.30%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.30 ms →        9.80 ms   (-4.83%) |       1   →       1              |       10.30 ms →        9.80 ms   (-4.83%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.30 ms →        9.80 ms   (-4.83%) |       1   →       1              |       10.30 ms →        9.80 ms   (-4.83%) | 
  │ ├ sirius::Periodic_function::add                                    |      554.44 μs →      548.95 μs   (-0.99%) |       2   →       2              |        1.11 ms →        1.10 ms   (-0.99%) | 
  │ ├ sirius::Potential::xc                                             |       53.70 ms →       53.57 ms   (-0.23%) |       1   →       1              |       53.70 ms →       53.57 ms   (-0.23%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.40 ms →       51.30 ms   (-0.20%) |       1   →       1              |       51.40 ms →       51.30 ms   (-0.20%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.60 ms →        5.58 ms   (-0.27%) |       2   →       2              |       11.20 ms →       11.17 ms   (-0.27%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.37 ms →        5.41 ms   (+0.69%) |       1   →       1              |        5.37 ms →        5.41 ms   (+0.69%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.94 ms →        5.79 ms   (-2.59%) |       1   →       1              |        5.94 ms →        5.79 ms   (-2.59%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.47 ms →       93.45 ms   (-0.03%) |       1   →       1              |       93.47 ms →       93.45 ms   (-0.03%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.44 ms →      299.08 ms   (-0.12%) |       1   →       1              |      299.44 ms →      299.08 ms   (-0.12%) | 
  ├ sirius::Hamiltonian0                                                |        8.30 ms →        8.37 ms   (+0.83%) |       1   →       1              |        8.30 ms →        8.37 ms   (+0.83%) | 
  │ ├ sirius::Local_operator                                            |        7.96 ms →        8.03 ms   (+0.76%) |       1   →       1              |        7.96 ms →        8.03 ms   (+0.76%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.67 ms →        4.69 ms   (+0.43%) |       1   →       1              |        4.67 ms →        4.69 ms   (+0.43%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        2.41 ms   (+1.57%) |       1   →       1              |        2.38 ms →        2.41 ms   (+1.57%) | 
  │ ├ sirius::Non_local_operator                                        |       62.54 μs →       64.13 μs   (+2.53%) |       2   →       2              |      125.08 μs →      128.25 μs   (+2.53%) | 
  │ ├ sirius::D_operator::initialize                                    |       89.81 μs →       92.59 μs   (+3.10%) |       1   →       1              |       89.81 μs →       92.59 μs   (+3.10%) | 
  │ └ sirius::Q_operator::initialize                                    |       67.22 μs →       68.76 μs   (+2.28%) |       1   →       1              |       67.22 μs →       68.76 μs   (+2.28%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.13 s    (+1.03%) |       1   →       1              |        3.09 s  →        3.13 s    (+1.03%) | 
- │ ├ sirius::Hamiltonian_k                                             |      374.18 μs →        1.10 ms (+194.66%) |       4   →       4              |        1.50 ms →        4.41 ms (+194.66%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      369.17 μs →        1.10 ms (+197.37%) |       4   →       4              |        1.48 ms →        4.39 ms (+197.37%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.27 μs →        3.29 μs   (+0.60%) |       4   →       4              |       13.08 μs →       13.16 μs   (+0.60%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      773.07 ms →      780.34 ms   (+0.94%) |       4   →       4              |        3.09 s  →        3.12 s    (+0.94%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       31.99 ms →       31.98 ms   (-0.03%) |      16   →      16              |      511.81 ms →      511.64 ms   (-0.03%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.45 ms →       15.33 ms   (+6.10%) |       4   →       4              |       57.80 ms →       61.32 ms   (+6.10%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.29 ms →        5.33 ms   (+0.80%) |       4   →       4              |       21.16 ms →       21.33 ms   (+0.80%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      353.42 ms →      356.54 ms   (+0.88%) |       4   →       4              |        1.41 s  →        1.43 s    (+0.88%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      256.88 ms →      257.46 ms   (+0.22%) |       4   →       4              |        1.03 s  →        1.03 s    (+0.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       62.88 ms →       63.14 ms   (+0.42%) |       4   →       4              |      251.50 ms →      252.57 ms   (+0.42%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.05 ms →       16.36 ms   (+1.91%) |       4   →       4              |       64.21 ms →       65.43 ms   (+1.91%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.05 ms →       16.36 ms   (+1.91%) |       4   →       4              |       64.20 ms →       65.43 ms   (+1.91%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.31 ms →       40.23 ms   (-0.22%) |       4   →       4              |      161.26 ms →      160.91 ms   (-0.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       15.97 ms →       16.22 ms   (+1.61%) |       4   →       4              |       63.86 ms →       64.89 ms   (+1.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.96 ms →       16.22 ms   (+1.61%) |       4   →       4              |       63.85 ms →       64.88 ms   (+1.61%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.37 ms →       54.31 ms   (-0.11%) |       4   →       4              |      217.47 ms →      217.23 ms   (-0.11%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.30 ms →       36.24 ms   (-0.18%) |       4   →       4              |      145.20 ms →      144.94 ms   (-0.18%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.96 ms →        1.95 ms   (-0.72%) |       4   →       4              |        7.85 ms →        7.80 ms   (-0.72%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.29 ms →       40.27 ms   (-0.04%) |       4   →       4              |      161.15 ms →      161.07 ms   (-0.04%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.00 ms →        7.05 ms   (+0.70%) |       4   →       4              |       28.00 ms →       28.20 ms   (+0.70%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.13 ms →       28.41 ms   (+4.74%) |       8   →       8              |      217.00 ms →      227.28 ms   (+4.74%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.94 ms →       14.76 ms   (-1.19%) |       8   →       8              |      119.53 ms →      118.11 ms   (-1.19%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.90 ms →       14.72 ms   (-1.20%) |       8   →       8              |      119.17 ms →      117.74 ms   (-1.20%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       51.13 ns →       58.38 ns  (+14.18%) |       8   →       8              |      409.00 ns →      467.00 ns  (+14.18%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.70 ms →       14.53 ms   (-1.16%) |       8   →       8              |      117.62 ms →      116.26 ms   (-1.16%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       21.25 ns →       33.63 ns  (+58.24%) |       8   →       8              |      170.00 ns →      269.00 ns  (+58.24%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      118.19 ms →      121.85 ms   (+3.10%) |       4   →       4              |      472.75 ms →      487.41 ms   (+3.10%) | 
  │ │ └ sddk::wf_trans                                                  |       26.70 ms →       26.69 ms   (-0.02%) |       4   →       4              |      106.79 ms →      106.76 ms   (-0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.56 ms →       26.55 ms   (-0.04%) |       4   →       4              |      106.25 ms →      106.21 ms   (-0.04%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      343.50 ns →      392.00 ns  (+14.12%) |       4   →       4              |        1.37 μs →        1.57 μs  (+14.12%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      212.25 s  →      211.45 s    (-0.38%) |       1   →       1              |      212.25 s  →      211.45 s    (-0.38%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.70 ms →        5.68 ms   (-0.37%) |      19   →      19              |      108.33 ms →      107.93 ms   (-0.37%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.15 s  →        8.12 s    (-0.37%) |      26   →      26              |      211.88 s  →      211.09 s    (-0.37%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.03 ms →        4.59 ms   (-8.81%) |      26   →      26              |      130.72 ms →      119.21 ms   (-8.81%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.43 ms →        4.23 ms   (-4.48%) |      26   →      26              |      115.17 ms →      110.01 ms   (-4.48%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      990.90 μs →      961.87 μs   (-2.93%) |      26   →      26              |       25.76 ms →       25.01 ms   (-2.93%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.38 ms →        2.38 ms   (+0.09%) |      26   →      26              |       61.88 ms →       61.94 ms   (+0.09%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       63.93 μs →       64.47 μs   (+0.86%) |      52   →      52              |        3.32 ms →        3.35 ms   (+0.86%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      169.95 μs →       90.99 μs  (-46.46%) |      26   →      26              |        4.42 ms →        2.37 ms  (-46.46%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |      227.63 μs →       65.58 μs  (-71.19%) |      26   →      26              |        5.92 ms →        1.71 ms  (-71.19%) | 
  │ │ ├ sirius::Band::solve                                             |        6.05 s  →        6.03 s    (-0.31%) |      26   →      26              |      157.32 s  →      156.83 s    (-0.31%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      391.93 μs →      322.15 μs  (-17.80%) |     104   →     104              |       40.76 ms →       33.50 ms  (-17.80%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      386.41 μs →      316.72 μs  (-18.04%) |     104   →     104              |       40.19 ms →       32.94 ms  (-18.04%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.00 μs →        4.11 μs   (+2.67%) |     104   →     104              |      416.31 μs →      427.44 μs   (+2.67%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.51 s  →        1.51 s    (-0.31%) |     104   →     104              |      157.27 s  →      156.79 s    (-0.31%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.00 ms →       11.95 ms   (-0.41%) |     104   →     104              |        1.25 s  →        1.24 s    (-0.41%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      752.42 ns →      712.47 ns   (-5.31%) |     624   →     624              |      469.51 μs →      444.58 μs   (-5.31%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.86 ms →        1.84 ms   (-1.21%) |     104   →     104              |      193.38 ms →      191.03 ms   (-1.21%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      354.01 μs →      354.49 μs   (+0.14%) |     104   →     104              |       36.82 ms →       36.87 ms   (+0.14%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      559.55 μs →      553.69 μs   (-1.05%) |     208   →     208              |      116.39 ms →      115.17 ms   (-1.05%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.49 s  →        1.48 s    (-0.31%) |     104   →     104              |      154.89 s  →      154.41 s    (-0.31%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       66.72 ms →       67.28 ms   (+0.84%) |     982   →     974     (-0.81%) |       65.52 s  →       65.53 s    (+0.02%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.61 ms →       42.92 ms   (+0.73%) |     982   →     974     (-0.81%) |       41.84 s  →       41.81 s    (-0.09%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.51 ms →        8.56 ms   (+0.55%) |     982   →     974     (-0.81%) |        8.36 s  →        8.34 s    (-0.27%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      212.52 μs →      215.88 μs   (+1.58%) |     982   →     974     (-0.81%) |      208.69 ms →      210.27 ms   (+0.75%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.99 ms →        2.00 ms   (+0.77%) |     104   →     104              |      206.84 ms →      208.43 ms   (+0.77%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.57 ms →        6.62 ms   (+0.75%) |     982   →     974     (-0.81%) |        6.45 s  →        6.45 s    (-0.07%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       80.94 μs →       83.19 μs   (+2.79%) |     982   →     974     (-0.81%) |       79.48 ms →       81.03 ms   (+1.95%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      741.14 μs →      756.73 μs   (+2.10%) |     104   →     104              |       77.08 ms →       78.70 ms   (+2.10%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.38 ms →        9.41 ms   (+0.26%) |     982   →     974     (-0.81%) |        9.22 s  →        9.16 s    (-0.56%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.93 ms →        5.93 ms   (-0.14%) |     982   →     974     (-0.81%) |        5.83 s  →        5.77 s    (-0.96%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (+0.07%) |     982   →     974     (-0.81%) |        1.49 s  →        1.48 s    (-0.74%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.17 ms →        8.25 ms   (+1.05%) |     982   →     974     (-0.81%) |        8.02 s  →        8.04 s    (+0.23%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.18 ms →        1.18 ms   (-0.21%) |     982   →     974     (-0.81%) |        1.16 s  →        1.15 s    (-1.02%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.20 ms →        7.28 ms   (+1.14%) |    1.96 K →    1.95 K   (-0.81%) |       14.14 s  →       14.18 s    (+0.32%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.76 ms →       27.99 ms   (+0.85%) |     982   →     974     (-0.81%) |       27.26 s  →       27.26 s    (+0.03%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.87 ms →        1.88 ms   (+0.32%) |    1.86 K →    1.84 K   (-0.86%) |        3.49 s  →        3.47 s    (-0.54%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       75.90 ns →       94.20 ns  (+24.10%) |    1.86 K →    1.84 K   (-0.86%) |      141.18 μs →      173.70 μs  (+23.03%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.87 ms →        1.87 ms   (+0.32%) |    1.86 K →    1.84 K   (-0.86%) |        3.47 s  →        3.45 s    (-0.55%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       75.80 ns →       71.88 ns   (-5.17%) |    1.86 K →    1.84 K   (-0.86%) |      140.99 μs →      132.55 μs   (-5.99%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      821.46 μs →      799.12 μs   (-2.72%) |     982   →     974     (-0.81%) |      806.67 ms →      778.34 ms   (-3.51%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      744.93 μs →      752.18 μs   (+0.97%) |     982   →     974     (-0.81%) |      731.52 ms →      732.62 ms   (+0.15%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.43 ms →        5.49 ms   (+1.08%) |    3.82 K →    3.79 K   (-0.84%) |       20.76 s  →       20.81 s    (+0.23%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.70 ms →        3.74 ms   (+1.09%) |    5.58 K →    5.53 K   (-0.86%) |       20.64 s  →       20.68 s    (+0.23%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.19 ms →        5.14 ms   (-0.82%) |     982   →     974     (-0.81%) |        5.09 s  →        5.01 s    (-1.63%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.39 ms →        3.39 ms   (+0.26%) |     982   →     974     (-0.81%) |        3.33 s  →        3.31 s    (-0.56%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       87.04 ns →       76.55 ns  (-12.05%) |     982   →     974     (-0.81%) |       85.47 μs →       74.56 μs  (-12.77%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.37 ms →        3.38 ms   (+0.26%) |     982   →     974     (-0.81%) |        3.31 s  →        3.29 s    (-0.56%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.03 ns →       43.75 ns   (+1.67%) |     982   →     974     (-0.81%) |       42.26 μs →       42.61 μs   (+0.84%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       33.20 ms →       33.16 ms   (-0.13%) |     982   →     974     (-0.81%) |       32.61 s  →       32.30 s    (-0.95%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.92 ms →       10.68 ms   (-2.15%) |     953   →     946     (-0.73%) |       10.40 s  →       10.11 s    (-2.87%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.51 ms →       10.31 ms   (-1.94%) |     911   →     902     (-0.99%) |        9.58 s  →        9.30 s    (-2.91%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.24 ms →        5.13 ms   (-1.97%) |    1.82 K →    1.80 K   (-0.99%) |        9.54 s  →        9.26 s    (-2.94%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      637.48 μs →      624.53 μs   (-2.03%) |     911   →     902     (-0.99%) |      580.74 ms →      563.33 ms   (-3.00%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.41 ms →       41.08 ms   (+1.67%) |     346   →     345     (-0.29%) |       13.98 s  →       14.17 s    (+1.38%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       23.65 ms →       24.06 ms   (+1.73%) |     588   →     586     (-0.34%) |       13.91 s  →       14.10 s    (+1.39%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       16.69 ms →       16.99 ms   (+1.78%) |     830   →     827     (-0.36%) |       13.86 s  →       14.05 s    (+1.42%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      481.16 ns →      534.65 ns  (+11.12%) |     104   →     104              |       50.04 μs →       55.60 μs  (+11.12%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.62 μs →       23.76 μs   (+5.01%) |      26   →      26              |      588.20 μs →      617.64 μs   (+5.01%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      597.55 μs →      606.44 μs   (+1.49%) |      26   →      26              |       15.54 ms →       15.77 ms   (+1.49%) | 
  │ │ ├ sirius::Density::generate                                       |      892.42 ms →      895.36 ms   (+0.33%) |      26   →      26              |       23.20 s  →       23.28 s    (+0.33%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      525.08 ms →      524.03 ms   (-0.20%) |      26   →      26              |       13.65 s  →       13.62 s    (-0.20%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.37 ms →       24.37 ms   (+0.01%) |     104   →     104              |        2.53 s  →        2.53 s    (+0.01%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.95 μs →        5.88 μs   (-1.14%) |     104   →     104              |      618.52 μs →      611.48 μs   (-1.14%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.55 μs →       12.66 μs   (+0.88%) |       8   →       8              |      100.40 μs →      101.29 μs   (+0.88%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.25 ms →       20.26 ms   (+0.07%) |     104   →     104              |        2.11 s  →        2.11 s    (+0.07%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.80 ms →       29.83 ms   (+0.10%) |     104   →     104              |        3.10 s  →        3.10 s    (+0.10%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.84 μs →       10.87 μs   (+0.22%) |     104   →     104              |        1.13 ms →        1.13 ms   (+0.22%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (-0.12%) |     104   →     104              |      151.87 ms →      151.69 ms   (-0.12%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.86 ms →       27.89 ms   (+0.11%) |     104   →     104              |        2.90 s  →        2.90 s    (+0.11%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.73 ms →        3.75 ms   (+0.55%) |     104   →     104              |      387.49 ms →      389.63 ms   (+0.55%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      469.98 ns →      501.66 ns   (+6.74%) |     104   →     104              |       48.88 μs →       52.17 μs   (+6.74%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.73 ms →       42.50 ms   (-0.53%) |     104   →     104              |        4.44 s  →        4.42 s    (-0.53%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.63 ms   (-0.70%) |      26   →      26              |       42.69 ms →       42.40 ms   (-0.70%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.97 ms →       88.98 ms   (+0.01%) |      26   →      26              |        2.31 s  →        2.31 s    (+0.01%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.74 ms →       88.75 ms   (+0.01%) |      26   →      26              |        2.31 s  →        2.31 s    (+0.01%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      274.82 ms →      277.76 ms   (+1.07%) |      26   →      26              |        7.15 s  →        7.22 s    (+1.07%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      274.82 ms →      277.76 ms   (+1.07%) |      26   →      26              |        7.15 s  →        7.22 s    (+1.07%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.41 ms →       24.53 ms   (+0.48%) |      26   →      26              |      634.62 ms →      637.69 ms   (+0.48%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      224.67 ms →      227.35 ms   (+1.19%) |      26   →      26              |        5.84 s  →        5.91 s    (+1.19%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.89 ms →       24.09 ms   (+0.86%) |      26   →      26              |      621.07 ms →      626.41 ms   (+0.86%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.93 ms →       81.54 ms   (+0.75%) |      26   →      26              |        2.10 s  →        2.12 s    (+0.75%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.00 ms →        8.44 ms   (+5.52%) |      26   →      26              |      208.02 ms →      219.51 ms   (+5.52%) | 
  │ │ ├ sirius::Density::mix                                            |      219.45 ms →      203.33 ms   (-7.34%) |      26   →      26              |        5.71 s  →        5.29 s    (-7.34%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      963.30 μs →      930.40 μs   (-3.42%) |      26   →      26              |       25.05 ms →       24.19 ms   (-3.42%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.75 ms →       10.46 ms   (-2.71%) |     334   →     334              |        3.59 s  →        3.49 s    (-2.71%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.44 ms →        9.98 ms   (-4.42%) |     334   →     334              |        3.49 s  →        3.33 s    (-4.42%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.44 ms →        9.98 ms   (-4.43%) |     334   →     334              |        3.49 s  →        3.33 s    (-4.43%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.30 ms →        6.99 ms  (+10.87%) |      26   →      26              |      163.82 ms →      181.63 ms  (+10.87%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.50 ms →        6.14 ms  (+11.76%) |      26   →      26              |      142.90 ms →      159.70 ms  (+11.76%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.19 ms →      580.87 ms   (+0.12%) |      26   →      26              |       15.09 s  →       15.10 s    (+0.12%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.90 ms →      136.94 ms   (+0.03%) |      26   →      26              |        3.56 s  →        3.56 s    (+0.03%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.10 ms →       18.97 ms  (+25.65%) |      26   →      26              |      392.56 ms →      493.23 ms  (+25.65%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.63 ms →       10.24 ms   (-3.62%) |      26   →      26              |      276.27 ms →      266.27 ms   (-3.62%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.38 ms →        9.92 ms   (-4.46%) |      26   →      26              |      269.86 ms →      257.82 ms   (-4.46%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.38 ms →        9.92 ms   (-4.46%) |      26   →      26              |      269.84 ms →      257.81 ms   (-4.46%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      552.18 μs →      548.40 μs   (-0.68%) |      52   →      52              |       28.71 ms →       28.52 ms   (-0.68%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       50.01 ms →       49.84 ms   (-0.34%) |      26   →      26              |        1.30 s  →        1.30 s    (-0.34%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.62 ms →       47.52 ms   (-0.23%) |      26   →      26              |        1.24 s  →        1.24 s    (-0.23%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.07 ms →        3.00 ms   (-2.00%) |      52   →      52              |      159.42 ms →      156.23 ms   (-2.00%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.34 ms →        5.79 ms   (+8.56%) |      26   →      26              |      138.77 ms →      150.64 ms   (+8.56%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.76 ms →        6.85 ms   (+1.32%) |      26   →      26              |      175.69 ms →      178.01 ms   (+1.32%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.95 ms →       91.05 ms   (+0.11%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.11%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.15 ms →      293.81 ms   (+0.23%) |      26   →      26              |        7.62 s  →        7.64 s    (+0.23%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      279.15 ms →      280.84 ms   (+0.61%) |      26   →      26              |        7.26 s  →        7.30 s    (+0.61%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      279.15 ms →      280.84 ms   (+0.61%) |      26   →      26              |        7.26 s  →        7.30 s    (+0.61%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.00 ms →       27.13 ms   (+0.48%) |      26   →      26              |      702.01 ms →      705.40 ms   (+0.48%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.36 ms →      225.97 ms   (+0.72%) |      26   →      26              |        5.83 s  →        5.88 s    (+0.72%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.94 ms →       23.93 ms   (-0.07%) |      26   →      26              |      622.47 ms →      622.07 ms   (-0.07%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.08 ms →        5.58 ms   (-8.22%) |      26   →      26              |      158.18 ms →      145.18 ms   (-8.22%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.48 ms →       10.76 ms   (+2.66%) |     182   →     182              |        1.91 s  →        1.96 s    (+2.66%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.92 ms →       10.32 ms   (+4.02%) |     182   →     182              |        1.81 s  →        1.88 s    (+4.02%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.92 ms →       10.32 ms   (+4.02%) |     182   →     182              |        1.81 s  →        1.88 s    (+4.02%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.61 ms →       10.18 ms   (-4.06%) |      78   →      78              |      827.39 ms →      793.78 ms   (-4.06%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.30 ms →        9.81 ms   (-4.74%) |      78   →      78              |      803.36 ms →      765.32 ms   (-4.74%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.97 ms →        9.99 ms   (+0.18%) |      26   →      26              |      259.31 ms →      259.77 ms   (+0.18%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      221.42 μs →      110.67 μs  (-50.02%) |      26   →      26              |        5.76 ms →        2.88 ms  (-50.02%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      216.49 μs →      105.31 μs  (-51.36%) |      26   →      26              |        5.63 ms →        2.74 ms  (-51.36%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.10 ms →        5.11 ms   (+0.23%) |       2   →       2              |       10.19 ms →       10.22 ms   (+0.23%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.01 ms →       10.30 ms   (+2.83%) |       6   →       6              |       60.08 ms →       61.78 ms   (+2.83%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.72 ms →       10.29 ms   (+5.77%) |       6   →       6              |       58.34 ms →       61.71 ms   (+5.77%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.72 ms →       10.29 ms   (+5.77%) |       6   →       6              |       58.34 ms →       61.71 ms   (+5.77%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.45 ms →        9.73 ms   (-6.85%) |       3   →       3              |       31.34 ms →       29.19 ms   (-6.85%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.04 ms →        9.72 ms   (-3.21%) |       3   →       3              |       30.13 ms →       29.16 ms   (-3.21%) | 
  ├ sirius::Periodic_function|inner                                     |       10.03 ms →       10.22 ms   (+1.89%) |       2   →       2              |       20.06 ms →       20.44 ms   (+1.89%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms →       10.21 ms   (+1.89%) |       2   →       2              |       20.04 ms →       20.42 ms   (+1.89%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms →       10.21 ms   (+1.89%) |       2   →       2              |       20.04 ms →       20.42 ms   (+1.89%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.52 ms →        9.73 ms   (-7.50%) |       1   →       1              |       10.52 ms →        9.73 ms   (-7.50%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.39 ms →        9.73 ms   (-6.44%) |       1   →       1              |       10.39 ms →        9.73 ms   (-6.44%) | 
- └ sirius::finalize                                                    |      293.38 ms →      333.20 ms  (+13.57%) |       1   →       1              |      293.38 ms →      333.20 ms  (+13.57%) | 
  ====================================================================================================================================================================================================
```
