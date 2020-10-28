# Benchmark 6f26e1b85d392e75fe8ae23eb64d38742c01496b vs 52d6cc62f84d89d2fdc84536db65e2617fd3b399
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      128.84 s  →      128.66 s    (-0.14%) |       1   →       1              |      128.84 s  →      128.66 s    (-0.14%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.67 s    (+0.55%) |       1   →       1              |        2.65 s  →        2.67 s    (+0.55%) | 
  ├ sirius::Simulation_context::initialize                              |        2.94 s  →        2.92 s    (-0.69%) |       1   →       1              |        2.94 s  →        2.92 s    (-0.69%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       43.10 ms →        2.66 ms  (-93.82%) |       1   →       1              |       43.10 ms →        2.66 ms  (-93.82%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       84.03 ms →      135.54 ms  (+61.30%) |       1   →       1              |       84.03 ms →      135.54 ms  (+61.30%) | 
- │ │ ├ sirius::Atom_type::init                                         |       30.72 ms →       56.68 ms  (+84.46%) |       2   →       2              |       61.45 ms →      113.35 ms  (+84.46%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.50 ms →       22.11 ms   (-1.73%) |       1   →       1              |       22.50 ms →       22.11 ms   (-1.73%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.35 ms →        6.38 ms   (+0.43%) |       1   →       1              |        6.35 ms →        6.38 ms   (+0.43%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.10 ms →       15.69 ms   (-2.57%) |       1   →       1              |       16.10 ms →       15.69 ms   (-2.57%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.08 ms →       15.67 ms   (-2.57%) |       1   →       1              |       16.08 ms →       15.67 ms   (-2.57%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.14 ms   (+0.02%) |       1   →       1              |        4.14 ms →        4.14 ms   (+0.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.33 ms   (-0.57%) |       1   →       1              |        2.34 ms →        2.33 ms   (-0.57%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.19 μs →      105.72 μs   (+0.51%) |       1   →       1              |      105.19 μs →      105.72 μs   (+0.51%) | 
  │ └ sirius::Simulation_context::update                                |        2.77 s  →        2.74 s    (-1.16%) |       1   →       1              |        2.77 s  →        2.74 s    (-1.16%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.90 ms →       10.88 ms   (-0.17%) |       1   →       1              |       10.90 ms →       10.88 ms   (-0.17%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.51 ms →        4.46 ms   (-1.17%) |       1   →       1              |        4.51 ms →        4.46 ms   (-1.17%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.39 ms   (+0.63%) |       1   →       1              |        6.35 ms →        6.39 ms   (+0.63%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.37 ms   (+0.62%) |       1   →       1              |        6.33 ms →        6.37 ms   (+0.62%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.86 ms   (+0.81%) |       1   →       1              |        3.83 ms →        3.86 ms   (+0.81%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.22%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.22%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.75 μs →      102.26 μs   (-1.44%) |       1   →       1              |      103.75 μs →      102.26 μs   (-1.44%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.75 ms →       62.45 ms   (-0.48%) |       2   →       2              |      125.50 ms →      124.90 ms   (-0.48%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.12 ms →        5.28 ms   (+3.26%) |       2   →       2              |       10.23 ms →       10.57 ms   (+3.26%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.49 ms   (+0.80%) |       1   →       1              |        4.46 ms →        4.49 ms   (+0.80%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.76 ms   (+0.01%) |       2   →       2              |       43.51 ms →       43.52 ms   (+0.01%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.81 ms   (-0.09%) |       2   →       2              |       29.65 ms →       29.62 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.76 ms →       19.84 ms   (+0.41%) |       4   →       4              |       79.03 ms →       79.35 ms   (+0.41%) | 
  │   ├ sddk::Gvec::init                                                |      182.91 ms →      176.03 ms   (-3.76%) |       2   →       2              |      365.82 ms →      352.05 ms   (-3.76%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      133.79 ms →      132.58 ms   (-0.91%) |       2   →       2              |      267.59 ms →      265.16 ms   (-0.91%) | 
+ │   ├ sddk::Gvec_shells                                               |      189.13 ms →      169.42 ms  (-10.42%) |       1   →       1              |      189.13 ms →      169.42 ms  (-10.42%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (-0.03%) |       1   →       1              |        1.32 ms →        1.32 ms   (-0.03%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.83 ms →      294.23 ms   (+0.82%) |       2   →       2              |      583.66 ms →      588.45 ms   (+0.82%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.32 ms →       35.52 ms   (+0.55%) |       1   →       1              |       35.32 ms →       35.52 ms   (+0.55%) | 
+ │ ├ sirius::K_point::K_point                                          |        4.07 μs →        2.56 μs  (-37.16%) |       4   →       4              |       16.28 μs →       10.23 μs  (-37.16%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.22 ms →       35.40 ms   (+0.52%) |       1   →       1              |       35.22 ms →       35.40 ms   (+0.52%) | 
  │   └ sirius::K_point::initialize                                     |       35.12 ms →       35.30 ms   (+0.53%) |       1   →       1              |       35.12 ms →       35.30 ms   (+0.53%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.87 ms →       18.01 ms   (+0.81%) |       1   →       1              |       17.87 ms →       18.01 ms   (+0.81%) | 
  │     │ └ sddk::Gvec::init                                            |        8.03 ms →        8.19 ms   (+2.09%) |       1   →       1              |        8.03 ms →        8.19 ms   (+2.09%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.87 μs →       10.45 μs   (+5.79%) |       1   →       1              |        9.87 μs →       10.45 μs   (+5.79%) | 
  │     └ sirius::K_point::update                                       |       12.47 ms →       12.46 ms   (-0.07%) |       1   →       1              |       12.47 ms →       12.46 ms   (-0.07%) | 
  │       └ sirius::Beta_projectors                                     |        6.06 ms →        6.14 ms   (+1.35%) |       1   →       1              |        6.06 ms →        6.14 ms   (+1.35%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.51 ms →        3.51 ms   (-0.12%) |       1   →       1              |        3.51 ms →        3.51 ms   (-0.12%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.25 ms →        5.53 ms   (+5.23%) |       2   →       2              |       10.50 ms →       11.05 ms   (+5.23%) | 
  ├ sirius::Potential                                                   |      154.95 ms →      160.11 ms   (+3.33%) |       1   →       1              |      154.95 ms →      160.11 ms   (+3.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        6.05 ms   (+4.57%) |       6   →       6              |       34.72 ms →       36.30 ms   (+4.57%) | 
  │ └ sirius::Potential::update                                         |      119.49 ms →      123.03 ms   (+2.96%) |       1   →       1              |      119.49 ms →      123.03 ms   (+2.96%) | 
  │   └ sirius::Potential::generate_local_potential                     |      118.75 ms →      122.27 ms   (+2.96%) |       1   →       1              |      118.75 ms →      122.27 ms   (+2.96%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      107.95 ms →      114.90 ms   (+6.43%) |       1   →       1              |      107.95 ms →      114.90 ms   (+6.43%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.93 ms →        6.45 ms  (-34.99%) |       1   →       1              |        9.93 ms →        6.45 ms  (-34.99%) | 
  ├ sirius::Density                                                     |      129.21 ms →      133.90 ms   (+3.63%) |       1   →       1              |      129.21 ms →      133.90 ms   (+3.63%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.14 ms →        5.27 ms   (+2.43%) |       2   →       2              |       10.29 ms →       10.54 ms   (+2.43%) | 
  │ └ sirius::Density::update                                           |      118.66 ms →      123.09 ms   (+3.74%) |       1   →       1              |      118.66 ms →      123.09 ms   (+3.74%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      118.23 ms →      122.65 ms   (+3.74%) |       1   →       1              |      118.23 ms →      122.65 ms   (+3.74%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      104.22 μs →      106.41 μs   (+2.10%) |       1   →       1              |      104.22 μs →      106.41 μs   (+2.10%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.17 ms →      116.97 ms   (+6.17%) |       1   →       1              |      110.17 ms →      116.97 ms   (+6.17%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.50 ms →        5.11 ms  (-31.81%) |       1   →       1              |        7.50 ms →        5.11 ms  (-31.81%) | 
  ├ sirius::Density::initial_density                                    |      162.76 ms →      174.04 ms   (+6.93%) |       1   →       1              |      162.76 ms →      174.04 ms   (+6.93%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      109.88 ms →      121.51 ms  (+10.58%) |       1   →       1              |      109.88 ms →      121.51 ms  (+10.58%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.16 ms →        5.04 ms   (-2.27%) |       2   →       2              |       10.32 ms →       10.09 ms   (-2.27%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.07 ms →        9.80 ms   (-2.63%) |       1   →       1              |       10.07 ms →        9.80 ms   (-2.63%) | 
  ├ sirius::Potential::generate                                         |      580.95 ms →      594.50 ms   (+2.33%) |       1   →       1              |      580.95 ms →      594.50 ms   (+2.33%) | 
  │ ├ sirius::Potential::poisson                                        |      126.82 ms →      137.66 ms   (+8.55%) |       1   →       1              |      126.82 ms →      137.66 ms   (+8.55%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.86 ms →        5.43 ms   (-7.31%) |       1   →       1              |        5.86 ms →        5.43 ms   (-7.31%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       11.31 ms →       11.38 ms   (+0.61%) |       1   →       1              |       11.31 ms →       11.38 ms   (+0.61%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.32 ms →       11.01 ms   (+6.70%) |       1   →       1              |       10.32 ms →       11.01 ms   (+6.70%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.31 ms →       11.00 ms   (+6.70%) |       1   →       1              |       10.31 ms →       11.00 ms   (+6.70%) | 
  │ ├ sirius::Periodic_function::add                                    |      548.16 μs →      550.87 μs   (+0.49%) |       2   →       2              |        1.10 ms →        1.10 ms   (+0.49%) | 
  │ ├ sirius::Potential::xc                                             |       53.56 ms →       55.92 ms   (+4.41%) |       1   →       1              |       53.56 ms →       55.92 ms   (+4.41%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.20 ms →       53.60 ms   (+4.68%) |       1   →       1              |       51.20 ms →       53.60 ms   (+4.68%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.67 ms →        5.76 ms   (+1.59%) |       2   →       2              |       11.34 ms →       11.52 ms   (+1.59%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.34 ms →        5.79 ms   (+8.27%) |       1   →       1              |        5.34 ms →        5.79 ms   (+8.27%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.85 ms →        5.77 ms   (-1.39%) |       1   →       1              |        5.85 ms →        5.77 ms   (-1.39%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.65 ms →       92.66 ms   (+0.00%) |       1   →       1              |       92.65 ms →       92.66 ms   (+0.00%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.61 ms →      300.01 ms   (+0.14%) |       1   →       1              |      299.61 ms →      300.01 ms   (+0.14%) | 
  ├ sirius::Hamiltonian0                                                |        8.40 ms →        8.40 ms   (+0.00%) |       1   →       1              |        8.40 ms →        8.40 ms   (+0.00%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        8.03 ms   (+0.23%) |       1   →       1              |        8.02 ms →        8.03 ms   (+0.23%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms →        4.72 ms   (-0.82%) |       1   →       1              |        4.76 ms →        4.72 ms   (-0.82%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        2.39 ms   (+2.24%) |       1   →       1              |        2.33 ms →        2.39 ms   (+2.24%) | 
  │ ├ sirius::Non_local_operator                                        |       63.48 μs →       62.85 μs   (-0.99%) |       2   →       2              |      126.96 μs →      125.71 μs   (-0.99%) | 
+ │ ├ sirius::D_operator::initialize                                    |      114.23 μs →       95.72 μs  (-16.20%) |       1   →       1              |      114.23 μs →       95.72 μs  (-16.20%) | 
  │ └ sirius::Q_operator::initialize                                    |       77.20 μs →       73.82 μs   (-4.38%) |       1   →       1              |       77.20 μs →       73.82 μs   (-4.38%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.86 s    (-0.08%) |       1   →       1              |        1.86 s  →        1.86 s    (-0.08%) | 
  │ ├ sirius::Hamiltonian_k                                             |       19.22 ms →       19.65 ms   (+2.24%) |       1   →       1              |       19.22 ms →       19.65 ms   (+2.24%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      191.01 μs →      175.23 μs   (-8.26%) |       1   →       1              |      191.01 μs →      175.23 μs   (-8.26%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       19.03 ms →       19.48 ms   (+2.35%) |       1   →       1              |       19.03 ms →       19.48 ms   (+2.35%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.84 s    (-0.11%) |       1   →       1              |        1.84 s  →        1.84 s    (-0.11%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      127.22 ms →      128.90 ms   (+1.32%) |       4   →       4              |      508.87 ms →      515.60 ms   (+1.32%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.53 ms →       52.54 ms   (+0.03%) |       1   →       1              |       52.53 ms →       52.54 ms   (+0.03%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.12 ms →       21.02 ms   (-0.47%) |       1   →       1              |       21.12 ms →       21.02 ms   (-0.47%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      640.52 ms →      636.34 ms   (-0.65%) |       1   →       1              |      640.52 ms →      636.34 ms   (-0.65%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      301.44 ms →      297.39 ms   (-1.34%) |       1   →       1              |      301.44 ms →      297.39 ms   (-1.34%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.27 μs →        3.04 μs   (-6.98%) |       1   →       1              |        3.27 μs →        3.04 μs   (-6.98%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.36 μs →        2.06 μs  (-12.58%) |       1   →       1              |        2.36 μs →        2.06 μs  (-12.58%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      361.00 ns →      358.00 ns   (-0.83%) |       1   →       1              |      361.00 ns →      358.00 ns   (-0.83%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      590.00 ns →      483.00 ns  (-18.14%) |       1   →       1              |      590.00 ns →      483.00 ns  (-18.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.24 ms   (+0.15%) |       1   →       1              |        9.22 ms →        9.24 ms   (+0.15%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.85 ms →      121.01 ms   (-0.69%) |       1   →       1              |      121.85 ms →      121.01 ms   (-0.69%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.98 ms →      104.34 ms   (+0.34%) |       2   →       2              |      207.97 ms →      208.67 ms   (+0.34%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.23 ms →       40.30 ms   (+0.19%) |       2   →       2              |       80.46 ms →       80.60 ms   (+0.19%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.68 ms →       39.71 ms   (+0.07%) |       2   →       2              |       79.35 ms →       79.41 ms   (+0.07%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       37.50 ns →       62.00 ns  (+65.33%) |       2   →       2              |       75.00 ns →      124.00 ns  (+65.33%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.22 ms →       39.23 ms   (+0.02%) |       2   →       2              |       78.44 ms →       78.46 ms   (+0.02%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       29.00 ns →       21.00 ns  (-27.59%) |       2   →       2              |       58.00 ns →       42.00 ns  (-27.59%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       62.27 ms →       56.83 ms   (-8.73%) |       1   →       1              |       62.27 ms →       56.83 ms   (-8.73%) | 
  │ │ └ sddk::wf_trans                                                  |       30.76 ms →       30.76 ms   (+0.02%) |       1   →       1              |       30.76 ms →       30.76 ms   (+0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.76 ms →       30.76 ms   (+0.02%) |       1   →       1              |       30.76 ms →       30.76 ms   (+0.02%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      502.00 ns →      394.00 ns  (-21.51%) |       1   →       1              |      502.00 ns →      394.00 ns  (-21.51%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.32 s  →      119.10 s    (-0.18%) |       1   →       1              |      119.32 s  →      119.10 s    (-0.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.75 ms →        5.80 ms   (+0.99%) |      19   →      19              |      109.18 ms →      110.26 ms   (+0.99%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.57 s  →        4.57 s    (-0.17%) |      26   →      26              |      118.93 s  →      118.72 s    (-0.17%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.26 ms →        4.77 ms   (-9.32%) |      26   →      26              |      136.63 ms →      123.89 ms   (-9.32%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.89 ms →        4.39 ms  (-10.15%) |      26   →      26              |      127.16 ms →      114.25 ms  (-10.15%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      998.07 μs →      963.65 μs   (-3.45%) |      26   →      26              |       25.95 ms →       25.05 ms   (-3.45%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.00 ms →        2.53 ms  (-15.62%) |      26   →      26              |       77.93 ms →       65.76 ms  (-15.62%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       63.44 μs →       64.10 μs   (+1.04%) |      52   →      52              |        3.30 ms →        3.33 ms   (+1.04%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.45 μs →       89.15 μs   (+3.13%) |      26   →      26              |        2.25 ms →        2.32 ms   (+3.13%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.13 μs →       79.76 μs   (+3.41%) |      26   →      26              |        2.01 ms →        2.07 ms   (+3.41%) | 
  │ │ ├ sirius::Band::solve                                             |        2.61 s  →        2.60 s    (-0.29%) |      26   →      26              |       67.86 s  →       67.66 s    (-0.29%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      157.40 μs →      156.75 μs   (-0.41%) |      26   →      26              |        4.09 ms →        4.08 ms   (-0.41%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      149.85 μs →      148.42 μs   (-0.95%) |      26   →      26              |        3.90 ms →        3.86 ms   (-0.95%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.57 μs →        6.41 μs  (+15.02%) |      26   →      26              |      144.83 μs →      166.58 μs  (+15.02%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.48 s  →        2.48 s    (+0.13%) |      26   →      26              |       64.39 s  →       64.47 s    (+0.13%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.66 ms →       97.04 ms   (+1.44%) |      26   →      26              |        2.49 s  →        2.52 s    (+1.44%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.62 ms →        7.74 ms   (+1.56%) |     156   →     156              |        1.19 s  →        1.21 s    (+1.56%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.89 ms →        5.90 ms   (+0.13%) |      26   →      26              |      153.25 ms →      153.45 ms   (+0.13%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.54 μs →      347.81 μs   (-1.06%) |      26   →      26              |        9.14 ms →        9.04 ms   (-1.06%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.28 ms →        2.30 ms   (+0.94%) |      52   →      52              |      118.68 ms →      119.80 ms   (+0.94%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.34 s  →        2.34 s    (+0.08%) |      26   →      26              |       60.82 s  →       60.87 s    (+0.08%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      137.51 ms →      137.01 ms   (-0.36%) |     262   →     262              |       36.03 s  →       35.90 s    (-0.36%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.63 ms →       55.97 ms   (+0.62%) |     262   →     262              |       14.58 s  →       14.66 s    (+0.62%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.15 μs →        2.22 μs   (+3.26%) |     262   →     262              |      563.07 μs →      581.43 μs   (+3.26%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.77 μs →        1.85 μs   (+4.54%) |     262   →     262              |      464.63 μs →      485.71 μs   (+4.54%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      396.67 ns →      457.80 ns  (+15.41%) |     262   →     262              |      103.93 μs →      119.94 μs  (+15.41%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      496.83 ns →      544.28 ns   (+9.55%) |     262   →     262              |      130.17 μs →      142.60 μs   (+9.55%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.46 ms →        7.46 ms   (+0.01%) |     262   →     262              |        1.95 s  →        1.95 s    (+0.01%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       25.44 ms →       24.62 ms   (-3.21%) |     262   →     262              |        6.67 s  →        6.45 s    (-3.21%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.48 ms →       24.47 ms   (-0.05%) |     524   →     524              |       12.83 s  →       12.82 s    (-0.05%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.89 ms →       35.86 ms   (-0.09%) |     262   →     262              |        9.40 s  →        9.39 s    (-0.09%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        6.22 ms   (-0.18%) |     498   →     498              |        3.10 s  →        3.10 s    (-0.18%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       49.84 ns →       59.79 ns  (+19.97%) |     498   →     498              |       24.82 μs →       29.78 μs  (+19.97%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.12 ms →        5.11 ms   (-0.14%) |     498   →     498              |        2.55 s  →        2.54 s    (-0.14%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       27.23 ns →       31.35 ns  (+15.12%) |     498   →     498              |       13.56 μs →       15.61 μs  (+15.12%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      659.03 μs →      652.60 μs   (-0.98%) |     262   →     262              |      172.67 ms →      170.98 ms   (-0.98%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.31 ms →       10.32 ms   (+0.05%) |     262   →     262              |        2.70 s  →        2.70 s    (+0.05%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.51 ms →       14.50 ms   (-0.07%) |     236   →     236              |        3.42 s  →        3.42 s    (-0.07%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        4.83 ms   (-0.07%) |     708   →     708              |        3.42 s  →        3.42 s    (-0.07%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.38 ms →       10.39 ms   (+0.06%) |     262   →     262              |        2.72 s  →        2.72 s    (+0.06%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       10.19 ms   (+0.04%) |     262   →     262              |        2.67 s  →        2.67 s    (+0.04%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       22.38 ns →       41.08 ns  (+83.57%) |     262   →     262              |        5.86 μs →       10.76 μs  (+83.57%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.07 ms →        9.08 ms   (+0.08%) |     262   →     262              |        2.38 s  →        2.38 s    (+0.08%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       47.56 ns →       50.61 ns   (+6.40%) |     262   →     262              |       12.46 μs →       13.26 μs   (+6.40%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.25 ms →       18.94 ms   (+3.80%) |     262   →     262              |        4.78 s  →        4.96 s    (+3.80%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.14 ms →       13.15 ms   (+0.10%) |     252   →     252              |        3.31 s  →        3.31 s    (+0.10%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.70 ms →       11.72 ms   (+0.14%) |     242   →     242              |        2.83 s  →        2.84 s    (+0.14%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.85 ms →        5.86 ms   (+0.14%) |     484   →     484              |        2.83 s  →        2.83 s    (+0.14%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.72 ms →        1.72 ms   (-0.24%) |     242   →     242              |      417.07 ms →      416.08 ms   (-0.24%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.74 ms →       53.74 ms   (-0.00%) |      85   →      85              |        4.57 s  →        4.57 s    (-0.00%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.45 ms →       31.45 ms   (-0.01%) |     144   →     144              |        4.53 s  →        4.53 s    (-0.01%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.31 ms →       22.31 ms   (-0.02%) |     203   →     203              |        4.53 s  →        4.53 s    (-0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      452.12 ns →      442.19 ns   (-2.19%) |      26   →      26              |       11.76 μs →       11.50 μs   (-2.19%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.52 μs →       30.44 μs   (+3.11%) |      26   →      26              |      767.52 μs →      791.42 μs   (+3.11%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      608.20 μs →      610.15 μs   (+0.32%) |      26   →      26              |       15.81 ms →       15.86 ms   (+0.32%) | 
  │ │ ├ sirius::Density::generate                                       |      772.79 ms →      773.63 ms   (+0.11%) |      26   →      26              |       20.09 s  →       20.11 s    (+0.11%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.13 ms →      403.03 ms   (+0.22%) |      26   →      26              |       10.46 s  →       10.48 s    (+0.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.59 μs →        3.59 μs   (-0.01%) |      26   →      26              |       93.44 μs →       93.43 μs   (-0.01%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.30 μs →        3.32 μs   (+0.61%) |      26   →      26              |       85.80 μs →       86.32 μs   (+0.61%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.56 ms →      100.20 ms   (-0.36%) |      26   →      26              |        2.61 s  →        2.61 s    (-0.36%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.78 μs →       11.21 μs   (+3.97%) |      26   →      26              |      280.23 μs →      291.37 μs   (+3.97%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (+0.01%) |      26   →      26              |      185.34 ms →      185.35 ms   (+0.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.51 ms →       91.15 ms   (-0.40%) |      26   →      26              |        2.38 s  →        2.37 s    (-0.40%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      528.35 ns →      559.58 ns   (+5.91%) |      26   →      26              |       13.74 μs →       14.55 μs   (+5.91%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.63 ms →      165.48 ms   (+1.13%) |      26   →      26              |        4.25 s  →        4.30 s    (+1.13%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.49%) |      26   →      26              |       42.68 ms →       42.89 ms   (+0.49%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.24 ms →       88.20 ms   (-0.05%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.05%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.02 ms →       87.97 ms   (-0.05%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.05%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.60 ms →      271.22 ms   (-2.65%) |      26   →      26              |        7.24 s  →        7.05 s    (-2.65%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.60 ms →      271.22 ms   (-2.65%) |      26   →      26              |        7.24 s  →        7.05 s    (-2.65%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.14 ms →       24.22 ms  (-16.86%) |      26   →      26              |      757.56 ms →      629.82 ms  (-16.86%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      219.12 ms →      222.81 ms   (+1.68%) |      26   →      26              |        5.70 s  →        5.79 s    (+1.68%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       29.15 ms →       22.99 ms  (-21.13%) |      26   →      26              |      757.93 ms →      597.74 ms  (-21.13%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.71 ms →       81.90 ms   (+0.24%) |      26   →      26              |        2.12 s  →        2.13 s    (+0.24%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.76 ms →       13.85 ms (+104.92%) |      26   →      26              |      175.70 ms →      360.04 ms (+104.92%) | 
  │ │ ├ sirius::Density::mix                                            |      213.61 ms →      210.10 ms   (-1.64%) |      26   →      26              |        5.55 s  →        5.46 s    (-1.64%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      917.20 μs →      973.13 μs   (+6.10%) |      26   →      26              |       23.85 ms →       25.30 ms   (+6.10%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.29 ms →       10.72 ms   (+4.09%) |     334   →     320     (-4.19%) |        3.44 s  →        3.43 s    (-0.27%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.93 ms →       10.35 ms   (+4.16%) |     334   →     320     (-4.19%) |        3.32 s  →        3.31 s    (-0.20%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.93 ms →       10.35 ms   (+4.16%) |     334   →     320     (-4.19%) |        3.32 s  →        3.31 s    (-0.20%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.10 ms →        6.34 ms   (+3.90%) |      26   →      26              |      158.67 ms →      164.85 ms   (+3.90%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.25 ms →        5.52 ms   (+5.15%) |      26   →      26              |      136.50 ms →      143.53 ms   (+5.15%) | 
  │ │ ├ sirius::Potential::generate                                     |      568.09 ms →      579.69 ms   (+2.04%) |      26   →      26              |       14.77 s  →       15.07 s    (+2.04%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.20 ms →      136.99 ms   (+8.55%) |      26   →      26              |        3.28 s  →        3.56 s    (+8.55%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.37 ms →        5.27 ms   (-1.87%) |      26   →      26              |      139.69 ms →      137.08 ms   (-1.87%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.78 ms →       10.69 ms   (-0.92%) |      26   →      26              |      280.40 ms →      277.83 ms   (-0.92%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.34 ms →       10.37 ms   (+0.30%) |      26   →      26              |      268.72 ms →      269.53 ms   (+0.30%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.33 ms →       10.37 ms   (+0.30%) |      26   →      26              |      268.71 ms →      269.52 ms   (+0.30%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      551.03 μs →      553.39 μs   (+0.43%) |      52   →      52              |       28.65 ms →       28.78 ms   (+0.43%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.49 ms →       49.75 ms   (+0.51%) |      26   →      26              |        1.29 s  →        1.29 s    (+0.51%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.10 ms →       47.40 ms   (+0.64%) |      26   →      26              |        1.22 s  →        1.23 s    (+0.64%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.01 ms   (-1.70%) |      52   →      52              |      159.00 ms →      156.30 ms   (-1.70%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.38 ms →        5.36 ms   (-0.41%) |      26   →      26              |      139.93 ms →      139.36 ms   (-0.41%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.60 ms →        6.62 ms   (+0.30%) |      26   →      26              |      171.61 ms →      172.13 ms   (+0.30%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.87 ms →       90.95 ms   (+0.10%) |      26   →      26              |        2.36 s  →        2.36 s    (+0.10%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.52 ms →      292.97 ms   (+0.15%) |      26   →      26              |        7.61 s  →        7.62 s    (+0.15%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      283.62 ms →      275.37 ms   (-2.91%) |      26   →      26              |        7.37 s  →        7.16 s    (-2.91%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      283.62 ms →      275.37 ms   (-2.91%) |      26   →      26              |        7.37 s  →        7.16 s    (-2.91%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.47 ms →       27.31 ms  (-15.87%) |      26   →      26              |      844.15 ms →      710.15 ms  (-15.87%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      216.88 ms →      220.60 ms   (+1.72%) |      26   →      26              |        5.64 s  →        5.74 s    (+1.72%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       30.47 ms →       23.65 ms  (-22.40%) |      26   →      26              |      792.23 ms →      614.78 ms  (-22.40%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.23 ms →        5.69 ms   (+8.76%) |      26   →      26              |      136.07 ms →      148.00 ms   (+8.76%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.64 ms →       10.30 ms   (-3.16%) |     182   →     182              |        1.94 s  →        1.87 s    (-3.16%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.21 ms →        9.78 ms   (-4.25%) |     182   →     182              |        1.86 s  →        1.78 s    (-4.25%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.21 ms →        9.78 ms   (-4.24%) |     182   →     182              |        1.86 s  →        1.78 s    (-4.24%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.12 ms →       10.59 ms   (+4.63%) |      78   →      78              |      789.68 ms →      826.23 ms   (+4.63%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.74 ms →       10.18 ms   (+4.56%) |      78   →      78              |      759.39 ms →      794.02 ms   (+4.56%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.96 ms →        9.93 ms   (-0.32%) |      26   →      26              |      259.04 ms →      258.20 ms   (-0.32%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      110.48 μs →      112.31 μs   (+1.66%) |      26   →      26              |        2.87 ms →        2.92 ms   (+1.66%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      105.42 μs →      107.16 μs   (+1.65%) |      26   →      26              |        2.74 ms →        2.79 ms   (+1.65%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.13 ms →        5.15 ms   (+0.50%) |       2   →       2              |       10.26 ms →       10.31 ms   (+0.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.21 ms →       10.16 ms   (-0.41%) |       6   →       6              |       61.24 ms →       60.99 ms   (-0.41%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.06 ms →        9.80 ms   (-2.53%) |       6   →       6              |       60.35 ms →       58.82 ms   (-2.53%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.06 ms →        9.80 ms   (-2.53%) |       6   →       6              |       60.35 ms →       58.82 ms   (-2.53%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.89 ms →       10.82 ms   (+9.48%) |       3   →       3              |       29.66 ms →       32.47 ms   (+9.48%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.63 ms →       10.11 ms   (+4.99%) |       3   →       3              |       28.90 ms →       30.34 ms   (+4.99%) | 
  ├ sirius::Periodic_function|inner                                     |       10.56 ms →       10.16 ms   (-3.77%) |       2   →       2              |       21.11 ms →       20.32 ms   (-3.77%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.25 ms →        9.98 ms   (-2.64%) |       2   →       2              |       20.49 ms →       19.95 ms   (-2.64%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.25 ms →        9.98 ms   (-2.64%) |       2   →       2              |       20.49 ms →       19.95 ms   (-2.64%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.69 ms →       10.52 ms   (+8.59%) |       1   →       1              |        9.69 ms →       10.52 ms   (+8.59%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.68 ms →       10.51 ms   (+8.59%) |       1   →       1              |        9.68 ms →       10.51 ms   (+8.59%) | 
- └ sirius::finalize                                                    |      165.41 ms →      194.13 ms  (+17.37%) |       1   →       1              |      165.41 ms →      194.13 ms  (+17.37%) | 
  ====================================================================================================================================================================================================
```
