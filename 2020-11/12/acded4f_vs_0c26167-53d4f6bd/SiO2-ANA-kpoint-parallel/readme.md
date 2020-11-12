# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs acded4f8dc8bf829fcf788e7dbd08a23ea769390
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      130.76 s  →      151.99 s   (+16.23%) |       1   →       1              |      130.76 s  →      151.99 s   (+16.23%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.70 s    (+0.25%) |       1   →       1              |        2.69 s  →        2.70 s    (+0.25%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        3.01 s    (+3.08%) |       1   →       1              |        2.92 s  →        3.01 s    (+3.08%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       44.16 ms →       37.41 ms  (-15.29%) |       1   →       1              |       44.16 ms →       37.41 ms  (-15.29%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      137.58 ms →      219.96 ms  (+59.88%) |       1   →       1              |      137.58 ms →      219.96 ms  (+59.88%) | 
- │ │ ├ sirius::Atom_type::init                                         |       56.92 ms →       98.57 ms  (+73.15%) |       2   →       2              |      113.85 ms →      197.13 ms  (+73.15%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.66 ms →       22.75 ms   (-3.83%) |       1   →       1              |       23.66 ms →       22.75 ms   (-3.83%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.26 ms →        6.37 ms   (+1.82%) |       1   →       1              |        6.26 ms →        6.37 ms   (+1.82%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.35 ms →       16.34 ms   (-5.84%) |       1   →       1              |       17.35 ms →       16.34 ms   (-5.84%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.33 ms →       16.32 ms   (-5.85%) |       1   →       1              |       17.33 ms →       16.32 ms   (-5.85%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.16 ms   (+0.65%) |       1   →       1              |        4.13 ms →        4.16 ms   (+0.65%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (+0.04%) |       1   →       1              |        2.34 ms →        2.34 ms   (+0.04%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.77 μs →      102.92 μs   (-3.61%) |       1   →       1              |      106.77 μs →      102.92 μs   (-3.61%) | 
  │ └ sirius::Simulation_context::update                                |        2.69 s  →        2.71 s    (+0.49%) |       1   →       1              |        2.69 s  →        2.71 s    (+0.49%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.98 ms →       10.92 ms   (-0.53%) |       1   →       1              |       10.98 ms →       10.92 ms   (-0.53%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.48 ms →        4.47 ms   (-0.22%) |       1   →       1              |        4.48 ms →        4.47 ms   (-0.22%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.46 ms →        6.42 ms   (-0.73%) |       1   →       1              |        6.46 ms →        6.42 ms   (-0.73%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.44 ms →        6.40 ms   (-0.75%) |       1   →       1              |        6.44 ms →        6.40 ms   (-0.75%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.96 ms →        3.89 ms   (-1.80%) |       1   →       1              |        3.96 ms →        3.89 ms   (-1.80%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+1.01%) |       1   →       1              |        2.32 ms →        2.34 ms   (+1.01%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      101.82 μs →      100.24 μs   (-1.55%) |       1   →       1              |      101.82 μs →      100.24 μs   (-1.55%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.43 ms →       62.55 ms   (+0.19%) |       2   →       2              |      124.86 ms →      125.09 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.14 ms   (+0.20%) |       2   →       2              |       10.26 ms →       10.28 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.23%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.78 ms →       21.75 ms   (-0.12%) |       2   →       2              |       43.56 ms →       43.51 ms   (-0.12%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.81 ms →       14.82 ms   (+0.04%) |       2   →       2              |       29.63 ms →       29.64 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.71 ms →       19.59 ms   (-0.57%) |       4   →       4              |       78.83 ms →       78.38 ms   (-0.57%) | 
  │   ├ sddk::Gvec::init                                                |      171.28 ms →      172.45 ms   (+0.69%) |       2   →       2              |      342.56 ms →      344.90 ms   (+0.69%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.72 ms →      129.94 ms   (+0.95%) |       2   →       2              |      257.43 ms →      259.88 ms   (+0.95%) | 
  │   ├ sddk::Gvec_shells                                               |      168.16 ms →      164.35 ms   (-2.27%) |       1   →       1              |      168.16 ms →      164.35 ms   (-2.27%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.71%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.71%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.28 ms →      294.67 ms   (+0.82%) |       2   →       2              |      584.57 ms →      589.34 ms   (+0.82%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.59 ms →       35.64 ms   (+0.15%) |       1   →       1              |       35.59 ms →       35.64 ms   (+0.15%) | 
  │ ├ sirius::K_point::K_point                                          |        2.62 μs →        2.63 μs   (+0.48%) |       4   →       4              |       10.47 μs →       10.52 μs   (+0.48%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.48 ms →       35.53 ms   (+0.12%) |       1   →       1              |       35.48 ms →       35.53 ms   (+0.12%) | 
  │   └ sirius::K_point::initialize                                     |       35.38 ms →       35.43 ms   (+0.13%) |       1   →       1              |       35.38 ms →       35.43 ms   (+0.13%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.10 ms →       18.18 ms   (+0.46%) |       1   →       1              |       18.10 ms →       18.18 ms   (+0.46%) | 
  │     │ └ sddk::Gvec::init                                            |        8.09 ms →        8.12 ms   (+0.41%) |       1   →       1              |        8.09 ms →        8.12 ms   (+0.41%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.49 μs →        9.29 μs   (-2.17%) |       1   →       1              |        9.49 μs →        9.29 μs   (-2.17%) | 
  │     └ sirius::K_point::update                                       |       12.32 ms →       12.43 ms   (+0.96%) |       1   →       1              |       12.32 ms →       12.43 ms   (+0.96%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.20 ms   (+1.77%) |       1   →       1              |        6.09 ms →        6.20 ms   (+1.77%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.51 ms →        3.65 ms   (+3.93%) |       1   →       1              |        3.51 ms →        3.65 ms   (+3.93%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.44 ms →        5.25 ms   (-3.40%) |       2   →       2              |       10.88 ms →       10.51 ms   (-3.40%) | 
  ├ sirius::Potential                                                   |      162.11 ms →      159.31 ms   (-1.73%) |       1   →       1              |      162.11 ms →      159.31 ms   (-1.73%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.22 ms →        5.85 ms   (-6.00%) |       6   →       6              |       37.33 ms →       35.09 ms   (-6.00%) | 
  │ └ sirius::Potential::update                                         |      124.03 ms →      123.46 ms   (-0.45%) |       1   →       1              |      124.03 ms →      123.46 ms   (-0.45%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.32 ms →      122.66 ms   (-0.53%) |       1   →       1              |      123.32 ms →      122.66 ms   (-0.53%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      115.93 ms →      115.48 ms   (-0.39%) |       1   →       1              |      115.93 ms →      115.48 ms   (-0.39%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.47 ms →        6.29 ms   (-2.82%) |       1   →       1              |        6.47 ms →        6.29 ms   (-2.82%) | 
  ├ sirius::Density                                                     |      133.18 ms →      134.85 ms   (+1.26%) |       1   →       1              |      133.18 ms →      134.85 ms   (+1.26%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.16 ms →        5.11 ms   (-0.92%) |       2   →       2              |       10.32 ms →       10.23 ms   (-0.92%) | 
  │ └ sirius::Density::update                                           |      122.58 ms →      124.35 ms   (+1.45%) |       1   →       1              |      122.58 ms →      124.35 ms   (+1.45%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      122.16 ms →      123.92 ms   (+1.44%) |       1   →       1              |      122.16 ms →      123.92 ms   (+1.44%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.85 μs →      102.10 μs   (-3.54%) |       1   →       1              |      105.85 μs →      102.10 μs   (-3.54%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      116.47 ms →      118.26 ms   (+1.54%) |       1   →       1              |      116.47 ms →      118.26 ms   (+1.54%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.16 ms →        5.11 ms   (-0.85%) |       1   →       1              |        5.16 ms →        5.11 ms   (-0.85%) | 
  ├ sirius::Density::initial_density                                    |      174.41 ms →      174.97 ms   (+0.32%) |       1   →       1              |      174.41 ms →      174.97 ms   (+0.32%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      121.79 ms →      122.23 ms   (+0.36%) |       1   →       1              |      121.79 ms →      122.23 ms   (+0.36%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.29 ms →        5.15 ms   (-2.52%) |       2   →       2              |       10.57 ms →       10.30 ms   (-2.52%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.06 ms →        9.94 ms   (-1.14%) |       1   →       1              |       10.06 ms →        9.94 ms   (-1.14%) | 
  ├ sirius::Potential::generate                                         |      590.98 ms →      594.95 ms   (+0.67%) |       1   →       1              |      590.98 ms →      594.95 ms   (+0.67%) | 
  │ ├ sirius::Potential::poisson                                        |      136.51 ms →      137.53 ms   (+0.75%) |       1   →       1              |      136.51 ms →      137.53 ms   (+0.75%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.34 ms →        5.32 ms   (-0.37%) |       1   →       1              |        5.34 ms →        5.32 ms   (-0.37%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.26 ms →       10.92 ms   (+6.35%) |       1   →       1              |       10.26 ms →       10.92 ms   (+6.35%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.24 ms →        9.90 ms   (-3.38%) |       1   →       1              |       10.24 ms →        9.90 ms   (-3.38%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.24 ms →        9.89 ms   (-3.39%) |       1   →       1              |       10.24 ms →        9.89 ms   (-3.39%) | 
  │ ├ sirius::Periodic_function::add                                    |      546.41 μs →      557.30 μs   (+1.99%) |       2   →       2              |        1.09 ms →        1.11 ms   (+1.99%) | 
  │ ├ sirius::Potential::xc                                             |       53.51 ms →       56.79 ms   (+6.12%) |       1   →       1              |       53.51 ms →       56.79 ms   (+6.12%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.23 ms →       54.36 ms   (+6.11%) |       1   →       1              |       51.23 ms →       54.36 ms   (+6.11%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.68 ms →        5.75 ms   (+1.20%) |       2   →       2              |       11.36 ms →       11.50 ms   (+1.20%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.20 ms →        6.07 ms  (+16.88%) |       1   →       1              |        5.20 ms →        6.07 ms  (+16.88%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.90 ms →        5.81 ms   (-1.59%) |       1   →       1              |        5.90 ms →        5.81 ms   (-1.59%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.83 ms →       92.68 ms   (-0.16%) |       1   →       1              |       92.83 ms →       92.68 ms   (-0.16%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.79 ms →      299.64 ms   (-0.05%) |       1   →       1              |      299.79 ms →      299.64 ms   (-0.05%) | 
  ├ sirius::Hamiltonian0                                                |        8.38 ms →        8.41 ms   (+0.45%) |       1   →       1              |        8.38 ms →        8.41 ms   (+0.45%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        8.05 ms   (+0.30%) |       1   →       1              |        8.02 ms →        8.05 ms   (+0.30%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms →        4.78 ms   (+0.50%) |       1   →       1              |        4.76 ms →        4.78 ms   (+0.50%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.33 ms   (-0.39%) |       1   →       1              |        2.34 ms →        2.33 ms   (-0.39%) | 
  │ ├ sirius::Non_local_operator                                        |       63.37 μs →       63.75 μs   (+0.60%) |       2   →       2              |      126.74 μs →      127.50 μs   (+0.60%) | 
  │ ├ sirius::D_operator::initialize                                    |      100.33 μs →      101.51 μs   (+1.17%) |       1   →       1              |      100.33 μs →      101.51 μs   (+1.17%) | 
  │ └ sirius::Q_operator::initialize                                    |       73.55 μs →       79.45 μs   (+8.02%) |       1   →       1              |       73.55 μs →       79.45 μs   (+8.02%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.90 s    (+2.86%) |       1   →       1              |        1.85 s  →        1.90 s    (+2.86%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.69 ms →       18.05 ms   (-3.45%) |       1   →       1              |       18.69 ms →       18.05 ms   (-3.45%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      183.56 μs →      172.68 μs   (-5.93%) |       1   →       1              |      183.56 μs →      172.68 μs   (-5.93%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       17.87 ms   (-3.43%) |       1   →       1              |       18.51 ms →       17.87 ms   (-3.43%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.88 s    (+2.93%) |       1   →       1              |        1.83 s  →        1.88 s    (+2.93%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.33 ms →      136.61 ms   (+8.13%) |       4   →       4              |      505.33 ms →      546.43 ms   (+8.13%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.76 ms →       51.79 ms   (-1.84%) |       1   →       1              |       52.76 ms →       51.79 ms   (-1.84%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.31 ms →       20.96 ms   (-1.63%) |       1   →       1              |       21.31 ms →       20.96 ms   (-1.63%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.54 ms →      642.78 ms   (+1.30%) |       1   →       1              |      634.54 ms →      642.78 ms   (+1.30%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.79 ms →      302.30 ms   (+1.52%) |       1   →       1              |      297.79 ms →      302.30 ms   (+1.52%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.83 μs →        3.00 μs  (-21.59%) |       1   →       1              |        3.83 μs →        3.00 μs  (-21.59%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.83 μs →        2.15 μs  (-23.82%) |       1   →       1              |        2.83 μs →        2.15 μs  (-23.82%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      327.00 ns →      400.00 ns  (+22.32%) |       1   →       1              |      327.00 ns →      400.00 ns  (+22.32%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      406.00 ns →      689.00 ns  (+69.70%) |       1   →       1              |      406.00 ns →      689.00 ns  (+69.70%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.12%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.12%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.62 ms →      121.60 ms   (+0.81%) |       1   →       1              |      120.62 ms →      121.60 ms   (+0.81%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.44 ms →      104.81 ms   (+1.32%) |       2   →       2              |      206.88 ms →      209.62 ms   (+1.32%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.15 ms →       40.28 ms   (+0.33%) |       2   →       2              |       80.30 ms →       80.57 ms   (+0.33%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.62 ms →       39.72 ms   (+0.26%) |       2   →       2              |       79.23 ms →       79.44 ms   (+0.26%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       16.50 ns →       19.00 ns  (+15.15%) |       2   →       2              |       33.00 ns →       38.00 ns  (+15.15%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.15 ms →       39.26 ms   (+0.29%) |       2   →       2              |       78.29 ms →       78.52 ms   (+0.29%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       17.00 ns →       29.00 ns  (+70.59%) |       2   →       2              |       34.00 ns →       58.00 ns  (+70.59%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.39 ms →       62.47 ms  (+10.80%) |       1   →       1              |       56.39 ms →       62.47 ms  (+10.80%) | 
  │ │ └ sddk::wf_trans                                                  |       30.81 ms →       30.75 ms   (-0.20%) |       1   →       1              |       30.81 ms →       30.75 ms   (-0.20%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.81 ms →       30.74 ms   (-0.20%) |       1   →       1              |       30.81 ms →       30.74 ms   (-0.20%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      374.00 ns →      509.00 ns  (+36.10%) |       1   →       1              |      374.00 ns →      509.00 ns  (+36.10%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      121.15 s  →      142.26 s   (+17.43%) |       1   →       1              |      121.15 s  →      142.26 s   (+17.43%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.75 ms →        5.80 ms   (+1.01%) |      19   →      83   (+336.84%) |      109.18 ms →      481.75 ms (+341.23%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.64 s  →        4.72 s    (+1.71%) |      26   →      30    (+15.38%) |      120.56 s  →      141.48 s   (+17.35%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.50 ms →        4.75 ms  (-13.62%) |      26   →      30    (+15.38%) |      142.99 ms →      142.52 ms   (-0.33%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.13 ms →        4.39 ms  (-14.54%) |      26   →      30    (+15.38%) |      133.47 ms →      131.62 ms   (-1.39%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      983.62 μs →      988.13 μs   (+0.46%) |      26   →      30    (+15.38%) |       25.57 ms →       29.64 ms  (+15.91%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.26 ms →        2.51 ms  (-23.01%) |      26   →      30    (+15.38%) |       84.83 ms →       75.36 ms  (-11.17%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       64.72 μs →       64.45 μs   (-0.42%) |      52   →      60    (+15.38%) |        3.37 ms →        3.87 ms  (+14.90%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       88.14 μs →       88.54 μs   (+0.46%) |      26   →      30    (+15.38%) |        2.29 ms →        2.66 ms  (+15.92%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       78.68 μs →       77.82 μs   (-1.10%) |      26   →      30    (+15.38%) |        2.05 ms →        2.33 ms  (+14.12%) | 
! │ │ ├ sirius::Band::solve                                             |        2.66 s  →        2.44 s    (-8.18%) |      26   →      30    (+15.38%) |       69.06 s  →       73.16 s    (+5.94%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      150.51 μs →      154.08 μs   (+2.37%) |      26   →      30    (+15.38%) |        3.91 ms →        4.62 ms  (+18.12%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      143.82 μs →      147.89 μs   (+2.83%) |      26   →      30    (+15.38%) |        3.74 ms →        4.44 ms  (+18.64%) | 
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.96 μs →        4.50 μs   (-9.32%) |      26   →      30    (+15.38%) |      128.92 μs →      134.88 μs   (+4.63%) | 
! │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.52 s  →        2.34 s    (-7.39%) |      26   →      30    (+15.38%) |       65.64 s  →       70.14 s    (+6.86%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.78 ms →       89.77 ms   (-7.24%) |      26   →      30    (+15.38%) |        2.52 s  →        2.69 s    (+7.03%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.82 ms →        6.73 ms  (-13.91%) |     156   →     180    (+15.38%) |        1.22 s  →        1.21 s    (-0.66%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.04 ms →        5.94 ms   (-1.75%) |      26   →      30    (+15.38%) |      157.08 ms →      178.07 ms  (+13.36%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.86 μs →      346.38 μs   (-1.56%) |      26   →      30    (+15.38%) |        9.15 ms →       10.39 ms  (+13.59%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.34 ms →        2.29 ms   (-1.76%) |      52   →      60    (+15.38%) |      121.42 ms →      137.63 ms  (+13.35%) | 
! │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.39 s  →        2.21 s    (-7.52%) |      26   →      30    (+15.38%) |       62.04 s  →       66.20 s    (+6.71%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.00 ms →      138.27 ms   (+1.67%) |     262   →     278     (+6.11%) |       35.63 s  →       38.44 s    (+7.88%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.47 ms →       55.96 ms   (+0.88%) |     262   →     278     (+6.11%) |       14.53 s  →       15.56 s    (+7.04%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.83 μs →        1.98 μs   (+8.13%) |     262   →     278     (+6.11%) |      480.39 μs →      551.18 μs  (+14.73%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.55 μs →        1.71 μs  (+10.46%) |     262   →     278     (+6.11%) |      404.81 μs →      474.47 μs  (+17.21%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      356.57 ns →      322.49 ns   (-9.56%) |     262   →     278     (+6.11%) |       93.42 μs →       89.65 μs   (-4.03%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      438.27 ns →      444.72 ns   (+1.47%) |     262   →     278     (+6.11%) |      114.83 μs →      123.63 μs   (+7.67%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.45 ms   (+0.03%) |     262   →     278     (+6.11%) |        1.95 s  →        2.07 s    (+6.14%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.46 ms →       25.67 ms   (+4.91%) |     262   →     278     (+6.11%) |        6.41 s  →        7.13 s   (+11.32%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.30 ms →       24.59 ms   (+1.19%) |     524   →     556     (+6.11%) |       12.73 s  →       13.67 s    (+7.37%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       42.45 ms →       41.93 ms   (-1.23%) |     262   →     278     (+6.11%) |       11.12 s  →       11.66 s    (+4.80%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.21 ms →        6.18 ms   (-0.57%) |     498   →     526     (+5.62%) |        3.09 s  →        3.25 s    (+5.02%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       62.74 ns →       59.40 ns   (-5.34%) |     498   →     526     (+5.62%) |       31.25 μs →       31.24 μs   (-0.01%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.10 ms →        5.07 ms   (-0.63%) |     498   →     526     (+5.62%) |        2.54 s  →        2.67 s    (+4.96%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       28.41 ns →       49.68 ns  (+74.87%) |     498   →     526     (+5.62%) |       14.15 μs →       26.13 μs  (+84.71%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        7.28 ms →        7.37 ms   (+1.27%) |     262   →     278     (+6.11%) |        1.91 s  →        2.05 s    (+7.45%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.30 ms →       10.47 ms   (+1.59%) |     262   →     278     (+6.11%) |        2.70 s  →        2.91 s    (+7.80%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.50 ms →       13.90 ms   (-4.11%) |     236   →     248     (+5.08%) |        3.42 s  →        3.45 s    (+0.76%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.83 ms →        4.63 ms   (-4.12%) |     708   →     744     (+5.08%) |        3.42 s  →        3.45 s    (+0.76%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.58 ms →       10.45 ms   (-1.21%) |     262   →     278     (+6.11%) |        2.77 s  →        2.91 s    (+4.82%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       10.05 ms   (-1.22%) |     262   →     278     (+6.11%) |        2.67 s  →        2.79 s    (+4.81%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       25.69 ns →       84.76 ns (+229.95%) |     262   →     278     (+6.11%) |        6.73 μs →       23.56 μs (+250.10%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.06 ms →        8.94 ms   (-1.35%) |     262   →     278     (+6.11%) |        2.37 s  →        2.48 s    (+4.67%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       45.34 ns →       55.96 ns  (+23.41%) |     262   →     278     (+6.11%) |       11.88 μs →       15.56 μs  (+30.95%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.65 ms →       17.67 ms   (+0.09%) |     262   →     278     (+6.11%) |        4.62 s  →        4.91 s    (+6.20%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.15 ms →       13.24 ms   (+0.68%) |     252   →     268     (+6.35%) |        3.31 s  →        3.55 s    (+7.08%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.71 ms →       11.70 ms   (-0.08%) |     242   →     259     (+7.02%) |        2.83 s  →        3.03 s    (+6.94%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.85 ms →        5.85 ms   (-0.08%) |     484   →     518     (+7.02%) |        2.83 s  →        3.03 s    (+6.94%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.72 ms →        1.73 ms   (+0.89%) |     242   →     259     (+7.02%) |      415.36 ms →      448.51 ms   (+7.98%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.74 ms →       50.87 ms   (-5.34%) |      85   →      93     (+9.41%) |        4.57 s  →        4.73 s    (+3.57%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.45 ms →       30.06 ms   (-4.41%) |     144   →     156     (+8.33%) |        4.53 s  →        4.69 s    (+3.55%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.31 ms →       21.41 ms   (-4.02%) |     203   →     219     (+7.88%) |        4.53 s  →        4.69 s    (+3.55%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      407.35 ns →      435.40 ns   (+6.89%) |      26   →      30    (+15.38%) |       10.59 μs →       13.06 μs  (+23.33%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.03 μs →       51.23 μs  (+76.48%) |      26   →      30    (+15.38%) |      754.74 μs →        1.54 ms (+103.63%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      607.84 μs →      615.24 μs   (+1.22%) |      26   →      30    (+15.38%) |       15.80 ms →       18.46 ms  (+16.79%) | 
- │ │ ├ sirius::Density::generate                                       |      774.01 ms →      778.88 ms   (+0.63%) |      26   →      30    (+15.38%) |       20.12 s  →       23.37 s   (+16.11%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      401.95 ms →      403.12 ms   (+0.29%) |      26   →      30    (+15.38%) |       10.45 s  →       12.09 s   (+15.72%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.37 μs →        3.24 μs   (-4.07%) |      26   →      30    (+15.38%) |       87.69 μs →       97.07 μs  (+10.69%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.09 μs →        2.99 μs   (-3.16%) |      26   →      30    (+15.38%) |       80.41 μs →       89.84 μs  (+11.73%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.15 ms →      100.71 ms   (+0.56%) |      26   →      30    (+15.38%) |        2.60 s  →        3.02 s   (+16.03%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.53 μs →       10.58 μs   (+0.44%) |      26   →      30    (+15.38%) |      273.77 μs →      317.29 μs  (+15.90%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (-0.00%) |      26   →      30    (+15.38%) |      185.27 ms →      213.77 ms  (+15.38%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.11 ms →       91.67 ms   (+0.62%) |      26   →      30    (+15.38%) |        2.37 s  →        2.75 s   (+16.10%) | 
! │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      606.27 ns →      554.23 ns   (-8.58%) |      26   →      30    (+15.38%) |       15.76 μs →       16.63 μs   (+5.48%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.15 ms →      162.40 ms   (-0.46%) |      26   →      30    (+15.38%) |        4.24 s  →        4.87 s   (+14.85%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.49%) |      26   →      30    (+15.38%) |       42.90 ms →       49.26 ms  (+14.82%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       88.41 ms →       88.26 ms   (-0.16%) |      26   →      30    (+15.38%) |        2.30 s  →        2.65 s   (+15.20%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.18 ms →       88.03 ms   (-0.17%) |      26   →      30    (+15.38%) |        2.29 s  →        2.64 s   (+15.19%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.19 ms →      279.88 ms   (+0.97%) |      26   →      30    (+15.38%) |        7.21 s  →        8.40 s   (+16.50%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.19 ms →      279.88 ms   (+0.97%) |      26   →      30    (+15.38%) |        7.21 s  →        8.40 s   (+16.50%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       26.31 ms →       25.57 ms   (-2.83%) |      26   →      30    (+15.38%) |      684.17 ms →      767.06 ms  (+12.12%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.13 ms →      230.24 ms   (+2.27%) |      26   →      30    (+15.38%) |        5.85 s  →        6.91 s   (+18.00%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.58 ms →       22.92 ms   (-6.76%) |      26   →      30    (+15.38%) |      638.98 ms →      687.47 ms   (+7.59%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.24 ms →       80.78 ms   (-1.77%) |      26   →      30    (+15.38%) |        2.14 s  →        2.42 s   (+13.34%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.05 ms →       11.51 ms  (+27.19%) |      26   →      30    (+15.38%) |      235.30 ms →      345.33 ms  (+46.76%) | 
- │ │ ├ sirius::Density::mix                                            |      216.54 ms →      509.01 ms (+135.07%) |      26   →      30    (+15.38%) |        5.63 s  →       15.27 s  (+171.23%) | 
! │ │ │ ├ sirius::Density::mixer_input                                  |      987.90 μs →      938.45 μs   (-5.00%) |      26   →      30    (+15.38%) |       25.69 ms →       28.15 ms   (+9.61%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.45 ms →       10.24 ms   (-2.00%) |     334   →    1.31 K (+291.02%) |        3.49 s  →       13.38 s  (+283.21%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.95 ms →        9.86 ms   (-0.90%) |     334   →    1.31 K (+291.02%) |        3.32 s  →       12.88 s  (+287.51%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.95 ms →        9.86 ms   (-0.90%) |     334   →    1.31 K (+291.02%) |        3.32 s  →       12.88 s  (+287.51%) | 
! │ │ │ └ sirius::Density::mixer_output                                 |        7.21 ms →        6.83 ms   (-5.28%) |      26   →      30    (+15.38%) |      187.42 ms →      204.84 ms   (+9.29%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.38 ms →        5.78 ms   (-9.41%) |      26   →      30    (+15.38%) |      165.91 ms →      173.42 ms   (+4.52%) | 
- │ │ ├ sirius::Potential::generate                                     |      577.90 ms →      578.77 ms   (+0.15%) |      26   →      30    (+15.38%) |       15.03 s  →       17.36 s   (+15.56%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      136.33 ms →      137.17 ms   (+0.62%) |      26   →      30    (+15.38%) |        3.54 s  →        4.12 s   (+16.10%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.21 ms →        5.29 ms   (+1.43%) |      26   →      30    (+15.38%) |      135.49 ms →      158.58 ms  (+17.04%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.23 ms →       10.37 ms   (+1.39%) |      26   →      30    (+15.38%) |      265.87 ms →      311.03 ms  (+16.98%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.95 ms →       10.10 ms   (+1.50%) |      26   →      30    (+15.38%) |      258.79 ms →      303.10 ms  (+17.12%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.95 ms →       10.10 ms   (+1.50%) |      26   →      30    (+15.38%) |      258.78 ms →      303.08 ms  (+17.12%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      553.24 μs →      560.71 μs   (+1.35%) |      52   →      60    (+15.38%) |       28.77 ms →       33.64 ms  (+16.94%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       48.97 ms →       49.00 ms   (+0.05%) |      26   →      30    (+15.38%) |        1.27 s  →        1.47 s   (+15.44%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.62 ms →       46.61 ms   (-0.01%) |      26   →      30    (+15.38%) |        1.21 s  →        1.40 s   (+15.37%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        3.05 ms   (+0.59%) |      52   →      60    (+15.38%) |      157.45 ms →      182.75 ms  (+16.07%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.39 ms →        5.58 ms   (+3.62%) |      26   →      30    (+15.38%) |      140.10 ms →      167.50 ms  (+19.56%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.54 ms →        6.64 ms   (+1.57%) |      26   →      30    (+15.38%) |      170.04 ms →      199.28 ms  (+17.19%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.95 ms →       90.94 ms   (-0.02%) |      26   →      30    (+15.38%) |        2.36 s  →        2.73 s   (+15.37%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.69 ms →      292.58 ms   (-0.04%) |      26   →      30    (+15.38%) |        7.61 s  →        8.78 s   (+15.34%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      281.36 ms →      283.21 ms   (+0.66%) |      26   →      30    (+15.38%) |        7.32 s  →        8.50 s   (+16.14%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      281.36 ms →      283.21 ms   (+0.66%) |      26   →      30    (+15.38%) |        7.32 s  →        8.50 s   (+16.14%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       28.58 ms →       27.31 ms   (-4.44%) |      26   →      30    (+15.38%) |      742.96 ms →      819.24 ms  (+10.27%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.83 ms →      228.10 ms   (+1.45%) |      26   →      30    (+15.38%) |        5.85 s  →        6.84 s   (+17.06%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.16 ms →       23.97 ms   (-0.81%) |      26   →      30    (+15.38%) |      628.24 ms →      719.01 ms  (+14.45%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.62 ms →        5.91 ms  (-22.35%) |      26   →      30    (+15.38%) |      198.00 ms →      177.41 ms  (-10.40%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.76 ms →       10.62 ms   (-1.30%) |     182   →     210    (+15.38%) |        1.96 s  →        2.23 s   (+13.88%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |       10.40 ms →       10.24 ms   (-1.48%) |     182   →     210    (+15.38%) |        1.89 s  →        2.15 s   (+13.67%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.39 ms →       10.24 ms   (-1.48%) |     182   →     210    (+15.38%) |        1.89 s  →        2.15 s   (+13.67%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.52 ms →       10.47 ms   (-0.48%) |      78   →      90    (+15.38%) |      820.73 ms →      942.41 ms  (+14.83%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.80 ms →        9.73 ms   (-0.66%) |      78   →      90    (+15.38%) |      764.37 ms →      876.12 ms  (+14.62%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        9.99 ms →        9.94 ms   (-0.52%) |      26   →      30    (+15.38%) |      259.86 ms →      298.26 ms  (+14.78%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      111.35 μs →      114.64 μs   (+2.95%) |      26   →      30    (+15.38%) |        2.90 ms →        3.44 ms  (+18.79%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.65 μs →      109.60 μs   (+2.76%) |      26   →      30    (+15.38%) |        2.77 ms →        3.29 ms  (+18.57%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.07 ms →        7.11 ms   (+0.49%) |       2   →       2              |       14.15 ms →       14.22 ms   (+0.49%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.18 ms →       10.40 ms   (+2.22%) |       6   →       6              |       61.07 ms →       62.42 ms   (+2.22%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.16 ms →       10.27 ms   (+1.10%) |       6   →       6              |       60.94 ms →       61.61 ms   (+1.10%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.16 ms →       10.27 ms   (+1.10%) |       6   →       6              |       60.94 ms →       61.61 ms   (+1.10%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.14 ms →        9.75 ms   (-3.87%) |       3   →       3              |       30.42 ms →       29.24 ms   (-3.87%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.13 ms →        9.60 ms   (-5.24%) |       3   →       3              |       30.39 ms →       28.80 ms   (-5.24%) | 
  ├ sirius::Periodic_function|inner                                     |       10.11 ms →       10.43 ms   (+3.13%) |       2   →       2              |       20.22 ms →       20.86 ms   (+3.13%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.09 ms →       10.42 ms   (+3.25%) |       2   →       2              |       20.18 ms →       20.84 ms   (+3.25%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.09 ms →       10.42 ms   (+3.25%) |       2   →       2              |       20.18 ms →       20.84 ms   (+3.25%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.97 ms →        9.96 ms   (-0.17%) |       1   →       1              |        9.97 ms →        9.96 ms   (-0.17%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.97 ms →        9.95 ms   (-0.15%) |       1   →       1              |        9.97 ms →        9.95 ms   (-0.15%) | 
+ └ sirius::finalize                                                    |      234.45 ms →      183.10 ms  (-21.90%) |       1   →       1              |      234.45 ms →      183.10 ms  (-21.90%) | 
  ====================================================================================================================================================================================================
```
