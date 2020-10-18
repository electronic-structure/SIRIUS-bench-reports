# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      243.52 s  →      220.58 s    (-9.42%) |       1   →       1              |      243.52 s  →      220.58 s    (-9.42%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.74 s    (+1.77%) |       1   →       1              |        2.69 s  →        2.74 s    (+1.77%) | 
  ├ sirius::Simulation_context::initialize                              |        2.96 s  →        2.95 s    (-0.24%) |       1   →       1              |        2.96 s  →        2.95 s    (-0.24%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       52.28 ms →      202.91 μs  (-99.61%) |       1   →       1              |       52.28 ms →      202.91 μs  (-99.61%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      154.82 ms →      208.00 ms  (+34.35%) |       1   →       1              |      154.82 ms →      208.00 ms  (+34.35%) | 
- │ │ ├ sirius::Atom_type::init                                         |       65.78 ms →       91.98 ms  (+39.84%) |       2   →       2              |      131.55 ms →      183.96 ms  (+39.84%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.19 ms →       23.96 ms   (+3.32%) |       1   →       1              |       23.19 ms →       23.96 ms   (+3.32%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.40 ms →        6.29 ms   (-1.70%) |       1   →       1              |        6.40 ms →        6.29 ms   (-1.70%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.75 ms →       17.63 ms   (+5.23%) |       1   →       1              |       16.75 ms →       17.63 ms   (+5.23%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.73 ms →       17.61 ms   (+5.24%) |       1   →       1              |       16.73 ms →       17.61 ms   (+5.24%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.14 ms   (-0.03%) |       1   →       1              |        4.14 ms →        4.14 ms   (-0.03%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.17%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.17%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.36 μs →      105.75 μs   (+0.38%) |       1   →       1              |      105.36 μs →      105.75 μs   (+0.38%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.70 s    (-0.22%) |       1   →       1              |        2.71 s  →        2.70 s    (-0.22%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.73 ms →       10.80 ms   (+0.73%) |       1   →       1              |       10.73 ms →       10.80 ms   (+0.73%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.35 ms →        4.44 ms   (+1.88%) |       1   →       1              |        4.35 ms →        4.44 ms   (+1.88%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.34 ms   (-0.07%) |       1   →       1              |        6.34 ms →        6.34 ms   (-0.07%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.32 ms   (-0.08%) |       1   →       1              |        6.32 ms →        6.32 ms   (-0.08%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.83 ms   (+0.02%) |       1   →       1              |        3.83 ms →        3.83 ms   (+0.02%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.31 ms   (-0.49%) |       1   →       1              |        2.32 ms →        2.31 ms   (-0.49%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      102.70 μs →      101.05 μs   (-1.61%) |       1   →       1              |      102.70 μs →      101.05 μs   (-1.61%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.14 ms →       64.63 ms   (+2.36%) |       2   →       2              |      126.29 ms →      129.27 ms   (+2.36%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.18 ms →        5.15 ms   (-0.71%) |       2   →       2              |       10.37 ms →       10.30 ms   (-0.71%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.45 ms →        4.48 ms   (+0.47%) |       1   →       1              |        4.45 ms →        4.48 ms   (+0.47%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.88 ms →       21.75 ms   (-0.60%) |       2   →       2              |       43.76 ms →       43.49 ms   (-0.60%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.00 ms →       14.81 ms   (-1.22%) |       2   →       2              |       29.99 ms →       29.63 ms   (-1.22%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.66 ms →       19.75 ms   (+0.46%) |       4   →       4              |       78.65 ms →       79.02 ms   (+0.46%) | 
  │   ├ sddk::Gvec::init                                                |      173.17 ms →      171.34 ms   (-1.06%) |       2   →       2              |      346.34 ms →      342.68 ms   (-1.06%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.71 ms →      128.99 ms   (-1.31%) |       2   →       2              |      261.42 ms →      257.99 ms   (-1.31%) | 
  │   ├ sddk::Gvec_shells                                               |      179.34 ms →      179.82 ms   (+0.27%) |       1   →       1              |      179.34 ms →      179.82 ms   (+0.27%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.31 ms   (+0.31%) |       1   →       1              |        1.31 ms →        1.31 ms   (+0.31%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      290.97 ms →      301.67 ms   (+3.68%) |       2   →       2              |      581.94 ms →      603.33 ms   (+3.68%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       74.42 ms →       75.22 ms   (+1.08%) |       1   →       1              |       74.42 ms →       75.22 ms   (+1.08%) | 
- │ ├ sirius::K_point::K_point                                          |        2.41 μs →        2.78 μs  (+15.24%) |       4   →       4              |        9.64 μs →       11.11 μs  (+15.24%) | 
  │ └ sirius::K_point_set::initialize                                   |       74.31 ms →       75.12 ms   (+1.08%) |       1   →       1              |       74.31 ms →       75.12 ms   (+1.08%) | 
  │   └ sirius::K_point::initialize                                     |       18.57 ms →       18.76 ms   (+1.03%) |       4   →       4              |       74.26 ms →       75.03 ms   (+1.03%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.06 ms →       14.20 ms   (+0.96%) |       4   →       4              |       56.24 ms →       56.78 ms   (+0.96%) | 
  │     │ └ sddk::Gvec::init                                            |        3.84 ms →        3.84 ms   (+0.00%) |       4   →       4              |       15.35 ms →       15.35 ms   (+0.00%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.39 μs →        8.83 μs   (+5.31%) |       4   →       4              |       33.55 μs →       35.33 μs   (+5.31%) | 
  │     └ sirius::K_point::update                                       |        3.20 ms →        3.26 ms   (+1.84%) |       4   →       4              |       12.80 ms →       13.03 ms   (+1.84%) | 
  │       └ sirius::Beta_projectors                                     |        1.70 ms →        1.76 ms   (+3.90%) |       4   →       4              |        6.79 ms →        7.05 ms   (+3.90%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      942.74 μs →      927.77 μs   (-1.59%) |       4   →       4              |        3.77 ms →        3.71 ms   (-1.59%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.38 ms   (+1.18%) |       2   →       2              |       10.63 ms →       10.75 ms   (+1.18%) | 
  ├ sirius::Potential                                                   |      159.72 ms →      159.06 ms   (-0.41%) |       1   →       1              |      159.72 ms →      159.06 ms   (-0.41%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.80 ms   (+0.08%) |       6   →       6              |       34.76 ms →       34.79 ms   (+0.08%) | 
  │ └ sirius::Potential::update                                         |      124.26 ms →      123.55 ms   (-0.57%) |       1   →       1              |      124.26 ms →      123.55 ms   (-0.57%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.54 ms →      122.84 ms   (-0.57%) |       1   →       1              |      123.54 ms →      122.84 ms   (-0.57%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.22 ms →      107.57 ms   (+1.27%) |       1   →       1              |      106.22 ms →      107.57 ms   (+1.27%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.43 ms →       14.39 ms  (-12.44%) |       1   →       1              |       16.43 ms →       14.39 ms  (-12.44%) | 
  ├ sirius::Density                                                     |      136.88 ms →      135.96 ms   (-0.68%) |       1   →       1              |      136.88 ms →      135.96 ms   (-0.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.63 ms →        5.26 ms   (-6.69%) |       2   →       2              |       11.27 ms →       10.51 ms   (-6.69%) | 
  │ └ sirius::Density::update                                           |      125.32 ms →      125.13 ms   (-0.15%) |       1   →       1              |      125.32 ms →      125.13 ms   (-0.15%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.87 ms →      124.72 ms   (-0.12%) |       1   →       1              |      124.87 ms →      124.72 ms   (-0.12%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      115.71 μs →      104.10 μs  (-10.04%) |       1   →       1              |      115.71 μs →      104.10 μs  (-10.04%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.94 ms →      109.62 ms   (-0.29%) |       1   →       1              |      109.94 ms →      109.62 ms   (-0.29%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.37 ms →       14.54 ms   (+1.16%) |       1   →       1              |       14.37 ms →       14.54 ms   (+1.16%) | 
  ├ sirius::Density::initial_density                                    |      176.76 ms →      175.25 ms   (-0.86%) |       1   →       1              |      176.76 ms →      175.25 ms   (-0.86%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.89 ms →      109.36 ms   (+0.44%) |       1   →       1              |      108.89 ms →      109.36 ms   (+0.44%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       12.66 ms →       11.67 ms   (-7.81%) |       2   →       2              |       25.32 ms →       23.34 ms   (-7.81%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.09 ms →       10.26 ms   (+1.69%) |       1   →       1              |       10.09 ms →       10.26 ms   (+1.69%) | 
  ├ sirius::Potential::generate                                         |      593.83 ms →      594.15 ms   (+0.05%) |       1   →       1              |      593.83 ms →      594.15 ms   (+0.05%) | 
  │ ├ sirius::Potential::poisson                                        |      139.06 ms →      138.48 ms   (-0.42%) |       1   →       1              |      139.06 ms →      138.48 ms   (-0.42%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       20.71 ms →       19.83 ms   (-4.25%) |       1   →       1              |       20.71 ms →       19.83 ms   (-4.25%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.28 ms →       10.87 ms   (+5.72%) |       1   →       1              |       10.28 ms →       10.87 ms   (+5.72%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →       10.85 ms   (+9.73%) |       1   →       1              |        9.88 ms →       10.85 ms   (+9.73%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →       10.85 ms   (+9.74%) |       1   →       1              |        9.88 ms →       10.85 ms   (+9.74%) | 
  │ ├ sirius::Periodic_function::add                                    |      550.93 μs →      538.29 μs   (-2.29%) |       2   →       2              |        1.10 ms →        1.08 ms   (-2.29%) | 
  │ ├ sirius::Potential::xc                                             |       53.64 ms →       53.72 ms   (+0.15%) |       1   →       1              |       53.64 ms →       53.72 ms   (+0.15%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.36 ms →       51.41 ms   (+0.11%) |       1   →       1              |       51.36 ms →       51.41 ms   (+0.11%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.58 ms →        5.61 ms   (+0.55%) |       2   →       2              |       11.16 ms →       11.22 ms   (+0.55%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.43 ms →        5.51 ms   (+1.32%) |       1   →       1              |        5.43 ms →        5.51 ms   (+1.32%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.17 ms →        5.93 ms   (-3.86%) |       1   →       1              |        6.17 ms →        5.93 ms   (-3.86%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.60 ms →       93.59 ms   (+1.07%) |       1   →       1              |       92.60 ms →       93.59 ms   (+1.07%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.95 ms →      300.02 ms   (+0.02%) |       1   →       1              |      299.95 ms →      300.02 ms   (+0.02%) | 
  ├ sirius::Hamiltonian0                                                |        8.34 ms →        8.35 ms   (+0.22%) |       1   →       1              |        8.34 ms →        8.35 ms   (+0.22%) | 
  │ ├ sirius::Local_operator                                            |        7.99 ms →        8.00 ms   (+0.21%) |       1   →       1              |        7.99 ms →        8.00 ms   (+0.21%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.70 ms →        4.75 ms   (+1.06%) |       1   →       1              |        4.70 ms →        4.75 ms   (+1.06%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.37 ms →        2.34 ms   (-1.19%) |       1   →       1              |        2.37 ms →        2.34 ms   (-1.19%) | 
  │ ├ sirius::Non_local_operator                                        |       63.94 μs →       63.43 μs   (-0.80%) |       2   →       2              |      127.88 μs →      126.85 μs   (-0.80%) | 
  │ ├ sirius::D_operator::initialize                                    |       97.90 μs →       96.87 μs   (-1.05%) |       1   →       1              |       97.90 μs →       96.87 μs   (-1.05%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.67 μs →       68.06 μs   (-0.88%) |       1   →       1              |       68.67 μs →       68.06 μs   (-0.88%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.12 s  →        3.09 s    (-0.73%) |       1   →       1              |        3.12 s  →        3.09 s    (-0.73%) | 
  │ ├ sirius::Hamiltonian_k                                             |      371.70 μs →      363.25 μs   (-2.27%) |       4   →       4              |        1.49 ms →        1.45 ms   (-2.27%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      366.59 μs →      358.07 μs   (-2.32%) |       4   →       4              |        1.47 ms →        1.43 ms   (-2.32%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.39 μs →        3.48 μs   (+2.63%) |       4   →       4              |       13.57 μs →       13.93 μs   (+2.63%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      779.05 ms →      773.35 ms   (-0.73%) |       4   →       4              |        3.12 s  →        3.09 s    (-0.73%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.37 ms →       33.20 ms   (+2.56%) |      16   →      16              |      517.88 ms →      531.15 ms   (+2.56%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.46 ms →       14.54 ms   (+0.59%) |       4   →       4              |       57.84 ms →       58.18 ms   (+0.59%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.30 ms →        5.38 ms   (+1.36%) |       4   →       4              |       21.22 ms →       21.51 ms   (+1.36%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.31 ms →      355.29 ms   (-0.29%) |       4   →       4              |        1.43 s  →        1.42 s    (-0.29%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      258.88 ms →      258.72 ms   (-0.06%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.06%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.41 ms →       63.30 ms   (-0.17%) |       4   →       4              |      253.63 ms →      253.19 ms   (-0.17%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.23 ms →       16.95 ms   (+4.42%) |       4   →       4              |       64.91 ms →       67.78 ms   (+4.42%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.23 ms →       16.94 ms   (+4.42%) |       4   →       4              |       64.90 ms →       67.77 ms   (+4.42%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.68 ms →       40.00 ms   (-1.67%) |       4   →       4              |      162.70 ms →      159.99 ms   (-1.67%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.03 ms →       16.67 ms   (+4.00%) |       4   →       4              |       64.12 ms →       66.69 ms   (+4.00%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.03 ms →       16.67 ms   (+4.00%) |       4   →       4              |       64.11 ms →       66.67 ms   (+4.00%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       55.56 ms →       54.05 ms   (-2.71%) |       4   →       4              |      222.22 ms →      216.21 ms   (-2.71%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       37.52 ms →       36.02 ms   (-3.98%) |       4   →       4              |      150.06 ms →      144.09 ms   (-3.98%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.93 ms   (-1.16%) |       4   →       4              |        7.81 ms →        7.72 ms   (-1.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.08 ms →       40.17 ms   (-2.23%) |       4   →       4              |      164.34 ms →      160.68 ms   (-2.23%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.94 ms →        7.04 ms  (-11.26%) |       4   →       4              |       31.75 ms →       28.18 ms  (-11.26%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.17 ms →       27.21 ms   (+0.16%) |       8   →       8              |      217.36 ms →      217.71 ms   (+0.16%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.35 ms →       14.83 ms   (-3.39%) |       8   →       8              |      122.79 ms →      118.64 ms   (-3.39%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.31 ms →       14.79 ms   (-3.39%) |       8   →       8              |      122.44 ms →      118.29 ms   (-3.39%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       29.38 ns →       26.75 ns   (-8.94%) |       8   →       8              |      235.00 ns →      214.00 ns   (-8.94%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.10 ms →       14.61 ms   (-3.27%) |       8   →       8              |      120.79 ms →      116.84 ms   (-3.27%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.87 ns →       31.25 ns  (+36.61%) |       8   →       8              |      183.00 ns →      250.00 ns  (+36.61%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      123.50 ms →      118.34 ms   (-4.18%) |       4   →       4              |      494.01 ms →      473.34 ms   (-4.18%) | 
  │ │ └ sddk::wf_trans                                                  |       23.57 ms →       23.57 ms   (+0.02%) |       4   →       4              |       94.27 ms →       94.29 ms   (+0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.25 ms →       23.38 ms   (+0.55%) |       4   →       4              |       93.00 ms →       93.52 ms   (+0.55%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      460.75 ns →      361.25 ns  (-21.60%) |       4   →       4              |        1.84 μs →        1.45 μs  (-21.60%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      232.79 s  →      209.84 s    (-9.86%) |       1   →       1              |      232.79 s  →      209.84 s    (-9.86%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.68 ms   (-2.68%) |      19   →      19              |      110.96 ms →      107.98 ms   (-2.68%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.94 s  →        7.76 s   (-13.17%) |      26   →      27     (+3.85%) |      232.36 s  →      209.51 s    (-9.84%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.46 ms →        4.54 ms   (+1.82%) |      26   →      27     (+3.85%) |      116.03 ms →      122.68 ms   (+5.74%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.11 ms →        4.19 ms   (+1.93%) |      26   →      27     (+3.85%) |      106.79 ms →      113.03 ms   (+5.85%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      967.76 μs →      972.42 μs   (+0.48%) |      26   →      27     (+3.85%) |       25.16 ms →       26.26 ms   (+4.35%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        2.33 ms   (+3.28%) |      26   →      27     (+3.85%) |       58.57 ms →       62.82 ms   (+7.26%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.63 μs →       64.50 μs   (-0.20%) |      52   →      54     (+3.85%) |        3.36 ms →        3.48 ms   (+3.64%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.58 μs →       93.29 μs   (-0.31%) |      26   →      27     (+3.85%) |        2.43 ms →        2.52 ms   (+3.52%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       64.88 μs →       67.03 μs   (+3.31%) |      26   →      27     (+3.85%) |        1.69 ms →        1.81 ms   (+7.29%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.83 s  →        5.66 s   (-17.04%) |      26   →      27     (+3.85%) |      177.46 s  →      152.88 s   (-13.85%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      332.62 μs →      323.01 μs   (-2.89%) |     104   →     108     (+3.85%) |       34.59 ms →       34.89 ms   (+0.85%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      327.13 μs →      317.68 μs   (-2.89%) |     104   →     108     (+3.85%) |       34.02 ms →       34.31 ms   (+0.85%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.97 μs →        3.82 μs   (-3.70%) |     104   →     108     (+3.85%) |      412.40 μs →      412.40 μs   (-0.00%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.71 s  →        1.42 s   (-17.05%) |     104   →     108     (+3.85%) |      177.42 s  →      152.84 s   (-13.86%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.88 ms →       11.99 ms   (+0.87%) |     104   →     108     (+3.85%) |        1.24 s  →        1.29 s    (+4.75%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      665.13 ns →      667.89 ns   (+0.42%) |     624   →     648     (+3.85%) |      415.04 μs →      432.79 μs   (+4.28%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (+0.22%) |     104   →     108     (+3.85%) |      190.06 ms →      197.80 ms   (+4.07%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.28 μs →      354.67 μs   (+0.68%) |     104   →     108     (+3.85%) |       36.64 ms →       38.30 ms   (+4.55%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      548.25 μs →      548.33 μs   (+0.02%) |     208   →     216     (+3.85%) |      114.04 ms →      118.44 ms   (+3.86%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.68 s  →        1.39 s   (-17.29%) |     104   →     108     (+3.85%) |      175.06 s  →      150.37 s   (-14.10%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.69 ms →       69.34 ms   (-0.51%) |     910   →     952     (+4.62%) |       63.42 s  →       66.01 s    (+4.08%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.42 ms →       44.39 ms   (-0.08%) |     910   →     952     (+4.62%) |       40.42 s  →       42.26 s    (+4.53%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.67 ms →        8.77 ms   (+1.21%) |     910   →     952     (+4.62%) |        7.89 s  →        8.35 s    (+5.88%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      233.64 μs →      220.99 μs   (-5.42%) |     910   →     952     (+4.62%) |      212.62 ms →      210.38 ms   (-1.05%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.03 ms →        1.93 ms   (-4.72%) |     104   →     108     (+3.85%) |      210.83 ms →      208.61 ms   (-1.05%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.84 ms →        6.78 ms   (-0.89%) |     910   →     952     (+4.62%) |        6.23 s  →        6.46 s    (+3.69%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       89.14 μs →       84.17 μs   (-5.57%) |     910   →     952     (+4.62%) |       81.12 ms →       80.13 ms   (-1.21%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      756.74 μs →      718.99 μs   (-4.99%) |     104   →     108     (+3.85%) |       78.70 ms →       77.65 ms   (-1.33%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.75 ms →        9.70 ms   (-0.49%) |     910   →     952     (+4.62%) |        8.87 s  →        9.23 s    (+4.10%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.12 ms →        6.09 ms   (-0.49%) |     910   →     952     (+4.62%) |        5.57 s  →        5.80 s    (+4.10%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.10%) |     910   →     952     (+4.62%) |        1.38 s  →        1.44 s    (+4.51%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.81 ms →        8.54 ms   (-3.12%) |     910   →     952     (+4.62%) |        8.02 s  →        8.13 s    (+1.35%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.45 ms →        1.27 ms  (-12.21%) |     910   →     952     (+4.62%) |        1.32 s  →        1.21 s    (-8.16%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.46 ms →        7.43 ms   (-0.30%) |    1.82 K →    1.90 K   (+4.62%) |       13.57 s  →       14.16 s    (+4.31%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.92 ms →       26.99 ms   (-3.34%) |     910   →     952     (+4.62%) |       25.41 s  →       25.70 s    (+1.12%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.05 ms →        1.96 ms   (-4.48%) |    1.72 K →    1.80 K   (+4.66%) |        3.52 s  →        3.52 s    (-0.02%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       65.93 ns →       67.94 ns   (+3.06%) |    1.72 K →    1.80 K   (+4.66%) |      113.14 μs →      122.03 μs   (+7.86%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.04 ms →        1.95 ms   (-4.39%) |    1.72 K →    1.80 K   (+4.66%) |        3.50 s  →        3.50 s    (+0.07%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       60.09 ns →       65.13 ns   (+8.39%) |    1.72 K →    1.80 K   (+4.66%) |      103.12 μs →      116.98 μs  (+13.44%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      804.81 μs →      798.92 μs   (-0.73%) |     910   →     952     (+4.62%) |      732.38 ms →      760.58 ms   (+3.85%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      771.11 μs →      749.86 μs   (-2.76%) |     910   →     952     (+4.62%) |      701.71 ms →      713.86 ms   (+1.73%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.37 ms →        5.19 ms   (-3.36%) |    3.54 K →    3.70 K   (+4.64%) |       19.00 s  →       19.21 s    (+1.12%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.66 ms →        3.53 ms   (-3.63%) |    5.15 K →    5.39 K   (+4.66%) |       18.85 s  →       19.01 s    (+0.87%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.49 ms →        5.23 ms   (-4.73%) |     910   →     952     (+4.62%) |        4.99 s  →        4.97 s    (-0.33%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.72 ms →        3.50 ms   (-6.06%) |     910   →     952     (+4.62%) |        3.39 s  →        3.33 s    (-1.73%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       65.96 ns →       56.16 ns  (-14.86%) |     910   →     952     (+4.62%) |       60.02 μs →       53.46 μs  (-10.93%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.71 ms →        3.48 ms   (-6.10%) |     910   →     952     (+4.62%) |        3.38 s  →        3.32 s    (-1.77%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       49.43 ns →       48.68 ns   (-1.51%) |     910   →     952     (+4.62%) |       44.98 μs →       46.35 μs   (+3.03%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       67.08 ms →       33.37 ms  (-50.26%) |     910   →     952     (+4.62%) |       61.04 s  →       31.77 s   (-47.96%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.59 ms →        9.94 ms   (-6.16%) |     890   →     925     (+3.93%) |        9.43 s  →        9.20 s    (-2.47%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.22 ms →        9.52 ms   (-6.84%) |     844   →     882     (+4.50%) |        8.62 s  →        8.40 s    (-2.64%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.08 ms →        4.73 ms   (-6.94%) |    1.69 K →    1.76 K   (+4.50%) |        8.57 s  →        8.34 s    (-2.75%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      635.42 μs →      636.33 μs   (+0.14%) |     844   →     882     (+4.50%) |      536.29 ms →      561.24 ms   (+4.65%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.34 ms →       36.59 ms  (-28.73%) |     209   →     347    (+66.03%) |       10.73 s  →       12.70 s   (+18.33%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.06 ms →       21.54 ms  (-36.76%) |     314   →     586    (+86.62%) |       10.70 s  →       12.62 s   (+18.03%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.39 ms →       15.20 ms  (-40.13%) |     419   →     825    (+96.90%) |       10.64 s  →       12.54 s   (+17.89%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      590.93 ns →      573.65 ns   (-2.92%) |     104   →     108     (+3.85%) |       61.46 μs →       61.95 μs   (+0.81%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.02 μs →       22.38 μs   (+1.67%) |      26   →      27     (+3.85%) |      572.41 μs →      604.34 μs   (+5.58%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      586.31 μs →      595.98 μs   (+1.65%) |      26   →      27     (+3.85%) |       15.24 ms →       16.09 ms   (+5.56%) | 
  │ │ ├ sirius::Density::generate                                       |      901.58 ms →      892.97 ms   (-0.96%) |      26   →      27     (+3.85%) |       23.44 s  →       24.11 s    (+2.85%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      528.34 ms →      523.26 ms   (-0.96%) |      26   →      27     (+3.85%) |       13.74 s  →       14.13 s    (+2.85%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.63 ms →       24.28 ms   (-1.39%) |     104   →     108     (+3.85%) |        2.56 s  →        2.62 s    (+2.40%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.27 μs →        8.86 μs   (+7.10%) |     104   →     108     (+3.85%) |      860.55 μs →      957.11 μs  (+11.22%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.10 μs →       16.10 μs   (+6.61%) |       8   →       8              |      120.78 μs →      128.76 μs   (+6.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.49 ms →       20.16 ms   (-1.60%) |     104   →     108     (+3.85%) |        2.13 s  →        2.18 s    (+2.19%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.35 ms →       29.63 ms   (-2.40%) |     104   →     108     (+3.85%) |        3.16 s  →        3.20 s    (+1.36%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.44 μs →        9.62 μs   (+1.93%) |     104   →     108     (+3.85%) |      981.83 μs →        1.04 ms   (+5.85%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (+0.08%) |     104   →     108     (+3.85%) |      150.93 ms →      156.86 ms   (+3.93%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.42 ms →       27.70 ms   (-2.53%) |     104   →     108     (+3.85%) |        2.96 s  →        2.99 s    (+1.22%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.29 ms →        3.57 ms  (-16.69%) |     104   →     108     (+3.85%) |      445.73 ms →      385.63 ms  (-13.48%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      594.80 ns →      534.09 ns  (-10.21%) |     104   →     108     (+3.85%) |       61.86 μs →       57.68 μs   (-6.75%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.72 ms →       42.64 ms   (-0.19%) |     104   →     108     (+3.85%) |        4.44 s  →        4.61 s    (+3.65%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.10%) |      26   →      27     (+3.85%) |       42.68 ms →       44.37 ms   (+3.96%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.86 ms →       88.89 ms   (+0.03%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.87%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.63 ms →       88.65 ms   (+0.02%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.87%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.21 ms →      277.43 ms   (-0.99%) |      26   →      27     (+3.85%) |        7.29 s  →        7.49 s    (+2.82%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.21 ms →      277.43 ms   (-0.99%) |      26   →      27     (+3.85%) |        7.29 s  →        7.49 s    (+2.82%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.17 ms →       24.34 ms   (+0.71%) |      26   →      27     (+3.85%) |      628.47 ms →      657.26 ms   (+4.58%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.42 ms →      227.59 ms   (-1.23%) |      26   →      27     (+3.85%) |        5.99 s  →        6.14 s    (+2.57%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.86 ms →       23.73 ms   (-0.53%) |      26   →      27     (+3.85%) |      620.23 ms →      640.70 ms   (+3.30%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.59 ms →       80.53 ms   (-1.30%) |      26   →      27     (+3.85%) |        2.12 s  →        2.17 s    (+2.49%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.84 ms →        8.12 ms   (+3.56%) |      26   →      27     (+3.85%) |      203.80 ms →      219.16 ms   (+7.54%) | 
  │ │ ├ sirius::Density::mix                                            |      219.21 ms →      215.32 ms   (-1.77%) |      26   →      27     (+3.85%) |        5.70 s  →        5.81 s    (+2.00%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      951.64 μs →      963.98 μs   (+1.30%) |      26   →      27     (+3.85%) |       24.74 ms →       26.03 ms   (+5.19%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.73 ms →       10.32 ms   (-3.83%) |     334   →     349     (+4.49%) |        3.58 s  →        3.60 s    (+0.49%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.46 ms →        9.99 ms   (-4.47%) |     334   →     349     (+4.49%) |        3.49 s  →        3.49 s    (-0.18%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.45 ms →        9.99 ms   (-4.47%) |     334   →     349     (+4.49%) |        3.49 s  →        3.49 s    (-0.18%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.64 ms →        6.81 ms   (+2.51%) |      26   →      27     (+3.85%) |      172.74 ms →      183.88 ms   (+6.45%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.85 ms →        5.95 ms   (+1.84%) |      26   →      27     (+3.85%) |      151.97 ms →      160.72 ms   (+5.76%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.48 ms →      578.71 ms   (-0.30%) |      26   →      27     (+3.85%) |       15.09 s  →       15.63 s    (+3.53%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.73 ms →      137.18 ms   (-1.12%) |      26   →      27     (+3.85%) |        3.61 s  →        3.70 s    (+2.69%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       20.35 ms →       19.17 ms   (-5.78%) |      26   →      27     (+3.85%) |      529.03 ms →      517.63 ms   (-2.15%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.32 ms →       10.28 ms   (-0.32%) |      26   →      27     (+3.85%) |      268.27 ms →      277.68 ms   (+3.51%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.06 ms →        9.92 ms   (-1.33%) |      26   →      27     (+3.85%) |      261.48 ms →      267.92 ms   (+2.46%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.06 ms →        9.92 ms   (-1.33%) |      26   →      27     (+3.85%) |      261.46 ms →      267.90 ms   (+2.46%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      547.47 μs →      548.16 μs   (+0.13%) |      52   →      54     (+3.85%) |       28.47 ms →       29.60 ms   (+3.98%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.08 ms →       48.95 ms   (-0.27%) |      26   →      27     (+3.85%) |        1.28 s  →        1.32 s    (+3.57%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.76 ms →       46.59 ms   (-0.35%) |      26   →      27     (+3.85%) |        1.22 s  →        1.26 s    (+3.48%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        3.01 ms   (-0.59%) |      52   →      54     (+3.85%) |      157.34 ms →      162.43 ms   (+3.24%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.40 ms →        5.35 ms   (-0.86%) |      26   →      27     (+3.85%) |      140.40 ms →      144.54 ms   (+2.95%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.76 ms →        6.68 ms   (-1.20%) |      26   →      27     (+3.85%) |      175.72 ms →      180.28 ms   (+2.60%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       90.85 ms   (-0.06%) |      26   →      27     (+3.85%) |        2.36 s  →        2.45 s    (+3.78%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.61 ms →      292.67 ms   (+0.02%) |      26   →      27     (+3.85%) |        7.61 s  →        7.90 s    (+3.87%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      284.42 ms →      283.53 ms   (-0.31%) |      26   →      27     (+3.85%) |        7.39 s  →        7.66 s    (+3.52%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      284.42 ms →      283.53 ms   (-0.31%) |      26   →      27     (+3.85%) |        7.39 s  →        7.66 s    (+3.52%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.18 ms →       27.28 ms   (+0.39%) |      26   →      27     (+3.85%) |      706.58 ms →      736.63 ms   (+4.25%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      229.56 ms →      228.58 ms   (-0.43%) |      26   →      27     (+3.85%) |        5.97 s  →        6.17 s    (+3.40%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.86 ms →       23.88 ms   (+0.07%) |      26   →      27     (+3.85%) |      620.40 ms →      644.71 ms   (+3.92%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.49 ms →        5.92 ms   (+7.79%) |      26   →      27     (+3.85%) |      142.84 ms →      159.88 ms  (+11.93%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.31 ms →       10.38 ms   (+0.69%) |     182   →     189     (+3.85%) |        1.88 s  →        1.96 s    (+4.56%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.94 ms →        9.90 ms   (-0.38%) |     182   →     189     (+3.85%) |        1.81 s  →        1.87 s    (+3.45%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.94 ms →        9.90 ms   (-0.38%) |     182   →     189     (+3.85%) |        1.81 s  →        1.87 s    (+3.45%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.98 ms →       10.92 ms   (-0.63%) |      78   →      81     (+3.85%) |      856.81 ms →      884.14 ms   (+3.19%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.72 ms →       10.27 ms   (-4.20%) |      78   →      81     (+3.85%) |      836.03 ms →      831.69 ms   (-0.52%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms →       10.11 ms   (+1.64%) |      26   →      27     (+3.85%) |      258.70 ms →      273.05 ms   (+5.55%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      125.00 μs →      113.05 μs   (-9.56%) |      26   →      27     (+3.85%) |        3.25 ms →        3.05 ms   (-6.08%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      119.84 μs →      108.09 μs   (-9.80%) |      26   →      27     (+3.85%) |        3.12 ms →        2.92 ms   (-6.33%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.14 ms →        5.11 ms   (-0.51%) |       2   →       2              |       10.27 ms →       10.22 ms   (-0.51%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.17 ms →       10.15 ms   (-0.19%) |       6   →       6              |       61.03 ms →       60.91 ms   (-0.19%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.03 ms →        9.68 ms   (-3.49%) |       6   →       6              |       60.18 ms →       58.08 ms   (-3.49%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.03 ms →        9.68 ms   (-3.49%) |       6   →       6              |       60.18 ms →       58.08 ms   (-3.49%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.97 ms →       10.57 ms   (-3.65%) |       3   →       3              |       32.90 ms →       31.70 ms   (-3.65%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.83 ms →       10.08 ms   (-6.95%) |       3   →       3              |       32.49 ms →       30.24 ms   (-6.95%) | 
  ├ sirius::Periodic_function|inner                                     |       10.35 ms →       10.10 ms   (-2.34%) |       2   →       2              |       20.69 ms →       20.21 ms   (-2.34%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.34 ms →        9.74 ms   (-5.75%) |       2   →       2              |       20.67 ms →       19.49 ms   (-5.75%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.34 ms →        9.74 ms   (-5.74%) |       2   →       2              |       20.67 ms →       19.49 ms   (-5.74%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.58 ms →       10.59 ms   (+0.09%) |       1   →       1              |       10.58 ms →       10.59 ms   (+0.09%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.52 ms →       10.20 ms   (-3.10%) |       1   →       1              |       10.52 ms →       10.20 ms   (-3.10%) | 
  └ sirius::finalize                                                    |      272.02 ms →      288.89 ms   (+6.20%) |       1   →       1              |      272.02 ms →      288.89 ms   (+6.20%) | 
  ====================================================================================================================================================================================================
```
