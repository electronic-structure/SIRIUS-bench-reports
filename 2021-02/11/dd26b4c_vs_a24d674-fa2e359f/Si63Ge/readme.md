# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      107.99 s  →       68.63 s   (-36.45%) |       1   →       1              |      107.99 s  →       68.63 s   (-36.45%) | 
  ├ sirius::initialize                                                  |        2.89 s  →        2.88 s    (-0.28%) |       1   →       1              |        2.89 s  →        2.88 s    (-0.28%) | 
- ├ sirius::Simulation_context::initialize                              |        5.16 s  →        6.66 s   (+29.12%) |       1   →       1              |        5.16 s  →        6.66 s   (+29.12%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       18.46 ms →       38.63 ms (+109.30%) |       1   →       1              |       18.46 ms →       38.63 ms (+109.30%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      220.85 ms →        1.85 s  (+737.72%) |       1   →       1              |      220.85 ms →        1.85 s  (+737.72%) | 
- │ │ ├ sirius::Atom_type::init                                         |       97.73 ms →      914.22 ms (+835.42%) |       2   →       2              |      195.47 ms →        1.83 s  (+835.42%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       25.29 ms →       21.49 ms  (-15.00%) |       1   →       1              |       25.29 ms →       21.49 ms  (-15.00%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       12.88 ms →       10.83 ms  (-15.89%) |       1   →       1              |       12.88 ms →       10.83 ms  (-15.89%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       12.33 ms →       10.59 ms  (-14.13%) |       1   →       1              |       12.33 ms →       10.59 ms  (-14.13%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       12.25 ms →       10.51 ms  (-14.23%) |       1   →       1              |       12.25 ms →       10.51 ms  (-14.23%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.78 ms →        2.76 ms   (-0.72%) |       1   →       1              |        2.78 ms →        2.76 ms   (-0.72%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.39 ms →      711.17 μs  (-70.25%) |       1   →       1              |        2.39 ms →      711.17 μs  (-70.25%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.01 μs →       16.47 μs   (-3.14%) |       1   →       1              |       17.01 μs →       16.47 μs   (-3.14%) | 
  │ └ sirius::Simulation_context::update                                |        4.81 s  →        4.57 s    (-4.94%) |       1   →       1              |        4.81 s  →        4.57 s    (-4.94%) | 
+ │   ├ sirius::Unit_cell::update                                       |       15.44 ms →        7.47 ms  (-51.63%) |       1   →       1              |       15.44 ms →        7.47 ms  (-51.63%) | 
+ │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.17 ms →        3.49 ms  (-65.71%) |       1   →       1              |       10.17 ms →        3.49 ms  (-65.71%) | 
+ │   │ └ sirius::Unit_cell::get_symmetry                               |        5.21 ms →        3.94 ms  (-24.37%) |       1   →       1              |        5.21 ms →        3.94 ms  (-24.37%) | 
+ │   │   └ sirius::Unit_cell_symmetry                                  |        5.13 ms →        3.89 ms  (-24.25%) |       1   →       1              |        5.13 ms →        3.89 ms  (-24.25%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.80 ms   (+3.28%) |       1   →       1              |        2.71 ms →        2.80 ms   (+3.28%) | 
+ │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.37 ms →        1.05 ms  (-55.74%) |       1   →       1              |        2.37 ms →        1.05 ms  (-55.74%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |       24.14 μs →       15.14 μs  (-37.30%) |       1   →       1              |       24.14 μs →       15.14 μs  (-37.30%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |      464.26 ms →      398.87 ms  (-14.08%) |       2   →       2              |      928.52 ms →      797.75 ms  (-14.08%) | 
+ │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       55.29 ms →       36.39 ms  (-34.18%) |       2   →       2              |      110.58 ms →       72.79 ms  (-34.18%) | 
+ │   ├ sirius::Radial_integrals|rho_pseudo                             |       51.13 ms →       32.32 ms  (-36.78%) |       1   →       1              |       51.13 ms →       32.32 ms  (-36.78%) | 
+ │   ├ sirius::Radial_integrals|vloc                                   |      181.56 ms →      116.46 ms  (-35.85%) |       2   →       2              |      363.11 ms →      232.93 ms  (-35.85%) | 
+ │   ├ sirius::Radial_integrals|beta                                   |      135.91 ms →       93.52 ms  (-31.19%) |       2   →       2              |      271.82 ms →      187.04 ms  (-31.19%) | 
- │   ├ sirius::Radial_integrals|atomic_wfs                             |      126.28 ms →      202.99 ms  (+60.75%) |       4   →       4              |      505.11 ms →      811.96 ms  (+60.75%) | 
  │   ├ sddk::Gvec::init                                                |       99.89 ms →       99.66 ms   (-0.23%) |       2   →       2              |      199.78 ms →      199.32 ms   (-0.23%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       74.42 ms →       74.77 ms   (+0.47%) |       2   →       2              |      148.85 ms →      149.55 ms   (+0.47%) | 
+ │   ├ sddk::Gvec_shells                                               |      178.59 ms →      115.29 ms  (-35.44%) |       1   →       1              |      178.59 ms →      115.29 ms  (-35.44%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |       12.00 ms →       13.77 ms  (+14.78%) |       1   →       1              |       12.00 ms →       13.77 ms  (+14.78%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      475.89 ms →      474.36 ms   (-0.32%) |       2   →       2              |      951.77 ms →      948.73 ms   (-0.32%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |      131.47 ms →      149.94 ms  (+14.05%) |       1   →       1              |      131.47 ms →      149.94 ms  (+14.05%) | 
- │ ├ sirius::K_point::K_point                                          |        1.99 μs →        3.95 μs  (+98.03%) |       4   →       4              |        7.98 μs →       15.79 μs  (+98.03%) | 
- │ └ sirius::K_point_set::initialize                                   |      131.40 ms →      149.85 ms  (+14.04%) |       1   →       1              |      131.40 ms →      149.85 ms  (+14.04%) | 
  │   └ sirius::K_point::initialize                                     |       40.57 ms →       39.24 ms   (-3.27%) |       1   →       1              |       40.57 ms →       39.24 ms   (-3.27%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       12.05 ms →       11.03 ms   (-8.40%) |       1   →       1              |       12.05 ms →       11.03 ms   (-8.40%) | 
  │     │ └ sddk::Gvec::init                                            |        5.32 ms →        4.87 ms   (-8.61%) |       1   →       1              |        5.32 ms →        4.87 ms   (-8.61%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        6.76 μs →        6.93 μs   (+2.41%) |       1   →       1              |        6.76 μs →        6.93 μs   (+2.41%) | 
  │     └ sirius::K_point::update                                       |       25.14 ms →       25.29 ms   (+0.61%) |       1   →       1              |       25.14 ms →       25.29 ms   (+0.61%) | 
  │       └ sirius::Beta_projectors                                     |       20.79 ms →       21.24 ms   (+2.15%) |       1   →       1              |       20.79 ms →       21.24 ms   (+2.15%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |       17.58 ms →       19.19 ms   (+9.13%) |       1   →       1              |       17.58 ms →       19.19 ms   (+9.13%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.54 ms   (+0.24%) |       2   →       2              |        5.07 ms →        5.08 ms   (+0.24%) | 
- ├ sirius::Potential                                                   |       58.21 ms →      552.12 ms (+848.46%) |       1   →       1              |       58.21 ms →      552.12 ms (+848.46%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.94 ms   (+1.80%) |       6   →       5    (-16.67%) |       17.34 ms →       14.71 ms  (-15.16%) | 
- │ └ sirius::Potential::update                                         |       40.30 ms →      536.83 ms (+1232.05%) |       1   →       1              |       40.30 ms →      536.83 ms (+1232.05%) | 
- │   └ sirius::Potential::generate_local_potential                     |       39.89 ms →      536.44 ms (+1244.75%) |       1   →       1              |       39.89 ms →      536.44 ms (+1244.75%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       22.61 ms →      526.57 ms (+2229.31%) |       1   →       1              |       22.61 ms →      526.57 ms (+2229.31%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.97 ms →        6.88 ms  (-59.49%) |       1   →       1              |       16.97 ms →        6.88 ms  (-59.49%) | 
- ├ sirius::Density                                                     |       58.96 ms →      383.85 ms (+551.08%) |       1   →       1              |       58.96 ms →      383.85 ms (+551.08%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.83 ms   (-0.07%) |       2   →       2              |        5.66 ms →        5.65 ms   (-0.07%) | 
- │ └ sirius::Density::update                                           |       53.16 ms →      378.05 ms (+611.16%) |       1   →       1              |       53.16 ms →      378.05 ms (+611.16%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       52.93 ms →      377.83 ms (+613.88%) |       1   →       1              |       52.93 ms →      377.83 ms (+613.88%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        78.72 μs            |                   1              |                        78.72 μs            | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       16.36 ms →      372.90 ms (+2179.01%) |       1   →       1              |       16.36 ms →      372.90 ms (+2179.01%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       36.28 ms →        4.55 ms  (-87.47%) |       1   →       1              |       36.28 ms →        4.55 ms  (-87.47%) | 
- ├ sirius::Density::initial_density                                    |      217.25 ms →      441.79 ms (+103.36%) |       1   →       1              |      217.25 ms →      441.79 ms (+103.36%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      182.44 ms →       21.66 ms  (-88.13%) |       1   →       1              |      182.44 ms →       21.66 ms  (-88.13%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.21 ms →      199.38 ms (+2667.19%) |       2   →       2              |       14.41 ms →      398.76 ms (+2667.19%) | 
- │ └ sirius::Periodic_function::integrate                              |        6.78 ms →        7.77 ms  (+14.52%) |       1   →       1              |        6.78 ms →        7.77 ms  (+14.52%) | 
- ├ sirius::Potential::generate                                         |      423.21 ms →      487.20 ms  (+15.12%) |       1   →       1              |      423.21 ms →      487.20 ms  (+15.12%) | 
- │ ├ sirius::Potential::poisson                                        |       47.14 ms →      119.59 ms (+153.71%) |       1   →       1              |       47.14 ms →      119.59 ms (+153.71%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       28.65 ms →      102.51 ms (+257.83%) |       1   →       1              |       28.65 ms →      102.51 ms (+257.83%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        5.06 ms →        6.01 ms  (+18.81%) |       1   →       1              |        5.06 ms →        6.01 ms  (+18.81%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        5.05 ms →        4.87 ms   (-3.49%) |       1   →       1              |        5.05 ms →        4.87 ms   (-3.49%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        5.05 ms →        4.87 ms   (-3.50%) |       1   →       1              |        5.05 ms →        4.87 ms   (-3.50%) | 
+ │ ├ sirius::Periodic_function::add                                    |        4.13 ms →        2.00 ms  (-51.69%) |       2   →       2              |        8.26 ms →        3.99 ms  (-51.69%) | 
+ │ ├ sirius::Potential::xc                                             |       86.33 ms →       67.90 ms  (-21.34%) |       1   →       1              |       86.33 ms →       67.90 ms  (-21.34%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       86.33 ms →       66.83 ms  (-22.58%) |       1   →       1              |       86.33 ms →       66.83 ms  (-22.58%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.51 ms →        2.36 ms   (-5.92%) |       2   →       1    (-50.00%) |        5.03 ms →        2.36 ms  (-52.96%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.93 ms                             |       1                          |        5.93 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        20.93 ms            |                   2              |                        41.87 ms            | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.46 ms →       20.15 ms (+268.82%) |       1   →       1              |        5.46 ms →       20.15 ms (+268.82%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      271.58 ms →      274.79 ms   (+1.18%) |       1   →       1              |      271.58 ms →      274.79 ms   (+1.18%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      216.00 ns →      148.00 ns  (-31.48%) |       1   →       1              |      216.00 ns →      148.00 ns  (-31.48%) | 
  ├ sirius::Hamiltonian0                                                |       14.30 ms →       14.00 ms   (-2.10%) |       1   →       1              |       14.30 ms →       14.00 ms   (-2.10%) | 
+ │ ├ sirius::Local_operator                                            |       13.92 ms →        7.07 ms  (-49.18%) |       1   →       1              |       13.92 ms →        7.07 ms  (-49.18%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.68 ms →        2.68 ms   (+0.17%) |       1   →       1              |        2.68 ms →        2.68 ms   (+0.17%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        7.77 ms →        3.78 ms  (-51.28%) |       1   →       1              |        7.77 ms →        3.78 ms  (-51.28%) | 
- │ ├ sirius::Non_local_operator                                        |       61.06 μs →       69.66 μs  (+14.10%) |       2   →       2              |      122.11 μs →      139.33 μs  (+14.10%) | 
- │ ├ sirius::D_operator::initialize                                    |      109.71 μs →        2.29 ms (+1983.70%) |       1   →       1              |      109.71 μs →        2.29 ms (+1983.70%) | 
- │ └ sirius::Q_operator::initialize                                    |       88.12 μs →        4.44 ms (+4933.67%) |       1   →       1              |       88.12 μs →        4.44 ms (+4933.67%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.28 s    (-1.81%) |       1   →       1              |        1.30 s  →        1.28 s    (-1.81%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       34.16 ms →       30.37 ms  (-11.08%) |       1   →       1              |       34.16 ms →       30.37 ms  (-11.08%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      246.68 μs →      252.03 μs   (+2.17%) |       1   →       1              |      246.68 μs →      252.03 μs   (+2.17%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       33.91 ms →       30.12 ms  (-11.19%) |       1   →       1              |       33.91 ms →       30.12 ms  (-11.19%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.27 s  →        1.25 s    (-1.64%) |       1   →       1              |        1.27 s  →        1.25 s    (-1.64%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |       88.79 ms →       71.58 ms  (-19.38%) |       4   →       4              |      355.15 ms →      286.31 ms  (-19.38%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       36.70 ms →       36.56 ms   (-0.36%) |       1   →       1              |       36.70 ms →       36.56 ms   (-0.36%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.77 ms →        6.75 ms   (-0.18%) |       1   →       1              |        6.77 ms →        6.75 ms   (-0.18%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      374.75 ms →      312.76 ms  (-16.54%) |       1   →       1              |      374.75 ms →      312.76 ms  (-16.54%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.03 ms →      238.19 ms   (-3.97%) |       1   →       1              |      248.03 ms →      238.19 ms   (-3.97%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.00 μs →        3.62 μs   (-9.45%) |       1   →       1              |        4.00 μs →        3.62 μs   (-9.45%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.00 μs →        2.54 μs  (-15.18%) |       1   →       1              |        3.00 μs →        2.54 μs  (-15.18%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      519.00 ns →      478.00 ns   (-7.90%) |       1   →       1              |      519.00 ns →      478.00 ns   (-7.90%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      626.00 ns →      594.00 ns   (-5.11%) |       1   →       1              |      626.00 ns →      594.00 ns   (-5.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.15 ms →        3.20 ms   (+1.59%) |       1   →       1              |        3.15 ms →        3.20 ms   (+1.59%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       22.40 ms →       21.27 ms   (-5.02%) |       1   →       1              |       22.40 ms →       21.27 ms   (-5.02%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       50.56 ms →       25.02 ms  (-50.51%) |       2   →       2              |      101.13 ms →       50.05 ms  (-50.51%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |        9.66 ms →        7.53 ms  (-22.02%) |       2   →       2              |       19.31 ms →       15.06 ms  (-22.02%) | 
  │ │ │ ├ sddk::inner                                                   |        9.44 ms                             |       2                          |       18.87 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       21.43 μs                             |       2                          |       42.87 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                         7.32 ms            |                   2              |                        14.64 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        88.00 ns            |                   2              |                       176.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                         7.18 ms            |                   2              |                        14.35 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       433.50 ns            |                   2              |                       867.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      207.08 ms →      263.14 ms  (+27.07%) |       1   →       1              |      207.08 ms →      263.14 ms  (+27.07%) | 
  │ │ ├ sddk::transform                                                 |        2.83 ms                             |       1                          |        2.83 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.46 μs                             |       1                          |       14.46 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.32 μs                             |       1                          |       18.32 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.60 ms            |                   1              |                         2.60 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.59 ms            |                   1              |                         2.59 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      747.00 ns →      422.00 ns  (-43.51%) |       1   →       1              |      747.00 ns →      422.00 ns  (-43.51%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       96.27 s  →       54.49 s   (-43.40%) |       1   →       1              |       96.27 s  →       54.49 s   (-43.40%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.60 ms   (+6.64%) |      19   →      18     (-5.26%) |       46.36 ms →       46.83 ms   (+1.03%) | 
  │ ├ sirius::Density                                                   |                       446.94 ms            |                   1              |                       446.94 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         2.83 ms            |                   2              |                         5.67 ms            | 
  │ │ └ sirius::Density::update                                         |                       441.13 ms            |                   1              |                       441.13 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       440.92 ms            |                   1              |                       440.92 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                        95.35 μs            |                   1              |                        95.35 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        12.32 ms            |                   1              |                        12.32 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                       428.16 ms            |                   1              |                       428.16 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.79 s  →        3.58 s   (-25.17%) |      20   →      15    (-25.00%) |       95.74 s  →       53.73 s   (-43.88%) | 
- │ │ ├ sirius::Hamiltonian0                                            |       31.12 ms →       42.29 ms  (+35.89%) |      20   →      15    (-25.00%) |      622.48 ms →      634.40 ms   (+1.91%) | 
+ │ │ │ ├ sirius::Local_operator                                        |       18.88 ms →       16.40 ms  (-13.13%) |      20   →      15    (-25.00%) |      377.59 ms →      246.02 ms  (-34.85%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      541.43 μs →      501.05 μs   (-7.46%) |      20   →      15    (-25.00%) |       10.83 ms →        7.52 ms  (-30.59%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        7.58 ms →        6.88 ms   (-9.12%) |      20   →      15    (-25.00%) |      151.50 ms →      103.26 ms  (-31.84%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      251.10 μs →      192.61 μs  (-23.29%) |      40   →      30    (-25.00%) |       10.04 ms →        5.78 ms  (-42.47%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |        6.29 ms →        9.89 ms  (+57.15%) |      20   →      15    (-25.00%) |      125.89 ms →      148.38 ms  (+17.86%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |        5.37 ms →       15.55 ms (+189.49%) |      20   →      15    (-25.00%) |      107.42 ms →      233.22 ms (+117.11%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.36 s  →        1.60 s   (-32.47%) |      20   →      15    (-25.00%) |       47.28 s  →       23.95 s   (-49.35%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |        5.55 ms →        3.87 ms  (-30.21%) |      20   →      15    (-25.00%) |      110.98 ms →       58.09 ms  (-47.66%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |        5.54 ms →        3.86 ms  (-30.32%) |      20   →      15    (-25.00%) |      110.80 ms →       57.91 ms  (-47.74%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.37 μs →        5.77 μs   (-9.54%) |      20   →      15    (-25.00%) |      127.47 μs →       86.48 μs  (-32.16%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.32 s  →        1.44 s   (-38.22%) |      20   →      15    (-25.00%) |       46.49 s  →       21.54 s   (-53.67%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       86.81 ms →       79.73 ms   (-8.16%) |      20   →      15    (-25.00%) |        1.74 s  →        1.20 s   (-31.12%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.56 ms →       10.51 ms   (-9.14%) |     120   →      90    (-25.00%) |        1.39 s  →      945.56 ms  (-31.85%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       90.11 ms →       66.63 ms  (-26.06%) |      20   →      15    (-25.00%) |        1.80 s  →      999.40 ms  (-44.55%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      530.45 μs →      473.50 μs  (-10.74%) |      20   →      15    (-25.00%) |       10.61 ms →        7.10 ms  (-33.05%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |       42.14 ms →       30.73 ms  (-27.06%) |      40   →      30    (-25.00%) |        1.69 s  →      922.01 ms  (-45.30%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.14 s  →        1.28 s   (-40.19%) |      20   →      15    (-25.00%) |       42.82 s  →       19.21 s   (-55.14%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       65.39 ms →       82.93 ms  (+26.83%) |     250   →     116    (-53.60%) |       16.35 s  →        9.62 s   (-41.15%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       31.45 ms →       46.11 ms  (+46.59%) |     250   →     116    (-53.60%) |        7.86 s  →        5.35 s   (-31.98%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.84 μs →        1.68 μs   (-8.53%) |     250   →     116    (-53.60%) |      459.98 μs →      195.23 μs  (-57.56%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.56 μs →        1.39 μs  (-11.15%) |     250   →     116    (-53.60%) |      389.88 μs →      160.73 μs  (-58.78%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      372.18 ns →      398.97 ns   (+7.20%) |     250   →     116    (-53.60%) |       93.05 μs →       46.28 μs  (-50.26%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      497.57 ns →      458.37 ns   (-7.88%) |     250   →     116    (-53.60%) |      124.39 μs →       53.17 μs  (-57.26%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.67 ms →        2.74 ms   (+2.54%) |     250   →     116    (-53.60%) |      667.85 ms →      317.74 ms  (-52.42%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.49 ms →        4.55 ms  (+30.22%) |     250   →     116    (-53.60%) |      872.56 ms →      527.23 ms  (-39.58%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       13.88 ms →       14.76 ms   (+6.35%) |     500   →     232    (-53.60%) |        6.94 s  →        3.42 s   (-50.65%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       42.56 ms →       50.95 ms  (+19.73%) |     250   →     116    (-53.60%) |       10.64 s  →        5.91 s   (-44.45%) | 
  │ │ │ │   │ ├ sddk::inner                                             |      828.89 μs                             |     480                          |      397.87 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.76 μs                             |     480                          |       10.44 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.07 ms            |                 217              |                       232.31 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        85.19 ns            |                 217              |                        18.49 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       906.16 μs            |                 217              |                       196.64 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       207.41 ns            |                 217              |                        45.01 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       37.15 ms →       44.73 ms  (+20.41%) |     250   →     116    (-53.60%) |        9.29 s  →        5.19 s   (-44.13%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.56 ms →        1.97 ms  (+26.29%) |     250   →     116    (-53.60%) |      390.36 ms →      228.74 ms  (-41.40%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.44 ms                             |     230                          |      560.88 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.72 μs                             |     230                          |        4.08 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        6.84 μs                             |     690                          |        4.72 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.57 ms            |                 101              |                       259.46 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       855.56 μs            |                 303              |                       259.24 ms            | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       11.24 ms →       11.09 ms   (-1.35%) |     250   →     116    (-53.60%) |        2.81 s  →        1.29 s   (-54.23%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.46 ms                             |     250                          |      365.77 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       39.44 μs                             |     250                          |        9.86 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.33 ms            |                 116              |                       154.34 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       112.16 ns            |                 116              |                        13.01 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.17 ms            |                 116              |                       135.76 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       189.49 ns            |                 116              |                        21.98 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       49.00 ms →       16.82 ms  (-65.67%) |     250   →     116    (-53.60%) |       12.25 s  →        1.95 s   (-84.07%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.45 ms →        2.12 ms  (-13.40%) |     245   →     114    (-53.47%) |      599.86 ms →      241.71 ms  (-59.71%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.69 ms                             |     231                          |      390.17 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.44 μs                             |     231                          |        3.34 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.71 μs                             |     462                          |        4.49 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.20 ms            |                 101              |                       121.13 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       598.28 μs            |                 202              |                       120.85 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      818.41 μs →      951.21 μs  (+16.23%) |     231   →     101    (-56.28%) |      189.05 ms →       96.07 ms  (-49.18%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.48 ms →        4.02 ms  (-38.03%) |      25   →      47    (+88.00%) |      162.10 ms →      188.83 ms  (+16.49%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.32 ms                             |      30                          |      159.71 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.36 μs                             |      30                          |      310.66 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       10.74 μs                             |      35                          |      375.96 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         2.33 ms            |                  79              |                       183.82 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         1.65 ms            |                 111              |                       183.68 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      379.15 ns →      439.40 ns  (+15.89%) |      20   →      15    (-25.00%) |        7.58 μs →        6.59 μs  (-13.08%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.54 μs →      865.38 μs (+4113.34%) |      20   →      15    (-25.00%) |      410.78 μs →       12.98 ms (+3060.01%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →       64.23 ms (+4090.89%) |      20   →      15    (-25.00%) |       30.65 ms →      963.42 ms (+3043.17%) | 
+ │ │ ├ sirius::Density::generate                                       |      689.27 ms →      694.58 ms   (+0.77%) |      20   →      15    (-25.00%) |       13.79 s  →       10.42 s   (-24.42%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      446.67 ms →      458.93 ms   (+2.74%) |      20   →      15    (-25.00%) |        8.93 s  →        6.88 s   (-22.94%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.65 μs →        8.20 μs   (+7.17%) |      20   →      15    (-25.00%) |      152.95 μs →      122.93 μs  (-19.62%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.60 μs →        7.13 μs   (+8.07%) |      20   →      15    (-25.00%) |      132.00 μs →      106.99 μs  (-18.95%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       24.65 ms →       96.65 ms (+292.14%) |      20   →      15    (-25.00%) |      492.95 ms →        1.45 s  (+194.10%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        8.00 μs →        8.83 μs  (+10.36%) |      20   →      15    (-25.00%) |      160.06 μs →      132.47 μs  (-17.23%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.24 ms →       23.43 ms (+623.85%) |      20   →      15    (-25.00%) |       64.74 ms →      351.44 ms (+442.89%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       14.67 ms →       18.32 ms  (+24.89%) |      20   →      15    (-25.00%) |      293.36 ms →      274.78 ms   (-6.34%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      836.40 ns →      950.73 ns  (+13.67%) |      20   →      15    (-25.00%) |       16.73 μs →       14.26 μs  (-14.75%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      124.09 ms →       61.95 ms  (-50.08%) |      20   →      15    (-25.00%) |        2.48 s  →      929.19 ms  (-62.56%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       43.04 ms →       38.05 ms  (-11.59%) |      20   →      15    (-25.00%) |      860.82 ms →      570.78 ms  (-33.69%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      222.65 ms →      221.75 ms   (-0.41%) |      20   →      15    (-25.00%) |        4.45 s  →        3.33 s   (-25.30%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      218.65 ms →      217.60 ms   (-0.48%) |      20   →      15    (-25.00%) |        4.37 s  →        3.26 s   (-25.36%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      210.28 ms →      204.12 ms   (-2.93%) |      20   →      15    (-25.00%) |        4.21 s  →        3.06 s   (-27.20%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      210.28 ms →      204.11 ms   (-2.93%) |      20   →      15    (-25.00%) |        4.21 s  →        3.06 s   (-27.20%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       26.29 ms →       25.90 ms   (-1.47%) |      20   →      15    (-25.00%) |      525.83 ms →      388.56 ms  (-26.10%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      163.37 ms →      161.63 ms   (-1.06%) |      20   →      15    (-25.00%) |        3.27 s  →        2.42 s   (-25.80%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       19.99 ms →       15.93 ms  (-20.32%) |      20   →      15    (-25.00%) |      399.81 ms →      238.91 ms  (-40.24%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.94 ms →       23.90 ms   (-0.15%) |      20   →      15    (-25.00%) |      478.71 ms →      358.48 ms  (-25.12%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.38 ms →        7.53 ms  (-10.09%) |      20   →      15    (-25.00%) |      167.52 ms →      112.97 ms  (-32.56%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                         4.99 ms            |                 135              |                       673.26 ms            | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                         4.78 ms            |                 135              |                       645.03 ms            | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                         4.78 ms            |                 135              |                       644.95 ms            | 
+ │ │ ├ sirius::Density::mix                                            |      896.54 ms →      263.12 ms  (-70.65%) |      20   →      15    (-25.00%) |       17.93 s  →        3.95 s   (-77.99%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |        7.84 ms →        7.46 ms   (-4.91%) |      20   →      15    (-25.00%) |      156.89 ms →      111.90 ms  (-28.68%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |        7.71 ms →        5.31 ms  (-31.09%) |     244   →     169    (-30.74%) |        1.88 s  →      897.60 ms  (-52.27%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.98 ms →        4.64 ms   (-6.92%) |     244   →     169    (-30.74%) |        1.22 s  →      784.05 ms  (-35.53%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.98 ms →        4.64 ms   (-6.92%) |     244   →     169    (-30.74%) |        1.22 s  →      783.94 ms  (-35.53%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |       20.08 ms →       17.72 ms  (-11.75%) |      20   →      15    (-25.00%) |      401.52 ms →      265.77 ms  (-33.81%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |       10.06 ms →        9.23 ms   (-8.27%) |      20   →      15    (-25.00%) |      201.15 ms →      138.39 ms  (-31.20%) | 
+ │ │ ├ sirius::Potential::generate                                     |      507.12 ms →      548.07 ms   (+8.08%) |      20   →      15    (-25.00%) |       10.14 s  →        8.22 s   (-18.94%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       94.45 ms →      155.93 ms  (+65.08%) |      20   →      15    (-25.00%) |        1.89 s  →        2.34 s   (+23.81%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       33.15 ms →       49.95 ms  (+50.69%) |      20   →      15    (-25.00%) |      663.00 ms →      749.30 ms  (+13.02%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.24 ms →        5.99 ms  (+14.38%) |      20   →      15    (-25.00%) |      104.78 ms →       89.88 ms  (-14.22%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.77 ms →        4.85 ms   (+1.64%) |      20   →      15    (-25.00%) |       95.38 ms →       72.71 ms  (-23.77%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.77 ms →        4.85 ms   (+1.64%) |      20   →      15    (-25.00%) |       95.37 ms →       72.70 ms  (-23.77%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |        6.16 ms →        5.49 ms  (-10.95%) |      40   →      30    (-25.00%) |      246.49 ms →      164.62 ms  (-33.21%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |      106.91 ms →       90.02 ms  (-15.80%) |      20   →      15    (-25.00%) |        2.14 s  →        1.35 s   (-36.85%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |      106.90 ms →       88.97 ms  (-16.77%) |      20   →      15    (-25.00%) |        2.14 s  →        1.33 s   (-37.58%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |      562.82 μs →      557.53 μs   (-0.94%) |      40   →      15    (-62.50%) |       22.51 ms →        8.36 ms  (-62.85%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |       11.20 ms                             |      20                          |      224.07 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        36.51 ms            |                  30              |                         1.10 s             | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        8.78 ms →        8.72 ms   (-0.68%) |      20   →      15    (-25.00%) |      175.52 ms →      130.74 ms  (-25.51%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      278.35 ms →      276.33 ms   (-0.73%) |      20   →      15    (-25.00%) |        5.57 s  →        4.14 s   (-25.55%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      210.90 ns →      124.00 ns  (-41.20%) |      20   →      15    (-25.00%) |        4.22 μs →        1.86 μs  (-55.90%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      229.87 ms →      204.16 ms  (-11.18%) |      20   →      15    (-25.00%) |        4.60 s  →        3.06 s   (-33.39%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      229.87 ms →      204.16 ms  (-11.19%) |      20   →      15    (-25.00%) |        4.60 s  →        3.06 s   (-33.39%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.40 ms →       13.94 ms   (-9.47%) |      20   →      15    (-25.00%) |      308.04 ms →      209.15 ms  (-32.10%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      198.67 ms →      172.25 ms  (-13.30%) |      20   →      15    (-25.00%) |        3.97 s  →        2.58 s   (-34.97%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       15.19 ms →       17.34 ms  (+14.18%) |      20   →      15    (-25.00%) |      303.71 ms →      260.08 ms  (-14.37%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.47 ms →        9.75 ms   (+2.93%) |      20   →      15    (-25.00%) |      189.38 ms →      146.19 ms  (-22.81%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.82 ms                             |     140                          |      675.39 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms                             |     140                          |      666.16 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms                             |     140                          |      666.05 ms                             | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.72 ms →        4.84 ms   (+2.60%) |      60   →      45    (-25.00%) |      283.02 ms →      217.79 ms  (-23.05%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.55 ms →        4.75 ms   (+4.41%) |      60   →      45    (-25.00%) |      272.80 ms →      213.62 ms  (-21.69%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.59 ms   (+0.88%) |      20   →      15    (-25.00%) |       91.07 ms →       68.90 ms  (-24.34%) | 
- │ │ └ sirius::Density::get_magnetisation                              |        5.08 ms →       59.56 ms (+1071.79%) |      20   →      15    (-25.00%) |      101.65 ms →      893.35 ms (+778.84%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |        5.08 ms →       59.55 ms (+1072.78%) |      20   →      15    (-25.00%) |      101.55 ms →      893.21 ms (+779.59%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.67 ms →        5.72 ms   (+0.91%) |       2   →       2              |       11.34 ms →       11.44 ms   (+0.91%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.73 ms →        4.99 ms   (+5.43%) |       6   →       6              |       28.38 ms →       29.92 ms   (+5.43%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.73 ms →        4.98 ms   (+5.44%) |       6   →       6              |       28.36 ms →       29.90 ms   (+5.44%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.98 ms   (+5.44%) |       6   →       6              |       28.35 ms →       29.90 ms   (+5.44%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |        4.52 ms →        5.00 ms  (+10.75%) |       3   →       3              |       13.55 ms →       15.00 ms  (+10.75%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        4.51 ms →        5.00 ms  (+10.75%) |       3   →       3              |       13.54 ms →       14.99 ms  (+10.75%) | 
  ├ sirius::Periodic_function|inner                                     |        4.74 ms →        4.99 ms   (+5.30%) |       2   →       2              |        9.48 ms →        9.98 ms   (+5.30%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.74 ms →        4.99 ms   (+5.31%) |       2   →       2              |        9.47 ms →        9.98 ms   (+5.31%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms →        4.99 ms   (+5.31%) |       2   →       2              |        9.47 ms →        9.97 ms   (+5.31%) | 
- ├ sirius::Smooth_periodic_function|inner                              |        4.55 ms →        5.08 ms  (+11.76%) |       1   →       1              |        4.55 ms →        5.08 ms  (+11.76%) | 
- │ └ sirius::Smooth_periodic_function|inner_local                      |        4.54 ms →        5.07 ms  (+11.53%) |       1   →       1              |        4.54 ms →        5.07 ms  (+11.53%) | 
+ └ sirius::finalize                                                    |      926.91 ms →      222.36 ms  (-76.01%) |       1   →       1              |      926.91 ms →      222.36 ms  (-76.01%) | 
  ====================================================================================================================================================================================================
```
