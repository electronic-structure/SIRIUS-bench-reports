# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |     1068.14 s  →      492.01 s   (-53.94%) |       1   →       1              |     1068.14 s  →      492.01 s   (-53.94%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.68 s    (-2.36%) |       1   →       1              |        2.75 s  →        2.68 s    (-2.36%) | 
  ├ sirius::Simulation_context::initialize                              |        4.85 s  →        5.16 s    (+6.47%) |       1   →       1              |        4.85 s  →        5.16 s    (+6.47%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       17.92 ms →       44.06 ms (+145.89%) |       1   →       1              |       17.92 ms →       44.06 ms (+145.89%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      212.50 ms →      215.93 ms   (+1.61%) |       1   →       1              |      212.50 ms →      215.93 ms   (+1.61%) | 
  │ │ ├ sirius::Atom_type::init                                         |       89.71 ms →       92.12 ms   (+2.68%) |       2   →       2              |      179.42 ms →      184.23 ms   (+2.68%) | 
  │ │ └ sirius::Unit_cell::update                                       |       33.00 ms →       31.50 ms   (-4.56%) |       1   →       1              |       33.00 ms →       31.50 ms   (-4.56%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       15.17 ms →       12.97 ms  (-14.48%) |       1   →       1              |       15.17 ms →       12.97 ms  (-14.48%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.79 ms →       18.48 ms   (+3.86%) |       1   →       1              |       17.79 ms →       18.48 ms   (+3.86%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.77 ms →       18.45 ms   (+3.84%) |       1   →       1              |       17.77 ms →       18.45 ms   (+3.84%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.02 ms →        4.17 ms   (+3.79%) |       1   →       1              |        4.02 ms →        4.17 ms   (+3.79%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        4.60 ms →        4.60 ms   (+0.11%) |       1   →       1              |        4.60 ms →        4.60 ms   (+0.11%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      103.18 μs →      112.57 μs   (+9.10%) |       1   →       1              |      103.18 μs →      112.57 μs   (+9.10%) | 
  │ └ sirius::Simulation_context::update                                |        4.58 s  →        4.85 s    (+6.05%) |       1   →       1              |        4.58 s  →        4.85 s    (+6.05%) | 
- │   ├ sirius::Unit_cell::update                                       |       17.43 ms →       20.57 ms  (+18.00%) |       1   →       1              |       17.43 ms →       20.57 ms  (+18.00%) | 
- │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.84 ms →       12.03 ms  (+36.04%) |       1   →       1              |        8.84 ms →       12.03 ms  (+36.04%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        8.55 ms →        8.50 ms   (-0.58%) |       1   →       1              |        8.55 ms →        8.50 ms   (-0.58%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        8.53 ms →        8.47 ms   (-0.71%) |       1   →       1              |        8.53 ms →        8.47 ms   (-0.71%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.74 ms →        3.68 ms   (-1.60%) |       1   →       1              |        3.74 ms →        3.68 ms   (-1.60%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        4.61 ms →        4.61 ms   (-0.16%) |       1   →       1              |        4.61 ms →        4.61 ms   (-0.16%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      105.93 μs →      107.79 μs   (+1.76%) |       1   →       1              |      105.93 μs →      107.79 μs   (+1.76%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      142.04 ms →      137.28 ms   (-3.35%) |       2   →       2              |      284.09 ms →      274.57 ms   (-3.35%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       13.24 ms →       12.00 ms   (-9.30%) |       2   →       2              |       26.47 ms →       24.01 ms   (-9.30%) | 
- │   ├ sirius::Radial_integrals|rho_pseudo                             |       11.11 ms →       12.65 ms  (+13.90%) |       1   →       1              |       11.11 ms →       12.65 ms  (+13.90%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       50.59 ms →       48.62 ms   (-3.90%) |       2   →       2              |      101.18 ms →       97.23 ms   (-3.90%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       34.04 ms →       32.05 ms   (-5.84%) |       2   →       2              |       68.07 ms →       64.09 ms   (-5.84%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       46.50 ms →       48.02 ms   (+3.27%) |       4   →       4              |      185.99 ms →      192.07 ms   (+3.27%) | 
  │   ├ sddk::Gvec::init                                                |      177.22 ms →      171.64 ms   (-3.15%) |       2   →       2              |      354.44 ms →      343.27 ms   (-3.15%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.80 ms →      129.08 ms   (-2.07%) |       2   →       2              |      263.60 ms →      258.15 ms   (-2.07%) | 
+ │   ├ sddk::Gvec_shells                                               |      306.74 ms →      164.14 ms  (-46.49%) |       1   →       1              |      306.74 ms →      164.14 ms  (-46.49%) | 
+ │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        3.05 ms →        2.40 ms  (-21.56%) |       1   →       1              |        3.05 ms →        2.40 ms  (-21.56%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.41 ms →      292.52 ms   (-0.98%) |       2   →       2              |      590.81 ms →      585.04 ms   (-0.98%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      486.63 ms →      376.18 ms  (-22.70%) |       1   →       1              |      486.63 ms →      376.18 ms  (-22.70%) | 
- │ ├ sirius::K_point::K_point                                          |        2.88 μs →        4.77 μs  (+65.58%) |       4   →       4              |       11.52 μs →       19.07 μs  (+65.58%) | 
+ │ └ sirius::K_point_set::initialize                                   |      486.54 ms →      376.06 ms  (-22.71%) |       1   →       1              |      486.54 ms →      376.06 ms  (-22.71%) | 
+ │   └ sirius::K_point::initialize                                     |      121.62 ms →       94.00 ms  (-22.71%) |       4   →       4              |      486.49 ms →      376.00 ms  (-22.71%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |      115.25 ms →       87.96 ms  (-23.67%) |       4   →       4              |      460.99 ms →      351.86 ms  (-23.67%) | 
  │     │ └ sddk::Gvec::init                                            |        4.11 ms →        3.76 ms   (-8.60%) |       4   →       4              |       16.44 ms →       15.02 ms   (-8.60%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.05 μs →        8.16 μs   (+1.41%) |       4   →       4              |       32.19 μs →       32.65 μs   (+1.41%) | 
  │     └ sirius::K_point::update                                       |        4.86 ms →        4.76 ms   (-2.15%) |       4   →       4              |       19.45 ms →       19.03 ms   (-2.15%) | 
  │       └ sirius::Beta_projectors                                     |        3.11 ms →        3.22 ms   (+3.42%) |       4   →       4              |       12.45 ms →       12.88 ms   (+3.42%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        2.27 ms →        2.41 ms   (+6.04%) |       4   →       4              |        9.09 ms →        9.64 ms   (+6.04%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.05 ms →        5.08 ms   (+0.45%) |       2   →       2              |       10.11 ms →       10.15 ms   (+0.45%) | 
- ├ sirius::Potential                                                   |        1.06 s  →        1.23 s   (+16.69%) |       1   →       1              |        1.06 s  →        1.23 s   (+16.69%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.74 ms   (-0.90%) |       6   →       5    (-16.67%) |       34.75 ms →       28.70 ms  (-17.41%) | 
- │ └ sirius::Potential::update                                         |        1.02 s  →        1.20 s   (+17.85%) |       1   →       1              |        1.02 s  →        1.20 s   (+17.85%) | 
- │   └ sirius::Potential::generate_local_potential                     |        1.02 s  →        1.20 s   (+17.86%) |       1   →       1              |        1.02 s  →        1.20 s   (+17.86%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |      859.24 ms →        1.02 s   (+18.57%) |       1   →       1              |      859.24 ms →        1.02 s   (+18.57%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |      161.85 ms →      181.11 ms  (+11.90%) |       1   →       1              |      161.85 ms →      181.11 ms  (+11.90%) | 
  ├ sirius::Density                                                     |      862.56 ms →      912.24 ms   (+5.76%) |       1   →       1              |      862.56 ms →      912.24 ms   (+5.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.07 ms →        5.03 ms   (-0.70%) |       2   →       2              |       10.14 ms →       10.07 ms   (-0.70%) | 
  │ └ sirius::Density::update                                           |      852.15 ms →      901.90 ms   (+5.84%) |       1   →       1              |      852.15 ms →      901.90 ms   (+5.84%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      851.71 ms →      901.49 ms   (+5.84%) |       1   →       1              |      851.71 ms →      901.49 ms   (+5.84%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       106.28 μs            |                   1              |                       106.28 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      686.61 ms →      654.51 ms   (-4.67%) |       1   →       1              |      686.61 ms →      654.51 ms   (-4.67%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |      164.64 ms →      246.42 ms  (+49.67%) |       1   →       1              |      164.64 ms →      246.42 ms  (+49.67%) | 
  ├ sirius::Density::initial_density                                    |      887.68 ms →      806.21 ms   (-9.18%) |       1   →       1              |      887.68 ms →      806.21 ms   (-9.18%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      831.97 ms →      527.12 ms  (-36.64%) |       1   →       1              |      831.97 ms →      527.12 ms  (-36.64%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.07 ms →      115.41 ms (+2177.06%) |       2   →       2              |       10.14 ms →      230.81 ms (+2177.06%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.94 ms →       12.12 ms  (+21.93%) |       1   →       1              |        9.94 ms →       12.12 ms  (+21.93%) | 
+ ├ sirius::Potential::generate                                         |        1.54 s  →        1.31 s   (-14.61%) |       1   →       1              |        1.54 s  →        1.31 s   (-14.61%) | 
+ │ ├ sirius::Potential::poisson                                        |      978.14 ms →      785.22 ms  (-19.72%) |       1   →       1              |      978.14 ms →      785.22 ms  (-19.72%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |      456.65 ms →        5.35 ms  (-98.83%) |       1   →       1              |      456.65 ms →        5.35 ms  (-98.83%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.53 ms →       10.63 ms   (+0.95%) |       1   →       1              |       10.53 ms →       10.63 ms   (+0.95%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.50 ms →       10.19 ms   (-2.95%) |       1   →       1              |       10.50 ms →       10.19 ms   (-2.95%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.50 ms →       10.19 ms   (-2.95%) |       1   →       1              |       10.50 ms →       10.19 ms   (-2.95%) | 
+ │ ├ sirius::Periodic_function::add                                    |      661.79 μs →      555.09 μs  (-16.12%) |       2   →       2              |        1.32 ms →        1.11 ms  (-16.12%) | 
+ │ ├ sirius::Potential::xc                                             |       72.76 ms →       48.88 ms  (-32.82%) |       1   →       1              |       72.76 ms →       48.88 ms  (-32.82%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       72.76 ms →       46.59 ms  (-35.97%) |       1   →       1              |       72.76 ms →       46.59 ms  (-35.97%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        5.69 ms →        6.04 ms   (+6.12%) |       2   →       1    (-50.00%) |       11.38 ms →        6.04 ms  (-46.94%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        8.26 ms                             |       1                          |        8.26 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        16.45 ms            |                   2              |                        32.91 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.87 ms →        6.13 ms   (+4.45%) |       1   →       1              |        5.87 ms →        6.13 ms   (+4.45%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.55 ms →       93.71 ms   (+0.17%) |       1   →       1              |       93.55 ms →       93.71 ms   (+0.17%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      385.45 ms →      377.18 ms   (-2.15%) |       1   →       1              |      385.45 ms →      377.18 ms   (-2.15%) | 
- ├ sirius::Hamiltonian0                                                |        8.59 ms →       13.13 ms  (+52.80%) |       1   →       1              |        8.59 ms →       13.13 ms  (+52.80%) | 
  │ ├ sirius::Local_operator                                            |        8.15 ms →        8.16 ms   (+0.14%) |       1   →       1              |        8.15 ms →        8.16 ms   (+0.14%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.60 ms →        4.53 ms   (-1.37%) |       1   →       1              |        4.60 ms →        4.53 ms   (-1.37%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.56 ms →        2.62 ms   (+2.38%) |       1   →       1              |        2.56 ms →        2.62 ms   (+2.38%) | 
  │ ├ sirius::Non_local_operator                                        |       63.56 μs →       62.63 μs   (-1.47%) |       2   →       2              |      127.12 μs →      125.26 μs   (-1.47%) | 
- │ ├ sirius::D_operator::initialize                                    |      174.54 μs →        1.85 ms (+960.01%) |       1   →       1              |      174.54 μs →        1.85 ms (+960.01%) | 
- │ └ sirius::Q_operator::initialize                                    |       86.75 μs →        2.93 ms (+3282.59%) |       1   →       1              |       86.75 μs →        2.93 ms (+3282.59%) | 
  ├ sirius::Band::initialize_subspace                                   |        6.15 s  →        5.92 s    (-3.74%) |       1   →       1              |        6.15 s  →        5.92 s    (-3.74%) | 
- │ ├ sirius::Hamiltonian_k                                             |      312.16 μs →      510.74 μs  (+63.61%) |       4   →       4              |        1.25 ms →        2.04 ms  (+63.61%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      307.16 μs →      502.26 μs  (+63.52%) |       4   →       4              |        1.23 ms →        2.01 ms  (+63.52%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.50 μs →        3.66 μs   (+4.66%) |       4   →       4              |       13.98 μs →       14.63 μs   (+4.66%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.54 s  →        1.48 s    (-3.80%) |       4   →       4              |        6.15 s  →        5.92 s    (-3.80%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.89 ms →       32.41 ms   (-1.44%) |      16   →      16              |      526.18 ms →      518.59 ms   (-1.44%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       34.42 ms →       33.69 ms   (-2.13%) |       4   →       4              |      137.68 ms →      134.75 ms   (-2.13%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.51 ms →        6.55 ms   (+0.58%) |       4   →       4              |       26.05 ms →       26.20 ms   (+0.58%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      367.27 ms →      362.53 ms   (-1.29%) |       4   →       4              |        1.47 s  →        1.45 s    (-1.29%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      269.82 ms →      265.78 ms   (-1.50%) |       4   →       4              |        1.08 s  →        1.06 s    (-1.50%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.74 ms →       66.12 ms   (-5.18%) |       4   →       4              |      278.95 ms →      264.50 ms   (-5.18%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.89 ms →       16.42 ms   (-2.73%) |       4   →       4              |       67.54 ms →       65.70 ms   (-2.73%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.88 ms →       16.42 ms   (-2.73%) |       4   →       4              |       67.54 ms →       65.69 ms   (-2.73%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       43.85 ms →       40.28 ms   (-8.14%) |       4   →       4              |      175.40 ms →      161.13 ms   (-8.14%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.60 ms →       16.35 ms   (-1.48%) |       4   →       4              |       66.40 ms →       65.42 ms   (-1.48%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.60 ms →       16.35 ms   (-1.48%) |       4   →       4              |       66.38 ms →       65.40 ms   (-1.48%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       59.39 ms →       58.81 ms   (-0.97%) |       4   →       4              |      237.54 ms →      235.23 ms   (-0.97%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.94 ms →       37.51 ms   (+1.53%) |       4   →       4              |      147.77 ms →      150.03 ms   (+1.53%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.97 ms →        1.95 ms   (-1.01%) |       4   →       4              |        7.86 ms →        7.78 ms   (-1.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.35 ms →       40.31 ms   (-2.51%) |       4   →       4              |      165.41 ms →      161.26 ms   (-2.51%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.23 ms →        7.12 ms  (-13.56%) |       4   →       4              |       32.93 ms →       28.46 ms  (-13.56%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.04 ms →       27.22 ms   (+0.67%) |       8   →       8              |      216.33 ms →      217.77 ms   (+0.67%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.54 ms →       14.71 ms   (+1.14%) |       8   →       8              |      116.32 ms →      117.65 ms   (+1.14%) | 
  │ │ │ ├ sddk::inner                                                   |       14.48 ms                             |       8                          |      115.83 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       47.90 μs                             |       8                          |      383.23 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.66 ms            |                   8              |                       117.26 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        69.88 ns            |                   8              |                       559.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.47 ms            |                   8              |                       115.72 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       282.75 ns            |                   8              |                         2.26 μs            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      847.74 ms →      786.43 ms   (-7.23%) |       4   →       4              |        3.39 s  →        3.15 s    (-7.23%) | 
  │ │ ├ sddk::transform                                                 |       28.42 ms                             |       4                          |      113.67 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       28.63 μs                             |       4                          |      114.52 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.08 ms                             |       4                          |        4.30 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       22.30 μs                             |       4                          |       89.19 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        27.07 ms            |                   4              |                       108.28 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        26.99 ms            |                   4              |                       107.95 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      507.50 ns →      347.00 ns  (-31.63%) |       4   →       4              |        2.03 μs →        1.39 μs  (-31.63%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |     1047.61 s  →      471.95 s   (-54.95%) |       1   →       1              |     1047.61 s  →      471.95 s   (-54.95%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.34 ms   (-8.17%) |      19   →      18     (-5.26%) |      110.47 ms →       96.10 ms  (-13.01%) | 
  │ ├ sirius::Density                                                   |                         1.08 s             |                   1              |                         1.08 s             | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.23 ms            |                   2              |                        10.47 ms            | 
  │ │ └ sirius::Density::update                                         |                         1.07 s             |                   1              |                         1.07 s             | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                         1.07 s             |                   1              |                         1.07 s             | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       132.86 μs            |                   1              |                       132.86 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       583.90 ms            |                   1              |                       583.90 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                       484.85 ms            |                   1              |                       484.85 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       32.73 s  →       16.21 s   (-50.45%) |      32   →      29     (-9.38%) |     1047.21 s  →      470.23 s   (-55.10%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.98 ms →        9.65 ms  (+93.80%) |      32   →      29     (-9.38%) |      159.33 ms →      279.83 ms  (+75.63%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.49 ms →        4.12 ms   (-8.24%) |      32   →      29     (-9.38%) |      143.56 ms →      119.38 ms  (-16.84%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      918.04 μs →      796.72 μs  (-13.22%) |      32   →      29     (-9.38%) |       29.38 ms →       23.10 ms  (-21.35%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.53 ms →        2.30 ms   (-8.82%) |      32   →      29     (-9.38%) |       80.81 ms →       66.77 ms  (-17.37%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       65.73 μs →       65.87 μs   (+0.21%) |      64   →      58     (-9.38%) |        4.21 ms →        3.82 ms   (-9.18%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      174.80 μs →        1.83 ms (+946.81%) |      32   →      29     (-9.38%) |        5.59 ms →       53.06 ms (+848.67%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |      121.18 μs →        3.51 ms (+2796.39%) |      32   →      29     (-9.38%) |        3.88 ms →      101.78 ms (+2524.85%) | 
+ │ │ ├ sirius::Band::solve                                             |       29.53 s  →       13.08 s   (-55.71%) |      32   →      29     (-9.38%) |      944.82 s  →      379.22 s   (-59.86%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      305.62 μs →      475.03 μs  (+55.43%) |     128   →     116     (-9.38%) |       39.12 ms →       55.10 ms  (+40.86%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      299.28 μs →      466.69 μs  (+55.94%) |     128   →     116     (-9.38%) |       38.31 ms →       54.14 ms  (+41.32%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.86 μs →        4.21 μs  (-13.44%) |     128   →     116     (-9.38%) |      622.34 μs →      488.20 μs  (-21.55%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        7.38 s  →        3.27 s   (-55.73%) |     128   →     116     (-9.38%) |      944.78 s  →      379.05 s   (-59.88%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       16.21 ms →       12.06 ms  (-25.58%) |     128   →     116     (-9.38%) |        2.07 s  →        1.40 s   (-32.56%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      651.76 μs →      628.19 ns  (-99.90%) |     768   →     696     (-9.38%) |      500.55 ms →      437.22 μs  (-99.91%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        7.36 ms →        9.23 ms  (+25.36%) |     128   →     116     (-9.38%) |      942.33 ms →        1.07 s   (+13.61%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      369.88 μs →      368.48 μs   (-0.38%) |     128   →     116     (-9.38%) |       47.35 ms →       42.74 ms   (-9.72%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        3.28 ms →        4.23 ms  (+28.70%) |     256   →     232     (-9.38%) |      840.85 ms →      980.72 ms  (+16.63%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        7.35 s  →        3.24 s   (-55.95%) |     128   →     116     (-9.38%) |      940.60 s  →      375.53 s   (-60.08%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       73.70 ms →       62.27 ms  (-15.51%) |     865   →    1.08 K  (+24.74%) |       63.75 s  →       67.19 s    (+5.39%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       47.37 ms →       39.53 ms  (-16.55%) |     865   →    1.08 K  (+24.74%) |       40.97 s  →       42.65 s    (+4.09%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        9.48 ms →        8.50 ms  (-10.39%) |     865   →    1.08 K  (+24.74%) |        8.20 s  →        9.17 s   (+11.77%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       62.51 μs →      195.84 μs (+213.28%) |     865   →    1.08 K  (+24.74%) |       54.08 ms →      211.32 ms (+290.78%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      408.88 μs →        1.80 ms (+341.17%) |     128   →     116     (-9.38%) |       52.34 ms →      209.25 ms (+299.81%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.85 ms →        6.87 ms  (-12.49%) |     865   →    1.08 K  (+24.74%) |        6.79 s  →        7.41 s    (+9.17%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       63.44 μs →       80.07 μs  (+26.21%) |     865   →    1.08 K  (+24.74%) |       54.88 ms →       86.40 ms  (+57.44%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      408.92 μs →      718.95 μs  (+75.82%) |     128   →     116     (-9.38%) |       52.34 ms →       83.40 ms  (+59.34%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.52 ms →        8.72 ms  (-17.14%) |     865   →    1.08 K  (+24.74%) |        9.10 s  →        9.40 s    (+3.36%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.50 ms →        5.43 ms  (-16.44%) |     865   →    1.08 K  (+24.74%) |        5.62 s  →        5.86 s    (+4.23%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.54 ms →        1.50 ms   (-2.21%) |     865   →    1.08 K  (+24.74%) |        1.33 s  →        1.62 s   (+21.99%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        9.29 ms →        7.50 ms  (-19.24%) |     865   →    1.08 K  (+24.74%) |        8.04 s  →        8.10 s    (+0.74%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.57 ms →        1.11 ms  (-28.96%) |     865   →    1.08 K  (+24.74%) |        1.36 s  →        1.20 s   (-11.39%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.74 ms →        6.85 ms  (-11.47%) |    1.73 K →    2.16 K  (+24.74%) |       13.39 s  →       14.79 s   (+10.43%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       50.15 ms →       46.76 ms   (-6.77%) |     865   →    1.08 K  (+24.74%) |       43.38 s  →       50.45 s   (+16.30%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.76 ms                             |    1.60 K                        |        4.43 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       35.64 μs                             |    1.76 K                        |       62.66 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.68 ms            |                2.04 K            |                         3.43 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       110.96 ns            |                2.04 K            |                       226.58 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.67 ms            |                2.04 K            |                         3.41 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       232.73 ns            |                2.04 K            |                       475.23 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |        9.82 ms →        7.44 ms  (-24.30%) |     865   →    1.08 K  (+24.74%) |        8.50 s  →        8.02 s    (-5.57%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |       19.06 ms →       14.83 ms  (-22.20%) |     865   →    1.08 K  (+24.74%) |       16.49 s  →       16.00 s    (-2.95%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.64 ms                             |    3.33 K                        |       12.12 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.96 μs                             |    3.33 K                        |       49.85 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      665.41 μs                             |    3.33 K                        |        2.22 s                              | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.50 μs                             |    4.81 K                        |       50.44 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.10 ms            |                4.20 K            |                        21.41 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.47 ms            |                6.13 K            |                        21.25 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.80 ms →        5.14 ms  (-24.44%) |     865   →    1.08 K  (+24.74%) |        5.88 s  →        5.54 s    (-5.75%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.74 ms                             |     865                          |        4.10 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       63.91 μs                             |    1.06 K                        |       67.49 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.25 ms            |                1.08 K            |                         3.51 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       128.74 ns            |                1.08 K            |                       138.91 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.23 ms            |                1.08 K            |                         3.49 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       337.63 ns            |                1.08 K            |                       364.31 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      939.53 ms →      211.86 ms  (-77.45%) |     865   →    1.08 K  (+24.74%) |      812.69 s  →      228.59 s   (-71.87%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.88 ms →        9.97 ms  (-28.12%) |     851   →    1.06 K  (+24.44%) |       11.81 s  →       10.56 s   (-10.55%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        9.75 ms                             |     789                          |        7.69 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.84 μs                             |     789                          |       17.23 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |        2.41 ms                             |     789                          |        1.90 s                              | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       15.43 μs                             |    1.58 K                        |       24.34 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         6.93 ms            |                 963              |                         6.67 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.44 ms            |                1.93 K            |                         6.63 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      981.33 μs →      522.05 μs  (-46.80%) |     789   →     963    (+22.05%) |      774.27 ms →      502.74 ms  (-35.07%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       22.44 ms →       33.52 ms  (+49.38%) |     136   →     389   (+186.03%) |        3.05 s  →       13.04 s  (+327.28%) | 
  │ │ │ │     ├ sddk::transform                                         |       21.13 ms                             |     144                          |        3.04 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       21.47 μs                             |     144                          |        3.09 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        3.51 ms                             |     144                          |      505.94 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       21.16 μs                             |     152                          |        3.22 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        19.53 ms            |                 662              |                        12.93 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        13.74 ms            |                 935              |                        12.85 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      663.12 ns →      430.42 ns  (-35.09%) |     128   →     116     (-9.38%) |       84.88 μs →       49.93 μs  (-41.18%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.41 μs →        3.61 ms (+16755.77%) |      32   →      29     (-9.38%) |      685.08 μs →      104.65 ms (+15175.54%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      616.78 μs →       58.22 ms (+9339.99%) |      32   →      29     (-9.38%) |       19.74 ms →        1.69 s  (+8454.99%) | 
  │ │ ├ sirius::Density::generate                                       |      928.95 ms →      946.87 ms   (+1.93%) |      32   →      29     (-9.38%) |       29.73 s  →       27.46 s    (-7.63%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      535.69 ms →      586.84 ms   (+9.55%) |      32   →      29     (-9.38%) |       17.14 s  →       17.02 s    (-0.72%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       25.20 ms →       26.33 ms   (+4.47%) |     128   →     116     (-9.38%) |        3.23 s  →        3.05 s    (-5.33%) | 
+ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.79 μs →        5.14 μs  (-41.48%) |     128   →     116     (-9.38%) |        1.13 ms →      596.78 μs  (-46.96%) | 
+ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.48 μs →       10.95 μs  (-29.28%) |       8   →       8              |      123.86 μs →       87.59 μs  (-29.28%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.50 ms →       21.43 ms   (+4.55%) |     128   →     116     (-9.38%) |        2.62 s  →        2.49 s    (-5.25%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       31.14 ms →       41.86 ms  (+34.41%) |     128   →     116     (-9.38%) |        3.99 s  →        4.86 s   (+21.81%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.57 μs →        9.89 μs   (-6.42%) |     128   →     116     (-9.38%) |        1.35 ms →        1.15 ms  (-15.19%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.81%) |     128   →     116     (-9.38%) |      187.17 ms →      168.25 ms  (-10.11%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.95 ms →       28.11 ms   (-2.92%) |     128   →     116     (-9.38%) |        3.71 s  →        3.26 s   (-12.02%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.79 ms →        4.00 ms  (-16.53%) |     128   →     116     (-9.38%) |      613.25 ms →      463.91 ms  (-24.35%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      770.12 ns →      770.49 ns   (+0.05%) |     128   →     116     (-9.38%) |       98.58 μs →       89.38 μs   (-9.33%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       43.00 ms →       43.18 ms   (+0.40%) |     128   →     116     (-9.38%) |        5.50 s  →        5.01 s    (-9.01%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.70 ms →        1.70 ms   (-0.26%) |      32   →      29     (-9.38%) |       54.54 ms →       49.30 ms   (-9.61%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.37 ms →       89.11 ms   (+0.84%) |      32   →      29     (-9.38%) |        2.83 s  →        2.58 s    (-8.61%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.11 ms →       88.86 ms   (+0.85%) |      32   →      29     (-9.38%) |        2.82 s  →        2.58 s    (-8.61%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      294.12 ms →      261.08 ms  (-11.23%) |      32   →      29     (-9.38%) |        9.41 s  →        7.57 s   (-19.55%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      294.12 ms →      261.08 ms  (-11.24%) |      32   →      29     (-9.38%) |        9.41 s  →        7.57 s   (-19.56%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       31.50 ms →       26.21 ms  (-16.78%) |      32   →      29     (-9.38%) |        1.01 s  →      760.20 ms  (-24.58%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      233.49 ms →      210.24 ms   (-9.96%) |      32   →      29     (-9.38%) |        7.47 s  →        6.10 s   (-18.40%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.36 ms →       23.38 ms  (-14.55%) |      32   →      29     (-9.38%) |      875.60 ms →      678.08 ms  (-22.56%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.18 ms →       81.25 ms   (+0.08%) |      32   →      29     (-9.38%) |        2.60 s  →        2.36 s    (-9.30%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.18 ms →        7.91 ms  (-13.79%) |      32   →      29     (-9.38%) |      293.66 ms →      229.42 ms  (-21.87%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                        11.26 ms            |                 261              |                         2.94 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                        10.63 ms            |                 261              |                         2.77 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                        10.63 ms            |                 261              |                         2.77 s             | 
+ │ │ ├ sirius::Density::mix                                            |      414.36 ms →      218.36 ms  (-47.30%) |      32   →      29     (-9.38%) |       13.26 s  →        6.33 s   (-52.24%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |        1.13 ms →        1.18 ms   (+5.10%) |      32   →      29     (-9.38%) |       36.00 ms →       34.29 ms   (-4.76%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.88 ms →       10.22 ms  (-13.99%) |     424   →     379    (-10.61%) |        5.04 s  →        3.87 s   (-23.12%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       11.57 ms →       10.02 ms  (-13.33%) |     424   →     379    (-10.61%) |        4.90 s  →        3.80 s   (-22.53%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       11.57 ms →       10.02 ms  (-13.33%) |     424   →     379    (-10.61%) |        4.90 s  →        3.80 s   (-22.53%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        8.39 ms →        7.18 ms  (-14.42%) |      32   →      29     (-9.38%) |      268.41 ms →      208.16 ms  (-22.45%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.34 ms →        5.92 ms  (-19.36%) |      32   →      29     (-9.38%) |      235.01 ms →      171.75 ms  (-26.92%) | 
  │ │ ├ sirius::Potential::generate                                     |        1.43 s  →        1.43 s    (-0.20%) |      32   →      29     (-9.38%) |       45.79 s  →       41.41 s    (-9.56%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      883.89 ms →      890.88 ms   (+0.79%) |      32   →      29     (-9.38%) |       28.28 s  →       25.84 s    (-8.66%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |      124.34 ms →       52.71 ms  (-57.61%) |      32   →      29     (-9.38%) |        3.98 s  →        1.53 s   (-61.58%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       11.00 ms →       10.92 ms   (-0.76%) |      32   →      29     (-9.38%) |      352.14 ms →      316.70 ms  (-10.06%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.65 ms →       10.49 ms   (-1.44%) |      32   →      29     (-9.38%) |      340.69 ms →      304.29 ms  (-10.68%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.65 ms →       10.49 ms   (-1.44%) |      32   →      29     (-9.38%) |      340.67 ms →      304.28 ms  (-10.68%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      599.58 μs →      552.52 μs   (-7.85%) |      64   →      58     (-9.38%) |       38.37 ms →       32.05 ms  (-16.49%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       70.19 ms →       46.89 ms  (-33.19%) |      32   →      29     (-9.38%) |        2.25 s  →        1.36 s   (-39.45%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       70.19 ms →       44.69 ms  (-36.32%) |      32   →      29     (-9.38%) |        2.25 s  →        1.30 s   (-42.29%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        1.22 ms  (-59.94%) |      64   →      29    (-54.69%) |      194.29 ms →       35.27 ms  (-81.85%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        9.11 ms                             |      32                          |      291.50 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        17.70 ms            |                  58              |                         1.03 s             | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.01 ms →        9.44 ms  (+34.70%) |      32   →      29     (-9.38%) |      224.31 ms →      273.83 ms  (+22.08%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       91.07 ms   (+0.12%) |      32   →      29     (-9.38%) |        2.91 s  →        2.64 s    (-9.27%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      376.09 ms →      387.06 ms   (+2.92%) |      32   →      29     (-9.38%) |       12.03 s  →       11.22 s    (-6.73%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      298.04 ms →      261.01 ms  (-12.42%) |      32   →      29     (-9.38%) |        9.54 s  →        7.57 s   (-20.63%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      298.03 ms →      261.00 ms  (-12.43%) |      32   →      29     (-9.38%) |        9.54 s  →        7.57 s   (-20.64%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.47 ms →       24.94 ms  (-23.21%) |      32   →      29     (-9.38%) |        1.04 s  →      723.18 ms  (-30.41%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      234.47 ms →      211.41 ms   (-9.84%) |      32   →      29     (-9.38%) |        7.50 s  →        6.13 s   (-18.29%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.44 ms →       23.51 ms  (-14.31%) |      32   →      29     (-9.38%) |      877.96 ms →      681.82 ms  (-22.34%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.13 ms →        5.93 ms   (-3.20%) |      32   →      29     (-9.38%) |      196.07 ms →      172.00 ms  (-12.28%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.70 ms                             |     224                          |        2.40 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.43 ms                             |     224                          |        2.34 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.43 ms                             |     224                          |        2.34 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.19 ms →       11.13 ms   (+9.31%) |      96   →      87     (-9.38%) |      977.78 ms →      968.62 ms   (-0.94%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.97 ms →       10.64 ms   (+6.71%) |      96   →      87     (-9.38%) |      957.21 ms →      925.69 ms   (-3.29%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.05 ms →       10.63 ms   (+5.72%) |      32   →      29     (-9.38%) |      321.64 ms →      308.14 ms   (-4.20%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      120.35 μs →       34.13 ms (+28256.31%) |      32   →      29     (-9.38%) |        3.85 ms →      989.71 ms (+25597.90%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      114.82 μs →       34.12 ms (+29616.70%) |      32   →      29     (-9.38%) |        3.67 ms →      989.49 ms (+26830.76%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.27 ms →        4.64 ms  (-12.06%) |       2   →       2              |       10.54 ms →        9.27 ms  (-12.06%) | 
  │ ├ sirius::Periodic_function|inner                                   |       11.16 ms →       10.58 ms   (-5.18%) |       6   →       6              |       66.95 ms →       63.49 ms   (-5.18%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.17 ms →       10.31 ms   (+1.28%) |       6   →       6              |       61.05 ms →       61.83 ms   (+1.28%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.17 ms →       10.30 ms   (+1.28%) |       6   →       6              |       61.05 ms →       61.83 ms   (+1.28%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.65 ms →       10.50 ms   (-1.43%) |       3   →       3              |       31.96 ms →       31.51 ms   (-1.43%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.71 ms →       10.17 ms   (+4.68%) |       3   →       3              |       29.14 ms →       30.51 ms   (+4.68%) | 
  ├ sirius::Periodic_function|inner                                     |       11.09 ms →       10.59 ms   (-4.54%) |       2   →       2              |       22.18 ms →       21.18 ms   (-4.54%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.23 ms →       10.58 ms   (+3.39%) |       2   →       2              |       20.47 ms →       21.16 ms   (+3.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.23 ms →       10.58 ms   (+3.39%) |       2   →       2              |       20.47 ms →       21.16 ms   (+3.39%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.65 ms →       10.93 ms   (+2.65%) |       1   →       1              |       10.65 ms →       10.93 ms   (+2.65%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.68 ms →       10.50 ms   (+8.50%) |       1   →       1              |        9.68 ms →       10.50 ms   (+8.50%) | 
+ └ sirius::finalize                                                    |      395.46 ms →      301.64 ms  (-23.72%) |       1   →       1              |      395.46 ms →      301.64 ms  (-23.72%) | 
  ====================================================================================================================================================================================================
```
