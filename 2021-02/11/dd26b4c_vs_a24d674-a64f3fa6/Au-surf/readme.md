# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      155.82 s  →      138.27 s   (-11.26%) |       1   →       1              |      155.82 s  →      138.27 s   (-11.26%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.74 s    (-0.26%) |       1   →       1              |        2.75 s  →        2.74 s    (-0.26%) | 
  ├ sirius::Simulation_context::initialize                              |        2.09 s  →        2.12 s    (+1.26%) |       1   →       1              |        2.09 s  →        2.12 s    (+1.26%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       14.59 ms →       27.88 ms  (+90.99%) |       1   →       1              |       14.59 ms →       27.88 ms  (+90.99%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       87.50 ms →      116.42 ms  (+33.05%) |       1   →       1              |       87.50 ms →      116.42 ms  (+33.05%) | 
- │ │ ├ sirius::Atom_type::init                                         |       63.33 ms →       90.96 ms  (+43.63%) |       1   →       1              |       63.33 ms →       90.96 ms  (+43.63%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.11 ms →       25.30 ms   (+4.96%) |       1   →       1              |       24.11 ms →       25.30 ms   (+4.96%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.33 ms →       10.48 ms   (+1.41%) |       1   →       1              |       10.33 ms →       10.48 ms   (+1.41%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.75 ms →       14.79 ms   (+7.60%) |       1   →       1              |       13.75 ms →       14.79 ms   (+7.60%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.35 ms →       13.99 ms   (+4.85%) |       1   →       1              |       13.35 ms →       13.99 ms   (+4.85%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       13.13 ms →       13.76 ms   (+4.82%) |       1   →       1              |       13.13 ms →       13.76 ms   (+4.82%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      206.34 μs →      218.02 μs   (+5.66%) |       1   →       1              |      206.34 μs →      218.02 μs   (+5.66%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.29 μs →        3.22 μs  (+40.60%) |       1   →       1              |        2.29 μs →        3.22 μs  (+40.60%) | 
  │ └ sirius::Simulation_context::update                                |        1.93 s  →        1.91 s    (-1.16%) |       1   →       1              |        1.93 s  →        1.91 s    (-1.16%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.78 ms →       13.39 ms   (+4.79%) |       1   →       1              |       12.78 ms →       13.39 ms   (+4.79%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.20 ms →        8.45 ms   (+3.00%) |       1   →       1              |        8.20 ms →        8.45 ms   (+3.00%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.56 ms →        4.92 ms   (+8.03%) |       1   →       1              |        4.56 ms →        4.92 ms   (+8.03%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.15 ms →        4.34 ms   (+4.61%) |       1   →       1              |        4.15 ms →        4.34 ms   (+4.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.94 ms →        4.11 ms   (+4.30%) |       1   →       1              |        3.94 ms →        4.11 ms   (+4.30%) | 
- │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      202.54 μs →      224.01 μs  (+10.60%) |       1   →       1              |      202.54 μs →      224.01 μs  (+10.60%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.30 μs →        1.17 μs  (-10.04%) |       1   →       1              |        1.30 μs →        1.17 μs  (-10.04%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       17.41 ms →       16.94 ms   (-2.68%) |       2   →       2              |       34.82 ms →       33.89 ms   (-2.68%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.09 ms   (+0.44%) |       2   →       2              |        2.17 ms →        2.18 ms   (+0.44%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      947.95 μs →      952.00 μs   (+0.43%) |       1   →       1              |      947.95 μs →      952.00 μs   (+0.43%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.09 ms →        4.97 ms   (-2.47%) |       2   →       2              |       10.19 ms →        9.94 ms   (-2.47%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.63 ms →        3.64 ms   (+0.22%) |       2   →       2              |        7.26 ms →        7.27 ms   (+0.22%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.64 ms →       15.65 ms   (+0.09%) |       4   →       4              |       62.55 ms →       62.61 ms   (+0.09%) | 
  │   ├ sddk::Gvec::init                                                |      162.05 ms →      158.78 ms   (-2.02%) |       2   →       2              |      324.09 ms →      317.56 ms   (-2.02%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.17 ms →      126.10 ms   (-0.84%) |       2   →       2              |      254.34 ms →      252.20 ms   (-0.84%) | 
  │   ├ sddk::Gvec_shells                                               |      131.39 ms →      123.48 ms   (-6.02%) |       1   →       1              |      131.39 ms →      123.48 ms   (-6.02%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.03 ms   (-0.46%) |       1   →       1              |        1.04 ms →        1.03 ms   (-0.46%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      218.43 ms →      221.52 ms   (+1.42%) |       1   →       1              |      218.43 ms →      221.52 ms   (+1.42%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       29.91 ms →       29.15 ms   (-2.53%) |       1   →       1              |       29.91 ms →       29.15 ms   (-2.53%) | 
- │ ├ sirius::K_point::K_point                                          |        2.12 μs →        8.28 μs (+290.52%) |       2   →       2              |        4.24 μs →       16.55 μs (+290.52%) | 
  │ └ sirius::K_point_set::initialize                                   |       29.88 ms →       29.10 ms   (-2.61%) |       1   →       1              |       29.88 ms →       29.10 ms   (-2.61%) | 
  │   └ sirius::K_point::initialize                                     |       29.79 ms →       29.04 ms   (-2.51%) |       1   →       1              |       29.79 ms →       29.04 ms   (-2.51%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       21.86 ms →       21.91 ms   (+0.23%) |       1   →       1              |       21.86 ms →       21.91 ms   (+0.23%) | 
  │     │ └ sddk::Gvec::init                                            |        5.40 ms →        5.83 ms   (+8.01%) |       1   →       1              |        5.40 ms →        5.83 ms   (+8.01%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       10.68 μs →        8.47 μs  (-20.64%) |       1   →       1              |       10.68 μs →        8.47 μs  (-20.64%) | 
  │     └ sirius::K_point::update                                       |        4.86 ms →        4.55 ms   (-6.30%) |       1   →       1              |        4.86 ms →        4.55 ms   (-6.30%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.71 ms   (-0.26%) |       1   →       1              |        1.72 ms →        1.71 ms   (-0.26%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      902.64 μs →      885.79 μs   (-1.87%) |       1   →       1              |      902.64 μs →      885.79 μs   (-1.87%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.22 ms →        1.46 ms  (-34.12%) |       2   →       2              |        4.44 ms →        2.93 ms  (-34.12%) | 
- ├ sirius::Potential                                                   |       82.49 ms →      173.99 ms (+110.93%) |       1   →       1              |       82.49 ms →      173.99 ms (+110.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.49 ms   (+1.72%) |       6   →       6              |       14.70 ms →       14.95 ms   (+1.72%) | 
- │ └ sirius::Potential::update                                         |       67.47 ms →      158.67 ms (+135.17%) |       1   →       1              |       67.47 ms →      158.67 ms (+135.17%) | 
- │   └ sirius::Potential::generate_local_potential                     |       67.30 ms →      158.50 ms (+135.52%) |       1   →       1              |       67.30 ms →      158.50 ms (+135.52%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.86 ms →       49.80 ms  (-16.81%) |       1   →       1              |       59.86 ms →       49.80 ms  (-16.81%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        7.24 ms →       16.49 ms (+127.61%) |       1   →       1              |        7.24 ms →       16.49 ms (+127.61%) | 
  ├ sirius::Density                                                     |       72.94 ms →       74.92 ms   (+2.71%) |       1   →       1              |       72.94 ms →       74.92 ms   (+2.71%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.76 ms →        4.80 ms   (+0.88%) |       2   →       2              |        9.51 ms →        9.60 ms   (+0.88%) | 
  │ └ sirius::Density::update                                           |       63.32 ms →       65.21 ms   (+2.98%) |       1   →       1              |       63.32 ms →       65.21 ms   (+2.98%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       63.14 ms →       65.03 ms   (+2.99%) |       1   →       1              |       63.14 ms →       65.03 ms   (+2.99%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.12 ms            |                   1              |                         3.12 ms            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.48 ms →       53.49 ms  (-10.07%) |       1   →       1              |       59.48 ms →       53.49 ms  (-10.07%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.46 ms →        7.17 ms (+107.01%) |       1   →       1              |        3.46 ms →        7.17 ms (+107.01%) | 
  ├ sirius::Density::initial_density                                    |       80.15 ms →       78.73 ms   (-1.77%) |       1   →       1              |       80.15 ms →       78.73 ms   (-1.77%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       58.60 ms →       53.50 ms   (-8.69%) |       1   →       1              |       58.60 ms →       53.50 ms   (-8.69%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.76 ms →        4.70 ms  (+70.61%) |       2   →       2              |        5.51 ms →        9.41 ms  (+70.61%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.22 ms →        3.92 ms   (-7.10%) |       1   →       1              |        4.22 ms →        3.92 ms   (-7.10%) | 
- ├ sirius::Potential::generate                                         |      190.46 ms →      213.63 ms  (+12.17%) |       1   →       1              |      190.46 ms →      213.63 ms  (+12.17%) | 
  │ ├ sirius::Potential::poisson                                        |       64.64 ms →       64.29 ms   (-0.53%) |       1   →       1              |       64.64 ms →       64.29 ms   (-0.53%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.40 ms →        8.33 ms (+247.08%) |       1   →       1              |        2.40 ms →        8.33 ms (+247.08%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.39 ms →        4.59 ms   (+4.47%) |       1   →       1              |        4.39 ms →        4.59 ms   (+4.47%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.23 ms →        4.40 ms   (+3.89%) |       1   →       1              |        4.23 ms →        4.40 ms   (+3.89%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.23 ms →        4.39 ms   (+3.89%) |       1   →       1              |        4.23 ms →        4.39 ms   (+3.89%) | 
+ │ ├ sirius::Periodic_function::add                                    |      242.62 μs →      199.31 μs  (-17.85%) |       2   →       2              |      485.23 μs →      398.62 μs  (-17.85%) | 
- │ ├ sirius::Potential::xc                                             |       99.11 ms →      122.66 ms  (+23.76%) |       1   →       1              |       99.11 ms →      122.66 ms  (+23.76%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       99.11 ms →      121.57 ms  (+22.67%) |       1   →       1              |       99.11 ms →      121.57 ms  (+22.67%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.27 ms →        1.51 ms  (-33.52%) |       5   →       8    (+60.00%) |       11.33 ms →       12.05 ms   (+6.37%) | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.46 ms →        2.37 ms   (-3.34%) |       9   →      12    (+33.33%) |       22.10 ms →       28.48 ms  (+28.88%) | 
  │ │   ├ sirius::gradient                                              |        7.50 ms →        7.62 ms   (+1.72%) |       1   →       1              |        7.50 ms →        7.62 ms   (+1.72%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.41 ms →        2.44 ms   (+1.32%) |       3   →       3              |        7.22 ms →        7.31 ms   (+1.32%) | 
  │ │   ├ sirius::dot                                                   |        2.78 ms →        2.83 ms   (+1.89%) |       1   →       1              |        2.78 ms →        2.83 ms   (+1.89%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.57 ms →        2.61 ms   (+1.64%) |       1   →       1              |        2.57 ms →        2.61 ms   (+1.64%) | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                         9.53 ms            |                   2              |                        19.07 ms            | 
- │ │   └ sirius::divergence                                            |       22.44 ms →       19.76 ms  (-11.94%) |       1   →       2   (+100.00%) |       22.44 ms →       39.52 ms  (+76.13%) | 
- │ │     └ sirius::Smooth_periodic_function                            |        2.41 ms →        2.44 ms   (+1.55%) |       1   →       2   (+100.00%) |        2.41 ms →        4.89 ms (+103.10%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.36 ms →        3.37 ms   (+0.27%) |       1   →       1              |        3.36 ms →        3.37 ms   (+0.27%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.32 ms →       22.31 ms   (-0.04%) |       1   →       1              |       22.32 ms →       22.31 ms   (-0.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      201.00 ns →      198.00 ns   (-1.49%) |       1   →       1              |      201.00 ns →      198.00 ns   (-1.49%) | 
  ├ sirius::Hamiltonian0                                                |       14.22 ms →       15.35 ms   (+7.94%) |       1   →       1              |       14.22 ms →       15.35 ms   (+7.94%) | 
  │ ├ sirius::Local_operator                                            |       13.89 ms →       13.45 ms   (-3.15%) |       1   →       1              |       13.89 ms →       13.45 ms   (-3.15%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.15 ms →        7.15 ms   (-0.06%) |       1   →       1              |        7.15 ms →        7.15 ms   (-0.06%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.29 ms →        4.86 ms   (-8.24%) |       1   →       1              |        5.29 ms →        4.86 ms   (-8.24%) | 
  │ ├ sirius::Non_local_operator                                        |       60.98 μs →       59.67 μs   (-2.14%) |       2   →       2              |      121.96 μs →      119.34 μs   (-2.14%) | 
- │ ├ sirius::D_operator::initialize                                    |       80.86 μs →      613.80 μs (+659.10%) |       1   →       1              |       80.86 μs →      613.80 μs (+659.10%) | 
- │ └ sirius::Q_operator::initialize                                    |       69.11 μs →        1.10 ms (+1493.59%) |       1   →       1              |       69.11 μs →        1.10 ms (+1493.59%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.17 s  →        2.49 s   (+14.37%) |       1   →       1              |        2.17 s  →        2.49 s   (+14.37%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.43 ms →        8.42 ms   (-0.03%) |       1   →       1              |        8.43 ms →        8.42 ms   (-0.03%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      272.67 μs →      260.26 μs   (-4.55%) |       1   →       1              |      272.67 μs →      260.26 μs   (-4.55%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.16 ms   (+0.10%) |       1   →       1              |        8.15 ms →        8.16 ms   (+0.10%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.17 s  →        2.48 s   (+14.29%) |       1   →       1              |        2.17 s  →        2.48 s   (+14.29%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       87.80 ms →       87.63 ms   (-0.20%) |       4   →       4              |      351.22 ms →      350.52 ms   (-0.20%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.13 ms →       25.06 ms   (-0.29%) |       1   →       1              |       25.13 ms →       25.06 ms   (-0.29%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.33 ms →       14.36 ms   (+0.24%) |       1   →       1              |       14.33 ms →       14.36 ms   (+0.24%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.19 s  →        1.20 s    (+1.15%) |       1   →       1              |        1.19 s  →        1.20 s    (+1.15%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      969.84 ms →      982.99 ms   (+1.36%) |       1   →       1              |      969.84 ms →      982.99 ms   (+1.36%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      306.67 ms →      312.91 ms   (+2.04%) |       1   →       1              |      306.67 ms →      312.91 ms   (+2.04%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      177.79 ms →      177.49 ms   (-0.17%) |       1   →       1              |      177.79 ms →      177.49 ms   (-0.17%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      177.78 ms →      177.49 ms   (-0.17%) |       1   →       1              |      177.78 ms →      177.49 ms   (-0.17%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      110.11 ms →      117.07 ms   (+6.33%) |       1   →       1              |      110.11 ms →      117.07 ms   (+6.33%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      176.13 ms →      174.89 ms   (-0.71%) |       1   →       1              |      176.13 ms →      174.89 ms   (-0.71%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      176.13 ms →      174.88 ms   (-0.71%) |       1   →       1              |      176.13 ms →      174.88 ms   (-0.71%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      155.36 ms →      164.27 ms   (+5.74%) |       1   →       1              |      155.36 ms →      164.27 ms   (+5.74%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      105.01 ms →      113.85 ms   (+8.41%) |       1   →       1              |      105.01 ms →      113.85 ms   (+8.41%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.73 ms →        3.71 ms   (-0.72%) |       1   →       1              |        3.73 ms →        3.71 ms   (-0.72%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.24 ms →       89.78 ms   (+0.61%) |       1   →       1              |       89.24 ms →       89.78 ms   (+0.61%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.50 ms →       12.15 ms   (+5.64%) |       1   →       1              |       11.50 ms →       12.15 ms   (+5.64%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.20 ms →       64.20 ms   (-0.01%) |       2   →       2              |      128.41 ms →      128.40 ms   (-0.01%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.76 ms →      200.55 ms (+235.61%) |       2   →       2              |      119.51 ms →      401.09 ms (+235.61%) | 
  │ │ │ ├ sddk::inner                                                   |       59.62 ms                             |       2                          |      119.24 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       23.50 μs                             |       2                          |       47.00 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.57 ms                             |       4                          |      102.26 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      693.01 μs                             |       4                          |        2.77 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        7.07 ms                             |       2                          |       14.14 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                       200.44 ms            |                   2              |                       400.88 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       155.00 ns            |                   2              |                       310.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                       195.46 ms            |                   2              |                       390.92 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       771.00 ns            |                   2              |                         1.54 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.59 ms →      115.92 ms   (-0.57%) |       1   →       1              |      116.59 ms →      115.92 ms   (-0.57%) | 
  │ │ ├ sddk::transform                                                 |       36.07 ms                             |       1                          |       36.07 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.80 μs                             |       1                          |       14.80 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       19.52 μs                             |       1                          |       19.52 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        35.70 ms            |                   1              |                        35.70 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.68 ms            |                   1              |                        35.68 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      583.00 ns →      555.00 ns   (-4.80%) |       1   →       1              |      583.00 ns →      555.00 ns   (-4.80%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      147.12 s  →      129.23 s   (-12.16%) |       1   →       1              |      147.12 s  →      129.23 s   (-12.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.15 ms →        2.18 ms   (+1.13%) |      31   →      30     (-3.23%) |       66.75 ms →       65.33 ms   (-2.13%) | 
  │ ├ sirius::Density                                                   |                        70.04 ms            |                   1              |                        70.04 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         4.73 ms            |                   2              |                         9.47 ms            | 
  │ │ └ sirius::Density::update                                         |                        60.46 ms            |                   1              |                        60.46 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        60.29 ms            |                   1              |                        60.29 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                         3.18 ms            |                   1              |                         3.18 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        53.38 ms            |                   1              |                        53.38 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         2.45 ms            |                   1              |                         2.45 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.40 s  →        2.86 s   (-15.68%) |      43   →      45     (+4.65%) |      146.05 s  →      128.87 s   (-11.76%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        8.08 ms →        8.47 ms   (+4.82%) |      43   →      45     (+4.65%) |      347.60 ms →      381.29 ms   (+9.69%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        7.64 ms →        6.54 ms  (-14.43%) |      43   →      45     (+4.65%) |      328.58 ms →      294.23 ms  (-10.45%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.52 ms →        1.42 ms   (-6.16%) |      43   →      45     (+4.65%) |       65.28 ms →       64.11 ms   (-1.80%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.57 ms →        3.63 ms  (-20.50%) |      43   →      45     (+4.65%) |      196.42 ms →      163.41 ms  (-16.81%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       62.22 μs →       60.24 μs   (-3.18%) |      86   →      90     (+4.65%) |        5.35 ms →        5.42 ms   (+1.33%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      120.15 μs →      622.22 μs (+417.85%) |      43   →      45     (+4.65%) |        5.17 ms →       28.00 ms (+441.94%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |      135.36 μs →        1.13 ms (+737.60%) |      43   →      45     (+4.65%) |        5.82 ms →       51.02 ms (+776.56%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.63 s  →        1.93 s   (-26.60%) |      43   →      45     (+4.65%) |      113.24 s  →       86.99 s   (-23.18%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      272.79 μs →      212.26 μs  (-22.19%) |      43   →      45     (+4.65%) |       11.73 ms →        9.55 ms  (-18.57%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      265.83 μs →      203.21 μs  (-23.56%) |      43   →      45     (+4.65%) |       11.43 ms →        9.14 ms  (-20.00%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.21 μs →        5.05 μs   (-2.99%) |      43   →      45     (+4.65%) |      223.96 μs →      227.37 μs   (+1.53%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        1.87 s   (-28.66%) |      43   →      45     (+4.65%) |      112.57 s  →       84.04 s   (-25.34%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       69.00 ms →       56.28 ms  (-18.43%) |      43   →      45     (+4.65%) |        2.97 s  →        2.53 s   (-14.64%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.46 ms →        3.98 ms  (-27.07%) |     258   →     270     (+4.65%) |        1.41 s  →        1.08 s   (-23.68%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.36 ms →        1.64 ms  (-30.55%) |      43   →      45     (+4.65%) |      101.52 ms →       73.79 ms  (-27.32%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      424.38 μs →      427.41 μs   (+0.72%) |      43   →      45     (+4.65%) |       18.25 ms →       19.23 ms   (+5.40%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        1.22 ms →      948.45 μs  (-22.26%) |      43   →      45     (+4.65%) |       52.46 ms →       42.68 ms  (-18.64%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.52 s  →        1.79 s   (-29.21%) |      43   →      45     (+4.65%) |      108.45 s  →       80.35 s   (-25.92%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      216.34 ms →      205.05 ms   (-5.22%) |     208   →     209     (+0.48%) |       45.00 s  →       42.85 s    (-4.76%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      153.19 ms →      144.99 ms   (-5.35%) |     208   →     209     (+0.48%) |       31.86 s  →       30.30 s    (-4.90%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       28.32 ms →       26.40 ms   (-6.78%) |     208   →     209     (+0.48%) |        5.89 s  →        5.52 s    (-6.33%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      678.06 μs →      696.89 μs   (+2.78%) |     208   →     209     (+0.48%) |      141.04 ms →      145.65 ms   (+3.27%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.27 ms →        3.23 ms   (-1.27%) |      43   →      45     (+4.65%) |      140.57 ms →      145.24 ms   (+3.33%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       23.14 ms →       21.44 ms   (-7.37%) |     208   →     209     (+0.48%) |        4.81 s  →        4.48 s    (-6.93%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      669.45 μs →      681.48 μs   (+1.80%) |     208   →     209     (+0.48%) |      139.25 ms →      142.43 ms   (+2.29%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.23 ms →        3.15 ms   (-2.25%) |      43   →      45     (+4.65%) |      138.72 ms →      141.90 ms   (+2.29%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.53 ms →       32.51 ms   (-5.85%) |     208   →     209     (+0.48%) |        7.18 s  →        6.79 s    (-5.40%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.74 ms →       20.33 ms   (-6.48%) |     208   →     209     (+0.48%) |        4.52 s  →        4.25 s    (-6.03%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.64 ms   (-0.62%) |     208   →     209     (+0.48%) |      551.83 ms →      551.02 ms   (-0.15%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.00 ms →       21.54 ms   (-6.34%) |     208   →     209     (+0.48%) |        4.78 s  →        4.50 s    (-5.89%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.78 ms →        2.16 ms  (-22.36%) |     208   →     209     (+0.48%) |      578.66 ms →      451.45 ms  (-21.98%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.73 ms →       17.93 ms   (-4.32%) |     416   →     418     (+0.48%) |        7.79 s  →        7.49 s    (-3.86%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       83.59 ms →       81.28 ms   (-2.76%) |     208   →     209     (+0.48%) |       17.39 s  →       16.99 s    (-2.30%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.94 ms                             |     373                          |        4.08 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       18.76 μs                             |     373                          |        7.00 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.47 ms                             |     746                          |        3.33 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      107.01 μs                             |     746                          |       79.83 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.77 ms                             |     373                          |      661.57 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                        12.80 ms            |                 373              |                         4.78 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       256.20 ns            |                 373              |                        95.56 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         8.94 ms            |                 373              |                         3.33 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       223.09 ns            |                 373              |                        83.21 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.68 ms →       31.69 ms   (+3.29%) |     208   →     209     (+0.48%) |        6.38 s  →        6.62 s    (+3.79%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms →       15.90 ms   (-2.06%) |     208   →     209     (+0.48%) |        3.38 s  →        3.32 s    (-1.59%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.51 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.16 μs                             |     165                          |        3.33 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       53.62 μs                             |     495                          |       26.54 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        13.82 ms            |                 164              |                         2.27 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.56 ms            |                 492              |                         2.24 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       25.87 ms →       22.98 ms  (-11.16%) |     208   →     209     (+0.48%) |        5.38 s  →        4.80 s   (-10.74%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       21.65 ms                             |     208                          |        4.50 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       43.41 μs                             |     208                          |        9.03 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.91 ms                             |     416                          |        3.29 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      234.88 μs                             |     416                          |       97.71 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        5.32 ms                             |     208                          |        1.11 s                              | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        21.71 ms            |                 209              |                         4.54 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       205.31 ns            |                 209              |                        42.91 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        14.86 ms            |                 209              |                         3.10 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       395.12 ns            |                 209              |                        82.58 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      165.31 ms →       38.36 ms  (-76.79%) |     208   →     209     (+0.48%) |       34.38 s  →        8.02 s   (-76.68%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       19.50 ms →       15.84 ms  (-18.77%) |     207   →     204     (-1.45%) |        4.04 s  →        3.23 s   (-19.95%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.06 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.87 μs                             |     171                          |        2.71 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       56.93 μs                             |     342                          |       19.47 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        14.75 ms            |                 184              |                         2.71 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         6.85 ms            |                 368              |                         2.52 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.82 ms →        1.40 ms  (-50.47%) |     171   →     184     (+7.60%) |      482.29 ms →      257.04 ms  (-46.70%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.20 ms →       51.09 ms   (-0.22%) |      44   →      86    (+95.45%) |        2.25 s  →        4.39 s   (+95.03%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.79 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       13.00 μs                             |      45                          |      585.06 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       16.75 μs                             |      46                          |      770.61 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        33.63 ms            |                 127              |                         4.27 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        25.13 ms            |                 168              |                         4.22 s             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      599.74 ns →      600.04 ns   (+0.05%) |      43   →      45     (+4.65%) |       25.79 μs →       27.00 μs   (+4.70%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       48.34 μs →        3.09 ms (+6291.35%) |      43   →      45     (+4.65%) |        2.08 ms →      139.03 ms (+6588.63%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.51 ms →      193.80 ms (+5421.10%) |      43   →      45     (+4.65%) |      150.94 ms →        8.72 s  (+5677.90%) | 
  │ │ ├ sirius::Density::generate                                       |      298.56 ms →      307.04 ms   (+2.84%) |      43   →      45     (+4.65%) |       12.84 s  →       13.82 s    (+7.62%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      294.26 ms →      302.93 ms   (+2.94%) |      43   →      45     (+4.65%) |       12.65 s  →       13.63 s    (+7.73%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       68.33 ms →       67.37 ms   (-1.40%) |      43   →      45     (+4.65%) |        2.94 s  →        3.03 s    (+3.18%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.03 μs →       54.90 μs  (-11.49%) |      43   →      45     (+4.65%) |        2.67 ms →        2.47 ms   (-7.38%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.19 ms →        1.18 ms   (-0.80%) |       2   →       2              |        2.38 ms →        2.36 ms   (-0.80%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.08 ms →       56.14 ms   (-1.64%) |      43   →      45     (+4.65%) |        2.45 s  →        2.53 s    (+2.93%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.28 ms →       67.89 ms  (+10.77%) |      43   →      45     (+4.65%) |        2.64 s  →        3.05 s   (+15.93%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.62 μs →        9.10 μs   (-5.41%) |      43   →      45     (+4.65%) |      413.72 μs →      409.56 μs   (-1.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.30 ms →        2.30 ms   (-0.07%) |      43   →      45     (+4.65%) |       99.03 ms →      103.56 ms   (+4.57%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.42 ms →       57.64 ms   (-1.35%) |      43   →      45     (+4.65%) |        2.51 s  →        2.59 s    (+3.24%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.01 ms →        6.22 ms  (-11.28%) |      43   →      45     (+4.65%) |      301.48 ms →      279.91 ms   (-7.16%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      624.93 ns →      587.09 ns   (-6.06%) |      43   →      45     (+4.65%) |       26.87 μs →       26.42 μs   (-1.69%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.33 ms →      104.50 ms   (+0.16%) |      43   →      45     (+4.65%) |        4.49 s  →        4.70 s    (+4.81%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.40 ms   (-0.21%) |      43   →      45     (+4.65%) |      103.26 ms →      107.83 ms   (+4.43%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.36 ms   (+1.55%) |      43   →      45     (+4.65%) |      862.30 ms →      916.35 ms   (+6.27%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       20.19 ms   (+1.55%) |      43   →      45     (+4.65%) |      855.01 ms →      908.64 ms   (+6.27%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      303.44 ns →      337.91 ns  (+11.36%) |      43   →      45     (+4.65%) |       13.05 μs →       15.21 μs  (+16.54%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.27 ms   (+1.12%) |      43   →      45     (+4.65%) |       53.93 ms →       57.07 ms   (+5.82%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.04 ms →        2.84 ms   (-6.64%) |      43   →      45     (+4.65%) |      130.91 ms →      127.90 ms   (-2.30%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                         4.33 ms            |                 405              |                         1.75 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                         4.14 ms            |                 405              |                         1.67 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                         4.13 ms            |                 405              |                         1.67 s             | 
+ │ │ ├ sirius::Density::mix                                            |      208.05 ms →      110.71 ms  (-46.79%) |      43   →      45     (+4.65%) |        8.95 s  →        4.98 s   (-44.31%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      254.60 μs →      212.69 μs  (-16.46%) |      43   →      45     (+4.65%) |       10.95 ms →        9.57 ms  (-12.57%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |       34.86 ms →        7.24 ms  (-79.22%) |      43   →      45     (+4.65%) |        1.50 s  →      325.95 ms  (-78.25%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |       34.66 ms →        7.10 ms  (-79.53%) |      43   →      45     (+4.65%) |        1.49 s  →      319.29 ms  (-78.58%) | 
- │ │ ├ sirius::Potential::generate                                     |      195.13 ms →      211.34 ms   (+8.30%) |      43   →      45     (+4.65%) |        8.39 s  →        9.51 s   (+13.34%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       69.50 ms →       66.23 ms   (-4.71%) |      43   →      45     (+4.65%) |        2.99 s  →        2.98 s    (-0.28%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.10 ms →       10.18 ms  (+43.51%) |      43   →      45     (+4.65%) |      305.09 ms →      458.19 ms  (+50.18%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.47 ms →        4.55 ms   (+1.77%) |      43   →      45     (+4.65%) |      192.18 ms →      204.67 ms   (+6.50%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.24 ms →        4.34 ms   (+2.38%) |      43   →      45     (+4.65%) |      182.40 ms →      195.43 ms   (+7.14%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.24 ms →        4.34 ms   (+2.40%) |      43   →      45     (+4.65%) |      182.35 ms →      195.41 ms   (+7.16%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      232.54 μs →      194.68 μs  (-16.28%) |      86   →      90     (+4.65%) |       20.00 ms →       17.52 ms  (-12.39%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       99.26 ms →      119.61 ms  (+20.49%) |      43   →      45     (+4.65%) |        4.27 s  →        5.38 s   (+26.10%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       99.26 ms →      118.57 ms  (+19.45%) |      43   →      45     (+4.65%) |        4.27 s  →        5.34 s   (+25.01%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.66 ms →        1.50 ms   (-9.79%) |     215   →     360    (+67.44%) |      356.55 ms →      538.54 ms  (+51.04%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        3.15 ms →        2.60 ms  (-17.57%) |     387   →     540    (+39.53%) |        1.22 s  →        1.40 s   (+15.02%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.42 ms →        1.83 ms  (-24.56%) |      43   →      45     (+4.65%) |      104.22 ms →       82.28 ms  (-21.06%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      714.27 μs →      514.44 μs  (-27.98%) |     129   →     135     (+4.65%) |       92.14 ms →       69.45 ms  (-24.63%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.83 ms →      693.94 μs  (-75.47%) |      43   →      45     (+4.65%) |      121.66 ms →       31.23 ms  (-74.33%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.59 ms →      531.53 μs  (-79.48%) |      43   →      45     (+4.65%) |      111.38 ms →       23.92 ms  (-78.53%) | 
  │ │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                |                         9.68 ms            |                  90              |                       871.01 ms            | 
- │ │ │ │   └ sirius::divergence                                        |       22.79 ms →       19.81 ms  (-13.09%) |      43   →      90   (+109.30%) |      979.98 ms →        1.78 s   (+81.91%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.46 ms →        2.45 ms   (-0.34%) |      43   →      90   (+109.30%) |      105.75 ms →      220.59 ms (+108.59%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        4.25 ms →        3.61 ms  (-15.19%) |      43   →      45     (+4.65%) |      182.92 ms →      162.35 ms  (-11.25%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       21.09 ms →       20.93 ms   (-0.76%) |      43   →      45     (+4.65%) |      906.84 ms →      941.81 ms   (+3.86%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      189.53 ns →      353.76 ns  (+86.64%) |      43   →      45     (+4.65%) |        8.15 μs →       15.92 μs  (+95.33%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      304.37 ns →      595.24 ns  (+95.56%) |      43   →      45     (+4.65%) |       13.09 μs →       26.79 μs (+104.66%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.48 ms →        2.31 ms   (-6.76%) |      43   →      45     (+4.65%) |      106.51 ms →      103.93 ms   (-2.42%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.33 ms                             |     301                          |        1.30 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.07 ms                             |     301                          |        1.22 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.07 ms                             |     301                          |        1.22 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.06 ms →        4.21 ms   (+3.75%) |     129   →     135     (+4.65%) |      523.96 ms →      568.86 ms   (+8.57%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.87 ms →        4.05 ms   (+4.60%) |     129   →     135     (+4.65%) |      499.02 ms →      546.23 ms   (+9.46%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.05 ms →        4.15 ms   (+2.43%) |      43   →      45     (+4.65%) |      174.11 ms →      186.64 ms   (+7.20%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      304.42 μs →       13.44 ms (+4315.92%) |      43   →      45     (+4.65%) |       13.09 ms →      604.94 ms (+4521.32%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      300.62 μs →       13.44 ms (+4369.41%) |      43   →      45     (+4.65%) |       12.93 ms →      604.62 ms (+4577.29%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.69 ms →        5.49 ms  (-17.95%) |       2   →       2              |       13.38 ms →       10.98 ms  (-17.95%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.19 ms →        4.43 ms   (+5.69%) |       6   →       6              |       25.15 ms →       26.58 ms   (+5.69%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.18 ms →        4.19 ms   (+0.17%) |       6   →       6              |       25.09 ms →       25.13 ms   (+0.17%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.18 ms →        4.19 ms   (+0.17%) |       6   →       6              |       25.09 ms →       25.13 ms   (+0.17%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.06 ms →        4.16 ms   (+2.53%) |       3   →       3              |       12.18 ms →       12.49 ms   (+2.53%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.05 ms →        4.13 ms   (+1.88%) |       3   →       3              |       12.16 ms →       12.38 ms   (+1.88%) | 
  ├ sirius::Periodic_function|inner                                     |        4.15 ms →        4.20 ms   (+1.21%) |       2   →       2              |        8.30 ms →        8.40 ms   (+1.21%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.13 ms →        4.19 ms   (+1.42%) |       2   →       2              |        8.26 ms →        8.38 ms   (+1.42%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.13 ms →        4.19 ms   (+1.42%) |       2   →       2              |        8.26 ms →        8.38 ms   (+1.42%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        3.98 ms →        4.13 ms   (+3.79%) |       1   →       1              |        3.98 ms →        4.13 ms   (+3.79%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.87 ms →        4.08 ms   (+5.28%) |       1   →       1              |        3.87 ms →        4.08 ms   (+5.28%) | 
- └ sirius::finalize                                                    |      306.75 ms →      467.48 ms  (+52.40%) |       1   →       1              |      306.75 ms →      467.48 ms  (+52.40%) | 
  ====================================================================================================================================================================================================
```
