# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      180.44 s  →      364.27 s  (+101.87%) |       1   →       1              |      180.44 s  →      364.27 s  (+101.87%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.73 s    (+0.92%) |       1   →       1              |        2.70 s  →        2.73 s    (+0.92%) | 
  ├ sirius::Simulation_context::initialize                              |        3.17 s  →        2.93 s    (-7.57%) |       1   →       1              |        3.17 s  →        2.93 s    (-7.57%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      119.99 ms →       24.90 ms  (-79.25%) |       1   →       1              |      119.99 ms →       24.90 ms  (-79.25%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       93.78 ms →      146.26 ms  (+55.96%) |       1   →       1              |       93.78 ms →      146.26 ms  (+55.96%) | 
- │ │ ├ sirius::Atom_type::init                                         |       53.90 ms →      104.03 ms  (+93.02%) |       1   →       1              |       53.90 ms →      104.03 ms  (+93.02%) | 
  │ │ └ sirius::Unit_cell::update                                       |       39.83 ms →       42.08 ms   (+5.65%) |       1   →       1              |       39.83 ms →       42.08 ms   (+5.65%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       25.21 ms →       27.52 ms   (+9.13%) |       1   →       1              |       25.21 ms →       27.52 ms   (+9.13%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.59 ms →       14.53 ms   (-0.36%) |       1   →       1              |       14.59 ms →       14.53 ms   (-0.36%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.86 ms →       13.81 ms   (-0.37%) |       1   →       1              |       13.86 ms →       13.81 ms   (-0.37%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       13.62 ms →       13.57 ms   (-0.39%) |       1   →       1              |       13.62 ms →       13.57 ms   (-0.39%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      226.14 μs →      226.31 μs   (+0.07%) |       1   →       1              |      226.14 μs →      226.31 μs   (+0.07%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.28 μs →        2.33 μs   (+2.19%) |       1   →       1              |        2.28 μs →        2.33 μs   (+2.19%) | 
  │ └ sirius::Simulation_context::update                                |        2.90 s  →        2.70 s    (-7.10%) |       1   →       1              |        2.90 s  →        2.70 s    (-7.10%) | 
  │   ├ sirius::Unit_cell::update                                       |       19.62 ms →       20.24 ms   (+3.16%) |       1   →       1              |       19.62 ms →       20.24 ms   (+3.16%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |       14.99 ms →       15.62 ms   (+4.23%) |       1   →       1              |       14.99 ms →       15.62 ms   (+4.23%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.62 ms →        4.60 ms   (-0.32%) |       1   →       1              |        4.62 ms →        4.60 ms   (-0.32%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.03 ms →        4.01 ms   (-0.40%) |       1   →       1              |        4.03 ms →        4.01 ms   (-0.40%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.78 ms →        3.78 ms   (-0.09%) |       1   →       1              |        3.78 ms →        3.78 ms   (-0.09%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      243.27 μs →      230.69 μs   (-5.17%) |       1   →       1              |      243.27 μs →      230.69 μs   (-5.17%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.33 μs →        1.10 μs  (-17.42%) |       1   →       1              |        1.33 μs →        1.10 μs  (-17.42%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |       38.61 ms →       33.07 ms  (-14.35%) |       2   →       2              |       77.22 ms →       66.14 ms  (-14.35%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        2.37 ms →        2.60 ms   (+9.88%) |       2   →       2              |        4.74 ms →        5.21 ms   (+9.88%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        2.33 ms →        2.47 ms   (+6.10%) |       1   →       1              |        2.33 ms →        2.47 ms   (+6.10%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       11.19 ms →       11.27 ms   (+0.69%) |       2   →       2              |       22.39 ms →       22.54 ms   (+0.69%) | 
- │   ├ sirius::Radial_integrals|beta                                   |        7.13 ms →        7.86 ms  (+10.20%) |       2   →       2              |       14.26 ms →       15.71 ms  (+10.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       41.78 ms →       38.66 ms   (-7.47%) |       4   →       4              |      167.12 ms →      154.63 ms   (-7.47%) | 
  │   ├ sddk::Gvec::init                                                |      163.70 ms →      160.03 ms   (-2.25%) |       2   →       2              |      327.41 ms →      320.05 ms   (-2.25%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.25 ms →      125.40 ms   (-2.22%) |       2   →       2              |      256.50 ms →      250.80 ms   (-2.22%) | 
- │   ├ sddk::Gvec_shells                                               |      210.27 ms →      279.65 ms  (+33.00%) |       1   →       1              |      210.27 ms →      279.65 ms  (+33.00%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.82 ms →        1.66 ms   (-8.94%) |       1   →       1              |        1.82 ms →        1.66 ms   (-8.94%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      219.32 ms →      220.70 ms   (+0.63%) |       1   →       1              |      219.32 ms →      220.70 ms   (+0.63%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       30.38 ms →      112.39 ms (+269.95%) |       1   →       1              |       30.38 ms →      112.39 ms (+269.95%) | 
  │ ├ sirius::K_point::K_point                                          |        4.67 μs →        4.63 μs   (-0.79%) |       2   →       2              |        9.34 μs →        9.26 μs   (-0.79%) | 
- │ └ sirius::K_point_set::initialize                                   |       30.34 ms →      112.34 ms (+270.25%) |       1   →       1              |       30.34 ms →      112.34 ms (+270.25%) | 
+ │   └ sirius::K_point::initialize                                     |       30.28 ms →       27.00 ms  (-10.84%) |       1   →       1              |       30.28 ms →       27.00 ms  (-10.84%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       21.94 ms →       19.43 ms  (-11.48%) |       1   →       1              |       21.94 ms →       19.43 ms  (-11.48%) | 
+ │     │ └ sddk::Gvec::init                                            |        5.60 ms →        4.94 ms  (-11.79%) |       1   →       1              |        5.60 ms →        4.94 ms  (-11.79%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.13 μs →        7.43 μs  (-33.27%) |       1   →       1              |       11.13 μs →        7.43 μs  (-33.27%) | 
  │     └ sirius::K_point::update                                       |        5.76 ms →        5.49 ms   (-4.71%) |       1   →       1              |        5.76 ms →        5.49 ms   (-4.71%) | 
  │       └ sirius::Beta_projectors                                     |        2.93 ms →        3.17 ms   (+7.86%) |       1   →       1              |        2.93 ms →        3.17 ms   (+7.86%) | 
- │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        2.12 ms →        2.41 ms  (+13.77%) |       1   →       1              |        2.12 ms →        2.41 ms  (+13.77%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.20 ms →        1.70 ms  (-22.96%) |       2   →       2              |        4.40 ms →        3.39 ms  (-22.96%) | 
- ├ sirius::Potential                                                   |      518.33 ms →      613.33 ms  (+18.33%) |       1   →       1              |      518.33 ms →      613.33 ms  (+18.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.42 ms   (-2.08%) |       6   →       6              |       14.82 ms →       14.51 ms   (-2.08%) | 
- │ └ sirius::Potential::update                                         |      503.17 ms →      598.46 ms  (+18.94%) |       1   →       1              |      503.17 ms →      598.46 ms  (+18.94%) | 
- │   └ sirius::Potential::generate_local_potential                     |      502.99 ms →      598.29 ms  (+18.95%) |       1   →       1              |      502.99 ms →      598.29 ms  (+18.95%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      499.10 ms →      501.87 ms   (+0.55%) |       1   →       1              |      499.10 ms →      501.87 ms   (+0.55%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        3.70 ms →        3.72 ms   (+0.47%) |       1   →       1              |        3.70 ms →        3.72 ms   (+0.47%) | 
  ├ sirius::Density                                                     |      437.76 ms →      460.30 ms   (+5.15%) |       1   →       1              |      437.76 ms →      460.30 ms   (+5.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.74 ms →        4.62 ms   (-2.53%) |       2   →       2              |        9.48 ms →        9.24 ms   (-2.53%) | 
  │ └ sirius::Density::update                                           |      428.17 ms →      451.04 ms   (+5.34%) |       1   →       1              |      428.17 ms →      451.04 ms   (+5.34%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      428.00 ms →      450.87 ms   (+5.34%) |       1   →       1              |      428.00 ms →      450.87 ms   (+5.34%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.13 ms            |                   1              |                         3.13 ms            | 
- │     ├ sirius::Simulation_context::make_periodic_function            |      196.02 ms →      443.98 ms (+126.50%) |       1   →       1              |      196.02 ms →      443.98 ms (+126.50%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |      231.76 ms →        2.51 ms  (-98.92%) |       1   →       1              |      231.76 ms →        2.51 ms  (-98.92%) | 
- ├ sirius::Density::initial_density                                    |      422.59 ms →      479.00 ms  (+13.35%) |       1   →       1              |      422.59 ms →      479.00 ms  (+13.35%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      198.57 ms →      457.29 ms (+130.29%) |       1   →       1              |      198.57 ms →      457.29 ms (+130.29%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |      103.93 ms →        2.65 ms  (-97.45%) |       2   →       2              |      207.87 ms →        5.30 ms  (-97.45%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.53 ms →        4.38 ms   (-3.26%) |       1   →       1              |        4.53 ms →        4.38 ms   (-3.26%) | 
+ ├ sirius::Potential::generate                                         |        1.06 s  →      598.56 ms  (-43.41%) |       1   →       1              |        1.06 s  →      598.56 ms  (-43.41%) | 
+ │ ├ sirius::Potential::poisson                                        |      890.51 ms →      410.92 ms  (-53.86%) |       1   →       1              |      890.51 ms →      410.92 ms  (-53.86%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |      690.34 ms →      249.63 ms  (-63.84%) |       1   →       1              |      690.34 ms →      249.63 ms  (-63.84%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.36 ms →        4.49 ms   (+3.18%) |       1   →       1              |        4.36 ms →        4.49 ms   (+3.18%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.13 ms →        4.29 ms   (+3.93%) |       1   →       1              |        4.13 ms →        4.29 ms   (+3.93%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.13 ms →        4.29 ms   (+3.92%) |       1   →       1              |        4.13 ms →        4.29 ms   (+3.92%) | 
  │ ├ sirius::Periodic_function::add                                    |      282.42 μs →      269.55 μs   (-4.56%) |       2   →       2              |      564.84 μs →      539.10 μs   (-4.56%) | 
- │ ├ sirius::Potential::xc                                             |      140.45 ms →      160.99 ms  (+14.63%) |       1   →       1              |      140.45 ms →      160.99 ms  (+14.63%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      140.44 ms →      160.08 ms  (+13.98%) |       1   →       1              |      140.44 ms →      160.08 ms  (+13.98%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.38 ms →        1.46 ms  (-38.47%) |       5   →       8    (+60.00%) |       11.88 ms →       11.70 ms   (-1.56%) | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        3.54 ms →        3.15 ms  (-10.84%) |       9   →      12    (+33.33%) |       31.83 ms →       37.84 ms  (+18.88%) | 
  │ │   ├ sirius::gradient                                              |        8.35 ms →        7.83 ms   (-6.31%) |       1   →       1              |        8.35 ms →        7.83 ms   (-6.31%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.63 ms →        2.48 ms   (-5.76%) |       3   →       3              |        7.89 ms →        7.43 ms   (-5.76%) | 
  │ │   ├ sirius::dot                                                   |        2.93 ms →        2.86 ms   (-2.30%) |       1   →       1              |        2.93 ms →        2.86 ms   (-2.30%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.66 ms →        2.55 ms   (-3.99%) |       1   →       1              |        2.66 ms →        2.55 ms   (-3.99%) | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        22.20 ms            |                   2              |                        44.40 ms            | 
- │ │   └ sirius::divergence                                            |       31.86 ms →       21.29 ms  (-33.19%) |       1   →       2   (+100.00%) |       31.86 ms →       42.57 ms  (+33.63%) | 
- │ │     └ sirius::Smooth_periodic_function                            |        2.60 ms →        2.63 ms   (+0.82%) |       1   →       2   (+100.00%) |        2.60 ms →        5.25 ms (+101.64%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.34 ms →        3.50 ms   (+4.70%) |       1   →       1              |        3.34 ms →        3.50 ms   (+4.70%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.19 ms →       21.92 ms   (-1.21%) |       1   →       1              |       22.19 ms →       21.92 ms   (-1.21%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      139.00 ns →      193.00 ns  (+38.85%) |       1   →       1              |      139.00 ns →      193.00 ns  (+38.85%) | 
- ├ sirius::Hamiltonian0                                                |       14.51 ms →       18.57 ms  (+27.92%) |       1   →       1              |       14.51 ms →       18.57 ms  (+27.92%) | 
  │ ├ sirius::Local_operator                                            |       14.06 ms →       13.98 ms   (-0.59%) |       1   →       1              |       14.06 ms →       13.98 ms   (-0.59%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.13 ms →        7.28 ms   (+2.01%) |       1   →       1              |        7.13 ms →        7.28 ms   (+2.01%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.38 ms →        5.14 ms   (-4.49%) |       1   →       1              |        5.38 ms →        5.14 ms   (-4.49%) | 
  │ ├ sirius::Non_local_operator                                        |       59.03 μs →       60.97 μs   (+3.29%) |       2   →       2              |      118.05 μs →      121.93 μs   (+3.29%) | 
- │ ├ sirius::D_operator::initialize                                    |      149.77 μs →        1.57 ms (+949.14%) |       1   →       1              |      149.77 μs →        1.57 ms (+949.14%) | 
- │ └ sirius::Q_operator::initialize                                    |      126.89 μs →        2.84 ms (+2136.51%) |       1   →       1              |      126.89 μs →        2.84 ms (+2136.51%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.25 s  →        4.42 s   (+96.43%) |       1   →       1              |        2.25 s  →        4.42 s   (+96.43%) | 
  │ ├ sirius::Hamiltonian_k                                             |        7.42 ms →        7.47 ms   (+0.67%) |       1   →       1              |        7.42 ms →        7.47 ms   (+0.67%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      521.92 μs →      541.86 μs   (+3.82%) |       1   →       1              |      521.92 μs →      541.86 μs   (+3.82%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        6.89 ms →        6.92 ms   (+0.40%) |       1   →       1              |        6.89 ms →        6.92 ms   (+0.40%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.24 s  →        4.41 s   (+96.61%) |       1   →       1              |        2.24 s  →        4.41 s   (+96.61%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.96 ms →       87.06 ms   (+0.11%) |       4   →       4              |      347.85 ms →      348.24 ms   (+0.11%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.32 ms →       50.06 ms   (+3.61%) |       1   →       1              |       48.32 ms →       50.06 ms   (+3.61%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       16.61 ms →       17.61 ms   (+6.02%) |       1   →       1              |       16.61 ms →       17.61 ms   (+6.02%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.24 s  →        1.23 s    (-1.14%) |       1   →       1              |        1.24 s  →        1.23 s    (-1.14%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |        1.02 s  →        1.01 s    (-1.31%) |       1   →       1              |        1.02 s  →        1.01 s    (-1.31%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      327.17 ms →      318.87 ms   (-2.54%) |       1   →       1              |      327.17 ms →      318.87 ms   (-2.54%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      174.22 ms →      172.50 ms   (-0.99%) |       1   →       1              |      174.22 ms →      172.50 ms   (-0.99%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      174.22 ms →      172.50 ms   (-0.99%) |       1   →       1              |      174.22 ms →      172.50 ms   (-0.99%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      118.44 ms →      114.81 ms   (-3.07%) |       1   →       1              |      118.44 ms →      114.81 ms   (-3.07%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      172.01 ms →      170.96 ms   (-0.61%) |       1   →       1              |      172.01 ms →      170.96 ms   (-0.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      172.01 ms →      170.95 ms   (-0.61%) |       1   →       1              |      172.01 ms →      170.95 ms   (-0.61%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      190.30 ms →      185.88 ms   (-2.32%) |       1   →       1              |      190.30 ms →      185.88 ms   (-2.32%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      121.22 ms →      117.00 ms   (-3.48%) |       1   →       1              |      121.22 ms →      117.00 ms   (-3.48%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.74 ms →        3.73 ms   (-0.03%) |       1   →       1              |        3.74 ms →        3.73 ms   (-0.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.05 ms →       89.09 ms   (-1.06%) |       1   →       1              |       90.05 ms →       89.09 ms   (-1.06%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.38 ms →       11.49 ms   (-7.18%) |       1   →       1              |       12.38 ms →       11.49 ms   (-7.18%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.15 ms →       64.27 ms   (+0.19%) |       2   →       2              |      128.30 ms →      128.54 ms   (+0.19%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       62.25 ms →       67.78 ms   (+8.88%) |       2   →       2              |      124.50 ms →      135.56 ms   (+8.88%) | 
  │ │ │ ├ sddk::inner                                                   |       62.12 ms                             |       2                          |      124.24 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       20.09 μs                             |       2                          |       40.19 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.57 ms                             |       4                          |      102.30 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |        1.01 ms                             |       4                          |        4.05 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        8.92 ms                             |       2                          |       17.83 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        67.70 ms            |                   2              |                       135.41 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        88.00 ns            |                   2              |                       176.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        67.30 ms            |                   2              |                       134.61 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       473.00 ns            |                   2              |                       946.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      114.74 ms                             |       1                          |      114.74 ms                             | 
  │ │ ├ sddk::transform                                                 |       36.04 ms                             |       1                          |       36.04 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.36 μs                             |       1                          |       14.36 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       20.20 μs                             |       1                          |       20.20 μs                             | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |                         2.20 s             |                   1              |                         2.20 s             | 
  │ │ └ sddk::wf_trans                                                  |                       119.05 ms            |                   1              |                       119.05 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                       118.15 ms            |                   1              |                       118.15 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      471.00 ns →      433.00 ns   (-8.07%) |       1   →       1              |      471.00 ns →      433.00 ns   (-8.07%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      168.56 s  →      350.59 s  (+108.00%) |       1   →       1              |      168.56 s  →      350.59 s  (+108.00%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.12 ms →        2.23 ms   (+5.48%) |      31   →      30     (-3.23%) |       65.65 ms →       67.01 ms   (+2.07%) | 
  │ ├ sirius::Density                                                   |                       419.37 ms            |                   1              |                       419.37 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         4.95 ms            |                   2              |                         9.90 ms            | 
  │ │ └ sirius::Density::update                                         |                       409.36 ms            |                   1              |                       409.36 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       409.18 ms            |                   1              |                       409.18 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                         3.43 ms            |                   1              |                         3.43 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       229.52 ms            |                   1              |                       229.52 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                       174.93 ms            |                   1              |                       174.93 ms            | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.90 s  →        7.77 s   (+99.42%) |      43   →      45     (+4.65%) |      167.53 s  →      349.63 s  (+108.70%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.68 ms →       10.64 ms  (+38.43%) |      43   →      45     (+4.65%) |      330.42 ms →      478.66 ms  (+44.86%) | 
  │ │ │ ├ sirius::Local_operator                                        |        7.22 ms →        6.75 ms   (-6.56%) |      43   →      45     (+4.65%) |      310.66 ms →      303.79 ms   (-2.21%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.43 ms →        1.32 ms   (-7.62%) |      43   →      45     (+4.65%) |       61.56 ms →       59.51 ms   (-3.33%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.21 ms →        3.86 ms   (-8.37%) |      43   →      45     (+4.65%) |      180.91 ms →      173.49 ms   (-4.11%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.77 μs →       60.41 μs   (-2.20%) |      86   →      90     (+4.65%) |        5.31 ms →        5.44 ms   (+2.35%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      155.77 μs →        1.26 ms (+707.67%) |      43   →      45     (+4.65%) |        6.70 ms →       56.61 ms (+745.24%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |      122.34 μs →        2.45 ms (+1901.43%) |      43   →      45     (+4.65%) |        5.26 ms →      110.18 ms (+1994.52%) | 
- │ │ ├ sirius::Band::solve                                             |        2.79 s  →        6.43 s  (+130.55%) |      43   →      45     (+4.65%) |      120.00 s  →      289.53 s  (+141.27%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      406.47 μs →      415.01 μs   (+2.10%) |      43   →      45     (+4.65%) |       17.48 ms →       18.68 ms   (+6.85%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      398.93 μs →      404.35 μs   (+1.36%) |      43   →      45     (+4.65%) |       17.15 ms →       18.20 ms   (+6.07%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.62 μs →        5.52 μs   (-1.79%) |      43   →      45     (+4.65%) |      241.74 μs →      248.44 μs   (+2.77%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.77 s  →        5.15 s   (+86.07%) |      43   →      45     (+4.65%) |      119.07 s  →      231.86 s   (+94.72%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       70.32 ms →       57.82 ms  (-17.77%) |      43   →      45     (+4.65%) |        3.02 s  →        2.60 s   (-13.95%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.47 ms →        3.83 ms  (-29.98%) |     258   →     270     (+4.65%) |        1.41 s  →        1.03 s   (-26.72%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.38 ms →        3.81 ms  (-40.24%) |      43   →      45     (+4.65%) |      274.41 ms →      171.61 ms  (-37.46%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      431.29 μs →      432.48 μs   (+0.28%) |      43   →      45     (+4.65%) |       18.55 ms →       19.46 ms   (+4.94%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        5.32 ms →        3.11 ms  (-41.57%) |      43   →      45     (+4.65%) |      228.85 ms →      139.95 ms  (-38.85%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.67 s  →        5.07 s   (+89.91%) |      43   →      45     (+4.65%) |      114.72 s  →      228.00 s   (+98.74%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      219.14 ms →      207.86 ms   (-5.15%) |     208   →     210     (+0.96%) |       45.58 s  →       43.65 s    (-4.24%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      156.02 ms →      147.71 ms   (-5.33%) |     208   →     210     (+0.96%) |       32.45 s  →       31.02 s    (-4.41%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       30.03 ms →       28.50 ms   (-5.08%) |     208   →     210     (+0.96%) |        6.25 s  →        5.99 s    (-4.17%) | 
+ │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      696.20 μs →      329.11 μs  (-52.73%) |     208   →     210     (+0.96%) |      144.81 ms →       69.11 ms  (-52.27%) | 
+ │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.36 ms →        1.53 ms  (-54.54%) |      43   →      45     (+4.65%) |      144.36 ms →       68.68 ms  (-52.42%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       24.35 ms →       23.35 ms   (-4.08%) |     208   →     210     (+0.96%) |        5.06 s  →        4.90 s    (-3.16%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      706.29 μs →      652.39 μs   (-7.63%) |     208   →     210     (+0.96%) |      146.91 ms →      137.00 ms   (-6.74%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.40 ms →        3.03 ms  (-10.86%) |      43   →      45     (+4.65%) |      146.20 ms →      136.38 ms   (-6.71%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       35.70 ms →       33.23 ms   (-6.93%) |     208   →     210     (+0.96%) |        7.43 s  →        6.98 s    (-6.03%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       22.32 ms →       20.53 ms   (-8.01%) |     208   →     210     (+0.96%) |        4.64 s  →        4.31 s    (-7.12%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.64 ms   (-0.60%) |     208   →     210     (+0.96%) |      551.99 ms →      553.97 ms   (+0.36%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.88 ms →       21.50 ms   (-6.04%) |     208   →     210     (+0.96%) |        4.76 s  →        4.51 s    (-5.14%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.66 ms →        2.19 ms  (-17.57%) |     208   →     210     (+0.96%) |      552.76 ms →      460.04 ms  (-16.77%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.78 ms →       17.99 ms   (-4.22%) |     416   →     420     (+0.96%) |        7.81 s  →        7.55 s    (-3.30%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |      105.98 ms →      216.63 ms (+104.41%) |     208   →     210     (+0.96%) |       22.04 s  →       45.49 s  (+106.38%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.93 ms                             |     373                          |        4.08 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       20.26 μs                             |     373                          |        7.56 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.50 ms                             |     746                          |        3.36 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      157.59 μs                             |     746                          |      117.56 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.59 ms                             |     373                          |      594.66 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       53.04 ms                             |     208                          |       11.03 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.55 ms                             |     165                          |        3.56 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       26.55 μs                             |     165                          |        4.38 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       58.25 μs                             |     495                          |       28.84 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         8.97 ms            |                 375              |                         3.36 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       132.16 ns            |                 375              |                        49.56 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         8.96 ms            |                 375              |                         3.36 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       318.24 ns            |                 375              |                       119.34 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |                        28.39 ms            |                 210              |                         5.96 s             | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |                        66.18 ms            |                 210              |                        13.90 s             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        26.33 ms            |                 795              |                        20.93 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                        18.50 ms            |                1.13 K            |                        20.81 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       30.78 ms →       15.85 ms  (-48.50%) |     208   →     210     (+0.96%) |        6.40 s  →        3.33 s   (-48.00%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       25.87 ms                             |     208                          |        5.38 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       51.63 μs                             |     208                          |       10.74 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.94 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      293.54 μs                             |     416                          |      122.11 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        9.34 ms                             |     208                          |        1.94 s                              | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        13.97 ms            |                 210              |                         2.93 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       156.97 ns            |                 210              |                        32.96 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        13.96 ms            |                 210              |                         2.93 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       412.24 ns            |                 210              |                        86.57 μs            | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      164.73 ms                             |     208                          |       34.26 s                              | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |                       548.75 ms            |                 210              |                       115.24 s             | 
- │ │ │ │   ├ sirius::residuals                                         |       20.09 ms →       41.34 ms (+105.73%) |     207   →     205     (-0.97%) |        4.16 s  →        8.47 s  (+103.74%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.51 μs                             |     171                          |        2.82 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       56.04 μs                             |     342                          |       19.17 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        40.16 ms            |                 185              |                         7.43 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                        20.01 ms            |                 370              |                         7.40 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        3.51 ms →        1.49 ms  (-57.45%) |     171   →     185     (+8.19%) |      600.34 ms →      276.37 ms  (-53.96%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.25 ms →      139.89 ms (+172.95%) |      44   →      84    (+90.91%) |        2.26 s  →       11.75 s  (+421.10%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.84 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.81 μs                             |      45                          |      576.64 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       17.52 μs                             |      46                          |      806.03 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        95.18 ms            |                 123              |                        11.71 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        71.85 ms            |                 162              |                        11.64 s             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      584.02 ns →      591.09 ns   (+1.21%) |      43   →      45     (+4.65%) |       25.11 μs →       26.60 μs   (+5.92%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       48.93 μs →        3.10 ms (+6244.33%) |      43   →      45     (+4.65%) |        2.10 ms →      139.69 ms (+6539.42%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.45 ms →      192.84 ms (+5495.64%) |      43   →      45     (+4.65%) |      148.19 ms →        8.68 s  (+5755.90%) | 
- │ │ ├ sirius::Density::generate                                       |      302.51 ms →      319.34 ms   (+5.56%) |      43   →      45     (+4.65%) |       13.01 s  →       14.37 s   (+10.47%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      298.57 ms →      315.28 ms   (+5.60%) |      43   →      45     (+4.65%) |       12.84 s  →       14.19 s   (+10.51%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       70.75 ms →       67.85 ms   (-4.10%) |      43   →      45     (+4.65%) |        3.04 s  →        3.05 s    (+0.36%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       61.52 μs →       55.36 μs  (-10.01%) |      43   →      45     (+4.65%) |        2.65 ms →        2.49 ms   (-5.83%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms →        1.19 ms   (+1.55%) |       2   →       2              |        2.34 ms →        2.38 ms   (+1.55%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       57.88 ms →       54.27 ms   (-6.23%) |      43   →      45     (+4.65%) |        2.49 s  →        2.44 s    (-1.86%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       62.30 ms →       76.09 ms  (+22.15%) |      43   →      45     (+4.65%) |        2.68 s  →        3.42 s   (+27.83%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.06 μs →       10.03 μs   (-9.24%) |      43   →      45     (+4.65%) |      475.40 μs →      451.53 μs   (-5.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.30 ms →        2.31 ms   (+0.13%) |      43   →      45     (+4.65%) |       99.08 ms →      103.82 ms   (+4.79%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       59.00 ms →       57.58 ms   (-2.42%) |      43   →      45     (+4.65%) |        2.54 s  →        2.59 s    (+2.12%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.53 ms →        6.05 ms  (-19.58%) |      43   →      45     (+4.65%) |      323.76 ms →      272.47 ms  (-15.84%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      722.74 ns →      886.40 ns  (+22.64%) |      43   →      45     (+4.65%) |       31.08 μs →       39.89 μs  (+28.35%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.45 ms →      105.57 ms   (+1.08%) |      43   →      45     (+4.65%) |        4.49 s  →        4.75 s    (+5.78%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.50 ms →        2.49 ms   (-0.61%) |      43   →      45     (+4.65%) |      107.53 ms →      111.84 ms   (+4.01%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.08 ms →       20.71 ms   (+3.12%) |      43   →      45     (+4.65%) |      863.38 ms →      931.75 ms   (+7.92%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms →       20.52 ms   (+3.13%) |      43   →      45     (+4.65%) |      855.73 ms →      923.55 ms   (+7.93%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      291.16 ns →      362.71 ns  (+24.57%) |      43   →      45     (+4.65%) |       12.52 μs →       16.32 μs  (+30.37%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.24 ms →        1.24 ms   (+0.34%) |      43   →      45     (+4.65%) |       53.23 ms →       55.90 ms   (+5.01%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.69 ms →        2.81 ms   (+4.31%) |      43   →      45     (+4.65%) |      115.88 ms →      126.49 ms   (+9.16%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                         4.70 ms            |                 405              |                         1.90 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                         4.39 ms            |                 405              |                         1.78 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                         4.39 ms            |                 405              |                         1.78 s             | 
+ │ │ ├ sirius::Density::mix                                            |      194.29 ms →      113.94 ms  (-41.35%) |      43   →      45     (+4.65%) |        8.35 s  →        5.13 s   (-38.63%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      370.35 μs →      344.35 μs   (-7.02%) |      43   →      45     (+4.65%) |       15.92 ms →       15.50 ms   (-2.70%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.14 ms →        3.48 ms  (-32.33%) |      43   →      45     (+4.65%) |      221.19 ms →      156.65 ms  (-29.18%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.80 ms →        3.14 ms  (-34.54%) |      43   →      45     (+4.65%) |      206.48 ms →      141.45 ms  (-31.49%) | 
- │ │ ├ sirius::Potential::generate                                     |      546.11 ms →      591.37 ms   (+8.29%) |      43   →      45     (+4.65%) |       23.48 s  →       26.61 s   (+13.32%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      387.75 ms →      413.09 ms   (+6.53%) |      43   →      45     (+4.65%) |       16.67 s  →       18.59 s   (+11.49%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       93.51 ms →      103.49 ms  (+10.67%) |      43   →      45     (+4.65%) |        4.02 s  →        4.66 s   (+15.82%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.47 ms →        4.53 ms   (+1.24%) |      43   →      45     (+4.65%) |      192.26 ms →      203.70 ms   (+5.95%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.23 ms →        4.26 ms   (+0.84%) |      43   →      45     (+4.65%) |      181.84 ms →      191.91 ms   (+5.54%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.23 ms →        4.26 ms   (+0.86%) |      43   →      45     (+4.65%) |      181.79 ms →      191.88 ms   (+5.55%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      258.23 μs →      244.50 μs   (-5.32%) |      86   →      90     (+4.65%) |       22.21 ms →       22.00 ms   (-0.91%) | 
- │ │ │ ├ sirius::Potential::xc                                         |      132.33 ms →      152.45 ms  (+15.21%) |      43   →      45     (+4.65%) |        5.69 s  →        6.86 s   (+20.57%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |      132.33 ms →      151.47 ms  (+14.47%) |      43   →      45     (+4.65%) |        5.69 s  →        6.82 s   (+19.79%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.66 ms →        1.50 ms   (-9.69%) |     215   →     360    (+67.44%) |      356.00 ms →      538.30 ms  (+51.21%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        3.12 ms →        3.08 ms   (-1.37%) |     387   →     540    (+39.53%) |        1.21 s  →        1.66 s   (+37.63%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.62 ms →        2.02 ms  (-22.93%) |      43   →      45     (+4.65%) |      112.48 ms →       90.72 ms  (-19.35%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      727.02 μs →      522.57 μs  (-28.12%) |     129   →     135     (+4.65%) |       93.79 ms →       70.55 ms  (-24.78%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.90 ms →        1.02 ms  (-64.75%) |      43   →      45     (+4.65%) |      124.87 ms →       46.06 ms  (-63.11%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.60 ms →      727.44 μs  (-72.03%) |      43   →      45     (+4.65%) |      111.83 ms →       32.73 ms  (-70.73%) | 
  │ │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        21.69 ms            |                  90              |                         1.95 s             | 
- │ │ │ │   └ sirius::divergence                                        |       31.32 ms →       20.70 ms  (-33.91%) |      43   →      90   (+109.30%) |        1.35 s  →        1.86 s   (+38.33%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.57 ms →        2.55 ms   (-0.62%) |      43   →      90   (+109.30%) |      110.45 ms →      229.73 ms (+108.01%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.90 ms →        3.68 ms   (-5.64%) |      43   →      45     (+4.65%) |      167.52 ms →      165.42 ms   (-1.25%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.94 ms →       20.96 ms   (+0.12%) |      43   →      45     (+4.65%) |      900.44 ms →      943.42 ms   (+4.77%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      133.98 ns →      212.51 ns  (+58.62%) |      43   →      45     (+4.65%) |        5.76 μs →        9.56 μs  (+66.00%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      324.81 ns →      432.44 ns  (+33.14%) |      43   →      45     (+4.65%) |       13.97 μs →       19.46 μs  (+39.33%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.40 ms →        2.42 ms   (+0.67%) |      43   →      45     (+4.65%) |      103.15 ms →      108.68 ms   (+5.36%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.50 ms                             |     301                          |        1.35 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.25 ms                             |     301                          |        1.28 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.25 ms                             |     301                          |        1.28 s                              | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.28 ms →        4.57 ms   (+6.58%) |     129   →     135     (+4.65%) |      552.64 ms →      616.41 ms  (+11.54%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.05 ms →        4.34 ms   (+7.06%) |     129   →     135     (+4.65%) |      523.02 ms →      585.99 ms  (+12.04%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.27 ms →        4.36 ms   (+2.08%) |      43   →      45     (+4.65%) |      183.71 ms →      196.25 ms   (+6.83%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      115.28 μs →       15.91 ms (+13702.24%) |      43   →      45     (+4.65%) |        4.96 ms →      716.00 ms (+14344.20%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      111.28 μs →       15.90 ms (+14190.85%) |      43   →      45     (+4.65%) |        4.79 ms →      715.65 ms (+14855.54%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.27 ms →        5.58 ms  (-11.06%) |       2   →       2              |       12.54 ms →       11.15 ms  (-11.06%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.34 ms →        4.43 ms   (+2.12%) |       6   →       6              |       26.02 ms →       26.58 ms   (+2.12%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.20 ms →        4.27 ms   (+1.71%) |       6   →       6              |       25.19 ms →       25.62 ms   (+1.71%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.20 ms →        4.27 ms   (+1.71%) |       6   →       6              |       25.18 ms →       25.62 ms   (+1.71%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.16 ms →        4.46 ms   (+7.33%) |       3   →       3              |       12.48 ms →       13.39 ms   (+7.33%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.01 ms →        4.31 ms   (+7.49%) |       3   →       3              |       12.02 ms →       12.92 ms   (+7.49%) | 
  ├ sirius::Periodic_function|inner                                     |        4.30 ms →        4.53 ms   (+5.39%) |       2   →       2              |        8.60 ms →        9.06 ms   (+5.39%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.15 ms →        4.08 ms   (-1.61%) |       2   →       2              |        8.29 ms →        8.16 ms   (-1.61%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.15 ms →        4.08 ms   (-1.62%) |       2   →       2              |        8.29 ms →        8.16 ms   (-1.62%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.11 ms →        4.48 ms   (+8.78%) |       1   →       1              |        4.11 ms →        4.48 ms   (+8.78%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.95 ms →        4.01 ms   (+1.53%) |       1   →       1              |        3.95 ms →        4.01 ms   (+1.53%) | 
- └ sirius::finalize                                                    |      315.67 ms →      358.43 ms  (+13.54%) |       1   →       1              |      315.67 ms →      358.43 ms  (+13.54%) | 
  ====================================================================================================================================================================================================
```
