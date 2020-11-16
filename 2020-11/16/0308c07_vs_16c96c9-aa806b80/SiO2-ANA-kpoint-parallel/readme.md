# Benchmark 16c96c9521ba11c164891eb65cdeac5a4e0e34b3 vs 0308c074b92841e183b2aa72e055c15d8e0ec6ab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      129.37 s  →      131.20 s    (+1.41%) |       1   →       1              |      129.37 s  →      131.20 s    (+1.41%) | 
  ├ sirius::initialize                                                  |        2.68 s  →        2.72 s    (+1.44%) |       1   →       1              |        2.68 s  →        2.72 s    (+1.44%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        2.98 s    (-0.55%) |       1   →       1              |        2.99 s  →        2.98 s    (-0.55%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       67.59 ms →       49.66 ms  (-26.53%) |       1   →       1              |       67.59 ms →       49.66 ms  (-26.53%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      160.50 ms →      188.27 ms  (+17.30%) |       1   →       1              |      160.50 ms →      188.27 ms  (+17.30%) | 
- │ │ ├ sirius::Atom_type::init                                         |       68.35 ms →       81.98 ms  (+19.95%) |       2   →       2              |      136.69 ms →      163.96 ms  (+19.95%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.73 ms →       24.23 ms   (+2.11%) |       1   →       1              |       23.73 ms →       24.23 ms   (+2.11%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.53 ms →        6.36 ms   (-2.72%) |       1   →       1              |        6.53 ms →        6.36 ms   (-2.72%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.16 ms →       17.84 ms   (+3.96%) |       1   →       1              |       17.16 ms →       17.84 ms   (+3.96%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.14 ms →       17.82 ms   (+3.96%) |       1   →       1              |       17.14 ms →       17.82 ms   (+3.96%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.15 ms   (+0.32%) |       1   →       1              |        4.14 ms →        4.15 ms   (+0.32%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.37 ms →        2.34 ms   (-1.12%) |       1   →       1              |        2.37 ms →        2.34 ms   (-1.12%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.12 μs →      101.46 μs   (-0.65%) |       1   →       1              |      102.12 μs →      101.46 μs   (-0.65%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.69 s    (-0.73%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.73%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.87 ms →       10.85 ms   (-0.23%) |       1   →       1              |       10.87 ms →       10.85 ms   (-0.23%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.51 ms →        4.41 ms   (-2.37%) |       1   →       1              |        4.51 ms →        4.41 ms   (-2.37%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.33 ms →        6.41 ms   (+1.27%) |       1   →       1              |        6.33 ms →        6.41 ms   (+1.27%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.31 ms →        6.39 ms   (+1.27%) |       1   →       1              |        6.31 ms →        6.39 ms   (+1.27%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        3.89 ms   (+1.83%) |       1   →       1              |        3.82 ms →        3.89 ms   (+1.83%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.45%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.45%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      101.04 μs →      100.87 μs   (-0.17%) |       1   →       1              |      101.04 μs →      100.87 μs   (-0.17%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.35 ms →       62.89 ms   (+0.86%) |       2   →       2              |      124.70 ms →      125.78 ms   (+0.86%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.17 ms   (+0.61%) |       2   →       2              |       10.28 ms →       10.34 ms   (+0.61%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.53 ms   (+1.24%) |       1   →       1              |        4.47 ms →        4.53 ms   (+1.24%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.78 ms →       21.73 ms   (-0.20%) |       2   →       2              |       43.56 ms →       43.47 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.79 ms →       14.78 ms   (-0.06%) |       2   →       2              |       29.57 ms →       29.55 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.70 ms   (-0.42%) |       4   →       4              |       79.13 ms →       78.80 ms   (-0.42%) | 
  │   ├ sddk::Gvec::init                                                |      170.99 ms →      173.26 ms   (+1.33%) |       2   →       2              |      341.98 ms →      346.52 ms   (+1.33%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.75 ms →      130.78 ms   (+1.58%) |       2   →       2              |      257.51 ms →      261.56 ms   (+1.58%) | 
+ │   ├ sddk::Gvec_shells                                               |      183.50 ms →      164.98 ms  (-10.09%) |       1   →       1              |      183.50 ms →      164.98 ms  (-10.09%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.34 ms   (+1.07%) |       1   →       1              |        1.33 ms →        1.34 ms   (+1.07%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.73 ms →      292.54 ms   (-0.74%) |       2   →       2              |      589.46 ms →      585.09 ms   (-0.74%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       35.21 ms →       41.74 ms  (+18.55%) |       1   →       1              |       35.21 ms →       41.74 ms  (+18.55%) | 
  │ ├ sirius::K_point::K_point                                          |        2.48 μs →        2.71 μs   (+9.35%) |       4   →       4              |        9.92 μs →       10.85 μs   (+9.35%) | 
- │ └ sirius::K_point_set::initialize                                   |       35.10 ms →       41.64 ms  (+18.64%) |       1   →       1              |       35.10 ms →       41.64 ms  (+18.64%) | 
- │   └ sirius::K_point::initialize                                     |       34.99 ms →       41.54 ms  (+18.70%) |       1   →       1              |       34.99 ms →       41.54 ms  (+18.70%) | 
- │     ├ sirius::K_point::generate_gkvec                               |       18.03 ms →       24.17 ms  (+34.05%) |       1   →       1              |       18.03 ms →       24.17 ms  (+34.05%) | 
  │     │ └ sddk::Gvec::init                                            |        8.08 ms →        8.04 ms   (-0.51%) |       1   →       1              |        8.08 ms →        8.04 ms   (-0.51%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.93 μs →        9.52 μs   (-4.07%) |       1   →       1              |        9.93 μs →        9.52 μs   (-4.07%) | 
  │     └ sirius::K_point::update                                       |       12.13 ms →       12.49 ms   (+2.96%) |       1   →       1              |       12.13 ms →       12.49 ms   (+2.96%) | 
  │       └ sirius::Beta_projectors                                     |        5.96 ms →        6.26 ms   (+5.11%) |       1   →       1              |        5.96 ms →        6.26 ms   (+5.11%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.52 ms →        3.66 ms   (+3.90%) |       1   →       1              |        3.52 ms →        3.66 ms   (+3.90%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.61 ms →        5.39 ms   (-4.02%) |       2   →       2              |       11.22 ms →       10.77 ms   (-4.02%) | 
  ├ sirius::Potential                                                   |      159.19 ms →      154.25 ms   (-3.11%) |       1   →       1              |      159.19 ms →      154.25 ms   (-3.11%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.28 ms →        5.84 ms   (-6.98%) |       6   →       6              |       37.69 ms →       35.06 ms   (-6.98%) | 
  │ └ sirius::Potential::update                                         |      120.74 ms →      118.47 ms   (-1.88%) |       1   →       1              |      120.74 ms →      118.47 ms   (-1.88%) | 
  │   └ sirius::Potential::generate_local_potential                     |      119.99 ms →      117.74 ms   (-1.88%) |       1   →       1              |      119.99 ms →      117.74 ms   (-1.88%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.46 ms →      110.47 ms   (-0.88%) |       1   →       1              |      111.46 ms →      110.47 ms   (-0.88%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.60 ms →        6.34 ms  (-16.53%) |       1   →       1              |        7.60 ms →        6.34 ms  (-16.53%) | 
  ├ sirius::Density                                                     |      132.90 ms →      126.96 ms   (-4.47%) |       1   →       1              |      132.90 ms →      126.96 ms   (-4.47%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.69 ms →        5.11 ms  (-10.20%) |       2   →       2              |       11.39 ms →       10.22 ms  (-10.20%) | 
  │ └ sirius::Density::update                                           |      121.21 ms →      116.47 ms   (-3.91%) |       1   →       1              |      121.21 ms →      116.47 ms   (-3.91%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      120.77 ms →      116.06 ms   (-3.90%) |       1   →       1              |      120.77 ms →      116.06 ms   (-3.90%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |       84.39 μs →       73.13 μs  (-13.34%) |       1   →       1              |       84.39 μs →       73.13 μs  (-13.34%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.94 ms →      109.51 ms   (-2.17%) |       1   →       1              |      111.94 ms →      109.51 ms   (-2.17%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.31 ms →        6.03 ms  (-27.49%) |       1   →       1              |        8.31 ms →        6.03 ms  (-27.49%) | 
  ├ sirius::Density::initial_density                                    |      178.53 ms →      163.42 ms   (-8.47%) |       1   →       1              |      178.53 ms →      163.42 ms   (-8.47%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.16 ms →      110.61 ms   (-0.49%) |       1   →       1              |      111.16 ms →      110.61 ms   (-0.49%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.73 ms →        5.05 ms  (-56.93%) |       2   →       2              |       23.46 ms →       10.10 ms  (-56.93%) | 
+ │ └ sirius::Periodic_function::integrate                              |       11.85 ms →        9.74 ms  (-17.76%) |       1   →       1              |       11.85 ms →        9.74 ms  (-17.76%) | 
  ├ sirius::Potential::generate                                         |      595.45 ms →      582.76 ms   (-2.13%) |       1   →       1              |      595.45 ms →      582.76 ms   (-2.13%) | 
  │ ├ sirius::Potential::poisson                                        |      138.68 ms →      125.91 ms   (-9.21%) |       1   →       1              |      138.68 ms →      125.91 ms   (-9.21%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.66 ms →        5.76 ms  (-65.44%) |       1   →       1              |       16.66 ms →        5.76 ms  (-65.44%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       11.03 ms →       10.23 ms   (-7.30%) |       1   →       1              |       11.03 ms →       10.23 ms   (-7.30%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.31 ms →       10.20 ms   (-1.06%) |       1   →       1              |       10.31 ms →       10.20 ms   (-1.06%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.31 ms →       10.20 ms   (-1.05%) |       1   →       1              |       10.31 ms →       10.20 ms   (-1.05%) | 
  │ ├ sirius::Periodic_function::add                                    |      559.30 μs →      554.25 μs   (-0.90%) |       2   →       2              |        1.12 ms →        1.11 ms   (-0.90%) | 
  │ ├ sirius::Potential::xc                                             |       54.71 ms →       53.96 ms   (-1.37%) |       1   →       1              |       54.71 ms →       53.96 ms   (-1.37%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.41 ms →       51.67 ms   (-1.41%) |       1   →       1              |       52.41 ms →       51.67 ms   (-1.41%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.64 ms →        5.64 ms   (+0.01%) |       2   →       2              |       11.28 ms →       11.29 ms   (+0.01%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.46 ms →        5.42 ms   (-0.77%) |       1   →       1              |        5.46 ms →        5.42 ms   (-0.77%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.05 ms →        5.67 ms   (-6.33%) |       1   →       1              |        6.05 ms →        5.67 ms   (-6.33%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.42 ms →       93.50 ms   (+0.08%) |       1   →       1              |       93.42 ms →       93.50 ms   (+0.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.13 ms →      301.25 ms   (+0.37%) |       1   →       1              |      300.13 ms →      301.25 ms   (+0.37%) | 
  ├ sirius::Hamiltonian0                                                |        8.58 ms →        8.39 ms   (-2.18%) |       1   →       1              |        8.58 ms →        8.39 ms   (-2.18%) | 
  │ ├ sirius::Local_operator                                            |        8.23 ms →        8.05 ms   (-2.21%) |       1   →       1              |        8.23 ms →        8.05 ms   (-2.21%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.70 ms   (-1.19%) |       1   →       1              |        4.75 ms →        4.70 ms   (-1.19%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.56 ms →        2.43 ms   (-5.20%) |       1   →       1              |        2.56 ms →        2.43 ms   (-5.20%) | 
  │ ├ sirius::Non_local_operator                                        |       63.16 μs →       63.40 μs   (+0.38%) |       2   →       2              |      126.32 μs →      126.80 μs   (+0.38%) | 
  │ ├ sirius::D_operator::initialize                                    |       96.99 μs →       93.42 μs   (-3.68%) |       1   →       1              |       96.99 μs →       93.42 μs   (-3.68%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.22 μs →       73.91 μs   (-0.41%) |       1   →       1              |       74.22 μs →       73.91 μs   (-0.41%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.85 s    (-0.07%) |       1   →       1              |        1.85 s  →        1.85 s    (-0.07%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.66 ms →       18.69 ms   (+0.14%) |       1   →       1              |       18.66 ms →       18.69 ms   (+0.14%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      189.48 μs →      187.44 μs   (-1.08%) |       1   →       1              |      189.48 μs →      187.44 μs   (-1.08%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.47 ms →       18.50 ms   (+0.16%) |       1   →       1              |       18.47 ms →       18.50 ms   (+0.16%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.83 s    (-0.07%) |       1   →       1              |        1.83 s  →        1.83 s    (-0.07%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.88 ms →      126.20 ms   (-2.08%) |       4   →       4              |      515.51 ms →      504.79 ms   (-2.08%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.34 ms →       52.07 ms   (-0.52%) |       1   →       1              |       52.34 ms →       52.07 ms   (-0.52%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.22 ms →       20.96 ms   (-1.27%) |       1   →       1              |       21.22 ms →       20.96 ms   (-1.27%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.65 ms →      637.16 ms   (+0.40%) |       1   →       1              |      634.65 ms →      637.16 ms   (+0.40%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.00 ms →      298.04 ms   (+0.02%) |       1   →       1              |      298.00 ms →      298.04 ms   (+0.02%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.58 μs →        3.29 μs   (-7.96%) |       1   →       1              |        3.58 μs →        3.29 μs   (-7.96%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.26 μs →        2.28 μs   (+0.89%) |       1   →       1              |        2.26 μs →        2.28 μs   (+0.89%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      359.00 ns →      347.00 ns   (-3.34%) |       1   →       1              |      359.00 ns →      347.00 ns   (-3.34%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      485.00 ns →      511.00 ns   (+5.36%) |       1   →       1              |      485.00 ns →      511.00 ns   (+5.36%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.21 ms   (-0.08%) |       1   →       1              |        9.22 ms →        9.21 ms   (-0.08%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.65 ms →      121.33 ms   (+0.56%) |       1   →       1              |      120.65 ms →      121.33 ms   (+0.56%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.37 ms →      104.27 ms   (+0.87%) |       2   →       2              |      206.74 ms →      208.53 ms   (+0.87%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.01 ms →       40.39 ms   (+0.95%) |       2   →       2              |       80.03 ms →       80.79 ms   (+0.95%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.48 ms →       39.80 ms   (+0.82%) |       2   →       2              |       78.96 ms →       79.60 ms   (+0.82%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       21.50 ns →       26.50 ns  (+23.26%) |       2   →       2              |       43.00 ns →       53.00 ns  (+23.26%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.00 ms →       39.33 ms   (+0.83%) |       2   →       2              |       78.01 ms →       78.65 ms   (+0.83%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       29.50 ns →       13.00 ns  (-55.93%) |       2   →       2              |       59.00 ns →       26.00 ns  (-55.93%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.66 ms →       56.88 ms   (+0.38%) |       1   →       1              |       56.66 ms →       56.88 ms   (+0.38%) | 
  │ │ └ sddk::wf_trans                                                  |       30.69 ms →       30.76 ms   (+0.24%) |       1   →       1              |       30.69 ms →       30.76 ms   (+0.24%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.69 ms →       30.76 ms   (+0.24%) |       1   →       1              |       30.69 ms →       30.76 ms   (+0.24%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      519.00 ns →      574.00 ns  (+10.60%) |       1   →       1              |      519.00 ns →      574.00 ns  (+10.60%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.69 s  →      121.51 s    (+1.52%) |       1   →       1              |      119.69 s  →      121.51 s    (+1.52%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.73 ms   (+0.04%) |      17   →      17              |       97.29 ms →       97.33 ms   (+0.04%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.57 s  →        4.66 s    (+1.94%) |      26   →      26              |      118.86 s  →      121.16 s    (+1.94%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.42 ms →        5.23 ms   (-3.38%) |      26   →      26              |      140.81 ms →      136.05 ms   (-3.38%) | 
  │ │ │ ├ sirius::Local_operator                                        |        5.05 ms →        4.87 ms   (-3.55%) |      26   →      26              |      131.28 ms →      126.62 ms   (-3.55%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      988.84 μs →      974.64 μs   (-1.44%) |      26   →      26              |       25.71 ms →       25.34 ms   (-1.44%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.17 ms →        3.01 ms   (-5.20%) |      26   →      26              |       82.53 ms →       78.24 ms   (-5.20%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.67 μs →       64.70 μs   (+0.04%) |      52   →      52              |        3.36 ms →        3.36 ms   (+0.04%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.15 μs →       87.64 μs   (-0.58%) |      26   →      26              |        2.29 ms →        2.28 ms   (-0.58%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.72 μs →       76.03 μs   (-2.17%) |      26   →      26              |        2.02 ms →        1.98 ms   (-2.17%) | 
  │ │ ├ sirius::Band::solve                                             |        2.66 s  →        2.79 s    (+4.85%) |      26   →      26              |       69.21 s  →       72.57 s    (+4.85%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      153.12 μs →      155.02 μs   (+1.24%) |      26   →      26              |        3.98 ms →        4.03 ms   (+1.24%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      147.02 μs →      149.05 μs   (+1.38%) |      26   →      26              |        3.82 ms →        3.88 ms   (+1.38%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.63 μs →        4.38 μs   (-5.29%) |      26   →      26              |      120.28 μs →      113.92 μs   (-5.29%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.53 s  →        2.61 s    (+2.94%) |      26   →      26              |       65.81 s  →       67.75 s    (+2.94%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.15 ms →       95.52 ms   (+0.39%) |      26   →      26              |        2.47 s  →        2.48 s    (+0.39%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.73 ms →        7.61 ms   (-1.53%) |     156   →     156              |        1.21 s  →        1.19 s    (-1.53%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.85 ms →        6.06 ms   (+3.57%) |      26   →      26              |      152.07 ms →      157.51 ms   (+3.57%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.29 μs →      353.51 μs   (+1.21%) |      26   →      26              |        9.08 ms →        9.19 ms   (+1.21%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.32 ms →        2.34 ms   (+0.89%) |      52   →      52              |      120.79 ms →      121.87 ms   (+0.89%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.39 s  →        2.47 s    (+3.08%) |      26   →      26              |       62.26 s  →       64.18 s    (+3.08%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.81 ms →      117.96 ms  (-13.77%) |     262   →     314    (+19.85%) |       35.84 s  →       37.04 s    (+3.34%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.39 ms →       46.54 ms  (-15.98%) |     262   →     314    (+19.85%) |       14.51 s  →       14.61 s    (+0.70%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.85 μs →        1.81 μs   (-2.37%) |     262   →     314    (+19.85%) |      484.68 μs →      567.09 μs  (+17.00%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.53 μs   (-2.83%) |     262   →     314    (+19.85%) |      413.37 μs →      481.37 μs  (+16.45%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      340.27 ns →      353.46 ns   (+3.88%) |     262   →     314    (+19.85%) |       89.15 μs →      110.99 μs  (+24.49%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      414.25 ns →      415.41 ns   (+0.28%) |     262   →     314    (+19.85%) |      108.53 μs →      130.44 μs  (+20.18%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.39 ms   (-0.83%) |     262   →     314    (+19.85%) |        1.95 s  →        2.32 s   (+18.86%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       25.13 ms →       21.30 ms  (-15.23%) |     262   →     314    (+19.85%) |        6.58 s  →        6.69 s    (+1.59%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.41 ms →       21.36 ms  (-12.51%) |     524   →     628    (+19.85%) |       12.79 s  →       13.41 s    (+4.86%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       42.41 ms →       36.52 ms  (-13.89%) |     262   →     314    (+19.85%) |       11.11 s  →       11.47 s    (+3.20%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        5.43 ms  (-12.98%) |     498   →     602    (+20.88%) |        3.11 s  →        3.27 s    (+5.19%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       52.95 ns →       46.74 ns  (-11.74%) |     498   →     602    (+20.88%) |       26.37 μs →       28.14 μs   (+6.69%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.12 ms →        4.31 ms  (-15.76%) |     498   →     602    (+20.88%) |        2.55 s  →        2.60 s    (+1.83%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       47.02 ns →       37.57 ns  (-20.09%) |     498   →     602    (+20.88%) |       23.41 μs →       22.62 μs   (-3.40%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        7.16 ms →        6.13 ms  (-14.34%) |     262   →     314    (+19.85%) |        1.88 s  →        1.93 s    (+2.66%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.31 ms →        8.61 ms  (-16.53%) |     262   →     314    (+19.85%) |        2.70 s  →        2.70 s    (+0.03%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |       14.53 ms →       12.41 ms  (-14.62%) |     236   →     288    (+22.03%) |        3.43 s  →        3.57 s    (+4.20%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        4.13 ms  (-14.62%) |     708   →     864    (+22.03%) |        3.43 s  →        3.57 s    (+4.20%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.58 ms →        9.09 ms  (-14.12%) |     262   →     314    (+19.85%) |        2.77 s  →        2.85 s    (+2.93%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →        8.73 ms  (-14.21%) |     262   →     314    (+19.85%) |        2.67 s  →        2.74 s    (+2.82%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.45 ns →      101.07 ns (+143.83%) |     262   →     314    (+19.85%) |       10.86 μs →       31.74 μs (+192.23%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.06 ms →        7.62 ms  (-15.93%) |     262   →     314    (+19.85%) |        2.37 s  →        2.39 s    (+0.75%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       23.19 ns →       22.14 ns   (-4.52%) |     262   →     314    (+19.85%) |        6.08 μs →        6.95 μs  (+14.44%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.72 ms →       15.19 ms  (-14.29%) |     262   →     314    (+19.85%) |        4.64 s  →        4.77 s    (+2.72%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.14 ms →       10.93 ms  (-16.84%) |     252   →     302    (+19.84%) |        3.31 s  →        3.30 s    (-0.34%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       11.72 ms →        9.54 ms  (-18.55%) |     242   →     294    (+21.49%) |        2.84 s  →        2.81 s    (-1.05%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.86 ms →        4.77 ms  (-18.56%) |     484   →     588    (+21.49%) |        2.84 s  →        2.81 s    (-1.06%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.72 ms →        1.45 ms  (-15.41%) |     242   →     294    (+21.49%) |      415.41 ms →      426.91 ms   (+2.77%) | 
! │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.75 ms →       48.82 ms   (-9.18%) |      85   →      97    (+14.12%) |        4.57 s  →        4.74 s    (+3.64%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       31.46 ms →       27.91 ms  (-11.28%) |     144   →     168    (+16.67%) |        4.53 s  →        4.69 s    (+3.50%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |       22.32 ms →       19.62 ms  (-12.09%) |     203   →     239    (+17.73%) |        4.53 s  →        4.69 s    (+3.50%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      438.62 ns →      384.35 ns  (-12.37%) |      26   →      26              |       11.40 μs →        9.99 μs  (-12.37%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       32.49 μs →       30.58 μs   (-5.89%) |      26   →      26              |      844.74 μs →      795.01 μs   (-5.89%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      616.79 μs →      609.31 μs   (-1.21%) |      26   →      26              |       16.04 ms →       15.84 ms   (-1.21%) | 
  │ │ ├ sirius::Density::generate                                       |      766.27 ms →      775.69 ms   (+1.23%) |      26   →      26              |       19.92 s  →       20.17 s    (+1.23%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.67 ms →      402.47 ms   (-0.05%) |      26   →      26              |       10.47 s  →       10.46 s    (-0.05%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.32 μs →        3.45 μs   (+4.02%) |      26   →      26              |       86.29 μs →       89.75 μs   (+4.02%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.93 μs →        2.99 μs   (+2.24%) |      26   →      26              |       76.10 μs →       77.80 μs   (+2.24%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.32 ms →      100.36 ms   (+0.04%) |      26   →      26              |        2.61 s  →        2.61 s    (+0.04%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.91 μs →       11.39 μs   (+4.42%) |      26   →      26              |      283.69 μs →      296.24 μs   (+4.42%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (+0.06%) |      26   →      26              |      185.25 ms →      185.36 ms   (+0.06%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.29 ms →       91.33 ms   (+0.04%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.04%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      603.50 ns →      561.12 ns   (-7.02%) |      26   →      26              |       15.69 μs →       14.59 μs   (-7.02%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      161.98 ms →      162.76 ms   (+0.48%) |      26   →      26              |        4.21 s  →        4.23 s    (+0.48%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.17%) |      26   →      26              |       42.71 ms →       42.64 ms   (-0.17%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.33 ms   (+0.02%) |      26   →      26              |        2.30 s  →        2.30 s    (+0.02%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms →       88.10 ms   (+0.02%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      271.72 ms →      280.04 ms   (+3.06%) |      26   →      26              |        7.06 s  →        7.28 s    (+3.06%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      271.72 ms →      280.04 ms   (+3.06%) |      26   →      26              |        7.06 s  →        7.28 s    (+3.06%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.94 ms →       25.42 ms   (+1.95%) |      26   →      26              |      648.39 ms →      661.04 ms   (+1.95%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      221.19 ms →      230.34 ms   (+4.13%) |      26   →      26              |        5.75 s  →        5.99 s    (+4.13%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.42 ms →       23.11 ms   (-5.37%) |      26   →      26              |      634.95 ms →      600.85 ms   (-5.37%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.49 ms →       82.74 ms   (+2.79%) |      26   →      26              |        2.09 s  →        2.15 s    (+2.79%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.78 ms →        6.80 ms  (-12.65%) |      26   →      26              |      202.34 ms →      176.74 ms  (-12.65%) | 
+ │ │ ├ sirius::Density::mix                                            |      161.11 ms →      105.26 ms  (-34.67%) |      26   →      26              |        4.19 s  →        2.74 s   (-34.67%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      925.15 μs →      921.38 μs   (-0.41%) |      26   →      26              |       24.05 ms →       23.96 ms   (-0.41%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.63 ms →       10.59 ms   (-0.31%) |     334   →     206    (-38.32%) |        3.55 s  →        2.18 s   (-38.52%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.80 ms →       10.19 ms   (+4.02%) |     334   →     206    (-38.32%) |        3.27 s  →        2.10 s   (-35.84%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.80 ms →       10.19 ms   (+4.03%) |     334   →     206    (-38.32%) |        3.27 s  →        2.10 s   (-35.84%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.36 ms →        6.40 ms   (+0.61%) |      26   →      26              |      165.42 ms →      166.43 ms   (+0.61%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.27 ms →        5.34 ms   (+1.24%) |      26   →      26              |      137.14 ms →      138.85 ms   (+1.24%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.32 ms →      576.81 ms   (-0.61%) |      26   →      26              |       15.09 s  →       15.00 s    (-0.61%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.34 ms →      126.20 ms   (-8.77%) |      26   →      26              |        3.60 s  →        3.28 s    (-8.77%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.53 ms →        6.17 ms  (-62.64%) |      26   →      26              |      429.65 ms →      160.52 ms  (-62.64%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.83 ms →       10.49 ms   (-3.09%) |      26   →      26              |      281.52 ms →      272.82 ms   (-3.09%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.40 ms →       10.16 ms   (-2.31%) |      26   →      26              |      270.45 ms →      264.20 ms   (-2.31%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.40 ms →       10.16 ms   (-2.31%) |      26   →      26              |      270.43 ms →      264.18 ms   (-2.31%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.08 μs →      552.26 μs   (+0.40%) |      52   →      52              |       28.60 ms →       28.72 ms   (+0.40%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.43 ms →       49.28 ms   (-0.31%) |      26   →      26              |        1.29 s  →        1.28 s    (-0.31%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.05 ms →       46.91 ms   (-0.32%) |      26   →      26              |        1.22 s  →        1.22 s    (-0.32%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.08 ms   (+0.47%) |      52   →      52              |      159.18 ms →      159.93 ms   (+0.47%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.50 ms →        5.33 ms   (-3.10%) |      26   →      26              |      142.96 ms →      138.53 ms   (-3.10%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.60 ms →        6.47 ms   (-1.98%) |      26   →      26              |      171.49 ms →      168.10 ms   (-1.98%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       91.01 ms   (+0.13%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.13%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.64 ms →      301.44 ms   (+3.01%) |      26   →      26              |        7.61 s  →        7.84 s    (+3.01%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      275.88 ms →      282.07 ms   (+2.25%) |      26   →      26              |        7.17 s  →        7.33 s    (+2.25%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      275.88 ms →      282.07 ms   (+2.25%) |      26   →      26              |        7.17 s  →        7.33 s    (+2.25%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.18 ms →       26.81 ms   (-1.37%) |      26   →      26              |      706.62 ms →      696.95 ms   (-1.37%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      220.85 ms →      227.54 ms   (+3.03%) |      26   →      26              |        5.74 s  →        5.92 s    (+3.03%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.04 ms →       23.93 ms   (-0.46%) |      26   →      26              |      624.97 ms →      622.08 ms   (-0.46%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.56 ms →        5.38 ms   (-3.26%) |      26   →      26              |      144.46 ms →      139.75 ms   (-3.26%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.30 ms →       10.68 ms   (+3.69%) |     182   →     182              |        1.87 s  →        1.94 s    (+3.69%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.85 ms →       10.33 ms   (+4.87%) |     182   →     182              |        1.79 s  →        1.88 s    (+4.87%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.85 ms →       10.33 ms   (+4.87%) |     182   →     182              |        1.79 s  →        1.88 s    (+4.87%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.64 ms →       10.89 ms   (+2.34%) |      78   →      78              |      830.16 ms →      849.56 ms   (+2.34%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.22 ms →        9.82 ms   (-3.92%) |      78   →      78              |      797.24 ms →      765.99 ms   (-3.92%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.03 ms →       10.01 ms   (-0.14%) |      26   →      26              |      260.74 ms →      260.38 ms   (-0.14%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      125.96 μs →      106.72 μs  (-15.27%) |      26   →      26              |        3.27 ms →        2.77 ms  (-15.27%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      121.36 μs →      101.77 μs  (-16.14%) |      26   →      26              |        3.16 ms →        2.65 ms  (-16.14%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.93 ms →        6.91 ms   (-0.27%) |       2   →       2              |       13.86 ms →       13.82 ms   (-0.27%) | 
  │ ├ sirius::Periodic_function|inner                                   |       11.51 ms →       10.58 ms   (-8.09%) |       6   →       6              |       69.08 ms →       63.49 ms   (-8.09%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.69 ms →       10.49 ms   (+8.31%) |       6   →       6              |       58.13 ms →       62.96 ms   (+8.31%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.69 ms →       10.49 ms   (+8.31%) |       6   →       6              |       58.12 ms →       62.96 ms   (+8.31%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.90 ms →       10.06 ms   (-7.69%) |       3   →       3              |       32.69 ms →       30.17 ms   (-7.69%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.06 ms →       10.00 ms   (-0.61%) |       3   →       3              |       30.17 ms →       29.99 ms   (-0.61%) | 
  ├ sirius::Periodic_function|inner                                     |       10.14 ms →       10.30 ms   (+1.63%) |       2   →       2              |       20.27 ms →       20.60 ms   (+1.63%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.65 ms →       10.17 ms   (+5.41%) |       2   →       2              |       19.29 ms →       20.34 ms   (+5.41%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.65 ms →       10.17 ms   (+5.41%) |       2   →       2              |       19.29 ms →       20.33 ms   (+5.41%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.57 ms →        9.72 ms   (-8.03%) |       1   →       1              |       10.57 ms →        9.72 ms   (-8.03%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.52 ms →        9.65 ms   (-8.27%) |       1   →       1              |       10.52 ms →        9.65 ms   (-8.27%) | 
  └ sirius::finalize                                                    |      225.63 ms →      233.74 ms   (+3.59%) |       1   →       1              |      225.63 ms →      233.74 ms   (+3.59%) | 
  ====================================================================================================================================================================================================
```
