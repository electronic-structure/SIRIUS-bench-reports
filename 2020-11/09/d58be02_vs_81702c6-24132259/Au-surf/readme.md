# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs d58be0235bf025c49e07930fbe8483989a6b739c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      113.86 s  →      132.65 s   (+16.50%) |       1   →       1              |      113.86 s  →      132.65 s   (+16.50%) | 
  ├ sirius::initialize                                                  |        2.99 s  →        2.70 s    (-9.90%) |       1   →       1              |        2.99 s  →        2.70 s    (-9.90%) | 
  ├ sirius::Simulation_context::initialize                              |        2.04 s  →        2.05 s    (+0.25%) |       1   →       1              |        2.04 s  →        2.05 s    (+0.25%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       36.57 ms →       16.07 ms  (-56.07%) |       1   →       1              |       36.57 ms →       16.07 ms  (-56.07%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       66.87 ms →       72.84 ms   (+8.93%) |       1   →       1              |       66.87 ms →       72.84 ms   (+8.93%) | 
- │ │ ├ sirius::Atom_type::init                                         |       41.24 ms →       46.74 ms  (+13.34%) |       1   →       1              |       41.24 ms →       46.74 ms  (+13.34%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.57 ms →       26.04 ms   (+1.82%) |       1   →       1              |       25.57 ms →       26.04 ms   (+1.82%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.70 ms →       10.25 ms   (-4.25%) |       1   →       1              |       10.70 ms →       10.25 ms   (-4.25%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.84 ms →       15.76 ms   (+6.21%) |       1   →       1              |       14.84 ms →       15.76 ms   (+6.21%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.54 ms →       15.46 ms   (+6.32%) |       1   →       1              |       14.54 ms →       15.46 ms   (+6.32%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.32 ms →       15.23 ms   (+6.34%) |       1   →       1              |       14.32 ms →       15.23 ms   (+6.34%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      206.98 μs →      219.98 μs   (+6.28%) |       1   →       1              |      206.98 μs →      219.98 μs   (+6.28%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.55 μs →        2.59 μs   (+1.49%) |       1   →       1              |        2.55 μs →        2.59 μs   (+1.49%) | 
  │ └ sirius::Simulation_context::update                                |        1.88 s  →        1.90 s    (+0.79%) |       1   →       1              |        1.88 s  →        1.90 s    (+0.79%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.33 ms →       12.65 ms   (+2.57%) |       1   →       1              |       12.33 ms →       12.65 ms   (+2.57%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.85 ms →        8.15 ms   (+3.78%) |       1   →       1              |        7.85 ms →        8.15 ms   (+3.78%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.46 ms →        4.48 ms   (+0.47%) |       1   →       1              |        4.46 ms →        4.48 ms   (+0.47%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.16 ms →        4.19 ms   (+0.52%) |       1   →       1              |        4.16 ms →        4.19 ms   (+0.52%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.96 ms →        3.97 ms   (+0.28%) |       1   →       1              |        3.96 ms →        3.97 ms   (+0.28%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      203.81 μs →      215.25 μs   (+5.61%) |       1   →       1              |      203.81 μs →      215.25 μs   (+5.61%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.38 μs →        1.20 μs  (-13.16%) |       1   →       1              |        1.38 μs →        1.20 μs  (-13.16%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       15.17 ms →       17.11 ms  (+12.75%) |       2   →       2              |       30.34 ms →       34.21 ms  (+12.75%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (-0.41%) |       2   →       2              |        2.20 ms →        2.19 ms   (-0.41%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      954.28 μs →      968.93 μs   (+1.54%) |       1   →       1              |      954.28 μs →      968.93 μs   (+1.54%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.13 ms →        5.24 ms   (+2.29%) |       2   →       2              |       10.25 ms →       10.49 ms   (+2.29%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.68 ms   (+1.04%) |       2   →       2              |        7.28 ms →        7.36 ms   (+1.04%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.69 ms →       15.95 ms   (+1.66%) |       4   →       4              |       62.77 ms →       63.81 ms   (+1.66%) | 
  │   ├ sddk::Gvec::init                                                |      157.40 ms →      160.50 ms   (+1.97%) |       2   →       2              |      314.79 ms →      321.00 ms   (+1.97%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      124.98 ms →      128.15 ms   (+2.53%) |       2   →       2              |      249.97 ms →      256.29 ms   (+2.53%) | 
  │   ├ sddk::Gvec_shells                                               |      124.20 ms →      126.78 ms   (+2.08%) |       1   →       1              |      124.20 ms →      126.78 ms   (+2.08%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.03 ms   (-0.07%) |       1   →       1              |        1.03 ms →        1.03 ms   (-0.07%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      227.77 ms →      221.16 ms   (-2.90%) |       1   →       1              |      227.77 ms →      221.16 ms   (-2.90%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.65 ms →       28.10 ms   (+9.53%) |       1   →       1              |       25.65 ms →       28.10 ms   (+9.53%) | 
- │ ├ sirius::K_point::K_point                                          |        1.94 μs →        2.18 μs  (+12.13%) |       2   →       2              |        3.88 μs →        4.36 μs  (+12.13%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.62 ms →       28.06 ms   (+9.53%) |       1   →       1              |       25.62 ms →       28.06 ms   (+9.53%) | 
  │   └ sirius::K_point::initialize                                     |       25.56 ms →       28.00 ms   (+9.53%) |       1   →       1              |       25.56 ms →       28.00 ms   (+9.53%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.20 ms →       21.06 ms   (+9.69%) |       1   →       1              |       19.20 ms →       21.06 ms   (+9.69%) | 
  │     │ └ sddk::Gvec::init                                            |        4.92 ms →        5.37 ms   (+9.28%) |       1   →       1              |        4.92 ms →        5.37 ms   (+9.28%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.72 μs →       11.63 μs  (+50.67%) |       1   →       1              |        7.72 μs →       11.63 μs  (+50.67%) | 
  │     └ sirius::K_point::update                                       |        4.09 ms →        4.34 ms   (+6.05%) |       1   →       1              |        4.09 ms →        4.34 ms   (+6.05%) | 
  │       └ sirius::Beta_projectors                                     |        1.69 ms →        1.70 ms   (+0.50%) |       1   →       1              |        1.69 ms →        1.70 ms   (+0.50%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      893.12 μs →      899.28 μs   (+0.69%) |       1   →       1              |      893.12 μs →      899.28 μs   (+0.69%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.50 ms →        1.46 ms   (-2.64%) |       2   →       2              |        3.00 ms →        2.92 ms   (-2.64%) | 
  ├ sirius::Potential                                                   |       94.16 ms →       87.57 ms   (-6.99%) |       1   →       1              |       94.16 ms →       87.57 ms   (-6.99%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.56 ms →        2.45 ms   (-4.44%) |       6   →       6              |       15.37 ms →       14.69 ms   (-4.44%) | 
  │ └ sirius::Potential::update                                         |       78.42 ms →       72.55 ms   (-7.49%) |       1   →       1              |       78.42 ms →       72.55 ms   (-7.49%) | 
  │   └ sirius::Potential::generate_local_potential                     |       78.23 ms →       72.38 ms   (-7.48%) |       1   →       1              |       78.23 ms →       72.38 ms   (-7.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       50.94 ms →       49.96 ms   (-1.92%) |       1   →       1              |       50.94 ms →       49.96 ms   (-1.92%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       18.05 ms →       13.69 ms  (-24.20%) |       1   →       1              |       18.05 ms →       13.69 ms  (-24.20%) | 
  ├ sirius::Density                                                     |       75.40 ms →       75.87 ms   (+0.63%) |       1   →       1              |       75.40 ms →       75.87 ms   (+0.63%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.71 ms →        4.83 ms   (+2.52%) |       2   →       2              |        9.43 ms →        9.67 ms   (+2.52%) | 
  │ └ sirius::Density::update                                           |       65.86 ms →       66.09 ms   (+0.36%) |       1   →       1              |       65.86 ms →       66.09 ms   (+0.36%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.69 ms →       65.92 ms   (+0.35%) |       1   →       1              |       65.69 ms →       65.92 ms   (+0.35%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.22 ms →        3.19 ms   (-0.89%) |       1   →       1              |        3.22 ms →        3.19 ms   (-0.89%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.65 ms →       53.35 ms   (+1.32%) |       1   →       1              |       52.65 ms →       53.35 ms   (+1.32%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        8.60 ms →        8.13 ms   (-5.39%) |       1   →       1              |        8.60 ms →        8.13 ms   (-5.39%) | 
  ├ sirius::Density::initial_density                                    |       78.91 ms →       80.32 ms   (+1.79%) |       1   →       1              |       78.91 ms →       80.32 ms   (+1.79%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       52.83 ms →       53.53 ms   (+1.33%) |       1   →       1              |       52.83 ms →       53.53 ms   (+1.33%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.15 ms →        5.38 ms   (+4.44%) |       2   →       2              |       10.30 ms →       10.76 ms   (+4.44%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.21 ms →        4.21 ms   (-0.14%) |       1   →       1              |        4.21 ms →        4.21 ms   (-0.14%) | 
  ├ sirius::Potential::generate                                         |      186.46 ms →      190.20 ms   (+2.00%) |       1   →       1              |      186.46 ms →      190.20 ms   (+2.00%) | 
  │ ├ sirius::Potential::poisson                                        |       64.13 ms →       64.93 ms   (+1.26%) |       1   →       1              |       64.13 ms →       64.93 ms   (+1.26%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       10.04 ms →        9.76 ms   (-2.79%) |       1   →       1              |       10.04 ms →        9.76 ms   (-2.79%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.37 ms →        4.53 ms   (+3.84%) |       1   →       1              |        4.37 ms →        4.53 ms   (+3.84%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.21 ms →        4.52 ms   (+7.30%) |       1   →       1              |        4.21 ms →        4.52 ms   (+7.30%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.21 ms →        4.52 ms   (+7.30%) |       1   →       1              |        4.21 ms →        4.52 ms   (+7.30%) | 
  │ ├ sirius::Periodic_function::add                                    |      241.79 μs →      229.67 μs   (-5.01%) |       2   →       2              |      483.57 μs →      459.34 μs   (-5.01%) | 
  │ ├ sirius::Potential::xc                                             |       96.11 ms →       98.58 ms   (+2.58%) |       1   →       1              |       96.11 ms →       98.58 ms   (+2.58%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       95.09 ms →       97.52 ms   (+2.55%) |       1   →       1              |       95.09 ms →       97.52 ms   (+2.55%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.99 ms →        1.98 ms   (-0.60%) |       5   →       5              |        9.96 ms →        9.90 ms   (-0.60%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.45 ms →        2.64 ms   (+7.79%) |       9   →       9              |       22.05 ms →       23.77 ms   (+7.79%) | 
  │ │   ├ sirius::gradient                                              |        7.85 ms →        8.24 ms   (+4.99%) |       1   →       1              |        7.85 ms →        8.24 ms   (+4.99%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.52 ms →        2.66 ms   (+5.45%) |       3   →       3              |        7.56 ms →        7.97 ms   (+5.45%) | 
  │ │   ├ sirius::dot                                                   |        2.79 ms →        2.79 ms   (-0.25%) |       1   →       1              |        2.79 ms →        2.79 ms   (-0.25%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.58 ms →        2.56 ms   (-0.94%) |       1   →       1              |        2.58 ms →        2.56 ms   (-0.94%) | 
  │ │   └ sirius::divergence                                            |       19.64 ms →       19.84 ms   (+1.02%) |       1   →       1              |       19.64 ms →       19.84 ms   (+1.02%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.41 ms →        2.49 ms   (+3.55%) |       1   →       1              |        2.41 ms →        2.49 ms   (+3.55%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.29 ms →        3.41 ms   (+3.67%) |       1   →       1              |        3.29 ms →        3.41 ms   (+3.67%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       21.92 ms →       22.25 ms   (+1.50%) |       1   →       1              |       21.92 ms →       22.25 ms   (+1.50%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      190.00 ns →      204.00 ns   (+7.37%) |       1   →       1              |      190.00 ns →      204.00 ns   (+7.37%) | 
  ├ sirius::Hamiltonian0                                                |       13.90 ms →       13.87 ms   (-0.21%) |       1   →       1              |       13.90 ms →       13.87 ms   (-0.21%) | 
  │ ├ sirius::Local_operator                                            |       13.58 ms →       13.55 ms   (-0.22%) |       1   →       1              |       13.58 ms →       13.55 ms   (-0.22%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.04 ms →        7.10 ms   (+0.85%) |       1   →       1              |        7.04 ms →        7.10 ms   (+0.85%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.10 ms →        5.00 ms   (-2.09%) |       1   →       1              |        5.10 ms →        5.00 ms   (-2.09%) | 
  │ ├ sirius::Non_local_operator                                        |       59.59 μs →       59.90 μs   (+0.52%) |       2   →       2              |      119.17 μs →      119.80 μs   (+0.52%) | 
  │ ├ sirius::D_operator::initialize                                    |       79.56 μs →       78.92 μs   (-0.81%) |       1   →       1              |       79.56 μs →       78.92 μs   (-0.81%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.44 μs →       67.48 μs   (-1.40%) |       1   →       1              |       68.44 μs →       67.48 μs   (-1.40%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.48 s  →        2.45 s    (-1.17%) |       1   →       1              |        2.48 s  →        2.45 s    (-1.17%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms →        8.39 ms   (-0.21%) |       1   →       1              |        8.40 ms →        8.39 ms   (-0.21%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      239.62 μs →      230.84 μs   (-3.66%) |       1   →       1              |      239.62 μs →      230.84 μs   (-3.66%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.15 ms   (-0.11%) |       1   →       1              |        8.16 ms →        8.15 ms   (-0.11%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.47 s  →        2.45 s    (-1.17%) |       1   →       1              |        2.47 s  →        2.45 s    (-1.17%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       94.59 ms →       86.23 ms   (-8.83%) |       4   →       4              |      378.34 ms →      344.92 ms   (-8.83%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.20 ms →       25.62 ms   (+1.70%) |       1   →       1              |       25.20 ms →       25.62 ms   (+1.70%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.35 ms →       14.85 ms   (+3.49%) |       1   →       1              |       14.35 ms →       14.85 ms   (+3.49%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.21 s    (+0.39%) |       1   →       1              |        1.21 s  →        1.21 s    (+0.39%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      982.07 ms →      987.96 ms   (+0.60%) |       1   →       1              |      982.07 ms →      987.96 ms   (+0.60%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      309.45 ms →      317.24 ms   (+2.52%) |       1   →       1              |      309.45 ms →      317.24 ms   (+2.52%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      181.88 ms →      174.11 ms   (-4.27%) |       1   →       1              |      181.88 ms →      174.11 ms   (-4.27%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      181.87 ms →      174.11 ms   (-4.27%) |       1   →       1              |      181.87 ms →      174.11 ms   (-4.27%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      109.08 ms →      124.73 ms  (+14.35%) |       1   →       1              |      109.08 ms →      124.73 ms  (+14.35%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      178.06 ms →      172.87 ms   (-2.92%) |       1   →       1              |      178.06 ms →      172.87 ms   (-2.92%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      178.06 ms →      172.86 ms   (-2.92%) |       1   →       1              |      178.06 ms →      172.86 ms   (-2.92%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      164.21 ms →      167.49 ms   (+2.00%) |       1   →       1              |      164.21 ms →      167.49 ms   (+2.00%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      113.71 ms →      116.92 ms   (+2.82%) |       1   →       1              |      113.71 ms →      116.92 ms   (+2.82%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.74 ms →        3.77 ms   (+0.69%) |       1   →       1              |        3.74 ms →        3.77 ms   (+0.69%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.89 ms →       89.72 ms   (-1.29%) |       1   →       1              |       90.89 ms →       89.72 ms   (-1.29%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       13.14 ms →       12.04 ms   (-8.38%) |       1   →       1              |       13.14 ms →       12.04 ms   (-8.38%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.22 ms →       64.19 ms   (-0.05%) |       2   →       2              |      128.45 ms →      128.38 ms   (-0.05%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      192.68 ms →      192.35 ms   (-0.17%) |       2   →       2              |      385.35 ms →      384.71 ms   (-0.17%) | 
  │ │ │ └ sddk::wf_inner                                                |      192.57 ms →      192.25 ms   (-0.16%) |       2   →       2              |      385.14 ms →      384.51 ms   (-0.16%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       35.50 ns →       14.50 ns  (-59.15%) |       2   →       2              |       71.00 ns →       29.00 ns  (-59.15%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      190.91 ms →      190.64 ms   (-0.14%) |       2   →       2              |      381.81 ms →      381.28 ms   (-0.14%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       30.00 ns →       14.50 ns  (-51.67%) |       2   →       2              |       60.00 ns →       29.00 ns  (-51.67%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      114.76 ms →      114.81 ms   (+0.04%) |       1   →       1              |      114.76 ms →      114.81 ms   (+0.04%) | 
  │ │ └ sddk::wf_trans                                                  |       37.67 ms →       38.69 ms   (+2.70%) |       1   →       1              |       37.67 ms →       38.69 ms   (+2.70%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.65 ms →       35.65 ms   (-0.02%) |       1   →       1              |       35.65 ms →       35.65 ms   (-0.02%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      399.00 ns →      599.00 ns  (+50.13%) |       1   →       1              |      399.00 ns →      599.00 ns  (+50.13%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      104.74 s  →      123.78 s   (+18.18%) |       1   →       1              |      104.74 s  →      123.78 s   (+18.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.14 ms →        2.16 ms   (+1.12%) |      31   →      31              |       66.20 ms →       66.94 ms   (+1.12%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.75 s  →        2.74 s    (-0.41%) |      38   →      45    (+18.42%) |      104.44 s  →      123.17 s   (+17.94%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.58 ms →        8.57 ms  (+13.08%) |      38   →      45    (+18.42%) |      287.85 ms →      385.46 ms  (+33.91%) | 
- │ │ │ ├ sirius::Local_operator                                        |        7.24 ms →        8.23 ms  (+13.66%) |      38   →      45    (+18.42%) |      275.21 ms →      370.43 ms  (+34.60%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.56 ms →        1.51 ms   (-3.41%) |      38   →      45    (+18.42%) |       59.32 ms →       67.85 ms  (+14.38%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.22 ms →        5.26 ms  (+24.78%) |      38   →      45    (+18.42%) |      160.18 ms →      236.69 ms  (+47.77%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       60.81 μs →       60.88 μs   (+0.11%) |      76   →      90    (+18.42%) |        4.62 ms →        5.48 ms  (+18.55%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       81.73 μs →       83.20 μs   (+1.81%) |      38   →      45    (+18.42%) |        3.11 ms →        3.74 ms  (+20.56%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       68.65 μs →       68.99 μs   (+0.49%) |      38   →      45    (+18.42%) |        2.61 ms →        3.10 ms  (+19.00%) | 
- │ │ ├ sirius::Band::solve                                             |        2.08 s  →        2.05 s    (-1.34%) |      38   →      45    (+18.42%) |       79.10 s  →       92.42 s   (+16.83%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      204.57 μs →      206.30 μs   (+0.85%) |      38   →      45    (+18.42%) |        7.77 ms →        9.28 ms  (+19.42%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      197.96 μs →      199.16 μs   (+0.61%) |      38   →      45    (+18.42%) |        7.52 ms →        8.96 ms  (+19.14%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.99 μs →        5.17 μs   (+3.63%) |      38   →      45    (+18.42%) |      189.45 μs →      232.48 μs  (+22.72%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.07 s  →        2.03 s    (-2.05%) |      38   →      45    (+18.42%) |       78.81 s  →       91.42 s   (+15.99%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       60.25 ms →       92.08 ms  (+52.84%) |      38   →      45    (+18.42%) |        2.29 s  →        4.14 s   (+81.00%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.61 ms →        2.96 ms  (-35.83%) |     228   →     315    (+38.16%) |        1.05 s  →      932.13 ms  (-11.34%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.64 ms →        1.67 ms   (+1.85%) |      38   →      45    (+18.42%) |       62.47 ms →       75.35 ms  (+20.61%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      417.97 μs →      419.08 μs   (+0.27%) |      38   →      45    (+18.42%) |       15.88 ms →       18.86 ms  (+18.74%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      963.72 μs →        1.00 ms   (+4.25%) |      38   →      45    (+18.42%) |       36.62 ms →       45.21 ms  (+23.45%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.99 s  →        1.87 s    (-5.94%) |      38   →      45    (+18.42%) |       75.55 s  →       84.15 s   (+11.39%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      213.33 ms →      189.18 ms  (-11.32%) |     201   →     254    (+26.37%) |       42.88 s  →       48.05 s   (+12.06%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.09 ms →      133.44 ms  (-11.68%) |     201   →     254    (+26.37%) |       30.37 s  →       33.89 s   (+11.61%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.83 ms →       24.39 ms  (-12.34%) |     201   →     254    (+26.37%) |        5.59 s  →        6.20 s   (+10.78%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      713.17 μs →        1.18 ms  (+66.04%) |     201   →     254    (+26.37%) |      143.35 ms →      300.78 ms (+109.82%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.76 ms →        6.53 ms  (+73.56%) |      38   →      46    (+21.05%) |      142.90 ms →      300.23 ms (+110.10%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.72 ms →       19.31 ms  (-15.00%) |     201   →     254    (+26.37%) |        4.57 s  →        4.90 s    (+7.41%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      767.99 μs →        1.36 ms  (+77.66%) |     201   →     254    (+26.37%) |      154.37 ms →      346.55 ms (+124.50%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        4.05 ms →        7.52 ms  (+85.77%) |      38   →      46    (+21.05%) |      153.82 ms →      345.89 ms (+124.87%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.40 ms →       29.66 ms  (-13.76%) |     201   →     254    (+26.37%) |        6.91 s  →        7.53 s    (+8.98%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.82 ms →       18.54 ms  (-15.05%) |     201   →     254    (+26.37%) |        4.39 s  →        4.71 s    (+7.35%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.60 ms   (-1.88%) |     201   →     254    (+26.37%) |      533.12 ms →      661.06 ms  (+24.00%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.70 ms →       19.94 ms  (-12.15%) |     201   →     254    (+26.37%) |        4.56 s  →        5.06 s   (+11.01%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.76 ms →        2.18 ms  (-20.98%) |     201   →     254    (+26.37%) |      554.95 ms →      554.13 ms   (-0.15%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.43 ms →       16.59 ms  (-10.01%) |     402   →     508    (+26.37%) |        7.41 s  →        8.43 s   (+13.72%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       57.42 ms →       50.79 ms  (-11.54%) |     201   →     254    (+26.37%) |       11.54 s  →       12.90 s   (+11.78%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |       13.45 ms →       11.96 ms  (-11.03%) |     364   →     463    (+27.20%) |        4.89 s  →        5.54 s   (+13.16%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       52.76 ns →       52.93 ns   (+0.32%) |     364   →     463    (+27.20%) |       19.21 μs →       24.51 μs  (+27.61%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.74 ms →        8.31 ms  (-14.66%) |     364   →     463    (+27.20%) |        3.55 s  →        3.85 s    (+8.56%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       39.20 ns →       72.91 ns  (+85.99%) |     364   →     463    (+27.20%) |       14.27 μs →       33.76 μs (+136.58%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.16 ms →        2.82 ms  (-10.53%) |     201   →     254    (+26.37%) |      634.40 ms →      717.23 ms  (+13.06%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.65 ms →       13.85 ms  (-11.48%) |     201   →     254    (+26.37%) |        3.14 s  →        3.52 s   (+11.86%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |       17.58 ms →       14.95 ms  (-14.95%) |     163   →     209    (+28.22%) |        2.87 s  →        3.13 s    (+9.05%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.83 ms →        4.96 ms  (-14.99%) |     489   →     627    (+28.22%) |        2.85 s  →        3.11 s    (+9.00%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       20.82 ms →       18.23 ms  (-12.43%) |     201   →     254    (+26.37%) |        4.18 s  →        4.63 s   (+10.66%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |       19.75 ms →       17.27 ms  (-12.55%) |     201   →     254    (+26.37%) |        3.97 s  →        4.39 s   (+10.50%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |      116.21 ns →       42.58 ns  (-63.36%) |     201   →     254    (+26.37%) |       23.36 μs →       10.81 μs  (-53.70%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       16.21 ms →       13.73 ms  (-15.29%) |     201   →     254    (+26.37%) |        3.26 s  →        3.49 s    (+7.04%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       20.58 ns →       36.01 ns  (+74.95%) |     201   →     254    (+26.37%) |        4.14 μs →        9.15 μs (+121.08%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       46.66 ms →       40.28 ms  (-13.69%) |     201   →     254    (+26.37%) |        9.38 s  →       10.23 s    (+9.07%) | 
- │ │ │ │   ├ sirius::residuals                                         |       17.12 ms →       15.71 ms   (-8.26%) |     196   →     249    (+27.04%) |        3.36 s  →        3.91 s   (+16.55%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |       18.19 ms →       13.91 ms  (-23.51%) |     164   →     249    (+51.83%) |        2.98 s  →        3.46 s   (+16.14%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.03 ms →        6.20 ms  (-22.85%) |     328   →     498    (+51.83%) |        2.64 s  →        3.09 s   (+17.14%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.56 ms →        1.23 ms  (-20.89%) |     164   →     249    (+51.83%) |      255.27 ms →      306.62 ms  (+20.12%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       52.45 ms →       51.30 ms   (-2.21%) |      80   →      86     (+7.50%) |        4.20 s  →        4.41 s    (+5.12%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       33.45 ms →       33.83 ms   (+1.15%) |     122   →     127     (+4.10%) |        4.08 s  →        4.30 s    (+5.30%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       24.22 ms →       25.46 ms   (+5.12%) |     164   →     168     (+2.44%) |        3.97 s  →        4.28 s    (+7.68%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      536.29 ns →      709.60 ns  (+32.32%) |      38   →      45    (+18.42%) |       20.38 μs →       31.93 μs  (+56.69%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.29 μs →       75.94 μs (+150.70%) |      38   →      45    (+18.42%) |        1.15 ms →        3.42 ms (+196.88%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.52 ms →        3.40 ms   (-3.23%) |      38   →      45    (+18.42%) |      133.69 ms →      153.21 ms  (+14.60%) | 
- │ │ ├ sirius::Density::generate                                       |      300.49 ms →      303.40 ms   (+0.97%) |      38   →      45    (+18.42%) |       11.42 s  →       13.65 s   (+19.57%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      296.35 ms →      299.13 ms   (+0.94%) |      38   →      45    (+18.42%) |       11.26 s  →       13.46 s   (+19.53%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.43 ms →       64.73 ms   (-4.00%) |      38   →      45    (+18.42%) |        2.56 s  →        2.91 s   (+13.68%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       64.22 μs →       57.44 μs  (-10.56%) |      38   →      45    (+18.42%) |        2.44 ms →        2.58 ms   (+5.91%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms →        1.20 ms   (+2.53%) |       2   →       2              |        2.33 ms →        2.39 ms   (+2.53%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       56.17 ms →       53.45 ms   (-4.84%) |      38   →      45    (+18.42%) |        2.13 s  →        2.41 s   (+12.69%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.11 ms →       60.99 ms   (-0.19%) |      38   →      45    (+18.42%) |        2.32 s  →        2.74 s   (+18.19%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.13 μs →       10.94 μs   (-1.71%) |      38   →      45    (+18.42%) |      423.03 μs →      492.38 μs  (+16.39%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (-0.04%) |      38   →      45    (+18.42%) |       87.68 ms →      103.78 ms  (+18.37%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.26 ms →       58.14 ms   (-0.20%) |      38   →      45    (+18.42%) |        2.21 s  →        2.62 s   (+18.19%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.83 ms →        6.72 ms   (-1.54%) |      38   →      45    (+18.42%) |      259.37 ms →      302.43 ms  (+16.60%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      746.74 ns →      591.62 ns  (-20.77%) |      38   →      45    (+18.42%) |       28.38 μs →       26.62 μs   (-6.18%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.26 ms →      104.51 ms   (+0.24%) |      38   →      45    (+18.42%) |        3.96 s  →        4.70 s   (+18.71%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.41 ms   (+0.39%) |      38   →      45    (+18.42%) |       91.25 ms →      108.49 ms  (+18.89%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       20.08 ms →       20.04 ms   (-0.18%) |      38   →      45    (+18.42%) |      762.98 ms →      901.94 ms  (+18.21%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.91 ms →       19.87 ms   (-0.17%) |      38   →      45    (+18.42%) |      756.52 ms →      894.32 ms  (+18.22%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      233.61 ns →      217.84 ns   (-6.75%) |      38   →      45    (+18.42%) |        8.88 μs →        9.80 μs  (+10.43%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.25 ms   (-0.22%) |      38   →      45    (+18.42%) |       47.67 ms →       56.33 ms  (+18.16%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.88 ms →        3.02 ms   (+4.91%) |      38   →      45    (+18.42%) |      109.55 ms →      136.11 ms  (+24.24%) | 
- │ │ ├ sirius::Density::mix                                            |      126.51 ms →      133.20 ms   (+5.29%) |      38   →      45    (+18.42%) |        4.81 s  →        5.99 s   (+24.69%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      260.20 μs →      263.02 μs   (+1.09%) |      38   →      45    (+18.42%) |        9.89 ms →       11.84 ms  (+19.71%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        2.79 ms →        3.15 ms  (+12.93%) |      38   →      45    (+18.42%) |      105.89 ms →      141.61 ms  (+33.73%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.60 ms →        2.95 ms  (+13.68%) |      38   →      45    (+18.42%) |       98.70 ms →      132.87 ms  (+34.62%) | 
- │ │ ├ sirius::Potential::generate                                     |      180.72 ms →      186.33 ms   (+3.10%) |      38   →      45    (+18.42%) |        6.87 s  →        8.38 s   (+22.09%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       64.21 ms →       66.02 ms   (+2.81%) |      38   →      45    (+18.42%) |        2.44 s  →        2.97 s   (+21.75%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       10.23 ms →       10.91 ms   (+6.71%) |      38   →      45    (+18.42%) |      388.67 ms →      491.16 ms  (+26.37%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.18 ms →        4.37 ms   (+4.66%) |      38   →      45    (+18.42%) |      158.66 ms →      196.64 ms  (+23.94%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.05 ms →        4.25 ms   (+5.07%) |      38   →      45    (+18.42%) |      153.87 ms →      191.45 ms  (+24.42%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.05 ms →        4.25 ms   (+5.06%) |      38   →      45    (+18.42%) |      153.85 ms →      191.42 ms  (+24.42%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      231.55 μs →      229.86 μs   (-0.73%) |      76   →      90    (+18.42%) |       17.60 ms →       20.69 ms  (+17.56%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       91.15 ms →       94.44 ms   (+3.61%) |      38   →      45    (+18.42%) |        3.46 s  →        4.25 s   (+22.69%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       90.09 ms →       93.40 ms   (+3.67%) |      38   →      45    (+18.42%) |        3.42 s  →        4.20 s   (+22.77%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.58 ms →        1.60 ms   (+0.80%) |     190   →     225    (+18.42%) |      301.06 ms →      359.39 ms  (+19.37%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.51 ms →        2.84 ms  (+13.09%) |     342   →     405    (+18.42%) |      858.30 ms →        1.15 s   (+33.92%) | 
- │ │ │ │   ├ sirius::gradient                                          |        2.49 ms →        2.44 ms   (-2.11%) |      38   →      45    (+18.42%) |       94.78 ms →      109.88 ms  (+15.92%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      739.53 μs →      719.85 μs   (-2.66%) |     114   →     135    (+18.42%) |       84.31 ms →       97.18 ms  (+15.27%) | 
- │ │ │ │   ├ sirius::dot                                               |        2.81 ms →        2.82 ms   (+0.61%) |      38   →      45    (+18.42%) |      106.60 ms →      127.00 ms  (+19.14%) | 
- │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms →        2.59 ms   (+0.50%) |      38   →      45    (+18.42%) |       97.85 ms →      116.46 ms  (+19.01%) | 
- │ │ │ │   └ sirius::divergence                                        |       19.69 ms →       19.76 ms   (+0.36%) |      38   →      45    (+18.42%) |      748.27 ms →      889.34 ms  (+18.85%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.43 ms →        2.44 ms   (+0.23%) |      38   →      45    (+18.42%) |       92.47 ms →      109.75 ms  (+18.69%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.34 ms →        3.59 ms   (+7.32%) |      38   →      45    (+18.42%) |      127.00 ms →      161.41 ms  (+27.09%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       21.00 ms →       21.27 ms   (+1.26%) |      38   →      45    (+18.42%) |      798.05 ms →      956.95 ms  (+19.91%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      281.92 ns →      216.29 ns  (-23.28%) |      38   →      45    (+18.42%) |       10.71 μs →        9.73 μs   (-9.15%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      216.03 ns →      209.09 ns   (-3.21%) |      38   →      45    (+18.42%) |        8.21 μs →        9.41 μs  (+14.62%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.30 ms →        2.70 ms  (+17.16%) |      38   →      45    (+18.42%) |       87.42 ms →      121.29 ms  (+38.74%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.18 ms →        4.12 ms   (-1.60%) |     266   →     315    (+18.42%) |        1.11 s  →        1.30 s   (+16.53%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.08 ms →        3.92 ms   (-3.87%) |     266   →     315    (+18.42%) |        1.08 s  →        1.23 s   (+13.84%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        3.92 ms   (-3.87%) |     266   →     315    (+18.42%) |        1.08 s  →        1.23 s   (+13.83%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.01 ms →        4.20 ms   (+4.76%) |     114   →     135    (+18.42%) |      457.51 ms →      567.60 ms  (+24.06%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.88 ms →        4.06 ms   (+4.59%) |     114   →     135    (+18.42%) |      442.20 ms →      547.69 ms  (+23.86%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        3.96 ms →        4.05 ms   (+2.38%) |      38   →      45    (+18.42%) |      150.48 ms →      182.44 ms  (+21.24%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      116.25 μs →      152.59 μs  (+31.27%) |      38   →      45    (+18.42%) |        4.42 ms →        6.87 ms  (+55.45%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      112.65 μs →      149.25 μs  (+32.49%) |      38   →      45    (+18.42%) |        4.28 ms →        6.72 ms  (+56.90%) | 
- │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.53 ms →        8.07 ms  (+45.95%) |       2   →       2              |       11.06 ms →       16.14 ms  (+45.95%) | 
+ │ ├ sirius::Periodic_function|inner                                   |        4.53 ms →        3.95 ms  (-12.91%) |       6   →       6              |       27.20 ms →       23.69 ms  (-12.91%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.09 ms →        3.88 ms   (-5.08%) |       6   →       6              |       24.54 ms →       23.30 ms   (-5.08%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.09 ms →        3.88 ms   (-5.08%) |       6   →       6              |       24.54 ms →       23.29 ms   (-5.08%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.35 ms →        4.18 ms   (-3.94%) |       3   →       3              |       13.06 ms →       12.54 ms   (-3.94%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.85 ms →        4.03 ms   (+4.68%) |       3   →       3              |       11.55 ms →       12.09 ms   (+4.68%) | 
+ ├ sirius::Periodic_function|inner                                     |        4.53 ms →        3.93 ms  (-13.29%) |       2   →       2              |        9.07 ms →        7.86 ms  (-13.29%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.03 ms →        3.87 ms   (-3.75%) |       2   →       2              |        8.05 ms →        7.75 ms   (-3.75%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.03 ms →        3.87 ms   (-3.75%) |       2   →       2              |        8.05 ms →        7.75 ms   (-3.75%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.35 ms →        4.07 ms   (-6.50%) |       1   →       1              |        4.35 ms →        4.07 ms   (-6.50%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.88 ms →        4.01 ms   (+3.15%) |       1   →       1              |        3.88 ms →        4.01 ms   (+3.15%) | 
  └ sirius::finalize                                                    |      480.72 ms →      470.10 ms   (-2.21%) |       1   →       1              |      480.72 ms →      470.10 ms   (-2.21%) | 
  ====================================================================================================================================================================================================
```
