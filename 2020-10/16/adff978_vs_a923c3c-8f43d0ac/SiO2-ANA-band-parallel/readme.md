# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      242.60 s  →      215.89 s   (-11.01%) |       1   →       1              |      242.60 s  →      215.89 s   (-11.01%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.81 s    (+2.97%) |       1   →       1              |        2.73 s  →        2.81 s    (+2.97%) | 
  ├ sirius::Simulation_context::initialize                              |        2.94 s  →        3.03 s    (+3.22%) |       1   →       1              |        2.94 s  →        3.03 s    (+3.22%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       13.83 ms →      226.98 μs  (-98.36%) |       1   →       1              |       13.83 ms →      226.98 μs  (-98.36%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      158.94 ms →      259.26 ms  (+63.12%) |       1   →       1              |      158.94 ms →      259.26 ms  (+63.12%) | 
- │ │ ├ sirius::Atom_type::init                                         |       67.84 ms →      117.30 ms  (+72.90%) |       2   →       2              |      135.68 ms →      234.59 ms  (+72.90%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.19 ms →       24.59 ms   (+6.04%) |       1   →       1              |       23.19 ms →       24.59 ms   (+6.04%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.30 ms →        6.38 ms   (+1.26%) |       1   →       1              |        6.30 ms →        6.38 ms   (+1.26%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.85 ms →       18.17 ms   (+7.86%) |       1   →       1              |       16.85 ms →       18.17 ms   (+7.86%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.83 ms →       18.15 ms   (+7.86%) |       1   →       1              |       16.83 ms →       18.15 ms   (+7.86%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.17 ms   (+0.76%) |       1   →       1              |        4.14 ms →        4.17 ms   (+0.76%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.42%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.42%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.35 μs →      100.82 μs   (+0.47%) |       1   →       1              |      100.35 μs →      100.82 μs   (+0.47%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.73 s    (+0.29%) |       1   →       1              |        2.72 s  →        2.73 s    (+0.29%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.81 ms →       10.75 ms   (-0.60%) |       1   →       1              |       10.81 ms →       10.75 ms   (-0.60%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.36 ms   (-1.72%) |       1   →       1              |        4.44 ms →        4.36 ms   (-1.72%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.35 ms   (+0.12%) |       1   →       1              |        6.34 ms →        6.35 ms   (+0.12%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.33 ms   (+0.12%) |       1   →       1              |        6.32 ms →        6.33 ms   (+0.12%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.84 ms →        3.83 ms   (-0.38%) |       1   →       1              |        3.84 ms →        3.83 ms   (-0.38%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.34 ms   (+1.29%) |       1   →       1              |        2.31 ms →        2.34 ms   (+1.29%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.43 μs →       99.68 μs   (+0.26%) |       1   →       1              |       99.43 μs →       99.68 μs   (+0.26%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.22 ms →       64.96 ms   (+1.16%) |       2   →       2              |      128.45 ms →      129.93 ms   (+1.16%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.16 ms   (+0.23%) |       2   →       2              |       10.29 ms →       10.31 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.48 ms   (+0.44%) |       1   →       1              |        4.46 ms →        4.48 ms   (+0.44%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.72 ms →       21.77 ms   (+0.22%) |       2   →       2              |       43.45 ms →       43.54 ms   (+0.22%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.83 ms   (-0.10%) |       2   →       2              |       29.69 ms →       29.66 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.91 ms →       19.77 ms   (-0.72%) |       4   →       4              |       79.64 ms →       79.06 ms   (-0.72%) | 
  │   ├ sddk::Gvec::init                                                |      171.26 ms →      175.42 ms   (+2.43%) |       2   →       2              |      342.52 ms →      350.84 ms   (+2.43%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.02 ms →      133.03 ms   (+3.11%) |       2   →       2              |      258.03 ms →      266.06 ms   (+3.11%) | 
  │   ├ sddk::Gvec_shells                                               |      165.70 ms →      165.52 ms   (-0.11%) |       1   →       1              |      165.70 ms →      165.52 ms   (-0.11%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.65%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.65%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      290.79 ms →      300.68 ms   (+3.40%) |       2   →       2              |      581.59 ms →      601.37 ms   (+3.40%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       77.20 ms →       75.94 ms   (-1.63%) |       1   →       1              |       77.20 ms →       75.94 ms   (-1.63%) | 
  │ ├ sirius::K_point::K_point                                          |        2.77 μs →        2.54 μs   (-8.28%) |       4   →       4              |       11.09 μs →       10.17 μs   (-8.28%) | 
  │ └ sirius::K_point_set::initialize                                   |       77.09 ms →       75.84 ms   (-1.62%) |       1   →       1              |       77.09 ms →       75.84 ms   (-1.62%) | 
  │   └ sirius::K_point::initialize                                     |       19.26 ms →       18.94 ms   (-1.68%) |       4   →       4              |       77.04 ms →       75.75 ms   (-1.68%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.81 ms →       14.38 ms   (-2.90%) |       4   →       4              |       59.23 ms →       57.52 ms   (-2.90%) | 
  │     │ └ sddk::Gvec::init                                            |        3.83 ms →        3.85 ms   (+0.62%) |       4   →       4              |       15.30 ms →       15.40 ms   (+0.62%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.13 μs →        9.62 μs   (+5.29%) |       4   →       4              |       36.54 μs →       38.47 μs   (+5.29%) | 
  │     └ sirius::K_point::update                                       |        3.17 ms →        3.26 ms   (+2.97%) |       4   →       4              |       12.68 ms →       13.05 ms   (+2.97%) | 
  │       └ sirius::Beta_projectors                                     |        1.68 ms →        1.76 ms   (+4.90%) |       4   →       4              |        6.72 ms →        7.05 ms   (+4.90%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      932.29 μs →      930.29 μs   (-0.21%) |       4   →       4              |        3.73 ms →        3.72 ms   (-0.21%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.28 ms →        5.45 ms   (+3.11%) |       2   →       2              |       10.57 ms →       10.90 ms   (+3.11%) | 
  ├ sirius::Potential                                                   |      159.17 ms →      155.49 ms   (-2.32%) |       1   →       1              |      159.17 ms →      155.49 ms   (-2.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.83 ms   (-0.39%) |       6   →       6              |       35.12 ms →       34.98 ms   (-0.39%) | 
  │ └ sirius::Potential::update                                         |      123.33 ms →      119.75 ms   (-2.90%) |       1   →       1              |      123.33 ms →      119.75 ms   (-2.90%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.55 ms →      119.01 ms   (-2.89%) |       1   →       1              |      122.55 ms →      119.01 ms   (-2.89%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      114.54 ms →      111.62 ms   (-2.55%) |       1   →       1              |      114.54 ms →      111.62 ms   (-2.55%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.14 ms →        6.53 ms   (-8.52%) |       1   →       1              |        7.14 ms →        6.53 ms   (-8.52%) | 
  ├ sirius::Density                                                     |      135.89 ms →      129.59 ms   (-4.64%) |       1   →       1              |      135.89 ms →      129.59 ms   (-4.64%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.21 ms →        5.26 ms   (+1.04%) |       2   →       2              |       10.42 ms →       10.52 ms   (+1.04%) | 
  │ └ sirius::Density::update                                           |      125.20 ms →      118.80 ms   (-5.12%) |       1   →       1              |      125.20 ms →      118.80 ms   (-5.12%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.78 ms →      118.37 ms   (-5.13%) |       1   →       1              |      124.78 ms →      118.37 ms   (-5.13%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      103.64 μs →      128.80 μs  (+24.28%) |       1   →       1              |      103.64 μs →      128.80 μs  (+24.28%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      118.45 ms →      112.72 ms   (-4.84%) |       1   →       1              |      118.45 ms →      112.72 ms   (-4.84%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        5.77 ms →        5.07 ms  (-12.11%) |       1   →       1              |        5.77 ms →        5.07 ms  (-12.11%) | 
  ├ sirius::Density::initial_density                                    |      174.97 ms →      163.73 ms   (-6.42%) |       1   →       1              |      174.97 ms →      163.73 ms   (-6.42%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.17 ms →      110.19 ms   (-9.81%) |       1   →       1              |      122.17 ms →      110.19 ms   (-9.81%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.01 ms →        5.54 ms  (+10.46%) |       2   →       2              |       10.03 ms →       11.08 ms  (+10.46%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.75 ms →       10.02 ms   (+2.76%) |       1   →       1              |        9.75 ms →       10.02 ms   (+2.76%) | 
  ├ sirius::Potential::generate                                         |      593.51 ms →      582.13 ms   (-1.92%) |       1   →       1              |      593.51 ms →      582.13 ms   (-1.92%) | 
  │ ├ sirius::Potential::poisson                                        |      137.28 ms →      127.46 ms   (-7.16%) |       1   →       1              |      137.28 ms →      127.46 ms   (-7.16%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.50 ms →        6.29 ms  (+14.23%) |       1   →       1              |        5.50 ms →        6.29 ms  (+14.23%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.38 ms →       10.33 ms   (-0.54%) |       1   →       1              |       10.38 ms →       10.33 ms   (-0.54%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.36 ms →       10.31 ms   (-0.53%) |       1   →       1              |       10.36 ms →       10.31 ms   (-0.53%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.36 ms →       10.31 ms   (-0.53%) |       1   →       1              |       10.36 ms →       10.31 ms   (-0.53%) | 
  │ ├ sirius::Periodic_function::add                                    |      557.05 μs →      582.95 μs   (+4.65%) |       2   →       2              |        1.11 ms →        1.17 ms   (+4.65%) | 
  │ ├ sirius::Potential::xc                                             |       53.74 ms →       54.02 ms   (+0.52%) |       1   →       1              |       53.74 ms →       54.02 ms   (+0.52%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.36 ms →       51.61 ms   (+0.48%) |       1   →       1              |       51.36 ms →       51.61 ms   (+0.48%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.75 ms   (+0.95%) |       2   →       2              |       11.40 ms →       11.51 ms   (+0.95%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.28 ms →        5.42 ms   (+2.80%) |       1   →       1              |        5.28 ms →        5.42 ms   (+2.80%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.96 ms →        5.86 ms   (-1.53%) |       1   →       1              |        5.96 ms →        5.86 ms   (-1.53%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.40 ms →       92.78 ms   (-0.66%) |       1   →       1              |       93.40 ms →       92.78 ms   (-0.66%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.66 ms →      299.46 ms   (-0.40%) |       1   →       1              |      300.66 ms →      299.46 ms   (-0.40%) | 
  ├ sirius::Hamiltonian0                                                |        8.35 ms →        8.40 ms   (+0.60%) |       1   →       1              |        8.35 ms →        8.40 ms   (+0.60%) | 
  │ ├ sirius::Local_operator                                            |        8.01 ms →        8.06 ms   (+0.65%) |       1   →       1              |        8.01 ms →        8.06 ms   (+0.65%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.76 ms   (+0.06%) |       1   →       1              |        4.75 ms →        4.76 ms   (+0.06%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        2.39 ms   (+2.20%) |       1   →       1              |        2.33 ms →        2.39 ms   (+2.20%) | 
  │ ├ sirius::Non_local_operator                                        |       63.13 μs →       62.24 μs   (-1.41%) |       2   →       2              |      126.27 μs →      124.48 μs   (-1.41%) | 
  │ ├ sirius::D_operator::initialize                                    |       97.08 μs →       97.78 μs   (+0.73%) |       1   →       1              |       97.08 μs →       97.78 μs   (+0.73%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.02 μs →       68.96 μs   (-0.09%) |       1   →       1              |       69.02 μs →       68.96 μs   (-0.09%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.09 s    (+0.05%) |       1   →       1              |        3.09 s  →        3.09 s    (+0.05%) | 
- │ ├ sirius::Hamiltonian_k                                             |      375.81 μs →      687.67 μs  (+82.98%) |       4   →       4              |        1.50 ms →        2.75 ms  (+82.98%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      370.76 μs →      683.11 μs  (+84.25%) |       4   →       4              |        1.48 ms →        2.73 ms  (+84.25%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.30 μs →        2.97 μs   (-9.97%) |       4   →       4              |       13.21 μs →       11.89 μs   (-9.97%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      772.02 ms →      772.08 ms   (+0.01%) |       4   →       4              |        3.09 s  →        3.09 s    (+0.01%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       31.94 ms →       32.99 ms   (+3.27%) |      16   →      16              |      511.10 ms →      527.79 ms   (+3.27%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.54 ms →       14.67 ms   (+0.94%) |       4   →       4              |       58.15 ms →       58.69 ms   (+0.94%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.29 ms →        5.46 ms   (+3.33%) |       4   →       4              |       21.16 ms →       21.86 ms   (+3.33%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      353.98 ms →      354.84 ms   (+0.24%) |       4   →       4              |        1.42 s  →        1.42 s    (+0.24%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      257.20 ms →      258.29 ms   (+0.42%) |       4   →       4              |        1.03 s  →        1.03 s    (+0.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.13 ms →       63.20 ms   (+0.10%) |       4   →       4              |      252.53 ms →      252.78 ms   (+0.10%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.18 ms →       16.66 ms   (+2.93%) |       4   →       4              |       64.73 ms →       66.62 ms   (+2.93%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.18 ms →       16.65 ms   (+2.93%) |       4   →       4              |       64.72 ms →       66.62 ms   (+2.93%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.46 ms →       40.11 ms   (-0.86%) |       4   →       4              |      161.82 ms →      160.44 ms   (-0.86%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       15.94 ms →       16.66 ms   (+4.52%) |       4   →       4              |       63.76 ms →       66.64 ms   (+4.52%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.94 ms →       16.66 ms   (+4.51%) |       4   →       4              |       63.75 ms →       66.63 ms   (+4.51%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.22 ms →       54.46 ms   (+0.43%) |       4   →       4              |      216.90 ms →      217.83 ms   (+0.43%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.19 ms →       36.40 ms   (+0.56%) |       4   →       4              |      144.78 ms →      145.59 ms   (+0.56%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.95 ms   (+0.02%) |       4   →       4              |        7.81 ms →        7.81 ms   (+0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.62 ms →       40.27 ms   (-0.85%) |       4   →       4              |      162.48 ms →      161.09 ms   (-0.85%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.49 ms →        7.05 ms   (-5.89%) |       4   →       4              |       29.95 ms →       28.18 ms   (-5.89%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.14 ms   (+0.21%) |       8   →       8              |      216.70 ms →      217.15 ms   (+0.21%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.88 ms →       14.72 ms   (-1.08%) |       8   →       8              |      119.04 ms →      117.76 ms   (-1.08%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.83 ms →       14.67 ms   (-1.07%) |       8   →       8              |      118.66 ms →      117.40 ms   (-1.07%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       31.25 ns →       63.00 ns (+101.60%) |       8   →       8              |      250.00 ns →      504.00 ns (+101.60%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.63 ms →       14.47 ms   (-1.10%) |       8   →       8              |      117.07 ms →      115.78 ms   (-1.10%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       33.75 ns  (+50.00%) |       8   →       8              |      180.00 ns →      270.00 ns  (+50.00%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      121.69 ms →      117.67 ms   (-3.30%) |       4   →       4              |      486.76 ms →      470.68 ms   (-3.30%) | 
  │ │ └ sddk::wf_trans                                                  |       23.51 ms →       23.62 ms   (+0.47%) |       4   →       4              |       94.05 ms →       94.49 ms   (+0.47%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.41 ms →       23.34 ms   (-0.31%) |       4   →       4              |       93.65 ms →       93.36 ms   (-0.31%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      433.75 ns →      393.75 ns   (-9.22%) |       4   →       4              |        1.74 μs →        1.57 μs   (-9.22%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      231.86 s  →      204.83 s   (-11.66%) |       1   →       1              |      231.86 s  →      204.83 s   (-11.66%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.74 ms   (-0.77%) |      19   →      19              |      109.92 ms →      109.07 ms   (-0.77%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.90 s  →        7.86 s   (-11.68%) |      26   →      26              |      231.50 s  →      204.46 s   (-11.68%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.48 ms →        4.56 ms   (+1.81%) |      26   →      26              |      116.55 ms →      118.66 ms   (+1.81%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.13 ms →        4.20 ms   (+1.87%) |      26   →      26              |      107.25 ms →      109.26 ms   (+1.87%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      975.18 μs →      973.40 μs   (-0.18%) |      26   →      26              |       25.35 ms →       25.31 ms   (-0.18%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.26 ms →        2.34 ms   (+3.43%) |      26   →      26              |       58.82 ms →       60.84 ms   (+3.43%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.25 μs →       64.45 μs   (+0.32%) |      52   →      52              |        3.34 ms →        3.35 ms   (+0.32%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.29 μs →       96.23 μs   (+2.06%) |      26   →      26              |        2.45 ms →        2.50 ms   (+2.06%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.06 μs →       66.63 μs   (+0.86%) |      26   →      26              |        1.72 ms →        1.73 ms   (+0.86%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.80 s  →        5.78 s   (-14.95%) |      26   →      26              |      176.70 s  →      150.28 s   (-14.95%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      346.16 μs →      336.69 μs   (-2.73%) |     104   →     104              |       36.00 ms →       35.02 ms   (-2.73%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      340.48 μs →      331.09 μs   (-2.76%) |     104   →     104              |       35.41 ms →       34.43 ms   (-2.76%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.14 μs →        4.15 μs   (+0.30%) |     104   →     104              |      430.79 μs →      432.09 μs   (+0.30%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.70 s  →        1.44 s   (-14.96%) |     104   →     104              |      176.66 s  →      150.24 s   (-14.96%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.95 ms →       12.09 ms   (+1.21%) |     104   →     104              |        1.24 s  →        1.26 s    (+1.21%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      649.69 ns →      723.10 ns  (+11.30%) |     624   →     624              |      405.41 μs →      451.21 μs  (+11.30%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.83 ms   (-0.54%) |     104   →     104              |      191.37 ms →      190.33 ms   (-0.54%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.45 μs →      352.82 μs   (-0.74%) |     104   →     104              |       36.97 ms →       36.69 ms   (-0.74%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      549.63 μs →      550.86 μs   (+0.22%) |     208   →     208              |      114.32 ms →      114.58 ms   (+0.22%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.68 s  →        1.42 s   (-15.17%) |     104   →     104              |      174.29 s  →      147.85 s   (-15.17%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       70.01 ms →       68.30 ms   (-2.44%) |     906   →     957     (+5.63%) |       63.43 s  →       65.36 s    (+3.05%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.71 ms →       43.62 ms   (-2.43%) |     906   →     957     (+5.63%) |       40.51 s  →       41.75 s    (+3.07%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.72 ms →        8.64 ms   (-0.91%) |     906   →     957     (+5.63%) |        7.90 s  →        8.27 s    (+4.67%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      227.85 μs →      224.54 μs   (-1.45%) |     906   →     957     (+5.63%) |      206.43 ms →      214.89 ms   (+4.10%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.97 ms →        2.05 ms   (+4.08%) |     104   →     104              |      204.68 ms →      213.03 ms   (+4.08%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.90 ms →        6.66 ms   (-3.40%) |     906   →     957     (+5.63%) |        6.25 s  →        6.38 s    (+2.04%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       87.89 μs →       86.55 μs   (-1.52%) |     906   →     957     (+5.63%) |       79.63 ms →       82.83 ms   (+4.02%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      741.87 μs →      772.02 μs   (+4.06%) |     104   →     104              |       77.15 ms →       80.29 ms   (+4.06%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.87 ms →        9.56 ms   (-3.16%) |     906   →     957     (+5.63%) |        8.94 s  →        9.15 s    (+2.29%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.23 ms →        6.00 ms   (-3.67%) |     906   →     957     (+5.63%) |        5.64 s  →        5.74 s    (+1.75%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (+0.05%) |     906   →     957     (+5.63%) |        1.38 s  →        1.45 s    (+5.69%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.81 ms →        8.39 ms   (-4.79%) |     906   →     957     (+5.63%) |        7.98 s  →        8.03 s    (+0.57%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.42 ms →        1.21 ms  (-15.07%) |     906   →     957     (+5.63%) |        1.29 s  →        1.16 s   (-10.29%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.47 ms →        7.37 ms   (-1.35%) |    1.81 K →    1.91 K   (+5.63%) |       13.54 s  →       14.11 s    (+4.20%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.15 ms →       26.46 ms   (-6.00%) |     906   →     957     (+5.63%) |       25.50 s  →       25.32 s    (-0.71%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.06 ms →        1.89 ms   (-8.00%) |    1.71 K →    1.81 K   (+5.97%) |        3.51 s  →        3.42 s    (-2.51%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       71.48 ns →       62.52 ns  (-12.53%) |    1.71 K →    1.81 K   (+5.97%) |      122.09 μs →      113.17 μs   (-7.31%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.04 ms →        1.88 ms   (-7.94%) |    1.71 K →    1.81 K   (+5.97%) |        3.49 s  →        3.41 s    (-2.44%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       54.54 ns →       58.87 ns   (+7.95%) |    1.71 K →    1.81 K   (+5.97%) |       93.15 μs →      106.56 μs  (+14.39%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      831.11 μs →      772.92 μs   (-7.00%) |     906   →     957     (+5.63%) |      752.99 ms →      739.68 ms   (-1.77%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      772.86 μs →      729.50 μs   (-5.61%) |     906   →     957     (+5.63%) |      700.21 ms →      698.13 ms   (-0.30%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.42 ms →        5.10 ms   (-5.93%) |    3.52 K →    3.72 K   (+5.80%) |       19.08 s  →       18.99 s    (-0.47%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.69 ms →        3.47 ms   (-6.03%) |    5.12 K →    5.43 K   (+5.97%) |       18.92 s  →       18.85 s    (-0.42%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.52 ms →        5.16 ms   (-6.50%) |     906   →     957     (+5.63%) |        5.00 s  →        4.94 s    (-1.24%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.79 ms →        3.42 ms   (-9.78%) |     906   →     957     (+5.63%) |        3.44 s  →        3.28 s    (-4.70%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       60.04 ns →       47.59 ns  (-20.73%) |     906   →     957     (+5.63%) |       54.39 μs →       45.54 μs  (-16.27%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.78 ms →        3.41 ms   (-9.66%) |     906   →     957     (+5.63%) |        3.42 s  →        3.26 s    (-4.58%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       71.94 ns →       46.18 ns  (-35.81%) |     906   →     957     (+5.63%) |       65.18 μs →       44.20 μs  (-32.19%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       66.22 ms →       32.04 ms  (-51.62%) |     906   →     957     (+5.63%) |       59.99 s  →       30.66 s   (-48.90%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       10.84 ms →        9.68 ms  (-10.68%) |     885   →     929     (+4.97%) |        9.59 s  →        8.99 s    (-6.24%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       10.47 ms →        9.25 ms  (-11.62%) |     840   →     887     (+5.60%) |        8.79 s  →        8.20 s    (-6.68%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.20 ms →        4.60 ms  (-11.53%) |    1.68 K →    1.77 K   (+5.60%) |        8.74 s  →        8.16 s    (-6.58%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      644.18 μs →      624.21 μs   (-3.10%) |     840   →     887     (+5.60%) |      541.11 ms →      553.68 ms   (+2.32%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.45 ms →       36.51 ms  (-29.04%) |     209   →     344    (+64.59%) |       10.75 s  →       12.56 s   (+16.80%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.13 ms →       21.38 ms  (-37.36%) |     314   →     584    (+85.99%) |       10.72 s  →       12.49 s   (+16.50%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.46 ms →       15.08 ms  (-40.79%) |     419   →     824    (+96.66%) |       10.67 s  →       12.42 s   (+16.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      570.15 ns →      535.07 ns   (-6.15%) |     104   →     104              |       59.30 μs →       55.65 μs   (-6.15%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.78 μs →       21.94 μs   (-3.67%) |      26   →      26              |      592.17 μs →      570.45 μs   (-3.67%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      594.57 μs →      589.61 μs   (-0.83%) |      26   →      26              |       15.46 ms →       15.33 ms   (-0.83%) | 
  │ │ ├ sirius::Density::generate                                       |      900.48 ms →      895.19 ms   (-0.59%) |      26   →      26              |       23.41 s  →       23.27 s    (-0.59%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      529.46 ms →      524.68 ms   (-0.90%) |      26   →      26              |       13.77 s  →       13.64 s    (-0.90%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.86 ms →       24.35 ms   (-2.04%) |     104   →     104              |        2.59 s  →        2.53 s    (-2.04%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.65 μs →        8.83 μs   (+2.10%) |     104   →     104              |      899.45 μs →      918.34 μs   (+2.10%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.57 μs →       16.30 μs   (+4.68%) |       8   →       8              |      124.59 μs →      130.42 μs   (+4.68%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.74 ms →       20.18 ms   (-2.70%) |     104   →     104              |        2.16 s  →        2.10 s    (-2.70%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.30 ms →       29.63 ms   (-2.22%) |     104   →     104              |        3.15 s  →        3.08 s    (-2.22%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.42 μs →        9.77 μs   (+3.72%) |     104   →     104              |      979.86 μs →        1.02 ms   (+3.72%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.49%) |     104   →     104              |      150.89 ms →      151.63 ms   (+0.49%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.37 ms →       27.69 ms   (-2.38%) |     104   →     104              |        2.95 s  →        2.88 s    (-2.38%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.24 ms →        3.56 ms  (-15.98%) |     104   →     104              |      440.54 ms →      370.14 ms  (-15.98%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      602.12 ns →      508.81 ns  (-15.50%) |     104   →     104              |       62.62 μs →       52.92 μs  (-15.50%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.75 ms →       42.82 ms   (+0.16%) |     104   →     104              |        4.45 s  →        4.45 s    (+0.16%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.63 ms →        1.63 ms   (+0.14%) |      26   →      26              |       42.39 ms →       42.45 ms   (+0.14%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.91 ms →       88.85 ms   (-0.07%) |      26   →      26              |        2.31 s  →        2.31 s    (-0.07%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.68 ms →       88.62 ms   (-0.07%) |      26   →      26              |        2.31 s  →        2.30 s    (-0.07%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.88 ms →      278.00 ms   (+0.04%) |      26   →      26              |        7.22 s  →        7.23 s    (+0.04%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.88 ms →      278.00 ms   (+0.04%) |      26   →      26              |        7.22 s  →        7.23 s    (+0.04%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.77 ms →       24.92 ms   (+0.61%) |      26   →      26              |      644.03 ms →      647.95 ms   (+0.61%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.32 ms →      227.47 ms   (+0.51%) |      26   →      26              |        5.88 s  →        5.91 s    (+0.51%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       25.01 ms →       23.81 ms   (-4.78%) |      26   →      26              |      650.15 ms →      619.09 ms   (-4.78%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.19 ms →       80.55 ms   (-2.00%) |      26   →      26              |        2.14 s  →        2.09 s    (-2.00%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.36 ms →        8.36 ms  (+13.68%) |      26   →      26              |      191.30 ms →      217.48 ms  (+13.68%) | 
  │ │ ├ sirius::Density::mix                                            |      219.64 ms →      212.86 ms   (-3.09%) |      26   →      26              |        5.71 s  →        5.53 s    (-3.09%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      961.91 μs →      999.32 μs   (+3.89%) |      26   →      26              |       25.01 ms →       25.98 ms   (+3.89%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.77 ms →       10.24 ms   (-4.98%) |     334   →     334              |        3.60 s  →        3.42 s    (-4.98%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.42 ms →        9.96 ms   (-4.36%) |     334   →     334              |        3.48 s  →        3.33 s    (-4.36%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.42 ms →        9.96 ms   (-4.36%) |     334   →     334              |        3.48 s  →        3.33 s    (-4.36%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.19 ms →        6.68 ms   (-7.11%) |      26   →      26              |      186.95 ms →      173.65 ms   (-7.11%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.34 ms →        5.83 ms   (-8.08%) |      26   →      26              |      164.81 ms →      151.50 ms   (-8.08%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.86 ms →      568.33 ms   (-1.82%) |      26   →      26              |       15.05 s  →       14.78 s    (-1.82%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.10 ms →      126.28 ms   (-7.89%) |      26   →      26              |        3.56 s  →        3.28 s    (-7.89%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.37 ms →        5.47 ms   (+2.01%) |      26   →      26              |      139.49 ms →      142.29 ms   (+2.01%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.35 ms →       10.21 ms   (-1.37%) |      26   →      26              |      269.10 ms →      265.41 ms   (-1.37%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.18 ms →        9.97 ms   (-2.11%) |      26   →      26              |      264.74 ms →      259.16 ms   (-2.11%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.18 ms →        9.97 ms   (-2.11%) |      26   →      26              |      264.73 ms →      259.14 ms   (-2.11%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      549.61 μs →      582.85 μs   (+6.05%) |      52   →      52              |       28.58 ms →       30.31 ms   (+6.05%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.26 ms →       48.95 ms   (-0.63%) |      26   →      26              |        1.28 s  →        1.27 s    (-0.63%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.91 ms →       46.60 ms   (-0.65%) |      26   →      26              |        1.22 s  →        1.21 s    (-0.65%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.04 ms   (-0.88%) |      52   →      52              |      159.30 ms →      157.90 ms   (-0.88%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.36 ms →        5.37 ms   (+0.14%) |      26   →      26              |      139.44 ms →      139.64 ms   (+0.14%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.64 ms →        6.64 ms   (-0.02%) |      26   →      26              |      172.60 ms →      172.57 ms   (-0.02%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.85 ms →       91.10 ms   (+0.27%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.27%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.61 ms →      292.89 ms   (+0.10%) |      26   →      26              |        7.61 s  →        7.62 s    (+0.10%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.21 ms →      281.00 ms   (-0.08%) |      26   →      26              |        7.31 s  →        7.31 s    (-0.08%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.21 ms →      281.00 ms   (-0.08%) |      26   →      26              |        7.31 s  →        7.31 s    (-0.08%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.08 ms →       27.26 ms   (+0.67%) |      26   →      26              |      704.02 ms →      708.76 ms   (+0.67%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.21 ms →      226.21 ms   (+0.00%) |      26   →      26              |        5.88 s  →        5.88 s    (+0.00%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.09 ms →       23.72 ms   (-1.53%) |      26   →      26              |      626.41 ms →      616.80 ms   (-1.53%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.72 ms →        5.54 ms   (-3.09%) |      26   →      26              |      148.71 ms →      144.11 ms   (-3.09%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.43 ms →       10.41 ms   (-0.18%) |     182   →     182              |        1.90 s  →        1.90 s    (-0.18%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.15 ms →        9.82 ms   (-3.23%) |     182   →     182              |        1.85 s  →        1.79 s    (-3.23%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.15 ms →        9.82 ms   (-3.23%) |     182   →     182              |        1.85 s  →        1.79 s    (-3.23%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.11 ms →       10.83 ms   (-2.55%) |      78   →      78              |      866.91 ms →      844.83 ms   (-2.55%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.82 ms →       10.19 ms   (-5.87%) |      78   →      78              |      844.34 ms →      794.80 ms   (-5.87%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.05 ms →       10.06 ms   (+0.12%) |      26   →      26              |      261.35 ms →      261.65 ms   (+0.12%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      127.50 μs →      110.71 μs  (-13.17%) |      26   →      26              |        3.32 ms →        2.88 ms  (-13.17%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      122.48 μs →      105.79 μs  (-13.63%) |      26   →      26              |        3.18 ms →        2.75 ms  (-13.63%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.10 ms →        5.05 ms   (-1.07%) |       2   →       2              |       10.21 ms →       10.10 ms   (-1.07%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.52 ms →        9.72 ms   (-7.65%) |       6   →       6              |       63.14 ms →       58.31 ms   (-7.65%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.73 ms →        9.69 ms   (-0.47%) |       6   →       6              |       58.39 ms →       58.11 ms   (-0.47%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.73 ms →        9.69 ms   (-0.47%) |       6   →       6              |       58.39 ms →       58.11 ms   (-0.47%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.82 ms →       10.23 ms   (-5.46%) |       3   →       3              |       32.47 ms →       30.70 ms   (-5.46%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.51 ms →       10.22 ms   (-2.75%) |       3   →       3              |       31.54 ms →       30.67 ms   (-2.75%) | 
  ├ sirius::Periodic_function|inner                                     |       10.49 ms →        9.87 ms   (-5.96%) |       2   →       2              |       20.98 ms →       19.73 ms   (-5.96%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.33 ms →        9.84 ms   (-4.79%) |       2   →       2              |       20.67 ms →       19.68 ms   (-4.79%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.33 ms →        9.84 ms   (-4.80%) |       2   →       2              |       20.67 ms →       19.68 ms   (-4.80%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.81 ms →       10.19 ms   (-5.77%) |       1   →       1              |       10.81 ms →       10.19 ms   (-5.77%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.18 ms   (-2.79%) |       1   →       1              |       10.47 ms →       10.18 ms   (-2.79%) | 
+ └ sirius::finalize                                                    |      309.74 ms →      272.41 ms  (-12.05%) |       1   →       1              |      309.74 ms →      272.41 ms  (-12.05%) | 
  ====================================================================================================================================================================================================
```
