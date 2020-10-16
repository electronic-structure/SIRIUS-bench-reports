# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      250.33 s  →      218.75 s   (-12.62%) |       1   →       1              |      250.33 s  →      218.75 s   (-12.62%) | 
  ├ sirius::initialize                                                  |        2.74 s  →        2.68 s    (-2.09%) |       1   →       1              |        2.74 s  →        2.68 s    (-2.09%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        2.99 s    (-0.00%) |       1   →       1              |        2.99 s  →        2.99 s    (-0.00%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       46.51 ms →       57.95 ms  (+24.60%) |       1   →       1              |       46.51 ms →       57.95 ms  (+24.60%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      166.72 ms →      185.47 ms  (+11.25%) |       1   →       1              |      166.72 ms →      185.47 ms  (+11.25%) | 
- │ │ ├ sirius::Atom_type::init                                         |       71.25 ms →       80.58 ms  (+13.10%) |       2   →       2              |      142.50 ms →      161.17 ms  (+13.10%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.14 ms →       24.23 ms   (+0.35%) |       1   →       1              |       24.14 ms →       24.23 ms   (+0.35%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.17 ms →        6.38 ms   (+3.28%) |       1   →       1              |        6.17 ms →        6.38 ms   (+3.28%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.93 ms →       17.81 ms   (-0.70%) |       1   →       1              |       17.93 ms →       17.81 ms   (-0.70%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.91 ms →       17.79 ms   (-0.69%) |       1   →       1              |       17.91 ms →       17.79 ms   (-0.69%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.18 ms   (+0.68%) |       1   →       1              |        4.15 ms →        4.18 ms   (+0.68%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.33 ms   (-0.54%) |       1   →       1              |        2.35 ms →        2.33 ms   (-0.54%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.93 μs →      102.26 μs   (-2.55%) |       1   →       1              |      104.93 μs →      102.26 μs   (-2.55%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.69 s    (-1.41%) |       1   →       1              |        2.73 s  →        2.69 s    (-1.41%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.67 ms →       11.10 ms   (+3.98%) |       1   →       1              |       10.67 ms →       11.10 ms   (+3.98%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.25 ms →        4.47 ms   (+5.03%) |       1   →       1              |        4.25 ms →        4.47 ms   (+5.03%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.60 ms   (+3.26%) |       1   →       1              |        6.39 ms →        6.60 ms   (+3.26%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.58 ms   (+3.28%) |       1   →       1              |        6.37 ms →        6.58 ms   (+3.28%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        4.08 ms   (+5.13%) |       1   →       1              |        3.89 ms →        4.08 ms   (+5.13%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.32 ms   (+0.27%) |       1   →       1              |        2.31 ms →        2.32 ms   (+0.27%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.79 μs →       99.41 μs   (-4.22%) |       1   →       1              |      103.79 μs →       99.41 μs   (-4.22%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.80 ms →       62.64 ms   (-1.83%) |       2   →       2              |      127.61 ms →      125.27 ms   (-1.83%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.16 ms   (+0.07%) |       2   →       2              |       10.31 ms →       10.32 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.49 ms   (+0.36%) |       1   →       1              |        4.47 ms →        4.49 ms   (+0.36%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.84 ms →       21.75 ms   (-0.44%) |       2   →       2              |       43.69 ms →       43.49 ms   (-0.44%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.06 ms →       14.81 ms   (-1.67%) |       2   →       2              |       30.12 ms →       29.62 ms   (-1.67%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.84 ms →       19.60 ms   (-1.21%) |       4   →       4              |       79.37 ms →       78.41 ms   (-1.21%) | 
  │   ├ sddk::Gvec::init                                                |      189.43 ms →      175.50 ms   (-7.35%) |       2   →       2              |      378.86 ms →      351.00 ms   (-7.35%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      142.36 ms →      131.14 ms   (-7.88%) |       2   →       2              |      284.72 ms →      262.28 ms   (-7.88%) | 
  │   ├ sddk::Gvec_shells                                               |      183.59 ms →      177.50 ms   (-3.32%) |       1   →       1              |      183.59 ms →      177.50 ms   (-3.32%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.95%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.95%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.03 ms →      295.46 ms   (+0.48%) |       2   →       2              |      588.07 ms →      590.91 ms   (+0.48%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.20 ms →       75.63 ms   (-0.75%) |       1   →       1              |       76.20 ms →       75.63 ms   (-0.75%) | 
  │ ├ sirius::K_point::K_point                                          |        2.79 μs →        2.70 μs   (-3.11%) |       4   →       4              |       11.17 μs →       10.82 μs   (-3.11%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.10 ms →       75.53 ms   (-0.75%) |       1   →       1              |       76.10 ms →       75.53 ms   (-0.75%) | 
  │   └ sirius::K_point::initialize                                     |       19.01 ms →       18.86 ms   (-0.80%) |       4   →       4              |       76.05 ms →       75.44 ms   (-0.80%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.44 ms →       14.16 ms   (-1.89%) |       4   →       4              |       57.74 ms →       56.65 ms   (-1.89%) | 
  │     │ └ sddk::Gvec::init                                            |        3.89 ms →        3.96 ms   (+1.85%) |       4   →       4              |       15.54 ms →       15.83 ms   (+1.85%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.25 μs →        9.24 μs   (-0.15%) |       4   →       4              |       37.01 μs →       36.95 μs   (-0.15%) | 
  │     └ sirius::K_point::update                                       |        3.27 ms →        3.37 ms   (+2.85%) |       4   →       4              |       13.09 ms →       13.47 ms   (+2.85%) | 
  │       └ sirius::Beta_projectors                                     |        1.75 ms →        1.79 ms   (+2.63%) |       4   →       4              |        6.99 ms →        7.17 ms   (+2.63%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      914.66 μs →      935.23 μs   (+2.25%) |       4   →       4              |        3.66 ms →        3.74 ms   (+2.25%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.24 ms   (-1.30%) |       2   →       2              |       10.62 ms →       10.48 ms   (-1.30%) | 
  ├ sirius::Potential                                                   |      154.33 ms →      158.73 ms   (+2.86%) |       1   →       1              |      154.33 ms →      158.73 ms   (+2.86%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.95 ms →        5.81 ms   (-2.46%) |       6   →       6              |       35.73 ms →       34.85 ms   (-2.46%) | 
  │ └ sirius::Potential::update                                         |      117.81 ms →      123.15 ms   (+4.54%) |       1   →       1              |      117.81 ms →      123.15 ms   (+4.54%) | 
  │   └ sirius::Potential::generate_local_potential                     |      117.02 ms →      122.43 ms   (+4.62%) |       1   →       1              |      117.02 ms →      122.43 ms   (+4.62%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      107.25 ms →      106.95 ms   (-0.28%) |       1   →       1              |      107.25 ms →      106.95 ms   (-0.28%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        8.86 ms →       14.57 ms  (+64.56%) |       1   →       1              |        8.86 ms →       14.57 ms  (+64.56%) | 
  ├ sirius::Density                                                     |      128.03 ms →      134.23 ms   (+4.84%) |       1   →       1              |      128.03 ms →      134.23 ms   (+4.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms →        5.10 ms   (-2.65%) |       2   →       2              |       10.48 ms →       10.20 ms   (-2.65%) | 
  │ └ sirius::Density::update                                           |      117.28 ms →      123.76 ms   (+5.53%) |       1   →       1              |      117.28 ms →      123.76 ms   (+5.53%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      116.85 ms →      123.29 ms   (+5.51%) |       1   →       1              |      116.85 ms →      123.29 ms   (+5.51%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.00 μs →      110.63 μs   (+5.36%) |       1   →       1              |      105.00 μs →      110.63 μs   (+5.36%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.24 ms →      109.35 ms   (-0.81%) |       1   →       1              |      110.24 ms →      109.35 ms   (-0.81%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.03 ms →       13.36 ms (+121.66%) |       1   →       1              |        6.03 ms →       13.36 ms (+121.66%) | 
  ├ sirius::Density::initial_density                                    |      166.36 ms →      173.81 ms   (+4.47%) |       1   →       1              |      166.36 ms →      173.81 ms   (+4.47%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      109.85 ms →      108.49 ms   (-1.25%) |       1   →       1              |      109.85 ms →      108.49 ms   (-1.25%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.56 ms →       11.60 ms (+108.77%) |       2   →       2              |       11.12 ms →       23.21 ms (+108.77%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.54 ms →        9.96 ms   (-5.57%) |       1   →       1              |       10.54 ms →        9.96 ms   (-5.57%) | 
  ├ sirius::Potential::generate                                         |      622.27 ms →      592.99 ms   (-4.70%) |       1   →       1              |      622.27 ms →      592.99 ms   (-4.70%) | 
  │ ├ sirius::Potential::poisson                                        |      125.48 ms →      136.22 ms   (+8.56%) |       1   →       1              |      125.48 ms →      136.22 ms   (+8.56%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.42 ms →       17.27 ms (+218.71%) |       1   →       1              |        5.42 ms →       17.27 ms (+218.71%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.23 ms →       10.26 ms   (+0.26%) |       1   →       1              |       10.23 ms →       10.26 ms   (+0.26%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.95 ms →        9.81 ms   (-1.40%) |       1   →       1              |        9.95 ms →        9.81 ms   (-1.40%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.95 ms →        9.81 ms   (-1.40%) |       1   →       1              |        9.95 ms →        9.81 ms   (-1.40%) | 
  │ ├ sirius::Periodic_function::add                                    |      559.81 μs →      551.14 μs   (-1.55%) |       2   →       2              |        1.12 ms →        1.10 ms   (-1.55%) | 
  │ ├ sirius::Potential::xc                                             |       54.00 ms →       54.23 ms   (+0.42%) |       1   →       1              |       54.00 ms →       54.23 ms   (+0.42%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.54 ms →       51.89 ms   (+0.68%) |       1   →       1              |       51.54 ms →       51.89 ms   (+0.68%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.75 ms →        5.63 ms   (-2.09%) |       2   →       2              |       11.51 ms →       11.27 ms   (-2.09%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.24 ms →        5.23 ms   (-0.29%) |       1   →       1              |        5.24 ms →        5.23 ms   (-0.29%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.91 ms →        5.85 ms   (-0.90%) |       1   →       1              |        5.91 ms →        5.85 ms   (-0.90%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.54 ms →       93.50 ms   (-0.05%) |       1   →       1              |       93.54 ms →       93.50 ms   (-0.05%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      340.82 ms →      300.74 ms  (-11.76%) |       1   →       1              |      340.82 ms →      300.74 ms  (-11.76%) | 
  ├ sirius::Hamiltonian0                                                |        8.42 ms →        8.40 ms   (-0.17%) |       1   →       1              |        8.42 ms →        8.40 ms   (-0.17%) | 
  │ ├ sirius::Local_operator                                            |        8.07 ms →        8.06 ms   (-0.15%) |       1   →       1              |        8.07 ms →        8.06 ms   (-0.15%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.77 ms   (-0.09%) |       1   →       1              |        4.77 ms →        4.77 ms   (-0.09%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        2.36 ms   (-0.84%) |       1   →       1              |        2.38 ms →        2.36 ms   (-0.84%) | 
  │ ├ sirius::Non_local_operator                                        |       63.09 μs →       62.56 μs   (-0.84%) |       2   →       2              |      126.19 μs →      125.13 μs   (-0.84%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.46 μs →       95.26 μs   (+0.84%) |       1   →       1              |       94.46 μs →       95.26 μs   (+0.84%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.95 μs →       68.99 μs   (-1.37%) |       1   →       1              |       69.95 μs →       68.99 μs   (-1.37%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.13 s  →        3.09 s    (-1.33%) |       1   →       1              |        3.13 s  →        3.09 s    (-1.33%) | 
  │ ├ sirius::Hamiltonian_k                                             |      381.30 μs →      375.50 μs   (-1.52%) |       4   →       4              |        1.53 ms →        1.50 ms   (-1.52%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      375.51 μs →      370.08 μs   (-1.44%) |       4   →       4              |        1.50 ms →        1.48 ms   (-1.44%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.85 μs →        3.53 μs   (-8.35%) |       4   →       4              |       15.39 μs →       14.11 μs   (-8.35%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      782.25 ms →      771.83 ms   (-1.33%) |       4   →       4              |        3.13 s  →        3.09 s    (-1.33%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.74 ms →       32.60 ms   (-0.44%) |      16   →      16              |      523.85 ms →      521.53 ms   (-0.44%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.42 ms →       14.54 ms   (+0.83%) |       4   →       4              |       57.68 ms →       58.16 ms   (+0.83%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.37 ms →        5.34 ms   (-0.49%) |       4   →       4              |       21.46 ms →       21.36 ms   (-0.49%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      358.51 ms →      354.52 ms   (-1.11%) |       4   →       4              |        1.43 s  →        1.42 s    (-1.11%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      260.61 ms →      258.18 ms   (-0.93%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.93%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.53 ms →       62.92 ms   (-2.49%) |       4   →       4              |      258.12 ms →      251.69 ms   (-2.49%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.66 ms →       16.53 ms   (-0.76%) |       4   →       4              |       66.64 ms →       66.13 ms   (-0.76%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.66 ms →       16.53 ms   (-0.76%) |       4   →       4              |       66.63 ms →       66.12 ms   (-0.76%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.53 ms →       39.86 ms   (-4.02%) |       4   →       4              |      166.12 ms →      159.44 ms   (-4.02%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.40 ms →       16.50 ms   (+0.60%) |       4   →       4              |       65.60 ms →       66.00 ms   (+0.60%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.40 ms →       16.50 ms   (+0.61%) |       4   →       4              |       65.59 ms →       65.99 ms   (+0.61%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.72 ms →       53.60 ms   (-2.04%) |       4   →       4              |      218.86 ms →      214.40 ms   (-2.04%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.70 ms →       35.55 ms   (-3.14%) |       4   →       4              |      146.80 ms →      142.19 ms   (-3.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.93 ms   (-0.73%) |       4   →       4              |        7.79 ms →        7.73 ms   (-0.73%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.69 ms →       40.05 ms   (-3.93%) |       4   →       4              |      166.76 ms →      160.21 ms   (-3.93%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.56 ms →        6.91 ms  (-19.21%) |       4   →       4              |       34.22 ms →       27.65 ms  (-19.21%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.11 ms →       27.16 ms   (+0.17%) |       8   →       8              |      216.89 ms →      217.26 ms   (+0.17%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.08 ms →       14.85 ms   (-1.53%) |       8   →       8              |      120.62 ms →      118.77 ms   (-1.53%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.03 ms →       14.80 ms   (-1.54%) |       8   →       8              |      120.28 ms →      118.43 ms   (-1.54%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       30.00 ns →       28.75 ns   (-4.17%) |       8   →       8              |      240.00 ns →      230.00 ns   (-4.17%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.86 ms →       14.63 ms   (-1.56%) |       8   →       8              |      118.85 ms →      117.00 ms   (-1.56%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       26.25 ns →       37.00 ns  (+40.95%) |       8   →       8              |      210.00 ns →      296.00 ns  (+40.95%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      124.87 ms →      118.58 ms   (-5.04%) |       4   →       4              |      499.49 ms →      474.30 ms   (-5.04%) | 
  │ │ └ sddk::wf_trans                                                  |       23.60 ms →       23.63 ms   (+0.13%) |       4   →       4              |       94.41 ms →       94.53 ms   (+0.13%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.49 ms →       23.35 ms   (-0.60%) |       4   →       4              |       93.96 ms →       93.40 ms   (-0.60%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      469.25 ns →      333.50 ns  (-28.93%) |       4   →       4              |        1.88 μs →        1.33 μs  (-28.93%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      239.42 s  →      207.96 s   (-13.14%) |       1   →       1              |      239.42 s  →      207.96 s   (-13.14%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.73 ms   (-1.35%) |      19   →      19              |      110.30 ms →      108.81 ms   (-1.35%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        9.19 s  →        7.98 s   (-13.14%) |      26   →      26              |      238.96 s  →      207.56 s   (-13.14%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.65 ms →        4.51 ms   (-3.07%) |      26   →      26              |      120.93 ms →      117.22 ms   (-3.07%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.29 ms →        4.15 ms   (-3.26%) |      26   →      26              |      111.60 ms →      107.97 ms   (-3.26%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      962.48 μs →      982.18 μs   (+2.05%) |      26   →      26              |       25.02 ms →       25.54 ms   (+2.05%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.44 ms →        2.28 ms   (-6.37%) |      26   →      26              |       63.44 ms →       59.40 ms   (-6.37%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.75 μs →       64.54 μs   (-0.32%) |      52   →      52              |        3.37 ms →        3.36 ms   (-0.32%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.37 μs →       92.81 μs   (-1.66%) |      26   →      26              |        2.45 ms →        2.41 ms   (-1.66%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.02 μs →       65.59 μs   (-0.66%) |      26   →      26              |        1.72 ms →        1.71 ms   (-0.66%) | 
+ │ │ ├ sirius::Band::solve                                             |        7.08 s  →        5.89 s   (-16.83%) |      26   →      26              |      183.99 s  →      153.03 s   (-16.83%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      331.76 μs →      323.62 μs   (-2.45%) |     104   →     104              |       34.50 ms →       33.66 ms   (-2.45%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      326.37 μs →      318.53 μs   (-2.40%) |     104   →     104              |       33.94 ms →       33.13 ms   (-2.40%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.87 μs →        3.71 μs   (-4.34%) |     104   →     104              |      402.84 μs →      385.37 μs   (-4.34%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.77 s  →        1.47 s   (-16.83%) |     104   →     104              |      183.96 s  →      152.99 s   (-16.83%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.99 ms →       12.03 ms   (+0.35%) |     104   →     104              |        1.25 s  →        1.25 s    (+0.35%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      700.55 ns →      719.50 ns   (+2.70%) |     624   →     624              |      437.14 μs →      448.96 μs   (+2.70%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.84 ms   (+0.37%) |     104   →     104              |      190.36 ms →      191.07 ms   (+0.37%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      354.34 μs →      354.04 μs   (-0.08%) |     104   →     104              |       36.85 ms →       36.82 ms   (-0.08%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      549.06 μs →      548.71 μs   (-0.06%) |     208   →     208              |      114.20 ms →      114.13 ms   (-0.06%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.75 s  →        1.45 s   (-17.06%) |     104   →     104              |      181.58 s  →      150.61 s   (-17.06%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.23 ms →       68.39 ms   (+0.24%) |     941   →     954     (+1.38%) |       64.20 s  →       65.24 s    (+1.62%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.47 ms →       43.70 ms   (+0.55%) |     941   →     954     (+1.38%) |       40.90 s  →       41.69 s    (+1.94%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.60 ms →        8.65 ms   (+0.57%) |     941   →     954     (+1.38%) |        8.09 s  →        8.25 s    (+1.96%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      225.44 μs →      222.38 μs   (-1.36%) |     941   →     954     (+1.38%) |      212.14 ms →      212.15 ms   (+0.00%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.02 ms →        2.02 ms   (+0.04%) |     104   →     104              |      210.27 ms →      210.35 ms   (+0.04%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.83 ms →        6.69 ms   (-2.15%) |     941   →     954     (+1.38%) |        6.43 s  →        6.38 s    (-0.80%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       87.51 μs →       89.94 μs   (+2.78%) |     941   →     954     (+1.38%) |       82.34 ms →       85.80 ms   (+4.20%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      768.51 μs →      801.72 μs   (+4.32%) |     104   →     104              |       79.93 ms →       83.38 ms   (+4.32%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.69 ms →        9.55 ms   (-1.51%) |     941   →     954     (+1.38%) |        9.12 s  →        9.11 s    (-0.15%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.18 ms →        5.99 ms   (-2.94%) |     941   →     954     (+1.38%) |        5.81 s  →        5.72 s    (-1.60%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.12%) |     941   →     954     (+1.38%) |        1.43 s  →        1.45 s    (+1.26%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.69 ms →        8.40 ms   (-3.26%) |     941   →     954     (+1.38%) |        8.17 s  →        8.02 s    (-1.92%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.58 ms →        1.23 ms  (-21.93%) |     941   →     954     (+1.38%) |        1.49 s  →        1.18 s   (-20.85%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.27 ms →        7.37 ms   (+1.42%) |    1.88 K →    1.91 K   (+1.38%) |       13.68 s  →       14.06 s    (+2.82%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.47 ms →       26.64 ms   (-3.02%) |     941   →     954     (+1.38%) |       25.85 s  →       25.42 s    (-1.68%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.05 ms →        1.94 ms   (-5.17%) |    1.78 K →    1.80 K   (+1.46%) |        3.64 s  →        3.50 s    (-3.79%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       66.57 ns →       75.27 ns  (+13.06%) |    1.78 K →    1.80 K   (+1.46%) |      118.37 μs →      135.78 μs  (+14.71%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.03 ms →        1.93 ms   (-4.95%) |    1.78 K →    1.80 K   (+1.46%) |        3.61 s  →        3.48 s    (-3.56%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       65.75 ns →       40.59 ns  (-38.27%) |    1.78 K →    1.80 K   (+1.46%) |      116.91 μs →       73.23 μs  (-37.36%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      807.00 μs →      776.86 μs   (-3.74%) |     941   →     954     (+1.38%) |      759.39 ms →      741.12 ms   (-2.41%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      770.15 μs →      728.21 μs   (-5.45%) |     941   →     954     (+1.38%) |      724.71 ms →      694.71 ms   (-4.14%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.27 ms →        5.12 ms   (-2.77%) |    3.66 K →    3.71 K   (+1.42%) |       19.28 s  →       19.01 s    (-1.39%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.57 ms →        3.48 ms   (-2.53%) |    5.33 K →    5.41 K   (+1.46%) |       19.05 s  →       18.84 s    (-1.10%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.50 ms →        5.21 ms   (-5.21%) |     941   →     954     (+1.38%) |        5.17 s  →        4.97 s    (-3.90%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.73 ms →        3.44 ms   (-7.78%) |     941   →     954     (+1.38%) |        3.51 s  →        3.28 s    (-6.51%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       66.38 ns →       65.39 ns   (-1.50%) |     941   →     954     (+1.38%) |       62.47 μs →       62.38 μs   (-0.13%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.71 ms →        3.43 ms   (-7.57%) |     941   →     954     (+1.38%) |        3.49 s  →        3.27 s    (-6.29%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       64.81 ns →      104.17 ns  (+60.73%) |     941   →     954     (+1.38%) |       60.98 μs →       99.37 μs  (+62.95%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       69.88 ms →       34.60 ms  (-50.49%) |     941   →     954     (+1.38%) |       65.76 s  →       33.01 s   (-49.80%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.62 ms →       10.07 ms   (-5.14%) |     919   →     929     (+1.09%) |        9.76 s  →        9.36 s    (-4.11%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.23 ms →        9.70 ms   (-5.18%) |     874   →     882     (+0.92%) |        8.94 s  →        8.55 s    (-4.31%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.07 ms →        4.82 ms   (-4.95%) |    1.75 K →    1.76 K   (+0.92%) |        8.86 s  →        8.50 s    (-4.08%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      642.40 μs →      643.53 μs   (+0.17%) |     874   →     882     (+0.92%) |      561.46 ms →      567.59 ms   (+1.09%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.70 ms →       37.11 ms  (-28.21%) |     209   →     339    (+62.20%) |       10.81 s  →       12.58 s   (+16.44%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.30 ms →       21.79 ms  (-36.47%) |     314   →     574    (+82.80%) |       10.77 s  →       12.51 s   (+16.14%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.53 ms →       15.37 ms  (-39.81%) |     419   →     809    (+93.08%) |       10.70 s  →       12.43 s   (+16.21%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      596.36 ns →      505.22 ns  (-15.28%) |     104   →     104              |       62.02 μs →       52.54 μs  (-15.28%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.99 μs →       21.59 μs   (+2.84%) |      26   →      26              |      545.83 μs →      561.32 μs   (+2.84%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      611.29 μs →      601.75 μs   (-1.56%) |      26   →      26              |       15.89 ms →       15.65 ms   (-1.56%) | 
  │ │ ├ sirius::Density::generate                                       |      909.14 ms →      895.20 ms   (-1.53%) |      26   →      26              |       23.64 s  →       23.28 s    (-1.53%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      532.33 ms →      523.15 ms   (-1.73%) |      26   →      26              |       13.84 s  →       13.60 s    (-1.73%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.23 ms →       24.34 ms   (-3.55%) |     104   →     104              |        2.62 s  →        2.53 s    (-3.55%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.52 μs →        8.94 μs   (+4.87%) |     104   →     104              |      886.46 μs →      929.60 μs   (+4.87%) | 
- │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.27 μs →       18.50 μs  (+21.20%) |       8   →       8              |      122.14 μs →      148.03 μs  (+21.20%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       21.11 ms →       20.21 ms   (-4.26%) |     104   →     104              |        2.20 s  →        2.10 s    (-4.26%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.68 ms →       29.63 ms   (-3.41%) |     104   →     104              |        3.19 s  →        3.08 s    (-3.41%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.48 μs →        9.67 μs   (+1.99%) |     104   →     104              |      986.04 μs →        1.01 ms   (+1.99%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.36%) |     104   →     104              |      151.40 ms →      150.85 ms   (-0.36%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.74 ms →       27.70 ms   (-3.60%) |     104   →     104              |        2.99 s  →        2.88 s    (-3.60%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.61 ms →        3.57 ms  (-22.45%) |     104   →     104              |      479.17 ms →      371.60 ms  (-22.45%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      638.17 ns →      549.87 ns  (-13.84%) |     104   →     104              |       66.37 μs →       57.19 μs  (-13.84%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.74 ms →       42.49 ms   (-0.58%) |     104   →     104              |        4.44 s  →        4.42 s    (-0.58%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.66 ms   (+1.08%) |      26   →      26              |       42.59 ms →       43.04 ms   (+1.08%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.91 ms →       88.91 ms   (+0.01%) |      26   →      26              |        2.31 s  →        2.31 s    (+0.01%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.68 ms →       88.68 ms   (+0.01%) |      26   →      26              |        2.31 s  →        2.31 s    (+0.01%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      285.64 ms →      279.36 ms   (-2.20%) |      26   →      26              |        7.43 s  →        7.26 s    (-2.20%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      285.64 ms →      279.36 ms   (-2.20%) |      26   →      26              |        7.43 s  →        7.26 s    (-2.20%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.58 ms →       24.49 ms  (-17.20%) |      26   →      26              |      769.12 ms →      636.83 ms  (-17.20%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      223.71 ms →      229.07 ms   (+2.39%) |      26   →      26              |        5.82 s  →        5.96 s    (+2.39%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       30.58 ms →       23.98 ms  (-21.57%) |      26   →      26              |      794.99 ms →      623.51 ms  (-21.57%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.75 ms →       80.84 ms   (-1.12%) |      26   →      26              |        2.13 s  →        2.10 s    (-1.12%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.82 ms →        8.26 ms  (+41.81%) |      26   →      26              |      151.44 ms →      214.76 ms  (+41.81%) | 
  │ │ ├ sirius::Density::mix                                            |      210.30 ms →      213.88 ms   (+1.70%) |      26   →      26              |        5.47 s  →        5.56 s    (+1.70%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      973.65 μs →      973.02 μs   (-0.07%) |      26   →      26              |       25.32 ms →       25.30 ms   (-0.07%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.72 ms →       10.27 ms   (-4.20%) |     320   →     334     (+4.37%) |        3.43 s  →        3.43 s    (-0.01%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.47 ms →       10.04 ms   (-4.11%) |     320   →     334     (+4.37%) |        3.35 s  →        3.35 s    (+0.08%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.47 ms →       10.04 ms   (-4.11%) |     320   →     334     (+4.37%) |        3.35 s  →        3.35 s    (+0.08%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.48 ms →        6.06 ms   (-6.56%) |      26   →      26              |      168.53 ms →      157.48 ms   (-6.56%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.61 ms →        5.23 ms   (-6.78%) |      26   →      26              |      145.98 ms →      136.08 ms   (-6.78%) | 
  │ │ ├ sirius::Potential::generate                                     |      575.89 ms →      577.88 ms   (+0.35%) |      26   →      26              |       14.97 s  →       15.02 s    (+0.35%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.17 ms →      136.18 ms   (+7.93%) |      26   →      26              |        3.28 s  →        3.54 s    (+7.93%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.64 ms →       18.14 ms (+221.70%) |      26   →      26              |      146.61 ms →      471.63 ms (+221.70%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.34 ms →       10.19 ms   (-1.52%) |      26   →      26              |      268.94 ms →      264.85 ms   (-1.52%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.08 ms →        9.97 ms   (-1.10%) |      26   →      26              |      262.09 ms →      259.20 ms   (-1.10%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.08 ms →        9.97 ms   (-1.10%) |      26   →      26              |      262.07 ms →      259.19 ms   (-1.10%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      557.93 μs →      552.58 μs   (-0.96%) |      52   →      52              |       29.01 ms →       28.73 ms   (-0.96%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.50 ms →       48.80 ms   (-1.42%) |      26   →      26              |        1.29 s  →        1.27 s    (-1.42%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.16 ms →       46.44 ms   (-1.54%) |      26   →      26              |        1.23 s  →        1.21 s    (-1.54%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.00 ms →        3.02 ms   (+0.83%) |      52   →      52              |      155.98 ms →      157.29 ms   (+0.83%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.72 ms →        5.23 ms   (-8.62%) |      26   →      26              |      148.69 ms →      135.87 ms   (-8.62%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.69 ms →        6.60 ms   (-1.24%) |      26   →      26              |      173.82 ms →      171.67 ms   (-1.24%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.00 ms →       90.85 ms   (-0.16%) |      26   →      26              |        2.37 s  →        2.36 s    (-0.16%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      300.13 ms →      293.06 ms   (-2.36%) |      26   →      26              |        7.80 s  →        7.62 s    (-2.36%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      291.66 ms →      285.48 ms   (-2.12%) |      26   →      26              |        7.58 s  →        7.42 s    (-2.12%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      291.66 ms →      285.48 ms   (-2.12%) |      26   →      26              |        7.58 s  →        7.42 s    (-2.12%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.21 ms →       27.20 ms  (-15.56%) |      26   →      26              |      837.46 ms →      707.17 ms  (-15.56%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.37 ms →      230.47 ms   (+2.26%) |      26   →      26              |        5.86 s  →        5.99 s    (+2.26%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       30.30 ms →       24.00 ms  (-20.81%) |      26   →      26              |      787.91 ms →      623.93 ms  (-20.81%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.31 ms →        5.49 ms   (+3.35%) |      26   →      26              |      138.17 ms →      142.81 ms   (+3.35%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.31 ms →       10.22 ms   (-0.93%) |     182   →     182              |        1.88 s  →        1.86 s    (-0.93%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.87 ms →        9.82 ms   (-0.51%) |     182   →     182              |        1.80 s  →        1.79 s    (-0.51%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.87 ms →        9.82 ms   (-0.51%) |     182   →     182              |        1.80 s  →        1.79 s    (-0.51%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.28 ms →       10.77 ms   (-4.54%) |      78   →      78              |      879.67 ms →      839.77 ms   (-4.54%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.64 ms →       10.16 ms   (-4.52%) |      78   →      78              |      829.91 ms →      792.40 ms   (-4.52%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.99 ms →       10.34 ms   (+3.59%) |      26   →      26              |      259.65 ms →      268.97 ms   (+3.59%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      149.60 μs →      111.86 μs  (-25.23%) |      26   →      26              |        3.89 ms →        2.91 ms  (-25.23%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      144.39 μs →      106.54 μs  (-26.21%) |      26   →      26              |        3.75 ms →        2.77 ms  (-26.21%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.20 ms →        5.04 ms   (-2.99%) |       2   →       2              |       10.39 ms →       10.08 ms   (-2.99%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.12 ms →       10.29 ms   (+1.64%) |       6   →       6              |       60.75 ms →       61.75 ms   (+1.64%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.94 ms →       10.28 ms   (+3.41%) |       6   →       6              |       59.66 ms →       61.70 ms   (+3.41%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.94 ms →       10.28 ms   (+3.41%) |       6   →       6              |       59.66 ms →       61.70 ms   (+3.41%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.79 ms →       10.72 ms   (-0.62%) |       3   →       3              |       32.36 ms →       32.16 ms   (-0.62%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.62 ms →       10.71 ms   (+0.87%) |       3   →       3              |       31.87 ms →       32.14 ms   (+0.87%) | 
  ├ sirius::Periodic_function|inner                                     |       10.05 ms →       10.67 ms   (+6.23%) |       2   →       2              |       20.10 ms →       21.35 ms   (+6.23%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.04 ms →       10.67 ms   (+6.23%) |       2   →       2              |       20.08 ms →       21.33 ms   (+6.23%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.04 ms →       10.67 ms   (+6.23%) |       2   →       2              |       20.08 ms →       21.33 ms   (+6.23%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.79 ms →       11.14 ms   (+3.22%) |       1   →       1              |       10.79 ms →       11.14 ms   (+3.22%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.78 ms →       11.13 ms   (+3.22%) |       1   →       1              |       10.78 ms →       11.13 ms   (+3.22%) | 
  └ sirius::finalize                                                    |      316.20 ms →      304.66 ms   (-3.65%) |       1   →       1              |      316.20 ms →      304.66 ms   (-3.65%) | 
  ====================================================================================================================================================================================================
```
