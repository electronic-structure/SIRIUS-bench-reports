# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      145.01 s  →      131.84 s    (-9.09%) |       1   →       1              |      145.01 s  →      131.84 s    (-9.09%) | 
  ├ sirius::initialize                                                  |        2.79 s  →        2.73 s    (-2.14%) |       1   →       1              |        2.79 s  →        2.73 s    (-2.14%) | 
  ├ sirius::Simulation_context::initialize                              |        2.07 s  →        2.22 s    (+7.36%) |       1   →       1              |        2.07 s  →        2.22 s    (+7.36%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       13.93 ms →       16.83 ms  (+20.79%) |       1   →       1              |       13.93 ms →       16.83 ms  (+20.79%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       69.80 ms →      191.58 ms (+174.47%) |       1   →       1              |       69.80 ms →      191.58 ms (+174.47%) | 
- │ │ ├ sirius::Atom_type::init                                         |       43.22 ms →      166.20 ms (+284.51%) |       1   →       1              |       43.22 ms →      166.20 ms (+284.51%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.51 ms →       25.31 ms   (-4.53%) |       1   →       1              |       26.51 ms →       25.31 ms   (-4.53%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.72 ms →       10.32 ms   (-3.72%) |       1   →       1              |       10.72 ms →       10.32 ms   (-3.72%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.77 ms →       14.95 ms   (-5.18%) |       1   →       1              |       15.77 ms →       14.95 ms   (-5.18%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.46 ms →       14.53 ms   (-6.04%) |       1   →       1              |       15.46 ms →       14.53 ms   (-6.04%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       15.23 ms →       14.31 ms   (-6.02%) |       1   →       1              |       15.23 ms →       14.31 ms   (-6.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      222.89 μs →      206.21 μs   (-7.48%) |       1   →       1              |      222.89 μs →      206.21 μs   (-7.48%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.32 μs →        2.29 μs   (-0.95%) |       1   →       1              |        2.32 μs →        2.29 μs   (-0.95%) | 
  │ └ sirius::Simulation_context::update                                |        1.93 s  →        1.96 s    (+1.48%) |       1   →       1              |        1.93 s  →        1.96 s    (+1.48%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.67 ms →       12.80 ms   (+1.07%) |       1   →       1              |       12.67 ms →       12.80 ms   (+1.07%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.24 ms →        8.23 ms   (-0.14%) |       1   →       1              |        8.24 ms →        8.23 ms   (-0.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.40 ms →        4.55 ms   (+3.37%) |       1   →       1              |        4.40 ms →        4.55 ms   (+3.37%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.10 ms →        4.13 ms   (+0.86%) |       1   →       1              |        4.10 ms →        4.13 ms   (+0.86%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.93 ms   (+0.93%) |       1   →       1              |        3.89 ms →        3.93 ms   (+0.93%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      204.12 μs →      203.42 μs   (-0.34%) |       1   →       1              |      204.12 μs →      203.42 μs   (-0.34%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.32 μs →        1.23 μs   (-6.61%) |       1   →       1              |        1.32 μs →        1.23 μs   (-6.61%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       14.96 ms →       32.82 ms (+119.36%) |       2   →       2              |       29.92 ms →       65.64 ms (+119.36%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.17 ms →        1.10 ms   (-6.12%) |       2   →       2              |        2.33 ms →        2.19 ms   (-6.12%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      954.91 μs →        1.01 ms   (+6.22%) |       1   →       1              |      954.91 μs →        1.01 ms   (+6.22%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.12 ms →        5.06 ms   (-1.13%) |       2   →       2              |       10.24 ms →       10.13 ms   (-1.13%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.76 ms   (+2.97%) |       2   →       2              |        7.30 ms →        7.51 ms   (+2.97%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.61 ms →       15.77 ms   (+0.99%) |       4   →       4              |       62.46 ms →       63.07 ms   (+0.99%) | 
  │   ├ sddk::Gvec::init                                                |      162.76 ms →      157.44 ms   (-3.27%) |       2   →       2              |      325.52 ms →      314.89 ms   (-3.27%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.04 ms →      124.37 ms   (-2.87%) |       2   →       2              |      256.07 ms →      248.73 ms   (-2.87%) | 
+ │   ├ sddk::Gvec_shells                                               |      145.97 ms →      122.66 ms  (-15.97%) |       1   →       1              |      145.97 ms →      122.66 ms  (-15.97%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.06 ms   (+2.92%) |       1   →       1              |        1.03 ms →        1.06 ms   (+2.92%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      227.96 ms →      218.31 ms   (-4.23%) |       1   →       1              |      227.96 ms →      218.31 ms   (-4.23%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       28.73 ms →       25.75 ms  (-10.38%) |       1   →       1              |       28.73 ms →       25.75 ms  (-10.38%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.06 μs →        1.70 μs  (-17.47%) |       2   →       2              |        4.12 μs →        3.40 μs  (-17.47%) | 
+ │ └ sirius::K_point_set::initialize                                   |       28.71 ms →       25.71 ms  (-10.42%) |       1   →       1              |       28.71 ms →       25.71 ms  (-10.42%) | 
+ │   └ sirius::K_point::initialize                                     |       28.65 ms →       25.66 ms  (-10.42%) |       1   →       1              |       28.65 ms →       25.66 ms  (-10.42%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       21.62 ms →       19.28 ms  (-10.82%) |       1   →       1              |       21.62 ms →       19.28 ms  (-10.82%) | 
  │     │ └ sddk::Gvec::init                                            |        5.37 ms →        5.03 ms   (-6.27%) |       1   →       1              |        5.37 ms →        5.03 ms   (-6.27%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.11 μs →       10.85 μs   (-2.37%) |       1   →       1              |       11.11 μs →       10.85 μs   (-2.37%) | 
  │     └ sirius::K_point::update                                       |        4.39 ms →        4.11 ms   (-6.31%) |       1   →       1              |        4.39 ms →        4.11 ms   (-6.31%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.71 ms   (-0.65%) |       1   →       1              |        1.72 ms →        1.71 ms   (-0.65%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      916.68 μs →      895.02 μs   (-2.36%) |       1   →       1              |      916.68 μs →      895.02 μs   (-2.36%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.22 ms →        1.49 ms  (-32.84%) |       2   →       2              |        4.44 ms →        2.98 ms  (-32.84%) | 
  ├ sirius::Potential                                                   |       89.10 ms →       89.59 ms   (+0.54%) |       1   →       1              |       89.10 ms →       89.59 ms   (+0.54%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.49 ms   (+0.84%) |       6   →       6              |       14.80 ms →       14.93 ms   (+0.84%) | 
  │ └ sirius::Potential::update                                         |       73.98 ms →       74.31 ms   (+0.45%) |       1   →       1              |       73.98 ms →       74.31 ms   (+0.45%) | 
  │   └ sirius::Potential::generate_local_potential                     |       73.80 ms →       74.14 ms   (+0.45%) |       1   →       1              |       73.80 ms →       74.14 ms   (+0.45%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       54.50 ms →       51.45 ms   (-5.59%) |       1   →       1              |       54.50 ms →       51.45 ms   (-5.59%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       19.12 ms →       13.77 ms  (-27.97%) |       1   →       1              |       19.12 ms →       13.77 ms  (-27.97%) | 
  ├ sirius::Density                                                     |       71.54 ms →       76.69 ms   (+7.20%) |       1   →       1              |       71.54 ms →       76.69 ms   (+7.20%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.76 ms →        4.83 ms   (+1.50%) |       2   →       2              |        9.53 ms →        9.67 ms   (+1.50%) | 
  │ └ sirius::Density::update                                           |       61.90 ms →       66.91 ms   (+8.09%) |       1   →       1              |       61.90 ms →       66.91 ms   (+8.09%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.73 ms →       66.74 ms   (+8.12%) |       1   →       1              |       61.73 ms →       66.74 ms   (+8.12%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.15 ms            |                   1              |                         3.15 ms            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       54.16 ms →       52.53 ms   (-3.01%) |       1   →       1              |       54.16 ms →       52.53 ms   (-3.01%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        7.37 ms →        9.79 ms  (+32.87%) |       1   →       1              |        7.37 ms →        9.79 ms  (+32.87%) | 
  ├ sirius::Density::initial_density                                    |       79.10 ms →       78.75 ms   (-0.45%) |       1   →       1              |       79.10 ms →       78.75 ms   (-0.45%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.41 ms →       52.73 ms   (-1.27%) |       1   →       1              |       53.41 ms →       52.73 ms   (-1.27%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.86 ms →        5.15 ms   (+5.95%) |       2   →       2              |        9.73 ms →       10.31 ms   (+5.95%) | 
+ │ └ sirius::Periodic_function::integrate                              |        4.35 ms →        3.91 ms  (-10.05%) |       1   →       1              |        4.35 ms →        3.91 ms  (-10.05%) | 
  ├ sirius::Potential::generate                                         |      192.22 ms →      186.94 ms   (-2.75%) |       1   →       1              |      192.22 ms →      186.94 ms   (-2.75%) | 
  │ ├ sirius::Potential::poisson                                        |       63.86 ms →       63.62 ms   (-0.37%) |       1   →       1              |       63.86 ms →       63.62 ms   (-0.37%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.99 ms →        9.56 ms   (+6.32%) |       1   →       1              |        8.99 ms →        9.56 ms   (+6.32%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.14 ms →        4.15 ms   (+0.29%) |       1   →       1              |        4.14 ms →        4.15 ms   (+0.29%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.04 ms →        4.14 ms   (+2.29%) |       1   →       1              |        4.04 ms →        4.14 ms   (+2.29%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.04 ms →        4.14 ms   (+2.29%) |       1   →       1              |        4.04 ms →        4.14 ms   (+2.29%) | 
  │ ├ sirius::Periodic_function::add                                    |      241.15 μs →      233.02 μs   (-3.37%) |       2   →       2              |      482.29 μs →      466.04 μs   (-3.37%) | 
  │ ├ sirius::Potential::xc                                             |      101.71 ms →       96.86 ms   (-4.77%) |       1   →       1              |      101.71 ms →       96.86 ms   (-4.77%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      101.71 ms →       95.82 ms   (-5.79%) |       1   →       1              |      101.71 ms →       95.82 ms   (-5.79%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.29 ms →        2.02 ms  (-11.88%) |       5   →       5              |       11.44 ms →       10.08 ms  (-11.88%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.69 ms →        2.43 ms   (-9.47%) |       9   →       9              |       24.18 ms →       21.89 ms   (-9.47%) | 
  │ │   ├ sirius::gradient                                              |        7.62 ms →        7.65 ms   (+0.40%) |       1   →       1              |        7.62 ms →        7.65 ms   (+0.40%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.45 ms →        2.46 ms   (+0.24%) |       3   →       3              |        7.35 ms →        7.37 ms   (+0.24%) | 
  │ │   ├ sirius::dot                                                   |        2.82 ms →        2.89 ms   (+2.76%) |       1   →       1              |        2.82 ms →        2.89 ms   (+2.76%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.58 ms →        2.63 ms   (+1.77%) |       1   →       1              |        2.58 ms →        2.63 ms   (+1.77%) | 
+ │ │   └ sirius::divergence                                            |       22.60 ms →       19.96 ms  (-11.66%) |       1   →       1              |       22.60 ms →       19.96 ms  (-11.66%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.46 ms →        2.47 ms   (+0.49%) |       1   →       1              |        2.46 ms →        2.47 ms   (+0.49%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.27 ms →        3.17 ms   (-3.12%) |       1   →       1              |        3.27 ms →        3.17 ms   (-3.12%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.34 ms →       22.23 ms   (-0.52%) |       1   →       1              |       22.34 ms →       22.23 ms   (-0.52%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      121.00 ns →      279.00 ns (+130.58%) |       1   →       1              |      121.00 ns →      279.00 ns (+130.58%) | 
  ├ sirius::Hamiltonian0                                                |       13.98 ms →       14.00 ms   (+0.11%) |       1   →       1              |       13.98 ms →       14.00 ms   (+0.11%) | 
  │ ├ sirius::Local_operator                                            |       13.65 ms →       13.67 ms   (+0.17%) |       1   →       1              |       13.65 ms →       13.67 ms   (+0.17%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.22 ms →        7.19 ms   (-0.47%) |       1   →       1              |        7.22 ms →        7.19 ms   (-0.47%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.97 ms →        5.02 ms   (+0.94%) |       1   →       1              |        4.97 ms →        5.02 ms   (+0.94%) | 
  │ ├ sirius::Non_local_operator                                        |       60.58 μs →       60.25 μs   (-0.53%) |       2   →       2              |      121.15 μs →      120.51 μs   (-0.53%) | 
  │ ├ sirius::D_operator::initialize                                    |       84.48 μs →       81.87 μs   (-3.09%) |       1   →       1              |       84.48 μs →       81.87 μs   (-3.09%) | 
  │ └ sirius::Q_operator::initialize                                    |       71.39 μs →       69.30 μs   (-2.93%) |       1   →       1              |       71.39 μs →       69.30 μs   (-2.93%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.20 s  →        2.46 s   (+11.86%) |       1   →       1              |        2.20 s  →        2.46 s   (+11.86%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.41 ms   (-0.09%) |       1   →       1              |        8.41 ms →        8.41 ms   (-0.09%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      253.26 μs →      248.06 μs   (-2.05%) |       1   →       1              |      253.26 μs →      248.06 μs   (-2.05%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.16 ms   (-0.03%) |       1   →       1              |        8.16 ms →        8.16 ms   (-0.03%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.19 s  →        2.45 s   (+11.90%) |       1   →       1              |        2.19 s  →        2.45 s   (+11.90%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.35 ms →       87.32 ms   (-3.35%) |       4   →       4              |      361.38 ms →      349.28 ms   (-3.35%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.75 ms →       25.99 ms   (+0.91%) |       1   →       1              |       25.75 ms →       25.99 ms   (+0.91%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.75 ms →       15.02 ms   (+1.80%) |       1   →       1              |       14.75 ms →       15.02 ms   (+1.80%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.20 s  →        1.20 s    (+0.11%) |       1   →       1              |        1.20 s  →        1.20 s    (+0.11%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      981.11 ms →      982.40 ms   (+0.13%) |       1   →       1              |      981.11 ms →      982.40 ms   (+0.13%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      311.53 ms →      315.23 ms   (+1.19%) |       1   →       1              |      311.53 ms →      315.23 ms   (+1.19%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      182.90 ms →      176.19 ms   (-3.67%) |       1   →       1              |      182.90 ms →      176.19 ms   (-3.67%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      182.90 ms →      176.18 ms   (-3.67%) |       1   →       1              |      182.90 ms →      176.18 ms   (-3.67%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      110.08 ms →      120.43 ms   (+9.40%) |       1   →       1              |      110.08 ms →      120.43 ms   (+9.40%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      179.45 ms →      174.24 ms   (-2.90%) |       1   →       1              |      179.45 ms →      174.24 ms   (-2.90%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      179.45 ms →      174.24 ms   (-2.90%) |       1   →       1              |      179.45 ms →      174.24 ms   (-2.90%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      159.28 ms →      162.16 ms   (+1.81%) |       1   →       1              |      159.28 ms →      162.16 ms   (+1.81%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      108.69 ms →      111.54 ms   (+2.62%) |       1   →       1              |      108.69 ms →      111.54 ms   (+2.62%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.71 ms →        3.74 ms   (+0.90%) |       1   →       1              |        3.71 ms →        3.74 ms   (+0.90%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.51 ms →       89.60 ms   (+0.10%) |       1   →       1              |       89.51 ms →       89.60 ms   (+0.10%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.43 ms →       11.97 ms   (+4.69%) |       1   →       1              |       11.43 ms →       11.97 ms   (+4.69%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.18 ms →       64.17 ms   (-0.01%) |       2   →       2              |      128.35 ms →      128.34 ms   (-0.01%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.38 ms →      193.35 ms (+225.59%) |       2   →       2              |      118.77 ms →      386.70 ms (+225.59%) | 
  │ │ │ ├ sddk::inner                                                   |       59.25 ms                             |       2                          |      118.50 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       21.43 μs                             |       2                          |       42.87 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.22 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |        1.06 ms                             |       4                          |        4.24 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        5.99 ms                             |       2                          |       11.98 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                       193.25 ms            |                   2              |                       386.49 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        47.00 ns            |                   2              |                        94.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                       191.66 ms            |                   2              |                       383.33 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        17.50 ns            |                   2              |                        35.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.43 ms →      114.87 ms   (-1.34%) |       1   →       1              |      116.43 ms →      114.87 ms   (-1.34%) | 
  │ │ ├ sddk::transform                                                 |       36.04 ms                             |       1                          |       36.04 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.79 μs                             |       1                          |       14.79 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       19.34 μs                             |       1                          |       19.34 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        36.46 ms            |                   1              |                        36.46 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.65 ms            |                   1              |                        35.65 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      794.00 ns →      430.00 ns  (-45.84%) |       1   →       1              |      794.00 ns →      430.00 ns  (-45.84%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      136.23 s  →      122.88 s    (-9.79%) |       1   →       1              |      136.23 s  →      122.88 s    (-9.79%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.13 ms →        2.17 ms   (+1.97%) |      31   →      31              |       65.89 ms →       67.19 ms   (+1.97%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.16 s  →        2.72 s   (-13.68%) |      43   →      45     (+4.65%) |      135.73 s  →      122.62 s    (-9.66%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.08 ms →        7.26 ms   (+2.58%) |      43   →      45     (+4.65%) |      304.41 ms →      326.79 ms   (+7.35%) | 
  │ │ │ ├ sirius::Local_operator                                        |        6.74 ms →        6.92 ms   (+2.70%) |      43   →      45     (+4.65%) |      289.83 ms →      311.50 ms   (+7.47%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.51 ms →        1.47 ms   (-2.45%) |      43   →      45     (+4.65%) |       64.82 ms →       66.18 ms   (+2.09%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.76 ms →        4.00 ms   (+6.14%) |      43   →      45     (+4.65%) |      161.86 ms →      179.79 ms  (+11.07%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.25 μs →       62.76 μs   (+2.46%) |      86   →      90     (+4.65%) |        5.27 ms →        5.65 ms   (+7.23%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       84.29 μs →       82.30 μs   (-2.36%) |      43   →      45     (+4.65%) |        3.62 ms →        3.70 ms   (+2.19%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       71.62 μs →       70.56 μs   (-1.47%) |      43   →      45     (+4.65%) |        3.08 ms →        3.18 ms   (+3.11%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.47 s  →        2.06 s   (-16.69%) |      43   →      45     (+4.65%) |      106.37 s  →       92.74 s   (-12.81%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      207.28 μs →      204.63 μs   (-1.28%) |      43   →      45     (+4.65%) |        8.91 ms →        9.21 ms   (+3.31%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      200.20 μs →      197.18 μs   (-1.51%) |      43   →      45     (+4.65%) |        8.61 ms →        8.87 ms   (+3.07%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.49 μs →        5.45 μs   (-0.76%) |      43   →      45     (+4.65%) |      236.26 μs →      245.37 μs   (+3.86%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.46 s  →        2.05 s   (-16.51%) |      43   →      45     (+4.65%) |      105.72 s  →       92.37 s   (-12.62%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       70.60 ms →       55.35 ms  (-21.61%) |      43   →      45     (+4.65%) |        3.04 s  →        2.49 s   (-17.96%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.62 ms →        3.93 ms  (-30.13%) |     258   →     270     (+4.65%) |        1.45 s  →        1.06 s   (-26.89%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.04 ms →        1.61 ms  (-20.87%) |      43   →      45     (+4.65%) |       87.72 ms →       72.64 ms  (-17.19%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      422.70 μs →      420.54 μs   (-0.51%) |      43   →      45     (+4.65%) |       18.18 ms →       18.92 ms   (+4.12%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      944.09 μs →      939.88 μs   (-0.45%) |      43   →      45     (+4.65%) |       40.60 ms →       42.29 ms   (+4.18%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.36 s  →        1.97 s   (-16.51%) |      43   →      45     (+4.65%) |      101.55 s  →       88.72 s   (-12.63%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.22 ms →      191.05 ms  (-10.82%) |     208   →     245    (+17.79%) |       44.56 s  →       46.81 s    (+5.05%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.62 ms →      134.37 ms  (-11.38%) |     208   →     245    (+17.79%) |       31.54 s  →       32.92 s    (+4.38%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.12 ms →       23.87 ms  (-11.99%) |     208   →     245    (+17.79%) |        5.64 s  →        5.85 s    (+3.67%) | 
+ │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      668.90 μs →      568.00 μs  (-15.08%) |     208   →     245    (+17.79%) |      139.13 ms →      139.16 ms   (+0.02%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.22 ms →        3.08 ms   (-4.45%) |      43   →      45     (+4.65%) |      138.66 ms →      138.65 ms   (-0.01%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.79 ms →       19.27 ms  (-11.56%) |     208   →     245    (+17.79%) |        4.53 s  →        4.72 s    (+4.17%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      667.19 μs →      568.61 μs  (-14.78%) |     208   →     245    (+17.79%) |      138.78 ms →      139.31 ms   (+0.38%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.22 ms →        3.08 ms   (-4.18%) |      43   →      45     (+4.65%) |      138.27 ms →      138.64 ms   (+0.27%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.07 ms →       29.84 ms  (-12.43%) |     208   →     245    (+17.79%) |        7.09 s  →        7.31 s    (+3.15%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.22 ms →       18.42 ms  (-13.20%) |     208   →     245    (+17.79%) |        4.41 s  →        4.51 s    (+2.25%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.61 ms   (-1.57%) |     208   →     245    (+17.79%) |      551.55 ms →      639.45 ms  (+15.94%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.45 ms →       20.31 ms   (-9.50%) |     208   →     245    (+17.79%) |        4.67 s  →        4.98 s    (+6.60%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.23 ms →        2.19 ms   (-1.58%) |     208   →     245    (+17.79%) |      463.86 ms →      537.75 ms  (+15.93%) | 
! │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.74 ms →       16.87 ms   (-9.96%) |     416   →     490    (+17.79%) |        7.79 s  →        8.27 s    (+6.05%) | 
! │ │ │ │   ├ sddk::orthogonalize                                       |       55.34 ms →       51.48 ms   (-6.97%) |     208   →     245    (+17.79%) |       11.51 s  →       12.61 s    (+9.58%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.52 ms                             |     373                          |        3.92 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       21.23 μs                             |     373                          |        7.92 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.48 ms                             |     746                          |        3.34 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      106.09 μs                             |     746                          |       79.14 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.33 ms                             |     373                          |      494.81 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                        11.91 ms            |                 445              |                         5.30 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        66.47 ns            |                 445              |                        29.58 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         8.47 ms            |                 445              |                         3.77 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        59.00 ns            |                 445              |                        26.25 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.09 ms →        2.94 ms   (-5.04%) |     208   →     245    (+17.79%) |      643.24 ms →      719.46 ms  (+11.85%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.27 ms →       14.32 ms  (-12.01%) |     208   →     245    (+17.79%) |        3.38 s  →        3.51 s    (+3.64%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.56 ms                             |     165                          |        3.56 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       26.24 μs                             |     165                          |        4.33 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       67.27 μs                             |     495                          |       33.30 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        15.43 ms            |                 200              |                         3.09 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         5.12 ms            |                 600              |                         3.07 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.37 ms →       19.22 ms  (-14.08%) |     208   →     245    (+17.79%) |        4.65 s  →        4.71 s    (+1.21%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       18.36 ms                             |     208                          |        3.82 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       45.33 μs                             |     208                          |        9.43 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.93 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      219.08 μs                             |     416                          |       91.14 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        2.01 ms                             |     208                          |      417.53 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        17.90 ms            |                 245              |                         4.39 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        74.02 ns            |                 245              |                        18.14 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        14.48 ms            |                 245              |                         3.55 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        25.48 ns            |                 245              |                         6.24 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      166.42 ms →       68.02 ms  (-59.13%) |     208   →     245    (+17.79%) |       34.61 s  →       16.66 s   (-51.86%) | 
! │ │ │ │   ├ sirius::residuals                                         |       19.07 ms →       17.35 ms   (-9.03%) |     207   →     239    (+15.46%) |        3.95 s  →        4.15 s    (+5.03%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.06 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.21 μs                             |     171                          |        2.94 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       59.98 μs                             |     342                          |       20.51 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        17.83 ms            |                 208              |                         3.71 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         7.57 ms            |                 416              |                         3.15 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.30 ms →        1.45 ms  (-37.00%) |     171   →     208    (+21.64%) |      392.64 ms →      300.88 ms  (-23.37%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.22 ms →       62.88 ms  (+22.76%) |      44   →      60    (+36.36%) |        2.25 s  →        3.77 s   (+67.40%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.82 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.96 μs                             |      45                          |      583.24 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       16.24 μs                             |      46                          |      746.83 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        49.76 ms            |                  75              |                         3.73 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        40.68 ms            |                  90              |                         3.66 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      587.72 ns →      631.69 ns   (+7.48%) |      43   →      45     (+4.65%) |       25.27 μs →       28.43 μs  (+12.48%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.55 μs →       26.95 μs   (-8.80%) |      43   →      45     (+4.65%) |        1.27 ms →        1.21 ms   (-4.56%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.44 ms →        3.44 ms   (+0.05%) |      43   →      45     (+4.65%) |      147.92 ms →      154.88 ms   (+4.70%) | 
  │ │ ├ sirius::Density::generate                                       |      294.15 ms →      293.30 ms   (-0.29%) |      43   →      45     (+4.65%) |       12.65 s  →       13.20 s    (+4.35%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      289.74 ms →      289.23 ms   (-0.18%) |      43   →      45     (+4.65%) |       12.46 s  →       13.02 s    (+4.47%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       66.09 ms →       64.71 ms   (-2.09%) |      43   →      45     (+4.65%) |        2.84 s  →        2.91 s    (+2.47%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       64.47 μs →       61.34 μs   (-4.84%) |      43   →      45     (+4.65%) |        2.77 ms →        2.76 ms   (-0.42%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.22 ms →        1.21 ms   (-1.06%) |       2   →       2              |        2.44 ms →        2.41 ms   (-1.06%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       54.73 ms →       53.25 ms   (-2.69%) |      43   →      45     (+4.65%) |        2.35 s  →        2.40 s    (+1.84%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       59.78 ms →       60.41 ms   (+1.05%) |      43   →      45     (+4.65%) |        2.57 s  →        2.72 s    (+5.75%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.77 μs →        9.41 μs   (-3.61%) |      43   →      45     (+4.65%) |      420.00 μs →      423.65 μs   (+0.87%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (+0.34%) |      43   →      45     (+4.65%) |       99.17 ms →      104.14 ms   (+5.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       56.93 ms →       57.55 ms   (+1.08%) |      43   →      45     (+4.65%) |        2.45 s  →        2.59 s    (+5.78%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.46 ms →        6.14 ms  (+12.46%) |      43   →      45     (+4.65%) |      234.78 ms →      276.33 ms  (+17.70%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      555.26 ns →      765.71 ns  (+37.90%) |      43   →      45     (+4.65%) |       23.88 μs →       34.46 μs  (+44.32%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.67 ms →      104.58 ms   (-0.08%) |      43   →      45     (+4.65%) |        4.50 s  →        4.71 s    (+4.56%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.43 ms →        2.42 ms   (-0.55%) |      43   →      45     (+4.65%) |      104.69 ms →      108.96 ms   (+4.08%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms →       20.05 ms   (-0.09%) |      43   →      45     (+4.65%) |      862.73 ms →      902.07 ms   (+4.56%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms →       19.88 ms   (-0.08%) |      43   →      45     (+4.65%) |      855.43 ms →      894.48 ms   (+4.56%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      251.79 ns →      248.96 ns   (-1.13%) |      43   →      45     (+4.65%) |       10.83 μs →       11.20 μs   (+3.47%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.27 ms →        1.25 ms   (-1.04%) |      43   →      45     (+4.65%) |       54.41 ms →       56.35 ms   (+3.56%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.14 ms →        2.81 ms  (-10.31%) |      43   →      45     (+4.65%) |      134.82 ms →      126.54 ms   (-6.14%) | 
  │ │ ├ sirius::Density::mix                                            |      144.59 ms →      131.58 ms   (-9.00%) |      43   →      45     (+4.65%) |        6.22 s  →        5.92 s    (-4.77%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      293.59 μs →      266.32 μs   (-9.29%) |      43   →      45     (+4.65%) |       12.62 ms →       11.98 ms   (-5.07%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        2.78 ms →        2.91 ms   (+4.73%) |      43   →      45     (+4.65%) |      119.47 ms →      130.93 ms   (+9.60%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.58 ms →        2.71 ms   (+4.79%) |      43   →      45     (+4.65%) |      111.15 ms →      121.90 ms   (+9.67%) | 
  │ │ ├ sirius::Potential::generate                                     |      185.68 ms →      180.31 ms   (-2.89%) |      43   →      45     (+4.65%) |        7.98 s  →        8.11 s    (+1.62%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.00 ms →       63.90 ms   (-0.16%) |      43   →      45     (+4.65%) |        2.75 s  →        2.88 s    (+4.48%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.09 ms →        9.77 ms   (+7.41%) |      43   →      45     (+4.65%) |      391.00 ms →      439.53 ms  (+12.41%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.19 ms →        4.15 ms   (-0.84%) |      43   →      45     (+4.65%) |      180.07 ms →      186.86 ms   (+3.78%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.06 ms →        4.07 ms   (+0.08%) |      43   →      45     (+4.65%) |      174.76 ms →      183.02 ms   (+4.73%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.06 ms →        4.07 ms   (+0.08%) |      43   →      45     (+4.65%) |      174.72 ms →      183.00 ms   (+4.74%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      232.77 μs →      231.68 μs   (-0.47%) |      86   →      90     (+4.65%) |       20.02 ms →       20.85 ms   (+4.16%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       96.01 ms →       91.12 ms   (-5.09%) |      43   →      45     (+4.65%) |        4.13 s  →        4.10 s    (-0.68%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       96.01 ms →       90.10 ms   (-6.16%) |      43   →      45     (+4.65%) |        4.13 s  →        4.05 s    (-1.79%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.66 ms →        1.58 ms   (-4.41%) |     215   →     225     (+4.65%) |      356.06 ms →      356.20 ms   (+0.04%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.82 ms →        2.50 ms  (-11.26%) |     387   →     405     (+4.65%) |        1.09 s  →        1.01 s    (-7.13%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.40 ms →        2.40 ms   (+0.04%) |      43   →      45     (+4.65%) |      103.28 ms →      108.13 ms   (+4.70%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      706.23 μs →      708.44 μs   (+0.31%) |     129   →     135     (+4.65%) |       91.10 ms →       95.64 ms   (+4.98%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.85 ms   (+1.27%) |      43   →      45     (+4.65%) |      121.14 ms →      128.38 ms   (+5.98%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms →        2.61 ms   (+1.09%) |      43   →      45     (+4.65%) |      110.87 ms →      117.28 ms   (+5.79%) | 
+ │ │ │ │   └ sirius::divergence                                        |       22.64 ms →       19.81 ms  (-12.49%) |      43   →      45     (+4.65%) |      973.50 ms →      891.58 ms   (-8.41%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.45 ms →        2.44 ms   (-0.38%) |      43   →      45     (+4.65%) |      105.15 ms →      109.62 ms   (+4.25%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.70 ms →        3.33 ms   (-9.98%) |      43   →      45     (+4.65%) |      159.07 ms →      149.86 ms   (-5.79%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.95 ms →       20.95 ms   (-0.00%) |      43   →      45     (+4.65%) |      900.95 ms →      942.84 ms   (+4.65%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      145.44 ns →      286.82 ns  (+97.21%) |      43   →      45     (+4.65%) |        6.25 μs →       12.91 μs (+106.38%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      217.84 ns →      248.16 ns  (+13.92%) |      43   →      45     (+4.65%) |        9.37 μs →       11.17 μs  (+19.22%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms →        2.27 ms   (+1.37%) |      43   →      45     (+4.65%) |       96.09 ms →      101.94 ms   (+6.09%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.08 ms →        4.07 ms   (-0.16%) |     301   →     315     (+4.65%) |        1.23 s  →        1.28 s    (+4.48%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.92 ms →        3.91 ms   (-0.20%) |     301   →     315     (+4.65%) |        1.18 s  →        1.23 s    (+4.45%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.92 ms →        3.91 ms   (-0.20%) |     301   →     315     (+4.65%) |        1.18 s  →        1.23 s    (+4.45%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.18 ms →        4.35 ms   (+4.10%) |     129   →     135     (+4.65%) |      539.42 ms →      587.63 ms   (+8.94%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.06 ms →        4.23 ms   (+4.08%) |     129   →     135     (+4.65%) |      523.67 ms →      570.38 ms   (+8.92%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.39 ms →        3.99 ms   (-9.25%) |      43   →      45     (+4.65%) |      188.91 ms →      179.41 ms   (-5.03%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      109.71 μs →      120.37 μs   (+9.72%) |      43   →      45     (+4.65%) |        4.72 ms →        5.42 ms  (+14.82%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.29 μs →      117.17 μs  (+10.24%) |      43   →      45     (+4.65%) |        4.57 ms →        5.27 ms  (+15.36%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.29 ms →        5.41 ms  (-14.00%) |       2   →       2              |       12.58 ms →       10.82 ms  (-14.00%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.07 ms →        4.09 ms   (+0.54%) |       6   →       6              |       24.44 ms →       24.57 ms   (+0.54%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.00 ms →        4.08 ms   (+2.03%) |       6   →       6              |       24.00 ms →       24.48 ms   (+2.03%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.00 ms →        4.08 ms   (+2.03%) |       6   →       6              |       24.00 ms →       24.48 ms   (+2.03%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.20 ms →        4.29 ms   (+2.36%) |       3   →       3              |       12.59 ms →       12.88 ms   (+2.36%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.19 ms →        4.29 ms   (+2.37%) |       3   →       3              |       12.56 ms →       12.86 ms   (+2.37%) | 
  ├ sirius::Periodic_function|inner                                     |        3.97 ms →        3.90 ms   (-1.75%) |       2   →       2              |        7.94 ms →        7.81 ms   (-1.75%) | 
  │ └ sirius::Periodic_function|inner_local                             |        3.96 ms →        3.87 ms   (-2.25%) |       2   →       2              |        7.93 ms →        7.75 ms   (-2.25%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.96 ms →        3.87 ms   (-2.25%) |       2   →       2              |        7.93 ms →        7.75 ms   (-2.25%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.14 ms →        4.22 ms   (+2.02%) |       1   →       1              |        4.14 ms →        4.22 ms   (+2.02%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.13 ms →        4.18 ms   (+1.15%) |       1   →       1              |        4.13 ms →        4.18 ms   (+1.15%) | 
+ └ sirius::finalize                                                    |      349.80 ms →      277.30 ms  (-20.73%) |       1   →       1              |      349.80 ms →      277.30 ms  (-20.73%) | 
  ====================================================================================================================================================================================================
```
