# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      249.13 s  →      216.79 s   (-12.98%) |       1   →       1              |      249.13 s  →      216.79 s   (-12.98%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.80 s    (+3.32%) |       1   →       1              |        2.71 s  →        2.80 s    (+3.32%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        3.01 s    (+0.78%) |       1   →       1              |        2.99 s  →        3.01 s    (+0.78%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       59.04 ms →      211.21 μs  (-99.64%) |       1   →       1              |       59.04 ms →      211.21 μs  (-99.64%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      199.83 ms →      193.21 ms   (-3.31%) |       1   →       1              |      199.83 ms →      193.21 ms   (-3.31%) | 
  │ │ ├ sirius::Atom_type::init                                         |       87.76 ms →       85.02 ms   (-3.12%) |       2   →       2              |      175.52 ms →      170.04 ms   (-3.12%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.24 ms →       23.09 ms   (-4.76%) |       1   →       1              |       24.24 ms →       23.09 ms   (-4.76%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.25 ms →        6.36 ms   (+1.67%) |       1   →       1              |        6.25 ms →        6.36 ms   (+1.67%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.95 ms →       16.69 ms   (-6.99%) |       1   →       1              |       17.95 ms →       16.69 ms   (-6.99%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.92 ms →       16.67 ms   (-6.98%) |       1   →       1              |       17.92 ms →       16.67 ms   (-6.98%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.15 ms   (-0.18%) |       1   →       1              |        4.16 ms →        4.15 ms   (-0.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.12%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.12%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.58 μs →      104.81 μs   (-0.74%) |       1   →       1              |      105.58 μs →      104.81 μs   (-0.74%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.67 s    (-0.09%) |       1   →       1              |        2.68 s  →        2.67 s    (-0.09%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.77 ms   (-0.73%) |       1   →       1              |       10.85 ms →       10.77 ms   (-0.73%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.42 ms →        4.40 ms   (-0.42%) |       1   →       1              |        4.42 ms →        4.40 ms   (-0.42%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.40 ms →        6.34 ms   (-0.95%) |       1   →       1              |        6.40 ms →        6.34 ms   (-0.95%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.38 ms →        6.32 ms   (-0.93%) |       1   →       1              |        6.38 ms →        6.32 ms   (-0.93%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.87 ms →        3.82 ms   (-1.17%) |       1   →       1              |        3.87 ms →        3.82 ms   (-1.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.45%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.45%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.53 μs →      102.95 μs   (-0.56%) |       1   →       1              |      103.53 μs →      102.95 μs   (-0.56%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.02 ms →       64.56 ms   (+2.44%) |       2   →       2              |      126.05 ms →      129.13 ms   (+2.44%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.15 ms   (+0.19%) |       2   →       2              |       10.29 ms →       10.30 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (-0.05%) |       1   →       1              |        4.48 ms →        4.48 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.85 ms →       21.73 ms   (-0.56%) |       2   →       2              |       43.70 ms →       43.45 ms   (-0.56%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.08 ms →       14.83 ms   (-1.68%) |       2   →       2              |       30.17 ms →       29.66 ms   (-1.68%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.79 ms →       19.76 ms   (-0.14%) |       4   →       4              |       79.14 ms →       79.03 ms   (-0.14%) | 
  │   ├ sddk::Gvec::init                                                |      176.11 ms →      172.30 ms   (-2.16%) |       2   →       2              |      352.22 ms →      344.61 ms   (-2.16%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.97 ms →      130.14 ms   (-1.39%) |       2   →       2              |      263.94 ms →      260.27 ms   (-1.39%) | 
  │   ├ sddk::Gvec_shells                                               |      174.52 ms →      179.04 ms   (+2.59%) |       1   →       1              |      174.52 ms →      179.04 ms   (+2.59%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.76%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.76%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.66 ms →      296.22 ms   (+0.87%) |       2   →       2              |      587.31 ms →      592.45 ms   (+0.87%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.59 ms →       76.30 ms   (-0.38%) |       1   →       1              |       76.59 ms →       76.30 ms   (-0.38%) | 
  │ ├ sirius::K_point::K_point                                          |        2.28 μs →        2.44 μs   (+7.43%) |       4   →       4              |        9.10 μs →        9.78 μs   (+7.43%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.48 ms →       76.19 ms   (-0.38%) |       1   →       1              |       76.48 ms →       76.19 ms   (-0.38%) | 
  │   └ sirius::K_point::initialize                                     |       19.11 ms →       19.03 ms   (-0.43%) |       4   →       4              |       76.44 ms →       76.11 ms   (-0.43%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.47 ms →       14.38 ms   (-0.67%) |       4   →       4              |       57.89 ms →       57.50 ms   (-0.67%) | 
  │     │ └ sddk::Gvec::init                                            |        3.87 ms →        3.95 ms   (+1.85%) |       4   →       4              |       15.50 ms →       15.78 ms   (+1.85%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.49 μs →        9.11 μs   (+7.28%) |       4   →       4              |       33.96 μs →       36.43 μs   (+7.28%) | 
  │     └ sirius::K_point::update                                       |        3.31 ms →        3.33 ms   (+0.40%) |       4   →       4              |       13.26 ms →       13.31 ms   (+0.40%) | 
  │       └ sirius::Beta_projectors                                     |        1.80 ms →        1.78 ms   (-1.10%) |       4   →       4              |        7.19 ms →        7.11 ms   (-1.10%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      937.33 μs →      918.98 μs   (-1.96%) |       4   →       4              |        3.75 ms →        3.68 ms   (-1.96%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.27 ms →        5.27 ms   (+0.12%) |       2   →       2              |       10.53 ms →       10.55 ms   (+0.12%) | 
  ├ sirius::Potential                                                   |      159.64 ms →      158.18 ms   (-0.92%) |       1   →       1              |      159.64 ms →      158.18 ms   (-0.92%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.89 ms →        5.84 ms   (-0.82%) |       6   →       6              |       35.34 ms →       35.05 ms   (-0.82%) | 
  │ └ sirius::Potential::update                                         |      123.57 ms →      122.38 ms   (-0.97%) |       1   →       1              |      123.57 ms →      122.38 ms   (-0.97%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.82 ms →      121.65 ms   (-0.96%) |       1   →       1              |      122.82 ms →      121.65 ms   (-0.96%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.92 ms →      106.56 ms   (-3.06%) |       1   →       1              |      109.92 ms →      106.56 ms   (-3.06%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       12.00 ms →       14.18 ms  (+18.16%) |       1   →       1              |       12.00 ms →       14.18 ms  (+18.16%) | 
  ├ sirius::Density                                                     |      134.84 ms →      135.71 ms   (+0.65%) |       1   →       1              |      134.84 ms →      135.71 ms   (+0.65%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.20 ms →        5.20 ms   (-0.10%) |       2   →       2              |       10.40 ms →       10.39 ms   (-0.10%) | 
  │ └ sirius::Density::update                                           |      124.17 ms →      125.05 ms   (+0.71%) |       1   →       1              |      124.17 ms →      125.05 ms   (+0.71%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.74 ms →      124.62 ms   (+0.71%) |       1   →       1              |      123.74 ms →      124.62 ms   (+0.71%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.55 μs →      104.06 μs   (+1.47%) |       1   →       1              |      102.55 μs →      104.06 μs   (+1.47%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.12 ms →      109.47 ms   (-1.49%) |       1   →       1              |      111.12 ms →      109.47 ms   (-1.49%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       12.05 ms →       14.59 ms  (+21.05%) |       1   →       1              |       12.05 ms →       14.59 ms  (+21.05%) | 
  ├ sirius::Density::initial_density                                    |      177.70 ms →      178.37 ms   (+0.38%) |       1   →       1              |      177.70 ms →      178.37 ms   (+0.38%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      109.91 ms →      108.79 ms   (-1.02%) |       1   →       1              |      109.91 ms →      108.79 ms   (-1.02%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.72 ms →       12.42 ms   (+5.96%) |       2   →       2              |       23.45 ms →       24.84 ms   (+5.96%) | 
  │ └ sirius::Periodic_function::integrate                              |       11.73 ms →       11.79 ms   (+0.51%) |       1   →       1              |       11.73 ms →       11.79 ms   (+0.51%) | 
  ├ sirius::Potential::generate                                         |      593.28 ms →      592.60 ms   (-0.11%) |       1   →       1              |      593.28 ms →      592.60 ms   (-0.11%) | 
  │ ├ sirius::Potential::poisson                                        |      137.50 ms →      137.19 ms   (-0.23%) |       1   →       1              |      137.50 ms →      137.19 ms   (-0.23%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       18.06 ms →       19.63 ms   (+8.69%) |       1   →       1              |       18.06 ms →       19.63 ms   (+8.69%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.63 ms →       10.43 ms   (-1.79%) |       1   →       1              |       10.63 ms →       10.43 ms   (-1.79%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.23 ms →        9.96 ms   (-2.58%) |       1   →       1              |       10.23 ms →        9.96 ms   (-2.58%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.23 ms →        9.96 ms   (-2.59%) |       1   →       1              |       10.23 ms →        9.96 ms   (-2.59%) | 
- │ ├ sirius::Periodic_function::add                                    |      564.97 μs →      770.11 μs  (+36.31%) |       2   →       2              |        1.13 ms →        1.54 ms  (+36.31%) | 
  │ ├ sirius::Potential::xc                                             |       54.45 ms →       53.54 ms   (-1.67%) |       1   →       1              |       54.45 ms →       53.54 ms   (-1.67%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.10 ms →       51.16 ms   (-1.79%) |       1   →       1              |       52.10 ms →       51.16 ms   (-1.79%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.71 ms →        5.66 ms   (-0.83%) |       2   →       2              |       11.42 ms →       11.32 ms   (-0.83%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.24 ms →        5.11 ms   (-2.37%) |       1   →       1              |        5.24 ms →        5.11 ms   (-2.37%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.71 ms →        5.66 ms   (-0.99%) |       1   →       1              |        5.71 ms →        5.66 ms   (-0.99%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.44 ms →       93.52 ms   (+0.08%) |       1   →       1              |       93.44 ms →       93.52 ms   (+0.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.68 ms →      299.77 ms   (+0.03%) |       1   →       1              |      299.68 ms →      299.77 ms   (+0.03%) | 
  ├ sirius::Hamiltonian0                                                |        8.46 ms →        8.47 ms   (+0.17%) |       1   →       1              |        8.46 ms →        8.47 ms   (+0.17%) | 
  │ ├ sirius::Local_operator                                            |        8.11 ms →        8.12 ms   (+0.10%) |       1   →       1              |        8.11 ms →        8.12 ms   (+0.10%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.82 ms   (+1.51%) |       1   →       1              |        4.75 ms →        4.82 ms   (+1.51%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.45 ms →        2.38 ms   (-3.08%) |       1   →       1              |        2.45 ms →        2.38 ms   (-3.08%) | 
  │ ├ sirius::Non_local_operator                                        |       62.37 μs →       62.71 μs   (+0.55%) |       2   →       2              |      124.73 μs →      125.42 μs   (+0.55%) | 
  │ ├ sirius::D_operator::initialize                                    |       95.59 μs →      101.33 μs   (+6.00%) |       1   →       1              |       95.59 μs →      101.33 μs   (+6.00%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.30 μs →       69.40 μs   (+0.14%) |       1   →       1              |       69.30 μs →       69.40 μs   (+0.14%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.12 s    (+0.26%) |       1   →       1              |        3.11 s  →        3.12 s    (+0.26%) | 
  │ ├ sirius::Hamiltonian_k                                             |      384.27 μs →      369.66 μs   (-3.80%) |       4   →       4              |        1.54 ms →        1.48 ms   (-3.80%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      379.22 μs →      364.45 μs   (-3.90%) |       4   →       4              |        1.52 ms →        1.46 ms   (-3.90%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.35 μs →        3.41 μs   (+1.73%) |       4   →       4              |       13.42 μs →       13.65 μs   (+1.73%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      778.00 ms →      780.05 ms   (+0.26%) |       4   →       4              |        3.11 s  →        3.12 s    (+0.26%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.55 ms →       32.62 ms   (+0.22%) |      16   →      16              |      520.78 ms →      521.92 ms   (+0.22%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.62 ms →       14.86 ms   (+1.62%) |       4   →       4              |       58.49 ms →       59.44 ms   (+1.62%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.32 ms →        5.46 ms   (+2.64%) |       4   →       4              |       21.30 ms →       21.86 ms   (+2.64%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.04 ms →      355.02 ms   (-0.28%) |       4   →       4              |        1.42 s  →        1.42 s    (-0.28%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      256.95 ms →      257.68 ms   (+0.28%) |       4   →       4              |        1.03 s  →        1.03 s    (+0.28%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.23 ms →       63.00 ms   (-0.36%) |       4   →       4              |      252.92 ms →      252.00 ms   (-0.36%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.71 ms →       16.64 ms   (-0.43%) |       4   →       4              |       66.84 ms →       66.55 ms   (-0.43%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.71 ms →       16.64 ms   (-0.43%) |       4   →       4              |       66.83 ms →       66.54 ms   (-0.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.14 ms →       40.00 ms   (-0.35%) |       4   →       4              |      160.56 ms →      160.00 ms   (-0.35%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.36 ms →       16.32 ms   (-0.27%) |       4   →       4              |       65.44 ms →       65.27 ms   (-0.27%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.36 ms →       16.31 ms   (-0.26%) |       4   →       4              |       65.43 ms →       65.26 ms   (-0.26%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.41 ms →       53.48 ms   (+0.13%) |       4   →       4              |      213.64 ms →      213.92 ms   (+0.13%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.40 ms →       35.44 ms   (+0.09%) |       4   →       4              |      141.61 ms →      141.74 ms   (+0.09%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.89 ms →        1.94 ms   (+2.63%) |       4   →       4              |        7.58 ms →        7.77 ms   (+2.63%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       43.05 ms →       41.15 ms   (-4.43%) |       4   →       4              |      172.22 ms →      164.59 ms   (-4.43%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        9.93 ms →        8.00 ms  (-19.41%) |       4   →       4              |       39.71 ms →       32.00 ms  (-19.41%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.05 ms →       27.11 ms   (+0.21%) |       8   →       8              |      216.40 ms →      216.85 ms   (+0.21%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.36 ms →       15.17 ms   (-1.26%) |       8   →       8              |      122.89 ms →      121.34 ms   (-1.26%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.31 ms →       15.12 ms   (-1.23%) |       8   →       8              |      122.51 ms →      121.00 ms   (-1.23%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       28.75 ns →       26.00 ns   (-9.57%) |       8   →       8              |      230.00 ns →      208.00 ns   (-9.57%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.12 ms →       14.94 ms   (-1.19%) |       8   →       8              |      120.96 ms →      119.52 ms   (-1.19%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       27.25 ns →       35.00 ns  (+28.44%) |       8   →       8              |      218.00 ns →      280.00 ns  (+28.44%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      123.04 ms →      124.91 ms   (+1.52%) |       4   →       4              |      492.17 ms →      499.65 ms   (+1.52%) | 
  │ │ └ sddk::wf_trans                                                  |       23.65 ms →       23.50 ms   (-0.63%) |       4   →       4              |       94.59 ms →       94.00 ms   (-0.63%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.46 ms →       23.38 ms   (-0.34%) |       4   →       4              |       93.84 ms →       93.52 ms   (-0.34%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      491.75 ns →      357.50 ns  (-27.30%) |       4   →       4              |        1.97 μs →        1.43 μs  (-27.30%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      238.31 s  →      205.89 s   (-13.60%) |       1   →       1              |      238.31 s  →      205.89 s   (-13.60%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms →        5.74 ms   (-0.50%) |      19   →      19              |      109.62 ms →      109.08 ms   (-0.50%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        9.15 s  →        8.22 s   (-10.20%) |      26   →      25     (-3.85%) |      237.90 s  →      205.41 s   (-13.66%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.95 ms →        4.59 ms   (-7.23%) |      26   →      25     (-3.85%) |      128.72 ms →      114.81 ms  (-10.80%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.59 ms →        4.23 ms   (-7.80%) |      26   →      25     (-3.85%) |      119.39 ms →      105.85 ms  (-11.34%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      978.50 μs →      974.45 μs   (-0.41%) |      26   →      25     (-3.85%) |       25.44 ms →       24.36 ms   (-4.24%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.72 ms →        2.37 ms  (-12.72%) |      26   →      25     (-3.85%) |       70.63 ms →       59.28 ms  (-16.07%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.39 μs →       64.67 μs   (+0.44%) |      52   →      50     (-3.85%) |        3.35 ms →        3.23 ms   (-3.42%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.96 μs →       94.59 μs   (-0.39%) |      26   →      25     (-3.85%) |        2.47 ms →        2.36 ms   (-4.22%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.40 μs →       66.07 μs   (-0.50%) |      26   →      25     (-3.85%) |        1.73 ms →        1.65 ms   (-4.33%) | 
+ │ │ ├ sirius::Band::solve                                             |        7.03 s  →        6.12 s   (-12.98%) |      26   →      25     (-3.85%) |      182.88 s  →      153.03 s   (-16.32%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      361.05 μs →      322.95 μs  (-10.55%) |     104   →     100     (-3.85%) |       37.55 ms →       32.30 ms  (-13.99%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      355.56 μs →      317.60 μs  (-10.68%) |     104   →     100     (-3.85%) |       36.98 ms →       31.76 ms  (-14.11%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.91 μs →        3.90 μs   (-0.36%) |     104   →     100     (-3.85%) |      406.60 μs →      389.55 μs   (-4.19%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.76 s  →        1.53 s   (-12.98%) |     104   →     100     (-3.85%) |      182.84 s  →      152.99 s   (-16.33%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.92 ms →       12.04 ms   (+1.05%) |     104   →     100     (-3.85%) |        1.24 s  →        1.20 s    (-2.83%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      638.48 ns →      699.73 ns   (+9.59%) |     624   →     600     (-3.85%) |      398.41 μs →      419.84 μs   (+5.38%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.08 ms →        1.83 ms  (-12.12%) |     104   →     100     (-3.85%) |      216.61 ms →      183.04 ms  (-15.50%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.62 μs →      353.71 μs   (-0.54%) |     104   →     100     (-3.85%) |       36.98 ms →       35.37 ms   (-4.36%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      659.68 μs →      548.98 μs  (-16.78%) |     208   →     200     (-3.85%) |      137.21 ms →      109.80 ms  (-19.98%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.74 s  →        1.51 s   (-13.14%) |     104   →     100     (-3.85%) |      180.45 s  →      150.70 s   (-16.48%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.82 ms →       66.86 ms   (-4.24%) |     906   →     961     (+6.07%) |       63.26 s  →       64.25 s    (+1.57%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.54 ms →       42.51 ms   (-4.56%) |     906   →     961     (+6.07%) |       40.36 s  →       40.86 s    (+1.24%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.64 ms →        8.44 ms   (-2.39%) |     906   →     961     (+6.07%) |        7.83 s  →        8.11 s    (+3.54%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      234.98 μs →      234.75 μs   (-0.10%) |     906   →     961     (+6.07%) |      212.89 ms →      225.59 ms   (+5.97%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.03 ms →        2.24 ms  (+10.25%) |     104   →     100     (-3.85%) |      211.10 ms →      223.78 ms   (+6.01%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.81 ms →        6.48 ms   (-4.91%) |     906   →     961     (+6.07%) |        6.17 s  →        6.23 s    (+0.86%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       89.94 μs →       84.45 μs   (-6.10%) |     906   →     961     (+6.07%) |       81.49 ms →       81.16 ms   (-0.40%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      759.95 μs →      786.60 μs   (+3.51%) |     104   →     100     (-3.85%) |       79.04 ms →       78.66 ms   (-0.47%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.81 ms →        9.20 ms   (-6.15%) |     906   →     961     (+6.07%) |        8.88 s  →        8.84 s    (-0.45%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.15 ms →        5.74 ms   (-6.64%) |     906   →     961     (+6.07%) |        5.57 s  →        5.52 s    (-0.97%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.48 ms →        1.52 ms   (+2.78%) |     906   →     961     (+6.07%) |        1.34 s  →        1.46 s    (+9.02%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.89 ms →        8.36 ms   (-5.95%) |     906   →     961     (+6.07%) |        8.05 s  →        8.03 s    (-0.24%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.53 ms →        1.37 ms  (-10.96%) |     906   →     961     (+6.07%) |        1.39 s  →        1.31 s    (-5.55%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.44 ms →        7.22 ms   (-2.97%) |    1.81 K →    1.92 K   (+6.07%) |       13.49 s  →       13.88 s    (+2.92%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.52 ms →       26.45 ms   (-7.25%) |     906   →     961     (+6.07%) |       25.83 s  →       25.42 s    (-1.62%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.11 ms →        1.95 ms   (-7.48%) |    1.71 K →    1.82 K   (+6.67%) |        3.61 s  →        3.56 s    (-1.31%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       74.62 ns →       61.26 ns  (-17.91%) |    1.71 K →    1.82 K   (+6.67%) |      127.46 μs →      111.61 μs  (-12.43%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.10 ms →        1.94 ms   (-7.53%) |    1.71 K →    1.82 K   (+6.67%) |        3.59 s  →        3.54 s    (-1.36%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       57.81 ns →       63.21 ns   (+9.34%) |    1.71 K →    1.82 K   (+6.67%) |       98.74 μs →      115.17 μs  (+16.64%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      904.12 μs →      765.58 μs  (-15.32%) |     906   →     961     (+6.07%) |      819.13 ms →      735.72 ms  (-10.18%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      829.01 μs →      752.54 μs   (-9.22%) |     906   →     961     (+6.07%) |      751.09 ms →      723.19 ms   (-3.71%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.46 ms →        5.06 ms   (-7.22%) |    3.52 K →    3.74 K   (+6.36%) |       19.21 s  →       18.96 s    (-1.32%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.71 ms →        3.44 ms   (-7.38%) |    5.12 K →    5.47 K   (+6.67%) |       19.03 s  →       18.81 s    (-1.19%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.55 ms →        5.22 ms   (-5.93%) |     906   →     961     (+6.07%) |        5.03 s  →        5.02 s    (-0.22%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.84 ms →        3.47 ms   (-9.72%) |     906   →     961     (+6.07%) |        3.48 s  →        3.33 s    (-4.24%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       57.87 ns →       53.12 ns   (-8.20%) |     906   →     961     (+6.07%) |       52.43 μs →       51.05 μs   (-2.63%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.83 ms →        3.45 ms   (-9.76%) |     906   →     961     (+6.07%) |        3.47 s  →        3.32 s    (-4.28%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       72.01 ns →       38.95 ns  (-45.92%) |     906   →     961     (+6.07%) |       65.25 μs →       37.43 μs  (-42.63%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       72.77 ms →       35.93 ms  (-50.63%) |     906   →     961     (+6.07%) |       65.93 s  →       34.53 s   (-47.63%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       10.82 ms →        9.59 ms  (-11.33%) |     885   →     935     (+5.65%) |        9.58 s  →        8.97 s    (-6.33%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       10.45 ms →        9.19 ms  (-12.12%) |     840   →     890     (+5.95%) |        8.78 s  →        8.18 s    (-6.89%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.18 ms →        4.56 ms  (-12.00%) |    1.68 K →    1.78 K   (+5.95%) |        8.71 s  →        8.12 s    (-6.76%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      645.09 μs →      623.15 μs   (-3.40%) |     840   →     890     (+5.95%) |      541.88 ms →      554.60 ms   (+2.35%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.60 ms →       36.95 ms  (-28.40%) |     209   →     338    (+61.72%) |       10.79 s  →       12.49 s   (+15.80%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.24 ms →       21.56 ms  (-37.04%) |     314   →     576    (+83.44%) |       10.75 s  →       12.42 s   (+15.49%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.51 ms →       15.17 ms  (-40.52%) |     419   →     814    (+94.27%) |       10.69 s  →       12.35 s   (+15.56%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      584.76 ns →      570.01 ns   (-2.52%) |     104   →     100     (-3.85%) |       60.82 μs →       57.00 μs   (-6.27%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.66 μs →       22.51 μs   (+3.91%) |      26   →      25     (-3.85%) |      563.14 μs →      562.67 μs   (-0.08%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      599.75 μs →      590.25 μs   (-1.58%) |      26   →      25     (-3.85%) |       15.59 ms →       14.76 ms   (-5.37%) | 
  │ │ ├ sirius::Density::generate                                       |      897.48 ms →      896.02 ms   (-0.16%) |      26   →      25     (-3.85%) |       23.33 s  →       22.40 s    (-4.00%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      527.39 ms →      524.39 ms   (-0.57%) |      26   →      25     (-3.85%) |       13.71 s  →       13.11 s    (-4.39%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.51 ms →       23.76 ms   (-3.09%) |     104   →     100     (-3.85%) |        2.55 s  →        2.38 s    (-6.81%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.53 μs →        8.87 μs   (+3.93%) |     104   →     100     (-3.85%) |      887.28 μs →      886.71 μs   (-0.07%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.97 μs →       16.15 μs   (+1.10%) |       8   →       8              |      127.77 μs →      129.17 μs   (+1.10%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.39 ms →       19.63 ms   (-3.72%) |     104   →     100     (-3.85%) |        2.12 s  →        1.96 s    (-7.42%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.23 ms →       30.11 ms   (-0.39%) |     104   →     100     (-3.85%) |        3.14 s  →        3.01 s    (-4.23%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.41 μs →        9.88 μs   (+5.00%) |     104   →     100     (-3.85%) |      978.71 μs →      988.14 μs   (+0.96%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.41 ms →        1.46 ms   (+3.34%) |     104   →     100     (-3.85%) |      146.44 ms →      145.51 ms   (-0.63%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.35 ms →       28.17 ms   (-0.62%) |     104   →     100     (-3.85%) |        2.95 s  →        2.82 s    (-4.44%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.21 ms →        4.03 ms   (-4.30%) |     104   →     100     (-3.85%) |      438.35 ms →      403.37 ms   (-7.98%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      629.37 ns →      534.06 ns  (-15.14%) |     104   →     100     (-3.85%) |       65.45 μs →       53.41 μs  (-18.41%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.74 ms →       42.81 ms   (+0.18%) |     104   →     100     (-3.85%) |        4.44 s  →        4.28 s    (-3.68%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.13%) |      26   →      25     (-3.85%) |       42.70 ms →       41.01 ms   (-3.97%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.87 ms →       88.90 ms   (+0.03%) |      26   →      25     (-3.85%) |        2.31 s  →        2.22 s    (-3.81%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.63 ms →       88.66 ms   (+0.04%) |      26   →      25     (-3.85%) |        2.30 s  →        2.22 s    (-3.81%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.72 ms →      278.38 ms   (+0.24%) |      26   →      25     (-3.85%) |        7.22 s  →        6.96 s    (-3.62%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.72 ms →      278.38 ms   (+0.24%) |      26   →      25     (-3.85%) |        7.22 s  →        6.96 s    (-3.62%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.94 ms →       24.62 ms   (-1.28%) |      26   →      25     (-3.85%) |      648.33 ms →      615.41 ms   (-5.08%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.81 ms →      228.00 ms   (+0.53%) |      26   →      25     (-3.85%) |        5.90 s  →        5.70 s    (-3.34%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.20 ms →       23.94 ms   (-1.06%) |      26   →      25     (-3.85%) |      629.16 ms →      598.54 ms   (-4.87%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.89 ms →       80.91 ms   (-1.19%) |      26   →      25     (-3.85%) |        2.13 s  →        2.02 s    (-4.99%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.89 ms →        8.74 ms  (+26.87%) |      26   →      25     (-3.85%) |      179.01 ms →      218.38 ms  (+21.99%) | 
+ │ │ ├ sirius::Density::mix                                            |      233.41 ms →      212.36 ms   (-9.02%) |      26   →      25     (-3.85%) |        6.07 s  →        5.31 s   (-12.52%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      972.82 μs →      966.06 μs   (-0.69%) |      26   →      25     (-3.85%) |       25.29 ms →       24.15 ms   (-4.51%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.84 ms →       10.33 ms  (-12.82%) |     334   →     319     (-4.49%) |        3.96 s  →        3.29 s   (-16.74%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.42 ms →        9.98 ms   (-4.23%) |     334   →     319     (-4.49%) |        3.48 s  →        3.18 s    (-8.53%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.42 ms →        9.98 ms   (-4.23%) |     334   →     319     (-4.49%) |        3.48 s  →        3.18 s    (-8.54%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.51 ms →        6.20 ms   (-4.69%) |      26   →      25     (-3.85%) |      169.25 ms →      155.11 ms   (-8.35%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.66 ms →        5.36 ms   (-5.42%) |      26   →      25     (-3.85%) |      147.22 ms →      133.89 ms   (-9.06%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.67 ms →      579.37 ms   (-0.05%) |      26   →      25     (-3.85%) |       15.07 s  →       14.48 s    (-3.90%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.29 ms →      137.23 ms   (-0.05%) |      26   →      25     (-3.85%) |        3.57 s  →        3.43 s    (-3.89%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.65 ms →       19.80 ms   (+6.17%) |      26   →      25     (-3.85%) |      484.97 ms →      495.11 ms   (+2.09%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.33 ms →       10.35 ms   (+0.21%) |      26   →      25     (-3.85%) |      268.53 ms →      258.73 ms   (-3.65%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.07 ms →       10.00 ms   (-0.61%) |      26   →      25     (-3.85%) |      261.69 ms →      250.09 ms   (-4.43%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.06 ms →       10.00 ms   (-0.61%) |      26   →      25     (-3.85%) |      261.68 ms →      250.07 ms   (-4.43%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      579.05 μs →      557.46 μs   (-3.73%) |      52   →      50     (-3.85%) |       30.11 ms →       27.87 ms   (-7.43%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.21 ms →       49.10 ms   (-0.21%) |      26   →      25     (-3.85%) |        1.28 s  →        1.23 s    (-4.05%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.85 ms →       46.74 ms   (-0.23%) |      26   →      25     (-3.85%) |        1.22 s  →        1.17 s    (-4.07%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.03 ms   (+0.36%) |      52   →      50     (-3.85%) |      157.04 ms →      151.55 ms   (-3.50%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.46 ms →        5.33 ms   (-2.42%) |      26   →      25     (-3.85%) |      141.97 ms →      133.20 ms   (-6.17%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.69 ms →        6.64 ms   (-0.79%) |      26   →      25     (-3.85%) |      173.99 ms →      165.98 ms   (-4.61%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.99 ms →       90.92 ms   (-0.08%) |      26   →      25     (-3.85%) |        2.37 s  →        2.27 s    (-3.92%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.02 ms →      293.06 ms   (+0.01%) |      26   →      25     (-3.85%) |        7.62 s  →        7.33 s    (-3.83%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      278.31 ms →      281.29 ms   (+1.07%) |      26   →      25     (-3.85%) |        7.24 s  →        7.03 s    (-2.81%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      278.31 ms →      281.29 ms   (+1.07%) |      26   →      25     (-3.85%) |        7.24 s  →        7.03 s    (-2.81%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.37 ms →       27.20 ms   (-0.63%) |      26   →      25     (-3.85%) |      711.67 ms →      680.01 ms   (-4.45%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.09 ms →      226.37 ms   (+1.47%) |      26   →      25     (-3.85%) |        5.80 s  →        5.66 s    (-2.43%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.05 ms →       23.93 ms   (-0.51%) |      26   →      25     (-3.85%) |      625.37 ms →      598.26 ms   (-4.34%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.57 ms →        5.39 ms   (-3.22%) |      26   →      25     (-3.85%) |      144.70 ms →      134.66 ms   (-6.94%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.31 ms →       10.54 ms   (+2.16%) |     182   →     175     (-3.85%) |        1.88 s  →        1.84 s    (-1.77%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.94 ms →        9.81 ms   (-1.32%) |     182   →     175     (-3.85%) |        1.81 s  →        1.72 s    (-5.11%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.94 ms →        9.81 ms   (-1.32%) |     182   →     175     (-3.85%) |        1.81 s  →        1.72 s    (-5.11%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.15 ms →       10.59 ms   (-5.04%) |      78   →      75     (-3.85%) |      869.61 ms →      794.05 ms   (-8.69%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.73 ms →       10.17 ms   (-5.26%) |      78   →      75     (-3.85%) |      836.98 ms →      762.48 ms   (-8.90%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.02 ms →        9.95 ms   (-0.66%) |      26   →      25     (-3.85%) |      260.49 ms →      248.82 ms   (-4.48%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      177.75 μs →      119.75 μs  (-32.63%) |      26   →      25     (-3.85%) |        4.62 ms →        2.99 ms  (-35.22%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      172.57 μs →      114.01 μs  (-33.94%) |      26   →      25     (-3.85%) |        4.49 ms →        2.85 ms  (-36.48%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.30 ms →        5.48 ms   (+3.49%) |       2   →       2              |       10.59 ms →       10.96 ms   (+3.49%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.73 ms →       10.25 ms   (+5.31%) |       6   →       6              |       58.39 ms →       61.50 ms   (+5.31%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.67 ms →       10.24 ms   (+5.82%) |       6   →       6              |       58.04 ms →       61.42 ms   (+5.82%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.67 ms →       10.24 ms   (+5.82%) |       6   →       6              |       58.04 ms →       61.42 ms   (+5.82%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.67 ms →       10.54 ms   (-1.22%) |       3   →       3              |       32.00 ms →       31.61 ms   (-1.22%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.50 ms →       10.52 ms   (+0.18%) |       3   →       3              |       31.51 ms →       31.57 ms   (+0.18%) | 
  ├ sirius::Periodic_function|inner                                     |        9.70 ms →        9.84 ms   (+1.45%) |       2   →       2              |       19.39 ms →       19.68 ms   (+1.45%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.62 ms →        9.76 ms   (+1.47%) |       2   →       2              |       19.23 ms →       19.51 ms   (+1.47%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.62 ms →        9.76 ms   (+1.47%) |       2   →       2              |       19.23 ms →       19.51 ms   (+1.47%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.54 ms →       10.16 ms   (-3.57%) |       1   →       1              |       10.54 ms →       10.16 ms   (-3.57%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.48 ms →       10.15 ms   (-3.10%) |       1   →       1              |       10.48 ms →       10.15 ms   (-3.10%) | 
  └ sirius::finalize                                                    |      333.02 ms →      308.07 ms   (-7.49%) |       1   →       1              |      333.02 ms →      308.07 ms   (-7.49%) | 
  ====================================================================================================================================================================================================
```
