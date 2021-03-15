# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8d4c8fb637741d881d5cdc9faf167adefd93fb67
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      150.95 s  →      124.40 s   (-17.59%) |       1   →       1              |      150.95 s  →      124.40 s   (-17.59%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.72 s    (+0.30%) |       1   →       1              |        2.72 s  →        2.72 s    (+0.30%) | 
  ├ sirius::Simulation_context::initialize                              |        2.09 s  →        2.11 s    (+0.96%) |       1   →       1              |        2.09 s  →        2.11 s    (+0.96%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      787.52 μs →       44.79 ms (+5587.01%) |       1   →       1              |      787.52 μs →       44.79 ms (+5587.01%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       98.68 ms →      102.52 ms   (+3.90%) |       1   →       1              |       98.68 ms →      102.52 ms   (+3.90%) | 
  │ │ ├ sirius::Atom_type::init                                         |       75.38 ms →       75.53 ms   (+0.20%) |       1   →       1              |       75.38 ms →       75.53 ms   (+0.20%) | 
- │ │ └ sirius::Unit_cell::update                                       |       23.23 ms →       26.83 ms  (+15.50%) |       1   →       1              |       23.23 ms →       26.83 ms  (+15.50%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.13 ms →       12.05 ms  (+18.91%) |       1   →       1              |       10.13 ms →       12.05 ms  (+18.91%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       13.07 ms →       14.76 ms  (+12.87%) |       1   →       1              |       13.07 ms →       14.76 ms  (+12.87%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       12.52 ms →       14.00 ms  (+11.84%) |       1   →       1              |       12.52 ms →       14.00 ms  (+11.84%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |       12.31 ms →       13.77 ms  (+11.87%) |       1   →       1              |       12.31 ms →       13.77 ms  (+11.87%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      198.90 μs →      220.30 μs  (+10.76%) |       1   →       1              |      198.90 μs →      220.30 μs  (+10.76%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.57 μs →        2.97 μs  (+15.62%) |       1   →       1              |        2.57 μs →        2.97 μs  (+15.62%) | 
  │ └ sirius::Simulation_context::update                                |        1.93 s  →        1.91 s    (-1.32%) |       1   →       1              |        1.93 s  →        1.91 s    (-1.32%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.43 ms →       11.09 ms   (-2.97%) |       1   →       1              |       11.43 ms →       11.09 ms   (-2.97%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.26 ms →        7.91 ms   (-4.35%) |       1   →       1              |        8.26 ms →        7.91 ms   (-4.35%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.14 ms →        3.16 ms   (+0.58%) |       1   →       1              |        3.14 ms →        3.16 ms   (+0.58%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.69 ms →        2.64 ms   (-1.83%) |       1   →       1              |        2.69 ms →        2.64 ms   (-1.83%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.47 ms →        2.43 ms   (-1.55%) |       1   →       1              |        2.47 ms →        2.43 ms   (-1.55%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      216.23 μs →      204.91 μs   (-5.24%) |       1   →       1              |      216.23 μs →      204.91 μs   (-5.24%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.20 μs →        1.57 μs  (+30.87%) |       1   →       1              |        1.20 μs →        1.57 μs  (+30.87%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       17.81 ms →       17.28 ms   (-2.96%) |       2   →       2              |       35.61 ms →       34.56 ms   (-2.96%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.13 ms →        1.12 ms   (-0.78%) |       2   →       2              |        2.25 ms →        2.23 ms   (-0.78%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      954.86 μs →      956.24 μs   (+0.14%) |       1   →       1              |      954.86 μs →      956.24 μs   (+0.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.07 ms →        5.10 ms   (+0.61%) |       2   →       2              |       10.14 ms →       10.20 ms   (+0.61%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.64 ms   (+0.04%) |       2   →       2              |        7.27 ms →        7.27 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.67 ms →       15.64 ms   (-0.15%) |       4   →       4              |       62.66 ms →       62.57 ms   (-0.15%) | 
  │   ├ sddk::Gvec::init                                                |      162.53 ms →      157.61 ms   (-3.03%) |       2   →       2              |      325.07 ms →      315.23 ms   (-3.03%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.65 ms →      124.61 ms   (-3.14%) |       2   →       2              |      257.31 ms →      249.22 ms   (-3.14%) | 
- │   ├ sddk::Gvec_shells                                               |      115.92 ms →      132.65 ms  (+14.43%) |       1   →       1              |      115.92 ms →      132.65 ms  (+14.43%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.04 ms   (+0.42%) |       1   →       1              |        1.03 ms →        1.04 ms   (+0.42%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      224.97 ms →      217.81 ms   (-3.18%) |       1   →       1              |      224.97 ms →      217.81 ms   (-3.18%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       27.81 ms →       26.22 ms   (-5.72%) |       1   →       1              |       27.81 ms →       26.22 ms   (-5.72%) | 
- │ ├ sirius::K_point::K_point                                          |        2.12 μs →        5.13 μs (+141.67%) |       2   →       2              |        4.25 μs →       10.27 μs (+141.67%) | 
  │ └ sirius::K_point_set::initialize                                   |       27.78 ms →       26.17 ms   (-5.79%) |       1   →       1              |       27.78 ms →       26.17 ms   (-5.79%) | 
  │   └ sirius::K_point::initialize                                     |       27.73 ms →       26.11 ms   (-5.82%) |       1   →       1              |       27.73 ms →       26.11 ms   (-5.82%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       20.93 ms →       19.64 ms   (-6.18%) |       1   →       1              |       20.93 ms →       19.64 ms   (-6.18%) | 
  │     │ └ sddk::Gvec::init                                            |        5.40 ms →        5.01 ms   (-7.23%) |       1   →       1              |        5.40 ms →        5.01 ms   (-7.23%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.03 μs                             |       1                          |       11.03 μs                             | 
  │     └ sirius::K_point::update                                       |        4.35 ms →        4.12 ms   (-5.22%) |       1   →       1              |        4.35 ms →        4.12 ms   (-5.22%) | 
  │       └ sirius::Beta_projectors                                     |        1.67 ms →        1.70 ms   (+2.32%) |       1   →       1              |        1.67 ms →        1.70 ms   (+2.32%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      920.23 μs →      894.11 μs   (-2.84%) |       1   →       1              |      920.23 μs →      894.11 μs   (-2.84%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.20 ms                             |       2                          |        4.40 ms                             | 
  ├ sirius::Potential                                                   |       91.29 ms →       96.50 ms   (+5.71%) |       1   →       1              |       91.29 ms →       96.50 ms   (+5.71%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.41 ms                             |       6                          |       14.46 ms                             | 
  │ └ sirius::Potential::update                                         |       76.50 ms →       81.10 ms   (+6.01%) |       1   →       1              |       76.50 ms →       81.10 ms   (+6.01%) | 
  │   └ sirius::Potential::generate_local_potential                     |       76.34 ms →       80.92 ms   (+6.01%) |       1   →       1              |       76.34 ms →       80.92 ms   (+6.01%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.51 ms →       49.99 ms  (-16.01%) |       1   →       1              |       59.51 ms →       49.99 ms  (-16.01%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.64 ms →       10.32 ms  (-37.98%) |       1   →       1              |       16.64 ms →       10.32 ms  (-37.98%) | 
  ├ sirius::Density                                                     |       71.60 ms →       74.46 ms   (+4.00%) |       1   →       1              |       71.60 ms →       74.46 ms   (+4.00%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.66 ms                             |       2                          |        9.32 ms                             | 
  │ └ sirius::Density::update                                           |       62.17 ms →       64.61 ms   (+3.92%) |       1   →       1              |       62.17 ms →       64.61 ms   (+3.92%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       62.01 ms →       64.43 ms   (+3.91%) |       1   →       1              |       62.01 ms →       64.43 ms   (+3.91%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.21 ms →       51.76 ms  (-12.58%) |       1   →       1              |       59.21 ms →       51.76 ms  (-12.58%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.61 ms →        8.62 ms (+230.48%) |       1   →       1              |        2.61 ms →        8.62 ms (+230.48%) | 
  ├ sirius::Density::initial_density                                    |       79.21 ms →       80.78 ms   (+1.99%) |       1   →       1              |       79.21 ms →       80.78 ms   (+1.99%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       58.65 ms →       50.99 ms  (-13.05%) |       1   →       1              |       58.65 ms →       50.99 ms  (-13.05%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.43 ms →        6.15 ms (+152.90%) |       2   →       2              |        4.86 ms →       12.30 ms (+152.90%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.00 ms →        4.45 ms  (+11.13%) |       1   →       1              |        4.00 ms →        4.45 ms  (+11.13%) | 
- ├ sirius::Potential::generate                                         |      189.83 ms →      220.05 ms  (+15.92%) |       1   →       1              |      189.83 ms →      220.05 ms  (+15.92%) | 
  │ ├ sirius::Potential::poisson                                        |       64.62 ms →       63.92 ms   (-1.07%) |       1   →       1              |       64.62 ms →       63.92 ms   (-1.07%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        9.46 ms (+302.47%) |       1   →       1              |        2.35 ms →        9.46 ms (+302.47%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.50 ms                             |       1                          |        4.50 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.21 ms                             |       1                          |        4.21 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.21 ms                             |       1                          |        4.21 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.34 ms            |                   1              |                         4.34 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      237.71 μs →      203.39 μs  (-14.44%) |       2   →       2              |      475.42 μs →      406.78 μs  (-14.44%) | 
- │ ├ sirius::Potential::xc                                             |       98.74 ms →      127.87 ms  (+29.50%) |       1   →       1              |       98.74 ms →      127.87 ms  (+29.50%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       98.73 ms →      126.77 ms  (+28.40%) |       1   →       1              |       98.73 ms →      126.77 ms  (+28.40%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.22 ms                             |       5                          |       11.11 ms                             | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.46 ms →        2.46 ms   (-0.16%) |       9   →      12    (+33.33%) |       22.15 ms →       29.49 ms  (+33.12%) | 
  │ │   ├ sirius::gradient                                              |        7.39 ms →        7.64 ms   (+3.26%) |       1   →       1              |        7.39 ms →        7.64 ms   (+3.26%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.37 ms                             |       3                          |        7.11 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.77 ms →        2.84 ms   (+2.60%) |       1   →       1              |        2.77 ms →        2.84 ms   (+2.60%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.55 ms                             |       1                          |        2.55 ms                             | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        11.28 ms            |                   2              |                        22.57 ms            | 
- │ │   └ sirius::divergence                                            |       19.47 ms →       20.01 ms   (+2.75%) |       1   →       2   (+100.00%) |       19.47 ms →       40.02 ms (+105.51%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.38 ms                             |       1                          |        2.38 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.28 ms →        3.27 ms   (-0.26%) |       1   →       1              |        3.28 ms →        3.27 ms   (-0.26%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.19 ms →       22.70 ms   (+2.29%) |       1   →       1              |       22.19 ms →       22.70 ms   (+2.29%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      205.00 ns →      148.00 ns  (-27.80%) |       1   →       1              |      205.00 ns →      148.00 ns  (-27.80%) | 
  ├ sirius::Hamiltonian0                                                |       14.38 ms →       15.70 ms   (+9.17%) |       1   →       1              |       14.38 ms →       15.70 ms   (+9.17%) | 
  │ ├ sirius::Local_operator                                            |       14.05 ms →       13.86 ms   (-1.32%) |       1   →       1              |       14.05 ms →       13.86 ms   (-1.32%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.05 ms                             |       1                          |        7.05 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.52 ms →        5.27 ms   (-4.51%) |       1   →       1              |        5.52 ms →        5.27 ms   (-4.51%) | 
  │ ├ sirius::Non_local_operator                                        |       61.05 μs →       61.37 μs   (+0.52%) |       2   →       2              |      122.11 μs →      122.75 μs   (+0.52%) | 
- │ ├ sirius::D_operator::initialize                                    |       82.80 μs →      585.06 μs (+606.59%) |       1   →       1              |       82.80 μs →      585.06 μs (+606.59%) | 
- │ └ sirius::Q_operator::initialize                                    |       71.59 μs →        1.08 ms (+1401.66%) |       1   →       1              |       71.59 μs →        1.08 ms (+1401.66%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.19 s  →        2.25 s    (+2.76%) |       1   →       1              |        2.19 s  →        2.25 s    (+2.76%) | 
- │ ├ sirius::Hamiltonian_k                                             |        7.11 ms →        8.43 ms  (+18.52%) |       1   →       1              |        7.11 ms →        8.43 ms  (+18.52%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      242.35 μs →      265.94 μs   (+9.73%) |       1   →       1              |      242.35 μs →      265.94 μs   (+9.73%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |        6.86 ms →        8.16 ms  (+18.82%) |       1   →       1              |        6.86 ms →        8.16 ms  (+18.82%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.19 s  →        2.24 s    (+2.63%) |       1   →       1              |        2.19 s  →        2.24 s    (+2.63%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.33 ms                             |       4                          |      345.32 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.23 ms →       25.12 ms   (-0.44%) |       1   →       1              |       25.23 ms →       25.12 ms   (-0.44%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.35 ms →       14.39 ms   (+0.29%) |       1   →       1              |       14.35 ms →       14.39 ms   (+0.29%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.22 s  →        1.21 s    (-0.90%) |       1   →       1              |        1.22 s  →        1.21 s    (-0.90%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |        1.00 s  →      989.25 ms   (-1.13%) |       1   →       1              |        1.00 s  →      989.25 ms   (-1.13%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      328.57 ms →      318.03 ms   (-3.21%) |       1   →       1              |      328.57 ms →      318.03 ms   (-3.21%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      170.61 ms                             |       1                          |      170.61 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      170.60 ms                             |       1                          |      170.60 ms                             | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      139.54 ms →      122.34 ms  (-12.33%) |       1   →       1              |      139.54 ms →      122.34 ms  (-12.33%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      170.63 ms                             |       1                          |      170.63 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      170.63 ms                             |       1                          |      170.63 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      167.25 ms →      166.15 ms   (-0.66%) |       1   →       1              |      167.25 ms →      166.15 ms   (-0.66%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      116.79 ms →      115.71 ms   (-0.92%) |       1   →       1              |      116.79 ms →      115.71 ms   (-0.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.72 ms →        3.72 ms   (+0.20%) |       1   →       1              |        3.72 ms →        3.72 ms   (+0.20%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.75 ms →       90.18 ms   (+0.48%) |       1   →       1              |       89.75 ms →       90.18 ms   (+0.48%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.11 ms →       12.59 ms   (+3.91%) |       1   →       1              |       12.11 ms →       12.59 ms   (+3.91%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.31 ms →       64.25 ms   (-0.09%) |       2   →       2              |      128.63 ms →      128.51 ms   (-0.09%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.35 ms →       84.70 ms  (+42.72%) |       2   →       2              |      118.70 ms →      169.40 ms  (+42.72%) | 
  │ │ │ ├ sddk::inner                                                   |       59.24 ms                             |       2                          |      118.47 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       21.74 μs                             |       2                          |       43.48 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.19 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      696.43 μs                             |       4                          |        2.79 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        6.71 ms                             |       2                          |       13.42 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        84.59 ms            |                   2              |                       169.19 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       143.00 ns            |                   2              |                       286.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        82.84 ms            |                   2              |                       165.67 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       725.00 ns            |                   2              |                         1.45 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.37 ms →      115.12 ms   (-1.07%) |       1   →       1              |      116.37 ms →      115.12 ms   (-1.07%) | 
  │ │ ├ sddk::transform                                                 |       36.04 ms                             |       1                          |       36.04 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.58 μs                             |       1                          |       14.58 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       19.96 μs                             |       1                          |       19.96 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        36.65 ms            |                   1              |                        36.65 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.29 ms            |                   1              |                        35.29 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      595.00 ns →      492.00 ns  (-17.31%) |       1   →       1              |      595.00 ns →      492.00 ns  (-17.31%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      142.18 s  →      115.84 s   (-18.53%) |       1   →       1              |      142.18 s  →      115.84 s   (-18.53%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.11 ms                             |      31                          |       65.28 ms                             | 
  │ ├ sirius::Density                                                   |                        94.06 ms            |                   1              |                        94.06 ms            | 
  │ │ └ sirius::Density::update                                         |                        84.53 ms            |                   1              |                        84.53 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        84.36 ms            |                   1              |                        84.36 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        51.62 ms            |                   1              |                        51.62 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         8.93 ms            |                   1              |                         8.93 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.30 s  →        2.57 s   (-22.20%) |      43   →      45     (+4.65%) |      141.88 s  →      115.52 s   (-18.58%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.66 ms →        8.46 ms  (+10.34%) |      43   →      45     (+4.65%) |      329.50 ms →      380.48 ms  (+15.47%) | 
  │ │ │ ├ sirius::Local_operator                                        |        7.33 ms →        6.62 ms   (-9.61%) |      43   →      45     (+4.65%) |      315.13 ms →      298.10 ms   (-5.40%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.49 ms                             |      43                          |       63.96 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.37 ms →        3.64 ms  (-16.75%) |      43   →      45     (+4.65%) |      187.82 ms →      163.64 ms  (-12.88%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       60.62 μs →       61.39 μs   (+1.28%) |      86   →      90     (+4.65%) |        5.21 ms →        5.53 ms   (+5.99%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       81.49 μs →      581.74 μs (+613.90%) |      43   →      45     (+4.65%) |        3.50 ms →       26.18 ms (+647.10%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       71.14 μs →        1.07 ms (+1399.30%) |      43   →      45     (+4.65%) |        3.06 ms →       48.00 ms (+1469.03%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.62 s  →        1.87 s   (-28.70%) |      43   →      45     (+4.65%) |      112.80 s  →       84.17 s   (-25.38%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      216.26 μs →      219.36 μs   (+1.43%) |      43   →      45     (+4.65%) |        9.30 ms →        9.87 ms   (+6.15%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      208.84 μs →      209.77 μs   (+0.44%) |      43   →      45     (+4.65%) |        8.98 ms →        9.44 ms   (+5.11%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.50 μs →        5.16 μs   (-6.14%) |      43   →      45     (+4.65%) |      236.33 μs →      232.13 μs   (-1.78%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.61 s  →        1.83 s   (-29.63%) |      43   →      45     (+4.65%) |      112.10 s  →       82.55 s   (-26.36%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       70.13 ms                             |      43                          |        3.02 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.53 ms                             |     258                          |        1.43 s                              | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.03 ms →        1.63 ms  (-19.75%) |      43   →      45     (+4.65%) |       87.30 ms →       73.32 ms  (-16.02%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.24 μs                             |      43                          |       18.11 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      952.07 μs                             |      43                          |       40.94 ms                             | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.51 s                              |      43                          |      107.95 s                              | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                          |      216.37 ms                             |     208                          |       45.01 s                              | 
  │ │ │ │ │ │ ├ sirius::Local_operator::apply_h                         |      153.52 ms                             |     208                          |       31.93 s                              | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                   |       28.18 ms                             |     208                          |        5.86 s                              | 
  │ │ │ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      696.38 μs                             |     208                          |      144.85 ms                             | 
  │ │ │ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.36 ms                             |      43                          |      144.40 ms                             | 
  │ │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.99 ms                             |     208                          |        4.78 s                              | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                   |      691.17 μs                             |     208                          |      143.76 ms                             | 
  │ │ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.33 ms                             |      43                          |      143.21 ms                             | 
  │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                  |       34.94 ms                             |     208                          |        7.27 s                              | 
  │ │ │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi            |       22.13 ms                             |     208                          |        4.60 s                              | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms                             |     208                          |      551.81 ms                             | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                     |       22.76 ms                             |     208                          |        4.74 s                              | 
  │ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.55 ms                             |     208                          |      530.20 ms                             | 
  │ │ │ │ │ │ └ sirius::Non_local_operator::apply                       |       18.70 ms                             |     416                          |        7.78 s                              | 
  │ │ │ │ │ ├ sddk::orthogonalize                                       |       82.02 ms                             |     208                          |       17.06 s                              | 
  │ │ │ │ │ │ ├ sddk::inner                                             |       10.43 ms                             |     373                          |        3.89 s                              | 
  │ │ │ │ │ │ │ ├ sddk::inner|local                                     |       18.82 μs                             |     373                          |        7.02 ms                             | 
  │ │ │ │ │ │ │ ├ sddk::inner|device_copy                               |        4.46 ms                             |     746                          |        3.32 s                              | 
  │ │ │ │ │ │ │ ├ sddk::inner|store                                     |      102.53 μs                             |     746                          |       76.48 ms                             | 
  │ │ │ │ │ │ │ └ sddk::inner|mpi                                       |        1.29 ms                             |     373                          |      480.57 ms                             | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|tmtrx                               |       30.03 ms                             |     208                          |        6.25 s                              | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|transform                           |       16.23 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │ │ │ └ sddk::transform                                         |       21.50 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │ │ │   ├ sddk::transform|init                                  |       20.65 μs                             |     165                          |        3.41 ms                             | 
  │ │ │ │ │ │   └ sddk::transform|local                                 |       51.06 μs                             |     495                          |       25.27 ms                             | 
  │ │ │ │ │ ├ sirius::Band::set_subspace_mtrx                           |       25.10 ms                             |     208                          |        5.22 s                              | 
  │ │ │ │ │ │ └ sddk::inner                                             |       20.94 ms                             |     208                          |        4.36 s                              | 
  │ │ │ │ │ │   ├ sddk::inner|local                                     |       44.22 μs                             |     208                          |        9.20 ms                             | 
  │ │ │ │ │ │   ├ sddk::inner|device_copy                               |        7.92 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │ │ │   ├ sddk::inner|store                                     |      236.34 μs                             |     416                          |       98.32 ms                             | 
  │ │ │ │ │ │   └ sddk::inner|mpi                                       |        4.57 ms                             |     208                          |      951.07 ms                             | 
  │ │ │ │ │ ├ Eigensolver_cuda|zheevdx                                  |      164.82 ms                             |     208                          |       34.28 s                              | 
  │ │ │ │ │ ├ sirius::residuals                                         |       19.87 ms                             |     207                          |        4.11 s                              | 
  │ │ │ │ │ │ ├ sddk::transform                                         |       20.06 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │ │ │ │ ├ sddk::transform|init                                  |       15.80 μs                             |     171                          |        2.70 ms                             | 
  │ │ │ │ │ │ │ └ sddk::transform|local                                 |       55.16 μs                             |     342                          |       18.87 ms                             | 
  │ │ │ │ │ │ └ sirius::normalized_preconditioned_residuals             |        3.26 ms                             |     171                          |      556.89 ms                             | 
  │ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.18 ms                             |      44                          |        2.25 s                              | 
  │ │ │ │ │   └ sddk::transform                                         |       49.75 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │ │     ├ sddk::transform|init                                  |       13.92 μs                             |      45                          |      626.29 μs                             | 
  │ │ │ │ │     └ sddk::transform|local                                 |       16.92 μs                             |      46                          |      778.36 μs                             | 
  │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                            |                       206.23 ms            |                 209              |                        43.10 s             | 
  │ │ │ │ │ ├ sirius::Local_operator::apply_h                           |                       145.92 ms            |                 209              |                        30.50 s             | 
  │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                     |                        26.77 ms            |                 209              |                         5.60 s             | 
  │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi               |                        21.83 ms            |                 209              |                         4.56 s             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                    |                        33.05 ms            |                 209              |                         6.91 s             | 
  │ │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi              |                        20.91 ms            |                 209              |                         4.37 s             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |                         2.63 ms            |                 209              |                       550.71 ms            | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |                        21.76 ms            |                 209              |                         4.55 s             | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |                         2.38 ms            |                 209              |                       498.11 ms            | 
  │ │ │ │ │ └ sirius::Non_local_operator::apply                         |                        17.95 ms            |                 418              |                         7.50 s             | 
  │ │ │ │ ├ sddk::orthogonalize                                         |                        75.19 ms            |                 209              |                        15.71 s             | 
  │ │ │ │ │ ├ sddk::wf_inner                                            |                        12.04 ms            |                 373              |                         4.49 s             | 
  │ │ │ │ │ │ ├ sddk::wf_inner|scale                                    |                       188.17 ns            |                 373              |                        70.19 μs            | 
  │ │ │ │ │ │ ├ sddk::wf_inner|pw                                       |                         8.61 ms            |                 373              |                         3.21 s             | 
  │ │ │ │ │ │ └ sddk::wf_inner|scale_back                               |                       298.79 ns            |                 373              |                       111.45 μs            | 
  │ │ │ │ │ ├ sddk::orthogonalize|tmtrx                                 |                        27.03 ms            |                 209              |                         5.65 s             | 
  │ │ │ │ │ ├ sddk::orthogonalize|transform                             |                        15.89 ms            |                 209              |                         3.32 s             | 
  │ │ │ │ │ └ sddk::wf_trans                                            |                        13.73 ms            |                 164              |                         2.25 s             | 
  │ │ │ │ │   └ sddk::wf_trans|pw                                       |                         4.56 ms            |                 492              |                         2.24 s             | 
  │ │ │ │ ├ sirius::Band::set_subspace_mtrx                             |                        21.78 ms            |                 209              |                         4.55 s             | 
  │ │ │ │ │ └ sddk::wf_inner                                            |                        20.84 ms            |                 209              |                         4.36 s             | 
  │ │ │ │ │   ├ sddk::wf_inner|scale                                    |                       181.06 ns            |                 209              |                        37.84 μs            | 
  │ │ │ │ │   ├ sddk::wf_inner|pw                                       |                        14.76 ms            |                 209              |                         3.09 s             | 
  │ │ │ │ │   └ sddk::wf_inner|scale_back                               |                       373.61 ns            |                 209              |                        78.08 μs            | 
  │ │ │ │ ├ Eigensolver_cuda|zheevdx                                    |                        38.15 ms            |                 209              |                         7.97 s             | 
  │ │ │ │ ├ sirius::residuals                                           |                        15.41 ms            |                 204              |                         3.14 s             | 
  │ │ │ │ │ ├ sddk::wf_trans                                            |                        14.45 ms            |                 184              |                         2.66 s             | 
  │ │ │ │ │ │ └ sddk::wf_trans|pw                                       |                         6.85 ms            |                 368              |                         2.52 s             | 
  │ │ │ │ │ └ sirius::normalized_preconditioned_residuals               |                         1.39 ms            |                 184              |                       256.29 ms            | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi     |                        50.51 ms            |                  86              |                         4.34 s             | 
  │ │ │ │   └ sddk::wf_trans                                            |                        33.34 ms            |                 127              |                         4.23 s             | 
  │ │ │ │     └ sddk::wf_trans|pw                                       |                        25.11 ms            |                 168              |                         4.22 s             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      592.37 ns →      569.80 ns   (-3.81%) |      43   →      45     (+4.65%) |       25.47 μs →       25.64 μs   (+0.66%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       22.78 μs                             |      43                          |      979.35 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        94.15 μs            |                  45              |                         4.24 ms            | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.40 ms →      961.49 μs  (-71.75%) |      43   →      45     (+4.65%) |      146.35 ms →       43.27 ms  (-70.44%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        22.44 μs            |                  45              |                         1.01 ms            | 
  │ │ ├ sirius::Density::generate                                       |      297.74 ms →      298.23 ms   (+0.17%) |      43   →      45     (+4.65%) |       12.80 s  →       13.42 s    (+4.82%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      293.81 ms →      294.31 ms   (+0.17%) |      43   →      45     (+4.65%) |       12.63 s  →       13.24 s    (+4.83%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.52 ms →       67.39 ms   (-3.06%) |      43   →      45     (+4.65%) |        2.99 s  →        3.03 s    (+1.45%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       64.82 μs                             |      43                          |        2.79 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.24 ms                             |       2                          |        2.47 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       58.29 ms →       56.18 ms   (-3.63%) |      43   →      45     (+4.65%) |        2.51 s  →        2.53 s    (+0.86%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.69 ms →       61.07 ms   (+0.61%) |      43   →      45     (+4.65%) |        2.61 s  →        2.75 s    (+5.29%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.65 μs →        9.06 μs   (-6.08%) |      43   →      45     (+4.65%) |      414.76 μs →      407.65 μs   (-1.72%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.30 ms   (-0.20%) |      43   →      45     (+4.65%) |       99.20 ms →      103.61 ms   (+4.44%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       57.84 ms →       58.15 ms   (+0.54%) |      43   →      45     (+4.65%) |        2.49 s  →        2.62 s    (+5.22%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.42 ms →        6.77 ms   (+5.39%) |      43   →      45     (+4.65%) |      276.10 ms →      304.51 ms  (+10.29%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      602.98 ns →      535.53 ns  (-11.19%) |      43   →      45     (+4.65%) |       25.93 μs →       24.10 μs   (-7.05%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.66 ms →      104.76 ms   (+0.10%) |      43   →      45     (+4.65%) |        4.50 s  →        4.71 s    (+4.76%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.41 ms →        2.40 ms   (-0.58%) |      43   →      45     (+4.65%) |      103.73 ms →      107.93 ms   (+4.05%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms →       20.33 ms   (+1.36%) |      43   →      45     (+4.65%) |      862.38 ms →      914.79 ms   (+6.08%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       20.15 ms   (+1.36%) |      43   →      45     (+4.65%) |      855.04 ms →      906.95 ms   (+6.07%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      248.53 ns →      357.78 ns  (+43.95%) |      43   →      45     (+4.65%) |       10.69 μs →       16.10 μs  (+50.65%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.26 ms   (+0.97%) |      43   →      45     (+4.65%) |       53.81 ms →       56.86 ms   (+5.66%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.67 ms →        2.65 ms   (-0.57%) |      43   →      45     (+4.65%) |      114.70 ms →      119.35 ms   (+4.05%) | 
  │ │ ├ sirius::inner                                                   |                         4.40 ms            |                 540              |                         2.38 s             | 
+ │ │ ├ sirius::Density::mix                                            |      133.16 ms →      102.97 ms  (-22.67%) |      43   →      45     (+4.65%) |        5.73 s  →        4.63 s   (-19.07%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      263.79 μs →      212.34 μs  (-19.51%) |      43   →      45     (+4.65%) |       11.34 ms →        9.56 ms  (-15.76%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.64 ms →        2.63 ms  (-27.88%) |      43   →      45     (+4.65%) |      156.60 ms →      118.19 ms  (-24.53%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.45 ms →        2.48 ms  (-28.09%) |      43   →      45     (+4.65%) |      148.42 ms →      111.69 ms  (-24.75%) | 
- │ │ ├ sirius::Potential::generate                                     |      185.65 ms →      212.67 ms  (+14.55%) |      43   →      45     (+4.65%) |        7.98 s  →        9.57 s   (+19.88%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.76 ms →       64.11 ms   (-1.01%) |      43   →      45     (+4.65%) |        2.78 s  →        2.88 s    (+3.59%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.41 ms →        9.47 ms (+293.77%) |      43   →      45     (+4.65%) |      103.43 ms →      426.21 ms (+312.08%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |        4.39 ms                             |      43                          |      188.76 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |        4.25 ms                             |      43                          |      182.77 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |        4.25 ms                             |      43                          |      182.73 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                         4.43 ms            |                  45              |                       199.22 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      229.84 μs →      201.52 μs  (-12.32%) |      86   →      90     (+4.65%) |       19.77 ms →       18.14 ms   (-8.24%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       95.18 ms →      122.10 ms  (+28.28%) |      43   →      45     (+4.65%) |        4.09 s  →        5.49 s   (+34.25%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       95.18 ms →      121.06 ms  (+27.19%) |      43   →      45     (+4.65%) |        4.09 s  →        5.45 s   (+33.11%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.63 ms                             |     215                          |      349.79 ms                             | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.71 ms →        2.52 ms   (-7.19%) |     387   →     540    (+39.53%) |        1.05 s  →        1.36 s   (+29.50%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.36 ms →        1.86 ms  (-21.25%) |      43   →      45     (+4.65%) |      101.69 ms →       83.80 ms  (-17.59%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      695.55 μs                             |     129                          |       89.73 ms                             | 
+ │ │ │ │   ├ sirius::dot                                               |        2.80 ms →      697.06 μs  (-75.11%) |      43   →      45     (+4.65%) |      120.41 ms →       31.37 ms  (-73.95%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.56 ms                             |      43                          |      110.22 ms                             | 
  │ │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        11.28 ms            |                  90              |                         1.02 s             | 
- │ │ │ │   └ sirius::divergence                                        |       19.68 ms →       20.00 ms   (+1.62%) |      43   →      90   (+109.30%) |      846.22 ms →        1.80 s  (+112.69%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.42 ms                             |      43                          |      103.92 ms                             | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.78 ms →        3.40 ms  (-10.07%) |      43   →      45     (+4.65%) |      162.56 ms →      152.98 ms   (-5.89%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.92 ms →       20.91 ms   (-0.03%) |      43   →      45     (+4.65%) |      899.50 ms →      941.07 ms   (+4.62%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      177.00 ns →      165.42 ns   (-6.54%) |      43   →      45     (+4.65%) |        7.61 μs →        7.44 μs   (-2.19%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      264.84 ns →      356.67 ns  (+34.67%) |      43   →      45     (+4.65%) |       11.39 μs →       16.05 μs  (+40.94%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.24 ms →        2.24 ms   (+0.05%) |      43   →      45     (+4.65%) |       96.30 ms →      100.83 ms   (+4.71%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.23 ms                             |     301                          |        1.27 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.10 ms                             |     301                          |        1.24 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.10 ms                             |     301                          |        1.24 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.20 ms                             |     129                          |      541.77 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.09 ms                             |     129                          |      527.70 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.02 ms →        4.17 ms   (+3.72%) |      43   →      45     (+4.65%) |      172.67 ms →      187.43 ms   (+8.55%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      101.40 μs →       12.36 ms (+12092.66%) |      43   →      45     (+4.65%) |        4.36 ms →      556.35 ms (+12659.76%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       98.04 μs →       12.36 ms (+12503.56%) |      43   →      45     (+4.65%) |        4.22 ms →      556.05 ms (+13089.77%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.56 ms →        5.28 ms  (-19.47%) |       2   →       2              |       13.11 ms →       10.56 ms  (-19.47%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.53 ms                             |       6                          |       27.19 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.14 ms                             |       6                          |       24.84 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.14 ms                             |       6                          |       24.84 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |        4.34 ms                             |       3                          |       13.02 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        3.93 ms                             |       3                          |       11.80 ms                             | 
  │ └ sirius::inner                                                     |                         4.33 ms            |                   9              |                        38.95 ms            | 
  ├ sirius::Periodic_function|inner                                     |        4.53 ms                             |       2                          |        9.05 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.10 ms                             |       2                          |        8.20 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.10 ms                             |       2                          |        8.20 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.34 ms                             |       1                          |        4.34 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.91 ms                             |       1                          |        3.91 ms                             | 
  ├ sirius::inner                                                       |                         4.45 ms            |                   3              |                        13.36 ms            | 
+ └ sirius::finalize                                                    |      395.48 ms →      334.33 ms  (-15.46%) |       1   →       1              |      395.48 ms →      334.33 ms  (-15.46%) | 
  ====================================================================================================================================================================================================
```
