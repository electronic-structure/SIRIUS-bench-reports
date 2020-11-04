# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 4abe991ed1b67a61e2f44af0d6336c92b3f43afd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      218.92 s  →      216.20 s    (-1.24%) |       1   →       1              |      218.92 s  →      216.20 s    (-1.24%) | 
  ├ sirius::initialize                                                  |        2.64 s  →        2.66 s    (+0.64%) |       1   →       1              |        2.64 s  →        2.66 s    (+0.64%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.94 s    (+0.34%) |       1   →       1              |        2.93 s  →        2.94 s    (+0.34%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |        6.03 ms →      348.32 μs  (-94.22%) |       1   →       1              |        6.03 ms →      348.32 μs  (-94.22%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      141.33 ms →      149.03 ms   (+5.45%) |       1   →       1              |      141.33 ms →      149.03 ms   (+5.45%) | 
  │ │ ├ sirius::Atom_type::init                                         |       59.27 ms →       63.10 ms   (+6.47%) |       2   →       2              |      118.54 ms →      126.21 ms   (+6.47%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.71 ms →       22.75 ms   (+0.15%) |       1   →       1              |       22.71 ms →       22.75 ms   (+0.15%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.42 ms →        6.37 ms   (-0.68%) |       1   →       1              |        6.42 ms →        6.37 ms   (-0.68%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.25 ms →       16.33 ms   (+0.50%) |       1   →       1              |       16.25 ms →       16.33 ms   (+0.50%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.23 ms →       16.31 ms   (+0.49%) |       1   →       1              |       16.23 ms →       16.31 ms   (+0.49%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.18 ms →        4.19 ms   (+0.24%) |       1   →       1              |        4.18 ms →        4.19 ms   (+0.24%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.79%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.79%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      110.05 μs →      105.52 μs   (-4.11%) |       1   →       1              |      110.05 μs →      105.52 μs   (-4.11%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.74 s    (+0.38%) |       1   →       1              |        2.73 s  →        2.74 s    (+0.38%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.82 ms →       10.90 ms   (+0.67%) |       1   →       1              |       10.82 ms →       10.90 ms   (+0.67%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.42 ms   (-0.29%) |       1   →       1              |        4.44 ms →        4.42 ms   (-0.29%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.44 ms   (+1.36%) |       1   →       1              |        6.35 ms →        6.44 ms   (+1.36%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.42 ms   (+1.37%) |       1   →       1              |        6.33 ms →        6.42 ms   (+1.37%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        3.91 ms   (+2.25%) |       1   →       1              |        3.82 ms →        3.91 ms   (+2.25%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.23%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.23%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      106.41 μs →      102.15 μs   (-4.00%) |       1   →       1              |      106.41 μs →      102.15 μs   (-4.00%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.58 ms →       62.99 ms   (+0.65%) |       2   →       2              |      125.16 ms →      125.98 ms   (+0.65%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.13 ms   (+0.05%) |       2   →       2              |       10.26 ms →       10.26 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.47 ms   (+0.23%) |       1   →       1              |        4.46 ms →        4.47 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.72 ms →       21.81 ms   (+0.43%) |       2   →       2              |       43.43 ms →       43.62 ms   (+0.43%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.78 ms →       14.78 ms   (-0.02%) |       2   →       2              |       29.56 ms →       29.55 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.65 ms →       19.57 ms   (-0.37%) |       4   →       4              |       78.59 ms →       78.30 ms   (-0.37%) | 
  │   ├ sddk::Gvec::init                                                |      170.75 ms →      171.61 ms   (+0.50%) |       2   →       2              |      341.51 ms →      343.21 ms   (+0.50%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.94 ms →      128.27 ms   (+0.26%) |       2   →       2              |      255.88 ms →      256.54 ms   (+0.26%) | 
  │   ├ sddk::Gvec_shells                                               |      184.30 ms →      174.33 ms   (-5.41%) |       1   →       1              |      184.30 ms →      174.33 ms   (-5.41%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.33 ms   (+1.09%) |       1   →       1              |        1.31 ms →        1.33 ms   (+1.09%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.09 ms →      291.43 ms   (-1.24%) |       2   →       2              |      590.18 ms →      582.87 ms   (-1.24%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       74.33 ms →       75.71 ms   (+1.87%) |       1   →       1              |       74.33 ms →       75.71 ms   (+1.87%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.84 μs →        2.51 μs  (-11.72%) |       4   →       4              |       11.37 μs →       10.03 μs  (-11.72%) | 
  │ └ sirius::K_point_set::initialize                                   |       74.23 ms →       75.61 ms   (+1.87%) |       1   →       1              |       74.23 ms →       75.61 ms   (+1.87%) | 
  │   └ sirius::K_point::initialize                                     |       18.53 ms →       18.88 ms   (+1.88%) |       4   →       4              |       74.13 ms →       75.53 ms   (+1.88%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       13.95 ms →       14.29 ms   (+2.47%) |       4   →       4              |       55.79 ms →       57.16 ms   (+2.47%) | 
  │     │ └ sddk::Gvec::init                                            |        3.85 ms →        3.87 ms   (+0.44%) |       4   →       4              |       15.42 ms →       15.49 ms   (+0.44%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.05 μs →        9.70 μs   (+7.17%) |       4   →       4              |       36.22 μs →       38.81 μs   (+7.17%) | 
  │     └ sirius::K_point::update                                       |        3.30 ms →        3.30 ms   (+0.19%) |       4   →       4              |       13.18 ms →       13.21 ms   (+0.19%) | 
  │       └ sirius::Beta_projectors                                     |        1.80 ms →        1.78 ms   (-0.94%) |       4   →       4              |        7.18 ms →        7.12 ms   (-0.94%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      947.24 μs →      930.52 μs   (-1.76%) |       4   →       4              |        3.79 ms →        3.72 ms   (-1.76%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.30 ms →        5.30 ms   (+0.17%) |       2   →       2              |       10.59 ms →       10.61 ms   (+0.17%) | 
  ├ sirius::Potential                                                   |      160.89 ms →      158.69 ms   (-1.37%) |       1   →       1              |      160.89 ms →      158.69 ms   (-1.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.95 ms →        5.89 ms   (-1.08%) |       6   →       6              |       35.71 ms →       35.32 ms   (-1.08%) | 
  │ └ sirius::Potential::update                                         |      124.46 ms →      122.65 ms   (-1.45%) |       1   →       1              |      124.46 ms →      122.65 ms   (-1.45%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.65 ms →      121.87 ms   (-1.43%) |       1   →       1              |      123.65 ms →      121.87 ms   (-1.43%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      107.28 ms →      111.12 ms   (+3.58%) |       1   →       1              |      107.28 ms →      111.12 ms   (+3.58%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       15.43 ms →        9.81 ms  (-36.39%) |       1   →       1              |       15.43 ms →        9.81 ms  (-36.39%) | 
  ├ sirius::Density                                                     |      135.63 ms →      133.89 ms   (-1.28%) |       1   →       1              |      135.63 ms →      133.89 ms   (-1.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.18 ms →        5.19 ms   (+0.26%) |       2   →       2              |       10.35 ms →       10.38 ms   (+0.26%) | 
  │ └ sirius::Density::update                                           |      125.01 ms →      123.24 ms   (-1.42%) |       1   →       1              |      125.01 ms →      123.24 ms   (-1.42%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.13 ms →      122.80 ms   (-1.07%) |       1   →       1              |      124.13 ms →      122.80 ms   (-1.07%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      114.98 μs →      105.75 μs   (-8.02%) |       1   →       1              |      114.98 μs →      105.75 μs   (-8.02%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.37 ms →      112.28 ms   (+2.67%) |       1   →       1              |      109.37 ms →      112.28 ms   (+2.67%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       14.19 ms →        9.96 ms  (-29.77%) |       1   →       1              |       14.19 ms →        9.96 ms  (-29.77%) | 
  ├ sirius::Density::initial_density                                    |      176.47 ms →      175.89 ms   (-0.33%) |       1   →       1              |      176.47 ms →      175.89 ms   (-0.33%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.85 ms →      110.63 ms   (+1.64%) |       1   →       1              |      108.85 ms →      110.63 ms   (+1.64%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       12.69 ms →       11.26 ms  (-11.34%) |       2   →       2              |       25.39 ms →       22.51 ms  (-11.34%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.40 ms →        9.72 ms   (-6.50%) |       1   →       1              |       10.40 ms →        9.72 ms   (-6.50%) | 
  ├ sirius::Potential::generate                                         |      602.42 ms →      594.14 ms   (-1.37%) |       1   →       1              |      602.42 ms →      594.14 ms   (-1.37%) | 
  │ ├ sirius::Potential::poisson                                        |      138.93 ms →      138.69 ms   (-0.17%) |       1   →       1              |      138.93 ms →      138.69 ms   (-0.17%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       21.44 ms →       16.67 ms  (-22.23%) |       1   →       1              |       21.44 ms →       16.67 ms  (-22.23%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.38 ms →       11.15 ms   (+7.44%) |       1   →       1              |       10.38 ms →       11.15 ms   (+7.44%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.36 ms →        9.80 ms   (-5.37%) |       1   →       1              |       10.36 ms →        9.80 ms   (-5.37%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.36 ms →        9.80 ms   (-5.37%) |       1   →       1              |       10.36 ms →        9.80 ms   (-5.37%) | 
  │ ├ sirius::Periodic_function::add                                    |      547.59 μs →      544.32 μs   (-0.60%) |       2   →       2              |        1.10 ms →        1.09 ms   (-0.60%) | 
  │ ├ sirius::Potential::xc                                             |       53.85 ms →       53.73 ms   (-0.21%) |       1   →       1              |       53.85 ms →       53.73 ms   (-0.21%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.41 ms →       51.33 ms   (-0.16%) |       1   →       1              |       51.41 ms →       51.33 ms   (-0.16%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.81 ms →        5.76 ms   (-0.91%) |       2   →       2              |       11.62 ms →       11.51 ms   (-0.91%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.11 ms →        5.22 ms   (+2.29%) |       1   →       1              |        5.11 ms →        5.22 ms   (+2.29%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.67 ms →        5.89 ms   (+3.95%) |       1   →       1              |        5.67 ms →        5.89 ms   (+3.95%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.59 ms →       92.63 ms   (+0.04%) |       1   →       1              |       92.59 ms →       92.63 ms   (+0.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      308.91 ms →      300.73 ms   (-2.65%) |       1   →       1              |      308.91 ms →      300.73 ms   (-2.65%) | 
  ├ sirius::Hamiltonian0                                                |        8.39 ms →        8.39 ms   (+0.00%) |       1   →       1              |        8.39 ms →        8.39 ms   (+0.00%) | 
  │ ├ sirius::Local_operator                                            |        8.05 ms →        8.05 ms   (+0.00%) |       1   →       1              |        8.05 ms →        8.05 ms   (+0.00%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.78 ms →        4.77 ms   (-0.15%) |       1   →       1              |        4.78 ms →        4.77 ms   (-0.15%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.35 ms   (+0.36%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.36%) | 
  │ ├ sirius::Non_local_operator                                        |       62.26 μs →       62.52 μs   (+0.41%) |       2   →       2              |      124.53 μs →      125.04 μs   (+0.41%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.23 μs →       91.10 μs   (-3.32%) |       1   →       1              |       94.23 μs →       91.10 μs   (-3.32%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.81 μs →       69.12 μs   (+0.45%) |       1   →       1              |       68.81 μs →       69.12 μs   (+0.45%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.10 s    (+0.18%) |       1   →       1              |        3.09 s  →        3.10 s    (+0.18%) | 
  │ ├ sirius::Hamiltonian_k                                             |      385.95 μs →      394.52 μs   (+2.22%) |       4   →       4              |        1.54 ms →        1.58 ms   (+2.22%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      381.10 μs →      389.52 μs   (+2.21%) |       4   →       4              |        1.52 ms →        1.56 ms   (+2.21%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.13 μs →        3.34 μs   (+6.74%) |       4   →       4              |       12.51 μs →       13.35 μs   (+6.74%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      772.31 ms →      773.73 ms   (+0.18%) |       4   →       4              |        3.09 s  →        3.09 s    (+0.18%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.25 ms →       32.37 ms   (+0.37%) |      16   →      16              |      516.07 ms →      517.99 ms   (+0.37%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.65 ms →       14.57 ms   (-0.56%) |       4   →       4              |       58.62 ms →       58.29 ms   (-0.56%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.29 ms →        5.28 ms   (-0.25%) |       4   →       4              |       21.17 ms →       21.12 ms   (-0.25%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      353.29 ms →      353.31 ms   (+0.00%) |       4   →       4              |        1.41 s  →        1.41 s    (+0.00%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      256.88 ms →      256.77 ms   (-0.04%) |       4   →       4              |        1.03 s  →        1.03 s    (-0.04%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       62.55 ms →       63.06 ms   (+0.82%) |       4   →       4              |      250.19 ms →      252.24 ms   (+0.82%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.27 ms →       16.38 ms   (+0.69%) |       4   →       4              |       65.09 ms →       65.53 ms   (+0.69%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.27 ms →       16.38 ms   (+0.68%) |       4   →       4              |       65.08 ms →       65.52 ms   (+0.68%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       39.75 ms →       40.19 ms   (+1.10%) |       4   →       4              |      159.00 ms →      160.75 ms   (+1.10%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.02 ms →       16.09 ms   (+0.44%) |       4   →       4              |       64.07 ms →       64.36 ms   (+0.44%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.01 ms →       16.09 ms   (+0.44%) |       4   →       4              |       64.06 ms →       64.34 ms   (+0.44%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.48 ms →       53.87 ms   (-1.12%) |       4   →       4              |      217.92 ms →      215.47 ms   (-1.12%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.46 ms →       35.81 ms   (-1.79%) |       4   →       4              |      145.85 ms →      143.24 ms   (-1.79%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.95 ms   (+0.13%) |       4   →       4              |        7.79 ms →        7.80 ms   (+0.13%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.15 ms →       40.25 ms   (+0.24%) |       4   →       4              |      160.60 ms →      160.99 ms   (+0.24%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        6.93 ms →        7.10 ms   (+2.40%) |       4   →       4              |       27.73 ms →       28.40 ms   (+2.40%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.14 ms →       27.15 ms   (+0.04%) |       8   →       8              |      217.13 ms →      217.21 ms   (+0.04%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.85 ms →       14.81 ms   (-0.24%) |       8   →       8              |      118.78 ms →      118.49 ms   (-0.24%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.80 ms →       14.77 ms   (-0.25%) |       8   →       8              |      118.43 ms →      118.13 ms   (-0.25%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       89.50 ns →       30.75 ns  (-65.64%) |       8   →       8              |      716.00 ns →      246.00 ns  (-65.64%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.62 ms →       14.58 ms   (-0.28%) |       8   →       8              |      116.99 ms →      116.66 ms   (-0.28%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       21.38 ns →       17.13 ns  (-19.88%) |       8   →       8              |      171.00 ns →      137.00 ns  (-19.88%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      118.57 ms →      119.09 ms   (+0.44%) |       4   →       4              |      474.28 ms →      476.37 ms   (+0.44%) | 
  │ │ └ sddk::wf_trans                                                  |       26.63 ms →       26.63 ms   (-0.00%) |       4   →       4              |      106.53 ms →      106.53 ms   (-0.00%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.46 ms →       26.38 ms   (-0.30%) |       4   →       4              |      105.84 ms →      105.52 ms   (-0.30%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      356.50 ns →      393.25 ns  (+10.31%) |       4   →       4              |        1.43 μs →        1.57 μs  (+10.31%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      208.33 s  →      205.53 s    (-1.34%) |       1   →       1              |      208.33 s  →      205.53 s    (-1.34%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.88 ms →        5.85 ms   (-0.50%) |      19   →      19              |      111.65 ms →      111.10 ms   (-0.50%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.00 s  →        8.21 s    (+2.60%) |      26   →      25     (-3.85%) |      207.93 s  →      205.14 s    (-1.34%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.44 ms →        4.46 ms   (+0.41%) |      26   →      25     (-3.85%) |      115.54 ms →      111.56 ms   (-3.45%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.09 ms →        4.11 ms   (+0.40%) |      26   →      25     (-3.85%) |      106.35 ms →      102.67 ms   (-3.46%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      971.37 μs →      976.93 μs   (+0.57%) |      26   →      25     (-3.85%) |       25.26 ms →       24.42 ms   (-3.30%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.23 ms →        2.24 ms   (+0.47%) |      26   →      25     (-3.85%) |       57.93 ms →       55.97 ms   (-3.39%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.20 μs →       63.98 μs   (-0.35%) |      52   →      50     (-3.85%) |        3.34 ms →        3.20 ms   (-4.18%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       90.92 μs →       90.54 μs   (-0.42%) |      26   →      25     (-3.85%) |        2.36 ms →        2.26 ms   (-4.25%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.76 μs →       66.37 μs   (+0.92%) |      26   →      25     (-3.85%) |        1.71 ms →        1.66 ms   (-2.96%) | 
  │ │ ├ sirius::Band::solve                                             |        5.90 s  →        6.12 s    (+3.75%) |      26   →      25     (-3.85%) |      153.49 s  →      153.12 s    (-0.24%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      321.71 μs →      343.20 μs   (+6.68%) |     104   →     100     (-3.85%) |       33.46 ms →       34.32 ms   (+2.58%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      316.32 μs →      337.55 μs   (+6.71%) |     104   →     100     (-3.85%) |       32.90 ms →       33.76 ms   (+2.61%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.05 μs →        4.25 μs   (+4.94%) |     104   →     100     (-3.85%) |      421.36 μs →      425.16 μs   (+0.90%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.48 s  →        1.53 s    (+3.75%) |     104   →     100     (-3.85%) |      153.45 s  →      153.08 s    (-0.24%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.93 ms →       11.98 ms   (+0.40%) |     104   →     100     (-3.85%) |        1.24 s  →        1.20 s    (-3.46%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      667.48 ns →      739.34 ns  (+10.77%) |     624   →     600     (-3.85%) |      416.51 μs →      443.61 μs   (+6.51%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.86 ms   (+1.77%) |     104   →     100     (-3.85%) |      190.29 ms →      186.21 ms   (-2.14%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.37 μs →      353.53 μs   (-0.52%) |     104   →     100     (-3.85%) |       36.96 ms →       35.35 ms   (-4.35%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.16 μs →      566.38 μs   (+2.95%) |     208   →     200     (-3.85%) |      114.43 ms →      113.28 ms   (-1.01%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.45 s  →        1.51 s    (+3.80%) |     104   →     100     (-3.85%) |      151.08 s  →      150.79 s    (-0.19%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.80 ms →       67.90 ms   (-2.73%) |     931   →     947     (+1.72%) |       64.98 s  →       64.30 s    (-1.05%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.67 ms →       43.40 ms   (-2.85%) |     931   →     947     (+1.72%) |       41.59 s  →       41.10 s    (-1.18%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.88 ms →        8.65 ms   (-2.53%) |     931   →     947     (+1.72%) |        8.26 s  →        8.19 s    (-0.86%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      223.89 μs →      222.59 μs   (-0.58%) |     931   →     947     (+1.72%) |      208.44 ms →      210.79 ms   (+1.13%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.99 ms →        2.09 ms   (+5.06%) |     104   →     100     (-3.85%) |      206.64 ms →      208.74 ms   (+1.02%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.83 ms →        6.66 ms   (-2.52%) |     931   →     947     (+1.72%) |        6.36 s  →        6.31 s    (-0.85%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       86.16 μs →       84.92 μs   (-1.44%) |     931   →     947     (+1.72%) |       80.22 ms →       80.42 ms   (+0.25%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      749.40 μs →      780.67 μs   (+4.17%) |     104   →     100     (-3.85%) |       77.94 ms →       78.07 ms   (+0.17%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.78 ms →        9.51 ms   (-2.69%) |     931   →     947     (+1.72%) |        9.10 s  →        9.01 s    (-1.02%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.14 ms →        6.00 ms   (-2.28%) |     931   →     947     (+1.72%) |        5.72 s  →        5.69 s    (-0.60%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.52 ms   (-0.40%) |     931   →     947     (+1.72%) |        1.42 s  →        1.44 s    (+1.31%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.57 ms →        8.32 ms   (-3.02%) |     931   →     947     (+1.72%) |        7.98 s  →        7.87 s    (-1.36%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.26 ms →        1.23 ms   (-2.71%) |     931   →     947     (+1.72%) |        1.17 s  →        1.16 s    (-1.04%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.50 ms →        7.32 ms   (-2.43%) |    1.86 K →    1.89 K   (+1.72%) |       13.97 s  →       13.86 s    (-0.75%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       29.09 ms →       28.26 ms   (-2.85%) |     931   →     947     (+1.72%) |       27.09 s  →       26.77 s    (-1.18%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.97 ms →        1.89 ms   (-4.33%) |    1.76 K →    1.79 K   (+2.05%) |        3.47 s  →        3.39 s    (-2.38%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       72.26 ns →       60.19 ns  (-16.71%) |    1.76 K →    1.79 K   (+2.05%) |      127.04 μs →      107.98 μs  (-15.01%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.97 ms →        1.88 ms   (-4.29%) |    1.76 K →    1.79 K   (+2.05%) |        3.45 s  →        3.37 s    (-2.33%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       67.68 ns →       87.59 ns  (+29.43%) |    1.76 K →    1.79 K   (+2.05%) |      118.97 μs →      157.14 μs  (+32.08%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      823.95 μs →      801.05 μs   (-2.78%) |     931   →     947     (+1.72%) |      767.10 ms →      758.60 ms   (-1.11%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      742.15 μs →      726.61 μs   (-2.09%) |     931   →     947     (+1.72%) |      690.94 ms →      688.10 ms   (-0.41%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.72 ms →        5.55 ms   (-2.82%) |    3.62 K →    3.69 K   (+1.88%) |       20.69 s  →       20.48 s    (-0.99%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.90 ms →        3.78 ms   (-3.00%) |    5.27 K →    5.38 K   (+2.05%) |       20.55 s  →       20.34 s    (-1.01%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.29 ms →        5.28 ms   (-0.18%) |     931   →     947     (+1.72%) |        4.93 s  →        5.00 s    (+1.54%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.54 ms →        3.44 ms   (-2.60%) |     931   →     947     (+1.72%) |        3.29 s  →        3.26 s    (-0.93%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       71.31 ns →       51.72 ns  (-27.47%) |     931   →     947     (+1.72%) |       66.39 μs →       48.98 μs  (-26.22%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.52 ms →        3.43 ms   (-2.58%) |     931   →     947     (+1.72%) |        3.28 s  →        3.25 s    (-0.90%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       58.83 ns →       55.97 ns   (-4.86%) |     931   →     947     (+1.72%) |       54.77 μs →       53.01 μs   (-3.22%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       32.74 ms →       32.74 ms   (-0.02%) |     931   →     947     (+1.72%) |       30.48 s  →       31.00 s    (+1.70%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.67 ms →       10.61 ms   (-0.55%) |     904   →     920     (+1.77%) |        9.64 s  →        9.76 s    (+1.21%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.31 ms →       10.23 ms   (-0.78%) |     861   →     878     (+1.97%) |        8.87 s  →        8.98 s    (+1.18%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.13 ms →        5.09 ms   (-0.81%) |    1.72 K →    1.76 K   (+1.97%) |        8.83 s  →        8.93 s    (+1.15%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      623.27 μs →      621.21 μs   (-0.33%) |     861   →     878     (+1.97%) |      536.63 ms →      545.42 ms   (+1.64%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.98 ms →       41.00 ms   (+0.05%) |     340   →     340              |       13.93 s  →       13.94 s    (+0.05%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       24.06 ms →       23.91 ms   (-0.65%) |     576   →     580     (+0.69%) |       13.86 s  →       13.87 s    (+0.04%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       16.98 ms →       16.82 ms   (-0.94%) |     812   →     820     (+0.99%) |       13.79 s  →       13.80 s    (+0.04%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      473.99 ns →      526.83 ns  (+11.15%) |     104   →     100     (-3.85%) |       49.30 μs →       52.68 μs   (+6.87%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.39 μs →       22.33 μs   (-0.31%) |      26   →      25     (-3.85%) |      582.25 μs →      558.14 μs   (-4.14%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      605.77 μs →      602.52 μs   (-0.54%) |      26   →      25     (-3.85%) |       15.75 ms →       15.06 ms   (-4.36%) | 
  │ │ ├ sirius::Density::generate                                       |      890.78 ms →      893.35 ms   (+0.29%) |      26   →      25     (-3.85%) |       23.16 s  →       22.33 s    (-3.57%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      524.72 ms →      525.22 ms   (+0.10%) |      26   →      25     (-3.85%) |       13.64 s  →       13.13 s    (-3.75%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.47 ms →       24.45 ms   (-0.05%) |     104   →     100     (-3.85%) |        2.54 s  →        2.45 s    (-3.90%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.99 μs →        6.31 μs   (+5.29%) |     104   →     100     (-3.85%) |      623.05 μs →      630.76 μs   (+1.24%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.97 μs →       13.59 μs   (+4.81%) |       8   →       8              |      103.75 μs →      108.74 μs   (+4.81%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.34 ms →       20.33 ms   (-0.07%) |     104   →     100     (-3.85%) |        2.12 s  →        2.03 s    (-3.91%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.94 ms →       29.92 ms   (-0.09%) |     104   →     100     (-3.85%) |        3.11 s  →        2.99 s    (-3.93%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.07 μs →       11.35 μs   (+2.58%) |     104   →     100     (-3.85%) |        1.15 ms →        1.14 ms   (-1.36%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (-0.04%) |     104   →     100     (-3.85%) |      151.93 ms →      146.02 ms   (-3.89%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.99 ms →       27.98 ms   (-0.05%) |     104   →     100     (-3.85%) |        2.91 s  →        2.80 s    (-3.89%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.86 ms →        3.85 ms   (-0.16%) |     104   →     100     (-3.85%) |      401.11 ms →      385.05 ms   (-4.00%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      567.34 ns →      526.95 ns   (-7.12%) |     104   →     100     (-3.85%) |       59.00 μs →       52.69 μs  (-10.69%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.39 ms →       42.64 ms   (+0.58%) |     104   →     100     (-3.85%) |        4.41 s  →        4.26 s    (-3.29%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.25%) |      26   →      25     (-3.85%) |       42.74 ms →       40.99 ms   (-4.09%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.99 ms →       89.00 ms   (+0.01%) |      26   →      25     (-3.85%) |        2.31 s  →        2.22 s    (-3.84%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.75 ms →       88.76 ms   (+0.01%) |      26   →      25     (-3.85%) |        2.31 s  →        2.22 s    (-3.83%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      271.62 ms →      276.04 ms   (+1.63%) |      26   →      25     (-3.85%) |        7.06 s  →        6.90 s    (-2.28%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      271.62 ms →      276.04 ms   (+1.63%) |      26   →      25     (-3.85%) |        7.06 s  →        6.90 s    (-2.28%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.66 ms →       24.57 ms   (-0.37%) |      26   →      25     (-3.85%) |      641.18 ms →      614.25 ms   (-4.20%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      221.31 ms →      225.54 ms   (+1.91%) |      26   →      25     (-3.85%) |        5.75 s  →        5.64 s    (-2.01%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.84 ms →       24.12 ms   (+1.14%) |      26   →      25     (-3.85%) |      619.97 ms →      602.92 ms   (-2.75%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.95 ms →       81.48 ms   (+0.65%) |      26   →      25     (-3.85%) |        2.10 s  →        2.04 s    (-3.22%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.89 ms →        7.01 ms  (-29.10%) |      26   →      25     (-3.85%) |      257.20 ms →      175.33 ms  (-31.83%) | 
+ │ │ ├ sirius::Density::mix                                            |      220.00 ms →      199.21 ms   (-9.45%) |      26   →      25     (-3.85%) |        5.72 s  →        4.98 s   (-12.93%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      940.78 μs →      933.26 μs   (-0.80%) |      26   →      25     (-3.85%) |       24.46 ms →       23.33 ms   (-4.61%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.84 ms →       10.25 ms   (-5.48%) |     334   →     319     (-4.49%) |        3.62 s  →        3.27 s    (-9.72%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.42 ms →        9.96 ms   (-4.44%) |     334   →     319     (-4.49%) |        3.48 s  →        3.18 s    (-8.73%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.42 ms →        9.96 ms   (-4.44%) |     334   →     319     (-4.49%) |        3.48 s  →        3.18 s    (-8.73%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.21 ms →        6.54 ms   (-9.34%) |      26   →      25     (-3.85%) |      187.57 ms →      163.52 ms  (-12.82%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.39 ms →        5.69 ms  (-10.85%) |      26   →      25     (-3.85%) |      166.05 ms →      142.34 ms  (-14.28%) | 
  │ │ ├ sirius::Potential::generate                                     |      583.18 ms →      580.21 ms   (-0.51%) |      26   →      25     (-3.85%) |       15.16 s  →       14.51 s    (-4.34%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      141.20 ms →      137.49 ms   (-2.62%) |      26   →      25     (-3.85%) |        3.67 s  →        3.44 s    (-6.37%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       21.45 ms →       16.18 ms  (-24.56%) |      26   →      25     (-3.85%) |      557.66 ms →      404.54 ms  (-27.46%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       12.72 ms →       10.28 ms  (-19.23%) |      26   →      25     (-3.85%) |      330.78 ms →      256.90 ms  (-22.34%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       12.70 ms →        9.90 ms  (-22.10%) |      26   →      25     (-3.85%) |      330.26 ms →      247.38 ms  (-25.10%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       12.70 ms →        9.89 ms  (-22.10%) |      26   →      25     (-3.85%) |      330.24 ms →      247.36 ms  (-25.10%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      553.47 μs →      550.50 μs   (-0.54%) |      52   →      50     (-3.85%) |       28.78 ms →       27.52 ms   (-4.36%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.27 ms →       49.38 ms   (+0.23%) |      26   →      25     (-3.85%) |        1.28 s  →        1.23 s    (-3.62%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.91 ms →       47.05 ms   (+0.30%) |      26   →      25     (-3.85%) |        1.22 s  →        1.18 s    (-3.56%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.03 ms   (-0.22%) |      52   →      50     (-3.85%) |      158.11 ms →      151.69 ms   (-4.06%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.32 ms →        5.40 ms   (+1.45%) |      26   →      25     (-3.85%) |      138.28 ms →      134.89 ms   (-2.45%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.73 ms →        6.80 ms   (+0.98%) |      26   →      25     (-3.85%) |      175.00 ms →      169.92 ms   (-2.90%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.94 ms →       90.92 ms   (-0.02%) |      26   →      25     (-3.85%) |        2.36 s  →        2.27 s    (-3.87%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.63 ms →      293.24 ms   (+0.21%) |      26   →      25     (-3.85%) |        7.61 s  →        7.33 s    (-3.65%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      274.26 ms →      281.47 ms   (+2.63%) |      26   →      25     (-3.85%) |        7.13 s  →        7.04 s    (-1.32%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      274.26 ms →      281.46 ms   (+2.63%) |      26   →      25     (-3.85%) |        7.13 s  →        7.04 s    (-1.32%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.30 ms →       27.09 ms   (-0.76%) |      26   →      25     (-3.85%) |      709.67 ms →      677.16 ms   (-4.58%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      219.44 ms →      226.39 ms   (+3.17%) |      26   →      25     (-3.85%) |        5.71 s  →        5.66 s    (-0.80%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.72 ms →       24.19 ms   (+1.99%) |      26   →      25     (-3.85%) |      616.63 ms →      604.69 ms   (-1.94%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.69 ms →        5.74 ms   (+0.79%) |      26   →      25     (-3.85%) |      147.97 ms →      143.39 ms   (-3.09%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.40 ms →       10.68 ms   (+2.73%) |     182   →     175     (-3.85%) |        1.89 s  →        1.87 s    (-1.22%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.81 ms →       10.21 ms   (+4.05%) |     182   →     175     (-3.85%) |        1.79 s  →        1.79 s    (+0.05%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms →       10.21 ms   (+4.06%) |     182   →     175     (-3.85%) |        1.79 s  →        1.79 s    (+0.05%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.60 ms →       10.22 ms   (-3.53%) |      78   →      75     (-3.85%) |      826.69 ms →      766.81 ms   (-7.24%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.20 ms →        9.76 ms   (-4.29%) |      78   →      75     (-3.85%) |      795.56 ms →      732.14 ms   (-7.97%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms →       10.01 ms   (+0.57%) |      26   →      25     (-3.85%) |      258.79 ms →      250.26 ms   (-3.29%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      112.37 μs →      111.73 μs   (-0.57%) |      26   →      25     (-3.85%) |        2.92 ms →        2.79 ms   (-4.39%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.17 μs →      106.76 μs   (-0.38%) |      26   →      25     (-3.85%) |        2.79 ms →        2.67 ms   (-4.21%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.20 ms →        5.15 ms   (-0.87%) |       2   →       2              |       10.39 ms →       10.30 ms   (-0.87%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.20 ms →       10.42 ms   (+2.14%) |       6   →       6              |       61.23 ms →       62.54 ms   (+2.14%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.11 ms →       10.11 ms   (+0.03%) |       6   →       6              |       60.63 ms →       60.65 ms   (+0.03%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.11 ms →       10.11 ms   (+0.03%) |       6   →       6              |       60.63 ms →       60.65 ms   (+0.03%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.40 ms →       10.35 ms   (-0.48%) |       3   →       3              |       31.20 ms →       31.05 ms   (-0.48%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.39 ms →        9.68 ms   (-6.80%) |       3   →       3              |       31.17 ms →       29.05 ms   (-6.80%) | 
  ├ sirius::Periodic_function|inner                                     |       10.03 ms →       10.34 ms   (+3.11%) |       2   →       2              |       20.05 ms →       20.67 ms   (+3.11%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms →       10.09 ms   (+0.73%) |       2   →       2              |       20.03 ms →       20.18 ms   (+0.73%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms →       10.09 ms   (+0.73%) |       2   →       2              |       20.03 ms →       20.18 ms   (+0.73%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.44 ms →       10.01 ms   (-4.12%) |       1   →       1              |       10.44 ms →       10.01 ms   (-4.12%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.43 ms →        9.63 ms   (-7.67%) |       1   →       1              |       10.43 ms →        9.63 ms   (-7.67%) | 
- └ sirius::finalize                                                    |      282.53 ms →      339.81 ms  (+20.28%) |       1   →       1              |      282.53 ms →      339.81 ms  (+20.28%) | 
  ====================================================================================================================================================================================================
```
