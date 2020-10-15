# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      250.68 s  →      224.19 s   (-10.57%) |       1   →       1              |      250.68 s  →      224.19 s   (-10.57%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.76 s    (+0.42%) |       1   →       1              |        2.75 s  →        2.76 s    (+0.42%) | 
  ├ sirius::Simulation_context::initialize                              |        2.90 s  →        2.90 s    (+0.12%) |       1   →       1              |        2.90 s  →        2.90 s    (+0.12%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      232.30 μs →        3.61 ms (+1452.12%) |       1   →       1              |      232.30 μs →        3.61 ms (+1452.12%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      145.12 ms →      153.86 ms   (+6.02%) |       1   →       1              |      145.12 ms →      153.86 ms   (+6.02%) | 
  │ │ ├ sirius::Atom_type::init                                         |       61.37 ms →       64.80 ms   (+5.59%) |       2   →       2              |      122.75 ms →      129.61 ms   (+5.59%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.29 ms →       24.16 ms   (+8.36%) |       1   →       1              |       22.29 ms →       24.16 ms   (+8.36%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.28 ms →        6.41 ms   (+2.04%) |       1   →       1              |        6.28 ms →        6.41 ms   (+2.04%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       15.97 ms →       17.70 ms  (+10.83%) |       1   →       1              |       15.97 ms →       17.70 ms  (+10.83%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       15.95 ms →       17.68 ms  (+10.86%) |       1   →       1              |       15.95 ms →       17.68 ms  (+10.86%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (-0.18%) |       1   →       1              |        4.16 ms →        4.16 ms   (-0.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.01%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.01%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.63 μs →      101.09 μs   (-4.30%) |       1   →       1              |      105.63 μs →      101.09 μs   (-4.30%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.70 s    (+0.52%) |       1   →       1              |        2.68 s  →        2.70 s    (+0.52%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.76 ms →       10.90 ms   (+1.31%) |       1   →       1              |       10.76 ms →       10.90 ms   (+1.31%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.37 ms →        4.46 ms   (+1.93%) |       1   →       1              |        4.37 ms →        4.46 ms   (+1.93%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.39 ms   (+0.67%) |       1   →       1              |        6.35 ms →        6.39 ms   (+0.67%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.38 ms   (+0.68%) |       1   →       1              |        6.33 ms →        6.38 ms   (+0.68%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.84 ms →        3.89 ms   (+1.39%) |       1   →       1              |        3.84 ms →        3.89 ms   (+1.39%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (-0.17%) |       1   →       1              |        2.32 ms →        2.32 ms   (-0.17%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      105.15 μs →       99.38 μs   (-5.49%) |       1   →       1              |      105.15 μs →       99.38 μs   (-5.49%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.52 ms →       65.36 ms   (+2.90%) |       2   →       2              |      127.03 ms →      130.71 ms   (+2.90%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.20 ms   (+0.86%) |       2   →       2              |       10.32 ms →       10.41 ms   (+0.86%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.55 ms →        4.47 ms   (-1.74%) |       1   →       1              |        4.55 ms →        4.47 ms   (-1.74%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.29 ms →       21.81 ms   (-2.17%) |       2   →       2              |       44.58 ms →       43.61 ms   (-2.17%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.04 ms →       14.88 ms   (-1.06%) |       2   →       2              |       30.07 ms →       29.75 ms   (-1.06%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.57 ms →       19.71 ms   (+0.68%) |       4   →       4              |       78.30 ms →       78.83 ms   (+0.68%) | 
  │   ├ sddk::Gvec::init                                                |      171.23 ms →      171.27 ms   (+0.02%) |       2   →       2              |      342.46 ms →      342.54 ms   (+0.02%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.06 ms →      128.99 ms   (-0.05%) |       2   →       2              |      258.12 ms →      257.98 ms   (-0.05%) | 
- │   ├ sddk::Gvec_shells                                               |      175.88 ms →      198.17 ms  (+12.67%) |       1   →       1              |      175.88 ms →      198.17 ms  (+12.67%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.31 ms   (+0.10%) |       1   →       1              |        1.31 ms →        1.31 ms   (+0.10%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.67 ms →      293.56 ms   (+0.65%) |       2   →       2              |      583.35 ms →      587.13 ms   (+0.65%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.50 ms →       77.96 ms   (+1.91%) |       1   →       1              |       76.50 ms →       77.96 ms   (+1.91%) | 
  │ ├ sirius::K_point::K_point                                          |        2.93 μs →        2.73 μs   (-6.77%) |       4   →       4              |       11.71 μs →       10.92 μs   (-6.77%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.40 ms →       77.86 ms   (+1.91%) |       1   →       1              |       76.40 ms →       77.86 ms   (+1.91%) | 
  │   └ sirius::K_point::initialize                                     |       19.09 ms →       19.44 ms   (+1.86%) |       4   →       4              |       76.35 ms →       77.77 ms   (+1.86%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.45 ms →       14.77 ms   (+2.24%) |       4   →       4              |       57.78 ms →       59.08 ms   (+2.24%) | 
  │     │ └ sddk::Gvec::init                                            |        3.93 ms →        3.96 ms   (+0.82%) |       4   →       4              |       15.73 ms →       15.86 ms   (+0.82%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.39 μs →        9.35 μs   (-0.47%) |       4   →       4              |       37.56 μs →       37.38 μs   (-0.47%) | 
  │     └ sirius::K_point::update                                       |        3.31 ms →        3.33 ms   (+0.71%) |       4   →       4              |       13.22 ms →       13.32 ms   (+0.71%) | 
  │       └ sirius::Beta_projectors                                     |        1.73 ms →        1.74 ms   (+0.65%) |       4   →       4              |        6.90 ms →        6.95 ms   (+0.65%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      918.32 μs →      920.66 μs   (+0.26%) |       4   →       4              |        3.67 ms →        3.68 ms   (+0.26%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.14 ms →        5.21 ms   (+1.52%) |       2   →       2              |       10.27 ms →       10.43 ms   (+1.52%) | 
  ├ sirius::Potential                                                   |      163.03 ms →      161.15 ms   (-1.15%) |       1   →       1              |      163.03 ms →      161.15 ms   (-1.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.76 ms →        5.77 ms   (+0.28%) |       6   →       6              |       34.55 ms →       34.65 ms   (+0.28%) | 
  │ └ sirius::Potential::update                                         |      127.76 ms →      125.76 ms   (-1.56%) |       1   →       1              |      127.76 ms →      125.76 ms   (-1.56%) | 
  │   └ sirius::Potential::generate_local_potential                     |      127.06 ms →      125.10 ms   (-1.54%) |       1   →       1              |      127.06 ms →      125.10 ms   (-1.54%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.39 ms →      109.33 ms   (-1.85%) |       1   →       1              |      111.39 ms →      109.33 ms   (-1.85%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.80 ms →       14.87 ms   (+0.49%) |       1   →       1              |       14.80 ms →       14.87 ms   (+0.49%) | 
  ├ sirius::Density                                                     |      135.21 ms →      136.96 ms   (+1.30%) |       1   →       1              |      135.21 ms →      136.96 ms   (+1.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.09 ms →        5.14 ms   (+1.13%) |       2   →       2              |       10.17 ms →       10.29 ms   (+1.13%) | 
  │ └ sirius::Density::update                                           |      124.77 ms →      126.38 ms   (+1.29%) |       1   →       1              |      124.77 ms →      126.38 ms   (+1.29%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.36 ms →      125.96 ms   (+1.29%) |       1   →       1              |      124.36 ms →      125.96 ms   (+1.29%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      103.56 μs →      115.42 μs  (+11.45%) |       1   →       1              |      103.56 μs →      115.42 μs  (+11.45%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.67 ms →      110.42 ms   (-1.99%) |       1   →       1              |      112.67 ms →      110.42 ms   (-1.99%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       11.15 ms →       14.97 ms  (+34.23%) |       1   →       1              |       11.15 ms →       14.97 ms  (+34.23%) | 
  ├ sirius::Density::initial_density                                    |      178.72 ms →      177.26 ms   (-0.82%) |       1   →       1              |      178.72 ms →      177.26 ms   (-0.82%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.33 ms →      109.44 ms   (-1.70%) |       1   →       1              |      111.33 ms →      109.44 ms   (-1.70%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.33 ms →       12.09 ms   (+6.74%) |       2   →       2              |       22.66 ms →       24.18 ms   (+6.74%) | 
+ │ └ sirius::Periodic_function::integrate                              |       12.58 ms →       11.26 ms  (-10.48%) |       1   →       1              |       12.58 ms →       11.26 ms  (-10.48%) | 
  ├ sirius::Potential::generate                                         |      591.56 ms →      591.27 ms   (-0.05%) |       1   →       1              |      591.56 ms →      591.27 ms   (-0.05%) | 
  │ ├ sirius::Potential::poisson                                        |      136.80 ms →      138.02 ms   (+0.89%) |       1   →       1              |      136.80 ms →      138.02 ms   (+0.89%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.57 ms →       19.45 ms  (+17.37%) |       1   →       1              |       16.57 ms →       19.45 ms  (+17.37%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.38 ms →       11.37 ms   (+9.48%) |       1   →       1              |       10.38 ms →       11.37 ms   (+9.48%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.92 ms →        9.89 ms   (-0.39%) |       1   →       1              |        9.92 ms →        9.89 ms   (-0.39%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.92 ms →        9.89 ms   (-0.39%) |       1   →       1              |        9.92 ms →        9.89 ms   (-0.39%) | 
  │ ├ sirius::Periodic_function::add                                    |      546.33 μs →      552.42 μs   (+1.12%) |       2   →       2              |        1.09 ms →        1.10 ms   (+1.12%) | 
  │ ├ sirius::Potential::xc                                             |       53.10 ms →       53.50 ms   (+0.76%) |       1   →       1              |       53.10 ms →       53.50 ms   (+0.76%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.80 ms →       51.21 ms   (+0.81%) |       1   →       1              |       50.80 ms →       51.21 ms   (+0.81%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.57 ms →        5.68 ms   (+1.93%) |       2   →       2              |       11.14 ms →       11.36 ms   (+1.93%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.16 ms →        5.12 ms   (-0.64%) |       1   →       1              |        5.16 ms →        5.12 ms   (-0.64%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.72 ms →        5.54 ms   (-3.16%) |       1   →       1              |        5.72 ms →        5.54 ms   (-3.16%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.54 ms →       92.74 ms   (-0.85%) |       1   →       1              |       93.54 ms →       92.74 ms   (-0.85%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.97 ms →      299.01 ms   (-0.32%) |       1   →       1              |      299.97 ms →      299.01 ms   (-0.32%) | 
  ├ sirius::Hamiltonian0                                                |        8.38 ms →        8.43 ms   (+0.61%) |       1   →       1              |        8.38 ms →        8.43 ms   (+0.61%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        8.08 ms   (+0.75%) |       1   →       1              |        8.02 ms →        8.08 ms   (+0.75%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.69 ms →        4.75 ms   (+1.30%) |       1   →       1              |        4.69 ms →        4.75 ms   (+1.30%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.41 ms →        2.41 ms   (-0.13%) |       1   →       1              |        2.41 ms →        2.41 ms   (-0.13%) | 
  │ ├ sirius::Non_local_operator                                        |       67.94 μs →       63.93 μs   (-5.91%) |       2   →       2              |      135.88 μs →      127.85 μs   (-5.91%) | 
  │ ├ sirius::D_operator::initialize                                    |       97.75 μs →       98.15 μs   (+0.40%) |       1   →       1              |       97.75 μs →       98.15 μs   (+0.40%) | 
  │ └ sirius::Q_operator::initialize                                    |       72.01 μs →       71.80 μs   (-0.29%) |       1   →       1              |       72.01 μs →       71.80 μs   (-0.29%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.15 s  →        3.13 s    (-0.64%) |       1   →       1              |        3.15 s  →        3.13 s    (-0.64%) | 
  │ ├ sirius::Hamiltonian_k                                             |      373.90 μs →      383.29 μs   (+2.51%) |       4   →       4              |        1.50 ms →        1.53 ms   (+2.51%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      368.08 μs →      377.64 μs   (+2.60%) |       4   →       4              |        1.47 ms →        1.51 ms   (+2.60%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.94 μs →        3.62 μs   (-8.16%) |       4   →       4              |       15.77 μs →       14.48 μs   (-8.16%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      785.94 ms →      780.89 ms   (-0.64%) |       4   →       4              |        3.14 s  →        3.12 s    (-0.64%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       31.79 ms →       32.04 ms   (+0.79%) |      16   →      16              |      508.64 ms →      512.63 ms   (+0.79%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.32 ms →       14.68 ms   (+2.57%) |       4   →       4              |       57.26 ms →       58.73 ms   (+2.57%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.32 ms →        5.61 ms   (+5.34%) |       4   →       4              |       21.30 ms →       22.44 ms   (+5.34%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.83 ms →      352.53 ms   (-0.65%) |       4   →       4              |        1.42 s  →        1.41 s    (-0.65%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      257.43 ms →      253.80 ms   (-1.41%) |       4   →       4              |        1.03 s  →        1.02 s    (-1.41%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.18 ms →       60.72 ms   (-3.90%) |       4   →       4              |      252.74 ms →      242.89 ms   (-3.90%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       15.90 ms →       16.09 ms   (+1.14%) |       4   →       4              |       63.62 ms →       64.34 ms   (+1.14%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.90 ms →       16.08 ms   (+1.15%) |       4   →       4              |       63.61 ms →       64.33 ms   (+1.15%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.80 ms →       38.15 ms   (-6.50%) |       4   →       4              |      163.22 ms →      152.60 ms   (-6.50%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       15.90 ms →       16.02 ms   (+0.77%) |       4   →       4              |       63.59 ms →       64.08 ms   (+0.77%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.89 ms →       16.02 ms   (+0.77%) |       4   →       4              |       63.57 ms →       64.06 ms   (+0.77%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.97 ms →       51.65 ms   (-2.50%) |       4   →       4              |      211.88 ms →      206.59 ms   (-2.50%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.98 ms →       33.62 ms   (-3.89%) |       4   →       4              |      139.93 ms →      134.49 ms   (-3.89%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.93 ms →        1.94 ms   (+0.39%) |       4   →       4              |        7.72 ms →        7.75 ms   (+0.39%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.25 ms →       42.48 ms   (+2.98%) |       4   →       4              |      165.00 ms →      169.93 ms   (+2.98%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.13 ms →        9.35 ms  (+14.96%) |       4   →       4              |       32.54 ms →       37.40 ms  (+14.96%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.14 ms   (+0.19%) |       8   →       8              |      216.69 ms →      217.09 ms   (+0.19%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.60 ms →       15.33 ms   (-1.70%) |       8   →       8              |      124.79 ms →      122.67 ms   (-1.70%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.56 ms →       15.29 ms   (-1.70%) |       8   →       8              |      124.44 ms →      122.33 ms   (-1.70%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       30.00 ns →       29.50 ns   (-1.67%) |       8   →       8              |      240.00 ns →      236.00 ns   (-1.67%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.38 ms →       15.09 ms   (-1.91%) |       8   →       8              |      123.07 ms →      120.72 ms   (-1.91%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       31.13 ns →       38.63 ns  (+24.10%) |       8   →       8              |      249.00 ns →      309.00 ns  (+24.10%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      130.11 ms →      128.12 ms   (-1.53%) |       4   →       4              |      520.44 ms →      512.47 ms   (-1.53%) | 
  │ │ └ sddk::wf_trans                                                  |       23.58 ms →       23.57 ms   (-0.05%) |       4   →       4              |       94.34 ms →       94.29 ms   (-0.05%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.40 ms →       23.36 ms   (-0.17%) |       4   →       4              |       93.61 ms →       93.45 ms   (-0.17%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      357.50 ns →      327.75 ns   (-8.32%) |       4   →       4              |        1.43 μs →        1.31 μs   (-8.32%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      239.87 s  →      213.39 s   (-11.04%) |       1   →       1              |      239.87 s  →      213.39 s   (-11.04%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.66 ms →        5.69 ms   (+0.47%) |      19   →      19              |      107.62 ms →      108.13 ms   (+0.47%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        9.20 s  →        7.89 s   (-14.27%) |      26   →      27     (+3.85%) |      239.26 s  →      213.01 s   (-10.97%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.73 ms →        4.86 ms   (+2.66%) |      26   →      27     (+3.85%) |      123.04 ms →      131.17 ms   (+6.61%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.38 ms →        4.50 ms   (+2.80%) |      26   →      27     (+3.85%) |      113.79 ms →      121.47 ms   (+6.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      968.94 μs →      981.67 μs   (+1.31%) |      26   →      27     (+3.85%) |       25.19 ms →       26.51 ms   (+5.21%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.52 ms →        2.62 ms   (+4.16%) |      26   →      27     (+3.85%) |       65.50 ms →       70.85 ms   (+8.17%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.41 μs →       64.67 μs   (+0.40%) |      52   →      54     (+3.85%) |        3.35 ms →        3.49 ms   (+4.27%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.45 μs →       93.86 μs   (+0.44%) |      26   →      27     (+3.85%) |        2.43 ms →        2.53 ms   (+4.30%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.70 μs →       66.07 μs   (+0.57%) |      26   →      27     (+3.85%) |        1.71 ms →        1.78 ms   (+4.43%) | 
+ │ │ ├ sirius::Band::solve                                             |        7.11 s  →        5.79 s   (-18.53%) |      26   →      27     (+3.85%) |      184.74 s  →      156.30 s   (-15.40%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      339.56 μs →      336.77 μs   (-0.82%) |     104   →     108     (+3.85%) |       35.31 ms →       36.37 ms   (+2.99%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      334.01 μs →      331.29 μs   (-0.81%) |     104   →     108     (+3.85%) |       34.74 ms →       35.78 ms   (+3.00%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.97 μs →        3.94 μs   (-0.79%) |     104   →     108     (+3.85%) |      413.33 μs →      425.83 μs   (+3.02%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.78 s  →        1.45 s   (-18.53%) |     104   →     108     (+3.85%) |      184.70 s  →      156.26 s   (-15.40%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.97 ms →       12.18 ms   (+1.73%) |     104   →     108     (+3.85%) |        1.25 s  →        1.32 s    (+5.65%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      691.03 ns →      708.51 ns   (+2.53%) |     624   →     648     (+3.85%) |      431.20 μs →      459.11 μs   (+6.47%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (+0.10%) |     104   →     108     (+3.85%) |      190.07 ms →      197.57 ms   (+3.95%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.84 μs →      351.25 μs   (-0.45%) |     104   →     108     (+3.85%) |       36.70 ms →       37.93 ms   (+3.38%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      549.59 μs →      552.20 μs   (+0.48%) |     208   →     216     (+3.85%) |      114.31 ms →      119.28 ms   (+4.34%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.75 s  →        1.42 s   (-18.79%) |     104   →     108     (+3.85%) |      182.33 s  →      153.77 s   (-15.66%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.72 ms →       70.81 ms   (+1.56%) |     911   →     924     (+1.43%) |       63.51 s  →       65.43 s    (+3.01%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.47 ms →       44.91 ms   (+0.98%) |     911   →     924     (+1.43%) |       40.51 s  →       41.49 s    (+2.42%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.69 ms →        8.52 ms   (-1.94%) |     911   →     924     (+1.43%) |        7.91 s  →        7.87 s    (-0.54%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      229.24 μs →      224.78 μs   (-1.94%) |     911   →     924     (+1.43%) |      208.84 ms →      207.70 ms   (-0.54%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.99 ms →        1.91 ms   (-4.26%) |     104   →     108     (+3.85%) |      207.04 ms →      205.85 ms   (-0.57%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.86 ms →        6.47 ms   (-5.75%) |     911   →     924     (+1.43%) |        6.25 s  →        5.98 s    (-4.41%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       87.82 μs →       87.10 μs   (-0.82%) |     911   →     924     (+1.43%) |       80.00 ms →       80.48 ms   (+0.60%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      746.46 μs →      721.65 μs   (-3.32%) |     104   →     108     (+3.85%) |       77.63 ms →       77.94 ms   (+0.39%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.82 ms →        9.67 ms   (-1.50%) |     911   →     924     (+1.43%) |        8.95 s  →        8.94 s    (-0.10%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.20 ms →        5.93 ms   (-4.31%) |     911   →     924     (+1.43%) |        5.65 s  →        5.48 s    (-2.94%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.53 ms   (+0.22%) |     911   →     924     (+1.43%) |        1.39 s  →        1.41 s    (+1.65%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.86 ms →        9.09 ms   (+2.54%) |     911   →     924     (+1.43%) |        8.07 s  →        8.40 s    (+4.00%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.51 ms →        1.57 ms   (+3.73%) |     911   →     924     (+1.43%) |        1.38 s  →        1.45 s    (+5.21%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.42 ms →        7.63 ms   (+2.87%) |    1.82 K →    1.85 K   (+1.43%) |       13.52 s  →       14.10 s    (+4.34%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.24 ms →       28.37 ms   (+0.47%) |     911   →     924     (+1.43%) |       25.73 s  →       26.22 s    (+1.90%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.08 ms →        2.12 ms   (+1.82%) |    1.72 K →    1.74 K   (+1.28%) |        3.57 s  →        3.68 s    (+3.12%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       67.25 ns →       53.93 ns  (-19.81%) |    1.72 K →    1.74 K   (+1.28%) |      115.54 μs →       93.84 μs  (-18.78%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.07 ms →        2.10 ms   (+1.80%) |    1.72 K →    1.74 K   (+1.28%) |        3.55 s  →        3.66 s    (+3.10%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       58.31 ns →       70.85 ns  (+21.52%) |    1.72 K →    1.74 K   (+1.28%) |      100.17 μs →      123.29 μs  (+23.08%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      793.42 μs →      905.99 μs  (+14.19%) |     911   →     924     (+1.43%) |      722.81 ms →      837.13 ms  (+15.82%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      850.50 μs →      842.17 μs   (-0.98%) |     911   →     924     (+1.43%) |      774.80 ms →      778.17 ms   (+0.43%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.43 ms →        5.41 ms   (-0.29%) |    3.54 K →    3.59 K   (+1.36%) |       19.22 s  →       19.43 s    (+1.06%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.69 ms →        3.68 ms   (-0.25%) |    5.15 K →    5.22 K   (+1.28%) |       19.02 s  →       19.22 s    (+1.03%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.50 ms →        5.48 ms   (-0.29%) |     911   →     924     (+1.43%) |        5.01 s  →        5.06 s    (+1.14%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.80 ms →        3.73 ms   (-2.03%) |     911   →     924     (+1.43%) |        3.47 s  →        3.44 s    (-0.63%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       57.28 ns →       47.07 ns  (-17.82%) |     911   →     924     (+1.43%) |       52.18 μs →       43.49 μs  (-16.64%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.79 ms →        3.71 ms   (-2.01%) |     911   →     924     (+1.43%) |        3.45 s  →        3.43 s    (-0.61%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       55.08 ns →       37.21 ns  (-32.44%) |     911   →     924     (+1.43%) |       50.18 μs →       34.39 μs  (-31.48%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       74.33 ms →       37.79 ms  (-49.16%) |     911   →     924     (+1.43%) |       67.71 s  →       34.91 s   (-48.44%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.71 ms →       10.30 ms   (-3.77%) |     891   →     902     (+1.23%) |        9.54 s  →        9.29 s    (-2.58%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.34 ms →        9.93 ms   (-4.00%) |     845   →     853     (+0.95%) |        8.74 s  →        8.47 s    (-3.09%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.13 ms →        4.92 ms   (-4.00%) |    1.69 K →    1.71 K   (+0.95%) |        8.67 s  →        8.40 s    (-3.09%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      643.71 μs →      661.04 μs   (+2.69%) |     845   →     853     (+0.95%) |      543.93 ms →      563.87 ms   (+3.67%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.65 ms →       35.82 ms  (-30.64%) |     209   →     358    (+71.29%) |       10.80 s  →       12.82 s   (+18.80%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.27 ms →       20.97 ms  (-38.81%) |     314   →     608    (+93.63%) |       10.76 s  →       12.75 s   (+18.48%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.51 ms →       14.75 ms  (-42.18%) |     419   →     858   (+104.77%) |       10.69 s  →       12.66 s   (+18.41%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      551.66 ns →      462.19 ns  (-16.22%) |     104   →     108     (+3.85%) |       57.37 μs →       49.92 μs  (-13.00%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.52 μs →       21.84 μs   (+1.48%) |      26   →      27     (+3.85%) |      559.48 μs →      589.60 μs   (+5.38%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      591.95 μs →      597.88 μs   (+1.00%) |      26   →      27     (+3.85%) |       15.39 ms →       16.14 ms   (+4.89%) | 
  │ │ ├ sirius::Density::generate                                       |      899.09 ms →      892.41 ms   (-0.74%) |      26   →      27     (+3.85%) |       23.38 s  →       24.10 s    (+3.08%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      529.89 ms →      522.61 ms   (-1.37%) |      26   →      27     (+3.85%) |       13.78 s  →       14.11 s    (+2.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.04 ms →       22.97 ms   (-8.30%) |     104   →     108     (+3.85%) |        2.60 s  →        2.48 s    (-4.77%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.53 μs →        8.86 μs   (+3.83%) |     104   →     108     (+3.85%) |      887.09 μs →      956.48 μs   (+7.82%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.25 μs →       15.96 μs   (+4.63%) |       8   →       8              |      122.01 μs →      127.65 μs   (+4.63%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.94 ms →       18.74 ms  (-10.49%) |     104   →     108     (+3.85%) |        2.18 s  →        2.02 s    (-7.04%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.45 ms →       30.40 ms   (-0.18%) |     104   →     108     (+3.85%) |        3.17 s  →        3.28 s    (+3.66%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.36 μs →        9.68 μs   (+3.48%) |     104   →     108     (+3.85%) |      973.09 μs →        1.05 ms   (+7.46%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.15%) |     104   →     108     (+3.85%) |      151.59 ms →      157.65 ms   (+4.00%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.52 ms →       28.46 ms   (-0.22%) |     104   →     108     (+3.85%) |        2.97 s  →        3.07 s    (+3.62%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.39 ms →        4.33 ms   (-1.26%) |     104   →     108     (+3.85%) |      456.06 ms →      467.65 ms   (+2.54%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      632.46 ns →      534.31 ns  (-15.52%) |     104   →     108     (+3.85%) |       65.78 μs →       57.71 μs  (-12.27%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.52 ms →       42.79 ms   (+0.65%) |     104   →     108     (+3.85%) |        4.42 s  →        4.62 s    (+4.52%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.14%) |      26   →      27     (+3.85%) |       42.55 ms →       44.25 ms   (+3.99%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.86 ms →       88.86 ms   (-0.00%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.84%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.63 ms →       88.63 ms   (-0.00%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.84%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.26 ms →      277.92 ms   (+0.24%) |      26   →      27     (+3.85%) |        7.21 s  →        7.50 s    (+4.09%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.26 ms →      277.92 ms   (+0.24%) |      26   →      27     (+3.85%) |        7.21 s  →        7.50 s    (+4.09%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.44 ms →       25.88 ms   (+5.88%) |      26   →      27     (+3.85%) |      635.47 ms →      698.72 ms   (+9.95%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.91 ms →      225.86 ms   (-0.46%) |      26   →      27     (+3.85%) |        5.90 s  →        6.10 s    (+3.37%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.15 ms →       24.37 ms   (+0.91%) |      26   →      27     (+3.85%) |      628.01 ms →      658.12 ms   (+4.79%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.13 ms →       80.50 ms   (-1.98%) |      26   →      27     (+3.85%) |        2.14 s  →        2.17 s    (+1.79%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.22 ms →        7.78 ms  (+25.06%) |      26   →      27     (+3.85%) |      161.76 ms →      210.09 ms  (+29.87%) | 
  │ │ ├ sirius::Density::mix                                            |      210.14 ms →      218.12 ms   (+3.80%) |      26   →      27     (+3.85%) |        5.46 s  →        5.89 s    (+7.79%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      923.21 μs →      939.91 μs   (+1.81%) |      26   →      27     (+3.85%) |       24.00 ms →       25.38 ms   (+5.72%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.79 ms →       10.46 ms   (-3.04%) |     320   →     349     (+9.06%) |        3.45 s  →        3.65 s    (+5.75%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.44 ms →        9.96 ms   (-4.61%) |     320   →     349     (+9.06%) |        3.34 s  →        3.48 s    (+4.04%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.44 ms →        9.96 ms   (-4.61%) |     320   →     349     (+9.06%) |        3.34 s  →        3.47 s    (+4.04%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.14 ms →        6.11 ms  (-14.39%) |      26   →      27     (+3.85%) |      185.54 ms →      164.96 ms  (-11.09%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.28 ms →        5.25 ms  (-16.31%) |      26   →      27     (+3.85%) |      163.17 ms →      141.81 ms  (-13.09%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.16 ms →      580.44 ms   (+0.22%) |      26   →      27     (+3.85%) |       15.06 s  →       15.67 s    (+4.07%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.99 ms →      138.06 ms   (+0.78%) |      26   →      27     (+3.85%) |        3.56 s  →        3.73 s    (+4.66%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.09 ms →       18.66 ms  (+15.97%) |      26   →      27     (+3.85%) |      418.42 ms →      503.90 ms  (+20.43%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.31 ms →       11.20 ms   (+8.62%) |      26   →      27     (+3.85%) |      268.17 ms →      302.50 ms  (+12.80%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.98 ms →        9.90 ms   (-0.76%) |      26   →      27     (+3.85%) |      259.46 ms →      267.39 ms   (+3.06%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.98 ms →        9.90 ms   (-0.76%) |      26   →      27     (+3.85%) |      259.45 ms →      267.38 ms   (+3.06%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      543.95 μs →      557.70 μs   (+2.53%) |      52   →      54     (+3.85%) |       28.29 ms →       30.12 ms   (+6.47%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.01 ms →       48.78 ms   (-0.48%) |      26   →      27     (+3.85%) |        1.27 s  →        1.32 s    (+3.35%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.66 ms →       46.41 ms   (-0.54%) |      26   →      27     (+3.85%) |        1.21 s  →        1.25 s    (+3.28%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.03 ms   (+0.48%) |      52   →      54     (+3.85%) |      156.81 ms →      163.63 ms   (+4.35%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.40 ms →        5.14 ms   (-4.91%) |      26   →      27     (+3.85%) |      140.44 ms →      138.68 ms   (-1.26%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.67 ms →        6.57 ms   (-1.44%) |      26   →      27     (+3.85%) |      173.32 ms →      177.40 ms   (+2.35%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       91.31 ms   (+0.46%) |      26   →      27     (+3.85%) |        2.36 s  →        2.47 s    (+4.32%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.23 ms →      293.30 ms   (+0.03%) |      26   →      27     (+3.85%) |        7.62 s  →        7.92 s    (+3.87%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.64 ms →      281.52 ms   (-0.04%) |      26   →      27     (+3.85%) |        7.32 s  →        7.60 s    (+3.80%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.64 ms →      281.52 ms   (-0.04%) |      26   →      27     (+3.85%) |        7.32 s  →        7.60 s    (+3.80%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.20 ms →       28.63 ms   (+5.24%) |      26   →      27     (+3.85%) |      707.27 ms →      772.98 ms   (+9.29%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.91 ms →      225.07 ms   (-0.81%) |      26   →      27     (+3.85%) |        5.90 s  →        6.08 s    (+3.00%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.74 ms →       23.99 ms   (+1.08%) |      26   →      27     (+3.85%) |      617.15 ms →      647.79 ms   (+4.96%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.52 ms →        7.12 ms  (+29.03%) |      26   →      27     (+3.85%) |      143.52 ms →      192.31 ms  (+33.99%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.35 ms →       10.37 ms   (+0.28%) |     182   →     189     (+3.85%) |        1.88 s  →        1.96 s    (+4.14%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.91 ms →        9.98 ms   (+0.69%) |     182   →     189     (+3.85%) |        1.80 s  →        1.89 s    (+4.56%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.91 ms →        9.98 ms   (+0.69%) |     182   →     189     (+3.85%) |        1.80 s  →        1.89 s    (+4.56%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.09 ms →       10.67 ms   (-3.76%) |      78   →      81     (+3.85%) |      865.05 ms →      864.54 ms   (-0.06%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.70 ms →       10.35 ms   (-3.25%) |      78   →      81     (+3.85%) |      834.47 ms →      838.40 ms   (+0.47%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.03 ms →       10.11 ms   (+0.75%) |      26   →      27     (+3.85%) |      260.91 ms →      272.98 ms   (+4.63%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      134.74 μs →      332.09 μs (+146.48%) |      26   →      27     (+3.85%) |        3.50 ms →        8.97 ms (+155.96%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      129.65 μs →      326.74 μs (+152.03%) |      26   →      27     (+3.85%) |        3.37 ms →        8.82 ms (+161.72%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.24 ms →        5.02 ms   (-4.09%) |       2   →       2              |       10.47 ms →       10.04 ms   (-4.09%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.08 ms →        9.88 ms   (-1.99%) |       6   →       6              |       60.48 ms →       59.28 ms   (-1.99%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.06 ms →        9.84 ms   (-2.25%) |       6   →       6              |       60.38 ms →       59.02 ms   (-2.25%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.06 ms →        9.84 ms   (-2.25%) |       6   →       6              |       60.38 ms →       59.02 ms   (-2.25%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.80 ms →       10.17 ms   (-5.86%) |       3   →       3              |       32.40 ms →       30.50 ms   (-5.86%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.79 ms →       10.08 ms   (-6.58%) |       3   →       3              |       32.37 ms →       30.24 ms   (-6.58%) | 
  ├ sirius::Periodic_function|inner                                     |        9.66 ms →       10.03 ms   (+3.80%) |       2   →       2              |       19.33 ms →       20.06 ms   (+3.80%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.65 ms →       10.02 ms   (+3.80%) |       2   →       2              |       19.31 ms →       20.04 ms   (+3.80%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.65 ms →       10.02 ms   (+3.80%) |       2   →       2              |       19.31 ms →       20.04 ms   (+3.80%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.55 ms →       10.48 ms   (-0.72%) |       1   →       1              |       10.55 ms →       10.48 ms   (-0.72%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.54 ms →       10.47 ms   (-0.67%) |       1   →       1              |       10.54 ms →       10.47 ms   (-0.67%) | 
  └ sirius::finalize                                                    |      316.55 ms →      323.26 ms   (+2.12%) |       1   →       1              |      316.55 ms →      323.26 ms   (+2.12%) | 
  ====================================================================================================================================================================================================
```
