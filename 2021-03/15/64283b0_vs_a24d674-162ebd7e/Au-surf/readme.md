# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 64283b0bdde21ce92493e897e38c4105358cbbe3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      151.07 s  →      123.61 s   (-18.17%) |       1   →       1              |      151.07 s  →      123.61 s   (-18.17%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.78 s    (+0.84%) |       1   →       1              |        2.75 s  →        2.78 s    (+0.84%) | 
  ├ sirius::Simulation_context::initialize                              |        2.05 s  →        2.00 s    (-2.31%) |       1   →       1              |        2.05 s  →        2.00 s    (-2.31%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      245.47 μs →      267.66 μs   (+9.04%) |       1   →       1              |      245.47 μs →      267.66 μs   (+9.04%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       65.31 ms →       60.49 ms   (-7.38%) |       1   →       1              |       65.31 ms →       60.49 ms   (-7.38%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       42.17 ms →       35.13 ms  (-16.69%) |       1   →       1              |       42.17 ms →       35.13 ms  (-16.69%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.08 ms →       25.21 ms   (+9.20%) |       1   →       1              |       23.08 ms →       25.21 ms   (+9.20%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.45 ms →       10.28 ms   (-1.67%) |       1   →       1              |       10.45 ms →       10.28 ms   (-1.67%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       12.60 ms →       14.90 ms  (+18.25%) |       1   →       1              |       12.60 ms →       14.90 ms  (+18.25%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       12.05 ms →       14.14 ms  (+17.33%) |       1   →       1              |       12.05 ms →       14.14 ms  (+17.33%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |       11.83 ms →       13.92 ms  (+17.66%) |       1   →       1              |       11.83 ms →       13.92 ms  (+17.66%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      205.77 μs →      205.48 μs   (-0.14%) |       1   →       1              |      205.77 μs →      205.48 μs   (-0.14%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.38 μs →        2.56 μs   (+7.49%) |       1   →       1              |        2.38 μs →        2.56 μs   (+7.49%) | 
  │ └ sirius::Simulation_context::update                                |        1.93 s  →        1.89 s    (-2.33%) |       1   →       1              |        1.93 s  →        1.89 s    (-2.33%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.99 ms →       11.15 ms   (+1.53%) |       1   →       1              |       10.99 ms →       11.15 ms   (+1.53%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.89 ms →        7.90 ms   (+0.08%) |       1   →       1              |        7.89 ms →        7.90 ms   (+0.08%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.08 ms →        3.24 ms   (+5.18%) |       1   →       1              |        3.08 ms →        3.24 ms   (+5.18%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.62 ms →        2.71 ms   (+3.46%) |       1   →       1              |        2.62 ms →        2.71 ms   (+3.46%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.41 ms →        2.49 ms   (+3.22%) |       1   →       1              |        2.41 ms →        2.49 ms   (+3.22%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      203.95 μs →      215.89 μs   (+5.86%) |       1   →       1              |      203.95 μs →      215.89 μs   (+5.86%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.20 μs →        1.37 μs  (+14.26%) |       1   →       1              |        1.20 μs →        1.37 μs  (+14.26%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       18.20 ms →       17.35 ms   (-4.64%) |       2   →       2              |       36.39 ms →       34.70 ms   (-4.64%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (-0.21%) |       2   →       2              |        2.20 ms →        2.19 ms   (-0.21%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      956.04 μs →      957.01 μs   (+0.10%) |       1   →       1              |      956.04 μs →      957.01 μs   (+0.10%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.08 ms →        5.08 ms   (-0.10%) |       2   →       2              |       10.16 ms →       10.15 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.67 ms →        3.63 ms   (-0.89%) |       2   →       2              |        7.33 ms →        7.27 ms   (-0.89%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.75 ms →       15.94 ms   (+1.18%) |       4   →       4              |       63.01 ms →       63.76 ms   (+1.18%) | 
  │   ├ sddk::Gvec::init                                                |      158.33 ms →      159.39 ms   (+0.67%) |       2   →       2              |      316.65 ms →      318.78 ms   (+0.67%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      125.22 ms →      126.06 ms   (+0.67%) |       2   →       2              |      250.43 ms →      252.12 ms   (+0.67%) | 
  │   ├ sddk::Gvec_shells                                               |      122.99 ms →      127.22 ms   (+3.44%) |       1   →       1              |      122.99 ms →      127.22 ms   (+3.44%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.03 ms   (-0.23%) |       1   →       1              |        1.03 ms →        1.03 ms   (-0.23%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      218.43 ms →      217.51 ms   (-0.42%) |       1   →       1              |      218.43 ms →      217.51 ms   (-0.42%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       27.38 ms →       26.83 ms   (-2.00%) |       1   →       1              |       27.38 ms →       26.83 ms   (-2.00%) | 
- │ ├ sirius::K_point::K_point                                          |        2.08 μs →        5.35 μs (+157.44%) |       2   →       2              |        4.16 μs →       10.70 μs (+157.44%) | 
  │ └ sirius::K_point_set::initialize                                   |       27.35 ms →       26.79 ms   (-2.06%) |       1   →       1              |       27.35 ms →       26.79 ms   (-2.06%) | 
  │   └ sirius::K_point::initialize                                     |       27.29 ms →       26.73 ms   (-2.05%) |       1   →       1              |       27.29 ms →       26.73 ms   (-2.05%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       20.73 ms →       20.05 ms   (-3.26%) |       1   →       1              |       20.73 ms →       20.05 ms   (-3.26%) | 
  │     │ └ sddk::Gvec::init                                            |        4.90 ms →        5.01 ms   (+2.32%) |       1   →       1              |        4.90 ms →        5.01 ms   (+2.32%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.47 μs                             |       1                          |        8.47 μs                             | 
  │     └ sirius::K_point::update                                       |        4.25 ms →        4.22 ms   (-0.87%) |       1   →       1              |        4.25 ms →        4.22 ms   (-0.87%) | 
  │       └ sirius::Beta_projectors                                     |        1.71 ms →        1.69 ms   (-1.29%) |       1   →       1              |        1.71 ms →        1.69 ms   (-1.29%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      910.44 μs →      884.81 μs   (-2.82%) |       1   →       1              |      910.44 μs →      884.81 μs   (-2.82%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.20 ms                             |       2                          |        4.40 ms                             | 
  ├ sirius::Potential                                                   |       89.80 ms →       94.15 ms   (+4.84%) |       1   →       1              |       89.80 ms →       94.15 ms   (+4.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.41 ms                             |       6                          |       14.49 ms                             | 
  │ └ sirius::Potential::update                                         |       75.00 ms →       78.91 ms   (+5.22%) |       1   →       1              |       75.00 ms →       78.91 ms   (+5.22%) | 
  │   └ sirius::Potential::generate_local_potential                     |       74.84 ms →       78.74 ms   (+5.21%) |       1   →       1              |       74.84 ms →       78.74 ms   (+5.21%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.43 ms →       49.39 ms   (-5.80%) |       1   →       1              |       52.43 ms →       49.39 ms   (-5.80%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       22.22 ms →       11.44 ms  (-48.54%) |       1   →       1              |       22.22 ms →       11.44 ms  (-48.54%) | 
  ├ sirius::Density                                                     |       71.50 ms →       75.77 ms   (+5.97%) |       1   →       1              |       71.50 ms →       75.77 ms   (+5.97%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.71 ms                             |       2                          |        9.41 ms                             | 
  │ └ sirius::Density::update                                           |       61.98 ms →       65.97 ms   (+6.44%) |       1   →       1              |       61.98 ms →       65.97 ms   (+6.44%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.80 ms →       65.79 ms   (+6.46%) |       1   →       1              |       61.80 ms →       65.79 ms   (+6.46%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.17 ms →       52.89 ms   (+1.38%) |       1   →       1              |       52.17 ms →       52.89 ms   (+1.38%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.43 ms →        8.34 ms  (-11.61%) |       1   →       1              |        9.43 ms →        8.34 ms  (-11.61%) | 
  ├ sirius::Density::initial_density                                    |       79.06 ms →       81.25 ms   (+2.78%) |       1   →       1              |       79.06 ms →       81.25 ms   (+2.78%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       51.62 ms →       52.11 ms   (+0.95%) |       1   →       1              |       51.62 ms →       52.11 ms   (+0.95%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.58 ms →        5.89 ms   (+5.49%) |       2   →       2              |       11.16 ms →       11.77 ms   (+5.49%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.29 ms →        4.16 ms   (-3.14%) |       1   →       1              |        4.29 ms →        4.16 ms   (-3.14%) | 
- ├ sirius::Potential::generate                                         |      189.90 ms →      220.77 ms  (+16.26%) |       1   →       1              |      189.90 ms →      220.77 ms  (+16.26%) | 
  │ ├ sirius::Potential::poisson                                        |       64.33 ms →       64.85 ms   (+0.81%) |       1   →       1              |       64.33 ms →       64.85 ms   (+0.81%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.53 ms →        9.45 ms   (-0.84%) |       1   →       1              |        9.53 ms →        9.45 ms   (-0.84%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.54 ms                             |       1                          |        4.54 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.21 ms                             |       1                          |        4.21 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.21 ms                             |       1                          |        4.21 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.89 ms            |                   1              |                         4.89 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      242.58 μs →      202.03 μs  (-16.72%) |       2   →       2              |      485.16 μs →      404.06 μs  (-16.72%) | 
- │ ├ sirius::Potential::xc                                             |       99.12 ms →      127.52 ms  (+28.65%) |       1   →       1              |       99.12 ms →      127.52 ms  (+28.65%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       99.12 ms →      126.48 ms  (+27.60%) |       1   →       1              |       99.12 ms →      126.48 ms  (+27.60%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.24 ms                             |       5                          |       11.22 ms                             | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.46 ms →        2.35 ms   (-4.12%) |       9   →      12    (+33.33%) |       22.10 ms →       28.25 ms  (+27.84%) | 
  │ │   ├ sirius::gradient                                              |        7.47 ms →        8.03 ms   (+7.47%) |       1   →       1              |        7.47 ms →        8.03 ms   (+7.47%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.40 ms                             |       3                          |        7.19 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.76 ms →        2.86 ms   (+3.58%) |       1   →       1              |        2.76 ms →        2.86 ms   (+3.58%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.55 ms                             |       1                          |        2.55 ms                             | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        11.26 ms            |                   2              |                        22.52 ms            | 
- │ │   └ sirius::divergence                                            |       19.73 ms →       20.17 ms   (+2.23%) |       1   →       2   (+100.00%) |       19.73 ms →       40.33 ms (+104.46%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.40 ms                             |       1                          |        2.40 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.22 ms →        3.25 ms   (+0.93%) |       1   →       1              |        3.22 ms →        3.25 ms   (+0.93%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.20 ms →       22.75 ms   (+2.49%) |       1   →       1              |       22.20 ms →       22.75 ms   (+2.49%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      194.00 ns →      215.00 ns  (+10.82%) |       1   →       1              |      194.00 ns →      215.00 ns  (+10.82%) | 
- ├ sirius::Hamiltonian0                                                |       13.76 ms →       15.30 ms  (+11.22%) |       1   →       1              |       13.76 ms →       15.30 ms  (+11.22%) | 
  │ ├ sirius::Local_operator                                            |       13.44 ms →       13.49 ms   (+0.42%) |       1   →       1              |       13.44 ms →       13.49 ms   (+0.42%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.05 ms                             |       1                          |        7.05 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.94 ms →        4.72 ms   (-4.43%) |       1   →       1              |        4.94 ms →        4.72 ms   (-4.43%) | 
  │ ├ sirius::Non_local_operator                                        |       59.40 μs →       60.01 μs   (+1.03%) |       2   →       2              |      118.79 μs →      120.02 μs   (+1.03%) | 
- │ ├ sirius::D_operator::initialize                                    |       79.75 μs →      574.38 μs (+620.26%) |       1   →       1              |       79.75 μs →      574.38 μs (+620.26%) | 
- │ └ sirius::Q_operator::initialize                                    |       67.95 μs →        1.06 ms (+1454.35%) |       1   →       1              |       67.95 μs →        1.06 ms (+1454.35%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.21 s  →        2.22 s    (+0.66%) |       1   →       1              |        2.21 s  →        2.22 s    (+0.66%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.41 ms →        8.42 ms   (+0.15%) |       1   →       1              |        8.41 ms →        8.42 ms   (+0.15%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      251.02 μs →      255.65 μs   (+1.84%) |       1   →       1              |      251.02 μs →      255.65 μs   (+1.84%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.16 ms   (+0.07%) |       1   →       1              |        8.16 ms →        8.16 ms   (+0.07%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.20 s  →        2.21 s    (+0.58%) |       1   →       1              |        2.20 s  →        2.21 s    (+0.58%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       89.95 ms                             |       4                          |      359.79 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.00 ms →       25.87 ms   (+3.51%) |       1   →       1              |       25.00 ms →       25.87 ms   (+3.51%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.42 ms →       14.95 ms   (+3.68%) |       1   →       1              |       14.42 ms →       14.95 ms   (+3.68%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.18 s    (-2.14%) |       1   →       1              |        1.21 s  →        1.18 s    (-2.14%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      984.75 ms →      959.64 ms   (-2.55%) |       1   →       1              |      984.75 ms →      959.64 ms   (-2.55%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      308.42 ms →      299.20 ms   (-2.99%) |       1   →       1              |      308.42 ms →      299.20 ms   (-2.99%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      180.52 ms                             |       1                          |      180.52 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      180.51 ms                             |       1                          |      180.51 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      109.42 ms →      104.47 ms   (-4.52%) |       1   →       1              |      109.42 ms →      104.47 ms   (-4.52%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      177.56 ms                             |       1                          |      177.56 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      177.55 ms                             |       1                          |      177.55 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      166.43 ms →      156.04 ms   (-6.25%) |       1   →       1              |      166.43 ms →      156.04 ms   (-6.25%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      115.81 ms →      105.66 ms   (-8.77%) |       1   →       1              |      115.81 ms →      105.66 ms   (-8.77%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.75 ms →        3.76 ms   (+0.23%) |       1   →       1              |        3.75 ms →        3.76 ms   (+0.23%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.27 ms →       89.52 ms   (-0.83%) |       1   →       1              |       90.27 ms →       89.52 ms   (-0.83%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.44 ms →       11.71 ms   (-5.85%) |       1   →       1              |       12.44 ms →       11.71 ms   (-5.85%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.23 ms →       64.25 ms   (+0.03%) |       2   →       2              |      128.46 ms →      128.49 ms   (+0.03%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       60.30 ms →       83.23 ms  (+38.04%) |       2   →       2              |      120.59 ms →      166.46 ms  (+38.04%) | 
  │ │ │ ├ sddk::inner                                                   |       60.18 ms                             |       2                          |      120.36 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       20.74 μs                             |       2                          |       41.48 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.56 ms                             |       4                          |      102.25 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      682.89 μs                             |       4                          |        2.73 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        7.66 ms                             |       2                          |       15.32 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        83.13 ms            |                   2              |                       166.25 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       145.50 ns            |                   2              |                       291.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        81.66 ms            |                   2              |                       163.32 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       770.50 ns            |                   2              |                         1.54 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.09 ms →      116.78 ms   (+0.60%) |       1   →       1              |      116.09 ms →      116.78 ms   (+0.60%) | 
  │ │ ├ sddk::transform                                                 |       36.02 ms                             |       1                          |       36.02 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       15.06 μs                             |       1                          |       15.06 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       19.84 μs                             |       1                          |       19.84 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        35.31 ms            |                   1              |                        35.31 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.29 ms            |                   1              |                        35.29 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      542.00 ns →      535.00 ns   (-1.29%) |       1   →       1              |      542.00 ns →      535.00 ns   (-1.29%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      142.37 s  →      115.14 s   (-19.12%) |       1   →       1              |      142.37 s  →      115.14 s   (-19.12%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.32 ms                             |      31                          |       71.84 ms                             | 
  │ ├ sirius::Density                                                   |                       109.73 ms            |                   1              |                       109.73 ms            | 
  │ │ └ sirius::Density::update                                         |                       100.16 ms            |                   1              |                       100.16 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        99.97 ms            |                   1              |                        99.97 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        52.97 ms            |                   1              |                        52.97 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         8.26 ms            |                   1              |                         8.26 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.30 s  →        2.55 s   (-22.85%) |      43   →      45     (+4.65%) |      142.07 s  →      114.70 s   (-19.27%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.05 ms →        8.49 ms  (+20.45%) |      43   →      45     (+4.65%) |      302.96 ms →      381.88 ms  (+26.05%) | 
  │ │ │ ├ sirius::Local_operator                                        |        6.71 ms →        6.65 ms   (-0.84%) |      43   →      45     (+4.65%) |      288.48 ms →      299.36 ms   (+3.77%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.49 ms                             |      43                          |       64.05 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.73 ms →        3.65 ms   (-2.19%) |      43   →      45     (+4.65%) |      160.46 ms →      164.25 ms   (+2.36%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       62.13 μs →       61.37 μs   (-1.21%) |      86   →      90     (+4.65%) |        5.34 ms →        5.52 ms   (+3.38%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       80.97 μs →      589.95 μs (+628.61%) |      43   →      45     (+4.65%) |        3.48 ms →       26.55 ms (+662.50%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       71.08 μs →        1.06 ms (+1394.28%) |      43   →      45     (+4.65%) |        3.06 ms →       47.80 ms (+1463.78%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.63 s  →        1.86 s   (-29.37%) |      43   →      45     (+4.65%) |      113.00 s  →       83.53 s   (-26.08%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      231.76 μs →      213.17 μs   (-8.02%) |      43   →      45     (+4.65%) |        9.97 ms →        9.59 ms   (-3.74%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      224.58 μs →      204.06 μs   (-9.14%) |      43   →      45     (+4.65%) |        9.66 ms →        9.18 ms   (-4.91%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.41 μs →        4.85 μs  (-10.25%) |      43   →      45     (+4.65%) |      232.46 μs →      218.34 μs   (-6.07%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.60 s  →        1.82 s   (-30.18%) |      43   →      45     (+4.65%) |      112.01 s  →       81.85 s   (-26.93%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       70.20 ms                             |      43                          |        3.02 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.60 ms                             |     258                          |        1.44 s                              | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.03 ms →        1.64 ms  (-19.30%) |      43   →      45     (+4.65%) |       87.36 ms →       73.78 ms  (-15.55%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      418.34 μs                             |      43                          |       17.99 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      953.59 μs                             |      43                          |       41.00 ms                             | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.51 s  →        1.74 s   (-30.80%) |      43   →      45     (+4.65%) |      107.86 s  →       78.12 s   (-27.58%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.89 ms →      202.61 ms   (-5.72%) |     208   →     209     (+0.48%) |       44.70 s  →       42.35 s    (-5.26%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      152.05 ms →      142.33 ms   (-6.40%) |     208   →     209     (+0.48%) |       31.63 s  →       29.75 s    (-5.95%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.32 ms →       24.90 ms   (-8.86%) |     208   →     209     (+0.48%) |        5.68 s  →        5.20 s    (-8.42%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      660.53 μs                             |     208                          |      137.39 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.18 ms                             |      43                          |      136.93 ms                             | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.19 ms →       19.96 ms  (-10.03%) |     208   →     209     (+0.48%) |        4.61 s  →        4.17 s    (-9.60%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      655.67 μs                             |     208                          |      136.38 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.16 ms                             |      43                          |      135.80 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.34 ms →       31.28 ms   (-8.91%) |     208   →     209     (+0.48%) |        7.14 s  →        6.54 s    (-8.48%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.56 ms →       19.11 ms  (-11.38%) |     208   →     209     (+0.48%) |        4.48 s  →        3.99 s   (-10.96%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.64 ms   (-0.54%) |     208   →     209     (+0.48%) |      551.61 ms →      551.26 ms   (-0.06%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.80 ms →       21.63 ms   (-5.13%) |     208   →     209     (+0.48%) |        4.74 s  →        4.52 s    (-4.68%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.59 ms →        2.24 ms  (-13.60%) |     208   →     209     (+0.48%) |      538.74 ms →      467.69 ms  (-13.19%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.68 ms →       17.99 ms   (-3.69%) |     416   →     418     (+0.48%) |        7.77 s  →        7.52 s    (-3.23%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       82.23 ms →       75.27 ms   (-8.47%) |     208   →     209     (+0.48%) |       17.10 s  →       15.73 s    (-8.03%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.45 ms                             |     373                          |        3.90 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       20.26 μs                             |     373                          |        7.56 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.46 ms                             |     746                          |        3.33 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      102.41 μs                             |     746                          |       76.40 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.30 ms                             |     373                          |      484.94 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                        12.07 ms            |                 373              |                         4.50 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       223.35 ns            |                 373              |                        83.31 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         8.60 ms            |                 373              |                         3.21 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       355.99 ns            |                 373              |                       132.78 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.19 ms →       27.04 ms  (-10.42%) |     208   →     209     (+0.48%) |        6.28 s  →        5.65 s    (-9.99%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms →       15.90 ms   (-2.03%) |     208   →     209     (+0.48%) |        3.38 s  →        3.32 s    (-1.56%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.51 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.11 μs                             |     165                          |        3.48 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       64.27 μs                             |     495                          |       31.82 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        13.74 ms            |                 164              |                         2.25 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.55 ms            |                 492              |                         2.24 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       25.13 ms →       21.47 ms  (-14.56%) |     208   →     209     (+0.48%) |        5.23 s  →        4.49 s   (-14.15%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       20.94 ms                             |     208                          |        4.36 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       45.78 μs                             |     208                          |        9.52 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.91 ms                             |     416                          |        3.29 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      230.78 μs                             |     416                          |       96.00 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        4.61 ms                             |     208                          |      959.58 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        20.48 ms            |                 209              |                         4.28 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       213.00 ns            |                 209              |                        44.52 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        14.70 ms            |                 209              |                         3.07 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       440.85 ns            |                 209              |                        92.14 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      165.21 ms →       38.70 ms  (-76.58%) |     208   →     209     (+0.48%) |       34.36 s  →        8.09 s   (-76.46%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       20.31 ms →       15.10 ms  (-25.62%) |     207   →     204     (-1.45%) |        4.20 s  →        3.08 s   (-26.70%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.06 μs                             |     171                          |        2.92 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       62.49 μs                             |     342                          |       21.37 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        14.09 ms            |                 184              |                         2.59 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         6.85 ms            |                 368              |                         2.52 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        3.79 ms →        1.41 ms  (-62.67%) |     171   →     184     (+7.60%) |      648.14 ms →      260.34 ms  (-59.83%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.16 ms →       50.58 ms   (-1.15%) |      44   →      86    (+95.45%) |        2.25 s  →        4.35 s   (+93.21%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.73 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       13.22 μs                             |      45                          |      595.03 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       16.86 μs                             |      46                          |      775.79 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        33.37 ms            |                 127              |                         4.24 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        25.14 ms            |                 168              |                         4.22 s             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      587.12 ns →      590.40 ns   (+0.56%) |      43   →      45     (+4.65%) |       25.25 μs →       26.57 μs   (+5.24%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       27.41 μs                             |      43                          |        1.18 ms                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        93.96 μs            |                  45              |                         4.23 ms            | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.39 ms →      944.17 μs  (-72.13%) |      43   →      45     (+4.65%) |      145.68 ms →       42.49 ms  (-70.84%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        21.30 μs            |                  45              |                       958.34 μs            | 
  │ │ ├ sirius::Density::generate                                       |      298.49 ms →      294.31 ms   (-1.40%) |      43   →      45     (+4.65%) |       12.84 s  →       13.24 s    (+3.19%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      294.60 ms →      290.17 ms   (-1.50%) |      43   →      45     (+4.65%) |       12.67 s  →       13.06 s    (+3.08%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.86 ms →       62.91 ms   (-7.29%) |      43   →      45     (+4.65%) |        2.92 s  →        2.83 s    (-2.98%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.71 μs                             |      43                          |        2.70 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.20 ms                             |       2                          |        2.40 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       56.63 ms →       51.49 ms   (-9.07%) |      43   →      45     (+4.65%) |        2.43 s  →        2.32 s    (-4.84%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.87 ms →       60.25 ms   (-1.02%) |      43   →      45     (+4.65%) |        2.62 s  →        2.71 s    (+3.58%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.67 μs →        9.82 μs   (+1.63%) |      43   →      45     (+4.65%) |      415.67 μs →      442.09 μs   (+6.36%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.30 ms   (-0.26%) |      43   →      45     (+4.65%) |       99.15 ms →      103.50 ms   (+4.38%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.01 ms →       57.34 ms   (-1.17%) |      43   →      45     (+4.65%) |        2.49 s  →        2.58 s    (+3.43%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.59 ms →        5.92 ms  (-10.11%) |      43   →      45     (+4.65%) |      283.17 ms →      266.39 ms   (-5.93%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      589.07 ns →      519.18 ns  (-11.86%) |      43   →      45     (+4.65%) |       25.33 μs →       23.36 μs   (-7.77%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.36 ms →      104.99 ms   (+0.60%) |      43   →      45     (+4.65%) |        4.49 s  →        4.72 s    (+5.28%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.41 ms →        2.42 ms   (+0.64%) |      43   →      45     (+4.65%) |      103.60 ms →      109.10 ms   (+5.32%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.07 ms →       20.32 ms   (+1.28%) |      43   →      45     (+4.65%) |      862.80 ms →      914.46 ms   (+5.99%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms →       20.15 ms   (+1.28%) |      43   →      45     (+4.65%) |      855.59 ms →      906.84 ms   (+5.99%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      273.42 ns →      284.82 ns   (+4.17%) |      43   →      45     (+4.65%) |       11.76 μs →       12.82 μs   (+9.02%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.28 ms   (+1.85%) |      43   →      45     (+4.65%) |       53.90 ms →       57.45 ms   (+6.59%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.64 ms →        2.86 ms   (+8.55%) |      43   →      45     (+4.65%) |      113.33 ms →      128.73 ms  (+13.59%) | 
  │ │ ├ sirius::inner                                                   |                         4.33 ms            |                 540              |                         2.34 s             | 
+ │ │ ├ sirius::Density::mix                                            |      133.47 ms →      104.15 ms  (-21.97%) |      43   →      45     (+4.65%) |        5.74 s  →        4.69 s   (-18.34%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      253.37 μs →      214.02 μs  (-15.53%) |      43   →      45     (+4.65%) |       10.89 ms →        9.63 ms  (-11.60%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.72 ms →        2.58 ms  (-30.54%) |      43   →      45     (+4.65%) |      159.96 ms →      116.28 ms  (-27.31%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.53 ms →        2.44 ms  (-30.96%) |      43   →      45     (+4.65%) |      151.72 ms →      109.61 ms  (-27.75%) | 
- │ │ ├ sirius::Potential::generate                                     |      185.46 ms →      212.25 ms  (+14.44%) |      43   →      45     (+4.65%) |        7.97 s  →        9.55 s   (+19.77%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.30 ms →       65.15 ms   (+1.31%) |      43   →      45     (+4.65%) |        2.77 s  →        2.93 s    (+6.03%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.66 ms →        9.77 ms   (+1.16%) |      43   →      45     (+4.65%) |      415.46 ms →      439.81 ms   (+5.86%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |        4.38 ms                             |      43                          |      188.38 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |        4.24 ms                             |      43                          |      182.50 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |        4.24 ms                             |      43                          |      182.46 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                         4.87 ms            |                  45              |                       219.19 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      233.66 μs →      201.76 μs  (-13.65%) |      86   →      90     (+4.65%) |       20.09 ms →       18.16 ms   (-9.64%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       95.32 ms →      120.63 ms  (+26.55%) |      43   →      45     (+4.65%) |        4.10 s  →        5.43 s   (+32.43%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       95.32 ms →      119.59 ms  (+25.46%) |      43   →      45     (+4.65%) |        4.10 s  →        5.38 s   (+31.29%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.62 ms                             |     215                          |      348.81 ms                             | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.70 ms →        2.42 ms  (-10.40%) |     387   →     540    (+39.53%) |        1.05 s  →        1.31 s   (+25.03%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.37 ms →        1.85 ms  (-22.01%) |      43   →      45     (+4.65%) |      101.86 ms →       83.14 ms  (-18.38%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      696.65 μs                             |     129                          |       89.87 ms                             | 
+ │ │ │ │   ├ sirius::dot                                               |        2.81 ms →      703.65 μs  (-74.94%) |      43   →      45     (+4.65%) |      120.71 ms →       31.66 ms  (-73.77%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.57 ms                             |      43                          |      110.54 ms                             | 
  │ │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        11.26 ms            |                  90              |                         1.01 s             | 
- │ │ │ │   └ sirius::divergence                                        |       19.93 ms →       19.77 ms   (-0.79%) |      43   →      90   (+109.30%) |      856.82 ms →        1.78 s  (+107.64%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.46 ms                             |      43                          |      105.64 ms                             | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        3.41 ms  (-12.31%) |      43   →      45     (+4.65%) |      167.24 ms →      153.48 ms   (-8.23%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.93 ms →       20.92 ms   (-0.05%) |      43   →      45     (+4.65%) |      899.93 ms →      941.30 ms   (+4.60%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      162.00 ns →      344.47 ns (+112.63%) |      43   →      45     (+4.65%) |        6.97 μs →       15.50 μs (+122.52%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      282.42 ns →      265.51 ns   (-5.99%) |      43   →      45     (+4.65%) |       12.14 μs →       11.95 μs   (-1.61%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms →        2.25 ms   (+0.81%) |      43   →      45     (+4.65%) |       95.91 ms →      101.18 ms   (+5.49%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.25 ms                             |     301                          |        1.28 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.08 ms                             |     301                          |        1.23 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.08 ms                             |     301                          |        1.23 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.01 ms                             |     129                          |      517.36 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.88 ms                             |     129                          |      500.66 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        3.99 ms →        4.13 ms   (+3.46%) |      43   →      45     (+4.65%) |      171.49 ms →      185.67 ms   (+8.27%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      100.80 μs →       12.48 ms (+12284.24%) |      43   →      45     (+4.65%) |        4.33 ms →      561.72 ms (+12860.25%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       97.35 μs →       12.48 ms (+12716.04%) |      43   →      45     (+4.65%) |        4.19 ms →      561.41 ms (+13312.13%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.15 ms →        5.43 ms  (-11.70%) |       2   →       2              |       12.29 ms →       10.85 ms  (-11.70%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.16 ms                             |       6                          |       24.93 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.14 ms                             |       6                          |       24.82 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.14 ms                             |       6                          |       24.82 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |        4.07 ms                             |       3                          |       12.22 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        3.96 ms                             |       3                          |       11.87 ms                             | 
  │ └ sirius::inner                                                     |                         4.33 ms            |                   9              |                        38.94 ms            | 
  ├ sirius::Periodic_function|inner                                     |        4.10 ms                             |       2                          |        8.20 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.09 ms                             |       2                          |        8.18 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.09 ms                             |       2                          |        8.18 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.03 ms                             |       1                          |        4.03 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.86 ms                             |       1                          |        3.86 ms                             | 
  ├ sirius::inner                                                       |                         4.23 ms            |                   3              |                        12.68 ms            | 
  └ sirius::finalize                                                    |      313.45 ms →      321.63 ms   (+2.61%) |       1   →       1              |      313.45 ms →      321.63 ms   (+2.61%) | 
  ====================================================================================================================================================================================================
```
