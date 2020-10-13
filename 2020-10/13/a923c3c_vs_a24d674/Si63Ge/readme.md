# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       77.48 s  →       71.90 s    (-7.21%) |       1   →       1              |       77.48 s  →       71.90 s    (-7.21%) | 
  ├ sirius::initialize                                                  |        2.89 s  →        2.89 s    (-0.08%) |       1   →       1              |        2.89 s  →        2.89 s    (-0.08%) | 
  ├ sirius::Simulation_context::initialize                              |        3.95 s  →        3.65 s    (-7.65%) |       1   →       1              |        3.95 s  →        3.65 s    (-7.65%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       53.14 ms →        1.58 ms  (-97.02%) |       1   →       1              |       53.14 ms →        1.58 ms  (-97.02%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      369.12 ms →      190.02 ms  (-48.52%) |       1   →       1              |      369.12 ms →      190.02 ms  (-48.52%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      174.80 ms →       85.55 ms  (-51.06%) |       2   →       2              |      349.60 ms →      171.10 ms  (-51.06%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.44 ms →       18.83 ms   (-3.12%) |       1   →       1              |       19.44 ms →       18.83 ms   (-3.12%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        4.96 ms  (+36.14%) |       1   →       1              |        3.65 ms →        4.96 ms  (+36.14%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       15.74 ms →       13.80 ms  (-12.30%) |       1   →       1              |       15.74 ms →       13.80 ms  (-12.30%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       15.66 ms →       13.74 ms  (-12.27%) |       1   →       1              |       15.66 ms →       13.74 ms  (-12.27%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.86 ms →        2.75 ms   (-3.77%) |       1   →       1              |        2.86 ms →        2.75 ms   (-3.77%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      518.93 μs →      495.52 μs   (-4.51%) |       1   →       1              |      518.93 μs →      495.52 μs   (-4.51%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.28 μs →       15.16 μs  (-12.27%) |       1   →       1              |       17.28 μs →       15.16 μs  (-12.27%) | 
  │ └ sirius::Simulation_context::update                                |        3.44 s  →        3.24 s    (-5.74%) |       1   →       1              |        3.44 s  →        3.24 s    (-5.74%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.82 ms →        6.99 ms   (+2.50%) |       1   →       1              |        6.82 ms →        6.99 ms   (+2.50%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.46 ms →        3.65 ms   (+5.38%) |       1   →       1              |        3.46 ms →        3.65 ms   (+5.38%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.30 ms   (-0.05%) |       1   →       1              |        3.30 ms →        3.30 ms   (-0.05%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.25 ms   (-0.04%) |       1   →       1              |        3.26 ms →        3.25 ms   (-0.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.71 ms   (+0.24%) |       1   →       1              |        2.70 ms →        2.71 ms   (+0.24%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      519.27 μs →      510.63 μs   (-1.66%) |       1   →       1              |      519.27 μs →      510.63 μs   (-1.66%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.31 μs →       14.24 μs   (-0.46%) |       1   →       1              |       14.31 μs →       14.24 μs   (-0.46%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.59 ms →      212.70 ms   (-0.42%) |       2   →       2              |      427.18 ms →      425.40 ms   (-0.42%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.63 ms →       15.16 ms   (-2.98%) |       2   →       2              |       31.26 ms →       30.32 ms   (-2.98%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.35 ms →       13.26 ms   (-0.68%) |       1   →       1              |       13.35 ms →       13.26 ms   (-0.68%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.43 ms →       56.32 ms   (-0.20%) |       2   →       2              |      112.85 ms →      112.63 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.15 ms →       45.19 ms   (+0.10%) |       2   →       2              |       90.29 ms →       90.38 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.60 ms →       60.44 ms   (-0.25%) |       4   →       4              |      242.38 ms →      241.78 ms   (-0.25%) | 
  │   ├ sddk::Gvec::init                                                |       96.77 ms →       92.53 ms   (-4.38%) |       2   →       2              |      193.53 ms →      185.05 ms   (-4.38%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.48 ms →       69.27 ms   (-3.09%) |       2   →       2              |      142.96 ms →      138.55 ms   (-3.09%) | 
+ │   ├ sddk::Gvec_shells                                               |      109.84 ms →       98.01 ms  (-10.77%) |       1   →       1              |      109.84 ms →       98.01 ms  (-10.77%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        1.95 ms   (-0.66%) |       1   →       1              |        1.96 ms →        1.95 ms   (-0.66%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      555.68 ms →      465.99 ms  (-16.14%) |       2   →       2              |        1.11 s  →      931.98 ms  (-16.14%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      148.40 ms →      139.36 ms   (-6.09%) |       1   →       1              |      148.40 ms →      139.36 ms   (-6.09%) | 
- │ ├ sirius::K_point::K_point                                          |        1.22 μs →        2.60 μs (+112.38%) |       4   →       4              |        4.89 μs →       10.39 μs (+112.38%) | 
  │ └ sirius::K_point_set::initialize                                   |      148.33 ms →      139.27 ms   (-6.10%) |       1   →       1              |      148.33 ms →      139.27 ms   (-6.10%) | 
  │   └ sirius::K_point::initialize                                     |       30.40 ms →       27.96 ms   (-8.00%) |       1   →       1              |       30.40 ms →       27.96 ms   (-8.00%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       12.06 ms →       11.00 ms   (-8.73%) |       1   →       1              |       12.06 ms →       11.00 ms   (-8.73%) | 
  │     │ └ sddk::Gvec::init                                            |        5.32 ms →        5.00 ms   (-6.00%) |       1   →       1              |        5.32 ms →        5.00 ms   (-6.00%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        6.92 μs →        7.40 μs   (+6.95%) |       1   →       1              |        6.92 μs →        7.40 μs   (+6.95%) | 
  │     └ sirius::K_point::update                                       |       15.01 ms →       14.09 ms   (-6.11%) |       1   →       1              |       15.01 ms →       14.09 ms   (-6.11%) | 
  │       └ sirius::Beta_projectors                                     |       10.60 ms →       10.15 ms   (-4.31%) |       1   →       1              |       10.60 ms →       10.15 ms   (-4.31%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.63 ms →        8.20 ms   (-5.02%) |       1   →       1              |        8.63 ms →        8.20 ms   (-5.02%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms →        2.53 ms   (-1.38%) |       2   →       2              |        5.14 ms →        5.07 ms   (-1.38%) | 
  ├ sirius::Potential                                                   |       51.39 ms →       52.98 ms   (+3.09%) |       1   →       1              |       51.39 ms →       52.98 ms   (+3.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.94 ms →        2.92 ms   (-0.71%) |       6   →       6              |       17.65 ms →       17.53 ms   (-0.71%) | 
  │ └ sirius::Potential::update                                         |       33.25 ms →       34.82 ms   (+4.73%) |       1   →       1              |       33.25 ms →       34.82 ms   (+4.73%) | 
  │   └ sirius::Potential::generate_local_potential                     |       32.83 ms →       34.44 ms   (+4.90%) |       1   →       1              |       32.83 ms →       34.44 ms   (+4.90%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.26 ms →       26.57 ms   (+5.18%) |       1   →       1              |       25.26 ms →       26.57 ms   (+5.18%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.28 ms →        7.33 ms   (+0.74%) |       1   →       1              |        7.28 ms →        7.33 ms   (+0.74%) | 
  ├ sirius::Density                                                     |       42.38 ms →       39.86 ms   (-5.94%) |       1   →       1              |       42.38 ms →       39.86 ms   (-5.94%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.83 ms   (+0.70%) |       2   →       2              |        5.63 ms →        5.67 ms   (+0.70%) | 
  │ └ sirius::Density::update                                           |       36.61 ms →       34.05 ms   (-6.99%) |       1   →       1              |       36.61 ms →       34.05 ms   (-6.99%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.40 ms →       33.73 ms   (-7.33%) |       1   →       1              |       36.40 ms →       33.73 ms   (-7.33%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        76.58 μs            |                   1              |                        76.58 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       28.64 ms →       26.39 ms   (-7.88%) |       1   →       1              |       28.64 ms →       26.39 ms   (-7.88%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.46 ms →        6.96 ms   (-6.75%) |       1   →       1              |        7.46 ms →        6.96 ms   (-6.75%) | 
  ├ sirius::Density::initial_density                                    |       59.44 ms →       59.02 ms   (-0.71%) |       1   →       1              |       59.44 ms →       59.02 ms   (-0.71%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.92 ms →       26.76 ms   (-4.15%) |       1   →       1              |       27.92 ms →       26.76 ms   (-4.15%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.23 ms →        7.05 ms  (+13.18%) |       2   →       2              |       12.46 ms →       14.10 ms  (+13.18%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.56 ms →        4.57 ms  (-17.76%) |       1   →       1              |        5.56 ms →        4.57 ms  (-17.76%) | 
  ├ sirius::Potential::generate                                         |      364.61 ms →      368.57 ms   (+1.08%) |       1   →       1              |      364.61 ms →      368.57 ms   (+1.08%) | 
  │ ├ sirius::Potential::poisson                                        |       39.16 ms →       41.43 ms   (+5.81%) |       1   →       1              |       39.16 ms →       41.43 ms   (+5.81%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.83 ms →       10.86 ms  (+38.67%) |       1   →       1              |        7.83 ms →       10.86 ms  (+38.67%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.00 ms →        4.84 ms   (-3.21%) |       1   →       1              |        5.00 ms →        4.84 ms   (-3.21%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.64 ms   (+0.15%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.15%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.63 ms   (+0.02%) |       1   →       1              |        4.63 ms →        4.63 ms   (+0.02%) | 
  │ ├ sirius::Periodic_function::add                                    |      773.76 μs →      777.81 μs   (+0.52%) |       2   →       2              |        1.55 ms →        1.56 ms   (+0.52%) | 
  │ ├ sirius::Potential::xc                                             |       50.39 ms →       51.65 ms   (+2.50%) |       1   →       1              |       50.39 ms →       51.65 ms   (+2.50%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.39 ms →       50.46 ms   (+0.13%) |       1   →       1              |       50.39 ms →       50.46 ms   (+0.13%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.58 ms   (+1.98%) |       2   →       2              |        5.06 ms →        5.16 ms   (+1.98%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.85 ms →        4.57 ms   (-5.66%) |       1   →       1              |        4.85 ms →        4.57 ms   (-5.66%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.29 ms →        2.84 ms  (-13.54%) |       1   →       1              |        3.29 ms →        2.84 ms  (-13.54%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.82 ms →      269.67 ms   (+0.31%) |       1   →       1              |      268.82 ms →      269.67 ms   (+0.31%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      152.00 ns →      280.00 ns  (+84.21%) |       1   →       1              |      152.00 ns →      280.00 ns  (+84.21%) | 
+ ├ sirius::Hamiltonian0                                                |        7.68 ms →        6.31 ms  (-17.87%) |       1   →       1              |        7.68 ms →        6.31 ms  (-17.87%) | 
+ │ ├ sirius::Local_operator                                            |        6.98 ms →        5.84 ms  (-16.37%) |       1   →       1              |        6.98 ms →        5.84 ms  (-16.37%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.76 ms   (+0.23%) |       1   →       1              |        2.75 ms →        2.76 ms   (+0.23%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.18 ms →        2.34 ms  (-26.29%) |       1   →       1              |        3.18 ms →        2.34 ms  (-26.29%) | 
+ │ ├ sirius::Non_local_operator                                        |      204.69 μs →       71.22 μs  (-65.21%) |       2   →       2              |      409.38 μs →      142.44 μs  (-65.21%) | 
  │ ├ sirius::D_operator::initialize                                    |      118.71 μs →      123.87 μs   (+4.35%) |       1   →       1              |      118.71 μs →      123.87 μs   (+4.35%) | 
- │ └ sirius::Q_operator::initialize                                    |       93.11 μs →      123.44 μs  (+32.57%) |       1   →       1              |       93.11 μs →      123.44 μs  (+32.57%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.27 s    (-0.43%) |       1   →       1              |        1.27 s  →        1.27 s    (-0.43%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       64.20 ms →       46.98 ms  (-26.83%) |       1   →       1              |       64.20 ms →       46.98 ms  (-26.83%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      316.01 μs →      376.21 μs  (+19.05%) |       1   →       1              |      316.01 μs →      376.21 μs  (+19.05%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       63.88 ms →       46.59 ms  (-27.06%) |       1   →       1              |       63.88 ms →       46.59 ms  (-27.06%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.21 s  →        1.22 s    (+0.97%) |       1   →       1              |        1.21 s  →        1.22 s    (+0.97%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       89.21 ms →       91.99 ms   (+3.12%) |       4   →       4              |      356.85 ms →      367.98 ms   (+3.12%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.04 ms →       37.90 ms   (+2.32%) |       1   →       1              |       37.04 ms →       37.90 ms   (+2.32%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.04 ms →        7.88 ms  (+11.86%) |       1   →       1              |        7.04 ms →        7.88 ms  (+11.86%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      386.31 ms →      381.75 ms   (-1.18%) |       1   →       1              |      386.31 ms →      381.75 ms   (-1.18%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      314.61 ms →      270.63 ms  (-13.98%) |       1   →       1              |      314.61 ms →      270.63 ms  (-13.98%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.46 μs →        4.64 μs   (+4.17%) |       1   →       1              |        4.46 μs →        4.64 μs   (+4.17%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.47 μs →        3.41 μs   (-1.53%) |       1   →       1              |        3.47 μs →        3.41 μs   (-1.53%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      469.00 ns →      503.00 ns   (+7.25%) |       1   →       1              |      469.00 ns →      503.00 ns   (+7.25%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      876.00 ns →      649.00 ns  (-25.91%) |       1   →       1              |      876.00 ns →      649.00 ns  (-25.91%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::generate                        |        7.86 ms →        3.06 ms  (-61.02%) |       1   →       1              |        7.86 ms →        3.06 ms  (-61.02%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.27 ms →       39.29 ms  (+84.72%) |       1   →       1              |       21.27 ms →       39.29 ms  (+84.72%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.26 ms →       34.36 ms  (+61.65%) |       2   →       2              |       42.52 ms →       68.73 ms  (+61.65%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.34 ms →        6.56 ms  (-57.24%) |       2   →       2              |       30.67 ms →       13.11 ms  (-57.24%) | 
  │ │ │ ├ sddk::inner                                                   |       15.13 ms                             |       2                          |       30.25 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       25.84 μs                             |       2                          |       51.68 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                         6.34 ms            |                   2              |                        12.69 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        20.00 ns            |                   2              |                        40.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                         6.19 ms            |                   2              |                        12.38 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        20.00 ns            |                   2              |                        40.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      180.91 ms →      200.02 ms  (+10.56%) |       1   →       1              |      180.91 ms →      200.02 ms  (+10.56%) | 
  │ │ ├ sddk::transform                                                 |        2.82 ms                             |       1                          |        2.82 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.50 μs                             |       1                          |       14.50 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       17.38 μs                             |       1                          |       17.38 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         4.81 ms            |                   1              |                         4.81 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         4.80 ms            |                   1              |                         4.80 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      435.00 ns →      526.00 ns  (+20.92%) |       1   →       1              |      435.00 ns →      526.00 ns  (+20.92%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       67.35 s  →       62.24 s    (-7.59%) |       1   →       1              |       67.35 s  →       62.24 s    (-7.59%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms →        2.44 ms   (+0.23%) |      19   →      19              |       46.18 ms →       46.28 ms   (+0.23%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.35 s  →        3.26 s    (-2.69%) |      20   →      19     (-5.00%) |       67.09 s  →       62.02 s    (-7.55%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.58 ms →        5.54 ms   (-0.58%) |      20   →      19     (-5.00%) |      111.51 ms →      105.32 ms   (-5.55%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.84 ms →        4.73 ms   (-2.39%) |      20   →      19     (-5.00%) |       96.87 ms →       89.82 ms   (-7.27%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      556.56 μs →      566.75 μs   (+1.83%) |      20   →      19     (-5.00%) |       11.13 ms →       10.77 ms   (-3.26%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.89 ms →        2.97 ms   (+2.57%) |      20   →      19     (-5.00%) |       57.83 ms →       56.35 ms   (-2.56%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      224.38 μs →      266.74 μs  (+18.88%) |      40   →      38     (-5.00%) |        8.98 ms →       10.14 ms  (+12.93%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      108.61 μs →      114.98 μs   (+5.87%) |      20   →      19     (-5.00%) |        2.17 ms →        2.18 ms   (+0.57%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       95.82 μs →       88.96 μs   (-7.15%) |      20   →      19     (-5.00%) |        1.92 ms →        1.69 ms  (-11.80%) | 
  │ │ ├ sirius::Band::solve                                             |        2.12 s  →        2.03 s    (-4.33%) |      20   →      19     (-5.00%) |       42.50 s  →       38.62 s    (-9.11%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      196.87 μs →      253.17 μs  (+28.60%) |      20   →      19     (-5.00%) |        3.94 ms →        4.81 ms  (+22.17%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      187.63 μs →      243.37 μs  (+29.71%) |      20   →      19     (-5.00%) |        3.75 ms →        4.62 ms  (+23.23%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.25 μs →        7.35 μs   (+1.41%) |      20   →      19     (-5.00%) |      145.03 μs →      139.71 μs   (-3.66%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.98 s  →        1.97 s    (-0.37%) |      20   →      19     (-5.00%) |       39.52 s  →       37.41 s    (-5.35%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.85 ms →       77.34 ms  (-19.31%) |      20   →      19     (-5.00%) |        1.92 s  →        1.47 s   (-23.34%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.43 ms →        7.98 ms  (-30.22%) |     120   →     114     (-5.00%) |        1.37 s  →      909.60 ms  (-33.71%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.07 ms →       19.10 ms  (+11.87%) |      20   →      19     (-5.00%) |      341.43 ms →      362.86 ms   (+6.27%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      480.22 μs →      470.94 μs   (-1.93%) |      20   →      19     (-5.00%) |        9.60 ms →        8.95 ms   (-6.84%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.09 ms →        8.86 ms   (+9.53%) |      40   →      38     (-5.00%) |      323.49 ms →      336.60 ms   (+4.05%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.86 s    (+0.47%) |      20   →      19     (-5.00%) |       37.12 s  →       35.43 s    (-4.55%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       66.60 ms →       52.45 ms  (-21.24%) |     250   →     356    (+42.40%) |       16.65 s  →       18.67 s   (+12.15%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       38.51 ms →       29.64 ms  (-23.05%) |     250   →     356    (+42.40%) |        9.63 s  →       10.55 s    (+9.57%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.39 μs →        2.09 μs  (-12.20%) |     250   →     356    (+42.40%) |      596.44 μs →      745.68 μs  (+25.02%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.95 μs →        1.78 μs   (-8.85%) |     250   →     356    (+42.40%) |      487.75 μs →      633.07 μs  (+29.79%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      427.24 ns →      484.45 ns  (+13.39%) |     250   →     356    (+42.40%) |      106.81 μs →      172.46 μs  (+61.47%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      620.40 ns →      646.56 ns   (+4.22%) |     250   →     356    (+42.40%) |      155.10 μs →      230.17 μs  (+48.40%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.06 ms →        2.96 ms   (-3.32%) |     250   →     356    (+42.40%) |      764.38 ms →        1.05 s   (+37.67%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.59 ms →        3.19 ms  (-11.00%) |     250   →     356    (+42.40%) |      896.35 ms →        1.14 s   (+26.74%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       10.71 ms →        8.32 ms  (-22.28%) |     500   →     712    (+42.40%) |        5.36 s  →        5.93 s   (+10.67%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        8.49 ms →        6.66 ms  (-21.54%) |     250   →     356    (+42.40%) |        2.12 s  →        2.37 s   (+11.72%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.31 ms                             |     480                          |      629.68 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.27 μs                             |     480                          |       12.61 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.12 ms            |                 693              |                       773.11 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        56.86 ns            |                 693              |                        39.41 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       953.66 μs            |                 693              |                       660.89 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        45.70 ns            |                 693              |                        31.67 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      184.91 μs →      136.10 μs  (-26.40%) |     250   →     356    (+42.40%) |       46.23 ms →       48.45 ms   (+4.81%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.87 ms →        2.11 ms  (-26.53%) |     250   →     356    (+42.40%) |      716.81 ms →      749.91 ms   (+4.62%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.17 ms                             |     230                          |      728.98 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.84 μs                             |     230                          |        5.02 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        8.72 μs                             |     690                          |        6.01 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.37 ms            |                 337              |                       798.83 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       789.30 μs            |                1.01 K            |                       797.98 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.76 ms →        1.49 ms  (-15.60%) |     250   →     356    (+42.40%) |      440.55 ms →      529.45 ms  (+20.18%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.55 ms                             |     250                          |      388.25 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.78 μs                             |     250                          |        6.70 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.41 ms            |                 356              |                       503.65 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        40.93 ns            |                 356              |                        14.57 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.25 ms            |                 356              |                       445.72 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        38.99 ns            |                 356              |                        13.88 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       67.54 ms →       35.06 ms  (-48.09%) |     250   →     356    (+42.40%) |       16.89 s  →       12.48 s   (-26.08%) | 
- │ │ │ │   ├ sirius::residuals                                         |        3.43 ms →        2.83 ms  (-17.49%) |     245   →     340    (+38.78%) |      840.41 ms →      962.35 ms  (+14.51%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.13 ms                             |     231                          |      492.49 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.45 μs                             |     231                          |        4.03 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       11.41 μs                             |     462                          |        5.27 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.35 ms            |                 337              |                       453.60 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       671.54 μs            |                 674              |                       452.62 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.43 ms →        1.40 ms   (-2.13%) |     231   →     337    (+45.89%) |      330.44 ms →      471.80 ms  (+42.78%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.86 ms →        7.48 ms   (+9.06%) |      25   →      54   (+116.00%) |      171.43 ms →      403.86 ms (+135.58%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.63 ms                             |      30                          |      168.88 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       11.25 μs                             |      30                          |      337.55 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       12.36 μs                             |      35                          |      432.67 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         4.49 ms            |                  89              |                       399.42 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         3.22 ms            |                 124              |                       399.25 ms            | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      391.00 ns →      377.84 ns   (-3.37%) |      20   →      19     (-5.00%) |        7.82 μs →        7.18 μs   (-8.20%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.77 μs →       19.56 μs  (-14.09%) |      20   →      19     (-5.00%) |      455.46 μs →      371.71 μs  (-18.39%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms →        1.52 ms   (+1.57%) |      20   →      19     (-5.00%) |       29.87 ms →       28.82 ms   (-3.51%) | 
  │ │ ├ sirius::Density::generate                                       |      575.40 ms →      572.27 ms   (-0.54%) |      20   →      19     (-5.00%) |       11.51 s  →       10.87 s    (-5.52%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.97 ms →      401.25 ms   (-0.18%) |      20   →      19     (-5.00%) |        8.04 s  →        7.62 s    (-5.17%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.68 μs →        8.33 μs   (+8.44%) |      20   →      19     (-5.00%) |      153.69 μs →      158.33 μs   (+3.02%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.02 μs →        7.80 μs  (+10.98%) |      20   →      19     (-5.00%) |      140.47 μs →      148.11 μs   (+5.43%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       41.44 ms →       38.05 ms   (-8.20%) |      20   →      19     (-5.00%) |      828.89 ms →      722.87 ms  (-12.79%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.65 μs →        7.70 μs   (+0.63%) |      20   →      19     (-5.00%) |      153.04 μs →      146.30 μs   (-4.40%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.93 ms →        6.22 ms  (-10.26%) |      20   →      19     (-5.00%) |      138.51 ms →      118.09 ms  (-14.74%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       33.47 ms →       30.78 ms   (-8.03%) |      20   →      19     (-5.00%) |      669.39 ms →      584.86 ms  (-12.63%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      547.15 ns →      621.74 ns  (+13.63%) |      20   →      19     (-5.00%) |       10.94 μs →       11.81 μs   (+7.95%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.58 ms →      108.01 ms   (+3.29%) |      20   →      19     (-5.00%) |        2.09 s  →        2.05 s    (-1.88%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        2.08 ms   (-7.56%) |      20   →      19     (-5.00%) |       44.97 ms →       39.49 ms  (-12.19%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      208.82 ms →      215.79 ms   (+3.34%) |      20   →      19     (-5.00%) |        4.18 s  →        4.10 s    (-1.83%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      208.59 ms →      215.58 ms   (+3.35%) |      20   →      19     (-5.00%) |        4.17 s  →        4.10 s    (-1.82%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      144.60 ms →      143.35 ms   (-0.87%) |      20   →      19     (-5.00%) |        2.89 s  →        2.72 s    (-5.82%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      144.60 ms →      143.35 ms   (-0.87%) |      20   →      19     (-5.00%) |        2.89 s  →        2.72 s    (-5.82%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       61.37 ms →       58.26 ms   (-5.07%) |      20   →      19     (-5.00%) |        1.23 s  →        1.11 s    (-9.81%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.02 ms →       71.81 ms   (+5.58%) |      20   →      19     (-5.00%) |        1.36 s  →        1.36 s    (+0.30%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.57 ms →       12.62 ms  (-13.36%) |      20   →      19     (-5.00%) |      291.36 ms →      239.82 ms  (-17.69%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       24.09 ms →       23.69 ms   (-1.64%) |      20   →      19     (-5.00%) |      481.70 ms →      450.13 ms   (-6.55%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.73 ms →        3.98 ms  (-15.97%) |      20   →      19     (-5.00%) |       94.66 ms →       75.56 ms  (-20.18%) | 
  │ │ ├ sirius::Density::mix                                            |      134.18 ms →      134.02 ms   (-0.12%) |      20   →      19     (-5.00%) |        2.68 s  →        2.55 s    (-5.11%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      928.67 μs →      284.21 μs  (-69.40%) |      20   →      19     (-5.00%) |       18.57 ms →        5.40 ms  (-70.93%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.88 ms →        4.96 ms   (+1.58%) |     244   →     229     (-6.15%) |        1.19 s  →        1.14 s    (-4.67%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.83 ms   (+0.19%) |     244   →     229     (-6.15%) |        1.18 s  →        1.11 s    (-5.97%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.83 ms   (+0.19%) |     244   →     229     (-6.15%) |        1.18 s  →        1.11 s    (-5.97%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.67 ms →        4.71 ms  (-29.37%) |      20   →      19     (-5.00%) |      133.43 ms →       89.53 ms  (-32.90%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.87 ms →        4.05 ms  (-31.10%) |      20   →      19     (-5.00%) |      117.48 ms →       76.90 ms  (-34.54%) | 
  │ │ ├ sirius::Potential::generate                                     |      358.31 ms →      361.49 ms   (+0.89%) |      20   →      19     (-5.00%) |        7.17 s  →        6.87 s    (-4.16%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       39.47 ms →       41.13 ms   (+4.19%) |      20   →      19     (-5.00%) |      789.40 ms →      781.38 ms   (-1.02%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.35 ms →       10.73 ms  (+28.55%) |      20   →      19     (-5.00%) |      166.99 ms →      203.93 ms  (+22.12%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.82 ms →        4.73 ms   (-1.84%) |      20   →      19     (-5.00%) |       96.40 ms →       89.90 ms   (-6.75%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (-0.10%) |      20   →      19     (-5.00%) |       92.60 ms →       87.88 ms   (-5.10%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.62 ms   (-0.10%) |      20   →      19     (-5.00%) |       92.58 ms →       87.87 ms   (-5.10%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      751.33 μs →      789.21 μs   (+5.04%) |      40   →      38     (-5.00%) |       30.05 ms →       29.99 ms   (-0.21%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.19 ms →       45.11 ms   (+2.08%) |      20   →      19     (-5.00%) |      883.83 ms →      857.06 ms   (-3.03%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.19 ms →       43.91 ms   (-0.62%) |      20   →      19     (-5.00%) |      883.75 ms →      834.38 ms   (-5.59%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      667.40 μs →      685.34 μs   (+2.69%) |      40   →      38     (-5.00%) |       26.70 ms →       26.04 ms   (-2.45%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.91 ms →        4.56 ms   (-7.26%) |      20   →      19     (-5.00%) |       98.26 ms →       86.57 ms  (-11.90%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.21 ms →        3.41 ms   (+6.29%) |      20   →      19     (-5.00%) |       64.21 ms →       64.84 ms   (+0.98%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.51 ms →      268.80 ms   (+0.11%) |      20   →      19     (-5.00%) |        5.37 s  →        5.11 s    (-4.90%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      220.65 ns →      309.42 ns  (+40.23%) |      20   →      19     (-5.00%) |        4.41 μs →        5.88 μs  (+33.22%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       98.29 ms →       99.11 ms   (+0.83%) |      20   →      19     (-5.00%) |        1.97 s  →        1.88 s    (-4.21%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       98.29 ms →       99.10 ms   (+0.83%) |      20   →      19     (-5.00%) |        1.97 s  →        1.88 s    (-4.21%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.30 ms →       14.24 ms   (-6.91%) |      20   →      19     (-5.00%) |      305.94 ms →      270.57 ms  (-11.56%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       67.85 ms →       71.64 ms   (+5.58%) |      20   →      19     (-5.00%) |        1.36 s  →        1.36 s    (+0.30%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.51 ms →       12.60 ms  (-13.17%) |      20   →      19     (-5.00%) |      290.26 ms →      239.42 ms  (-17.51%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.96 ms →        4.04 ms   (+1.86%) |      20   →      19     (-5.00%) |       79.29 ms →       76.73 ms   (-3.23%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.70 ms →        4.82 ms   (+2.69%) |     140   →     133     (-5.00%) |      657.42 ms →      641.35 ms   (-2.44%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.59 ms →        4.58 ms   (-0.43%) |     140   →     133     (-5.00%) |      643.29 ms →      608.50 ms   (-5.41%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.59 ms →        4.57 ms   (-0.43%) |     140   →     133     (-5.00%) |      643.18 ms →      608.41 ms   (-5.41%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.77 ms →        4.95 ms   (+3.79%) |      60   →      57     (-5.00%) |      286.31 ms →      282.29 ms   (-1.40%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.77 ms →        4.95 ms   (+3.77%) |      60   →      57     (-5.00%) |      285.96 ms →      281.91 ms   (-1.42%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.92 ms →        4.54 ms   (-7.73%) |      20   →      19     (-5.00%) |       98.31 ms →       86.18 ms  (-12.34%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.85 μs →       76.26 μs   (+0.54%) |      20   →      19     (-5.00%) |        1.52 ms →        1.45 ms   (-4.49%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.88 μs →       71.37 μs   (+0.69%) |      20   →      19     (-5.00%) |        1.42 ms →        1.36 ms   (-4.34%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.77 ms →        5.63 ms   (-2.58%) |       2   →       2              |       11.55 ms →       11.25 ms   (-2.58%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.83 ms →        4.57 ms   (-5.50%) |       6   →       6              |       29.00 ms →       27.40 ms   (-5.50%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.83 ms →        4.56 ms   (-5.52%) |       6   →       6              |       28.98 ms →       27.38 ms   (-5.52%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.83 ms →        4.56 ms   (-5.55%) |       6   →       6              |       28.97 ms →       27.37 ms   (-5.55%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.98 ms →        4.94 ms   (-0.71%) |       3   →       3              |       14.93 ms →       14.82 ms   (-0.71%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.97 ms →        4.93 ms   (-0.73%) |       3   →       3              |       14.91 ms →       14.80 ms   (-0.73%) | 
  ├ sirius::Periodic_function|inner                                     |        4.80 ms →        4.54 ms   (-5.37%) |       2   →       2              |        9.59 ms →        9.08 ms   (-5.37%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.79 ms →        4.53 ms   (-5.38%) |       2   →       2              |        9.58 ms →        9.07 ms   (-5.38%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        4.53 ms   (-5.38%) |       2   →       2              |        9.58 ms →        9.07 ms   (-5.38%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.97 ms →        4.92 ms   (-1.02%) |       1   →       1              |        4.97 ms →        4.92 ms   (-1.02%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.97 ms →        4.92 ms   (-1.03%) |       1   →       1              |        4.97 ms →        4.92 ms   (-1.03%) | 
+ └ sirius::finalize                                                    |      937.23 ms →      153.36 ms  (-83.64%) |       1   →       1              |      937.23 ms →      153.36 ms  (-83.64%) | 
  ====================================================================================================================================================================================================
```
