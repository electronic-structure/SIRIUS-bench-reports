# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      334.82 s  →      238.47 s   (-28.78%) |       1   →       1              |      334.82 s  →      238.47 s   (-28.78%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.71 s    (-0.65%) |       1   →       1              |        2.73 s  →        2.71 s    (-0.65%) | 
  ├ sirius::Simulation_context::initialize                              |        3.09 s  →        2.92 s    (-5.37%) |       1   →       1              |        3.09 s  →        2.92 s    (-5.37%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       48.35 ms →       11.97 ms  (-75.23%) |       1   →       1              |       48.35 ms →       11.97 ms  (-75.23%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      184.16 ms →      175.64 ms   (-4.62%) |       1   →       1              |      184.16 ms →      175.64 ms   (-4.62%) | 
  │ │ ├ sirius::Atom_type::init                                         |       79.63 ms →       75.91 ms   (-4.67%) |       2   →       2              |      159.25 ms →      151.82 ms   (-4.67%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.82 ms →       23.75 ms   (-4.32%) |       1   →       1              |       24.82 ms →       23.75 ms   (-4.32%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.47 ms →        6.28 ms   (-3.04%) |       1   →       1              |        6.47 ms →        6.28 ms   (-3.04%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.31 ms →       17.43 ms   (-4.77%) |       1   →       1              |       18.31 ms →       17.43 ms   (-4.77%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.28 ms →       17.41 ms   (-4.75%) |       1   →       1              |       18.28 ms →       17.41 ms   (-4.75%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.14 ms   (-0.48%) |       1   →       1              |        4.16 ms →        4.14 ms   (-0.48%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.34 ms   (-0.57%) |       1   →       1              |        2.35 ms →        2.34 ms   (-0.57%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.58 μs →      105.51 μs   (+2.85%) |       1   →       1              |      102.58 μs →      105.51 μs   (+2.85%) | 
  │ └ sirius::Simulation_context::update                                |        2.80 s  →        2.68 s    (-4.34%) |       1   →       1              |        2.80 s  →        2.68 s    (-4.34%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.08 ms →       10.85 ms   (-2.08%) |       1   →       1              |       11.08 ms →       10.85 ms   (-2.08%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.64 ms →        4.41 ms   (-5.13%) |       1   →       1              |        4.64 ms →        4.41 ms   (-5.13%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.40 ms →        6.41 ms   (+0.09%) |       1   →       1              |        6.40 ms →        6.41 ms   (+0.09%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.38 ms →        6.39 ms   (+0.10%) |       1   →       1              |        6.38 ms →        6.39 ms   (+0.10%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.88 ms   (-0.20%) |       1   →       1              |        3.89 ms →        3.88 ms   (-0.20%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.47%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.47%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.30 μs →      104.17 μs   (+3.86%) |       1   →       1              |      100.30 μs →      104.17 μs   (+3.86%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.54 ms →       62.49 ms   (-1.66%) |       2   →       2              |      127.09 ms →      124.98 ms   (-1.66%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.17 ms →        5.15 ms   (-0.39%) |       2   →       2              |       10.34 ms →       10.30 ms   (-0.39%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.49 ms →        4.48 ms   (-0.24%) |       1   →       1              |        4.49 ms →        4.48 ms   (-0.24%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       23.02 ms →       21.96 ms   (-4.59%) |       2   →       2              |       46.03 ms →       43.92 ms   (-4.59%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.83 ms →       14.81 ms   (-0.14%) |       2   →       2              |       29.67 ms →       29.63 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       20.06 ms →       19.94 ms   (-0.60%) |       4   →       4              |       80.25 ms →       79.76 ms   (-0.60%) | 
  │   ├ sddk::Gvec::init                                                |      179.81 ms →      170.21 ms   (-5.34%) |       2   →       2              |      359.62 ms →      340.42 ms   (-5.34%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.69 ms →      128.07 ms   (-3.48%) |       2   →       2              |      265.37 ms →      256.13 ms   (-3.48%) | 
+ │   ├ sddk::Gvec_shells                                               |      211.33 ms →      175.09 ms  (-17.15%) |       1   →       1              |      211.33 ms →      175.09 ms  (-17.15%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.34 ms →        1.32 ms   (-2.13%) |       1   →       1              |        1.34 ms →        1.32 ms   (-2.13%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      298.23 ms →      294.71 ms   (-1.18%) |       2   →       2              |      596.45 ms →      589.43 ms   (-1.18%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       83.69 ms →       76.29 ms   (-8.84%) |       1   →       1              |       83.69 ms →       76.29 ms   (-8.84%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.84 μs →        2.44 μs  (-14.24%) |       4   →       4              |       11.38 μs →        9.76 μs  (-14.24%) | 
  │ └ sirius::K_point_set::initialize                                   |       83.59 ms →       76.18 ms   (-8.87%) |       1   →       1              |       83.59 ms →       76.18 ms   (-8.87%) | 
  │   └ sirius::K_point::initialize                                     |       20.89 ms →       19.03 ms   (-8.87%) |       4   →       4              |       83.55 ms →       76.13 ms   (-8.87%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       15.91 ms →       14.15 ms  (-11.07%) |       4   →       4              |       63.63 ms →       56.59 ms  (-11.07%) | 
  │     │ └ sddk::Gvec::init                                            |        4.03 ms →        3.84 ms   (-4.82%) |       4   →       4              |       16.12 ms →       15.34 ms   (-4.82%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.81 μs →        9.20 μs   (+4.41%) |       4   →       4              |       35.25 μs →       36.80 μs   (+4.41%) | 
  │     └ sirius::K_point::update                                       |        3.49 ms →        3.58 ms   (+2.56%) |       4   →       4              |       13.95 ms →       14.31 ms   (+2.56%) | 
- │       └ sirius::Beta_projectors                                     |        1.78 ms →        2.04 ms  (+14.37%) |       4   →       4              |        7.12 ms →        8.14 ms  (+14.37%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      927.08 μs →        1.01 ms   (+8.54%) |       4   →       4              |        3.71 ms →        4.02 ms   (+8.54%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.26 ms →        5.22 ms   (-0.83%) |       2   →       2              |       10.52 ms →       10.44 ms   (-0.83%) | 
  ├ sirius::Potential                                                   |      170.74 ms →      158.06 ms   (-7.43%) |       1   →       1              |      170.74 ms →      158.06 ms   (-7.43%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.78 ms   (+0.81%) |       6   →       6              |       34.42 ms →       34.70 ms   (+0.81%) | 
  │ └ sirius::Potential::update                                         |      135.64 ms →      122.63 ms   (-9.59%) |       1   →       1              |      135.64 ms →      122.63 ms   (-9.59%) | 
  │   └ sirius::Potential::generate_local_potential                     |      134.96 ms →      121.92 ms   (-9.67%) |       1   →       1              |      134.96 ms →      121.92 ms   (-9.67%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.94 ms →      109.58 ms   (-3.83%) |       1   →       1              |      113.94 ms →      109.58 ms   (-3.83%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       20.49 ms →       11.44 ms  (-44.17%) |       1   →       1              |       20.49 ms →       11.44 ms  (-44.17%) | 
  ├ sirius::Density                                                     |      142.27 ms →      135.26 ms   (-4.93%) |       1   →       1              |      142.27 ms →      135.26 ms   (-4.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.27 ms →        5.17 ms   (-2.05%) |       2   →       2              |       10.55 ms →       10.33 ms   (-2.05%) | 
  │ └ sirius::Density::update                                           |      131.46 ms →      124.66 ms   (-5.17%) |       1   →       1              |      131.46 ms →      124.66 ms   (-5.17%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      131.06 ms →      124.25 ms   (-5.20%) |       1   →       1              |      131.06 ms →      124.25 ms   (-5.20%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       104.07 μs            |                   1              |                       104.07 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.03 ms →      112.24 ms   (-0.70%) |       1   →       1              |      113.03 ms →      112.24 ms   (-0.70%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       17.59 ms →       11.46 ms  (-34.85%) |       1   →       1              |       17.59 ms →       11.46 ms  (-34.85%) | 
  ├ sirius::Density::initial_density                                    |      176.83 ms →      178.54 ms   (+0.96%) |       1   →       1              |      176.83 ms →      178.54 ms   (+0.96%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      112.07 ms →      111.85 ms   (-0.20%) |       1   →       1              |      112.07 ms →      111.85 ms   (-0.20%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.05 ms →       10.87 ms   (-1.64%) |       2   →       2              |       22.10 ms →       21.74 ms   (-1.64%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.48 ms →       12.55 ms  (+19.76%) |       1   →       1              |       10.48 ms →       12.55 ms  (+19.76%) | 
  ├ sirius::Potential::generate                                         |      587.22 ms →      593.97 ms   (+1.15%) |       1   →       1              |      587.22 ms →      593.97 ms   (+1.15%) | 
  │ ├ sirius::Potential::poisson                                        |      139.48 ms →      136.74 ms   (-1.97%) |       1   →       1              |      139.48 ms →      136.74 ms   (-1.97%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       18.14 ms →       16.26 ms  (-10.35%) |       1   →       1              |       18.14 ms →       16.26 ms  (-10.35%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.30 ms →       10.26 ms   (-0.44%) |       1   →       1              |       10.30 ms →       10.26 ms   (-0.44%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.91 ms   (+0.27%) |       1   →       1              |        9.88 ms →        9.91 ms   (+0.27%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.91 ms   (+0.27%) |       1   →       1              |        9.88 ms →        9.91 ms   (+0.27%) | 
  │ ├ sirius::Periodic_function::add                                    |      564.02 μs →      565.78 μs   (+0.31%) |       2   →       2              |        1.13 ms →        1.13 ms   (+0.31%) | 
  │ ├ sirius::Potential::xc                                             |       52.13 ms →       56.19 ms   (+7.79%) |       1   →       1              |       52.13 ms →       56.19 ms   (+7.79%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.12 ms →       53.89 ms   (+3.38%) |       1   →       1              |       52.12 ms →       53.89 ms   (+3.38%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.63 ms →        5.69 ms   (+0.99%) |       2   →       2              |       11.26 ms →       11.37 ms   (+0.99%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.32 ms →        6.01 ms  (+12.86%) |       1   →       1              |        5.32 ms →        6.01 ms  (+12.86%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.79 ms →        5.92 ms   (+2.15%) |       1   →       1              |        5.79 ms →        5.92 ms   (+2.15%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.96 ms →       92.59 ms   (-1.46%) |       1   →       1              |       93.96 ms →       92.59 ms   (-1.46%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.36 ms →      300.04 ms   (+2.28%) |       1   →       1              |      293.36 ms →      300.04 ms   (+2.28%) | 
  ├ sirius::Hamiltonian0                                                |        8.56 ms →        8.43 ms   (-1.51%) |       1   →       1              |        8.56 ms →        8.43 ms   (-1.51%) | 
  │ ├ sirius::Local_operator                                            |        8.21 ms →        8.08 ms   (-1.58%) |       1   →       1              |        8.21 ms →        8.08 ms   (-1.58%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        5.02 ms →        4.72 ms   (-5.97%) |       1   →       1              |        5.02 ms →        4.72 ms   (-5.97%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.30 ms →        2.45 ms   (+6.33%) |       1   →       1              |        2.30 ms →        2.45 ms   (+6.33%) | 
  │ ├ sirius::Non_local_operator                                        |       63.33 μs →       63.21 μs   (-0.19%) |       2   →       2              |      126.66 μs →      126.42 μs   (-0.19%) | 
  │ ├ sirius::D_operator::initialize                                    |       99.16 μs →       97.38 μs   (-1.79%) |       1   →       1              |       99.16 μs →       97.38 μs   (-1.79%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.59 μs →       69.78 μs   (+1.74%) |       1   →       1              |       68.59 μs →       69.78 μs   (+1.74%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.12 s  →        3.09 s    (-1.00%) |       1   →       1              |        3.12 s  →        3.09 s    (-1.00%) | 
- │ ├ sirius::Hamiltonian_k                                             |      203.53 μs →      378.39 μs  (+85.91%) |       4   →       4              |      814.14 μs →        1.51 ms  (+85.91%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      198.72 μs →      372.79 μs  (+87.59%) |       4   →       4              |      794.89 μs →        1.49 ms  (+87.59%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |        3.29 μs →        3.75 μs  (+14.16%) |       4   →       4              |       13.15 μs →       15.02 μs  (+14.16%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      780.60 ms →      772.66 ms   (-1.02%) |       4   →       4              |        3.12 s  →        3.09 s    (-1.02%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       33.07 ms →       32.26 ms   (-2.45%) |      16   →      16              |      529.08 ms →      516.14 ms   (-2.45%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       15.68 ms →       14.58 ms   (-7.03%) |       4   →       4              |       62.72 ms →       58.31 ms   (-7.03%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.46 ms →        5.38 ms   (-1.38%) |       4   →       4              |       21.84 ms →       21.53 ms   (-1.38%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.91 ms →      354.61 ms   (-0.64%) |       4   →       4              |        1.43 s  →        1.42 s    (-0.64%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      260.27 ms →      258.22 ms   (-0.79%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.79%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.01 ms →       63.28 ms   (-1.15%) |       4   →       4              |      256.05 ms →      253.11 ms   (-1.15%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.61 ms →       16.38 ms   (-1.43%) |       4   →       4              |       66.46 ms →       65.51 ms   (-1.43%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.61 ms →       16.37 ms   (-1.43%) |       4   →       4              |       66.45 ms →       65.50 ms   (-1.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.01 ms →       40.51 ms   (-1.22%) |       4   →       4              |      164.03 ms →      162.03 ms   (-1.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.58 ms →       16.41 ms   (-1.01%) |       4   →       4              |       66.31 ms →       65.64 ms   (-1.01%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.57 ms →       16.41 ms   (-1.01%) |       4   →       4              |       66.30 ms →       65.62 ms   (-1.01%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       55.70 ms →       53.65 ms   (-3.68%) |       4   →       4              |      222.80 ms →      214.60 ms   (-3.68%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       37.65 ms →       35.62 ms   (-5.39%) |       4   →       4              |      150.61 ms →      142.50 ms   (-5.39%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.93 ms   (-0.39%) |       4   →       4              |        7.76 ms →        7.73 ms   (-0.39%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.44 ms →       40.23 ms   (-0.52%) |       4   →       4              |      161.77 ms →      160.92 ms   (-0.52%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.32 ms →        7.12 ms   (-2.77%) |       4   →       4              |       29.28 ms →       28.47 ms   (-2.77%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.11 ms →       27.10 ms   (-0.05%) |       8   →       8              |      216.88 ms →      216.77 ms   (-0.05%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.26 ms →       14.84 ms   (+4.03%) |       8   →       8              |      114.11 ms →      118.71 ms   (+4.03%) | 
  │ │ │ ├ sddk::inner                                                   |       14.20 ms                             |       8                          |      113.59 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       56.16 μs                             |       8                          |      449.31 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.80 ms            |                   8              |                       118.37 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        32.88 ns            |                   8              |                       263.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.62 ms            |                   8              |                       116.98 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        23.38 ns            |                   8              |                       187.00 ns            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      121.38 ms →      118.39 ms   (-2.47%) |       4   →       4              |      485.51 ms →      473.54 ms   (-2.47%) | 
  │ │ ├ sddk::transform                                                 |       27.81 ms                             |       4                          |      111.23 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       25.15 μs                             |       4                          |      100.58 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |      957.82 μs                             |       4                          |        3.83 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       19.47 μs                             |       4                          |       77.87 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        23.56 ms            |                   4              |                        94.24 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        23.38 ms            |                   4              |                        93.51 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      401.50 ns →      434.00 ns   (+8.09%) |       4   →       4              |        1.61 μs →        1.74 μs   (+8.09%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      323.68 s  →      227.79 s   (-29.63%) |       1   →       1              |      323.68 s  →      227.79 s   (-29.63%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.67 ms   (-0.81%) |      19   →      19              |      108.59 ms →      107.71 ms   (-0.81%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.51 s  →        8.75 s    (+2.80%) |      38   →      26    (-31.58%) |      323.35 s  →      227.45 s   (-29.66%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.96 ms →        4.63 ms   (-6.70%) |      38   →      26    (-31.58%) |      188.62 ms →      120.41 ms  (-36.16%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.60 ms →        4.27 ms   (-7.10%) |      38   →      26    (-31.58%) |      174.77 ms →      111.09 ms  (-36.44%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      972.78 μs →      985.10 μs   (+1.27%) |      38   →      26    (-31.58%) |       36.97 ms →       25.61 ms  (-30.71%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.74 ms →        2.40 ms  (-12.32%) |      38   →      26    (-31.58%) |      104.10 ms →       62.45 ms  (-40.01%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.58 μs →       64.66 μs   (+0.12%) |      76   →      52    (-31.58%) |        4.91 ms →        3.36 ms  (-31.49%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       99.92 μs →       94.27 μs   (-5.65%) |      38   →      26    (-31.58%) |        3.80 ms →        2.45 ms  (-35.44%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       70.27 μs →       66.35 μs   (-5.58%) |      38   →      26    (-31.58%) |        2.67 ms →        1.73 ms  (-35.39%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.40 s  →        6.64 s    (+3.85%) |      38   →      26    (-31.58%) |      243.06 s  →      172.70 s   (-28.95%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      203.13 μs →      362.23 μs  (+78.32%) |     152   →     104    (-31.58%) |       30.88 ms →       37.67 ms  (+22.01%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.58 μs →      356.70 μs  (+80.53%) |     152   →     104    (-31.58%) |       30.03 ms →       37.10 ms  (+23.52%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.22 μs →        3.90 μs   (-7.63%) |     152   →     104    (-31.58%) |      641.43 μs →      405.37 μs  (-36.80%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.60 s  →        1.66 s    (+3.84%) |     152   →     104    (-31.58%) |      243.03 s  →      172.66 s   (-28.95%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       15.25 ms →       11.95 ms  (-21.67%) |     152   →     104    (-31.58%) |        2.32 s  →        1.24 s   (-46.41%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      555.84 μs →      656.01 ns  (-99.88%) |     912   →     624    (-31.58%) |      506.93 ms →      409.35 μs  (-99.92%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.83 ms   (-0.57%) |     152   →     104    (-31.58%) |      280.35 ms →      190.74 ms  (-31.97%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.02 μs →      353.52 μs   (+1.00%) |     152   →     104    (-31.58%) |       53.20 ms →       36.77 ms  (-30.89%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      548.11 μs →      548.69 μs   (+0.10%) |     304   →     208    (-31.58%) |      166.63 ms →      114.13 ms  (-31.51%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.57 s  →        1.64 s    (+4.11%) |     152   →     104    (-31.58%) |      239.05 s  →      170.29 s   (-28.76%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       78.33 ms →       70.84 ms   (-9.56%) |     884   →     890     (+0.68%) |       69.24 s  →       63.05 s    (-8.94%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.19 ms →       45.41 ms   (-9.52%) |     884   →     890     (+0.68%) |       44.37 s  →       40.42 s    (-8.90%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        9.45 ms →        8.78 ms   (-7.11%) |     884   →     890     (+0.68%) |        8.36 s  →        7.81 s    (-6.48%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       61.10 μs →      235.91 μs (+286.09%) |     884   →     890     (+0.68%) |       54.01 ms →      209.96 ms (+288.71%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      344.65 μs →        2.00 ms (+480.87%) |     152   →     104    (-31.58%) |       52.39 ms →      208.21 ms (+297.44%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.92 ms →        6.94 ms  (-12.31%) |     884   →     890     (+0.68%) |        7.00 s  →        6.18 s   (-11.72%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       62.05 μs →       90.07 μs  (+45.17%) |     884   →     890     (+0.68%) |       54.85 ms →       80.16 ms  (+46.15%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      348.05 μs →      748.31 μs (+115.00%) |     152   →     104    (-31.58%) |       52.90 ms →       77.82 ms  (+47.11%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       11.30 ms →       10.07 ms  (-10.92%) |     884   →     890     (+0.68%) |        9.99 s  →        8.96 s   (-10.32%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        7.19 ms →        6.35 ms  (-11.58%) |     884   →     890     (+0.68%) |        6.35 s  →        5.65 s   (-10.98%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.54 ms →        1.52 ms   (-1.11%) |     884   →     890     (+0.68%) |        1.36 s  →        1.35 s    (-0.44%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       10.17 ms →        8.77 ms  (-13.69%) |     884   →     890     (+0.68%) |        8.99 s  →        7.81 s   (-13.11%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.90 ms →        1.30 ms  (-31.90%) |     884   →     890     (+0.68%) |        1.68 s  →        1.15 s   (-31.43%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.21 ms →        7.56 ms   (-7.93%) |    1.77 K →    1.78 K   (+0.68%) |       14.51 s  →       13.45 s    (-7.30%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       21.37 ms →       28.39 ms  (+32.80%) |     884   →     890     (+0.68%) |       18.90 s  →       25.26 s   (+33.71%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.52 ms                             |    1.62 K                        |        4.07 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       33.02 μs                             |    1.77 K                        |       58.50 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         2.04 ms            |                1.68 K            |                         3.42 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        74.18 ns            |                1.68 K            |                       124.32 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         2.03 ms            |                1.68 K            |                         3.41 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        65.43 ns            |                1.68 K            |                       109.67 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      930.22 μs →      832.30 μs  (-10.53%) |     884   →     890     (+0.68%) |      822.31 ms →      740.75 ms   (-9.92%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      972.80 μs →      772.42 μs  (-20.60%) |     884   →     890     (+0.68%) |      859.96 ms →      687.45 ms  (-20.06%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.32 ms                             |    3.38 K                        |       11.23 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.56 μs                             |    3.38 K                        |       45.87 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      227.66 μs                             |    3.38 K                        |      770.40 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.22 μs                             |    4.85 K                        |       49.53 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.48 ms            |                3.46 K            |                        18.96 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.74 ms            |                5.03 K            |                        18.80 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.09 ms →        5.42 ms  (-11.05%) |     884   →     890     (+0.68%) |        5.39 s  →        4.82 s   (-10.45%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.51 ms                             |     884                          |        3.99 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.44 μs                             |    1.07 K                        |       29.50 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.77 ms            |                 890              |                         3.35 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        48.30 ns            |                 890              |                        42.99 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.76 ms            |                 890              |                         3.34 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        57.55 ns            |                 890              |                        51.22 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      152.74 ms →       63.77 ms  (-58.25%) |     884   →     890     (+0.68%) |      135.02 s  →       56.75 s   (-57.97%) | 
- │ │ │ │   ├ sirius::residuals                                         |        8.70 ms →       11.06 ms  (+27.11%) |     871   →     871              |        7.58 s  →        9.63 s   (+27.11%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        8.02 ms                             |     809                          |        6.49 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.38 μs                             |     809                          |       16.49 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      413.69 μs                             |     809                          |      334.68 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       13.56 μs                             |    1.62 K                        |       21.94 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        10.73 ms            |                 824              |                         8.84 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.33 ms            |                1.65 K            |                         8.78 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.03 ms →      650.03 μs  (-37.08%) |     809   →     824     (+1.85%) |      835.80 ms →      535.63 ms  (-35.91%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       18.08 ms →       51.37 ms (+184.18%) |     160   →     209    (+30.62%) |        2.89 s  →       10.74 s  (+271.21%) | 
  │ │ │ │     ├ sddk::transform                                         |       17.16 ms                             |     168                          |        2.88 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       16.56 μs                             |     168                          |        2.78 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.14 ms                             |     168                          |      191.20 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       16.96 μs                             |     176                          |        2.98 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        34.08 ms            |                 314              |                        10.70 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        25.39 ms            |                 419              |                        10.64 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      501.28 ns →      568.13 ns  (+13.33%) |     152   →     104    (-31.58%) |       76.20 μs →       59.09 μs  (-22.46%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.49 μs →       21.06 μs   (+8.07%) |      38   →      26    (-31.58%) |      740.43 μs →      547.50 μs  (-26.06%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      611.43 μs →      590.16 μs   (-3.48%) |      38   →      26    (-31.58%) |       23.23 ms →       15.34 ms  (-33.96%) | 
+ │ │ ├ sirius::Density::generate                                       |      907.46 ms →      897.89 ms   (-1.05%) |      38   →      26    (-31.58%) |       34.48 s  →       23.35 s   (-32.30%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      531.62 ms →      523.56 ms   (-1.51%) |      38   →      26    (-31.58%) |       20.20 s  →       13.61 s   (-32.62%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.05 ms →       24.24 ms   (-3.23%) |     152   →     104    (-31.58%) |        3.81 s  →        2.52 s   (-33.79%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.37 μs →        8.51 μs   (+1.65%) |     152   →     104    (-31.58%) |        1.27 ms →      885.30 μs  (-30.45%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.32 μs →       15.26 μs   (+6.51%) |       8   →       8              |      114.60 μs →      122.06 μs   (+6.51%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       21.00 ms →       20.07 ms   (-4.42%) |     152   →     104    (-31.58%) |        3.19 s  →        2.09 s   (-34.60%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.73 ms →       29.63 ms   (-3.59%) |     152   →     104    (-31.58%) |        4.67 s  →        3.08 s   (-34.03%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.63 μs →        9.29 μs   (-3.53%) |     152   →     104    (-31.58%) |        1.46 ms →      965.76 μs  (-33.99%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (-0.06%) |     152   →     104    (-31.58%) |      220.69 ms →      150.90 ms  (-31.62%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.79 ms →       27.70 ms   (-3.81%) |     152   →     104    (-31.58%) |        4.38 s  →        2.88 s   (-34.19%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.72 ms →        3.56 ms  (-24.49%) |     152   →     104    (-31.58%) |      717.49 ms →      370.69 ms  (-48.34%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      504.66 ns →      690.69 ns  (+36.86%) |     152   →     104    (-31.58%) |       76.71 μs →       71.83 μs   (-6.36%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.57 ms →       42.73 ms   (+0.37%) |     152   →     104    (-31.58%) |        6.47 s  →        4.44 s   (-31.33%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.59%) |      38   →      26    (-31.58%) |       62.44 ms →       42.98 ms  (-31.18%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.92 ms   (+0.69%) |      38   →      26    (-31.58%) |        3.36 s  →        2.31 s   (-31.11%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.06 ms →       88.67 ms   (+0.69%) |      38   →      26    (-31.58%) |        3.35 s  →        2.31 s   (-31.10%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      282.53 ms →      279.61 ms   (-1.03%) |      38   →      26    (-31.58%) |       10.74 s  →        7.27 s   (-32.29%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      282.53 ms →      279.61 ms   (-1.03%) |      38   →      26    (-31.58%) |       10.74 s  →        7.27 s   (-32.29%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.69 ms →       24.60 ms  (-17.15%) |      38   →      26    (-31.58%) |        1.13 s  →      639.53 ms  (-43.31%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      223.47 ms →      229.20 ms   (+2.57%) |      38   →      26    (-31.58%) |        8.49 s  →        5.96 s   (-29.82%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.71 ms →       24.02 ms  (-13.33%) |      38   →      26    (-31.58%) |        1.05 s  →      624.53 ms  (-40.70%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.37 ms →       81.71 ms   (+0.42%) |      38   →      26    (-31.58%) |        3.09 s  →        2.12 s   (-31.29%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.35 ms →        9.41 ms  (+12.67%) |      38   →      26    (-31.58%) |      317.46 ms →      244.72 ms  (-22.91%) | 
+ │ │ ├ sirius::Density::mix                                            |      219.92 ms →      219.37 ms   (-0.25%) |      38   →      26    (-31.58%) |        8.36 s  →        5.70 s   (-31.75%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      969.70 μs →        1.02 ms   (+5.66%) |      38   →      26    (-31.58%) |       36.85 ms →       26.64 ms  (-27.70%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.31 ms →       10.67 ms   (+3.55%) |     500   →     334    (-33.20%) |        5.15 s  →        3.56 s   (-30.83%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.00 ms →       10.42 ms   (+4.14%) |     500   →     334    (-33.20%) |        5.00 s  →        3.48 s   (-30.44%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.00 ms →       10.42 ms   (+4.14%) |     500   →     334    (-33.20%) |        5.00 s  →        3.48 s   (-30.44%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.38 ms →        6.16 ms   (-3.35%) |      38   →      26    (-31.58%) |      242.25 ms →      160.19 ms  (-33.87%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.52 ms →        5.31 ms   (-3.92%) |      38   →      26    (-31.58%) |      209.89 ms →      137.98 ms  (-34.26%) | 
+ │ │ ├ sirius::Potential::generate                                     |      573.58 ms →      578.68 ms   (+0.89%) |      38   →      26    (-31.58%) |       21.80 s  →       15.05 s   (-30.97%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      139.31 ms →      136.67 ms   (-1.89%) |      38   →      26    (-31.58%) |        5.29 s  →        3.55 s   (-32.88%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       17.48 ms →       16.47 ms   (-5.78%) |      38   →      26    (-31.58%) |      664.17 ms →      428.16 ms  (-35.53%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.25 ms →       10.17 ms   (-0.77%) |      38   →      26    (-31.58%) |      389.58 ms →      264.50 ms  (-32.11%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.93 ms →        9.95 ms   (+0.20%) |      38   →      26    (-31.58%) |      377.28 ms →      258.65 ms  (-31.44%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.93 ms →        9.95 ms   (+0.20%) |      38   →      26    (-31.58%) |      377.26 ms →      258.63 ms  (-31.45%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      557.65 μs →      566.60 μs   (+1.60%) |      76   →      52    (-31.58%) |       42.38 ms →       29.46 ms  (-30.48%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       46.94 ms →       49.13 ms   (+4.67%) |      38   →      26    (-31.58%) |        1.78 s  →        1.28 s   (-28.38%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.94 ms →       46.75 ms   (-0.40%) |      38   →      26    (-31.58%) |        1.78 s  →        1.22 s   (-31.85%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.95 ms →        3.03 ms   (+2.89%) |      76   →      52    (-31.58%) |      224.03 ms →      157.71 ms  (-29.60%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.82 ms →        5.43 ms   (-6.68%) |      38   →      26    (-31.58%) |      221.28 ms →      141.29 ms  (-36.15%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.83 ms →        6.67 ms   (-2.38%) |      38   →      26    (-31.58%) |      259.44 ms →      173.30 ms  (-33.20%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.98 ms →       90.84 ms   (-0.15%) |      38   →      26    (-31.58%) |        3.46 s  →        2.36 s   (-31.68%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      287.09 ms →      292.93 ms   (+2.03%) |      38   →      26    (-31.58%) |       10.91 s  →        7.62 s   (-30.19%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      285.11 ms →      283.21 ms   (-0.67%) |      38   →      26    (-31.58%) |       10.83 s  →        7.36 s   (-32.04%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      285.11 ms →      283.21 ms   (-0.67%) |      38   →      26    (-31.58%) |       10.83 s  →        7.36 s   (-32.04%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.23 ms →       26.92 ms  (-16.46%) |      38   →      26    (-31.58%) |        1.22 s  →      700.02 ms  (-42.84%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      221.42 ms →      228.66 ms   (+3.27%) |      38   →      26    (-31.58%) |        8.41 s  →        5.95 s   (-29.34%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.74 ms →       23.83 ms  (-14.10%) |      38   →      26    (-31.58%) |        1.05 s  →      619.62 ms  (-41.22%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.66 ms →        5.61 ms  (-15.82%) |      38   →      26    (-31.58%) |      253.03 ms →      145.73 ms  (-42.41%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.26 ms →       10.33 ms   (+0.67%) |     266   →     182    (-31.58%) |        2.73 s  →        1.88 s   (-31.12%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.95 ms →       10.02 ms   (+0.74%) |     266   →     182    (-31.58%) |        2.65 s  →        1.82 s   (-31.07%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.95 ms →       10.02 ms   (+0.74%) |     266   →     182    (-31.58%) |        2.65 s  →        1.82 s   (-31.07%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.55 ms →       10.97 ms   (+3.94%) |     114   →      78    (-31.58%) |        1.20 s  →      855.58 ms  (-28.88%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.30 ms →       10.63 ms   (+3.20%) |     114   →      78    (-31.58%) |        1.17 s  →      829.40 ms  (-29.39%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.81 ms →        9.96 ms   (-7.82%) |      38   →      26    (-31.58%) |      410.71 ms →      259.04 ms  (-36.93%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      128.40 μs →      110.90 μs  (-13.63%) |      38   →      26    (-31.58%) |        4.88 ms →        2.88 ms  (-40.91%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      123.07 μs →      105.36 μs  (-14.39%) |      38   →      26    (-31.58%) |        4.68 ms →        2.74 ms  (-41.42%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.05 ms →        5.11 ms   (+1.20%) |       2   →       2              |       10.10 ms →       10.22 ms   (+1.20%) | 
+ │ ├ sirius::Periodic_function|inner                                   |       11.17 ms →        9.80 ms  (-12.29%) |       6   →       6              |       67.01 ms →       58.77 ms  (-12.29%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.07 ms →        9.73 ms   (-3.36%) |       6   →       6              |       60.44 ms →       58.41 ms   (-3.36%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.07 ms →        9.73 ms   (-3.36%) |       6   →       6              |       60.44 ms →       58.41 ms   (-3.36%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       11.45 ms →       10.61 ms   (-7.26%) |       3   →       3              |       34.34 ms →       31.84 ms   (-7.26%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.41 ms →       10.53 ms   (+1.15%) |       3   →       3              |       31.23 ms →       31.58 ms   (+1.15%) | 
+ ├ sirius::Periodic_function|inner                                     |       10.84 ms →        9.73 ms  (-10.22%) |       2   →       2              |       21.67 ms →       19.46 ms  (-10.22%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.07 ms →        9.71 ms   (-3.52%) |       2   →       2              |       20.13 ms →       19.42 ms   (-3.52%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.07 ms →        9.71 ms   (-3.52%) |       2   →       2              |       20.13 ms →       19.42 ms   (-3.52%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       11.33 ms →       10.62 ms   (-6.23%) |       1   →       1              |       11.33 ms →       10.62 ms   (-6.23%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.61 ms →       10.61 ms   (+0.05%) |       1   →       1              |       10.61 ms →       10.61 ms   (+0.05%) | 
+ └ sirius::finalize                                                    |      410.34 ms →      294.74 ms  (-28.17%) |       1   →       1              |      410.34 ms →      294.74 ms  (-28.17%) | 
  ====================================================================================================================================================================================================
```
