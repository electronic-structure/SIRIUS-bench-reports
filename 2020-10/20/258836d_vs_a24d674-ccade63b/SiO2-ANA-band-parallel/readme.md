# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      278.94 s  →      220.87 s   (-20.82%) |       1   →       1              |      278.94 s  →      220.87 s   (-20.82%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.65 s    (+0.14%) |       1   →       1              |        2.65 s  →        2.65 s    (+0.14%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        2.86 s    (-3.62%) |       1   →       1              |        2.97 s  →        2.86 s    (-3.62%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      577.89 μs →      209.56 μs  (-63.74%) |       1   →       1              |      577.89 μs →      209.56 μs  (-63.74%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      156.91 ms →      127.44 ms  (-18.78%) |       1   →       1              |      156.91 ms →      127.44 ms  (-18.78%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       66.87 ms →       52.01 ms  (-22.23%) |       2   →       2              |      133.74 ms →      104.01 ms  (-22.23%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.09 ms →       23.34 ms   (+1.09%) |       1   →       1              |       23.09 ms →       23.34 ms   (+1.09%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.38 ms →        6.34 ms   (-0.52%) |       1   →       1              |        6.38 ms →        6.34 ms   (-0.52%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.67 ms →       16.95 ms   (+1.71%) |       1   →       1              |       16.67 ms →       16.95 ms   (+1.71%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.64 ms →       16.93 ms   (+1.73%) |       1   →       1              |       16.64 ms →       16.93 ms   (+1.73%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.14 ms   (-0.47%) |       1   →       1              |        4.16 ms →        4.14 ms   (-0.47%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (+0.00%) |       1   →       1              |        2.34 ms →        2.34 ms   (+0.00%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.11 μs →      101.94 μs   (-0.17%) |       1   →       1              |      102.11 μs →      101.94 μs   (-0.17%) | 
  │ └ sirius::Simulation_context::update                                |        2.77 s  →        2.69 s    (-3.01%) |       1   →       1              |        2.77 s  →        2.69 s    (-3.01%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.90 ms →       10.86 ms   (-0.36%) |       1   →       1              |       10.90 ms →       10.86 ms   (-0.36%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.42 ms →        4.44 ms   (+0.54%) |       1   →       1              |        4.42 ms →        4.44 ms   (+0.54%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.44 ms →        6.38 ms   (-0.92%) |       1   →       1              |        6.44 ms →        6.38 ms   (-0.92%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.42 ms →        6.36 ms   (-0.93%) |       1   →       1              |        6.42 ms →        6.36 ms   (-0.93%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.94 ms →        3.86 ms   (-1.93%) |       1   →       1              |        3.94 ms →        3.86 ms   (-1.93%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.74%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.74%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.54 μs →       98.33 μs   (-1.21%) |       1   →       1              |       99.54 μs →       98.33 μs   (-1.21%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.21 ms →       62.44 ms   (-2.75%) |       2   →       2              |      128.42 ms →      124.89 ms   (-2.75%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.14 ms   (-0.11%) |       2   →       2              |       10.29 ms →       10.28 ms   (-0.11%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.47 ms   (-0.05%) |       1   →       1              |        4.48 ms →        4.47 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.97 ms →       21.84 ms   (-4.93%) |       2   →       2              |       45.94 ms →       43.68 ms   (-4.93%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.31 ms →       14.81 ms   (-3.30%) |       2   →       2              |       30.63 ms →       29.62 ms   (-3.30%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.61 ms →       19.79 ms   (+0.94%) |       4   →       4              |       78.43 ms →       79.17 ms   (+0.94%) | 
  │   ├ sddk::Gvec::init                                                |      177.04 ms →      175.25 ms   (-1.01%) |       2   →       2              |      354.08 ms →      350.49 ms   (-1.01%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.40 ms →      132.09 ms   (+1.30%) |       2   →       2              |      260.80 ms →      264.19 ms   (+1.30%) | 
+ │   ├ sddk::Gvec_shells                                               |      195.40 ms →      175.39 ms  (-10.24%) |       1   →       1              |      195.40 ms →      175.39 ms  (-10.24%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.33 ms   (+0.11%) |       1   →       1              |        1.33 ms →        1.33 ms   (+0.11%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.12 ms →      290.51 ms   (-0.21%) |       2   →       2              |      582.24 ms →      581.01 ms   (-0.21%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       81.78 ms →       74.90 ms   (-8.42%) |       1   →       1              |       81.78 ms →       74.90 ms   (-8.42%) | 
  │ ├ sirius::K_point::K_point                                          |        2.47 μs →        2.48 μs   (+0.33%) |       4   →       4              |        9.88 μs →        9.91 μs   (+0.33%) | 
  │ └ sirius::K_point_set::initialize                                   |       81.70 ms →       74.79 ms   (-8.45%) |       1   →       1              |       81.70 ms →       74.79 ms   (-8.45%) | 
  │   └ sirius::K_point::initialize                                     |       20.41 ms →       18.68 ms   (-8.50%) |       4   →       4              |       81.65 ms →       74.71 ms   (-8.50%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.46 ms →       14.07 ms   (-8.96%) |       4   →       4              |       61.83 ms →       56.29 ms   (-8.96%) | 
  │     │ └ sddk::Gvec::init                                            |        4.00 ms →        3.84 ms   (-3.88%) |       4   →       4              |       15.98 ms →       15.36 ms   (-3.88%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.61 μs →       11.76 μs  (+36.55%) |       4   →       4              |       34.46 μs →       47.05 μs  (+36.55%) | 
  │     └ sirius::K_point::update                                       |        3.48 ms →        3.30 ms   (-5.01%) |       4   →       4              |       13.90 ms →       13.21 ms   (-5.01%) | 
  │       └ sirius::Beta_projectors                                     |        1.78 ms →        1.80 ms   (+0.75%) |       4   →       4              |        7.14 ms →        7.19 ms   (+0.75%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      938.60 μs →      931.82 μs   (-0.72%) |       4   →       4              |        3.75 ms →        3.73 ms   (-0.72%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.20 ms →        5.25 ms   (+0.86%) |       2   →       2              |       10.41 ms →       10.50 ms   (+0.86%) | 
  ├ sirius::Potential                                                   |      170.32 ms →      159.84 ms   (-6.15%) |       1   →       1              |      170.32 ms →      159.84 ms   (-6.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.79 ms   (+0.22%) |       6   →       6              |       34.67 ms →       34.75 ms   (+0.22%) | 
  │ └ sirius::Potential::update                                         |      134.94 ms →      124.37 ms   (-7.83%) |       1   →       1              |      134.94 ms →      124.37 ms   (-7.83%) | 
  │   └ sirius::Potential::generate_local_potential                     |      134.17 ms →      123.59 ms   (-7.88%) |       1   →       1              |      134.17 ms →      123.59 ms   (-7.88%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.72 ms →      111.79 ms   (-1.70%) |       1   →       1              |      113.72 ms →      111.79 ms   (-1.70%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       19.91 ms →       10.90 ms  (-45.24%) |       1   →       1              |       19.91 ms →       10.90 ms  (-45.24%) | 
  ├ sirius::Density                                                     |      140.06 ms →      136.80 ms   (-2.33%) |       1   →       1              |      140.06 ms →      136.80 ms   (-2.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.14 ms →        5.15 ms   (+0.10%) |       2   →       2              |       10.29 ms →       10.30 ms   (+0.10%) | 
  │ └ sirius::Density::update                                           |      129.51 ms →      126.24 ms   (-2.52%) |       1   →       1              |      129.51 ms →      126.24 ms   (-2.52%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.08 ms →      125.80 ms   (-2.54%) |       1   →       1              |      129.08 ms →      125.80 ms   (-2.54%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       104.64 μs            |                   1              |                       104.64 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.93 ms →      112.76 ms   (-0.16%) |       1   →       1              |      112.93 ms →      112.76 ms   (-0.16%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       15.70 ms →       12.49 ms  (-20.49%) |       1   →       1              |       15.70 ms →       12.49 ms  (-20.49%) | 
  ├ sirius::Density::initial_density                                    |      174.59 ms →      180.48 ms   (+3.37%) |       1   →       1              |      174.59 ms →      180.48 ms   (+3.37%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.75 ms →      110.91 ms   (-0.75%) |       1   →       1              |      111.75 ms →      110.91 ms   (-0.75%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.07 ms →       12.35 ms  (+22.70%) |       2   →       2              |       20.13 ms →       24.70 ms  (+22.70%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.78 ms →       12.38 ms  (+14.85%) |       1   →       1              |       10.78 ms →       12.38 ms  (+14.85%) | 
  ├ sirius::Potential::generate                                         |      584.32 ms →      593.68 ms   (+1.60%) |       1   →       1              |      584.32 ms →      593.68 ms   (+1.60%) | 
  │ ├ sirius::Potential::poisson                                        |      136.22 ms →      138.58 ms   (+1.73%) |       1   →       1              |      136.22 ms →      138.58 ms   (+1.73%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       15.17 ms →       17.92 ms  (+18.12%) |       1   →       1              |       15.17 ms →       17.92 ms  (+18.12%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.95 ms →       10.21 ms   (+2.56%) |       1   →       1              |        9.95 ms →       10.21 ms   (+2.56%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.93 ms →        9.81 ms   (-1.24%) |       1   →       1              |        9.93 ms →        9.81 ms   (-1.24%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.93 ms →        9.81 ms   (-1.24%) |       1   →       1              |        9.93 ms →        9.81 ms   (-1.24%) | 
  │ ├ sirius::Periodic_function::add                                    |      536.34 μs →      554.71 μs   (+3.42%) |       2   →       2              |        1.07 ms →        1.11 ms   (+3.42%) | 
  │ ├ sirius::Potential::xc                                             |       51.27 ms →       53.58 ms   (+4.51%) |       1   →       1              |       51.27 ms →       53.58 ms   (+4.51%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.26 ms →       51.20 ms   (-0.12%) |       1   →       1              |       51.26 ms →       51.20 ms   (-0.12%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.65 ms   (-0.79%) |       2   →       2              |       11.39 ms →       11.30 ms   (-0.79%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.22 ms →        5.22 ms   (-0.05%) |       1   →       1              |        5.22 ms →        5.22 ms   (-0.05%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.63 ms →        5.78 ms   (+2.53%) |       1   →       1              |        5.63 ms →        5.78 ms   (+2.53%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.67 ms →       93.55 ms   (+0.95%) |       1   →       1              |       92.67 ms →       93.55 ms   (+0.95%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      296.08 ms →      299.74 ms   (+1.23%) |       1   →       1              |      296.08 ms →      299.74 ms   (+1.23%) | 
  ├ sirius::Hamiltonian0                                                |        8.37 ms →        8.44 ms   (+0.83%) |       1   →       1              |        8.37 ms →        8.44 ms   (+0.83%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        8.09 ms   (+0.91%) |       1   →       1              |        8.02 ms →        8.09 ms   (+0.91%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms →        4.75 ms   (+0.14%) |       1   →       1              |        4.74 ms →        4.75 ms   (+0.14%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        2.42 ms   (+3.01%) |       1   →       1              |        2.35 ms →        2.42 ms   (+3.01%) | 
  │ ├ sirius::Non_local_operator                                        |       61.18 μs →       62.07 μs   (+1.46%) |       2   →       2              |      122.36 μs →      124.14 μs   (+1.46%) | 
  │ ├ sirius::D_operator::initialize                                    |      103.84 μs →      103.19 μs   (-0.63%) |       1   →       1              |      103.84 μs →      103.19 μs   (-0.63%) | 
  │ └ sirius::Q_operator::initialize                                    |       72.67 μs →       69.47 μs   (-4.40%) |       1   →       1              |       72.67 μs →       69.47 μs   (-4.40%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.12 s  →        3.09 s    (-0.96%) |       1   →       1              |        3.12 s  →        3.09 s    (-0.96%) | 
- │ ├ sirius::Hamiltonian_k                                             |      208.11 μs →      395.94 μs  (+90.25%) |       4   →       4              |      832.45 μs →        1.58 ms  (+90.25%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      202.09 μs →      390.55 μs  (+93.26%) |       4   →       4              |      808.36 μs →        1.56 ms  (+93.26%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        4.37 μs →        3.41 μs  (-21.81%) |       4   →       4              |       17.46 μs →       13.65 μs  (-21.81%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      779.46 ms →      771.75 ms   (-0.99%) |       4   →       4              |        3.12 s  →        3.09 s    (-0.99%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       31.99 ms →       31.95 ms   (-0.15%) |      16   →      16              |      511.88 ms →      511.13 ms   (-0.15%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.55 ms →       14.71 ms   (+1.09%) |       4   →       4              |       58.21 ms →       58.84 ms   (+1.09%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.27 ms →        5.29 ms   (+0.38%) |       4   →       4              |       21.08 ms →       21.16 ms   (+0.38%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      357.08 ms →      351.16 ms   (-1.66%) |       4   →       4              |        1.43 s  →        1.40 s    (-1.66%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      259.50 ms →      254.59 ms   (-1.89%) |       4   →       4              |        1.04 s  →        1.02 s    (-1.89%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       65.73 ms →       61.58 ms   (-6.31%) |       4   →       4              |      262.91 ms →      246.33 ms   (-6.31%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.07 ms →       16.16 ms   (+0.59%) |       4   →       4              |       64.27 ms →       64.65 ms   (+0.59%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.06 ms →       16.16 ms   (+0.59%) |       4   →       4              |       64.26 ms →       64.64 ms   (+0.59%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       43.12 ms →       38.93 ms   (-9.72%) |       4   →       4              |      172.49 ms →      155.73 ms   (-9.72%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.08 ms →       15.91 ms   (-1.09%) |       4   →       4              |       64.32 ms →       63.62 ms   (-1.09%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.08 ms →       15.90 ms   (-1.10%) |       4   →       4              |       64.31 ms →       63.61 ms   (-1.10%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.50 ms →       52.23 ms   (-0.52%) |       4   →       4              |      210.01 ms →      208.91 ms   (-0.52%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.49 ms →       34.17 ms   (-0.94%) |       4   →       4              |      137.97 ms →      136.68 ms   (-0.94%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.89 ms   (-2.33%) |       4   →       4              |        7.76 ms →        7.58 ms   (-2.33%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.62 ms →       40.52 ms   (-0.25%) |       4   →       4              |      162.49 ms →      162.08 ms   (-0.25%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.52 ms →        7.40 ms   (-1.52%) |       4   →       4              |       30.07 ms →       29.61 ms   (-1.52%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.49 ms →       27.06 ms   (-1.55%) |       8   →       8              |      219.90 ms →      216.48 ms   (-1.55%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.39 ms →       15.10 ms   (+4.91%) |       8   →       8              |      115.14 ms →      120.80 ms   (+4.91%) | 
  │ │ │ ├ sddk::inner                                                   |       14.33 ms                             |       8                          |      114.61 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       51.54 μs                             |       8                          |      412.30 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.06 ms            |                   8              |                       120.45 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        22.75 ns            |                   8              |                       182.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.88 ms            |                   8              |                       119.02 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        25.50 ns            |                   8              |                       204.00 ns            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      124.18 ms →      120.85 ms   (-2.68%) |       4   →       4              |      496.70 ms →      483.38 ms   (-2.68%) | 
  │ │ ├ sddk::transform                                                 |       27.69 ms                             |       4                          |      110.76 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       31.45 μs                             |       4                          |      125.78 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.38 ms                             |       4                          |        5.52 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       28.19 μs                             |       4                          |      112.75 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        23.59 ms            |                   4              |                        94.38 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        23.37 ms            |                   4              |                        93.47 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      473.75 ns →      334.50 ns  (-29.39%) |       4   →       4              |        1.90 μs →        1.34 μs  (-29.39%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      268.04 s  →      210.21 s   (-21.58%) |       1   →       1              |      268.04 s  →      210.21 s   (-21.58%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.73 ms   (+0.26%) |      19   →      19              |      108.67 ms →      108.95 ms   (+0.26%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        9.56 s  →        7.77 s   (-18.68%) |      28   →      27     (-3.57%) |      267.64 s  →      209.86 s   (-21.59%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.50 ms →        4.54 ms   (+0.76%) |      28   →      27     (-3.57%) |      126.07 ms →      122.49 ms   (-2.84%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.14 ms →        4.17 ms   (+0.67%) |      28   →      27     (-3.57%) |      116.02 ms →      112.63 ms   (-2.92%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      982.12 μs →      963.38 μs   (-1.91%) |      28   →      27     (-3.57%) |       27.50 ms →       26.01 ms   (-5.41%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.27 ms →        2.32 ms   (+2.17%) |      28   →      27     (-3.57%) |       63.66 ms →       62.72 ms   (-1.48%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.21 μs →       64.18 μs   (-0.05%) |      56   →      54     (-3.57%) |        3.60 ms →        3.47 ms   (-3.62%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       91.18 μs →      100.87 μs  (+10.63%) |      28   →      27     (-3.57%) |        2.55 ms →        2.72 ms   (+6.68%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       69.39 μs →       66.94 μs   (-3.54%) |      28   →      27     (-3.57%) |        1.94 ms →        1.81 ms   (-6.99%) | 
+ │ │ ├ sirius::Band::solve                                             |        7.47 s  →        5.68 s   (-23.96%) |      28   →      27     (-3.57%) |      209.06 s  →      153.30 s   (-26.67%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      198.91 μs →      361.66 μs  (+81.82%) |     112   →     108     (-3.57%) |       22.28 ms →       39.06 ms  (+75.32%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      193.03 μs →      356.09 μs  (+84.47%) |     112   →     108     (-3.57%) |       21.62 ms →       38.46 ms  (+77.88%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.44 μs →        3.91 μs  (-11.93%) |     112   →     108     (-3.57%) |      497.42 μs →      422.42 μs  (-15.08%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.87 s  →        1.42 s   (-23.97%) |     112   →     108     (-3.57%) |      209.04 s  →      153.26 s   (-26.68%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       16.50 ms →       11.94 ms  (-27.61%) |     112   →     108     (-3.57%) |        1.85 s  →        1.29 s   (-30.20%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      741.62 μs →      661.90 ns  (-99.91%) |     672   →     648     (-3.57%) |      498.37 ms →      428.91 μs  (-99.91%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.85 ms →        2.06 ms  (+11.57%) |     112   →     108     (-3.57%) |      206.84 ms →      222.54 ms   (+7.59%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.53 μs →      353.48 μs   (+0.55%) |     112   →     108     (-3.57%) |       39.37 ms →       38.18 ms   (-3.04%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      549.95 μs →      660.63 μs  (+20.13%) |     224   →     216     (-3.57%) |      123.19 ms →      142.70 ms  (+15.83%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s  →        1.40 s   (-24.09%) |     112   →     108     (-3.57%) |      205.97 s  →      150.77 s   (-26.80%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.67 ms →       69.15 ms   (-0.75%) |     830   →     945    (+13.86%) |       57.83 s  →       65.34 s   (+13.00%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.23 ms →       44.12 ms   (-0.26%) |     830   →     945    (+13.86%) |       36.71 s  →       41.69 s   (+13.55%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.06 ms →        8.51 ms   (+5.48%) |     830   →     945    (+13.86%) |        6.69 s  →        8.04 s   (+20.10%) | 
- │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       64.87 μs →      220.79 μs (+240.37%) |     830   →     945    (+13.86%) |       53.84 ms →      208.65 ms (+287.54%) | 
- │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      467.43 μs →        1.92 ms (+309.77%) |     112   →     108     (-3.57%) |       52.35 ms →      206.86 ms (+295.14%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.67 ms →        6.49 ms   (-2.63%) |     830   →     945    (+13.86%) |        5.53 s  →        6.13 s   (+10.86%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       65.48 μs →       85.44 μs  (+30.48%) |     830   →     945    (+13.86%) |       54.35 ms →       80.74 ms  (+48.55%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      468.73 μs →      725.38 μs  (+54.75%) |     112   →     108     (-3.57%) |       52.50 ms →       78.34 ms  (+49.23%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.67 ms →        9.52 ms   (-1.52%) |     830   →     945    (+13.86%) |        8.02 s  →        9.00 s   (+12.13%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.95 ms →        5.88 ms   (-1.06%) |     830   →     945    (+13.86%) |        4.94 s  →        5.56 s   (+12.64%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.48 ms   (-3.61%) |     830   →     945    (+13.86%) |        1.27 s  →        1.40 s    (+9.74%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.84 ms →        8.67 ms   (-1.93%) |     830   →     945    (+13.86%) |        7.34 s  →        8.20 s   (+11.65%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.35 ms →        1.34 ms   (-0.65%) |     830   →     945    (+13.86%) |        1.12 s  →        1.26 s   (+13.12%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.52 ms →        7.43 ms   (-1.20%) |    1.66 K →    1.89 K  (+13.86%) |       12.48 s  →       14.04 s   (+12.49%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       19.82 ms →       27.20 ms  (+37.28%) |     830   →     945    (+13.86%) |       16.45 s  →       25.71 s   (+56.30%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.30 ms                             |    1.55 K                        |        3.56 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.36 μs                             |    1.70 K                        |       55.15 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         2.01 ms            |                1.78 K            |                         3.58 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        53.84 ns            |                1.78 K            |                        95.95 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         2.00 ms            |                1.78 K            |                         3.56 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        62.30 ns            |                1.78 K            |                       111.03 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      830.76 μs →      819.94 μs   (-1.30%) |     830   →     945    (+13.86%) |      689.53 ms →      774.84 ms  (+12.37%) | 
! │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      767.61 μs →      735.52 μs   (-4.18%) |     830   →     945    (+13.86%) |      637.12 ms →      695.07 ms   (+9.10%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.10 ms                             |    3.21 K                        |        9.96 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.29 μs                             |    3.21 K                        |       45.84 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      165.34 μs                             |    3.21 K                        |      530.42 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.10 μs                             |    4.64 K                        |       46.89 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.22 ms            |                3.67 K            |                        19.16 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.55 ms            |                5.35 K            |                        18.97 s             | 
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.84 ms →        5.39 ms   (-7.62%) |     830   →     945    (+13.86%) |        4.84 s  →        5.10 s    (+5.19%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.20 ms                             |     830                          |        3.48 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.59 μs                             |    1.02 K                        |       27.15 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.60 ms            |                 945              |                         3.40 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        45.42 ns            |                 945              |                        42.92 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.58 ms            |                 945              |                         3.39 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        47.70 ns            |                 945              |                        45.08 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      142.04 ms →       34.21 ms  (-75.92%) |     830   →     945    (+13.86%) |      117.89 s  →       32.33 s   (-72.58%) | 
- │ │ │ │   ├ sirius::residuals                                         |        7.84 ms →       10.19 ms  (+30.09%) |     818   →     919    (+12.35%) |        6.41 s  →        9.37 s   (+46.15%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.30 ms                             |     756                          |        5.52 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.78 μs                             |     756                          |       15.71 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      254.33 μs                             |     756                          |      192.27 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       13.34 μs                             |    1.51 K                        |       20.17 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         9.80 ms            |                 874              |                         8.56 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         4.87 ms            |                1.75 K            |                         8.50 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      886.87 μs →      651.56 μs  (-26.53%) |     756   →     874    (+15.61%) |      670.47 ms →      569.47 ms  (-15.07%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       20.94 ms →       36.23 ms  (+73.01%) |     120   →     356   (+196.67%) |        2.51 s  →       12.90 s  (+413.27%) | 
  │ │ │ │     ├ sddk::transform                                         |       19.56 ms                             |     128                          |        2.50 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       20.15 μs                             |     128                          |        2.58 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.16 ms                             |     128                          |      148.67 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       19.58 μs                             |     136                          |        2.66 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        21.23 ms            |                 604              |                        12.82 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        14.95 ms            |                 852              |                        12.73 s             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      479.21 ns →      482.05 ns   (+0.59%) |     112   →     108     (-3.57%) |       53.67 μs →       52.06 μs   (-3.00%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.43 μs →       21.66 μs  (+11.48%) |      28   →      27     (-3.57%) |      544.03 μs →      584.83 μs   (+7.50%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      613.28 μs →      598.29 μs   (-2.44%) |      28   →      27     (-3.57%) |       17.17 ms →       16.15 ms   (-5.93%) | 
  │ │ ├ sirius::Density::generate                                       |      895.57 ms →      888.01 ms   (-0.84%) |      28   →      27     (-3.57%) |       25.08 s  →       23.98 s    (-4.39%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      521.21 ms →      520.75 ms   (-0.09%) |      28   →      27     (-3.57%) |       14.59 s  →       14.06 s    (-3.65%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.83 ms →       23.66 ms   (-0.68%) |     112   →     108     (-3.57%) |        2.67 s  →        2.56 s    (-4.23%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.37 μs →        8.81 μs   (+5.23%) |     112   →     108     (-3.57%) |      937.66 μs →      951.43 μs   (+1.47%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.97 μs →       16.40 μs   (+9.59%) |       8   →       8              |      119.72 μs →      131.20 μs   (+9.59%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.77 ms →       19.50 ms   (-1.39%) |     112   →     108     (-3.57%) |        2.21 s  →        2.11 s    (-4.91%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.75 ms →       29.80 ms   (+0.17%) |     112   →     108     (-3.57%) |        3.33 s  →        3.22 s    (-3.41%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.81 μs →        9.47 μs   (-3.47%) |     112   →     108     (-3.57%) |        1.10 ms →        1.02 ms   (-6.92%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.41 ms   (-2.80%) |     112   →     108     (-3.57%) |      162.79 ms →      152.58 ms   (-6.28%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.81 ms →       27.90 ms   (+0.33%) |     112   →     108     (-3.57%) |        3.11 s  →        3.01 s    (-3.26%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.78 ms →        3.76 ms   (-0.45%) |     112   →     108     (-3.57%) |      422.95 ms →      406.01 ms   (-4.00%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      512.39 ns →      527.72 ns   (+2.99%) |     112   →     108     (-3.57%) |       57.39 μs →       56.99 μs   (-0.69%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.43 ms →       42.39 ms   (-0.08%) |     112   →     108     (-3.57%) |        4.75 s  →        4.58 s    (-3.65%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.50%) |      28   →      27     (-3.57%) |       46.06 ms →       44.19 ms   (-4.06%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.29 ms →       88.87 ms   (+0.66%) |      28   →      27     (-3.57%) |        2.47 s  →        2.40 s    (-2.93%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.06 ms →       88.64 ms   (+0.66%) |      28   →      27     (-3.57%) |        2.47 s  →        2.39 s    (-2.94%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      283.28 ms →      276.44 ms   (-2.41%) |      28   →      27     (-3.57%) |        7.93 s  →        7.46 s    (-5.90%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      283.28 ms →      276.44 ms   (-2.41%) |      28   →      27     (-3.57%) |        7.93 s  →        7.46 s    (-5.90%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.14 ms →       24.60 ms  (-12.59%) |      28   →      27     (-3.57%) |      788.05 ms →      664.23 ms  (-15.71%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.71 ms →      226.38 ms   (+0.30%) |      28   →      27     (-3.57%) |        6.32 s  →        6.11 s    (-3.29%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.60 ms →       23.66 ms  (-14.27%) |      28   →      27     (-3.57%) |      772.94 ms →      638.94 ms  (-17.34%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.30 ms →       80.10 ms   (-2.67%) |      28   →      27     (-3.57%) |        2.30 s  →        2.16 s    (-6.14%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.19 ms →        7.12 ms  (+36.98%) |      28   →      27     (-3.57%) |      145.46 ms →      192.13 ms  (+32.09%) | 
  │ │ ├ sirius::Density::mix                                            |      216.00 ms →      221.36 ms   (+2.48%) |      28   →      27     (-3.57%) |        6.05 s  →        5.98 s    (-1.18%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      951.35 μs →      960.26 μs   (+0.94%) |      28   →      27     (-3.57%) |       26.64 ms →       25.93 ms   (-2.67%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.23 ms →       10.80 ms   (+5.53%) |     364   →     349     (-4.12%) |        3.73 s  →        3.77 s    (+1.18%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.97 ms →       10.43 ms   (+4.61%) |     364   →     349     (-4.12%) |        3.63 s  →        3.64 s    (+0.30%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.97 ms →       10.43 ms   (+4.61%) |     364   →     349     (-4.12%) |        3.63 s  →        3.64 s    (+0.30%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        5.99 ms →        6.05 ms   (+1.00%) |      28   →      27     (-3.57%) |      167.77 ms →      163.39 ms   (-2.61%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.19 ms →        5.22 ms   (+0.70%) |      28   →      27     (-3.57%) |      145.23 ms →      141.02 ms   (-2.90%) | 
  │ │ ├ sirius::Potential::generate                                     |      570.13 ms →      582.24 ms   (+2.12%) |      28   →      27     (-3.57%) |       15.96 s  →       15.72 s    (-1.52%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.44 ms →      138.60 ms   (+1.59%) |      28   →      27     (-3.57%) |        3.82 s  →        3.74 s    (-2.04%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.02 ms →       17.71 ms  (+17.88%) |      28   →      27     (-3.57%) |      420.68 ms →      478.19 ms  (+13.67%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.25 ms →       10.41 ms   (+1.54%) |      28   →      27     (-3.57%) |      287.04 ms →      281.05 ms   (-2.09%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.94 ms →        9.96 ms   (+0.14%) |      28   →      27     (-3.57%) |      278.36 ms →      268.81 ms   (-3.43%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.94 ms →        9.96 ms   (+0.14%) |      28   →      27     (-3.57%) |      278.35 ms →      268.79 ms   (-3.43%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      551.83 μs →      552.30 μs   (+0.09%) |      56   →      54     (-3.57%) |       30.90 ms →       29.82 ms   (-3.49%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       46.82 ms →       49.75 ms   (+6.26%) |      28   →      27     (-3.57%) |        1.31 s  →        1.34 s    (+2.47%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.82 ms →       47.41 ms   (+1.26%) |      28   →      27     (-3.57%) |        1.31 s  →        1.28 s    (-2.36%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.02 ms   (-0.38%) |      56   →      54     (-3.57%) |      170.02 ms →      163.33 ms   (-3.94%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.23 ms →        5.36 ms   (+2.44%) |      28   →      27     (-3.57%) |      146.42 ms →      144.63 ms   (-1.22%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.65 ms →        6.71 ms   (+1.02%) |      28   →      27     (-3.57%) |      186.09 ms →      181.28 ms   (-2.58%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       91.00 ms   (+0.10%) |      28   →      27     (-3.57%) |        2.55 s  →        2.46 s    (-3.47%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.89 ms →      293.76 ms   (+2.40%) |      28   →      27     (-3.57%) |        8.03 s  →        7.93 s    (-1.26%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      285.08 ms →      279.14 ms   (-2.08%) |      28   →      27     (-3.57%) |        7.98 s  →        7.54 s    (-5.58%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      285.08 ms →      279.14 ms   (-2.08%) |      28   →      27     (-3.57%) |        7.98 s  →        7.54 s    (-5.58%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       30.70 ms →       27.06 ms  (-11.84%) |      28   →      27     (-3.57%) |      859.49 ms →      730.64 ms  (-14.99%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.08 ms →      224.44 ms   (+0.61%) |      28   →      27     (-3.57%) |        6.25 s  →        6.06 s    (-2.98%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.55 ms →       23.83 ms  (-13.49%) |      28   →      27     (-3.57%) |      771.36 ms →      643.48 ms  (-16.58%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.08 ms →        5.31 ms  (-12.69%) |      28   →      27     (-3.57%) |      170.16 ms →      143.26 ms  (-15.81%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.22 ms →       10.25 ms   (+0.36%) |     196   →     189     (-3.57%) |        2.00 s  →        1.94 s    (-3.23%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.86 ms   (+0.36%) |     196   →     189     (-3.57%) |        1.93 s  →        1.86 s    (-3.22%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →        9.86 ms   (+0.36%) |     196   →     189     (-3.57%) |        1.93 s  →        1.86 s    (-3.22%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.55 ms →       10.58 ms   (+0.34%) |      84   →      81     (-3.57%) |      886.02 ms →      857.25 ms   (-3.25%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.17 ms →       10.21 ms   (+0.36%) |      84   →      81     (-3.57%) |      854.20 ms →      826.67 ms   (-3.22%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.77 ms →        9.98 ms   (-7.39%) |      28   →      27     (-3.57%) |      301.67 ms →      269.40 ms  (-10.70%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      114.82 μs →      113.03 μs   (-1.56%) |      28   →      27     (-3.57%) |        3.21 ms →        3.05 ms   (-5.07%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      109.05 μs →      107.77 μs   (-1.18%) |      28   →      27     (-3.57%) |        3.05 ms →        2.91 ms   (-4.71%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.20 ms →        5.27 ms   (+1.37%) |       2   →       2              |       10.40 ms →       10.54 ms   (+1.37%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.92 ms →       10.10 ms   (-7.57%) |       6   →       6              |       65.53 ms →       60.57 ms   (-7.57%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.69 ms →       10.07 ms   (+3.91%) |       6   →       6              |       58.14 ms →       60.41 ms   (+3.91%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.69 ms →       10.07 ms   (+3.91%) |       6   →       6              |       58.14 ms →       60.41 ms   (+3.91%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.43 ms →       10.39 ms   (-0.35%) |       3   →       3              |       31.29 ms →       31.18 ms   (-0.35%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.03 ms →       10.27 ms   (+2.34%) |       3   →       3              |       30.10 ms →       30.80 ms   (+2.34%) | 
  ├ sirius::Periodic_function|inner                                     |       10.22 ms →       10.32 ms   (+0.95%) |       2   →       2              |       20.44 ms →       20.64 ms   (+0.95%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.21 ms →        9.68 ms   (-5.20%) |       2   →       2              |       20.42 ms →       19.36 ms   (-5.20%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.21 ms →        9.68 ms   (-5.16%) |       2   →       2              |       20.41 ms →       19.36 ms   (-5.16%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.88 ms →       10.47 ms   (-3.79%) |       1   →       1              |       10.88 ms →       10.47 ms   (-3.79%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.87 ms →       10.19 ms   (-6.22%) |       1   →       1              |       10.87 ms →       10.19 ms   (-6.22%) | 
+ └ sirius::finalize                                                    |      395.51 ms →      310.56 ms  (-21.48%) |       1   →       1              |      395.51 ms →      310.56 ms  (-21.48%) | 
  ====================================================================================================================================================================================================
```
