# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 4e60b1847c4444fb88c162c63a530351544e3d41
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      132.74 s  →      133.18 s    (+0.33%) |       1   →       1              |      132.74 s  →      133.18 s    (+0.33%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.74 s    (+1.46%) |       1   →       1              |        2.70 s  →        2.74 s    (+1.46%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        2.88 s    (-3.53%) |       1   →       1              |        2.99 s  →        2.88 s    (-3.53%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       34.27 ms →        9.95 ms  (-70.96%) |       1   →       1              |       34.27 ms →        9.95 ms  (-70.96%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      160.85 ms →      148.97 ms   (-7.38%) |       1   →       1              |      160.85 ms →      148.97 ms   (-7.38%) | 
  │ │ ├ sirius::Atom_type::init                                         |       68.37 ms →       63.20 ms   (-7.56%) |       2   →       2              |      136.74 ms →      126.40 ms   (-7.56%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.04 ms →       22.50 ms   (-6.41%) |       1   →       1              |       24.04 ms →       22.50 ms   (-6.41%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.38 ms →        5.37 ms  (-15.84%) |       1   →       1              |        6.38 ms →        5.37 ms  (-15.84%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.61 ms →       17.08 ms   (-3.02%) |       1   →       1              |       17.61 ms →       17.08 ms   (-3.02%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.59 ms →       17.06 ms   (-3.04%) |       1   →       1              |       17.59 ms →       17.06 ms   (-3.04%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.15 ms   (+0.33%) |       1   →       1              |        4.13 ms →        4.15 ms   (+0.33%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.35 ms   (+0.32%) |       1   →       1              |        2.35 ms →        2.35 ms   (+0.32%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.36 μs →      101.71 μs   (-0.63%) |       1   →       1              |      102.36 μs →      101.71 μs   (-0.63%) | 
  │ └ sirius::Simulation_context::update                                |        2.75 s  →        2.68 s    (-2.49%) |       1   →       1              |        2.75 s  →        2.68 s    (-2.49%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.87 ms →       10.85 ms   (-0.17%) |       1   →       1              |       10.87 ms →       10.85 ms   (-0.17%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.48 ms →        4.46 ms   (-0.47%) |       1   →       1              |        4.48 ms →        4.46 ms   (-0.47%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.36 ms   (+0.09%) |       1   →       1              |        6.35 ms →        6.36 ms   (+0.09%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.34 ms   (+0.08%) |       1   →       1              |        6.33 ms →        6.34 ms   (+0.08%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.84 ms →        3.85 ms   (+0.30%) |       1   →       1              |        3.84 ms →        3.85 ms   (+0.30%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.31 ms   (-0.57%) |       1   →       1              |        2.32 ms →        2.31 ms   (-0.57%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      101.49 μs →      100.69 μs   (-0.79%) |       1   →       1              |      101.49 μs →      100.69 μs   (-0.79%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.08 ms →       62.55 ms   (-0.83%) |       2   →       2              |      126.15 ms →      125.11 ms   (-0.83%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.17 ms   (+0.67%) |       2   →       2              |       10.27 ms →       10.34 ms   (+0.67%) | 
- │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        5.35 ms  (+19.68%) |       1   →       1              |        4.47 ms →        5.35 ms  (+19.68%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.97 ms →       21.73 ms   (-1.10%) |       2   →       2              |       43.94 ms →       43.45 ms   (-1.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.86 ms →       14.78 ms   (-0.52%) |       2   →       2              |       29.71 ms →       29.56 ms   (-0.52%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.69 ms →       19.79 ms   (+0.47%) |       4   →       4              |       78.78 ms →       79.15 ms   (+0.47%) | 
  │   ├ sddk::Gvec::init                                                |      171.06 ms →      172.61 ms   (+0.91%) |       2   →       2              |      342.12 ms →      345.22 ms   (+0.91%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.72 ms →      130.36 ms   (+1.27%) |       2   →       2              |      257.44 ms →      260.72 ms   (+1.27%) | 
  │   ├ sddk::Gvec_shells                                               |      187.10 ms →      173.72 ms   (-7.15%) |       1   →       1              |      187.10 ms →      173.72 ms   (-7.15%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.30 ms →        1.34 ms   (+2.57%) |       1   →       1              |        1.30 ms →        1.34 ms   (+2.57%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      300.34 ms →      292.61 ms   (-2.57%) |       2   →       2              |      600.67 ms →      585.21 ms   (-2.57%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.60 ms →       35.71 ms   (+0.30%) |       1   →       1              |       35.60 ms →       35.71 ms   (+0.30%) | 
  │ ├ sirius::K_point::K_point                                          |        2.60 μs →        2.52 μs   (-3.14%) |       4   →       4              |       10.40 μs →       10.08 μs   (-3.14%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.49 ms →       35.61 ms   (+0.31%) |       1   →       1              |       35.49 ms →       35.61 ms   (+0.31%) | 
  │   └ sirius::K_point::initialize                                     |       35.38 ms →       35.50 ms   (+0.34%) |       1   →       1              |       35.38 ms →       35.50 ms   (+0.34%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.02 ms →       17.94 ms   (-0.44%) |       1   →       1              |       18.02 ms →       17.94 ms   (-0.44%) | 
  │     │ └ sddk::Gvec::init                                            |        8.08 ms →        8.05 ms   (-0.33%) |       1   →       1              |        8.08 ms →        8.05 ms   (-0.33%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.53 μs →        9.86 μs   (+3.50%) |       1   →       1              |        9.53 μs →        9.86 μs   (+3.50%) | 
  │     └ sirius::K_point::update                                       |       12.42 ms →       12.66 ms   (+1.94%) |       1   →       1              |       12.42 ms →       12.66 ms   (+1.94%) | 
  │       └ sirius::Beta_projectors                                     |        6.16 ms →        6.35 ms   (+3.07%) |       1   →       1              |        6.16 ms →        6.35 ms   (+3.07%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.54 ms →        3.79 ms   (+6.94%) |       1   →       1              |        3.54 ms →        3.79 ms   (+6.94%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.43 ms →        5.31 ms   (-2.24%) |       2   →       2              |       10.87 ms →       10.62 ms   (-2.24%) | 
  ├ sirius::Potential                                                   |      159.34 ms →      158.27 ms   (-0.67%) |       1   →       1              |      159.34 ms →      158.27 ms   (-0.67%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.81 ms   (+0.03%) |       6   →       6              |       34.87 ms →       34.88 ms   (+0.03%) | 
  │ └ sirius::Potential::update                                         |      123.71 ms →      122.63 ms   (-0.87%) |       1   →       1              |      123.71 ms →      122.63 ms   (-0.87%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.95 ms →      121.86 ms   (-0.89%) |       1   →       1              |      122.95 ms →      121.86 ms   (-0.89%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.22 ms →      111.93 ms   (+0.64%) |       1   →       1              |      111.22 ms →      111.93 ms   (+0.64%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.81 ms →        9.03 ms  (-16.49%) |       1   →       1              |       10.81 ms →        9.03 ms  (-16.49%) | 
  ├ sirius::Density                                                     |      136.11 ms →      134.51 ms   (-1.18%) |       1   →       1              |      136.11 ms →      134.51 ms   (-1.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.29 ms →        5.45 ms   (+3.07%) |       2   →       2              |       10.58 ms →       10.90 ms   (+3.07%) | 
  │ └ sirius::Density::update                                           |      125.26 ms →      123.33 ms   (-1.54%) |       1   →       1              |      125.26 ms →      123.33 ms   (-1.54%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.82 ms →      122.89 ms   (-1.55%) |       1   →       1              |      124.82 ms →      122.89 ms   (-1.55%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      107.94 μs →      107.49 μs   (-0.42%) |       1   →       1              |      107.94 μs →      107.49 μs   (-0.42%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.98 ms →      112.88 ms   (-0.09%) |       1   →       1              |      112.98 ms →      112.88 ms   (-0.09%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.28 ms →        9.44 ms  (-16.30%) |       1   →       1              |       11.28 ms →        9.44 ms  (-16.30%) | 
  ├ sirius::Density::initial_density                                    |      178.70 ms →      173.53 ms   (-2.89%) |       1   →       1              |      178.70 ms →      173.53 ms   (-2.89%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.03 ms →      111.90 ms   (+0.79%) |       1   →       1              |      111.03 ms →      111.90 ms   (+0.79%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       12.05 ms →       10.00 ms  (-16.98%) |       2   →       2              |       24.10 ms →       20.00 ms  (-16.98%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.28 ms →        9.82 ms   (-4.46%) |       1   →       1              |       10.28 ms →        9.82 ms   (-4.46%) | 
  ├ sirius::Potential::generate                                         |      593.81 ms →      590.68 ms   (-0.53%) |       1   →       1              |      593.81 ms →      590.68 ms   (-0.53%) | 
  │ ├ sirius::Potential::poisson                                        |      138.71 ms →      136.26 ms   (-1.77%) |       1   →       1              |      138.71 ms →      136.26 ms   (-1.77%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       17.04 ms →       15.42 ms   (-9.53%) |       1   →       1              |       17.04 ms →       15.42 ms   (-9.53%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.86 ms →        9.97 ms   (-8.22%) |       1   →       1              |       10.86 ms →        9.97 ms   (-8.22%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.90 ms →        9.86 ms   (-0.42%) |       1   →       1              |        9.90 ms →        9.86 ms   (-0.42%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →        9.85 ms   (-0.42%) |       1   →       1              |        9.89 ms →        9.85 ms   (-0.42%) | 
  │ ├ sirius::Periodic_function::add                                    |      549.85 μs →      557.68 μs   (+1.42%) |       2   →       2              |        1.10 ms →        1.12 ms   (+1.42%) | 
  │ ├ sirius::Potential::xc                                             |       54.31 ms →       53.51 ms   (-1.47%) |       1   →       1              |       54.31 ms →       53.51 ms   (-1.47%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.92 ms →       51.11 ms   (-1.57%) |       1   →       1              |       51.92 ms →       51.11 ms   (-1.57%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.70 ms   (-0.04%) |       2   →       2              |       11.41 ms →       11.40 ms   (-0.04%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.44 ms →        5.17 ms   (-4.81%) |       1   →       1              |        5.44 ms →        5.17 ms   (-4.81%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.86 ms →        5.96 ms   (+1.79%) |       1   →       1              |        5.86 ms →        5.96 ms   (+1.79%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.66 ms →       93.55 ms   (+0.96%) |       1   →       1              |       92.66 ms →       93.55 ms   (+0.96%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.80 ms →      298.91 ms   (-0.30%) |       1   →       1              |      299.80 ms →      298.91 ms   (-0.30%) | 
  ├ sirius::Hamiltonian0                                                |        8.33 ms →        8.40 ms   (+0.90%) |       1   →       1              |        8.33 ms →        8.40 ms   (+0.90%) | 
  │ ├ sirius::Local_operator                                            |        7.97 ms →        8.04 ms   (+0.81%) |       1   →       1              |        7.97 ms →        8.04 ms   (+0.81%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.72 ms →        4.74 ms   (+0.60%) |       1   →       1              |        4.72 ms →        4.74 ms   (+0.60%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.36 ms   (+0.96%) |       1   →       1              |        2.34 ms →        2.36 ms   (+0.96%) | 
  │ ├ sirius::Non_local_operator                                        |       63.09 μs →       63.20 μs   (+0.17%) |       2   →       2              |      126.17 μs →      126.39 μs   (+0.17%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.24 μs →       96.90 μs   (-1.37%) |       1   →       1              |       98.24 μs →       96.90 μs   (-1.37%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.45 μs →       79.16 μs   (+6.32%) |       1   →       1              |       74.45 μs →       79.16 μs   (+6.32%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.86 s    (-0.01%) |       1   →       1              |        1.86 s  →        1.86 s    (-0.01%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.69 ms →       18.11 ms   (-3.11%) |       1   →       1              |       18.69 ms →       18.11 ms   (-3.11%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      185.54 μs →      189.28 μs   (+2.02%) |       1   →       1              |      185.54 μs →      189.28 μs   (+2.02%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       17.91 ms   (-3.17%) |       1   →       1              |       18.50 ms →       17.91 ms   (-3.17%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.84 s    (+0.02%) |       1   →       1              |        1.84 s  →        1.84 s    (+0.02%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.83 ms →      128.53 ms   (-0.24%) |       4   →       4              |      515.34 ms →      514.12 ms   (-0.24%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.56 ms →       51.94 ms   (-1.17%) |       1   →       1              |       52.56 ms →       51.94 ms   (-1.17%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.26 ms →       21.00 ms   (-1.22%) |       1   →       1              |       21.26 ms →       21.00 ms   (-1.22%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      635.41 ms →      638.29 ms   (+0.45%) |       1   →       1              |      635.41 ms →      638.29 ms   (+0.45%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.24 ms →      301.59 ms   (+1.12%) |       1   →       1              |      298.24 ms →      301.59 ms   (+1.12%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.83 μs →        3.63 μs   (-5.07%) |       1   →       1              |        3.83 μs →        3.63 μs   (-5.07%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.84 μs →        2.79 μs   (-1.83%) |       1   →       1              |        2.84 μs →        2.79 μs   (-1.83%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      344.00 ns →      371.00 ns   (+7.85%) |       1   →       1              |      344.00 ns →      371.00 ns   (+7.85%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      487.00 ns →      589.00 ns  (+20.94%) |       1   →       1              |      487.00 ns →      589.00 ns  (+20.94%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.22 ms   (-0.13%) |       1   →       1              |        9.23 ms →        9.22 ms   (-0.13%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.78 ms →      120.60 ms   (-0.14%) |       1   →       1              |      120.78 ms →      120.60 ms   (-0.14%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.56 ms →      103.42 ms   (-0.14%) |       2   →       2              |      207.13 ms →      206.84 ms   (-0.14%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.10 ms →       40.20 ms   (+0.25%) |       2   →       2              |       80.20 ms →       80.40 ms   (+0.25%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.57 ms →       39.67 ms   (+0.25%) |       2   →       2              |       79.13 ms →       79.33 ms   (+0.25%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       35.00 ns →       21.50 ns  (-38.57%) |       2   →       2              |       70.00 ns →       43.00 ns  (-38.57%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.09 ms →       39.21 ms   (+0.30%) |       2   →       2              |       78.18 ms →       78.42 ms   (+0.30%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       25.50 ns →       30.00 ns  (+17.65%) |       2   →       2              |       51.00 ns →       60.00 ns  (+17.65%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.01 ms →       61.48 ms   (+7.85%) |       1   →       1              |       57.01 ms →       61.48 ms   (+7.85%) | 
  │ │ └ sddk::wf_trans                                                  |       30.75 ms →       30.77 ms   (+0.08%) |       1   →       1              |       30.75 ms →       30.77 ms   (+0.08%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.74 ms →       30.77 ms   (+0.08%) |       1   →       1              |       30.74 ms →       30.77 ms   (+0.08%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      343.00 ns →      569.00 ns  (+65.89%) |       1   →       1              |      343.00 ns →      569.00 ns  (+65.89%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.00 s  →      123.59 s    (+0.48%) |       1   →       1              |      123.00 s  →      123.59 s    (+0.48%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.82 ms →        5.81 ms   (-0.17%) |      19   →      19              |      110.59 ms →      110.40 ms   (-0.17%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.64 s  →        4.65 s    (+0.14%) |      26   →      26              |      120.76 s  →      120.93 s    (+0.14%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.85 ms →        4.54 ms   (-6.49%) |      26   →      26              |      126.16 ms →      117.97 ms   (-6.49%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.49 ms →        4.18 ms   (-6.93%) |      26   →      26              |      116.64 ms →      108.56 ms   (-6.93%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      990.64 μs →      983.51 μs   (-0.72%) |      26   →      26              |       25.76 ms →       25.57 ms   (-0.72%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.61 ms →        2.31 ms  (-11.48%) |      26   →      26              |       67.74 ms →       59.96 ms  (-11.48%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.66 μs →       64.74 μs   (+0.13%) |      52   →      52              |        3.36 ms →        3.37 ms   (+0.13%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       87.65 μs →       87.13 μs   (-0.59%) |      26   →      26              |        2.28 ms →        2.27 ms   (-0.59%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       79.28 μs →       76.98 μs   (-2.91%) |      26   →      26              |        2.06 ms →        2.00 ms   (-2.91%) | 
  │ │ ├ sirius::Band::solve                                             |        2.66 s  →        2.66 s    (+0.08%) |      26   →      26              |       69.16 s  →       69.21 s    (+0.08%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      147.91 μs →      151.84 μs   (+2.66%) |      26   →      26              |        3.85 ms →        3.95 ms   (+2.66%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      140.82 μs →      145.02 μs   (+2.98%) |      26   →      26              |        3.66 ms →        3.77 ms   (+2.98%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.28 μs →        4.75 μs   (-9.92%) |      26   →      26              |      137.16 μs →      123.55 μs   (-9.92%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.53 s  →        2.53 s    (+0.03%) |      26   →      26              |       65.82 s  →       65.84 s    (+0.03%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.69 ms →       95.69 ms   (-1.04%) |      26   →      26              |        2.51 s  →        2.49 s    (-1.04%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.79 ms →        7.71 ms   (-1.01%) |     156   →     156              |        1.21 s  →        1.20 s    (-1.01%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.98 ms →        5.99 ms   (+0.17%) |      26   →      26              |      155.44 ms →      155.71 ms   (+0.17%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      348.61 μs →      349.17 μs   (+0.16%) |      26   →      26              |        9.06 ms →        9.08 ms   (+0.16%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.32 ms →        2.31 ms   (-0.27%) |      52   →      52              |      120.67 ms →      120.35 ms   (-0.27%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.39 s  →        2.39 s    (+0.07%) |      26   →      26              |       62.22 s  →       62.26 s    (+0.07%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.49 ms →      136.75 ms   (+0.19%) |     262   →     262              |       35.76 s  →       35.83 s    (+0.19%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.63 ms →       55.47 ms   (-0.29%) |     262   →     262              |       14.58 s  →       14.53 s    (-0.29%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.91 μs →        1.93 μs   (+1.13%) |     262   →     262              |      499.82 μs →      505.46 μs   (+1.13%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.57 μs →        1.59 μs   (+1.37%) |     262   →     262              |      411.79 μs →      417.43 μs   (+1.37%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      353.95 ns →      337.03 ns   (-4.78%) |     262   →     262              |       92.74 μs →       88.30 μs   (-4.78%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      433.32 ns →      433.10 ns   (-0.05%) |     262   →     262              |      113.53 μs →      113.47 μs   (-0.05%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.46 ms →        7.45 ms   (-0.06%) |     262   →     262              |        1.95 s  →        1.95 s    (-0.06%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.64 ms →       25.07 ms   (+1.74%) |     262   →     262              |        6.46 s  →        6.57 s    (+1.74%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.37 ms →       24.37 ms   (+0.01%) |     524   →     524              |       12.77 s  →       12.77 s    (+0.01%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       42.40 ms →       42.41 ms   (+0.03%) |     262   →     262              |       11.11 s  →       11.11 s    (+0.03%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.22 ms →        6.23 ms   (+0.23%) |     498   →     498              |        3.10 s  →        3.10 s    (+0.23%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       64.69 ns →       95.07 ns  (+46.96%) |     498   →     498              |       32.22 μs →       47.34 μs  (+46.96%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.10 ms →        5.12 ms   (+0.26%) |     498   →     498              |        2.54 s  →        2.55 s    (+0.26%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       28.97 ns →       26.58 ns   (-8.24%) |     498   →     498              |       14.43 μs →       13.24 μs   (-8.24%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        7.22 ms →        7.17 ms   (-0.62%) |     262   →     262              |        1.89 s  →        1.88 s    (-0.62%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.30 ms →       10.31 ms   (+0.08%) |     262   →     262              |        2.70 s  →        2.70 s    (+0.08%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.50 ms →       14.52 ms   (+0.16%) |     236   →     236              |        3.42 s  →        3.43 s    (+0.16%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.83 ms →        4.84 ms   (+0.16%) |     708   →     708              |        3.42 s  →        3.43 s    (+0.16%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.56 ms →       10.56 ms   (-0.06%) |     262   →     262              |        2.77 s  →        2.77 s    (-0.06%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.17 ms →       10.18 ms   (+0.07%) |     262   →     262              |        2.67 s  →        2.67 s    (+0.07%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       25.07 ns →       37.22 ns  (+48.44%) |     262   →     262              |        6.57 μs →        9.75 μs  (+48.44%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.06 ms →        9.06 ms   (+0.06%) |     262   →     262              |        2.37 s  →        2.37 s    (+0.06%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.28 ns →       43.46 ns   (+0.42%) |     262   →     262              |       11.34 μs →       11.39 μs   (+0.42%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.92 ms →       17.82 ms   (-0.56%) |     262   →     262              |        4.69 s  →        4.67 s    (-0.56%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.15 ms →       13.15 ms   (-0.06%) |     252   →     252              |        3.31 s  →        3.31 s    (-0.06%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.66 ms →       11.71 ms   (+0.38%) |     243   →     242     (-0.41%) |        2.83 s  →        2.83 s    (-0.03%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.83 ms →        5.85 ms   (+0.38%) |     486   →     484     (-0.41%) |        2.83 s  →        2.83 s    (-0.04%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.71 ms →        1.71 ms   (+0.28%) |     243   →     242     (-0.41%) |      415.53 ms →      414.98 ms   (-0.13%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.74 ms →       53.76 ms   (+0.04%) |      85   →      85              |        4.57 s  →        4.57 s    (+0.04%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.45 ms →       31.46 ms   (+0.03%) |     144   →     144              |        4.53 s  →        4.53 s    (+0.03%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.31 ms →       22.32 ms   (+0.03%) |     203   →     203              |        4.53 s  →        4.53 s    (+0.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      433.85 ns →      423.42 ns   (-2.40%) |      26   →      26              |       11.28 μs →       11.01 μs   (-2.40%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       49.76 μs →       29.07 μs  (-41.58%) |      26   →      26              |        1.29 ms →      755.89 μs  (-41.58%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      601.49 μs →      612.97 μs   (+1.91%) |      26   →      26              |       15.64 ms →       15.94 ms   (+1.91%) | 
  │ │ ├ sirius::Density::generate                                       |      777.73 ms →      769.99 ms   (-1.00%) |      26   →      26              |       20.22 s  →       20.02 s    (-1.00%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.80 ms →      401.94 ms   (-0.21%) |      26   →      26              |       10.47 s  →       10.45 s    (-0.21%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.19 μs →        2.99 μs   (-6.33%) |      26   →      26              |       82.93 μs →       77.69 μs   (-6.33%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.89 μs →        2.70 μs   (-6.75%) |      26   →      26              |       75.18 μs →       70.10 μs   (-6.75%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.23 ms →      100.25 ms   (+0.02%) |      26   →      26              |        2.61 s  →        2.61 s    (+0.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.44 μs →       10.49 μs   (+0.43%) |      26   →      26              |      271.50 μs →      272.68 μs   (+0.43%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (-0.03%) |      26   →      26              |      185.34 ms →      185.28 ms   (-0.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.15 ms →       91.21 ms   (+0.07%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.07%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      554.50 ns →      671.46 ns  (+21.09%) |      26   →      26              |       14.42 μs →       17.46 μs  (+21.09%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.75 ms →      162.41 ms   (-0.21%) |      26   →      26              |        4.23 s  →        4.22 s    (-0.21%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.57%) |      26   →      26              |       42.89 ms →       42.65 ms   (-0.57%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.25 ms →       88.32 ms   (+0.08%) |      26   →      26              |        2.29 s  →        2.30 s    (+0.08%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.02 ms →       88.10 ms   (+0.08%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.08%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.78 ms →      276.09 ms   (+0.11%) |      26   →      26              |        7.17 s  →        7.18 s    (+0.11%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.78 ms →      276.09 ms   (+0.11%) |      26   →      26              |        7.17 s  →        7.18 s    (+0.11%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       26.49 ms →       25.58 ms   (-3.41%) |      26   →      26              |      688.64 ms →      665.18 ms   (-3.41%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.21 ms →      226.10 ms   (+0.40%) |      26   →      26              |        5.86 s  →        5.88 s    (+0.40%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.93 ms →       23.24 ms   (+1.35%) |      26   →      26              |      596.16 ms →      604.20 ms   (+1.35%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.41 ms →       81.22 ms   (-0.23%) |      26   →      26              |        2.12 s  →        2.11 s    (-0.23%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       14.14 ms →        7.13 ms  (-49.56%) |      26   →      26              |      367.73 ms →      185.47 ms  (-49.56%) | 
  │ │ ├ sirius::Density::mix                                            |      215.66 ms →      227.23 ms   (+5.36%) |      26   →      26              |        5.61 s  →        5.91 s    (+5.36%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      966.83 μs →      921.37 μs   (-4.70%) |      26   →      26              |       25.14 ms →       23.96 ms   (-4.70%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.39 ms →       10.35 ms   (-0.42%) |     334   →     463    (+38.62%) |        3.47 s  →        4.79 s   (+38.04%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.94 ms →        9.87 ms   (-0.74%) |     334   →     463    (+38.62%) |        3.32 s  →        4.57 s   (+37.59%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.94 ms →        9.87 ms   (-0.74%) |     334   →     463    (+38.62%) |        3.32 s  →        4.57 s   (+37.59%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.49 ms →        6.49 ms  (-13.37%) |      26   →      26              |      194.65 ms →      168.62 ms  (-13.37%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.67 ms →        5.54 ms  (-16.87%) |      26   →      26              |      173.30 ms →      144.06 ms  (-16.87%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.94 ms →      582.95 ms   (+0.52%) |      26   →      26              |       15.08 s  →       15.16 s    (+0.52%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.10 ms →      136.74 ms   (-0.99%) |      26   →      26              |        3.59 s  →        3.56 s    (-0.99%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       17.12 ms →       16.25 ms   (-5.12%) |      26   →      26              |      445.19 ms →      422.41 ms   (-5.12%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.25 ms →       10.40 ms   (+1.51%) |      26   →      26              |      266.48 ms →      270.51 ms   (+1.51%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.00 ms →        9.85 ms   (-1.52%) |      26   →      26              |      260.10 ms →      256.16 ms   (-1.52%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.00 ms →        9.85 ms   (-1.52%) |      26   →      26              |      260.08 ms →      256.13 ms   (-1.52%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      567.50 μs →      552.65 μs   (-2.62%) |      52   →      52              |       29.51 ms →       28.74 ms   (-2.62%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.28 ms →       49.12 ms   (-0.33%) |      26   →      26              |        1.28 s  →        1.28 s    (-0.33%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.91 ms →       46.74 ms   (-0.36%) |      26   →      26              |        1.22 s  →        1.22 s    (-0.36%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.05 ms →        3.02 ms   (-0.97%) |      52   →      52              |      158.40 ms →      156.86 ms   (-0.97%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.57 ms →        5.35 ms   (-4.01%) |      26   →      26              |      144.87 ms →      139.06 ms   (-4.01%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.68 ms →        6.58 ms   (-1.48%) |      26   →      26              |      173.59 ms →      171.02 ms   (-1.48%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       90.94 ms   (-0.02%) |      26   →      26              |        2.37 s  →        2.36 s    (-0.02%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.46 ms →      297.15 ms   (+1.60%) |      26   →      26              |        7.60 s  →        7.73 s    (+1.60%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.26 ms →      280.71 ms   (-0.19%) |      26   →      26              |        7.31 s  →        7.30 s    (-0.19%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.26 ms →      280.71 ms   (-0.19%) |      26   →      26              |        7.31 s  →        7.30 s    (-0.19%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       28.88 ms →       27.30 ms   (-5.48%) |      26   →      26              |      750.84 ms →      709.72 ms   (-5.48%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.59 ms →      225.21 ms   (+0.28%) |      26   →      26              |        5.84 s  →        5.86 s    (+0.28%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.99 ms →       24.40 ms   (+1.68%) |      26   →      26              |      623.83 ms →      634.31 ms   (+1.68%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.77 ms →        5.88 ms  (-24.30%) |      26   →      26              |      201.91 ms →      152.85 ms  (-24.30%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.72 ms →       10.84 ms   (+1.16%) |     182   →     182              |        1.95 s  →        1.97 s    (+1.16%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.36 ms →       10.31 ms   (-0.54%) |     182   →     182              |        1.89 s  →        1.88 s    (-0.54%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.36 ms →       10.31 ms   (-0.54%) |     182   →     182              |        1.89 s  →        1.88 s    (-0.54%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.47 ms →       10.30 ms   (-1.56%) |      78   →      78              |      816.49 ms →      803.71 ms   (-1.56%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.77 ms →        9.81 ms   (+0.45%) |      78   →      78              |      761.74 ms →      765.18 ms   (+0.45%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.97 ms →       10.11 ms   (+1.36%) |      26   →      26              |      259.25 ms →      262.78 ms   (+1.36%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      139.31 μs →      110.01 μs  (-21.03%) |      26   →      26              |        3.62 ms →        2.86 ms  (-21.03%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      134.98 μs →      105.39 μs  (-21.93%) |      26   →      26              |        3.51 ms →        2.74 ms  (-21.93%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.47 ms →        5.25 ms  (-29.69%) |       2   →       2              |       14.93 ms →       10.50 ms  (-29.69%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.47 ms →       10.55 ms   (+0.73%) |       6   →       6              |       62.82 ms →       63.27 ms   (+0.73%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.29 ms →       10.54 ms   (+2.43%) |       6   →       6              |       61.71 ms →       63.21 ms   (+2.43%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.29 ms →       10.53 ms   (+2.43%) |       6   →       6              |       61.71 ms →       63.21 ms   (+2.43%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.10 ms →        9.97 ms   (-1.26%) |       3   →       3              |       30.31 ms →       29.92 ms   (-1.26%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.09 ms →        9.97 ms   (-1.25%) |       3   →       3              |       30.28 ms →       29.90 ms   (-1.25%) | 
  ├ sirius::Periodic_function|inner                                     |       10.10 ms →       10.49 ms   (+3.81%) |       2   →       2              |       20.20 ms →       20.97 ms   (+3.81%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.09 ms →       10.48 ms   (+3.81%) |       2   →       2              |       20.19 ms →       20.95 ms   (+3.81%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.09 ms →       10.48 ms   (+3.80%) |       2   →       2              |       20.19 ms →       20.95 ms   (+3.80%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.00 ms →       10.07 ms   (+0.70%) |       1   →       1              |       10.00 ms →       10.07 ms   (+0.70%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.00 ms →       10.07 ms   (+0.71%) |       1   →       1              |       10.00 ms →       10.07 ms   (+0.71%) | 
+ └ sirius::finalize                                                    |      232.49 ms →      196.48 ms  (-15.49%) |       1   →       1              |      232.49 ms →      196.48 ms  (-15.49%) | 
  ====================================================================================================================================================================================================
```
