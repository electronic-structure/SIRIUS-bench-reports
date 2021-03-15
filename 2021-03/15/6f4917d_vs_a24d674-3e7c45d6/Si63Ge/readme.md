# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 6f4917d65584ba2b52ea522b0bd003886a7daddd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       78.13 s  →       47.12 s   (-39.69%) |       1   →       1              |       78.13 s  →       47.12 s   (-39.69%) | 
  ├ sirius::initialize                                                  |        2.88 s  →        2.85 s    (-0.99%) |       1   →       1              |        2.88 s  →        2.85 s    (-0.99%) | 
+ ├ sirius::Simulation_context::initialize                              |        4.82 s  →        3.59 s   (-25.49%) |       1   →       1              |        4.82 s  →        3.59 s   (-25.49%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       33.26 ms →       20.00 ms  (-39.87%) |       1   →       1              |       33.26 ms →       20.00 ms  (-39.87%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.20 s  →      148.46 ms  (-87.66%) |       1   →       1              |        1.20 s  →      148.46 ms  (-87.66%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      596.40 ms →       63.23 ms  (-89.40%) |       2   →       2              |        1.19 s  →      126.46 ms  (-89.40%) | 
- │ │ └ sirius::Unit_cell::update                                       |       10.32 ms →       21.85 ms (+111.83%) |       1   →       1              |       10.32 ms →       21.85 ms (+111.83%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.92 ms →        5.20 ms  (+32.59%) |       1   →       1              |        3.92 ms →        5.20 ms  (+32.59%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →       16.60 ms (+162.02%) |       1   →       1              |        6.34 ms →       16.60 ms (+162.02%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |        6.29 ms →       16.53 ms (+162.93%) |       1   →       1              |        6.29 ms →       16.53 ms (+162.93%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.68 ms   (-0.55%) |       1   →       1              |        2.70 ms →        2.68 ms   (-0.55%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      491.78 μs →      496.25 μs   (+0.91%) |       1   →       1              |      491.78 μs →      496.25 μs   (+0.91%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.81 μs →       15.49 μs   (-2.03%) |       1   →       1              |       15.81 μs →       15.49 μs   (-2.03%) | 
  │ └ sirius::Simulation_context::update                                |        3.49 s  →        3.23 s    (-7.37%) |       1   →       1              |        3.49 s  →        3.23 s    (-7.37%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.98 ms →        7.12 ms   (+2.01%) |       1   →       1              |        6.98 ms →        7.12 ms   (+2.01%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.75 ms →        3.73 ms   (-0.47%) |       1   →       1              |        3.75 ms →        3.73 ms   (-0.47%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.20 ms →        3.35 ms   (+4.52%) |       1   →       1              |        3.20 ms →        3.35 ms   (+4.52%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.16 ms →        3.28 ms   (+3.80%) |       1   →       1              |        3.16 ms →        3.28 ms   (+3.80%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.63 ms →        2.74 ms   (+4.04%) |       1   →       1              |        2.63 ms →        2.74 ms   (+4.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      497.03 μs →      503.04 μs   (+1.21%) |       1   →       1              |      497.03 μs →      503.04 μs   (+1.21%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.51 μs →       19.73 μs  (+46.11%) |       1   →       1              |       13.51 μs →       19.73 μs  (+46.11%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.55 ms →      211.53 ms   (-0.48%) |       2   →       2              |      425.10 ms →      423.07 ms   (-0.48%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.19 ms →       15.20 ms   (+0.05%) |       2   →       2              |       30.39 ms →       30.40 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.23 ms →       13.32 ms   (+0.73%) |       1   →       1              |       13.23 ms →       13.32 ms   (+0.73%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.33 ms →       56.37 ms   (+0.09%) |       2   →       2              |      112.65 ms →      112.75 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       44.95 ms →       45.17 ms   (+0.50%) |       2   →       2              |       89.89 ms →       90.34 ms   (+0.50%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       59.92 ms →       60.12 ms   (+0.34%) |       4   →       4              |      239.68 ms →      240.50 ms   (+0.34%) | 
  │   ├ sddk::Gvec::init                                                |       95.02 ms →       93.84 ms   (-1.24%) |       2   →       2              |      190.03 ms →      187.67 ms   (-1.24%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.26 ms →       70.04 ms   (-1.71%) |       2   →       2              |      142.52 ms →      140.09 ms   (-1.71%) | 
- │   ├ sddk::Gvec_shells                                               |       92.57 ms →      105.64 ms  (+14.13%) |       1   →       1              |       92.57 ms →      105.64 ms  (+14.13%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.68 ms →        1.94 ms  (+15.73%) |       1   →       1              |        1.68 ms →        1.94 ms  (+15.73%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      602.13 ms →      463.26 ms  (-23.06%) |       2   →       2              |        1.20 s  →      926.52 ms  (-23.06%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      146.64 ms →      158.32 ms   (+7.97%) |       1   →       1              |      146.64 ms →      158.32 ms   (+7.97%) | 
- │ ├ sirius::K_point::K_point                                          |        1.31 μs →        5.42 μs (+313.81%) |       4   →       4              |        5.24 μs →       21.69 μs (+313.81%) | 
  │ └ sirius::K_point_set::initialize                                   |      146.57 ms →      158.22 ms   (+7.95%) |       1   →       1              |      146.57 ms →      158.22 ms   (+7.95%) | 
  │   └ sirius::K_point::initialize                                     |       28.52 ms →       28.63 ms   (+0.41%) |       1   →       1              |       28.52 ms →       28.63 ms   (+0.41%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.43 ms →       11.19 ms   (-2.06%) |       1   →       1              |       11.43 ms →       11.19 ms   (-2.06%) | 
  │     │ └ sddk::Gvec::init                                            |        4.94 ms →        4.97 ms   (+0.73%) |       1   →       1              |        4.94 ms →        4.97 ms   (+0.73%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       14.04 μs                             |       1                          |       14.04 μs                             | 
  │     └ sirius::K_point::update                                       |       14.19 ms →       14.59 ms   (+2.83%) |       1   →       1              |       14.19 ms →       14.59 ms   (+2.83%) | 
  │       └ sirius::Beta_projectors                                     |       10.21 ms →       10.60 ms   (+3.87%) |       1   →       1              |       10.21 ms →       10.60 ms   (+3.87%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.26 ms →        8.53 ms   (+3.24%) |       1   →       1              |        8.26 ms →        8.53 ms   (+3.24%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms                             |       2                          |        5.14 ms                             | 
  ├ sirius::Potential                                                   |       56.16 ms →       52.81 ms   (-5.96%) |       1   →       1              |       56.16 ms →       52.81 ms   (-5.96%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.87 ms                             |       6                          |       17.21 ms                             | 
  │ └ sirius::Potential::update                                         |       38.53 ms →       37.93 ms   (-1.58%) |       1   →       1              |       38.53 ms →       37.93 ms   (-1.58%) | 
  │   └ sirius::Potential::generate_local_potential                     |       38.16 ms →       37.56 ms   (-1.58%) |       1   →       1              |       38.16 ms →       37.56 ms   (-1.58%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       28.96 ms →       26.47 ms   (-8.59%) |       1   →       1              |       28.96 ms →       26.47 ms   (-8.59%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.90 ms →        7.94 ms  (-10.73%) |       1   →       1              |        8.90 ms →        7.94 ms  (-10.73%) | 
+ ├ sirius::Density                                                     |       46.06 ms →       40.78 ms  (-11.45%) |       1   →       1              |       46.06 ms →       40.78 ms  (-11.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms                             |       2                          |        5.67 ms                             | 
+ │ └ sirius::Density::update                                           |       40.25 ms →       35.00 ms  (-13.04%) |       1   →       1              |       40.25 ms →       35.00 ms  (-13.04%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       39.93 ms →       34.76 ms  (-12.95%) |       1   →       1              |       39.93 ms →       34.76 ms  (-12.95%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       35.95 ms →       26.41 ms  (-26.55%) |       1   →       1              |       35.95 ms →       26.41 ms  (-26.55%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.64 ms →        7.97 ms (+118.98%) |       1   →       1              |        3.64 ms →        7.97 ms (+118.98%) | 
+ ├ sirius::Density::initial_density                                    |       63.97 ms →       56.99 ms  (-10.91%) |       1   →       1              |       63.97 ms →       56.99 ms  (-10.91%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       35.62 ms →       25.80 ms  (-27.57%) |       1   →       1              |       35.62 ms →       25.80 ms  (-27.57%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.20 ms →        6.64 ms  (+27.76%) |       2   →       2              |       10.39 ms →       13.28 ms  (+27.76%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.53 ms →        4.58 ms   (+1.17%) |       1   →       1              |        4.53 ms →        4.58 ms   (+1.17%) | 
  ├ sirius::Potential::generate                                         |      380.21 ms →      368.81 ms   (-3.00%) |       1   →       1              |      380.21 ms →      368.81 ms   (-3.00%) | 
  │ ├ sirius::Potential::poisson                                        |       42.79 ms →       42.53 ms   (-0.59%) |       1   →       1              |       42.79 ms →       42.53 ms   (-0.59%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.13 ms →       12.00 ms (+190.39%) |       1   →       1              |        4.13 ms →       12.00 ms (+190.39%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.96 ms                             |       1                          |        4.96 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.63 ms                             |       1                          |        4.63 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms                             |       1                          |        4.63 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.82 ms            |                   1              |                         4.82 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      783.23 μs →      693.64 μs  (-11.44%) |       2   →       2              |        1.57 ms →        1.39 ms  (-11.44%) | 
+ │ ├ sirius::Potential::xc                                             |       62.08 ms →       49.36 ms  (-20.49%) |       1   →       1              |       62.08 ms →       49.36 ms  (-20.49%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       62.08 ms →       48.16 ms  (-22.42%) |       1   →       1              |       62.08 ms →       48.16 ms  (-22.42%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms                             |       2                          |        5.09 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        4.78 ms                             |       1                          |        4.78 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        20.04 ms            |                   2              |                        40.08 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.68 ms →        3.70 ms   (+0.79%) |       1   →       1              |        3.68 ms →        3.70 ms   (+0.79%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.69 ms →      268.88 ms   (+0.07%) |       1   →       1              |      268.69 ms →      268.88 ms   (+0.07%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      246.00 ns →      232.00 ns   (-5.69%) |       1   →       1              |      246.00 ns →      232.00 ns   (-5.69%) | 
- ├ sirius::Hamiltonian0                                                |        8.79 ms →       12.74 ms  (+45.00%) |       1   →       1              |        8.79 ms →       12.74 ms  (+45.00%) | 
+ │ ├ sirius::Local_operator                                            |        7.82 ms →        6.03 ms  (-22.90%) |       1   →       1              |        7.82 ms →        6.03 ms  (-22.90%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms                             |       1                          |        2.73 ms                             | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.85 ms →        2.54 ms  (-34.10%) |       1   →       1              |        3.85 ms →        2.54 ms  (-34.10%) | 
+ │ ├ sirius::Non_local_operator                                        |      344.43 μs →       70.79 μs  (-79.45%) |       2   →       2              |      688.86 μs →      141.59 μs  (-79.45%) | 
- │ ├ sirius::D_operator::initialize                                    |      122.66 μs →        2.19 ms (+1685.75%) |       1   →       1              |      122.66 μs →        2.19 ms (+1685.75%) | 
- │ └ sirius::Q_operator::initialize                                    |       91.72 μs →        4.31 ms (+4601.25%) |       1   →       1              |       91.72 μs →        4.31 ms (+4601.25%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.27 s    (-1.98%) |       1   →       1              |        1.30 s  →        1.27 s    (-1.98%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       81.82 ms →       42.11 ms  (-48.54%) |       1   →       1              |       81.82 ms →       42.11 ms  (-48.54%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      267.61 μs →      215.13 μs  (-19.61%) |       1   →       1              |      267.61 μs →      215.13 μs  (-19.61%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       81.55 ms →       41.89 ms  (-48.64%) |       1   →       1              |       81.55 ms →       41.89 ms  (-48.64%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.23 s    (+1.10%) |       1   →       1              |        1.22 s  →        1.23 s    (+1.10%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      111.71 ms                             |       4                          |      446.85 ms                             | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.36 ms →       51.75 ms  (+38.53%) |       1   →       1              |       37.36 ms →       51.75 ms  (+38.53%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.45 ms →        7.92 ms  (+22.81%) |       1   →       1              |        6.45 ms →        7.92 ms  (+22.81%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      512.37 ms →      311.79 ms  (-39.15%) |       1   →       1              |      512.37 ms →      311.79 ms  (-39.15%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      422.01 ms →      243.70 ms  (-42.25%) |       1   →       1              |      422.01 ms →      243.70 ms  (-42.25%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.03 μs →        3.16 μs   (+4.36%) |       1   →       1              |        3.03 μs →        3.16 μs   (+4.36%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.09 μs                             |       1                          |        2.09 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      424.00 ns                             |       1                          |      424.00 ns                             | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      734.00 ns →      652.00 ns  (-11.17%) |       1   →       1              |      734.00 ns →      652.00 ns  (-11.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        2.98 ms →        3.27 ms   (+9.61%) |       1   →       1              |        2.98 ms →        3.27 ms   (+9.61%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       38.96 ms →       21.32 ms  (-45.27%) |       1   →       1              |       38.96 ms →       21.32 ms  (-45.27%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       24.19 ms →       21.72 ms  (-10.18%) |       2   →       2              |       48.38 ms →       43.45 ms  (-10.18%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.20 ms →       16.28 ms (+212.95%) |       2   →       2              |       10.40 ms →       32.55 ms (+212.95%) | 
  │ │ │ ├ sddk::inner                                                   |        4.99 ms                             |       2                          |        9.97 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       17.44 μs                             |       2                          |       34.88 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        16.06 ms            |                   2              |                        32.13 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        65.00 ns            |                   2              |                       130.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        15.93 ms            |                   2              |                        31.87 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       387.00 ns            |                   2              |                       774.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |       66.97 ms →      248.01 ms (+270.30%) |       1   →       1              |       66.97 ms →      248.01 ms (+270.30%) | 
  │ │ ├ sddk::transform                                                 |        2.80 ms                             |       1                          |        2.80 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.70 μs                             |       1                          |       11.70 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       14.91 μs                             |       1                          |       14.91 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      396.00 ns →      391.00 ns   (-1.26%) |       1   →       1              |      396.00 ns →      391.00 ns   (-1.26%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.10 s  →       37.61 s   (-43.95%) |       1   →       1              |       67.10 s  →       37.61 s   (-43.95%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms                             |      19                          |       45.92 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.34 s                              |      20                          |       66.89 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.10 ms                             |      20                          |      102.02 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.39 ms                             |      20                          |       87.90 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      530.20 μs                             |      20                          |       10.60 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.61 ms                             |      20                          |       52.13 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |      213.20 μs                             |      40                          |        8.53 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      108.82 μs                             |      20                          |        2.18 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       94.01 μs                             |      20                          |        1.88 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.11 s                              |      20                          |       42.29 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      197.42 μs                             |      20                          |        3.95 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      188.25 μs                             |      20                          |        3.76 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.25 μs                             |      20                          |      145.10 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s                              |      20                          |       39.38 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       97.83 ms                             |      20                          |        1.96 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.35 ms                             |     120                          |        1.36 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       14.60 ms                             |      20                          |      292.03 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      479.63 μs                             |      20                          |        9.59 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        6.89 ms                             |      40                          |      275.48 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s                              |      20                          |       36.99 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       72.60 ms                             |     250                          |       18.15 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       47.91 ms                             |     250                          |       11.98 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.03 μs                             |     250                          |      506.71 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.65 μs                             |     250                          |      411.86 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      438.36 ns                             |     250                          |      109.59 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      518.78 ns                             |     250                          |      129.70 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.30 ms                             |     250                          |      824.36 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.69 ms                             |     250                          |      923.65 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.84 ms                             |     500                          |        4.42 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.43 ms                             |     250                          |        1.61 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |      895.69 μs                             |     480                          |      429.93 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.32 μs                             |     480                          |       11.19 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      385.81 μs                             |     250                          |       96.45 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.83 ms                             |     250                          |      458.04 ms                             | 
  │ │ │ │   │ └ sddk::transform                                         |        2.71 ms                             |     230                          |      622.18 ms                             | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.22 μs                             |     230                          |        4.42 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |        7.84 μs                             |     690                          |        5.41 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.49 ms                             |     250                          |      372.45 ms                             | 
  │ │ │ │   │ └ sddk::inner                                             |        1.29 ms                             |     250                          |      321.62 ms                             | 
  │ │ │ │   │   └ sddk::inner|local                                     |       24.01 μs                             |     250                          |        6.00 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       63.67 ms                             |     250                          |       15.92 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |        3.02 ms                             |     245                          |      739.60 ms                             | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.91 ms                             |     231                          |      442.07 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.29 μs                             |     231                          |        3.76 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.58 μs                             |     462                          |        4.89 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.21 ms                             |     231                          |      280.16 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.81 ms                             |      25                          |      195.19 ms                             | 
  │ │ │ │     └ sddk::transform                                         |        6.42 ms                             |      30                          |      192.52 ms                             | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.12 μs                             |      30                          |      333.53 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       12.15 μs                             |      35                          |      425.31 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      423.85 ns                             |      20                          |        8.48 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.43 μs                             |      20                          |      448.53 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms                             |      20                          |       29.80 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      564.90 ms                             |      20                          |       11.30 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      385.09 ms                             |      20                          |        7.70 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.92 μs                             |      20                          |      158.46 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.23 μs                             |      20                          |      144.53 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       42.86 ms                             |      20                          |      857.14 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.65 μs                             |      20                          |      153.03 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.45 ms                             |      20                          |      468.99 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       18.36 ms                             |      20                          |      367.22 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      556.20 ns                             |      20                          |       11.12 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       96.64 ms                             |      20                          |        1.93 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.10 ms                             |      20                          |       42.00 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |      201.64 ms                             |      20                          |        4.03 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      201.42 ms                             |      20                          |        4.03 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      150.92 ms                             |      20                          |        3.02 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      150.92 ms                             |      20                          |        3.02 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       70.03 ms                             |      20                          |        1.40 s                              | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       67.63 ms                             |      20                          |        1.35 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.62 ms                             |      20                          |      252.48 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.50 ms                             |      20                          |      469.96 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.38 ms                             |      20                          |      107.67 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      134.89 ms                             |      20                          |        2.70 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      825.47 μs                             |      20                          |       16.51 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.89 ms                             |     244                          |        1.19 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms                             |     244                          |        1.17 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms                             |     244                          |        1.17 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.51 ms                             |      20                          |      130.25 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.69 ms                             |      20                          |      113.87 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      373.75 ms                             |      20                          |        7.47 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       43.15 ms                             |      20                          |      863.05 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.71 ms                             |      20                          |       94.29 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.73 ms                             |      20                          |       94.66 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.62 ms                             |      20                          |       92.38 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms                             |      20                          |       92.36 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      755.54 μs                             |      40                          |       30.22 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       55.73 ms                             |      20                          |        1.11 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       55.73 ms                             |      20                          |        1.11 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      642.06 μs                             |      40                          |       25.68 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.85 ms                             |      20                          |       97.01 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.74 ms                             |      20                          |       74.82 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.22 ms                             |      20                          |        5.36 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      228.90 ns                             |      20                          |        4.58 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       93.72 ms                             |      20                          |        1.87 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       93.72 ms                             |      20                          |        1.87 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.24 ms                             |      20                          |      264.80 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       67.28 ms                             |      20                          |        1.35 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.57 ms                             |      20                          |      251.36 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.37 ms                             |      20                          |       87.35 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.67 ms                             |     140                          |      653.13 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.55 ms                             |     140                          |      636.92 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.55 ms                             |     140                          |      636.82 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.75 ms                             |      60                          |      284.90 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.74 ms                             |      60                          |      284.43 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms                             |      20                          |       90.94 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.07 μs                             |      20                          |        1.52 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.03 μs                             |      20                          |        1.42 ms                             | 
  │ ├ sirius::Density                                                   |                        54.99 ms            |                   1              |                        54.99 ms            | 
  │ │ └ sirius::Density::update                                         |                        49.27 ms            |                   1              |                        49.27 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        49.04 ms            |                   1              |                        49.04 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        26.37 ms            |                   1              |                        26.37 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         8.11 ms            |                   1              |                         8.11 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                        11.13 ms            |                  15              |                       166.90 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.42 ms            |                  15              |                        66.30 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.65 ms            |                  15              |                        39.77 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                       101.21 μs            |                  30              |                         3.04 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         2.19 ms            |                  15              |                        32.90 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         4.25 ms            |                  15              |                        63.69 ms            | 
  │ ├ sirius::Band::solve                                               |                         1.29 s             |                  15              |                        19.34 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       179.57 μs            |                  15              |                         2.69 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       169.14 μs            |                  15              |                         2.54 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         5.61 μs            |                  15              |                        84.18 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         1.13 s             |                  15              |                        16.92 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                        16.06 ms            |                  15              |                       240.94 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                        91.60 ms            |                 116              |                        10.63 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        57.59 ms            |                 116              |                         6.68 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         1.48 μs            |                 116              |                       172.18 μs            | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                       471.38 ns            |                 116              |                        54.68 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         3.43 ms            |                 116              |                       398.38 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                         4.80 ms            |                 116              |                       557.25 ms            | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        12.87 ms            |                 232              |                         2.99 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                         9.73 ms            |                 116              |                         1.13 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         1.69 ms            |                 217              |                       366.99 ms            | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                        88.62 ns            |                 217              |                        19.23 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         1.52 ms            |                 217              |                       329.73 ms            | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       238.90 ns            |                 217              |                        51.84 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                       508.24 μs            |                 116              |                        58.96 ms            | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                         3.45 ms            |                 116              |                       400.47 ms            | 
  │ │ │ │ └ sddk::wf_trans                                              |                         2.98 ms            |                 101              |                       301.35 ms            | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                       993.85 μs            |                 303              |                       301.14 ms            | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         1.65 ms            |                 116              |                       191.55 ms            | 
  │ │ │ │ └ sddk::wf_inner                                              |                         1.59 ms            |                 116              |                       184.47 ms            | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                        99.73 ns            |                 116              |                        11.57 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         1.42 ms            |                 116              |                       165.03 ms            | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       196.16 ns            |                 116              |                        22.75 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        22.38 ms            |                 116              |                         2.60 s             | 
  │ │ │ ├ sirius::residuals                                             |                         3.12 ms            |                 114              |                       356.03 ms            | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         1.54 ms            |                 101              |                       155.67 ms            | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                       769.35 μs            |                 202              |                       155.41 ms            | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.78 ms            |                 101              |                       179.68 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                         5.29 ms            |                  47              |                       248.73 ms            | 
  │ │ │   └ sddk::wf_trans                                              |                         3.10 ms            |                  79              |                       245.03 ms            | 
  │ │ │     └ sddk::wf_trans|pw                                         |                         2.21 ms            |                 111              |                       244.89 ms            | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       368.13 ns            |                  15              |                         5.52 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        62.34 μs            |                  15              |                       935.14 μs            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       998.62 μs            |                  15              |                        14.98 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        13.45 μs            |                  15              |                       201.74 μs            | 
  │ ├ sirius::Density::generate                                         |                       559.90 ms            |                  15              |                         8.40 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       370.11 ms            |                  15              |                         5.55 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                         5.11 μs            |                  15              |                        76.59 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        41.33 ms            |                  15              |                       619.93 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         8.81 μs            |                  15              |                       132.08 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                        22.97 ms            |                  15              |                       344.52 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        17.28 ms            |                  15              |                       259.23 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       516.27 ns            |                  15              |                         7.74 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                        97.40 ms            |                  15              |                         1.46 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         1.82 ms            |                  15              |                        27.36 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                       195.46 ms            |                  15              |                         2.93 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                       195.23 ms            |                  15              |                         2.93 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       162.43 ms            |                  15              |                         2.44 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       162.42 ms            |                  15              |                         2.44 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        83.83 ms            |                  15              |                         1.26 s             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                        65.00 ms            |                  15              |                       974.93 ms            | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        12.94 ms            |                  15              |                       194.12 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        23.59 ms            |                  15              |                       353.78 ms            | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         3.77 ms            |                  15              |                        56.51 ms            | 
  │ ├ sirius::inner                                                     |                         4.84 ms            |                 189              |                       915.06 ms            | 
  │ ├ sirius::Density::mix                                              |                        77.20 ms            |                  15              |                         1.16 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.01 ms            |                  15              |                        15.14 ms            | 
  │ │ ├ sirius::inner                                                   |                         4.78 ms            |                 169              |                       807.00 ms            | 
  │ │ └ sirius::Density::mixer_output                                   |                         5.84 ms            |                  15              |                        87.65 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         4.90 ms            |                  15              |                        73.55 ms            | 
  │ ├ sirius::Potential::generate                                       |                       365.32 ms            |                  15              |                         5.48 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                        42.37 ms            |                  15              |                       635.62 ms            | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                        11.34 ms            |                  15              |                       170.07 ms            | 
  │ │ │ └ sirius::inner                                                 |                         5.37 ms            |                  15              |                        80.53 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       717.07 μs            |                  30              |                        21.51 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        46.80 ms            |                  15              |                       702.06 ms            | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        45.63 ms            |                  15              |                       684.38 ms            | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        19.56 ms            |                  30              |                       586.72 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         3.66 ms            |                  15              |                        54.92 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                       268.12 ms            |                  15              |                         4.02 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       178.53 ns            |                  15              |                         2.68 μs            | 
  │ ├ sirius::Field4D::symmetrize                                       |                        91.69 ms            |                  15              |                         1.38 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                        91.68 ms            |                  15              |                         1.38 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        13.35 ms            |                  15              |                       200.18 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                        64.88 ms            |                  15              |                       973.27 ms            | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        12.82 ms            |                  15              |                       192.36 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         3.69 ms            |                  15              |                        55.40 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                         4.60 ms            |                  15              |                        68.96 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        23.32 ms            |                  15              |                       349.84 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        23.32 ms            |                  15              |                       349.74 ms            | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.54 ms →        5.54 ms   (-0.04%) |       2   →       2              |       11.08 ms →       11.08 ms   (-0.04%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms                             |       6                          |       28.80 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms                             |       6                          |       28.78 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms                             |       6                          |       28.78 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.99 ms                             |       3                          |       14.97 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.99 ms                             |       3                          |       14.96 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.79 ms                             |       2                          |        9.59 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.79 ms                             |       2                          |        9.58 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms                             |       2                          |        9.58 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.96 ms                             |       1                          |        4.96 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.95 ms                             |       1                          |        4.95 ms                             | 
  ├ sirius::inner                                                       |                         4.88 ms            |                   3              |                        14.63 ms            | 
+ └ sirius::finalize                                                    |      929.37 ms →      761.48 ms  (-18.07%) |       1   →       1              |      929.37 ms →      761.48 ms  (-18.07%) | 
  ====================================================================================================================================================================================================
```
