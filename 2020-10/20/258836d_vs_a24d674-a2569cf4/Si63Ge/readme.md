# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       76.99 s  →       72.28 s    (-6.11%) |       1   →       1              |       76.99 s  →       72.28 s    (-6.11%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.90 s    (+1.50%) |       1   →       1              |        2.86 s  →        2.90 s    (+1.50%) | 
  ├ sirius::Simulation_context::initialize                              |        3.72 s  →        3.63 s    (-2.41%) |       1   →       1              |        3.72 s  →        3.63 s    (-2.41%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      916.18 μs →       25.88 ms (+2725.11%) |       1   →       1              |      916.18 μs →       25.88 ms (+2725.11%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      267.46 ms →      207.33 ms  (-22.48%) |       1   →       1              |      267.46 ms →      207.33 ms  (-22.48%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      125.30 ms →       94.57 ms  (-24.52%) |       2   →       2              |      250.60 ms →      189.14 ms  (-24.52%) | 
  │ │ └ sirius::Unit_cell::update                                       |       16.77 ms →       18.09 ms   (+7.88%) |       1   →       1              |       16.77 ms →       18.09 ms   (+7.88%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.63 ms →        5.19 ms  (+43.11%) |       1   →       1              |        3.63 ms →        5.19 ms  (+43.11%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.10 ms →       12.85 ms   (-1.92%) |       1   →       1              |       13.10 ms →       12.85 ms   (-1.92%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.02 ms →       12.77 ms   (-1.90%) |       1   →       1              |       13.02 ms →       12.77 ms   (-1.90%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.77 ms →        2.73 ms   (-1.17%) |       1   →       1              |        2.77 ms →        2.73 ms   (-1.17%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      528.14 μs →      501.70 μs   (-5.01%) |       1   →       1              |      528.14 μs →      501.70 μs   (-5.01%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.21 μs →       16.44 μs   (+1.41%) |       1   →       1              |       16.21 μs →       16.44 μs   (+1.41%) | 
  │ └ sirius::Simulation_context::update                                |        3.26 s  →        3.31 s    (+1.48%) |       1   →       1              |        3.26 s  →        3.31 s    (+1.48%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.01 ms →        7.02 ms   (+0.02%) |       1   →       1              |        7.01 ms →        7.02 ms   (+0.02%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.70 ms →        3.65 ms   (-1.41%) |       1   →       1              |        3.70 ms →        3.65 ms   (-1.41%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.27 ms →        3.32 ms   (+1.56%) |       1   →       1              |        3.27 ms →        3.32 ms   (+1.56%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.25 ms   (+0.83%) |       1   →       1              |        3.23 ms →        3.25 ms   (+0.83%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.69 ms →        2.71 ms   (+0.74%) |       1   →       1              |        2.69 ms →        2.71 ms   (+0.74%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      497.38 μs →      504.81 μs   (+1.49%) |       1   →       1              |      497.38 μs →      504.81 μs   (+1.49%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.88 μs →       13.54 μs   (-2.39%) |       1   →       1              |       13.88 μs →       13.54 μs   (-2.39%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.42 ms →      213.00 ms   (-0.20%) |       2   →       2              |      426.84 ms →      426.00 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.17 ms   (-0.02%) |       2   →       2              |       30.35 ms →       30.34 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.27 ms   (+0.05%) |       1   →       1              |       13.26 ms →       13.27 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.42 ms →       56.34 ms   (-0.16%) |       2   →       2              |      112.85 ms →      112.67 ms   (-0.16%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.25 ms →       45.27 ms   (+0.06%) |       2   →       2              |       90.50 ms →       90.55 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.49 ms →       60.48 ms   (-0.01%) |       4   →       4              |      241.96 ms →      241.94 ms   (-0.01%) | 
  │   ├ sddk::Gvec::init                                                |       96.89 ms →       93.67 ms   (-3.32%) |       2   →       2              |      193.78 ms →      187.34 ms   (-3.32%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.50 ms →       70.14 ms   (-1.90%) |       2   →       2              |      142.99 ms →      140.27 ms   (-1.90%) | 
+ │   ├ sddk::Gvec_shells                                               |      147.53 ms →      100.49 ms  (-31.89%) |       1   →       1              |      147.53 ms →      100.49 ms  (-31.89%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        2.05 ms →        1.97 ms   (-4.31%) |       1   →       1              |        2.05 ms →        1.97 ms   (-4.31%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      456.46 ms →      515.12 ms  (+12.85%) |       2   →       2              |      912.92 ms →        1.03 s   (+12.85%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      157.97 ms →      158.44 ms   (+0.29%) |       1   →       1              |      157.97 ms →      158.44 ms   (+0.29%) | 
  │ ├ sirius::K_point::K_point                                          |        1.14 μs →        1.22 μs   (+6.92%) |       4   →       4              |        4.58 μs →        4.90 μs   (+6.92%) | 
  │ └ sirius::K_point_set::initialize                                   |      157.90 ms →      158.35 ms   (+0.28%) |       1   →       1              |      157.90 ms →      158.35 ms   (+0.28%) | 
  │   └ sirius::K_point::initialize                                     |       29.79 ms →       29.65 ms   (-0.48%) |       1   →       1              |       29.79 ms →       29.65 ms   (-0.48%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       12.04 ms →       11.77 ms   (-2.22%) |       1   →       1              |       12.04 ms →       11.77 ms   (-2.22%) | 
  │     │ └ sddk::Gvec::init                                            |        5.32 ms →        5.33 ms   (+0.33%) |       1   →       1              |        5.32 ms →        5.33 ms   (+0.33%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        6.69 μs →        7.89 μs  (+17.91%) |       1   →       1              |        6.69 μs →        7.89 μs  (+17.91%) | 
  │     └ sirius::K_point::update                                       |       14.52 ms →       15.03 ms   (+3.50%) |       1   →       1              |       14.52 ms →       15.03 ms   (+3.50%) | 
  │       └ sirius::Beta_projectors                                     |       10.18 ms →       10.76 ms   (+5.70%) |       1   →       1              |       10.18 ms →       10.76 ms   (+5.70%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.25 ms →        8.70 ms   (+5.52%) |       1   →       1              |        8.25 ms →        8.70 ms   (+5.52%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.54 ms →        2.59 ms   (+2.03%) |       2   →       2              |        5.07 ms →        5.17 ms   (+2.03%) | 
+ ├ sirius::Potential                                                   |       55.34 ms →       49.64 ms  (-10.30%) |       1   →       1              |       55.34 ms →       49.64 ms  (-10.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.91 ms   (+0.12%) |       6   →       6              |       17.46 ms →       17.49 ms   (+0.12%) | 
+ │ └ sirius::Potential::update                                         |       37.33 ms →       31.52 ms  (-15.58%) |       1   →       1              |       37.33 ms →       31.52 ms  (-15.58%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       36.92 ms →       31.12 ms  (-15.71%) |       1   →       1              |       36.92 ms →       31.12 ms  (-15.71%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       27.05 ms →       24.19 ms  (-10.57%) |       1   →       1              |       27.05 ms →       24.19 ms  (-10.57%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.56 ms →        6.42 ms  (-32.84%) |       1   →       1              |        9.56 ms →        6.42 ms  (-32.84%) | 
+ ├ sirius::Density                                                     |       45.43 ms →       38.72 ms  (-14.78%) |       1   →       1              |       45.43 ms →       38.72 ms  (-14.78%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.82 ms   (-0.19%) |       2   →       2              |        5.66 ms →        5.65 ms   (-0.19%) | 
+ │ └ sirius::Density::update                                           |       39.63 ms →       32.93 ms  (-16.91%) |       1   →       1              |       39.63 ms →       32.93 ms  (-16.91%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       39.32 ms →       32.70 ms  (-16.83%) |       1   →       1              |       39.32 ms →       32.70 ms  (-16.83%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        77.70 μs            |                   1              |                        77.70 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       28.64 ms →       24.15 ms  (-15.67%) |       1   →       1              |       28.64 ms →       24.15 ms  (-15.67%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.35 ms →        8.18 ms  (-20.96%) |       1   →       1              |       10.35 ms →        8.18 ms  (-20.96%) | 
+ ├ sirius::Density::initial_density                                    |       62.25 ms →       55.70 ms  (-10.53%) |       1   →       1              |       62.25 ms →       55.70 ms  (-10.53%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       28.06 ms →       25.14 ms  (-10.40%) |       1   →       1              |       28.06 ms →       25.14 ms  (-10.40%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        8.06 ms →        5.79 ms  (-28.13%) |       2   →       2              |       16.12 ms →       11.58 ms  (-28.13%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.70 ms →        5.34 ms  (+13.70%) |       1   →       1              |        4.70 ms →        5.34 ms  (+13.70%) | 
  ├ sirius::Potential::generate                                         |      371.22 ms →      362.52 ms   (-2.35%) |       1   →       1              |      371.22 ms →      362.52 ms   (-2.35%) | 
+ │ ├ sirius::Potential::poisson                                        |       43.25 ms →       35.04 ms  (-18.97%) |       1   →       1              |       43.25 ms →       35.04 ms  (-18.97%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       12.24 ms →        6.32 ms  (-48.41%) |       1   →       1              |       12.24 ms →        6.32 ms  (-48.41%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.96 ms →        5.74 ms  (+15.59%) |       1   →       1              |        4.96 ms →        5.74 ms  (+15.59%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.65 ms   (+0.44%) |       1   →       1              |        4.63 ms →        4.65 ms   (+0.44%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.62 ms →        4.64 ms   (+0.26%) |       1   →       1              |        4.62 ms →        4.64 ms   (+0.26%) | 
  │ ├ sirius::Periodic_function::add                                    |      782.13 μs →      821.41 μs   (+5.02%) |       2   →       2              |        1.56 ms →        1.64 ms   (+5.02%) | 
  │ ├ sirius::Potential::xc                                             |       52.50 ms →       51.06 ms   (-2.75%) |       1   →       1              |       52.50 ms →       51.06 ms   (-2.75%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.50 ms →       49.85 ms   (-5.05%) |       1   →       1              |       52.50 ms →       49.85 ms   (-5.05%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.54 ms   (+0.45%) |       2   →       2              |        5.06 ms →        5.08 ms   (+0.45%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.80 ms →        4.28 ms  (-10.91%) |       1   →       1              |        4.80 ms →        4.28 ms  (-10.91%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.68 ms →        3.94 ms   (+7.14%) |       1   →       1              |        3.68 ms →        3.94 ms   (+7.14%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.83 ms →      269.43 ms   (+0.22%) |       1   →       1              |      268.83 ms →      269.43 ms   (+0.22%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      187.00 ns →      238.00 ns  (+27.27%) |       1   →       1              |      187.00 ns →      238.00 ns  (+27.27%) | 
  ├ sirius::Hamiltonian0                                                |        7.62 ms →        6.87 ms   (-9.77%) |       1   →       1              |        7.62 ms →        6.87 ms   (-9.77%) | 
+ │ ├ sirius::Local_operator                                            |        7.08 ms →        6.34 ms  (-10.44%) |       1   →       1              |        7.08 ms →        6.34 ms  (-10.44%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.77 ms   (+1.10%) |       1   →       1              |        2.74 ms →        2.77 ms   (+1.10%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.25 ms →        2.78 ms  (-14.39%) |       1   →       1              |        3.25 ms →        2.78 ms  (-14.39%) | 
+ │ ├ sirius::Non_local_operator                                        |      124.40 μs →       72.70 μs  (-41.56%) |       2   →       2              |      248.79 μs →      145.40 μs  (-41.56%) | 
- │ ├ sirius::D_operator::initialize                                    |      112.56 μs →      180.94 μs  (+60.76%) |       1   →       1              |      112.56 μs →      180.94 μs  (+60.76%) | 
  │ └ sirius::Q_operator::initialize                                    |       93.73 μs →      102.48 μs   (+9.34%) |       1   →       1              |       93.73 μs →      102.48 μs   (+9.34%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.28 s    (+0.94%) |       1   →       1              |        1.27 s  →        1.28 s    (+0.94%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       61.23 ms →       44.58 ms  (-27.19%) |       1   →       1              |       61.23 ms →       44.58 ms  (-27.19%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      309.23 μs →      285.39 μs   (-7.71%) |       1   →       1              |      309.23 μs →      285.39 μs   (-7.71%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       60.92 ms →       44.29 ms  (-27.30%) |       1   →       1              |       60.92 ms →       44.29 ms  (-27.30%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.21 s  →        1.24 s    (+2.37%) |       1   →       1              |        1.21 s  →        1.24 s    (+2.37%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.77 ms →       78.15 ms  (-13.91%) |       4   →       4              |      363.10 ms →      312.58 ms  (-13.91%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       36.03 ms →       47.78 ms  (+32.62%) |       1   →       1              |       36.03 ms →       47.78 ms  (+32.62%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.86 ms →        7.73 ms  (+12.54%) |       1   →       1              |        6.86 ms →        7.73 ms  (+12.54%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      380.26 ms →      311.88 ms  (-17.98%) |       1   →       1              |      380.26 ms →      311.88 ms  (-17.98%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      288.58 ms →      244.18 ms  (-15.39%) |       1   →       1              |      288.58 ms →      244.18 ms  (-15.39%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.62 μs →        3.77 μs  (-18.36%) |       1   →       1              |        4.62 μs →        3.77 μs  (-18.36%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.41 μs →        2.77 μs  (-18.89%) |       1   →       1              |        3.41 μs →        2.77 μs  (-18.89%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      509.00 ns →      466.00 ns   (-8.45%) |       1   →       1              |      509.00 ns →      466.00 ns   (-8.45%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      652.00 ns →      595.00 ns   (-8.74%) |       1   →       1              |      652.00 ns →      595.00 ns   (-8.74%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.10 ms →        3.11 ms   (+0.38%) |       1   →       1              |        3.10 ms →        3.11 ms   (+0.38%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       38.25 ms →       21.36 ms  (-44.17%) |       1   →       1              |       38.25 ms →       21.36 ms  (-44.17%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       25.14 ms →       21.59 ms  (-14.13%) |       2   →       2              |       50.28 ms →       43.18 ms  (-14.13%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.29 ms →       15.93 ms (+201.50%) |       2   →       2              |       10.57 ms →       31.87 ms (+201.50%) | 
  │ │ │ ├ sddk::inner                                                   |        5.07 ms                             |       2                          |       10.14 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       24.93 μs                             |       2                          |       49.86 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.73 ms            |                   2              |                        31.45 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        20.00 ns            |                   2              |                        40.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        15.60 ms            |                   2              |                        31.20 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        26.50 ns            |                   2              |                        53.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      200.40 ms →      250.48 ms  (+24.99%) |       1   →       1              |      200.40 ms →      250.48 ms  (+24.99%) | 
  │ │ ├ sddk::transform                                                 |        2.87 ms                             |       1                          |        2.87 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       13.96 μs                             |       1                          |       13.96 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       16.04 μs                             |       1                          |       16.04 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         4.87 ms            |                   1              |                         4.87 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         4.86 ms            |                   1              |                         4.86 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      414.00 ns →      475.00 ns  (+14.73%) |       1   →       1              |      414.00 ns →      475.00 ns  (+14.73%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       67.03 s  →       62.68 s    (-6.49%) |       1   →       1              |       67.03 s  →       62.68 s    (-6.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms →        2.46 ms   (+1.33%) |      19   →      19              |       46.10 ms →       46.72 ms   (+1.33%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.34 s  →        2.97 s   (-11.08%) |      20   →      21     (+5.00%) |       66.73 s  →       62.30 s    (-6.63%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.57 ms →        5.15 ms   (-7.64%) |      20   →      21     (+5.00%) |      111.49 ms →      108.12 ms   (-3.02%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.96 ms →        4.47 ms   (-9.94%) |      20   →      21     (+5.00%) |       99.30 ms →       93.90 ms   (-5.44%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      549.69 μs →      556.90 μs   (+1.31%) |      20   →      21     (+5.00%) |       10.99 ms →       11.69 ms   (+6.38%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.10 ms →        2.80 ms   (-9.90%) |      20   →      21     (+5.00%) |       62.09 ms →       58.74 ms   (-5.40%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      159.33 μs →      197.51 μs  (+23.96%) |      40   →      42     (+5.00%) |        6.37 ms →        8.30 ms  (+30.16%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      113.62 μs →      113.41 μs   (-0.18%) |      20   →      21     (+5.00%) |        2.27 ms →        2.38 ms   (+4.81%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       98.22 μs →       91.13 μs   (-7.22%) |      20   →      21     (+5.00%) |        1.96 ms →        1.91 ms   (-2.58%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.11 s  →        1.75 s   (-17.04%) |      20   →      21     (+5.00%) |       42.20 s  →       36.76 s   (-12.89%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      207.77 μs →      234.66 μs  (+12.94%) |      20   →      21     (+5.00%) |        4.16 ms →        4.93 ms  (+18.59%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.81 μs →      225.49 μs  (+13.42%) |      20   →      21     (+5.00%) |        3.98 ms →        4.74 ms  (+19.09%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.92 μs →        6.74 μs   (-2.56%) |      20   →      21     (+5.00%) |      138.44 μs →      141.64 μs   (+2.31%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.63 s   (-16.76%) |      20   →      21     (+5.00%) |       39.10 s  →       34.18 s   (-12.60%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       97.16 ms →       66.42 ms  (-31.65%) |      20   →      21     (+5.00%) |        1.94 s  →        1.39 s   (-28.23%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.60 ms →        7.21 ms  (-37.80%) |     120   →     126     (+5.00%) |        1.39 s  →      908.84 ms  (-34.69%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.00 ms →       16.88 ms  (+12.55%) |      20   →      21     (+5.00%) |      300.02 ms →      354.55 ms  (+18.17%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      492.54 μs →      458.76 μs   (-6.86%) |      20   →      21     (+5.00%) |        9.85 ms →        9.63 ms   (-2.20%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.07 ms →        7.59 ms   (+7.40%) |      40   →      42     (+5.00%) |      282.77 ms →      318.89 ms  (+12.77%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s  →        1.54 s   (-16.38%) |      20   →      21     (+5.00%) |       36.72 s  →       32.24 s   (-12.19%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.26 ms →       49.52 ms  (-28.50%) |     250   →     361    (+44.40%) |       17.32 s  →       17.88 s    (+3.25%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.28 ms →       29.70 ms  (-31.38%) |     250   →     361    (+44.40%) |       10.82 s  →       10.72 s    (-0.91%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.99 μs →        2.23 μs  (+12.12%) |     250   →     361    (+44.40%) |      498.00 μs →      806.31 μs  (+61.91%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.63 μs →        1.87 μs  (+14.58%) |     250   →     361    (+44.40%) |      407.89 μs →      674.87 μs  (+65.45%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      370.88 ns →      473.80 ns  (+27.75%) |     250   →     361    (+44.40%) |       92.72 μs →      171.04 μs  (+84.47%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      397.89 ns →      723.25 ns  (+81.77%) |     250   →     361    (+44.40%) |       99.47 μs →      261.09 μs (+162.48%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.19 ms →        2.85 ms  (-10.56%) |     250   →     361    (+44.40%) |      796.26 ms →        1.03 s   (+29.15%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.92 ms →        3.27 ms  (-16.65%) |     250   →     361    (+44.40%) |      979.39 ms →        1.18 s   (+20.36%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.43 ms →        6.85 ms  (-27.42%) |     500   →     722    (+44.40%) |        4.72 s  →        4.94 s    (+4.80%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        7.61 ms →        6.44 ms  (-15.43%) |     250   →     361    (+44.40%) |        1.90 s  →        2.32 s   (+22.12%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.07 ms                             |     480                          |      512.67 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.45 μs                             |     480                          |       10.30 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.04 ms            |                 701              |                       732.16 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        52.01 ns            |                 701              |                        36.46 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       880.91 μs            |                 701              |                       617.52 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        46.13 ns            |                 701              |                        32.33 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      187.51 μs →      136.94 μs  (-26.97%) |     250   →     361    (+44.40%) |       46.88 ms →       49.43 ms   (+5.45%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.45 ms →        1.93 ms  (-21.28%) |     250   →     361    (+44.40%) |      612.88 ms →      696.71 ms  (+13.68%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.17 ms                             |     230                          |      729.46 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.36 μs                             |     230                          |        3.99 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        7.04 μs                             |     690                          |        4.86 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.48 ms            |                 340              |                       844.32 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       826.93 μs            |                1.02 K            |                       843.47 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.61 ms →        1.24 ms  (-23.23%) |     250   →     361    (+44.40%) |      402.81 ms →      446.56 ms  (+10.86%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.40 ms                             |     250                          |      349.89 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       22.29 μs                             |     250                          |        5.57 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.19 ms            |                 361              |                       429.30 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        42.58 ns            |                 361              |                        15.37 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.03 ms            |                 361              |                       370.57 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        47.01 ns            |                 361              |                        16.97 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       64.43 ms →       28.71 ms  (-55.43%) |     250   →     361    (+44.40%) |       16.11 s  →       10.37 s   (-35.65%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        3.19 ms →        2.31 ms  (-27.42%) |     245   →     346    (+41.22%) |      781.16 ms →      800.71 ms   (+2.50%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.06 ms                             |     231                          |      475.81 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.09 μs                             |     231                          |        3.26 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.44 μs                             |     462                          |        4.36 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.10 ms            |                 342              |                       377.88 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       550.99 μs            |                 684              |                       376.87 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.25 ms →        1.15 ms   (-7.88%) |     231   →     342    (+48.05%) |      288.03 ms →      392.85 ms  (+36.39%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        8.12 ms →        4.66 ms  (-42.64%) |      25   →      90   (+260.00%) |      203.00 ms →      419.22 ms (+106.51%) | 
  │ │ │ │     ├ sddk::transform                                         |        6.69 ms                             |      30                          |      200.58 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.56 μs                             |      30                          |      316.74 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       11.57 μs                             |      35                          |      405.03 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         2.58 ms            |                 159              |                       410.68 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         1.80 ms            |                 228              |                       410.36 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      410.65 ns →      563.24 ns  (+37.16%) |      20   →      21     (+5.00%) |        8.21 μs →       11.83 μs  (+44.02%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.72 μs →       19.61 μs  (-13.69%) |      20   →      21     (+5.00%) |      454.43 μs →      411.83 μs   (-9.37%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.53 ms   (+0.93%) |      20   →      21     (+5.00%) |       30.30 ms →       32.11 ms   (+5.98%) | 
  │ │ ├ sirius::Density::generate                                       |      569.14 ms →      563.17 ms   (-1.05%) |      20   →      21     (+5.00%) |       11.38 s  →       11.83 s    (+3.90%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      377.64 ms →      393.22 ms   (+4.13%) |      20   →      21     (+5.00%) |        7.55 s  →        8.26 s    (+9.33%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.07 μs →        7.92 μs   (-1.92%) |      20   →      21     (+5.00%) |      161.42 μs →      166.23 μs   (+2.98%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.47 μs →        7.43 μs   (-0.60%) |      20   →      21     (+5.00%) |      149.48 μs →      156.02 μs   (+4.37%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       43.33 ms →       20.27 ms  (-53.23%) |      20   →      21     (+5.00%) |      866.64 ms →      425.61 ms  (-50.89%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.43 μs →        8.08 μs   (+8.72%) |      20   →      21     (+5.00%) |      148.54 μs →      169.58 μs  (+14.16%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.50 ms →        3.38 ms  (-85.60%) |      20   →      21     (+5.00%) |      469.98 ms →       71.06 ms  (-84.88%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       18.78 ms →       15.82 ms  (-15.74%) |      20   →      21     (+5.00%) |      375.63 ms →      332.32 ms  (-11.53%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      751.55 ns →        1.12 μs  (+49.22%) |      20   →      21     (+5.00%) |       15.03 μs →       23.55 μs  (+56.68%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       96.10 ms →      125.59 ms  (+30.69%) |      20   →      21     (+5.00%) |        1.92 s  →        2.64 s   (+37.22%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.79 ms →        2.00 ms  (+11.95%) |      20   →      21     (+5.00%) |       35.81 ms →       42.10 ms  (+17.54%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      191.07 ms →      207.43 ms   (+8.56%) |      20   →      21     (+5.00%) |        3.82 s  →        4.36 s   (+13.99%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      190.84 ms →      207.20 ms   (+8.57%) |      20   →      21     (+5.00%) |        3.82 s  →        4.35 s   (+14.00%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      163.31 ms →      143.29 ms  (-12.26%) |      20   →      21     (+5.00%) |        3.27 s  →        3.01 s    (-7.87%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      163.31 ms →      143.29 ms  (-12.26%) |      20   →      21     (+5.00%) |        3.27 s  →        3.01 s    (-7.87%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       79.79 ms →       58.93 ms  (-26.14%) |      20   →      21     (+5.00%) |        1.60 s  →        1.24 s   (-22.45%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.29 ms →       69.52 ms   (+1.80%) |      20   →      21     (+5.00%) |        1.37 s  →        1.46 s    (+6.89%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.59 ms →       14.19 ms   (-2.73%) |      20   →      21     (+5.00%) |      291.71 ms →      297.92 ms   (+2.13%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.80 ms →       23.55 ms   (-1.03%) |      20   →      21     (+5.00%) |      475.92 ms →      494.57 ms   (+3.92%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.39 ms →        3.10 ms  (-29.31%) |      20   →      21     (+5.00%) |       87.70 ms →       65.10 ms  (-25.78%) | 
  │ │ ├ sirius::Density::mix                                            |      132.82 ms →      136.10 ms   (+2.46%) |      20   →      21     (+5.00%) |        2.66 s  →        2.86 s    (+7.59%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      522.96 μs →        1.05 ms (+101.29%) |      20   →      21     (+5.00%) |       10.46 ms →       22.11 ms (+111.36%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.75 ms →        4.92 ms   (+3.65%) |     244   →     259     (+6.15%) |        1.16 s  →        1.27 s   (+10.03%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.62 ms →        4.82 ms   (+4.42%) |     244   →     259     (+6.15%) |        1.13 s  →        1.25 s   (+10.84%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.62 ms →        4.82 ms   (+4.42%) |     244   →     259     (+6.15%) |        1.13 s  →        1.25 s   (+10.84%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        5.60 ms →        5.72 ms   (+2.23%) |      20   →      21     (+5.00%) |      112.00 ms →      120.22 ms   (+7.34%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.91 ms →        4.94 ms   (+0.48%) |      20   →      21     (+5.00%) |       98.25 ms →      103.66 ms   (+5.51%) | 
  │ │ ├ sirius::Potential::generate                                     |      362.23 ms →      356.26 ms   (-1.65%) |      20   →      21     (+5.00%) |        7.24 s  →        7.48 s    (+3.27%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       43.12 ms →       35.74 ms  (-17.11%) |      20   →      21     (+5.00%) |      862.41 ms →      750.56 ms  (-12.97%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       12.45 ms →        6.82 ms  (-45.18%) |      20   →      21     (+5.00%) |      249.01 ms →      143.32 ms  (-42.44%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.63 ms →        5.83 ms  (+25.98%) |      20   →      21     (+5.00%) |       92.56 ms →      122.44 ms  (+32.28%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.62 ms →        4.64 ms   (+0.30%) |      20   →      21     (+5.00%) |       92.47 ms →       97.38 ms   (+5.31%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms →        4.64 ms   (+0.29%) |      20   →      21     (+5.00%) |       92.45 ms →       97.35 ms   (+5.31%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      775.41 μs →      808.21 μs   (+4.23%) |      40   →      42     (+5.00%) |       31.02 ms →       33.94 ms   (+9.44%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       43.91 ms →       44.61 ms   (+1.59%) |      20   →      21     (+5.00%) |      878.17 ms →      936.77 ms   (+6.67%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.91 ms →       43.42 ms   (-1.10%) |      20   →      21     (+5.00%) |      878.10 ms →      911.89 ms   (+3.85%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      654.20 μs →      678.16 μs   (+3.66%) |      40   →      42     (+5.00%) |       26.17 ms →       28.48 ms   (+8.85%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.78 ms →        4.27 ms  (-10.66%) |      20   →      21     (+5.00%) |       95.57 ms →       89.65 ms   (-6.20%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.66 ms →        3.86 ms   (+5.64%) |      20   →      21     (+5.00%) |       73.13 ms →       81.11 ms  (+10.92%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.60 ms →      269.02 ms   (+0.16%) |      20   →      21     (+5.00%) |        5.37 s  →        5.65 s    (+5.16%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      199.25 ns →      257.29 ns  (+29.13%) |      20   →      21     (+5.00%) |        3.99 μs →        5.40 μs  (+35.58%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       98.56 ms →       98.75 ms   (+0.20%) |      20   →      21     (+5.00%) |        1.97 s  →        2.07 s    (+5.21%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       98.56 ms →       98.75 ms   (+0.20%) |      20   →      21     (+5.00%) |        1.97 s  →        2.07 s    (+5.21%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.31 ms →       14.74 ms   (-3.75%) |      20   →      21     (+5.00%) |      306.20 ms →      309.44 ms   (+1.06%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.09 ms →       68.91 ms   (+1.21%) |      20   →      21     (+5.00%) |        1.36 s  →        1.45 s    (+6.27%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.53 ms →       14.47 ms   (-0.37%) |      20   →      21     (+5.00%) |      290.57 ms →      303.97 ms   (+4.61%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.58 ms →        2.92 ms  (-36.30%) |      20   →      21     (+5.00%) |       91.67 ms →       61.31 ms  (-33.12%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.61 ms →        4.68 ms   (+1.54%) |     140   →     147     (+5.00%) |      645.27 ms →      687.95 ms   (+6.61%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.57 ms   (-0.12%) |     140   →     147     (+5.00%) |      640.24 ms →      671.47 ms   (+4.88%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.57 ms   (-0.11%) |     140   →     147     (+5.00%) |      640.12 ms →      671.37 ms   (+4.88%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.74 ms →        4.75 ms   (+0.34%) |      60   →      63     (+5.00%) |      284.28 ms →      299.50 ms   (+5.35%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.75 ms   (+0.37%) |      60   →      63     (+5.00%) |      283.74 ms →      299.04 ms   (+5.39%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.95 ms →        4.94 ms   (-0.25%) |      20   →      21     (+5.00%) |       98.95 ms →      103.64 ms   (+4.74%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       78.35 μs →       74.72 μs   (-4.64%) |      20   →      21     (+5.00%) |        1.57 ms →        1.57 ms   (+0.13%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       73.28 μs →       69.92 μs   (-4.59%) |      20   →      21     (+5.00%) |        1.47 ms →        1.47 ms   (+0.18%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.56 ms →        5.11 ms   (-8.20%) |       2   →       2              |       11.12 ms →       10.21 ms   (-8.20%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.79 ms →        4.82 ms   (+0.53%) |       6   →       6              |       28.76 ms →       28.91 ms   (+0.53%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.79 ms →        4.81 ms   (+0.53%) |       6   →       6              |       28.73 ms →       28.89 ms   (+0.53%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.79 ms →        4.81 ms   (+0.54%) |       6   →       6              |       28.73 ms →       28.88 ms   (+0.54%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.99 ms →        4.98 ms   (-0.09%) |       3   →       3              |       14.97 ms →       14.95 ms   (-0.09%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.98 ms →        4.98 ms   (-0.16%) |       3   →       3              |       14.95 ms →       14.93 ms   (-0.16%) | 
  ├ sirius::Periodic_function|inner                                     |        4.53 ms →        4.78 ms   (+5.39%) |       2   →       2              |        9.07 ms →        9.56 ms   (+5.39%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.78 ms   (+5.39%) |       2   →       2              |        9.06 ms →        9.55 ms   (+5.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.78 ms   (+5.40%) |       2   →       2              |        9.06 ms →        9.55 ms   (+5.40%) | 
- ├ sirius::Smooth_periodic_function|inner                              |        4.75 ms →        5.53 ms  (+16.41%) |       1   →       1              |        4.75 ms →        5.53 ms  (+16.41%) | 
- │ └ sirius::Smooth_periodic_function|inner_local                      |        4.75 ms →        5.53 ms  (+16.43%) |       1   →       1              |        4.75 ms →        5.53 ms  (+16.43%) | 
+ └ sirius::finalize                                                    |      936.96 ms →      149.06 ms  (-84.09%) |       1   →       1              |      936.96 ms →      149.06 ms  (-84.09%) | 
  ====================================================================================================================================================================================================
```
