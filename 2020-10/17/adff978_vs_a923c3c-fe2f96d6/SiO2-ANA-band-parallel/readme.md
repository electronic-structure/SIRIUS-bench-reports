# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      235.33 s  →      224.54 s    (-4.59%) |       1   →       1              |      235.33 s  →      224.54 s    (-4.59%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.75 s    (-0.79%) |       1   →       1              |        2.77 s  →        2.75 s    (-0.79%) | 
  ├ sirius::Simulation_context::initialize                              |        2.89 s  →        2.93 s    (+1.13%) |       1   →       1              |        2.89 s  →        2.93 s    (+1.13%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      219.34 μs →       17.09 ms (+7693.63%) |       1   →       1              |      219.34 μs →       17.09 ms (+7693.63%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      137.38 ms →      180.25 ms  (+31.20%) |       1   →       1              |      137.38 ms →      180.25 ms  (+31.20%) | 
- │ │ ├ sirius::Atom_type::init                                         |       56.28 ms →       78.60 ms  (+39.66%) |       2   →       2              |      112.56 ms →      157.20 ms  (+39.66%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.75 ms →       22.97 ms   (-7.16%) |       1   →       1              |       24.75 ms →       22.97 ms   (-7.16%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.25 ms →        6.44 ms   (+3.03%) |       1   →       1              |        6.25 ms →        6.44 ms   (+3.03%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       18.45 ms →       16.50 ms  (-10.59%) |       1   →       1              |       18.45 ms →       16.50 ms  (-10.59%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       18.43 ms →       16.48 ms  (-10.60%) |       1   →       1              |       18.43 ms →       16.48 ms  (-10.60%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.14 ms   (-0.41%) |       1   →       1              |        4.15 ms →        4.14 ms   (-0.41%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.46%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.46%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.43 μs →      106.52 μs   (+1.03%) |       1   →       1              |      105.43 μs →      106.52 μs   (+1.03%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.68 s    (-1.05%) |       1   →       1              |        2.71 s  →        2.68 s    (-1.05%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.77 ms →       10.69 ms   (-0.75%) |       1   →       1              |       10.77 ms →       10.69 ms   (-0.75%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.34 ms →        4.27 ms   (-1.47%) |       1   →       1              |        4.34 ms →        4.27 ms   (-1.47%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.38 ms   (-0.24%) |       1   →       1              |        6.39 ms →        6.38 ms   (-0.24%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.36 ms   (-0.23%) |       1   →       1              |        6.37 ms →        6.36 ms   (-0.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.87 ms   (-0.57%) |       1   →       1              |        3.89 ms →        3.87 ms   (-0.57%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.12%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.12%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.37 μs →      102.42 μs   (+3.07%) |       1   →       1              |       99.37 μs →      102.42 μs   (+3.07%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.05 ms →       64.23 ms   (+0.29%) |       2   →       2              |      128.10 ms →      128.47 ms   (+0.29%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.19 ms →        5.15 ms   (-0.82%) |       2   →       2              |       10.38 ms →       10.29 ms   (-0.82%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.19%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.85 ms →       21.83 ms   (-0.06%) |       2   →       2              |       43.69 ms →       43.67 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.84 ms →       14.81 ms   (-0.20%) |       2   →       2              |       29.67 ms →       29.61 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.63 ms →       19.68 ms   (+0.25%) |       4   →       4              |       78.51 ms →       78.71 ms   (+0.25%) | 
  │   ├ sddk::Gvec::init                                                |      171.26 ms →      174.18 ms   (+1.71%) |       2   →       2              |      342.53 ms →      348.37 ms   (+1.71%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.22 ms →      131.59 ms   (+2.63%) |       2   →       2              |      256.45 ms →      263.18 ms   (+2.63%) | 
  │   ├ sddk::Gvec_shells                                               |      162.03 ms →      177.16 ms   (+9.34%) |       1   →       1              |      162.03 ms →      177.16 ms   (+9.34%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.37 ms   (+3.68%) |       1   →       1              |        1.32 ms →        1.37 ms   (+3.68%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      296.54 ms →      294.68 ms   (-0.62%) |       2   →       2              |      593.07 ms →      589.37 ms   (-0.62%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       86.90 ms →       75.93 ms  (-12.62%) |       1   →       1              |       86.90 ms →       75.93 ms  (-12.62%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.80 μs →        1.99 μs  (-28.84%) |       4   →       4              |       11.19 μs →        7.97 μs  (-28.84%) | 
+ │ └ sirius::K_point_set::initialize                                   |       86.80 ms →       75.83 ms  (-12.64%) |       1   →       1              |       86.80 ms →       75.83 ms  (-12.64%) | 
+ │   └ sirius::K_point::initialize                                     |       21.69 ms →       18.94 ms  (-12.69%) |       4   →       4              |       86.75 ms →       75.75 ms  (-12.69%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       16.97 ms →       14.32 ms  (-15.57%) |       4   →       4              |       67.86 ms →       57.29 ms  (-15.57%) | 
  │     │ └ sddk::Gvec::init                                            |        4.02 ms →        3.83 ms   (-4.79%) |       4   →       4              |       16.08 ms →       15.31 ms   (-4.79%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.12 μs →        9.31 μs   (+2.05%) |       4   →       4              |       36.50 μs →       37.25 μs   (+2.05%) | 
  │     └ sirius::K_point::update                                       |        3.35 ms →        3.30 ms   (-1.53%) |       4   →       4              |       13.40 ms →       13.20 ms   (-1.53%) | 
  │       └ sirius::Beta_projectors                                     |        1.74 ms →        1.78 ms   (+2.20%) |       4   →       4              |        6.97 ms →        7.12 ms   (+2.20%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      917.54 μs →      925.30 μs   (+0.85%) |       4   →       4              |        3.67 ms →        3.70 ms   (+0.85%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.37 ms   (+1.10%) |       2   →       2              |       10.62 ms →       10.73 ms   (+1.10%) | 
  ├ sirius::Potential                                                   |      158.90 ms →      157.43 ms   (-0.93%) |       1   →       1              |      158.90 ms →      157.43 ms   (-0.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.81 ms   (+0.44%) |       6   →       6              |       34.68 ms →       34.83 ms   (+0.44%) | 
  │ └ sirius::Potential::update                                         |      123.50 ms →      121.88 ms   (-1.31%) |       1   →       1              |      123.50 ms →      121.88 ms   (-1.31%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.84 ms →      121.17 ms   (-1.36%) |       1   →       1              |      122.84 ms →      121.17 ms   (-1.36%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      115.56 ms →      106.70 ms   (-7.66%) |       1   →       1              |      115.56 ms →      106.70 ms   (-7.66%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.42 ms →       13.58 ms (+111.58%) |       1   →       1              |        6.42 ms →       13.58 ms (+111.58%) | 
  ├ sirius::Density                                                     |      136.71 ms →      134.51 ms   (-1.61%) |       1   →       1              |      136.71 ms →      134.51 ms   (-1.61%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.22 ms →        5.20 ms   (-0.44%) |       2   →       2              |       10.44 ms →       10.40 ms   (-0.44%) | 
  │ └ sirius::Density::update                                           |      126.00 ms →      123.85 ms   (-1.71%) |       1   →       1              |      126.00 ms →      123.85 ms   (-1.71%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.56 ms →      123.38 ms   (-1.74%) |       1   →       1              |      125.56 ms →      123.38 ms   (-1.74%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      126.65 μs →      111.39 μs  (-12.05%) |       1   →       1              |      126.65 μs →      111.39 μs  (-12.05%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      119.76 ms →      109.59 ms   (-8.49%) |       1   →       1              |      119.76 ms →      109.59 ms   (-8.49%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.23 ms →       13.23 ms (+153.01%) |       1   →       1              |        5.23 ms →       13.23 ms (+153.01%) | 
  ├ sirius::Density::initial_density                                    |      176.71 ms →      178.12 ms   (+0.80%) |       1   →       1              |      176.71 ms →      178.12 ms   (+0.80%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      124.02 ms →      108.25 ms  (-12.71%) |       1   →       1              |      124.02 ms →      108.25 ms  (-12.71%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.03 ms →       12.48 ms (+147.85%) |       2   →       2              |       10.07 ms →       24.96 ms (+147.85%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.17 ms →       12.48 ms  (+22.72%) |       1   →       1              |       10.17 ms →       12.48 ms  (+22.72%) | 
  ├ sirius::Potential::generate                                         |      593.54 ms →      590.00 ms   (-0.60%) |       1   →       1              |      593.54 ms →      590.00 ms   (-0.60%) | 
  │ ├ sirius::Potential::poisson                                        |      137.70 ms →      136.43 ms   (-0.92%) |       1   →       1              |      137.70 ms →      136.43 ms   (-0.92%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.30 ms →       18.70 ms (+252.56%) |       1   →       1              |        5.30 ms →       18.70 ms (+252.56%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.94 ms →        9.93 ms   (-0.10%) |       1   →       1              |        9.94 ms →        9.93 ms   (-0.10%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.92 ms →        9.88 ms   (-0.35%) |       1   →       1              |        9.92 ms →        9.88 ms   (-0.35%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.91 ms →        9.88 ms   (-0.35%) |       1   →       1              |        9.91 ms →        9.88 ms   (-0.35%) | 
  │ ├ sirius::Periodic_function::add                                    |      551.85 μs →      562.48 μs   (+1.93%) |       2   →       2              |        1.10 ms →        1.12 ms   (+1.93%) | 
  │ ├ sirius::Potential::xc                                             |       55.81 ms →       53.67 ms   (-3.83%) |       1   →       1              |       55.81 ms →       53.67 ms   (-3.83%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.46 ms →       51.33 ms   (-3.99%) |       1   →       1              |       53.46 ms →       51.33 ms   (-3.99%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        6.21 ms →        5.70 ms   (-8.11%) |       2   →       2              |       12.41 ms →       11.41 ms   (-8.11%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms →        5.14 ms   (-2.16%) |       1   →       1              |        5.26 ms →        5.14 ms   (-2.16%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.73 ms →        5.76 ms   (+0.44%) |       1   →       1              |        5.73 ms →        5.76 ms   (+0.44%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.59 ms →       92.62 ms   (+0.04%) |       1   →       1              |       92.59 ms →       92.62 ms   (+0.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.21 ms →      299.02 ms   (-0.06%) |       1   →       1              |      299.21 ms →      299.02 ms   (-0.06%) | 
  ├ sirius::Hamiltonian0                                                |        8.39 ms →        8.41 ms   (+0.31%) |       1   →       1              |        8.39 ms →        8.41 ms   (+0.31%) | 
  │ ├ sirius::Local_operator                                            |        8.04 ms →        8.07 ms   (+0.35%) |       1   →       1              |        8.04 ms →        8.07 ms   (+0.35%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.75 ms   (-0.11%) |       1   →       1              |        4.75 ms →        4.75 ms   (-0.11%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        2.39 ms   (+0.67%) |       1   →       1              |        2.38 ms →        2.39 ms   (+0.67%) | 
  │ ├ sirius::Non_local_operator                                        |       63.34 μs →       60.10 μs   (-5.12%) |       2   →       2              |      126.69 μs →      120.20 μs   (-5.12%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.25 μs →       95.98 μs   (+1.84%) |       1   →       1              |       94.25 μs →       95.98 μs   (+1.84%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.14 μs →       68.37 μs   (+0.34%) |       1   →       1              |       68.14 μs →       68.37 μs   (+0.34%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.14 s    (+1.09%) |       1   →       1              |        3.11 s  →        3.14 s    (+1.09%) | 
  │ ├ sirius::Hamiltonian_k                                             |      369.93 μs →      370.76 μs   (+0.23%) |       4   →       4              |        1.48 ms →        1.48 ms   (+0.23%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      364.52 μs →      365.82 μs   (+0.36%) |       4   →       4              |        1.46 ms →        1.46 ms   (+0.36%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.64 μs →        3.36 μs   (-7.83%) |       4   →       4              |       14.57 μs →       13.43 μs   (-7.83%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      776.83 ms →      785.34 ms   (+1.10%) |       4   →       4              |        3.11 s  →        3.14 s    (+1.10%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       33.09 ms →       32.72 ms   (-1.14%) |      16   →      16              |      529.52 ms →      523.48 ms   (-1.14%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.63 ms →       14.62 ms   (-0.06%) |       4   →       4              |       58.51 ms →       58.47 ms   (-0.06%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.45 ms →        5.39 ms   (-1.16%) |       4   →       4              |       21.81 ms →       21.55 ms   (-1.16%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      358.27 ms →      354.34 ms   (-1.10%) |       4   →       4              |        1.43 s  →        1.42 s    (-1.10%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      262.05 ms →      257.40 ms   (-1.77%) |       4   →       4              |        1.05 s  →        1.03 s    (-1.77%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       65.45 ms →       62.44 ms   (-4.60%) |       4   →       4              |      261.79 ms →      249.75 ms   (-4.60%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.64 ms →       16.61 ms   (-0.14%) |       4   →       4              |       66.54 ms →       66.45 ms   (-0.14%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.63 ms →       16.61 ms   (-0.14%) |       4   →       4              |       66.53 ms →       66.44 ms   (-0.14%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       42.37 ms →       39.46 ms   (-6.86%) |       4   →       4              |      169.46 ms →      157.84 ms   (-6.86%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       18.07 ms →       16.37 ms   (-9.43%) |       4   →       4              |       72.28 ms →       65.47 ms   (-9.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       18.07 ms →       16.36 ms   (-9.43%) |       4   →       4              |       72.27 ms →       65.46 ms   (-9.43%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.36 ms →       54.47 ms   (+2.08%) |       4   →       4              |      213.46 ms →      217.89 ms   (+2.08%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.38 ms →       36.49 ms   (+3.13%) |       4   →       4              |      141.51 ms →      145.94 ms   (+3.13%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.95 ms   (+0.89%) |       4   →       4              |        7.75 ms →        7.82 ms   (+0.89%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.05 ms →       40.68 ms   (+1.57%) |       4   →       4              |      160.21 ms →      162.72 ms   (+1.57%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        6.95 ms →        7.59 ms   (+9.15%) |       4   →       4              |       27.81 ms →       30.35 ms   (+9.15%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.10 ms →       27.13 ms   (+0.13%) |       8   →       8              |      216.77 ms →      217.05 ms   (+0.13%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.86 ms →       15.35 ms   (+3.30%) |       8   →       8              |      118.86 ms →      122.78 ms   (+3.30%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.81 ms →       15.30 ms   (+3.28%) |       8   →       8              |      118.51 ms →      122.40 ms   (+3.28%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       27.25 ns →       34.12 ns  (+25.23%) |       8   →       8              |      218.00 ns →      273.00 ns  (+25.23%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.63 ms →       15.11 ms   (+3.26%) |       8   →       8              |      117.06 ms →      120.88 ms   (+3.26%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       23.75 ns →       34.12 ns  (+43.68%) |       8   →       8              |      190.00 ns →      273.00 ns  (+43.68%) | 
- │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      117.13 ms →      130.08 ms  (+11.06%) |       4   →       4              |      468.52 ms →      520.32 ms  (+11.06%) | 
  │ │ └ sddk::wf_trans                                                  |       23.53 ms →       23.67 ms   (+0.59%) |       4   →       4              |       94.13 ms →       94.68 ms   (+0.59%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.30 ms →       23.36 ms   (+0.29%) |       4   →       4              |       93.18 ms →       93.45 ms   (+0.29%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      383.25 ns →      390.75 ns   (+1.96%) |       4   →       4              |        1.53 μs →        1.56 μs   (+1.96%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      224.58 s  →      213.72 s    (-4.84%) |       1   →       1              |      224.58 s  →      213.72 s    (-4.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.71 ms →        5.82 ms   (+2.09%) |      19   →      19              |      108.40 ms →      110.67 ms   (+2.09%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.97 s  →        7.90 s   (-11.90%) |      25   →      27     (+8.00%) |      224.21 s  →      213.33 s    (-4.85%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.67 ms →        4.51 ms   (-3.43%) |      25   →      27     (+8.00%) |      116.69 ms →      121.70 ms   (+4.29%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.30 ms →        4.15 ms   (-3.55%) |      25   →      27     (+8.00%) |      107.60 ms →      112.09 ms   (+4.17%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      984.73 μs →      960.19 μs   (-2.49%) |      25   →      27     (+8.00%) |       24.62 ms →       25.93 ms   (+5.31%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.43 ms →        2.30 ms   (-5.40%) |      25   →      27     (+8.00%) |       60.78 ms →       62.10 ms   (+2.17%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.40 μs →       64.91 μs   (+0.79%) |      50   →      54     (+8.00%) |        3.22 ms →        3.51 ms   (+8.86%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.52 μs →       92.45 μs   (-2.19%) |      25   →      27     (+8.00%) |        2.36 ms →        2.50 ms   (+5.64%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.68 μs →       66.28 μs   (-0.61%) |      25   →      27     (+8.00%) |        1.67 ms →        1.79 ms   (+7.34%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.87 s  →        5.81 s   (-15.36%) |      25   →      27     (+8.00%) |      171.71 s  →      156.97 s    (-8.58%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      334.59 μs →      324.29 μs   (-3.08%) |     100   →     108     (+8.00%) |       33.46 ms →       35.02 ms   (+4.67%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      328.95 μs →      318.99 μs   (-3.03%) |     100   →     108     (+8.00%) |       32.90 ms →       34.45 ms   (+4.73%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.12 μs →        3.82 μs   (-7.32%) |     100   →     108     (+8.00%) |      412.15 μs →      412.55 μs   (+0.10%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.72 s  →        1.45 s   (-15.36%) |     100   →     108     (+8.00%) |      171.67 s  →      156.93 s    (-8.59%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.96 ms →       11.95 ms   (-0.04%) |     100   →     108     (+8.00%) |        1.20 s  →        1.29 s    (+7.96%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      697.45 ns →      740.03 ns   (+6.11%) |     600   →     648     (+8.00%) |      418.47 μs →      479.54 μs  (+14.59%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.82 ms   (-0.70%) |     100   →     108     (+8.00%) |      183.60 ms →      196.90 ms   (+7.24%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      353.99 μs →      354.18 μs   (+0.05%) |     100   →     108     (+8.00%) |       35.40 ms →       38.25 ms   (+8.06%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.07 μs →      548.16 μs   (-0.35%) |     200   →     216     (+8.00%) |      110.01 ms →      118.40 ms   (+7.62%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.69 s  →        1.43 s   (-15.57%) |     100   →     108     (+8.00%) |      169.39 s  →      154.46 s    (-8.81%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.99 ms →       68.19 ms   (-1.16%) |     901   →     976     (+8.32%) |       62.16 s  →       66.55 s    (+7.07%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.09 ms →       43.44 ms   (-1.47%) |     901   →     976     (+8.32%) |       39.72 s  →       42.40 s    (+6.73%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.56 ms →        8.60 ms   (+0.53%) |     901   →     976     (+8.32%) |        7.71 s  →        8.39 s    (+8.90%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      233.89 μs →      218.70 μs   (-6.49%) |     901   →     976     (+8.32%) |      210.73 ms →      213.45 ms   (+1.29%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.09 ms →        1.96 ms   (-6.22%) |     100   →     108     (+8.00%) |      208.96 ms →      211.64 ms   (+1.28%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.76 ms →        6.64 ms   (-1.71%) |     901   →     976     (+8.32%) |        6.09 s  →        6.48 s    (+6.47%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       89.35 μs →       84.26 μs   (-5.69%) |     901   →     976     (+8.32%) |       80.50 ms →       82.24 ms   (+2.16%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      780.60 μs →      738.39 μs   (-5.41%) |     100   →     108     (+8.00%) |       78.06 ms →       79.75 ms   (+2.16%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.72 ms →        9.51 ms   (-2.20%) |     901   →     976     (+8.32%) |        8.76 s  →        9.28 s    (+5.94%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.11 ms →        5.98 ms   (-2.19%) |     901   →     976     (+8.32%) |        5.51 s  →        5.84 s    (+5.95%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (+0.05%) |     901   →     976     (+8.32%) |        1.37 s  →        1.48 s    (+8.38%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.54 ms →        8.53 ms   (-0.08%) |     901   →     976     (+8.32%) |        7.69 s  →        8.33 s    (+8.24%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.25 ms →        1.40 ms  (+11.41%) |     901   →     976     (+8.32%) |        1.13 s  →        1.36 s   (+20.68%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.41 ms →        7.34 ms   (-0.99%) |    1.80 K →    1.95 K   (+8.32%) |       13.35 s  →       14.32 s    (+7.26%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.71 ms →       26.80 ms   (-3.26%) |     901   →     976     (+8.32%) |       24.97 s  →       26.16 s    (+4.79%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.00 ms →        1.98 ms   (-0.99%) |    1.70 K →    1.84 K   (+8.34%) |        3.40 s  →        3.65 s    (+7.27%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       65.44 ns →       70.24 ns   (+7.34%) |    1.70 K →    1.84 K   (+8.34%) |      111.37 μs →      129.52 μs  (+16.29%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.99 ms →        1.97 ms   (-1.14%) |    1.70 K →    1.84 K   (+8.34%) |        3.39 s  →        3.63 s    (+7.11%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       60.77 ns →       67.05 ns  (+10.34%) |    1.70 K →    1.84 K   (+8.34%) |      103.43 μs →      123.64 μs  (+19.54%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      810.40 μs →      821.64 μs   (+1.39%) |     901   →     976     (+8.32%) |      730.17 ms →      801.92 ms   (+9.83%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      749.50 μs →      790.44 μs   (+5.46%) |     901   →     976     (+8.32%) |      675.30 ms →      771.47 ms  (+14.24%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.36 ms →        5.12 ms   (-4.46%) |    3.50 K →    3.80 K   (+8.33%) |       18.78 s  →       19.44 s    (+3.50%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.65 ms →        3.48 ms   (-4.72%) |    5.11 K →    5.53 K   (+8.34%) |       18.62 s  →       19.23 s    (+3.23%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.40 ms →        5.29 ms   (-2.09%) |     901   →     976     (+8.32%) |        4.87 s  →        5.16 s    (+6.06%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.69 ms →        3.57 ms   (-3.24%) |     901   →     976     (+8.32%) |        3.33 s  →        3.49 s    (+4.82%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       50.04 ns →       55.31 ns  (+10.53%) |     901   →     976     (+8.32%) |       45.09 μs →       53.98 μs  (+19.73%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.68 ms →        3.56 ms   (-3.30%) |     901   →     976     (+8.32%) |        3.32 s  →        3.47 s    (+4.75%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       52.95 ns →       50.79 ns   (-4.08%) |     901   →     976     (+8.32%) |       47.71 μs →       49.57 μs   (+3.91%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       63.77 ms →       35.32 ms  (-44.62%) |     901   →     976     (+8.32%) |       57.45 s  →       34.47 s   (-40.01%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.51 ms →        9.81 ms   (-6.64%) |     880   →     948     (+7.73%) |        9.25 s  →        9.30 s    (+0.57%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.15 ms →        9.35 ms   (-7.89%) |     835   →     906     (+8.50%) |        8.47 s  →        8.47 s    (-0.06%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.05 ms →        4.64 ms   (-8.14%) |    1.67 K →    1.81 K   (+8.50%) |        8.43 s  →        8.40 s    (-0.33%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      625.43 μs →      638.82 μs   (+2.14%) |     835   →     906     (+8.50%) |      522.23 ms →      578.77 ms  (+10.83%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       52.04 ms →       36.55 ms  (-29.75%) |     205   →     350    (+70.73%) |       10.67 s  →       12.79 s   (+19.93%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.30 ms →       21.49 ms  (-37.35%) |     310   →     592    (+90.97%) |       10.63 s  →       12.72 s   (+19.63%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.49 ms →       15.16 ms  (-40.55%) |     415   →     834   (+100.96%) |       10.58 s  →       12.64 s   (+19.48%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      553.67 ns →      482.05 ns  (-12.94%) |     100   →     108     (+8.00%) |       55.37 μs →       52.06 μs   (-5.97%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.21 μs →       21.68 μs   (+2.23%) |      25   →      27     (+8.00%) |      530.27 μs →      585.46 μs  (+10.41%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      592.39 μs →      594.09 μs   (+0.29%) |      25   →      27     (+8.00%) |       14.81 ms →       16.04 ms   (+8.31%) | 
  │ │ ├ sirius::Density::generate                                       |      894.67 ms →      895.33 ms   (+0.07%) |      25   →      27     (+8.00%) |       22.37 s  →       24.17 s    (+8.08%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      524.66 ms →      525.88 ms   (+0.23%) |      25   →      27     (+8.00%) |       13.12 s  →       14.20 s    (+8.25%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.53 ms →       24.47 ms   (-0.24%) |     100   →     108     (+8.00%) |        2.45 s  →        2.64 s    (+7.74%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.78 μs →        8.62 μs   (-1.71%) |     100   →     108     (+8.00%) |      877.53 μs →      931.49 μs   (+6.15%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.54 μs →       15.43 μs   (-0.67%) |       8   →       8              |      124.32 μs →      123.48 μs   (-0.67%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.39 ms →       20.36 ms   (-0.17%) |     100   →     108     (+8.00%) |        2.04 s  →        2.20 s    (+7.82%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.63 ms →       30.15 ms   (+1.77%) |     100   →     108     (+8.00%) |        2.96 s  →        3.26 s    (+9.91%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.65 μs →        9.43 μs   (-2.23%) |     100   →     108     (+8.00%) |      964.84 μs →        1.02 ms   (+5.59%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.49%) |     100   →     108     (+8.00%) |      144.93 ms →      157.28 ms   (+8.53%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.70 ms →       28.22 ms   (+1.87%) |     100   →     108     (+8.00%) |        2.77 s  →        3.05 s   (+10.01%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.58 ms →        4.09 ms  (+14.38%) |     100   →     108     (+8.00%) |      357.58 ms →      441.73 ms  (+23.53%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      669.28 ns →      517.91 ns  (-22.62%) |     100   →     108     (+8.00%) |       66.93 μs →       55.93 μs  (-16.43%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.74 ms →       42.43 ms   (-0.71%) |     100   →     108     (+8.00%) |        4.27 s  →        4.58 s    (+7.23%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.08%) |      25   →      27     (+8.00%) |       41.03 ms →       44.34 ms   (+8.09%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       89.00 ms →       88.86 ms   (-0.16%) |      25   →      27     (+8.00%) |        2.22 s  →        2.40 s    (+7.83%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.75 ms →       88.63 ms   (-0.14%) |      25   →      27     (+8.00%) |        2.22 s  →        2.39 s    (+7.85%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.34 ms →      276.49 ms   (-0.31%) |      25   →      27     (+8.00%) |        6.93 s  →        7.47 s    (+7.67%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.34 ms →      276.48 ms   (-0.31%) |      25   →      27     (+8.00%) |        6.93 s  →        7.47 s    (+7.67%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.30 ms →       24.62 ms   (+1.32%) |      25   →      27     (+8.00%) |      607.55 ms →      664.83 ms   (+9.43%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.57 ms →      225.80 ms   (-0.78%) |      25   →      27     (+8.00%) |        5.69 s  →        6.10 s    (+7.16%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.69 ms →       24.29 ms   (+2.54%) |      25   →      27     (+8.00%) |      592.19 ms →      655.83 ms  (+10.75%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.46 ms →       81.84 ms   (+1.71%) |      25   →      27     (+8.00%) |        2.01 s  →        2.21 s    (+9.85%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.61 ms →        7.53 ms  (-12.55%) |      25   →      27     (+8.00%) |      215.21 ms →      203.25 ms   (-5.56%) | 
  │ │ ├ sirius::Density::mix                                            |      218.01 ms →      208.29 ms   (-4.46%) |      25   →      27     (+8.00%) |        5.45 s  →        5.62 s    (+3.18%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      938.10 μs →      962.09 μs   (+2.56%) |      25   →      27     (+8.00%) |       23.45 ms →       25.98 ms  (+10.76%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.74 ms →       10.35 ms   (-3.60%) |     319   →     335     (+5.02%) |        3.42 s  →        3.47 s    (+1.23%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.35 ms →        9.98 ms   (-3.55%) |     319   →     335     (+5.02%) |        3.30 s  →        3.34 s    (+1.29%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.35 ms →        9.98 ms   (-3.55%) |     319   →     335     (+5.02%) |        3.30 s  →        3.34 s    (+1.29%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.19 ms →        6.30 ms  (-12.30%) |      25   →      27     (+8.00%) |      179.72 ms →      170.21 ms   (-5.29%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.33 ms →        5.50 ms  (-13.25%) |      25   →      27     (+8.00%) |      158.37 ms →      148.39 ms   (-6.31%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.28 ms →      578.72 ms   (-0.27%) |      25   →      27     (+8.00%) |       14.51 s  →       15.63 s    (+7.71%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.13 ms →      136.97 ms   (-0.84%) |      25   →      27     (+8.00%) |        3.45 s  →        3.70 s    (+7.09%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.23 ms →       18.73 ms (+258.25%) |      25   →      27     (+8.00%) |      130.72 ms →      505.79 ms (+286.92%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.27 ms →       10.36 ms   (+0.79%) |      25   →      27     (+8.00%) |      256.86 ms →      279.60 ms   (+8.85%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.94 ms →       10.02 ms   (+0.82%) |      25   →      27     (+8.00%) |      248.51 ms →      270.58 ms   (+8.88%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.94 ms →       10.02 ms   (+0.82%) |      25   →      27     (+8.00%) |      248.49 ms →      270.57 ms   (+8.88%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      558.60 μs →      558.46 μs   (-0.03%) |      50   →      54     (+8.00%) |       27.93 ms →       30.16 ms   (+7.97%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.05 ms →       49.06 ms   (+0.02%) |      25   →      27     (+8.00%) |        1.23 s  →        1.32 s    (+8.02%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.67 ms →       46.75 ms   (+0.17%) |      25   →      27     (+8.00%) |        1.17 s  →        1.26 s    (+8.19%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.07 ms →        2.98 ms   (-3.00%) |      50   →      54     (+8.00%) |      153.70 ms →      161.02 ms   (+4.77%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.37 ms →        5.37 ms   (+0.09%) |      25   →      27     (+8.00%) |      134.19 ms →      145.06 ms   (+8.10%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.69 ms →        6.60 ms   (-1.35%) |      25   →      27     (+8.00%) |      167.25 ms →      178.20 ms   (+6.54%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.94 ms   (+0.06%) |      25   →      27     (+8.00%) |        2.27 s  →        2.46 s    (+8.07%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.06 ms →      292.76 ms   (-0.10%) |      25   →      27     (+8.00%) |        7.33 s  →        7.90 s    (+7.89%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.35 ms →      280.59 ms   (-0.27%) |      25   →      27     (+8.00%) |        7.03 s  →        7.58 s    (+7.71%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.35 ms →      280.59 ms   (-0.27%) |      25   →      27     (+8.00%) |        7.03 s  →        7.58 s    (+7.71%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.22 ms →       27.01 ms   (-0.75%) |      25   →      27     (+8.00%) |      680.38 ms →      729.30 ms   (+7.19%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.70 ms →      226.02 ms   (-0.30%) |      25   →      27     (+8.00%) |        5.67 s  →        6.10 s    (+7.67%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.63 ms →       23.78 ms   (+0.63%) |      25   →      27     (+8.00%) |      590.64 ms →      641.93 ms   (+8.68%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.58 ms →        5.46 ms   (-2.27%) |      25   →      27     (+8.00%) |      139.55 ms →      147.29 ms   (+5.55%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.27 ms →       10.29 ms   (+0.16%) |     175   →     189     (+8.00%) |        1.80 s  →        1.94 s    (+8.17%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.84 ms →        9.94 ms   (+1.04%) |     175   →     189     (+8.00%) |        1.72 s  →        1.88 s    (+9.13%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.84 ms →        9.94 ms   (+1.04%) |     175   →     189     (+8.00%) |        1.72 s  →        1.88 s    (+9.13%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.00 ms →       10.60 ms   (-3.67%) |      75   →      81     (+8.00%) |      825.18 ms →      858.52 ms   (+4.04%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.64 ms →       10.30 ms   (-3.22%) |      75   →      81     (+8.00%) |      798.09 ms →      834.19 ms   (+4.52%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.96 ms →       10.02 ms   (+0.65%) |      25   →      27     (+8.00%) |      248.93 ms →      270.59 ms   (+8.70%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      113.05 μs →      119.57 μs   (+5.77%) |      25   →      27     (+8.00%) |        2.83 ms →        3.23 ms  (+14.23%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      108.09 μs →      114.49 μs   (+5.93%) |      25   →      27     (+8.00%) |        2.70 ms →        3.09 ms  (+14.40%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.11 ms →        5.50 ms   (+7.75%) |       2   →       2              |       10.21 ms →       11.00 ms   (+7.75%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.10 ms →        9.81 ms   (-2.90%) |       6   →       6              |       60.60 ms →       58.84 ms   (-2.90%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.09 ms →        9.74 ms   (-3.42%) |       6   →       6              |       60.53 ms →       58.46 ms   (-3.42%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.09 ms →        9.74 ms   (-3.43%) |       6   →       6              |       60.53 ms →       58.45 ms   (-3.43%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.81 ms →       10.28 ms   (-4.84%) |       3   →       3              |       32.42 ms →       30.85 ms   (-4.84%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.80 ms →       10.11 ms   (-6.35%) |       3   →       3              |       32.39 ms →       30.34 ms   (-6.35%) | 
  ├ sirius::Periodic_function|inner                                     |       10.13 ms →        9.73 ms   (-3.93%) |       2   →       2              |       20.26 ms →       19.46 ms   (-3.93%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.12 ms →        9.61 ms   (-5.03%) |       2   →       2              |       20.24 ms →       19.22 ms   (-5.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.12 ms →        9.61 ms   (-5.03%) |       2   →       2              |       20.24 ms →       19.22 ms   (-5.03%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.98 ms →       10.23 ms   (-6.83%) |       1   →       1              |       10.98 ms →       10.23 ms   (-6.83%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.97 ms →       10.09 ms   (-8.05%) |       1   →       1              |       10.97 ms →       10.09 ms   (-8.05%) | 
- └ sirius::finalize                                                    |      288.75 ms →      330.04 ms  (+14.30%) |       1   →       1              |      288.75 ms →      330.04 ms  (+14.30%) | 
  ====================================================================================================================================================================================================
```
