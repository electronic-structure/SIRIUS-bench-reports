# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      145.92 s  →      112.69 s   (-22.78%) |       1   →       1              |      145.92 s  →      112.69 s   (-22.78%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.81 s    (+3.06%) |       1   →       1              |        2.73 s  →        2.81 s    (+3.06%) | 
  ├ sirius::Simulation_context::initialize                              |        2.21 s  →        2.05 s    (-7.39%) |       1   →       1              |        2.21 s  →        2.05 s    (-7.39%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       68.33 ms →      265.25 μs  (-99.61%) |       1   →       1              |       68.33 ms →      265.25 μs  (-99.61%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       72.20 ms →       88.03 ms  (+21.92%) |       1   →       1              |       72.20 ms →       88.03 ms  (+21.92%) | 
- │ │ ├ sirius::Atom_type::init                                         |       46.62 ms →       62.25 ms  (+33.53%) |       1   →       1              |       46.62 ms →       62.25 ms  (+33.53%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.52 ms →       25.71 ms   (+0.77%) |       1   →       1              |       25.52 ms →       25.71 ms   (+0.77%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        9.30 ms →        9.58 ms   (+3.03%) |       1   →       1              |        9.30 ms →        9.58 ms   (+3.03%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.19 ms →       16.10 ms   (-0.55%) |       1   →       1              |       16.19 ms →       16.10 ms   (-0.55%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.87 ms →       15.69 ms   (-1.16%) |       1   →       1              |       15.87 ms →       15.69 ms   (-1.16%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       15.66 ms →       15.43 ms   (-1.43%) |       1   →       1              |       15.66 ms →       15.43 ms   (-1.43%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      201.75 μs →      240.22 μs  (+19.07%) |       1   →       1              |      201.75 μs →      240.22 μs  (+19.07%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.29 μs →        2.37 μs   (+3.54%) |       1   →       1              |        2.29 μs →        2.37 μs   (+3.54%) | 
  │ └ sirius::Simulation_context::update                                |        2.01 s  →        1.90 s    (-5.62%) |       1   →       1              |        2.01 s  →        1.90 s    (-5.62%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.71 ms →       12.92 ms   (+1.66%) |       1   →       1              |       12.71 ms →       12.92 ms   (+1.66%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.30 ms →        8.38 ms   (+1.00%) |       1   →       1              |        8.30 ms →        8.38 ms   (+1.00%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.39 ms →        4.52 ms   (+2.87%) |       1   →       1              |        4.39 ms →        4.52 ms   (+2.87%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.10 ms →        4.11 ms   (+0.23%) |       1   →       1              |        4.10 ms →        4.11 ms   (+0.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.90 ms   (+0.25%) |       1   →       1              |        3.89 ms →        3.90 ms   (+0.25%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      202.62 μs →      201.98 μs   (-0.32%) |       1   →       1              |      202.62 μs →      201.98 μs   (-0.32%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.11 μs →        1.08 μs   (-3.06%) |       1   →       1              |        1.11 μs →        1.08 μs   (-3.06%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       16.10 ms →       15.23 ms   (-5.39%) |       2   →       2              |       32.20 ms →       30.46 ms   (-5.39%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.11 ms   (+0.58%) |       2   →       2              |        2.20 ms →        2.21 ms   (+0.58%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      971.49 μs →      987.14 μs   (+1.61%) |       1   →       1              |      971.49 μs →      987.14 μs   (+1.61%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.08 ms →        5.13 ms   (+0.88%) |       2   →       2              |       10.17 ms →       10.26 ms   (+0.88%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.71 ms →        3.66 ms   (-1.32%) |       2   →       2              |        7.42 ms →        7.32 ms   (-1.32%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.71 ms →       15.70 ms   (-0.05%) |       4   →       4              |       62.83 ms →       62.80 ms   (-0.05%) | 
  │   ├ sddk::Gvec::init                                                |      163.37 ms →      159.56 ms   (-2.33%) |       2   →       2              |      326.75 ms →      319.12 ms   (-2.33%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      126.72 ms →      126.64 ms   (-0.06%) |       2   →       2              |      253.45 ms →      253.29 ms   (-0.06%) | 
+ │   ├ sddk::Gvec_shells                                               |      177.39 ms →      126.66 ms  (-28.60%) |       1   →       1              |      177.39 ms →      126.66 ms  (-28.60%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.04 ms   (+0.94%) |       1   →       1              |        1.03 ms →        1.04 ms   (+0.94%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      220.63 ms →      218.14 ms   (-1.13%) |       1   →       1              |      220.63 ms →      218.14 ms   (-1.13%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       28.89 ms →       27.24 ms   (-5.70%) |       1   →       1              |       28.89 ms →       27.24 ms   (-5.70%) | 
- │ ├ sirius::K_point::K_point                                          |        1.98 μs →        6.42 μs (+224.53%) |       2   →       2              |        3.96 μs →       12.84 μs (+224.53%) | 
  │ └ sirius::K_point_set::initialize                                   |       28.86 ms →       27.20 ms   (-5.77%) |       1   →       1              |       28.86 ms →       27.20 ms   (-5.77%) | 
  │   └ sirius::K_point::initialize                                     |       28.81 ms →       27.14 ms   (-5.81%) |       1   →       1              |       28.81 ms →       27.14 ms   (-5.81%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       21.75 ms →       20.42 ms   (-6.09%) |       1   →       1              |       21.75 ms →       20.42 ms   (-6.09%) | 
  │     │ └ sddk::Gvec::init                                            |        5.41 ms →        5.28 ms   (-2.45%) |       1   →       1              |        5.41 ms →        5.28 ms   (-2.45%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |       10.65 μs →       12.10 μs  (+13.62%) |       1   →       1              |       10.65 μs →       12.10 μs  (+13.62%) | 
  │     └ sirius::K_point::update                                       |        4.43 ms →        4.24 ms   (-4.34%) |       1   →       1              |        4.43 ms →        4.24 ms   (-4.34%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.75 ms   (+1.65%) |       1   →       1              |        1.72 ms →        1.75 ms   (+1.65%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      903.53 μs →      938.17 μs   (+3.83%) |       1   →       1              |      903.53 μs →      938.17 μs   (+3.83%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.30 ms →        1.47 ms  (-36.17%) |       2   →       2              |        4.61 ms →        2.94 ms  (-36.17%) | 
  ├ sirius::Potential                                                   |       89.04 ms →       93.01 ms   (+4.45%) |       1   →       1              |       89.04 ms →       93.01 ms   (+4.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.54 ms →        2.49 ms   (-2.31%) |       6   →       6              |       15.27 ms →       14.92 ms   (-2.31%) | 
  │ └ sirius::Potential::update                                         |       73.41 ms →       77.76 ms   (+5.92%) |       1   →       1              |       73.41 ms →       77.76 ms   (+5.92%) | 
  │   └ sirius::Potential::generate_local_potential                     |       73.23 ms →       77.58 ms   (+5.94%) |       1   →       1              |       73.23 ms →       77.58 ms   (+5.94%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.15 ms →       51.82 ms  (-12.40%) |       1   →       1              |       59.15 ms →       51.82 ms  (-12.40%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       13.89 ms →       17.05 ms  (+22.74%) |       1   →       1              |       13.89 ms →       17.05 ms  (+22.74%) | 
  ├ sirius::Density                                                     |       72.29 ms →       75.36 ms   (+4.25%) |       1   →       1              |       72.29 ms →       75.36 ms   (+4.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.14 ms →        5.08 ms   (-1.09%) |       2   →       2              |       10.28 ms →       10.16 ms   (-1.09%) | 
  │ └ sirius::Density::update                                           |       61.89 ms →       65.08 ms   (+5.15%) |       1   →       1              |       61.89 ms →       65.08 ms   (+5.15%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.72 ms →       64.90 ms   (+5.17%) |       1   →       1              |       61.72 ms →       64.90 ms   (+5.17%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.27 ms            |                   1              |                         3.27 ms            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.01 ms →       52.16 ms  (-11.62%) |       1   →       1              |       59.01 ms →       52.16 ms  (-11.62%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.51 ms →        8.13 ms (+224.27%) |       1   →       1              |        2.51 ms →        8.13 ms (+224.27%) | 
  ├ sirius::Density::initial_density                                    |       80.83 ms →       79.48 ms   (-1.67%) |       1   →       1              |       80.83 ms →       79.48 ms   (-1.67%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       58.19 ms →       52.95 ms   (-9.00%) |       1   →       1              |       58.19 ms →       52.95 ms   (-9.00%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.91 ms →        5.24 ms  (+79.87%) |       2   →       2              |        5.82 ms →       10.47 ms  (+79.87%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.17 ms →        4.21 ms  (-18.49%) |       1   →       1              |        5.17 ms →        4.21 ms  (-18.49%) | 
  ├ sirius::Potential::generate                                         |      194.22 ms →      188.43 ms   (-2.98%) |       1   →       1              |      194.22 ms →      188.43 ms   (-2.98%) | 
  │ ├ sirius::Potential::poisson                                        |       65.02 ms →       65.41 ms   (+0.61%) |       1   →       1              |       65.02 ms →       65.41 ms   (+0.61%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.66 ms →        9.43 ms (+157.43%) |       1   →       1              |        3.66 ms →        9.43 ms (+157.43%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.19 ms →        4.33 ms   (+3.20%) |       1   →       1              |        4.19 ms →        4.33 ms   (+3.20%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.08 ms →        4.08 ms   (-0.08%) |       1   →       1              |        4.08 ms →        4.08 ms   (-0.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms →        4.08 ms   (-0.08%) |       1   →       1              |        4.08 ms →        4.08 ms   (-0.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      251.92 μs →      243.46 μs   (-3.36%) |       2   →       2              |      503.84 μs →      486.91 μs   (-3.36%) | 
  │ ├ sirius::Potential::xc                                             |      102.30 ms →       96.37 ms   (-5.79%) |       1   →       1              |      102.30 ms →       96.37 ms   (-5.79%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      102.30 ms →       95.29 ms   (-6.85%) |       1   →       1              |      102.30 ms →       95.29 ms   (-6.85%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.28 ms →        2.02 ms  (-11.36%) |       5   →       5              |       11.40 ms →       10.10 ms  (-11.36%) | 
+ │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.70 ms →        2.41 ms  (-10.60%) |       9   →       9              |       24.31 ms →       21.73 ms  (-10.60%) | 
  │ │   ├ sirius::gradient                                              |        7.60 ms →        7.65 ms   (+0.73%) |       1   →       1              |        7.60 ms →        7.65 ms   (+0.73%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.44 ms →        2.46 ms   (+0.83%) |       3   →       3              |        7.31 ms →        7.37 ms   (+0.83%) | 
  │ │   ├ sirius::dot                                                   |        2.82 ms →        2.83 ms   (+0.39%) |       1   →       1              |        2.82 ms →        2.83 ms   (+0.39%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.60 ms →        2.60 ms   (+0.23%) |       1   →       1              |        2.60 ms →        2.60 ms   (+0.23%) | 
+ │ │   └ sirius::divergence                                            |       22.75 ms →       19.76 ms  (-13.15%) |       1   →       1              |       22.75 ms →       19.76 ms  (-13.15%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.46 ms →        2.47 ms   (+0.60%) |       1   →       1              |        2.46 ms →        2.47 ms   (+0.60%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.58 ms →        3.26 ms   (-8.85%) |       1   →       1              |        3.58 ms →        3.26 ms   (-8.85%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.25 ms →       22.33 ms   (+0.38%) |       1   →       1              |       22.25 ms →       22.33 ms   (+0.38%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      115.00 ns →      209.00 ns  (+81.74%) |       1   →       1              |      115.00 ns →      209.00 ns  (+81.74%) | 
  ├ sirius::Hamiltonian0                                                |       14.39 ms →       13.81 ms   (-4.01%) |       1   →       1              |       14.39 ms →       13.81 ms   (-4.01%) | 
  │ ├ sirius::Local_operator                                            |       14.05 ms →       13.49 ms   (-4.04%) |       1   →       1              |       14.05 ms →       13.49 ms   (-4.04%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.20 ms →        7.20 ms   (-0.06%) |       1   →       1              |        7.20 ms →        7.20 ms   (-0.06%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.40 ms →        4.83 ms  (-10.43%) |       1   →       1              |        5.40 ms →        4.83 ms  (-10.43%) | 
  │ ├ sirius::Non_local_operator                                        |       61.62 μs →       60.44 μs   (-1.91%) |       2   →       2              |      123.23 μs →      120.88 μs   (-1.91%) | 
  │ ├ sirius::D_operator::initialize                                    |       81.66 μs →       80.03 μs   (-1.99%) |       1   →       1              |       81.66 μs →       80.03 μs   (-1.99%) | 
  │ └ sirius::Q_operator::initialize                                    |       71.17 μs →       68.52 μs   (-3.74%) |       1   →       1              |       71.17 μs →       68.52 μs   (-3.74%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.23 s  →        2.47 s   (+10.90%) |       1   →       1              |        2.23 s  →        2.47 s   (+10.90%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms →        8.41 ms   (+0.09%) |       1   →       1              |        8.40 ms →        8.41 ms   (+0.09%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      245.83 μs →      247.19 μs   (+0.55%) |       1   →       1              |      245.83 μs →      247.19 μs   (+0.55%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.16 ms   (+0.07%) |       1   →       1              |        8.15 ms →        8.16 ms   (+0.07%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.22 s  →        2.46 s   (+10.94%) |       1   →       1              |        2.22 s  →        2.46 s   (+10.94%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       95.99 ms →       87.20 ms   (-9.16%) |       4   →       4              |      383.97 ms →      348.82 ms   (-9.16%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.97 ms →       25.74 ms   (-0.89%) |       1   →       1              |       25.97 ms →       25.74 ms   (-0.89%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       15.03 ms →       14.78 ms   (-1.64%) |       1   →       1              |       15.03 ms →       14.78 ms   (-1.64%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.21 s    (+0.25%) |       1   →       1              |        1.21 s  →        1.21 s    (+0.25%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      984.25 ms →      988.21 ms   (+0.40%) |       1   →       1              |      984.25 ms →      988.21 ms   (+0.40%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      309.92 ms →      320.70 ms   (+3.48%) |       1   →       1              |      309.92 ms →      320.70 ms   (+3.48%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      181.42 ms →      175.79 ms   (-3.10%) |       1   →       1              |      181.42 ms →      175.79 ms   (-3.10%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      181.42 ms →      175.79 ms   (-3.10%) |       1   →       1              |      181.42 ms →      175.79 ms   (-3.10%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      110.03 ms →      126.49 ms  (+14.95%) |       1   →       1              |      110.03 ms →      126.49 ms  (+14.95%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      179.03 ms →      174.14 ms   (-2.73%) |       1   →       1              |      179.03 ms →      174.14 ms   (-2.73%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      179.03 ms →      174.13 ms   (-2.73%) |       1   →       1              |      179.03 ms →      174.13 ms   (-2.73%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      164.58 ms →      162.54 ms   (-1.24%) |       1   →       1              |      164.58 ms →      162.54 ms   (-1.24%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      114.04 ms →      112.05 ms   (-1.75%) |       1   →       1              |      114.04 ms →      112.05 ms   (-1.75%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.75 ms →        3.73 ms   (-0.48%) |       1   →       1              |        3.75 ms →        3.73 ms   (-0.48%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.18 ms →       89.27 ms   (-1.01%) |       1   →       1              |       90.18 ms →       89.27 ms   (-1.01%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.40 ms →       11.67 ms   (-5.87%) |       1   →       1              |       12.40 ms →       11.67 ms   (-5.87%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.19 ms →       64.22 ms   (+0.04%) |       2   →       2              |      128.39 ms →      128.43 ms   (+0.04%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       60.35 ms →      191.72 ms (+217.70%) |       2   →       2              |      120.69 ms →      383.44 ms (+217.70%) | 
  │ │ │ ├ sddk::inner                                                   |       60.21 ms                             |       2                          |      120.42 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       29.09 μs                             |       2                          |       58.19 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.71 ms                             |       4                          |      102.85 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      701.97 μs                             |       4                          |        2.81 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        7.35 ms                             |       2                          |       14.69 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                       191.62 ms            |                   2              |                       383.24 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        47.50 ns            |                   2              |                        95.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                       189.95 ms            |                   2              |                       379.90 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        13.00 ns            |                   2              |                        26.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.24 ms →      116.56 ms   (+0.28%) |       1   →       1              |      116.24 ms →      116.56 ms   (+0.28%) | 
  │ │ ├ sddk::transform                                                 |       36.04 ms                             |       1                          |       36.04 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       16.56 μs                             |       1                          |       16.56 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.17 μs                             |       1                          |       18.17 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        36.98 ms            |                   1              |                        36.98 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.65 ms            |                   1              |                        35.65 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      655.00 ns →      442.00 ns  (-32.52%) |       1   →       1              |      655.00 ns →      442.00 ns  (-32.52%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      137.02 s  →      103.77 s   (-24.27%) |       1   →       1              |      137.02 s  →      103.77 s   (-24.27%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.16 ms →        2.20 ms   (+1.82%) |      31   →      31              |       66.90 ms →       68.12 ms   (+1.82%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.18 s  →        2.72 s   (-14.34%) |      43   →      38    (-11.63%) |      136.75 s  →      103.52 s   (-24.30%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        7.09 ms →        7.58 ms   (+6.96%) |      43   →      38    (-11.63%) |      304.93 ms →      288.22 ms   (-5.48%) | 
! │ │ │ ├ sirius::Local_operator                                        |        6.75 ms →        7.24 ms   (+7.19%) |      43   →      38    (-11.63%) |      290.34 ms →      275.03 ms   (-5.27%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.57 ms →        1.54 ms   (-1.82%) |      43   →      38    (-11.63%) |       67.34 ms →       58.43 ms  (-13.24%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.72 ms →        4.16 ms  (+11.73%) |      43   →      38    (-11.63%) |      160.07 ms →      158.05 ms   (-1.26%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       61.65 μs →       62.69 μs   (+1.69%) |      86   →      76    (-11.63%) |        5.30 ms →        4.76 ms  (-10.13%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |       83.81 μs →       85.39 μs   (+1.89%) |      43   →      38    (-11.63%) |        3.60 ms →        3.24 ms   (-9.96%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       70.97 μs →       71.54 μs   (+0.79%) |      43   →      38    (-11.63%) |        3.05 ms →        2.72 ms  (-10.93%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.48 s  →        2.06 s   (-16.99%) |      43   →      38    (-11.63%) |      106.70 s  →       78.27 s   (-26.64%) | 
! │ │ │ ├ sirius::Hamiltonian_k                                         |      208.70 μs →      213.08 μs   (+2.10%) |      43   →      38    (-11.63%) |        8.97 ms →        8.10 ms   (-9.77%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      201.99 μs →      205.41 μs   (+1.69%) |      43   →      38    (-11.63%) |        8.69 ms →        7.81 ms  (-10.14%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.14 μs →        5.79 μs  (+12.61%) |      43   →      38    (-11.63%) |      220.91 μs →      219.85 μs   (-0.48%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.46 s  →        2.06 s   (-16.33%) |      43   →      38    (-11.63%) |      105.72 s  →       78.17 s   (-26.06%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       69.99 ms →       60.30 ms  (-13.84%) |      43   →      38    (-11.63%) |        3.01 s  →        2.29 s   (-23.86%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.59 ms →        4.66 ms  (-16.72%) |     258   →     228    (-11.63%) |        1.44 s  →        1.06 s   (-26.40%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.06 ms →        1.65 ms  (-19.98%) |      43   →      38    (-11.63%) |       88.69 ms →       62.72 ms  (-29.28%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.27 μs →      420.20 μs   (-0.25%) |      43   →      38    (-11.63%) |       18.11 ms →       15.97 ms  (-11.85%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      963.36 μs →      973.20 μs   (+1.02%) |      43   →      38    (-11.63%) |       41.42 ms →       36.98 ms  (-10.73%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.36 s  →        1.97 s   (-16.57%) |      43   →      38    (-11.63%) |      101.58 s  →       74.90 s   (-26.27%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.50 ms →      211.38 ms   (-1.46%) |     208   →     201     (-3.37%) |       44.62 s  →       42.49 s    (-4.77%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.53 ms →      149.66 ms   (-1.23%) |     208   →     201     (-3.37%) |       31.52 s  →       30.08 s    (-4.56%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.17 ms →       27.20 ms   (+0.11%) |     208   →     201     (-3.37%) |        5.65 s  →        5.47 s    (-3.26%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      680.46 μs →      712.17 μs   (+4.66%) |     208   →     201     (-3.37%) |      141.53 ms →      143.15 ms   (+1.14%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.28 ms →        3.75 ms  (+14.44%) |      43   →      38    (-11.63%) |      141.09 ms →      142.69 ms   (+1.14%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.89 ms →       22.00 ms   (+0.54%) |     208   →     201     (-3.37%) |        4.55 s  →        4.42 s    (-2.85%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      678.85 μs →      711.88 μs   (+4.87%) |     208   →     201     (-3.37%) |      141.20 ms →      143.09 ms   (+1.34%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.27 ms →        3.75 ms  (+14.60%) |      43   →      38    (-11.63%) |      140.71 ms →      142.50 ms   (+1.28%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.00 ms →       33.14 ms   (-2.55%) |     208   →     201     (-3.37%) |        7.07 s  →        6.66 s    (-5.83%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.18 ms →       20.55 ms   (-3.00%) |     208   →     201     (-3.37%) |        4.41 s  →        4.13 s    (-6.26%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.65 ms   (-0.21%) |     208   →     201     (-3.37%) |      551.44 ms →      531.76 ms   (-3.57%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.85 ms →       22.11 ms   (-3.24%) |     208   →     201     (-3.37%) |        4.75 s  →        4.44 s    (-6.50%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.64 ms →        2.19 ms  (-17.04%) |     208   →     201     (-3.37%) |      548.60 ms →      439.81 ms  (-19.83%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.72 ms →       18.47 ms   (-1.36%) |     416   →     402     (-3.37%) |        7.79 s  →        7.42 s    (-4.68%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       55.49 ms →       56.32 ms   (+1.50%) |     208   →     201     (-3.37%) |       11.54 s  →       11.32 s    (-1.92%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.64 ms                             |     373                          |        3.97 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       19.74 μs                             |     373                          |        7.36 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.45 ms                             |     746                          |        3.32 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      105.10 μs                             |     746                          |       78.40 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.51 ms                             |     373                          |      561.79 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                        12.84 ms            |                 364              |                         4.67 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        52.60 ns            |                 364              |                        19.15 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         9.39 ms            |                 364              |                         3.42 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        35.90 ns            |                 364              |                        13.07 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        3.13 ms →        3.18 ms   (+1.54%) |     208   →     201     (-3.37%) |      651.06 ms →      638.86 ms   (-1.87%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.22 ms →       15.65 ms   (-3.52%) |     208   →     201     (-3.37%) |        3.37 s  →        3.15 s    (-6.77%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.49 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       24.47 μs                             |     165                          |        4.04 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       58.62 μs                             |     495                          |       29.02 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        17.55 ms            |                 163              |                         2.86 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         5.83 ms            |                 489              |                         2.85 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.70 ms →       20.25 ms  (-10.80%) |     208   →     201     (-3.37%) |        4.72 s  →        4.07 s   (-13.81%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       18.70 ms                             |     208                          |        3.89 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       42.73 μs                             |     208                          |        8.89 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.91 ms                             |     416                          |        3.29 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      218.24 μs                             |     416                          |       90.79 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        2.39 ms                             |     208                          |      497.29 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        19.17 ms            |                 201              |                         3.85 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       122.83 ns            |                 201              |                        24.69 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        15.77 ms            |                 201              |                         3.17 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        20.02 ns            |                 201              |                         4.02 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      165.79 ms →       48.33 ms  (-70.85%) |     208   →     201     (-3.37%) |       34.48 s  →        9.72 s   (-71.83%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       19.09 ms →       16.06 ms  (-15.84%) |     207   →     196     (-5.31%) |        3.95 s  →        3.15 s   (-20.31%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.86 μs                             |     171                          |        2.88 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       58.20 μs                             |     342                          |       19.90 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        16.89 ms            |                 164              |                         2.77 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         8.04 ms            |                 328              |                         2.64 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.31 ms →        1.59 ms  (-31.23%) |     171   →     164     (-4.09%) |      394.35 ms →      260.08 ms  (-34.05%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.15 ms →       51.84 ms   (+1.34%) |      44   →      80    (+81.82%) |        2.25 s  →        4.15 s   (+84.25%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.73 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.75 μs                             |      45                          |      573.88 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       16.39 μs                             |      46                          |      753.89 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        33.04 ms            |                 122              |                         4.03 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        24.39 ms            |                 164              |                         4.00 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      594.07 ns →      518.95 ns  (-12.65%) |      43   →      38    (-11.63%) |       25.55 μs →       19.72 μs  (-22.80%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       25.32 μs →       34.58 μs  (+36.57%) |      43   →      38    (-11.63%) |        1.09 ms →        1.31 ms  (+20.69%) | 
! │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.46 ms →        3.63 ms   (+4.84%) |      43   →      38    (-11.63%) |      148.86 ms →      137.91 ms   (-7.35%) | 
+ │ │ ├ sirius::Density::generate                                       |      299.13 ms →      293.32 ms   (-1.94%) |      43   →      38    (-11.63%) |       12.86 s  →       11.15 s   (-13.34%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      294.67 ms →      289.33 ms   (-1.81%) |      43   →      38    (-11.63%) |       12.67 s  →       10.99 s   (-13.23%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.10 ms →       65.62 ms   (-2.21%) |      43   →      38    (-11.63%) |        2.89 s  →        2.49 s   (-13.58%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.51 μs →       70.71 μs  (+13.13%) |      43   →      38    (-11.63%) |        2.69 ms →        2.69 ms   (-0.03%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms →        1.20 ms   (+1.04%) |       2   →       2              |        2.37 ms →        2.39 ms   (+1.04%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.66 ms →       54.22 ms   (-2.58%) |      43   →      38    (-11.63%) |        2.39 s  →        2.06 s   (-13.91%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.98 ms →       59.79 ms   (-1.95%) |      43   →      38    (-11.63%) |        2.62 s  →        2.27 s   (-13.35%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.91 μs →        9.27 μs   (-6.47%) |      43   →      38    (-11.63%) |      426.17 μs →      352.24 μs  (-17.35%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.30 ms →        2.32 ms   (+0.74%) |      43   →      38    (-11.63%) |       99.02 ms →       88.15 ms  (-10.98%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.13 ms →       56.92 ms   (-2.08%) |      43   →      38    (-11.63%) |        2.50 s  →        2.16 s   (-13.47%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.71 ms →        5.51 ms  (-17.88%) |      43   →      38    (-11.63%) |      288.65 ms →      209.47 ms  (-27.43%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      586.58 ns →      740.92 ns  (+26.31%) |      43   →      38    (-11.63%) |       25.22 μs →       28.15 μs  (+11.62%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.44 ms →      105.22 ms   (+0.74%) |      43   →      38    (-11.63%) |        4.49 s  →        4.00 s   (-10.97%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.41 ms →        2.41 ms   (+0.16%) |      43   →      38    (-11.63%) |      103.64 ms →       91.74 ms  (-11.48%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       20.07 ms →       20.05 ms   (-0.14%) |      43   →      38    (-11.63%) |      863.14 ms →      761.73 ms  (-11.75%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms →       19.88 ms   (-0.12%) |      43   →      38    (-11.63%) |      855.80 ms →      755.41 ms  (-11.73%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      256.67 ns →      341.29 ns  (+32.97%) |      43   →      38    (-11.63%) |       11.04 μs →       12.97 μs  (+17.50%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.82%) |      43   →      38    (-11.63%) |       54.39 ms →       47.67 ms  (-12.35%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.19 ms →        2.74 ms  (-14.23%) |      43   →      38    (-11.63%) |      137.24 ms →      104.03 ms  (-24.20%) | 
+ │ │ ├ sirius::Density::mix                                            |      154.44 ms →      128.94 ms  (-16.51%) |      43   →      38    (-11.63%) |        6.64 s  →        4.90 s   (-26.22%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      261.41 μs →      263.35 μs   (+0.74%) |      43   →      38    (-11.63%) |       11.24 ms →       10.01 ms  (-10.97%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        2.80 ms →        3.68 ms  (+31.40%) |      43   →      38    (-11.63%) |      120.37 ms →      139.78 ms  (+16.12%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.61 ms →        3.48 ms  (+33.27%) |      43   →      38    (-11.63%) |      112.19 ms →      132.12 ms  (+17.77%) | 
+ │ │ ├ sirius::Potential::generate                                     |      186.63 ms →      182.33 ms   (-2.30%) |      43   →      38    (-11.63%) |        8.03 s  →        6.93 s   (-13.66%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       64.89 ms →       65.89 ms   (+1.54%) |      43   →      38    (-11.63%) |        2.79 s  →        2.50 s   (-10.26%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.36 ms →        8.90 ms (+165.21%) |      43   →      38    (-11.63%) |      144.27 ms →      338.13 ms (+134.38%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        4.18 ms →        4.22 ms   (+1.05%) |      43   →      38    (-11.63%) |      179.70 ms →      160.46 ms  (-10.70%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.09 ms →        4.07 ms   (-0.51%) |      43   →      38    (-11.63%) |      176.01 ms →      154.75 ms  (-12.08%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.09 ms →        4.07 ms   (-0.50%) |      43   →      38    (-11.63%) |      175.97 ms →      154.72 ms  (-12.07%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      238.75 μs →      231.70 μs   (-2.95%) |      86   →      76    (-11.63%) |       20.53 ms →       17.61 ms  (-14.24%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       96.05 ms →       91.13 ms   (-5.12%) |      43   →      38    (-11.63%) |        4.13 s  →        3.46 s   (-16.15%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       96.05 ms →       90.07 ms   (-6.22%) |      43   →      38    (-11.63%) |        4.13 s  →        3.42 s   (-17.12%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.63 ms →        1.60 ms   (-1.97%) |     215   →     190    (-11.63%) |      350.57 ms →      303.71 ms  (-13.37%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.82 ms →        2.51 ms  (-11.12%) |     387   →     342    (-11.63%) |        1.09 s  →      858.13 ms  (-21.46%) | 
! │ │ │ │   ├ sirius::gradient                                          |        2.45 ms →        2.50 ms   (+2.01%) |      43   →      38    (-11.63%) |      105.22 ms →       94.85 ms   (-9.85%) | 
! │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      720.68 μs →      736.70 μs   (+2.22%) |     129   →     114    (-11.63%) |       92.97 ms →       83.98 ms   (-9.66%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.85 ms →        2.83 ms   (-0.75%) |      43   →      38    (-11.63%) |      122.49 ms →      107.44 ms  (-12.29%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.60 ms →        2.59 ms   (-0.44%) |      43   →      38    (-11.63%) |      111.95 ms →       98.49 ms  (-12.02%) | 
+ │ │ │ │   └ sirius::divergence                                        |       22.70 ms →       19.82 ms  (-12.70%) |      43   →      38    (-11.63%) |      976.13 ms →      753.08 ms  (-22.85%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.46 ms →        2.47 ms   (+0.20%) |      43   →      38    (-11.63%) |      105.98 ms →       93.84 ms  (-11.46%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.71 ms →        3.34 ms  (-10.02%) |      43   →      38    (-11.63%) |      159.60 ms →      126.91 ms  (-20.48%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.92 ms →       20.95 ms   (+0.13%) |      43   →      38    (-11.63%) |      899.57 ms →      795.99 ms  (-11.51%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      131.47 ns →      226.84 ns  (+72.55%) |      43   →      38    (-11.63%) |        5.65 μs →        8.62 μs  (+52.49%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      213.51 ns →      362.21 ns  (+69.64%) |      43   →      38    (-11.63%) |        9.18 μs →       13.76 μs  (+49.92%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms →        2.28 ms   (+2.25%) |      43   →      38    (-11.63%) |       95.90 ms →       86.65 ms   (-9.64%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.09 ms →        4.14 ms   (+1.24%) |     301   →     266    (-11.63%) |        1.23 s  →        1.10 s   (-10.53%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        3.91 ms →        3.91 ms   (-0.11%) |     301   →     266    (-11.63%) |        1.18 s  →        1.04 s   (-11.72%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.91 ms →        3.91 ms   (-0.10%) |     301   →     266    (-11.63%) |        1.18 s  →        1.04 s   (-11.72%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.19 ms →        4.34 ms   (+3.67%) |     129   →     114    (-11.63%) |      540.59 ms →      495.27 ms   (-8.38%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.05 ms →        4.05 ms   (-0.01%) |     129   →     114    (-11.63%) |      522.20 ms →      461.44 ms  (-11.64%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.39 ms →        4.03 ms   (-8.27%) |      43   →      38    (-11.63%) |      188.91 ms →      153.13 ms  (-18.94%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      122.51 μs →      179.43 μs  (+46.46%) |      43   →      38    (-11.63%) |        5.27 ms →        6.82 ms  (+29.43%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      119.12 μs →      175.71 μs  (+47.51%) |      43   →      38    (-11.63%) |        5.12 ms →        6.68 ms  (+30.36%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.25 ms →        5.12 ms  (-17.98%) |       2   →       2              |       12.49 ms →       10.25 ms  (-17.98%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.25 ms →        4.00 ms   (-5.87%) |       6   →       6              |       25.51 ms →       24.02 ms   (-5.87%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.96 ms →        3.97 ms   (+0.25%) |       6   →       6              |       23.75 ms →       23.81 ms   (+0.25%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.96 ms →        3.97 ms   (+0.25%) |       6   →       6              |       23.75 ms →       23.81 ms   (+0.25%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.30 ms →        4.12 ms   (-4.25%) |       3   →       3              |       12.89 ms →       12.35 ms   (-4.25%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.01 ms →        4.08 ms   (+1.78%) |       3   →       3              |       12.02 ms →       12.23 ms   (+1.78%) | 
  ├ sirius::Periodic_function|inner                                     |        4.08 ms →        3.92 ms   (-3.99%) |       2   →       2              |        8.17 ms →        7.84 ms   (-3.99%) | 
  │ └ sirius::Periodic_function|inner_local                             |        3.86 ms →        3.88 ms   (+0.41%) |       2   →       2              |        7.73 ms →        7.76 ms   (+0.41%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.86 ms →        3.88 ms   (+0.41%) |       2   →       2              |        7.73 ms →        7.76 ms   (+0.41%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.26 ms →        4.07 ms   (-4.44%) |       1   →       1              |        4.26 ms →        4.07 ms   (-4.44%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.01 ms →        4.05 ms   (+0.96%) |       1   →       1              |        4.01 ms →        4.05 ms   (+0.96%) | 
+ └ sirius::finalize                                                    |      354.35 ms →      310.55 ms  (-12.36%) |       1   →       1              |      354.35 ms →      310.55 ms  (-12.36%) | 
  ====================================================================================================================================================================================================
```
