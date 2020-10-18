# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      243.68 s  →      215.69 s   (-11.48%) |       1   →       1              |      243.68 s  →      215.69 s   (-11.48%) | 
  ├ sirius::initialize                                                  |        2.94 s  →        2.70 s    (-8.20%) |       1   →       1              |        2.94 s  →        2.70 s    (-8.20%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.98 s    (+1.73%) |       1   →       1              |        2.93 s  →        2.98 s    (+1.73%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       24.27 ms →       21.69 ms  (-10.66%) |       1   →       1              |       24.27 ms →       21.69 ms  (-10.66%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      140.93 ms →      207.55 ms  (+47.27%) |       1   →       1              |      140.93 ms →      207.55 ms  (+47.27%) | 
- │ │ ├ sirius::Atom_type::init                                         |       59.16 ms →       92.23 ms  (+55.91%) |       2   →       2              |      118.32 ms →      184.47 ms  (+55.91%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.54 ms →       23.00 ms   (+2.04%) |       1   →       1              |       22.54 ms →       23.00 ms   (+2.04%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.28 ms →        6.34 ms   (+0.84%) |       1   →       1              |        6.28 ms →        6.34 ms   (+0.84%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.21 ms →       16.63 ms   (+2.56%) |       1   →       1              |       16.21 ms →       16.63 ms   (+2.56%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.19 ms →       16.61 ms   (+2.56%) |       1   →       1              |       16.19 ms →       16.61 ms   (+2.56%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.15 ms   (-0.29%) |       1   →       1              |        4.16 ms →        4.15 ms   (-0.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.23%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.23%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      109.61 μs →      105.32 μs   (-3.91%) |       1   →       1              |      109.61 μs →      105.32 μs   (-3.91%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.70 s    (-0.52%) |       1   →       1              |        2.71 s  →        2.70 s    (-0.52%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.81 ms →       10.76 ms   (-0.51%) |       1   →       1              |       10.81 ms →       10.76 ms   (-0.51%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.42 ms →        4.39 ms   (-0.80%) |       1   →       1              |        4.42 ms →        4.39 ms   (-0.80%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.33 ms   (-0.37%) |       1   →       1              |        6.36 ms →        6.33 ms   (-0.37%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.32 ms   (-0.37%) |       1   →       1              |        6.34 ms →        6.32 ms   (-0.37%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.85 ms →        3.82 ms   (-0.79%) |       1   →       1              |        3.85 ms →        3.82 ms   (-0.79%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.26%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.26%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.68 μs →      101.21 μs   (+0.53%) |       1   →       1              |      100.68 μs →      101.21 μs   (+0.53%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.81 ms →       65.68 ms   (+4.56%) |       2   →       2              |      125.63 ms →      131.35 ms   (+4.56%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.17 ms   (+0.35%) |       2   →       2              |       10.31 ms →       10.35 ms   (+0.35%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.49 ms   (+0.37%) |       1   →       1              |        4.47 ms →        4.49 ms   (+0.37%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.75 ms   (-0.07%) |       2   →       2              |       43.52 ms →       43.49 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.83 ms →       14.86 ms   (+0.24%) |       2   →       2              |       29.65 ms →       29.72 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.63 ms →       19.61 ms   (-0.07%) |       4   →       4              |       78.51 ms →       78.46 ms   (-0.07%) | 
  │   ├ sddk::Gvec::init                                                |      175.52 ms →      173.17 ms   (-1.34%) |       2   →       2              |      351.03 ms →      346.33 ms   (-1.34%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.89 ms →      130.66 ms   (-1.68%) |       2   →       2              |      265.78 ms →      261.32 ms   (-1.68%) | 
- │   ├ sddk::Gvec_shells                                               |      164.50 ms →      181.23 ms  (+10.17%) |       1   →       1              |      164.50 ms →      181.23 ms  (+10.17%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.31 ms   (-0.54%) |       1   →       1              |        1.31 ms →        1.31 ms   (-0.54%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.99 ms →      294.16 ms   (+0.06%) |       2   →       2              |      587.99 ms →      588.32 ms   (+0.06%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       75.65 ms →       76.22 ms   (+0.76%) |       1   →       1              |       75.65 ms →       76.22 ms   (+0.76%) | 
- │ ├ sirius::K_point::K_point                                          |        2.24 μs →        2.92 μs  (+30.01%) |       4   →       4              |        8.98 μs →       11.67 μs  (+30.01%) | 
  │ └ sirius::K_point_set::initialize                                   |       75.54 ms →       76.12 ms   (+0.76%) |       1   →       1              |       75.54 ms →       76.12 ms   (+0.76%) | 
  │   └ sirius::K_point::initialize                                     |       18.87 ms →       19.01 ms   (+0.71%) |       4   →       4              |       75.50 ms →       76.03 ms   (+0.71%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.30 ms →       14.31 ms   (+0.07%) |       4   →       4              |       57.21 ms →       57.24 ms   (+0.07%) | 
  │     │ └ sddk::Gvec::init                                            |        3.89 ms →        3.96 ms   (+1.82%) |       4   →       4              |       15.55 ms →       15.83 ms   (+1.82%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.59 μs →        9.03 μs   (+5.11%) |       4   →       4              |       34.37 μs →       36.13 μs   (+5.11%) | 
  │     └ sirius::K_point::update                                       |        3.29 ms →        3.35 ms   (+1.72%) |       4   →       4              |       13.16 ms →       13.39 ms   (+1.72%) | 
  │       └ sirius::Beta_projectors                                     |        1.77 ms →        1.76 ms   (-0.60%) |       4   →       4              |        7.09 ms →        7.05 ms   (-0.60%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      938.88 μs →      913.72 μs   (-2.68%) |       4   →       4              |        3.76 ms →        3.65 ms   (-2.68%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.41 ms →        5.46 ms   (+0.93%) |       2   →       2              |       10.81 ms →       10.91 ms   (+0.93%) | 
  ├ sirius::Potential                                                   |      160.95 ms →      157.59 ms   (-2.09%) |       1   →       1              |      160.95 ms →      157.59 ms   (-2.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.27 ms →        5.75 ms   (-8.31%) |       6   →       6              |       37.60 ms →       34.48 ms   (-8.31%) | 
  │ └ sirius::Potential::update                                         |      122.57 ms →      122.38 ms   (-0.15%) |       1   →       1              |      122.57 ms →      122.38 ms   (-0.15%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.75 ms →      121.64 ms   (-0.09%) |       1   →       1              |      121.75 ms →      121.64 ms   (-0.09%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      114.66 ms →      106.53 ms   (-7.09%) |       1   →       1              |      114.66 ms →      106.53 ms   (-7.09%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.20 ms →       14.22 ms (+129.52%) |       1   →       1              |        6.20 ms →       14.22 ms (+129.52%) | 
  ├ sirius::Density                                                     |      133.98 ms →      135.42 ms   (+1.08%) |       1   →       1              |      133.98 ms →      135.42 ms   (+1.08%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.18 ms →        5.61 ms   (+8.32%) |       2   →       2              |       10.35 ms →       11.21 ms   (+8.32%) | 
  │ └ sirius::Density::update                                           |      123.35 ms →      123.91 ms   (+0.45%) |       1   →       1              |      123.35 ms →      123.91 ms   (+0.45%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      122.93 ms →      123.48 ms   (+0.45%) |       1   →       1              |      122.93 ms →      123.48 ms   (+0.45%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      103.72 μs →      116.64 μs  (+12.45%) |       1   →       1              |      103.72 μs →      116.64 μs  (+12.45%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      117.19 ms →      108.93 ms   (-7.05%) |       1   →       1              |      117.19 ms →      108.93 ms   (-7.05%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.18 ms →       13.98 ms (+169.82%) |       1   →       1              |        5.18 ms →       13.98 ms (+169.82%) | 
  ├ sirius::Density::initial_density                                    |      174.35 ms →      175.09 ms   (+0.42%) |       1   →       1              |      174.35 ms →      175.09 ms   (+0.42%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      122.05 ms →      109.41 ms  (-10.35%) |       1   →       1              |      122.05 ms →      109.41 ms  (-10.35%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.89 ms →       11.73 ms (+140.00%) |       2   →       2              |        9.78 ms →       23.46 ms (+140.00%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.20 ms →        9.72 ms   (-4.68%) |       1   →       1              |       10.20 ms →        9.72 ms   (-4.68%) | 
  ├ sirius::Potential::generate                                         |      590.66 ms →      592.05 ms   (+0.24%) |       1   →       1              |      590.66 ms →      592.05 ms   (+0.24%) | 
  │ ├ sirius::Potential::poisson                                        |      136.44 ms →      137.33 ms   (+0.65%) |       1   →       1              |      136.44 ms →      137.33 ms   (+0.65%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.21 ms →       19.50 ms (+274.01%) |       1   →       1              |        5.21 ms →       19.50 ms (+274.01%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.39 ms →       10.21 ms   (-1.74%) |       1   →       1              |       10.39 ms →       10.21 ms   (-1.74%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.89 ms   (+0.16%) |       1   →       1              |        9.88 ms →        9.89 ms   (+0.16%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.89 ms   (+0.16%) |       1   →       1              |        9.88 ms →        9.89 ms   (+0.16%) | 
  │ ├ sirius::Periodic_function::add                                    |      533.95 μs →      545.12 μs   (+2.09%) |       2   →       2              |        1.07 ms →        1.09 ms   (+2.09%) | 
  │ ├ sirius::Potential::xc                                             |       53.53 ms →       54.16 ms   (+1.18%) |       1   →       1              |       53.53 ms →       54.16 ms   (+1.18%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.17 ms →       51.87 ms   (+1.36%) |       1   →       1              |       51.17 ms →       51.87 ms   (+1.36%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.67 ms →        5.57 ms   (-1.78%) |       2   →       2              |       11.33 ms →       11.13 ms   (-1.78%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.17 ms →        5.36 ms   (+3.61%) |       1   →       1              |        5.17 ms →        5.36 ms   (+3.61%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.59 ms →        5.97 ms   (+6.73%) |       1   →       1              |        5.59 ms →        5.97 ms   (+6.73%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.66 ms →       92.67 ms   (+0.02%) |       1   →       1              |       92.66 ms →       92.67 ms   (+0.02%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.02 ms →      299.51 ms   (-0.17%) |       1   →       1              |      300.02 ms →      299.51 ms   (-0.17%) | 
  ├ sirius::Hamiltonian0                                                |        8.45 ms →        8.34 ms   (-1.30%) |       1   →       1              |        8.45 ms →        8.34 ms   (-1.30%) | 
  │ ├ sirius::Local_operator                                            |        8.09 ms →        8.00 ms   (-1.06%) |       1   →       1              |        8.09 ms →        8.00 ms   (-1.06%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms →        4.72 ms   (-0.41%) |       1   →       1              |        4.74 ms →        4.72 ms   (-0.41%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.40 ms →        2.37 ms   (-1.51%) |       1   →       1              |        2.40 ms →        2.37 ms   (-1.51%) | 
  │ ├ sirius::Non_local_operator                                        |       62.56 μs →       62.96 μs   (+0.63%) |       2   →       2              |      125.12 μs →      125.91 μs   (+0.63%) | 
  │ ├ sirius::D_operator::initialize                                    |       99.36 μs →       91.65 μs   (-7.76%) |       1   →       1              |       99.36 μs →       91.65 μs   (-7.76%) | 
+ │ └ sirius::Q_operator::initialize                                    |       80.97 μs →       68.56 μs  (-15.32%) |       1   →       1              |       80.97 μs →       68.56 μs  (-15.32%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.12 s    (+0.96%) |       1   →       1              |        3.09 s  →        3.12 s    (+0.96%) | 
  │ ├ sirius::Hamiltonian_k                                             |      377.47 μs →      365.52 μs   (-3.17%) |       4   →       4              |        1.51 ms →        1.46 ms   (-3.17%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      372.11 μs →      360.67 μs   (-3.08%) |       4   →       4              |        1.49 ms →        1.44 ms   (-3.08%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.47 μs →        3.27 μs   (-5.97%) |       4   →       4              |       13.89 μs →       13.06 μs   (-5.97%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      772.22 ms →      779.67 ms   (+0.97%) |       4   →       4              |        3.09 s  →        3.12 s    (+0.97%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.20 ms →       32.49 ms   (+0.88%) |      16   →      16              |      515.25 ms →      519.78 ms   (+0.88%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.52 ms →       14.54 ms   (+0.13%) |       4   →       4              |       58.07 ms →       58.14 ms   (+0.13%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.29 ms →        5.32 ms   (+0.63%) |       4   →       4              |       21.16 ms →       21.29 ms   (+0.63%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      351.43 ms →      355.76 ms   (+1.23%) |       4   →       4              |        1.41 s  →        1.42 s    (+1.23%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      254.66 ms →      258.02 ms   (+1.32%) |       4   →       4              |        1.02 s  →        1.03 s    (+1.32%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       61.71 ms →       62.82 ms   (+1.80%) |       4   →       4              |      246.86 ms →      251.29 ms   (+1.80%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.15 ms →       16.18 ms   (+0.22%) |       4   →       4              |       64.59 ms →       64.73 ms   (+0.22%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.15 ms →       16.18 ms   (+0.21%) |       4   →       4              |       64.58 ms →       64.72 ms   (+0.21%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       39.00 ms →       40.13 ms   (+2.91%) |       4   →       4              |      156.01 ms →      160.54 ms   (+2.91%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.31 ms →       16.29 ms   (-0.16%) |       4   →       4              |       65.26 ms →       65.16 ms   (-0.16%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.31 ms →       16.29 ms   (-0.16%) |       4   →       4              |       65.24 ms →       65.14 ms   (-0.16%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.23 ms →       55.02 ms   (+5.35%) |       4   →       4              |      208.90 ms →      220.08 ms   (+5.35%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.17 ms →       37.01 ms   (+8.29%) |       4   →       4              |      136.69 ms →      148.02 ms   (+8.29%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.96 ms   (+0.69%) |       4   →       4              |        7.77 ms →        7.83 ms   (+0.69%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.64 ms →       41.49 ms   (+2.09%) |       4   →       4              |      162.57 ms →      165.96 ms   (+2.09%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.54 ms →        8.37 ms  (+11.12%) |       4   →       4              |       30.14 ms →       33.49 ms  (+11.12%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.07 ms →       27.13 ms   (+0.20%) |       8   →       8              |      216.58 ms →      217.03 ms   (+0.20%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.08 ms →       15.14 ms   (+0.36%) |       8   →       8              |      120.67 ms →      121.11 ms   (+0.36%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.04 ms →       15.10 ms   (+0.37%) |       8   →       8              |      120.32 ms →      120.77 ms   (+0.37%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       31.88 ns →       34.38 ns   (+7.84%) |       8   →       8              |      255.00 ns →      275.00 ns   (+7.84%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.87 ms →       14.92 ms   (+0.37%) |       8   →       8              |      118.92 ms →      119.36 ms   (+0.37%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       22.38 ns →       24.00 ns   (+7.26%) |       8   →       8              |      179.00 ns →      192.00 ns   (+7.26%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      123.11 ms →      124.77 ms   (+1.35%) |       4   →       4              |      492.42 ms →      499.07 ms   (+1.35%) | 
  │ │ └ sddk::wf_trans                                                  |       23.49 ms →       23.62 ms   (+0.55%) |       4   →       4              |       93.95 ms →       94.46 ms   (+0.55%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.30 ms →       23.23 ms   (-0.31%) |       4   →       4              |       93.19 ms →       92.90 ms   (-0.31%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      432.00 ns →      372.50 ns  (-13.77%) |       4   →       4              |        1.73 μs →        1.49 μs  (-13.77%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      232.76 s  →      204.92 s   (-11.96%) |       1   →       1              |      232.76 s  →      204.92 s   (-11.96%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.76 ms →        5.70 ms   (-1.06%) |      19   →      19              |      109.39 ms →      108.23 ms   (-1.06%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.93 s  →        8.17 s    (-8.50%) |      26   →      25     (-3.85%) |      232.29 s  →      204.37 s   (-12.02%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.54 ms →        4.76 ms   (+4.93%) |      26   →      25     (-3.85%) |      118.03 ms →      119.09 ms   (+0.89%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.18 ms →        4.40 ms   (+5.33%) |      26   →      25     (-3.85%) |      108.70 ms →      110.09 ms   (+1.28%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      985.45 μs →      992.24 μs   (+0.69%) |      26   →      25     (-3.85%) |       25.62 ms →       24.81 ms   (-3.18%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.31 ms →        2.34 ms   (+1.47%) |      26   →      25     (-3.85%) |       59.93 ms →       58.47 ms   (-2.44%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.31 μs →       64.75 μs   (+0.69%) |      52   →      50     (-3.85%) |        3.34 ms →        3.24 ms   (-3.18%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.58 μs →       95.06 μs   (+0.50%) |      26   →      25     (-3.85%) |        2.46 ms →        2.38 ms   (-3.36%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.61 μs →       66.06 μs   (+0.69%) |      26   →      25     (-3.85%) |        1.71 ms →        1.65 ms   (-3.18%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.84 s  →        6.08 s   (-11.06%) |      26   →      25     (-3.85%) |      177.80 s  →      152.05 s   (-14.48%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      370.73 μs →      320.92 μs  (-13.44%) |     104   →     100     (-3.85%) |       38.56 ms →       32.09 ms  (-16.76%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      365.02 μs →      315.59 μs  (-13.54%) |     104   →     100     (-3.85%) |       37.96 ms →       31.56 ms  (-16.87%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.98 μs →        3.88 μs   (-2.47%) |     104   →     100     (-3.85%) |      413.66 μs →      387.95 μs   (-6.22%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.71 s  →        1.52 s   (-11.06%) |     104   →     100     (-3.85%) |      177.75 s  →      152.02 s   (-14.48%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.07 ms →       12.06 ms   (-0.05%) |     104   →     100     (-3.85%) |        1.26 s  →        1.21 s    (-3.89%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      669.58 ns →      679.28 ns   (+1.45%) |     624   →     600     (-3.85%) |      417.82 μs →      407.57 μs   (-2.45%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (+0.34%) |     104   →     100     (-3.85%) |      190.11 ms →      183.43 ms   (-3.52%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.28 μs →      356.23 μs   (+1.12%) |     104   →     100     (-3.85%) |       36.64 ms →       35.62 ms   (-2.77%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      548.33 μs →      549.95 μs   (+0.30%) |     208   →     200     (-3.85%) |      114.05 ms →      109.99 ms   (-3.56%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.69 s  →        1.50 s   (-11.21%) |     104   →     100     (-3.85%) |      175.37 s  →      149.73 s   (-14.62%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       67.75 ms →       66.03 ms   (-2.53%) |     928   →     980     (+5.60%) |       62.87 s  →       64.71 s    (+2.93%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.04 ms →       42.04 ms   (-2.31%) |     928   →     980     (+5.60%) |       39.94 s  →       41.20 s    (+3.17%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.29 ms →        8.39 ms   (+1.14%) |     928   →     980     (+5.60%) |        7.69 s  →        8.22 s    (+6.80%) | 
+ │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      241.63 μs →      216.32 μs  (-10.47%) |     928   →     980     (+5.60%) |      224.23 ms →      211.99 ms   (-5.46%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.14 ms →        2.10 ms   (-1.74%) |     104   →     100     (-3.85%) |      222.40 ms →      210.12 ms   (-5.52%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.47 ms →        6.48 ms   (+0.08%) |     928   →     980     (+5.60%) |        6.00 s  →        6.35 s    (+5.69%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       87.06 μs →       87.76 μs   (+0.80%) |     928   →     980     (+5.60%) |       80.79 ms →       86.00 ms   (+6.45%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      752.90 μs →      834.77 μs  (+10.87%) |     104   →     100     (-3.85%) |       78.30 ms →       83.48 ms   (+6.61%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.21 ms →        9.26 ms   (+0.54%) |     928   →     980     (+5.60%) |        8.55 s  →        9.08 s    (+6.17%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.65 ms →        5.87 ms   (+3.91%) |     928   →     980     (+5.60%) |        5.24 s  →        5.75 s    (+9.74%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.35%) |     928   →     980     (+5.60%) |        1.41 s  →        1.49 s    (+5.23%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.52 ms →        8.22 ms   (-3.60%) |     928   →     980     (+5.60%) |        7.91 s  →        8.05 s    (+1.80%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.31 ms →        1.33 ms   (+1.62%) |     928   →     980     (+5.60%) |        1.21 s  →        1.30 s    (+7.31%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.32 ms →        7.12 ms   (-2.79%) |    1.86 K →    1.96 K   (+5.60%) |       13.59 s  →       13.95 s    (+2.66%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.50 ms →       25.83 ms   (-6.07%) |     928   →     980     (+5.60%) |       25.52 s  →       25.32 s    (-0.81%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.02 ms →        1.91 ms   (-5.53%) |    1.75 K →    1.86 K   (+6.16%) |        3.53 s  →        3.54 s    (+0.29%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       77.31 ns →       64.02 ns  (-17.19%) |    1.75 K →    1.86 K   (+6.16%) |      135.44 μs →      119.08 μs  (-12.08%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.01 ms →        1.89 ms   (-5.58%) |    1.75 K →    1.86 K   (+6.16%) |        3.52 s  →        3.52 s    (+0.24%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       66.14 ns →       63.94 ns   (-3.33%) |    1.75 K →    1.86 K   (+6.16%) |      115.89 μs →      118.93 μs   (+2.63%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      787.29 μs →      757.05 μs   (-3.84%) |     928   →     980     (+5.60%) |      730.61 ms →      741.91 ms   (+1.55%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      774.78 μs →      721.82 μs   (-6.84%) |     928   →     980     (+5.60%) |      718.99 ms →      707.38 ms   (-1.61%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.29 ms →        4.94 ms   (-6.56%) |    3.61 K →    3.82 K   (+5.88%) |       19.08 s  →       18.88 s    (-1.07%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.60 ms →        3.35 ms   (-6.96%) |    5.26 K →    5.58 K   (+6.16%) |       18.91 s  →       18.68 s    (-1.23%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.32 ms →        5.21 ms   (-2.08%) |     928   →     980     (+5.60%) |        4.93 s  →        5.10 s    (+3.41%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.60 ms →        3.38 ms   (-6.03%) |     928   →     980     (+5.60%) |        3.34 s  →        3.31 s    (-0.77%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       53.58 ns →       66.45 ns  (+24.02%) |     928   →     980     (+5.60%) |       49.72 μs →       65.12 μs  (+30.97%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.58 ms →        3.36 ms   (-6.09%) |     928   →     980     (+5.60%) |        3.32 s  →        3.30 s    (-0.82%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       56.03 ns →       47.48 ns  (-15.27%) |     928   →     980     (+5.60%) |       52.00 μs →       46.53 μs  (-10.52%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       66.30 ms →       33.45 ms  (-49.55%) |     928   →     980     (+5.60%) |       61.53 s  →       32.78 s   (-46.73%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.73 ms →        9.67 ms   (-9.86%) |     907   →     950     (+4.74%) |        9.73 s  →        9.19 s    (-5.59%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       10.36 ms →        9.23 ms  (-10.89%) |     861   →     907     (+5.34%) |        8.92 s  →        8.37 s    (-6.13%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.14 ms →        4.58 ms  (-10.92%) |    1.72 K →    1.81 K   (+5.34%) |        8.86 s  →        8.31 s    (-6.16%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      639.75 μs →      623.93 μs   (-2.47%) |     861   →     907     (+5.34%) |      550.83 ms →      565.91 ms   (+2.74%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.44 ms →       37.16 ms  (-27.75%) |     209   →     339    (+62.20%) |       10.75 s  →       12.60 s   (+17.19%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.12 ms →       21.67 ms  (-36.49%) |     314   →     578    (+84.08%) |       10.72 s  →       12.53 s   (+16.90%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.42 ms →       15.22 ms  (-40.14%) |     419   →     817    (+94.99%) |       10.65 s  →       12.43 s   (+16.72%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      575.36 ns →      696.67 ns  (+21.09%) |     104   →     100     (-3.85%) |       59.84 μs →       69.67 μs  (+16.43%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.13 μs →       23.00 μs   (+3.94%) |      26   →      25     (-3.85%) |      575.40 μs →      575.06 μs   (-0.06%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      586.18 μs →      600.78 μs   (+2.49%) |      26   →      25     (-3.85%) |       15.24 ms →       15.02 ms   (-1.45%) | 
  │ │ ├ sirius::Density::generate                                       |      892.18 ms →      896.76 ms   (+0.51%) |      26   →      25     (-3.85%) |       23.20 s  →       22.42 s    (-3.35%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      522.09 ms →      528.86 ms   (+1.30%) |      26   →      25     (-3.85%) |       13.57 s  →       13.22 s    (-2.60%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.58 ms →       24.93 ms   (+5.75%) |     104   →     100     (-3.85%) |        2.45 s  →        2.49 s    (+1.68%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.49 μs →        8.75 μs   (+3.10%) |     104   →     100     (-3.85%) |      883.08 μs →      875.43 μs   (-0.87%) | 
- │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.53 μs →       16.15 μs  (+11.15%) |       8   →       8              |      116.21 μs →      129.17 μs  (+11.15%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.46 ms →       20.82 ms   (+6.99%) |     104   →     100     (-3.85%) |        2.02 s  →        2.08 s    (+2.87%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.84 ms →       30.23 ms   (+1.32%) |     104   →     100     (-3.85%) |        3.10 s  →        3.02 s    (-2.58%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.44 μs →        9.78 μs   (+3.62%) |     104   →     100     (-3.85%) |      981.80 μs →      978.17 μs   (-0.37%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.11%) |     104   →     100     (-3.85%) |      151.41 ms →      145.42 ms   (-3.95%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.90 ms →       28.26 ms   (+1.30%) |     104   →     100     (-3.85%) |        2.90 s  →        2.83 s    (-2.60%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.77 ms →        4.13 ms   (+9.57%) |     104   →     100     (-3.85%) |      391.77 ms →      412.75 ms   (+5.35%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      606.44 ns →      626.56 ns   (+3.32%) |     104   →     100     (-3.85%) |       63.07 μs →       62.66 μs   (-0.66%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.74 ms →       42.52 ms   (-0.52%) |     104   →     100     (-3.85%) |        4.45 s  →        4.25 s    (-4.35%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.39%) |      26   →      25     (-3.85%) |       42.63 ms →       41.15 ms   (-3.47%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.88 ms →       88.88 ms   (-0.00%) |      26   →      25     (-3.85%) |        2.31 s  →        2.22 s    (-3.85%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.64 ms →       88.65 ms   (+0.01%) |      26   →      25     (-3.85%) |        2.30 s  →        2.22 s    (-3.84%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      274.84 ms →      276.30 ms   (+0.53%) |      26   →      25     (-3.85%) |        7.15 s  →        6.91 s    (-3.34%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      274.84 ms →      276.30 ms   (+0.53%) |      26   →      25     (-3.85%) |        7.15 s  →        6.91 s    (-3.34%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       25.83 ms →       24.38 ms   (-5.62%) |      26   →      25     (-3.85%) |      671.69 ms →      609.56 ms   (-9.25%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      222.50 ms →      225.83 ms   (+1.50%) |      26   →      25     (-3.85%) |        5.79 s  →        5.65 s    (-2.41%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.73 ms →       24.25 ms   (-1.92%) |      26   →      25     (-3.85%) |      642.95 ms →      606.37 ms   (-5.69%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.72 ms →       80.34 ms   (-0.47%) |      26   →      25     (-3.85%) |        2.10 s  →        2.01 s    (-4.30%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       10.94 ms →        7.67 ms  (-29.88%) |      26   →      25     (-3.85%) |      284.43 ms →      191.76 ms  (-32.58%) | 
  │ │ ├ sirius::Density::mix                                            |      217.77 ms →      213.12 ms   (-2.14%) |      26   →      25     (-3.85%) |        5.66 s  →        5.33 s    (-5.90%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      973.36 μs →      982.90 μs   (+0.98%) |      26   →      25     (-3.85%) |       25.31 ms →       24.57 ms   (-2.90%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.65 ms →       10.33 ms   (-3.06%) |     334   →     319     (-4.49%) |        3.56 s  →        3.29 s    (-7.41%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.38 ms →        9.99 ms   (-3.74%) |     334   →     319     (-4.49%) |        3.47 s  →        3.19 s    (-8.06%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.38 ms →        9.99 ms   (-3.74%) |     334   →     319     (-4.49%) |        3.47 s  →        3.19 s    (-8.07%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.29 ms →        6.70 ms   (+6.57%) |      26   →      25     (-3.85%) |      163.56 ms →      167.61 ms   (+2.47%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.44 ms →        5.86 ms   (+7.72%) |      26   →      25     (-3.85%) |      141.44 ms →      146.49 ms   (+3.58%) | 
  │ │ ├ sirius::Potential::generate                                     |      577.90 ms →      579.44 ms   (+0.27%) |      26   →      25     (-3.85%) |       15.03 s  →       14.49 s    (-3.59%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.15 ms →      137.24 ms   (+0.80%) |      26   →      25     (-3.85%) |        3.54 s  →        3.43 s    (-3.07%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.13 ms →       19.52 ms (+280.76%) |      26   →      25     (-3.85%) |      133.27 ms →      487.92 ms (+266.12%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.22 ms →       10.43 ms   (+2.00%) |      26   →      25     (-3.85%) |      265.76 ms →      260.66 ms   (-1.92%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.13 ms →       10.05 ms   (-0.78%) |      26   →      25     (-3.85%) |      263.47 ms →      251.35 ms   (-4.60%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.13 ms →       10.05 ms   (-0.78%) |      26   →      25     (-3.85%) |      263.45 ms →      251.34 ms   (-4.60%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.86 μs →      550.05 μs   (-0.15%) |      52   →      50     (-3.85%) |       28.64 ms →       27.50 ms   (-3.99%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.94 ms →       49.44 ms   (+1.01%) |      26   →      25     (-3.85%) |        1.27 s  →        1.24 s    (-2.88%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.56 ms →       47.04 ms   (+1.03%) |      26   →      25     (-3.85%) |        1.21 s  →        1.18 s    (-2.85%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.07 ms   (+0.53%) |      52   →      50     (-3.85%) |      159.04 ms →      153.74 ms   (-3.33%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.21 ms →        5.35 ms   (+2.56%) |      26   →      25     (-3.85%) |      135.52 ms →      133.64 ms   (-1.39%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.45 ms →        6.61 ms   (+2.45%) |      26   →      25     (-3.85%) |      167.72 ms →      165.22 ms   (-1.49%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.87 ms →       91.02 ms   (+0.16%) |      26   →      25     (-3.85%) |        2.36 s  →        2.28 s    (-3.70%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.07 ms →      292.74 ms   (-0.11%) |      26   →      25     (-3.85%) |        7.62 s  →        7.32 s    (-3.95%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      277.88 ms →      278.25 ms   (+0.13%) |      26   →      25     (-3.85%) |        7.22 s  →        6.96 s    (-3.72%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      277.88 ms →      278.25 ms   (+0.13%) |      26   →      25     (-3.85%) |        7.22 s  →        6.96 s    (-3.72%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       28.49 ms →       27.07 ms   (-4.98%) |      26   →      25     (-3.85%) |      740.75 ms →      676.77 ms   (-8.64%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      221.91 ms →      223.59 ms   (+0.76%) |      26   →      25     (-3.85%) |        5.77 s  →        5.59 s    (-3.12%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.68 ms →       23.79 ms   (+0.44%) |      26   →      25     (-3.85%) |      615.81 ms →      594.72 ms   (-3.42%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.56 ms →        5.38 ms  (-28.81%) |      26   →      25     (-3.85%) |      196.45 ms →      134.47 ms  (-31.55%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.54 ms →       10.29 ms   (-2.38%) |     182   →     175     (-3.85%) |        1.92 s  →        1.80 s    (-6.14%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.90 ms →        9.88 ms   (-0.24%) |     182   →     175     (-3.85%) |        1.80 s  →        1.73 s    (-4.07%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.90 ms →        9.88 ms   (-0.24%) |     182   →     175     (-3.85%) |        1.80 s  →        1.73 s    (-4.07%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.14 ms →       10.64 ms   (-4.51%) |      78   →      75     (-3.85%) |      868.91 ms →      797.83 ms   (-8.18%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.68 ms →       10.22 ms   (-4.35%) |      78   →      75     (-3.85%) |      833.29 ms →      766.41 ms   (-8.03%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.06 ms →        9.95 ms   (-1.13%) |      26   →      25     (-3.85%) |      261.67 ms →      248.77 ms   (-4.93%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      113.05 μs →      177.94 μs  (+57.40%) |      26   →      25     (-3.85%) |        2.94 ms →        4.45 ms  (+51.35%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.82 μs →      172.13 μs  (+59.64%) |      26   →      25     (-3.85%) |        2.80 ms →        4.30 ms  (+53.50%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.39 ms →        5.11 ms   (-5.23%) |       2   →       2              |       10.79 ms →       10.22 ms   (-5.23%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.75 ms →       10.13 ms   (+3.94%) |       6   →       6              |       58.50 ms →       60.81 ms   (+3.94%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.74 ms →        9.83 ms   (+0.97%) |       6   →       6              |       58.42 ms →       58.99 ms   (+0.97%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.74 ms →        9.83 ms   (+0.96%) |       6   →       6              |       58.42 ms →       58.98 ms   (+0.96%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.63 ms →       10.49 ms   (-1.33%) |       3   →       3              |       31.89 ms →       31.47 ms   (-1.33%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.54 ms →       10.07 ms   (-4.44%) |       3   →       3              |       31.61 ms →       30.20 ms   (-4.44%) | 
  ├ sirius::Periodic_function|inner                                     |       10.49 ms →       10.06 ms   (-4.09%) |       2   →       2              |       20.98 ms →       20.12 ms   (-4.09%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.63 ms →       10.01 ms   (+3.95%) |       2   →       2              |       19.27 ms →       20.03 ms   (+3.95%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.63 ms →       10.01 ms   (+3.95%) |       2   →       2              |       19.27 ms →       20.03 ms   (+3.95%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.47 ms →       10.52 ms   (+0.47%) |       1   →       1              |       10.47 ms →       10.52 ms   (+0.47%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.46 ms →       10.48 ms   (+0.18%) |       1   →       1              |       10.46 ms →       10.48 ms   (+0.18%) | 
  └ sirius::finalize                                                    |      283.03 ms →      311.30 ms   (+9.99%) |       1   →       1              |      283.03 ms →      311.30 ms   (+9.99%) | 
  ====================================================================================================================================================================================================
```
