# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs d58be0235bf025c49e07930fbe8483989a6b739c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      129.20 s  →      131.41 s    (+1.71%) |       1   →       1              |      129.20 s  →      131.41 s    (+1.71%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.74 s    (+2.04%) |       1   →       1              |        2.69 s  →        2.74 s    (+2.04%) | 
  ├ sirius::Simulation_context::initialize                              |        2.94 s  →        2.98 s    (+1.21%) |       1   →       1              |        2.94 s  →        2.98 s    (+1.21%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       97.93 ms →      218.18 μs  (-99.78%) |       1   →       1              |       97.93 ms →      218.18 μs  (-99.78%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      127.54 ms →      136.32 ms   (+6.88%) |       1   →       1              |      127.54 ms →      136.32 ms   (+6.88%) | 
  │ │ ├ sirius::Atom_type::init                                         |       52.40 ms →       56.53 ms   (+7.88%) |       2   →       2              |      104.81 ms →      113.07 ms   (+7.88%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.66 ms →       23.18 ms   (+2.27%) |       1   →       1              |       22.66 ms →       23.18 ms   (+2.27%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.40 ms →        6.08 ms   (-4.99%) |       1   →       1              |        6.40 ms →        6.08 ms   (-4.99%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.22 ms →       17.06 ms   (+5.14%) |       1   →       1              |       16.22 ms →       17.06 ms   (+5.14%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.20 ms →       17.04 ms   (+5.15%) |       1   →       1              |       16.20 ms →       17.04 ms   (+5.15%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.14 ms   (-0.48%) |       1   →       1              |        4.16 ms →        4.14 ms   (-0.48%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.20%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.20%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.83 μs →      102.40 μs   (-3.24%) |       1   →       1              |      105.83 μs →      102.40 μs   (-3.24%) | 
  │ └ sirius::Simulation_context::update                                |        2.67 s  →        2.79 s    (+4.60%) |       1   →       1              |        2.67 s  →        2.79 s    (+4.60%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.82 ms →       10.88 ms   (+0.62%) |       1   →       1              |       10.82 ms →       10.88 ms   (+0.62%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.46 ms   (+0.48%) |       1   →       1              |        4.44 ms →        4.46 ms   (+0.48%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.38 ms   (+0.71%) |       1   →       1              |        6.34 ms →        6.38 ms   (+0.71%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.36 ms   (+0.68%) |       1   →       1              |        6.32 ms →        6.36 ms   (+0.68%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.88 ms   (+1.42%) |       1   →       1              |        3.83 ms →        3.88 ms   (+1.42%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.31 ms   (-0.42%) |       1   →       1              |        2.32 ms →        2.31 ms   (-0.42%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      101.28 μs →       99.19 μs   (-2.07%) |       1   →       1              |      101.28 μs →       99.19 μs   (-2.07%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       64.57 ms →      101.04 ms  (+56.47%) |       2   →       2              |      129.15 ms →      202.08 ms  (+56.47%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.26 ms →        5.17 ms   (-1.76%) |       2   →       2              |       10.52 ms →       10.33 ms   (-1.76%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.47 ms   (-0.17%) |       1   →       1              |        4.48 ms →        4.47 ms   (-0.17%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.87 ms →       21.79 ms   (-0.36%) |       2   →       2              |       43.74 ms →       43.59 ms   (-0.36%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.02 ms →       14.87 ms   (-0.98%) |       2   →       2              |       30.04 ms →       29.75 ms   (-0.98%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.87 ms →       19.57 ms   (-1.51%) |       4   →       4              |       79.47 ms →       78.27 ms   (-1.51%) | 
  │   ├ sddk::Gvec::init                                                |      173.24 ms →      174.95 ms   (+0.99%) |       2   →       2              |      346.47 ms →      349.91 ms   (+0.99%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.40 ms →      132.51 ms   (+1.62%) |       2   →       2              |      260.80 ms →      265.01 ms   (+1.62%) | 
  │   ├ sddk::Gvec_shells                                               |      179.01 ms →      187.80 ms   (+4.91%) |       1   →       1              |      179.01 ms →      187.80 ms   (+4.91%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (-0.50%) |       1   →       1              |        1.32 ms →        1.32 ms   (-0.50%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      290.81 ms →      294.61 ms   (+1.31%) |       2   →       2              |      581.61 ms →      589.22 ms   (+1.31%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.43 ms →       36.33 ms   (+2.55%) |       1   →       1              |       35.43 ms →       36.33 ms   (+2.55%) | 
  │ ├ sirius::K_point::K_point                                          |        2.45 μs →        2.64 μs   (+7.66%) |       4   →       4              |        9.81 μs →       10.56 μs   (+7.66%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.31 ms →       36.22 ms   (+2.56%) |       1   →       1              |       35.31 ms →       36.22 ms   (+2.56%) | 
  │   └ sirius::K_point::initialize                                     |       35.21 ms →       36.12 ms   (+2.57%) |       1   →       1              |       35.21 ms →       36.12 ms   (+2.57%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.96 ms →       18.30 ms   (+1.91%) |       1   →       1              |       17.96 ms →       18.30 ms   (+1.91%) | 
  │     │ └ sddk::Gvec::init                                            |        8.08 ms →        8.11 ms   (+0.47%) |       1   →       1              |        8.08 ms →        8.11 ms   (+0.47%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        9.13 μs →       10.30 μs  (+12.84%) |       1   →       1              |        9.13 μs →       10.30 μs  (+12.84%) | 
  │     └ sirius::K_point::update                                       |       12.46 ms →       12.52 ms   (+0.55%) |       1   →       1              |       12.46 ms →       12.52 ms   (+0.55%) | 
  │       └ sirius::Beta_projectors                                     |        6.13 ms →        6.04 ms   (-1.48%) |       1   →       1              |        6.13 ms →        6.04 ms   (-1.48%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.53 ms →        3.45 ms   (-2.27%) |       1   →       1              |        3.53 ms →        3.45 ms   (-2.27%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.50 ms →        5.40 ms   (-1.78%) |       2   →       2              |       10.99 ms →       10.80 ms   (-1.78%) | 
  ├ sirius::Potential                                                   |      158.82 ms →      151.93 ms   (-4.34%) |       1   →       1              |      158.82 ms →      151.93 ms   (-4.34%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.11 ms →        5.74 ms   (-6.11%) |       6   →       6              |       36.66 ms →       34.42 ms   (-6.11%) | 
  │ └ sirius::Potential::update                                         |      121.42 ms →      116.78 ms   (-3.82%) |       1   →       1              |      121.42 ms →      116.78 ms   (-3.82%) | 
  │   └ sirius::Potential::generate_local_potential                     |      120.61 ms →      116.03 ms   (-3.80%) |       1   →       1              |      120.61 ms →      116.03 ms   (-3.80%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.87 ms →      107.45 ms   (+0.55%) |       1   →       1              |      106.87 ms →      107.45 ms   (+0.55%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.85 ms →        7.67 ms  (-40.26%) |       1   →       1              |       12.85 ms →        7.67 ms  (-40.26%) | 
  ├ sirius::Density                                                     |      135.30 ms →      128.31 ms   (-5.16%) |       1   →       1              |      135.30 ms →      128.31 ms   (-5.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.11 ms →        5.19 ms   (+1.51%) |       2   →       2              |       10.22 ms →       10.37 ms   (+1.51%) | 
  │ └ sirius::Density::update                                           |      124.77 ms →      117.67 ms   (-5.69%) |       1   →       1              |      124.77 ms →      117.67 ms   (-5.69%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.31 ms →      117.24 ms   (-5.69%) |       1   →       1              |      124.31 ms →      117.24 ms   (-5.69%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.88 μs →      114.52 μs   (+8.16%) |       1   →       1              |      105.88 μs →      114.52 μs   (+8.16%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.97 ms →      109.93 ms   (+0.88%) |       1   →       1              |      108.97 ms →      109.93 ms   (+0.88%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       14.78 ms →        6.75 ms  (-54.36%) |       1   →       1              |       14.78 ms →        6.75 ms  (-54.36%) | 
  ├ sirius::Density::initial_density                                    |      179.15 ms →      164.53 ms   (-8.16%) |       1   →       1              |      179.15 ms →      164.53 ms   (-8.16%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.84 ms →      110.09 ms   (+1.14%) |       1   →       1              |      108.84 ms →      110.09 ms   (+1.14%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       13.29 ms →        5.38 ms  (-59.50%) |       2   →       2              |       26.58 ms →       10.77 ms  (-59.50%) | 
  │ └ sirius::Periodic_function::integrate                              |       11.57 ms →       11.14 ms   (-3.72%) |       1   →       1              |       11.57 ms →       11.14 ms   (-3.72%) | 
  ├ sirius::Potential::generate                                         |      595.37 ms →      580.04 ms   (-2.57%) |       1   →       1              |      595.37 ms →      580.04 ms   (-2.57%) | 
  │ ├ sirius::Potential::poisson                                        |      137.44 ms →      125.68 ms   (-8.56%) |       1   →       1              |      137.44 ms →      125.68 ms   (-8.56%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.47 ms →        6.60 ms  (-66.12%) |       1   →       1              |       19.47 ms →        6.60 ms  (-66.12%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.37 ms →       10.95 ms   (+5.62%) |       1   →       1              |       10.37 ms →       10.95 ms   (+5.62%) | 
- │ │   └ sirius::Periodic_function|inner_local                         |        9.90 ms →       10.93 ms  (+10.37%) |       1   →       1              |        9.90 ms →       10.93 ms  (+10.37%) | 
- │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.90 ms →       10.92 ms  (+10.38%) |       1   →       1              |        9.90 ms →       10.92 ms  (+10.38%) | 
  │ ├ sirius::Periodic_function::add                                    |      547.48 μs →      546.80 μs   (-0.12%) |       2   →       2              |        1.09 ms →        1.09 ms   (-0.12%) | 
  │ ├ sirius::Potential::xc                                             |       55.73 ms →       54.55 ms   (-2.13%) |       1   →       1              |       55.73 ms →       54.55 ms   (-2.13%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.34 ms →       52.23 ms   (-2.08%) |       1   →       1              |       53.34 ms →       52.23 ms   (-2.08%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        6.24 ms →        5.70 ms   (-8.74%) |       2   →       2              |       12.49 ms →       11.40 ms   (-8.74%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.19 ms →        5.19 ms   (-0.07%) |       1   →       1              |        5.19 ms →        5.19 ms   (-0.07%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.97 ms →        5.64 ms   (-5.57%) |       1   →       1              |        5.97 ms →        5.64 ms   (-5.57%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       94.57 ms →       92.72 ms   (-1.95%) |       1   →       1              |       94.57 ms →       92.72 ms   (-1.95%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.17 ms →      299.00 ms   (-0.06%) |       1   →       1              |      299.17 ms →      299.00 ms   (-0.06%) | 
  ├ sirius::Hamiltonian0                                                |        8.96 ms →        8.38 ms   (-6.41%) |       1   →       1              |        8.96 ms →        8.38 ms   (-6.41%) | 
  │ ├ sirius::Local_operator                                            |        8.60 ms →        8.03 ms   (-6.72%) |       1   →       1              |        8.60 ms →        8.03 ms   (-6.72%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        5.06 ms →        4.74 ms   (-6.35%) |       1   →       1              |        5.06 ms →        4.74 ms   (-6.35%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.64 ms →        2.37 ms  (-10.23%) |       1   →       1              |        2.64 ms →        2.37 ms  (-10.23%) | 
  │ ├ sirius::Non_local_operator                                        |       62.46 μs →       63.65 μs   (+1.91%) |       2   →       2              |      124.91 μs →      127.30 μs   (+1.91%) | 
  │ ├ sirius::D_operator::initialize                                    |       97.01 μs →      101.87 μs   (+5.01%) |       1   →       1              |       97.01 μs →      101.87 μs   (+5.01%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.86 μs →       73.71 μs   (-1.53%) |       1   →       1              |       74.86 μs →       73.71 μs   (-1.53%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.86 s    (+0.40%) |       1   →       1              |        1.86 s  →        1.86 s    (+0.40%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.73 ms →       18.71 ms   (-0.10%) |       1   →       1              |       18.73 ms →       18.71 ms   (-0.10%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      190.19 μs →      177.49 μs   (-6.67%) |       1   →       1              |      190.19 μs →      177.49 μs   (-6.67%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.53 ms →       18.53 ms   (-0.03%) |       1   →       1              |       18.53 ms →       18.53 ms   (-0.03%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.84 s    (+0.41%) |       1   →       1              |        1.84 s  →        1.84 s    (+0.41%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.16 ms →      130.01 ms   (+3.06%) |       4   →       4              |      504.63 ms →      520.06 ms   (+3.06%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.30 ms →       51.93 ms   (-0.72%) |       1   →       1              |       52.30 ms →       51.93 ms   (-0.72%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.11 ms →       21.04 ms   (-0.32%) |       1   →       1              |       21.11 ms →       21.04 ms   (-0.32%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.86 ms →      635.20 ms   (+0.05%) |       1   →       1              |      634.86 ms →      635.20 ms   (+0.05%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.71 ms →      298.05 ms   (+0.11%) |       1   →       1              |      297.71 ms →      298.05 ms   (+0.11%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.67 μs →       14.71 μs (+300.87%) |       1   →       1              |        3.67 μs →       14.71 μs (+300.87%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.71 μs →        2.37 μs  (-12.44%) |       1   →       1              |        2.71 μs →        2.37 μs  (-12.44%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      366.00 ns →      354.00 ns   (-3.28%) |       1   →       1              |      366.00 ns →      354.00 ns   (-3.28%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      518.00 ns →      461.00 ns  (-11.00%) |       1   →       1              |      518.00 ns →      461.00 ns  (-11.00%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.21 ms   (-0.11%) |       1   →       1              |        9.22 ms →        9.21 ms   (-0.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.72 ms →      120.73 ms   (+0.01%) |       1   →       1              |      120.72 ms →      120.73 ms   (+0.01%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.59 ms →      103.58 ms   (-0.01%) |       2   →       2              |      207.17 ms →      207.16 ms   (-0.01%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.15 ms →       40.16 ms   (+0.02%) |       2   →       2              |       80.31 ms →       80.32 ms   (+0.02%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.59 ms →       39.60 ms   (+0.04%) |       2   →       2              |       79.17 ms →       79.20 ms   (+0.04%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       28.50 ns →       13.50 ns  (-52.63%) |       2   →       2              |       57.00 ns →       27.00 ns  (-52.63%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.11 ms →       39.13 ms   (+0.04%) |       2   →       2              |       78.22 ms →       78.26 ms   (+0.04%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       23.50 ns →       23.00 ns   (-2.13%) |       2   →       2              |       47.00 ns →       46.00 ns   (-2.13%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.32 ms →       57.13 ms   (+1.44%) |       1   →       1              |       56.32 ms →       57.13 ms   (+1.44%) | 
  │ │ └ sddk::wf_trans                                                  |       30.77 ms →       30.77 ms   (+0.01%) |       1   →       1              |       30.77 ms →       30.77 ms   (+0.01%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.77 ms →       30.77 ms   (+0.01%) |       1   →       1              |       30.77 ms →       30.77 ms   (+0.01%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      376.00 ns →      603.00 ns  (+60.37%) |       1   →       1              |      376.00 ns →      603.00 ns  (+60.37%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.58 s  →      121.61 s    (+1.69%) |       1   →       1              |      119.58 s  →      121.61 s    (+1.69%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.73 ms   (-1.87%) |      19   →      19              |      111.00 ms →      108.92 ms   (-1.87%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.57 s  →        4.85 s    (+6.14%) |      26   →      25     (-3.85%) |      118.78 s  →      121.22 s    (+2.06%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.70 ms →        5.10 ms  (-10.56%) |      26   →      25     (-3.85%) |      148.19 ms →      127.44 ms  (-14.00%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.34 ms →        4.73 ms  (-11.34%) |      26   →      25     (-3.85%) |      138.78 ms →      118.31 ms  (-14.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      954.49 μs →        1.00 ms   (+4.94%) |      26   →      25     (-3.85%) |       24.82 ms →       25.04 ms   (+0.91%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.49 ms →        2.84 ms  (-18.63%) |      26   →      25     (-3.85%) |       90.84 ms →       71.07 ms  (-21.76%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.51 μs →       64.13 μs   (-0.59%) |      52   →      50     (-3.85%) |        3.35 ms →        3.21 ms   (-4.42%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.44 μs →       87.15 μs   (+0.82%) |      26   →      25     (-3.85%) |        2.25 ms →        2.18 ms   (-3.06%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.82 μs →       78.14 μs   (+0.41%) |      26   →      25     (-3.85%) |        2.02 ms →        1.95 ms   (-3.45%) | 
- │ │ ├ sirius::Band::solve                                             |        2.59 s  →        2.90 s   (+12.14%) |      26   →      25     (-3.85%) |       67.27 s  →       72.53 s    (+7.82%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      151.94 μs →      155.40 μs   (+2.27%) |      26   →      25     (-3.85%) |        3.95 ms →        3.89 ms   (-1.66%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      145.32 μs →      149.20 μs   (+2.67%) |      26   →      25     (-3.85%) |        3.78 ms →        3.73 ms   (-1.28%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.91 μs →        4.32 μs  (-11.93%) |      26   →      25     (-3.85%) |      127.59 μs →      108.04 μs  (-15.32%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.46 s  →        2.70 s    (+9.56%) |      26   →      25     (-3.85%) |       63.95 s  →       67.38 s    (+5.35%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.62 ms →      154.71 ms  (+61.79%) |      26   →      25     (-3.85%) |        2.49 s  →        3.87 s   (+55.57%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.59 ms →        6.98 ms   (-8.12%) |     156   →     175    (+12.18%) |        1.18 s  →        1.22 s    (+3.07%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.98 ms →        6.12 ms   (+2.32%) |      26   →      25     (-3.85%) |      155.45 ms →      152.93 ms   (-1.62%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.57 μs →      347.17 μs   (-0.69%) |      26   →      25     (-3.85%) |        9.09 ms →        8.68 ms   (-4.51%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.38 ms   (+2.76%) |      52   →      50     (-3.85%) |      120.33 ms →      118.90 ms   (-1.19%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.32 s  →        2.43 s    (+4.80%) |      26   →      25     (-3.85%) |       60.38 s  →       60.85 s    (+0.77%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.32 ms →      130.36 ms   (-4.37%) |     262   →     275     (+4.96%) |       35.72 s  →       35.85 s    (+0.37%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.59 ms →       53.03 ms   (-4.61%) |     262   →     275     (+4.96%) |       14.57 s  →       14.58 s    (+0.12%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.93 μs →        1.75 μs   (-9.57%) |     262   →     275     (+4.96%) |      506.22 μs →      480.47 μs   (-5.09%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.48 μs   (-6.40%) |     262   →     275     (+4.96%) |      413.52 μs →      406.25 μs   (-1.76%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      431.74 ns →      295.04 ns  (-31.66%) |     262   →     275     (+4.96%) |      113.12 μs →       81.14 μs  (-28.27%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      436.96 ns →      409.70 ns   (-6.24%) |     262   →     275     (+4.96%) |      114.48 μs →      112.67 μs   (-1.59%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.44 ms   (-0.20%) |     262   →     275     (+4.96%) |        1.95 s  →        2.04 s    (+4.75%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.54 ms →       23.69 ms   (-3.45%) |     262   →     275     (+4.96%) |        6.43 s  →        6.52 s    (+1.34%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.36 ms →       23.09 ms   (-5.21%) |     524   →     550     (+4.96%) |       12.76 s  →       12.70 s    (-0.50%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.83 ms →       34.53 ms   (-3.61%) |     262   →     275     (+4.96%) |        9.39 s  →        9.50 s    (+1.17%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.21 ms →        5.98 ms   (-3.77%) |     498   →     525     (+5.42%) |        3.09 s  →        3.14 s    (+1.45%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.63 ns →       76.65 ns  (+48.46%) |     498   →     525     (+5.42%) |       25.71 μs →       40.24 μs  (+56.50%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.10 ms →        4.84 ms   (-5.01%) |     498   →     525     (+5.42%) |        2.54 s  →        2.54 s    (+0.14%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       28.56 ns →       35.19 ns  (+23.22%) |     498   →     525     (+5.42%) |       14.22 μs →       18.48 μs  (+29.90%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      664.68 μs →      628.27 μs   (-5.48%) |     262   →     275     (+4.96%) |      174.15 ms →      172.77 ms   (-0.79%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.30 ms →        9.55 ms   (-7.27%) |     262   →     275     (+4.96%) |        2.70 s  →        2.63 s    (-2.67%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.49 ms →       14.23 ms   (-1.79%) |     236   →     250     (+5.93%) |        3.42 s  →        3.56 s    (+4.04%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.83 ms →        4.74 ms   (-1.79%) |     708   →     750     (+5.93%) |        3.42 s  →        3.56 s    (+4.04%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.37 ms →        9.88 ms   (-4.71%) |     262   →     275     (+4.96%) |        2.72 s  →        2.72 s    (+0.02%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.17 ms →        9.69 ms   (-4.72%) |     262   →     275     (+4.96%) |        2.66 s  →        2.66 s    (+0.01%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       25.07 ns →       50.39 ns (+101.02%) |     262   →     275     (+4.96%) |        6.57 μs →       13.86 μs (+110.99%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.06 ms →        8.56 ms   (-5.51%) |     262   →     275     (+4.96%) |        2.37 s  →        2.35 s    (-0.82%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       48.13 ns →       69.39 ns  (+44.16%) |     262   →     275     (+4.96%) |       12.61 μs →       19.08 μs  (+51.32%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.86 ms →       17.63 ms   (-1.26%) |     262   →     275     (+4.96%) |        4.68 s  →        4.85 s    (+3.64%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.14 ms →       12.53 ms   (-4.65%) |     252   →     265     (+5.16%) |        3.31 s  →        3.32 s    (+0.26%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.71 ms →       10.70 ms   (-8.60%) |     242   →     264     (+9.09%) |        2.83 s  →        2.83 s    (-0.29%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.85 ms →        5.35 ms   (-8.60%) |     484   →     528     (+9.09%) |        2.83 s  →        2.82 s    (-0.29%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.71 ms →        1.63 ms   (-5.00%) |     242   →     264     (+9.09%) |      414.73 ms →      429.84 ms   (+3.64%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.72 ms →       51.78 ms   (-3.62%) |      85   →      89     (+4.71%) |        4.57 s  →        4.61 s    (+0.92%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.45 ms →       29.84 ms   (-5.11%) |     144   →     153     (+6.25%) |        4.53 s  →        4.57 s    (+0.82%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.31 ms →       21.04 ms   (-5.69%) |     203   →     217     (+6.90%) |        4.53 s  →        4.57 s    (+0.81%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      446.35 ns →      802.16 ns  (+79.72%) |      26   →      25     (-3.85%) |       11.61 μs →       20.05 μs  (+72.80%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       53.14 μs →       43.99 μs  (-17.22%) |      26   →      25     (-3.85%) |        1.38 ms →        1.10 ms  (-20.40%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      607.16 μs →      607.32 μs   (+0.03%) |      26   →      25     (-3.85%) |       15.79 ms →       15.18 ms   (-3.82%) | 
  │ │ ├ sirius::Density::generate                                       |      773.22 ms →      766.13 ms   (-0.92%) |      26   →      25     (-3.85%) |       20.10 s  →       19.15 s    (-4.73%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      405.81 ms →      402.23 ms   (-0.88%) |      26   →      25     (-3.85%) |       10.55 s  →       10.06 s    (-4.69%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.50 μs →        3.54 μs   (+1.00%) |      26   →      25     (-3.85%) |       91.07 μs →       88.44 μs   (-2.88%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.21 μs →        3.13 μs   (-2.62%) |      26   →      25     (-3.85%) |       83.50 μs →       78.18 μs   (-6.36%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.17 ms →      100.36 ms   (+0.18%) |      26   →      25     (-3.85%) |        2.60 s  →        2.51 s    (-3.67%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.75 μs →       12.13 μs  (+12.80%) |      26   →      25     (-3.85%) |      279.58 μs →      303.25 μs   (+8.47%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (-0.03%) |      26   →      25     (-3.85%) |      185.36 ms →      178.18 ms   (-3.88%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.14 ms →       91.32 ms   (+0.20%) |      26   →      25     (-3.85%) |        2.37 s  →        2.28 s    (-3.65%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      591.77 ns →      711.28 ns  (+20.20%) |      26   →      25     (-3.85%) |       15.39 μs →       17.78 μs  (+15.57%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      161.15 ms →      162.36 ms   (+0.75%) |      26   →      25     (-3.85%) |        4.19 s  →        4.06 s    (-3.12%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.04%) |      26   →      25     (-3.85%) |       42.68 ms →       41.06 ms   (-3.81%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.28 ms   (-0.04%) |      26   →      25     (-3.85%) |        2.30 s  →        2.21 s    (-3.88%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms →       88.04 ms   (-0.05%) |      26   →      25     (-3.85%) |        2.29 s  →        2.20 s    (-3.89%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      273.00 ms →      268.80 ms   (-1.54%) |      26   →      25     (-3.85%) |        7.10 s  →        6.72 s    (-5.32%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      273.00 ms →      268.80 ms   (-1.54%) |      26   →      25     (-3.85%) |        7.10 s  →        6.72 s    (-5.32%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.48 ms →       25.87 ms   (+5.69%) |      26   →      25     (-3.85%) |      636.40 ms →      646.75 ms   (+1.63%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      222.92 ms →      218.35 ms   (-2.05%) |      26   →      25     (-3.85%) |        5.80 s  →        5.46 s    (-5.82%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.42 ms →       23.38 ms   (-4.25%) |      26   →      25     (-3.85%) |      634.88 ms →      584.52 ms   (-7.93%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.23 ms →       81.55 ms   (+0.40%) |      26   →      25     (-3.85%) |        2.11 s  →        2.04 s    (-3.46%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.59 ms →        9.93 ms   (+3.56%) |      26   →      25     (-3.85%) |      249.40 ms →      248.35 ms   (-0.42%) | 
  │ │ ├ sirius::Density::mix                                            |      218.18 ms →      212.86 ms   (-2.44%) |      26   →      25     (-3.85%) |        5.67 s  →        5.32 s    (-6.19%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      930.91 μs →      956.38 μs   (+2.74%) |      26   →      25     (-3.85%) |       24.20 ms →       23.91 ms   (-1.22%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.63 ms →       10.40 ms   (-2.19%) |     334   →     319     (-4.49%) |        3.55 s  →        3.32 s    (-6.58%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.42 ms →        9.94 ms   (-4.62%) |     334   →     319     (-4.49%) |        3.48 s  →        3.17 s    (-8.90%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.42 ms →        9.94 ms   (-4.62%) |     334   →     319     (-4.49%) |        3.48 s  →        3.17 s    (-8.90%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.82 ms →        6.61 ms   (-2.98%) |      26   →      25     (-3.85%) |      177.22 ms →      165.34 ms   (-6.71%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.97 ms →        5.74 ms   (-3.79%) |      26   →      25     (-3.85%) |      155.11 ms →      143.49 ms   (-7.49%) | 
  │ │ ├ sirius::Potential::generate                                     |      581.59 ms →      566.99 ms   (-2.51%) |      26   →      25     (-3.85%) |       15.12 s  →       14.17 s    (-6.26%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.91 ms →      125.54 ms   (-8.97%) |      26   →      25     (-3.85%) |        3.59 s  →        3.14 s   (-12.47%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       19.79 ms →        6.66 ms  (-66.37%) |      26   →      25     (-3.85%) |      514.53 ms →      166.38 ms  (-67.66%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.20 ms →       10.94 ms   (+7.22%) |      26   →      25     (-3.85%) |      265.22 ms →      273.43 ms   (+3.10%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.00 ms →       10.49 ms   (+4.93%) |      26   →      25     (-3.85%) |      260.03 ms →      262.36 ms   (+0.90%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.00 ms →       10.49 ms   (+4.93%) |      26   →      25     (-3.85%) |      260.01 ms →      262.33 ms   (+0.89%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      545.26 μs →      549.92 μs   (+0.85%) |      52   →      50     (-3.85%) |       28.35 ms →       27.50 ms   (-3.03%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.42 ms →       49.13 ms   (-0.59%) |      26   →      25     (-3.85%) |        1.28 s  →        1.23 s    (-4.41%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.07 ms →       46.74 ms   (-0.72%) |      26   →      25     (-3.85%) |        1.22 s  →        1.17 s    (-4.53%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.99 ms →        3.07 ms   (+2.68%) |      52   →      50     (-3.85%) |      155.68 ms →      153.69 ms   (-1.27%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        6.01 ms →        5.25 ms  (-12.73%) |      26   →      25     (-3.85%) |      156.28 ms →      131.14 ms  (-16.09%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.03 ms →        6.42 ms   (-8.70%) |      26   →      25     (-3.85%) |      182.80 ms →      160.48 ms  (-12.21%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.23 ms →       90.91 ms   (-0.35%) |      26   →      25     (-3.85%) |        2.37 s  →        2.27 s    (-4.18%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.62 ms →      292.56 ms   (-0.36%) |      26   →      25     (-3.85%) |        7.63 s  →        7.31 s    (-4.19%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.89 ms →      273.47 ms   (-2.64%) |      26   →      25     (-3.85%) |        7.30 s  →        6.84 s    (-6.39%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.89 ms →      273.47 ms   (-2.64%) |      26   →      25     (-3.85%) |        7.30 s  →        6.84 s    (-6.39%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.99 ms →       28.61 ms   (+2.21%) |      26   →      25     (-3.85%) |      727.79 ms →      715.26 ms   (-1.72%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.53 ms →      217.22 ms   (-3.26%) |      26   →      25     (-3.85%) |        5.84 s  →        5.43 s    (-6.98%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.58 ms →       23.83 ms   (-3.03%) |      26   →      25     (-3.85%) |      639.03 ms →      595.83 ms   (-6.76%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.91 ms →        7.64 ms  (+29.20%) |      26   →      25     (-3.85%) |      153.74 ms →      190.98 ms  (+24.23%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.64 ms →       10.40 ms   (-2.22%) |     182   →     175     (-3.85%) |        1.94 s  →        1.82 s    (-5.98%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.27 ms →        9.80 ms   (-4.53%) |     182   →     175     (-3.85%) |        1.87 s  →        1.72 s    (-8.21%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.27 ms →        9.80 ms   (-4.53%) |     182   →     175     (-3.85%) |        1.87 s  →        1.72 s    (-8.21%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.05 ms →       10.58 ms   (+5.29%) |      78   →      75     (-3.85%) |      784.14 ms →      793.86 ms   (+1.24%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.80 ms →       10.14 ms   (+3.44%) |      78   →      75     (-3.85%) |      764.73 ms →      760.63 ms   (-0.54%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.92 ms →        9.95 ms   (+0.32%) |      26   →      25     (-3.85%) |      257.96 ms →      248.83 ms   (-3.54%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      196.61 μs →      119.49 μs  (-39.22%) |      26   →      25     (-3.85%) |        5.11 ms →        2.99 ms  (-41.56%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      192.02 μs →      114.82 μs  (-40.21%) |      26   →      25     (-3.85%) |        4.99 ms →        2.87 ms  (-42.51%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.50 ms →        5.26 ms   (-4.32%) |       2   →       2              |       11.00 ms →       10.53 ms   (-4.32%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.55 ms →       10.45 ms   (-0.93%) |       6   →       6              |       63.29 ms →       62.70 ms   (-0.93%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.50 ms →       10.43 ms   (-0.67%) |       6   →       6              |       62.98 ms →       62.56 ms   (-0.67%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.50 ms →       10.43 ms   (-0.67%) |       6   →       6              |       62.98 ms →       62.56 ms   (-0.67%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.99 ms →       10.51 ms   (+5.18%) |       3   →       3              |       29.96 ms →       31.52 ms   (+5.18%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.98 ms →       10.48 ms   (+5.04%) |       3   →       3              |       29.94 ms →       31.45 ms   (+5.04%) | 
  ├ sirius::Periodic_function|inner                                     |       10.50 ms →       10.08 ms   (-4.01%) |       2   →       2              |       20.99 ms →       20.15 ms   (-4.01%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.49 ms →        9.76 ms   (-6.94%) |       2   →       2              |       20.97 ms →       19.52 ms   (-6.94%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.49 ms →        9.76 ms   (-6.94%) |       2   →       2              |       20.97 ms →       19.52 ms   (-6.94%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.95 ms →       10.55 ms   (+6.05%) |       1   →       1              |        9.95 ms →       10.55 ms   (+6.05%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.94 ms →       10.17 ms   (+2.30%) |       1   →       1              |        9.94 ms →       10.17 ms   (+2.30%) | 
- └ sirius::finalize                                                    |      193.52 ms →      239.60 ms  (+23.81%) |       1   →       1              |      193.52 ms →      239.60 ms  (+23.81%) | 
  ====================================================================================================================================================================================================
```
