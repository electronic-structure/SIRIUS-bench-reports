# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      310.18 s  →      219.36 s   (-29.28%) |       1   →       1              |      310.18 s  →      219.36 s   (-29.28%) | 
  ├ sirius::initialize                                                  |        2.83 s  →        2.77 s    (-1.94%) |       1   →       1              |        2.83 s  →        2.77 s    (-1.94%) | 
  ├ sirius::Simulation_context::initialize                              |        3.09 s  →        2.97 s    (-3.59%) |       1   →       1              |        3.09 s  →        2.97 s    (-3.59%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       52.23 ms →      217.51 μs  (-99.58%) |       1   →       1              |       52.23 ms →      217.51 μs  (-99.58%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      201.04 ms →      213.26 ms   (+6.08%) |       1   →       1              |      201.04 ms →      213.26 ms   (+6.08%) | 
  │ │ ├ sirius::Atom_type::init                                         |       88.24 ms →       94.51 ms   (+7.11%) |       2   →       2              |      176.49 ms →      189.03 ms   (+7.11%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.47 ms →       24.15 ms   (-1.28%) |       1   →       1              |       24.47 ms →       24.15 ms   (-1.28%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.44 ms →        6.33 ms   (-1.59%) |       1   →       1              |        6.44 ms →        6.33 ms   (-1.59%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.99 ms →       17.77 ms   (-1.18%) |       1   →       1              |       17.99 ms →       17.77 ms   (-1.18%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.96 ms →       17.75 ms   (-1.15%) |       1   →       1              |       17.96 ms →       17.75 ms   (-1.15%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.16 ms   (-0.17%) |       1   →       1              |        4.17 ms →        4.16 ms   (-0.17%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.33 ms   (-0.71%) |       1   →       1              |        2.34 ms →        2.33 ms   (-0.71%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.61 μs →      105.77 μs   (-0.79%) |       1   →       1              |      106.61 μs →      105.77 μs   (-0.79%) | 
  │ └ sirius::Simulation_context::update                                |        2.79 s  →        2.72 s    (-2.59%) |       1   →       1              |        2.79 s  →        2.72 s    (-2.59%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.93 ms →       11.13 ms   (+1.80%) |       1   →       1              |       10.93 ms →       11.13 ms   (+1.80%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.53 ms →        4.45 ms   (-1.79%) |       1   →       1              |        4.53 ms →        4.45 ms   (-1.79%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.37 ms →        6.65 ms   (+4.35%) |       1   →       1              |        6.37 ms →        6.65 ms   (+4.35%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.35 ms →        6.63 ms   (+4.39%) |       1   →       1              |        6.35 ms →        6.63 ms   (+4.39%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        4.13 ms   (+7.76%) |       1   →       1              |        3.83 ms →        4.13 ms   (+7.76%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-1.03%) |       1   →       1              |        2.34 ms →        2.32 ms   (-1.03%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.71 μs →      100.19 μs   (-3.40%) |       1   →       1              |      103.71 μs →      100.19 μs   (-3.40%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.41 ms →       63.95 ms   (-0.72%) |       2   →       2              |      128.82 ms →      127.89 ms   (-0.72%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.17 ms →        5.18 ms   (+0.12%) |       2   →       2              |       10.34 ms →       10.35 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.49 ms →        4.52 ms   (+0.77%) |       1   →       1              |        4.49 ms →        4.52 ms   (+0.77%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.72 ms   (-0.19%) |       2   →       2              |       43.52 ms →       43.44 ms   (-0.19%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.80 ms →       14.87 ms   (+0.41%) |       2   →       2              |       29.61 ms →       29.73 ms   (+0.41%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.87 ms →       19.89 ms   (+0.12%) |       4   →       4              |       79.47 ms →       79.57 ms   (+0.12%) | 
  │   ├ sddk::Gvec::init                                                |      179.25 ms →      174.14 ms   (-2.85%) |       2   →       2              |      358.51 ms →      348.28 ms   (-2.85%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.66 ms →      131.64 ms   (-0.77%) |       2   →       2              |      265.31 ms →      263.27 ms   (-0.77%) | 
+ │   ├ sddk::Gvec_shells                                               |      208.05 ms →      178.99 ms  (-13.97%) |       1   →       1              |      208.05 ms →      178.99 ms  (-13.97%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.34 ms →        1.31 ms   (-2.45%) |       1   →       1              |        1.34 ms →        1.31 ms   (-2.45%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      296.04 ms →      305.43 ms   (+3.17%) |       2   →       2              |      592.07 ms →      610.87 ms   (+3.17%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       83.52 ms →       75.31 ms   (-9.83%) |       1   →       1              |       83.52 ms →       75.31 ms   (-9.83%) | 
  │ ├ sirius::K_point::K_point                                          |        2.56 μs →        2.45 μs   (-4.26%) |       4   →       4              |       10.25 μs →        9.81 μs   (-4.26%) | 
  │ └ sirius::K_point_set::initialize                                   |       83.43 ms →       75.21 ms   (-9.85%) |       1   →       1              |       83.43 ms →       75.21 ms   (-9.85%) | 
  │   └ sirius::K_point::initialize                                     |       20.85 ms →       18.78 ms   (-9.90%) |       4   →       4              |       83.38 ms →       75.13 ms   (-9.90%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       15.92 ms →       13.95 ms  (-12.33%) |       4   →       4              |       63.66 ms →       55.81 ms  (-12.33%) | 
  │     │ └ sddk::Gvec::init                                            |        3.99 ms →        3.82 ms   (-4.40%) |       4   →       4              |       15.97 ms →       15.26 ms   (-4.40%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.50 μs →        8.52 μs   (+0.24%) |       4   →       4              |       34.01 μs →       34.09 μs   (+0.24%) | 
  │     └ sirius::K_point::update                                       |        3.44 ms →        3.51 ms   (+2.16%) |       4   →       4              |       13.76 ms →       14.05 ms   (+2.16%) | 
- │       └ sirius::Beta_projectors                                     |        1.77 ms →        1.98 ms  (+11.82%) |       4   →       4              |        7.07 ms →        7.90 ms  (+11.82%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      937.42 μs →        1.03 ms   (+9.91%) |       4   →       4              |        3.75 ms →        4.12 ms   (+9.91%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.14 ms →        5.30 ms   (+3.17%) |       2   →       2              |       10.28 ms →       10.61 ms   (+3.17%) | 
  ├ sirius::Potential                                                   |      169.40 ms →      159.22 ms   (-6.01%) |       1   →       1              |      169.40 ms →      159.22 ms   (-6.01%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.73 ms   (-0.10%) |       6   →       6              |       34.42 ms →       34.39 ms   (-0.10%) | 
  │ └ sirius::Potential::update                                         |      134.29 ms →      124.14 ms   (-7.56%) |       1   →       1              |      134.29 ms →      124.14 ms   (-7.56%) | 
  │   └ sirius::Potential::generate_local_potential                     |      133.57 ms →      123.41 ms   (-7.61%) |       1   →       1              |      133.57 ms →      123.41 ms   (-7.61%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.96 ms →      108.22 ms   (-4.19%) |       1   →       1              |      112.96 ms →      108.22 ms   (-4.19%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       20.07 ms →       14.32 ms  (-28.66%) |       1   →       1              |       20.07 ms →       14.32 ms  (-28.66%) | 
  ├ sirius::Density                                                     |      140.81 ms →      135.67 ms   (-3.66%) |       1   →       1              |      140.81 ms →      135.67 ms   (-3.66%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.15 ms →        5.09 ms   (-1.16%) |       2   →       2              |       10.30 ms →       10.18 ms   (-1.16%) | 
  │ └ sirius::Density::update                                           |      130.24 ms →      125.22 ms   (-3.86%) |       1   →       1              |      130.24 ms →      125.22 ms   (-3.86%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.84 ms →      124.80 ms   (-3.88%) |       1   →       1              |      129.84 ms →      124.80 ms   (-3.88%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       101.83 μs            |                   1              |                       101.83 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.09 ms →      111.34 ms   (-1.55%) |       1   →       1              |      113.09 ms →      111.34 ms   (-1.55%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.31 ms →       12.93 ms  (-20.73%) |       1   →       1              |       16.31 ms →       12.93 ms  (-20.73%) | 
  ├ sirius::Density::initial_density                                    |      175.65 ms →      176.89 ms   (+0.71%) |       1   →       1              |      175.65 ms →      176.89 ms   (+0.71%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.43 ms →      110.26 ms   (-0.16%) |       1   →       1              |      110.43 ms →      110.26 ms   (-0.16%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.33 ms →       11.05 ms   (-2.44%) |       2   →       2              |       22.66 ms →       22.11 ms   (-2.44%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.82 ms →       10.34 ms   (-4.47%) |       1   →       1              |       10.82 ms →       10.34 ms   (-4.47%) | 
  ├ sirius::Potential::generate                                         |      585.65 ms →      595.04 ms   (+1.60%) |       1   →       1              |      585.65 ms →      595.04 ms   (+1.60%) | 
  │ ├ sirius::Potential::poisson                                        |      137.73 ms →      138.33 ms   (+0.44%) |       1   →       1              |      137.73 ms →      138.33 ms   (+0.44%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.50 ms →       19.21 ms  (+16.43%) |       1   →       1              |       16.50 ms →       19.21 ms  (+16.43%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.35 ms →       10.85 ms   (+4.82%) |       1   →       1              |       10.35 ms →       10.85 ms   (+4.82%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.80 ms →        9.93 ms   (+1.27%) |       1   →       1              |        9.80 ms →        9.93 ms   (+1.27%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →        9.93 ms   (+1.27%) |       1   →       1              |        9.80 ms →        9.93 ms   (+1.27%) | 
  │ ├ sirius::Periodic_function::add                                    |      550.08 μs →      540.92 μs   (-1.67%) |       2   →       2              |        1.10 ms →        1.08 ms   (-1.67%) | 
  │ ├ sirius::Potential::xc                                             |       51.25 ms →       54.50 ms   (+6.34%) |       1   →       1              |       51.25 ms →       54.50 ms   (+6.34%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.25 ms →       52.20 ms   (+1.86%) |       1   →       1              |       51.25 ms →       52.20 ms   (+1.86%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.67 ms →        5.61 ms   (-1.01%) |       2   →       2              |       11.34 ms →       11.23 ms   (-1.01%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.42 ms →        5.67 ms   (+4.55%) |       1   →       1              |        5.42 ms →        5.67 ms   (+4.55%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.76 ms →        5.81 ms   (+0.88%) |       1   →       1              |        5.76 ms →        5.81 ms   (+0.88%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.62 ms →       92.56 ms   (-0.06%) |       1   →       1              |       92.62 ms →       92.56 ms   (-0.06%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      295.85 ms →      301.43 ms   (+1.88%) |       1   →       1              |      295.85 ms →      301.43 ms   (+1.88%) | 
  ├ sirius::Hamiltonian0                                                |        8.41 ms →        8.42 ms   (+0.11%) |       1   →       1              |        8.41 ms →        8.42 ms   (+0.11%) | 
  │ ├ sirius::Local_operator                                            |        8.07 ms →        8.08 ms   (+0.03%) |       1   →       1              |        8.07 ms →        8.08 ms   (+0.03%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.70 ms →        4.70 ms   (+0.15%) |       1   →       1              |        4.70 ms →        4.70 ms   (+0.15%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.46 ms →        2.46 ms   (-0.16%) |       1   →       1              |        2.46 ms →        2.46 ms   (-0.16%) | 
  │ ├ sirius::Non_local_operator                                        |       63.27 μs →       63.51 μs   (+0.37%) |       2   →       2              |      126.54 μs →      127.01 μs   (+0.37%) | 
  │ ├ sirius::D_operator::initialize                                    |       95.90 μs →       98.77 μs   (+2.99%) |       1   →       1              |       95.90 μs →       98.77 μs   (+2.99%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.29 μs →       68.27 μs   (-0.02%) |       1   →       1              |       68.29 μs →       68.27 μs   (-0.02%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.12 s    (+0.54%) |       1   →       1              |        3.11 s  →        3.12 s    (+0.54%) | 
- │ ├ sirius::Hamiltonian_k                                             |      203.18 μs →      367.93 μs  (+81.08%) |       4   →       4              |      812.74 μs →        1.47 ms  (+81.08%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      197.95 μs →      362.77 μs  (+83.26%) |       4   →       4              |      791.80 μs →        1.45 ms  (+83.26%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.75 μs →        3.45 μs   (-8.07%) |       4   →       4              |       15.01 μs →       13.80 μs   (-8.07%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      776.80 ms →      780.85 ms   (+0.52%) |       4   →       4              |        3.11 s  →        3.12 s    (+0.52%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.11 ms →       32.42 ms   (+0.99%) |      16   →      16              |      513.72 ms →      518.79 ms   (+0.99%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       15.51 ms →       14.48 ms   (-6.62%) |       4   →       4              |       62.03 ms →       57.93 ms   (-6.62%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.31 ms →        5.28 ms   (-0.60%) |       4   →       4              |       21.25 ms →       21.12 ms   (-0.60%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      358.34 ms →      357.24 ms   (-0.31%) |       4   →       4              |        1.43 s  →        1.43 s    (-0.31%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      262.00 ms →      260.18 ms   (-0.70%) |       4   →       4              |        1.05 s  →        1.04 s    (-0.70%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.29 ms →       63.88 ms   (-5.08%) |       4   →       4              |      269.17 ms →      255.50 ms   (-5.08%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.79 ms →       16.46 ms   (-1.94%) |       4   →       4              |       67.16 ms →       65.86 ms   (-1.94%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.79 ms →       16.46 ms   (-1.94%) |       4   →       4              |       67.15 ms →       65.85 ms   (-1.94%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       43.97 ms →       40.92 ms   (-6.95%) |       4   →       4              |      175.89 ms →      163.66 ms   (-6.95%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.54 ms →       16.28 ms   (-1.60%) |       4   →       4              |       66.17 ms →       65.11 ms   (-1.60%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.54 ms →       16.27 ms   (-1.61%) |       4   →       4              |       66.16 ms →       65.10 ms   (-1.61%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.97 ms →       54.81 ms   (+3.48%) |       4   →       4              |      211.86 ms →      219.24 ms   (+3.48%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.95 ms →       36.74 ms   (+5.14%) |       4   →       4              |      139.79 ms →      146.97 ms   (+5.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.93 ms →        1.95 ms   (+1.10%) |       4   →       4              |        7.72 ms →        7.80 ms   (+1.10%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.08 ms →       40.83 ms   (+1.86%) |       4   →       4              |      160.34 ms →      163.32 ms   (+1.86%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        6.97 ms →        7.66 ms  (+10.01%) |       4   →       4              |       27.87 ms →       30.66 ms  (+10.01%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.14 ms →       27.12 ms   (-0.06%) |       8   →       8              |      217.12 ms →      216.99 ms   (-0.06%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.12 ms →       15.14 ms   (+7.22%) |       8   →       8              |      112.95 ms →      121.10 ms   (+7.22%) | 
  │ │ │ ├ sddk::inner                                                   |       14.05 ms                             |       8                          |      112.42 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       50.87 μs                             |       8                          |      406.95 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.09 ms            |                   8              |                       120.76 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        28.13 ns            |                   8              |                       225.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.91 ms            |                   8              |                       119.31 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        35.75 ns            |                   8              |                       286.00 ns            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      119.19 ms →      120.58 ms   (+1.17%) |       4   →       4              |      476.76 ms →      482.33 ms   (+1.17%) | 
  │ │ ├ sddk::transform                                                 |       28.88 ms                             |       4                          |      115.52 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       26.03 μs                             |       4                          |      104.14 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.15 ms                             |       4                          |        4.62 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       23.11 μs                             |       4                          |       92.45 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        23.67 ms            |                   4              |                        94.69 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        23.53 ms            |                   4              |                        94.11 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      512.75 ns →      422.25 ns  (-17.65%) |       4   →       4              |        2.05 μs →        1.69 μs  (-17.65%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      298.95 s  →      208.55 s   (-30.24%) |       1   →       1              |      298.95 s  →      208.55 s   (-30.24%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.67 ms →        5.65 ms   (-0.21%) |      19   →      19              |      107.66 ms →      107.44 ms   (-0.21%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.29 s  →        7.98 s    (-3.75%) |      36   →      26    (-27.78%) |      298.49 s  →      207.50 s   (-30.48%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.58 ms →        4.63 ms   (+1.02%) |      36   →      26    (-27.78%) |      164.99 ms →      120.38 ms  (-27.04%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.22 ms →        4.27 ms   (+1.25%) |      36   →      26    (-27.78%) |      151.84 ms →      111.04 ms  (-26.87%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      951.05 μs →      975.24 μs   (+2.54%) |      36   →      26    (-27.78%) |       34.24 ms →       25.36 ms  (-25.94%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.38 ms →        2.41 ms   (+1.06%) |      36   →      26    (-27.78%) |       85.78 ms →       62.61 ms  (-27.01%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.68 μs →       64.60 μs   (-0.12%) |      72   →      52    (-27.78%) |        4.66 ms →        3.36 ms  (-27.87%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       99.27 μs →       95.60 μs   (-3.69%) |      36   →      26    (-27.78%) |        3.57 ms →        2.49 ms  (-30.44%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       70.97 μs →       65.89 μs   (-7.17%) |      36   →      26    (-27.78%) |        2.56 ms →        1.71 ms  (-32.95%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.17 s  →        5.87 s    (-4.97%) |      36   →      26    (-27.78%) |      222.23 s  →      152.52 s   (-31.37%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      201.13 μs →      321.32 μs  (+59.76%) |     144   →     104    (-27.78%) |       28.96 ms →       33.42 ms  (+15.38%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      195.47 μs →      315.99 μs  (+61.66%) |     144   →     104    (-27.78%) |       28.15 ms →       32.86 ms  (+16.75%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.41 μs →        3.84 μs  (-12.93%) |     144   →     104    (-27.78%) |      635.62 μs →      399.72 μs  (-37.11%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.54 s  →        1.47 s    (-4.98%) |     144   →     104    (-27.78%) |      222.20 s  →      152.48 s   (-31.37%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       15.23 ms →       11.94 ms  (-21.58%) |     144   →     104    (-27.78%) |        2.19 s  →        1.24 s   (-43.36%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      570.15 μs →      709.19 ns  (-99.88%) |     864   →     624    (-27.78%) |      492.61 ms →      442.54 μs  (-99.91%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.83 ms   (-0.81%) |     144   →     104    (-27.78%) |      265.59 ms →      190.25 ms  (-28.37%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.81 μs →      354.17 μs   (+0.96%) |     144   →     104    (-27.78%) |       50.52 ms →       36.83 ms  (-27.09%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      547.24 μs →      548.76 μs   (+0.28%) |     288   →     208    (-27.78%) |      157.60 ms →      114.14 ms  (-27.58%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.52 s  →        1.44 s    (-4.85%) |     144   →     104    (-27.78%) |      218.44 s  →      150.10 s   (-31.28%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       75.91 ms →       67.82 ms  (-10.66%) |     874   →     965    (+10.41%) |       66.35 s  →       65.45 s    (-1.36%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       48.62 ms →       43.29 ms  (-10.97%) |     874   →     965    (+10.41%) |       42.50 s  →       41.78 s    (-1.70%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.92 ms →        8.66 ms   (-2.84%) |     874   →     965    (+10.41%) |        7.79 s  →        8.36 s    (+7.27%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       60.75 μs →      214.48 μs (+253.04%) |     874   →     965    (+10.41%) |       53.10 ms →      206.97 ms (+289.79%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      357.47 μs →        1.97 ms (+451.70%) |     144   →     104    (-27.78%) |       51.48 ms →      205.11 ms (+298.45%) | 
! │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.40 ms →        6.70 ms   (-9.48%) |     874   →     965    (+10.41%) |        6.47 s  →        6.47 s    (-0.06%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       66.83 μs →       82.37 μs  (+23.27%) |     874   →     965    (+10.41%) |       58.41 ms →       79.49 ms  (+36.10%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      392.14 μs →      739.94 μs  (+88.69%) |     144   →     104    (-27.78%) |       56.47 ms →       76.95 ms  (+36.28%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.77 ms →        9.41 ms  (-12.61%) |     874   →     965    (+10.41%) |        9.42 s  →        9.09 s    (-3.51%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.73 ms →        5.91 ms  (-12.23%) |     874   →     965    (+10.41%) |        5.88 s  →        5.70 s    (-3.09%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.52 ms   (-0.91%) |     874   →     965    (+10.41%) |        1.34 s  →        1.47 s    (+9.41%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        9.49 ms →        8.41 ms  (-11.36%) |     874   →     965    (+10.41%) |        8.30 s  →        8.12 s    (-2.13%) | 
! │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.40 ms →        1.30 ms   (-7.57%) |     874   →     965    (+10.41%) |        1.23 s  →        1.25 s    (+2.05%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.12 ms →        7.29 ms  (-10.26%) |    1.75 K →    1.93 K  (+10.41%) |       14.19 s  →       14.06 s    (-0.92%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       20.56 ms →       26.50 ms  (+28.89%) |     874   →     965    (+10.41%) |       17.97 s  →       25.57 s   (+42.31%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.36 ms                             |    1.60 K                        |        3.79 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.66 μs                             |    1.76 K                        |       57.48 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.95 ms            |                1.83 K            |                         3.57 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        68.09 ns            |                1.83 K            |                       124.34 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.94 ms            |                1.83 K            |                         3.55 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        75.38 ns            |                1.83 K            |                       137.64 μs            | 
! │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      813.67 μs →      794.16 μs   (-2.40%) |     874   →     965    (+10.41%) |      711.15 ms →      766.37 ms   (+7.76%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      864.89 μs →      747.17 μs  (-13.61%) |     874   →     965    (+10.41%) |      755.91 ms →      721.01 ms   (-4.62%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.24 ms                             |    3.35 K                        |       10.85 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.00 μs                             |    3.35 K                        |       46.93 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      175.66 μs                             |    3.35 K                        |      588.80 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.77 μs                             |    4.81 K                        |       51.81 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.07 ms            |                3.76 K            |                        19.04 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.45 ms            |                5.48 K            |                        18.89 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.85 ms →        5.16 ms  (-11.86%) |     874   →     965    (+10.41%) |        5.11 s  →        4.98 s    (-2.68%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.26 ms                             |     874                          |        3.73 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.23 μs                             |    1.06 K                        |       29.01 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.39 ms            |                 965              |                         3.28 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        59.91 ns            |                 965              |                        57.82 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.38 ms            |                 965              |                         3.26 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        52.60 ns            |                 965              |                        50.76 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      136.21 ms →       33.51 ms  (-75.40%) |     874   →     965    (+10.41%) |      119.05 s  →       32.34 s   (-72.84%) | 
- │ │ │ │   ├ sirius::residuals                                         |        8.27 ms →        9.65 ms  (+16.77%) |     861   →     937     (+8.83%) |        7.12 s  →        9.05 s   (+27.08%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.67 ms                             |     799                          |        6.13 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.00 μs                             |     799                          |       16.78 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      260.05 μs                             |     799                          |      207.78 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       13.95 μs                             |    1.60 K                        |       22.29 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         9.23 ms            |                 894              |                         8.25 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         4.59 ms            |                1.79 K            |                         8.20 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      948.56 μs →      624.09 μs  (-34.21%) |     799   →     894    (+11.89%) |      757.90 ms →      557.94 ms  (-26.38%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       18.40 ms →       36.91 ms (+100.55%) |     152   →     344   (+126.32%) |        2.80 s  →       12.70 s  (+353.88%) | 
  │ │ │ │     ├ sddk::transform                                         |       17.43 ms                             |     160                          |        2.79 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       17.32 μs                             |     160                          |        2.77 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.02 ms                             |     160                          |      162.54 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       17.39 μs                             |     168                          |        2.92 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        21.61 ms            |                 584              |                        12.62 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        15.23 ms            |                 824              |                        12.55 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      509.34 ns →      580.93 ns  (+14.06%) |     144   →     104    (-27.78%) |       73.35 μs →       60.42 μs  (-17.63%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       18.56 μs →       23.36 μs  (+25.90%) |      36   →      26    (-27.78%) |      668.07 μs →      607.45 μs   (-9.07%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      614.29 μs →      595.36 μs   (-3.08%) |      36   →      26    (-27.78%) |       22.11 ms →       15.48 ms  (-30.00%) | 
+ │ │ ├ sirius::Density::generate                                       |      904.18 ms →      907.85 ms   (+0.41%) |      36   →      26    (-27.78%) |       32.55 s  →       23.60 s   (-27.48%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      521.06 ms →      527.58 ms   (+1.25%) |      36   →      26    (-27.78%) |       18.76 s  →       13.72 s   (-26.87%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.22 ms →       24.95 ms   (+2.99%) |     144   →     104    (-27.78%) |        3.49 s  →        2.59 s   (-25.62%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.34 μs →        8.85 μs   (+6.02%) |     144   →     104    (-27.78%) |        1.20 ms →      920.07 μs  (-23.43%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.58 μs →       15.92 μs   (+9.16%) |       8   →       8              |      116.66 μs →      127.35 μs   (+9.16%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.19 ms →       20.82 ms   (+3.13%) |     144   →     104    (-27.78%) |        2.91 s  →        2.16 s   (-25.52%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.52 ms →       30.04 ms   (+1.73%) |     144   →     104    (-27.78%) |        4.25 s  →        3.12 s   (-26.53%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.59 μs →        9.79 μs   (+2.07%) |     144   →     104    (-27.78%) |        1.38 ms →        1.02 ms  (-26.28%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.21%) |     144   →     104    (-27.78%) |      209.21 ms →      151.42 ms  (-27.62%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.59 ms →       28.10 ms   (+1.84%) |     144   →     104    (-27.78%) |        3.97 s  →        2.92 s   (-26.45%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.53 ms →        3.97 ms  (+12.33%) |     144   →     104    (-27.78%) |      508.71 ms →      412.70 ms  (-18.87%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      647.84 ns →      509.76 ns  (-21.31%) |     144   →     104    (-27.78%) |       93.29 μs →       53.02 μs  (-43.17%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.44 ms →       42.57 ms   (+0.29%) |     144   →     104    (-27.78%) |        6.11 s  →        4.43 s   (-27.57%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.05%) |      36   →      26    (-27.78%) |       59.03 ms →       42.61 ms  (-27.81%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.30 ms →       88.88 ms   (+0.66%) |      36   →      26    (-27.78%) |        3.18 s  →        2.31 s   (-27.30%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.07 ms →       88.65 ms   (+0.66%) |      36   →      26    (-27.78%) |        3.17 s  →        2.30 s   (-27.30%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      287.54 ms →      280.20 ms   (-2.55%) |      36   →      26    (-27.78%) |       10.35 s  →        7.29 s   (-29.62%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      287.54 ms →      280.19 ms   (-2.55%) |      36   →      26    (-27.78%) |       10.35 s  →        7.29 s   (-29.62%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       30.07 ms →       24.51 ms  (-18.50%) |      36   →      26    (-27.78%) |        1.08 s  →      637.21 ms  (-41.14%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.21 ms →      230.09 ms   (+0.82%) |      36   →      26    (-27.78%) |        8.22 s  →        5.98 s   (-27.18%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.54 ms →       23.79 ms  (-13.64%) |      36   →      26    (-27.78%) |      991.48 ms →      618.41 ms  (-37.63%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.67 ms →       90.91 ms  (+12.70%) |      36   →      26    (-27.78%) |        2.90 s  →        2.36 s   (-18.61%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       11.33 ms →        5.58 ms  (-50.75%) |      36   →      26    (-27.78%) |      407.70 ms →      145.02 ms  (-64.43%) | 
+ │ │ ├ sirius::Density::mix                                            |      222.42 ms →      219.41 ms   (-1.35%) |      36   →      26    (-27.78%) |        8.01 s  →        5.70 s   (-28.75%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      931.07 μs →      971.29 μs   (+4.32%) |      36   →      26    (-27.78%) |       33.52 ms →       25.25 ms  (-24.66%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.33 ms →       10.72 ms   (+3.77%) |     484   →     334    (-30.99%) |        5.00 s  →        3.58 s   (-28.39%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.95 ms →       10.42 ms   (+4.70%) |     484   →     334    (-30.99%) |        4.82 s  →        3.48 s   (-27.75%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.95 ms →       10.42 ms   (+4.69%) |     484   →     334    (-30.99%) |        4.82 s  →        3.48 s   (-27.75%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.25 ms →        6.76 ms   (-6.78%) |      36   →      26    (-27.78%) |      260.96 ms →      175.68 ms  (-32.68%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.41 ms →        5.94 ms   (-7.44%) |      36   →      26    (-27.78%) |      230.88 ms →      154.35 ms  (-33.15%) | 
+ │ │ ├ sirius::Potential::generate                                     |      572.97 ms →      578.95 ms   (+1.04%) |      36   →      26    (-27.78%) |       20.63 s  →       15.05 s   (-27.02%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.53 ms →      137.07 ms   (-0.34%) |      36   →      26    (-27.78%) |        4.95 s  →        3.56 s   (-28.02%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.77 ms →       18.37 ms  (+16.50%) |      36   →      26    (-27.78%) |      567.62 ms →      477.58 ms  (-15.86%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.20 ms →       10.30 ms   (+1.03%) |      36   →      26    (-27.78%) |      367.15 ms →      267.91 ms  (-27.03%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.92 ms →       10.04 ms   (+1.22%) |      36   →      26    (-27.78%) |      357.13 ms →      261.07 ms  (-26.90%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.92 ms →       10.04 ms   (+1.22%) |      36   →      26    (-27.78%) |      357.12 ms →      261.05 ms  (-26.90%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      557.50 μs →      547.84 μs   (-1.73%) |      72   →      52    (-27.78%) |       40.14 ms →       28.49 ms  (-29.03%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       47.45 ms →       49.33 ms   (+3.95%) |      36   →      26    (-27.78%) |        1.71 s  →        1.28 s   (-24.92%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.45 ms →       46.98 ms   (-0.98%) |      36   →      26    (-27.78%) |        1.71 s  →        1.22 s   (-28.48%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.98 ms →        3.04 ms   (+2.11%) |      72   →      52    (-27.78%) |      214.49 ms →      158.18 ms  (-26.25%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.50 ms →        5.38 ms   (-2.25%) |      36   →      26    (-27.78%) |      197.97 ms →      139.75 ms  (-29.41%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.60 ms →        6.64 ms   (+0.74%) |      36   →      26    (-27.78%) |      237.46 ms →      172.77 ms  (-27.24%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.85 ms →       90.85 ms   (-0.00%) |      36   →      26    (-27.78%) |        3.27 s  →        2.36 s   (-27.78%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      288.15 ms →      292.68 ms   (+1.57%) |      36   →      26    (-27.78%) |       10.37 s  →        7.61 s   (-26.64%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      291.02 ms →      282.18 ms   (-3.04%) |      36   →      26    (-27.78%) |       10.48 s  →        7.34 s   (-29.97%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      291.02 ms →      282.18 ms   (-3.04%) |      36   →      26    (-27.78%) |       10.48 s  →        7.34 s   (-29.97%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.00 ms →       27.26 ms  (-14.82%) |      36   →      26    (-27.78%) |        1.15 s  →      708.74 ms  (-38.48%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.60 ms →      227.34 ms   (-0.11%) |      36   →      26    (-27.78%) |        8.19 s  →        5.91 s   (-27.86%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.68 ms →       23.76 ms  (-14.17%) |      36   →      26    (-27.78%) |      996.47 ms →      617.67 ms  (-38.01%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.15 ms →        5.56 ms  (-22.33%) |      36   →      26    (-27.78%) |      257.57 ms →      144.49 ms  (-43.90%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.35 ms →       10.44 ms   (+0.90%) |     252   →     182    (-27.78%) |        2.61 s  →        1.90 s   (-27.13%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.95 ms →        9.87 ms   (-0.81%) |     252   →     182    (-27.78%) |        2.51 s  →        1.80 s   (-28.36%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.95 ms →        9.87 ms   (-0.81%) |     252   →     182    (-27.78%) |        2.51 s  →        1.80 s   (-28.36%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.63 ms →       10.67 ms   (+0.41%) |     108   →      78    (-27.78%) |        1.15 s  →      832.44 ms  (-27.48%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.26 ms →       10.21 ms   (-0.43%) |     108   →      78    (-27.78%) |        1.11 s  →      796.60 ms  (-28.09%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.83 ms →       10.08 ms   (-6.94%) |      36   →      26    (-27.78%) |      389.88 ms →      262.04 ms  (-32.79%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      110.48 μs →      113.17 μs   (+2.43%) |      36   →      26    (-27.78%) |        3.98 ms →        2.94 ms  (-26.02%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      105.48 μs →      108.04 μs   (+2.42%) |      36   →      26    (-27.78%) |        3.80 ms →        2.81 ms  (-26.03%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.16 ms   (+0.74%) |       2   →       2              |       10.24 ms →       10.32 ms   (+0.74%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.89 ms →        9.83 ms   (-0.55%) |       6   →       6              |       59.33 ms →       59.00 ms   (-0.55%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.86 ms →        9.82 ms   (-0.44%) |       6   →       6              |       59.17 ms →       58.91 ms   (-0.44%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.86 ms →        9.82 ms   (-0.44%) |       6   →       6              |       59.17 ms →       58.90 ms   (-0.44%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.25 ms →       10.20 ms   (-0.44%) |       3   →       3              |       30.74 ms →       30.60 ms   (-0.44%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.20 ms →       10.19 ms   (-0.10%) |       3   →       3              |       30.60 ms →       30.57 ms   (-0.10%) | 
  ├ sirius::Periodic_function|inner                                     |       10.02 ms →       10.43 ms   (+4.08%) |       2   →       2              |       20.04 ms →       20.86 ms   (+4.08%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.01 ms →       10.03 ms   (+0.16%) |       2   →       2              |       20.03 ms →       20.06 ms   (+0.16%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →       10.03 ms   (+0.16%) |       2   →       2              |       20.03 ms →       20.06 ms   (+0.16%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.37 ms →       10.47 ms   (+1.00%) |       1   →       1              |       10.37 ms →       10.47 ms   (+1.00%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.36 ms →       10.47 ms   (+0.99%) |       1   →       1              |       10.36 ms →       10.47 ms   (+0.99%) | 
+ └ sirius::finalize                                                    |      397.74 ms →      274.17 ms  (-31.07%) |       1   →       1              |      397.74 ms →      274.17 ms  (-31.07%) | 
  ====================================================================================================================================================================================================
```
