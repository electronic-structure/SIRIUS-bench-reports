# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      144.45 s  →      112.31 s   (-22.25%) |       1   →       1              |      144.45 s  →      112.31 s   (-22.25%) | 
  ├ sirius::initialize                                                  |        2.66 s  →        2.65 s    (-0.36%) |       1   →       1              |        2.66 s  →        2.65 s    (-0.36%) | 
  ├ sirius::Simulation_context::initialize                              |        2.12 s  →        2.11 s    (-0.68%) |       1   →       1              |        2.12 s  →        2.11 s    (-0.68%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      529.34 μs →       11.42 ms (+2057.13%) |       1   →       1              |      529.34 μs →       11.42 ms (+2057.13%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      126.63 ms →      120.15 ms   (-5.11%) |       1   →       1              |      126.63 ms →      120.15 ms   (-5.11%) | 
  │ │ ├ sirius::Atom_type::init                                         |      100.45 ms →       94.03 ms   (-6.39%) |       1   →       1              |      100.45 ms →       94.03 ms   (-6.39%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.11 ms →       26.05 ms   (-0.23%) |       1   →       1              |       26.11 ms →       26.05 ms   (-0.23%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.18 ms →       10.57 ms   (+3.82%) |       1   →       1              |       10.18 ms →       10.57 ms   (+3.82%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.91 ms →       15.46 ms   (-2.85%) |       1   →       1              |       15.91 ms →       15.46 ms   (-2.85%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.12 ms →       14.68 ms   (-2.92%) |       1   →       1              |       15.12 ms →       14.68 ms   (-2.92%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.88 ms →       14.44 ms   (-2.99%) |       1   →       1              |       14.88 ms →       14.44 ms   (-2.99%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      219.76 μs →      221.53 μs   (+0.80%) |       1   →       1              |      219.76 μs →      221.53 μs   (+0.80%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.30 μs →        2.30 μs   (-0.22%) |       1   →       1              |        2.30 μs →        2.30 μs   (-0.22%) | 
  │ └ sirius::Simulation_context::update                                |        1.94 s  →        1.92 s    (-1.04%) |       1   →       1              |        1.94 s  →        1.92 s    (-1.04%) | 
  │   ├ sirius::Unit_cell::update                                       |       13.18 ms →       13.30 ms   (+0.98%) |       1   →       1              |       13.18 ms →       13.30 ms   (+0.98%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.44 ms →        8.37 ms   (-0.80%) |       1   →       1              |        8.44 ms →        8.37 ms   (-0.80%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.72 ms →        4.92 ms   (+4.18%) |       1   →       1              |        4.72 ms →        4.92 ms   (+4.18%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.11 ms →        4.32 ms   (+5.17%) |       1   →       1              |        4.11 ms →        4.32 ms   (+5.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        4.11 ms   (+5.45%) |       1   →       1              |        3.90 ms →        4.11 ms   (+5.45%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      202.74 μs →      202.69 μs   (-0.02%) |       1   →       1              |      202.74 μs →      202.69 μs   (-0.02%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.23 μs →        1.13 μs   (-8.67%) |       1   →       1              |        1.23 μs →        1.13 μs   (-8.67%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.45 ms →       15.18 ms   (-1.75%) |       2   →       2              |       30.91 ms →       30.37 ms   (-1.75%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (+0.37%) |       2   →       2              |        2.19 ms →        2.20 ms   (+0.37%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      951.77 μs →      953.67 μs   (+0.20%) |       1   →       1              |      951.77 μs →      953.67 μs   (+0.20%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.08 ms →        5.11 ms   (+0.44%) |       2   →       2              |       10.17 ms →       10.21 ms   (+0.44%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.64 ms   (-0.28%) |       2   →       2              |        7.31 ms →        7.29 ms   (-0.28%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.75 ms →       15.62 ms   (-0.83%) |       4   →       4              |       63.01 ms →       62.48 ms   (-0.83%) | 
  │   ├ sddk::Gvec::init                                                |      162.36 ms →      157.66 ms   (-2.89%) |       2   →       2              |      324.72 ms →      315.32 ms   (-2.89%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.33 ms →      123.88 ms   (-2.71%) |       2   →       2              |      254.66 ms →      247.76 ms   (-2.71%) | 
+ │   ├ sddk::Gvec_shells                                               |      140.90 ms →      119.47 ms  (-15.21%) |       1   →       1              |      140.90 ms →      119.47 ms  (-15.21%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.02 ms →        1.02 ms   (-0.02%) |       1   →       1              |        1.02 ms →        1.02 ms   (-0.02%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      217.51 ms →      217.34 ms   (-0.08%) |       1   →       1              |      217.51 ms →      217.34 ms   (-0.08%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       28.66 ms →       26.85 ms   (-6.33%) |       1   →       1              |       28.66 ms →       26.85 ms   (-6.33%) | 
  │ ├ sirius::K_point::K_point                                          |        1.82 μs →        1.68 μs   (-8.09%) |       2   →       2              |        3.65 μs →        3.35 μs   (-8.09%) | 
  │ └ sirius::K_point_set::initialize                                   |       28.64 ms →       26.81 ms   (-6.36%) |       1   →       1              |       28.64 ms →       26.81 ms   (-6.36%) | 
  │   └ sirius::K_point::initialize                                     |       28.58 ms →       26.75 ms   (-6.40%) |       1   →       1              |       28.58 ms →       26.75 ms   (-6.40%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       21.49 ms →       20.39 ms   (-5.10%) |       1   →       1              |       21.49 ms →       20.39 ms   (-5.10%) | 
  │     │ └ sddk::Gvec::init                                            |        5.20 ms →        4.95 ms   (-4.89%) |       1   →       1              |        5.20 ms →        4.95 ms   (-4.89%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       12.05 μs →       11.79 μs   (-2.17%) |       1   →       1              |       12.05 μs →       11.79 μs   (-2.17%) | 
  │     └ sirius::K_point::update                                       |        4.46 ms →        4.04 ms   (-9.44%) |       1   →       1              |        4.46 ms →        4.04 ms   (-9.44%) | 
  │       └ sirius::Beta_projectors                                     |        1.75 ms →        1.68 ms   (-4.30%) |       1   →       1              |        1.75 ms →        1.68 ms   (-4.30%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      893.09 μs →      898.25 μs   (+0.58%) |       1   →       1              |      893.09 μs →      898.25 μs   (+0.58%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.20 ms →        1.46 ms  (-33.55%) |       2   →       2              |        4.40 ms →        2.92 ms  (-33.55%) | 
- ├ sirius::Potential                                                   |       82.83 ms →       92.96 ms  (+12.23%) |       1   →       1              |       82.83 ms →       92.96 ms  (+12.23%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.42 ms   (-1.04%) |       6   →       6              |       14.67 ms →       14.52 ms   (-1.04%) | 
- │ └ sirius::Potential::update                                         |       67.84 ms →       78.10 ms  (+15.12%) |       1   →       1              |       67.84 ms →       78.10 ms  (+15.12%) | 
- │   └ sirius::Potential::generate_local_potential                     |       67.67 ms →       77.93 ms  (+15.16%) |       1   →       1              |       67.67 ms →       77.93 ms  (+15.16%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       54.54 ms →       58.44 ms   (+7.15%) |       1   →       1              |       54.54 ms →       58.44 ms   (+7.15%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.94 ms →       10.86 ms  (-16.04%) |       1   →       1              |       12.94 ms →       10.86 ms  (-16.04%) | 
  ├ sirius::Density                                                     |       71.89 ms →       75.36 ms   (+4.82%) |       1   →       1              |       71.89 ms →       75.36 ms   (+4.82%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.72 ms →        4.77 ms   (+1.02%) |       2   →       2              |        9.44 ms →        9.54 ms   (+1.02%) | 
  │ └ sirius::Density::update                                           |       62.43 ms →       65.80 ms   (+5.40%) |       1   →       1              |       62.43 ms →       65.80 ms   (+5.40%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       62.25 ms →       65.62 ms   (+5.42%) |       1   →       1              |       62.25 ms →       65.62 ms   (+5.42%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.07 ms            |                   1              |                         3.07 ms            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       54.32 ms →       58.86 ms   (+8.36%) |       1   →       1              |       54.32 ms →       58.86 ms   (+8.36%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.73 ms →        2.43 ms  (-68.56%) |       1   →       1              |        7.73 ms →        2.43 ms  (-68.56%) | 
  ├ sirius::Density::initial_density                                    |       80.49 ms →       79.32 ms   (-1.46%) |       1   →       1              |       80.49 ms →       79.32 ms   (-1.46%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.62 ms →       58.81 ms   (+9.68%) |       1   →       1              |       53.62 ms →       58.81 ms   (+9.68%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.04 ms →        2.40 ms  (-52.35%) |       2   →       2              |       10.08 ms →        4.80 ms  (-52.35%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.20 ms →        3.97 ms  (-23.73%) |       1   →       1              |        5.20 ms →        3.97 ms  (-23.73%) | 
  ├ sirius::Potential::generate                                         |      191.04 ms →      186.08 ms   (-2.60%) |       1   →       1              |      191.04 ms →      186.08 ms   (-2.60%) | 
  │ ├ sirius::Potential::poisson                                        |       65.14 ms →       64.71 ms   (-0.66%) |       1   →       1              |       65.14 ms →       64.71 ms   (-0.66%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       10.43 ms →        2.33 ms  (-77.64%) |       1   →       1              |       10.43 ms →        2.33 ms  (-77.64%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.10 ms →        4.38 ms   (+7.06%) |       1   →       1              |        4.10 ms →        4.38 ms   (+7.06%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.04 ms →        4.10 ms   (+1.33%) |       1   →       1              |        4.04 ms →        4.10 ms   (+1.33%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.04 ms →        4.10 ms   (+1.33%) |       1   →       1              |        4.04 ms →        4.10 ms   (+1.33%) | 
  │ ├ sirius::Periodic_function::add                                    |      245.86 μs →      239.33 μs   (-2.66%) |       2   →       2              |      491.72 μs →      478.66 μs   (-2.66%) | 
  │ ├ sirius::Potential::xc                                             |       99.50 ms →       95.04 ms   (-4.48%) |       1   →       1              |       99.50 ms →       95.04 ms   (-4.48%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       99.49 ms →       94.00 ms   (-5.53%) |       1   →       1              |       99.49 ms →       94.00 ms   (-5.53%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.26 ms →        1.97 ms  (-12.79%) |       5   →       5              |       11.31 ms →        9.86 ms  (-12.79%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.36 ms →        2.39 ms   (+1.58%) |       9   →       9              |       21.21 ms →       21.54 ms   (+1.58%) | 
  │ │   ├ sirius::gradient                                              |        7.55 ms →        7.59 ms   (+0.45%) |       1   →       1              |        7.55 ms →        7.59 ms   (+0.45%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.43 ms →        2.43 ms   (+0.28%) |       3   →       3              |        7.28 ms →        7.30 ms   (+0.28%) | 
  │ │   ├ sirius::dot                                                   |        2.80 ms →        2.79 ms   (-0.39%) |       1   →       1              |        2.80 ms →        2.79 ms   (-0.39%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.57 ms →        2.56 ms   (-0.51%) |       1   →       1              |        2.57 ms →        2.56 ms   (-0.51%) | 
+ │ │   └ sirius::divergence                                            |       23.95 ms →       19.49 ms  (-18.63%) |       1   →       1              |       23.95 ms →       19.49 ms  (-18.63%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.54 ms →        2.40 ms   (-5.38%) |       1   →       1              |        2.54 ms →        2.40 ms   (-5.38%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.22 ms →        3.17 ms   (-1.52%) |       1   →       1              |        3.22 ms →        3.17 ms   (-1.52%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.16 ms →       22.14 ms   (-0.08%) |       1   →       1              |       22.16 ms →       22.14 ms   (-0.08%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      133.00 ns →      202.00 ns  (+51.88%) |       1   →       1              |      133.00 ns →      202.00 ns  (+51.88%) | 
  ├ sirius::Hamiltonian0                                                |       14.19 ms →       14.07 ms   (-0.83%) |       1   →       1              |       14.19 ms →       14.07 ms   (-0.83%) | 
  │ ├ sirius::Local_operator                                            |       13.87 ms →       13.74 ms   (-0.98%) |       1   →       1              |       13.87 ms →       13.74 ms   (-0.98%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.12 ms →        7.55 ms   (+6.00%) |       1   →       1              |        7.12 ms →        7.55 ms   (+6.00%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.30 ms →        4.70 ms  (-11.22%) |       1   →       1              |        5.30 ms →        4.70 ms  (-11.22%) | 
  │ ├ sirius::Non_local_operator                                        |       58.19 μs →       60.71 μs   (+4.33%) |       2   →       2              |      116.38 μs →      121.42 μs   (+4.33%) | 
  │ ├ sirius::D_operator::initialize                                    |       75.70 μs →       82.12 μs   (+8.48%) |       1   →       1              |       75.70 μs →       82.12 μs   (+8.48%) | 
  │ └ sirius::Q_operator::initialize                                    |       67.34 μs →       71.58 μs   (+6.29%) |       1   →       1              |       67.34 μs →       71.58 μs   (+6.29%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.18 s  →        2.47 s   (+13.37%) |       1   →       1              |        2.18 s  →        2.47 s   (+13.37%) | 
+ │ ├ sirius::Hamiltonian_k                                             |        8.38 ms →        7.12 ms  (-15.02%) |       1   →       1              |        8.38 ms →        7.12 ms  (-15.02%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      247.54 μs →      254.59 μs   (+2.85%) |       1   →       1              |      247.54 μs →      254.59 μs   (+2.85%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        8.13 ms →        6.86 ms  (-15.58%) |       1   →       1              |        8.13 ms →        6.86 ms  (-15.58%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.17 s  →        2.46 s   (+13.48%) |       1   →       1              |        2.17 s  →        2.46 s   (+13.48%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.93 ms →       87.42 ms   (+0.56%) |       4   →       4              |      347.72 ms →      349.68 ms   (+0.56%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.05 ms →       25.16 ms   (+0.42%) |       1   →       1              |       25.05 ms →       25.16 ms   (+0.42%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.35 ms →       14.33 ms   (-0.13%) |       1   →       1              |       14.35 ms →       14.33 ms   (-0.13%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.20 s  →        1.21 s    (+0.65%) |       1   →       1              |        1.20 s  →        1.21 s    (+0.65%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      976.97 ms →      984.52 ms   (+0.77%) |       1   →       1              |      976.97 ms →      984.52 ms   (+0.77%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      312.45 ms →      317.69 ms   (+1.68%) |       1   →       1              |      312.45 ms →      317.69 ms   (+1.68%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      175.78 ms →      173.36 ms   (-1.38%) |       1   →       1              |      175.78 ms →      173.36 ms   (-1.38%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      175.78 ms →      173.35 ms   (-1.38%) |       1   →       1              |      175.78 ms →      173.35 ms   (-1.38%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      118.27 ms →      125.92 ms   (+6.47%) |       1   →       1              |      118.27 ms →      125.92 ms   (+6.47%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      173.60 ms →      173.73 ms   (+0.07%) |       1   →       1              |      173.60 ms →      173.73 ms   (+0.07%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      173.59 ms →      173.72 ms   (+0.08%) |       1   →       1              |      173.59 ms →      173.72 ms   (+0.08%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      160.05 ms →      158.95 ms   (-0.69%) |       1   →       1              |      160.05 ms →      158.95 ms   (-0.69%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      109.68 ms →      108.31 ms   (-1.24%) |       1   →       1              |      109.68 ms →      108.31 ms   (-1.24%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.71 ms →        3.69 ms   (-0.47%) |       1   →       1              |        3.71 ms →        3.69 ms   (-0.47%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.54 ms →       89.54 ms   (+0.01%) |       1   →       1              |       89.54 ms →       89.54 ms   (+0.01%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.77 ms →       11.84 ms   (+0.58%) |       1   →       1              |       11.77 ms →       11.84 ms   (+0.58%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.13 ms →       64.26 ms   (+0.20%) |       2   →       2              |      128.26 ms →      128.51 ms   (+0.20%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       58.92 ms →      198.17 ms (+236.35%) |       2   →       2              |      117.83 ms →      396.33 ms (+236.35%) | 
  │ │ │ ├ sddk::inner                                                   |       58.78 ms                             |       2                          |      117.56 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       20.59 μs                             |       2                          |       41.17 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.19 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      682.39 μs                             |       4                          |        2.73 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        6.29 ms                             |       2                          |       12.58 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                       198.07 ms            |                   2              |                       396.13 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        34.00 ns            |                   2              |                        68.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                       196.49 ms            |                   2              |                       392.98 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        17.50 ns            |                   2              |                        35.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.21 ms →      118.47 ms   (+1.95%) |       1   →       1              |      116.21 ms →      118.47 ms   (+1.95%) | 
  │ │ ├ sddk::transform                                                 |       36.02 ms                             |       1                          |       36.02 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.19 μs                             |       1                          |       14.19 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       19.92 μs                             |       1                          |       19.92 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        37.87 ms            |                   1              |                        37.87 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.73 ms            |                   1              |                        35.73 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      479.00 ns →      486.00 ns   (+1.46%) |       1   →       1              |      479.00 ns →      486.00 ns   (+1.46%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      135.72 s  →      103.49 s   (-23.75%) |       1   →       1              |      135.72 s  →      103.49 s   (-23.75%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.14 ms →        2.16 ms   (+0.89%) |      31   →      31              |       66.44 ms →       67.03 ms   (+0.89%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.15 s  →        2.72 s   (-13.78%) |      43   →      38    (-11.63%) |      135.47 s  →      103.21 s   (-23.81%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        7.39 ms →        7.10 ms   (-3.90%) |      43   →      38    (-11.63%) |      317.85 ms →      269.95 ms  (-15.07%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        7.06 ms →        6.77 ms   (-4.08%) |      43   →      38    (-11.63%) |      303.58 ms →      257.34 ms  (-15.23%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.48 ms →        1.54 ms   (+4.28%) |      43   →      38    (-11.63%) |       63.68 ms →       58.69 ms   (-7.84%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.12 ms →        3.76 ms   (-8.71%) |      43   →      38    (-11.63%) |      177.01 ms →      142.80 ms  (-19.33%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       60.57 μs →       60.08 μs   (-0.81%) |      86   →      76    (-11.63%) |        5.21 ms →        4.57 ms  (-12.34%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |       79.26 μs →       80.82 μs   (+1.97%) |      43   →      38    (-11.63%) |        3.41 ms →        3.07 ms   (-9.88%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       68.25 μs →       68.91 μs   (+0.96%) |      43   →      38    (-11.63%) |        2.93 ms →        2.62 ms  (-10.78%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.47 s  →        2.06 s   (-16.65%) |      43   →      38    (-11.63%) |      106.06 s  →       78.12 s   (-26.35%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      210.22 μs →      209.08 μs   (-0.54%) |      43   →      38    (-11.63%) |        9.04 ms →        7.94 ms  (-12.11%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      202.04 μs →      201.67 μs   (-0.18%) |      43   →      38    (-11.63%) |        8.69 ms →        7.66 ms  (-11.79%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.33 μs →        5.38 μs  (-15.09%) |      43   →      38    (-11.63%) |      272.35 μs →      204.37 μs  (-24.96%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.45 s  →        2.05 s   (-16.47%) |      43   →      38    (-11.63%) |      105.55 s  →       77.91 s   (-26.18%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       68.11 ms →       60.54 ms  (-11.11%) |      43   →      38    (-11.63%) |        2.93 s  →        2.30 s   (-21.45%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.35 ms →        4.71 ms  (-12.00%) |     258   →     228    (-11.63%) |        1.38 s  →        1.07 s   (-22.23%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.02 ms →        1.82 ms   (-9.81%) |      43   →      38    (-11.63%) |       86.69 ms →       69.09 ms  (-20.30%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      420.60 μs →      422.78 μs   (+0.52%) |      43   →      38    (-11.63%) |       18.09 ms →       16.07 ms  (-11.17%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      945.78 μs →        1.10 ms  (+16.45%) |      43   →      38    (-11.63%) |       40.67 ms →       41.85 ms   (+2.91%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.36 s  →        1.96 s   (-16.79%) |      43   →      38    (-11.63%) |      101.49 s  →       74.63 s   (-26.47%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      212.56 ms →      209.14 ms   (-1.61%) |     208   →     201     (-3.37%) |       44.21 s  →       42.04 s    (-4.92%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      150.07 ms →      147.43 ms   (-1.76%) |     208   →     201     (-3.37%) |       31.21 s  →       29.63 s    (-5.06%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       26.18 ms →       25.93 ms   (-0.94%) |     208   →     201     (-3.37%) |        5.45 s  →        5.21 s    (-4.28%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      656.13 μs →      707.38 μs   (+7.81%) |     208   →     201     (-3.37%) |      136.48 ms →      142.18 ms   (+4.18%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.16 ms →        3.73 ms  (+17.87%) |      43   →      38    (-11.63%) |      136.03 ms →      141.70 ms   (+4.16%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.01 ms →       20.83 ms   (-0.89%) |     208   →     201     (-3.37%) |        4.37 s  →        4.19 s    (-4.22%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      653.74 μs →      701.76 μs   (+7.35%) |     208   →     201     (-3.37%) |      135.98 ms →      141.05 ms   (+3.73%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.15 ms →        3.70 ms  (+17.31%) |      43   →      38    (-11.63%) |      135.50 ms →      140.48 ms   (+3.67%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.31 ms →       32.50 ms   (-2.42%) |     208   →     201     (-3.37%) |        6.93 s  →        6.53 s    (-5.70%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       20.53 ms →       19.96 ms   (-2.78%) |     208   →     201     (-3.37%) |        4.27 s  →        4.01 s    (-6.05%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.62 ms →        2.62 ms   (-0.25%) |     208   →     201     (-3.37%) |      545.51 ms →      525.82 ms   (-3.61%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.56 ms →       22.24 ms   (-1.42%) |     208   →     201     (-3.37%) |        4.69 s  →        4.47 s    (-4.73%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.35 ms →        2.32 ms   (-1.29%) |     208   →     201     (-3.37%) |      488.80 ms →      466.25 ms   (-4.61%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.64 ms →       18.41 ms   (-1.21%) |     416   →     402     (-3.37%) |        7.75 s  →        7.40 s    (-4.53%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       55.62 ms →       56.84 ms   (+2.18%) |     208   →     201     (-3.37%) |       11.57 s  →       11.42 s    (-1.26%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.70 ms                             |     373                          |        3.99 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       19.91 μs                             |     373                          |        7.43 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.46 ms                             |     746                          |        3.32 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      108.73 μs                             |     746                          |       81.11 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.55 ms                             |     373                          |      577.27 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                        13.13 ms            |                 364              |                         4.78 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        42.69 ns            |                 364              |                        15.54 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         9.51 ms            |                 364              |                         3.46 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        34.18 ns            |                 364              |                        12.44 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.16 ms →        3.16 ms   (-0.01%) |     208   →     201     (-3.37%) |      657.50 ms →      635.29 ms   (-3.38%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.22 ms →       15.65 ms   (-3.49%) |     208   →     201     (-3.37%) |        3.37 s  →        3.15 s    (-6.74%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.50 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       31.26 μs                             |     165                          |        5.16 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       52.43 μs                             |     495                          |       25.95 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        17.56 ms            |                 163              |                         2.86 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         5.83 ms            |                 489              |                         2.85 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.50 ms →       20.52 ms   (-8.80%) |     208   →     201     (-3.37%) |        4.68 s  →        4.12 s   (-11.87%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       18.46 ms                             |     208                          |        3.84 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       42.25 μs                             |     208                          |        8.79 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.91 ms                             |     416                          |        3.29 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      215.76 μs                             |     416                          |       89.76 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        2.16 ms                             |     208                          |      448.67 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        19.44 ms            |                 201              |                         3.91 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       112.81 ns            |                 201              |                        22.67 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        15.91 ms            |                 201              |                         3.20 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        19.80 ns            |                 201              |                         3.98 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      166.50 ms →       48.02 ms  (-71.16%) |     208   →     201     (-3.37%) |       34.63 s  →        9.65 s   (-72.13%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       19.94 ms →       16.43 ms  (-17.61%) |     207   →     196     (-5.31%) |        4.13 s  →        3.22 s   (-21.99%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.06 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.03 μs                             |     171                          |        3.08 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       55.45 μs                             |     342                          |       18.96 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        17.35 ms            |                 164              |                         2.85 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         8.04 ms            |                 328              |                         2.64 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        3.33 ms →        1.55 ms  (-53.30%) |     171   →     164     (-4.09%) |      569.13 ms →      254.92 ms  (-55.21%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.15 ms →       51.99 ms   (+1.64%) |      44   →      80    (+81.82%) |        2.25 s  →        4.16 s   (+84.80%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.73 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       13.89 μs                             |      45                          |      624.85 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       17.38 μs                             |      46                          |      799.62 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        33.15 ms            |                 122              |                         4.04 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        24.39 ms            |                 164              |                         4.00 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      603.86 ns →      532.24 ns  (-11.86%) |      43   →      38    (-11.63%) |       25.97 μs →       20.23 μs  (-22.11%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.16 μs →       22.65 μs   (+2.21%) |      43   →      38    (-11.63%) |      953.02 μs →      860.84 μs   (-9.67%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.44 ms →        3.49 ms   (+1.27%) |      43   →      38    (-11.63%) |      148.01 ms →      132.47 ms  (-10.50%) | 
+ │ │ ├ sirius::Density::generate                                       |      292.40 ms →      294.41 ms   (+0.69%) |      43   →      38    (-11.63%) |       12.57 s  →       11.19 s   (-11.02%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      288.26 ms →      290.37 ms   (+0.73%) |      43   →      38    (-11.63%) |       12.40 s  →       11.03 s   (-10.98%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.57 ms →       66.47 ms   (+2.95%) |      43   →      38    (-11.63%) |        2.78 s  →        2.53 s    (-9.02%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       63.10 μs →       69.59 μs  (+10.28%) |      43   →      38    (-11.63%) |        2.71 ms →        2.64 ms   (-2.54%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.21 ms →        1.17 ms   (-2.77%) |       2   →       2              |        2.42 ms →        2.35 ms   (-2.77%) | 
! │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       53.34 ms →       55.18 ms   (+3.46%) |      43   →      38    (-11.63%) |        2.29 s  →        2.10 s    (-8.57%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.12 ms →       60.02 ms   (-0.18%) |      43   →      38    (-11.63%) |        2.59 s  →        2.28 s   (-11.79%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.79 μs →        9.64 μs   (-1.56%) |      43   →      38    (-11.63%) |      421.16 μs →      366.38 μs  (-13.01%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.29 ms →        2.28 ms   (-0.12%) |      43   →      38    (-11.63%) |       98.26 ms →       86.73 ms  (-11.73%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       57.30 ms →       57.18 ms   (-0.20%) |      43   →      38    (-11.63%) |        2.46 s  →        2.17 s   (-11.80%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.89 ms →        5.76 ms   (-2.19%) |      43   →      38    (-11.63%) |      253.33 ms →      218.96 ms  (-13.57%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      552.19 ns →      775.03 ns  (+40.36%) |      43   →      38    (-11.63%) |       23.74 μs →       29.45 μs  (+24.04%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      105.06 ms →      104.98 ms   (-0.08%) |      43   →      38    (-11.63%) |        4.52 s  →        3.99 s   (-11.70%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.41 ms   (+0.54%) |      43   →      38    (-11.63%) |      103.10 ms →       91.60 ms  (-11.15%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       20.03 ms →       20.06 ms   (+0.14%) |      43   →      38    (-11.63%) |      861.21 ms →      762.12 ms  (-11.51%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.86 ms →       19.88 ms   (+0.11%) |      43   →      38    (-11.63%) |      853.99 ms →      755.54 ms  (-11.53%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      232.05 ns →      335.05 ns  (+44.39%) |      43   →      38    (-11.63%) |        9.98 μs →       12.73 μs  (+27.60%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.48%) |      43   →      38    (-11.63%) |       54.17 ms →       47.64 ms  (-12.05%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.88 ms →        2.78 ms   (-3.49%) |      43   →      38    (-11.63%) |      123.87 ms →      105.64 ms  (-14.72%) | 
+ │ │ ├ sirius::Density::mix                                            |      148.68 ms →      126.88 ms  (-14.66%) |      43   →      38    (-11.63%) |        6.39 s  →        4.82 s   (-24.59%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      259.05 μs →      406.54 μs  (+56.94%) |      43   →      38    (-11.63%) |       11.14 ms →       15.45 ms  (+38.69%) | 
! │ │ │ └ sirius::Density::mixer_output                                 |        2.66 ms →        2.88 ms   (+8.26%) |      43   →      38    (-11.63%) |      114.50 ms →      109.54 ms   (-4.33%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.47 ms →        2.69 ms   (+8.88%) |      43   →      38    (-11.63%) |      106.34 ms →      102.32 ms   (-3.78%) | 
+ │ │ ├ sirius::Potential::generate                                     |      183.82 ms →      180.40 ms   (-1.86%) |      43   →      38    (-11.63%) |        7.90 s  →        6.86 s   (-13.27%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       65.53 ms →       64.68 ms   (-1.30%) |      43   →      38    (-11.63%) |        2.82 s  →        2.46 s   (-12.78%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       10.36 ms →        2.38 ms  (-77.06%) |      43   →      38    (-11.63%) |      445.62 ms →       90.36 ms  (-79.72%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.33 ms →        4.18 ms   (-3.37%) |      43   →      38    (-11.63%) |      186.16 ms →      158.97 ms  (-14.61%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.07 ms →        4.08 ms   (+0.36%) |      43   →      38    (-11.63%) |      174.96 ms →      155.17 ms  (-11.31%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.07 ms →        4.08 ms   (+0.37%) |      43   →      38    (-11.63%) |      174.91 ms →      155.14 ms  (-11.30%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      231.37 μs →      232.95 μs   (+0.68%) |      86   →      76    (-11.63%) |       19.90 ms →       17.70 ms  (-11.03%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       93.07 ms →       90.52 ms   (-2.73%) |      43   →      38    (-11.63%) |        4.00 s  →        3.44 s   (-14.04%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       93.07 ms →       89.47 ms   (-3.86%) |      43   →      38    (-11.63%) |        4.00 s  →        3.40 s   (-15.04%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.68 ms →        1.59 ms   (-5.29%) |     215   →     190    (-11.63%) |      361.52 ms →      302.59 ms  (-16.30%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.52 ms →        2.44 ms   (-3.19%) |     387   →     342    (-11.63%) |      973.68 ms →      833.06 ms  (-14.44%) | 
! │ │ │ │   ├ sirius::gradient                                          |        2.37 ms →        2.54 ms   (+6.97%) |      43   →      38    (-11.63%) |      101.94 ms →       96.37 ms   (-5.47%) | 
! │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      696.20 μs →      751.28 μs   (+7.91%) |     129   →     114    (-11.63%) |       89.81 ms →       85.65 ms   (-4.64%) | 
! │ │ │ │   ├ sirius::dot                                               |        2.81 ms →        2.86 ms   (+1.99%) |      43   →      38    (-11.63%) |      120.65 ms →      108.75 ms   (-9.87%) | 
! │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.57 ms →        2.62 ms   (+2.13%) |      43   →      38    (-11.63%) |      110.48 ms →       99.72 ms   (-9.75%) | 
+ │ │ │ │   └ sirius::divergence                                        |       22.51 ms →       19.60 ms  (-12.94%) |      43   →      38    (-11.63%) |      967.94 ms →      744.70 ms  (-23.06%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.41 ms →        2.44 ms   (+1.36%) |      43   →      38    (-11.63%) |      103.63 ms →       92.82 ms  (-10.43%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.31 ms →        3.27 ms   (-1.25%) |      43   →      38    (-11.63%) |      142.40 ms →      124.27 ms  (-12.73%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.90 ms →       20.91 ms   (+0.03%) |      43   →      38    (-11.63%) |      898.71 ms →      794.45 ms  (-11.60%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      136.09 ns →      241.13 ns  (+77.18%) |      43   →      38    (-11.63%) |        5.85 μs →        9.16 μs  (+56.58%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      207.12 ns →      327.37 ns  (+58.06%) |      43   →      38    (-11.63%) |        8.91 μs →       12.44 μs  (+39.68%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms →        2.28 ms   (+2.22%) |      43   →      38    (-11.63%) |       95.89 ms →       86.62 ms   (-9.67%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.07 ms →        4.11 ms   (+1.04%) |     301   →     266    (-11.63%) |        1.23 s  →        1.09 s   (-10.71%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.90 ms →        3.91 ms   (+0.36%) |     301   →     266    (-11.63%) |        1.17 s  →        1.04 s   (-11.31%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.90 ms →        3.91 ms   (+0.36%) |     301   →     266    (-11.63%) |        1.17 s  →        1.04 s   (-11.31%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.22 ms →        4.19 ms   (-0.62%) |     129   →     114    (-11.63%) |      544.31 ms →      478.04 ms  (-12.18%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.03 ms →        4.05 ms   (+0.32%) |     129   →     114    (-11.63%) |      520.20 ms →      461.18 ms  (-11.35%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.45 ms →        4.14 ms   (-6.94%) |      43   →      38    (-11.63%) |      191.31 ms →      157.33 ms  (-17.76%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       99.17 μs →      137.88 μs  (+39.04%) |      43   →      38    (-11.63%) |        4.26 ms →        5.24 ms  (+22.87%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       95.82 μs →      134.21 μs  (+40.07%) |      43   →      38    (-11.63%) |        4.12 ms →        5.10 ms  (+23.78%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.39 ms →        5.41 ms   (+0.50%) |       2   →       2              |       10.78 ms →       10.83 ms   (+0.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.07 ms →        4.07 ms   (-0.12%) |       6   →       6              |       24.42 ms →       24.39 ms   (-0.12%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.01 ms →        3.93 ms   (-2.06%) |       6   →       6              |       24.05 ms →       23.55 ms   (-2.06%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.01 ms →        3.93 ms   (-2.06%) |       6   →       6              |       24.05 ms →       23.55 ms   (-2.06%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.21 ms →        4.08 ms   (-2.97%) |       3   →       3              |       12.63 ms →       12.25 ms   (-2.97%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.20 ms →        4.01 ms   (-4.59%) |       3   →       3              |       12.60 ms →       12.02 ms   (-4.59%) | 
  ├ sirius::Periodic_function|inner                                     |        4.24 ms →        3.93 ms   (-7.14%) |       2   →       2              |        8.47 ms →        7.87 ms   (-7.14%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.01 ms →        3.92 ms   (-2.07%) |       2   →       2              |        8.01 ms →        7.85 ms   (-2.07%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.01 ms →        3.92 ms   (-2.06%) |       2   →       2              |        8.01 ms →        7.85 ms   (-2.06%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.12 ms →        4.09 ms   (-0.65%) |       1   →       1              |        4.12 ms →        4.09 ms   (-0.65%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.11 ms →        4.08 ms   (-0.68%) |       1   →       1              |        4.11 ms →        4.08 ms   (-0.68%) | 
+ └ sirius::finalize                                                    |      350.74 ms →      279.04 ms  (-20.44%) |       1   →       1              |      350.74 ms →      279.04 ms  (-20.44%) | 
  ====================================================================================================================================================================================================
```
