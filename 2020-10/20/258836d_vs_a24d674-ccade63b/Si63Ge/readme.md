# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       76.87 s  →       72.22 s    (-6.05%) |       1   →       1              |       76.87 s  →       72.22 s    (-6.05%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.85 s    (+3.08%) |       1   →       1              |        2.77 s  →        2.85 s    (+3.08%) | 
  ├ sirius::Simulation_context::initialize                              |        3.92 s  →        3.69 s    (-6.01%) |       1   →       1              |        3.92 s  →        3.69 s    (-6.01%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       28.63 ms →      352.81 μs  (-98.77%) |       1   →       1              |       28.63 ms →      352.81 μs  (-98.77%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      202.26 ms →      133.20 ms  (-34.15%) |       1   →       1              |      202.26 ms →      133.20 ms  (-34.15%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       91.93 ms →       56.79 ms  (-38.22%) |       2   →       2              |      183.86 ms →      113.59 ms  (-38.22%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.31 ms →       19.52 ms   (+6.57%) |       1   →       1              |       18.31 ms →       19.52 ms   (+6.57%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.23 ms →        5.18 ms   (-1.08%) |       1   →       1              |        5.23 ms →        5.18 ms   (-1.08%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       12.99 ms →       14.28 ms   (+9.99%) |       1   →       1              |       12.99 ms →       14.28 ms   (+9.99%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       12.91 ms →       14.20 ms   (+9.99%) |       1   →       1              |       12.91 ms →       14.20 ms   (+9.99%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        3.33 ms  (+20.68%) |       1   →       1              |        2.76 ms →        3.33 ms  (+20.68%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      557.35 μs →      509.79 μs   (-8.53%) |       1   →       1              |      557.35 μs →      509.79 μs   (-8.53%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.87 μs →       16.39 μs   (-2.87%) |       1   →       1              |       16.87 μs →       16.39 μs   (-2.87%) | 
  │ └ sirius::Simulation_context::update                                |        3.50 s  →        3.44 s    (-1.58%) |       1   →       1              |        3.50 s  →        3.44 s    (-1.58%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.04 ms →        7.02 ms   (-0.27%) |       1   →       1              |        7.04 ms →        7.02 ms   (-0.27%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.67 ms →        3.65 ms   (-0.51%) |       1   →       1              |        3.67 ms →        3.65 ms   (-0.51%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        3.33 ms   (-0.04%) |       1   →       1              |        3.33 ms →        3.33 ms   (-0.04%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.26 ms   (-0.34%) |       1   →       1              |        3.27 ms →        3.26 ms   (-0.34%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.70 ms   (-0.82%) |       1   →       1              |        2.72 ms →        2.70 ms   (-0.82%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      507.72 μs →      510.95 μs   (+0.64%) |       1   →       1              |      507.72 μs →      510.95 μs   (+0.64%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.51 μs →       21.59 μs  (+48.81%) |       1   →       1              |       14.51 μs →       21.59 μs  (+48.81%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      216.92 ms →      213.24 ms   (-1.70%) |       2   →       2              |      433.84 ms →      426.48 ms   (-1.70%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.21 ms →       15.16 ms   (-0.28%) |       2   →       2              |       30.41 ms →       30.33 ms   (-0.28%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.26 ms   (-0.00%) |       1   →       1              |       13.26 ms →       13.26 ms   (-0.00%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.41 ms →       56.38 ms   (-0.06%) |       2   →       2              |      112.82 ms →      112.75 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.41 ms →       45.23 ms   (-0.40%) |       2   →       2              |       90.83 ms →       90.46 ms   (-0.40%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.00 ms →       60.47 ms   (+0.78%) |       4   →       4              |      240.02 ms →      241.90 ms   (+0.78%) | 
  │   ├ sddk::Gvec::init                                                |       97.48 ms →       93.75 ms   (-3.83%) |       2   →       2              |      194.95 ms →      187.49 ms   (-3.83%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.06 ms →       69.10 ms   (-2.77%) |       2   →       2              |      142.13 ms →      138.19 ms   (-2.77%) | 
  │   ├ sddk::Gvec_shells                                               |      105.67 ms →       97.99 ms   (-7.27%) |       1   →       1              |      105.67 ms →       97.99 ms   (-7.27%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.98 ms →        1.96 ms   (-0.63%) |       1   →       1              |        1.98 ms →        1.96 ms   (-0.63%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      549.85 ms →      554.87 ms   (+0.91%) |       2   →       2              |        1.10 s  →        1.11 s    (+0.91%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      155.41 ms →      135.18 ms  (-13.02%) |       1   →       1              |      155.41 ms →      135.18 ms  (-13.02%) | 
  │ ├ sirius::K_point::K_point                                          |        2.08 μs →        2.19 μs   (+4.93%) |       4   →       4              |        8.33 μs →        8.74 μs   (+4.93%) | 
+ │ └ sirius::K_point_set::initialize                                   |      155.35 ms →      135.10 ms  (-13.03%) |       1   →       1              |      155.35 ms →      135.10 ms  (-13.03%) | 
  │   └ sirius::K_point::initialize                                     |       31.06 ms →       28.63 ms   (-7.80%) |       1   →       1              |       31.06 ms →       28.63 ms   (-7.80%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       12.05 ms →       10.78 ms  (-10.56%) |       1   →       1              |       12.05 ms →       10.78 ms  (-10.56%) | 
  │     │ └ sddk::Gvec::init                                            |        5.39 ms →        4.87 ms   (-9.55%) |       1   →       1              |        5.39 ms →        4.87 ms   (-9.55%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.16 μs →        9.56 μs  (+17.21%) |       1   →       1              |        8.16 μs →        9.56 μs  (+17.21%) | 
  │     └ sirius::K_point::update                                       |       15.13 ms →       14.95 ms   (-1.21%) |       1   →       1              |       15.13 ms →       14.95 ms   (-1.21%) | 
  │       └ sirius::Beta_projectors                                     |       10.69 ms →       11.02 ms   (+3.12%) |       1   →       1              |       10.69 ms →       11.02 ms   (+3.12%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.72 ms →        8.87 ms   (+1.67%) |       1   →       1              |        8.72 ms →        8.87 ms   (+1.67%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.57 ms   (+0.91%) |       2   →       2              |        5.10 ms →        5.14 ms   (+0.91%) | 
  ├ sirius::Potential                                                   |       53.57 ms →       50.94 ms   (-4.90%) |       1   →       1              |       53.57 ms →       50.94 ms   (-4.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.91 ms   (+0.65%) |       6   →       6              |       17.33 ms →       17.44 ms   (+0.65%) | 
  │ └ sirius::Potential::update                                         |       35.63 ms →       32.89 ms   (-7.68%) |       1   →       1              |       35.63 ms →       32.89 ms   (-7.68%) | 
  │   └ sirius::Potential::generate_local_potential                     |       35.24 ms →       32.49 ms   (-7.82%) |       1   →       1              |       35.24 ms →       32.49 ms   (-7.82%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.01 ms →       26.30 ms  (-15.17%) |       1   →       1              |       31.01 ms →       26.30 ms  (-15.17%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.90 ms →        5.65 ms  (+45.01%) |       1   →       1              |        3.90 ms →        5.65 ms  (+45.01%) | 
+ ├ sirius::Density                                                     |       45.76 ms →       39.95 ms  (-12.70%) |       1   →       1              |       45.76 ms →       39.95 ms  (-12.70%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.78 ms   (-1.37%) |       2   →       2              |        5.64 ms →        5.56 ms   (-1.37%) | 
+ │ └ sirius::Density::update                                           |       39.98 ms →       34.25 ms  (-14.33%) |       1   →       1              |       39.98 ms →       34.25 ms  (-14.33%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       39.70 ms →       34.04 ms  (-14.28%) |       1   →       1              |       39.70 ms →       34.04 ms  (-14.28%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        74.83 μs            |                   1              |                        74.83 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       36.47 ms →       26.36 ms  (-27.71%) |       1   →       1              |       36.47 ms →       26.36 ms  (-27.71%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.89 ms →        7.31 ms (+153.11%) |       1   →       1              |        2.89 ms →        7.31 ms (+153.11%) | 
  ├ sirius::Density::initial_density                                    |       63.39 ms →       58.31 ms   (-8.01%) |       1   →       1              |       63.39 ms →       58.31 ms   (-8.01%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       35.94 ms →       26.71 ms  (-25.67%) |       1   →       1              |       35.94 ms →       26.71 ms  (-25.67%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.66 ms →        6.19 ms  (+32.89%) |       2   →       2              |        9.31 ms →       12.37 ms  (+32.89%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.73 ms →        5.71 ms  (+20.78%) |       1   →       1              |        4.73 ms →        5.71 ms  (+20.78%) | 
  ├ sirius::Potential::generate                                         |      368.76 ms →      365.34 ms   (-0.93%) |       1   →       1              |      368.76 ms →      365.34 ms   (-0.93%) | 
+ │ ├ sirius::Potential::poisson                                        |       42.61 ms →       38.11 ms  (-10.56%) |       1   →       1              |       42.61 ms →       38.11 ms  (-10.56%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.66 ms →        6.67 ms  (+82.11%) |       1   →       1              |        3.66 ms →        6.67 ms  (+82.11%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.64 ms →        5.92 ms  (+27.53%) |       1   →       1              |        4.64 ms →        5.92 ms  (+27.53%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.65 ms   (+0.35%) |       1   →       1              |        4.63 ms →        4.65 ms   (+0.35%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.64 ms   (+0.16%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.16%) | 
  │ ├ sirius::Periodic_function::add                                    |      785.11 μs →      785.15 μs   (+0.00%) |       2   →       2              |        1.57 ms →        1.57 ms   (+0.00%) | 
  │ ├ sirius::Potential::xc                                             |       50.81 ms →       50.97 ms   (+0.32%) |       1   →       1              |       50.81 ms →       50.97 ms   (+0.32%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.80 ms →       49.77 ms   (-2.04%) |       1   →       1              |       50.80 ms →       49.77 ms   (-2.04%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.53 ms   (-0.41%) |       2   →       2              |        5.08 ms →        5.06 ms   (-0.41%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.95 ms →        3.99 ms  (-19.43%) |       1   →       1              |        4.95 ms →        3.99 ms  (-19.43%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.11 ms →        3.52 ms  (+13.45%) |       1   →       1              |        3.11 ms →        3.52 ms  (+13.45%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.25 ms →      269.78 ms   (+0.20%) |       1   →       1              |      269.25 ms →      269.78 ms   (+0.20%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      142.00 ns →      233.00 ns  (+64.08%) |       1   →       1              |      142.00 ns →      233.00 ns  (+64.08%) | 
+ ├ sirius::Hamiltonian0                                                |        8.64 ms →        6.89 ms  (-20.24%) |       1   →       1              |        8.64 ms →        6.89 ms  (-20.24%) | 
+ │ ├ sirius::Local_operator                                            |        7.74 ms →        6.36 ms  (-17.85%) |       1   →       1              |        7.74 ms →        6.36 ms  (-17.85%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.75 ms   (+0.11%) |       1   →       1              |        2.75 ms →        2.75 ms   (+0.11%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.84 ms →        2.81 ms  (-26.85%) |       1   →       1              |        3.84 ms →        2.81 ms  (-26.85%) | 
+ │ ├ sirius::Non_local_operator                                        |      318.49 μs →       89.11 μs  (-72.02%) |       2   →       2              |      636.98 μs →      178.22 μs  (-72.02%) | 
- │ ├ sirius::D_operator::initialize                                    |      105.83 μs →      164.07 μs  (+55.03%) |       1   →       1              |      105.83 μs →      164.07 μs  (+55.03%) | 
- │ └ sirius::Q_operator::initialize                                    |       92.95 μs →      102.47 μs  (+10.24%) |       1   →       1              |       92.95 μs →      102.47 μs  (+10.24%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.27 s    (-2.33%) |       1   →       1              |        1.30 s  →        1.27 s    (-2.33%) | 
  │ ├ sirius::Hamiltonian_k                                             |       66.23 ms →       66.66 ms   (+0.64%) |       1   →       1              |       66.23 ms →       66.66 ms   (+0.64%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      233.26 μs →      266.61 μs  (+14.29%) |       1   →       1              |      233.26 μs →      266.61 μs  (+14.29%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       65.99 ms →       66.38 ms   (+0.59%) |       1   →       1              |       65.99 ms →       66.38 ms   (+0.59%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.20 s    (-2.49%) |       1   →       1              |        1.23 s  →        1.20 s    (-2.49%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       89.64 ms →       84.88 ms   (-5.30%) |       4   →       4              |      358.55 ms →      339.54 ms   (-5.30%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       54.50 ms →       47.53 ms  (-12.80%) |       1   →       1              |       54.50 ms →       47.53 ms  (-12.80%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.67 ms →        7.93 ms   (-8.48%) |       1   →       1              |        8.67 ms →        7.93 ms   (-8.48%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      383.55 ms →      384.64 ms   (+0.29%) |       1   →       1              |      383.55 ms →      384.64 ms   (+0.29%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      272.98 ms →      270.26 ms   (-1.00%) |       1   →       1              |      272.98 ms →      270.26 ms   (-1.00%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.91 μs →        3.54 μs   (-9.41%) |       1   →       1              |        3.91 μs →        3.54 μs   (-9.41%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.84 μs →        2.58 μs   (-9.36%) |       1   →       1              |        2.84 μs →        2.58 μs   (-9.36%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      384.00 ns →      659.00 ns  (+71.61%) |       1   →       1              |      384.00 ns →      659.00 ns  (+71.61%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.28 μs →        1.78 μs  (+38.64%) |       1   →       1              |        1.28 μs →        1.78 μs  (+38.64%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.05 ms →        3.14 ms   (+2.73%) |       1   →       1              |        3.05 ms →        3.14 ms   (+2.73%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       38.52 ms →       39.43 ms   (+2.36%) |       1   →       1              |       38.52 ms →       39.43 ms   (+2.36%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       34.48 ms →       35.89 ms   (+4.09%) |       2   →       2              |       68.96 ms →       71.78 ms   (+4.09%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.27 ms →        6.83 ms  (+29.60%) |       2   →       2              |       10.54 ms →       13.67 ms  (+29.60%) | 
  │ │ │ ├ sddk::inner                                                   |        5.06 ms                             |       2                          |       10.12 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       21.68 μs                             |       2                          |       43.35 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                         6.62 ms            |                   2              |                        13.24 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        21.00 ns            |                   2              |                        42.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                         6.49 ms            |                   2              |                        12.98 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        23.50 ns            |                   2              |                        47.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      203.74 ms →      204.12 ms   (+0.19%) |       1   →       1              |      203.74 ms →      204.12 ms   (+0.19%) | 
  │ │ ├ sddk::transform                                                 |        2.83 ms                             |       1                          |        2.83 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       12.70 μs                             |       1                          |       12.70 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       21.00 μs                             |       1                          |       21.00 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.62 ms            |                   1              |                         2.62 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.62 ms            |                   1              |                         2.62 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      396.00 ns →      390.00 ns   (-1.52%) |       1   →       1              |      396.00 ns →      390.00 ns   (-1.52%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       66.82 s  →       62.65 s    (-6.25%) |       1   →       1              |       66.82 s  →       62.65 s    (-6.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.45 ms   (+0.04%) |      19   →      19              |       46.56 ms →       46.58 ms   (+0.04%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.33 s  →        2.97 s   (-10.74%) |      20   →      21     (+5.00%) |       66.58 s  →       62.41 s    (-6.28%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.13 ms →        5.03 ms   (-1.99%) |      20   →      21     (+5.00%) |      102.67 ms →      105.66 ms   (+2.91%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.45 ms →        4.38 ms   (-1.63%) |      20   →      21     (+5.00%) |       89.01 ms →       91.94 ms   (+3.29%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      543.51 μs →      558.48 μs   (+2.75%) |      20   →      21     (+5.00%) |       10.87 ms →       11.73 ms   (+7.89%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.85 ms →        2.85 ms   (+0.02%) |      20   →      21     (+5.00%) |       57.02 ms →       59.88 ms   (+5.02%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |      199.34 μs →      181.44 μs   (-8.98%) |      40   →      42     (+5.00%) |        7.97 ms →        7.62 ms   (-4.43%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      108.37 μs →      122.05 μs  (+12.62%) |      20   →      21     (+5.00%) |        2.17 ms →        2.56 ms  (+18.25%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       94.08 μs →       91.21 μs   (-3.05%) |      20   →      21     (+5.00%) |        1.88 ms →        1.92 ms   (+1.79%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.10 s  →        1.75 s   (-16.62%) |      20   →      21     (+5.00%) |       42.09 s  →       36.85 s   (-12.45%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      190.90 μs →      197.87 μs   (+3.65%) |      20   →      21     (+5.00%) |        3.82 ms →        4.16 ms   (+8.83%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      182.11 μs →      188.33 μs   (+3.41%) |      20   →      21     (+5.00%) |        3.64 ms →        3.95 ms   (+8.58%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.80 μs →        6.84 μs   (+0.61%) |      20   →      21     (+5.00%) |      135.96 μs →      143.63 μs   (+5.64%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.94 s  →        1.63 s   (-16.27%) |      20   →      21     (+5.00%) |       38.86 s  →       34.16 s   (-12.08%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       89.45 ms →       65.70 ms  (-26.55%) |      20   →      21     (+5.00%) |        1.79 s  →        1.38 s   (-22.88%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.27 ms →        7.11 ms  (-36.91%) |     120   →     126     (+5.00%) |        1.35 s  →      895.99 ms  (-33.75%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.80 ms →       17.19 ms   (+8.84%) |      20   →      21     (+5.00%) |      315.94 ms →      361.07 ms  (+14.28%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      455.26 μs →      455.49 μs   (+0.05%) |      20   →      21     (+5.00%) |        9.11 ms →        9.57 ms   (+5.05%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.45 ms →        7.74 ms   (+3.95%) |      40   →      42     (+5.00%) |      297.86 ms →      325.11 ms   (+9.15%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.83 s  →        1.54 s   (-16.13%) |      20   →      21     (+5.00%) |       36.61 s  →       32.24 s   (-11.93%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.66 ms →       47.76 ms   (-5.72%) |     250   →     361    (+44.40%) |       12.66 s  →       17.24 s   (+36.15%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       32.73 ms →       29.30 ms  (-10.49%) |     250   →     361    (+44.40%) |        8.18 s  →       10.58 s   (+29.25%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.19 μs →        2.14 μs   (-2.34%) |     250   →     361    (+44.40%) |      546.94 μs →      771.27 μs  (+41.02%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.82 μs →        1.78 μs   (-2.17%) |     250   →     361    (+44.40%) |      455.12 μs →      642.91 μs  (+41.26%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      457.46 ns →      411.54 ns  (-10.04%) |     250   →     361    (+44.40%) |      114.37 μs →      148.56 μs  (+29.90%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      529.88 ns →      609.14 ns  (+14.96%) |     250   →     361    (+44.40%) |      132.47 μs →      219.90 μs  (+66.00%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.67 ms →        2.77 ms   (+3.54%) |     250   →     361    (+44.40%) |      668.59 ms →      999.60 ms  (+49.51%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.43 ms →        3.21 ms   (-6.24%) |     250   →     361    (+44.40%) |      857.18 ms →        1.16 s   (+35.38%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        5.90 ms →        6.23 ms   (+5.57%) |     500   →     722    (+44.40%) |        2.95 s  →        4.50 s   (+52.45%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.37 ms →        6.11 ms   (-4.17%) |     250   →     361    (+44.40%) |        1.59 s  →        2.20 s   (+38.38%) | 
  │ │ │ │   │ ├ sddk::inner                                             |      842.57 μs                             |     480                          |      404.44 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.89 μs                             |     480                          |       11.47 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                       948.55 μs            |                 701              |                       664.93 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        46.00 ns            |                 701              |                        32.25 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       787.45 μs            |                 701              |                       552.00 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        48.88 ns            |                 701              |                        34.27 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      183.14 μs →      136.58 μs  (-25.42%) |     250   →     361    (+44.40%) |       45.79 ms →       49.31 ms   (+7.69%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.18 ms →        1.95 ms  (-10.77%) |     250   →     361    (+44.40%) |      545.75 ms →      703.19 ms  (+28.85%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.59 ms                             |     230                          |      595.48 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.94 μs                             |     230                          |        5.05 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        7.90 μs                             |     690                          |        5.45 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.31 ms            |                 340              |                       785.00 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       768.77 μs            |                1.02 K            |                       784.15 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.61 ms →        1.33 ms  (-17.46%) |     250   →     361    (+44.40%) |      402.58 ms →      479.82 ms  (+19.19%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.40 ms                             |     250                          |      351.13 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       24.73 μs                             |     250                          |        6.18 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.29 ms            |                 361              |                       463.97 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        42.68 ns            |                 361              |                        15.41 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.12 ms            |                 361              |                       405.18 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        46.49 ns            |                 361              |                        16.78 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       84.94 ms →       30.85 ms  (-63.67%) |     250   →     361    (+44.40%) |       21.23 s  →       11.14 s   (-47.55%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.27 ms →        2.24 ms   (-1.12%) |     245   →     346    (+41.22%) |      555.33 ms →      775.45 ms  (+39.64%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.66 ms                             |     231                          |      383.04 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.91 μs                             |     231                          |        3.91 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.81 μs                             |     462                          |        4.99 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.07 ms            |                 342              |                       367.04 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       535.15 μs            |                 684              |                       366.04 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      671.77 μs →        1.11 ms  (+64.50%) |     231   →     342    (+48.05%) |      155.18 ms →      377.94 ms (+143.55%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.26 ms →        4.41 ms  (-29.64%) |      25   →      90   (+260.00%) |      156.54 ms →      396.50 ms (+153.29%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.14 ms                             |      30                          |      154.07 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.96 μs                             |      30                          |      328.88 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       11.75 μs                             |      35                          |      411.22 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         2.44 ms            |                 159              |                       387.75 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         1.70 ms            |                 228              |                       387.43 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      373.40 ns →      525.29 ns  (+40.68%) |      20   →      21     (+5.00%) |        7.47 μs →       11.03 μs  (+47.71%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.75 μs →       20.42 μs   (-1.58%) |      20   →      21     (+5.00%) |      414.90 μs →      428.78 μs   (+3.35%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms →        1.59 ms   (+6.30%) |      20   →      21     (+5.00%) |       29.84 ms →       33.31 ms  (+11.62%) | 
  │ │ ├ sirius::Density::generate                                       |      570.08 ms →      562.48 ms   (-1.33%) |      20   →      21     (+5.00%) |       11.40 s  →       11.81 s    (+3.60%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      426.66 ms →      423.79 ms   (-0.67%) |      20   →      21     (+5.00%) |        8.53 s  →        8.90 s    (+4.29%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.18 μs →        8.05 μs   (-1.64%) |      20   →      21     (+5.00%) |      163.60 μs →      168.96 μs   (+3.28%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.43 μs →        7.54 μs   (+1.41%) |      20   →      21     (+5.00%) |      148.67 μs →      158.31 μs   (+6.48%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       18.77 ms →       27.43 ms  (+46.10%) |      20   →      21     (+5.00%) |      375.48 ms →      576.03 ms  (+53.41%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.39 μs →        8.02 μs   (+8.49%) |      20   →      21     (+5.00%) |      147.83 μs →      168.40 μs  (+13.92%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.04 ms →        4.93 ms  (+61.90%) |      20   →      21     (+5.00%) |       60.88 ms →      103.49 ms  (+70.00%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       14.67 ms →       21.44 ms  (+46.22%) |      20   →      21     (+5.00%) |      293.32 ms →      450.33 ms  (+53.53%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      727.80 ns →        1.03 μs  (+41.63%) |      20   →      21     (+5.00%) |       14.56 μs →       21.65 μs  (+48.71%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      126.39 ms →      118.59 ms   (-6.17%) |      20   →      21     (+5.00%) |        2.53 s  →        2.49 s    (-1.48%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.93 ms →        2.27 ms  (+17.72%) |      20   →      21     (+5.00%) |       38.56 ms →       47.66 ms  (+23.61%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      251.24 ms →      249.19 ms   (-0.82%) |      20   →      21     (+5.00%) |        5.02 s  →        5.23 s    (+4.14%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      251.03 ms →      248.98 ms   (-0.82%) |      20   →      21     (+5.00%) |        5.02 s  →        5.23 s    (+4.14%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      114.59 ms →      111.19 ms   (-2.97%) |      20   →      21     (+5.00%) |        2.29 s  →        2.33 s    (+1.88%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      114.59 ms →      111.19 ms   (-2.97%) |      20   →      21     (+5.00%) |        2.29 s  →        2.33 s    (+1.88%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       31.04 ms →       28.97 ms   (-6.69%) |      20   →      21     (+5.00%) |      620.88 ms →      608.33 ms   (-2.02%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.28 ms →       68.92 ms   (+0.93%) |      20   →      21     (+5.00%) |        1.37 s  →        1.45 s    (+5.98%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.62 ms →       12.64 ms  (-13.52%) |      20   →      21     (+5.00%) |      292.39 ms →      265.52 ms   (-9.19%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.56 ms →       23.65 ms   (+0.37%) |      20   →      21     (+5.00%) |      471.24 ms →      496.66 ms   (+5.39%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms →        3.85 ms  (-26.86%) |      20   →      21     (+5.00%) |      105.27 ms →       80.84 ms  (-23.20%) | 
  │ │ ├ sirius::Density::mix                                            |      132.08 ms →      136.13 ms   (+3.07%) |      20   →      21     (+5.00%) |        2.64 s  →        2.86 s    (+8.22%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      881.06 μs →      765.86 μs  (-13.07%) |      20   →      21     (+5.00%) |       17.62 ms →       16.08 ms   (-8.73%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.69 ms →        4.91 ms   (+4.74%) |     244   →     259     (+6.15%) |        1.14 s  →        1.27 s   (+11.18%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.62 ms →        4.82 ms   (+4.32%) |     244   →     259     (+6.15%) |        1.13 s  →        1.25 s   (+10.73%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.62 ms →        4.81 ms   (+4.32%) |     244   →     259     (+6.15%) |        1.13 s  →        1.25 s   (+10.73%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.64 ms →        5.42 ms  (-18.40%) |      20   →      21     (+5.00%) |      132.79 ms →      113.77 ms  (-14.32%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.83 ms →        4.71 ms  (-19.14%) |      20   →      21     (+5.00%) |      116.61 ms →       99.00 ms  (-15.10%) | 
  │ │ ├ sirius::Potential::generate                                     |      361.27 ms →      360.27 ms   (-0.28%) |      20   →      21     (+5.00%) |        7.23 s  →        7.57 s    (+4.71%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       42.66 ms →       39.85 ms   (-6.59%) |      20   →      21     (+5.00%) |      853.19 ms →      836.83 ms   (-1.92%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.96 ms →        6.31 ms (+113.50%) |      20   →      21     (+5.00%) |       59.15 ms →      132.61 ms (+124.18%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.35 ms →        5.92 ms  (+10.63%) |      20   →      21     (+5.00%) |      107.04 ms →      124.35 ms  (+16.17%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.64 ms   (+0.11%) |      20   →      21     (+5.00%) |       92.63 ms →       97.37 ms   (+5.11%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.64 ms   (+0.10%) |      20   →      21     (+5.00%) |       92.62 ms →       97.34 ms   (+5.11%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      780.12 μs →      782.07 μs   (+0.25%) |      40   →      42     (+5.00%) |       31.20 ms →       32.85 ms   (+5.26%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       43.53 ms →       44.76 ms   (+2.84%) |      20   →      21     (+5.00%) |      870.57 ms →      940.03 ms   (+7.98%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.53 ms →       43.58 ms   (+0.12%) |      20   →      21     (+5.00%) |      870.51 ms →      915.14 ms   (+5.13%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      647.82 μs →      682.21 μs   (+5.31%) |      40   →      42     (+5.00%) |       25.91 ms →       28.65 ms  (+10.57%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.91 ms →        4.11 ms  (-16.26%) |      20   →      21     (+5.00%) |       98.22 ms →       86.36 ms  (-12.07%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.21 ms →        3.73 ms  (+16.15%) |      20   →      21     (+5.00%) |       64.30 ms →       78.42 ms  (+21.96%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.87 ms →      268.99 ms   (+0.04%) |      20   →      21     (+5.00%) |        5.38 s  →        5.65 s    (+5.05%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |       63.80 ns →      216.14 ns (+238.78%) |      20   →      21     (+5.00%) |        1.28 μs →        4.54 μs (+255.72%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       98.49 ms →       95.16 ms   (-3.38%) |      20   →      21     (+5.00%) |        1.97 s  →        2.00 s    (+1.45%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       98.49 ms →       95.15 ms   (-3.38%) |      20   →      21     (+5.00%) |        1.97 s  →        2.00 s    (+1.45%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.74 ms →       13.31 ms  (-15.47%) |      20   →      21     (+5.00%) |      314.90 ms →      279.50 ms  (-11.24%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       67.54 ms →       68.66 ms   (+1.66%) |      20   →      21     (+5.00%) |        1.35 s  →        1.44 s    (+6.74%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.57 ms →       12.56 ms  (-13.82%) |      20   →      21     (+5.00%) |      291.45 ms →      263.74 ms   (-9.51%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.75 ms →        3.57 ms  (-24.81%) |      20   →      21     (+5.00%) |       95.01 ms →       75.01 ms  (-21.05%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.59 ms →        4.81 ms   (+4.92%) |     140   →     147     (+5.00%) |      642.07 ms →      707.36 ms  (+10.17%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.62 ms   (+1.43%) |     140   →     147     (+5.00%) |      638.39 ms →      679.87 ms   (+6.50%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.62 ms   (+1.43%) |     140   →     147     (+5.00%) |      638.29 ms →      679.78 ms   (+6.50%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.75 ms →        4.76 ms   (+0.18%) |      60   →      63     (+5.00%) |      284.81 ms →      299.57 ms   (+5.18%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.75 ms   (+0.41%) |      60   →      63     (+5.00%) |      283.60 ms →      299.00 ms   (+5.43%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.92 ms →        4.55 ms   (-7.43%) |      20   →      21     (+5.00%) |       98.40 ms →       95.64 ms   (-2.80%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |       97.58 μs →       75.12 μs  (-23.02%) |      20   →      21     (+5.00%) |        1.95 ms →        1.58 ms  (-19.17%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |       92.39 μs →       70.15 μs  (-24.06%) |      20   →      21     (+5.00%) |        1.85 ms →        1.47 ms  (-20.27%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.38 ms →        5.08 ms   (-5.69%) |       2   →       2              |       10.77 ms →       10.15 ms   (-5.69%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.54 ms →        4.70 ms   (+3.61%) |       6   →       6              |       27.24 ms →       28.22 ms   (+3.61%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.53 ms →        4.54 ms   (+0.11%) |       6   →       6              |       27.20 ms →       27.23 ms   (+0.11%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.53 ms →        4.54 ms   (+0.11%) |       6   →       6              |       27.20 ms →       27.23 ms   (+0.11%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.71 ms →        4.76 ms   (+1.04%) |       3   →       3              |       14.14 ms →       14.29 ms   (+1.04%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.71 ms →        4.75 ms   (+0.91%) |       3   →       3              |       14.13 ms →       14.26 ms   (+0.91%) | 
  ├ sirius::Periodic_function|inner                                     |        4.58 ms →        4.66 ms   (+1.69%) |       2   →       2              |        9.17 ms →        9.32 ms   (+1.69%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.58 ms →        4.53 ms   (-1.08%) |       2   →       2              |        9.16 ms →        9.06 ms   (-1.08%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.58 ms →        4.53 ms   (-1.08%) |       2   →       2              |        9.16 ms →        9.06 ms   (-1.08%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.70 ms →        4.75 ms   (+1.12%) |       1   →       1              |        4.70 ms →        4.75 ms   (+1.12%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.70 ms →        4.75 ms   (+1.10%) |       1   →       1              |        4.70 ms →        4.75 ms   (+1.10%) | 
+ └ sirius::finalize                                                    |      918.15 ms →      287.20 ms  (-68.72%) |       1   →       1              |      918.15 ms →      287.20 ms  (-68.72%) | 
  ====================================================================================================================================================================================================
```
