# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      245.06 s  →      225.04 s    (-8.17%) |       1   →       1              |      245.06 s  →      225.04 s    (-8.17%) | 
  ├ sirius::initialize                                                  |        2.66 s  →        2.72 s    (+2.34%) |       1   →       1              |        2.66 s  →        2.72 s    (+2.34%) | 
  ├ sirius::Simulation_context::initialize                              |        3.13 s  →        3.06 s    (-2.14%) |       1   →       1              |        3.13 s  →        3.06 s    (-2.14%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       11.58 ms →        7.85 ms  (-32.21%) |       1   →       1              |       11.58 ms →        7.85 ms  (-32.21%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      366.09 ms →      305.75 ms  (-16.48%) |       1   →       1              |      366.09 ms →      305.75 ms  (-16.48%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      171.51 ms →      141.26 ms  (-17.64%) |       2   →       2              |      343.01 ms →      282.52 ms  (-17.64%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.99 ms →       23.15 ms   (+0.69%) |       1   →       1              |       22.99 ms →       23.15 ms   (+0.69%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.28 ms →        6.32 ms   (+0.71%) |       1   →       1              |        6.28 ms →        6.32 ms   (+0.71%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.66 ms →       16.78 ms   (+0.70%) |       1   →       1              |       16.66 ms →       16.78 ms   (+0.70%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.64 ms →       16.76 ms   (+0.69%) |       1   →       1              |       16.64 ms →       16.76 ms   (+0.69%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.17 ms   (+0.04%) |       1   →       1              |        4.17 ms →        4.17 ms   (+0.04%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.28%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.28%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.73 μs →      106.98 μs   (+1.18%) |       1   →       1              |      105.73 μs →      106.98 μs   (+1.18%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.70 s    (-0.16%) |       1   →       1              |        2.71 s  →        2.70 s    (-0.16%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.94 ms →       11.04 ms   (+0.88%) |       1   →       1              |       10.94 ms →       11.04 ms   (+0.88%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.47 ms →        4.45 ms   (-0.53%) |       1   →       1              |        4.47 ms →        4.45 ms   (-0.53%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.43 ms →        6.56 ms   (+1.90%) |       1   →       1              |        6.43 ms →        6.56 ms   (+1.90%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.41 ms →        6.54 ms   (+1.91%) |       1   →       1              |        6.41 ms →        6.54 ms   (+1.91%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.92 ms →        4.03 ms   (+2.85%) |       1   →       1              |        3.92 ms →        4.03 ms   (+2.85%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.39%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.39%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.75 μs →      100.25 μs   (-0.50%) |       1   →       1              |      100.75 μs →      100.25 μs   (-0.50%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.24 ms →       62.81 ms   (-2.22%) |       2   →       2              |      128.49 ms →      125.63 ms   (-2.22%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.14 ms   (-0.38%) |       2   →       2              |       10.33 ms →       10.29 ms   (-0.38%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (+0.02%) |       1   →       1              |        4.48 ms →        4.48 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.72 ms →       21.94 ms   (+1.02%) |       2   →       2              |       43.43 ms →       43.88 ms   (+1.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.83 ms →       15.03 ms   (+1.35%) |       2   →       2              |       29.67 ms →       30.07 ms   (+1.35%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.75 ms →       19.74 ms   (-0.03%) |       4   →       4              |       79.00 ms →       78.97 ms   (-0.03%) | 
  │   ├ sddk::Gvec::init                                                |      173.80 ms →      171.83 ms   (-1.13%) |       2   →       2              |      347.60 ms →      343.66 ms   (-1.13%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.24 ms →      129.32 ms   (-1.46%) |       2   →       2              |      262.47 ms →      258.65 ms   (-1.46%) | 
  │   ├ sddk::Gvec_shells                                               |      164.92 ms →      163.53 ms   (-0.84%) |       1   →       1              |      164.92 ms →      163.53 ms   (-0.84%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.34 ms   (+1.27%) |       1   →       1              |        1.32 ms →        1.34 ms   (+1.27%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.14 ms →      299.91 ms   (+2.31%) |       2   →       2              |      586.28 ms →      599.82 ms   (+2.31%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.56 ms →       75.93 ms   (-0.81%) |       1   →       1              |       76.56 ms →       75.93 ms   (-0.81%) | 
  │ ├ sirius::K_point::K_point                                          |        2.41 μs →        2.43 μs   (+0.77%) |       4   →       4              |        9.66 μs →        9.73 μs   (+0.77%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.46 ms →       75.84 ms   (-0.81%) |       1   →       1              |       76.46 ms →       75.84 ms   (-0.81%) | 
  │   └ sirius::K_point::initialize                                     |       19.10 ms →       18.94 ms   (-0.86%) |       4   →       4              |       76.41 ms →       75.75 ms   (-0.86%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.51 ms →       14.32 ms   (-1.27%) |       4   →       4              |       58.04 ms →       57.30 ms   (-1.27%) | 
  │     │ └ sddk::Gvec::init                                            |        3.87 ms →        3.86 ms   (-0.28%) |       4   →       4              |       15.47 ms →       15.43 ms   (-0.28%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.99 μs →        9.78 μs   (+8.82%) |       4   →       4              |       35.95 μs →       39.12 μs   (+8.82%) | 
  │     └ sirius::K_point::update                                       |        3.28 ms →        3.31 ms   (+0.82%) |       4   →       4              |       13.14 ms →       13.25 ms   (+0.82%) | 
  │       └ sirius::Beta_projectors                                     |        1.79 ms →        1.80 ms   (+0.44%) |       4   →       4              |        7.15 ms →        7.18 ms   (+0.44%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      937.48 μs →      938.50 μs   (+0.11%) |       4   →       4              |        3.75 ms →        3.75 ms   (+0.11%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.29 ms →        5.46 ms   (+3.16%) |       2   →       2              |       10.59 ms →       10.92 ms   (+3.16%) | 
  ├ sirius::Potential                                                   |      158.40 ms →      159.74 ms   (+0.84%) |       1   →       1              |      158.40 ms →      159.74 ms   (+0.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.91 ms   (+1.06%) |       6   →       6              |       35.07 ms →       35.44 ms   (+1.06%) | 
  │ └ sirius::Potential::update                                         |      122.59 ms →      123.56 ms   (+0.79%) |       1   →       1              |      122.59 ms →      123.56 ms   (+0.79%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.83 ms →      122.82 ms   (+0.82%) |       1   →       1              |      121.83 ms →      122.82 ms   (+0.82%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      114.76 ms →      114.49 ms   (-0.24%) |       1   →       1              |      114.76 ms →      114.49 ms   (-0.24%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.19 ms →        7.46 ms  (+20.50%) |       1   →       1              |        6.19 ms →        7.46 ms  (+20.50%) | 
  ├ sirius::Density                                                     |      133.83 ms →      136.51 ms   (+2.00%) |       1   →       1              |      133.83 ms →      136.51 ms   (+2.00%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.17 ms →        5.30 ms   (+2.40%) |       2   →       2              |       10.35 ms →       10.60 ms   (+2.40%) | 
  │ └ sirius::Density::update                                           |      123.21 ms →      125.64 ms   (+1.97%) |       1   →       1              |      123.21 ms →      125.64 ms   (+1.97%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      122.77 ms →      125.17 ms   (+1.96%) |       1   →       1              |      122.77 ms →      125.17 ms   (+1.96%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      103.64 μs →      119.82 μs  (+15.61%) |       1   →       1              |      103.64 μs →      119.82 μs  (+15.61%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      117.30 ms →      117.96 ms   (+0.56%) |       1   →       1              |      117.30 ms →      117.96 ms   (+0.56%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.92 ms →        6.64 ms  (+35.10%) |       1   →       1              |        4.92 ms →        6.64 ms  (+35.10%) | 
  ├ sirius::Density::initial_density                                    |      176.35 ms →      175.60 ms   (-0.42%) |       1   →       1              |      176.35 ms →      175.60 ms   (-0.42%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.35 ms →      121.94 ms   (-0.33%) |       1   →       1              |      122.35 ms →      121.94 ms   (-0.33%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.17 ms →        5.51 ms   (+6.59%) |       2   →       2              |       10.33 ms →       11.01 ms   (+6.59%) | 
+ │ └ sirius::Periodic_function::integrate                              |       11.14 ms →        9.90 ms  (-11.10%) |       1   →       1              |       11.14 ms →        9.90 ms  (-11.10%) | 
  ├ sirius::Potential::generate                                         |      593.86 ms →      591.98 ms   (-0.32%) |       1   →       1              |      593.86 ms →      591.98 ms   (-0.32%) | 
  │ ├ sirius::Potential::poisson                                        |      136.19 ms →      137.57 ms   (+1.01%) |       1   →       1              |      136.19 ms →      137.57 ms   (+1.01%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.11 ms →        6.02 ms  (+17.69%) |       1   →       1              |        5.11 ms →        6.02 ms  (+17.69%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.32 ms →       10.34 ms   (+0.18%) |       1   →       1              |       10.32 ms →       10.34 ms   (+0.18%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.30 ms →       10.32 ms   (+0.18%) |       1   →       1              |       10.30 ms →       10.32 ms   (+0.18%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.30 ms →       10.32 ms   (+0.18%) |       1   →       1              |       10.30 ms →       10.32 ms   (+0.18%) | 
  │ ├ sirius::Periodic_function::add                                    |      550.74 μs →      569.48 μs   (+3.40%) |       2   →       2              |        1.10 ms →        1.14 ms   (+3.40%) | 
  │ ├ sirius::Potential::xc                                             |       55.64 ms →       53.87 ms   (-3.17%) |       1   →       1              |       55.64 ms →       53.87 ms   (-3.17%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.19 ms →       51.46 ms   (-3.27%) |       1   →       1              |       53.19 ms →       51.46 ms   (-3.27%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.77 ms →        5.81 ms   (+0.65%) |       2   →       2              |       11.55 ms →       11.62 ms   (+0.65%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.10 ms →        5.15 ms   (+0.92%) |       1   →       1              |        5.10 ms →        5.15 ms   (+0.92%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.65 ms →        5.85 ms   (+3.66%) |       1   →       1              |        5.65 ms →        5.85 ms   (+3.66%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.52 ms →       92.58 ms   (-1.00%) |       1   →       1              |       93.52 ms →       92.58 ms   (-1.00%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.43 ms →      299.59 ms   (-0.28%) |       1   →       1              |      300.43 ms →      299.59 ms   (-0.28%) | 
  ├ sirius::Hamiltonian0                                                |        8.38 ms →        8.40 ms   (+0.22%) |       1   →       1              |        8.38 ms →        8.40 ms   (+0.22%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        8.05 ms   (+0.29%) |       1   →       1              |        8.03 ms →        8.05 ms   (+0.29%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.81 ms →        4.80 ms   (-0.23%) |       1   →       1              |        4.81 ms →        4.80 ms   (-0.23%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.31 ms →        2.33 ms   (+1.07%) |       1   →       1              |        2.31 ms →        2.33 ms   (+1.07%) | 
  │ ├ sirius::Non_local_operator                                        |       63.68 μs →       62.69 μs   (-1.56%) |       2   →       2              |      127.36 μs →      125.37 μs   (-1.56%) | 
  │ ├ sirius::D_operator::initialize                                    |       96.41 μs →       95.40 μs   (-1.05%) |       1   →       1              |       96.41 μs →       95.40 μs   (-1.05%) | 
  │ └ sirius::Q_operator::initialize                                    |       71.22 μs →       69.96 μs   (-1.76%) |       1   →       1              |       71.22 μs →       69.96 μs   (-1.76%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.11 s    (+0.09%) |       1   →       1              |        3.11 s  →        3.11 s    (+0.09%) | 
  │ ├ sirius::Hamiltonian_k                                             |      372.08 μs →      367.75 μs   (-1.16%) |       4   →       4              |        1.49 ms →        1.47 ms   (-1.16%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      367.19 μs →      362.43 μs   (-1.30%) |       4   →       4              |        1.47 ms →        1.45 ms   (-1.30%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |        3.06 μs →        3.43 μs  (+12.02%) |       4   →       4              |       12.25 μs →       13.73 μs  (+12.02%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      776.62 ms →      777.32 ms   (+0.09%) |       4   →       4              |        3.11 s  →        3.11 s    (+0.09%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.47 ms →       32.21 ms   (-0.79%) |      16   →      16              |      519.52 ms →      515.42 ms   (-0.79%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.52 ms →       14.56 ms   (+0.26%) |       4   →       4              |       58.07 ms →       58.22 ms   (+0.26%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.33 ms →        5.34 ms   (+0.09%) |       4   →       4              |       21.33 ms →       21.34 ms   (+0.09%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      346.81 ms →      355.65 ms   (+2.55%) |       4   →       4              |        1.39 s  →        1.42 s    (+2.55%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      249.76 ms →      258.36 ms   (+3.44%) |       4   →       4              |      999.03 ms →        1.03 s    (+3.44%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       59.45 ms →       63.40 ms   (+6.65%) |       4   →       4              |      237.80 ms →      253.62 ms   (+6.65%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.47 ms →       16.32 ms   (-0.93%) |       4   →       4              |       65.90 ms →       65.28 ms   (-0.93%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.47 ms →       16.32 ms   (-0.93%) |       4   →       4              |       65.89 ms →       65.27 ms   (-0.93%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       36.49 ms →       40.57 ms  (+11.18%) |       4   →       4              |      145.96 ms →      162.29 ms  (+11.18%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.29 ms →       16.03 ms   (-1.58%) |       4   →       4              |       65.16 ms →       64.13 ms   (-1.58%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.29 ms →       16.03 ms   (-1.57%) |       4   →       4              |       65.14 ms →       64.12 ms   (-1.57%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       50.13 ms →       53.66 ms   (+7.05%) |       4   →       4              |      200.51 ms →      214.64 ms   (+7.05%) | 
- │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       32.12 ms →       35.62 ms  (+10.89%) |       4   →       4              |      128.48 ms →      142.47 ms  (+10.89%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.94 ms   (+0.30%) |       4   →       4              |        7.75 ms →        7.78 ms   (+0.30%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.91 ms →       40.99 ms   (+0.20%) |       4   →       4              |      163.63 ms →      163.95 ms   (+0.20%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.83 ms →        7.85 ms   (+0.33%) |       4   →       4              |       31.30 ms →       31.41 ms   (+0.33%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.08 ms →       27.16 ms   (+0.27%) |       8   →       8              |      216.68 ms →      217.27 ms   (+0.27%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.19 ms →       15.09 ms   (-0.65%) |       8   →       8              |      121.52 ms →      120.73 ms   (-0.65%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.15 ms →       15.05 ms   (-0.65%) |       8   →       8              |      121.16 ms →      120.38 ms   (-0.65%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       25.63 ns →       25.88 ns   (+0.98%) |       8   →       8              |      205.00 ns →      207.00 ns   (+0.98%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.97 ms →       14.87 ms   (-0.66%) |       8   →       8              |      119.74 ms →      118.94 ms   (-0.66%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.88 ns →       25.37 ns  (+21.56%) |       8   →       8              |      167.00 ns →      203.00 ns  (+21.56%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      128.06 ms →      122.27 ms   (-4.52%) |       4   →       4              |      512.24 ms →      489.07 ms   (-4.52%) | 
  │ │ └ sddk::wf_trans                                                  |       23.65 ms →       23.53 ms   (-0.50%) |       4   →       4              |       94.58 ms →       94.11 ms   (-0.50%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.52 ms →       23.38 ms   (-0.62%) |       4   →       4              |       94.10 ms →       93.51 ms   (-0.62%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      430.75 ns →      393.50 ns   (-8.65%) |       4   →       4              |        1.72 μs →        1.57 μs   (-8.65%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      234.20 s  →      214.20 s    (-8.54%) |       1   →       1              |      234.20 s  →      214.20 s    (-8.54%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.84 ms   (+0.03%) |      19   →      19              |      111.00 ms →      111.04 ms   (+0.03%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.99 s  →        8.12 s    (-9.63%) |      26   →      26              |      233.63 s  →      211.13 s    (-9.63%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.44 ms →        4.51 ms   (+1.73%) |      26   →      26              |      115.31 ms →      117.30 ms   (+1.73%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.08 ms →        4.15 ms   (+1.86%) |      26   →      26              |      106.02 ms →      107.99 ms   (+1.86%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      973.25 μs →      968.26 μs   (-0.51%) |      26   →      26              |       25.30 ms →       25.17 ms   (-0.51%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.21 ms →        2.30 ms   (+3.65%) |      26   →      26              |       57.57 ms →       59.67 ms   (+3.65%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.32 μs →       64.76 μs   (+0.69%) |      52   →      52              |        3.34 ms →        3.37 ms   (+0.69%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.46 μs →       93.75 μs   (+0.31%) |      26   →      26              |        2.43 ms →        2.44 ms   (+0.31%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.42 μs →       66.58 μs   (+0.25%) |      26   →      26              |        1.73 ms →        1.73 ms   (+0.25%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.89 s  →        6.02 s   (-12.58%) |      26   →      26              |      179.11 s  →      156.57 s   (-12.58%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      333.35 μs →      323.37 μs   (-3.00%) |     104   →     104              |       34.67 ms →       33.63 ms   (-3.00%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      327.94 μs →      317.92 μs   (-3.05%) |     104   →     104              |       34.11 ms →       33.06 ms   (-3.05%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.83 μs →        3.90 μs   (+1.72%) |     104   →     104              |      398.49 μs →      405.35 μs   (+1.72%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.72 s  →        1.51 s   (-12.59%) |     104   →     104              |      179.07 s  →      156.53 s   (-12.59%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.04 ms →       11.88 ms   (-1.33%) |     104   →     104              |        1.25 s  →        1.24 s    (-1.33%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      660.64 ns →      669.39 ns   (+1.32%) |     624   →     624              |      412.24 μs →      417.70 μs   (+1.32%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (-0.37%) |     104   →     104              |      190.76 ms →      190.05 ms   (-0.37%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.28 μs →      352.89 μs   (-0.67%) |     104   →     104              |       36.95 ms →       36.70 ms   (-0.67%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.54 μs →      549.20 μs   (-0.24%) |     208   →     208              |      114.51 ms →      114.23 ms   (-0.24%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.70 s  →        1.48 s   (-12.75%) |     104   →     104              |      176.69 s  →      154.17 s   (-12.75%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       67.90 ms →       71.29 ms   (+4.98%) |     914   →     914              |       62.07 s  →       65.16 s    (+4.98%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.76 ms →       45.57 ms   (+6.58%) |     914   →     914              |       39.08 s  →       41.65 s    (+6.58%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        7.84 ms →        8.93 ms  (+13.93%) |     914   →     914              |        7.17 s  →        8.16 s   (+13.93%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      230.27 μs →      234.91 μs   (+2.01%) |     914   →     914              |      210.47 ms →      214.70 ms   (+2.01%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.01 ms →        2.05 ms   (+2.05%) |     104   →     104              |      208.70 ms →      212.98 ms   (+2.05%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.05 ms →        6.94 ms  (+14.68%) |     914   →     914              |        5.53 s  →        6.35 s   (+14.68%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       89.19 μs →       90.54 μs   (+1.52%) |     914   →     914              |       81.52 ms →       82.76 ms   (+1.52%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      760.95 μs →      772.48 μs   (+1.51%) |     104   →     104              |       79.14 ms →       80.34 ms   (+1.51%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.02 ms →       10.11 ms  (+12.13%) |     914   →     914              |        8.24 s  →        9.24 s   (+12.13%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.40 ms →        6.42 ms  (+18.78%) |     914   →     914              |        4.94 s  →        5.87 s   (+18.78%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.53 ms   (+0.84%) |     914   →     914              |        1.39 s  →        1.40 s    (+0.84%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.78 ms →        8.95 ms   (+1.95%) |     914   →     914              |        8.02 s  →        8.18 s    (+1.95%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.43 ms →        1.53 ms   (+6.92%) |     914   →     914              |        1.31 s  →        1.40 s    (+6.92%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.42 ms →        7.61 ms   (+2.62%) |    1.83 K →    1.83 K            |       13.56 s  →       13.91 s    (+2.62%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.01 ms →       28.25 ms   (+0.87%) |     914   →     914              |       25.60 s  →       25.82 s    (+0.87%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.05 ms →        2.07 ms   (+0.77%) |    1.72 K →    1.72 K            |        3.54 s  →        3.57 s    (+0.77%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       70.00 ns →       51.96 ns  (-25.77%) |    1.72 K →    1.72 K            |      120.68 μs →       89.58 μs  (-25.77%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.04 ms →        2.06 ms   (+0.71%) |    1.72 K →    1.72 K            |        3.53 s  →        3.55 s    (+0.71%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       68.78 ns →       72.46 ns   (+5.35%) |    1.72 K →    1.72 K            |      118.57 μs →      124.92 μs   (+5.35%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      810.64 μs →      847.39 μs   (+4.53%) |     914   →     914              |      740.93 ms →      774.51 ms   (+4.53%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      811.49 μs →      840.67 μs   (+3.60%) |     914   →     914              |      741.71 ms →      768.37 ms   (+3.60%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.38 ms →        5.42 ms   (+0.66%) |    3.55 K →    3.55 K            |       19.12 s  →       19.24 s    (+0.66%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.66 ms →        3.69 ms   (+0.67%) |    5.17 K →    5.17 K            |       18.95 s  →       19.08 s    (+0.67%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.49 ms →        5.34 ms   (-2.79%) |     914   →     914              |        5.02 s  →        4.88 s    (-2.79%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.79 ms →        3.70 ms   (-2.44%) |     914   →     914              |        3.46 s  →        3.38 s    (-2.44%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       43.75 ns →       44.60 ns   (+1.94%) |     914   →     914              |       39.99 μs →       40.76 μs   (+1.94%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.77 ms →        3.68 ms   (-2.42%) |     914   →     914              |        3.45 s  →        3.37 s    (-2.42%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       56.14 ns →       55.83 ns   (-0.56%) |     914   →     914              |       51.32 μs →       51.03 μs   (-0.56%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       69.63 ms →       39.72 ms  (-42.96%) |     914   →     914              |       63.64 s  →       36.30 s   (-42.96%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.70 ms →       10.69 ms   (-0.02%) |     894   →     890     (-0.45%) |        9.56 s  →        9.52 s    (-0.46%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.31 ms →       10.30 ms   (-0.10%) |     849   →     845     (-0.47%) |        8.75 s  →        8.70 s    (-0.57%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.12 ms →        5.12 ms   (-0.10%) |    1.70 K →    1.69 K   (-0.47%) |        8.70 s  →        8.65 s    (-0.57%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      641.37 μs →      671.45 μs   (+4.69%) |     849   →     845     (-0.47%) |      544.52 ms →      567.37 ms   (+4.20%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.53 ms →       39.69 ms  (-22.99%) |     209   →     314    (+50.24%) |       10.77 s  →       12.46 s   (+15.71%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.19 ms →       23.66 ms  (-30.80%) |     314   →     524    (+66.88%) |       10.74 s  →       12.40 s   (+15.48%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.49 ms →       16.78 ms  (-34.17%) |     419   →     734    (+75.18%) |       10.68 s  →       12.32 s   (+15.33%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      588.85 ns →      569.34 ns   (-3.31%) |     104   →     104              |       61.24 μs →       59.21 μs   (-3.31%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.20 μs →       22.03 μs   (+3.94%) |      26   →      26              |      551.10 μs →      572.82 μs   (+3.94%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      595.59 μs →      601.88 μs   (+1.06%) |      26   →      26              |       15.49 ms →       15.65 ms   (+1.06%) | 
  │ │ ├ sirius::Density::generate                                       |      892.74 ms →      897.68 ms   (+0.55%) |      26   →      26              |       23.21 s  →       23.34 s    (+0.55%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      518.47 ms →      529.09 ms   (+2.05%) |      26   →      26              |       13.48 s  →       13.76 s    (+2.05%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       22.07 ms →       25.17 ms  (+14.05%) |     104   →     104              |        2.29 s  →        2.62 s   (+14.05%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.42 μs →        8.77 μs   (+4.16%) |     104   →     104              |      875.99 μs →      912.46 μs   (+4.16%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.17 μs →       15.75 μs   (+3.88%) |       8   →       8              |      121.33 μs →      126.03 μs   (+3.88%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       17.93 ms →       21.06 ms  (+17.44%) |     104   →     104              |        1.86 s  →        2.19 s   (+17.44%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.21 ms →       30.16 ms   (-0.16%) |     104   →     104              |        3.14 s  →        3.14 s    (-0.16%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.28 μs →        9.59 μs   (+3.42%) |     104   →     104              |      964.73 μs →      997.77 μs   (+3.42%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.19%) |     104   →     104              |      151.30 ms →      151.59 ms   (+0.19%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.27 ms →       28.23 ms   (-0.17%) |     104   →     104              |        2.94 s  →        2.94 s    (-0.17%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.14 ms →        4.10 ms   (-1.06%) |     104   →     104              |      430.86 ms →      426.30 ms   (-1.06%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      613.78 ns →      599.06 ns   (-2.40%) |     104   →     104              |       63.83 μs →       62.30 μs   (-2.40%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.86 ms →       42.54 ms   (-0.75%) |     104   →     104              |        4.46 s  →        4.42 s    (-0.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.74%) |      26   →      26              |       42.95 ms →       42.63 ms   (-0.74%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.86 ms →       88.85 ms   (-0.01%) |      26   →      26              |        2.31 s  →        2.31 s    (-0.01%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.63 ms →       88.62 ms   (-0.01%) |      26   →      26              |        2.30 s  →        2.30 s    (-0.01%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.63 ms →      275.02 ms   (-2.00%) |      26   →      26              |        7.30 s  →        7.15 s    (-2.00%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.63 ms →      275.02 ms   (-2.00%) |      26   →      26              |        7.30 s  →        7.15 s    (-2.00%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.53 ms →       25.36 ms   (+3.39%) |      26   →      26              |      637.75 ms →      659.39 ms   (+3.39%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.55 ms →      223.96 ms   (-2.86%) |      26   →      26              |        5.99 s  →        5.82 s    (-2.86%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.79 ms →       23.88 ms   (+0.40%) |      26   →      26              |      618.46 ms →      620.95 ms   (+0.40%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.46 ms →       80.89 ms   (-0.70%) |      26   →      26              |        2.12 s  →        2.10 s    (-0.70%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.58 ms →        9.08 ms   (+5.82%) |      26   →      26              |      223.18 ms →      236.17 ms   (+5.82%) | 
  │ │ ├ sirius::Density::mix                                            |      218.62 ms →      214.83 ms   (-1.73%) |      26   →      26              |        5.68 s  →        5.59 s    (-1.73%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      960.78 μs →      984.66 μs   (+2.48%) |      26   →      26              |       24.98 ms →       25.60 ms   (+2.48%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.69 ms →       10.32 ms   (-3.52%) |     334   →     334              |        3.57 s  →        3.45 s    (-3.52%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.43 ms →        9.97 ms   (-4.44%) |     334   →     334              |        3.48 s  →        3.33 s    (-4.44%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.43 ms →        9.97 ms   (-4.44%) |     334   →     334              |        3.48 s  →        3.33 s    (-4.44%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.21 ms →        6.44 ms   (+3.71%) |      26   →      26              |      161.46 ms →      167.45 ms   (+3.71%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.38 ms →        5.62 ms   (+4.45%) |      26   →      26              |      139.88 ms →      146.11 ms   (+4.45%) | 
  │ │ ├ sirius::Potential::generate                                     |      577.61 ms →      579.99 ms   (+0.41%) |      26   →      26              |       15.02 s  →       15.08 s    (+0.41%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.64 ms →      137.73 ms   (+0.80%) |      26   →      26              |        3.55 s  →        3.58 s    (+0.80%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.95 ms →        5.94 ms  (+20.17%) |      26   →      26              |      128.61 ms →      154.56 ms  (+20.17%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.90 ms →       10.34 ms   (-5.06%) |      26   →      26              |      283.27 ms →      268.95 ms   (-5.06%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.25 ms →       10.13 ms   (-1.09%) |      26   →      26              |      266.40 ms →      263.50 ms   (-1.09%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.25 ms →       10.13 ms   (-1.09%) |      26   →      26              |      266.38 ms →      263.48 ms   (-1.09%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      549.44 μs →      555.82 μs   (+1.16%) |      52   →      52              |       28.57 ms →       28.90 ms   (+1.16%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.74 ms →       49.12 ms   (+0.78%) |      26   →      26              |        1.27 s  →        1.28 s    (+0.78%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.40 ms →       46.80 ms   (+0.87%) |      26   →      26              |        1.21 s  →        1.22 s    (+0.87%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.04 ms   (-0.16%) |      52   →      52              |      158.12 ms →      157.86 ms   (-0.16%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.06 ms →        5.36 ms   (+5.87%) |      26   →      26              |      131.65 ms →      139.38 ms   (+5.87%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.37 ms →        6.71 ms   (+5.21%) |      26   →      26              |      165.71 ms →      174.35 ms   (+5.21%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       90.90 ms   (-0.08%) |      26   →      26              |        2.37 s  →        2.36 s    (-0.08%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.52 ms →      293.15 ms   (+0.22%) |      26   →      26              |        7.61 s  →        7.62 s    (+0.22%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      282.25 ms →      280.69 ms   (-0.55%) |      26   →      26              |        7.34 s  →        7.30 s    (-0.55%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      282.25 ms →      280.69 ms   (-0.55%) |      26   →      26              |        7.34 s  →        7.30 s    (-0.55%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       26.87 ms →       28.12 ms   (+4.64%) |      26   →      26              |      698.63 ms →      731.03 ms   (+4.64%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.71 ms →      224.95 ms   (-1.21%) |      26   →      26              |        5.92 s  →        5.85 s    (-1.21%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.87 ms →       23.80 ms   (-0.29%) |      26   →      26              |      620.62 ms →      618.80 ms   (-0.29%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.44 ms →        5.97 ms   (+9.57%) |      26   →      26              |      141.56 ms →      155.11 ms   (+9.57%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.24 ms →       10.29 ms   (+0.46%) |     182   →     182              |        1.86 s  →        1.87 s    (+0.46%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.92 ms →        9.94 ms   (+0.25%) |     182   →     182              |        1.81 s  →        1.81 s    (+0.25%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.92 ms →        9.94 ms   (+0.25%) |     182   →     182              |        1.81 s  →        1.81 s    (+0.25%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.06 ms →       10.63 ms   (-3.91%) |      78   →      78              |      863.04 ms →      829.29 ms   (-3.91%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.71 ms →       10.30 ms   (-3.84%) |      78   →      78              |      835.38 ms →      803.28 ms   (-3.84%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms →        9.98 ms   (+0.29%) |      26   →      26              |      258.81 ms →      259.57 ms   (+0.29%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      141.13 μs →      228.93 μs  (+62.21%) |      26   →      26              |        3.67 ms →        5.95 ms  (+62.21%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      136.11 μs →      223.55 μs  (+64.24%) |      26   →      26              |        3.54 ms →        5.81 ms  (+64.24%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.13 ms →        5.43 ms   (+5.82%) |       2   →       2              |       10.26 ms →       10.85 ms   (+5.82%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.13 ms →       10.23 ms   (+0.95%) |       6   →       6              |       60.79 ms →       61.37 ms   (+0.95%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.11 ms →       10.06 ms   (-0.49%) |       6   →       6              |       60.63 ms →       60.34 ms   (-0.49%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.11 ms →       10.06 ms   (-0.49%) |       6   →       6              |       60.63 ms →       60.34 ms   (-0.49%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.90 ms →       10.76 ms   (-1.28%) |       3   →       3              |       32.70 ms →       32.28 ms   (-1.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.89 ms →       10.38 ms   (-4.63%) |       3   →       3              |       32.66 ms →       31.15 ms   (-4.63%) | 
  ├ sirius::Periodic_function|inner                                     |        9.98 ms →       10.02 ms   (+0.39%) |       2   →       2              |       19.96 ms →       20.03 ms   (+0.39%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.97 ms →       10.01 ms   (+0.39%) |       2   →       2              |       19.94 ms →       20.02 ms   (+0.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.97 ms →       10.01 ms   (+0.39%) |       2   →       2              |       19.94 ms →       20.02 ms   (+0.39%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.86 ms →       10.41 ms   (-4.12%) |       1   →       1              |       10.86 ms →       10.41 ms   (-4.12%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.85 ms →       10.40 ms   (-4.13%) |       1   →       1              |       10.85 ms →       10.40 ms   (-4.13%) | 
  └ sirius::finalize                                                    |      271.36 ms →      277.55 ms   (+2.28%) |       1   →       1              |      271.36 ms →      277.55 ms   (+2.28%) | 
  ====================================================================================================================================================================================================
```
