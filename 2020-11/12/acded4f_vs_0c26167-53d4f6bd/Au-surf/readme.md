# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs acded4f8dc8bf829fcf788e7dbd08a23ea769390
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      118.55 s  →      126.44 s    (+6.66%) |       1   →       1              |      118.55 s  →      126.44 s    (+6.66%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.69 s    (+0.13%) |       1   →       1              |        2.69 s  →        2.69 s    (+0.13%) | 
  ├ sirius::Simulation_context::initialize                              |        2.13 s  →        2.12 s    (-0.58%) |       1   →       1              |        2.13 s  →        2.12 s    (-0.58%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       90.80 ms →       60.93 ms  (-32.90%) |       1   →       1              |       90.80 ms →       60.93 ms  (-32.90%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |       94.01 ms →       70.67 ms  (-24.83%) |       1   →       1              |       94.01 ms →       70.67 ms  (-24.83%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       67.93 ms →       45.87 ms  (-32.48%) |       1   →       1              |       67.93 ms →       45.87 ms  (-32.48%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.02 ms →       24.74 ms   (-4.89%) |       1   →       1              |       26.02 ms →       24.74 ms   (-4.89%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.08 ms →       10.47 ms   (+3.87%) |       1   →       1              |       10.08 ms →       10.47 ms   (+3.87%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       15.91 ms →       14.25 ms  (-10.42%) |       1   →       1              |       15.91 ms →       14.25 ms  (-10.42%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.18 ms →       13.96 ms   (-8.05%) |       1   →       1              |       15.18 ms →       13.96 ms   (-8.05%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.95 ms →       13.74 ms   (-8.13%) |       1   →       1              |       14.95 ms →       13.74 ms   (-8.13%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      208.15 μs →      205.09 μs   (-1.47%) |       1   →       1              |      208.15 μs →      205.09 μs   (-1.47%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.55 μs →        2.63 μs   (+3.26%) |       1   →       1              |        2.55 μs →        2.63 μs   (+3.26%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.93 s    (+2.17%) |       1   →       1              |        1.89 s  →        1.93 s    (+2.17%) | 
  │   ├ sirius::Unit_cell::update                                       |       13.02 ms →       12.78 ms   (-1.87%) |       1   →       1              |       13.02 ms →       12.78 ms   (-1.87%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.25 ms →        8.32 ms   (+0.77%) |       1   →       1              |        8.25 ms →        8.32 ms   (+0.77%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.75 ms →        4.44 ms   (-6.43%) |       1   →       1              |        4.75 ms →        4.44 ms   (-6.43%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.12 ms →        4.15 ms   (+0.57%) |       1   →       1              |        4.12 ms →        4.15 ms   (+0.57%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.93 ms →        3.93 ms   (+0.11%) |       1   →       1              |        3.93 ms →        3.93 ms   (+0.11%) | 
- │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      193.20 μs →      213.29 μs  (+10.40%) |       1   →       1              |      193.20 μs →      213.29 μs  (+10.40%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.26 μs →        1.06 μs  (-15.50%) |       1   →       1              |        1.26 μs →        1.06 μs  (-15.50%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       16.13 ms →       16.53 ms   (+2.50%) |       2   →       2              |       32.26 ms →       33.07 ms   (+2.50%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (+0.09%) |       2   →       2              |        2.20 ms →        2.20 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      957.86 μs →      962.09 μs   (+0.44%) |       1   →       1              |      957.86 μs →      962.09 μs   (+0.44%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.08 ms →        5.06 ms   (-0.45%) |       2   →       2              |       10.16 ms →       10.11 ms   (-0.45%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.65 ms   (-0.23%) |       2   →       2              |        7.31 ms →        7.29 ms   (-0.23%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.50 ms →       15.59 ms   (+0.60%) |       4   →       4              |       61.99 ms →       62.36 ms   (+0.60%) | 
  │   ├ sddk::Gvec::init                                                |      159.89 ms →      169.28 ms   (+5.87%) |       2   →       2              |      319.77 ms →      338.56 ms   (+5.87%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.17 ms →      136.07 ms   (+7.00%) |       2   →       2              |      254.34 ms →      272.14 ms   (+7.00%) | 
- │   ├ sddk::Gvec_shells                                               |      116.13 ms →      127.97 ms  (+10.19%) |       1   →       1              |      116.13 ms →      127.97 ms  (+10.19%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.02 ms →        1.04 ms   (+1.87%) |       1   →       1              |        1.02 ms →        1.04 ms   (+1.87%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      218.57 ms →      217.38 ms   (-0.55%) |       1   →       1              |      218.57 ms →      217.38 ms   (-0.55%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.19 ms →       25.69 ms   (-1.90%) |       1   →       1              |       26.19 ms →       25.69 ms   (-1.90%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.23 μs →        1.93 μs  (-13.53%) |       2   →       2              |        4.46 μs →        3.86 μs  (-13.53%) | 
  │ └ sirius::K_point_set::initialize                                   |       26.15 ms →       25.65 ms   (-1.90%) |       1   →       1              |       26.15 ms →       25.65 ms   (-1.90%) | 
  │   └ sirius::K_point::initialize                                     |       26.09 ms →       25.61 ms   (-1.86%) |       1   →       1              |       26.09 ms →       25.61 ms   (-1.86%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.63 ms →       19.20 ms   (-2.16%) |       1   →       1              |       19.63 ms →       19.20 ms   (-2.16%) | 
  │     │ └ sddk::Gvec::init                                            |        5.16 ms →        4.92 ms   (-4.71%) |       1   →       1              |        5.16 ms →        4.92 ms   (-4.71%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.61 μs →       10.70 μs   (+0.88%) |       1   →       1              |       10.61 μs →       10.70 μs   (+0.88%) | 
  │     └ sirius::K_point::update                                       |        4.12 ms →        4.13 ms   (+0.26%) |       1   →       1              |        4.12 ms →        4.13 ms   (+0.26%) | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms →        1.72 ms   (+0.30%) |       1   →       1              |        1.72 ms →        1.72 ms   (+0.30%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      911.61 μs →      905.30 μs   (-0.69%) |       1   →       1              |      911.61 μs →      905.30 μs   (-0.69%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.55 ms →        1.47 ms   (-5.29%) |       2   →       2              |        3.10 ms →        2.93 ms   (-5.29%) | 
  ├ sirius::Potential                                                   |       93.38 ms →       94.91 ms   (+1.64%) |       1   →       1              |       93.38 ms →       94.91 ms   (+1.64%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.69 ms →        2.45 ms   (-8.89%) |       6   →       6              |       16.11 ms →       14.68 ms   (-8.89%) | 
  │ └ sirius::Potential::update                                         |       76.89 ms →       79.89 ms   (+3.90%) |       1   →       1              |       76.89 ms →       79.89 ms   (+3.90%) | 
  │   └ sirius::Potential::generate_local_potential                     |       76.71 ms →       79.72 ms   (+3.93%) |       1   →       1              |       76.71 ms →       79.72 ms   (+3.93%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       58.21 ms →       50.87 ms  (-12.60%) |       1   →       1              |       58.21 ms →       50.87 ms  (-12.60%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        8.76 ms →       19.97 ms (+127.97%) |       1   →       1              |        8.76 ms →       19.97 ms (+127.97%) | 
  ├ sirius::Density                                                     |       75.11 ms →       75.41 ms   (+0.40%) |       1   →       1              |       75.11 ms →       75.41 ms   (+0.40%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.84 ms →        4.80 ms   (-0.89%) |       2   →       2              |        9.68 ms →        9.59 ms   (-0.89%) | 
  │ └ sirius::Density::update                                           |       65.32 ms →       65.70 ms   (+0.59%) |       1   →       1              |       65.32 ms →       65.70 ms   (+0.59%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.14 ms →       65.53 ms   (+0.60%) |       1   →       1              |       65.14 ms →       65.53 ms   (+0.60%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.19 ms →        3.07 ms   (-3.70%) |       1   →       1              |        3.19 ms →        3.07 ms   (-3.70%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       58.31 ms →       51.91 ms  (-10.98%) |       1   →       1              |       58.31 ms →       51.91 ms  (-10.98%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.38 ms →        9.30 ms (+290.31%) |       1   →       1              |        2.38 ms →        9.30 ms (+290.31%) | 
  ├ sirius::Density::initial_density                                    |       78.45 ms →       79.21 ms   (+0.97%) |       1   →       1              |       78.45 ms →       79.21 ms   (+0.97%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       58.13 ms →       51.73 ms  (-11.01%) |       1   →       1              |       58.13 ms →       51.73 ms  (-11.01%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.35 ms →        5.84 ms (+148.63%) |       2   →       2              |        4.70 ms →       11.69 ms (+148.63%) | 
  │ └ sirius::Periodic_function::integrate                              |        3.90 ms →        3.90 ms   (-0.15%) |       1   →       1              |        3.90 ms →        3.90 ms   (-0.15%) | 
  ├ sirius::Potential::generate                                         |      186.34 ms →      188.29 ms   (+1.05%) |       1   →       1              |      186.34 ms →      188.29 ms   (+1.05%) | 
  │ ├ sirius::Potential::poisson                                        |       63.98 ms →       64.96 ms   (+1.53%) |       1   →       1              |       63.98 ms →       64.96 ms   (+1.53%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →       10.62 ms (+353.07%) |       1   →       1              |        2.34 ms →       10.62 ms (+353.07%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.25 ms →        4.34 ms   (+2.04%) |       1   →       1              |        4.25 ms →        4.34 ms   (+2.04%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.10 ms →        4.04 ms   (-1.37%) |       1   →       1              |        4.10 ms →        4.04 ms   (-1.37%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.10 ms →        4.04 ms   (-1.37%) |       1   →       1              |        4.10 ms →        4.04 ms   (-1.37%) | 
  │ ├ sirius::Periodic_function::add                                    |      246.86 μs →      238.52 μs   (-3.38%) |       2   →       2              |      493.73 μs →      477.04 μs   (-3.38%) | 
  │ ├ sirius::Potential::xc                                             |       95.90 ms →       96.73 ms   (+0.87%) |       1   →       1              |       95.90 ms →       96.73 ms   (+0.87%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       94.85 ms →       95.69 ms   (+0.88%) |       1   →       1              |       94.85 ms →       95.69 ms   (+0.88%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.01 ms →        2.00 ms   (-0.83%) |       5   →       5              |       10.07 ms →        9.99 ms   (-0.83%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.37 ms →        2.55 ms   (+7.67%) |       9   →       9              |       21.34 ms →       22.97 ms   (+7.67%) | 
  │ │   ├ sirius::gradient                                              |        7.61 ms →        7.49 ms   (-1.56%) |       1   →       1              |        7.61 ms →        7.49 ms   (-1.56%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.44 ms →        2.40 ms   (-1.61%) |       3   →       3              |        7.33 ms →        7.21 ms   (-1.61%) | 
  │ │   ├ sirius::dot                                                   |        2.81 ms →        2.81 ms   (-0.05%) |       1   →       1              |        2.81 ms →        2.81 ms   (-0.05%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.59 ms →        2.59 ms   (-0.17%) |       1   →       1              |        2.59 ms →        2.59 ms   (-0.17%) | 
  │ │   └ sirius::divergence                                            |       19.94 ms →       19.66 ms   (-1.40%) |       1   →       1              |       19.94 ms →       19.66 ms   (-1.40%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.44 ms   (+0.91%) |       1   →       1              |        2.42 ms →        2.44 ms   (+0.91%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.17 ms →        3.27 ms   (+3.15%) |       1   →       1              |        3.17 ms →        3.27 ms   (+3.15%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.24 ms →       22.30 ms   (+0.29%) |       1   →       1              |       22.24 ms →       22.30 ms   (+0.29%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      132.00 ns →      102.00 ns  (-22.73%) |       1   →       1              |      132.00 ns →      102.00 ns  (-22.73%) | 
  ├ sirius::Hamiltonian0                                                |       14.11 ms →       13.91 ms   (-1.42%) |       1   →       1              |       14.11 ms →       13.91 ms   (-1.42%) | 
  │ ├ sirius::Local_operator                                            |       13.79 ms →       13.58 ms   (-1.47%) |       1   →       1              |       13.79 ms →       13.58 ms   (-1.47%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.16 ms →        7.16 ms   (-0.01%) |       1   →       1              |        7.16 ms →        7.16 ms   (-0.01%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.17 ms →        4.96 ms   (-4.05%) |       1   →       1              |        5.17 ms →        4.96 ms   (-4.05%) | 
  │ ├ sirius::Non_local_operator                                        |       60.16 μs →       60.26 μs   (+0.16%) |       2   →       2              |      120.33 μs →      120.52 μs   (+0.16%) | 
  │ ├ sirius::D_operator::initialize                                    |       77.94 μs →       80.22 μs   (+2.92%) |       1   →       1              |       77.94 μs →       80.22 μs   (+2.92%) | 
  │ └ sirius::Q_operator::initialize                                    |       67.63 μs →       67.27 μs   (-0.53%) |       1   →       1              |       67.63 μs →       67.27 μs   (-0.53%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.46 s  →        2.52 s    (+2.47%) |       1   →       1              |        2.46 s  →        2.52 s    (+2.47%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.39 ms →        8.40 ms   (+0.09%) |       1   →       1              |        8.39 ms →        8.40 ms   (+0.09%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      249.97 μs →      243.00 μs   (-2.79%) |       1   →       1              |      249.97 μs →      243.00 μs   (-2.79%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.14 ms →        8.15 ms   (+0.18%) |       1   →       1              |        8.14 ms →        8.15 ms   (+0.18%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.45 s  →        2.51 s    (+2.48%) |       1   →       1              |        2.45 s  →        2.51 s    (+2.48%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       88.02 ms →       86.42 ms   (-1.82%) |       4   →       4              |      352.07 ms →      345.67 ms   (-1.82%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.10 ms →       25.16 ms   (+0.25%) |       1   →       1              |       25.10 ms →       25.16 ms   (+0.25%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.34 ms →       14.32 ms   (-0.10%) |       1   →       1              |       14.34 ms →       14.32 ms   (-0.10%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.20 s  →        1.25 s    (+4.73%) |       1   →       1              |        1.20 s  →        1.25 s    (+4.73%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      974.32 ms →        1.03 s    (+5.39%) |       1   →       1              |      974.32 ms →        1.03 s    (+5.39%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      307.35 ms →      356.48 ms  (+15.99%) |       1   →       1              |      307.35 ms →      356.48 ms  (+15.99%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      177.73 ms →      173.88 ms   (-2.17%) |       1   →       1              |      177.73 ms →      173.88 ms   (-2.17%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      177.73 ms →      173.88 ms   (-2.17%) |       1   →       1              |      177.73 ms →      173.88 ms   (-2.17%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      111.11 ms →      164.26 ms  (+47.83%) |       1   →       1              |      111.11 ms →      164.26 ms  (+47.83%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      174.53 ms →      171.33 ms   (-1.83%) |       1   →       1              |      174.53 ms →      171.33 ms   (-1.83%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      174.52 ms →      171.33 ms   (-1.83%) |       1   →       1              |      174.52 ms →      171.33 ms   (-1.83%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      160.15 ms →      167.41 ms   (+4.54%) |       1   →       1              |      160.15 ms →      167.41 ms   (+4.54%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      109.51 ms →      116.52 ms   (+6.41%) |       1   →       1              |      109.51 ms →      116.52 ms   (+6.41%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.77 ms →        3.76 ms   (-0.29%) |       1   →       1              |        3.77 ms →        3.76 ms   (-0.29%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.23 ms →       93.26 ms   (+4.51%) |       1   →       1              |       89.23 ms →       93.26 ms   (+4.51%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.43 ms →       15.58 ms  (+36.26%) |       1   →       1              |       11.43 ms →       15.58 ms  (+36.26%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.20 ms →       64.20 ms   (-0.01%) |       2   →       2              |      128.41 ms →      128.39 ms   (-0.01%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      195.25 ms →      202.38 ms   (+3.65%) |       2   →       2              |      390.49 ms →      404.75 ms   (+3.65%) | 
  │ │ │ └ sddk::wf_inner                                                |      195.15 ms →      202.27 ms   (+3.65%) |       2   →       2              |      390.29 ms →      404.55 ms   (+3.65%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       31.50 ns →       18.50 ns  (-41.27%) |       2   →       2              |       63.00 ns →       37.00 ns  (-41.27%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      193.61 ms →      200.24 ms   (+3.42%) |       2   →       2              |      387.22 ms →      400.47 ms   (+3.42%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       29.00 ns →       22.00 ns  (-24.14%) |       2   →       2              |       58.00 ns →       44.00 ns  (-24.14%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      115.14 ms →      116.07 ms   (+0.81%) |       1   →       1              |      115.14 ms →      116.07 ms   (+0.81%) | 
  │ │ └ sddk::wf_trans                                                  |       38.50 ms →       35.68 ms   (-7.34%) |       1   →       1              |       38.50 ms →       35.68 ms   (-7.34%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.69 ms →       35.66 ms   (-0.08%) |       1   →       1              |       35.69 ms →       35.66 ms   (-0.08%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      677.00 ns →      470.00 ns  (-30.58%) |       1   →       1              |      677.00 ns →      470.00 ns  (-30.58%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      109.69 s  →      117.47 s    (+7.09%) |       1   →       1              |      109.69 s  →      117.47 s    (+7.09%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms →        2.34 ms   (+7.56%) |      31   →      83   (+167.74%) |       67.35 ms →      193.97 ms (+187.99%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.88 s  →        3.08 s    (+6.89%) |      38   →      38              |      109.43 s  →      116.97 s    (+6.89%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.34 ms →        7.32 ms   (-0.30%) |      38   →      38              |      278.82 ms →      277.98 ms   (-0.30%) | 
  │ │ │ ├ sirius::Local_operator                                        |        7.01 ms →        6.98 ms   (-0.41%) |      38   →      38              |      266.22 ms →      265.13 ms   (-0.41%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.52 ms →        1.50 ms   (-1.16%) |      38   →      38              |       57.80 ms →       57.13 ms   (-1.16%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.02 ms →        4.02 ms   (+0.07%) |      38   →      38              |      152.72 ms →      152.83 ms   (+0.07%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       59.63 μs →       61.48 μs   (+3.12%) |      76   →      76              |        4.53 ms →        4.67 ms   (+3.12%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       82.71 μs →       82.93 μs   (+0.26%) |      38   →      38              |        3.14 ms →        3.15 ms   (+0.26%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       69.06 μs →       69.26 μs   (+0.29%) |      38   →      38              |        2.62 ms →        2.63 ms   (+0.29%) | 
  │ │ ├ sirius::Band::solve                                             |        2.22 s  →        2.28 s    (+2.83%) |      38   →      38              |       84.18 s  →       86.56 s    (+2.83%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      205.38 μs →      206.22 μs   (+0.41%) |      38   →      38              |        7.80 ms →        7.84 ms   (+0.41%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.71 μs →      199.18 μs   (+0.24%) |      38   →      38              |        7.55 ms →        7.57 ms   (+0.24%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.98 μs →        5.36 μs   (+7.51%) |      38   →      38              |      189.36 μs →      203.58 μs   (+7.51%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.21 s  →        2.26 s    (+2.35%) |      38   →      38              |       84.05 s  →       86.03 s    (+2.35%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       61.28 ms →       60.84 ms   (-0.71%) |      38   →      38              |        2.33 s  →        2.31 s    (-0.71%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.69 ms →        4.70 ms   (+0.28%) |     228   →     228              |        1.07 s  →        1.07 s    (+0.28%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.64 ms →        1.65 ms   (+0.43%) |      38   →      38              |       62.48 ms →       62.75 ms   (+0.43%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.54 μs →      420.52 μs   (-0.24%) |      38   →      38              |       16.02 ms →       15.98 ms   (-0.24%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      963.09 μs →      974.12 μs   (+1.15%) |      38   →      38              |       36.60 ms →       37.02 ms   (+1.15%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.12 s  →        2.18 s    (+2.47%) |      38   →      38              |       80.75 s  →       82.74 s    (+2.47%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      210.24 ms →      198.60 ms   (-5.54%) |     201   →     219     (+8.96%) |       42.26 s  →       43.49 s    (+2.92%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      148.31 ms →      140.22 ms   (-5.46%) |     201   →     219     (+8.96%) |       29.81 s  →       30.71 s    (+3.01%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       26.78 ms →       26.12 ms   (-2.46%) |     201   →     219     (+8.96%) |        5.38 s  →        5.72 s    (+6.28%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      698.88 μs →      639.46 μs   (-8.50%) |     201   →     219     (+8.96%) |      140.47 ms →      140.04 ms   (-0.31%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.68 ms →        3.67 ms   (-0.34%) |      38   →      38              |      140.01 ms →      139.53 ms   (-0.34%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.68 ms →       21.41 ms   (-1.25%) |     201   →     219     (+8.96%) |        4.36 s  →        4.69 s    (+7.59%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      695.98 μs →      637.29 μs   (-8.43%) |     201   →     219     (+8.96%) |      139.89 ms →      139.57 ms   (-0.23%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.67 ms →        3.66 ms   (-0.29%) |      38   →      38              |      139.35 ms →      138.95 ms   (-0.29%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       32.69 ms →       32.12 ms   (-1.72%) |     201   →     219     (+8.96%) |        6.57 s  →        7.04 s    (+7.08%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       20.11 ms →       20.54 ms   (+2.11%) |     201   →     219     (+8.96%) |        4.04 s  →        4.50 s   (+11.26%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.62 ms   (-0.97%) |     201   →     219     (+8.96%) |      531.95 ms →      573.95 ms   (+7.90%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.41 ms →       21.28 ms   (-5.03%) |     201   →     219     (+8.96%) |        4.50 s  →        4.66 s    (+3.48%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.48 ms →        2.78 ms  (+11.97%) |     201   →     219     (+8.96%) |      498.55 ms →      608.22 ms  (+22.00%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.43 ms →       17.22 ms   (-6.53%) |     402   →     438     (+8.96%) |        7.41 s  →        7.54 s    (+1.84%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       84.83 ms →       80.80 ms   (-4.75%) |     201   →     219     (+8.96%) |       17.05 s  →       17.69 s    (+3.78%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       13.03 ms →       12.82 ms   (-1.63%) |     364   →     400     (+9.89%) |        4.74 s  →        5.13 s    (+8.10%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       55.93 ns →      110.56 ns  (+97.69%) |     364   →     400     (+9.89%) |       20.36 μs →       44.22 μs (+117.24%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.56 ms →        9.15 ms   (-4.24%) |     364   →     400     (+9.89%) |        3.48 s  →        3.66 s    (+5.23%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       37.48 ns →      119.25 ns (+218.20%) |     364   →     400     (+9.89%) |       13.64 μs →       47.70 μs (+249.67%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       31.32 ms →       29.45 ms   (-5.98%) |     201   →     219     (+8.96%) |        6.30 s  →        6.45 s    (+2.44%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.65 ms →       14.49 ms   (-7.47%) |     201   →     219     (+8.96%) |        3.15 s  →        3.17 s    (+0.82%) | 
! │ │ │ │   │ └ sddk::wf_trans                                          |       17.56 ms →       16.26 ms   (-7.41%) |     163   →     181    (+11.04%) |        2.86 s  →        2.94 s    (+2.82%) | 
! │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.83 ms →        5.39 ms   (-7.46%) |     489   →     543    (+11.04%) |        2.85 s  →        2.93 s    (+2.76%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       23.25 ms →       21.74 ms   (-6.50%) |     201   →     219     (+8.96%) |        4.67 s  →        4.76 s    (+1.87%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       21.96 ms →       20.54 ms   (-6.45%) |     201   →     219     (+8.96%) |        4.41 s  →        4.50 s    (+1.92%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |      168.00 ns →      150.00 ns  (-10.72%) |     201   →     219     (+8.96%) |       33.77 μs →       32.85 μs   (-2.72%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       16.08 ms →       15.34 ms   (-4.60%) |     201   →     219     (+8.96%) |        3.23 s  →        3.36 s    (+3.94%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       24.97 ns →      104.52 ns (+318.56%) |     201   →     219     (+8.96%) |        5.02 μs →       22.89 μs (+356.05%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       47.14 ms →       42.72 ms   (-9.38%) |     201   →     219     (+8.96%) |        9.48 s  →        9.36 s    (-1.26%) | 
  │ │ │ │   ├ sirius::residuals                                         |       16.01 ms →       14.72 ms   (-8.07%) |     196   →     213     (+8.67%) |        3.14 s  →        3.13 s    (-0.09%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       16.85 ms →       14.85 ms  (-11.86%) |     164   →     185    (+12.80%) |        2.76 s  →        2.75 s    (-0.57%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.04 ms →        7.16 ms  (-10.96%) |     328   →     370    (+12.80%) |        2.64 s  →        2.65 s    (+0.44%) | 
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.56 ms →        1.44 ms   (-7.75%) |     164   →     185    (+12.80%) |      255.41 ms →      265.78 ms   (+4.06%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.76 ms →       51.11 ms   (-1.25%) |      80   →      84     (+5.00%) |        4.14 s  →        4.29 s    (+3.68%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       33.00 ms →       32.06 ms   (-2.84%) |     122   →     130     (+6.56%) |        4.03 s  →        4.17 s    (+3.53%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       24.25 ms →       23.42 ms   (-3.43%) |     164   →     176     (+7.32%) |        3.98 s  →        4.12 s    (+3.63%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      549.45 ns →      672.97 ns  (+22.48%) |      38   →      38              |       20.88 μs →       25.57 μs  (+22.48%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       56.76 μs →       33.23 μs  (-41.46%) |      38   →      38              |        2.16 ms →        1.26 ms  (-41.46%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.52 ms →        3.59 ms   (+2.02%) |      38   →      38              |      133.84 ms →      136.55 ms   (+2.02%) | 
  │ │ ├ sirius::Density::generate                                       |      294.24 ms →      304.86 ms   (+3.61%) |      38   →      38              |       11.18 s  →       11.58 s    (+3.61%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      290.22 ms →      300.76 ms   (+3.63%) |      38   →      38              |       11.03 s  →       11.43 s    (+3.63%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.79 ms →       70.38 ms   (+8.63%) |      38   →      38              |        2.46 s  →        2.67 s    (+8.63%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       70.88 μs →       65.52 μs   (-7.57%) |      38   →      38              |        2.69 ms →        2.49 ms   (-7.57%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.28 ms →        1.19 ms   (-7.15%) |       2   →       2              |        2.57 ms →        2.38 ms   (-7.15%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       53.49 ms →       59.12 ms  (+10.51%) |      38   →      38              |        2.03 s  →        2.25 s   (+10.51%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.23 ms →       61.87 ms   (+1.05%) |      38   →      38              |        2.33 s  →        2.35 s    (+1.05%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.94 μs →       10.51 μs   (-3.94%) |      38   →      38              |      415.69 μs →      399.32 μs   (-3.94%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (+0.18%) |      38   →      38              |       87.72 ms →       87.87 ms   (+0.18%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.37 ms →       59.02 ms   (+1.12%) |      38   →      38              |        2.22 s  →        2.24 s    (+1.12%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.93 ms →        7.58 ms   (+9.34%) |      38   →      38              |      263.42 ms →      288.04 ms   (+9.34%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      803.79 ns →      544.29 ns  (-32.28%) |      38   →      38              |       30.54 μs →       20.68 μs  (-32.28%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.32 ms →      104.16 ms   (-0.15%) |      38   →      38              |        3.96 s  →        3.96 s    (-0.15%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.39 ms   (-0.37%) |      38   →      38              |       91.27 ms →       90.93 ms   (-0.37%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.06 ms   (+0.06%) |      38   →      38              |      761.96 ms →      762.40 ms   (+0.06%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.90 ms   (+0.07%) |      38   →      38              |      755.59 ms →      756.11 ms   (+0.07%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      254.21 ns →      226.03 ns  (-11.09%) |      38   →      38              |        9.66 μs →        8.59 μs  (-11.09%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.52%) |      38   →      38              |       47.85 ms →       47.60 ms   (-0.52%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.77 ms →        2.85 ms   (+2.87%) |      38   →      38              |      105.11 ms →      108.13 ms   (+2.87%) | 
- │ │ ├ sirius::Density::mix                                            |      129.10 ms →      253.35 ms  (+96.24%) |      38   →      38              |        4.91 s  →        9.63 s   (+96.24%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      255.74 μs →      256.37 μs   (+0.24%) |      38   →      38              |        9.72 ms →        9.74 ms   (+0.24%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.58 ms →        2.61 ms  (-27.11%) |      38   →      38              |      136.22 ms →       99.29 ms  (-27.11%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.39 ms →        2.48 ms  (-27.05%) |      38   →      38              |      128.92 ms →       94.05 ms  (-27.05%) | 
  │ │ ├ sirius::Potential::generate                                     |      180.85 ms →      182.11 ms   (+0.70%) |      38   →      38              |        6.87 s  →        6.92 s    (+0.70%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.18 ms →       64.90 ms   (+1.12%) |      38   →      38              |        2.44 s  →        2.47 s    (+1.12%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.44 ms →       10.66 ms (+337.11%) |      38   →      38              |       92.69 ms →      405.15 ms (+337.11%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.24 ms →        4.25 ms   (+0.32%) |      38   →      38              |      161.14 ms →      161.65 ms   (+0.32%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.10 ms →        4.08 ms   (-0.53%) |      38   →      38              |      155.79 ms →      154.96 ms   (-0.53%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.10 ms →        4.08 ms   (-0.53%) |      38   →      38              |      155.76 ms →      154.94 ms   (-0.53%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      233.93 μs →      228.28 μs   (-2.42%) |      76   →      76              |       17.78 ms →       17.35 ms   (-2.42%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       91.32 ms →       91.67 ms   (+0.38%) |      38   →      38              |        3.47 s  →        3.48 s    (+0.38%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       90.28 ms →       90.64 ms   (+0.40%) |      38   →      38              |        3.43 s  →        3.44 s    (+0.40%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.60 ms   (+0.12%) |     190   →     190              |      302.74 ms →      303.12 ms   (+0.12%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.50 ms →        2.59 ms   (+3.45%) |     342   →     342              |      856.10 ms →      885.66 ms   (+3.45%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.48 ms →        2.45 ms   (-1.45%) |      38   →      38              |       94.43 ms →       93.06 ms   (-1.45%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      732.45 μs →      724.33 μs   (-1.11%) |     114   →     114              |       83.50 ms →       82.57 ms   (-1.11%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.82 ms →        2.81 ms   (-0.19%) |      38   →      38              |      107.15 ms →      106.94 ms   (-0.19%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.59 ms →        2.58 ms   (-0.39%) |      38   →      38              |       98.39 ms →       98.01 ms   (-0.39%) | 
  │ │ │ │   └ sirius::divergence                                        |       19.82 ms →       19.57 ms   (-1.22%) |      38   →      38              |      753.00 ms →      743.80 ms   (-1.22%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.45 ms →        2.43 ms   (-0.75%) |      38   →      38              |       93.01 ms →       92.31 ms   (-0.75%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.36 ms →        3.44 ms   (+2.57%) |      38   →      38              |      127.54 ms →      130.82 ms   (+2.57%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.97 ms →       21.09 ms   (+0.57%) |      38   →      38              |      796.79 ms →      801.33 ms   (+0.57%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      246.34 ns →      172.00 ns  (-30.18%) |      38   →      38              |        9.36 μs →        6.54 μs  (-30.18%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      238.47 ns →      237.39 ns   (-0.45%) |      38   →      38              |        9.06 μs →        9.02 μs   (-0.45%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.31 ms →        2.44 ms   (+5.82%) |      38   →      38              |       87.78 ms →       92.89 ms   (+5.82%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.31 ms →        4.24 ms   (-1.49%) |     266   →     266              |        1.15 s  →        1.13 s    (-1.49%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.11 ms →        4.09 ms   (-0.39%) |     266   →     266              |        1.09 s  →        1.09 s    (-0.39%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.11 ms →        4.09 ms   (-0.39%) |     266   →     266              |        1.09 s  →        1.09 s    (-0.39%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.17 ms →        4.09 ms   (-2.05%) |     114   →     114              |      475.91 ms →      466.14 ms   (-2.05%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.92 ms →        4.02 ms   (+2.72%) |     114   →     114              |      446.44 ms →      458.57 ms   (+2.72%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.03 ms →        4.24 ms   (+5.28%) |      38   →      38              |      153.05 ms →      161.13 ms   (+5.28%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      139.14 μs →      187.74 μs  (+34.93%) |      38   →      38              |        5.29 ms →        7.13 ms  (+34.93%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      135.55 μs →      184.12 μs  (+35.83%) |      38   →      38              |        5.15 ms →        7.00 ms  (+35.83%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.38 ms →        5.85 ms   (+8.71%) |       2   →       2              |       10.76 ms →       11.69 ms   (+8.71%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.27 ms →        4.53 ms   (+6.08%) |       6   →       6              |       25.64 ms →       27.20 ms   (+6.08%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.14 ms →        4.15 ms   (+0.15%) |       6   →       6              |       24.85 ms →       24.89 ms   (+0.15%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.14 ms →        4.15 ms   (+0.15%) |       6   →       6              |       24.85 ms →       24.89 ms   (+0.15%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.39 ms →        4.36 ms   (-0.63%) |       3   →       3              |       13.16 ms →       13.07 ms   (-0.63%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.94 ms →        4.01 ms   (+1.84%) |       3   →       3              |       11.81 ms →       12.02 ms   (+1.84%) | 
- ├ sirius::Periodic_function|inner                                     |        4.10 ms →        4.53 ms  (+10.49%) |       2   →       2              |        8.20 ms →        9.06 ms  (+10.49%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.09 ms →        4.11 ms   (+0.46%) |       2   →       2              |        8.18 ms →        8.22 ms   (+0.46%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.09 ms →        4.11 ms   (+0.46%) |       2   →       2              |        8.18 ms →        8.21 ms   (+0.46%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        3.96 ms →        4.34 ms   (+9.48%) |       1   →       1              |        3.96 ms →        4.34 ms   (+9.48%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.96 ms →        3.97 ms   (+0.33%) |       1   →       1              |        3.96 ms →        3.97 ms   (+0.33%) | 
  └ sirius::finalize                                                    |      465.67 ms →      508.91 ms   (+9.29%) |       1   →       1              |      465.67 ms →      508.91 ms   (+9.29%) | 
  ====================================================================================================================================================================================================
```
