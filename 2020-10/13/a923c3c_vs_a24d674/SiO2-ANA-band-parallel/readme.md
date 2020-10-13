# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      390.63 s  →      239.53 s   (-38.68%) |       1   →       1              |      390.63 s  →      239.53 s   (-38.68%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.73 s    (-0.79%) |       1   →       1              |        2.75 s  →        2.73 s    (-0.79%) | 
+ ├ sirius::Simulation_context::initialize                              |        3.35 s  →        2.98 s   (-10.97%) |       1   →       1              |        3.35 s  →        2.98 s   (-10.97%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        7.75 ms →       33.81 ms (+336.04%) |       1   →       1              |        7.75 ms →       33.81 ms (+336.04%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      539.03 ms →      184.96 ms  (-65.69%) |       1   →       1              |      539.03 ms →      184.96 ms  (-65.69%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      257.06 ms →       80.90 ms  (-68.53%) |       2   →       2              |      514.12 ms →      161.80 ms  (-68.53%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.82 ms →       23.08 ms   (-7.00%) |       1   →       1              |       24.82 ms →       23.08 ms   (-7.00%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.65 ms →        6.37 ms   (-4.21%) |       1   →       1              |        6.65 ms →        6.37 ms   (-4.21%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.13 ms →       16.67 ms   (-8.05%) |       1   →       1              |       18.13 ms →       16.67 ms   (-8.05%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.11 ms →       16.65 ms   (-8.03%) |       1   →       1              |       18.11 ms →       16.65 ms   (-8.03%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.13 ms   (-1.00%) |       1   →       1              |        4.17 ms →        4.13 ms   (-1.00%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.03%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.03%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.64 μs →      101.07 μs   (-0.57%) |       1   →       1              |      101.64 μs →      101.07 μs   (-0.57%) | 
  │ └ sirius::Simulation_context::update                                |        2.76 s  →        2.71 s    (-1.74%) |       1   →       1              |        2.76 s  →        2.71 s    (-1.74%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.88 ms →       10.85 ms   (-0.26%) |       1   →       1              |       10.88 ms →       10.85 ms   (-0.26%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.41 ms →        4.44 ms   (+0.67%) |       1   →       1              |        4.41 ms →        4.44 ms   (+0.67%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.43 ms →        6.37 ms   (-0.93%) |       1   →       1              |        6.43 ms →        6.37 ms   (-0.93%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.41 ms →        6.35 ms   (-0.91%) |       1   →       1              |        6.41 ms →        6.35 ms   (-0.91%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.91 ms →        3.86 ms   (-1.48%) |       1   →       1              |        3.91 ms →        3.86 ms   (-1.48%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.04%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.04%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.97 μs →      100.57 μs   (+0.60%) |       1   →       1              |       99.97 μs →      100.57 μs   (+0.60%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       65.20 ms →       62.76 ms   (-3.75%) |       2   →       2              |      130.41 ms →      125.52 ms   (-3.75%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.30 ms →        5.13 ms   (-3.17%) |       2   →       2              |       10.60 ms →       10.27 ms   (-3.17%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.52 ms →        4.47 ms   (-1.05%) |       1   →       1              |        4.52 ms →        4.47 ms   (-1.05%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.91 ms →       21.79 ms   (-0.55%) |       2   →       2              |       43.82 ms →       43.58 ms   (-0.55%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.86 ms →       14.82 ms   (-0.28%) |       2   →       2              |       29.71 ms →       29.63 ms   (-0.28%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.76 ms →       19.76 ms   (-0.03%) |       4   →       4              |       79.05 ms →       79.03 ms   (-0.03%) | 
  │   ├ sddk::Gvec::init                                                |      180.14 ms →      171.45 ms   (-4.83%) |       2   →       2              |      360.28 ms →      342.89 ms   (-4.83%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      133.11 ms →      129.07 ms   (-3.04%) |       2   →       2              |      266.23 ms →      258.14 ms   (-3.04%) | 
+ │   ├ sddk::Gvec_shells                                               |      215.83 ms →      163.52 ms  (-24.23%) |       1   →       1              |      215.83 ms →      163.52 ms  (-24.23%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.35 ms →        1.32 ms   (-2.19%) |       1   →       1              |        1.35 ms →        1.32 ms   (-2.19%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      297.85 ms →      292.95 ms   (-1.65%) |       2   →       2              |      595.70 ms →      585.90 ms   (-1.65%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       82.01 ms →       76.93 ms   (-6.20%) |       1   →       1              |       82.01 ms →       76.93 ms   (-6.20%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.83 μs →        2.07 μs  (-26.72%) |       4   →       4              |       11.30 μs →        8.28 μs  (-26.72%) | 
  │ └ sirius::K_point_set::initialize                                   |       81.92 ms →       76.83 ms   (-6.22%) |       1   →       1              |       81.92 ms →       76.83 ms   (-6.22%) | 
  │   └ sirius::K_point::initialize                                     |       20.47 ms →       19.19 ms   (-6.22%) |       4   →       4              |       81.87 ms →       76.78 ms   (-6.22%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.50 ms →       14.60 ms   (-5.82%) |       4   →       4              |       62.01 ms →       58.40 ms   (-5.82%) | 
  │     │ └ sddk::Gvec::init                                            |        4.04 ms →        3.91 ms   (-3.21%) |       4   →       4              |       16.16 ms →       15.64 ms   (-3.21%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.25 μs →        9.39 μs   (+1.56%) |       4   →       4              |       36.99 μs →       37.57 μs   (+1.56%) | 
  │     └ sirius::K_point::update                                       |        3.48 ms →        3.28 ms   (-5.57%) |       4   →       4              |       13.90 ms →       13.13 ms   (-5.57%) | 
  │       └ sirius::Beta_projectors                                     |        1.79 ms →        1.75 ms   (-2.16%) |       4   →       4              |        7.14 ms →        6.99 ms   (-2.16%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      930.80 μs →      916.02 μs   (-1.59%) |       4   →       4              |        3.72 ms →        3.66 ms   (-1.59%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.56 ms   (+4.67%) |       2   →       2              |       10.63 ms →       11.12 ms   (+4.67%) | 
  ├ sirius::Potential                                                   |      157.34 ms →      162.19 ms   (+3.08%) |       1   →       1              |      157.34 ms →      162.19 ms   (+3.08%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.75 ms →        6.37 ms  (+10.67%) |       6   →       6              |       34.51 ms →       38.19 ms  (+10.67%) | 
  │ └ sirius::Potential::update                                         |      122.14 ms →      123.17 ms   (+0.85%) |       1   →       1              |      122.14 ms →      123.17 ms   (+0.85%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.40 ms →      122.41 ms   (+0.83%) |       1   →       1              |      121.40 ms →      122.41 ms   (+0.83%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.19 ms →      115.18 ms   (+3.59%) |       1   →       1              |      111.19 ms →      115.18 ms   (+3.59%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.66 ms →        6.32 ms  (-34.64%) |       1   →       1              |        9.66 ms →        6.32 ms  (-34.64%) | 
  ├ sirius::Density                                                     |      130.91 ms →      135.19 ms   (+3.27%) |       1   →       1              |      130.91 ms →      135.19 ms   (+3.27%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms →        5.20 ms   (-0.78%) |       2   →       2              |       10.47 ms →       10.39 ms   (-0.78%) | 
  │ └ sirius::Density::update                                           |      120.17 ms →      124.52 ms   (+3.63%) |       1   →       1              |      120.17 ms →      124.52 ms   (+3.63%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      119.75 ms →      124.09 ms   (+3.63%) |       1   →       1              |      119.75 ms →      124.09 ms   (+3.63%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       103.80 μs            |                   1              |                       103.80 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.82 ms →      118.34 ms   (+6.79%) |       1   →       1              |      110.82 ms →      118.34 ms   (+6.79%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.49 ms →        5.17 ms  (-39.09%) |       1   →       1              |        8.49 ms →        5.17 ms  (-39.09%) | 
  ├ sirius::Density::initial_density                                    |      166.29 ms →      175.32 ms   (+5.43%) |       1   →       1              |      166.29 ms →      175.32 ms   (+5.43%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      109.57 ms →      122.97 ms  (+12.23%) |       1   →       1              |      109.57 ms →      122.97 ms  (+12.23%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.41 ms →        5.07 ms  (-20.91%) |       2   →       2              |       12.82 ms →       10.14 ms  (-20.91%) | 
+ │ └ sirius::Periodic_function::integrate                              |       12.06 ms →        9.78 ms  (-18.86%) |       1   →       1              |       12.06 ms →        9.78 ms  (-18.86%) | 
  ├ sirius::Potential::generate                                         |      574.25 ms →      610.15 ms   (+6.25%) |       1   →       1              |      574.25 ms →      610.15 ms   (+6.25%) | 
  │ ├ sirius::Potential::poisson                                        |      126.11 ms →      138.35 ms   (+9.71%) |       1   →       1              |      126.11 ms →      138.35 ms   (+9.71%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.26 ms →        5.31 ms  (-26.93%) |       1   →       1              |        7.26 ms →        5.31 ms  (-26.93%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.46 ms →       10.88 ms   (+3.98%) |       1   →       1              |       10.46 ms →       10.88 ms   (+3.98%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.07 ms →       10.85 ms   (+7.76%) |       1   →       1              |       10.07 ms →       10.85 ms   (+7.76%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.07 ms →       10.85 ms   (+7.75%) |       1   →       1              |       10.07 ms →       10.85 ms   (+7.75%) | 
  │ ├ sirius::Periodic_function::add                                    |      557.36 μs →      540.97 μs   (-2.94%) |       2   →       2              |        1.11 ms →        1.08 ms   (-2.94%) | 
  │ ├ sirius::Potential::xc                                             |       52.82 ms →       55.49 ms   (+5.06%) |       1   →       1              |       52.82 ms →       55.49 ms   (+5.06%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.81 ms →       53.01 ms   (+0.38%) |       1   →       1              |       52.81 ms →       53.01 ms   (+0.38%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        6.22 ms   (+9.21%) |       2   →       2              |       11.39 ms →       12.44 ms   (+9.21%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.90 ms →        5.24 ms  (-11.27%) |       1   →       1              |        5.90 ms →        5.24 ms  (-11.27%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.67 ms →        5.82 ms   (+2.54%) |       1   →       1              |        5.67 ms →        5.82 ms   (+2.54%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.38 ms →       92.64 ms   (-0.79%) |       1   →       1              |       93.38 ms →       92.64 ms   (-0.79%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.78 ms →      315.36 ms   (+7.35%) |       1   →       1              |      293.78 ms →      315.36 ms   (+7.35%) | 
  ├ sirius::Hamiltonian0                                                |        8.60 ms →        8.38 ms   (-2.52%) |       1   →       1              |        8.60 ms →        8.38 ms   (-2.52%) | 
  │ ├ sirius::Local_operator                                            |        8.24 ms →        8.03 ms   (-2.57%) |       1   →       1              |        8.24 ms →        8.03 ms   (-2.57%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.71 ms →        4.79 ms   (+1.85%) |       1   →       1              |        4.71 ms →        4.79 ms   (+1.85%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.61 ms →        2.31 ms  (-11.71%) |       1   →       1              |        2.61 ms →        2.31 ms  (-11.71%) | 
  │ ├ sirius::Non_local_operator                                        |       64.68 μs →       64.85 μs   (+0.26%) |       2   →       2              |      129.37 μs →      129.70 μs   (+0.26%) | 
  │ ├ sirius::D_operator::initialize                                    |       99.77 μs →       97.53 μs   (-2.24%) |       1   →       1              |       99.77 μs →       97.53 μs   (-2.24%) | 
  │ └ sirius::Q_operator::initialize                                    |       72.10 μs →       70.60 μs   (-2.08%) |       1   →       1              |       72.10 μs →       70.60 μs   (-2.08%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.11 s    (-0.00%) |       1   →       1              |        3.11 s  →        3.11 s    (-0.00%) | 
- │ ├ sirius::Hamiltonian_k                                             |      204.81 μs →      376.41 μs  (+83.78%) |       4   →       4              |      819.25 μs →        1.51 ms  (+83.78%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      198.98 μs →      370.95 μs  (+86.43%) |       4   →       4              |      795.92 μs →        1.48 ms  (+86.43%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        4.07 μs →        3.42 μs  (-16.16%) |       4   →       4              |       16.30 μs →       13.66 μs  (-16.16%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      777.47 ms →      777.30 ms   (-0.02%) |       4   →       4              |        3.11 s  →        3.11 s    (-0.02%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       31.99 ms →       32.86 ms   (+2.71%) |      16   →      16              |      511.86 ms →      525.71 ms   (+2.71%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.69 ms →       14.66 ms   (-0.21%) |       4   →       4              |       58.76 ms →       58.64 ms   (-0.21%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.46 ms →        5.55 ms   (+1.68%) |       4   →       4              |       21.83 ms →       22.20 ms   (+1.68%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.30 ms →      357.34 ms   (+0.29%) |       4   →       4              |        1.43 s  →        1.43 s    (+0.29%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      259.39 ms →      260.38 ms   (+0.38%) |       4   →       4              |        1.04 s  →        1.04 s    (+0.38%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       65.81 ms →       63.71 ms   (-3.18%) |       4   →       4              |      263.22 ms →      254.84 ms   (-3.18%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.02 ms →       16.64 ms   (+3.85%) |       4   →       4              |       64.09 ms →       66.56 ms   (+3.85%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.02 ms →       16.64 ms   (+3.85%) |       4   →       4              |       64.08 ms →       66.55 ms   (+3.85%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       43.32 ms →       40.62 ms   (-6.23%) |       4   →       4              |      173.29 ms →      162.49 ms   (-6.23%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.17 ms →       17.89 ms  (+10.62%) |       4   →       4              |       64.69 ms →       71.56 ms  (+10.62%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.17 ms →       17.89 ms  (+10.62%) |       4   →       4              |       64.68 ms →       71.54 ms  (+10.62%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.02 ms →       53.44 ms   (+2.74%) |       4   →       4              |      208.07 ms →      213.77 ms   (+2.74%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.01 ms →       35.41 ms   (+4.11%) |       4   →       4              |      136.05 ms →      141.64 ms   (+4.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.93 ms →        1.93 ms   (+0.11%) |       4   →       4              |        7.71 ms →        7.72 ms   (+0.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.73 ms →       40.75 ms   (+0.05%) |       4   →       4              |      162.90 ms →      162.98 ms   (+0.05%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.65 ms →        7.61 ms   (-0.52%) |       4   →       4              |       30.58 ms →       30.42 ms   (-0.52%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.11 ms →       27.12 ms   (+0.05%) |       8   →       8              |      216.88 ms →      216.98 ms   (+0.05%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.62 ms →       14.98 ms   (+2.43%) |       8   →       8              |      116.96 ms →      119.81 ms   (+2.43%) | 
  │ │ │ ├ sddk::inner                                                   |       14.56 ms                             |       8                          |      116.47 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       49.97 μs                             |       8                          |      399.75 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.93 ms            |                   8              |                       119.45 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        31.75 ns            |                   8              |                       254.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.75 ms            |                   8              |                       118.03 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        25.25 ns            |                   8              |                       202.00 ns            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      124.27 ms →      118.93 ms   (-4.30%) |       4   →       4              |      497.08 ms →      475.73 ms   (-4.30%) | 
  │ │ ├ sddk::transform                                                 |       27.70 ms                             |       4                          |      110.80 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       25.58 μs                             |       4                          |      102.30 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.48 ms                             |       4                          |        5.93 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       23.96 μs                             |       4                          |       95.84 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        23.51 ms            |                   4              |                        94.02 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        23.30 ms            |                   4              |                        93.21 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      366.00 ns →      348.50 ns   (-4.78%) |       4   →       4              |        1.46 μs →        1.39 μs   (-4.78%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      379.31 s  →      228.73 s   (-39.70%) |       1   →       1              |      379.31 s  →      228.73 s   (-39.70%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.70 ms →        5.86 ms   (+2.73%) |      19   →      19              |      108.30 ms →      111.27 ms   (+2.73%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        6.89 s  →        9.13 s   (+32.57%) |      55   →      25    (-54.55%) |      378.98 s  →      228.37 s   (-39.74%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.54 ms →        4.44 ms   (-2.16%) |      55   →      25    (-54.55%) |      249.67 ms →      111.04 ms  (-55.53%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.17 ms →        4.08 ms   (-2.17%) |      55   →      25    (-54.55%) |      229.59 ms →      102.10 ms  (-55.53%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      971.01 μs →      983.97 μs   (+1.33%) |      55   →      25    (-54.55%) |       53.41 ms →       24.60 ms  (-53.94%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.32 ms →        2.21 ms   (-4.50%) |      55   →      25    (-54.55%) |      127.47 ms →       55.33 ms  (-56.59%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.85 μs →       64.40 μs   (-0.69%) |     110   →      50    (-54.55%) |        7.13 ms →        3.22 ms  (-54.86%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      100.10 μs →       94.44 μs   (-5.66%) |      55   →      25    (-54.55%) |        5.51 ms →        2.36 ms  (-57.12%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       71.04 μs →       65.71 μs   (-7.51%) |      55   →      25    (-54.55%) |        3.91 ms →        1.64 ms  (-57.96%) | 
- │ │ ├ sirius::Band::solve                                             |        4.79 s  →        7.03 s   (+46.70%) |      55   →      25    (-54.55%) |      263.46 s  →      175.68 s   (-33.32%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      200.89 μs →      335.66 μs  (+67.09%) |     220   →     100    (-54.55%) |       44.20 ms →       33.57 ms  (-24.05%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      195.18 μs →      329.98 μs  (+69.06%) |     220   →     100    (-54.55%) |       42.94 ms →       33.00 ms  (-23.15%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.37 μs →        4.08 μs   (-6.55%) |     220   →     100    (-54.55%) |      960.58 μs →      408.02 μs  (-57.52%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.20 s  →        1.76 s   (+46.70%) |     220   →     100    (-54.55%) |      263.41 s  →      175.64 s   (-33.32%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       14.05 ms →       11.86 ms  (-15.55%) |     220   →     100    (-54.55%) |        3.09 s  →        1.19 s   (-61.61%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      381.95 μs →      680.63 ns  (-99.82%) |    1.32 K →     600    (-54.55%) |      504.18 ms →      408.38 μs  (-99.92%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.84 ms   (-0.12%) |     220   →     100    (-54.55%) |      404.39 ms →      183.60 ms  (-54.60%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.88 μs →      354.93 μs   (+1.16%) |     220   →     100    (-54.55%) |       77.19 ms →       35.49 ms  (-54.02%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      546.44 μs →      549.80 μs   (+0.62%) |     440   →     200    (-54.55%) |      240.43 ms →      109.96 ms  (-54.27%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.17 s  →        1.73 s   (+47.87%) |     220   →     100    (-54.55%) |      257.93 s  →      173.37 s   (-32.79%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       89.10 ms →       68.49 ms  (-23.13%) |     946   →     913     (-3.49%) |       84.29 s  →       62.53 s   (-25.81%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       57.35 ms →       43.69 ms  (-23.82%) |     946   →     913     (-3.49%) |       54.25 s  →       39.89 s   (-26.48%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       10.17 ms →        8.55 ms  (-15.98%) |     946   →     913     (-3.49%) |        9.62 s  →        7.80 s   (-18.91%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       56.72 μs →      237.48 μs (+318.67%) |     946   →     913     (-3.49%) |       53.66 ms →      216.82 ms (+304.06%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      235.97 μs →        2.15 ms (+811.14%) |     220   →     100    (-54.55%) |       51.91 ms →      215.00 ms (+314.15%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        8.42 ms →        6.74 ms  (-19.92%) |     946   →     913     (-3.49%) |        7.96 s  →        6.15 s   (-22.71%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       58.06 μs →       93.34 μs  (+60.76%) |     946   →     913     (-3.49%) |       54.93 ms →       85.22 ms  (+55.15%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      239.84 μs →      827.55 μs (+245.05%) |     220   →     100    (-54.55%) |       52.76 ms →       82.75 ms  (+56.84%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       12.49 ms →        9.60 ms  (-23.10%) |     946   →     913     (-3.49%) |       11.81 s  →        8.77 s   (-25.78%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        7.64 ms →        6.03 ms  (-21.08%) |     946   →     913     (-3.49%) |        7.22 s  →        5.50 s   (-23.83%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.56 ms →        1.52 ms   (-2.48%) |     946   →     913     (-3.49%) |        1.48 s  →        1.39 s    (-5.88%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       11.60 ms →        8.57 ms  (-26.14%) |     946   →     913     (-3.49%) |       10.97 s  →        7.82 s   (-28.71%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.01 ms →        1.37 ms  (-32.10%) |     946   →     913     (-3.49%) |        1.91 s  →        1.25 s   (-34.47%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.28 ms →        7.35 ms  (-20.88%) |    1.89 K →    1.83 K   (-3.49%) |       17.56 s  →       13.41 s   (-23.64%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       23.39 ms →       27.63 ms  (+18.10%) |     946   →     913     (-3.49%) |       22.13 s  →       25.22 s   (+13.98%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.72 ms                             |    1.67 K                        |        4.55 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       33.00 μs                             |    1.83 K                        |       60.33 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         2.04 ms            |                1.73 K            |                         3.52 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        70.97 ns            |                1.73 K            |                       122.50 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         2.03 ms            |                1.73 K            |                         3.50 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        64.86 ns            |                1.73 K            |                       111.95 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |        1.05 ms →      832.91 μs  (-20.64%) |     946   →     913     (-3.49%) |      992.89 ms →      760.45 ms  (-23.41%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.15 ms →      744.80 μs  (-35.29%) |     946   →     913     (-3.49%) |        1.09 s  →      680.00 ms  (-37.55%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.66 ms                             |    3.56 K                        |       13.03 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.62 μs                             |    3.56 K                        |       48.53 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      239.04 μs                             |    3.56 K                        |      851.95 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.59 μs                             |    5.02 K                        |       53.12 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.30 ms            |                3.55 K            |                        18.84 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.61 ms            |                5.18 K            |                        18.69 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.25 ms →        5.39 ms  (-13.83%) |     946   →     913     (-3.49%) |        5.92 s  →        4.92 s   (-16.83%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.78 ms                             |     946                          |        4.52 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.80 μs                             |    1.14 K                        |       31.61 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.68 ms            |                 913              |                         3.36 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        77.65 ns            |                 913              |                        70.89 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.67 ms            |                 913              |                         3.35 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        80.78 ns            |                 913              |                        73.75 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      141.17 ms →       65.93 ms  (-53.30%) |     946   →     913     (-3.49%) |      133.55 s  →       60.19 s   (-54.93%) | 
- │ │ │ │   ├ sirius::residuals                                         |        9.12 ms →       11.00 ms  (+20.62%) |     934   →     891     (-4.60%) |        8.52 s  →        9.80 s   (+15.06%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        8.40 ms                             |     871                          |        7.32 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.40 μs                             |     871                          |       17.77 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      353.63 μs                             |     871                          |      308.01 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       13.75 μs                             |    1.74 K                        |       23.96 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        10.62 ms            |                 847              |                         8.99 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.28 ms            |                1.69 K            |                         8.94 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.06 ms →      641.78 μs  (-39.62%) |     871   →     847     (-2.76%) |      925.79 ms →      543.59 ms  (-41.28%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       15.31 ms →       52.04 ms (+240.01%) |     228   →     205    (-10.09%) |        3.49 s  →       10.67 s  (+205.71%) | 
  │ │ │ │     ├ sddk::transform                                         |       14.75 ms                             |     236                          |        3.48 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       14.36 μs                             |     236                          |        3.39 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |      909.33 μs                             |     236                          |      214.60 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       15.93 μs                             |     244                          |        3.89 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        34.30 ms            |                 310              |                        10.63 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        25.51 ms            |                 415              |                        10.59 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      472.27 ns →      582.46 ns  (+23.33%) |     220   →     100    (-54.55%) |      103.90 μs →       58.25 μs  (-43.94%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       18.81 μs →       21.96 μs  (+16.72%) |      55   →      25    (-54.55%) |        1.03 ms →      548.96 μs  (-46.95%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      593.14 μs →      599.50 μs   (+1.07%) |      55   →      25    (-54.55%) |       32.62 ms →       14.99 ms  (-54.06%) | 
+ │ │ ├ sirius::Density::generate                                       |      893.84 ms →      896.62 ms   (+0.31%) |      55   →      25    (-54.55%) |       49.16 s  →       22.42 s   (-54.40%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      520.36 ms →      527.47 ms   (+1.37%) |      55   →      25    (-54.55%) |       28.62 s  →       13.19 s   (-53.92%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.05 ms →       24.84 ms   (+7.77%) |     220   →     100    (-54.55%) |        5.07 s  →        2.48 s   (-51.01%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.24 μs →        8.56 μs   (+3.93%) |     220   →     100    (-54.55%) |        1.81 ms →      856.10 μs  (-52.76%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.86 μs →       14.86 μs   (-6.32%) |       8   →       8              |      126.90 μs →      118.89 μs   (-6.32%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.01 ms →       20.59 ms   (+8.30%) |     220   →     100    (-54.55%) |        4.18 s  →        2.06 s   (-50.77%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.31 ms →       30.04 ms   (-0.90%) |     220   →     100    (-54.55%) |        6.67 s  →        3.00 s   (-54.95%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.38 μs →        9.52 μs   (+1.49%) |     220   →     100    (-54.55%) |        2.06 ms →      952.34 μs  (-53.87%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (-0.07%) |     220   →     100    (-54.55%) |      319.85 ms →      145.28 ms  (-54.58%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.37 ms →       28.11 ms   (-0.95%) |     220   →     100    (-54.55%) |        6.24 s  →        2.81 s   (-54.98%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.28 ms →        3.98 ms   (-7.02%) |     220   →     100    (-54.55%) |      941.20 ms →      397.80 ms  (-57.73%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      591.22 ns →      605.58 ns   (+2.43%) |     220   →     100    (-54.55%) |      130.07 μs →       60.56 μs  (-53.44%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.45 ms →       42.71 ms   (+0.61%) |     220   →     100    (-54.55%) |        9.34 s  →        4.27 s   (-54.27%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.25%) |      55   →      25    (-54.55%) |       90.26 ms →       40.92 ms  (-54.66%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.26 ms →       88.94 ms   (+0.76%) |      55   →      25    (-54.55%) |        4.85 s  →        2.22 s   (-54.20%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.03 ms →       88.70 ms   (+0.76%) |      55   →      25    (-54.55%) |        4.84 s  →        2.22 s   (-54.20%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      281.14 ms →      274.55 ms   (-2.34%) |      55   →      25    (-54.55%) |       15.46 s  →        6.86 s   (-55.61%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      281.14 ms →      274.55 ms   (-2.34%) |      55   →      25    (-54.55%) |       15.46 s  →        6.86 s   (-55.61%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.34 ms →       24.62 ms  (-16.09%) |      55   →      25    (-54.55%) |        1.61 s  →      615.51 ms  (-61.86%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      220.18 ms →      224.47 ms   (+1.95%) |      55   →      25    (-54.55%) |       12.11 s  →        5.61 s   (-53.66%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       29.96 ms →       23.66 ms  (-21.02%) |      55   →      25    (-54.55%) |        1.65 s  →      591.49 ms  (-64.10%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.77 ms →       80.63 ms   (-1.40%) |      55   →      25    (-54.55%) |        4.50 s  →        2.02 s   (-55.18%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.97 ms →       10.38 ms  (+48.84%) |      55   →      25    (-54.55%) |      383.55 ms →      259.50 ms  (-32.34%) | 
+ │ │ ├ sirius::Density::mix                                            |      238.02 ms →      218.68 ms   (-8.13%) |      55   →      25    (-54.55%) |       13.09 s  →        5.47 s   (-58.24%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      962.36 μs →      985.57 μs   (+2.41%) |      55   →      25    (-54.55%) |       52.93 ms →       24.64 ms  (-53.45%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.75 ms →       10.71 ms   (-0.37%) |     769   →     319    (-58.52%) |        8.26 s  →        3.42 s   (-58.67%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.36 ms →       10.44 ms   (+0.73%) |     769   →     319    (-58.52%) |        7.97 s  →        3.33 s   (-58.21%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.36 ms →       10.44 ms   (+0.73%) |     769   →     319    (-58.52%) |        7.97 s  →        3.33 s   (-58.21%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.26 ms →        6.19 ms   (-1.15%) |      55   →      25    (-54.55%) |      344.54 ms →      154.80 ms  (-55.07%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.44 ms →        5.33 ms   (-2.05%) |      55   →      25    (-54.55%) |      299.42 ms →      133.31 ms  (-55.48%) | 
+ │ │ ├ sirius::Potential::generate                                     |      560.36 ms →      587.94 ms   (+4.92%) |      55   →      25    (-54.55%) |       30.82 s  →       14.70 s   (-52.31%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      126.14 ms →      137.77 ms   (+9.22%) |      55   →      25    (-54.55%) |        6.94 s  →        3.44 s   (-50.36%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.12 ms →        5.23 ms  (-26.55%) |      55   →      25    (-54.55%) |      391.41 ms →      130.68 ms  (-66.61%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.49 ms →       10.37 ms   (-1.06%) |      55   →      25    (-54.55%) |      576.70 ms →      259.37 ms  (-55.03%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.15 ms →       10.18 ms   (+0.32%) |      55   →      25    (-54.55%) |      558.15 ms →      254.51 ms  (-54.40%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.15 ms →       10.18 ms   (+0.32%) |      55   →      25    (-54.55%) |      558.12 ms →      254.49 ms  (-54.40%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      552.33 μs →      554.01 μs   (+0.30%) |     110   →      50    (-54.55%) |       60.76 ms →       27.70 ms  (-54.41%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       46.77 ms →       49.85 ms   (+6.60%) |      55   →      25    (-54.55%) |        2.57 s  →        1.25 s   (-51.54%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.76 ms →       47.48 ms   (+1.53%) |      55   →      25    (-54.55%) |        2.57 s  →        1.19 s   (-53.85%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        3.07 ms   (+1.27%) |     110   →      50    (-54.55%) |      333.10 ms →      153.33 ms  (-53.97%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.30 ms →        5.48 ms   (+3.35%) |      55   →      25    (-54.55%) |      291.53 ms →      136.96 ms  (-53.02%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.61 ms →        6.67 ms   (+0.87%) |      55   →      25    (-54.55%) |      363.43 ms →      166.63 ms  (-54.15%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.92 ms →       90.90 ms   (-0.02%) |      55   →      25    (-54.55%) |        5.00 s  →        2.27 s   (-54.55%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      287.50 ms →      300.29 ms   (+4.45%) |      55   →      25    (-54.55%) |       15.81 s  →        7.51 s   (-52.52%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      282.92 ms →      278.53 ms   (-1.55%) |      55   →      25    (-54.55%) |       15.56 s  →        6.96 s   (-55.25%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      282.92 ms →      278.52 ms   (-1.55%) |      55   →      25    (-54.55%) |       15.56 s  →        6.96 s   (-55.25%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.31 ms →       27.34 ms  (-15.38%) |      55   →      25    (-54.55%) |        1.78 s  →      683.62 ms  (-61.53%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      217.43 ms →      223.68 ms   (+2.88%) |      55   →      25    (-54.55%) |       11.96 s  →        5.59 s   (-53.24%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       29.38 ms →       23.68 ms  (-19.39%) |      55   →      25    (-54.55%) |        1.62 s  →      592.09 ms  (-63.36%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.32 ms →        5.71 ms   (+7.29%) |      55   →      25    (-54.55%) |      292.80 ms →      142.79 ms  (-51.23%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.27 ms →       10.27 ms   (+0.01%) |     385   →     175    (-54.55%) |        3.95 s  →        1.80 s   (-54.54%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.94 ms   (+0.46%) |     385   →     175    (-54.55%) |        3.81 s  →        1.74 s   (-54.34%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →        9.94 ms   (+0.46%) |     385   →     175    (-54.55%) |        3.81 s  →        1.74 s   (-54.34%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.60 ms →       10.99 ms   (+3.64%) |     165   →      75    (-54.55%) |        1.75 s  →      823.96 ms  (-52.89%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.25 ms →       10.67 ms   (+4.06%) |     165   →      75    (-54.55%) |        1.69 s  →      800.03 ms  (-52.70%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.73 ms →        9.95 ms   (-7.31%) |      55   →      25    (-54.55%) |      590.30 ms →      248.71 ms  (-57.87%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      118.53 μs →      118.53 μs   (+0.00%) |      55   →      25    (-54.55%) |        6.52 ms →        2.96 ms  (-54.54%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      113.30 μs →      113.17 μs   (-0.12%) |      55   →      25    (-54.55%) |        6.23 ms →        2.83 ms  (-54.60%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.30 ms →        5.33 ms   (+0.47%) |       2   →       2              |       10.61 ms →       10.66 ms   (+0.47%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.05 ms →       10.18 ms   (+1.30%) |       6   →       6              |       60.32 ms →       61.11 ms   (+1.30%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.04 ms →        9.76 ms   (-2.82%) |       6   →       6              |       60.26 ms →       58.56 ms   (-2.82%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.04 ms →        9.76 ms   (-2.82%) |       6   →       6              |       60.26 ms →       58.56 ms   (-2.82%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.37 ms →       10.93 ms   (+5.38%) |       3   →       3              |       31.12 ms →       32.79 ms   (+5.38%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.36 ms →       10.59 ms   (+2.18%) |       3   →       3              |       31.09 ms →       31.77 ms   (+2.18%) | 
  ├ sirius::Periodic_function|inner                                     |       10.03 ms →       10.04 ms   (+0.09%) |       2   →       2              |       20.06 ms →       20.08 ms   (+0.09%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms →        9.82 ms   (-2.01%) |       2   →       2              |       20.04 ms →       19.64 ms   (-2.01%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms →        9.82 ms   (-2.01%) |       2   →       2              |       20.04 ms →       19.64 ms   (-2.01%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.47 ms →       10.97 ms   (+4.83%) |       1   →       1              |       10.47 ms →       10.97 ms   (+4.83%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.46 ms →       10.61 ms   (+1.44%) |       1   →       1              |       10.46 ms →       10.61 ms   (+1.44%) | 
+ └ sirius::finalize                                                    |      395.60 ms →      287.13 ms  (-27.42%) |       1   →       1              |      395.60 ms →      287.13 ms  (-27.42%) | 
  ====================================================================================================================================================================================================
```
