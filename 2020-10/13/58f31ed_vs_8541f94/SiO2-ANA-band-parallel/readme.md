# Benchmark 8541f94e2e0e288633941ac63ad4d565828afb1d vs 58f31ed08f2b4e9e6d289f9ed116027f00413e03
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      292.44 s  →      250.95 s   (-14.19%) |       1   →       1              |      292.44 s  →      250.95 s   (-14.19%) | 
  ├ sirius::initialize                                                  |        2.91 s  →        2.73 s    (-6.25%) |       1   →       1              |        2.91 s  →        2.73 s    (-6.25%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.94 s    (+0.38%) |       1   →       1              |        2.93 s  →        2.94 s    (+0.38%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      358.33 μs →       24.50 ms (+6736.75%) |       1   →       1              |      358.33 μs →       24.50 ms (+6736.75%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      131.72 ms →      168.58 ms  (+27.98%) |       1   →       1              |      131.72 ms →      168.58 ms  (+27.98%) | 
- │ │ ├ sirius::Atom_type::init                                         |       53.47 ms →       71.84 ms  (+34.36%) |       2   →       2              |      106.94 ms →      143.67 ms  (+34.36%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.70 ms →       24.82 ms   (+0.48%) |       1   →       1              |       24.70 ms →       24.82 ms   (+0.48%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.50 ms →        6.21 ms   (-4.52%) |       1   →       1              |        6.50 ms →        6.21 ms   (-4.52%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.16 ms →       18.57 ms   (+2.25%) |       1   →       1              |       18.16 ms →       18.57 ms   (+2.25%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.13 ms →       18.55 ms   (+2.29%) |       1   →       1              |       18.13 ms →       18.55 ms   (+2.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (+0.01%) |       1   →       1              |        4.16 ms →        4.16 ms   (+0.01%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.44%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.44%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.82 μs →      100.96 μs   (-3.68%) |       1   →       1              |      104.82 μs →      100.96 μs   (-3.68%) | 
  │ └ sirius::Simulation_context::update                                |        2.75 s  →        2.70 s    (-1.71%) |       1   →       1              |        2.75 s  →        2.70 s    (-1.71%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.08 ms →       10.86 ms   (-2.04%) |       1   →       1              |       11.08 ms →       10.86 ms   (-2.04%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.64 ms →        4.47 ms   (-3.65%) |       1   →       1              |        4.64 ms →        4.47 ms   (-3.65%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.41 ms →        6.35 ms   (-0.93%) |       1   →       1              |        6.41 ms →        6.35 ms   (-0.93%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.39 ms →        6.33 ms   (-0.90%) |       1   →       1              |        6.39 ms →        6.33 ms   (-0.90%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.84 ms   (-1.62%) |       1   →       1              |        3.90 ms →        3.84 ms   (-1.62%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.10%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.10%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      102.34 μs →      100.55 μs   (-1.75%) |       1   →       1              |      102.34 μs →      100.55 μs   (-1.75%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       66.39 ms →       64.49 ms   (-2.85%) |       2   →       2              |      132.77 ms →      128.99 ms   (-2.85%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.16 ms   (+0.34%) |       2   →       2              |       10.29 ms →       10.33 ms   (+0.34%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.52 ms   (+1.28%) |       1   →       1              |        4.46 ms →        4.52 ms   (+1.28%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.73 ms →       21.81 ms   (+0.37%) |       2   →       2              |       43.46 ms →       43.62 ms   (+0.37%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.84 ms →       14.88 ms   (+0.27%) |       2   →       2              |       29.68 ms →       29.76 ms   (+0.27%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.91 ms   (+0.64%) |       4   →       4              |       79.13 ms →       79.64 ms   (+0.64%) | 
  │   ├ sddk::Gvec::init                                                |      179.98 ms →      174.41 ms   (-3.10%) |       2   →       2              |      359.96 ms →      348.82 ms   (-3.10%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      133.68 ms →      131.90 ms   (-1.33%) |       2   →       2              |      267.36 ms →      263.80 ms   (-1.33%) | 
  │   ├ sddk::Gvec_shells                                               |      196.70 ms →      177.55 ms   (-9.73%) |       1   →       1              |      196.70 ms →      177.55 ms   (-9.73%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.35 ms →        1.32 ms   (-1.93%) |       1   →       1              |        1.35 ms →        1.32 ms   (-1.93%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.98 ms →      294.54 ms   (+0.19%) |       2   →       2              |      587.96 ms →      589.07 ms   (+0.19%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       85.46 ms →       75.42 ms  (-11.75%) |       1   →       1              |       85.46 ms →       75.42 ms  (-11.75%) | 
  │ ├ sirius::K_point::K_point                                          |        3.01 μs →        2.74 μs   (-8.89%) |       4   →       4              |       12.04 μs →       10.97 μs   (-8.89%) | 
+ │ └ sirius::K_point_set::initialize                                   |       85.36 ms →       75.32 ms  (-11.77%) |       1   →       1              |       85.36 ms →       75.32 ms  (-11.77%) | 
+ │   └ sirius::K_point::initialize                                     |       21.33 ms →       18.82 ms  (-11.77%) |       4   →       4              |       85.32 ms →       75.27 ms  (-11.77%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       15.85 ms →       14.25 ms  (-10.09%) |       4   →       4              |       63.40 ms →       57.00 ms  (-10.09%) | 
  │     │ └ sddk::Gvec::init                                            |        4.20 ms →        3.84 ms   (-8.55%) |       4   →       4              |       16.80 ms →       15.36 ms   (-8.55%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.58 μs →        8.91 μs   (-7.03%) |       4   →       4              |       38.33 μs →       35.64 μs   (-7.03%) | 
+ │     └ sirius::K_point::update                                       |        3.93 ms →        3.28 ms  (-16.54%) |       4   →       4              |       15.73 ms →       13.13 ms  (-16.54%) | 
+ │       └ sirius::Beta_projectors                                     |        2.14 ms →        1.79 ms  (-16.48%) |       4   →       4              |        8.58 ms →        7.16 ms  (-16.48%) | 
+ │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        1.29 ms →      929.71 μs  (-28.09%) |       4   →       4              |        5.17 ms →        3.72 ms  (-28.09%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.35 ms →        5.22 ms   (-2.49%) |       2   →       2              |       10.70 ms →       10.43 ms   (-2.49%) | 
  ├ sirius::Potential                                                   |      170.27 ms →      159.27 ms   (-6.46%) |       1   →       1              |      170.27 ms →      159.27 ms   (-6.46%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.88 ms →        5.81 ms   (-1.15%) |       6   →       6              |       35.27 ms →       34.86 ms   (-1.15%) | 
  │ └ sirius::Potential::update                                         |      134.21 ms →      123.67 ms   (-7.85%) |       1   →       1              |      134.21 ms →      123.67 ms   (-7.85%) | 
  │   └ sirius::Potential::generate_local_potential                     |      133.45 ms →      122.94 ms   (-7.88%) |       1   →       1              |      133.45 ms →      122.94 ms   (-7.88%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.37 ms →      107.54 ms   (-5.14%) |       1   →       1              |      113.37 ms →      107.54 ms   (-5.14%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       19.53 ms →       14.50 ms  (-25.73%) |       1   →       1              |       19.53 ms →       14.50 ms  (-25.73%) | 
  ├ sirius::Density                                                     |      140.54 ms →      136.36 ms   (-2.98%) |       1   →       1              |      140.54 ms →      136.36 ms   (-2.98%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.32 ms →        5.15 ms   (-3.20%) |       2   →       2              |       10.64 ms →       10.30 ms   (-3.20%) | 
  │ └ sirius::Density::update                                           |      129.63 ms →      125.79 ms   (-2.97%) |       1   →       1              |      129.63 ms →      125.79 ms   (-2.97%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.20 ms →      125.36 ms   (-2.97%) |       1   →       1              |      129.20 ms →      125.36 ms   (-2.97%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       103.63 μs            |                   1              |                       103.63 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.76 ms →      109.68 ms   (-2.74%) |       1   →       1              |      112.76 ms →      109.68 ms   (-2.74%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       15.99 ms →       15.12 ms   (-5.40%) |       1   →       1              |       15.99 ms →       15.12 ms   (-5.40%) | 
  ├ sirius::Density::initial_density                                    |      175.06 ms →      174.87 ms   (-0.11%) |       1   →       1              |      175.06 ms →      174.87 ms   (-0.11%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.81 ms →      109.53 ms   (-1.15%) |       1   →       1              |      110.81 ms →      109.53 ms   (-1.15%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.82 ms →       11.43 ms   (+5.68%) |       2   →       2              |       21.64 ms →       22.87 ms   (+5.68%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.92 ms →       10.25 ms   (+3.23%) |       1   →       1              |        9.92 ms →       10.25 ms   (+3.23%) | 
  ├ sirius::Potential::generate                                         |      585.22 ms →      594.75 ms   (+1.63%) |       1   →       1              |      585.22 ms →      594.75 ms   (+1.63%) | 
  │ ├ sirius::Potential::poisson                                        |      137.80 ms →      138.52 ms   (+0.52%) |       1   →       1              |      137.80 ms →      138.52 ms   (+0.52%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.14 ms →       20.58 ms  (+27.50%) |       1   →       1              |       16.14 ms →       20.58 ms  (+27.50%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.73 ms →        9.99 ms   (-6.95%) |       1   →       1              |       10.73 ms →        9.99 ms   (-6.95%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.71 ms →        9.80 ms   (-8.45%) |       1   →       1              |       10.71 ms →        9.80 ms   (-8.45%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.71 ms →        9.80 ms   (-8.45%) |       1   →       1              |       10.71 ms →        9.80 ms   (-8.45%) | 
  │ ├ sirius::Periodic_function::add                                    |      551.73 μs →      546.93 μs   (-0.87%) |       2   →       2              |        1.10 ms →        1.09 ms   (-0.87%) | 
  │ ├ sirius::Potential::xc                                             |       52.27 ms →       54.21 ms   (+3.70%) |       1   →       1              |       52.27 ms →       54.21 ms   (+3.70%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.27 ms →       51.87 ms   (-0.76%) |       1   →       1              |       52.27 ms →       51.87 ms   (-0.76%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.73 ms →        5.72 ms   (-0.19%) |       2   →       2              |       11.46 ms →       11.44 ms   (-0.19%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms →        5.76 ms   (+9.43%) |       1   →       1              |        5.26 ms →        5.76 ms   (+9.43%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.73 ms →        6.46 ms   (-3.99%) |       1   →       1              |        6.73 ms →        6.46 ms   (-3.99%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.07 ms →       92.69 ms   (-0.41%) |       1   →       1              |       93.07 ms →       92.69 ms   (-0.41%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      292.85 ms →      300.41 ms   (+2.58%) |       1   →       1              |      292.85 ms →      300.41 ms   (+2.58%) | 
  ├ sirius::Hamiltonian0                                                |        8.50 ms →        8.61 ms   (+1.26%) |       1   →       1              |        8.50 ms →        8.61 ms   (+1.26%) | 
  │ ├ sirius::Local_operator                                            |        8.15 ms →        8.27 ms   (+1.40%) |       1   →       1              |        8.15 ms →        8.27 ms   (+1.40%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms →        4.78 ms   (+0.32%) |       1   →       1              |        4.76 ms →        4.78 ms   (+0.32%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.46 ms →        2.57 ms   (+4.18%) |       1   →       1              |        2.46 ms →        2.57 ms   (+4.18%) | 
  │ ├ sirius::Non_local_operator                                        |       62.18 μs →       62.83 μs   (+1.05%) |       2   →       2              |      124.36 μs →      125.67 μs   (+1.05%) | 
  │ ├ sirius::D_operator::initialize                                    |      101.97 μs →       93.56 μs   (-8.24%) |       1   →       1              |      101.97 μs →       93.56 μs   (-8.24%) | 
  │ └ sirius::Q_operator::initialize                                    |       70.38 μs →       70.02 μs   (-0.51%) |       1   →       1              |       70.38 μs →       70.02 μs   (-0.51%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.19 s  →        3.17 s    (-0.74%) |       1   →       1              |        3.19 s  →        3.17 s    (-0.74%) | 
- │ ├ sirius::Hamiltonian_k                                             |      212.12 μs →      378.91 μs  (+78.63%) |       4   →       4              |      848.47 μs →        1.52 ms  (+78.63%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      206.62 μs →      373.51 μs  (+80.77%) |       4   →       4              |      826.48 μs →        1.49 ms  (+80.77%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.82 μs →        3.56 μs   (-6.71%) |       4   →       4              |       15.29 μs →       14.26 μs   (-6.71%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      797.75 ms →      791.72 ms   (-0.76%) |       4   →       4              |        3.19 s  →        3.17 s    (-0.76%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.13 ms →       32.58 ms   (+1.39%) |      16   →      16              |      514.13 ms →      521.27 ms   (+1.39%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.82 ms →       14.50 ms   (-2.15%) |       4   →       4              |       59.27 ms →       57.99 ms   (-2.15%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.41 ms →        5.45 ms   (+0.81%) |       4   →       4              |       21.64 ms →       21.82 ms   (+0.81%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      361.57 ms →      355.05 ms   (-1.80%) |       4   →       4              |        1.45 s  →        1.42 s    (-1.80%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      261.89 ms →      256.52 ms   (-2.05%) |       4   →       4              |        1.05 s  →        1.03 s    (-2.05%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.28 ms →       62.32 ms   (-7.37%) |       4   →       4              |      269.10 ms →      249.27 ms   (-7.37%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.34 ms →       16.63 ms   (+1.77%) |       4   →       4              |       65.37 ms →       66.52 ms   (+1.77%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.34 ms →       16.63 ms   (+1.76%) |       4   →       4              |       65.36 ms →       66.51 ms   (+1.76%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       44.53 ms →       39.29 ms  (-11.77%) |       4   →       4              |      178.12 ms →      157.16 ms  (-11.77%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.13 ms →       16.39 ms   (+1.59%) |       4   →       4              |       64.54 ms →       65.57 ms   (+1.59%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.13 ms →       16.39 ms   (+1.59%) |       4   →       4              |       64.53 ms →       65.55 ms   (+1.59%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.26 ms →       52.75 ms   (-0.97%) |       4   →       4              |      213.05 ms →      210.98 ms   (-0.97%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.26 ms →       34.72 ms   (-1.55%) |       4   →       4              |      141.06 ms →      138.88 ms   (-1.55%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.94 ms   (+0.28%) |       4   →       4              |        7.75 ms →        7.77 ms   (+0.28%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       43.44 ms →       42.34 ms   (-2.53%) |       4   →       4              |      173.77 ms →      169.37 ms   (-2.53%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       10.31 ms →        9.19 ms  (-10.85%) |       4   →       4              |       41.23 ms →       36.76 ms  (-10.85%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.13 ms →       27.10 ms   (-0.12%) |       8   →       8              |      217.06 ms →      216.80 ms   (-0.12%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.67 ms →       16.37 ms   (+4.44%) |       8   →       8              |      125.37 ms →      130.94 ms   (+4.44%) | 
  │ │ │ ├ sddk::inner                                                   |       15.61 ms                             |       8                          |      124.89 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       53.41 μs                             |       8                          |      427.30 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        16.32 ms            |                   8              |                       130.59 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        40.88 ns            |                   8              |                       327.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        16.14 ms            |                   8              |                       129.15 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        25.00 ns            |                   8              |                       200.00 ns            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      133.74 ms →      133.65 ms   (-0.06%) |       4   →       4              |      534.95 ms →      534.62 ms   (-0.06%) | 
  │ │ ├ sddk::transform                                                 |       28.09 ms                             |       4                          |      112.37 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       26.45 μs                             |       4                          |      105.82 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.51 ms                             |       4                          |        6.05 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       23.66 μs                             |       4                          |       94.63 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        23.75 ms            |                   4              |                        94.99 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        23.56 ms            |                   4              |                        94.24 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      458.75 ns →      344.75 ns  (-24.85%) |       4   →       4              |        1.83 μs →        1.38 μs  (-24.85%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      281.36 s  →      240.16 s   (-14.64%) |       1   →       1              |      281.36 s  →      240.16 s   (-14.64%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.75 ms   (-0.75%) |      19   →      19              |      110.01 ms →      109.18 ms   (-0.75%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       13.35 s  →        9.22 s   (-30.91%) |      21   →      26    (+23.81%) |      280.39 s  →      239.84 s   (-14.46%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.57 ms →        4.58 ms   (+0.05%) |      21   →      26    (+23.81%) |       96.03 ms →      118.96 ms  (+23.87%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.20 ms →        4.22 ms   (+0.40%) |      21   →      26    (+23.81%) |       88.18 ms →      109.61 ms  (+24.31%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      998.32 μs →      957.41 μs   (-4.10%) |      21   →      26    (+23.81%) |       20.96 ms →       24.89 ms  (+18.74%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.31 ms →        2.37 ms   (+2.63%) |      21   →      26    (+23.81%) |       48.51 ms →       61.65 ms  (+27.07%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       64.16 μs →       64.74 μs   (+0.91%) |      42   →      52    (+23.81%) |        2.69 ms →        3.37 ms  (+24.93%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      102.48 μs →       94.48 μs   (-7.81%) |      21   →      26    (+23.81%) |        2.15 ms →        2.46 ms  (+14.14%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       70.22 μs →       66.19 μs   (-5.75%) |      21   →      26    (+23.81%) |        1.47 ms →        1.72 ms  (+16.69%) | 
+ │ │ ├ sirius::Band::solve                                             |       11.25 s  →        7.12 s   (-36.66%) |      21   →      26    (+23.81%) |      236.16 s  →      185.19 s   (-21.58%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      198.76 μs →      332.71 μs  (+67.39%) |      84   →     104    (+23.81%) |       16.70 ms →       34.60 ms (+107.24%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      192.94 μs →      326.77 μs  (+69.36%) |      84   →     104    (+23.81%) |       16.21 ms →       33.98 ms (+109.69%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.26 μs →        4.11 μs   (-3.47%) |      84   →     104    (+23.81%) |      357.57 μs →      427.36 μs  (+19.52%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.81 s  →        1.78 s   (-36.67%) |      84   →     104    (+23.81%) |      236.15 s  →      185.16 s   (-21.59%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.95 ms →       11.93 ms   (-0.14%) |      84   →     104    (+23.81%) |        1.00 s  →        1.24 s   (+23.63%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      608.09 ns →      674.24 ns  (+10.88%) |     504   →     624    (+23.81%) |      306.48 μs →      420.72 μs  (+37.28%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.85 ms →        1.83 ms   (-1.51%) |      84   →     104    (+23.81%) |      155.77 ms →      189.95 ms  (+21.94%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.72 μs →      353.87 μs   (+0.61%) |      84   →     104    (+23.81%) |       29.54 ms →       36.80 ms  (+24.57%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      554.67 μs →      547.55 μs   (-1.28%) |     168   →     208    (+23.81%) |       93.18 ms →      113.89 ms  (+22.22%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.79 s  →        1.76 s   (-36.97%) |      84   →     104    (+23.81%) |      234.23 s  →      182.78 s   (-21.96%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       86.98 ms →       69.34 ms  (-20.28%) |    1.00 K →     912     (-9.16%) |       87.33 s  →       63.24 s   (-27.59%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.83 ms →       43.74 ms  (-21.66%) |    1.00 K →     912     (-9.16%) |       56.06 s  →       39.89 s   (-28.84%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       10.02 ms →        8.29 ms  (-17.22%) |    1.00 K →     912     (-9.16%) |       10.06 s  →        7.56 s   (-24.81%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      211.53 μs →      230.54 μs   (+8.99%) |    1.00 K →     912     (-9.16%) |      212.37 ms →      210.26 ms   (-1.00%) | 
+ │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.51 ms →        2.00 ms  (-20.01%) |      84   →     104    (+23.81%) |      210.49 ms →      208.45 ms   (-0.97%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        8.14 ms →        6.49 ms  (-20.18%) |    1.00 K →     912     (-9.16%) |        8.17 s  →        5.92 s   (-27.50%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       82.02 μs →       89.20 μs   (+8.76%) |    1.00 K →     912     (-9.16%) |       82.35 ms →       81.35 ms   (-1.21%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      944.33 μs →      758.73 μs  (-19.65%) |      84   →     104    (+23.81%) |       79.32 ms →       78.91 ms   (-0.52%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       12.15 ms →        9.48 ms  (-21.98%) |    1.00 K →     912     (-9.16%) |       12.20 s  →        8.65 s   (-29.13%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        7.44 ms →        5.84 ms  (-21.48%) |    1.00 K →     912     (-9.16%) |        7.47 s  →        5.33 s   (-28.67%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.56 ms →        1.52 ms   (-2.35%) |    1.00 K →     912     (-9.16%) |        1.57 s  →        1.39 s   (-11.30%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       11.14 ms →        9.24 ms  (-17.08%) |    1.00 K →     912     (-9.16%) |       11.19 s  →        8.43 s   (-24.68%) | 
+ │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.15 ms →        1.93 ms  (-10.52%) |    1.00 K →     912     (-9.16%) |        2.16 s  →        1.76 s   (-18.72%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.21 ms →        7.41 ms  (-19.58%) |    2.01 K →    1.82 K   (-9.16%) |       18.49 s  →       13.51 s   (-26.95%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       22.57 ms →       28.83 ms  (+27.73%) |    1.00 K →     912     (-9.16%) |       22.66 s  →       26.29 s   (+16.03%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.72 ms                             |    1.92 K                        |        5.24 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       39.03 μs                             |    1.92 K                        |       75.09 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         2.20 ms            |                1.72 K            |                         3.79 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        72.24 ns            |                1.72 K            |                       124.26 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         2.19 ms            |                1.72 K            |                         3.76 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        69.82 ns            |                1.72 K            |                       120.09 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      946.10 μs →      870.79 μs   (-7.96%) |    1.00 K →     912     (-9.16%) |      949.88 ms →      794.16 ms  (-16.39%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      724.52 μs →      877.05 μs  (+21.05%) |    1.00 K →     912     (-9.16%) |      727.42 ms →      799.87 ms   (+9.96%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.59 ms                             |    3.93 K                        |       14.11 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.00 μs                             |    3.93 K                        |       58.97 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      262.53 μs                             |    3.93 K                        |        1.03 s                              | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.69 μs                             |    5.77 K                        |       55.96 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.49 ms            |                3.54 K            |                        19.45 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.73 ms            |                5.16 K            |                        19.25 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.86 ms →        5.72 ms   (-2.49%) |    1.00 K →     912     (-9.16%) |        5.89 s  →        5.21 s   (-11.43%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.58 ms                             |    1.00 K                        |        4.60 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       37.79 μs                             |    1.00 K                        |       37.94 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         4.02 ms            |                 912              |                         3.67 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        75.47 ns            |                 912              |                        68.83 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         4.00 ms            |                 912              |                         3.65 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        50.93 ns            |                 912              |                        46.45 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       94.78 ms →       73.74 ms  (-22.21%) |    1.00 K →     912     (-9.16%) |       95.16 s  →       67.25 s   (-29.33%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       19.96 ms →       11.16 ms  (-44.11%) |     958   →     891     (-6.99%) |       19.12 s  →        9.94 s   (-48.02%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       17.51 ms                             |     958                          |       16.78 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.34 μs                             |     958                          |       17.57 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      831.94 μs                             |     958                          |      797.00 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.73 μs                             |    1.92 K                        |       20.56 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        10.76 ms            |                 845              |                         9.09 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.33 ms            |                1.69 K            |                         9.00 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.39 ms →      652.88 μs  (-72.66%) |     958   →     845    (-11.80%) |        2.29 s  →      551.69 ms  (-75.88%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       12.90 ms →       51.79 ms (+301.32%) |     312   →     209    (-33.01%) |        4.03 s  →       10.82 s  (+168.84%) | 
  │ │ │ │     ├ sddk::transform                                         |       12.67 ms                             |     312                          |        3.95 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |        9.63 μs                             |     312                          |        3.01 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.03 ms                             |     312                          |      321.06 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       12.47 μs                             |     312                          |        3.89 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        34.36 ms            |                 314              |                        10.79 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        25.60 ms            |                 419              |                        10.73 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      454.37 ns →      607.64 ns  (+33.73%) |      84   →     104    (+23.81%) |       38.17 μs →       63.20 μs  (+65.57%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.21 μs →       22.32 μs  (+10.44%) |      21   →      26    (+23.81%) |      424.44 μs →      580.33 μs  (+36.73%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      643.74 μs →      593.90 μs   (-7.74%) |      21   →      26    (+23.81%) |       13.52 ms →       15.44 ms  (+14.23%) | 
- │ │ ├ sirius::Density::generate                                       |      907.98 ms →      897.61 ms   (-1.14%) |      21   →      26    (+23.81%) |       19.07 s  →       23.34 s   (+22.40%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      528.49 ms →      531.41 ms   (+0.55%) |      21   →      26    (+23.81%) |       11.10 s  →       13.82 s   (+24.49%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.70 ms →       23.34 ms   (-1.51%) |      84   →     104    (+23.81%) |        1.99 s  →        2.43 s   (+21.95%) | 
- │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        9.17 μs →        8.58 μs   (-6.40%) |      84   →     104    (+23.81%) |      769.89 μs →      892.18 μs  (+15.88%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.42 μs →       15.81 μs   (+2.50%) |       8   →       8              |      123.39 μs →      126.48 μs   (+2.50%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.61 ms →       19.17 ms   (-2.24%) |      84   →     104    (+23.81%) |        1.65 s  →        1.99 s   (+21.03%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       31.14 ms →       32.08 ms   (+3.02%) |      84   →     104    (+23.81%) |        2.62 s  →        3.34 s   (+27.55%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.96 μs →        9.42 μs   (-5.51%) |      84   →     104    (+23.81%) |      837.01 μs →      979.17 μs  (+16.98%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.46 ms   (+0.34%) |      84   →     104    (+23.81%) |      122.01 ms →      151.58 ms  (+24.24%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       29.19 ms →       30.14 ms   (+3.25%) |      84   →     104    (+23.81%) |        2.45 s  →        3.13 s   (+27.83%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.19 ms →        6.01 ms  (+15.78%) |      84   →     104    (+23.81%) |      436.29 ms →      625.40 ms  (+43.35%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      624.44 ns →      591.29 ns   (-5.31%) |      84   →     104    (+23.81%) |       52.45 μs →       61.49 μs  (+17.24%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.46 ms →       42.69 ms   (+0.53%) |      84   →     104    (+23.81%) |        3.57 s  →        4.44 s   (+24.46%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.63 ms   (-0.60%) |      21   →      26    (+23.81%) |       34.48 ms →       42.43 ms  (+23.07%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       89.08 ms →       88.86 ms   (-0.25%) |      21   →      26    (+23.81%) |        1.87 s  →        2.31 s   (+23.50%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.84 ms →       88.62 ms   (-0.24%) |      21   →      26    (+23.81%) |        1.87 s  →        2.30 s   (+23.51%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      287.01 ms →      274.25 ms   (-4.45%) |      21   →      26    (+23.81%) |        6.03 s  →        7.13 s   (+18.30%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      287.01 ms →      274.25 ms   (-4.45%) |      21   →      26    (+23.81%) |        6.03 s  →        7.13 s   (+18.30%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.17 ms →       24.44 ms  (-13.25%) |      21   →      26    (+23.81%) |      591.64 ms →      635.49 ms   (+7.41%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      231.25 ms →      223.84 ms   (-3.21%) |      21   →      26    (+23.81%) |        4.86 s  →        5.82 s   (+19.84%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.31 ms →       24.21 ms   (-8.01%) |      21   →      26    (+23.81%) |      552.59 ms →      629.36 ms  (+13.89%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.70 ms →       80.44 ms   (-1.54%) |      21   →      26    (+23.81%) |        1.72 s  →        2.09 s   (+21.90%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.19 ms →        7.94 ms  (+10.48%) |      21   →      26    (+23.81%) |      150.89 ms →      206.40 ms  (+36.79%) | 
- │ │ ├ sirius::Density::mix                                            |      206.40 ms →      219.99 ms   (+6.58%) |      21   →      26    (+23.81%) |        4.33 s  →        5.72 s   (+31.96%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      978.13 μs →      949.08 μs   (-2.97%) |      21   →      26    (+23.81%) |       20.54 ms →       24.68 ms  (+20.13%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.27 ms →       10.77 ms   (+4.91%) |     259   →     334    (+28.96%) |        2.66 s  →        3.60 s   (+35.29%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.00 ms →       10.39 ms   (+3.94%) |     259   →     334    (+28.96%) |        2.59 s  →        3.47 s   (+34.04%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.00 ms →       10.39 ms   (+3.94%) |     259   →     334    (+28.96%) |        2.59 s  →        3.47 s   (+34.04%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.21 ms →        6.61 ms   (+6.44%) |      21   →      26    (+23.81%) |      130.46 ms →      171.92 ms  (+31.78%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.38 ms →        5.77 ms   (+7.27%) |      21   →      26    (+23.81%) |      112.90 ms →      149.94 ms  (+32.81%) | 
- │ │ ├ sirius::Potential::generate                                     |      570.59 ms →      579.28 ms   (+1.52%) |      21   →      26    (+23.81%) |       11.98 s  →       15.06 s   (+25.70%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      137.57 ms →      137.23 ms   (-0.25%) |      21   →      26    (+23.81%) |        2.89 s  →        3.57 s   (+23.50%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.05 ms →       18.99 ms  (+18.32%) |      21   →      26    (+23.81%) |      337.01 ms →      493.71 ms  (+46.50%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.81 ms →       10.38 ms   (-4.00%) |      21   →      26    (+23.81%) |      227.01 ms →      269.83 ms  (+18.86%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.47 ms →        9.97 ms   (-4.74%) |      21   →      26    (+23.81%) |      219.83 ms →      259.26 ms  (+17.94%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.47 ms →        9.97 ms   (-4.74%) |      21   →      26    (+23.81%) |      219.81 ms →      259.25 ms  (+17.94%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      555.41 μs →      554.26 μs   (-0.21%) |      42   →      52    (+23.81%) |       23.33 ms →       28.82 ms  (+23.55%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       46.67 ms →       49.21 ms   (+5.43%) |      21   →      26    (+23.81%) |      980.17 ms →        1.28 s   (+30.53%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.67 ms →       46.88 ms   (+0.44%) |      21   →      26    (+23.81%) |      980.14 ms →        1.22 s   (+24.36%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.00 ms   (-1.68%) |      42   →      52    (+23.81%) |      128.35 ms →      156.24 ms  (+21.73%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.50 ms →        5.34 ms   (-3.05%) |      21   →      26    (+23.81%) |      115.57 ms →      138.71 ms  (+20.03%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.37 ms →        6.62 ms   (+3.97%) |      21   →      26    (+23.81%) |      133.73 ms →      172.14 ms  (+28.72%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       90.95 ms   (-0.01%) |      21   →      26    (+23.81%) |        1.91 s  →        2.36 s   (+23.80%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.58 ms →      292.88 ms   (+2.20%) |      21   →      26    (+23.81%) |        6.02 s  →        7.61 s   (+26.53%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      295.63 ms →      278.81 ms   (-5.69%) |      21   →      26    (+23.81%) |        6.21 s  →        7.25 s   (+16.77%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      295.63 ms →      278.81 ms   (-5.69%) |      21   →      26    (+23.81%) |        6.21 s  →        7.25 s   (+16.77%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       31.20 ms →       26.90 ms  (-13.77%) |      21   →      26    (+23.81%) |      655.12 ms →      699.42 ms   (+6.76%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      233.15 ms →      224.11 ms   (-3.88%) |      21   →      26    (+23.81%) |        4.90 s  →        5.83 s   (+19.01%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.43 ms →       24.02 ms  (-12.43%) |      21   →      26    (+23.81%) |      576.10 ms →      624.62 ms   (+8.42%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.49 ms →        5.34 ms   (-2.77%) |      21   →      26    (+23.81%) |      115.23 ms →      138.72 ms  (+20.39%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.63 ms →       10.29 ms   (-3.19%) |     147   →     182    (+23.81%) |        1.56 s  →        1.87 s   (+19.86%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |       10.42 ms →        9.93 ms   (-4.73%) |     147   →     182    (+23.81%) |        1.53 s  →        1.81 s   (+17.96%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.42 ms →        9.93 ms   (-4.73%) |     147   →     182    (+23.81%) |        1.53 s  →        1.81 s   (+17.95%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.10 ms →       11.06 ms   (+9.51%) |      63   →      78    (+23.81%) |      636.55 ms →      863.06 ms  (+35.58%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.86 ms →       10.72 ms   (+8.67%) |      63   →      78    (+23.81%) |      621.37 ms →      835.99 ms  (+34.54%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        9.87 ms →       10.00 ms   (+1.34%) |      21   →      26    (+23.81%) |      207.26 ms →      260.06 ms  (+25.47%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      128.16 μs →      124.72 μs   (-2.69%) |      21   →      26    (+23.81%) |        2.69 ms →        3.24 ms  (+20.48%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      123.13 μs →      119.66 μs   (-2.82%) |      21   →      26    (+23.81%) |        2.59 ms →        3.11 ms  (+20.32%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.09 ms →        5.05 ms   (-0.82%) |       2   →       2              |       10.19 ms →       10.10 ms   (-0.82%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.50 ms →       10.25 ms   (-2.38%) |       6   →       6              |       63.01 ms →       61.51 ms   (-2.38%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.49 ms →        9.74 ms   (-7.18%) |       6   →       6              |       62.94 ms →       58.42 ms   (-7.18%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.49 ms →        9.74 ms   (-7.18%) |       6   →       6              |       62.94 ms →       58.42 ms   (-7.18%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.97 ms →       10.88 ms   (+9.21%) |       3   →       3              |       29.90 ms →       32.65 ms   (+9.21%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.94 ms →       10.46 ms   (+5.16%) |       3   →       3              |       29.83 ms →       31.37 ms   (+5.16%) | 
  ├ sirius::Periodic_function|inner                                     |       10.50 ms →       10.05 ms   (-4.24%) |       2   →       2              |       20.99 ms →       20.10 ms   (-4.24%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.49 ms →        9.65 ms   (-8.04%) |       2   →       2              |       20.98 ms →       19.29 ms   (-8.04%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.49 ms →        9.65 ms   (-8.04%) |       2   →       2              |       20.98 ms →       19.29 ms   (-8.04%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.23 ms →       10.96 ms   (+7.12%) |       1   →       1              |       10.23 ms →       10.96 ms   (+7.12%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.22 ms →       10.50 ms   (+2.77%) |       1   →       1              |       10.22 ms →       10.50 ms   (+2.77%) | 
+ └ sirius::finalize                                                    |      377.22 ms →      283.91 ms  (-24.74%) |       1   →       1              |      377.22 ms →      283.91 ms  (-24.74%) | 
  ====================================================================================================================================================================================================
```
