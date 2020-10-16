# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      135.33 s  →      129.79 s    (-4.10%) |       1   →       1              |      135.33 s  →      129.79 s    (-4.10%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.74 s    (+1.51%) |       1   →       1              |        2.70 s  →        2.74 s    (+1.51%) | 
- ├ sirius::Simulation_context::initialize                              |        2.95 s  →        3.46 s   (+17.32%) |       1   →       1              |        2.95 s  →        3.46 s   (+17.32%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       15.95 ms →      986.66 μs  (-93.82%) |       1   →       1              |       15.95 ms →      986.66 μs  (-93.82%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      153.38 ms →      661.55 ms (+331.31%) |       1   →       1              |      153.38 ms →      661.55 ms (+331.31%) | 
- │ │ ├ sirius::Atom_type::init                                         |       64.87 ms →      318.84 ms (+391.47%) |       2   →       2              |      129.75 ms →      637.68 ms (+391.47%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.56 ms →       23.80 ms   (+1.02%) |       1   →       1              |       23.56 ms →       23.80 ms   (+1.02%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.62 ms →        6.33 ms   (-4.31%) |       1   →       1              |        6.62 ms →        6.33 ms   (-4.31%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.89 ms →       17.43 ms   (+3.15%) |       1   →       1              |       16.89 ms →       17.43 ms   (+3.15%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.87 ms →       17.40 ms   (+3.16%) |       1   →       1              |       16.87 ms →       17.40 ms   (+3.16%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.18 ms   (+0.96%) |       1   →       1              |        4.14 ms →        4.18 ms   (+0.96%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.32 ms   (-1.13%) |       1   →       1              |        2.35 ms →        2.32 ms   (-1.13%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |      120.94 μs →      102.30 μs  (-15.42%) |       1   →       1              |      120.94 μs →      102.30 μs  (-15.42%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.75 s    (+0.68%) |       1   →       1              |        2.73 s  →        2.75 s    (+0.68%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.89 ms   (+0.36%) |       1   →       1              |       10.85 ms →       10.89 ms   (+0.36%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.46 ms →        4.42 ms   (-0.83%) |       1   →       1              |        4.46 ms →        4.42 ms   (-0.83%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.44 ms   (+1.22%) |       1   →       1              |        6.36 ms →        6.44 ms   (+1.22%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.42 ms   (+1.21%) |       1   →       1              |        6.34 ms →        6.42 ms   (+1.21%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.84 ms →        3.91 ms   (+1.87%) |       1   →       1              |        3.84 ms →        3.91 ms   (+1.87%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.11%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.11%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.97 μs →      104.00 μs   (+3.01%) |       1   →       1              |      100.97 μs →      104.00 μs   (+3.01%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       66.84 ms →       69.91 ms   (+4.59%) |       2   →       2              |      133.68 ms →      139.82 ms   (+4.59%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.19 ms →        5.17 ms   (-0.31%) |       2   →       2              |       10.37 ms →       10.34 ms   (-0.31%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.60 ms →        4.54 ms   (-1.25%) |       1   →       1              |        4.60 ms →        4.54 ms   (-1.25%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.00 ms →       21.82 ms   (-0.83%) |       2   →       2              |       44.00 ms →       43.63 ms   (-0.83%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.08 ms →       15.19 ms   (+0.73%) |       2   →       2              |       30.17 ms →       30.39 ms   (+0.73%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.75 ms →       19.82 ms   (+0.32%) |       4   →       4              |       79.01 ms →       79.27 ms   (+0.32%) | 
  │   ├ sddk::Gvec::init                                                |      176.89 ms →      179.12 ms   (+1.26%) |       2   →       2              |      353.77 ms →      358.24 ms   (+1.26%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.51 ms →      135.87 ms   (+2.54%) |       2   →       2              |      265.02 ms →      271.75 ms   (+2.54%) | 
+ │   ├ sddk::Gvec_shells                                               |      203.83 ms →      172.35 ms  (-15.45%) |       1   →       1              |      203.83 ms →      172.35 ms  (-15.45%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.33 ms   (+1.05%) |       1   →       1              |        1.32 ms →        1.33 ms   (+1.05%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.25 ms →      296.91 ms   (+1.25%) |       2   →       2              |      586.50 ms →      593.81 ms   (+1.25%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.19 ms →       35.57 ms   (-1.71%) |       1   →       1              |       36.19 ms →       35.57 ms   (-1.71%) | 
  │ ├ sirius::K_point::K_point                                          |        2.52 μs →        2.27 μs   (-9.82%) |       4   →       4              |       10.07 μs →        9.09 μs   (-9.82%) | 
  │ └ sirius::K_point_set::initialize                                   |       36.09 ms →       35.47 ms   (-1.71%) |       1   →       1              |       36.09 ms →       35.47 ms   (-1.71%) | 
  │   └ sirius::K_point::initialize                                     |       35.99 ms →       35.36 ms   (-1.75%) |       1   →       1              |       35.99 ms →       35.36 ms   (-1.75%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.26 ms →       18.15 ms   (-0.64%) |       1   →       1              |       18.26 ms →       18.15 ms   (-0.64%) | 
  │     │ └ sddk::Gvec::init                                            |        8.15 ms →        8.19 ms   (+0.41%) |       1   →       1              |        8.15 ms →        8.19 ms   (+0.41%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.43 μs →       10.13 μs   (-2.92%) |       1   →       1              |       10.43 μs →       10.13 μs   (-2.92%) | 
  │     └ sirius::K_point::update                                       |       12.66 ms →       12.42 ms   (-1.89%) |       1   →       1              |       12.66 ms →       12.42 ms   (-1.89%) | 
  │       └ sirius::Beta_projectors                                     |        6.21 ms →        6.17 ms   (-0.76%) |       1   →       1              |        6.21 ms →        6.17 ms   (-0.76%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.59 ms →        3.55 ms   (-1.19%) |       1   →       1              |        3.59 ms →        3.55 ms   (-1.19%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.25 ms →        5.41 ms   (+2.94%) |       2   →       2              |       10.50 ms →       10.81 ms   (+2.94%) | 
  ├ sirius::Potential                                                   |      159.54 ms →      159.77 ms   (+0.15%) |       1   →       1              |      159.54 ms →      159.77 ms   (+0.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.88 ms →        5.91 ms   (+0.44%) |       6   →       6              |       35.28 ms →       35.44 ms   (+0.44%) | 
  │ └ sirius::Potential::update                                         |      123.51 ms →      123.57 ms   (+0.05%) |       1   →       1              |      123.51 ms →      123.57 ms   (+0.05%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.69 ms →      122.76 ms   (+0.06%) |       1   →       1              |      122.69 ms →      122.76 ms   (+0.06%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.29 ms →      115.16 ms   (+3.48%) |       1   →       1              |      111.29 ms →      115.16 ms   (+3.48%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.48 ms →        6.72 ms  (-35.88%) |       1   →       1              |       10.48 ms →        6.72 ms  (-35.88%) | 
  ├ sirius::Density                                                     |      136.48 ms →      136.85 ms   (+0.27%) |       1   →       1              |      136.48 ms →      136.85 ms   (+0.27%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.20 ms →        5.24 ms   (+0.63%) |       2   →       2              |       10.41 ms →       10.47 ms   (+0.63%) | 
  │ └ sirius::Density::update                                           |      125.79 ms →      126.07 ms   (+0.22%) |       1   →       1              |      125.79 ms →      126.07 ms   (+0.22%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.36 ms →      125.64 ms   (+0.22%) |       1   →       1              |      125.36 ms →      125.64 ms   (+0.22%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.19 μs →      102.76 μs   (-2.31%) |       1   →       1              |      105.19 μs →      102.76 μs   (-2.31%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.91 ms →      119.54 ms   (+5.88%) |       1   →       1              |      112.91 ms →      119.54 ms   (+5.88%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.88 ms →        5.53 ms  (-53.41%) |       1   →       1              |       11.88 ms →        5.53 ms  (-53.41%) | 
  ├ sirius::Density::initial_density                                    |      176.41 ms →      179.70 ms   (+1.87%) |       1   →       1              |      176.41 ms →      179.70 ms   (+1.87%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      111.53 ms →      124.06 ms  (+11.24%) |       1   →       1              |      111.53 ms →      124.06 ms  (+11.24%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.53 ms →        5.71 ms  (-45.75%) |       2   →       2              |       21.06 ms →       11.42 ms  (-45.75%) | 
  │ └ sirius::Periodic_function::integrate                              |       11.25 ms →       11.74 ms   (+4.32%) |       1   →       1              |       11.25 ms →       11.74 ms   (+4.32%) | 
  ├ sirius::Potential::generate                                         |      597.65 ms →      594.38 ms   (-0.55%) |       1   →       1              |      597.65 ms →      594.38 ms   (-0.55%) | 
  │ ├ sirius::Potential::poisson                                        |      138.06 ms →      138.30 ms   (+0.17%) |       1   →       1              |      138.06 ms →      138.30 ms   (+0.17%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       14.94 ms →        5.32 ms  (-64.37%) |       1   →       1              |       14.94 ms →        5.32 ms  (-64.37%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.36 ms →       10.26 ms   (-0.92%) |       1   →       1              |       10.36 ms →       10.26 ms   (-0.92%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.93 ms →       10.21 ms   (+2.80%) |       1   →       1              |        9.93 ms →       10.21 ms   (+2.80%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.92 ms →       10.20 ms   (+2.79%) |       1   →       1              |        9.92 ms →       10.20 ms   (+2.79%) | 
  │ ├ sirius::Periodic_function::add                                    |      547.58 μs →      548.93 μs   (+0.25%) |       2   →       2              |        1.10 ms →        1.10 ms   (+0.25%) | 
  │ ├ sirius::Potential::xc                                             |       56.26 ms →       54.55 ms   (-3.05%) |       1   →       1              |       56.26 ms →       54.55 ms   (-3.05%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.86 ms →       52.13 ms   (-3.22%) |       1   →       1              |       53.86 ms →       52.13 ms   (-3.22%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.76 ms →        5.82 ms   (+1.17%) |       2   →       2              |       11.51 ms →       11.65 ms   (+1.17%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        6.08 ms →        5.22 ms  (-14.12%) |       1   →       1              |        6.08 ms →        5.22 ms  (-14.12%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.72 ms →        5.81 ms   (+1.70%) |       1   →       1              |        5.72 ms →        5.81 ms   (+1.70%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.69 ms →       93.53 ms   (-0.17%) |       1   →       1              |       93.69 ms →       93.53 ms   (-0.17%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      301.43 ms →      299.70 ms   (-0.57%) |       1   →       1              |      301.43 ms →      299.70 ms   (-0.57%) | 
  ├ sirius::Hamiltonian0                                                |        8.51 ms →        8.69 ms   (+2.13%) |       1   →       1              |        8.51 ms →        8.69 ms   (+2.13%) | 
  │ ├ sirius::Local_operator                                            |        8.16 ms →        8.34 ms   (+2.20%) |       1   →       1              |        8.16 ms →        8.34 ms   (+2.20%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.78 ms   (+0.59%) |       1   →       1              |        4.75 ms →        4.78 ms   (+0.59%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.49 ms →        2.64 ms   (+5.99%) |       1   →       1              |        2.49 ms →        2.64 ms   (+5.99%) | 
  │ ├ sirius::Non_local_operator                                        |       62.55 μs →       62.77 μs   (+0.34%) |       2   →       2              |      125.11 μs →      125.53 μs   (+0.34%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.17 μs →       95.01 μs   (+0.89%) |       1   →       1              |       94.17 μs →       95.01 μs   (+0.89%) | 
  │ └ sirius::Q_operator::initialize                                    |       75.39 μs →       74.44 μs   (-1.27%) |       1   →       1              |       75.39 μs →       74.44 μs   (-1.27%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.89 s  →        1.88 s    (-0.32%) |       1   →       1              |        1.89 s  →        1.88 s    (-0.32%) | 
  │ ├ sirius::Hamiltonian_k                                             |       19.76 ms →       18.70 ms   (-5.40%) |       1   →       1              |       19.76 ms →       18.70 ms   (-5.40%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      187.56 μs →      187.35 μs   (-0.12%) |       1   →       1              |      187.56 μs →      187.35 μs   (-0.12%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       19.57 ms →       18.51 ms   (-5.45%) |       1   →       1              |       19.57 ms →       18.51 ms   (-5.45%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.87 s  →        1.86 s    (-0.27%) |       1   →       1              |        1.87 s  →        1.86 s    (-0.27%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      130.90 ms →      131.64 ms   (+0.56%) |       4   →       4              |      523.62 ms →      526.56 ms   (+0.56%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.03 ms →       52.25 ms   (+0.42%) |       1   →       1              |       52.03 ms →       52.25 ms   (+0.42%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.05 ms →       20.99 ms   (-0.25%) |       1   →       1              |       21.05 ms →       20.99 ms   (-0.25%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.72 ms →      637.71 ms   (+0.15%) |       1   →       1              |      636.72 ms →      637.71 ms   (+0.15%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.60 ms →      297.70 ms   (+0.03%) |       1   →       1              |      297.60 ms →      297.70 ms   (+0.03%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.38 μs →        3.83 μs  (+13.40%) |       1   →       1              |        3.38 μs →        3.83 μs  (+13.40%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.50 μs →        2.92 μs  (+16.71%) |       1   →       1              |        2.50 μs →        2.92 μs  (+16.71%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      366.00 ns →      457.00 ns  (+24.86%) |       1   →       1              |      366.00 ns →      457.00 ns  (+24.86%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      515.00 ns →      556.00 ns   (+7.96%) |       1   →       1              |      515.00 ns →      556.00 ns   (+7.96%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.21 ms   (-0.19%) |       1   →       1              |        9.23 ms →        9.21 ms   (-0.19%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.71 ms →      121.89 ms   (+0.97%) |       1   →       1              |      120.71 ms →      121.89 ms   (+0.97%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.57 ms →      104.43 ms   (-0.13%) |       2   →       2              |      209.14 ms →      208.87 ms   (-0.13%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.16 ms →       40.23 ms   (+0.19%) |       2   →       2              |       80.32 ms →       80.47 ms   (+0.19%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.60 ms →       39.67 ms   (+0.19%) |       2   →       2              |       79.19 ms →       79.35 ms   (+0.19%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |      113.00 ns →       25.50 ns  (-77.43%) |       2   →       2              |      226.00 ns →       51.00 ns  (-77.43%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.12 ms →       39.20 ms   (+0.19%) |       2   →       2              |       78.24 ms →       78.40 ms   (+0.19%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       30.50 ns  (+60.53%) |       2   →       2              |       38.00 ns →       61.00 ns  (+60.53%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.25 ms →       56.68 ms   (+0.75%) |       1   →       1              |       56.25 ms →       56.68 ms   (+0.75%) | 
  │ │ └ sddk::wf_trans                                                  |       30.73 ms →       30.74 ms   (+0.03%) |       1   →       1              |       30.73 ms →       30.74 ms   (+0.03%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.73 ms →       30.73 ms   (+0.03%) |       1   →       1              |       30.73 ms →       30.73 ms   (+0.03%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      380.00 ns →      487.00 ns  (+28.16%) |       1   →       1              |      380.00 ns →      487.00 ns  (+28.16%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      125.57 s  →      119.54 s    (-4.81%) |       1   →       1              |      125.57 s  →      119.54 s    (-4.81%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.88 ms   (+0.04%) |      19   →      19              |      111.61 ms →      111.65 ms   (+0.04%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.80 s  →        4.58 s    (-4.61%) |      26   →      26              |      124.90 s  →      119.14 s    (-4.61%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        6.10 ms →        4.53 ms  (-25.82%) |      26   →      26              |      158.68 ms →      117.72 ms  (-25.82%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.73 ms →        4.16 ms  (-27.42%) |      26   →      26              |      149.01 ms →      108.16 ms  (-27.42%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      967.29 μs →      976.09 μs   (+0.91%) |      26   →      26              |       25.15 ms →       25.38 ms   (+0.91%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.82 ms →        2.29 ms  (-40.13%) |      26   →      26              |       99.24 ms →       59.42 ms  (-40.13%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.80 μs →       64.75 μs   (-0.07%) |      52   →      52              |        3.37 ms →        3.37 ms   (-0.07%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       89.09 μs →       89.25 μs   (+0.18%) |      26   →      26              |        2.32 ms →        2.32 ms   (+0.18%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       80.24 μs →       78.53 μs   (-2.14%) |      26   →      26              |        2.09 ms →        2.04 ms   (-2.14%) | 
  │ │ ├ sirius::Band::solve                                             |        2.78 s  →        2.60 s    (-6.32%) |      26   →      26              |       72.27 s  →       67.71 s    (-6.32%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      157.87 μs →      151.63 μs   (-3.96%) |      26   →      26              |        4.10 ms →        3.94 ms   (-3.96%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      150.01 μs →      144.33 μs   (-3.79%) |      26   →      26              |        3.90 ms →        3.75 ms   (-3.79%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.89 μs →        5.34 μs   (-9.38%) |      26   →      26              |      153.27 μs →      138.90 μs   (-9.38%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.65 s  →        2.48 s    (-6.37%) |      26   →      26              |       68.99 s  →       64.60 s    (-6.37%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.36 ms →       96.12 ms   (+0.79%) |      26   →      26              |        2.48 s  →        2.50 s    (+0.79%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.74 ms →        7.83 ms   (+1.15%) |     156   →     156              |        1.21 s  →        1.22 s    (+1.15%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.93 ms →        5.91 ms   (-0.25%) |      26   →      26              |      154.08 ms →      153.68 ms   (-0.25%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.50 μs →      347.37 μs   (-1.18%) |      26   →      26              |        9.14 ms →        9.03 ms   (-1.18%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.29 ms   (-0.63%) |      52   →      52              |      120.02 ms →      119.26 ms   (-0.63%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.52 s  →        2.35 s    (-6.75%) |      26   →      26              |       65.43 s  →       61.01 s    (-6.75%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      127.90 ms →      137.76 ms   (+7.70%) |     278   →     262     (-5.76%) |       35.56 s  →       36.09 s    (+1.50%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       51.19 ms →       55.81 ms   (+9.03%) |     278   →     262     (-5.76%) |       14.23 s  →       14.62 s    (+2.75%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.20 μs →        2.00 μs   (-8.86%) |     278   →     262     (-5.76%) |      611.38 μs →      525.17 μs  (-14.10%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.88 μs →        1.70 μs   (-9.54%) |     278   →     262     (-5.76%) |      521.49 μs →      444.57 μs  (-14.75%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      409.49 ns →      426.21 ns   (+4.08%) |     278   →     262     (-5.76%) |      113.84 μs →      111.67 μs   (-1.91%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      506.72 ns →      562.48 ns  (+11.01%) |     278   →     262     (-5.76%) |      140.87 μs →      147.37 μs   (+4.62%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.43%) |     278   →     262     (-5.76%) |        2.06 s  →        1.95 s    (-5.35%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.36 ms →       25.39 ms   (+8.67%) |     278   →     262     (-5.76%) |        6.49 s  →        6.65 s    (+2.41%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.96 ms →       24.55 ms   (+6.92%) |     556   →     524     (-5.76%) |       12.77 s  →       12.86 s    (+0.76%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.23 ms →       35.89 ms   (+4.82%) |     278   →     262     (-5.76%) |        9.52 s  →        9.40 s    (-1.21%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.95 ms →        6.23 ms   (+4.66%) |     530   →     498     (-6.04%) |        3.15 s  →        3.10 s    (-1.66%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       79.93 ns →       48.29 ns  (-39.59%) |     530   →     498     (-6.04%) |       42.36 μs →       24.05 μs  (-43.24%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.84 ms →        5.12 ms   (+5.70%) |     530   →     498     (-6.04%) |        2.57 s  →        2.55 s    (-0.68%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       51.95 ns →       29.69 ns  (-42.85%) |     530   →     498     (-6.04%) |       27.54 μs →       14.79 μs  (-46.30%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      602.98 μs →      660.07 μs   (+9.47%) |     278   →     262     (-5.76%) |      167.63 ms →      172.94 ms   (+3.17%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.52 ms →       10.31 ms   (+8.29%) |     278   →     262     (-5.76%) |        2.65 s  →        2.70 s    (+2.06%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.08 ms →       14.51 ms   (+3.09%) |     252   →     236     (-6.35%) |        3.55 s  →        3.43 s    (-3.46%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.69 ms →        4.84 ms   (+3.09%) |     756   →     708     (-6.35%) |        3.55 s  →        3.42 s    (-3.46%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.31 ms →       10.39 ms   (+0.75%) |     278   →     262     (-5.76%) |        2.87 s  →        2.72 s    (-5.05%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.04 ms →       10.18 ms   (+1.42%) |     278   →     262     (-5.76%) |        2.79 s  →        2.67 s    (-4.41%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       45.19 ns →       30.12 ns  (-33.36%) |     278   →     262     (-5.76%) |       12.56 μs →        7.89 μs  (-37.19%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.93 ms →        9.07 ms   (+1.58%) |     278   →     262     (-5.76%) |        2.48 s  →        2.38 s    (-4.26%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       65.69 ns →       46.98 ns  (-28.48%) |     278   →     262     (-5.76%) |       18.26 μs →       12.31 μs  (-32.59%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       35.56 ms →       18.72 ms  (-47.34%) |     278   →     262     (-5.76%) |        9.88 s  →        4.91 s   (-50.37%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.47 ms →       13.16 ms   (-2.27%) |     269   →     252     (-6.32%) |        3.62 s  →        3.32 s    (-8.45%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.16 ms →       11.73 ms   (-3.54%) |     259   →     242     (-6.56%) |        3.15 s  →        2.84 s    (-9.87%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.08 ms →        5.86 ms   (-3.54%) |     518   →     484     (-6.56%) |        3.15 s  →        2.84 s    (-9.87%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.73 ms   (+8.58%) |     259   →     242     (-6.56%) |      412.04 ms →      418.04 ms   (+1.46%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.93 ms →       53.73 ms  (-28.29%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+15.01%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.41 ms →       31.45 ms  (-36.35%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.57%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.94 ms →       22.31 ms  (-39.61%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.57%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      647.81 ns →      422.50 ns  (-34.78%) |      26   →      26              |       16.84 μs →       10.98 μs  (-34.78%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |      246.28 μs →       45.38 μs  (-81.58%) |      26   →      26              |        6.40 ms →        1.18 ms  (-81.58%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      600.88 μs →      610.16 μs   (+1.55%) |      26   →      26              |       15.62 ms →       15.86 ms   (+1.55%) | 
  │ │ ├ sirius::Density::generate                                       |      794.05 ms →      780.21 ms   (-1.74%) |      26   →      26              |       20.65 s  →       20.29 s    (-1.74%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      408.52 ms →      403.79 ms   (-1.16%) |      26   →      26              |       10.62 s  →       10.50 s    (-1.16%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.69 μs →        8.81 μs   (+1.44%) |      26   →      26              |      225.84 μs →      229.10 μs   (+1.44%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.17 μs →        8.28 μs   (+1.33%) |      26   →      26              |      212.41 μs →      215.24 μs   (+1.33%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.32 ms →      100.43 ms   (+0.11%) |      26   →      26              |        2.61 s  →        2.61 s    (+0.11%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.75 μs →        7.86 μs   (+1.36%) |      26   →      26              |      201.62 μs →      204.36 μs   (+1.36%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.03%) |      26   →      26              |      185.08 ms →      185.14 ms   (+0.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.28 ms →       91.43 ms   (+0.17%) |      26   →      26              |        2.37 s  →        2.38 s    (+0.17%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      875.42 ns →      777.85 ns  (-11.15%) |      26   →      26              |       22.76 μs →       20.22 μs  (-11.15%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.09 ms →      163.31 ms   (-0.48%) |      26   →      26              |        4.27 s  →        4.25 s    (-0.48%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.63 ms →        1.64 ms   (+0.83%) |      26   →      26              |       42.39 ms →       42.75 ms   (+0.83%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.24 ms →       88.28 ms   (+0.04%) |      26   →      26              |        2.29 s  →        2.30 s    (+0.04%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.02 ms →       88.04 ms   (+0.02%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      287.69 ms →      274.66 ms   (-4.53%) |      26   →      26              |        7.48 s  →        7.14 s    (-4.53%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      287.69 ms →      274.66 ms   (-4.53%) |      26   →      26              |        7.48 s  →        7.14 s    (-4.53%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       30.75 ms →       24.08 ms  (-21.69%) |      26   →      26              |      799.57 ms →      626.16 ms  (-21.69%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      223.99 ms →      226.25 ms   (+1.01%) |      26   →      26              |        5.82 s  →        5.88 s    (+1.01%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       31.75 ms →       23.13 ms  (-27.14%) |      26   →      26              |      825.52 ms →      601.48 ms  (-27.14%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       86.48 ms →       81.64 ms   (-5.60%) |      26   →      26              |        2.25 s  →        2.12 s    (-5.60%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.78 ms →       16.54 ms (+112.52%) |      26   →      26              |      202.31 ms →      429.96 ms (+112.52%) | 
  │ │ ├ sirius::Density::mix                                            |      220.05 ms →      212.99 ms   (-3.21%) |      26   →      26              |        5.72 s  →        5.54 s    (-3.21%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      968.61 μs →      932.25 μs   (-3.75%) |      26   →      26              |       25.18 ms →       24.24 ms   (-3.75%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.68 ms →       10.29 ms   (-3.66%) |     334   →     334              |        3.57 s  →        3.44 s    (-3.66%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.33 ms →        9.92 ms   (-3.93%) |     334   →     334              |        3.45 s  →        3.31 s    (-3.93%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.33 ms →        9.92 ms   (-3.93%) |     334   →     334              |        3.45 s  →        3.31 s    (-3.93%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        8.81 ms →        6.65 ms  (-24.53%) |      26   →      26              |      229.00 ms →      172.84 ms  (-24.53%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.96 ms →        5.80 ms  (-27.20%) |      26   →      26              |      207.00 ms →      150.70 ms  (-27.20%) | 
  │ │ ├ sirius::Potential::generate                                     |      584.71 ms →      580.38 ms   (-0.74%) |      26   →      26              |       15.20 s  →       15.09 s    (-0.74%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.16 ms →      138.48 ms   (+0.23%) |      26   →      26              |        3.59 s  →        3.60 s    (+0.23%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.57 ms →        5.30 ms  (-65.94%) |      26   →      26              |      404.94 ms →      137.91 ms  (-65.94%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.35 ms →       10.30 ms   (-0.54%) |      26   →      26              |      269.15 ms →      267.70 ms   (-0.54%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.95 ms →       10.07 ms   (+1.25%) |      26   →      26              |      258.70 ms →      261.94 ms   (+1.25%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.95 ms →       10.07 ms   (+1.26%) |      26   →      26              |      258.68 ms →      261.93 ms   (+1.26%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.82 μs →      553.48 μs   (+0.48%) |      52   →      52              |       28.64 ms →       28.78 ms   (+0.48%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       51.83 ms →       49.24 ms   (-4.99%) |      26   →      26              |        1.35 s  →        1.28 s    (-4.99%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       49.47 ms →       46.86 ms   (-5.27%) |      26   →      26              |        1.29 s  →        1.22 s    (-5.27%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        3.04 ms   (+0.46%) |      52   →      52              |      157.44 ms →      158.16 ms   (+0.46%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        8.15 ms →        5.66 ms  (-30.58%) |      26   →      26              |      211.87 ms →      147.08 ms  (-30.58%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.25 ms →        6.68 ms   (-7.93%) |      26   →      26              |      188.54 ms →      173.58 ms   (-7.93%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       92.29 ms →       90.99 ms   (-1.41%) |      26   →      26              |        2.40 s  →        2.37 s    (-1.41%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.80 ms →      292.57 ms   (-0.08%) |      26   →      26              |        7.61 s  →        7.61 s    (-0.08%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      294.60 ms →      280.69 ms   (-4.72%) |      26   →      26              |        7.66 s  →        7.30 s    (-4.72%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      294.60 ms →      280.69 ms   (-4.72%) |      26   →      26              |        7.66 s  →        7.30 s    (-4.72%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       34.36 ms →       27.38 ms  (-20.31%) |      26   →      26              |      893.29 ms →      711.85 ms  (-20.31%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.26 ms →      225.63 ms   (+0.17%) |      26   →      26              |        5.86 s  →        5.87 s    (+0.17%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       31.20 ms →       23.87 ms  (-23.50%) |      26   →      26              |      811.25 ms →      620.63 ms  (-23.50%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.13 ms →        5.61 ms  (-21.33%) |      26   →      26              |      185.35 ms →      145.82 ms  (-21.33%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.44 ms →       10.16 ms   (-2.72%) |     182   →     182              |        1.90 s  →        1.85 s    (-2.72%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.79 ms   (-0.30%) |     182   →     182              |        1.79 s  →        1.78 s    (-0.30%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →        9.79 ms   (-0.29%) |     182   →     182              |        1.79 s  →        1.78 s    (-0.29%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.10 ms →       10.68 ms   (-3.77%) |      78   →      78              |      865.65 ms →      833.05 ms   (-3.77%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.65 ms →       10.18 ms   (-4.36%) |      78   →      78              |      830.64 ms →      794.42 ms   (-4.36%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.98 ms →        9.94 ms   (-0.43%) |      26   →      26              |      259.48 ms →      258.35 ms   (-0.43%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      217.40 μs →      158.22 μs  (-27.22%) |      26   →      26              |        5.65 ms →        4.11 ms  (-27.22%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      212.60 μs →      152.86 μs  (-28.10%) |      26   →      26              |        5.53 ms →        3.97 ms  (-28.10%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.33 ms →        5.17 ms   (-3.05%) |       2   →       2              |       10.66 ms →       10.34 ms   (-3.05%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.87 ms →        9.84 ms   (-9.49%) |       6   →       6              |       65.23 ms →       59.04 ms   (-9.49%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.09 ms →        9.81 ms   (-2.78%) |       6   →       6              |       60.56 ms →       58.87 ms   (-2.78%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.09 ms →        9.81 ms   (-2.78%) |       6   →       6              |       60.56 ms →       58.87 ms   (-2.78%) | 
+ │ └ sirius::Smooth_periodic_function|inner                            |       11.83 ms →       10.08 ms  (-14.77%) |       3   →       3              |       35.48 ms →       30.24 ms  (-14.77%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.83 ms →       10.06 ms   (-7.13%) |       3   →       3              |       32.49 ms →       30.17 ms   (-7.13%) | 
  ├ sirius::Periodic_function|inner                                     |       10.86 ms →       10.19 ms   (-6.25%) |       2   →       2              |       21.73 ms →       20.37 ms   (-6.25%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.65 ms →       10.18 ms   (+5.50%) |       2   →       2              |       19.29 ms →       20.35 ms   (+5.50%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.65 ms →       10.18 ms   (+5.50%) |       2   →       2              |       19.29 ms →       20.35 ms   (+5.50%) | 
+ ├ sirius::Smooth_periodic_function|inner                              |       11.84 ms →       10.43 ms  (-11.90%) |       1   →       1              |       11.84 ms →       10.43 ms  (-11.90%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.42 ms   (-0.52%) |       1   →       1              |       10.47 ms →       10.42 ms   (-0.52%) | 
  └ sirius::finalize                                                    |      234.49 ms →      223.27 ms   (-4.78%) |       1   →       1              |      234.49 ms →      223.27 ms   (-4.78%) | 
  ====================================================================================================================================================================================================
```
