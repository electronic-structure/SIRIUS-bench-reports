# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs 8cf25a48a521cee28df94fe46e001c67fed20f54
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      242.76 s  →      242.12 s    (-0.27%) |       1   →       1              |      242.76 s  →      242.12 s    (-0.27%) | 
  ├ sirius::initialize                                                  |        2.67 s  →        2.67 s    (-0.01%) |       1   →       1              |        2.67 s  →        2.67 s    (-0.01%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        2.94 s    (-1.84%) |       1   →       1              |        2.99 s  →        2.94 s    (-1.84%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       25.13 ms →      330.01 μs  (-98.69%) |       1   →       1              |       25.13 ms →      330.01 μs  (-98.69%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      201.75 ms →      160.34 ms  (-20.52%) |       1   →       1              |      201.75 ms →      160.34 ms  (-20.52%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       89.16 ms →       68.21 ms  (-23.49%) |       2   →       2              |      178.32 ms →      136.42 ms  (-23.49%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.35 ms →       23.84 ms   (+2.11%) |       1   →       1              |       23.35 ms →       23.84 ms   (+2.11%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.49 ms →        6.27 ms   (-3.41%) |       1   →       1              |        6.49 ms →        6.27 ms   (-3.41%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.81 ms →       17.53 ms   (+4.26%) |       1   →       1              |       16.81 ms →       17.53 ms   (+4.26%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.79 ms →       17.51 ms   (+4.26%) |       1   →       1              |       16.79 ms →       17.51 ms   (+4.26%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.13 ms   (-0.46%) |       1   →       1              |        4.14 ms →        4.13 ms   (-0.46%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (-0.18%) |       1   →       1              |        2.34 ms →        2.34 ms   (-0.18%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      111.57 μs →      110.46 μs   (-0.99%) |       1   →       1              |      111.57 μs →      110.46 μs   (-0.99%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.73 s    (+0.45%) |       1   →       1              |        2.72 s  →        2.73 s    (+0.45%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.02 ms →       10.76 ms   (-2.35%) |       1   →       1              |       11.02 ms →       10.76 ms   (-2.35%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.60 ms →        4.33 ms   (-5.85%) |       1   →       1              |        4.60 ms →        4.33 ms   (-5.85%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.40 ms   (+0.17%) |       1   →       1              |        6.39 ms →        6.40 ms   (+0.17%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.38 ms   (+0.17%) |       1   →       1              |        6.37 ms →        6.38 ms   (+0.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.88 ms →        3.88 ms   (+0.17%) |       1   →       1              |        3.88 ms →        3.88 ms   (+0.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.08%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.08%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      102.66 μs →      107.44 μs   (+4.66%) |       1   →       1              |      102.66 μs →      107.44 μs   (+4.66%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.60 ms →       62.30 ms   (-0.47%) |       2   →       2              |      125.19 ms →      124.61 ms   (-0.47%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.12 ms →        5.13 ms   (+0.20%) |       2   →       2              |       10.24 ms →       10.26 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.48 ms   (+0.44%) |       1   →       1              |        4.46 ms →        4.48 ms   (+0.44%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.79 ms →       21.83 ms   (+0.21%) |       2   →       2              |       43.58 ms →       43.67 ms   (+0.21%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.80 ms →       14.83 ms   (+0.17%) |       2   →       2              |       29.60 ms →       29.65 ms   (+0.17%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.56 ms →       19.72 ms   (+0.82%) |       4   →       4              |       78.25 ms →       78.89 ms   (+0.82%) | 
  │   ├ sddk::Gvec::init                                                |      174.74 ms →      175.49 ms   (+0.43%) |       2   →       2              |      349.48 ms →      350.98 ms   (+0.43%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.95 ms →      131.80 ms   (+0.65%) |       2   →       2              |      261.91 ms →      263.61 ms   (+0.65%) | 
  │   ├ sddk::Gvec_shells                                               |      175.79 ms →      188.23 ms   (+7.07%) |       1   →       1              |      175.79 ms →      188.23 ms   (+7.07%) | 
+ │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.75 ms →        1.32 ms  (-24.34%) |       1   →       1              |        1.75 ms →        1.32 ms  (-24.34%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.33 ms →      291.90 ms   (-0.15%) |       2   →       2              |      584.65 ms →      583.80 ms   (-0.15%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       75.05 ms →       79.87 ms   (+6.43%) |       1   →       1              |       75.05 ms →       79.87 ms   (+6.43%) | 
  │ ├ sirius::K_point::K_point                                          |        2.43 μs →        2.49 μs   (+2.72%) |       4   →       4              |        9.71 μs →        9.98 μs   (+2.72%) | 
  │ └ sirius::K_point_set::initialize                                   |       74.95 ms →       79.77 ms   (+6.43%) |       1   →       1              |       74.95 ms →       79.77 ms   (+6.43%) | 
  │   └ sirius::K_point::initialize                                     |       18.73 ms →       19.92 ms   (+6.38%) |       4   →       4              |       74.91 ms →       79.69 ms   (+6.38%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.09 ms →       15.25 ms   (+8.22%) |       4   →       4              |       56.37 ms →       61.00 ms   (+8.22%) | 
  │     │ └ sddk::Gvec::init                                            |        3.86 ms →        3.95 ms   (+2.20%) |       4   →       4              |       15.45 ms →       15.79 ms   (+2.20%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.91 μs →        9.27 μs   (+3.99%) |       4   →       4              |       35.66 μs →       37.08 μs   (+3.99%) | 
  │     └ sirius::K_point::update                                       |        3.33 ms →        3.33 ms   (-0.08%) |       4   →       4              |       13.33 ms →       13.32 ms   (-0.08%) | 
  │       └ sirius::Beta_projectors                                     |        1.78 ms →        1.76 ms   (-1.61%) |       4   →       4              |        7.14 ms →        7.02 ms   (-1.61%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      946.25 μs →      917.54 μs   (-3.03%) |       4   →       4              |        3.78 ms →        3.67 ms   (-3.03%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.19 ms →        5.41 ms   (+4.22%) |       2   →       2              |       10.38 ms →       10.82 ms   (+4.22%) | 
  ├ sirius::Potential                                                   |      160.92 ms →      157.29 ms   (-2.26%) |       1   →       1              |      160.92 ms →      157.29 ms   (-2.26%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms →        5.80 ms   (+0.42%) |       6   →       6              |       34.65 ms →       34.79 ms   (+0.42%) | 
  │ └ sirius::Potential::update                                         |      125.57 ms →      121.78 ms   (-3.02%) |       1   →       1              |      125.57 ms →      121.78 ms   (-3.02%) | 
  │   └ sirius::Potential::generate_local_potential                     |      124.80 ms →      121.03 ms   (-3.03%) |       1   →       1              |      124.80 ms →      121.03 ms   (-3.03%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.00 ms →      106.62 ms   (-2.19%) |       1   →       1              |      109.00 ms →      106.62 ms   (-2.19%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.90 ms →       13.54 ms   (-9.14%) |       1   →       1              |       14.90 ms →       13.54 ms   (-9.14%) | 
  ├ sirius::Density                                                     |      136.27 ms →      134.48 ms   (-1.31%) |       1   →       1              |      136.27 ms →      134.48 ms   (-1.31%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.16 ms →        5.24 ms   (+1.49%) |       2   →       2              |       10.32 ms →       10.48 ms   (+1.49%) | 
  │ └ sirius::Density::update                                           |      125.67 ms →      123.74 ms   (-1.54%) |       1   →       1              |      125.67 ms →      123.74 ms   (-1.54%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.24 ms →      123.30 ms   (-1.55%) |       1   →       1              |      125.24 ms →      123.30 ms   (-1.55%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.96 μs →      112.52 μs   (+9.28%) |       1   →       1              |      102.96 μs →      112.52 μs   (+9.28%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.23 ms →      109.20 ms   (-2.70%) |       1   →       1              |      112.23 ms →      109.20 ms   (-2.70%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       12.46 ms →       13.40 ms   (+7.51%) |       1   →       1              |       12.46 ms →       13.40 ms   (+7.51%) | 
  ├ sirius::Density::initial_density                                    |      176.12 ms →      175.24 ms   (-0.50%) |       1   →       1              |      176.12 ms →      175.24 ms   (-0.50%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      112.34 ms →      109.09 ms   (-2.89%) |       1   →       1              |      112.34 ms →      109.09 ms   (-2.89%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.80 ms →       12.02 ms  (+11.29%) |       2   →       2              |       21.61 ms →       24.05 ms  (+11.29%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.68 ms →       10.04 ms   (+3.68%) |       1   →       1              |        9.68 ms →       10.04 ms   (+3.68%) | 
  ├ sirius::Potential::generate                                         |      595.45 ms →      594.48 ms   (-0.16%) |       1   →       1              |      595.45 ms →      594.48 ms   (-0.16%) | 
  │ ├ sirius::Potential::poisson                                        |      139.40 ms →      138.15 ms   (-0.90%) |       1   →       1              |      139.40 ms →      138.15 ms   (-0.90%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       18.95 ms →       19.66 ms   (+3.75%) |       1   →       1              |       18.95 ms →       19.66 ms   (+3.75%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.83 ms →       11.34 ms   (+4.69%) |       1   →       1              |       10.83 ms →       11.34 ms   (+4.69%) | 
- │ │   └ sirius::Periodic_function|inner_local                         |        9.92 ms →       11.32 ms  (+14.08%) |       1   →       1              |        9.92 ms →       11.32 ms  (+14.08%) | 
- │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.92 ms →       11.32 ms  (+14.08%) |       1   →       1              |        9.92 ms →       11.32 ms  (+14.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      551.31 μs →      533.59 μs   (-3.21%) |       2   →       2              |        1.10 ms →        1.07 ms   (-3.21%) | 
  │ ├ sirius::Potential::xc                                             |       56.10 ms →       55.64 ms   (-0.83%) |       1   →       1              |       56.10 ms →       55.64 ms   (-0.83%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.75 ms →       53.29 ms   (-0.86%) |       1   →       1              |       53.75 ms →       53.29 ms   (-0.86%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.68 ms →        6.22 ms   (+9.57%) |       2   →       2              |       11.36 ms →       12.45 ms   (+9.57%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        6.07 ms →        5.16 ms  (-14.94%) |       1   →       1              |        6.07 ms →        5.16 ms  (-14.94%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.72 ms →        6.02 ms   (+5.07%) |       1   →       1              |        5.72 ms →        6.02 ms   (+5.07%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.74 ms →       92.61 ms   (-0.14%) |       1   →       1              |       92.74 ms →       92.61 ms   (-0.14%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.00 ms →      299.66 ms   (+0.22%) |       1   →       1              |      299.00 ms →      299.66 ms   (+0.22%) | 
  ├ sirius::Hamiltonian0                                                |        8.44 ms →        8.34 ms   (-1.24%) |       1   →       1              |        8.44 ms →        8.34 ms   (-1.24%) | 
  │ ├ sirius::Local_operator                                            |        8.10 ms →        8.00 ms   (-1.24%) |       1   →       1              |        8.10 ms →        8.00 ms   (-1.24%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms →        4.71 ms   (-0.51%) |       1   →       1              |        4.73 ms →        4.71 ms   (-0.51%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.44 ms →        2.37 ms   (-3.11%) |       1   →       1              |        2.44 ms →        2.37 ms   (-3.11%) | 
  │ ├ sirius::Non_local_operator                                        |       62.74 μs →       62.38 μs   (-0.57%) |       2   →       2              |      125.47 μs →      124.76 μs   (-0.57%) | 
  │ ├ sirius::D_operator::initialize                                    |       93.94 μs →       91.09 μs   (-3.04%) |       1   →       1              |       93.94 μs →       91.09 μs   (-3.04%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.48 μs →       67.80 μs   (-2.42%) |       1   →       1              |       69.48 μs →       67.80 μs   (-2.42%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.10 s    (+0.36%) |       1   →       1              |        3.09 s  →        3.10 s    (+0.36%) | 
  │ ├ sirius::Hamiltonian_k                                             |      379.13 μs →      389.61 μs   (+2.77%) |       4   →       4              |        1.52 ms →        1.56 ms   (+2.77%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      374.15 μs →      384.31 μs   (+2.72%) |       4   →       4              |        1.50 ms →        1.54 ms   (+2.72%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.11 μs →        3.36 μs   (+8.23%) |       4   →       4              |       12.43 μs →       13.45 μs   (+8.23%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      771.14 ms →      773.89 ms   (+0.36%) |       4   →       4              |        3.08 s  →        3.10 s    (+0.36%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.00 ms →       32.25 ms   (+0.80%) |      16   →      16              |      511.92 ms →      516.01 ms   (+0.80%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.49 ms →       14.50 ms   (+0.07%) |       4   →       4              |       57.95 ms →       57.99 ms   (+0.07%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.28 ms →        5.29 ms   (+0.12%) |       4   →       4              |       21.12 ms →       21.15 ms   (+0.12%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      353.51 ms →      356.39 ms   (+0.81%) |       4   →       4              |        1.41 s  →        1.43 s    (+0.81%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      256.92 ms →      259.76 ms   (+1.11%) |       4   →       4              |        1.03 s  →        1.04 s    (+1.11%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       62.90 ms →       63.58 ms   (+1.08%) |       4   →       4              |      251.59 ms →      254.31 ms   (+1.08%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       15.79 ms →       16.25 ms   (+2.94%) |       4   →       4              |       63.15 ms →       65.01 ms   (+2.94%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.79 ms →       16.25 ms   (+2.94%) |       4   →       4              |       63.14 ms →       65.00 ms   (+2.94%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.59 ms →       40.82 ms   (+0.56%) |       4   →       4              |      162.36 ms →      163.28 ms   (+0.56%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       15.83 ms →       16.19 ms   (+2.31%) |       4   →       4              |       63.31 ms →       64.77 ms   (+2.31%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.82 ms →       16.19 ms   (+2.31%) |       4   →       4              |       63.30 ms →       64.76 ms   (+2.31%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.42 ms →       56.19 ms   (+3.27%) |       4   →       4              |      217.66 ms →      224.77 ms   (+3.27%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.34 ms →       38.18 ms   (+5.05%) |       4   →       4              |      145.37 ms →      152.70 ms   (+5.05%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.96 ms →        1.97 ms   (+0.54%) |       4   →       4              |        7.84 ms →        7.88 ms   (+0.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.50 ms →       40.48 ms   (-0.04%) |       4   →       4              |      162.00 ms →      161.94 ms   (-0.04%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.36 ms →        7.33 ms   (-0.31%) |       4   →       4              |       29.42 ms →       29.33 ms   (-0.31%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.05 ms →       27.07 ms   (+0.08%) |       8   →       8              |      216.39 ms →      216.55 ms   (+0.08%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.96 ms →       14.88 ms   (-0.52%) |       8   →       8              |      119.69 ms →      119.06 ms   (-0.52%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.92 ms →       14.84 ms   (-0.52%) |       8   →       8              |      119.33 ms →      118.70 ms   (-0.52%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       32.13 ns →       29.12 ns   (-9.34%) |       8   →       8              |      257.00 ns →      233.00 ns   (-9.34%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.72 ms →       14.64 ms   (-0.55%) |       8   →       8              |      117.80 ms →      117.15 ms   (-0.55%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.37 ns →       32.38 ns  (+58.90%) |       8   →       8              |      163.00 ns →      259.00 ns  (+58.90%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      119.57 ms →      119.44 ms   (-0.11%) |       4   →       4              |      478.29 ms →      477.76 ms   (-0.11%) | 
  │ │ └ sddk::wf_trans                                                  |       23.56 ms →       23.55 ms   (-0.05%) |       4   →       4              |       94.26 ms →       94.20 ms   (-0.05%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.30 ms →       23.29 ms   (-0.05%) |       4   →       4              |       93.20 ms →       93.15 ms   (-0.05%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      364.75 ns →      374.75 ns   (+2.74%) |       4   →       4              |        1.46 μs →        1.50 μs   (+2.74%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      232.03 s  →      231.45 s    (-0.25%) |       1   →       1              |      232.03 s  →      231.45 s    (-0.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms →        5.79 ms   (+0.35%) |      19   →      19              |      109.67 ms →      110.05 ms   (+0.35%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.91 s  →        8.89 s    (-0.26%) |      26   →      26              |      231.65 s  →      231.05 s    (-0.26%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.47 ms →        4.45 ms   (-0.47%) |      26   →      26              |      116.33 ms →      115.78 ms   (-0.47%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.12 ms →        4.10 ms   (-0.55%) |      26   →      26              |      107.14 ms →      106.56 ms   (-0.55%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      952.76 μs →      966.75 μs   (+1.47%) |      26   →      26              |       24.77 ms →       25.14 ms   (+1.47%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.28 ms →        2.24 ms   (-1.77%) |      26   →      26              |       59.35 ms →       58.29 ms   (-1.77%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.46 μs →       64.47 μs   (+0.01%) |      52   →      52              |        3.35 ms →        3.35 ms   (+0.01%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       89.81 μs →       89.72 μs   (-0.10%) |      26   →      26              |        2.34 ms →        2.33 ms   (-0.10%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.55 μs →       65.78 μs   (-1.16%) |      26   →      26              |        1.73 ms →        1.71 ms   (-1.16%) | 
  │ │ ├ sirius::Band::solve                                             |        6.80 s  →        6.79 s    (-0.07%) |      26   →      26              |      176.72 s  →      176.60 s    (-0.07%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      347.00 μs →      335.51 μs   (-3.31%) |     104   →     104              |       36.09 ms →       34.89 ms   (-3.31%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      341.35 μs →      329.61 μs   (-3.44%) |     104   →     104              |       35.50 ms →       34.28 ms   (-3.44%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.91 μs →        4.19 μs   (+7.41%) |     104   →     104              |      406.13 μs →      436.22 μs   (+7.41%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.70 s  →        1.70 s    (-0.07%) |     104   →     104              |      176.68 s  →      176.56 s    (-0.07%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.00 ms →       11.95 ms   (-0.41%) |     104   →     104              |        1.25 s  →        1.24 s    (-0.41%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      738.54 ns →      741.74 ns   (+0.43%) |     624   →     624              |      460.85 μs →      462.85 μs   (+0.43%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.84 ms   (+0.37%) |     104   →     104              |      190.57 ms →      191.27 ms   (+0.37%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.27 μs →      353.39 μs   (-0.53%) |     104   →     104              |       36.95 ms →       36.75 ms   (-0.53%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.70 μs →      553.97 μs   (+0.59%) |     208   →     208              |      114.55 ms →      115.23 ms   (+0.59%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.68 s  →        1.67 s    (-0.06%) |     104   →     104              |      174.30 s  →      174.19 s    (-0.06%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.82 ms →       68.43 ms   (-0.57%) |     920   →     928     (+0.87%) |       63.31 s  →       63.50 s    (+0.29%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.96 ms →       43.64 ms   (-0.71%) |     920   →     928     (+0.87%) |       40.44 s  →       40.50 s    (+0.15%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.52 ms →        8.56 ms   (+0.50%) |     920   →     928     (+0.87%) |        7.84 s  →        7.95 s    (+1.38%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      226.50 μs →      224.79 μs   (-0.75%) |     920   →     928     (+0.87%) |      208.38 ms →      208.61 ms   (+0.11%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.99 ms →        1.99 ms   (+0.10%) |     104   →     104              |      206.51 ms →      206.71 ms   (+0.10%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.71 ms →        6.75 ms   (+0.45%) |     920   →     928     (+0.87%) |        6.18 s  →        6.26 s    (+1.32%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       86.70 μs →       86.01 μs   (-0.79%) |     920   →     928     (+0.87%) |       79.76 ms →       79.82 ms   (+0.07%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      743.06 μs →      746.14 μs   (+0.41%) |     104   →     104              |       77.28 ms →       77.60 ms   (+0.41%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.73 ms →        9.59 ms   (-1.47%) |     920   →     928     (+0.87%) |        8.95 s  →        8.90 s    (-0.61%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.13 ms →        6.02 ms   (-1.79%) |     920   →     928     (+0.87%) |        5.64 s  →        5.59 s    (-0.94%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.05%) |     920   →     928     (+0.87%) |        1.40 s  →        1.41 s    (+0.82%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.56 ms →        8.54 ms   (-0.28%) |     920   →     928     (+0.87%) |        7.88 s  →        7.92 s    (+0.58%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.29 ms →        1.35 ms   (+4.28%) |     920   →     928     (+0.87%) |        1.19 s  →        1.25 s    (+5.19%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.38 ms →        7.35 ms   (-0.36%) |    1.84 K →    1.86 K   (+0.87%) |       13.58 s  →       13.64 s    (+0.51%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.72 ms →       27.47 ms   (-0.92%) |     920   →     928     (+0.87%) |       25.50 s  →       25.49 s    (-0.05%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.02 ms →        2.02 ms   (+0.15%) |    1.74 K →    1.75 K   (+0.92%) |        3.51 s  →        3.54 s    (+1.08%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       64.40 ns →       76.49 ns  (+18.77%) |    1.74 K →    1.75 K   (+0.92%) |      111.80 μs →      134.02 μs  (+19.87%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.01 ms →        2.01 ms   (+0.13%) |    1.74 K →    1.75 K   (+0.92%) |        3.49 s  →        3.53 s    (+1.06%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       64.95 ns →       76.59 ns  (+17.92%) |    1.74 K →    1.75 K   (+0.92%) |      112.75 μs →      134.18 μs  (+19.01%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      869.94 μs →      825.76 μs   (-5.08%) |     920   →     928     (+0.87%) |      800.34 ms →      766.30 ms   (-4.25%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      756.63 μs →      754.59 μs   (-0.27%) |     920   →     928     (+0.87%) |      696.10 ms →      700.26 ms   (+0.60%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.32 ms →        5.27 ms   (-0.94%) |    3.58 K →    3.61 K   (+0.89%) |       19.04 s  →       19.03 s    (-0.05%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.62 ms →        3.59 ms   (-0.84%) |    5.21 K →    5.26 K   (+0.92%) |       18.83 s  →       18.85 s    (+0.07%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.51 ms →        5.46 ms   (-0.90%) |     920   →     928     (+0.87%) |        5.07 s  →        5.07 s    (-0.04%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.71 ms →        3.72 ms   (+0.20%) |     920   →     928     (+0.87%) |        3.42 s  →        3.45 s    (+1.08%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       61.00 ns →       54.32 ns  (-10.95%) |     920   →     928     (+0.87%) |       56.12 μs →       50.41 μs  (-10.18%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.70 ms →        3.71 ms   (+0.26%) |     920   →     928     (+0.87%) |        3.40 s  →        3.44 s    (+1.13%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       57.89 ns →       56.10 ns   (-3.09%) |     920   →     928     (+0.87%) |       53.26 μs →       52.06 μs   (-2.25%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       65.26 ms →       64.40 ms   (-1.32%) |     920   →     928     (+0.87%) |       60.04 s  →       59.76 s    (-0.46%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.68 ms →       10.56 ms   (-1.07%) |     899   →     908     (+1.00%) |        9.60 s  →        9.59 s    (-0.07%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.31 ms →       10.21 ms   (-0.93%) |     854   →     862     (+0.94%) |        8.80 s  →        8.80 s    (-0.00%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.11 ms →        5.08 ms   (-0.72%) |    1.71 K →    1.72 K   (+0.94%) |        8.73 s  →        8.75 s    (+0.21%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      631.77 μs →      622.93 μs   (-1.40%) |     854   →     862     (+0.94%) |      539.53 ms →      536.97 ms   (-0.47%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.41 ms →       51.41 ms   (-0.00%) |     209   →     209              |       10.74 s  →       10.74 s    (-0.00%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       34.11 ms →       34.11 ms   (+0.00%) |     314   →     314              |       10.71 s  →       10.71 s    (+0.00%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       25.37 ms →       25.42 ms   (+0.20%) |     419   →     419              |       10.63 s  →       10.65 s    (+0.20%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      504.89 ns →      524.33 ns   (+3.85%) |     104   →     104              |       52.51 μs →       54.53 μs   (+3.85%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.12 μs →       21.83 μs   (+3.35%) |      26   →      26              |      549.06 μs →      567.46 μs   (+3.35%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      591.73 μs →      597.45 μs   (+0.97%) |      26   →      26              |       15.39 ms →       15.53 ms   (+0.97%) | 
  │ │ ├ sirius::Density::generate                                       |      899.09 ms →      891.00 ms   (-0.90%) |      26   →      26              |       23.38 s  →       23.17 s    (-0.90%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      525.58 ms →      527.20 ms   (+0.31%) |      26   →      26              |       13.67 s  →       13.71 s    (+0.31%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.67 ms →       24.67 ms   (+0.02%) |     104   →     104              |        2.57 s  →        2.57 s    (+0.02%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.47 μs →        5.91 μs  (-30.23%) |     104   →     104              |      880.72 μs →      614.49 μs  (-30.23%) | 
+ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.79 μs →       12.75 μs  (-19.26%) |       8   →       8              |      126.33 μs →      102.01 μs  (-19.26%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.57 ms →       20.55 ms   (-0.08%) |     104   →     104              |        2.14 s  →        2.14 s    (-0.08%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.83 ms →       30.10 ms   (+0.91%) |     104   →     104              |        3.10 s  →        3.13 s    (+0.91%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.66 μs →       12.04 μs  (+24.61%) |     104   →     104              |        1.00 ms →        1.25 ms  (+24.61%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.59%) |     104   →     104              |      150.87 ms →      151.75 ms   (+0.59%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.90 ms →       28.15 ms   (+0.90%) |     104   →     104              |        2.90 s  →        2.93 s    (+0.90%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.77 ms →        4.01 ms   (+6.40%) |     104   →     104              |      392.26 ms →      417.36 ms   (+6.40%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      531.22 ns →      537.10 ns   (+1.11%) |     104   →     104              |       55.25 μs →       55.86 μs   (+1.11%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.54 ms →       42.72 ms   (+0.43%) |     104   →     104              |        4.42 s  →        4.44 s    (+0.43%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.72%) |      26   →      26              |       42.58 ms →       42.89 ms   (+0.72%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.91 ms →       88.94 ms   (+0.03%) |      26   →      26              |        2.31 s  →        2.31 s    (+0.03%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.68 ms →       88.70 ms   (+0.02%) |      26   →      26              |        2.31 s  →        2.31 s    (+0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      281.11 ms →      270.98 ms   (-3.61%) |      26   →      26              |        7.31 s  →        7.05 s    (-3.61%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      281.11 ms →      270.98 ms   (-3.61%) |      26   →      26              |        7.31 s  →        7.05 s    (-3.61%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.25 ms →       24.67 ms   (+1.70%) |      26   →      26              |      630.62 ms →      641.31 ms   (+1.70%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      231.03 ms →      219.71 ms   (-4.90%) |      26   →      26              |        6.01 s  →        5.71 s    (-4.90%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.05 ms →       24.82 ms   (+3.21%) |      26   →      26              |      625.31 ms →      645.38 ms   (+3.21%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.92 ms →       81.06 ms   (+0.17%) |      26   →      26              |        2.10 s  →        2.11 s    (+0.17%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.88 ms →        8.10 ms   (+2.80%) |      26   →      26              |      204.95 ms →      210.69 ms   (+2.80%) | 
  │ │ ├ sirius::Density::mix                                            |      219.96 ms →      214.27 ms   (-2.59%) |      26   →      26              |        5.72 s  →        5.57 s    (-2.59%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      956.02 μs →      966.45 μs   (+1.09%) |      26   →      26              |       24.86 ms →       25.13 ms   (+1.09%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.79 ms →       10.32 ms   (-4.36%) |     334   →     334              |        3.60 s  →        3.45 s    (-4.36%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.41 ms →        9.98 ms   (-4.11%) |     334   →     334              |        3.48 s  →        3.33 s    (-4.11%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.41 ms →        9.98 ms   (-4.11%) |     334   →     334              |        3.48 s  →        3.33 s    (-4.11%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.19 ms →        6.75 ms   (-6.11%) |      26   →      26              |      186.94 ms →      175.53 ms   (-6.11%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.40 ms →        5.93 ms   (-7.33%) |      26   →      26              |      166.35 ms →      154.15 ms   (-7.33%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.79 ms →      582.17 ms   (+0.24%) |      26   →      26              |       15.10 s  →       15.14 s    (+0.24%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.63 ms →      138.03 ms   (-0.44%) |      26   →      26              |        3.60 s  →        3.59 s    (-0.44%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.48 ms →       19.82 ms   (+7.28%) |      26   →      26              |      480.38 ms →      515.35 ms   (+7.28%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.28 ms →       11.16 ms   (+8.50%) |      26   →      26              |      267.32 ms →      290.05 ms   (+8.50%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.99 ms →       10.39 ms   (+4.00%) |      26   →      26              |      259.63 ms →      270.02 ms   (+4.00%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.99 ms →       10.38 ms   (+4.00%) |      26   →      26              |      259.61 ms →      270.00 ms   (+4.00%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      548.26 μs →      545.21 μs   (-0.56%) |      52   →      52              |       28.51 ms →       28.35 ms   (-0.56%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.18 ms →       49.57 ms   (+0.80%) |      26   →      26              |        1.28 s  →        1.29 s    (+0.80%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.85 ms →       47.25 ms   (+0.86%) |      26   →      26              |        1.22 s  →        1.23 s    (+0.86%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.99 ms →        3.02 ms   (+1.08%) |      52   →      52              |      155.41 ms →      157.08 ms   (+1.08%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.51 ms →        5.51 ms   (-0.07%) |      26   →      26              |      143.28 ms →      143.18 ms   (-0.07%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.80 ms →        6.80 ms   (+0.02%) |      26   →      26              |      176.67 ms →      176.71 ms   (+0.02%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.07 ms →       90.99 ms   (-0.09%) |      26   →      26              |        2.37 s  →        2.37 s    (-0.09%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.74 ms →      294.43 ms   (+0.58%) |      26   →      26              |        7.61 s  →        7.66 s    (+0.58%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      284.66 ms →      274.17 ms   (-3.68%) |      26   →      26              |        7.40 s  →        7.13 s    (-3.68%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      284.66 ms →      274.17 ms   (-3.68%) |      26   →      26              |        7.40 s  →        7.13 s    (-3.68%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.17 ms →       27.20 ms   (+0.09%) |      26   →      26              |      706.47 ms →      707.10 ms   (+0.09%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      229.70 ms →      219.10 ms   (-4.62%) |      26   →      26              |        5.97 s  →        5.70 s    (-4.62%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.01 ms →       24.03 ms   (+0.07%) |      26   →      26              |      624.30 ms →      624.74 ms   (+0.07%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.59 ms →        5.49 ms   (-1.90%) |      26   →      26              |      145.39 ms →      142.62 ms   (-1.90%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.54 ms →       11.66 ms  (+10.59%) |     182   →     182              |        1.92 s  →        2.12 s   (+10.59%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        9.99 ms →       11.15 ms  (+11.59%) |     182   →     182              |        1.82 s  →        2.03 s   (+11.59%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.99 ms →       11.15 ms  (+11.59%) |     182   →     182              |        1.82 s  →        2.03 s   (+11.59%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.18 ms →       10.11 ms   (-9.52%) |      78   →      78              |      871.80 ms →      788.80 ms   (-9.52%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.74 ms →        9.81 ms   (-8.68%) |      78   →      78              |      837.96 ms →      765.22 ms   (-8.68%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.14 ms →        9.94 ms   (-2.03%) |      26   →      26              |      263.68 ms →      258.32 ms   (-2.03%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      115.27 μs →      117.50 μs   (+1.94%) |      26   →      26              |        3.00 ms →        3.05 ms   (+1.94%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      110.18 μs →      111.90 μs   (+1.56%) |      26   →      26              |        2.86 ms →        2.91 ms   (+1.56%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.04 ms →        5.23 ms   (+3.67%) |       2   →       2              |       10.09 ms →       10.46 ms   (+3.67%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.19 ms →       11.17 ms   (+9.60%) |       6   →       6              |       61.17 ms →       67.04 ms   (+9.60%) | 
- │ │ └ sirius::Periodic_function|inner_local                           |       10.00 ms →       11.06 ms  (+10.62%) |       6   →       6              |       59.99 ms →       66.36 ms  (+10.62%) | 
- │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.00 ms →       11.06 ms  (+10.63%) |       6   →       6              |       59.98 ms →       66.36 ms  (+10.63%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.88 ms →        9.79 ms   (-9.98%) |       3   →       3              |       32.63 ms →       29.37 ms   (-9.98%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.72 ms →        9.66 ms   (-9.93%) |       3   →       3              |       32.17 ms →       28.98 ms   (-9.93%) | 
- ├ sirius::Periodic_function|inner                                     |        9.93 ms →       11.60 ms  (+16.80%) |       2   →       2              |       19.87 ms →       23.21 ms  (+16.80%) | 
- │ └ sirius::Periodic_function|inner_local                             |        9.72 ms →       11.55 ms  (+18.87%) |       2   →       2              |       19.43 ms →       23.10 ms  (+18.87%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        9.72 ms →       11.55 ms  (+18.87%) |       2   →       2              |       19.43 ms →       23.10 ms  (+18.87%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.87 ms →        9.98 ms   (-8.20%) |       1   →       1              |       10.87 ms →        9.98 ms   (-8.20%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.55 ms →        9.97 ms   (-5.55%) |       1   →       1              |       10.55 ms →        9.97 ms   (-5.55%) | 
  └ sirius::finalize                                                    |      304.57 ms →      298.54 ms   (-1.98%) |       1   →       1              |      304.57 ms →      298.54 ms   (-1.98%) | 
  ====================================================================================================================================================================================================
```
