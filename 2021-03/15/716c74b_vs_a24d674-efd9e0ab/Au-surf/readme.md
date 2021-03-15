# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      151.65 s  →      123.92 s   (-18.28%) |       1   →       1              |      151.65 s  →      123.92 s   (-18.28%) | 
  ├ sirius::initialize                                                  |        2.74 s  →        2.75 s    (+0.21%) |       1   →       1              |        2.74 s  →        2.75 s    (+0.21%) | 
  ├ sirius::Simulation_context::initialize                              |        2.05 s  →        2.08 s    (+1.02%) |       1   →       1              |        2.05 s  →        2.08 s    (+1.02%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       16.96 ms →       26.30 ms  (+55.06%) |       1   →       1              |       16.96 ms →       26.30 ms  (+55.06%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       97.47 ms →      102.09 ms   (+4.74%) |       1   →       1              |       97.47 ms →      102.09 ms   (+4.74%) | 
  │ │ ├ sirius::Atom_type::init                                         |       72.29 ms →       77.68 ms   (+7.46%) |       1   →       1              |       72.29 ms →       77.68 ms   (+7.46%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.12 ms →       24.27 ms   (-3.41%) |       1   →       1              |       25.12 ms →       24.27 ms   (-3.41%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.22 ms →       10.20 ms   (-0.20%) |       1   →       1              |       10.22 ms →       10.20 ms   (-0.20%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.88 ms →       14.04 ms   (-5.64%) |       1   →       1              |       14.88 ms →       14.04 ms   (-5.64%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.46 ms →       13.28 ms   (-8.16%) |       1   →       1              |       14.46 ms →       13.28 ms   (-8.16%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.23 ms →       13.05 ms   (-8.28%) |       1   →       1              |       14.23 ms →       13.05 ms   (-8.28%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      218.01 μs →      218.12 μs   (+0.05%) |       1   →       1              |      218.01 μs →      218.12 μs   (+0.05%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.57 μs →        2.43 μs   (-5.64%) |       1   →       1              |        2.57 μs →        2.43 μs   (-5.64%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.89 s    (+0.29%) |       1   →       1              |        1.89 s  →        1.89 s    (+0.29%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.98 ms →       11.47 ms   (+4.43%) |       1   →       1              |       10.98 ms →       11.47 ms   (+4.43%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.92 ms →        8.20 ms   (+3.61%) |       1   →       1              |        7.92 ms →        8.20 ms   (+3.61%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.05 ms →        3.25 ms   (+6.58%) |       1   →       1              |        3.05 ms →        3.25 ms   (+6.58%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.64 ms →        2.64 ms   (+0.10%) |       1   →       1              |        2.64 ms →        2.64 ms   (+0.10%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.43 ms →        2.43 ms   (+0.22%) |       1   →       1              |        2.43 ms →        2.43 ms   (+0.22%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      204.39 μs →      202.54 μs   (-0.90%) |       1   →       1              |      204.39 μs →      202.54 μs   (-0.90%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.71 μs →        1.07 μs  (-37.56%) |       1   →       1              |        1.71 μs →        1.07 μs  (-37.56%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       17.80 ms →       17.73 ms   (-0.40%) |       2   →       2              |       35.61 ms →       35.47 ms   (-0.40%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.13 ms →        1.10 ms   (-2.01%) |       2   →       2              |        2.25 ms →        2.21 ms   (-2.01%) | 
+ │   ├ sirius::Radial_integrals|rho_pseudo                             |        1.11 ms →      956.42 μs  (-13.97%) |       1   →       1              |        1.11 ms →      956.42 μs  (-13.97%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.16 ms →        5.10 ms   (-1.28%) |       2   →       2              |       10.33 ms →       10.19 ms   (-1.28%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.63 ms   (-0.20%) |       2   →       2              |        7.28 ms →        7.27 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.16 ms →       15.73 ms   (+3.74%) |       4   →       4              |       60.64 ms →       62.90 ms   (+3.74%) | 
  │   ├ sddk::Gvec::init                                                |      158.65 ms →      159.42 ms   (+0.48%) |       2   →       2              |      317.30 ms →      318.83 ms   (+0.48%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      125.84 ms →      126.26 ms   (+0.33%) |       2   →       2              |      251.68 ms →      252.51 ms   (+0.33%) | 
  │   ├ sddk::Gvec_shells                                               |      121.75 ms →      128.46 ms   (+5.51%) |       1   →       1              |      121.75 ms →      128.46 ms   (+5.51%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.03 ms   (-1.06%) |       1   →       1              |        1.04 ms →        1.03 ms   (-1.06%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      217.99 ms →      217.20 ms   (-0.36%) |       1   →       1              |      217.99 ms →      217.20 ms   (-0.36%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.67 ms →       26.48 ms   (-0.71%) |       1   →       1              |       26.67 ms →       26.48 ms   (-0.71%) | 
- │ ├ sirius::K_point::K_point                                          |        2.18 μs →        5.08 μs (+133.18%) |       2   →       2              |        4.36 μs →       10.16 μs (+133.18%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.64 ms →       26.44 ms   (-0.76%) |       1   →       1              |       26.64 ms →       26.44 ms   (-0.76%) | 
  │   └ sirius::K_point::initialize                                     |       26.58 ms →       26.39 ms   (-0.73%) |       1   →       1              |       26.58 ms →       26.39 ms   (-0.73%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.80 ms →       19.96 ms   (+0.79%) |       1   →       1              |       19.80 ms →       19.96 ms   (+0.79%) | 
  │     │ └ sddk::Gvec::init                                            |        5.12 ms →        5.33 ms   (+4.17%) |       1   →       1              |        5.12 ms →        5.33 ms   (+4.17%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       12.30 μs                             |       1                          |       12.30 μs                             | 
  │     └ sirius::K_point::update                                       |        4.37 ms →        4.11 ms   (-6.04%) |       1   →       1              |        4.37 ms →        4.11 ms   (-6.04%) | 
  │       └ sirius::Beta_projectors                                     |        1.71 ms →        1.69 ms   (-1.27%) |       1   →       1              |        1.71 ms →        1.69 ms   (-1.27%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      906.43 μs →      893.38 μs   (-1.44%) |       1   →       1              |      906.43 μs →      893.38 μs   (-1.44%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.25 ms                             |       2                          |        4.51 ms                             | 
  ├ sirius::Potential                                                   |       94.66 ms →       91.64 ms   (-3.20%) |       1   →       1              |       94.66 ms →       91.64 ms   (-3.20%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms                             |       6                          |       14.79 ms                             | 
  │ └ sirius::Potential::update                                         |       79.53 ms →       76.57 ms   (-3.73%) |       1   →       1              |       79.53 ms →       76.57 ms   (-3.73%) | 
  │   └ sirius::Potential::generate_local_potential                     |       79.36 ms →       76.39 ms   (-3.74%) |       1   →       1              |       79.36 ms →       76.39 ms   (-3.74%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.79 ms →       51.35 ms   (-4.54%) |       1   →       1              |       53.79 ms →       51.35 ms   (-4.54%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       25.38 ms →        8.96 ms  (-64.72%) |       1   →       1              |       25.38 ms →        8.96 ms  (-64.72%) | 
  ├ sirius::Density                                                     |       71.50 ms →       74.64 ms   (+4.39%) |       1   →       1              |       71.50 ms →       74.64 ms   (+4.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.77 ms                             |       2                          |        9.54 ms                             | 
  │ └ sirius::Density::update                                           |       61.85 ms →       64.85 ms   (+4.86%) |       1   →       1              |       61.85 ms →       64.85 ms   (+4.86%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.67 ms →       64.68 ms   (+4.87%) |       1   →       1              |       61.67 ms →       64.68 ms   (+4.87%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.74 ms →       51.67 ms   (-3.85%) |       1   →       1              |       53.74 ms →       51.67 ms   (-3.85%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        7.74 ms →        9.10 ms  (+17.66%) |       1   →       1              |        7.74 ms →        9.10 ms  (+17.66%) | 
  ├ sirius::Density::initial_density                                    |       79.33 ms →       80.24 ms   (+1.14%) |       1   →       1              |       79.33 ms →       80.24 ms   (+1.14%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       52.90 ms →       50.97 ms   (-3.64%) |       1   →       1              |       52.90 ms →       50.97 ms   (-3.64%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.37 ms →        6.18 ms  (+15.14%) |       2   →       2              |       10.74 ms →       12.37 ms  (+15.14%) | 
  │ └ sirius::Periodic_function::integrate                              |        3.99 ms →        3.89 ms   (-2.52%) |       1   →       1              |        3.99 ms →        3.89 ms   (-2.52%) | 
- ├ sirius::Potential::generate                                         |      192.32 ms →      219.24 ms  (+14.00%) |       1   →       1              |      192.32 ms →      219.24 ms  (+14.00%) | 
  │ ├ sirius::Potential::poisson                                        |       64.85 ms →       64.36 ms   (-0.76%) |       1   →       1              |       64.85 ms →       64.36 ms   (-0.76%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.88 ms →        9.45 ms   (-4.36%) |       1   →       1              |        9.88 ms →        9.45 ms   (-4.36%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.58 ms                             |       1                          |        4.58 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.21 ms                             |       1                          |        4.21 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.21 ms                             |       1                          |        4.21 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.65 ms            |                   1              |                         4.65 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      239.45 μs →      212.49 μs  (-11.26%) |       2   →       2              |      478.90 μs →      424.97 μs  (-11.26%) | 
- │ ├ sirius::Potential::xc                                             |      100.51 ms →      126.57 ms  (+25.94%) |       1   →       1              |      100.51 ms →      126.57 ms  (+25.94%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      100.50 ms →      125.49 ms  (+24.86%) |       1   →       1              |      100.50 ms →      125.49 ms  (+24.86%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.27 ms                             |       5                          |       11.33 ms                             | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.55 ms →        2.39 ms   (-6.33%) |       9   →      12    (+33.33%) |       22.98 ms →       28.70 ms  (+24.89%) | 
  │ │   ├ sirius::gradient                                              |        7.61 ms →        7.67 ms   (+0.87%) |       1   →       1              |        7.61 ms →        7.67 ms   (+0.87%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.43 ms                             |       3                          |        7.30 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.81 ms →        2.86 ms   (+1.56%) |       1   →       1              |        2.81 ms →        2.86 ms   (+1.56%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.59 ms                             |       1                          |        2.59 ms                             | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        11.30 ms            |                   2              |                        22.60 ms            | 
- │ │   └ sirius::divergence                                            |       19.54 ms →       19.80 ms   (+1.35%) |       1   →       2   (+100.00%) |       19.54 ms →       39.60 ms (+102.71%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.45 ms                             |       1                          |        2.45 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.45 ms →        3.39 ms   (-1.67%) |       1   →       1              |        3.45 ms →        3.39 ms   (-1.67%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.47 ms →       22.68 ms   (+0.92%) |       1   →       1              |       22.47 ms →       22.68 ms   (+0.92%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      196.00 ns →      133.00 ns  (-32.14%) |       1   →       1              |      196.00 ns →      133.00 ns  (-32.14%) | 
  ├ sirius::Hamiltonian0                                                |       14.28 ms →       15.67 ms   (+9.75%) |       1   →       1              |       14.28 ms →       15.67 ms   (+9.75%) | 
  │ ├ sirius::Local_operator                                            |       13.94 ms →       13.85 ms   (-0.69%) |       1   →       1              |       13.94 ms →       13.85 ms   (-0.69%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.15 ms                             |       1                          |        7.15 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.34 ms →        5.27 ms   (-1.36%) |       1   →       1              |        5.34 ms →        5.27 ms   (-1.36%) | 
  │ ├ sirius::Non_local_operator                                        |       59.72 μs →       60.54 μs   (+1.39%) |       2   →       2              |      119.43 μs →      121.09 μs   (+1.39%) | 
- │ ├ sirius::D_operator::initialize                                    |       83.95 μs →      567.37 μs (+575.85%) |       1   →       1              |       83.95 μs →      567.37 μs (+575.85%) | 
- │ └ sirius::Q_operator::initialize                                    |       70.58 μs →        1.07 ms (+1419.13%) |       1   →       1              |       70.58 μs →        1.07 ms (+1419.13%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.19 s  →        2.23 s    (+1.77%) |       1   →       1              |        2.19 s  →        2.23 s    (+1.77%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms →        8.41 ms   (+0.15%) |       1   →       1              |        8.40 ms →        8.41 ms   (+0.15%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      247.56 μs →      257.01 μs   (+3.82%) |       1   →       1              |      247.56 μs →      257.01 μs   (+3.82%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.15 ms   (+0.01%) |       1   →       1              |        8.15 ms →        8.15 ms   (+0.01%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.19 s  →        2.22 s    (+1.69%) |       1   →       1              |        2.19 s  →        2.22 s    (+1.69%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.58 ms                             |       4                          |      346.33 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.81 ms →       25.11 ms   (-2.72%) |       1   →       1              |       25.81 ms →       25.11 ms   (-2.72%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.93 ms →       14.38 ms   (-3.72%) |       1   →       1              |       14.93 ms →       14.38 ms   (-3.72%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.20 s    (-0.87%) |       1   →       1              |        1.21 s  →        1.20 s    (-0.87%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      992.01 ms →      982.22 ms   (-0.99%) |       1   →       1              |      992.01 ms →      982.22 ms   (-0.99%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      323.01 ms →      314.51 ms   (-2.63%) |       1   →       1              |      323.01 ms →      314.51 ms   (-2.63%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      174.46 ms                             |       1                          |      174.46 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      174.46 ms                             |       1                          |      174.46 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      130.08 ms →      122.41 ms   (-5.89%) |       1   →       1              |      130.08 ms →      122.41 ms   (-5.89%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      171.62 ms                             |       1                          |      171.62 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      171.62 ms                             |       1                          |      171.62 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      166.29 ms →      164.28 ms   (-1.21%) |       1   →       1              |      166.29 ms →      164.28 ms   (-1.21%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      115.79 ms →      113.79 ms   (-1.72%) |       1   →       1              |      115.79 ms →      113.79 ms   (-1.72%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.76 ms →        3.76 ms   (-0.00%) |       1   →       1              |        3.76 ms →        3.76 ms   (-0.00%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.89 ms →       89.08 ms   (-0.90%) |       1   →       1              |       89.89 ms →       89.08 ms   (-0.90%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.23 ms →       11.34 ms   (-7.22%) |       1   →       1              |       12.23 ms →       11.34 ms   (-7.22%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.22 ms →       64.23 ms   (+0.01%) |       2   →       2              |      128.44 ms →      128.46 ms   (+0.01%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.96 ms →       82.76 ms  (+38.02%) |       2   →       2              |      119.92 ms →      165.52 ms  (+38.02%) | 
  │ │ │ ├ sddk::inner                                                   |       59.85 ms                             |       2                          |      119.69 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       21.49 μs                             |       2                          |       42.98 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.20 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      714.40 μs                             |       4                          |        2.86 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        7.28 ms                             |       2                          |       14.57 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        82.65 ms            |                   2              |                       165.30 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       180.50 ns            |                   2              |                       361.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        81.16 ms            |                   2              |                       162.31 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       595.00 ns            |                   2              |                         1.19 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.17 ms →      116.05 ms   (-0.10%) |       1   →       1              |      116.17 ms →      116.05 ms   (-0.10%) | 
  │ │ ├ sddk::transform                                                 |       36.05 ms                             |       1                          |       36.05 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       15.17 μs                             |       1                          |       15.17 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       20.80 μs                             |       1                          |       20.80 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        35.89 ms            |                   1              |                        35.89 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.29 ms            |                   1              |                        35.29 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      444.00 ns →      443.00 ns   (-0.23%) |       1   →       1              |      444.00 ns →      443.00 ns   (-0.23%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      142.91 s  →      115.38 s   (-19.27%) |       1   →       1              |      142.91 s  →      115.38 s   (-19.27%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.16 ms                             |      31                          |       67.00 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.32 s                              |      43                          |      142.68 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        8.22 ms                             |      43                          |      353.28 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        7.88 ms                             |      43                          |      338.68 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.52 ms                             |      43                          |       65.31 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.89 ms                             |      43                          |      210.48 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.60 μs                             |      86                          |        5.30 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       83.57 μs                             |      43                          |        3.59 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       71.75 μs                             |      43                          |        3.09 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.64 s                              |      43                          |      113.39 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      215.88 μs                             |      43                          |        9.28 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      208.33 μs                             |      43                          |        8.96 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.70 μs                             |      43                          |      244.93 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s                              |      43                          |      112.56 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       68.84 ms                             |      43                          |        2.96 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.38 ms                             |     258                          |        1.39 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.02 ms                             |      43                          |       87.04 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      420.21 μs                             |      43                          |       18.07 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      944.52 μs                             |      43                          |       40.61 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.52 s                              |      43                          |      108.47 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      216.44 ms                             |     208                          |       45.02 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      153.41 ms                             |     208                          |       31.91 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       28.15 ms                             |     208                          |        5.85 s                              | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      668.44 μs                             |     208                          |      139.04 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.22 ms                             |      43                          |      138.59 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       23.00 ms                             |     208                          |        4.78 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      661.69 μs                             |     208                          |      137.63 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.19 ms                             |      43                          |      137.05 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.84 ms                             |     208                          |        7.25 s                              | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       22.05 ms                             |     208                          |        4.59 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.66 ms                             |     208                          |      552.33 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.85 ms                             |     208                          |        4.75 s                              | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.63 ms                             |     208                          |      547.33 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.75 ms                             |     416                          |        7.80 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       83.04 ms                             |     208                          |       17.27 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.76 ms                             |     373                          |        4.01 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       19.92 μs                             |     373                          |        7.43 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.48 ms                             |     746                          |        3.34 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      103.82 μs                             |     746                          |       77.45 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.57 ms                             |     373                          |      587.29 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.40 ms                             |     208                          |        6.32 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.24 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       21.55 ms                             |     165                          |        3.56 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       21.78 μs                             |     165                          |        3.59 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       60.79 μs                             |     495                          |       30.09 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       25.40 ms                             |     208                          |        5.28 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |       21.24 ms                             |     208                          |        4.42 s                              | 
  │ │ │ │   │   ├ sddk::inner|local                                     |       45.15 μs                             |     208                          |        9.39 ms                             | 
  │ │ │ │   │   ├ sddk::inner|device_copy                               |        7.93 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │   ├ sddk::inner|store                                     |      239.42 μs                             |     416                          |       99.60 ms                             | 
  │ │ │ │   │   └ sddk::inner|mpi                                       |        4.86 ms                             |     208                          |        1.01 s                              | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      166.39 ms                             |     208                          |       34.61 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       19.38 ms                             |     207                          |        4.01 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.52 μs                             |     171                          |        2.82 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       59.29 μs                             |     342                          |       20.28 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.66 ms                             |     171                          |      455.21 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.26 ms                             |      44                          |        2.26 s                              | 
  │ │ │ │     └ sddk::transform                                         |       49.85 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       13.34 μs                             |      45                          |      600.28 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       16.72 μs                             |      46                          |      769.06 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      628.35 ns                             |      43                          |       27.02 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.37 μs                             |      43                          |        1.26 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.52 ms                             |      43                          |      151.15 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      300.76 ms                             |      43                          |       12.93 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      296.73 ms                             |      43                          |       12.76 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.15 ms                             |      43                          |        2.97 s                              | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.55 μs                             |      43                          |        2.69 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.19 ms                             |       2                          |        2.39 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.90 ms                             |      43                          |        2.49 s                              | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.13 ms                             |      43                          |        2.63 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.65 μs                             |      43                          |      415.04 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms                             |      43                          |       99.47 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.27 ms                             |      43                          |        2.51 s                              | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.80 ms                             |      43                          |      292.61 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      607.58 ns                             |      43                          |       26.13 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.47 ms                             |      43                          |        4.49 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms                             |      43                          |      103.29 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms                             |      43                          |      862.17 ms                             | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms                             |      43                          |      855.10 ms                             | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      301.00 ns                             |      43                          |       12.94 μs                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms                             |      43                          |       53.87 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.78 ms                             |      43                          |      119.53 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      134.51 ms                             |      43                          |        5.78 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      269.25 μs                             |      43                          |       11.58 ms                             | 
  │ │ │ └ sirius::Density::mixer_output                                 |        3.56 ms                             |      43                          |      152.90 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.36 ms                             |      43                          |      144.29 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      185.46 ms                             |      43                          |        7.97 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.43 ms                             |      43                          |        2.77 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.55 ms                             |      43                          |      410.69 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.40 ms                             |      43                          |      189.38 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.25 ms                             |      43                          |      182.68 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.25 ms                             |      43                          |      182.63 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      230.99 μs                             |      86                          |       19.87 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       95.25 ms                             |      43                          |        4.10 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       95.25 ms                             |      43                          |        4.10 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.67 ms                             |     215                          |      358.40 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.68 ms                             |     387                          |        1.04 s                              | 
  │ │ │ │   ├ sirius::gradient                                          |        2.42 ms                             |      43                          |      104.27 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      713.77 μs                             |     129                          |       92.08 ms                             | 
  │ │ │ │   ├ sirius::dot                                               |        2.82 ms                             |      43                          |      121.47 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.60 ms                             |      43                          |      111.59 ms                             | 
  │ │ │ │   └ sirius::divergence                                        |       19.77 ms                             |      43                          |      850.07 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.45 ms                             |      43                          |      105.24 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.79 ms                             |      43                          |      162.84 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.97 ms                             |      43                          |      901.53 ms                             | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      183.30 ns                             |      43                          |        7.88 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      320.56 ns                             |      43                          |       13.78 μs                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.27 ms                             |      43                          |       97.47 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.29 ms                             |     301                          |        1.29 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.07 ms                             |     301                          |        1.22 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.07 ms                             |     301                          |        1.22 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.04 ms                             |     129                          |      520.89 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.87 ms                             |     129                          |      499.56 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        3.99 ms                             |      43                          |      171.52 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      108.14 μs                             |      43                          |        4.65 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      104.78 μs                             |      43                          |        4.51 ms                             | 
  │ ├ sirius::Density                                                   |                        88.85 ms            |                   1              |                        88.85 ms            | 
  │ │ └ sirius::Density::update                                         |                        79.41 ms            |                   1              |                        79.41 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        79.24 ms            |                   1              |                        79.24 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        51.53 ms            |                   1              |                        51.53 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         9.17 ms            |                   1              |                         9.17 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         8.47 ms            |                  45              |                       381.01 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         6.64 ms            |                  45              |                       298.72 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         3.66 ms            |                  45              |                       164.63 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        61.16 μs            |                  90              |                         5.50 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                       581.83 μs            |                  45              |                        26.18 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         1.06 ms            |                  45              |                        47.92 ms            | 
  │ ├ sirius::Band::solve                                               |                         1.86 s             |                  45              |                        83.72 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       212.41 μs            |                  45              |                         9.56 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       202.73 μs            |                  45              |                         9.12 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         5.45 μs            |                  45              |                       245.34 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         1.82 s             |                  45              |                        82.09 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         1.63 ms            |                  45              |                        73.13 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                       204.47 ms            |                 209              |                        42.73 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                       144.44 ms            |                 209              |                        30.19 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                        26.27 ms            |                 209              |                         5.49 s             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 |                        21.33 ms            |                 209              |                         4.46 s             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                        32.05 ms            |                 209              |                         6.70 s             | 
  │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                |                        19.90 ms            |                 209              |                         4.16 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         2.64 ms            |                 209              |                       551.90 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        21.49 ms            |                 209              |                         4.49 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         2.10 ms            |                 209              |                       439.45 ms            | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        17.93 ms            |                 418              |                         7.50 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        74.72 ms            |                 209              |                        15.62 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                        12.07 ms            |                 373              |                         4.50 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       191.68 ns            |                 373              |                        71.50 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         8.54 ms            |                 373              |                         3.19 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       338.69 ns            |                 373              |                       126.33 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                        26.51 ms            |                 209              |                         5.54 s             | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                        15.89 ms            |                 209              |                         3.32 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                        13.73 ms            |                 164              |                         2.25 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         4.55 ms            |                 492              |                         2.24 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                        21.86 ms            |                 209              |                         4.57 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                        20.94 ms            |                 209              |                         4.38 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       269.38 ns            |                 209              |                        56.30 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                        14.56 ms            |                 209              |                         3.04 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       460.66 ns            |                 209              |                        96.28 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        38.56 ms            |                 209              |                         8.06 s             | 
  │ │ │ ├ sirius::residuals                                             |                        15.00 ms            |                 204              |                         3.06 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                        13.98 ms            |                 184              |                         2.57 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         6.85 ms            |                 368              |                         2.52 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.40 ms            |                 184              |                       258.09 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        50.53 ms            |                  86              |                         4.35 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        33.34 ms            |                 127              |                         4.23 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        25.12 ms            |                 168              |                         4.22 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       528.93 ns            |                  45              |                        23.80 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        96.85 μs            |                  45              |                         4.36 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       937.67 μs            |                  45              |                        42.20 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        28.05 μs            |                  45              |                         1.26 ms            | 
  │ ├ sirius::Density::generate                                         |                       294.71 ms            |                  45              |                        13.26 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       290.75 ms            |                  45              |                        13.08 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                        64.73 ms            |                  45              |                         2.91 s             | 
  │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                     |                        53.52 ms            |                  45              |                         2.41 s             | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        60.48 ms            |                  45              |                         2.72 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         9.69 μs            |                  45              |                       435.96 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         2.30 ms            |                  45              |                       103.71 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        57.56 ms            |                  45              |                         2.59 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         6.18 ms            |                  45              |                       277.92 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       524.84 ns            |                  45              |                        23.62 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       104.85 ms            |                  45              |                         4.72 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         2.40 ms            |                  45              |                       107.92 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        20.33 ms            |                  45              |                       914.68 ms            | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        20.15 ms            |                  45              |                       906.95 ms            | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       348.51 ns            |                  45              |                        15.68 μs            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                         1.25 ms            |                  45              |                        56.45 ms            | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         2.69 ms            |                  45              |                       121.07 ms            | 
  │ ├ sirius::inner                                                     |                         4.20 ms            |                 549              |                         2.31 s             | 
  │ ├ sirius::Density::mix                                              |                       107.66 ms            |                  45              |                         4.84 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                       218.31 μs            |                  45              |                         9.82 ms            | 
  │ │ └ sirius::Density::mixer_output                                   |                         2.53 ms            |                  45              |                       113.86 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         2.39 ms            |                  45              |                       107.34 ms            | 
  │ ├ sirius::Potential::generate                                       |                       212.84 ms            |                  45              |                         9.58 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                        64.47 ms            |                  45              |                         2.90 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         9.90 ms            |                  45              |                       445.28 ms            | 
  │ │ │ └ sirius::inner                                                 |                         4.41 ms            |                  45              |                       198.33 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       202.19 μs            |                  90              |                        18.20 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                       121.83 ms            |                  45              |                         5.48 s             | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                       120.79 ms            |                  45              |                         5.44 s             | 
  │ │ │   ├ sirius::Smooth_periodic_function::fft_transform             |                         2.51 ms            |                 540              |                         1.36 s             | 
  │ │ │   ├ sirius::gradient                                            |                         1.83 ms            |                  45              |                        82.38 ms            | 
  │ │ │   ├ sirius::dot                                                 |                       697.57 μs            |                  45              |                        31.39 ms            | 
  │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        11.27 ms            |                  90              |                         1.01 s             | 
  │ │ │   └ sirius::divergence                                          |                        19.84 ms            |                  90              |                         1.79 s             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         3.43 ms            |                  45              |                       154.24 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        20.90 ms            |                  45              |                       940.54 ms            | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       305.84 ns            |                  45              |                        13.76 μs            | 
  │ ├ sirius::Field4D::symmetrize                                       |                       364.73 ns            |                  45              |                        16.41 μs            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         2.25 ms            |                  45              |                       101.35 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                         4.20 ms            |                  45              |                       188.90 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        12.39 ms            |                  45              |                       557.74 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        12.39 ms            |                  45              |                       557.44 ms            | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.68 ms →        5.48 ms  (-17.98%) |       2   →       2              |       13.37 ms →       10.97 ms  (-17.98%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.13 ms                             |       6                          |       24.81 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.06 ms                             |       6                          |       24.33 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.06 ms                             |       6                          |       24.33 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        3.90 ms                             |       3                          |       11.71 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.86 ms                             |       3                          |       11.59 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.17 ms                             |       2                          |        8.33 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.14 ms                             |       2                          |        8.29 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.14 ms                             |       2                          |        8.29 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        3.89 ms                             |       1                          |        3.89 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.86 ms                             |       1                          |        3.86 ms                             | 
  ├ sirius::inner                                                       |                         4.19 ms            |                   3              |                        12.58 ms            | 
  └ sirius::finalize                                                    |      369.64 ms →      352.96 ms   (-4.51%) |       1   →       1              |      369.64 ms →      352.96 ms   (-4.51%) | 
  ====================================================================================================================================================================================================
```
