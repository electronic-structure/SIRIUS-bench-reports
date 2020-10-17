# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      134.48 s  →      129.08 s    (-4.01%) |       1   →       1              |      134.48 s  →      129.08 s    (-4.01%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.69 s    (-0.97%) |       1   →       1              |        2.72 s  →        2.69 s    (-0.97%) | 
  ├ sirius::Simulation_context::initialize                              |        3.08 s  →        2.93 s    (-4.72%) |       1   →       1              |        3.08 s  →        2.93 s    (-4.72%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       50.62 ms →        3.57 ms  (-92.95%) |       1   →       1              |       50.62 ms →        3.57 ms  (-92.95%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      209.43 ms →      171.96 ms  (-17.89%) |       1   →       1              |      209.43 ms →      171.96 ms  (-17.89%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       92.70 ms →       73.90 ms  (-20.28%) |       2   →       2              |      185.41 ms →      147.80 ms  (-20.28%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.94 ms →       24.08 ms   (+0.59%) |       1   →       1              |       23.94 ms →       24.08 ms   (+0.59%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.90 ms →        6.35 ms   (+7.73%) |       1   →       1              |        5.90 ms →        6.35 ms   (+7.73%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.00 ms →       17.67 ms   (-1.82%) |       1   →       1              |       18.00 ms →       17.67 ms   (-1.82%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.98 ms →       17.65 ms   (-1.83%) |       1   →       1              |       17.98 ms →       17.65 ms   (-1.83%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.14 ms   (-0.42%) |       1   →       1              |        4.16 ms →        4.14 ms   (-0.42%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.19%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.19%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.99 μs →      102.21 μs   (+1.21%) |       1   →       1              |      100.99 μs →      102.21 μs   (+1.21%) | 
  │ └ sirius::Simulation_context::update                                |        2.78 s  →        2.72 s    (-2.18%) |       1   →       1              |        2.78 s  →        2.72 s    (-2.18%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.67 ms →       10.94 ms   (+2.53%) |       1   →       1              |       10.67 ms →       10.94 ms   (+2.53%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.23 ms →        4.48 ms   (+6.06%) |       1   →       1              |        4.23 ms →        4.48 ms   (+6.06%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.40 ms →        6.41 ms   (+0.08%) |       1   →       1              |        6.40 ms →        6.41 ms   (+0.08%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.39 ms →        6.39 ms   (+0.07%) |       1   →       1              |        6.39 ms →        6.39 ms   (+0.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.91 ms   (+0.12%) |       1   →       1              |        3.90 ms →        3.91 ms   (+0.12%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.06%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.06%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.92 μs →       99.28 μs   (-1.62%) |       1   →       1              |      100.92 μs →       99.28 μs   (-1.62%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.92 ms →       68.47 ms   (+8.82%) |       2   →       2              |      125.84 ms →      136.94 ms   (+8.82%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.31 ms →        5.16 ms   (-2.75%) |       2   →       2              |       10.62 ms →       10.33 ms   (-2.75%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.92 ms   (+9.80%) |       1   →       1              |        4.48 ms →        4.92 ms   (+9.80%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.87 ms →       21.76 ms   (-0.49%) |       2   →       2              |       43.73 ms →       43.52 ms   (-0.49%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.00 ms →       15.16 ms   (+1.10%) |       2   →       2              |       29.99 ms →       30.32 ms   (+1.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.79 ms   (+0.04%) |       4   →       4              |       79.13 ms →       79.16 ms   (+0.04%) | 
  │   ├ sddk::Gvec::init                                                |      183.89 ms →      172.08 ms   (-6.42%) |       2   →       2              |      367.78 ms →      344.16 ms   (-6.42%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      138.86 ms →      129.87 ms   (-6.47%) |       2   →       2              |      277.71 ms →      259.73 ms   (-6.47%) | 
+ │   ├ sddk::Gvec_shells                                               |      205.53 ms →      175.63 ms  (-14.55%) |       1   →       1              |      205.53 ms →      175.63 ms  (-14.55%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.36 ms   (+2.06%) |       1   →       1              |        1.33 ms →        1.36 ms   (+2.06%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.66 ms →      298.46 ms   (+0.95%) |       2   →       2              |      591.32 ms →      596.93 ms   (+0.95%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.63 ms →       35.65 ms   (+0.06%) |       1   →       1              |       35.63 ms →       35.65 ms   (+0.06%) | 
  │ ├ sirius::K_point::K_point                                          |        2.32 μs →        2.47 μs   (+6.46%) |       4   →       4              |        9.29 μs →        9.89 μs   (+6.46%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.53 ms →       35.55 ms   (+0.05%) |       1   →       1              |       35.53 ms →       35.55 ms   (+0.05%) | 
  │   └ sirius::K_point::initialize                                     |       35.44 ms →       35.44 ms   (+0.01%) |       1   →       1              |       35.44 ms →       35.44 ms   (+0.01%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.04 ms →       18.02 ms   (-0.14%) |       1   →       1              |       18.04 ms →       18.02 ms   (-0.14%) | 
  │     │ └ sddk::Gvec::init                                            |        8.11 ms →        8.06 ms   (-0.61%) |       1   →       1              |        8.11 ms →        8.06 ms   (-0.61%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.21 μs →        9.30 μs   (-8.89%) |       1   →       1              |       10.21 μs →        9.30 μs   (-8.89%) | 
  │     └ sirius::K_point::update                                       |       12.51 ms →       12.59 ms   (+0.63%) |       1   →       1              |       12.51 ms →       12.59 ms   (+0.63%) | 
  │       └ sirius::Beta_projectors                                     |        6.29 ms →        6.34 ms   (+0.77%) |       1   →       1              |        6.29 ms →        6.34 ms   (+0.77%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.71 ms →        3.73 ms   (+0.60%) |       1   →       1              |        3.71 ms →        3.73 ms   (+0.60%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.30 ms →        5.44 ms   (+2.62%) |       2   →       2              |       10.61 ms →       10.88 ms   (+2.62%) | 
  ├ sirius::Potential                                                   |      159.88 ms →      158.37 ms   (-0.94%) |       1   →       1              |      159.88 ms →      158.37 ms   (-0.94%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.85 ms   (-0.01%) |       6   →       6              |       35.08 ms →       35.08 ms   (-0.01%) | 
  │ └ sirius::Potential::update                                         |      124.05 ms →      122.57 ms   (-1.19%) |       1   →       1              |      124.05 ms →      122.57 ms   (-1.19%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.33 ms →      121.90 ms   (-1.16%) |       1   →       1              |      123.33 ms →      121.90 ms   (-1.16%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      116.04 ms →      110.93 ms   (-4.40%) |       1   →       1              |      116.04 ms →      110.93 ms   (-4.40%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.39 ms →       10.03 ms  (+56.80%) |       1   →       1              |        6.39 ms →       10.03 ms  (+56.80%) | 
  ├ sirius::Density                                                     |      137.26 ms →      136.33 ms   (-0.68%) |       1   →       1              |      137.26 ms →      136.33 ms   (-0.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.30 ms →        5.29 ms   (-0.07%) |       2   →       2              |       10.60 ms →       10.59 ms   (-0.07%) | 
  │ └ sirius::Density::update                                           |      126.39 ms →      125.47 ms   (-0.73%) |       1   →       1              |      126.39 ms →      125.47 ms   (-0.73%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.97 ms →      125.05 ms   (-0.72%) |       1   →       1              |      125.97 ms →      125.05 ms   (-0.72%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.96 μs →      102.25 μs   (-0.69%) |       1   →       1              |      102.96 μs →      102.25 μs   (-0.69%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      120.07 ms →      112.63 ms   (-6.20%) |       1   →       1              |      120.07 ms →      112.63 ms   (-6.20%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.31 ms →       11.89 ms (+123.99%) |       1   →       1              |        5.31 ms →       11.89 ms (+123.99%) | 
  ├ sirius::Density::initial_density                                    |      176.91 ms →      176.25 ms   (-0.37%) |       1   →       1              |      176.91 ms →      176.25 ms   (-0.37%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      124.13 ms →      110.71 ms  (-10.80%) |       1   →       1              |      124.13 ms →      110.71 ms  (-10.80%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.04 ms →       11.56 ms (+129.20%) |       2   →       2              |       10.08 ms →       23.11 ms (+129.20%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.72 ms →       10.01 ms   (+3.00%) |       1   →       1              |        9.72 ms →       10.01 ms   (+3.00%) | 
  ├ sirius::Potential::generate                                         |      593.30 ms →      593.51 ms   (+0.04%) |       1   →       1              |      593.30 ms →      593.51 ms   (+0.04%) | 
  │ ├ sirius::Potential::poisson                                        |      138.82 ms →      138.95 ms   (+0.09%) |       1   →       1              |      138.82 ms →      138.95 ms   (+0.09%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.32 ms →       17.86 ms (+235.52%) |       1   →       1              |        5.32 ms →       17.86 ms (+235.52%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.72 ms →       10.51 ms   (-1.95%) |       1   →       1              |       10.72 ms →       10.51 ms   (-1.95%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.21 ms →        9.93 ms   (-2.75%) |       1   →       1              |       10.21 ms →        9.93 ms   (-2.75%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.20 ms →        9.92 ms   (-2.75%) |       1   →       1              |       10.20 ms →        9.92 ms   (-2.75%) | 
  │ ├ sirius::Periodic_function::add                                    |      565.45 μs →      557.87 μs   (-1.34%) |       2   →       2              |        1.13 ms →        1.12 ms   (-1.34%) | 
  │ ├ sirius::Potential::xc                                             |       53.98 ms →       54.42 ms   (+0.81%) |       1   →       1              |       53.98 ms →       54.42 ms   (+0.81%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.61 ms →       52.15 ms   (+1.06%) |       1   →       1              |       51.61 ms →       52.15 ms   (+1.06%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.72 ms →        5.61 ms   (-2.02%) |       2   →       2              |       11.45 ms →       11.22 ms   (-2.02%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.42 ms →        5.45 ms   (+0.53%) |       1   →       1              |        5.42 ms →        5.45 ms   (+0.53%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.10 ms →        5.94 ms   (-2.58%) |       1   →       1              |        6.10 ms →        5.94 ms   (-2.58%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.68 ms →       92.73 ms   (+0.06%) |       1   →       1              |       92.68 ms →       92.73 ms   (+0.06%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.20 ms →      299.02 ms   (-0.06%) |       1   →       1              |      299.20 ms →      299.02 ms   (-0.06%) | 
  ├ sirius::Hamiltonian0                                                |        8.55 ms →        8.37 ms   (-2.15%) |       1   →       1              |        8.55 ms →        8.37 ms   (-2.15%) | 
  │ ├ sirius::Local_operator                                            |        8.21 ms →        8.02 ms   (-2.23%) |       1   →       1              |        8.21 ms →        8.02 ms   (-2.23%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.72 ms   (-1.11%) |       1   →       1              |        4.77 ms →        4.72 ms   (-1.11%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.52 ms →        2.39 ms   (-4.82%) |       1   →       1              |        2.52 ms →        2.39 ms   (-4.82%) | 
  │ ├ sirius::Non_local_operator                                        |       61.54 μs →       62.93 μs   (+2.26%) |       2   →       2              |      123.08 μs →      125.86 μs   (+2.26%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.24 μs →       94.24 μs   (-0.00%) |       1   →       1              |       94.24 μs →       94.24 μs   (-0.00%) | 
  │ └ sirius::Q_operator::initialize                                    |       75.32 μs →       73.39 μs   (-2.56%) |       1   →       1              |       75.32 μs →       73.39 μs   (-2.56%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.87 s    (+0.17%) |       1   →       1              |        1.87 s  →        1.87 s    (+0.17%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.70 ms   (-0.02%) |       1   →       1              |       18.70 ms →       18.70 ms   (-0.02%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      194.51 μs →      185.19 μs   (-4.79%) |       1   →       1              |      194.51 μs →      185.19 μs   (-4.79%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.51 ms   (+0.03%) |       1   →       1              |       18.50 ms →       18.51 ms   (+0.03%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.86 s    (+0.17%) |       1   →       1              |        1.85 s  →        1.86 s    (+0.17%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      129.93 ms →      131.52 ms   (+1.22%) |       4   →       4              |      519.72 ms →      526.08 ms   (+1.22%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.39 ms →       52.59 ms   (-1.51%) |       1   →       1              |       53.39 ms →       52.59 ms   (-1.51%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.63 ms →       21.03 ms   (-2.75%) |       1   →       1              |       21.63 ms →       21.03 ms   (-2.75%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.60 ms →      638.51 ms   (+0.62%) |       1   →       1              |      634.60 ms →      638.51 ms   (+0.62%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.68 ms →      297.79 ms   (+0.04%) |       1   →       1              |      297.68 ms →      297.79 ms   (+0.04%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.20 μs →        3.46 μs   (+8.16%) |       1   →       1              |        3.20 μs →        3.46 μs   (+8.16%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.36 μs →        2.41 μs   (+2.07%) |       1   →       1              |        2.36 μs →        2.41 μs   (+2.07%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      367.00 ns →      335.00 ns   (-8.72%) |       1   →       1              |      367.00 ns →      335.00 ns   (-8.72%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      495.00 ns →      517.00 ns   (+4.44%) |       1   →       1              |      495.00 ns →      517.00 ns   (+4.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.22 ms   (-0.09%) |       1   →       1              |        9.23 ms →        9.22 ms   (-0.09%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.52 ms →      122.45 ms   (+1.60%) |       1   →       1              |      120.52 ms →      122.45 ms   (+1.60%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.56 ms →      104.51 ms   (+0.91%) |       2   →       2              |      207.13 ms →      209.02 ms   (+0.91%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.16 ms →       40.15 ms   (-0.02%) |       2   →       2              |       80.33 ms →       80.31 ms   (-0.02%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.60 ms →       39.58 ms   (-0.04%) |       2   →       2              |       79.20 ms →       79.17 ms   (-0.04%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       12.50 ns →       33.50 ns (+168.00%) |       2   →       2              |       25.00 ns →       67.00 ns (+168.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.12 ms →       39.10 ms   (-0.05%) |       2   →       2              |       78.25 ms →       78.21 ms   (-0.05%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.50 ns →       30.00 ns  (+53.85%) |       2   →       2              |       39.00 ns →       60.00 ns  (+53.85%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.02 ms →       57.66 ms   (+1.12%) |       1   →       1              |       57.02 ms →       57.66 ms   (+1.12%) | 
  │ │ └ sddk::wf_trans                                                  |       30.74 ms →       31.12 ms   (+1.24%) |       1   →       1              |       30.74 ms →       31.12 ms   (+1.24%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.73 ms →       31.11 ms   (+1.23%) |       1   →       1              |       30.73 ms →       31.11 ms   (+1.23%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      571.00 ns →      358.00 ns  (-37.30%) |       1   →       1              |      571.00 ns →      358.00 ns  (-37.30%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      124.67 s  →      119.39 s    (-4.24%) |       1   →       1              |      124.67 s  →      119.39 s    (-4.24%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.75 ms   (-1.62%) |      19   →      19              |      111.05 ms →      109.24 ms   (-1.62%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.78 s  →        4.57 s    (-4.36%) |      26   →      26              |      124.23 s  →      118.82 s    (-4.36%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.00 ms →        4.60 ms   (-8.02%) |      26   →      26              |      130.07 ms →      119.64 ms   (-8.02%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.63 ms →        4.24 ms   (-8.61%) |      26   →      26              |      120.49 ms →      110.11 ms   (-8.61%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      995.40 μs →      940.26 μs   (-5.54%) |      26   →      26              |       25.88 ms →       24.45 ms   (-5.54%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.74 ms →        2.40 ms  (-12.34%) |      26   →      26              |       71.20 ms →       62.41 ms  (-12.34%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.03 μs →       64.68 μs   (+1.03%) |      52   →      52              |        3.33 ms →        3.36 ms   (+1.03%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.25 μs →       87.86 μs   (-0.44%) |      26   →      26              |        2.29 ms →        2.28 ms   (-0.44%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       79.12 μs →       79.20 μs   (+0.11%) |      26   →      26              |        2.06 ms →        2.06 ms   (+0.11%) | 
  │ │ ├ sirius::Band::solve                                             |        2.78 s  →        2.61 s    (-6.07%) |      26   →      26              |       72.16 s  →       67.78 s    (-6.07%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      157.87 μs →      155.11 μs   (-1.75%) |      26   →      26              |        4.10 ms →        4.03 ms   (-1.75%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      150.80 μs →      147.24 μs   (-2.36%) |      26   →      26              |        3.92 ms →        3.83 ms   (-2.36%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.14 μs →        5.93 μs  (+15.41%) |      26   →      26              |      133.53 μs →      154.11 μs  (+15.41%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.63 s  →        2.49 s    (-5.36%) |      26   →      26              |       68.35 s  →       64.69 s    (-5.36%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.15 ms →       96.42 ms   (+0.28%) |      26   →      26              |        2.50 s  →        2.51 s    (+0.28%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.75 ms →        7.88 ms   (+1.72%) |     156   →     156              |        1.21 s  →        1.23 s    (+1.72%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.92 ms →        5.90 ms   (-0.44%) |      26   →      26              |      153.99 ms →      153.31 ms   (-0.44%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.18 μs →      347.80 μs   (-0.68%) |      26   →      26              |        9.10 ms →        9.04 ms   (-0.68%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.30 ms   (+0.00%) |      52   →      52              |      119.86 ms →      119.86 ms   (+0.00%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.49 s  →        2.35 s    (-5.67%) |      26   →      26              |       64.77 s  →       61.10 s    (-5.67%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      127.00 ms →      138.07 ms   (+8.72%) |     277   →     262     (-5.42%) |       35.18 s  →       36.17 s    (+2.83%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       51.02 ms →       55.96 ms   (+9.67%) |     277   →     262     (-5.42%) |       14.13 s  →       14.66 s    (+3.73%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.93 μs →        2.10 μs   (+8.88%) |     277   →     262     (-5.42%) |      534.71 μs →      550.67 μs   (+2.99%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.66 μs →        1.77 μs   (+6.43%) |     277   →     262     (-5.42%) |      460.32 μs →      463.40 μs   (+0.67%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      370.86 ns →      484.68 ns  (+30.69%) |     277   →     262     (-5.42%) |      102.73 μs →      126.98 μs  (+23.61%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      437.50 ns →      543.26 ns  (+24.17%) |     277   →     262     (-5.42%) |      121.19 μs →      142.34 μs  (+17.45%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.41%) |     277   →     262     (-5.42%) |        2.06 s  →        1.95 s    (-5.03%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.81 ms →       25.48 ms  (+11.72%) |     277   →     262     (-5.42%) |        6.32 s  →        6.68 s    (+5.67%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.86 ms →       24.58 ms   (+7.50%) |     554   →     524     (-5.42%) |       12.67 s  →       12.88 s    (+1.68%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.30 ms →       35.90 ms   (+4.66%) |     277   →     262     (-5.42%) |        9.50 s  →        9.40 s    (-1.01%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.95 ms →        6.23 ms   (+4.66%) |     528   →     498     (-5.68%) |        3.14 s  →        3.10 s    (-1.28%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       68.98 ns →       63.40 ns   (-8.08%) |     528   →     498     (-5.68%) |       36.42 μs →       31.57 μs  (-13.31%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.84 ms →        5.12 ms   (+5.79%) |     528   →     498     (-5.68%) |        2.56 s  →        2.55 s    (-0.22%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.05 ns →       28.55 ns  (-45.14%) |     528   →     498     (-5.68%) |       27.48 μs →       14.22 μs  (-48.26%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      612.83 μs →      654.11 μs   (+6.74%) |     277   →     262     (-5.42%) |      169.75 ms →      171.38 ms   (+0.96%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.56 ms →       10.32 ms   (+7.96%) |     277   →     262     (-5.42%) |        2.65 s  →        2.70 s    (+2.12%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.10 ms →       14.52 ms   (+2.97%) |     251   →     236     (-5.98%) |        3.54 s  →        3.43 s    (-3.19%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.70 ms →        4.84 ms   (+2.97%) |     753   →     708     (-5.98%) |        3.54 s  →        3.43 s    (-3.19%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.32 ms →       10.39 ms   (+0.64%) |     277   →     262     (-5.42%) |        2.86 s  →        2.72 s    (-4.81%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.06 ms →       10.18 ms   (+1.27%) |     277   →     262     (-5.42%) |        2.79 s  →        2.67 s    (-4.22%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.00 ns →       29.66 ns  (-36.89%) |     277   →     262     (-5.42%) |       13.02 μs →        7.77 μs  (-40.31%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.94 ms →        9.07 ms   (+1.45%) |     277   →     262     (-5.42%) |        2.48 s  →        2.38 s    (-4.04%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       70.04 ns →       57.37 ns  (-18.10%) |     277   →     262     (-5.42%) |       19.40 μs →       15.03 μs  (-22.53%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       34.76 ms →       18.67 ms  (-46.28%) |     277   →     262     (-5.42%) |        9.63 s  →        4.89 s   (-49.19%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.53 ms →       13.17 ms   (-2.63%) |     268   →     252     (-5.97%) |        3.63 s  →        3.32 s    (-8.45%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.20 ms →       11.68 ms   (-4.21%) |     258   →     243     (-5.81%) |        3.15 s  →        2.84 s    (-9.78%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.10 ms →        5.84 ms   (-4.21%) |     516   →     486     (-5.81%) |        3.15 s  →        2.84 s    (-9.78%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.61 ms →        1.72 ms   (+6.97%) |     258   →     243     (-5.81%) |      415.82 ms →      418.93 ms   (+0.75%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.93 ms →       53.90 ms  (-28.08%) |      53   →      85    (+60.38%) |        3.97 s  →        4.58 s   (+15.35%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.41 ms →       31.55 ms  (-36.14%) |      80   →     144    (+80.00%) |        3.95 s  →        4.54 s   (+14.95%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.94 ms →       22.38 ms  (-39.41%) |     107   →     203    (+89.72%) |        3.95 s  →        4.54 s   (+14.94%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      601.00 ns →      451.85 ns  (-24.82%) |      26   →      26              |       15.63 μs →       11.75 μs  (-24.82%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       33.29 μs →      119.65 μs (+259.38%) |      26   →      26              |      865.62 μs →        3.11 ms (+259.38%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      596.11 μs →      611.91 μs   (+2.65%) |      26   →      26              |       15.50 ms →       15.91 ms   (+2.65%) | 
  │ │ ├ sirius::Density::generate                                       |      784.41 ms →      767.61 ms   (-2.14%) |      26   →      26              |       20.39 s  →       19.96 s    (-2.14%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      404.59 ms →      402.79 ms   (-0.45%) |      26   →      26              |       10.52 s  →       10.47 s    (-0.45%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.52 μs →        9.05 μs   (+6.27%) |      26   →      26              |      221.46 μs →      235.35 μs   (+6.27%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.91 μs →        8.51 μs   (+7.55%) |      26   →      26              |      205.67 μs →      221.19 μs   (+7.55%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.17 ms →      100.83 ms   (+0.66%) |      26   →      26              |        2.60 s  →        2.62 s    (+0.66%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.44 μs →        7.81 μs   (+4.94%) |      26   →      26              |      193.52 μs →      203.08 μs   (+4.94%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.02%) |      26   →      26              |      185.08 ms →      185.11 ms   (+0.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.14 ms →       91.80 ms   (+0.72%) |      26   →      26              |        2.37 s  →        2.39 s    (+0.72%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      721.73 ns →      562.50 ns  (-22.06%) |      26   →      26              |       18.77 μs →       14.62 μs  (-22.06%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.24 ms →      164.59 ms   (+0.22%) |      26   →      26              |        4.27 s  →        4.28 s    (+0.22%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.39%) |      26   →      26              |       42.82 ms →       42.65 ms   (-0.39%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.26 ms →       88.23 ms   (-0.03%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.03%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.01 ms →       87.99 ms   (-0.02%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      288.46 ms →      272.56 ms   (-5.51%) |      26   →      26              |        7.50 s  →        7.09 s    (-5.51%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      288.46 ms →      272.56 ms   (-5.51%) |      26   →      26              |        7.50 s  →        7.09 s    (-5.51%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.62 ms →       24.70 ms  (-16.60%) |      26   →      26              |      770.15 ms →      642.30 ms  (-16.60%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.11 ms →      223.29 ms   (-2.11%) |      26   →      26              |        5.93 s  →        5.81 s    (-2.11%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       29.53 ms →       23.38 ms  (-20.83%) |      26   →      26              |      767.83 ms →      607.92 ms  (-20.83%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.14 ms →       80.67 ms   (-0.59%) |      26   →      26              |        2.11 s  →        2.10 s    (-0.59%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.62 ms →        8.00 ms  (+20.79%) |      26   →      26              |      172.21 ms →      208.01 ms  (+20.79%) | 
  │ │ ├ sirius::Density::mix                                            |      218.82 ms →      211.92 ms   (-3.15%) |      26   →      26              |        5.69 s  →        5.51 s    (-3.15%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      981.88 μs →      952.21 μs   (-3.02%) |      26   →      26              |       25.53 ms →       24.76 ms   (-3.02%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.71 ms →       10.24 ms   (-4.37%) |     334   →     334              |        3.58 s  →        3.42 s    (-4.37%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.34 ms →        9.92 ms   (-4.06%) |     334   →     334              |        3.45 s  →        3.31 s    (-4.06%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.34 ms →        9.92 ms   (-4.06%) |     334   →     334              |        3.45 s  →        3.31 s    (-4.06%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.57 ms →        6.63 ms   (+0.95%) |      26   →      26              |      170.80 ms →      172.41 ms   (+0.95%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.71 ms →        5.81 ms   (+1.76%) |      26   →      26              |      148.57 ms →      151.19 ms   (+1.76%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.67 ms →      580.87 ms   (+0.03%) |      26   →      26              |       15.10 s  →       15.10 s    (+0.03%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.58 ms →      138.89 ms   (+0.22%) |      26   →      26              |        3.60 s  →        3.61 s    (+0.22%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.28 ms →       17.74 ms (+235.94%) |      26   →      26              |      137.31 ms →      461.28 ms (+235.94%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.47 ms →       10.44 ms   (-0.26%) |      26   →      26              |      272.12 ms →      271.40 ms   (-0.26%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.01 ms →        9.99 ms   (-0.19%) |      26   →      26              |      260.17 ms →      259.69 ms   (-0.19%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.01 ms →        9.99 ms   (-0.19%) |      26   →      26              |      260.16 ms →      259.67 ms   (-0.19%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      558.55 μs →      548.78 μs   (-1.75%) |      52   →      52              |       29.04 ms →       28.54 ms   (-1.75%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.66 ms →       49.13 ms   (-1.06%) |      26   →      26              |        1.29 s  →        1.28 s    (-1.06%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.26 ms →       46.85 ms   (-0.88%) |      26   →      26              |        1.23 s  →        1.22 s    (-0.88%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        2.96 ms   (-2.51%) |      52   →      52              |      158.06 ms →      154.09 ms   (-2.51%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.80 ms →        5.59 ms   (-3.63%) |      26   →      26              |      150.71 ms →      145.24 ms   (-3.63%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.61 ms →        6.64 ms   (+0.45%) |      26   →      26              |      171.78 ms →      172.54 ms   (+0.45%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.01 ms →       91.20 ms   (+0.20%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.20%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.36 ms →      292.66 ms   (+0.10%) |      26   →      26              |        7.60 s  →        7.61 s    (+0.10%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      292.62 ms →      279.06 ms   (-4.63%) |      26   →      26              |        7.61 s  →        7.26 s    (-4.63%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      292.62 ms →      279.06 ms   (-4.63%) |      26   →      26              |        7.61 s  →        7.26 s    (-4.63%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.81 ms →       27.19 ms  (-17.14%) |      26   →      26              |      853.07 ms →      706.84 ms  (-17.14%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.67 ms →      224.24 ms   (-0.63%) |      26   →      26              |        5.87 s  →        5.83 s    (-0.63%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       30.34 ms →       23.86 ms  (-21.37%) |      26   →      26              |      788.85 ms →      620.28 ms  (-21.37%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.48 ms →        5.68 ms   (+3.61%) |      26   →      26              |      142.52 ms →      147.67 ms   (+3.61%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.30 ms →       10.13 ms   (-1.67%) |     182   →     182              |        1.87 s  →        1.84 s    (-1.67%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.78 ms →        9.68 ms   (-0.97%) |     182   →     182              |        1.78 s  →        1.76 s    (-0.97%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.78 ms →        9.68 ms   (-0.97%) |     182   →     182              |        1.78 s  →        1.76 s    (-0.97%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.93 ms →       10.47 ms   (-4.23%) |      78   →      78              |      852.81 ms →      816.74 ms   (-4.23%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.58 ms →       10.06 ms   (-4.92%) |      78   →      78              |      825.47 ms →      784.89 ms   (-4.92%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.92 ms →        9.92 ms   (-0.01%) |      26   →      26              |      258.02 ms →      258.00 ms   (-0.01%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      235.50 μs →      160.23 μs  (-31.96%) |      26   →      26              |        6.12 ms →        4.17 ms  (-31.96%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      230.50 μs →      155.71 μs  (-32.45%) |      26   →      26              |        5.99 ms →        4.05 ms  (-32.45%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.26 ms →        5.26 ms   (+0.10%) |       2   →       2              |       10.51 ms →       10.52 ms   (+0.10%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.76 ms →       10.13 ms   (+3.78%) |       6   →       6              |       58.57 ms →       60.78 ms   (+3.78%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.68 ms →       10.11 ms   (+4.48%) |       6   →       6              |       58.08 ms →       60.68 ms   (+4.48%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.68 ms →       10.11 ms   (+4.48%) |       6   →       6              |       58.08 ms →       60.68 ms   (+4.48%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.59 ms →       10.71 ms   (+1.15%) |       3   →       3              |       31.78 ms →       32.14 ms   (+1.15%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.47 ms →       10.70 ms   (+2.21%) |       3   →       3              |       31.42 ms →       32.11 ms   (+2.21%) | 
  ├ sirius::Periodic_function|inner                                     |        9.69 ms →       10.19 ms   (+5.11%) |       2   →       2              |       19.39 ms →       20.38 ms   (+5.11%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.69 ms →       10.10 ms   (+4.28%) |       2   →       2              |       19.37 ms →       20.20 ms   (+4.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →       10.10 ms   (+4.29%) |       2   →       2              |       19.37 ms →       20.20 ms   (+4.29%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       11.21 ms →       10.54 ms   (-5.95%) |       1   →       1              |       11.21 ms →       10.54 ms   (-5.95%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.53 ms   (+0.59%) |       1   →       1              |       10.47 ms →       10.53 ms   (+0.59%) | 
  └ sirius::finalize                                                    |      206.87 ms →      189.93 ms   (-8.19%) |       1   →       1              |      206.87 ms →      189.93 ms   (-8.19%) | 
  ====================================================================================================================================================================================================
```
