# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      134.50 s  →      132.53 s    (-1.47%) |       1   →       1              |      134.50 s  →      132.53 s    (-1.47%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.75 s    (-0.06%) |       1   →       1              |        2.75 s  →        2.75 s    (-0.06%) | 
  ├ sirius::Simulation_context::initialize                              |        2.86 s  →        2.93 s    (+2.50%) |       1   →       1              |        2.86 s  →        2.93 s    (+2.50%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      211.65 μs →      917.89 μs (+333.69%) |       1   →       1              |      211.65 μs →      917.89 μs (+333.69%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      135.61 ms →      179.04 ms  (+32.02%) |       1   →       1              |      135.61 ms →      179.04 ms  (+32.02%) | 
- │ │ ├ sirius::Atom_type::init                                         |       55.49 ms →       77.79 ms  (+40.19%) |       2   →       2              |      110.98 ms →      155.58 ms  (+40.19%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.56 ms →       23.37 ms   (-4.83%) |       1   →       1              |       24.56 ms →       23.37 ms   (-4.83%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.36 ms →        6.26 ms   (-1.57%) |       1   →       1              |        6.36 ms →        6.26 ms   (-1.57%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.16 ms →       17.07 ms   (-6.04%) |       1   →       1              |       18.16 ms →       17.07 ms   (-6.04%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.15 ms →       17.05 ms   (-6.05%) |       1   →       1              |       18.15 ms →       17.05 ms   (-6.05%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.16 ms   (+0.26%) |       1   →       1              |        4.15 ms →        4.16 ms   (+0.26%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.35 ms   (+1.35%) |       1   →       1              |        2.32 ms →        2.35 ms   (+1.35%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.21 μs →      105.95 μs   (+4.69%) |       1   →       1              |      101.21 μs →      105.95 μs   (+4.69%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.70 s    (+0.97%) |       1   →       1              |        2.68 s  →        2.70 s    (+0.97%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.69 ms →       10.72 ms   (+0.30%) |       1   →       1              |       10.69 ms →       10.72 ms   (+0.30%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.22 ms →        4.34 ms   (+2.95%) |       1   →       1              |        4.22 ms →        4.34 ms   (+2.95%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.43 ms →        6.34 ms   (-1.40%) |       1   →       1              |        6.43 ms →        6.34 ms   (-1.40%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.41 ms →        6.32 ms   (-1.39%) |       1   →       1              |        6.41 ms →        6.32 ms   (-1.39%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.88 ms →        3.83 ms   (-1.34%) |       1   →       1              |        3.88 ms →        3.83 ms   (-1.34%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.36 ms →        2.33 ms   (-1.55%) |       1   →       1              |        2.36 ms →        2.33 ms   (-1.55%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.28 μs →       99.37 μs   (-0.91%) |       1   →       1              |      100.28 μs →       99.37 μs   (-0.91%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       62.95 ms →       72.87 ms  (+15.75%) |       2   →       2              |      125.91 ms →      145.74 ms  (+15.75%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.20 ms   (+0.74%) |       2   →       2              |       10.32 ms →       10.39 ms   (+0.74%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.49 ms   (+0.41%) |       1   →       1              |        4.47 ms →        4.49 ms   (+0.41%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.10 ms →       22.03 ms   (-0.33%) |       2   →       2              |       44.20 ms →       44.06 ms   (-0.33%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.08 ms →       15.18 ms   (+0.67%) |       2   →       2              |       30.16 ms →       30.36 ms   (+0.67%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.85 ms →       19.74 ms   (-0.59%) |       4   →       4              |       79.41 ms →       78.94 ms   (-0.59%) | 
  │   ├ sddk::Gvec::init                                                |      175.03 ms →      172.67 ms   (-1.35%) |       2   →       2              |      350.06 ms →      345.34 ms   (-1.35%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.31 ms →      130.18 ms   (-1.61%) |       2   →       2              |      264.62 ms →      260.35 ms   (-1.61%) | 
  │   ├ sddk::Gvec_shells                                               |      175.99 ms →      164.38 ms   (-6.60%) |       1   →       1              |      175.99 ms →      164.38 ms   (-6.60%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.34 ms   (+2.15%) |       1   →       1              |        1.31 ms →        1.34 ms   (+2.15%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.75 ms →      292.63 ms   (-0.04%) |       2   →       2              |      585.49 ms →      585.27 ms   (-0.04%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.59 ms →       36.05 ms   (+1.28%) |       1   →       1              |       35.59 ms →       36.05 ms   (+1.28%) | 
- │ ├ sirius::K_point::K_point                                          |        2.19 μs →        2.46 μs  (+12.53%) |       4   →       4              |        8.75 μs →        9.85 μs  (+12.53%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.49 ms →       35.91 ms   (+1.20%) |       1   →       1              |       35.49 ms →       35.91 ms   (+1.20%) | 
  │   └ sirius::K_point::initialize                                     |       35.40 ms →       35.81 ms   (+1.14%) |       1   →       1              |       35.40 ms →       35.81 ms   (+1.14%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.98 ms →       18.28 ms   (+1.64%) |       1   →       1              |       17.98 ms →       18.28 ms   (+1.64%) | 
  │     │ └ sddk::Gvec::init                                            |        8.06 ms →        8.18 ms   (+1.48%) |       1   →       1              |        8.06 ms →        8.18 ms   (+1.48%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.77 μs →       10.39 μs  (+18.52%) |       1   →       1              |        8.77 μs →       10.39 μs  (+18.52%) | 
  │     └ sirius::K_point::update                                       |       12.59 ms →       12.58 ms   (-0.11%) |       1   →       1              |       12.59 ms →       12.58 ms   (-0.11%) | 
  │       └ sirius::Beta_projectors                                     |        6.32 ms →        6.19 ms   (-2.02%) |       1   →       1              |        6.32 ms →        6.19 ms   (-2.02%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.70 ms →        3.59 ms   (-3.13%) |       1   →       1              |        3.70 ms →        3.59 ms   (-3.13%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms →        5.39 ms   (+3.00%) |       2   →       2              |       10.46 ms →       10.78 ms   (+3.00%) | 
  ├ sirius::Potential                                                   |      158.75 ms →      153.18 ms   (-3.50%) |       1   →       1              |      158.75 ms →      153.18 ms   (-3.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.80 ms →        5.93 ms   (+2.33%) |       6   →       6              |       34.79 ms →       35.60 ms   (+2.33%) | 
  │ └ sirius::Potential::update                                         |      123.24 ms →      116.86 ms   (-5.18%) |       1   →       1              |      123.24 ms →      116.86 ms   (-5.18%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.54 ms →      116.14 ms   (-5.23%) |       1   →       1              |      122.54 ms →      116.14 ms   (-5.23%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.79 ms →      108.94 ms   (+0.13%) |       1   →       1              |      108.79 ms →      108.94 ms   (+0.13%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.86 ms →        6.29 ms  (-51.07%) |       1   →       1              |       12.86 ms →        6.29 ms  (-51.07%) | 
  ├ sirius::Density                                                     |      135.49 ms →      130.15 ms   (-3.95%) |       1   →       1              |      135.49 ms →      130.15 ms   (-3.95%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.27 ms →        5.20 ms   (-1.37%) |       2   →       2              |       10.54 ms →       10.40 ms   (-1.37%) | 
  │ └ sirius::Density::update                                           |      124.68 ms →      119.48 ms   (-4.17%) |       1   →       1              |      124.68 ms →      119.48 ms   (-4.17%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.28 ms →      119.04 ms   (-4.21%) |       1   →       1              |      124.28 ms →      119.04 ms   (-4.21%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.64 μs →      102.08 μs   (-0.55%) |       1   →       1              |      102.64 μs →      102.08 μs   (-0.55%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.86 ms →      112.23 ms   (+0.33%) |       1   →       1              |      111.86 ms →      112.23 ms   (+0.33%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.86 ms →        6.26 ms  (-47.23%) |       1   →       1              |       11.86 ms →        6.26 ms  (-47.23%) | 
  ├ sirius::Density::initial_density                                    |      178.33 ms →      168.38 ms   (-5.58%) |       1   →       1              |      178.33 ms →      168.38 ms   (-5.58%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.46 ms →      112.00 ms   (+1.40%) |       1   →       1              |      110.46 ms →      112.00 ms   (+1.40%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.78 ms →        7.09 ms  (-34.26%) |       2   →       2              |       21.57 ms →       14.18 ms  (-34.26%) | 
+ │ └ sirius::Periodic_function::integrate                              |       10.85 ms →        9.68 ms  (-10.76%) |       1   →       1              |       10.85 ms →        9.68 ms  (-10.76%) | 
  ├ sirius::Potential::generate                                         |      592.64 ms →      585.39 ms   (-1.22%) |       1   →       1              |      592.64 ms →      585.39 ms   (-1.22%) | 
  │ ├ sirius::Potential::poisson                                        |      137.43 ms →      125.33 ms   (-8.81%) |       1   →       1              |      137.43 ms →      125.33 ms   (-8.81%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.33 ms →        5.53 ms  (-71.37%) |       1   →       1              |       19.33 ms →        5.53 ms  (-71.37%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.30 ms →        9.95 ms   (-3.38%) |       1   →       1              |       10.30 ms →        9.95 ms   (-3.38%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.89 ms   (+0.08%) |       1   →       1              |        9.89 ms →        9.89 ms   (+0.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.89 ms   (+0.07%) |       1   →       1              |        9.88 ms →        9.89 ms   (+0.07%) | 
  │ ├ sirius::Periodic_function::add                                    |      555.82 μs →      550.55 μs   (-0.95%) |       2   →       2              |        1.11 ms →        1.10 ms   (-0.95%) | 
  │ ├ sirius::Potential::xc                                             |       54.87 ms →       55.05 ms   (+0.32%) |       1   →       1              |       54.87 ms →       55.05 ms   (+0.32%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.56 ms →       52.67 ms   (+0.22%) |       1   →       1              |       52.56 ms →       52.67 ms   (+0.22%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.63 ms →        5.75 ms   (+2.21%) |       2   →       2              |       11.26 ms →       11.51 ms   (+2.21%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.67 ms →        6.49 ms  (+14.40%) |       1   →       1              |        5.67 ms →        6.49 ms  (+14.40%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.91 ms →        8.14 ms  (+37.74%) |       1   →       1              |        5.91 ms →        8.14 ms  (+37.74%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.72 ms →       93.92 ms   (+1.29%) |       1   →       1              |       92.72 ms →       93.92 ms   (+1.29%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.22 ms →      300.40 ms   (+0.40%) |       1   →       1              |      299.22 ms →      300.40 ms   (+0.40%) | 
- ├ sirius::Hamiltonian0                                                |        8.40 ms →        9.93 ms  (+18.21%) |       1   →       1              |        8.40 ms →        9.93 ms  (+18.21%) | 
- │ ├ sirius::Local_operator                                            |        8.05 ms →        9.57 ms  (+18.91%) |       1   →       1              |        8.05 ms →        9.57 ms  (+18.91%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.82 ms →        4.77 ms   (-1.01%) |       1   →       1              |        4.82 ms →        4.77 ms   (-1.01%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.31 ms →        3.89 ms  (+67.95%) |       1   →       1              |        2.31 ms →        3.89 ms  (+67.95%) | 
  │ ├ sirius::Non_local_operator                                        |       63.76 μs →       62.39 μs   (-2.16%) |       2   →       2              |      127.52 μs →      124.77 μs   (-2.16%) | 
  │ ├ sirius::D_operator::initialize                                    |       93.04 μs →       95.53 μs   (+2.68%) |       1   →       1              |       93.04 μs →       95.53 μs   (+2.68%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.32 μs →       79.28 μs   (+6.67%) |       1   →       1              |       74.32 μs →       79.28 μs   (+6.67%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.88 s    (+0.92%) |       1   →       1              |        1.86 s  →        1.88 s    (+0.92%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.69 ms →       18.71 ms   (+0.14%) |       1   →       1              |       18.69 ms →       18.71 ms   (+0.14%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      183.98 μs →      194.89 μs   (+5.93%) |       1   →       1              |      183.98 μs →      194.89 μs   (+5.93%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.51 ms   (+0.08%) |       1   →       1              |       18.50 ms →       18.51 ms   (+0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.86 s    (+0.92%) |       1   →       1              |        1.84 s  →        1.86 s    (+0.92%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.28 ms →      129.30 ms   (+0.79%) |       4   →       4              |      513.11 ms →      517.19 ms   (+0.79%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.48 ms →       53.43 ms   (-0.09%) |       1   →       1              |       53.48 ms →       53.43 ms   (-0.09%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.88 ms →       21.94 ms   (+0.27%) |       1   →       1              |       21.88 ms →       21.94 ms   (+0.27%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      637.55 ms →      634.41 ms   (-0.49%) |       1   →       1              |      637.55 ms →      634.41 ms   (-0.49%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.89 ms →      297.48 ms   (-0.14%) |       1   →       1              |      297.89 ms →      297.48 ms   (-0.14%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        2.89 μs →        3.67 μs  (+27.13%) |       1   →       1              |        2.89 μs →        3.67 μs  (+27.13%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        1.98 μs →        2.46 μs  (+23.80%) |       1   →       1              |        1.98 μs →        2.46 μs  (+23.80%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      403.00 ns →      382.00 ns   (-5.21%) |       1   →       1              |      403.00 ns →      382.00 ns   (-5.21%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      450.00 ns →      509.00 ns  (+13.11%) |       1   →       1              |      450.00 ns →      509.00 ns  (+13.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.21 ms →        9.22 ms   (+0.01%) |       1   →       1              |        9.21 ms →        9.22 ms   (+0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.69 ms →      120.60 ms   (-0.89%) |       1   →       1              |      121.69 ms →      120.60 ms   (-0.89%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.36 ms →      103.54 ms   (-0.79%) |       2   →       2              |      208.72 ms →      207.07 ms   (-0.79%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.32 ms →       40.08 ms   (-0.59%) |       2   →       2              |       80.63 ms →       80.15 ms   (-0.59%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.77 ms →       39.54 ms   (-0.57%) |       2   →       2              |       79.53 ms →       79.08 ms   (-0.57%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.00 ns →       61.50 ns (+223.68%) |       2   →       2              |       38.00 ns →      123.00 ns (+223.68%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.30 ms →       39.06 ms   (-0.61%) |       2   →       2              |       78.60 ms →       78.13 ms   (-0.61%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       12.50 ns →       53.50 ns (+328.00%) |       2   →       2              |       25.00 ns →      107.00 ns (+328.00%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.09 ms →       56.95 ms   (-0.24%) |       1   →       1              |       57.09 ms →       56.95 ms   (-0.24%) | 
  │ │ └ sddk::wf_trans                                                  |       30.75 ms →       30.82 ms   (+0.21%) |       1   →       1              |       30.75 ms →       30.82 ms   (+0.21%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.75 ms →       30.81 ms   (+0.21%) |       1   →       1              |       30.75 ms →       30.81 ms   (+0.21%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      499.00 ns →      648.00 ns  (+29.86%) |       1   →       1              |      499.00 ns →      648.00 ns  (+29.86%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      124.87 s  →      122.85 s    (-1.62%) |       1   →       1              |      124.87 s  →      122.85 s    (-1.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.88 ms   (+1.64%) |      19   →      19              |      109.85 ms →      111.66 ms   (+1.64%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.79 s  →        4.54 s    (-5.27%) |      26   →      27     (+3.85%) |      124.49 s  →      122.46 s    (-1.63%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.66 ms →        5.27 ms  (+13.00%) |      26   →      27     (+3.85%) |      121.18 ms →      142.20 ms  (+17.35%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.30 ms →        4.90 ms  (+13.94%) |      26   →      27     (+3.85%) |      111.73 ms →      132.20 ms  (+18.32%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      954.07 μs →      962.03 μs   (+0.83%) |      26   →      27     (+3.85%) |       24.81 ms →       25.97 ms   (+4.71%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.45 ms →        3.03 ms  (+23.82%) |      26   →      27     (+3.85%) |       63.71 ms →       81.92 ms  (+28.58%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.83 μs →       64.61 μs   (-0.33%) |      52   →      54     (+3.85%) |        3.37 ms →        3.49 ms   (+3.50%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.56 μs →       90.11 μs   (+4.10%) |      26   →      27     (+3.85%) |        2.25 ms →        2.43 ms   (+8.10%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.33 μs →       80.00 μs   (+3.45%) |      26   →      27     (+3.85%) |        2.01 ms →        2.16 ms   (+7.43%) | 
  │ │ ├ sirius::Band::solve                                             |        2.81 s  →        2.56 s    (-8.79%) |      26   →      27     (+3.85%) |       73.00 s  →       69.15 s    (-5.28%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      153.82 μs →      157.13 μs   (+2.15%) |      26   →      27     (+3.85%) |        4.00 ms →        4.24 ms   (+6.08%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      147.21 μs →      149.02 μs   (+1.23%) |      26   →      27     (+3.85%) |        3.83 ms →        4.02 ms   (+5.13%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.77 μs →        6.04 μs  (+26.77%) |      26   →      27     (+3.85%) |      123.95 μs →      163.18 μs  (+31.65%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.61 s  →        2.44 s    (-6.64%) |      26   →      27     (+3.85%) |       67.91 s  →       65.85 s    (-3.04%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       94.63 ms →       93.87 ms   (-0.80%) |      26   →      27     (+3.85%) |        2.46 s  →        2.53 s    (+3.02%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.62 ms →        7.39 ms   (-2.97%) |     156   →     162     (+3.85%) |        1.19 s  →        1.20 s    (+0.76%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.93 ms →        5.86 ms   (-1.18%) |      26   →      27     (+3.85%) |      154.09 ms →      158.14 ms   (+2.63%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      345.85 μs →      348.56 μs   (+0.79%) |      26   →      27     (+3.85%) |        8.99 ms →        9.41 ms   (+4.66%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.29 ms   (-1.15%) |      52   →      54     (+3.85%) |      120.32 ms →      123.50 ms   (+2.65%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.48 s  →        2.30 s    (-6.97%) |      26   →      27     (+3.85%) |       64.37 s  →       62.19 s    (-3.39%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      130.26 ms →      132.33 ms   (+1.59%) |     271   →     279     (+2.95%) |       35.30 s  →       36.92 s    (+4.59%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       52.11 ms →       53.52 ms   (+2.70%) |     271   →     279     (+2.95%) |       14.12 s  →       14.93 s    (+5.73%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.89 μs →        2.21 μs  (+17.31%) |     271   →     279     (+2.95%) |      511.27 μs →      617.49 μs  (+20.78%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.62 μs →        1.83 μs  (+13.25%) |     271   →     279     (+2.95%) |      438.15 μs →      510.86 μs  (+16.59%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      350.09 ns →      413.19 ns  (+18.02%) |     271   →     279     (+2.95%) |       94.87 μs →      115.28 μs  (+21.51%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      391.92 ns →      565.70 ns  (+44.34%) |     271   →     279     (+2.95%) |      106.21 μs →      157.83 μs  (+48.60%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.43 ms →        7.43 ms   (+0.06%) |     271   →     279     (+2.95%) |        2.01 s  →        2.07 s    (+3.01%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.94 ms →       24.20 ms   (+1.11%) |     271   →     279     (+2.95%) |        6.49 s  →        6.75 s    (+4.09%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.38 ms →       23.58 ms   (+0.84%) |     542   →     558     (+2.95%) |       12.67 s  →       13.16 s    (+3.82%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.91 ms →       34.30 ms   (-1.75%) |     271   →     279     (+2.95%) |        9.46 s  →        9.57 s    (+1.15%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.06 ms →        5.97 ms   (-1.45%) |     516   →     531     (+2.91%) |        3.12 s  →        3.17 s    (+1.42%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       66.25 ns →       54.73 ns  (-17.39%) |     516   →     531     (+2.91%) |       34.18 μs →       29.06 μs  (-14.99%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.95 ms →        4.86 ms   (-1.74%) |     516   →     531     (+2.91%) |        2.55 s  →        2.58 s    (+1.11%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.17 ns →       48.98 ns   (-6.12%) |     516   →     531     (+2.91%) |       26.92 μs →       26.01 μs   (-3.40%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      628.39 μs →      625.17 μs   (-0.51%) |     271   →     279     (+2.95%) |      170.29 ms →      174.42 ms   (+2.43%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.76 ms →        9.82 ms   (+0.59%) |     271   →     279     (+2.95%) |        2.65 s  →        2.74 s    (+3.55%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.36 ms →       13.83 ms   (-3.71%) |     245   →     252     (+2.86%) |        3.52 s  →        3.48 s    (-0.96%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.79 ms →        4.61 ms   (-3.71%) |     735   →     756     (+2.86%) |        3.52 s  →        3.48 s    (-0.96%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.50 ms →        9.87 ms   (-6.02%) |     271   →     279     (+2.95%) |        2.85 s  →        2.75 s    (-3.25%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.23 ms →        9.68 ms   (-5.42%) |     271   →     279     (+2.95%) |        2.77 s  →        2.70 s    (-2.63%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       45.84 ns →       44.13 ns   (-3.72%) |     271   →     279     (+2.95%) |       12.42 μs →       12.31 μs   (-0.88%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.12 ms →        8.57 ms   (-6.07%) |     271   →     279     (+2.95%) |        2.47 s  →        2.39 s    (-3.30%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       69.65 ns →       34.56 ns  (-50.39%) |     271   →     279     (+2.95%) |       18.87 μs →        9.64 μs  (-48.92%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.90 ms →       17.69 ms  (-47.82%) |     271   →     279     (+2.95%) |        9.19 s  →        4.94 s   (-46.28%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.72 ms →       12.62 ms   (-8.02%) |     262   →     267     (+1.91%) |        3.60 s  →        3.37 s    (-6.26%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       12.40 ms →       11.07 ms  (-10.74%) |     252   →     260     (+3.17%) |        3.13 s  →        2.88 s    (-7.90%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.20 ms →        5.53 ms  (-10.74%) |     504   →     520     (+3.17%) |        3.12 s  →        2.88 s    (-7.91%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.62 ms →        1.64 ms   (+1.77%) |     252   →     260     (+3.17%) |      407.34 ms →      427.70 ms   (+5.00%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.94 ms →       48.75 ms  (-34.96%) |      53   →      95    (+79.25%) |        3.97 s  →        4.63 s   (+16.59%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.42 ms →       28.15 ms  (-43.05%) |      80   →     163   (+103.75%) |        3.95 s  →        4.59 s   (+16.05%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.95 ms →       19.86 ms  (-46.25%) |     107   →     231   (+115.89%) |        3.95 s  →        4.59 s   (+16.04%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      517.81 ns →      459.93 ns  (-11.18%) |      26   →      27     (+3.85%) |       13.46 μs →       12.42 μs   (-7.76%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       61.11 μs →      110.42 μs  (+80.70%) |      26   →      27     (+3.85%) |        1.59 ms →        2.98 ms  (+87.65%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      610.30 μs →      600.06 μs   (-1.68%) |      26   →      27     (+3.85%) |       15.87 ms →       16.20 ms   (+2.10%) | 
  │ │ ├ sirius::Density::generate                                       |      779.01 ms →      778.87 ms   (-0.02%) |      26   →      27     (+3.85%) |       20.25 s  →       21.03 s    (+3.83%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      403.50 ms →      407.86 ms   (+1.08%) |      26   →      27     (+3.85%) |       10.49 s  →       11.01 s    (+4.97%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.55 μs →        8.60 μs   (+0.64%) |      26   →      27     (+3.85%) |      222.22 μs →      232.23 μs   (+4.51%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.00 μs →        7.77 μs   (-2.88%) |      26   →      27     (+3.85%) |      208.04 μs →      209.83 μs   (+0.86%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.65 ms →      100.30 ms   (-0.34%) |      26   →      27     (+3.85%) |        2.62 s  →        2.71 s    (+3.49%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.38 μs →        8.19 μs  (+10.96%) |      26   →      27     (+3.85%) |      191.86 μs →      221.08 μs  (+15.23%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.02%) |      26   →      27     (+3.85%) |      185.07 ms →      192.15 ms   (+3.82%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.61 ms →       91.27 ms   (-0.37%) |      26   →      27     (+3.85%) |        2.38 s  →        2.46 s    (+3.47%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      653.46 ns →      557.48 ns  (-14.69%) |      26   →      27     (+3.85%) |       16.99 μs →       15.05 μs  (-11.41%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.71 ms →      165.11 ms   (+0.85%) |      26   →      27     (+3.85%) |        4.26 s  →        4.46 s    (+4.73%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.33%) |      26   →      27     (+3.85%) |       42.72 ms →       44.22 ms   (+3.50%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.25 ms →       88.22 ms   (-0.03%) |      26   →      27     (+3.85%) |        2.29 s  →        2.38 s    (+3.82%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.01 ms →       87.98 ms   (-0.03%) |      26   →      27     (+3.85%) |        2.29 s  →        2.38 s    (+3.81%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.34 ms →      277.39 ms   (+0.38%) |      26   →      27     (+3.85%) |        7.18 s  →        7.49 s    (+4.24%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.34 ms →      277.39 ms   (+0.38%) |      26   →      27     (+3.85%) |        7.18 s  →        7.49 s    (+4.24%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.16 ms →       24.98 ms   (+3.37%) |      26   →      27     (+3.85%) |      628.19 ms →      674.34 ms   (+7.35%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.04 ms →      227.65 ms   (-0.17%) |      26   →      27     (+3.85%) |        5.93 s  →        6.15 s    (+3.67%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.94 ms →       23.58 ms   (+2.78%) |      26   →      27     (+3.85%) |      596.50 ms →      636.64 ms   (+6.73%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       89.67 ms →       80.53 ms  (-10.19%) |      26   →      27     (+3.85%) |        2.33 s  →        2.17 s    (-6.73%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.91 ms →        9.49 ms  (+60.54%) |      26   →      27     (+3.85%) |      153.67 ms →      256.19 ms  (+66.71%) | 
  │ │ ├ sirius::Density::mix                                            |      218.35 ms →      215.00 ms   (-1.53%) |      26   →      27     (+3.85%) |        5.68 s  →        5.81 s    (+2.26%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      917.91 μs →      950.67 μs   (+3.57%) |      26   →      27     (+3.85%) |       23.87 ms →       25.67 ms   (+7.55%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.67 ms →       10.27 ms   (-3.70%) |     334   →     349     (+4.49%) |        3.56 s  →        3.59 s    (+0.63%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.38 ms →        9.91 ms   (-4.47%) |     334   →     349     (+4.49%) |        3.47 s  →        3.46 s    (-0.18%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.38 ms →        9.91 ms   (-4.47%) |     334   →     349     (+4.49%) |        3.47 s  →        3.46 s    (-0.18%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.55 ms →        8.08 ms  (+23.49%) |      26   →      27     (+3.85%) |      170.19 ms →      218.26 ms  (+28.24%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.70 ms →        7.26 ms  (+27.42%) |      26   →      27     (+3.85%) |      148.21 ms →      196.10 ms  (+32.32%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.02 ms →      570.88 ms   (-1.24%) |      26   →      27     (+3.85%) |       15.03 s  →       15.41 s    (+2.56%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.18 ms →      126.64 ms   (-7.69%) |      26   →      27     (+3.85%) |        3.57 s  →        3.42 s    (-4.14%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.37 ms →        6.42 ms  (-65.06%) |      26   →      27     (+3.85%) |      477.52 ms →      173.25 ms  (-63.72%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.27 ms →       10.31 ms   (+0.44%) |      26   →      27     (+3.85%) |      266.94 ms →      278.42 ms   (+4.30%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.04 ms →        9.92 ms   (-1.16%) |      26   →      27     (+3.85%) |      261.01 ms →      267.90 ms   (+2.64%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.04 ms →        9.92 ms   (-1.16%) |      26   →      27     (+3.85%) |      261.00 ms →      267.89 ms   (+2.64%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      554.50 μs →      553.34 μs   (-0.21%) |      52   →      54     (+3.85%) |       28.83 ms →       29.88 ms   (+3.63%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.59 ms →       50.22 ms   (+3.35%) |      26   →      27     (+3.85%) |        1.26 s  →        1.36 s    (+7.33%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.23 ms →       47.90 ms   (+3.62%) |      26   →      27     (+3.85%) |        1.20 s  →        1.29 s    (+7.60%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.00 ms   (-1.24%) |      52   →      54     (+3.85%) |      158.21 ms →      162.26 ms   (+2.56%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.24 ms →        6.90 ms  (+31.61%) |      26   →      27     (+3.85%) |      136.23 ms →      186.20 ms  (+36.68%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.53 ms →        7.06 ms   (+8.16%) |      26   →      27     (+3.85%) |      169.71 ms →      190.63 ms  (+12.32%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.90 ms →       91.70 ms   (+0.88%) |      26   →      27     (+3.85%) |        2.36 s  →        2.48 s    (+4.76%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.39 ms →      292.83 ms   (+0.15%) |      26   →      27     (+3.85%) |        7.60 s  →        7.91 s    (+4.00%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.98 ms →      284.31 ms   (+1.19%) |      26   →      27     (+3.85%) |        7.31 s  →        7.68 s    (+5.08%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.97 ms →      284.31 ms   (+1.19%) |      26   →      27     (+3.85%) |        7.31 s  →        7.68 s    (+5.08%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.29 ms →       28.23 ms   (+3.47%) |      26   →      27     (+3.85%) |      709.44 ms →      762.28 ms   (+7.45%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.10 ms →      227.74 ms   (+0.72%) |      26   →      27     (+3.85%) |        5.88 s  →        6.15 s    (+4.60%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.79 ms →       24.52 ms   (+3.05%) |      26   →      27     (+3.85%) |      618.60 ms →      661.97 ms   (+7.01%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.63 ms →        7.06 ms  (+25.40%) |      26   →      27     (+3.85%) |      146.31 ms →      190.53 ms  (+30.22%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.03 ms →       10.13 ms   (+1.02%) |     182   →     189     (+3.85%) |        1.83 s  →        1.91 s    (+4.90%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.74 ms →        9.71 ms   (-0.27%) |     182   →     189     (+3.85%) |        1.77 s  →        1.84 s    (+3.56%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.74 ms →        9.71 ms   (-0.27%) |     182   →     189     (+3.85%) |        1.77 s  →        1.83 s    (+3.56%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.82 ms →       10.45 ms   (-3.41%) |      78   →      81     (+3.85%) |      844.02 ms →      846.60 ms   (+0.30%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.54 ms →       10.08 ms   (-4.41%) |      78   →      81     (+3.85%) |      822.12 ms →      816.11 ms   (-0.73%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.90 ms →        9.90 ms   (-0.01%) |      26   →      27     (+3.85%) |      257.52 ms →      267.39 ms   (+3.84%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      111.70 μs →      184.51 μs  (+65.18%) |      26   →      27     (+3.85%) |        2.90 ms →        4.98 ms  (+71.53%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.93 μs →      179.84 μs  (+68.18%) |      26   →      27     (+3.85%) |        2.78 ms →        4.86 ms  (+74.65%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.04 ms →        5.35 ms   (+6.09%) |       2   →       2              |       10.09 ms →       10.70 ms   (+6.09%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.11 ms →       10.13 ms   (+0.26%) |       6   →       6              |       60.63 ms →       60.79 ms   (+0.26%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.85 ms →       10.07 ms   (+2.16%) |       6   →       6              |       59.13 ms →       60.41 ms   (+2.16%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.85 ms →       10.07 ms   (+2.16%) |       6   →       6              |       59.13 ms →       60.41 ms   (+2.16%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.69 ms →       10.48 ms   (-1.96%) |       3   →       3              |       32.08 ms →       31.45 ms   (-1.96%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.64 ms →       10.41 ms   (-2.14%) |       3   →       3              |       31.91 ms →       31.23 ms   (-2.14%) | 
  ├ sirius::Periodic_function|inner                                     |       10.02 ms →       10.15 ms   (+1.31%) |       2   →       2              |       20.04 ms →       20.30 ms   (+1.31%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.01 ms →       10.13 ms   (+1.18%) |       2   →       2              |       20.02 ms →       20.25 ms   (+1.18%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →       10.13 ms   (+1.18%) |       2   →       2              |       20.02 ms →       20.25 ms   (+1.18%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.80 ms →       10.96 ms   (+1.56%) |       1   →       1              |       10.80 ms →       10.96 ms   (+1.56%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.79 ms →       10.45 ms   (-3.11%) |       1   →       1              |       10.79 ms →       10.45 ms   (-3.11%) | 
  └ sirius::finalize                                                    |      222.15 ms →      202.28 ms   (-8.94%) |       1   →       1              |      222.15 ms →      202.28 ms   (-8.94%) | 
  ====================================================================================================================================================================================================
```
