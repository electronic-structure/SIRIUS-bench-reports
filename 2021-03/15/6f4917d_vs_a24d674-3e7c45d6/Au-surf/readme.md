# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 6f4917d65584ba2b52ea522b0bd003886a7daddd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      151.18 s  →      124.15 s   (-17.88%) |       1   →       1              |      151.18 s  →      124.15 s   (-17.88%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.78 s    (+2.58%) |       1   →       1              |        2.71 s  →        2.78 s    (+2.58%) | 
+ ├ sirius::Simulation_context::initialize                              |        3.09 s  →        2.01 s   (-35.00%) |       1   →       1              |        3.09 s  →        2.01 s   (-35.00%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       41.04 ms →      244.53 μs  (-99.40%) |       1   →       1              |       41.04 ms →      244.53 μs  (-99.40%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.12 s  →       77.86 ms  (-93.02%) |       1   →       1              |        1.12 s  →       77.86 ms  (-93.02%) | 
+ │ │ ├ sirius::Atom_type::init                                         |        1.10 s  →       54.01 ms  (-95.09%) |       1   →       1              |        1.10 s  →       54.01 ms  (-95.09%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.11 ms →       23.69 ms  (+56.74%) |       1   →       1              |       15.11 ms →       23.69 ms  (+56.74%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        9.20 ms →       10.52 ms  (+14.37%) |       1   →       1              |        9.20 ms →       10.52 ms  (+14.37%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |        5.89 ms →       13.14 ms (+123.26%) |       1   →       1              |        5.89 ms →       13.14 ms (+123.26%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |        5.57 ms →       12.45 ms (+123.33%) |       1   →       1              |        5.57 ms →       12.45 ms (+123.33%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.36 ms →       12.24 ms (+128.46%) |       1   →       1              |        5.36 ms →       12.24 ms (+128.46%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      203.59 μs →      199.94 μs   (-1.79%) |       1   →       1              |      203.59 μs →      199.94 μs   (-1.79%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.56 μs →        2.34 μs   (-8.48%) |       1   →       1              |        2.56 μs →        2.34 μs   (-8.48%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.88 s    (-0.19%) |       1   →       1              |        1.89 s  →        1.88 s    (-0.19%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.30 ms →       11.59 ms   (+2.60%) |       1   →       1              |       11.30 ms →       11.59 ms   (+2.60%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.30 ms →        8.42 ms   (+1.39%) |       1   →       1              |        8.30 ms →        8.42 ms   (+1.39%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        2.98 ms →        3.16 ms   (+5.93%) |       1   →       1              |        2.98 ms →        3.16 ms   (+5.93%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.69 ms →        2.63 ms   (-1.93%) |       1   →       1              |        2.69 ms →        2.63 ms   (-1.93%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.47 ms →        2.42 ms   (-2.07%) |       1   →       1              |        2.47 ms →        2.42 ms   (-2.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      216.61 μs →      215.67 μs   (-0.43%) |       1   →       1              |      216.61 μs →      215.67 μs   (-0.43%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.04 μs →        1.06 μs   (+2.70%) |       1   →       1              |        1.04 μs →        1.06 μs   (+2.70%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       17.48 ms →       18.12 ms   (+3.69%) |       2   →       2              |       34.95 ms →       36.24 ms   (+3.69%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.09 ms   (-0.39%) |       2   →       2              |        2.19 ms →        2.18 ms   (-0.39%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      969.70 μs →      956.16 μs   (-1.40%) |       1   →       1              |      969.70 μs →      956.16 μs   (-1.40%) | 
- │   ├ sirius::Radial_integrals|vloc                                   |        4.55 ms →        5.07 ms  (+11.27%) |       2   →       2              |        9.11 ms →       10.13 ms  (+11.27%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.63 ms →        3.63 ms   (-0.04%) |       2   →       2              |        7.27 ms →        7.26 ms   (-0.04%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.28 ms →       15.70 ms   (+2.79%) |       4   →       4              |       61.11 ms →       62.82 ms   (+2.79%) | 
  │   ├ sddk::Gvec::init                                                |      158.66 ms →      156.66 ms   (-1.26%) |       2   →       2              |      317.32 ms →      313.31 ms   (-1.26%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      125.28 ms →      124.33 ms   (-0.76%) |       2   →       2              |      250.57 ms →      248.67 ms   (-0.76%) | 
  │   ├ sddk::Gvec_shells                                               |      126.48 ms →      125.56 ms   (-0.73%) |       1   →       1              |      126.48 ms →      125.56 ms   (-0.73%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.02 ms   (-1.58%) |       1   →       1              |        1.04 ms →        1.02 ms   (-1.58%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      219.29 ms →      217.70 ms   (-0.73%) |       1   →       1              |      219.29 ms →      217.70 ms   (-0.73%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       27.89 ms →       25.79 ms   (-7.54%) |       1   →       1              |       27.89 ms →       25.79 ms   (-7.54%) | 
- │ ├ sirius::K_point::K_point                                          |        1.99 μs →        5.16 μs (+159.63%) |       2   →       2              |        3.98 μs →       10.32 μs (+159.63%) | 
  │ └ sirius::K_point_set::initialize                                   |       27.86 ms →       25.75 ms   (-7.61%) |       1   →       1              |       27.86 ms →       25.75 ms   (-7.61%) | 
  │   └ sirius::K_point::initialize                                     |       27.81 ms →       25.69 ms   (-7.61%) |       1   →       1              |       27.81 ms →       25.69 ms   (-7.61%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       20.99 ms →       19.35 ms   (-7.80%) |       1   →       1              |       20.99 ms →       19.35 ms   (-7.80%) | 
+ │     │ └ sddk::Gvec::init                                            |        5.51 ms →        4.69 ms  (-14.84%) |       1   →       1              |        5.51 ms →        4.69 ms  (-14.84%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.38 μs                             |       1                          |        9.38 μs                             | 
  │     └ sirius::K_point::update                                       |        4.34 ms →        3.98 ms   (-8.32%) |       1   →       1              |        4.34 ms →        3.98 ms   (-8.32%) | 
  │       └ sirius::Beta_projectors                                     |        1.70 ms →        1.71 ms   (+0.19%) |       1   →       1              |        1.70 ms →        1.71 ms   (+0.19%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      915.80 μs →      899.11 μs   (-1.82%) |       1   →       1              |      915.80 μs →      899.11 μs   (-1.82%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.23 ms                             |       2                          |        4.45 ms                             | 
  ├ sirius::Potential                                                   |       89.86 ms →       98.13 ms   (+9.20%) |       1   →       1              |       89.86 ms →       98.13 ms   (+9.20%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms                             |       6                          |       14.79 ms                             | 
- │ └ sirius::Potential::update                                         |       74.75 ms →       83.31 ms  (+11.45%) |       1   →       1              |       74.75 ms →       83.31 ms  (+11.45%) | 
- │   └ sirius::Potential::generate_local_potential                     |       74.58 ms →       83.14 ms  (+11.48%) |       1   →       1              |       74.58 ms →       83.14 ms  (+11.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       54.13 ms →       48.82 ms   (-9.81%) |       1   →       1              |       54.13 ms →       48.82 ms   (-9.81%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       20.26 ms →       11.79 ms  (-41.80%) |       1   →       1              |       20.26 ms →       11.79 ms  (-41.80%) | 
  ├ sirius::Density                                                     |       71.86 ms →       74.78 ms   (+4.06%) |       1   →       1              |       71.86 ms →       74.78 ms   (+4.06%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.76 ms                             |       2                          |        9.52 ms                             | 
  │ └ sirius::Density::update                                           |       62.23 ms →       65.23 ms   (+4.82%) |       1   →       1              |       62.23 ms →       65.23 ms   (+4.82%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       62.06 ms →       65.07 ms   (+4.84%) |       1   →       1              |       62.06 ms →       65.07 ms   (+4.84%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.81 ms →       52.35 ms   (-2.71%) |       1   →       1              |       53.81 ms →       52.35 ms   (-2.71%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        8.05 ms →        8.00 ms   (-0.71%) |       1   →       1              |        8.05 ms →        8.00 ms   (-0.71%) | 
  ├ sirius::Density::initial_density                                    |       80.20 ms →       79.72 ms   (-0.60%) |       1   →       1              |       80.20 ms →       79.72 ms   (-0.60%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.11 ms →       51.67 ms   (-2.72%) |       1   →       1              |       53.11 ms →       51.67 ms   (-2.72%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.31 ms →        5.77 ms   (+8.68%) |       2   →       2              |       10.62 ms →       11.55 ms   (+8.68%) | 
+ │ └ sirius::Periodic_function::integrate                              |        4.87 ms →        3.92 ms  (-19.51%) |       1   →       1              |        4.87 ms →        3.92 ms  (-19.51%) | 
- ├ sirius::Potential::generate                                         |      190.18 ms →      218.67 ms  (+14.98%) |       1   →       1              |      190.18 ms →      218.67 ms  (+14.98%) | 
  │ ├ sirius::Potential::poisson                                        |       64.34 ms →       63.94 ms   (-0.63%) |       1   →       1              |       64.34 ms →       63.94 ms   (-0.63%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.51 ms →        9.99 ms  (+17.47%) |       1   →       1              |        8.51 ms →        9.99 ms  (+17.47%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.35 ms                             |       1                          |        4.35 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.04 ms                             |       1                          |        4.04 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.04 ms                             |       1                          |        4.04 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.45 ms            |                   1              |                         4.45 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      232.68 μs →      196.44 μs  (-15.57%) |       2   →       2              |      465.35 μs →      392.89 μs  (-15.57%) | 
- │ ├ sirius::Potential::xc                                             |       99.30 ms →      126.50 ms  (+27.39%) |       1   →       1              |       99.30 ms →      126.50 ms  (+27.39%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       99.30 ms →      125.49 ms  (+26.38%) |       1   →       1              |       99.30 ms →      125.49 ms  (+26.38%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.26 ms                             |       5                          |       11.32 ms                             | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.41 ms →        2.43 ms   (+0.93%) |       9   →      12    (+33.33%) |       21.70 ms →       29.20 ms  (+34.57%) | 
  │ │   ├ sirius::gradient                                              |        7.62 ms →        7.44 ms   (-2.37%) |       1   →       1              |        7.62 ms →        7.44 ms   (-2.37%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.45 ms                             |       3                          |        7.35 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.79 ms →        2.75 ms   (-1.66%) |       1   →       1              |        2.79 ms →        2.75 ms   (-1.66%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.56 ms                             |       1                          |        2.56 ms                             | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        11.27 ms            |                   2              |                        22.54 ms            | 
- │ │   └ sirius::divergence                                            |       19.74 ms →       19.73 ms   (-0.06%) |       1   →       2   (+100.00%) |       19.74 ms →       39.45 ms  (+99.89%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.45 ms                             |       1                          |        2.45 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.31 ms →        3.32 ms   (+0.14%) |       1   →       1              |        3.31 ms →        3.32 ms   (+0.14%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.20 ms →       22.68 ms   (+2.17%) |       1   →       1              |       22.20 ms →       22.68 ms   (+2.17%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      140.00 ns →      167.00 ns  (+19.29%) |       1   →       1              |      140.00 ns →      167.00 ns  (+19.29%) | 
- ├ sirius::Hamiltonian0                                                |       13.78 ms →       15.24 ms  (+10.63%) |       1   →       1              |       13.78 ms →       15.24 ms  (+10.63%) | 
  │ ├ sirius::Local_operator                                            |       13.44 ms →       13.41 ms   (-0.26%) |       1   →       1              |       13.44 ms →       13.41 ms   (-0.26%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.09 ms                             |       1                          |        7.09 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.90 ms →        4.88 ms   (-0.45%) |       1   →       1              |        4.90 ms →        4.88 ms   (-0.45%) | 
  │ ├ sirius::Non_local_operator                                        |       59.93 μs →       58.60 μs   (-2.21%) |       2   →       2              |      119.85 μs →      117.21 μs   (-2.21%) | 
- │ ├ sirius::D_operator::initialize                                    |       85.30 μs →      585.46 μs (+586.37%) |       1   →       1              |       85.30 μs →      585.46 μs (+586.37%) | 
- │ └ sirius::Q_operator::initialize                                    |       69.14 μs →        1.07 ms (+1449.69%) |       1   →       1              |       69.14 μs →        1.07 ms (+1449.69%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.18 s  →        2.23 s    (+2.26%) |       1   →       1              |        2.18 s  →        2.23 s    (+2.26%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.42 ms →        8.43 ms   (+0.10%) |       1   →       1              |        8.42 ms →        8.43 ms   (+0.10%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      257.26 μs →      263.05 μs   (+2.25%) |       1   →       1              |      257.26 μs →      263.05 μs   (+2.25%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.16 ms   (+0.00%) |       1   →       1              |        8.16 ms →        8.16 ms   (+0.00%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.18 s  →        2.22 s    (+2.18%) |       1   →       1              |        2.18 s  →        2.22 s    (+2.18%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.30 ms                             |       4                          |      345.21 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.00 ms →       25.11 ms   (+0.41%) |       1   →       1              |       25.00 ms →       25.11 ms   (+0.41%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.42 ms →       14.38 ms   (-0.23%) |       1   →       1              |       14.42 ms →       14.38 ms   (-0.23%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.20 s    (-0.73%) |       1   →       1              |        1.21 s  →        1.20 s    (-0.73%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      985.54 ms →      977.03 ms   (-0.86%) |       1   →       1              |      985.54 ms →      977.03 ms   (-0.86%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      302.32 ms →      308.26 ms   (+1.97%) |       1   →       1              |      302.32 ms →      308.26 ms   (+1.97%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      171.97 ms                             |       1                          |      171.97 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      171.96 ms                             |       1                          |      171.96 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      111.78 ms →      118.66 ms   (+6.16%) |       1   →       1              |      111.78 ms →      118.66 ms   (+6.16%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      173.41 ms                             |       1                          |      173.41 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      173.40 ms                             |       1                          |      173.40 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      177.15 ms →      164.96 ms   (-6.88%) |       1   →       1              |      177.15 ms →      164.96 ms   (-6.88%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      126.53 ms →      114.45 ms   (-9.54%) |       1   →       1              |      126.53 ms →      114.45 ms   (-9.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.74 ms →        3.73 ms   (-0.31%) |       1   →       1              |        3.74 ms →        3.73 ms   (-0.31%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.22 ms →       88.93 ms   (-0.32%) |       1   →       1              |       89.22 ms →       88.93 ms   (-0.32%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.62 ms →       11.24 ms   (-3.27%) |       1   →       1              |       11.62 ms →       11.24 ms   (-3.27%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.22 ms →       64.20 ms   (-0.03%) |       2   →       2              |      128.44 ms →      128.40 ms   (-0.03%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.17 ms →       82.91 ms  (+40.12%) |       2   →       2              |      118.33 ms →      165.81 ms  (+40.12%) | 
  │ │ │ ├ sddk::inner                                                   |       59.05 ms                             |       2                          |      118.11 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       21.15 μs                             |       2                          |       42.30 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.56 ms                             |       4                          |      102.23 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      689.28 μs                             |       4                          |        2.76 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        6.53 ms                             |       2                          |       13.06 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        82.80 ms            |                   2              |                       165.60 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       170.50 ns            |                   2              |                       341.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        81.24 ms            |                   2              |                       162.49 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       788.50 ns            |                   2              |                         1.58 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      115.93 ms →      116.74 ms   (+0.69%) |       1   →       1              |      115.93 ms →      116.74 ms   (+0.69%) | 
  │ │ ├ sddk::transform                                                 |       36.02 ms                             |       1                          |       36.02 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.97 μs                             |       1                          |       14.97 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.92 μs                             |       1                          |       18.92 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        35.30 ms            |                   1              |                        35.30 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.28 ms            |                   1              |                        35.28 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      436.00 ns →      677.00 ns  (+55.28%) |       1   →       1              |      436.00 ns →      677.00 ns  (+55.28%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      141.43 s  →      115.66 s   (-18.22%) |       1   →       1              |      141.43 s  →      115.66 s   (-18.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms                             |      31                          |       67.20 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.28 s                              |      43                          |      141.22 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.04 ms                             |      43                          |      302.84 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        6.71 ms                             |      43                          |      288.39 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.49 ms                             |      43                          |       64.04 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.76 ms                             |      43                          |      161.48 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.17 μs                             |      86                          |        5.26 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       83.31 μs                             |      43                          |        3.58 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       70.23 μs                             |      43                          |        3.02 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.61 s                              |      43                          |      112.44 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      226.75 μs                             |      43                          |        9.75 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      220.04 μs                             |      43                          |        9.46 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.14 μs                             |      43                          |      220.91 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.60 s                              |      43                          |      111.73 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       70.23 ms                             |      43                          |        3.02 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.70 ms                             |     258                          |        1.47 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.07 ms                             |      43                          |       88.94 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.32 μs                             |      43                          |       18.12 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      955.43 μs                             |      43                          |       41.08 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.50 s                              |      43                          |      107.58 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.73 ms                             |     208                          |       44.66 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.98 ms                             |     208                          |       31.61 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.43 ms                             |     208                          |        5.70 s                              | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      687.37 μs                             |     208                          |      142.97 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.32 ms                             |      43                          |      142.55 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.26 ms                             |     208                          |        4.63 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      680.78 μs                             |     208                          |      141.60 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.28 ms                             |      43                          |      141.06 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.31 ms                             |     208                          |        7.14 s                              | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.53 ms                             |     208                          |        4.48 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.66 ms                             |     208                          |      552.36 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.43 ms                             |     208                          |        4.67 s                              | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.21 ms                             |     208                          |      458.94 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.82 ms                             |     416                          |        7.83 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       82.37 ms                             |     208                          |       17.13 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.35 ms                             |     373                          |        3.86 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       18.43 μs                             |     373                          |        6.87 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.49 ms                             |     746                          |        3.35 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      101.08 μs                             |     746                          |       75.41 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.14 ms                             |     373                          |      426.47 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.47 ms                             |     208                          |        6.34 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       21.56 ms                             |     165                          |        3.56 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.15 μs                             |     165                          |        3.16 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       49.80 μs                             |     495                          |       24.65 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       24.74 ms                             |     208                          |        5.15 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |       20.54 ms                             |     208                          |        4.27 s                              | 
  │ │ │ │   │   ├ sddk::inner|local                                     |       42.28 μs                             |     208                          |        8.79 ms                             | 
  │ │ │ │   │   ├ sddk::inner|device_copy                               |        7.93 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │   ├ sddk::inner|store                                     |      229.49 μs                             |     416                          |       95.47 ms                             | 
  │ │ │ │   │   └ sddk::inner|mpi                                       |        4.18 ms                             |     208                          |      869.39 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      164.83 ms                             |     208                          |       34.29 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       19.73 ms                             |     207                          |        4.08 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.06 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.61 μs                             |     171                          |        2.67 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       54.78 μs                             |     342                          |       18.73 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        3.09 ms                             |     171                          |      528.61 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.24 ms                             |      44                          |        2.25 s                              | 
  │ │ │ │     └ sddk::transform                                         |       49.83 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       12.26 μs                             |      45                          |      551.86 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       16.64 μs                             |      46                          |      765.50 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      577.53 ns                             |      43                          |       24.83 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.40 μs                             |      43                          |        1.01 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.46 ms                             |      43                          |      148.67 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      293.87 ms                             |      43                          |       12.64 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      289.93 ms                             |      43                          |       12.47 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.02 ms                             |      43                          |        2.88 s                              | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.20 μs                             |      43                          |        2.67 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms                             |       2                          |        2.34 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.76 ms                             |      43                          |        2.40 s                              | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       59.85 ms                             |      43                          |        2.57 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.51 μs                             |      43                          |      408.83 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.30 ms                             |      43                          |       99.11 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       56.99 ms                             |      43                          |        2.45 s                              | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.53 ms                             |      43                          |      237.88 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      526.84 ns                             |      43                          |       22.65 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.30 ms                             |      43                          |        4.48 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.39 ms                             |      43                          |      102.64 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.07 ms                             |      43                          |      863.05 ms                             | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms                             |      43                          |      855.81 ms                             | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      272.93 ns                             |      43                          |       11.74 μs                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms                             |      43                          |       53.95 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.69 ms                             |      43                          |      115.51 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      131.63 ms                             |      43                          |        5.66 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      261.45 μs                             |      43                          |       11.24 ms                             | 
  │ │ │ └ sirius::Density::mixer_output                                 |        3.88 ms                             |      43                          |      167.02 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.69 ms                             |      43                          |      158.85 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      185.85 ms                             |      43                          |        7.99 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.41 ms                             |      43                          |        2.77 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.73 ms                             |      43                          |      375.26 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.17 ms                             |      43                          |      179.48 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.09 ms                             |      43                          |      175.72 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.09 ms                             |      43                          |      175.67 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      230.24 μs                             |      86                          |       19.80 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       96.28 ms                             |      43                          |        4.14 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       96.28 ms                             |      43                          |        4.14 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.61 ms                             |     215                          |      345.50 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.39 ms                             |     387                          |      924.73 ms                             | 
  │ │ │ │   ├ sirius::gradient                                          |        5.44 ms                             |      43                          |      233.80 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        1.72 ms                             |     129                          |      221.81 ms                             | 
  │ │ │ │   ├ sirius::dot                                               |        2.81 ms                             |      43                          |      120.89 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.57 ms                             |      43                          |      110.40 ms                             | 
  │ │ │ │   └ sirius::divergence                                        |       19.90 ms                             |      43                          |      855.57 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.46 ms                             |      43                          |      105.73 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.24 ms                             |      43                          |      139.42 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.90 ms                             |      43                          |      898.68 ms                             | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      219.74 ns                             |      43                          |        9.45 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      263.23 ns                             |      43                          |       11.32 μs                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms                             |      43                          |       95.75 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.06 ms                             |     301                          |        1.22 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.91 ms                             |     301                          |        1.18 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.91 ms                             |     301                          |        1.18 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.21 ms                             |     129                          |      543.16 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.05 ms                             |     129                          |      522.91 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.01 ms                             |      43                          |      172.23 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      102.25 μs                             |      43                          |        4.40 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       98.76 μs                             |      43                          |        4.25 ms                             | 
  │ ├ sirius::Density                                                   |                        86.83 ms            |                   1              |                        86.83 ms            | 
  │ │ └ sirius::Density::update                                         |                        77.38 ms            |                   1              |                        77.38 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        77.21 ms            |                   1              |                        77.21 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        52.40 ms            |                   1              |                        52.40 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         7.89 ms            |                   1              |                         7.89 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         8.50 ms            |                  45              |                       382.35 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         6.64 ms            |                  45              |                       298.99 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         3.67 ms            |                  45              |                       164.94 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        60.48 μs            |                  90              |                         5.44 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                       593.45 μs            |                  45              |                        26.71 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         1.08 ms            |                  45              |                        48.50 ms            | 
  │ ├ sirius::Band::solve                                               |                         1.87 s             |                  45              |                        84.12 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       211.79 μs            |                  45              |                         9.53 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       201.76 μs            |                  45              |                         9.08 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         5.39 μs            |                  45              |                       242.63 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         1.83 s             |                  45              |                        82.44 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         1.61 ms            |                  45              |                        72.61 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                       204.81 ms            |                 209              |                        42.81 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                       144.72 ms            |                 209              |                        30.25 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                        26.35 ms            |                 209              |                         5.51 s             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 |                        21.43 ms            |                 209              |                         4.48 s             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                        32.17 ms            |                 209              |                         6.72 s             | 
  │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                |                        20.01 ms            |                 209              |                         4.18 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         2.64 ms            |                 209              |                       551.12 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        21.51 ms            |                 209              |                         4.50 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         2.13 ms            |                 209              |                       445.78 ms            | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        17.96 ms            |                 418              |                         7.51 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        75.61 ms            |                 209              |                        15.80 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                        12.06 ms            |                 373              |                         4.50 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       196.06 ns            |                 373              |                        73.13 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         8.58 ms            |                 373              |                         3.20 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       326.95 ns            |                 373              |                       121.95 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                        27.40 ms            |                 209              |                         5.73 s             | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                        15.89 ms            |                 209              |                         3.32 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                        13.74 ms            |                 164              |                         2.25 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         4.56 ms            |                 492              |                         2.24 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                        21.98 ms            |                 209              |                         4.59 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                        21.03 ms            |                 209              |                         4.39 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       230.04 ns            |                 209              |                        48.08 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                        14.59 ms            |                 209              |                         3.05 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       486.01 ns            |                 209              |                       101.58 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        38.71 ms            |                 209              |                         8.09 s             | 
  │ │ │ ├ sirius::residuals                                             |                        15.05 ms            |                 204              |                         3.07 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                        14.04 ms            |                 184              |                         2.58 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         6.85 ms            |                 368              |                         2.52 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.41 ms            |                 184              |                       259.33 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        50.59 ms            |                  86              |                         4.35 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        33.38 ms            |                 127              |                         4.24 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        25.12 ms            |                 168              |                         4.22 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       604.73 ns            |                  45              |                        27.21 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                       123.06 μs            |                  45              |                         5.54 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       937.73 μs            |                  45              |                        42.20 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        22.73 μs            |                  45              |                         1.02 ms            | 
  │ ├ sirius::Density::generate                                         |                       294.77 ms            |                  45              |                        13.26 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       290.71 ms            |                  45              |                        13.08 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                        64.44 ms            |                  45              |                         2.90 s             | 
  │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                     |                        53.21 ms            |                  45              |                         2.39 s             | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        59.84 ms            |                  45              |                         2.69 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         9.78 μs            |                  45              |                       440.20 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         2.30 ms            |                  45              |                       103.59 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        56.93 ms            |                  45              |                         2.56 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         5.54 ms            |                  45              |                       249.24 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       538.16 ns            |                  45              |                        24.22 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       104.95 ms            |                  45              |                         4.72 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         2.45 ms            |                  45              |                       110.20 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        20.34 ms            |                  45              |                       915.16 ms            | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        20.17 ms            |                  45              |                       907.49 ms            | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       351.02 ns            |                  45              |                        15.80 μs            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                         1.26 ms            |                  45              |                        56.48 ms            | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         2.79 ms            |                  45              |                       125.76 ms            | 
  │ ├ sirius::inner                                                     |                         4.18 ms            |                 549              |                         2.30 s             | 
  │ ├ sirius::Density::mix                                              |                       107.04 ms            |                  45              |                         4.82 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                       211.76 μs            |                  45              |                         9.53 ms            | 
  │ │ └ sirius::Density::mixer_output                                   |                         2.72 ms            |                  45              |                       122.33 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         2.58 ms            |                  45              |                       115.91 ms            | 
  │ ├ sirius::Potential::generate                                       |                       211.94 ms            |                  45              |                         9.54 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                        64.08 ms            |                  45              |                         2.88 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         9.84 ms            |                  45              |                       442.59 ms            | 
  │ │ │ └ sirius::inner                                                 |                         4.41 ms            |                  45              |                       198.50 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       198.90 μs            |                  90              |                        17.90 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                       121.31 ms            |                  45              |                         5.46 s             | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                       120.28 ms            |                  45              |                         5.41 s             | 
  │ │ │   ├ sirius::Smooth_periodic_function::fft_transform             |                         2.47 ms            |                 540              |                         1.33 s             | 
  │ │ │   ├ sirius::gradient                                            |                         1.83 ms            |                  45              |                        82.46 ms            | 
  │ │ │   ├ sirius::dot                                                 |                       691.49 μs            |                  45              |                        31.12 ms            | 
  │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        11.31 ms            |                  90              |                         1.02 s             | 
  │ │ │   └ sirius::divergence                                          |                        19.80 ms            |                  90              |                         1.78 s             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         3.42 ms            |                  45              |                       154.05 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        20.92 ms            |                  45              |                       941.30 ms            | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       271.22 ns            |                  45              |                        12.20 μs            | 
  │ ├ sirius::Field4D::symmetrize                                       |                       345.00 ns            |                  45              |                        15.52 μs            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         2.31 ms            |                  45              |                       104.06 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                         4.18 ms            |                  45              |                       188.03 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        12.27 ms            |                  45              |                       552.14 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        12.26 ms            |                  45              |                       551.85 ms            | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.40 ms →        5.35 ms   (-0.96%) |       2   →       2              |       10.80 ms →       10.69 ms   (-0.96%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.03 ms                             |       6                          |       24.16 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.95 ms                             |       6                          |       23.67 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.95 ms                             |       6                          |       23.67 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.09 ms                             |       3                          |       12.27 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.05 ms                             |       3                          |       12.14 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        3.93 ms                             |       2                          |        7.86 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        3.87 ms                             |       2                          |        7.75 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.87 ms                             |       2                          |        7.75 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.08 ms                             |       1                          |        4.08 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.05 ms                             |       1                          |        4.05 ms                             | 
  ├ sirius::inner                                                       |                         4.18 ms            |                   3              |                        12.55 ms            | 
+ └ sirius::finalize                                                    |      371.21 ms →      321.18 ms  (-13.48%) |       1   →       1              |      371.21 ms →      321.18 ms  (-13.48%) | 
  ====================================================================================================================================================================================================
```
