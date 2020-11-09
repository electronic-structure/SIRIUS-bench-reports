# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs 4f6bf1684449bb549717c67734c215f779f51100
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      113.77 s  →      131.73 s   (+15.78%) |       1   →       1              |      113.77 s  →      131.73 s   (+15.78%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.73 s    (+1.18%) |       1   →       1              |        2.70 s  →        2.73 s    (+1.18%) | 
  ├ sirius::Simulation_context::initialize                              |        2.20 s  →        2.18 s    (-1.03%) |       1   →       1              |        2.20 s  →        2.18 s    (-1.03%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      105.69 ms →       53.09 ms  (-49.77%) |       1   →       1              |      105.69 ms →       53.09 ms  (-49.77%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      111.21 ms →      143.23 ms  (+28.79%) |       1   →       1              |      111.21 ms →      143.23 ms  (+28.79%) | 
- │ │ ├ sirius::Atom_type::init                                         |       85.24 ms →      116.61 ms  (+36.81%) |       1   →       1              |       85.24 ms →      116.61 ms  (+36.81%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.92 ms →       26.55 ms   (+2.46%) |       1   →       1              |       25.92 ms →       26.55 ms   (+2.46%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.45 ms →       10.53 ms   (+0.83%) |       1   →       1              |       10.45 ms →       10.53 ms   (+0.83%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.44 ms →       15.99 ms   (+3.57%) |       1   →       1              |       15.44 ms →       15.99 ms   (+3.57%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.14 ms →       15.68 ms   (+3.60%) |       1   →       1              |       15.14 ms →       15.68 ms   (+3.60%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.91 ms →       15.45 ms   (+3.62%) |       1   →       1              |       14.91 ms →       15.45 ms   (+3.62%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      217.46 μs →      223.10 μs   (+2.59%) |       1   →       1              |      217.46 μs →      223.10 μs   (+2.59%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.54 μs →        2.81 μs  (+10.93%) |       1   →       1              |        2.54 μs →        2.81 μs  (+10.93%) | 
  │ └ sirius::Simulation_context::update                                |        1.93 s  →        1.93 s    (-0.20%) |       1   →       1              |        1.93 s  →        1.93 s    (-0.20%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.85 ms →       12.96 ms   (+0.86%) |       1   →       1              |       12.85 ms →       12.96 ms   (+0.86%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.34 ms →        8.52 ms   (+2.13%) |       1   →       1              |        8.34 ms →        8.52 ms   (+2.13%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.49 ms →        4.42 ms   (-1.51%) |       1   →       1              |        4.49 ms →        4.42 ms   (-1.51%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.19 ms →        4.11 ms   (-1.94%) |       1   →       1              |        4.19 ms →        4.11 ms   (-1.94%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.97 ms →        3.90 ms   (-1.78%) |       1   →       1              |        3.97 ms →        3.90 ms   (-1.78%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      215.27 μs →      204.43 μs   (-5.04%) |       1   →       1              |      215.27 μs →      204.43 μs   (-5.04%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.25 μs →        1.30 μs   (+4.57%) |       1   →       1              |        1.25 μs →        1.30 μs   (+4.57%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.30 ms →       15.34 ms   (+0.26%) |       2   →       2              |       30.60 ms →       30.68 ms   (+0.26%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.09 ms   (-0.03%) |       2   →       2              |        2.18 ms →        2.18 ms   (-0.03%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      955.27 μs →      950.09 μs   (-0.54%) |       1   →       1              |      955.27 μs →      950.09 μs   (-0.54%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.16 ms →        5.10 ms   (-1.25%) |       2   →       2              |       10.32 ms →       10.19 ms   (-1.25%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.64 ms   (-0.11%) |       2   →       2              |        7.28 ms →        7.27 ms   (-0.11%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.10 ms →       15.81 ms   (+4.66%) |       4   →       4              |       60.41 ms →       63.23 ms   (+4.66%) | 
  │   ├ sddk::Gvec::init                                                |      159.33 ms →      157.74 ms   (-1.00%) |       2   →       2              |      318.65 ms →      315.47 ms   (-1.00%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      126.91 ms →      125.14 ms   (-1.40%) |       2   →       2              |      253.83 ms →      250.28 ms   (-1.40%) | 
  │   ├ sddk::Gvec_shells                                               |      140.33 ms →      137.58 ms   (-1.96%) |       1   →       1              |      140.33 ms →      137.58 ms   (-1.96%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.02 ms →        1.03 ms   (+0.46%) |       1   →       1              |        1.02 ms →        1.03 ms   (+0.46%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      219.26 ms →      219.87 ms   (+0.28%) |       1   →       1              |      219.26 ms →      219.87 ms   (+0.28%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.73 ms →       26.13 ms   (+1.58%) |       1   →       1              |       25.73 ms →       26.13 ms   (+1.58%) | 
  │ ├ sirius::K_point::K_point                                          |        2.06 μs →        1.88 μs   (-8.59%) |       2   →       2              |        4.11 μs →        3.76 μs   (-8.59%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.69 ms →       26.10 ms   (+1.58%) |       1   →       1              |       25.69 ms →       26.10 ms   (+1.58%) | 
  │   └ sirius::K_point::initialize                                     |       25.63 ms →       26.03 ms   (+1.55%) |       1   →       1              |       25.63 ms →       26.03 ms   (+1.55%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.21 ms →       19.43 ms   (+1.10%) |       1   →       1              |       19.21 ms →       19.43 ms   (+1.10%) | 
  │     │ └ sddk::Gvec::init                                            |        4.92 ms →        4.95 ms   (+0.63%) |       1   →       1              |        4.92 ms →        4.95 ms   (+0.63%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |       11.03 μs →       12.15 μs  (+10.22%) |       1   →       1              |       11.03 μs →       12.15 μs  (+10.22%) | 
  │     └ sirius::K_point::update                                       |        4.10 ms →        4.19 ms   (+2.18%) |       1   →       1              |        4.10 ms →        4.19 ms   (+2.18%) | 
  │       └ sirius::Beta_projectors                                     |        1.71 ms →        1.72 ms   (+0.64%) |       1   →       1              |        1.71 ms →        1.72 ms   (+0.64%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      887.12 μs →      904.72 μs   (+1.98%) |       1   →       1              |      887.12 μs →      904.72 μs   (+1.98%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.44 ms →        1.47 ms   (+1.87%) |       2   →       2              |        2.88 ms →        2.93 ms   (+1.87%) | 
  ├ sirius::Potential                                                   |       97.27 ms →       94.54 ms   (-2.80%) |       1   →       1              |       97.27 ms →       94.54 ms   (-2.80%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.41 ms →        2.47 ms   (+2.56%) |       6   →       6              |       14.46 ms →       14.83 ms   (+2.56%) | 
  │ └ sirius::Potential::update                                         |       82.46 ms →       79.37 ms   (-3.75%) |       1   →       1              |       82.46 ms →       79.37 ms   (-3.75%) | 
  │   └ sirius::Potential::generate_local_potential                     |       82.30 ms →       79.20 ms   (-3.77%) |       1   →       1              |       82.30 ms →       79.20 ms   (-3.77%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.39 ms →       51.84 ms   (-1.05%) |       1   →       1              |       52.39 ms →       51.84 ms   (-1.05%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       21.18 ms →       18.61 ms  (-12.13%) |       1   →       1              |       21.18 ms →       18.61 ms  (-12.13%) | 
  ├ sirius::Density                                                     |       75.70 ms →       75.63 ms   (-0.09%) |       1   →       1              |       75.70 ms →       75.63 ms   (-0.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.80 ms →        4.88 ms   (+1.63%) |       2   →       2              |        9.60 ms →        9.75 ms   (+1.63%) | 
  │ └ sirius::Density::update                                           |       65.99 ms →       65.77 ms   (-0.34%) |       1   →       1              |       65.99 ms →       65.77 ms   (-0.34%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.83 ms →       65.60 ms   (-0.35%) |       1   →       1              |       65.83 ms →       65.60 ms   (-0.35%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |        3.15 ms →        3.54 ms  (+12.34%) |       1   →       1              |        3.15 ms →        3.54 ms  (+12.34%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.98 ms →       53.20 ms   (+0.42%) |       1   →       1              |       52.98 ms →       53.20 ms   (+0.42%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.48 ms →        7.51 ms  (-11.43%) |       1   →       1              |        8.48 ms →        7.51 ms  (-11.43%) | 
  ├ sirius::Density::initial_density                                    |       78.86 ms →       79.97 ms   (+1.42%) |       1   →       1              |       78.86 ms →       79.97 ms   (+1.42%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.19 ms →       53.46 ms   (+0.51%) |       1   →       1              |       53.19 ms →       53.46 ms   (+0.51%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.80 ms →        5.38 ms  (+12.03%) |       2   →       2              |        9.61 ms →       10.76 ms  (+12.03%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.46 ms →        4.14 ms   (-7.17%) |       1   →       1              |        4.46 ms →        4.14 ms   (-7.17%) | 
  ├ sirius::Potential::generate                                         |      187.21 ms →      188.79 ms   (+0.84%) |       1   →       1              |      187.21 ms →      188.79 ms   (+0.84%) | 
  │ ├ sirius::Potential::poisson                                        |       64.06 ms →       64.47 ms   (+0.63%) |       1   →       1              |       64.06 ms →       64.47 ms   (+0.63%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.05 ms →        9.41 ms  (+16.96%) |       1   →       1              |        8.05 ms →        9.41 ms  (+16.96%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.19 ms →        4.24 ms   (+1.19%) |       1   →       1              |        4.19 ms →        4.24 ms   (+1.19%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.10 ms →        4.08 ms   (-0.46%) |       1   →       1              |        4.10 ms →        4.08 ms   (-0.46%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.10 ms →        4.08 ms   (-0.46%) |       1   →       1              |        4.10 ms →        4.08 ms   (-0.46%) | 
  │ ├ sirius::Periodic_function::add                                    |      224.82 μs →      244.29 μs   (+8.66%) |       2   →       2              |      449.64 μs →      488.57 μs   (+8.66%) | 
  │ ├ sirius::Potential::xc                                             |       96.77 ms →       97.87 ms   (+1.13%) |       1   →       1              |       96.77 ms →       97.87 ms   (+1.13%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       95.75 ms →       96.78 ms   (+1.07%) |       1   →       1              |       95.75 ms →       96.78 ms   (+1.07%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.98 ms →        1.99 ms   (+0.90%) |       5   →       5              |        9.89 ms →        9.97 ms   (+0.90%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.54 ms →        2.65 ms   (+4.37%) |       9   →       9              |       22.83 ms →       23.83 ms   (+4.37%) | 
  │ │   ├ sirius::gradient                                              |        7.47 ms →        7.64 ms   (+2.38%) |       1   →       1              |        7.47 ms →        7.64 ms   (+2.38%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.40 ms →        2.46 ms   (+2.53%) |       3   →       3              |        7.19 ms →        7.37 ms   (+2.53%) | 
  │ │   ├ sirius::dot                                                   |        2.80 ms →        2.79 ms   (-0.26%) |       1   →       1              |        2.80 ms →        2.79 ms   (-0.26%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.58 ms →        2.57 ms   (-0.68%) |       1   →       1              |        2.58 ms →        2.57 ms   (-0.68%) | 
  │ │   └ sirius::divergence                                            |       19.64 ms →       19.83 ms   (+0.99%) |       1   →       1              |       19.64 ms →       19.83 ms   (+0.99%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.41 ms →        2.42 ms   (+0.25%) |       1   →       1              |        2.41 ms →        2.42 ms   (+0.25%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.16 ms →        3.18 ms   (+0.59%) |       1   →       1              |        3.16 ms →        3.18 ms   (+0.59%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.23 ms →       22.22 ms   (-0.03%) |       1   →       1              |       22.23 ms →       22.22 ms   (-0.03%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      289.00 ns →      208.00 ns  (-28.03%) |       1   →       1              |      289.00 ns →      208.00 ns  (-28.03%) | 
- ├ sirius::Hamiltonian0                                                |       13.81 ms →       16.15 ms  (+16.93%) |       1   →       1              |       13.81 ms →       16.15 ms  (+16.93%) | 
- │ ├ sirius::Local_operator                                            |       13.49 ms →       15.81 ms  (+17.20%) |       1   →       1              |       13.49 ms →       15.81 ms  (+17.20%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.20 ms →        7.12 ms   (-1.13%) |       1   →       1              |        7.20 ms →        7.12 ms   (-1.13%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.85 ms →        7.25 ms  (+49.46%) |       1   →       1              |        4.85 ms →        7.25 ms  (+49.46%) | 
  │ ├ sirius::Non_local_operator                                        |       61.76 μs →       60.90 μs   (-1.39%) |       2   →       2              |      123.53 μs →      121.81 μs   (-1.39%) | 
  │ ├ sirius::D_operator::initialize                                    |       76.95 μs →       78.58 μs   (+2.11%) |       1   →       1              |       76.95 μs →       78.58 μs   (+2.11%) | 
- │ └ sirius::Q_operator::initialize                                    |       67.40 μs →       82.84 μs  (+22.91%) |       1   →       1              |       67.40 μs →       82.84 μs  (+22.91%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.45 s  →        2.48 s    (+1.07%) |       1   →       1              |        2.45 s  →        2.48 s    (+1.07%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.39 ms   (-0.18%) |       1   →       1              |        8.41 ms →        8.39 ms   (-0.18%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      236.97 μs →      235.74 μs   (-0.52%) |       1   →       1              |      236.97 μs →      235.74 μs   (-0.52%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.17 ms →        8.15 ms   (-0.17%) |       1   →       1              |        8.17 ms →        8.15 ms   (-0.17%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.44 s  →        2.47 s    (+1.07%) |       1   →       1              |        2.44 s  →        2.47 s    (+1.07%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       88.14 ms →       89.60 ms   (+1.66%) |       4   →       4              |      352.54 ms →      358.38 ms   (+1.66%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.13 ms →       25.25 ms   (+0.48%) |       1   →       1              |       25.13 ms →       25.25 ms   (+0.48%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.35 ms →       14.39 ms   (+0.30%) |       1   →       1              |       14.35 ms →       14.39 ms   (+0.30%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.20 s  →        1.20 s    (-0.17%) |       1   →       1              |        1.20 s  →        1.20 s    (-0.17%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      978.95 ms →      976.83 ms   (-0.22%) |       1   →       1              |      978.95 ms →      976.83 ms   (-0.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      312.50 ms →      308.77 ms   (-1.19%) |       1   →       1              |      312.50 ms →      308.77 ms   (-1.19%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      176.86 ms →      180.97 ms   (+2.32%) |       1   →       1              |      176.86 ms →      180.97 ms   (+2.32%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      176.86 ms →      180.96 ms   (+2.32%) |       1   →       1              |      176.86 ms →      180.96 ms   (+2.32%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      117.05 ms →      109.34 ms   (-6.59%) |       1   →       1              |      117.05 ms →      109.34 ms   (-6.59%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      175.46 ms →      177.56 ms   (+1.20%) |       1   →       1              |      175.46 ms →      177.56 ms   (+1.20%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      175.45 ms →      177.55 ms   (+1.20%) |       1   →       1              |      175.45 ms →      177.55 ms   (+1.20%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      158.96 ms →      159.91 ms   (+0.60%) |       1   →       1              |      158.96 ms →      159.91 ms   (+0.60%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      108.30 ms →      109.30 ms   (+0.92%) |       1   →       1              |      108.30 ms →      109.30 ms   (+0.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.76 ms →        3.75 ms   (-0.14%) |       1   →       1              |        3.76 ms →        3.75 ms   (-0.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.06 ms →       89.31 ms   (+0.28%) |       1   →       1              |       89.06 ms →       89.31 ms   (+0.28%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.39 ms →       11.09 ms   (-2.65%) |       1   →       1              |       11.39 ms →       11.09 ms   (-2.65%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.28 ms →       64.20 ms   (-0.11%) |       2   →       2              |      128.55 ms →      128.41 ms   (-0.11%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      191.36 ms →      200.23 ms   (+4.64%) |       2   →       2              |      382.72 ms →      400.46 ms   (+4.64%) | 
  │ │ │ └ sddk::wf_inner                                                |      191.26 ms →      200.13 ms   (+4.64%) |       2   →       2              |      382.52 ms →      400.27 ms   (+4.64%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       37.50 ns →       34.50 ns   (-8.00%) |       2   →       2              |       75.00 ns →       69.00 ns   (-8.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      189.83 ms →      198.54 ms   (+4.59%) |       2   →       2              |      379.65 ms →      397.07 ms   (+4.59%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       20.00 ns →       21.50 ns   (+7.50%) |       2   →       2              |       40.00 ns →       43.00 ns   (+7.50%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.22 ms →      114.35 ms   (-1.61%) |       1   →       1              |      116.22 ms →      114.35 ms   (-1.61%) | 
  │ │ └ sddk::wf_trans                                                  |       36.51 ms →       37.41 ms   (+2.45%) |       1   →       1              |       36.51 ms →       37.41 ms   (+2.45%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.68 ms →       35.65 ms   (-0.08%) |       1   →       1              |       35.68 ms →       35.65 ms   (-0.08%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      481.00 ns →      424.00 ns  (-11.85%) |       1   →       1              |      481.00 ns →      424.00 ns  (-11.85%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      104.77 s  →      122.68 s   (+17.09%) |       1   →       1              |      104.77 s  →      122.68 s   (+17.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.15 ms →        2.19 ms   (+1.98%) |      31   →      31              |       66.57 ms →       67.88 ms   (+1.98%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.73 s  →        2.85 s    (+4.17%) |      38   →      43    (+13.16%) |      103.80 s  →      122.36 s   (+17.88%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        7.78 ms →        7.15 ms   (-8.13%) |      38   →      43    (+13.16%) |      295.82 ms →      307.53 ms   (+3.96%) | 
! │ │ │ ├ sirius::Local_operator                                        |        7.43 ms →        6.82 ms   (-8.27%) |      38   →      43    (+13.16%) |      282.41 ms →      293.14 ms   (+3.80%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms →        1.51 ms   (+0.84%) |      38   →      43    (+13.16%) |       57.02 ms →       65.07 ms  (+14.11%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.48 ms →        3.85 ms  (-14.06%) |      38   →      43    (+13.16%) |      170.40 ms →      165.72 ms   (-2.75%) | 
! │ │ │ ├ sirius::Non_local_operator                                    |       67.80 μs →       62.10 μs   (-8.41%) |      76   →      86    (+13.16%) |        5.15 ms →        5.34 ms   (+3.64%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |       85.56 μs →       81.96 μs   (-4.21%) |      38   →      43    (+13.16%) |        3.25 ms →        3.52 ms   (+8.39%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       69.93 μs →       69.14 μs   (-1.14%) |      38   →      43    (+13.16%) |        2.66 ms →        2.97 ms  (+11.87%) | 
- │ │ ├ sirius::Band::solve                                             |        2.06 s  →        2.17 s    (+5.22%) |      38   →      43    (+13.16%) |       78.39 s  →       93.33 s   (+19.07%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      205.23 μs →      204.16 μs   (-0.52%) |      38   →      43    (+13.16%) |        7.80 ms →        8.78 ms  (+12.57%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.00 μs →      197.20 μs   (-0.40%) |      38   →      43    (+13.16%) |        7.52 ms →        8.48 ms  (+12.70%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.50 μs →        4.93 μs  (-10.27%) |      38   →      43    (+13.16%) |      208.89 μs →      212.09 μs   (+1.53%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.06 s  →        2.16 s    (+4.84%) |      38   →      43    (+13.16%) |       78.22 s  →       92.79 s   (+18.63%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       60.43 ms →       94.35 ms  (+56.13%) |      38   →      43    (+13.16%) |        2.30 s  →        4.06 s   (+76.67%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.72 ms →        3.43 ms  (-27.41%) |     228   →     301    (+32.02%) |        1.08 s  →        1.03 s    (-4.17%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.66 ms →        1.69 ms   (+1.95%) |      38   →      43    (+13.16%) |       63.17 ms →       72.88 ms  (+15.36%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      417.66 μs →      417.03 μs   (-0.15%) |      38   →      43    (+13.16%) |       15.87 ms →       17.93 ms  (+12.99%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      981.60 μs →        1.03 ms   (+4.50%) |      38   →      43    (+13.16%) |       37.30 ms →       44.11 ms  (+18.25%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.97 s  →        1.99 s    (+1.14%) |      38   →      43    (+13.16%) |       74.94 s  →       85.76 s   (+14.45%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      211.58 ms →      257.87 ms  (+21.88%) |     201   →     188     (-6.47%) |       42.53 s  →       48.48 s   (+14.00%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      149.74 ms →      184.14 ms  (+22.97%) |     201   →     188     (-6.47%) |       30.10 s  →       34.62 s   (+15.02%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.12 ms →       33.44 ms  (+23.32%) |     201   →     188     (-6.47%) |        5.45 s  →        6.29 s   (+15.34%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      687.75 μs →        1.71 ms (+148.21%) |     201   →     188     (-6.47%) |      138.24 ms →      320.93 ms (+132.16%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.63 ms →        7.28 ms (+100.90%) |      38   →      44    (+15.79%) |      137.78 ms →      320.50 ms (+132.62%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.03 ms →       26.36 ms  (+19.65%) |     201   →     188     (-6.47%) |        4.43 s  →        4.96 s   (+11.92%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      688.03 μs →        1.94 ms (+182.59%) |     201   →     188     (-6.47%) |      138.29 ms →      365.53 ms (+164.31%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.62 ms →        8.29 ms (+128.76%) |      38   →      44    (+15.79%) |      137.75 ms →      364.86 ms (+164.88%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.57 ms →       41.27 ms  (+22.93%) |     201   →     188     (-6.47%) |        6.75 s  →        7.76 s   (+14.98%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.02 ms →       25.90 ms  (+23.25%) |     201   →     188     (-6.47%) |        4.22 s  →        4.87 s   (+15.28%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.64 ms →        2.74 ms   (+3.53%) |     201   →     188     (-6.47%) |      531.38 ms →      514.58 ms   (-3.16%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.11 ms →       26.76 ms  (+21.05%) |     201   →     188     (-6.47%) |        4.44 s  →        5.03 s   (+13.22%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.18 ms →        2.60 ms  (+19.47%) |     201   →     188     (-6.47%) |      437.81 ms →      489.24 ms  (+11.75%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.53 ms →       22.10 ms  (+19.29%) |     402   →     376     (-6.47%) |        7.45 s  →        8.31 s   (+11.57%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       56.70 ms →       68.85 ms  (+21.41%) |     201   →     188     (-6.47%) |       11.40 s  →       12.94 s   (+13.56%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |       13.02 ms →       15.92 ms  (+22.26%) |     364   →     333     (-8.52%) |        4.74 s  →        5.30 s   (+11.85%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       54.83 ns →       88.90 ns  (+62.13%) |     364   →     333     (-8.52%) |       19.96 μs →       29.60 μs  (+48.32%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.47 ms →       11.91 ms  (+25.78%) |     364   →     333     (-8.52%) |        3.45 s  →        3.97 s   (+15.07%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       42.91 ns →       61.35 ns  (+42.97%) |     364   →     333     (-8.52%) |       15.62 μs →       20.43 μs  (+30.80%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.19 ms →        3.79 ms  (+19.06%) |     201   →     188     (-6.47%) |      640.61 ms →      713.39 ms  (+11.36%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.69 ms →       18.50 ms  (+17.97%) |     201   →     188     (-6.47%) |        3.15 s  →        3.48 s   (+10.34%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |       17.57 ms →       23.79 ms  (+35.39%) |     163   →     145    (-11.04%) |        2.86 s  →        3.45 s   (+20.44%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.83 ms →        7.91 ms  (+35.73%) |     489   →     435    (-11.04%) |        2.85 s  →        3.44 s   (+20.74%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       20.42 ms →       23.91 ms  (+17.13%) |     201   →     188     (-6.47%) |        4.10 s  →        4.50 s    (+9.55%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |       19.29 ms →       22.80 ms  (+18.15%) |     201   →     188     (-6.47%) |        3.88 s  →        4.29 s   (+10.51%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |      118.34 ns →       58.89 ns  (-50.23%) |     201   →     188     (-6.47%) |       23.79 μs →       11.07 μs  (-53.45%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       15.81 ms →       18.83 ms  (+19.06%) |     201   →     188     (-6.47%) |        3.18 s  →        3.54 s   (+11.36%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       22.97 ns →       51.15 ns (+122.70%) |     201   →     188     (-6.47%) |        4.62 μs →        9.62 μs (+108.30%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       48.23 ms →       61.02 ms  (+26.51%) |     201   →     188     (-6.47%) |        9.69 s  →       11.47 s   (+18.33%) | 
- │ │ │ │   ├ sirius::residuals                                         |       15.77 ms →       23.35 ms  (+48.03%) |     196   →     187     (-4.59%) |        3.09 s  →        4.37 s   (+41.23%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |       16.57 ms →       20.88 ms  (+26.07%) |     164   →     187    (+14.02%) |        2.72 s  →        3.91 s   (+43.75%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.04 ms →        8.90 ms  (+10.76%) |     328   →     374    (+14.02%) |        2.64 s  →        3.33 s   (+26.30%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.56 ms →        1.66 ms   (+6.19%) |     164   →     187    (+14.02%) |      256.57 ms →      310.65 ms  (+21.08%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.43 ms →       60.59 ms  (+17.82%) |      80   →      66    (-17.50%) |        4.11 s  →        4.00 s    (-2.80%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       32.81 ms →       44.12 ms  (+34.48%) |     122   →      89    (-27.05%) |        4.00 s  →        3.93 s    (-1.90%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       24.25 ms →       34.98 ms  (+44.27%) |     164   →     112    (-31.71%) |        3.98 s  →        3.92 s    (-1.47%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      539.92 ns →      664.49 ns  (+23.07%) |      38   →      43    (+13.16%) |       20.52 μs →       28.57 μs  (+39.26%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       31.51 μs →       31.20 μs   (-0.97%) |      38   →      43    (+13.16%) |        1.20 ms →        1.34 ms  (+12.06%) | 
! │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.53 ms →        3.41 ms   (-3.33%) |      38   →      43    (+13.16%) |      134.02 ms →      146.62 ms   (+9.39%) | 
- │ │ ├ sirius::Density::generate                                       |      292.99 ms →      293.20 ms   (+0.07%) |      38   →      43    (+13.16%) |       11.13 s  →       12.61 s   (+13.24%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      289.05 ms →      289.31 ms   (+0.09%) |      38   →      43    (+13.16%) |       10.98 s  →       12.44 s   (+13.26%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       65.36 ms →       66.70 ms   (+2.05%) |      38   →      43    (+13.16%) |        2.48 s  →        2.87 s   (+15.47%) | 
! │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       63.65 μs →       59.90 μs   (-5.89%) |      38   →      43    (+13.16%) |        2.42 ms →        2.58 ms   (+6.50%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.15 ms →        1.21 ms   (+4.84%) |       2   →       2              |        2.30 ms →        2.41 ms   (+4.84%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       54.07 ms →       55.41 ms   (+2.48%) |      38   →      43    (+13.16%) |        2.05 s  →        2.38 s   (+15.96%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.07 ms →       60.08 ms   (+0.01%) |      38   →      43    (+13.16%) |        2.28 s  →        2.58 s   (+13.17%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.40 μs →       10.48 μs   (-8.05%) |      38   →      43    (+13.16%) |      433.13 μs →      450.65 μs   (+4.05%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (-0.02%) |      38   →      43    (+13.16%) |       87.78 ms →       99.31 ms  (+13.14%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       57.22 ms →       57.22 ms   (+0.01%) |      38   →      43    (+13.16%) |        2.17 s  →        2.46 s   (+13.17%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.80 ms →        5.80 ms   (-0.09%) |      38   →      43    (+13.16%) |      220.43 ms →      249.20 ms  (+13.05%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      754.55 ns →      569.51 ns  (-24.52%) |      38   →      43    (+13.16%) |       28.67 μs →       24.49 μs  (-14.59%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.81 ms →      104.01 ms   (-0.76%) |      38   →      43    (+13.16%) |        3.98 s  →        4.47 s   (+12.29%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.40 ms   (-0.18%) |      38   →      43    (+13.16%) |       91.34 ms →      103.17 ms  (+12.96%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms →       20.06 ms   (+0.01%) |      38   →      43    (+13.16%) |      762.24 ms →      862.64 ms  (+13.17%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms →       19.89 ms   (-0.00%) |      38   →      43    (+13.16%) |      755.96 ms →      855.40 ms  (+13.15%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      232.29 ns →      429.47 ns  (+84.88%) |      38   →      43    (+13.16%) |        8.83 μs →       18.47 μs (+109.21%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.25 ms   (+0.15%) |      38   →      43    (+13.16%) |       47.58 ms →       53.92 ms  (+13.33%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.69 ms →        2.64 ms   (-1.81%) |      38   →      43    (+13.16%) |      102.05 ms →      113.39 ms  (+11.11%) | 
- │ │ ├ sirius::Density::mix                                            |      135.65 ms →      142.30 ms   (+4.91%) |      38   →      43    (+13.16%) |        5.15 s  →        6.12 s   (+18.71%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      260.57 μs →      255.15 μs   (-2.08%) |      38   →      43    (+13.16%) |        9.90 ms →       10.97 ms  (+10.81%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        2.72 ms →        2.69 ms   (-1.18%) |      38   →      43    (+13.16%) |      103.44 ms →      115.67 ms  (+11.82%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.53 ms →        2.49 ms   (-1.64%) |      38   →      43    (+13.16%) |       96.18 ms →      107.06 ms  (+11.30%) | 
- │ │ ├ sirius::Potential::generate                                     |      180.47 ms →      180.19 ms   (-0.15%) |      38   →      43    (+13.16%) |        6.86 s  →        7.75 s   (+12.99%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       64.11 ms →       64.44 ms   (+0.51%) |      38   →      43    (+13.16%) |        2.44 s  →        2.77 s   (+13.73%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.08 ms →        9.25 ms  (+14.42%) |      38   →      43    (+13.16%) |      307.14 ms →      397.67 ms  (+29.47%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.23 ms →        4.17 ms   (-1.34%) |      38   →      43    (+13.16%) |      160.65 ms →      179.35 ms  (+11.64%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms →        4.09 ms   (+0.19%) |      38   →      43    (+13.16%) |      155.04 ms →      175.77 ms  (+13.37%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.08 ms →        4.09 ms   (+0.20%) |      38   →      43    (+13.16%) |      155.01 ms →      175.75 ms  (+13.38%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      231.40 μs →      230.76 μs   (-0.28%) |      76   →      86    (+13.16%) |       17.59 ms →       19.85 ms  (+12.84%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       91.01 ms →       90.54 ms   (-0.52%) |      38   →      43    (+13.16%) |        3.46 s  →        3.89 s   (+12.57%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       89.98 ms →       89.51 ms   (-0.52%) |      38   →      43    (+13.16%) |        3.42 s  →        3.85 s   (+12.57%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.59 ms   (-0.27%) |     190   →     215    (+13.16%) |      302.48 ms →      341.36 ms  (+12.86%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.49 ms →        2.41 ms   (-3.07%) |     342   →     387    (+13.16%) |      852.09 ms →      934.56 ms   (+9.68%) | 
- │ │ │ │   ├ sirius::gradient                                          |        2.45 ms →        2.45 ms   (-0.03%) |      38   →      43    (+13.16%) |       93.17 ms →      105.40 ms  (+13.13%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      724.65 μs →      725.14 μs   (+0.07%) |     114   →     129    (+13.16%) |       82.61 ms →       93.54 ms  (+13.23%) | 
- │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.81 ms   (-0.33%) |      38   →      43    (+13.16%) |      106.98 ms →      120.66 ms  (+12.79%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.59 ms →        2.58 ms   (-0.28%) |      38   →      43    (+13.16%) |       98.26 ms →      110.88 ms  (+12.84%) | 
- │ │ │ │   └ sirius::divergence                                        |       19.71 ms →       19.92 ms   (+1.08%) |      38   →      43    (+13.16%) |      748.89 ms →      856.58 ms  (+14.38%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.44 ms →        2.44 ms   (+0.09%) |      38   →      43    (+13.16%) |       92.56 ms →      104.83 ms  (+13.26%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.37 ms →        3.28 ms   (-2.53%) |      38   →      43    (+13.16%) |      128.07 ms →      141.25 ms  (+10.29%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.95 ms →       20.92 ms   (-0.18%) |      38   →      43    (+13.16%) |      796.28 ms →      899.42 ms  (+12.95%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      291.92 ns →      309.07 ns   (+5.87%) |      38   →      43    (+13.16%) |       11.09 μs →       13.29 μs  (+19.81%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      225.29 ns →      247.51 ns   (+9.86%) |      38   →      43    (+13.16%) |        8.56 μs →       10.64 μs  (+24.32%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.25 ms →        2.23 ms   (-1.07%) |      38   →      43    (+13.16%) |       85.53 ms →       95.75 ms  (+11.94%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.24 ms →        4.27 ms   (+0.79%) |     266   →     301    (+13.16%) |        1.13 s  →        1.29 s   (+14.05%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.14 ms →        4.10 ms   (-1.06%) |     266   →     301    (+13.16%) |        1.10 s  →        1.23 s   (+11.96%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.14 ms →        4.10 ms   (-1.06%) |     266   →     301    (+13.16%) |        1.10 s  →        1.23 s   (+11.96%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.05 ms →        4.06 ms   (+0.10%) |     114   →     129    (+13.16%) |      461.94 ms →      523.24 ms  (+13.27%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.93 ms →        3.90 ms   (-0.70%) |     114   →     129    (+13.16%) |      447.46 ms →      502.81 ms  (+12.37%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.14 ms →        4.19 ms   (+1.33%) |      38   →      43    (+13.16%) |      157.19 ms →      180.25 ms  (+14.67%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      107.25 μs →      145.25 μs  (+35.43%) |      38   →      43    (+13.16%) |        4.08 ms →        6.25 ms  (+53.25%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      103.61 μs →      141.82 μs  (+36.88%) |      38   →      43    (+13.16%) |        3.94 ms →        6.10 ms  (+54.89%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.32 ms →        5.39 ms   (+1.36%) |       2   →       2              |       10.63 ms →       10.78 ms   (+1.36%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.39 ms →        4.13 ms   (-5.97%) |       6   →       6              |       26.33 ms →       24.76 ms   (-5.97%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.38 ms →        4.06 ms   (-7.22%) |       6   →       6              |       26.27 ms →       24.37 ms   (-7.22%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.38 ms →        4.06 ms   (-7.23%) |       6   →       6              |       26.27 ms →       24.37 ms   (-7.23%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.25 ms →        3.93 ms   (-7.64%) |       3   →       3              |       12.76 ms →       11.79 ms   (-7.64%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.18 ms →        3.88 ms   (-7.11%) |       3   →       3              |       12.55 ms →       11.65 ms   (-7.11%) | 
  ├ sirius::Periodic_function|inner                                     |        4.32 ms →        4.16 ms   (-3.61%) |       2   →       2              |        8.64 ms →        8.32 ms   (-3.61%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.31 ms →        4.15 ms   (-3.65%) |       2   →       2              |        8.62 ms →        8.30 ms   (-3.65%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.31 ms →        4.15 ms   (-3.65%) |       2   →       2              |        8.62 ms →        8.30 ms   (-3.65%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.31 ms →        3.90 ms   (-9.34%) |       1   →       1              |        4.31 ms →        3.90 ms   (-9.34%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.13 ms →        3.90 ms   (-5.72%) |       1   →       1              |        4.13 ms →        3.90 ms   (-5.72%) | 
  └ sirius::finalize                                                    |      474.28 ms →      469.02 ms   (-1.11%) |       1   →       1              |      474.28 ms →      469.02 ms   (-1.11%) | 
  ====================================================================================================================================================================================================
```
