# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      246.50 s  →      228.59 s    (-7.27%) |       1   →       1              |      246.50 s  →      228.59 s    (-7.27%) | 
  ├ sirius::initialize                                                  |        2.76 s  →        2.89 s    (+4.79%) |       1   →       1              |        2.76 s  →        2.89 s    (+4.79%) | 
  ├ sirius::Simulation_context::initialize                              |        2.88 s  →        2.89 s    (+0.39%) |       1   →       1              |        2.88 s  →        2.89 s    (+0.39%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      250.89 μs →       20.32 ms (+8000.74%) |       1   →       1              |      250.89 μs →       20.32 ms (+8000.74%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      135.35 ms →      138.66 ms   (+2.45%) |       1   →       1              |      135.35 ms →      138.66 ms   (+2.45%) | 
  │ │ ├ sirius::Atom_type::init                                         |       55.57 ms →       57.04 ms   (+2.63%) |       2   →       2              |      111.15 ms →      114.07 ms   (+2.63%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.13 ms →       24.51 ms   (+1.61%) |       1   →       1              |       24.13 ms →       24.51 ms   (+1.61%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.86 ms →        6.38 ms   (+8.83%) |       1   →       1              |        5.86 ms →        6.38 ms   (+8.83%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.23 ms →       18.10 ms   (-0.72%) |       1   →       1              |       18.23 ms →       18.10 ms   (-0.72%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.21 ms →       18.07 ms   (-0.73%) |       1   →       1              |       18.21 ms →       18.07 ms   (-0.73%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.17 ms   (+0.54%) |       1   →       1              |        4.15 ms →        4.17 ms   (+0.54%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.65%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.65%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.70 μs →      102.23 μs   (+1.51%) |       1   →       1              |      100.70 μs →      102.23 μs   (+1.51%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.68 s    (-0.67%) |       1   →       1              |        2.70 s  →        2.68 s    (-0.67%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.88 ms →       10.81 ms   (-0.69%) |       1   →       1              |       10.88 ms →       10.81 ms   (-0.69%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.41 ms   (-0.58%) |       1   →       1              |        4.43 ms →        4.41 ms   (-0.58%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.41 ms →        6.37 ms   (-0.75%) |       1   →       1              |        6.41 ms →        6.37 ms   (-0.75%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.40 ms →        6.35 ms   (-0.75%) |       1   →       1              |        6.40 ms →        6.35 ms   (-0.75%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.86 ms   (-0.60%) |       1   →       1              |        3.89 ms →        3.86 ms   (-0.60%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-0.99%) |       1   →       1              |        2.34 ms →        2.32 ms   (-0.99%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.18 μs →       98.93 μs   (-1.24%) |       1   →       1              |      100.18 μs →       98.93 μs   (-1.24%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       65.68 ms →       62.74 ms   (-4.47%) |       2   →       2              |      131.36 ms →      125.49 ms   (-4.47%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.17 ms   (+0.34%) |       2   →       2              |       10.30 ms →       10.33 ms   (+0.34%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.28%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.28%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.76 ms   (+0.02%) |       2   →       2              |       43.52 ms →       43.53 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.88 ms   (+0.20%) |       2   →       2              |       29.70 ms →       29.76 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.84 ms →       19.88 ms   (+0.22%) |       4   →       4              |       79.34 ms →       79.52 ms   (+0.22%) | 
  │   ├ sddk::Gvec::init                                                |      174.38 ms →      173.94 ms   (-0.25%) |       2   →       2              |      348.77 ms →      347.88 ms   (-0.25%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.55 ms →      131.14 ms   (-0.31%) |       2   →       2              |      263.10 ms →      262.28 ms   (-0.31%) | 
  │   ├ sddk::Gvec_shells                                               |      185.36 ms →      181.53 ms   (-2.07%) |       1   →       1              |      185.36 ms →      181.53 ms   (-2.07%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.33 ms   (+0.44%) |       1   →       1              |        1.32 ms →        1.33 ms   (+0.44%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.94 ms →      294.61 ms   (-0.45%) |       2   →       2              |      591.87 ms →      589.22 ms   (-0.45%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       75.48 ms →       78.20 ms   (+3.61%) |       1   →       1              |       75.48 ms →       78.20 ms   (+3.61%) | 
- │ ├ sirius::K_point::K_point                                          |        2.50 μs →        2.76 μs  (+10.59%) |       4   →       4              |        9.98 μs →       11.04 μs  (+10.59%) | 
  │ └ sirius::K_point_set::initialize                                   |       75.38 ms →       78.10 ms   (+3.61%) |       1   →       1              |       75.38 ms →       78.10 ms   (+3.61%) | 
  │   └ sirius::K_point::initialize                                     |       18.83 ms →       19.50 ms   (+3.56%) |       4   →       4              |       75.33 ms →       78.01 ms   (+3.56%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.26 ms →       14.80 ms   (+3.81%) |       4   →       4              |       57.05 ms →       59.22 ms   (+3.81%) | 
  │     │ └ sddk::Gvec::init                                            |        3.88 ms →        4.01 ms   (+3.10%) |       4   →       4              |       15.54 ms →       16.02 ms   (+3.10%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.74 μs →        9.76 μs  (+11.71%) |       4   →       4              |       34.96 μs →       39.05 μs  (+11.71%) | 
  │     └ sirius::K_point::update                                       |        3.27 ms →        3.35 ms   (+2.35%) |       4   →       4              |       13.08 ms →       13.39 ms   (+2.35%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.74 ms   (-1.15%) |       4   →       4              |        7.05 ms →        6.97 ms   (-1.15%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      929.53 μs →      909.42 μs   (-2.16%) |       4   →       4              |        3.72 ms →        3.64 ms   (-2.16%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.29 ms →        5.47 ms   (+3.46%) |       2   →       2              |       10.57 ms →       10.94 ms   (+3.46%) | 
  ├ sirius::Potential                                                   |      158.10 ms →      157.76 ms   (-0.22%) |       1   →       1              |      158.10 ms →      157.76 ms   (-0.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.94 ms →        5.89 ms   (-0.98%) |       6   →       6              |       35.66 ms →       35.32 ms   (-0.98%) | 
  │ └ sirius::Potential::update                                         |      121.73 ms →      121.72 ms   (-0.01%) |       1   →       1              |      121.73 ms →      121.72 ms   (-0.01%) | 
  │   └ sirius::Potential::generate_local_potential                     |      120.94 ms →      121.01 ms   (+0.06%) |       1   →       1              |      120.94 ms →      121.01 ms   (+0.06%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.68 ms →      110.03 ms   (+3.14%) |       1   →       1              |      106.68 ms →      110.03 ms   (+3.14%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       13.38 ms →       10.07 ms  (-24.73%) |       1   →       1              |       13.38 ms →       10.07 ms  (-24.73%) | 
  ├ sirius::Density                                                     |      134.74 ms →      137.13 ms   (+1.77%) |       1   →       1              |      134.74 ms →      137.13 ms   (+1.77%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.22 ms →        5.33 ms   (+2.10%) |       2   →       2              |       10.45 ms →       10.67 ms   (+2.10%) | 
  │ └ sirius::Density::update                                           |      124.02 ms →      126.19 ms   (+1.75%) |       1   →       1              |      124.02 ms →      126.19 ms   (+1.75%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.59 ms →      125.76 ms   (+1.76%) |       1   →       1              |      123.59 ms →      125.76 ms   (+1.76%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      103.56 μs →      102.98 μs   (-0.56%) |       1   →       1              |      103.56 μs →      102.98 μs   (-0.56%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.00 ms →      110.67 ms   (+1.53%) |       1   →       1              |      109.00 ms →      110.67 ms   (+1.53%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.02 ms →       14.53 ms   (+3.58%) |       1   →       1              |       14.02 ms →       14.53 ms   (+3.58%) | 
  ├ sirius::Density::initial_density                                    |      174.45 ms →      175.94 ms   (+0.86%) |       1   →       1              |      174.45 ms →      175.94 ms   (+0.86%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      109.11 ms →      109.21 ms   (+0.09%) |       1   →       1              |      109.11 ms →      109.21 ms   (+0.09%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.37 ms →       12.30 ms   (+8.12%) |       2   →       2              |       22.74 ms →       24.59 ms   (+8.12%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.83 ms →        9.69 ms   (-1.52%) |       1   →       1              |        9.83 ms →        9.69 ms   (-1.52%) | 
  ├ sirius::Potential::generate                                         |      592.53 ms →      591.66 ms   (-0.15%) |       1   →       1              |      592.53 ms →      591.66 ms   (-0.15%) | 
  │ ├ sirius::Potential::poisson                                        |      136.77 ms →      138.18 ms   (+1.03%) |       1   →       1              |      136.77 ms →      138.18 ms   (+1.03%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.24 ms →       19.58 ms   (+1.81%) |       1   →       1              |       19.24 ms →       19.58 ms   (+1.81%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.21 ms →        9.99 ms   (-2.11%) |       1   →       1              |       10.21 ms →        9.99 ms   (-2.11%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.92 ms →        9.81 ms   (-1.13%) |       1   →       1              |        9.92 ms →        9.81 ms   (-1.13%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.92 ms →        9.81 ms   (-1.13%) |       1   →       1              |        9.92 ms →        9.81 ms   (-1.13%) | 
  │ ├ sirius::Periodic_function::add                                    |      571.54 μs →      556.41 μs   (-2.65%) |       2   →       2              |        1.14 ms →        1.11 ms   (-2.65%) | 
  │ ├ sirius::Potential::xc                                             |       54.95 ms →       53.79 ms   (-2.12%) |       1   →       1              |       54.95 ms →       53.79 ms   (-2.12%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.57 ms →       51.44 ms   (-2.13%) |       1   →       1              |       52.57 ms →       51.44 ms   (-2.13%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.74 ms →        5.70 ms   (-0.66%) |       2   →       2              |       11.47 ms →       11.40 ms   (-0.66%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.94 ms →        5.54 ms   (-6.72%) |       1   →       1              |        5.94 ms →        5.54 ms   (-6.72%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.95 ms →        5.64 ms   (-5.14%) |       1   →       1              |        5.95 ms →        5.64 ms   (-5.14%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.74 ms →       92.62 ms   (-0.13%) |       1   →       1              |       92.74 ms →       92.62 ms   (-0.13%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.59 ms →      298.90 ms   (-0.23%) |       1   →       1              |      299.59 ms →      298.90 ms   (-0.23%) | 
  ├ sirius::Hamiltonian0                                                |        8.49 ms →        8.45 ms   (-0.43%) |       1   →       1              |        8.49 ms →        8.45 ms   (-0.43%) | 
  │ ├ sirius::Local_operator                                            |        8.14 ms →        8.11 ms   (-0.41%) |       1   →       1              |        8.14 ms →        8.11 ms   (-0.41%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.83 ms →        4.84 ms   (+0.25%) |       1   →       1              |        4.83 ms →        4.84 ms   (+0.25%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.39 ms →        2.34 ms   (-2.08%) |       1   →       1              |        2.39 ms →        2.34 ms   (-2.08%) | 
  │ ├ sirius::Non_local_operator                                        |       62.83 μs →       63.26 μs   (+0.67%) |       2   →       2              |      125.66 μs →      126.51 μs   (+0.67%) | 
  │ ├ sirius::D_operator::initialize                                    |       96.45 μs →       94.42 μs   (-2.11%) |       1   →       1              |       96.45 μs →       94.42 μs   (-2.11%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.51 μs →       69.16 μs   (-0.50%) |       1   →       1              |       69.51 μs →       69.16 μs   (-0.50%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.13 s  →        3.13 s    (+0.04%) |       1   →       1              |        3.13 s  →        3.13 s    (+0.04%) | 
  │ ├ sirius::Hamiltonian_k                                             |      374.08 μs →      378.27 μs   (+1.12%) |       4   →       4              |        1.50 ms →        1.51 ms   (+1.12%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      368.99 μs →      373.54 μs   (+1.23%) |       4   →       4              |        1.48 ms →        1.49 ms   (+1.23%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.33 μs →        3.05 μs   (-8.26%) |       4   →       4              |       13.32 μs →       12.22 μs   (-8.26%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      781.70 ms →      782.04 ms   (+0.04%) |       4   →       4              |        3.13 s  →        3.13 s    (+0.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       33.17 ms →       32.90 ms   (-0.81%) |      16   →      16              |      530.70 ms →      526.42 ms   (-0.81%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.49 ms →       14.75 ms   (+1.80%) |       4   →       4              |       57.95 ms →       58.99 ms   (+1.80%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.36 ms →        5.49 ms   (+2.40%) |       4   →       4              |       21.45 ms →       21.97 ms   (+2.40%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      353.46 ms →      354.25 ms   (+0.22%) |       4   →       4              |        1.41 s  →        1.42 s    (+0.22%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      256.79 ms →      257.49 ms   (+0.27%) |       4   →       4              |        1.03 s  →        1.03 s    (+0.27%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       61.79 ms →       62.66 ms   (+1.41%) |       4   →       4              |      247.15 ms →      250.64 ms   (+1.41%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.42 ms →       16.59 ms   (+1.01%) |       4   →       4              |       65.70 ms →       66.36 ms   (+1.01%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.42 ms →       16.59 ms   (+1.01%) |       4   →       4              |       65.69 ms →       66.36 ms   (+1.01%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       38.98 ms →       39.56 ms   (+1.49%) |       4   →       4              |      155.93 ms →      158.25 ms   (+1.49%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       17.88 ms →       16.33 ms   (-8.65%) |       4   →       4              |       71.51 ms →       65.33 ms   (-8.65%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       17.87 ms →       16.33 ms   (-8.65%) |       4   →       4              |       71.49 ms →       65.31 ms   (-8.65%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.07 ms →       54.42 ms   (+2.54%) |       4   →       4              |      212.27 ms →      217.67 ms   (+2.54%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.08 ms →       36.40 ms   (+3.74%) |       4   →       4              |      140.33 ms →      145.58 ms   (+3.74%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.96 ms   (+0.48%) |       4   →       4              |        7.81 ms →        7.85 ms   (+0.48%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.47 ms →       40.53 ms   (+0.13%) |       4   →       4              |      161.89 ms →      162.10 ms   (+0.13%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.31 ms →        7.37 ms   (+0.71%) |       4   →       4              |       29.26 ms →       29.46 ms   (+0.71%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.10 ms →       27.12 ms   (+0.06%) |       8   →       8              |      216.81 ms →      216.94 ms   (+0.06%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.93 ms →       15.27 ms   (+2.27%) |       8   →       8              |      119.45 ms →      122.15 ms   (+2.27%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.89 ms →       15.22 ms   (+2.27%) |       8   →       8              |      119.08 ms →      121.79 ms   (+2.27%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       25.75 ns →       33.25 ns  (+29.13%) |       8   →       8              |      206.00 ns →      266.00 ns  (+29.13%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.69 ms →       15.01 ms   (+2.23%) |       8   →       8              |      117.49 ms →      120.11 ms   (+2.23%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       27.63 ns →       31.63 ns  (+14.48%) |       8   →       8              |      221.00 ns →      253.00 ns  (+14.48%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      125.87 ms →      126.61 ms   (+0.58%) |       4   →       4              |      503.49 ms →      506.43 ms   (+0.58%) | 
  │ │ └ sddk::wf_trans                                                  |       23.68 ms →       23.74 ms   (+0.24%) |       4   →       4              |       94.71 ms →       94.94 ms   (+0.24%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.51 ms →       23.48 ms   (-0.16%) |       4   →       4              |       94.06 ms →       93.91 ms   (-0.16%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      406.50 ns →      387.75 ns   (-4.61%) |       4   →       4              |        1.63 μs →        1.55 μs   (-4.61%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      235.73 s  →      217.64 s    (-7.67%) |       1   →       1              |      235.73 s  →      217.64 s    (-7.67%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.76 ms   (-1.31%) |      19   →      19              |      110.97 ms →      109.52 ms   (-1.31%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        9.05 s  →        8.05 s   (-11.14%) |      26   →      27     (+3.85%) |      235.41 s  →      217.24 s    (-7.72%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.56 ms →        4.52 ms   (-0.94%) |      26   →      27     (+3.85%) |      118.61 ms →      122.02 ms   (+2.87%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.21 ms →        4.16 ms   (-0.99%) |      26   →      27     (+3.85%) |      109.35 ms →      112.43 ms   (+2.82%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      983.73 μs →      970.65 μs   (-1.33%) |      26   →      27     (+3.85%) |       25.58 ms →       26.21 ms   (+2.47%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.33 ms →        2.30 ms   (-1.25%) |      26   →      27     (+3.85%) |       60.68 ms →       62.23 ms   (+2.55%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.33 μs →       64.58 μs   (+0.39%) |      52   →      54     (+3.85%) |        3.35 ms →        3.49 ms   (+4.26%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.83 μs →       92.81 μs   (-1.08%) |      26   →      27     (+3.85%) |        2.44 ms →        2.51 ms   (+2.72%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.56 μs →       65.75 μs   (+0.28%) |      26   →      27     (+3.85%) |        1.70 ms →        1.78 ms   (+4.13%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.96 s  →        5.95 s   (-14.60%) |      26   →      27     (+3.85%) |      181.01 s  →      160.52 s   (-11.32%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      358.41 μs →      324.07 μs   (-9.58%) |     104   →     108     (+3.85%) |       37.27 ms →       35.00 ms   (-6.10%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      352.71 μs →      318.75 μs   (-9.63%) |     104   →     108     (+3.85%) |       36.68 ms →       34.43 ms   (-6.15%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.08 μs →        3.81 μs   (-6.62%) |     104   →     108     (+3.85%) |      424.78 μs →      411.92 μs   (-3.03%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.74 s  →        1.49 s   (-14.61%) |     104   →     108     (+3.85%) |      180.97 s  →      160.48 s   (-11.32%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.90 ms →       12.05 ms   (+1.26%) |     104   →     108     (+3.85%) |        1.24 s  →        1.30 s    (+5.15%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      631.53 ns →      672.96 ns   (+6.56%) |     624   →     648     (+3.85%) |      394.07 μs →      436.08 μs  (+10.66%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.87 ms →        1.83 ms   (-2.16%) |     104   →     108     (+3.85%) |      194.82 ms →      197.95 ms   (+1.60%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.37 μs →      354.62 μs   (+0.64%) |     104   →     108     (+3.85%) |       36.65 ms →       38.30 ms   (+4.51%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      563.14 μs →      549.71 μs   (-2.38%) |     208   →     216     (+3.85%) |      117.13 ms →      118.74 ms   (+1.37%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.72 s  →        1.46 s   (-14.81%) |     104   →     108     (+3.85%) |      178.60 s  →      158.01 s   (-11.53%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.02 ms →       69.88 ms   (+1.24%) |     914   →     947     (+3.61%) |       63.09 s  →       66.18 s    (+4.90%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.92 ms →       44.52 ms   (+1.36%) |     914   →     947     (+3.61%) |       40.15 s  →       42.16 s    (+5.02%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.41 ms →        8.73 ms   (+3.72%) |     914   →     947     (+3.61%) |        7.69 s  →        8.26 s    (+7.47%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      238.91 μs →      242.19 μs   (+1.37%) |     914   →     947     (+3.61%) |      218.36 ms →      229.35 ms   (+5.03%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.08 ms →        2.11 ms   (+1.19%) |     104   →     108     (+3.85%) |      216.56 ms →      227.56 ms   (+5.08%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.61 ms →        6.73 ms   (+1.71%) |     914   →     947     (+3.61%) |        6.05 s  →        6.37 s    (+5.38%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       90.74 μs →       87.27 μs   (-3.83%) |     914   →     947     (+3.61%) |       82.94 ms →       82.64 ms   (-0.35%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      774.07 μs →      742.36 μs   (-4.10%) |     104   →     108     (+3.85%) |       80.50 ms →       80.17 ms   (-0.41%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.61 ms →        9.71 ms   (+1.04%) |     914   →     947     (+3.61%) |        8.79 s  →        9.20 s    (+4.69%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.99 ms →        6.08 ms   (+1.46%) |     914   →     947     (+3.61%) |        5.47 s  →        5.75 s    (+5.12%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.53 ms   (+0.18%) |     914   →     947     (+3.61%) |        1.39 s  →        1.45 s    (+3.79%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.74 ms →        8.80 ms   (+0.78%) |     914   →     947     (+3.61%) |        7.99 s  →        8.34 s    (+4.41%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.42 ms →        1.48 ms   (+4.17%) |     914   →     947     (+3.61%) |        1.30 s  →        1.40 s    (+7.93%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.41 ms →        7.50 ms   (+1.29%) |    1.83 K →    1.89 K   (+3.61%) |       13.54 s  →       14.21 s    (+4.95%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.04 ms →       27.74 ms   (-1.08%) |     914   →     947     (+3.61%) |       25.63 s  →       26.27 s    (+2.49%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.06 ms →        2.06 ms   (+0.09%) |    1.72 K →    1.79 K   (+3.60%) |        3.54 s  →        3.67 s    (+3.69%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       77.87 ns →       53.34 ns  (-31.50%) |    1.72 K →    1.79 K   (+3.60%) |      134.24 μs →       95.26 μs  (-29.04%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.05 ms →        2.05 ms   (+0.04%) |    1.72 K →    1.79 K   (+3.60%) |        3.53 s  →        3.65 s    (+3.64%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       72.58 ns →       55.16 ns  (-24.00%) |    1.72 K →    1.79 K   (+3.60%) |      125.14 μs →       98.52 μs  (-21.27%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      802.32 μs →      776.84 μs   (-3.18%) |     914   →     947     (+3.61%) |      733.32 ms →      735.67 ms   (+0.32%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      798.40 μs →      803.12 μs   (+0.59%) |     914   →     947     (+3.61%) |      729.74 ms →      760.55 ms   (+4.22%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.40 ms →        5.33 ms   (-1.28%) |    3.55 K →    3.68 K   (+3.60%) |       19.17 s  →       19.60 s    (+2.27%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.67 ms →        3.62 ms   (-1.31%) |    5.17 K →    5.36 K   (+3.60%) |       18.99 s  →       19.41 s    (+2.23%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.48 ms →        5.25 ms   (-4.07%) |     914   →     947     (+3.61%) |        5.01 s  →        4.98 s    (-0.61%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.77 ms →        3.61 ms   (-4.19%) |     914   →     947     (+3.61%) |        3.45 s  →        3.42 s    (-0.73%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       74.37 ns →       53.15 ns  (-28.53%) |     914   →     947     (+3.61%) |       67.98 μs →       50.34 μs  (-25.95%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.76 ms →        3.60 ms   (-4.23%) |     914   →     947     (+3.61%) |        3.43 s  →        3.41 s    (-0.77%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       49.64 ns →       56.42 ns  (+13.66%) |     914   →     947     (+3.61%) |       45.38 μs →       53.43 μs  (+17.76%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       70.44 ms →       40.45 ms  (-42.57%) |     914   →     947     (+3.61%) |       64.38 s  →       38.30 s   (-40.50%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.84 ms →       10.45 ms   (-3.56%) |     894   →     923     (+3.24%) |        9.69 s  →        9.65 s    (-0.44%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.48 ms →       10.04 ms   (-4.19%) |     848   →     878     (+3.54%) |        8.89 s  →        8.82 s    (-0.80%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.20 ms →        4.98 ms   (-4.19%) |    1.70 K →    1.76 K   (+3.54%) |        8.82 s  →        8.75 s    (-0.80%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      647.28 μs →      662.59 μs   (+2.37%) |     848   →     878     (+3.54%) |      548.89 ms →      581.76 ms   (+5.99%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.55 ms →       39.02 ms  (-24.32%) |     209   →     323    (+54.55%) |       10.77 s  →       12.60 s   (+16.96%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.20 ms →       23.30 ms  (-31.87%) |     314   →     538    (+71.34%) |       10.74 s  →       12.54 s   (+16.73%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.49 ms →       16.54 ms  (-35.10%) |     419   →     753    (+79.71%) |       10.68 s  →       12.46 s   (+16.64%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      577.63 ns →      502.66 ns  (-12.98%) |     104   →     108     (+3.85%) |       60.07 μs →       54.29 μs   (-9.63%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.45 μs →       22.36 μs   (+4.22%) |      26   →      27     (+3.85%) |      557.73 μs →      603.62 μs   (+8.23%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      592.71 μs →      606.47 μs   (+2.32%) |      26   →      27     (+3.85%) |       15.41 ms →       16.37 ms   (+6.26%) | 
  │ │ ├ sirius::Density::generate                                       |      889.74 ms →      895.88 ms   (+0.69%) |      26   →      27     (+3.85%) |       23.13 s  →       24.19 s    (+4.56%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      524.30 ms →      526.22 ms   (+0.37%) |      26   →      27     (+3.85%) |       13.63 s  →       14.21 s    (+4.23%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.18 ms →       24.38 ms   (+0.81%) |     104   →     108     (+3.85%) |        2.51 s  →        2.63 s    (+4.68%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.73 μs →        8.86 μs   (+1.43%) |     104   →     108     (+3.85%) |      908.08 μs →      956.45 μs   (+5.33%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.75 μs →       15.97 μs   (+1.38%) |       8   →       8              |      126.03 μs →      127.77 μs   (+1.38%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.06 ms →       20.21 ms   (+0.72%) |     104   →     108     (+3.85%) |        2.09 s  →        2.18 s    (+4.59%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.10 ms →       30.16 ms   (+0.21%) |     104   →     108     (+3.85%) |        3.13 s  →        3.26 s    (+4.06%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.75 μs →        9.69 μs   (-0.63%) |     104   →     108     (+3.85%) |        1.01 ms →        1.05 ms   (+3.19%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.15%) |     104   →     108     (+3.85%) |      151.33 ms →      157.40 ms   (+4.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.16 ms →       28.22 ms   (+0.21%) |     104   →     108     (+3.85%) |        2.93 s  →        3.05 s    (+4.06%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.04 ms →        4.09 ms   (+1.44%) |     104   →     108     (+3.85%) |      419.64 ms →      442.05 ms   (+5.34%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      619.86 ns →      665.89 ns   (+7.43%) |     104   →     108     (+3.85%) |       64.47 μs →       71.92 μs  (+11.56%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.48 ms →       42.57 ms   (+0.20%) |     104   →     108     (+3.85%) |        4.42 s  →        4.60 s    (+4.06%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.76%) |      26   →      27     (+3.85%) |       42.53 ms →       44.51 ms   (+4.64%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.88 ms →       88.84 ms   (-0.04%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.80%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.64 ms →       88.61 ms   (-0.03%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.81%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      272.97 ms →      278.01 ms   (+1.85%) |      26   →      27     (+3.85%) |        7.10 s  →        7.51 s    (+5.76%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      272.97 ms →      278.01 ms   (+1.85%) |      26   →      27     (+3.85%) |        7.10 s  →        7.51 s    (+5.76%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.18 ms →       24.76 ms   (+2.37%) |      26   →      27     (+3.85%) |      628.75 ms →      668.42 ms   (+6.31%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      223.06 ms →      227.66 ms   (+2.06%) |      26   →      27     (+3.85%) |        5.80 s  →        6.15 s    (+5.99%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.95 ms →       23.80 ms   (-0.64%) |      26   →      27     (+3.85%) |      622.75 ms →      642.58 ms   (+3.18%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.27 ms →       80.63 ms   (-0.79%) |      26   →      27     (+3.85%) |        2.11 s  →        2.18 s    (+3.03%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.61 ms →        7.42 ms   (-2.47%) |      26   →      27     (+3.85%) |      197.86 ms →      200.39 ms   (+1.28%) | 
  │ │ ├ sirius::Density::mix                                            |      219.19 ms →      216.35 ms   (-1.29%) |      26   →      27     (+3.85%) |        5.70 s  →        5.84 s    (+2.50%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      973.97 μs →      956.78 μs   (-1.76%) |      26   →      27     (+3.85%) |       25.32 ms →       25.83 ms   (+2.01%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.72 ms →       10.32 ms   (-3.74%) |     334   →     349     (+4.49%) |        3.58 s  →        3.60 s    (+0.58%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.38 ms →       10.01 ms   (-3.61%) |     334   →     349     (+4.49%) |        3.47 s  →        3.49 s    (+0.71%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.38 ms →       10.00 ms   (-3.61%) |     334   →     349     (+4.49%) |        3.47 s  →        3.49 s    (+0.71%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.66 ms →        6.13 ms   (-7.99%) |      26   →      27     (+3.85%) |      173.26 ms →      165.55 ms   (-4.45%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.85 ms →        5.31 ms   (-9.27%) |      26   →      27     (+3.85%) |      152.04 ms →      143.26 ms   (-5.78%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.82 ms →      580.76 ms   (+0.34%) |      26   →      27     (+3.85%) |       15.05 s  →       15.68 s    (+4.19%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.86 ms →      138.89 ms   (+1.48%) |      26   →      27     (+3.85%) |        3.56 s  →        3.75 s    (+5.38%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       19.48 ms →       19.59 ms   (+0.53%) |      26   →      27     (+3.85%) |      506.54 ms →      528.81 ms   (+4.40%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.28 ms →       10.36 ms   (+0.84%) |      26   →      27     (+3.85%) |      267.16 ms →      279.77 ms   (+4.72%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.91 ms →        9.95 ms   (+0.43%) |      26   →      27     (+3.85%) |      257.61 ms →      268.66 ms   (+4.29%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.91 ms →        9.95 ms   (+0.43%) |      26   →      27     (+3.85%) |      257.59 ms →      268.64 ms   (+4.29%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      576.45 μs →      560.32 μs   (-2.80%) |      52   →      54     (+3.85%) |       29.98 ms →       30.26 ms   (+0.94%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.14 ms →       49.28 ms   (+0.28%) |      26   →      27     (+3.85%) |        1.28 s  →        1.33 s    (+4.14%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.82 ms →       46.93 ms   (+0.24%) |      26   →      27     (+3.85%) |        1.22 s  →        1.27 s    (+4.10%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.01 ms   (-0.50%) |      52   →      54     (+3.85%) |      157.26 ms →      162.49 ms   (+3.32%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.39 ms →        5.29 ms   (-1.88%) |      26   →      27     (+3.85%) |      140.23 ms →      142.88 ms   (+1.89%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.64 ms →        6.62 ms   (-0.25%) |      26   →      27     (+3.85%) |      172.62 ms →      178.81 ms   (+3.58%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.92 ms →       90.87 ms   (-0.06%) |      26   →      27     (+3.85%) |        2.36 s  →        2.45 s    (+3.78%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.82 ms →      292.67 ms   (-0.05%) |      26   →      27     (+3.85%) |        7.61 s  →        7.90 s    (+3.80%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      278.83 ms →      282.18 ms   (+1.20%) |      26   →      27     (+3.85%) |        7.25 s  →        7.62 s    (+5.09%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      278.83 ms →      282.18 ms   (+1.20%) |      26   →      27     (+3.85%) |        7.25 s  →        7.62 s    (+5.09%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.29 ms →       27.12 ms   (-0.65%) |      26   →      27     (+3.85%) |      709.64 ms →      732.17 ms   (+3.17%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.46 ms →      227.47 ms   (+1.80%) |      26   →      27     (+3.85%) |        5.81 s  →        6.14 s    (+5.71%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.23 ms →       23.78 ms   (-1.86%) |      26   →      27     (+3.85%) |      630.08 ms →      642.13 ms   (+1.91%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.54 ms →        5.60 ms   (+1.06%) |      26   →      27     (+3.85%) |      144.04 ms →      151.16 ms   (+4.94%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.25 ms →       10.35 ms   (+0.99%) |     182   →     189     (+3.85%) |        1.87 s  →        1.96 s    (+4.87%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.91 ms →        9.86 ms   (-0.41%) |     182   →     189     (+3.85%) |        1.80 s  →        1.86 s    (+3.42%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.90 ms →        9.86 ms   (-0.41%) |     182   →     189     (+3.85%) |        1.80 s  →        1.86 s    (+3.42%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.00 ms →       10.69 ms   (-2.78%) |      78   →      81     (+3.85%) |      857.99 ms →      866.26 ms   (+0.96%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.68 ms →       10.22 ms   (-4.38%) |      78   →      81     (+3.85%) |      833.32 ms →      827.45 ms   (-0.70%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.97 ms →       10.07 ms   (+0.99%) |      26   →      27     (+3.85%) |      259.32 ms →      271.95 ms   (+4.87%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      119.95 μs →      115.72 μs   (-3.53%) |      26   →      27     (+3.85%) |        3.12 ms →        3.12 ms   (+0.18%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      114.75 μs →      110.42 μs   (-3.78%) |      26   →      27     (+3.85%) |        2.98 ms →        2.98 ms   (-0.08%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.25 ms →        5.38 ms   (+2.45%) |       2   →       2              |       10.49 ms →       10.75 ms   (+2.45%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.88 ms →       10.15 ms   (-6.67%) |       6   →       6              |       65.25 ms →       60.90 ms   (-6.67%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.87 ms →       10.06 ms   (-7.40%) |       6   →       6              |       65.20 ms →       60.38 ms   (-7.40%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.87 ms →       10.06 ms   (-7.40%) |       6   →       6              |       65.20 ms →       60.38 ms   (-7.40%) | 
+ │ └ sirius::Smooth_periodic_function|inner                            |       11.82 ms →       10.49 ms  (-11.23%) |       3   →       3              |       35.45 ms →       31.46 ms  (-11.23%) | 
+ │   └ sirius::Smooth_periodic_function|inner_local                    |       11.81 ms →       10.35 ms  (-12.33%) |       3   →       3              |       35.42 ms →       31.06 ms  (-12.33%) | 
  ├ sirius::Periodic_function|inner                                     |       10.87 ms →       10.04 ms   (-7.64%) |       2   →       2              |       21.74 ms →       20.08 ms   (-7.64%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.86 ms →       10.00 ms   (-7.94%) |       2   →       2              |       21.72 ms →       20.00 ms   (-7.94%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.86 ms →       10.00 ms   (-7.90%) |       2   →       2              |       21.71 ms →       20.00 ms   (-7.90%) | 
+ ├ sirius::Smooth_periodic_function|inner                              |       11.83 ms →       10.55 ms  (-10.82%) |       1   →       1              |       11.83 ms →       10.55 ms  (-10.82%) | 
+ │ └ sirius::Smooth_periodic_function|inner_local                      |       11.82 ms →       10.41 ms  (-11.94%) |       1   →       1              |       11.82 ms →       10.41 ms  (-11.94%) | 
  └ sirius::finalize                                                    |      290.96 ms →      314.85 ms   (+8.21%) |       1   →       1              |      290.96 ms →      314.85 ms   (+8.21%) | 
  ====================================================================================================================================================================================================
```
