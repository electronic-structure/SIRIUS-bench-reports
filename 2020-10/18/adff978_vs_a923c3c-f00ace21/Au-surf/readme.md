# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      281.02 s  →      230.65 s   (-17.93%) |       1   →       1              |      281.02 s  →      230.65 s   (-17.93%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.69 s    (-0.94%) |       1   →       1              |        2.72 s  →        2.69 s    (-0.94%) | 
  ├ sirius::Simulation_context::initialize                              |        4.01 s  →        4.00 s    (-0.32%) |       1   →       1              |        4.01 s  →        4.00 s    (-0.32%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       73.19 ms →       48.24 ms  (-34.08%) |       1   →       1              |       73.19 ms →       48.24 ms  (-34.08%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      119.91 ms →      104.50 ms  (-12.85%) |       1   →       1              |      119.91 ms →      104.50 ms  (-12.85%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       94.02 ms →       78.32 ms  (-16.69%) |       1   →       1              |       94.02 ms →       78.32 ms  (-16.69%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.82 ms →       26.10 ms   (+1.10%) |       1   →       1              |       25.82 ms →       26.10 ms   (+1.10%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.40 ms →       10.08 ms   (-3.08%) |       1   →       1              |       10.40 ms →       10.08 ms   (-3.08%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.39 ms →       15.99 ms   (+3.92%) |       1   →       1              |       15.39 ms →       15.99 ms   (+3.92%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.59 ms →       15.24 ms   (+4.43%) |       1   →       1              |       14.59 ms →       15.24 ms   (+4.43%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.36 ms →       15.00 ms   (+4.50%) |       1   →       1              |       14.36 ms →       15.00 ms   (+4.50%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      218.09 μs →      218.70 μs   (+0.28%) |       1   →       1              |      218.09 μs →      218.70 μs   (+0.28%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.71 μs →        2.62 μs   (-3.32%) |       1   →       1              |        2.71 μs →        2.62 μs   (-3.32%) | 
  │ └ sirius::Simulation_context::update                                |        3.77 s  →        3.80 s    (+0.78%) |       1   →       1              |        3.77 s  →        3.80 s    (+0.78%) | 
  │   ├ sirius::Unit_cell::update                                       |       13.01 ms →       12.62 ms   (-2.99%) |       1   →       1              |       13.01 ms →       12.62 ms   (-2.99%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.19 ms →        7.94 ms   (-3.07%) |       1   →       1              |        8.19 ms →        7.94 ms   (-3.07%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.79 ms →        4.65 ms   (-2.92%) |       1   →       1              |        4.79 ms →        4.65 ms   (-2.92%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.11 ms →        4.10 ms   (-0.13%) |       1   →       1              |        4.11 ms →        4.10 ms   (-0.13%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.90 ms   (-0.10%) |       1   →       1              |        3.90 ms →        3.90 ms   (-0.10%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      204.62 μs →      202.95 μs   (-0.82%) |       1   →       1              |      204.62 μs →      202.95 μs   (-0.82%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.18 μs →        1.30 μs  (+10.78%) |       1   →       1              |        1.18 μs →        1.30 μs  (+10.78%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       31.69 ms →       33.42 ms   (+5.44%) |       2   →       2              |       63.39 ms →       66.84 ms   (+5.44%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.11 ms →        1.14 ms   (+3.03%) |       2   →       2              |        2.21 ms →        2.28 ms   (+3.03%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      952.54 μs →      991.69 μs   (+4.11%) |       1   →       1              |      952.54 μs →      991.69 μs   (+4.11%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.09 ms →        5.11 ms   (+0.28%) |       2   →       2              |       10.19 ms →       10.22 ms   (+0.28%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        4.75 ms →        4.94 ms   (+4.16%) |       2   →       2              |        9.49 ms →        9.89 ms   (+4.16%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.61 ms →       15.11 ms   (-3.20%) |       4   →       4              |       62.45 ms →       60.45 ms   (-3.20%) | 
  │   ├ sddk::Gvec::init                                                |      162.35 ms →      158.78 ms   (-2.20%) |       2   →       2              |      324.71 ms →      317.55 ms   (-2.20%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.46 ms →      126.13 ms   (-1.81%) |       2   →       2              |      256.92 ms →      252.27 ms   (-1.81%) | 
  │   ├ sddk::Gvec_shells                                               |      127.21 ms →      117.94 ms   (-7.29%) |       1   →       1              |      127.21 ms →      117.94 ms   (-7.29%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.03 ms   (+0.72%) |       1   →       1              |        1.03 ms →        1.03 ms   (+0.72%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |        2.05 s  →        2.08 s    (+1.19%) |       1   →       1              |        2.05 s  →        2.08 s    (+1.19%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       27.45 ms →       26.73 ms   (-2.63%) |       1   →       1              |       27.45 ms →       26.73 ms   (-2.63%) | 
+ │ ├ sirius::K_point::K_point                                          |        6.26 μs →        1.82 μs  (-70.92%) |       2   →       2              |       12.52 μs →        3.64 μs  (-70.92%) | 
  │ └ sirius::K_point_set::initialize                                   |       27.38 ms →       26.69 ms   (-2.51%) |       1   →       1              |       27.38 ms →       26.69 ms   (-2.51%) | 
  │   └ sirius::K_point::initialize                                     |       27.32 ms →       26.64 ms   (-2.50%) |       1   →       1              |       27.32 ms →       26.64 ms   (-2.50%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.80 ms →       19.35 ms   (-2.24%) |       1   →       1              |       19.80 ms →       19.35 ms   (-2.24%) | 
  │     │ └ sddk::Gvec::init                                            |        5.35 ms →        4.95 ms   (-7.33%) |       1   →       1              |        5.35 ms →        4.95 ms   (-7.33%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |       11.05 μs →       12.24 μs  (+10.70%) |       1   →       1              |       11.05 μs →       12.24 μs  (+10.70%) | 
  │     └ sirius::K_point::update                                       |        5.08 ms →        4.96 ms   (-2.30%) |       1   →       1              |        5.08 ms →        4.96 ms   (-2.30%) | 
  │       └ sirius::Beta_projectors                                     |        2.54 ms →        2.55 ms   (+0.42%) |       1   →       1              |        2.54 ms →        2.55 ms   (+0.42%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        1.35 ms →        1.35 ms   (-0.70%) |       1   →       1              |        1.35 ms →        1.35 ms   (-0.70%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.55 ms →        1.48 ms   (-4.51%) |       2   →       2              |        3.11 ms →        2.97 ms   (-4.51%) | 
  ├ sirius::Potential                                                   |       84.97 ms →       86.63 ms   (+1.95%) |       1   →       1              |       84.97 ms →       86.63 ms   (+1.95%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.71 ms →        2.50 ms   (-7.53%) |       6   →       6              |       16.23 ms →       15.01 ms   (-7.53%) | 
  │ └ sirius::Potential::update                                         |       68.29 ms →       71.17 ms   (+4.22%) |       1   →       1              |       68.29 ms →       71.17 ms   (+4.22%) | 
  │   └ sirius::Potential::generate_local_potential                     |       68.11 ms →       71.00 ms   (+4.24%) |       1   →       1              |       68.11 ms →       71.00 ms   (+4.24%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       50.99 ms →       58.47 ms  (+14.68%) |       1   →       1              |       50.99 ms →       58.47 ms  (+14.68%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.41 ms →        3.74 ms  (-49.49%) |       1   →       1              |        7.41 ms →        3.74 ms  (-49.49%) | 
  ├ sirius::Density                                                     |       75.16 ms →       76.13 ms   (+1.30%) |       1   →       1              |       75.16 ms →       76.13 ms   (+1.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.89 ms →        4.86 ms   (-0.57%) |       2   →       2              |        9.77 ms →        9.72 ms   (-0.57%) | 
  │ └ sirius::Density::update                                           |       64.98 ms →       66.01 ms   (+1.59%) |       1   →       1              |       64.98 ms →       66.01 ms   (+1.59%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       64.81 ms →       65.84 ms   (+1.59%) |       1   →       1              |       64.81 ms →       65.84 ms   (+1.59%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.14 ms →        3.09 ms   (-1.57%) |       1   →       1              |        3.14 ms →        3.09 ms   (-1.57%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       51.07 ms →       59.01 ms  (+15.56%) |       1   →       1              |       51.07 ms →       59.01 ms  (+15.56%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.35 ms →        2.42 ms  (-74.09%) |       1   →       1              |        9.35 ms →        2.42 ms  (-74.09%) | 
  ├ sirius::Density::initial_density                                    |       79.68 ms →       79.24 ms   (-0.55%) |       1   →       1              |       79.68 ms →       79.24 ms   (-0.55%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       50.71 ms →       58.58 ms  (+15.51%) |       1   →       1              |       50.71 ms →       58.58 ms  (+15.51%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.14 ms →        2.39 ms  (-61.17%) |       2   →       2              |       12.29 ms →        4.77 ms  (-61.17%) | 
+ │ └ sirius::Periodic_function::integrate                              |        4.86 ms →        4.07 ms  (-16.27%) |       1   →       1              |        4.86 ms →        4.07 ms  (-16.27%) | 
  ├ sirius::Potential::generate                                         |      158.70 ms →      160.31 ms   (+1.02%) |       1   →       1              |      158.70 ms →      160.31 ms   (+1.02%) | 
  │ ├ sirius::Potential::poisson                                        |       63.60 ms →       64.71 ms   (+1.75%) |       1   →       1              |       63.60 ms →       64.71 ms   (+1.75%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.63 ms →        2.33 ms  (-75.79%) |       1   →       1              |        9.63 ms →        2.33 ms  (-75.79%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.11 ms →        4.35 ms   (+5.71%) |       1   →       1              |        4.11 ms →        4.35 ms   (+5.71%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.06 ms →        4.04 ms   (-0.49%) |       1   →       1              |        4.06 ms →        4.04 ms   (-0.49%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.06 ms →        4.04 ms   (-0.49%) |       1   →       1              |        4.06 ms →        4.04 ms   (-0.49%) | 
  │ ├ sirius::Periodic_function::add                                    |      271.21 μs →      281.14 μs   (+3.66%) |       2   →       2              |      542.42 μs →      562.29 μs   (+3.66%) | 
  │ ├ sirius::Potential::xc                                             |       22.15 ms →       21.79 ms   (-1.59%) |       1   →       1              |       22.15 ms →       21.79 ms   (-1.59%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       21.07 ms →       20.71 ms   (-1.67%) |       1   →       1              |       21.07 ms →       20.71 ms   (-1.67%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.56 ms →        1.55 ms   (-0.75%) |       2   →       2              |        3.12 ms →        3.09 ms   (-0.75%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        2.53 ms →        2.62 ms   (+3.41%) |       1   →       1              |        2.53 ms →        2.62 ms   (+3.41%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.22 ms →        2.22 ms   (+0.16%) |       1   →       1              |        2.22 ms →        2.22 ms   (+0.16%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       69.61 ms →       70.45 ms   (+1.20%) |       1   →       1              |       69.61 ms →       70.45 ms   (+1.20%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      282.00 ns →      138.00 ns  (-51.06%) |       1   →       1              |      282.00 ns →      138.00 ns  (-51.06%) | 
  ├ sirius::Hamiltonian0                                                |       13.96 ms →       14.49 ms   (+3.76%) |       1   →       1              |       13.96 ms →       14.49 ms   (+3.76%) | 
  │ ├ sirius::Local_operator                                            |       12.52 ms →       13.00 ms   (+3.87%) |       1   →       1              |       12.52 ms →       13.00 ms   (+3.87%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.24 ms →        7.17 ms   (-0.92%) |       1   →       1              |        7.24 ms →        7.17 ms   (-0.92%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.81 ms →        4.37 ms  (+14.65%) |       1   →       1              |        3.81 ms →        4.37 ms  (+14.65%) | 
  │ ├ sirius::Non_local_operator                                        |       89.37 μs →       88.84 μs   (-0.59%) |       2   →       2              |      178.74 μs →      177.69 μs   (-0.59%) | 
  │ ├ sirius::D_operator::initialize                                    |      718.63 μs →      743.01 μs   (+3.39%) |       1   →       1              |      718.63 μs →      743.01 μs   (+3.39%) | 
  │ └ sirius::Q_operator::initialize                                    |      367.59 μs →      383.41 μs   (+4.30%) |       1   →       1              |      367.59 μs →      383.41 μs   (+4.30%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.67 s  →        2.69 s    (+1.03%) |       1   →       1              |        2.67 s  →        2.69 s    (+1.03%) | 
  │ ├ sirius::Hamiltonian_k                                             |       15.45 ms →       15.45 ms   (+0.01%) |       1   →       1              |       15.45 ms →       15.45 ms   (+0.01%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      263.92 μs →      251.24 μs   (-4.80%) |       1   →       1              |      263.92 μs →      251.24 μs   (-4.80%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       15.18 ms →       15.19 ms   (+0.10%) |       1   →       1              |       15.18 ms →       15.19 ms   (+0.10%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.65 s  →        2.68 s    (+1.04%) |       1   →       1              |        2.65 s  →        2.68 s    (+1.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       91.11 ms →       94.16 ms   (+3.34%) |       4   →       4              |      364.45 ms →      376.63 ms   (+3.34%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.80 ms →       25.62 ms   (-0.68%) |       1   →       1              |       25.80 ms →       25.62 ms   (-0.68%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.83 ms →       14.78 ms   (-0.30%) |       1   →       1              |       14.83 ms →       14.78 ms   (-0.30%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.41 s  →        1.41 s    (-0.09%) |       1   →       1              |        1.41 s  →        1.41 s    (-0.09%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      984.08 ms →      986.33 ms   (+0.23%) |       1   →       1              |      984.08 ms →      986.33 ms   (+0.23%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      311.16 ms →      312.98 ms   (+0.59%) |       1   →       1              |      311.16 ms →      312.98 ms   (+0.59%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      176.08 ms →      181.54 ms   (+3.10%) |       1   →       1              |      176.08 ms →      181.54 ms   (+3.10%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      176.07 ms →      181.54 ms   (+3.11%) |       1   →       1              |      176.07 ms →      181.54 ms   (+3.11%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      116.41 ms →      112.90 ms   (-3.01%) |       1   →       1              |      116.41 ms →      112.90 ms   (-3.01%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      178.02 ms →      180.00 ms   (+1.11%) |       1   →       1              |      178.02 ms →      180.00 ms   (+1.11%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      178.01 ms →      180.00 ms   (+1.11%) |       1   →       1              |      178.01 ms →      180.00 ms   (+1.11%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      164.16 ms →      162.66 ms   (-0.91%) |       1   →       1              |      164.16 ms →      162.66 ms   (-0.91%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      113.66 ms →      112.31 ms   (-1.18%) |       1   →       1              |      113.66 ms →      112.31 ms   (-1.18%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        5.97 ms →        5.96 ms   (-0.24%) |       1   →       1              |        5.97 ms →        5.96 ms   (-0.24%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      172.42 ms →      171.70 ms   (-0.42%) |       1   →       1              |      172.42 ms →      171.70 ms   (-0.42%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       23.82 ms →       24.76 ms   (+3.96%) |       1   →       1              |       23.82 ms →       24.76 ms   (+3.96%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      123.93 ms →      122.52 ms   (-1.14%) |       2   →       2              |      247.86 ms →      245.04 ms   (-1.14%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      190.62 ms →      198.48 ms   (+4.12%) |       2   →       2              |      381.24 ms →      396.95 ms   (+4.12%) | 
  │ │ │ └ sddk::wf_inner                                                |      190.52 ms →      198.37 ms   (+4.12%) |       2   →       2              |      381.03 ms →      396.75 ms   (+4.12%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       53.00 ns →       39.50 ns  (-25.47%) |       2   →       2              |      106.00 ns →       79.00 ns  (-25.47%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      188.89 ms →      196.53 ms   (+4.04%) |       2   →       2              |      377.79 ms →      393.07 ms   (+4.04%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       20.50 ns →       20.50 ns            |       2   →       2              |       41.00 ns →       41.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      115.74 ms →      116.27 ms   (+0.46%) |       1   →       1              |      115.74 ms →      116.27 ms   (+0.46%) | 
  │ │ └ sddk::wf_trans                                                  |       35.81 ms →       34.04 ms   (-4.96%) |       1   →       1              |       35.81 ms →       34.04 ms   (-4.96%) | 
  │ │   └ sddk::wf_trans|pw                                             |       34.50 ms →       34.02 ms   (-1.40%) |       1   →       1              |       34.50 ms →       34.02 ms   (-1.40%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      440.00 ns →      514.00 ns  (+16.82%) |       1   →       1              |      440.00 ns →      514.00 ns  (+16.82%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      270.11 s  →      219.65 s   (-18.68%) |       1   →       1              |      270.11 s  →      219.65 s   (-18.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.13 ms →        2.13 ms   (+0.08%) |      19   →      19              |       40.45 ms →       40.48 ms   (+0.08%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.17 s  →        3.43 s    (+7.91%) |      85   →      64    (-24.71%) |      269.86 s  →      219.27 s   (-18.75%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        8.34 ms →        8.34 ms   (+0.01%) |      85   →      64    (-24.71%) |      709.12 ms →      533.98 ms  (-24.70%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        7.02 ms →        7.00 ms   (-0.24%) |      85   →      64    (-24.71%) |      596.34 ms →      447.92 ms  (-24.89%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.49 ms →        1.52 ms   (+2.14%) |      85   →      64    (-24.71%) |      126.68 ms →       97.42 ms  (-23.09%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.05 ms →        4.00 ms   (-1.12%) |      85   →      64    (-24.71%) |      343.90 ms →      256.03 ms  (-25.55%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       90.87 μs →       90.57 μs   (-0.33%) |     170   →     128    (-24.71%) |       15.45 ms →       11.59 ms  (-24.95%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      591.62 μs →      602.85 μs   (+1.90%) |      85   →      64    (-24.71%) |       50.29 ms →       38.58 ms  (-23.28%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |      367.01 μs →      368.19 μs   (+0.32%) |      85   →      64    (-24.71%) |       31.20 ms →       23.56 ms  (-24.46%) | 
- │ │ ├ sirius::Band::solve                                             |        2.49 s  →        2.74 s   (+10.24%) |      85   →      64    (-24.71%) |      211.38 s  →      175.45 s   (-17.00%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      224.90 μs →      208.31 μs   (-7.38%) |      85   →      64    (-24.71%) |       19.12 ms →       13.33 ms  (-30.26%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      217.32 μs →      200.83 μs   (-7.59%) |      85   →      64    (-24.71%) |       18.47 ms →       12.85 ms  (-30.42%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.34 μs →        4.98 μs   (-6.76%) |      85   →      64    (-24.71%) |      453.69 μs →      318.50 μs  (-29.80%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.45 s  →        2.72 s   (+11.06%) |      85   →      64    (-24.71%) |      208.18 s  →      174.09 s   (-16.38%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       41.97 ms →       46.06 ms   (+9.74%) |      85   →      64    (-24.71%) |        3.57 s  →        2.95 s   (-17.37%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        2.09 ms →        2.77 ms  (+32.74%) |     510   →     384    (-24.71%) |        1.06 s  →        1.06 s    (-0.05%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        3.70 ms →        3.72 ms   (+0.65%) |      85   →      64    (-24.71%) |      314.32 ms →      238.21 ms  (-24.21%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |        1.50 ms →        1.50 ms   (+0.07%) |      85   →      64    (-24.71%) |      127.39 ms →       95.98 ms  (-24.66%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        1.94 ms →        1.96 ms   (+1.06%) |      85   →      64    (-24.71%) |      164.69 ms →      125.31 ms  (-23.91%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.38 s  →        2.65 s   (+11.20%) |      85   →      64    (-24.71%) |      202.41 s  →      169.47 s   (-16.27%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      246.33 ms →      233.11 ms   (-5.37%) |     482   →     446     (-7.47%) |      118.73 s  →      103.97 s   (-12.43%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      136.32 ms →      129.27 ms   (-5.17%) |     482   →     446     (-7.47%) |       65.71 s  →       57.65 s   (-12.26%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       24.34 ms →       23.31 ms   (-4.25%) |     482   →     446     (-7.47%) |       11.73 s  →       10.39 s   (-11.40%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      137.19 μs →      149.68 μs   (+9.10%) |     482   →     446     (-7.47%) |       66.12 ms →       66.76 ms   (+0.96%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      764.88 μs →        1.03 ms  (+34.27%) |      85   →      64    (-24.71%) |       65.01 ms →       65.73 ms   (+1.10%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       20.17 ms →       19.35 ms   (-4.06%) |     482   →     446     (-7.47%) |        9.72 s  →        8.63 s   (-11.22%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      269.63 μs →      299.36 μs  (+11.03%) |     482   →     446     (-7.47%) |      129.96 ms →      133.51 ms   (+2.73%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        1.51 ms →        2.07 ms  (+36.63%) |      85   →      64    (-24.71%) |      128.48 ms →      132.17 ms   (+2.88%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       31.16 ms →       29.71 ms   (-4.66%) |     482   →     446     (-7.47%) |       15.02 s  →       13.25 s   (-11.78%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       19.65 ms →       18.85 ms   (-4.09%) |     482   →     446     (-7.47%) |        9.47 s  →        8.41 s   (-11.25%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        4.82 ms →        4.81 ms   (-0.25%) |     482   →     446     (-7.47%) |        2.32 s  →        2.15 s    (-7.70%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       40.05 ms →       37.78 ms   (-5.66%) |     482   →     446     (-7.47%) |       19.30 s  →       16.85 s   (-12.71%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        4.50 ms →        4.46 ms   (-0.92%) |     482   →     446     (-7.47%) |        2.17 s  →        1.99 s    (-8.32%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       32.55 ms →       30.61 ms   (-5.97%) |     964   →     892     (-7.47%) |       31.38 s  →       27.31 s   (-12.99%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       52.90 ms →       51.54 ms   (-2.57%) |     482   →     446     (-7.47%) |       25.50 s  →       22.99 s    (-9.85%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       12.21 ms →       11.71 ms   (-4.10%) |     879   →     828     (-5.80%) |       10.73 s  →        9.70 s    (-9.66%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       71.82 ns →       66.34 ns   (-7.63%) |     879   →     828     (-5.80%) |       63.13 μs →       54.93 μs  (-12.99%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.23 ms →        8.71 ms   (-5.64%) |     879   →     828     (-5.80%) |        8.12 s  →        7.21 s   (-11.11%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       80.15 ns →       44.03 ns  (-45.06%) |     879   →     828     (-5.80%) |       70.45 μs →       36.46 μs  (-48.25%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        2.65 ms →        2.44 ms   (-7.79%) |     482   →     446     (-7.47%) |        1.28 s  →        1.09 s   (-14.68%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       14.08 ms →       13.03 ms   (-7.47%) |     482   →     446     (-7.47%) |        6.79 s  →        5.81 s   (-14.38%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       16.86 ms →       16.71 ms   (-0.88%) |     397   →     382     (-3.78%) |        6.69 s  →        6.38 s    (-4.63%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.59 ms →        5.54 ms   (-0.83%) |    1.19 K →    1.15 K   (-3.78%) |        6.66 s  →        6.35 s    (-4.58%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       19.49 ms →       18.30 ms   (-6.11%) |     482   →     446     (-7.47%) |        9.39 s  →        8.16 s   (-13.12%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |       18.19 ms →       17.21 ms   (-5.38%) |     482   →     446     (-7.47%) |        8.77 s  →        7.68 s   (-12.44%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       55.60 ns →      121.84 ns (+119.16%) |     482   →     446     (-7.47%) |       26.80 μs →       54.34 μs (+102.79%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       15.25 ms →       14.26 ms   (-6.48%) |     482   →     446     (-7.47%) |        7.35 s  →        6.36 s   (-13.46%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       80.06 ns →       20.80 ns  (-74.01%) |     482   →     446     (-7.47%) |       38.59 μs →        9.28 μs  (-75.96%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       64.26 ms →       40.28 ms  (-37.31%) |     482   →     446     (-7.47%) |       30.97 s  →       17.97 s   (-41.99%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       18.50 ms →       15.80 ms  (-14.61%) |     477   →     437     (-8.39%) |        8.83 s  →        6.90 s   (-21.77%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       19.11 ms →       15.92 ms  (-16.66%) |     411   →     383     (-6.81%) |        7.85 s  →        6.10 s   (-22.34%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.61 ms →        7.37 ms  (-14.48%) |     822   →     766     (-6.81%) |        7.08 s  →        5.64 s   (-20.30%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.43 ms  (-10.28%) |     411   →     383     (-6.81%) |      653.19 ms →      546.14 ms  (-16.39%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       66.92 ms →       48.83 ms  (-27.04%) |     134   →     194    (+44.78%) |        8.97 s  →        9.47 s    (+5.63%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |       48.36 ms →       28.31 ms  (-41.46%) |     183   →     324    (+77.05%) |        8.85 s  →        9.17 s    (+3.64%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |       37.54 ms →       19.99 ms  (-46.76%) |     232   →     454    (+95.69%) |        8.71 s  →        9.07 s    (+4.19%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      546.07 ns →      704.91 ns  (+29.09%) |      85   →      64    (-24.71%) |       46.42 μs →       45.11 μs   (-2.81%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       37.78 μs →       33.15 μs  (-12.26%) |      85   →      64    (-24.71%) |        3.21 ms →        2.12 ms  (-33.94%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.24 ms →        3.39 ms   (+4.67%) |      85   →      64    (-24.71%) |      275.05 ms →      216.77 ms  (-21.19%) | 
+ │ │ ├ sirius::Density::generate                                       |      401.20 ms →      400.65 ms   (-0.14%) |      85   →      64    (-24.71%) |       34.10 s  →       25.64 s   (-24.81%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      393.79 ms →      393.25 ms   (-0.14%) |      85   →      64    (-24.71%) |       33.47 s  →       25.17 s   (-24.81%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.12 ms →       68.39 ms   (-1.05%) |      85   →      64    (-24.71%) |        5.87 s  →        4.38 s   (-25.50%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        7.88 μs →        8.72 μs  (+10.70%) |      85   →      64    (-24.71%) |      669.47 μs →      558.00 μs  (-16.65%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       20.81 μs →       22.85 μs   (+9.79%) |       2   →       2              |       41.62 μs →       45.70 μs   (+9.79%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.89 ms →       57.20 ms   (-1.20%) |      85   →      64    (-24.71%) |        4.92 s  →        3.66 s   (-25.61%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      113.19 ms →      113.41 ms   (+0.19%) |      85   →      64    (-24.71%) |        9.62 s  →        7.26 s   (-24.56%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.57 μs →        9.53 μs   (-0.48%) |      85   →      64    (-24.71%) |      813.70 μs →      609.73 μs  (-25.07%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        4.52 ms →        4.53 ms   (+0.23%) |      85   →      64    (-24.71%) |      384.27 ms →      289.99 ms  (-24.53%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |      107.64 ms →      107.84 ms   (+0.19%) |      85   →      64    (-24.71%) |        9.15 s  →        6.90 s   (-24.56%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |       12.82 ms →       13.72 ms   (+7.04%) |      85   →      64    (-24.71%) |        1.09 s  →      878.08 ms  (-19.40%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      629.02 ns →      622.37 ns   (-1.06%) |      85   →      64    (-24.71%) |       53.47 μs →       39.83 μs  (-25.50%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.84 ms →      104.60 ms   (-0.24%) |      85   →      64    (-24.71%) |        8.91 s  →        6.69 s   (-24.88%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.41 ms   (-0.28%) |      85   →      64    (-24.71%) |      205.38 ms →      154.21 ms  (-24.92%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       66.26 ms →       66.23 ms   (-0.04%) |      85   →      64    (-24.71%) |        5.63 s  →        4.24 s   (-24.74%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       66.06 ms →       66.06 ms   (-0.01%) |      85   →      64    (-24.71%) |        5.62 s  →        4.23 s   (-24.71%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      237.82 ns →      474.22 ns  (+99.40%) |      85   →      64    (-24.71%) |       20.21 μs →       30.35 μs  (+50.14%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        4.48 ms →        4.45 ms   (-0.46%) |      85   →      64    (-24.71%) |      380.38 ms →      285.10 ms  (-25.05%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.93 ms →        2.95 ms   (+0.74%) |      85   →      64    (-24.71%) |      248.98 ms →      188.85 ms  (-24.15%) | 
+ │ │ ├ sirius::Density::mix                                            |       77.66 ms →       74.26 ms   (-4.38%) |      85   →      64    (-24.71%) |        6.60 s  →        4.75 s   (-28.00%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      232.77 μs →      199.19 μs  (-14.42%) |      85   →      64    (-24.71%) |       19.79 ms →       12.75 ms  (-35.57%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |        4.43 ms →        4.26 ms   (-3.73%) |    1.22 K →     904    (-25.84%) |        5.40 s  →        3.85 s   (-28.61%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.30 ms →        4.13 ms   (-3.83%) |    1.22 K →     904    (-25.84%) |        5.24 s  →        3.74 s   (-28.68%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.30 ms →        4.13 ms   (-3.83%) |    1.22 K →     904    (-25.84%) |        5.24 s  →        3.74 s   (-28.68%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        2.65 ms →        2.75 ms   (+3.72%) |      85   →      64    (-24.71%) |      225.02 ms →      175.73 ms  (-21.91%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.49 ms →        2.59 ms   (+3.92%) |      85   →      64    (-24.71%) |      211.64 ms →      165.60 ms  (-21.75%) | 
+ │ │ ├ sirius::Potential::generate                                     |      148.94 ms →      150.05 ms   (+0.75%) |      85   →      64    (-24.71%) |       12.66 s  →        9.60 s   (-24.14%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       63.80 ms →       64.76 ms   (+1.50%) |      85   →      64    (-24.71%) |        5.42 s  →        4.14 s   (-23.57%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.40 ms →        2.44 ms  (-74.03%) |      85   →      64    (-24.71%) |      798.88 ms →      156.23 ms  (-80.44%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.20 ms →        4.20 ms   (-0.04%) |      85   →      64    (-24.71%) |      357.35 ms →      268.96 ms  (-24.73%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms →        4.08 ms   (-0.00%) |      85   →      64    (-24.71%) |      346.99 ms →      261.25 ms  (-24.71%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.08 ms →        4.08 ms   (-0.00%) |      85   →      64    (-24.71%) |      346.94 ms →      261.22 ms  (-24.71%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      267.22 μs →      263.01 μs   (-1.58%) |     170   →     128    (-24.71%) |       45.43 ms →       33.66 ms  (-25.89%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       17.00 ms →       17.09 ms   (+0.55%) |      85   →      64    (-24.71%) |        1.45 s  →        1.09 s   (-24.29%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       15.98 ms →       16.06 ms   (+0.48%) |      85   →      64    (-24.71%) |        1.36 s  →        1.03 s   (-24.34%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |      515.62 μs →      526.53 μs   (+2.12%) |     170   →     128    (-24.71%) |       87.66 ms →       67.40 ms  (-23.11%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        2.60 ms →        2.56 ms   (-1.32%) |      85   →      64    (-24.71%) |      220.84 ms →      164.08 ms  (-25.70%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        2.24 ms →        2.25 ms   (+0.47%) |      85   →      64    (-24.71%) |      190.38 ms →      144.02 ms  (-24.35%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       64.82 ms →       64.87 ms   (+0.08%) |      85   →      64    (-24.71%) |        5.51 s  →        4.15 s   (-24.65%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      288.08 ns →      153.55 ns  (-46.70%) |      85   →      64    (-24.71%) |       24.49 μs →        9.83 μs  (-59.87%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      232.60 ns →      369.36 ns  (+58.80%) |      85   →      64    (-24.71%) |       19.77 μs →       23.64 μs  (+19.56%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.26 ms →        2.28 ms   (+0.77%) |      85   →      64    (-24.71%) |      192.36 ms →      145.95 ms  (-24.12%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.06 ms →        4.06 ms   (-0.03%) |     595   →     448    (-24.71%) |        2.42 s  →        1.82 s   (-24.73%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.92 ms →        3.92 ms   (-0.02%) |     595   →     448    (-24.71%) |        2.33 s  →        1.75 s   (-24.72%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.92 ms →        3.91 ms   (-0.03%) |     595   →     448    (-24.71%) |        2.33 s  →        1.75 s   (-24.73%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.42 ms →        4.19 ms   (-5.10%) |     255   →     192    (-24.71%) |        1.13 s  →      805.00 ms  (-28.54%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.23 ms →        4.06 ms   (-4.07%) |     255   →     192    (-24.71%) |        1.08 s  →      778.98 ms  (-27.77%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.04 ms →        4.01 ms   (-0.74%) |      85   →      64    (-24.71%) |      343.35 ms →      256.62 ms  (-25.26%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      115.47 μs →      117.55 μs   (+1.80%) |      85   →      64    (-24.71%) |        9.81 ms →        7.52 ms  (-23.35%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      112.12 μs →      114.15 μs   (+1.82%) |      85   →      64    (-24.71%) |        9.53 ms →        7.31 ms  (-23.34%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.87 ms →        6.27 ms   (-8.72%) |       2   →       2              |       13.75 ms →       12.55 ms   (-8.72%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.06 ms →        3.99 ms   (-1.87%) |       6   →       6              |       24.37 ms →       23.91 ms   (-1.87%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.90 ms →        3.89 ms   (-0.18%) |       6   →       6              |       23.37 ms →       23.33 ms   (-0.18%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.89 ms →        3.89 ms   (-0.18%) |       6   →       6              |       23.37 ms →       23.32 ms   (-0.18%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.25 ms →        4.06 ms   (-4.30%) |       3   →       3              |       12.74 ms →       12.19 ms   (-4.30%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.20 ms →        4.04 ms   (-3.77%) |       3   →       3              |       12.60 ms →       12.12 ms   (-3.77%) | 
  ├ sirius::Periodic_function|inner                                     |        4.20 ms →        3.96 ms   (-5.65%) |       2   →       2              |        8.40 ms →        7.93 ms   (-5.65%) | 
  │ └ sirius::Periodic_function|inner_local                             |        3.96 ms →        3.92 ms   (-1.03%) |       2   →       2              |        7.93 ms →        7.85 ms   (-1.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.96 ms →        3.92 ms   (-1.03%) |       2   →       2              |        7.93 ms →        7.85 ms   (-1.03%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.19 ms →        4.13 ms   (-1.33%) |       1   →       1              |        4.19 ms →        4.13 ms   (-1.33%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.18 ms →        4.12 ms   (-1.28%) |       1   →       1              |        4.18 ms →        4.12 ms   (-1.28%) | 
- └ sirius::finalize                                                    |      280.64 ms →      323.52 ms  (+15.28%) |       1   →       1              |      280.64 ms →      323.52 ms  (+15.28%) | 
  ====================================================================================================================================================================================================
```
