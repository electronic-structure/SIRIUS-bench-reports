# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      770.96 s  →      297.77 s   (-61.38%) |       1   →       1              |      770.96 s  →      297.77 s   (-61.38%) | 
  ├ sirius::initialize                                                  |        2.74 s  →        2.72 s    (-0.82%) |       1   →       1              |        2.74 s  →        2.72 s    (-0.82%) | 
  ├ sirius::Simulation_context::initialize                              |        3.03 s  →        2.89 s    (-4.76%) |       1   →       1              |        3.03 s  →        2.89 s    (-4.76%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       74.19 ms →       34.63 ms  (-53.32%) |       1   →       1              |       74.19 ms →       34.63 ms  (-53.32%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      158.35 ms →      103.95 ms  (-34.35%) |       1   →       1              |      158.35 ms →      103.95 ms  (-34.35%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       67.62 ms →       40.52 ms  (-40.09%) |       2   →       2              |      135.25 ms →       81.03 ms  (-40.09%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.02 ms →       22.73 ms   (-1.25%) |       1   →       1              |       23.02 ms →       22.73 ms   (-1.25%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.27 ms →        6.29 ms   (+0.46%) |       1   →       1              |        6.27 ms →        6.29 ms   (+0.46%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.72 ms →       16.40 ms   (-1.89%) |       1   →       1              |       16.72 ms →       16.40 ms   (-1.89%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.70 ms →       16.38 ms   (-1.92%) |       1   →       1              |       16.70 ms →       16.38 ms   (-1.92%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (+0.09%) |       1   →       1              |        4.16 ms →        4.16 ms   (+0.09%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.86%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.86%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.30 μs →      111.59 μs   (+9.08%) |       1   →       1              |      102.30 μs →      111.59 μs   (+9.08%) | 
  │ └ sirius::Simulation_context::update                                |        2.75 s  →        2.70 s    (-1.98%) |       1   →       1              |        2.75 s  →        2.70 s    (-1.98%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.81 ms   (-0.30%) |       1   →       1              |       10.85 ms →       10.81 ms   (-0.30%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.38 ms   (-1.12%) |       1   →       1              |        4.43 ms →        4.38 ms   (-1.12%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.38 ms →        6.40 ms   (+0.25%) |       1   →       1              |        6.38 ms →        6.40 ms   (+0.25%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.36 ms →        6.37 ms   (+0.20%) |       1   →       1              |        6.36 ms →        6.37 ms   (+0.20%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.87 ms →        3.86 ms   (-0.24%) |       1   →       1              |        3.87 ms →        3.86 ms   (-0.24%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.30%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.30%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.54 μs →      108.35 μs   (+8.85%) |       1   →       1              |       99.54 μs →      108.35 μs   (+8.85%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       66.73 ms →       65.18 ms   (-2.32%) |       2   →       2              |      133.46 ms →      130.36 ms   (-2.32%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.14 ms   (+0.13%) |       2   →       2              |       10.26 ms →       10.27 ms   (+0.13%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.47 ms   (-0.14%) |       1   →       1              |        4.48 ms →        4.47 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.72 ms →       22.05 ms   (+1.52%) |       2   →       2              |       43.44 ms →       44.10 ms   (+1.52%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.77 ms →       14.78 ms   (+0.10%) |       2   →       2              |       29.54 ms →       29.56 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.75 ms →       19.56 ms   (-0.99%) |       4   →       4              |       79.00 ms →       78.22 ms   (-0.99%) | 
  │   ├ sddk::Gvec::init                                                |      176.33 ms →      172.66 ms   (-2.08%) |       2   →       2              |      352.65 ms →      345.32 ms   (-2.08%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.51 ms →      130.02 ms   (-0.37%) |       2   →       2              |      261.02 ms →      260.04 ms   (-0.37%) | 
+ │   ├ sddk::Gvec_shells                                               |      206.96 ms →      182.62 ms  (-11.76%) |       1   →       1              |      206.96 ms →      182.62 ms  (-11.76%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.28%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.28%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.33 ms →      292.72 ms   (+0.13%) |       2   →       2              |      584.67 ms →      585.44 ms   (+0.13%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       85.96 ms →       77.45 ms   (-9.90%) |       1   →       1              |       85.96 ms →       77.45 ms   (-9.90%) | 
- │ ├ sirius::K_point::K_point                                          |        2.81 μs →        4.63 μs  (+65.08%) |       4   →       4              |       11.22 μs →       18.52 μs  (+65.08%) | 
  │ └ sirius::K_point_set::initialize                                   |       85.87 ms →       77.34 ms   (-9.93%) |       1   →       1              |       85.87 ms →       77.34 ms   (-9.93%) | 
  │   └ sirius::K_point::initialize                                     |       21.46 ms →       19.31 ms   (-9.99%) |       4   →       4              |       85.82 ms →       77.25 ms   (-9.99%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       16.19 ms →       14.74 ms   (-8.95%) |       4   →       4              |       64.77 ms →       58.97 ms   (-8.95%) | 
  │     │ └ sddk::Gvec::init                                            |        4.18 ms →        3.80 ms   (-9.02%) |       4   →       4              |       16.71 ms →       15.21 ms   (-9.02%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.79 μs →        8.17 μs   (-7.06%) |       4   →       4              |       35.15 μs →       32.67 μs   (-7.06%) | 
+ │     └ sirius::K_point::update                                       |        3.74 ms →        3.27 ms  (-12.47%) |       4   →       4              |       14.96 ms →       13.10 ms  (-12.47%) | 
  │       └ sirius::Beta_projectors                                     |        1.74 ms →        1.80 ms   (+3.61%) |       4   →       4              |        6.96 ms →        7.22 ms   (+3.61%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      919.04 μs →      950.71 μs   (+3.45%) |       4   →       4              |        3.68 ms →        3.80 ms   (+3.45%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.15 ms →        5.13 ms   (-0.33%) |       2   →       2              |       10.30 ms →       10.26 ms   (-0.33%) | 
  ├ sirius::Potential                                                   |      168.28 ms →      156.53 ms   (-6.98%) |       1   →       1              |      168.28 ms →      156.53 ms   (-6.98%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.83 ms →        5.75 ms   (-1.25%) |       6   →       5    (-16.67%) |       34.96 ms →       28.77 ms  (-17.71%) | 
  │ └ sirius::Potential::update                                         |      132.64 ms →      127.04 ms   (-4.22%) |       1   →       1              |      132.64 ms →      127.04 ms   (-4.22%) | 
  │   └ sirius::Potential::generate_local_potential                     |      131.92 ms →      126.30 ms   (-4.26%) |       1   →       1              |      131.92 ms →      126.30 ms   (-4.26%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      125.00 ms →      109.62 ms  (-12.31%) |       1   →       1              |      125.00 ms →      109.62 ms  (-12.31%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.38 ms →       12.41 ms  (+94.56%) |       1   →       1              |        6.38 ms →       12.41 ms  (+94.56%) | 
  ├ sirius::Density                                                     |      139.76 ms →      135.97 ms   (-2.71%) |       1   →       1              |      139.76 ms →      135.97 ms   (-2.71%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.09 ms →        5.08 ms   (-0.13%) |       2   →       2              |       10.18 ms →       10.17 ms   (-0.13%) | 
  │ └ sirius::Density::update                                           |      129.32 ms →      125.53 ms   (-2.93%) |       1   →       1              |      129.32 ms →      125.53 ms   (-2.93%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      128.90 ms →      125.12 ms   (-2.93%) |       1   →       1              |      128.90 ms →      125.12 ms   (-2.93%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       106.08 μs            |                   1              |                       106.08 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      123.29 ms →      110.84 ms  (-10.10%) |       1   →       1              |      123.29 ms →      110.84 ms  (-10.10%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.18 ms →       13.74 ms (+165.41%) |       1   →       1              |        5.18 ms →       13.74 ms (+165.41%) | 
  ├ sirius::Density::initial_density                                    |      174.36 ms →      175.33 ms   (+0.56%) |       1   →       1              |      174.36 ms →      175.33 ms   (+0.56%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      122.04 ms →      108.37 ms  (-11.20%) |       1   →       1              |      122.04 ms →      108.37 ms  (-11.20%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.02 ms →       12.04 ms (+140.12%) |       2   →       2              |       10.03 ms →       24.09 ms (+140.12%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.72 ms →        9.99 ms   (+2.73%) |       1   →       1              |        9.72 ms →        9.99 ms   (+2.73%) | 
  ├ sirius::Potential::generate                                         |      587.69 ms →      570.15 ms   (-2.99%) |       1   →       1              |      587.69 ms →      570.15 ms   (-2.99%) | 
  │ ├ sirius::Potential::poisson                                        |      138.27 ms →      136.95 ms   (-0.95%) |       1   →       1              |      138.27 ms →      136.95 ms   (-0.95%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.32 ms →       18.23 ms (+242.85%) |       1   →       1              |        5.32 ms →       18.23 ms (+242.85%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.94 ms →       10.55 ms   (-3.51%) |       1   →       1              |       10.94 ms →       10.55 ms   (-3.51%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.91 ms →       10.46 ms   (-4.19%) |       1   →       1              |       10.91 ms →       10.46 ms   (-4.19%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.91 ms →       10.46 ms   (-4.19%) |       1   →       1              |       10.91 ms →       10.46 ms   (-4.19%) | 
+ │ ├ sirius::Periodic_function::add                                    |      543.42 μs →      449.34 μs  (-17.31%) |       2   →       2              |        1.09 ms →      898.68 μs  (-17.31%) | 
+ │ ├ sirius::Potential::xc                                             |       51.60 ms →       31.85 ms  (-38.27%) |       1   →       1              |       51.60 ms →       31.85 ms  (-38.27%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.60 ms →       29.58 ms  (-42.67%) |       1   →       1              |       51.60 ms →       29.58 ms  (-42.67%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        5.64 ms →        5.50 ms   (-2.48%) |       2   →       1    (-50.00%) |       11.28 ms →        5.50 ms  (-51.24%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.60 ms                             |       1                          |        5.60 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                         8.51 ms            |                   2              |                        17.01 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.83 ms →        5.08 ms  (-12.98%) |       1   →       1              |        5.83 ms →        5.08 ms  (-12.98%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.73 ms →       93.92 ms   (+1.28%) |       1   →       1              |       92.73 ms →       93.92 ms   (+1.28%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      296.82 ms →      300.12 ms   (+1.11%) |       1   →       1              |      296.82 ms →      300.12 ms   (+1.11%) | 
- ├ sirius::Hamiltonian0                                                |        8.37 ms →       11.95 ms  (+42.83%) |       1   →       1              |        8.37 ms →       11.95 ms  (+42.83%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        8.02 ms   (-0.02%) |       1   →       1              |        8.02 ms →        8.02 ms   (-0.02%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.68 ms →        4.68 ms   (+0.10%) |       1   →       1              |        4.68 ms →        4.68 ms   (+0.10%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        2.42 ms   (-0.37%) |       1   →       1              |        2.43 ms →        2.42 ms   (-0.37%) | 
  │ ├ sirius::Non_local_operator                                        |       63.15 μs →       63.47 μs   (+0.52%) |       2   →       2              |      126.29 μs →      126.95 μs   (+0.52%) | 
- │ ├ sirius::D_operator::initialize                                    |       96.97 μs →        1.29 ms (+1226.08%) |       1   →       1              |       96.97 μs →        1.29 ms (+1226.08%) | 
- │ └ sirius::Q_operator::initialize                                    |       67.97 μs →        2.46 ms (+3522.52%) |       1   →       1              |       67.97 μs →        2.46 ms (+3522.52%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.04 s  →        4.21 s    (+4.26%) |       1   →       1              |        4.04 s  →        4.21 s    (+4.26%) | 
- │ ├ sirius::Hamiltonian_k                                             |      206.22 μs →      384.67 μs  (+86.54%) |       4   →       4              |      824.88 μs →        1.54 ms  (+86.54%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      200.96 μs →      377.79 μs  (+87.99%) |       4   →       4              |      803.86 μs →        1.51 ms  (+87.99%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.68 μs →        3.34 μs   (-9.27%) |       4   →       4              |       14.73 μs →       13.36 μs   (-9.27%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.01 s  →        1.05 s    (+4.17%) |       4   →       4              |        4.04 s  →        4.20 s    (+4.17%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.19 ms →       32.19 ms   (-0.02%) |      16   →      16              |      515.09 ms →      514.96 ms   (-0.02%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.90 ms →       14.53 ms   (-2.43%) |       4   →       4              |       59.58 ms →       58.14 ms   (-2.43%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.31 ms →        5.27 ms   (-0.63%) |       4   →       4              |       21.22 ms →       21.09 ms   (-0.63%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.82 ms →      360.27 ms   (+1.54%) |       4   →       4              |        1.42 s  →        1.44 s    (+1.54%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      258.52 ms →      263.08 ms   (+1.76%) |       4   →       4              |        1.03 s  →        1.05 s    (+1.76%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.12 ms →       66.16 ms   (+3.18%) |       4   →       4              |      256.49 ms →      264.65 ms   (+3.18%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.51 ms →       16.48 ms   (-0.17%) |       4   →       4              |       66.04 ms →       65.93 ms   (-0.17%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.51 ms →       16.48 ms   (-0.17%) |       4   →       4              |       66.03 ms →       65.92 ms   (-0.17%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.06 ms →       43.18 ms   (+5.17%) |       4   →       4              |      164.23 ms →      172.73 ms   (+5.17%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.70 ms →       16.28 ms   (-2.50%) |       4   →       4              |       66.80 ms →       65.14 ms   (-2.50%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.70 ms →       16.28 ms   (-2.50%) |       4   →       4              |       66.79 ms →       65.12 ms   (-2.50%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.33 ms →       56.10 ms   (+5.19%) |       4   →       4              |      213.31 ms →      224.39 ms   (+5.19%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.21 ms →       38.06 ms   (+8.11%) |       4   →       4              |      140.83 ms →      152.25 ms   (+8.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.95 ms   (-0.16%) |       4   →       4              |        7.80 ms →        7.78 ms   (-0.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.13 ms →       40.97 ms   (+2.10%) |       4   →       4              |      160.53 ms →      163.90 ms   (+2.10%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.01 ms →        7.90 ms  (+12.65%) |       4   →       4              |       28.05 ms →       31.60 ms  (+12.65%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.11 ms   (+0.08%) |       8   →       8              |      216.74 ms →      216.90 ms   (+0.08%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.37 ms →       15.05 ms   (+4.74%) |       8   →       8              |      114.95 ms →      120.40 ms   (+4.74%) | 
  │ │ │ ├ sddk::inner                                                   |       14.31 ms                             |       8                          |      114.46 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       57.68 μs                             |       8                          |      461.41 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.00 ms            |                   8              |                       120.02 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        80.50 ns            |                   8              |                       644.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.83 ms            |                   8              |                       118.65 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       296.38 ns            |                   8              |                         2.37 μs            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      354.57 ms →      388.53 ms   (+9.58%) |       4   →       4              |        1.42 s  →        1.55 s    (+9.58%) | 
  │ │ ├ sddk::transform                                                 |       27.80 ms                             |       4                          |      111.19 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       34.48 μs                             |       4                          |      137.90 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |      933.48 μs                             |       4                          |        3.73 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       26.98 μs                             |       4                          |      107.93 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        26.67 ms            |                   4              |                       106.69 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        26.54 ms            |                   4              |                       106.17 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      411.75 ns →      407.75 ns   (-0.97%) |       4   →       4              |        1.65 μs →        1.63 μs   (-0.97%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      759.02 s  →      285.98 s   (-62.32%) |       1   →       1              |      759.02 s  →      285.98 s   (-62.32%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.91 ms →        5.33 ms   (-9.82%) |      19   →      18     (-5.26%) |      112.25 ms →       95.90 ms  (-14.57%) | 
  │ ├ sirius::Density                                                   |                       135.05 ms            |                   1              |                       135.05 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.61 ms            |                   2              |                        11.22 ms            | 
  │ │ └ sirius::Density::update                                         |                       123.53 ms            |                   1              |                       123.53 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       123.07 ms            |                   1              |                       123.07 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       145.09 μs            |                   1              |                       145.09 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       111.25 ms            |                   1              |                       111.25 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        11.22 ms            |                   1              |                        11.22 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       27.09 s  →       11.90 s   (-56.09%) |      28   →      24    (-14.29%) |      758.55 s  →      285.52 s   (-62.36%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.45 ms →        8.12 ms  (+82.64%) |      28   →      24    (-14.29%) |      124.48 ms →      194.87 ms  (+56.55%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.08 ms →        4.17 ms   (+2.23%) |      28   →      24    (-14.29%) |      114.35 ms →      100.19 ms  (-12.38%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      964.20 μs →      953.15 μs   (-1.15%) |      28   →      24    (-14.29%) |       27.00 ms →       22.88 ms  (-15.27%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.23 ms →        2.29 ms   (+2.82%) |      28   →      24    (-14.29%) |       62.46 ms →       55.05 ms  (-11.87%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.89 μs →       64.51 μs   (-0.59%) |      56   →      48    (-14.29%) |        3.63 ms →        3.10 ms  (-14.79%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       94.30 μs →        1.29 ms (+1272.59%) |      28   →      24    (-14.29%) |        2.64 ms →       31.06 ms (+1076.51%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       70.79 μs →        2.46 ms (+3372.05%) |      28   →      24    (-14.29%) |        1.98 ms →       58.99 ms (+2876.05%) | 
+ │ │ ├ sirius::Band::solve                                             |       24.96 s  →        9.75 s   (-60.92%) |      28   →      24    (-14.29%) |      698.96 s  →      234.11 s   (-66.51%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      200.66 μs →      319.08 μs  (+59.02%) |     112   →      96    (-14.29%) |       22.47 ms →       30.63 ms  (+36.30%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      194.41 μs →      312.10 μs  (+60.54%) |     112   →      96    (-14.29%) |       21.77 ms →       29.96 ms  (+37.61%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.79 μs →        3.75 μs  (-21.58%) |     112   →      96    (-14.29%) |      535.97 μs →      360.25 μs  (-32.79%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        6.24 s  →        2.44 s   (-60.94%) |     112   →      96    (-14.29%) |      698.94 s  →      233.99 s   (-66.52%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       16.73 ms →       12.13 ms  (-27.50%) |     112   →      96    (-14.29%) |        1.87 s  →        1.16 s   (-37.86%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      753.84 μs →      583.62 ns  (-99.92%) |     672   →     576    (-14.29%) |      506.58 ms →      336.17 μs  (-99.93%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.86 ms →        1.84 ms   (-0.84%) |     112   →      96    (-14.29%) |      208.19 ms →      176.95 ms  (-15.01%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      357.83 μs →      359.27 μs   (+0.40%) |     112   →      96    (-14.29%) |       40.08 ms →       34.49 ms  (-13.94%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      548.59 μs →      552.99 μs   (+0.80%) |     224   →     192    (-14.29%) |      122.88 ms →      106.17 ms  (-13.60%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        6.21 s  →        2.41 s   (-61.14%) |     112   →      96    (-14.29%) |      695.84 s  →      231.78 s   (-66.69%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       71.96 ms →       67.18 ms   (-6.64%) |     811   →     869     (+7.15%) |       58.36 s  →       58.38 s    (+0.04%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       45.91 ms →       42.85 ms   (-6.66%) |     811   →     869     (+7.15%) |       37.23 s  →       37.23 s    (+0.01%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.59 ms →        8.79 ms   (+2.27%) |     811   →     869     (+7.15%) |        6.97 s  →        7.63 s    (+9.59%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       66.04 μs →      251.62 μs (+281.04%) |     811   →     869     (+7.15%) |       53.55 ms →      218.66 ms (+308.29%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      463.24 μs →        2.26 ms (+387.94%) |     112   →      96    (-14.29%) |       51.88 ms →      216.99 ms (+318.24%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.16 ms →        6.89 ms   (-3.76%) |     811   →     869     (+7.15%) |        5.81 s  →        5.99 s    (+3.13%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       66.46 μs →       98.44 μs  (+48.11%) |     811   →     869     (+7.15%) |       53.90 ms →       85.54 ms  (+58.71%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      464.05 μs →      869.74 μs  (+87.42%) |     112   →      96    (-14.29%) |       51.97 ms →       83.49 ms  (+60.65%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.12 ms →        9.61 ms   (-5.08%) |     811   →     869     (+7.15%) |        8.21 s  →        8.35 s    (+1.71%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.31 ms →        6.21 ms   (-1.55%) |     811   →     869     (+7.15%) |        5.12 s  →        5.40 s    (+5.50%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.52 ms   (-0.58%) |     811   →     869     (+7.15%) |        1.24 s  →        1.32 s    (+6.53%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        9.01 ms →        8.48 ms   (-5.89%) |     811   →     869     (+7.15%) |        7.31 s  →        7.37 s    (+0.84%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.33 ms →        1.54 ms  (+15.49%) |     811   →     869     (+7.15%) |        1.08 s  →        1.34 s   (+23.75%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.74 ms →        7.15 ms   (-7.65%) |    1.62 K →    1.74 K   (+7.15%) |       12.56 s  →       12.43 s    (-1.04%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       21.25 ms →       29.11 ms  (+37.03%) |     811   →     869     (+7.15%) |       17.23 s  →       25.30 s   (+46.82%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.35 ms                             |    1.51 K                        |        3.54 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.65 μs                             |    1.67 K                        |       54.39 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.96 ms            |                1.64 K            |                         3.22 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       133.97 ns            |                1.64 K            |                       219.98 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.95 ms            |                1.64 K            |                         3.20 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       222.57 ns            |                1.64 K            |                       365.46 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |        1.05 ms →        1.08 ms   (+3.32%) |     811   →     869     (+7.15%) |      849.69 ms →      940.73 ms  (+10.71%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.58 ms →        1.63 ms   (+3.27%) |     811   →     869     (+7.15%) |        1.28 s  →        1.42 s   (+10.65%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.18 ms                             |    3.13 K                        |        9.96 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.73 μs                             |    3.13 K                        |       42.99 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      167.44 μs                             |    3.13 K                        |      524.42 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.35 μs                             |    4.53 K                        |       46.87 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.44 ms            |                3.38 K            |                        18.38 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.69 ms            |                4.93 K            |                        18.16 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.34 ms →        5.47 ms  (-13.78%) |     811   →     869     (+7.15%) |        5.14 s  →        4.75 s    (-7.61%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.49 ms                             |     811                          |        3.64 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.84 μs                             |    1.00 K                        |       27.90 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.61 ms            |                 869              |                         3.14 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       117.55 ns            |                 869              |                       102.15 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.60 ms            |                 869              |                         3.13 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       267.40 ns            |                 869              |                       232.37 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      747.33 ms →      143.83 ms  (-80.75%) |     811   →     869     (+7.15%) |      606.09 s  →      124.99 s   (-79.38%) | 
  │ │ │ │   ├ sirius::residuals                                         |        8.01 ms →        7.69 ms   (-3.92%) |     800   →     854     (+6.75%) |        6.41 s  →        6.57 s    (+2.56%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.28 ms                             |     738                          |        5.37 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       24.63 μs                             |     738                          |       18.18 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      300.19 μs                             |     738                          |      221.54 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       15.69 μs                             |    1.48 K                        |       23.15 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         7.20 ms            |                 773              |                         5.57 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.56 ms            |                1.55 K            |                         5.51 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      879.27 μs →      561.49 μs  (-36.14%) |     738   →     773     (+4.74%) |      648.90 ms →      434.03 ms  (-33.11%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       21.48 ms →       36.34 ms  (+69.19%) |     120   →     321   (+167.50%) |        2.58 s  →       11.66 s  (+352.59%) | 
  │ │ │ │     ├ sddk::transform                                         |       20.07 ms                             |     128                          |        2.57 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       25.84 μs                             |     128                          |        3.31 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.49 ms                             |     128                          |      190.53 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       20.71 μs                             |     136                          |        2.82 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        21.20 ms            |                 546              |                        11.57 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        14.91 ms            |                 771              |                        11.50 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      537.35 ns →      476.36 ns  (-11.35%) |     112   →      96    (-14.29%) |       60.18 μs →       45.73 μs  (-24.01%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.43 μs →        3.58 ms (+16586.16%) |      28   →      24    (-14.29%) |      599.90 μs →       85.80 ms (+14202.42%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      639.76 μs →       59.50 ms (+9200.37%) |      28   →      24    (-14.29%) |       17.91 ms →        1.43 s  (+7871.75%) | 
+ │ │ ├ sirius::Density::generate                                       |      912.20 ms →      920.89 ms   (+0.95%) |      28   →      24    (-14.29%) |       25.54 s  →       22.10 s   (-13.47%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      524.46 ms →      568.02 ms   (+8.31%) |      28   →      24    (-14.29%) |       14.68 s  →       13.63 s    (-7.17%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.45 ms →       26.02 ms   (+6.43%) |     112   →      96    (-14.29%) |        2.74 s  →        2.50 s    (-8.77%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.01 μs →        4.78 μs  (-40.26%) |     112   →      96    (-14.29%) |      896.63 μs →      459.13 μs  (-48.79%) | 
+ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.78 μs →       12.30 μs  (-16.77%) |       8   →       8              |      118.27 μs →       98.44 μs  (-16.77%) | 
! │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.37 ms →       21.91 ms   (+7.54%) |     112   →      96    (-14.29%) |        2.28 s  →        2.10 s    (-7.83%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.62 ms →       37.84 ms  (+27.76%) |     112   →      96    (-14.29%) |        3.32 s  →        3.63 s    (+9.51%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        8.90 μs →        9.49 μs   (+6.64%) |     112   →      96    (-14.29%) |      997.09 μs →      911.43 μs   (-8.59%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.29%) |     112   →      96    (-14.29%) |      162.94 ms →      140.07 ms  (-14.03%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.67 ms →       29.13 ms   (+5.28%) |     112   →      96    (-14.29%) |        3.10 s  →        2.80 s    (-9.76%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.58 ms →        5.04 ms  (+40.73%) |     112   →      96    (-14.29%) |      401.34 ms →      484.14 ms  (+20.63%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      782.27 ns →      641.43 ns  (-18.00%) |     112   →      96    (-14.29%) |       87.61 μs →       61.58 μs  (-29.72%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.72 ms →       42.83 ms   (+0.24%) |     112   →      96    (-14.29%) |        4.79 s  →        4.11 s   (-14.08%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.26%) |      28   →      24    (-14.29%) |       45.93 ms →       39.26 ms  (-14.51%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.52 ms →       89.04 ms   (+0.59%) |      28   →      24    (-14.29%) |        2.48 s  →        2.14 s   (-13.78%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.30 ms →       88.81 ms   (+0.58%) |      28   →      24    (-14.29%) |        2.47 s  →        2.13 s   (-13.78%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      287.96 ms →      258.84 ms  (-10.11%) |      28   →      24    (-14.29%) |        8.06 s  →        6.21 s   (-22.95%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      287.96 ms →      258.83 ms  (-10.11%) |      28   →      24    (-14.29%) |        8.06 s  →        6.21 s   (-22.96%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.86 ms →       25.81 ms  (-10.55%) |      28   →      24    (-14.29%) |      808.07 ms →      619.54 ms  (-23.33%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      229.24 ms →      206.66 ms   (-9.85%) |      28   →      24    (-14.29%) |        6.42 s  →        4.96 s   (-22.73%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       28.07 ms →       25.10 ms  (-10.60%) |      28   →      24    (-14.29%) |      786.08 ms →      602.37 ms  (-23.37%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       90.36 ms →       81.01 ms  (-10.35%) |      28   →      24    (-14.29%) |        2.53 s  →        1.94 s   (-23.15%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.85 ms →        9.37 ms  (+59.98%) |      28   →      24    (-14.29%) |      163.93 ms →      224.79 ms  (+37.12%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                        10.89 ms            |                 216              |                         2.35 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                        10.25 ms            |                 216              |                         2.21 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                        10.25 ms            |                 216              |                         2.21 s             | 
+ │ │ ├ sirius::Density::mix                                            |      228.91 ms →      152.02 ms  (-33.59%) |      28   →      24    (-14.29%) |        6.41 s  →        3.65 s   (-43.08%) | 
! │ │ │ ├ sirius::Density::mixer_input                                  |      973.64 μs →        1.04 ms   (+7.27%) |      28   →      24    (-14.29%) |       27.26 ms →       25.07 ms   (-8.05%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.14 ms →       10.03 ms  (-10.00%) |     364   →     304    (-16.48%) |        4.06 s  →        3.05 s   (-24.84%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.92 ms →        9.75 ms  (-10.73%) |     364   →     304    (-16.48%) |        3.97 s  →        2.96 s   (-25.45%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.92 ms →        9.75 ms  (-10.73%) |     364   →     304    (-16.48%) |        3.97 s  →        2.96 s   (-25.45%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.94 ms →        6.69 ms   (-3.66%) |      28   →      24    (-14.29%) |      194.38 ms →      160.50 ms  (-17.43%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.14 ms →        5.56 ms   (-9.50%) |      28   →      24    (-14.29%) |      171.95 ms →      133.39 ms  (-22.43%) | 
+ │ │ ├ sirius::Potential::generate                                     |      571.52 ms →      556.80 ms   (-2.58%) |      28   →      24    (-14.29%) |       16.00 s  →       13.36 s   (-16.49%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.27 ms →      137.32 ms   (+0.03%) |      28   →      24    (-14.29%) |        3.84 s  →        3.30 s   (-14.26%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.22 ms →       18.11 ms (+247.30%) |      28   →      24    (-14.29%) |      146.02 ms →      434.68 ms (+197.68%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.66 ms →       10.74 ms   (+0.76%) |      28   →      24    (-14.29%) |      298.52 ms →      257.82 ms  (-13.63%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.48 ms →       10.42 ms   (-0.60%) |      28   →      24    (-14.29%) |      293.41 ms →      249.98 ms  (-14.80%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.48 ms →       10.42 ms   (-0.60%) |      28   →      24    (-14.29%) |      293.39 ms →      249.96 ms  (-14.80%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      541.38 μs →      460.82 μs  (-14.88%) |      56   →      48    (-14.29%) |       30.32 ms →       22.12 ms  (-27.04%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       47.49 ms →       27.30 ms  (-42.52%) |      28   →      24    (-14.29%) |        1.33 s  →      655.14 ms  (-50.73%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.49 ms →       24.96 ms  (-47.43%) |      28   →      24    (-14.29%) |        1.33 s  →      599.14 ms  (-54.94%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        1.19 ms  (-60.61%) |      56   →      24    (-57.14%) |      169.52 ms →       28.62 ms  (-83.12%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        5.41 ms                             |      28                          |      151.57 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                         8.30 ms            |                  48              |                       398.47 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.77 ms →        5.23 ms  (-22.73%) |      28   →      24    (-14.29%) |      189.57 ms →      125.55 ms  (-33.77%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.05 ms →       91.01 ms   (-0.05%) |      28   →      24    (-14.29%) |        2.55 s  →        2.18 s   (-14.32%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.54 ms →      293.72 ms   (+2.50%) |      28   →      24    (-14.29%) |        8.02 s  →        7.05 s   (-12.14%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      289.11 ms →      253.72 ms  (-12.24%) |      28   →      24    (-14.29%) |        8.10 s  →        6.09 s   (-24.78%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      289.11 ms →      253.71 ms  (-12.24%) |      28   →      24    (-14.29%) |        8.10 s  →        6.09 s   (-24.78%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       31.46 ms →       24.40 ms  (-22.44%) |      28   →      24    (-14.29%) |      880.75 ms →      585.52 ms  (-33.52%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.21 ms →      204.75 ms   (-9.49%) |      28   →      24    (-14.29%) |        6.33 s  →        4.91 s   (-22.42%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.66 ms →       23.42 ms  (-15.36%) |      28   →      24    (-14.29%) |      774.62 ms →      562.00 ms  (-27.45%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.83 ms →        5.73 ms   (-1.72%) |      28   →      24    (-14.29%) |      163.18 ms →      137.46 ms  (-15.76%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.70 ms                             |     196                          |        2.10 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.43 ms                             |     196                          |        2.04 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.43 ms                             |     196                          |        2.04 s                              | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.16 ms →       10.68 ms   (+5.03%) |      84   →      72    (-14.29%) |      853.85 ms →      768.67 ms   (-9.98%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.95 ms →       10.15 ms   (+2.02%) |      84   →      72    (-14.29%) |      835.66 ms →      730.72 ms  (-12.56%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        9.99 ms →       10.16 ms   (+1.73%) |      28   →      24    (-14.29%) |      279.68 ms →      243.87 ms  (-12.80%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      110.21 μs →       15.48 ms (+13944.21%) |      28   →      24    (-14.29%) |        3.09 ms →      371.48 ms (+11937.89%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      105.20 μs →       15.47 ms (+14606.66%) |      28   →      24    (-14.29%) |        2.95 ms →      371.33 ms (+12505.71%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.18 ms →        4.70 ms   (-9.34%) |       2   →       2              |       10.36 ms →        9.39 ms   (-9.34%) | 
+ │ ├ sirius::Periodic_function|inner                                   |       11.76 ms →       10.22 ms  (-13.06%) |       6   →       6              |       70.55 ms →       61.34 ms  (-13.06%) | 
+ │ │ └ sirius::Periodic_function|inner_local                           |       11.75 ms →       10.07 ms  (-14.25%) |       6   →       6              |       70.48 ms →       60.44 ms  (-14.25%) | 
+ │ │   └ sirius::Smooth_periodic_function|inner_local                  |       11.75 ms →       10.07 ms  (-14.26%) |       6   →       6              |       70.48 ms →       60.43 ms  (-14.26%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       11.23 ms →       10.17 ms   (-9.48%) |       3   →       3              |       33.69 ms →       30.50 ms   (-9.48%) | 
+ │   └ sirius::Smooth_periodic_function|inner_local                    |       11.22 ms →       10.04 ms  (-10.52%) |       3   →       3              |       33.67 ms →       30.13 ms  (-10.52%) | 
  ├ sirius::Periodic_function|inner                                     |       11.32 ms →       10.20 ms   (-9.91%) |       2   →       2              |       22.64 ms →       20.40 ms   (-9.91%) | 
+ │ └ sirius::Periodic_function|inner_local                             |       11.31 ms →       10.12 ms  (-10.58%) |       2   →       2              |       22.62 ms →       20.23 ms  (-10.58%) | 
+ │   └ sirius::Smooth_periodic_function|inner_local                    |       11.31 ms →       10.12 ms  (-10.58%) |       2   →       2              |       22.62 ms →       20.23 ms  (-10.58%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.85 ms →       10.14 ms   (-6.58%) |       1   →       1              |       10.85 ms →       10.14 ms   (-6.58%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.84 ms →       10.02 ms   (-7.60%) |       1   →       1              |       10.84 ms →       10.02 ms   (-7.60%) | 
+ └ sirius::finalize                                                    |      391.39 ms →      340.01 ms  (-13.13%) |       1   →       1              |      391.39 ms →      340.01 ms  (-13.13%) | 
  ====================================================================================================================================================================================================
```
