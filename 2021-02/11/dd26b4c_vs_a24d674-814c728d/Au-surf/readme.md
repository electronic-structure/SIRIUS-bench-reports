# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      151.83 s  →      235.85 s   (+55.34%) |       1   →       1              |      151.83 s  →      235.85 s   (+55.34%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.79 s    (+3.11%) |       1   →       1              |        2.71 s  →        2.79 s    (+3.11%) | 
  ├ sirius::Simulation_context::initialize                              |        2.12 s  →        2.10 s    (-0.58%) |       1   →       1              |        2.12 s  →        2.10 s    (-0.58%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       21.16 ms →       33.66 ms  (+59.11%) |       1   →       1              |       21.16 ms →       33.66 ms  (+59.11%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       99.82 ms →      115.04 ms  (+15.25%) |       1   →       1              |       99.82 ms →      115.04 ms  (+15.25%) | 
- │ │ ├ sirius::Atom_type::init                                         |       74.67 ms →       90.27 ms  (+20.89%) |       1   →       1              |       74.67 ms →       90.27 ms  (+20.89%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.09 ms →       24.62 ms   (-1.85%) |       1   →       1              |       25.09 ms →       24.62 ms   (-1.85%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.70 ms →       10.19 ms   (-4.76%) |       1   →       1              |       10.70 ms →       10.19 ms   (-4.76%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.36 ms →       14.40 ms   (+0.31%) |       1   →       1              |       14.36 ms →       14.40 ms   (+0.31%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.94 ms →       13.63 ms   (-2.17%) |       1   →       1              |       13.94 ms →       13.63 ms   (-2.17%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       13.70 ms →       13.40 ms   (-2.20%) |       1   →       1              |       13.70 ms →       13.40 ms   (-2.20%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      220.38 μs →      219.93 μs   (-0.20%) |       1   →       1              |      220.38 μs →      219.93 μs   (-0.20%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.49 μs →        2.74 μs   (+9.82%) |       1   →       1              |        2.49 μs →        2.74 μs   (+9.82%) | 
  │ └ sirius::Simulation_context::update                                |        1.94 s  →        1.90 s    (-1.92%) |       1   →       1              |        1.94 s  →        1.90 s    (-1.92%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.96 ms →       13.19 ms   (+1.78%) |       1   →       1              |       12.96 ms →       13.19 ms   (+1.78%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.39 ms →        8.42 ms   (+0.34%) |       1   →       1              |        8.39 ms →        8.42 ms   (+0.34%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.55 ms →        4.75 ms   (+4.46%) |       1   →       1              |        4.55 ms →        4.75 ms   (+4.46%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.13 ms →        4.17 ms   (+1.02%) |       1   →       1              |        4.13 ms →        4.17 ms   (+1.02%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.91 ms →        3.96 ms   (+1.14%) |       1   →       1              |        3.91 ms →        3.96 ms   (+1.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      215.84 μs →      214.20 μs   (-0.76%) |       1   →       1              |      215.84 μs →      214.20 μs   (-0.76%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.40 μs →        1.15 μs  (-17.76%) |       1   →       1              |        1.40 μs →        1.15 μs  (-17.76%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |       32.37 ms →       18.50 ms  (-42.87%) |       2   →       2              |       64.75 ms →       36.99 ms  (-42.87%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.09 ms   (+0.32%) |       2   →       2              |        2.18 ms →        2.19 ms   (+0.32%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      952.22 μs →      957.93 μs   (+0.60%) |       1   →       1              |      952.22 μs →      957.93 μs   (+0.60%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.05 ms →        4.97 ms   (-1.63%) |       2   →       2              |       10.10 ms →        9.94 ms   (-1.63%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.63 ms   (-0.17%) |       2   →       2              |        7.28 ms →        7.27 ms   (-0.17%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.81 ms →       15.79 ms   (-0.15%) |       4   →       4              |       63.24 ms →       63.14 ms   (-0.15%) | 
  │   ├ sddk::Gvec::init                                                |      163.67 ms →      156.75 ms   (-4.23%) |       2   →       2              |      327.33 ms →      313.49 ms   (-4.23%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.13 ms →      124.46 ms   (-3.62%) |       2   →       2              |      258.25 ms →      248.92 ms   (-3.62%) | 
+ │   ├ sddk::Gvec_shells                                               |      144.19 ms →      120.99 ms  (-16.09%) |       1   →       1              |      144.19 ms →      120.99 ms  (-16.09%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.03 ms   (-0.27%) |       1   →       1              |        1.04 ms →        1.03 ms   (-0.27%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      220.57 ms →      216.39 ms   (-1.90%) |       1   →       1              |      220.57 ms →      216.39 ms   (-1.90%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       31.86 ms →       25.87 ms  (-18.78%) |       1   →       1              |       31.86 ms →       25.87 ms  (-18.78%) | 
- │ ├ sirius::K_point::K_point                                          |        2.33 μs →        7.54 μs (+222.74%) |       2   →       2              |        4.67 μs →       15.07 μs (+222.74%) | 
+ │ └ sirius::K_point_set::initialize                                   |       31.83 ms →       25.82 ms  (-18.87%) |       1   →       1              |       31.83 ms →       25.82 ms  (-18.87%) | 
+ │   └ sirius::K_point::initialize                                     |       31.77 ms →       25.77 ms  (-18.89%) |       1   →       1              |       31.77 ms →       25.77 ms  (-18.89%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       24.01 ms →       19.70 ms  (-17.94%) |       1   →       1              |       24.01 ms →       19.70 ms  (-17.94%) | 
+ │     │ └ sddk::Gvec::init                                            |        5.93 ms →        5.23 ms  (-11.67%) |       1   →       1              |        5.93 ms →        5.23 ms  (-11.67%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.89 μs →       10.28 μs  (-13.51%) |       1   →       1              |       11.89 μs →       10.28 μs  (-13.51%) | 
+ │     └ sirius::K_point::update                                       |        4.84 ms →        3.94 ms  (-18.59%) |       1   →       1              |        4.84 ms →        3.94 ms  (-18.59%) | 
  │       └ sirius::Beta_projectors                                     |        1.69 ms →        1.71 ms   (+1.17%) |       1   →       1              |        1.69 ms →        1.71 ms   (+1.17%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      876.29 μs →      912.89 μs   (+4.18%) |       1   →       1              |      876.29 μs →      912.89 μs   (+4.18%) | 
+ ├ sirius::Smooth_periodic_function                                    |        2.22 ms →        1.78 ms  (-19.72%) |       2   →       2              |        4.44 ms →        3.57 ms  (-19.72%) | 
- ├ sirius::Potential                                                   |       85.56 ms →      188.17 ms (+119.92%) |       1   →       1              |       85.56 ms →      188.17 ms (+119.92%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.41 ms   (-1.58%) |       6   →       6              |       14.70 ms →       14.46 ms   (-1.58%) | 
- │ └ sirius::Potential::update                                         |       70.55 ms →      173.36 ms (+145.73%) |       1   →       1              |       70.55 ms →      173.36 ms (+145.73%) | 
- │   └ sirius::Potential::generate_local_potential                     |       70.37 ms →      173.19 ms (+146.10%) |       1   →       1              |       70.37 ms →      173.19 ms (+146.10%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.05 ms →       56.94 ms   (+7.35%) |       1   →       1              |       53.05 ms →       56.94 ms   (+7.35%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       17.14 ms →       22.45 ms  (+31.01%) |       1   →       1              |       17.14 ms →       22.45 ms  (+31.01%) | 
  ├ sirius::Density                                                     |       71.16 ms →       74.85 ms   (+5.18%) |       1   →       1              |       71.16 ms →       74.85 ms   (+5.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.73 ms →        4.61 ms   (-2.58%) |       2   →       2              |        9.45 ms →        9.21 ms   (-2.58%) | 
  │ └ sirius::Density::update                                           |       61.58 ms →       65.61 ms   (+6.54%) |       1   →       1              |       61.58 ms →       65.61 ms   (+6.54%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.40 ms →       65.45 ms   (+6.59%) |       1   →       1              |       61.40 ms →       65.45 ms   (+6.59%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                         3.14 ms            |                   1              |                         3.14 ms            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.78 ms →       57.90 ms   (+9.68%) |       1   →       1              |       52.78 ms →       57.90 ms   (+9.68%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.43 ms →        3.15 ms  (-62.56%) |       1   →       1              |        8.43 ms →        3.15 ms  (-62.56%) | 
  ├ sirius::Density::initial_density                                    |       78.86 ms →       79.71 ms   (+1.08%) |       1   →       1              |       78.86 ms →       79.71 ms   (+1.08%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       52.09 ms →       58.35 ms  (+12.01%) |       1   →       1              |       52.09 ms →       58.35 ms  (+12.01%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.38 ms →        2.80 ms  (-47.92%) |       2   →       2              |       10.77 ms →        5.61 ms  (-47.92%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.21 ms →        3.93 ms   (-6.55%) |       1   →       1              |        4.21 ms →        3.93 ms   (-6.55%) | 
- ├ sirius::Potential::generate                                         |      191.96 ms →      215.24 ms  (+12.13%) |       1   →       1              |      191.96 ms →      215.24 ms  (+12.13%) | 
  │ ├ sirius::Potential::poisson                                        |       63.96 ms →       64.99 ms   (+1.61%) |       1   →       1              |       63.96 ms →       64.99 ms   (+1.61%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.86 ms →        3.53 ms  (-60.15%) |       1   →       1              |        8.86 ms →        3.53 ms  (-60.15%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.55 ms →        4.52 ms   (-0.68%) |       1   →       1              |        4.55 ms →        4.52 ms   (-0.68%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.53 ms →        4.24 ms   (-6.38%) |       1   →       1              |        4.53 ms →        4.24 ms   (-6.38%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.53 ms →        4.24 ms   (-6.38%) |       1   →       1              |        4.53 ms →        4.24 ms   (-6.38%) | 
+ │ ├ sirius::Periodic_function::add                                    |      238.71 μs →      200.17 μs  (-16.15%) |       2   →       2              |      477.42 μs →      400.34 μs  (-16.15%) | 
- │ ├ sirius::Potential::xc                                             |      101.49 ms →      123.70 ms  (+21.89%) |       1   →       1              |      101.49 ms →      123.70 ms  (+21.89%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      101.49 ms →      122.67 ms  (+20.88%) |       1   →       1              |      101.49 ms →      122.67 ms  (+20.88%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.26 ms →        1.48 ms  (-34.37%) |       5   →       8    (+60.00%) |       11.28 ms →       11.84 ms   (+5.00%) | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.38 ms →        2.43 ms   (+1.96%) |       9   →      12    (+33.33%) |       21.42 ms →       29.12 ms  (+35.95%) | 
  │ │   ├ sirius::gradient                                              |        8.25 ms →        7.47 ms   (-9.44%) |       1   →       1              |        8.25 ms →        7.47 ms   (-9.44%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.66 ms →        2.40 ms   (-9.92%) |       3   →       3              |        7.98 ms →        7.19 ms   (-9.92%) | 
  │ │   ├ sirius::dot                                                   |        2.79 ms →        2.81 ms   (+0.52%) |       1   →       1              |        2.79 ms →        2.81 ms   (+0.52%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.56 ms →        2.58 ms   (+0.78%) |       1   →       1              |        2.56 ms →        2.58 ms   (+0.78%) | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                         9.53 ms            |                   2              |                        19.05 ms            | 
- │ │   └ sirius::divergence                                            |       25.08 ms →       19.81 ms  (-21.00%) |       1   →       2   (+100.00%) |       25.08 ms →       39.63 ms  (+57.99%) | 
- │ │     └ sirius::Smooth_periodic_function                            |        2.67 ms →        2.52 ms   (-5.72%) |       1   →       2   (+100.00%) |        2.67 ms →        5.03 ms  (+88.56%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.27 ms →        3.35 ms   (+2.50%) |       1   →       1              |        3.27 ms →        3.35 ms   (+2.50%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.22 ms →       22.25 ms   (+0.12%) |       1   →       1              |       22.22 ms →       22.25 ms   (+0.12%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      194.00 ns →      195.00 ns   (+0.52%) |       1   →       1              |      194.00 ns →      195.00 ns   (+0.52%) | 
- ├ sirius::Hamiltonian0                                                |       14.14 ms →       15.88 ms  (+12.30%) |       1   →       1              |       14.14 ms →       15.88 ms  (+12.30%) | 
  │ ├ sirius::Local_operator                                            |       13.82 ms →       14.00 ms   (+1.36%) |       1   →       1              |       13.82 ms →       14.00 ms   (+1.36%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.70 ms →        7.11 ms   (-7.73%) |       1   →       1              |        7.70 ms →        7.11 ms   (-7.73%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.68 ms →        5.45 ms  (+16.53%) |       1   →       1              |        4.68 ms →        5.45 ms  (+16.53%) | 
  │ ├ sirius::Non_local_operator                                        |       59.64 μs →       59.13 μs   (-0.86%) |       2   →       2              |      119.28 μs →      118.26 μs   (-0.86%) | 
- │ ├ sirius::D_operator::initialize                                    |       81.26 μs →      615.17 μs (+657.08%) |       1   →       1              |       81.26 μs →      615.17 μs (+657.08%) | 
- │ └ sirius::Q_operator::initialize                                    |       69.49 μs →        1.09 ms (+1465.40%) |       1   →       1              |       69.49 μs →        1.09 ms (+1465.40%) | 
- ├ sirius::Band::initialize_subspace                                   |        2.18 s  →        3.29 s   (+51.30%) |       1   →       1              |        2.18 s  →        3.29 s   (+51.30%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms →        8.42 ms   (+0.20%) |       1   →       1              |        8.40 ms →        8.42 ms   (+0.20%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      235.88 μs →      261.44 μs  (+10.84%) |       1   →       1              |      235.88 μs →      261.44 μs  (+10.84%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms →        8.15 ms   (-0.13%) |       1   →       1              |        8.16 ms →        8.15 ms   (-0.13%) | 
- │ ├ sirius::Band::initialize_subspace|kp                              |        2.17 s  →        3.28 s   (+51.37%) |       1   →       1              |        2.17 s  →        3.28 s   (+51.37%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       88.00 ms →       86.49 ms   (-1.72%) |       4   →       4              |      352.02 ms →      345.95 ms   (-1.72%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.18 ms →       25.23 ms   (+0.22%) |       1   →       1              |       25.18 ms →       25.23 ms   (+0.22%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.40 ms →       14.37 ms   (-0.26%) |       1   →       1              |       14.40 ms →       14.37 ms   (-0.26%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.19 s  →        1.19 s    (+0.23%) |       1   →       1              |        1.19 s  →        1.19 s    (+0.23%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      969.18 ms →      971.33 ms   (+0.22%) |       1   →       1              |      969.18 ms →      971.33 ms   (+0.22%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      304.32 ms →      302.11 ms   (-0.73%) |       1   →       1              |      304.32 ms →      302.11 ms   (-0.73%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      175.51 ms →      172.06 ms   (-1.97%) |       1   →       1              |      175.51 ms →      172.06 ms   (-1.97%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      175.51 ms →      172.05 ms   (-1.97%) |       1   →       1              |      175.51 ms →      172.05 ms   (-1.97%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      110.37 ms →      111.49 ms   (+1.01%) |       1   →       1              |      110.37 ms →      111.49 ms   (+1.01%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      174.41 ms →      171.90 ms   (-1.44%) |       1   →       1              |      174.41 ms →      171.90 ms   (-1.44%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      174.40 ms →      171.90 ms   (-1.44%) |       1   →       1              |      174.40 ms →      171.90 ms   (-1.44%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      158.01 ms →      164.74 ms   (+4.26%) |       1   →       1              |      158.01 ms →      164.74 ms   (+4.26%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      107.52 ms →      114.08 ms   (+6.10%) |       1   →       1              |      107.52 ms →      114.08 ms   (+6.10%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.75 ms →        3.73 ms   (-0.38%) |       1   →       1              |        3.75 ms →        3.73 ms   (-0.38%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.29 ms →       90.09 ms   (+0.89%) |       1   →       1              |       89.29 ms →       90.09 ms   (+0.89%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.76 ms →       12.27 ms   (+4.40%) |       1   →       1              |       11.76 ms →       12.27 ms   (+4.40%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.31 ms →       64.21 ms   (-0.17%) |       2   →       2              |      128.62 ms →      128.41 ms   (-0.17%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.03 ms →       70.05 ms  (+18.66%) |       2   →       2              |      118.06 ms →      140.09 ms  (+18.66%) | 
  │ │ │ ├ sddk::inner                                                   |       58.89 ms                             |       2                          |      117.77 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       19.95 μs                             |       2                          |       39.91 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.19 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      690.43 μs                             |       4                          |        2.76 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        6.38 ms                             |       2                          |       12.76 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        69.97 ms            |                   2              |                       139.94 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        72.00 ns            |                   2              |                       144.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        69.55 ms            |                   2              |                       139.10 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       560.50 ns            |                   2              |                         1.12 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      115.17 ms                             |       1                          |      115.17 ms                             | 
  │ │ ├ sddk::transform                                                 |       36.04 ms                             |       1                          |       36.04 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.36 μs                             |       1                          |       14.36 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       19.39 μs                             |       1                          |       19.39 μs                             | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |                         1.13 s             |                   1              |                         1.13 s             | 
  │ │ └ sddk::wf_trans                                                  |                       118.30 ms            |                   1              |                       118.30 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                       117.34 ms            |                   1              |                       117.34 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      538.00 ns →      440.00 ns  (-18.22%) |       1   →       1              |      538.00 ns →      440.00 ns  (-18.22%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      143.06 s  →      226.16 s   (+58.08%) |       1   →       1              |      143.06 s  →      226.16 s   (+58.08%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.14 ms →        2.24 ms   (+4.69%) |      31   →      30     (-3.23%) |       66.47 ms →       67.35 ms   (+1.31%) | 
  │ ├ sirius::Density                                                   |                        75.75 ms            |                   1              |                        75.75 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.16 ms            |                   2              |                        10.33 ms            | 
  │ │ └ sirius::Density::update                                         |                        65.30 ms            |                   1              |                        65.30 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        65.11 ms            |                   1              |                        65.11 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                         3.50 ms            |                   1              |                         3.50 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        57.73 ms            |                   1              |                        57.73 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         2.53 ms            |                   1              |                         2.53 ms            | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.32 s  →        5.02 s   (+51.21%) |      43   →      45     (+4.65%) |      142.65 s  →      225.74 s   (+58.25%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        7.94 ms →        8.50 ms   (+7.06%) |      43   →      45     (+4.65%) |      341.59 ms →      382.71 ms  (+12.04%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        7.61 ms →        6.61 ms  (-13.12%) |      43   →      45     (+4.65%) |      327.13 ms →      297.43 ms   (-9.08%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.49 ms →        1.44 ms   (-3.89%) |      43   →      45     (+4.65%) |       64.23 ms →       64.60 ms   (+0.58%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.67 ms →        3.69 ms  (-20.99%) |      43   →      45     (+4.65%) |      200.95 ms →      166.16 ms  (-17.31%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.45 μs →       60.65 μs   (-1.31%) |      86   →      90     (+4.65%) |        5.28 ms →        5.46 ms   (+3.28%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       82.48 μs →      606.71 μs (+635.56%) |      43   →      45     (+4.65%) |        3.55 ms →       27.30 ms (+669.77%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       71.14 μs →        1.11 ms (+1456.13%) |      43   →      45     (+4.65%) |        3.06 ms →       49.81 ms (+1528.51%) | 
- │ │ ├ sirius::Band::solve                                             |        2.63 s  →        4.09 s   (+55.81%) |      43   →      45     (+4.65%) |      112.90 s  →      184.09 s   (+63.06%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      212.88 μs →      210.58 μs   (-1.08%) |      43   →      45     (+4.65%) |        9.15 ms →        9.48 ms   (+3.52%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      206.12 μs →      201.10 μs   (-2.44%) |      43   →      45     (+4.65%) |        8.86 ms →        9.05 ms   (+2.10%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.07 μs →        5.13 μs   (+1.20%) |      43   →      45     (+4.65%) |      217.95 μs →      230.83 μs   (+5.91%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.60 s  →        4.00 s   (+53.78%) |      43   →      45     (+4.65%) |      111.80 s  →      179.93 s   (+60.93%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       69.18 ms →       57.16 ms  (-17.38%) |      43   →      45     (+4.65%) |        2.97 s  →        2.57 s   (-13.54%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.43 ms →        3.88 ms  (-28.51%) |     258   →     270     (+4.65%) |        1.40 s  →        1.05 s   (-25.18%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.04 ms →        1.51 ms  (-26.05%) |      43   →      45     (+4.65%) |       87.83 ms →       67.97 ms  (-22.62%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      420.39 μs →      433.37 μs   (+3.09%) |      43   →      45     (+4.65%) |       18.08 ms →       19.50 ms   (+7.88%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      948.93 μs →      815.63 μs  (-14.05%) |      43   →      45     (+4.65%) |       40.80 ms →       36.70 ms  (-10.05%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.50 s  →        3.92 s   (+56.34%) |      43   →      45     (+4.65%) |      107.70 s  →      176.20 s   (+63.61%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.79 ms →      203.70 ms   (-5.16%) |     208   →     210     (+0.96%) |       44.68 s  →       42.78 s    (-4.25%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.97 ms →      143.34 ms   (-5.68%) |     208   →     210     (+0.96%) |       31.61 s  →       30.10 s    (-4.77%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.47 ms →       25.45 ms   (-7.38%) |     208   →     210     (+0.96%) |        5.71 s  →        5.34 s    (-6.49%) | 
+ │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      677.99 μs →      332.94 μs  (-50.89%) |     208   →     210     (+0.96%) |      141.02 ms →       69.92 ms  (-50.42%) | 
+ │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.27 ms →        1.54 ms  (-52.75%) |      43   →      45     (+4.65%) |      140.58 ms →       69.51 ms  (-50.55%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.32 ms →       20.58 ms   (-7.79%) |     208   →     210     (+0.96%) |        4.64 s  →        4.32 s    (-6.91%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      670.91 μs →      712.38 μs   (+6.18%) |     208   →     210     (+0.96%) |      139.55 ms →      149.60 ms   (+7.20%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.23 ms →        3.31 ms   (+2.47%) |      43   →      45     (+4.65%) |      139.01 ms →      149.08 ms   (+7.24%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       34.15 ms →       32.00 ms   (-6.30%) |     208   →     210     (+0.96%) |        7.10 s  →        6.72 s    (-5.40%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.38 ms →       19.91 ms   (-6.85%) |     208   →     210     (+0.96%) |        4.45 s  →        4.18 s    (-5.95%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.64 ms   (-0.45%) |     208   →     210     (+0.96%) |      551.55 ms →      554.33 ms   (+0.50%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.72 ms →       21.71 ms   (-4.44%) |     208   →     210     (+0.96%) |        4.73 s  →        4.56 s    (-3.52%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.51 ms →        2.39 ms   (-4.98%) |     208   →     210     (+0.96%) |      523.09 ms →      501.82 ms   (-4.06%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.71 ms →       17.99 ms   (-3.86%) |     416   →     420     (+0.96%) |        7.78 s  →        7.56 s    (-2.93%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       82.21 ms →      130.17 ms  (+58.35%) |     208   →     210     (+0.96%) |       17.10 s  →       27.34 s   (+59.87%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.51 ms                             |     373                          |        3.92 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       19.67 μs                             |     373                          |        7.34 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.47 ms                             |     746                          |        3.33 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      102.41 μs                             |     746                          |       76.39 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.35 ms                             |     373                          |      503.99 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.05 ms                             |     208                          |        6.25 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       21.51 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.73 μs                             |     165                          |        3.42 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       62.54 μs                             |     495                          |       30.96 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         9.04 ms            |                 375              |                         3.39 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       156.66 ns            |                 375              |                        58.75 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         9.03 ms            |                 375              |                         3.39 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       343.28 ns            |                 375              |                       128.73 μs            | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |                         3.20 ms            |                 210              |                       671.43 ms            | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |                         5.09 ms            |                 210              |                         1.07 s             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        26.28 ms            |                 795              |                        20.89 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                        18.47 ms            |                1.13 K            |                        20.78 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       25.23 ms →       15.51 ms  (-38.51%) |     208   →     210     (+0.96%) |        5.25 s  →        3.26 s   (-37.91%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       21.01 ms                             |     208                          |        4.37 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       44.54 μs                             |     208                          |        9.26 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        7.92 ms                             |     416                          |        3.29 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      237.11 μs                             |     416                          |       98.64 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        4.65 ms                             |     208                          |      966.66 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        13.86 ms            |                 210              |                         2.91 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       162.74 ns            |                 210              |                        34.18 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                        13.84 ms            |                 210              |                         2.91 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       277.12 ns            |                 210              |                        58.20 μs            | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      164.74 ms                             |     208                          |       34.27 s                              | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |                       395.72 ms            |                 210              |                        83.10 s             | 
- │ │ │ │   ├ sirius::residuals                                         |       20.00 ms →       39.35 ms  (+96.73%) |     207   →     205     (-0.97%) |        4.14 s  →        8.07 s   (+94.83%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.35 μs                             |     171                          |        2.80 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       60.11 μs                             |     342                          |       20.56 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        40.12 ms            |                 185              |                         7.42 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                        19.99 ms            |                 370              |                         7.40 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        3.41 ms →        1.49 ms  (-56.20%) |     171   →     185     (+8.19%) |      582.90 ms →      276.22 ms  (-52.61%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.23 ms →      138.05 ms (+169.45%) |      44   →      84    (+90.91%) |        2.25 s  →       11.60 s  (+414.41%) | 
  │ │ │ │     ├ sddk::transform                                         |       49.81 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.90 μs                             |      45                          |      580.32 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       17.20 μs                             |      46                          |      791.32 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        93.93 ms            |                 123              |                        11.55 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        71.03 ms            |                 162              |                        11.51 s             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      563.42 ns →      586.20 ns   (+4.04%) |      43   →      45     (+4.65%) |       24.23 μs →       26.38 μs   (+8.88%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       26.05 μs →        3.07 ms (+11703.62%) |      43   →      45     (+4.65%) |        1.12 ms →      138.37 ms (+12252.63%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.55 ms →      192.98 ms (+5338.66%) |      43   →      45     (+4.65%) |      152.57 ms →        8.68 s  (+5591.62%) | 
  │ │ ├ sirius::Density::generate                                       |      298.69 ms →      309.83 ms   (+3.73%) |      43   →      45     (+4.65%) |       12.84 s  →       13.94 s    (+8.55%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      294.72 ms →      305.89 ms   (+3.79%) |      43   →      45     (+4.65%) |       12.67 s  →       13.76 s    (+8.62%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.00 ms →       66.96 ms   (-0.06%) |      43   →      45     (+4.65%) |        2.88 s  →        3.01 s    (+4.59%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       61.63 μs →       55.39 μs  (-10.13%) |      43   →      45     (+4.65%) |        2.65 ms →        2.49 ms   (-5.95%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms →        1.19 ms   (+1.28%) |       2   →       2              |        2.35 ms →        2.39 ms   (+1.28%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.78 ms →       55.52 ms   (-0.45%) |      43   →      45     (+4.65%) |        2.40 s  →        2.50 s    (+4.18%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       60.81 ms →       68.46 ms  (+12.57%) |      43   →      45     (+4.65%) |        2.61 s  →        3.08 s   (+17.81%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.50 μs →        9.88 μs   (+3.98%) |      43   →      45     (+4.65%) |      408.69 μs →      444.72 μs   (+8.82%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.30 ms →        2.31 ms   (+0.14%) |      43   →      45     (+4.65%) |       99.04 ms →      103.79 ms   (+4.80%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       57.94 ms →       58.21 ms   (+0.47%) |      43   →      45     (+4.65%) |        2.49 s  →        2.62 s    (+5.15%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.50 ms →        6.65 ms   (+2.37%) |      43   →      45     (+4.65%) |      279.50 ms →      299.42 ms   (+7.13%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      586.12 ns →      824.82 ns  (+40.73%) |      43   →      45     (+4.65%) |       25.20 μs →       37.12 μs  (+47.27%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.13 ms →      104.87 ms   (+0.72%) |      43   →      45     (+4.65%) |        4.48 s  →        4.72 s    (+5.40%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.40 ms   (-0.13%) |      43   →      45     (+4.65%) |      103.27 ms →      107.93 ms   (+4.52%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.07 ms →       20.35 ms   (+1.42%) |      43   →      45     (+4.65%) |      863.03 ms →      915.97 ms   (+6.13%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms →       20.18 ms   (+1.41%) |      43   →      45     (+4.65%) |      855.68 ms →      908.13 ms   (+6.13%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      321.47 ns →      322.49 ns   (+0.32%) |      43   →      45     (+4.65%) |       13.82 μs →       14.51 μs   (+4.98%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.27 ms   (+0.94%) |      43   →      45     (+4.65%) |       53.98 ms →       57.02 ms   (+5.63%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.72 ms →        2.67 ms   (-1.84%) |      43   →      45     (+4.65%) |      116.99 ms →      120.18 ms   (+2.73%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                         4.33 ms            |                 405              |                         1.75 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                         4.14 ms            |                 405              |                         1.68 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                         4.14 ms            |                 405              |                         1.68 s             | 
+ │ │ ├ sirius::Density::mix                                            |      148.31 ms →      106.79 ms  (-27.99%) |      43   →      45     (+4.65%) |        6.38 s  →        4.81 s   (-24.64%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      251.04 μs →      213.87 μs  (-14.81%) |      43   →      45     (+4.65%) |       10.79 ms →        9.62 ms  (-10.84%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.78 ms →        2.54 ms  (-32.91%) |      43   →      45     (+4.65%) |      162.67 ms →      114.20 ms  (-29.79%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.59 ms →        2.39 ms  (-33.52%) |      43   →      45     (+4.65%) |      154.47 ms →      107.47 ms  (-30.43%) | 
- │ │ ├ sirius::Potential::generate                                     |      184.42 ms →      208.38 ms  (+13.00%) |      43   →      45     (+4.65%) |        7.93 s  →        9.38 s   (+18.25%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       63.89 ms →       65.05 ms   (+1.82%) |      43   →      45     (+4.65%) |        2.75 s  →        2.93 s    (+6.56%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.94 ms →        3.54 ms  (-60.34%) |      43   →      45     (+4.65%) |      384.32 ms →      159.52 ms  (-58.49%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.42 ms →        4.51 ms   (+2.12%) |      43   →      45     (+4.65%) |      189.96 ms →      203.00 ms   (+6.87%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.24 ms →        4.33 ms   (+2.13%) |      43   →      45     (+4.65%) |      182.39 ms →      194.93 ms   (+6.88%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.24 ms →        4.33 ms   (+2.14%) |      43   →      45     (+4.65%) |      182.34 ms →      194.91 ms   (+6.89%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      233.70 μs →      211.65 μs   (-9.44%) |      86   →      90     (+4.65%) |       20.10 ms →       19.05 ms   (-5.22%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       94.87 ms →      117.94 ms  (+24.32%) |      43   →      45     (+4.65%) |        4.08 s  →        5.31 s   (+30.10%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       94.87 ms →      116.91 ms  (+23.23%) |      43   →      45     (+4.65%) |        4.08 s  →        5.26 s   (+28.96%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.65 ms →        1.49 ms  (-10.08%) |     215   →     360    (+67.44%) |      355.40 ms →      535.11 ms  (+50.56%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.73 ms →        2.48 ms   (-9.24%) |     387   →     540    (+39.53%) |        1.06 s  →        1.34 s   (+26.64%) | 
+ │ │ │ │   ├ sirius::gradient                                          |        2.40 ms →        1.86 ms  (-22.46%) |      43   →      45     (+4.65%) |      103.04 ms →       83.62 ms  (-18.85%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      706.46 μs →      524.65 μs  (-25.74%) |     129   →     135     (+4.65%) |       91.13 ms →       70.83 ms  (-22.28%) | 
+ │ │ │ │   ├ sirius::dot                                               |        2.82 ms →      902.90 μs  (-67.96%) |      43   →      45     (+4.65%) |      121.17 ms →       40.63 ms  (-66.47%) | 
+ │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms →      724.38 μs  (-71.88%) |      43   →      45     (+4.65%) |      110.75 ms →       32.60 ms  (-70.57%) | 
  │ │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                |                         9.54 ms            |                  90              |                       858.68 ms            | 
- │ │ │ │   └ sirius::divergence                                        |       22.51 ms →       19.74 ms  (-12.29%) |      43   →      90   (+109.30%) |      967.73 ms →        1.78 s   (+83.57%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.42 ms →        2.44 ms   (+0.71%) |      43   →      90   (+109.30%) |      104.19 ms →      219.63 ms (+110.80%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.72 ms →        3.47 ms   (-6.58%) |      43   →      45     (+4.65%) |      159.84 ms →      156.27 ms   (-2.24%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.92 ms →       20.91 ms   (-0.04%) |      43   →      45     (+4.65%) |      899.71 ms →      941.15 ms   (+4.61%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      192.44 ns →      204.20 ns   (+6.11%) |      43   →      45     (+4.65%) |        8.28 μs →        9.19 μs  (+11.05%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      346.09 ns →      385.16 ns  (+11.29%) |      43   →      45     (+4.65%) |       14.88 μs →       17.33 μs  (+16.46%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.26 ms →        2.24 ms   (-0.79%) |      43   →      45     (+4.65%) |       97.30 ms →      101.02 ms   (+3.82%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.25 ms                             |     301                          |        1.28 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.12 ms                             |     301                          |        1.24 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.12 ms                             |     301                          |        1.24 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.23 ms →        4.23 ms   (-0.07%) |     129   →     135     (+4.65%) |      545.63 ms →      570.63 ms   (+4.58%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.01 ms →        4.06 ms   (+1.04%) |     129   →     135     (+4.65%) |      517.74 ms →      547.44 ms   (+5.74%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.03 ms →        4.17 ms   (+3.46%) |      43   →      45     (+4.65%) |      173.25 ms →      187.58 ms   (+8.27%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       99.69 μs →       13.46 ms (+13397.63%) |      43   →      45     (+4.65%) |        4.29 ms →      605.54 ms (+14025.43%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       96.08 μs →       13.45 ms (+13897.72%) |      43   →      45     (+4.65%) |        4.13 ms →      605.21 ms (+14548.78%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.66 ms →        5.45 ms  (-18.18%) |       2   →       2              |       13.32 ms →       10.89 ms  (-18.18%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.26 ms →        4.25 ms   (-0.36%) |       6   →       6              |       25.58 ms →       25.49 ms   (-0.36%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.25 ms →        4.17 ms   (-1.98%) |       6   →       6              |       25.52 ms →       25.01 ms   (-1.98%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.25 ms →        4.17 ms   (-1.98%) |       6   →       6              |       25.52 ms →       25.01 ms   (-1.98%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.03 ms →        4.16 ms   (+3.37%) |       3   →       3              |       12.08 ms →       12.48 ms   (+3.37%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.02 ms →        4.11 ms   (+2.34%) |       3   →       3              |       12.05 ms →       12.33 ms   (+2.34%) | 
  ├ sirius::Periodic_function|inner                                     |        4.36 ms →        4.27 ms   (-2.02%) |       2   →       2              |        8.71 ms →        8.53 ms   (-2.02%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.35 ms →        4.26 ms   (-2.03%) |       2   →       2              |        8.69 ms →        8.52 ms   (-2.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.35 ms →        4.26 ms   (-2.03%) |       2   →       2              |        8.69 ms →        8.52 ms   (-2.03%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        3.97 ms →        4.10 ms   (+3.19%) |       1   →       1              |        3.97 ms →        4.10 ms   (+3.19%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.96 ms →        4.01 ms   (+1.12%) |       1   →       1              |        3.96 ms →        4.01 ms   (+1.12%) | 
+ └ sirius::finalize                                                    |      355.56 ms →      302.74 ms  (-14.85%) |       1   →       1              |      355.56 ms →      302.74 ms  (-14.85%) | 
  ====================================================================================================================================================================================================
```
