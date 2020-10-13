# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      290.69 s  →      245.96 s   (-15.39%) |       1   →       1              |      290.69 s  →      245.96 s   (-15.39%) | 
  ├ sirius::initialize                                                  |        2.79 s  →        2.69 s    (-3.47%) |       1   →       1              |        2.79 s  →        2.69 s    (-3.47%) | 
  ├ sirius::Simulation_context::initialize                              |        2.94 s  →        2.97 s    (+0.83%) |       1   →       1              |        2.94 s  →        2.97 s    (+0.83%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      231.87 μs →       22.38 ms (+9550.97%) |       1   →       1              |      231.87 μs →       22.38 ms (+9550.97%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      139.72 ms →      206.71 ms  (+47.94%) |       1   →       1              |      139.72 ms →      206.71 ms  (+47.94%) | 
- │ │ ├ sirius::Atom_type::init                                         |       56.97 ms →       91.20 ms  (+60.09%) |       2   →       2              |      113.93 ms →      182.40 ms  (+60.09%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.70 ms →       24.23 ms   (-5.72%) |       1   →       1              |       25.70 ms →       24.23 ms   (-5.72%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.48 ms →        6.26 ms   (-3.44%) |       1   →       1              |        6.48 ms →        6.26 ms   (-3.44%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       19.18 ms →       17.93 ms   (-6.52%) |       1   →       1              |       19.18 ms →       17.93 ms   (-6.52%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       19.15 ms →       17.91 ms   (-6.50%) |       1   →       1              |       19.15 ms →       17.91 ms   (-6.50%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (-0.12%) |       1   →       1              |        4.16 ms →        4.16 ms   (-0.12%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.33 ms   (-0.16%) |       1   →       1              |        2.34 ms →        2.33 ms   (-0.16%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.27 μs →      100.72 μs   (-1.51%) |       1   →       1              |      102.27 μs →      100.72 μs   (-1.51%) | 
  │ └ sirius::Simulation_context::update                                |        2.76 s  →        2.69 s    (-2.56%) |       1   →       1              |        2.76 s  →        2.69 s    (-2.56%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.04 ms →       11.09 ms   (+0.43%) |       1   →       1              |       11.04 ms →       11.09 ms   (+0.43%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.67 ms →        4.44 ms   (-4.83%) |       1   →       1              |        4.67 ms →        4.44 ms   (-4.83%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.61 ms   (+4.28%) |       1   →       1              |        6.34 ms →        6.61 ms   (+4.28%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.59 ms   (+4.32%) |       1   →       1              |        6.32 ms →        6.59 ms   (+4.32%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        4.10 ms   (+7.08%) |       1   →       1              |        3.83 ms →        4.10 ms   (+7.08%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.29%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.29%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.74 μs →      100.84 μs   (+1.10%) |       1   →       1              |       99.74 μs →      100.84 μs   (+1.10%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.25 ms →       63.20 ms   (-1.64%) |       2   →       2              |      128.51 ms →      126.40 ms   (-1.64%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.14 ms   (-0.42%) |       2   →       2              |       10.32 ms →       10.28 ms   (-0.42%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (+0.02%) |       1   →       1              |        4.48 ms →        4.48 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.91 ms   (+0.47%) |       2   →       2              |       43.62 ms →       43.82 ms   (+0.47%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.84 ms   (+0.14%) |       2   →       2              |       29.64 ms →       29.68 ms   (+0.14%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.89 ms →       19.66 ms   (-1.14%) |       4   →       4              |       79.55 ms →       78.64 ms   (-1.14%) | 
  │   ├ sddk::Gvec::init                                                |      182.69 ms →      170.53 ms   (-6.66%) |       2   →       2              |      365.38 ms →      341.06 ms   (-6.66%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      135.31 ms →      128.32 ms   (-5.16%) |       2   →       2              |      270.61 ms →      256.64 ms   (-5.16%) | 
+ │   ├ sddk::Gvec_shells                                               |      214.12 ms →      162.18 ms  (-24.26%) |       1   →       1              |      214.12 ms →      162.18 ms  (-24.26%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.38 ms →        1.31 ms   (-4.98%) |       1   →       1              |        1.38 ms →        1.31 ms   (-4.98%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      301.96 ms →      291.76 ms   (-3.38%) |       2   →       2              |      603.93 ms →      583.52 ms   (-3.38%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       87.25 ms →       78.06 ms  (-10.54%) |       1   →       1              |       87.25 ms →       78.06 ms  (-10.54%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.78 μs →        2.44 μs  (-12.20%) |       4   →       4              |       11.13 μs →        9.78 μs  (-12.20%) | 
+ │ └ sirius::K_point_set::initialize                                   |       87.16 ms →       77.96 ms  (-10.56%) |       1   →       1              |       87.16 ms →       77.96 ms  (-10.56%) | 
+ │   └ sirius::K_point::initialize                                     |       21.78 ms →       19.48 ms  (-10.57%) |       4   →       4              |       87.12 ms →       77.91 ms  (-10.57%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       16.24 ms →       14.91 ms   (-8.17%) |       4   →       4              |       64.96 ms →       59.65 ms   (-8.17%) | 
  │     │ └ sddk::Gvec::init                                            |        4.10 ms →        3.91 ms   (-4.60%) |       4   →       4              |       16.39 ms →       15.64 ms   (-4.60%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.73 μs →        8.80 μs   (+0.74%) |       4   →       4              |       34.93 μs →       35.18 μs   (+0.74%) | 
+ │     └ sirius::K_point::update                                       |        4.01 ms →        3.27 ms  (-18.43%) |       4   →       4              |       16.04 ms →       13.09 ms  (-18.43%) | 
+ │       └ sirius::Beta_projectors                                     |        2.26 ms →        1.79 ms  (-20.65%) |       4   →       4              |        9.04 ms →        7.17 ms  (-20.65%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        1.01 ms →      970.91 μs   (-4.22%) |       4   →       4              |        4.05 ms →        3.88 ms   (-4.22%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms →        5.30 ms   (+1.25%) |       2   →       2              |       10.46 ms →       10.60 ms   (+1.25%) | 
  ├ sirius::Potential                                                   |      171.24 ms →      159.93 ms   (-6.61%) |       1   →       1              |      171.24 ms →      159.93 ms   (-6.61%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.83 ms →        5.74 ms   (-1.48%) |       6   →       6              |       34.96 ms →       34.44 ms   (-1.48%) | 
  │ └ sirius::Potential::update                                         |      135.59 ms →      124.78 ms   (-7.97%) |       1   →       1              |      135.59 ms →      124.78 ms   (-7.97%) | 
  │   └ sirius::Potential::generate_local_potential                     |      134.87 ms →      124.05 ms   (-8.03%) |       1   →       1              |      134.87 ms →      124.05 ms   (-8.03%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.16 ms →      114.74 ms   (+3.22%) |       1   →       1              |      111.16 ms →      114.74 ms   (+3.22%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       23.16 ms →        8.42 ms  (-63.66%) |       1   →       1              |       23.16 ms →        8.42 ms  (-63.66%) | 
  ├ sirius::Density                                                     |      141.99 ms →      138.07 ms   (-2.76%) |       1   →       1              |      141.99 ms →      138.07 ms   (-2.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.23 ms →        5.66 ms   (+8.25%) |       2   →       2              |       10.46 ms →       11.32 ms   (+8.25%) | 
  │ └ sirius::Density::update                                           |      131.26 ms →      126.44 ms   (-3.67%) |       1   →       1              |      131.26 ms →      126.44 ms   (-3.67%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      130.84 ms →      126.01 ms   (-3.69%) |       1   →       1              |      130.84 ms →      126.01 ms   (-3.69%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       115.39 μs            |                   1              |                       115.39 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.00 ms →      119.41 ms   (+7.58%) |       1   →       1              |      111.00 ms →      119.41 ms   (+7.58%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       19.39 ms →        6.03 ms  (-68.92%) |       1   →       1              |       19.39 ms →        6.03 ms  (-68.92%) | 
  ├ sirius::Density::initial_density                                    |      181.28 ms →      177.19 ms   (-2.25%) |       1   →       1              |      181.28 ms →      177.19 ms   (-2.25%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      109.38 ms →      123.09 ms  (+12.53%) |       1   →       1              |      109.38 ms →      123.09 ms  (+12.53%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       12.47 ms →        5.77 ms  (-53.75%) |       2   →       2              |       24.93 ms →       11.53 ms  (-53.75%) | 
+ │ └ sirius::Periodic_function::integrate                              |       11.75 ms →        9.72 ms  (-17.28%) |       1   →       1              |       11.75 ms →        9.72 ms  (-17.28%) | 
  ├ sirius::Potential::generate                                         |      589.10 ms →      596.64 ms   (+1.28%) |       1   →       1              |      589.10 ms →      596.64 ms   (+1.28%) | 
  │ ├ sirius::Potential::poisson                                        |      139.21 ms →      138.69 ms   (-0.37%) |       1   →       1              |      139.21 ms →      138.69 ms   (-0.37%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       21.12 ms →        7.31 ms  (-65.38%) |       1   →       1              |       21.12 ms →        7.31 ms  (-65.38%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.29 ms →       10.21 ms   (-0.85%) |       1   →       1              |       10.29 ms →       10.21 ms   (-0.85%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.27 ms →       10.19 ms   (-0.84%) |       1   →       1              |       10.27 ms →       10.19 ms   (-0.84%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.27 ms →       10.19 ms   (-0.84%) |       1   →       1              |       10.27 ms →       10.19 ms   (-0.84%) | 
  │ ├ sirius::Periodic_function::add                                    |      555.14 μs →      552.73 μs   (-0.44%) |       2   →       2              |        1.11 ms →        1.11 ms   (-0.44%) | 
  │ ├ sirius::Potential::xc                                             |       52.69 ms →       53.74 ms   (+2.00%) |       1   →       1              |       52.69 ms →       53.74 ms   (+2.00%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.68 ms →       51.45 ms   (-2.34%) |       1   →       1              |       52.68 ms →       51.45 ms   (-2.34%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.73 ms →        5.67 ms   (-0.99%) |       2   →       2              |       11.46 ms →       11.35 ms   (-0.99%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.41 ms →        5.32 ms   (-1.77%) |       1   →       1              |        5.41 ms →        5.32 ms   (-1.77%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.91 ms →        5.86 ms   (-0.77%) |       1   →       1              |        5.91 ms →        5.86 ms   (-0.77%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.68 ms →       92.67 ms   (-1.08%) |       1   →       1              |       93.68 ms →       92.67 ms   (-1.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      295.16 ms →      303.23 ms   (+2.74%) |       1   →       1              |      295.16 ms →      303.23 ms   (+2.74%) | 
  ├ sirius::Hamiltonian0                                                |        8.40 ms →        8.39 ms   (-0.11%) |       1   →       1              |        8.40 ms →        8.39 ms   (-0.11%) | 
  │ ├ sirius::Local_operator                                            |        8.05 ms →        8.05 ms   (+0.02%) |       1   →       1              |        8.05 ms →        8.05 ms   (+0.02%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms →        4.69 ms   (-0.71%) |       1   →       1              |        4.73 ms →        4.69 ms   (-0.71%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.40 ms →        2.44 ms   (+1.75%) |       1   →       1              |        2.40 ms →        2.44 ms   (+1.75%) | 
  │ ├ sirius::Non_local_operator                                        |       63.08 μs →       63.69 μs   (+0.97%) |       2   →       2              |      126.17 μs →      127.38 μs   (+0.97%) | 
+ │ ├ sirius::D_operator::initialize                                    |      103.40 μs →       93.04 μs  (-10.02%) |       1   →       1              |      103.40 μs →       93.04 μs  (-10.02%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.50 μs →       68.71 μs   (-1.14%) |       1   →       1              |       69.50 μs →       68.71 μs   (-1.14%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.15 s  →        3.16 s    (+0.35%) |       1   →       1              |        3.15 s  →        3.16 s    (+0.35%) | 
- │ ├ sirius::Hamiltonian_k                                             |      211.91 μs →      370.76 μs  (+74.96%) |       4   →       4              |      847.66 μs →        1.48 ms  (+74.96%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      207.20 μs →      365.96 μs  (+76.63%) |       4   →       4              |      828.78 μs →        1.46 ms  (+76.63%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.30 μs →        3.01 μs   (-8.79%) |       4   →       4              |       13.21 μs →       12.05 μs   (-8.79%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      786.85 ms →      789.47 ms   (+0.33%) |       4   →       4              |        3.15 s  →        3.16 s    (+0.33%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.62 ms →       32.30 ms   (-0.97%) |      16   →      16              |      521.96 ms →      516.88 ms   (-0.97%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.75 ms →       14.64 ms   (-0.75%) |       4   →       4              |       58.99 ms →       58.55 ms   (-0.75%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.44 ms →        5.29 ms   (-2.65%) |       4   →       4              |       21.75 ms →       21.17 ms   (-2.65%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      361.11 ms →      358.76 ms   (-0.65%) |       4   →       4              |        1.44 s  →        1.44 s    (-0.65%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      263.41 ms →      261.24 ms   (-0.82%) |       4   →       4              |        1.05 s  →        1.04 s    (-0.82%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       66.03 ms →       64.04 ms   (-3.01%) |       4   →       4              |      264.13 ms →      256.17 ms   (-3.01%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.61 ms →       16.29 ms   (-1.91%) |       4   →       4              |       66.44 ms →       65.17 ms   (-1.91%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.61 ms →       16.29 ms   (-1.91%) |       4   →       4              |       66.43 ms →       65.16 ms   (-1.91%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       43.03 ms →       41.34 ms   (-3.93%) |       4   →       4              |      172.12 ms →      165.36 ms   (-3.93%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.38 ms →       16.02 ms   (-2.23%) |       4   →       4              |       65.54 ms →       64.08 ms   (-2.23%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.38 ms →       16.02 ms   (-2.24%) |       4   →       4              |       65.53 ms →       64.06 ms   (-2.24%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       56.95 ms →       57.30 ms   (+0.62%) |       4   →       4              |      227.78 ms →      229.20 ms   (+0.62%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       38.93 ms →       39.24 ms   (+0.78%) |       4   →       4              |      155.74 ms →      156.94 ms   (+0.78%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.94 ms   (+0.22%) |       4   →       4              |        7.75 ms →        7.77 ms   (+0.22%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.31 ms →       40.87 ms   (-1.07%) |       4   →       4              |      165.26 ms →      163.49 ms   (-1.07%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.17 ms →        7.75 ms   (-5.11%) |       4   →       4              |       32.66 ms →       31.00 ms   (-5.11%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.20 ms →       27.33 ms   (+0.47%) |       8   →       8              |      217.61 ms →      218.65 ms   (+0.47%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.69 ms →       15.20 ms   (+3.45%) |       8   →       8              |      117.53 ms →      121.58 ms   (+3.45%) | 
  │ │ │ ├ sddk::inner                                                   |       14.63 ms                             |       8                          |      117.02 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       49.98 μs                             |       8                          |      399.87 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.15 ms            |                   8              |                       121.22 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        39.75 ns            |                   8              |                       318.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.95 ms            |                   8              |                       119.62 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        18.88 ns            |                   8              |                       151.00 ns            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      124.72 ms →      123.27 ms   (-1.16%) |       4   →       4              |      498.90 ms →      493.10 ms   (-1.16%) | 
  │ │ ├ sddk::transform                                                 |       27.76 ms                             |       4                          |      111.04 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       26.48 μs                             |       4                          |      105.91 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.06 ms                             |       4                          |        4.24 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       21.79 μs                             |       4                          |       87.17 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        23.65 ms            |                   4              |                        94.61 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        23.32 ms            |                   4              |                        93.30 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      378.00 ns →      427.25 ns  (+13.03%) |       4   →       4              |        1.51 μs →        1.71 μs  (+13.03%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      279.69 s  →      235.14 s   (-15.93%) |       1   →       1              |      279.69 s  →      235.14 s   (-15.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.75 ms   (+0.50%) |      19   →      19              |      108.70 ms →      109.24 ms   (+0.50%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        9.63 s  →        9.00 s    (-6.49%) |      29   →      26    (-10.34%) |      279.17 s  →      234.06 s   (-16.16%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.52 ms →        4.50 ms   (-0.54%) |      29   →      26    (-10.34%) |      131.13 ms →      116.93 ms  (-10.83%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.15 ms →        4.14 ms   (-0.32%) |      29   →      26    (-10.34%) |      120.49 ms →      107.68 ms  (-10.63%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      981.26 μs →      965.10 μs   (-1.65%) |      29   →      26    (-10.34%) |       28.46 ms →       25.09 ms  (-11.82%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.28 ms →        2.29 ms   (+0.24%) |      29   →      26    (-10.34%) |       66.26 ms →       59.54 ms  (-10.13%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.53 μs →       64.51 μs   (-0.03%) |      58   →      52    (-10.34%) |        3.74 ms →        3.35 ms  (-10.37%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       99.21 μs →       93.90 μs   (-5.35%) |      29   →      26    (-10.34%) |        2.88 ms →        2.44 ms  (-15.14%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       70.97 μs →       65.88 μs   (-7.16%) |      29   →      26    (-10.34%) |        2.06 ms →        1.71 ms  (-16.77%) | 
+ │ │ ├ sirius::Band::solve                                             |        7.52 s  →        6.89 s    (-8.42%) |      29   →      26    (-10.34%) |      218.19 s  →      179.14 s   (-17.90%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      204.51 μs →      333.99 μs  (+63.31%) |     116   →     104    (-10.34%) |       23.72 ms →       34.73 ms  (+46.42%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.64 μs →      328.41 μs  (+65.33%) |     116   →     104    (-10.34%) |       23.04 ms →       34.15 ms  (+48.23%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.50 μs →        4.03 μs  (-10.40%) |     116   →     104    (-10.34%) |      521.45 μs →      418.90 μs  (-19.67%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.88 s  →        1.72 s    (-8.43%) |     116   →     104    (-10.34%) |      218.16 s  →      179.10 s   (-17.91%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       16.47 ms →       11.85 ms  (-28.06%) |     116   →     104    (-10.34%) |        1.91 s  →        1.23 s   (-35.50%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      730.82 μs →      697.58 ns  (-99.90%) |     696   →     624    (-10.34%) |      508.65 ms →      435.29 μs  (-99.91%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.85 ms →        1.84 ms   (-0.67%) |     116   →     104    (-10.34%) |      214.92 ms →      191.39 ms  (-10.95%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.60 μs →      354.20 μs   (+0.45%) |     116   →     104    (-10.34%) |       40.90 ms →       36.84 ms   (-9.94%) | 
! │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      548.77 μs →      551.27 μs   (+0.46%) |     232   →     208    (-10.34%) |      127.31 ms →      114.66 ms   (-9.94%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s  →        1.70 s    (-8.31%) |     116   →     104    (-10.34%) |      214.99 s  →      176.74 s   (-17.79%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       72.64 ms →       70.40 ms   (-3.08%) |     825   →     905     (+9.70%) |       59.92 s  →       63.71 s    (+6.32%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       46.38 ms →       45.05 ms   (-2.86%) |     825   →     905     (+9.70%) |       38.26 s  →       40.77 s    (+6.56%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.74 ms →        8.88 ms   (+1.54%) |     825   →     905     (+9.70%) |        7.21 s  →        8.03 s   (+11.38%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       66.05 μs →      230.91 μs (+249.59%) |     825   →     905     (+9.70%) |       54.49 ms →      208.98 ms (+283.49%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      456.36 μs →        1.99 ms (+336.47%) |     116   →     104    (-10.34%) |       52.94 ms →      207.16 ms (+291.32%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.32 ms →        7.05 ms   (-3.76%) |     825   →     905     (+9.70%) |        6.04 s  →        6.38 s    (+5.57%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       67.37 μs →       88.49 μs  (+31.35%) |     825   →     905     (+9.70%) |       55.58 ms →       80.09 ms  (+44.08%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      462.60 μs →      746.38 μs  (+61.34%) |     116   →     104    (-10.34%) |       53.66 ms →       77.62 ms  (+44.65%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.46 ms →       10.00 ms   (-4.47%) |     825   →     905     (+9.70%) |        8.63 s  →        9.05 s    (+4.79%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.66 ms →        6.35 ms   (-4.68%) |     825   →     905     (+9.70%) |        5.49 s  →        5.74 s    (+4.57%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.52 ms   (-0.60%) |     825   →     905     (+9.70%) |        1.26 s  →        1.37 s    (+9.04%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        9.25 ms →        8.88 ms   (-4.04%) |     825   →     905     (+9.70%) |        7.63 s  →        8.03 s    (+5.26%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.61 ms →        1.48 ms   (-7.73%) |     825   →     905     (+9.70%) |        1.33 s  →        1.34 s    (+1.22%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.73 ms →        7.46 ms   (-3.40%) |    1.65 K →    1.81 K   (+9.70%) |       12.75 s  →       13.51 s    (+5.96%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       20.39 ms →       28.34 ms  (+39.00%) |     825   →     905     (+9.70%) |       16.82 s  →       25.65 s   (+52.47%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.40 ms                             |    1.53 K                        |        3.69 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.47 μs                             |    1.69 K                        |       54.87 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         2.11 ms            |                1.71 K            |                         3.60 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        70.97 ns            |                1.71 K            |                       121.07 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         2.10 ms            |                1.71 K            |                         3.58 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        67.93 ns            |                1.71 K            |                       115.89 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      824.08 μs →      849.07 μs   (+3.03%) |     825   →     905     (+9.70%) |      679.86 ms →      768.41 ms  (+13.02%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      855.04 μs →      796.35 μs   (-6.86%) |     825   →     905     (+9.70%) |      705.41 ms →      720.69 ms   (+2.17%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.18 ms                             |    3.18 K                        |       10.12 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.79 μs                             |    3.18 K                        |       43.91 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      190.02 μs                             |    3.18 K                        |      605.02 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.18 μs                             |    4.60 K                        |       46.84 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.43 ms            |                3.52 K            |                        19.11 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.70 ms            |                5.12 K            |                        18.92 s             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.99 ms →        5.50 ms   (-8.16%) |     825   →     905     (+9.70%) |        4.94 s  →        4.98 s    (+0.74%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.33 ms                             |     825                          |        3.57 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.27 μs                             |    1.02 K                        |       26.69 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.79 ms            |                 905              |                         3.43 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        47.46 ns            |                 905              |                        42.95 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.78 ms            |                 905              |                         3.42 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        61.89 ns            |                 905              |                        56.01 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      150.59 ms →       68.23 ms  (-54.69%) |     825   →     905     (+9.70%) |      124.24 s  →       61.75 s   (-50.30%) | 
- │ │ │ │   ├ sirius::residuals                                         |        7.94 ms →       11.14 ms  (+40.26%) |     814   →     885     (+8.72%) |        6.46 s  →        9.85 s   (+52.50%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.38 ms                             |     752                          |        5.55 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.54 μs                             |     752                          |       15.44 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      323.81 μs                             |     752                          |      243.51 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       13.48 μs                             |    1.50 K                        |       20.28 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        10.76 ms            |                 840              |                         9.04 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.34 ms            |                1.68 K            |                         8.97 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      917.41 μs →      655.84 μs  (-28.51%) |     752   →     840    (+11.70%) |      689.90 ms →      550.90 ms  (-20.15%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       20.70 ms →       51.51 ms (+148.83%) |     124   →     209    (+68.55%) |        2.57 s  →       10.77 s  (+319.41%) | 
  │ │ │ │     ├ sddk::transform                                         |       19.38 ms                             |     132                          |        2.56 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       19.00 μs                             |     132                          |        2.51 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.32 ms                             |     132                          |      173.67 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       18.96 μs                             |     140                          |        2.65 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        34.18 ms            |                 314              |                        10.73 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        25.44 ms            |                 419              |                        10.66 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      510.74 ns →      630.85 ns  (+23.52%) |     116   →     104    (-10.34%) |       59.25 μs →       65.61 μs  (+10.74%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.56 μs →       21.77 μs   (+5.91%) |      29   →      26    (-10.34%) |      596.13 μs →      566.03 μs   (-5.05%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      632.91 μs →      602.08 μs   (-4.87%) |      29   →      26    (-10.34%) |       18.35 ms →       15.65 ms  (-14.71%) | 
+ │ │ ├ sirius::Density::generate                                       |      901.72 ms →      897.45 ms   (-0.47%) |      29   →      26    (-10.34%) |       26.15 s  →       23.33 s   (-10.77%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      531.32 ms →      530.33 ms   (-0.19%) |      29   →      26    (-10.34%) |       15.41 s  →       13.79 s   (-10.51%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.32 ms →       25.06 ms   (-1.03%) |     116   →     104    (-10.34%) |        2.94 s  →        2.61 s   (-11.27%) | 
! │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.55 μs →        8.80 μs   (+2.99%) |     116   →     104    (-10.34%) |      991.42 μs →      915.44 μs   (-7.66%) | 
- │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.18 μs →       15.91 μs  (+12.18%) |       8   →       8              |      113.46 μs →      127.28 μs  (+12.18%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       21.26 ms →       20.93 ms   (-1.54%) |     116   →     104    (-10.34%) |        2.47 s  →        2.18 s   (-11.73%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.49 ms →       30.44 ms   (-0.15%) |     116   →     104    (-10.34%) |        3.54 s  →        3.17 s   (-10.48%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.69 μs →        9.51 μs   (-1.89%) |     116   →     104    (-10.34%) |        1.12 ms →      988.76 μs  (-12.04%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (+0.15%) |     116   →     104    (-10.34%) |      168.19 ms →      151.03 ms  (-10.21%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.56 ms →       28.51 ms   (-0.17%) |     116   →     104    (-10.34%) |        3.31 s  →        2.96 s   (-10.50%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.52 ms →        4.38 ms   (-3.06%) |     116   →     104    (-10.34%) |      523.76 ms →      455.20 ms  (-13.09%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      536.93 ns →      598.57 ns  (+11.48%) |     116   →     104    (-10.34%) |       62.28 μs →       62.25 μs   (-0.05%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.62 ms →       42.70 ms   (+0.19%) |     116   →     104    (-10.34%) |        4.94 s  →        4.44 s   (-10.18%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.05%) |      29   →      26    (-10.34%) |       47.59 ms →       42.65 ms  (-10.39%) | 
! │ │ │ │ └ sirius::Density::augment                                    |       88.35 ms →       88.86 ms   (+0.58%) |      29   →      26    (-10.34%) |        2.56 s  →        2.31 s    (-9.82%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.11 ms →       88.62 ms   (+0.58%) |      29   →      26    (-10.34%) |        2.56 s  →        2.30 s    (-9.83%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.55 ms →      274.77 ms   (-1.36%) |      29   →      26    (-10.34%) |        8.08 s  →        7.14 s   (-11.56%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.55 ms →      274.77 ms   (-1.36%) |      29   →      26    (-10.34%) |        8.08 s  →        7.14 s   (-11.56%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.69 ms →       24.40 ms  (-14.97%) |      29   →      26    (-10.34%) |      832.03 ms →      634.30 ms  (-23.77%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      220.27 ms →      224.66 ms   (+1.99%) |      29   →      26    (-10.34%) |        6.39 s  →        5.84 s    (-8.56%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.81 ms →       23.94 ms  (-13.92%) |      29   →      26    (-10.34%) |      806.49 ms →      622.39 ms  (-22.83%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.64 ms →       81.16 ms   (-0.59%) |      29   →      26    (-10.34%) |        2.37 s  →        2.11 s   (-10.87%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.62 ms →        7.60 ms  (+14.83%) |      29   →      26    (-10.34%) |      192.05 ms →      197.71 ms   (+2.95%) | 
! │ │ ├ sirius::Density::mix                                            |      218.42 ms →      219.53 ms   (+0.51%) |      29   →      26    (-10.34%) |        6.33 s  →        5.71 s    (-9.89%) | 
! │ │ │ ├ sirius::Density::mixer_input                                  |      932.02 μs →      949.85 μs   (+1.91%) |      29   →      26    (-10.34%) |       27.03 ms →       24.70 ms   (-8.63%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |       10.38 ms →       10.79 ms   (+3.97%) |     379   →     334    (-11.87%) |        3.93 s  →        3.60 s    (-8.38%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.97 ms →       10.41 ms   (+4.36%) |     379   →     334    (-11.87%) |        3.78 s  →        3.48 s    (-8.03%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.97 ms →       10.41 ms   (+4.36%) |     379   →     334    (-11.87%) |        3.78 s  →        3.48 s    (-8.03%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.61 ms →        7.03 ms   (-7.63%) |      29   →      26    (-10.34%) |      220.71 ms →      182.78 ms  (-17.18%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.76 ms →        6.18 ms   (-8.60%) |      29   →      26    (-10.34%) |      195.97 ms →      160.59 ms  (-18.05%) | 
! │ │ ├ sirius::Potential::generate                                     |      572.37 ms →      588.48 ms   (+2.81%) |      29   →      26    (-10.34%) |       16.60 s  →       15.30 s    (-7.82%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      139.07 ms →      138.93 ms   (-0.10%) |      29   →      26    (-10.34%) |        4.03 s  →        3.61 s   (-10.44%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       20.82 ms →        7.00 ms  (-66.37%) |      29   →      26    (-10.34%) |      603.74 ms →      182.04 ms  (-69.85%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |       10.32 ms →       10.41 ms   (+0.85%) |      29   →      26    (-10.34%) |      299.30 ms →      270.62 ms   (-9.58%) | 
! │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.98 ms →       10.27 ms   (+2.87%) |      29   →      26    (-10.34%) |      289.46 ms →      266.97 ms   (-7.77%) | 
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.98 ms →       10.27 ms   (+2.87%) |      29   →      26    (-10.34%) |      289.45 ms →      266.96 ms   (-7.77%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      551.96 μs →      559.88 μs   (+1.43%) |      58   →      52    (-10.34%) |       32.01 ms →       29.11 ms   (-9.06%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       46.73 ms →       49.28 ms   (+5.45%) |      29   →      26    (-10.34%) |        1.36 s  →        1.28 s    (-5.46%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.73 ms →       46.93 ms   (+0.42%) |      29   →      26    (-10.34%) |        1.36 s  →        1.22 s    (-9.97%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.02 ms   (+0.03%) |      58   →      52    (-10.34%) |      175.19 ms →      157.12 ms  (-10.32%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.43 ms →        5.52 ms   (+1.64%) |      29   →      26    (-10.34%) |      157.47 ms →      143.49 ms   (-8.87%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.75 ms →        6.71 ms   (-0.61%) |      29   →      26    (-10.34%) |      195.76 ms →      174.44 ms  (-10.89%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.92 ms   (+0.03%) |      29   →      26    (-10.34%) |        2.64 s  →        2.36 s   (-10.32%) | 
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.51 ms →      300.25 ms   (+4.79%) |      29   →      26    (-10.34%) |        8.31 s  →        7.81 s    (-6.05%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      284.17 ms →      279.18 ms   (-1.76%) |      29   →      26    (-10.34%) |        8.24 s  →        7.26 s   (-11.92%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      284.17 ms →      279.18 ms   (-1.76%) |      29   →      26    (-10.34%) |        8.24 s  →        7.26 s   (-11.92%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.02 ms →       27.09 ms  (-15.40%) |      29   →      26    (-10.34%) |      928.64 ms →      704.38 ms  (-24.15%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      220.35 ms →      224.00 ms   (+1.65%) |      29   →      26    (-10.34%) |        6.39 s  →        5.82 s    (-8.86%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       28.06 ms →       24.32 ms  (-13.33%) |      29   →      26    (-10.34%) |      813.62 ms →      632.20 ms  (-22.30%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.52 ms →        5.97 ms   (+8.09%) |      29   →      26    (-10.34%) |      160.11 ms →      155.16 ms   (-3.09%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.41 ms →       10.44 ms   (+0.35%) |     203   →     182    (-10.34%) |        2.11 s  →        1.90 s   (-10.03%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.91 ms →        9.95 ms   (+0.34%) |     203   →     182    (-10.34%) |        2.01 s  →        1.81 s   (-10.04%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.91 ms →        9.95 ms   (+0.34%) |     203   →     182    (-10.34%) |        2.01 s  →        1.81 s   (-10.04%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.53 ms →       11.03 ms   (+4.71%) |      87   →      78    (-10.34%) |      916.42 ms →      860.33 ms   (-6.12%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.26 ms →       10.73 ms   (+4.55%) |      87   →      78    (-10.34%) |      892.77 ms →      836.87 ms   (-6.26%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.77 ms →        9.99 ms   (-7.22%) |      29   →      26    (-10.34%) |      312.21 ms →      259.71 ms  (-16.81%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      129.00 μs →      128.43 μs   (-0.44%) |      29   →      26    (-10.34%) |        3.74 ms →        3.34 ms  (-10.74%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      123.95 μs →      123.07 μs   (-0.71%) |      29   →      26    (-10.34%) |        3.59 ms →        3.20 ms  (-10.98%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.27 ms →        5.29 ms   (+0.37%) |       2   →       2              |       10.55 ms →       10.59 ms   (+0.37%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.76 ms →       10.21 ms   (+4.62%) |       6   →       6              |       58.54 ms →       61.24 ms   (+4.62%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.70 ms →       10.18 ms   (+4.86%) |       6   →       6              |       58.23 ms →       61.06 ms   (+4.86%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.70 ms →       10.18 ms   (+4.86%) |       6   →       6              |       58.23 ms →       61.06 ms   (+4.86%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |       10.12 ms →       11.23 ms  (+10.95%) |       3   →       3              |       30.37 ms →       33.70 ms  (+10.95%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |       10.04 ms →       11.21 ms  (+11.66%) |       3   →       3              |       30.11 ms →       33.62 ms  (+11.66%) | 
  ├ sirius::Periodic_function|inner                                     |        9.70 ms →        9.89 ms   (+2.02%) |       2   →       2              |       19.40 ms →       19.79 ms   (+2.02%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.65 ms →        9.75 ms   (+1.01%) |       2   →       2              |       19.30 ms →       19.50 ms   (+1.01%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.65 ms →        9.75 ms   (+1.01%) |       2   →       2              |       19.30 ms →       19.50 ms   (+1.01%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.15 ms →       10.61 ms   (+4.62%) |       1   →       1              |       10.15 ms →       10.61 ms   (+4.62%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.01 ms →       10.46 ms   (+4.45%) |       1   →       1              |       10.01 ms →       10.46 ms   (+4.45%) | 
+ └ sirius::finalize                                                    |      390.57 ms →      315.51 ms  (-19.22%) |       1   →       1              |      390.57 ms →      315.51 ms  (-19.22%) | 
  ====================================================================================================================================================================================================
```
