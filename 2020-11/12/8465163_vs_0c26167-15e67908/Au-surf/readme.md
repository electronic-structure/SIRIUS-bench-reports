# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 8465163e5150bf9c73ec5dac4bf03576202704b3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      118.38 s  →      117.76 s    (-0.52%) |       1   →       1              |      118.38 s  →      117.76 s    (-0.52%) | 
  ├ sirius::initialize                                                  |        2.78 s  →        2.75 s    (-1.17%) |       1   →       1              |        2.78 s  →        2.75 s    (-1.17%) | 
  ├ sirius::Simulation_context::initialize                              |        2.06 s  →        2.07 s    (+0.60%) |       1   →       1              |        2.06 s  →        2.07 s    (+0.60%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       36.42 ms →       42.91 ms  (+17.84%) |       1   →       1              |       36.42 ms →       42.91 ms  (+17.84%) | 
  │ ├ sirius::Unit_cell::initialize                                     |       80.96 ms →       82.00 ms   (+1.29%) |       1   →       1              |       80.96 ms →       82.00 ms   (+1.29%) | 
  │ │ ├ sirius::Atom_type::init                                         |       54.90 ms →       54.31 ms   (-1.07%) |       1   →       1              |       54.90 ms →       54.31 ms   (-1.07%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.00 ms →       27.62 ms   (+6.27%) |       1   →       1              |       26.00 ms →       27.62 ms   (+6.27%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.46 ms →       10.62 ms   (+1.47%) |       1   →       1              |       10.46 ms →       10.62 ms   (+1.47%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.50 ms →       16.97 ms   (+9.46%) |       1   →       1              |       15.50 ms →       16.97 ms   (+9.46%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.21 ms →       16.25 ms   (+6.82%) |       1   →       1              |       15.21 ms →       16.25 ms   (+6.82%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       14.99 ms →       16.02 ms   (+6.89%) |       1   →       1              |       14.99 ms →       16.02 ms   (+6.89%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      209.96 μs →      217.08 μs   (+3.39%) |       1   →       1              |      209.96 μs →      217.08 μs   (+3.39%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.85 μs →        2.32 μs  (-18.60%) |       1   →       1              |        2.85 μs →        2.32 μs  (-18.60%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.89 s    (+0.16%) |       1   →       1              |        1.89 s  →        1.89 s    (+0.16%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.80 ms →       13.35 ms   (+4.26%) |       1   →       1              |       12.80 ms →       13.35 ms   (+4.26%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.31 ms →        8.41 ms   (+1.25%) |       1   →       1              |        8.31 ms →        8.41 ms   (+1.25%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.47 ms →        4.91 ms   (+9.85%) |       1   →       1              |        4.47 ms →        4.91 ms   (+9.85%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.18 ms →        4.30 ms   (+2.90%) |       1   →       1              |        4.18 ms →        4.30 ms   (+2.90%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.96 ms →        4.08 ms   (+3.00%) |       1   →       1              |        3.96 ms →        4.08 ms   (+3.00%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      214.03 μs →      216.39 μs   (+1.10%) |       1   →       1              |      214.03 μs →      216.39 μs   (+1.10%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.25 μs →        1.22 μs   (-2.56%) |       1   →       1              |        1.25 μs →        1.22 μs   (-2.56%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       14.98 ms →       15.89 ms   (+6.06%) |       2   →       2              |       29.97 ms →       31.78 ms   (+6.06%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.10 ms   (+0.23%) |       2   →       2              |        2.20 ms →        2.20 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      959.83 μs →      958.45 μs   (-0.14%) |       1   →       1              |      959.83 μs →      958.45 μs   (-0.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |        5.07 ms →        5.10 ms   (+0.72%) |       2   →       2              |       10.13 ms →       10.20 ms   (+0.72%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.64 ms →        3.64 ms   (+0.00%) |       2   →       2              |        7.28 ms →        7.28 ms   (+0.00%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.70 ms →       16.03 ms   (+2.14%) |       4   →       4              |       62.79 ms →       64.14 ms   (+2.14%) | 
  │   ├ sddk::Gvec::init                                                |      157.72 ms →      159.10 ms   (+0.88%) |       2   →       2              |      315.45 ms →      318.21 ms   (+0.88%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      125.25 ms →      126.33 ms   (+0.86%) |       2   →       2              |      250.51 ms →      252.67 ms   (+0.86%) | 
  │   ├ sddk::Gvec_shells                                               |      118.42 ms →      122.61 ms   (+3.54%) |       1   →       1              |      118.42 ms →      122.61 ms   (+3.54%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.03 ms →        1.03 ms   (+0.20%) |       1   →       1              |        1.03 ms →        1.03 ms   (+0.20%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      216.89 ms →      218.86 ms   (+0.91%) |       1   →       1              |      216.89 ms →      218.86 ms   (+0.91%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.71 ms →       26.59 ms   (+3.43%) |       1   →       1              |       25.71 ms →       26.59 ms   (+3.43%) | 
  │ ├ sirius::K_point::K_point                                          |        2.00 μs →        1.83 μs   (-8.57%) |       2   →       2              |        4.00 μs →        3.66 μs   (-8.57%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.68 ms →       26.55 ms   (+3.42%) |       1   →       1              |       25.68 ms →       26.55 ms   (+3.42%) | 
  │   └ sirius::K_point::initialize                                     |       25.61 ms →       26.49 ms   (+3.44%) |       1   →       1              |       25.61 ms →       26.49 ms   (+3.44%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.19 ms →       19.98 ms   (+4.09%) |       1   →       1              |       19.19 ms →       19.98 ms   (+4.09%) | 
  │     │ └ sddk::Gvec::init                                            |        4.92 ms →        5.24 ms   (+6.68%) |       1   →       1              |        4.92 ms →        5.24 ms   (+6.68%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.23 μs →       12.21 μs   (+8.70%) |       1   →       1              |       11.23 μs →       12.21 μs   (+8.70%) | 
  │     └ sirius::K_point::update                                       |        4.08 ms →        4.11 ms   (+0.75%) |       1   →       1              |        4.08 ms →        4.11 ms   (+0.75%) | 
  │       └ sirius::Beta_projectors                                     |        1.70 ms →        1.72 ms   (+1.11%) |       1   →       1              |        1.70 ms →        1.72 ms   (+1.11%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      889.11 μs →      896.84 μs   (+0.87%) |       1   →       1              |      889.11 μs →      896.84 μs   (+0.87%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.47 ms →        1.50 ms   (+2.16%) |       2   →       2              |        2.93 ms →        3.00 ms   (+2.16%) | 
  ├ sirius::Potential                                                   |       90.99 ms →       95.80 ms   (+5.29%) |       1   →       1              |       90.99 ms →       95.80 ms   (+5.29%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.46 ms   (+0.63%) |       6   →       6              |       14.65 ms →       14.74 ms   (+0.63%) | 
  │ └ sirius::Potential::update                                         |       75.98 ms →       80.71 ms   (+6.23%) |       1   →       1              |       75.98 ms →       80.71 ms   (+6.23%) | 
  │   └ sirius::Potential::generate_local_potential                     |       75.81 ms →       80.54 ms   (+6.24%) |       1   →       1              |       75.81 ms →       80.54 ms   (+6.24%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       51.83 ms →       50.90 ms   (-1.80%) |       1   →       1              |       51.83 ms →       50.90 ms   (-1.80%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       15.30 ms →       20.78 ms  (+35.85%) |       1   →       1              |       15.30 ms →       20.78 ms  (+35.85%) | 
  ├ sirius::Density                                                     |       70.80 ms →       75.67 ms   (+6.88%) |       1   →       1              |       70.80 ms →       75.67 ms   (+6.88%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.80 ms →        4.78 ms   (-0.46%) |       2   →       2              |        9.60 ms →        9.56 ms   (-0.46%) | 
  │ └ sirius::Density::update                                           |       61.08 ms →       66.00 ms   (+8.05%) |       1   →       1              |       61.08 ms →       66.00 ms   (+8.05%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       60.91 ms →       65.83 ms   (+8.07%) |       1   →       1              |       60.91 ms →       65.83 ms   (+8.07%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.11 ms →        3.08 ms   (-0.99%) |       1   →       1              |        3.11 ms →        3.08 ms   (-0.99%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.27 ms →       52.47 ms   (-1.51%) |       1   →       1              |       53.27 ms →       52.47 ms   (-1.51%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.25 ms →        9.03 ms (+177.70%) |       1   →       1              |        3.25 ms →        9.03 ms (+177.70%) | 
  ├ sirius::Density::initial_density                                    |       75.42 ms →       79.86 ms   (+5.88%) |       1   →       1              |       75.42 ms →       79.86 ms   (+5.88%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.50 ms →       52.59 ms   (-1.71%) |       1   →       1              |       53.50 ms →       52.59 ms   (-1.71%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.91 ms →        5.47 ms  (+87.84%) |       2   →       2              |        5.82 ms →       10.93 ms  (+87.84%) | 
+ │ └ sirius::Periodic_function::integrate                              |        4.55 ms →        3.94 ms  (-13.38%) |       1   →       1              |        4.55 ms →        3.94 ms  (-13.38%) | 
  ├ sirius::Potential::generate                                         |      181.71 ms →      191.09 ms   (+5.16%) |       1   →       1              |      181.71 ms →      191.09 ms   (+5.16%) | 
- │ ├ sirius::Potential::poisson                                        |       57.69 ms →       64.50 ms  (+11.81%) |       1   →       1              |       57.69 ms →       64.50 ms  (+11.81%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.51 ms →       10.25 ms (+308.47%) |       1   →       1              |        2.51 ms →       10.25 ms (+308.47%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.44 ms →        4.45 ms   (+0.29%) |       1   →       1              |        4.44 ms →        4.45 ms   (+0.29%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.19 ms →        4.44 ms   (+6.08%) |       1   →       1              |        4.19 ms →        4.44 ms   (+6.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.19 ms →        4.44 ms   (+6.08%) |       1   →       1              |        4.19 ms →        4.44 ms   (+6.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      230.76 μs →      249.10 μs   (+7.95%) |       2   →       2              |      461.51 μs →      498.20 μs   (+7.95%) | 
  │ ├ sirius::Potential::xc                                             |       97.43 ms →       99.96 ms   (+2.60%) |       1   →       1              |       97.43 ms →       99.96 ms   (+2.60%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       96.32 ms →       98.91 ms   (+2.69%) |       1   →       1              |       96.32 ms →       98.91 ms   (+2.69%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        1.97 ms →        2.01 ms   (+1.67%) |       5   →       5              |        9.86 ms →       10.03 ms   (+1.67%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.65 ms →        2.45 ms   (-7.54%) |       9   →       9              |       23.81 ms →       22.02 ms   (-7.54%) | 
  │ │   ├ sirius::gradient                                              |        7.58 ms →        7.60 ms   (+0.32%) |       1   →       1              |        7.58 ms →        7.60 ms   (+0.32%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.43 ms →        2.44 ms   (+0.39%) |       3   →       3              |        7.30 ms →        7.32 ms   (+0.39%) | 
  │ │   ├ sirius::dot                                                   |        2.79 ms →        2.79 ms   (+0.30%) |       1   →       1              |        2.79 ms →        2.79 ms   (+0.30%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.55 ms →        2.57 ms   (+0.82%) |       1   →       1              |        2.55 ms →        2.57 ms   (+0.82%) | 
- │ │   └ sirius::divergence                                            |       19.58 ms →       23.19 ms  (+18.40%) |       1   →       1              |       19.58 ms →       23.19 ms  (+18.40%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.42 ms →        2.40 ms   (-0.88%) |       1   →       1              |        2.42 ms →        2.40 ms   (-0.88%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.37 ms →        3.21 ms   (-4.75%) |       1   →       1              |        3.37 ms →        3.21 ms   (-4.75%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.20 ms →       22.35 ms   (+0.68%) |       1   →       1              |       22.20 ms →       22.35 ms   (+0.68%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      121.00 ns →      203.00 ns  (+67.77%) |       1   →       1              |      121.00 ns →      203.00 ns  (+67.77%) | 
  ├ sirius::Hamiltonian0                                                |       13.81 ms →       14.70 ms   (+6.39%) |       1   →       1              |       13.81 ms →       14.70 ms   (+6.39%) | 
  │ ├ sirius::Local_operator                                            |       13.49 ms →       14.37 ms   (+6.50%) |       1   →       1              |       13.49 ms →       14.37 ms   (+6.50%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.07 ms →        7.22 ms   (+2.05%) |       1   →       1              |        7.07 ms →        7.22 ms   (+2.05%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.96 ms →        5.70 ms  (+15.12%) |       1   →       1              |        4.96 ms →        5.70 ms  (+15.12%) | 
  │ ├ sirius::Non_local_operator                                        |       58.40 μs →       61.44 μs   (+5.21%) |       2   →       2              |      116.81 μs →      122.89 μs   (+5.21%) | 
  │ ├ sirius::D_operator::initialize                                    |       81.48 μs →       80.52 μs   (-1.18%) |       1   →       1              |       81.48 μs →       80.52 μs   (-1.18%) | 
  │ └ sirius::Q_operator::initialize                                    |       67.52 μs →       69.10 μs   (+2.33%) |       1   →       1              |       67.52 μs →       69.10 μs   (+2.33%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.45 s  →        2.47 s    (+0.71%) |       1   →       1              |        2.45 s  →        2.47 s    (+0.71%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms →        8.39 ms   (-0.18%) |       1   →       1              |        8.40 ms →        8.39 ms   (-0.18%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      248.44 μs →      235.93 μs   (-5.04%) |       1   →       1              |      248.44 μs →      235.93 μs   (-5.04%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.15 ms →        8.15 ms   (-0.03%) |       1   →       1              |        8.15 ms →        8.15 ms   (-0.03%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.44 s  →        2.46 s    (+0.71%) |       1   →       1              |        2.44 s  →        2.46 s    (+0.71%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.05 ms →       87.14 ms   (+1.26%) |       4   →       4              |      344.22 ms →      348.54 ms   (+1.26%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.08 ms →       25.50 ms   (+1.68%) |       1   →       1              |       25.08 ms →       25.50 ms   (+1.68%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.33 ms →       14.66 ms   (+2.33%) |       1   →       1              |       14.33 ms →       14.66 ms   (+2.33%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.21 s    (+0.28%) |       1   →       1              |        1.21 s  →        1.21 s    (+0.28%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      986.88 ms →      983.85 ms   (-0.31%) |       1   →       1              |      986.88 ms →      983.85 ms   (-0.31%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      322.61 ms →      317.74 ms   (-1.51%) |       1   →       1              |      322.61 ms →      317.74 ms   (-1.51%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      172.95 ms →      173.69 ms   (+0.42%) |       1   →       1              |      172.95 ms →      173.69 ms   (+0.42%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      172.95 ms →      173.68 ms   (+0.42%) |       1   →       1              |      172.95 ms →      173.68 ms   (+0.42%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      131.18 ms →      125.47 ms   (-4.35%) |       1   →       1              |      131.18 ms →      125.47 ms   (-4.35%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      172.50 ms →      172.81 ms   (+0.18%) |       1   →       1              |      172.50 ms →      172.81 ms   (+0.18%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      172.50 ms →      172.80 ms   (+0.18%) |       1   →       1              |      172.50 ms →      172.80 ms   (+0.18%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      160.25 ms →      161.47 ms   (+0.76%) |       1   →       1              |      160.25 ms →      161.47 ms   (+0.76%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      109.61 ms →      110.87 ms   (+1.15%) |       1   →       1              |      109.61 ms →      110.87 ms   (+1.15%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.75 ms →        3.75 ms   (-0.14%) |       1   →       1              |        3.75 ms →        3.75 ms   (-0.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.91 ms →       96.27 ms   (+7.08%) |       1   →       1              |       89.91 ms →       96.27 ms   (+7.08%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.17 ms →       18.64 ms  (+53.16%) |       1   →       1              |       12.17 ms →       18.64 ms  (+53.16%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.19 ms →       64.21 ms   (+0.03%) |       2   →       2              |      128.39 ms →      128.43 ms   (+0.03%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      191.56 ms →      193.72 ms   (+1.13%) |       2   →       2              |      383.11 ms →      387.44 ms   (+1.13%) | 
  │ │ │ └ sddk::wf_inner                                                |      191.45 ms →      193.62 ms   (+1.13%) |       2   →       2              |      382.91 ms →      387.23 ms   (+1.13%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       38.50 ns →       32.00 ns  (-16.88%) |       2   →       2              |       77.00 ns →       64.00 ns  (-16.88%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      189.82 ms →      192.04 ms   (+1.17%) |       2   →       2              |      379.65 ms →      384.08 ms   (+1.17%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       21.50 ns   (-4.44%) |       2   →       2              |       45.00 ns →       43.00 ns   (-4.44%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      114.86 ms →      116.20 ms   (+1.17%) |       1   →       1              |      114.86 ms →      116.20 ms   (+1.17%) | 
  │ │ └ sddk::wf_trans                                                  |       36.84 ms →       35.68 ms   (-3.14%) |       1   →       1              |       36.84 ms →       35.68 ms   (-3.14%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.67 ms →       35.67 ms   (-0.02%) |       1   →       1              |       35.67 ms →       35.67 ms   (-0.02%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      404.00 ns →      762.00 ns  (+88.61%) |       1   →       1              |      404.00 ns →      762.00 ns  (+88.61%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      109.56 s  →      108.91 s    (-0.59%) |       1   →       1              |      109.56 s  →      108.91 s    (-0.59%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms →        2.17 ms   (+0.15%) |      31   →      31              |       67.23 ms →       67.33 ms   (+0.15%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.88 s  →        2.86 s    (-0.59%) |      38   →      38              |      109.33 s  →      108.68 s    (-0.59%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.14 ms →        7.18 ms   (+0.57%) |      38   →      38              |      271.42 ms →      272.97 ms   (+0.57%) | 
  │ │ │ ├ sirius::Local_operator                                        |        6.81 ms →        6.85 ms   (+0.54%) |      38   →      38              |      258.75 ms →      260.14 ms   (+0.54%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms →        1.51 ms   (+0.39%) |      38   →      38              |       57.11 ms →       57.33 ms   (+0.39%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.85 ms →        3.88 ms   (+0.75%) |      38   →      38              |      146.47 ms →      147.58 ms   (+0.75%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.29 μs →       61.61 μs   (+0.53%) |      76   →      76              |        4.66 ms →        4.68 ms   (+0.53%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       81.77 μs →       83.81 μs   (+2.50%) |      38   →      38              |        3.11 ms →        3.18 ms   (+2.50%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       68.55 μs →       69.53 μs   (+1.43%) |      38   →      38              |        2.60 ms →        2.64 ms   (+1.43%) | 
  │ │ ├ sirius::Band::solve                                             |        2.22 s  →        2.22 s    (-0.14%) |      38   →      38              |       84.38 s  →       84.26 s    (-0.14%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      205.44 μs →      210.36 μs   (+2.40%) |      38   →      38              |        7.81 ms →        7.99 ms   (+2.40%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.85 μs →      203.19 μs   (+2.19%) |      38   →      38              |        7.56 ms →        7.72 ms   (+2.19%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.85 μs →        5.56 μs  (+14.72%) |      38   →      38              |      184.31 μs →      211.45 μs  (+14.72%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.21 s  →        2.21 s    (+0.06%) |      38   →      38              |       84.12 s  →       84.16 s    (+0.06%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       59.80 ms →       60.99 ms   (+1.99%) |      38   →      38              |        2.27 s  →        2.32 s    (+1.99%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        4.60 ms →        4.82 ms   (+4.75%) |     228   →     228              |        1.05 s  →        1.10 s    (+4.75%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.64 ms →        1.64 ms   (+0.02%) |      38   →      38              |       62.28 ms →       62.29 ms   (+0.02%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.66 μs →      417.98 μs   (-0.87%) |      38   →      38              |       16.02 ms →       15.88 ms   (-0.87%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      960.38 μs →      959.57 μs   (-0.08%) |      38   →      38              |       36.49 ms →       36.46 ms   (-0.08%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.13 s  →        2.13 s    (+0.00%) |      38   →      38              |       80.86 s  →       80.87 s    (+0.00%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      210.59 ms →      210.30 ms   (-0.14%) |     201   →     201              |       42.33 s  →       42.27 s    (-0.14%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      148.44 ms →      148.09 ms   (-0.24%) |     201   →     201              |       29.84 s  →       29.77 s    (-0.24%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       26.67 ms →       26.31 ms   (-1.34%) |     201   →     201              |        5.36 s  →        5.29 s    (-1.34%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      737.66 μs →      726.61 μs   (-1.50%) |     201   →     201              |      148.27 ms →      146.05 ms   (-1.50%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.89 ms →        3.83 ms   (-1.51%) |      38   →      38              |      147.81 ms →      145.57 ms   (-1.51%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       21.53 ms →       21.19 ms   (-1.58%) |     201   →     201              |        4.33 s  →        4.26 s    (-1.58%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      687.00 μs →      695.74 μs   (+1.27%) |     201   →     201              |      138.09 ms →      139.84 ms   (+1.27%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.62 ms →        3.67 ms   (+1.25%) |      38   →      38              |      137.55 ms →      139.28 ms   (+1.25%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.01 ms →       32.96 ms   (-0.14%) |     201   →     201              |        6.63 s  →        6.62 s    (-0.14%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       20.43 ms →       20.40 ms   (-0.17%) |     201   →     201              |        4.11 s  →        4.10 s    (-0.17%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms →        2.65 ms   (+0.07%) |     201   →     201              |      531.68 ms →      532.05 ms   (+0.07%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.67 ms →       22.48 ms   (-0.83%) |     201   →     201              |        4.56 s  →        4.52 s    (-0.83%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.76 ms →        2.55 ms   (-7.46%) |     201   →     201              |      554.54 ms →      513.17 ms   (-7.46%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.40 ms →       18.52 ms   (+0.66%) |     402   →     402              |        7.40 s  →        7.45 s    (+0.66%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       85.86 ms →       86.13 ms   (+0.32%) |     201   →     201              |       17.26 s  →       17.31 s    (+0.32%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       13.18 ms →       13.06 ms   (-0.90%) |     364   →     364              |        4.80 s  →        4.75 s    (-0.90%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       56.96 ns →       38.55 ns  (-32.32%) |     364   →     364              |       20.73 μs →       14.03 μs  (-32.32%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        9.54 ms →        9.60 ms   (+0.59%) |     364   →     364              |        3.47 s  →        3.49 s    (+0.59%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       37.47 ns →       36.73 ns   (-1.96%) |     364   →     364              |       13.64 μs →       13.37 μs   (-1.96%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       32.09 ms →       32.59 ms   (+1.55%) |     201   →     201              |        6.45 s  →        6.55 s    (+1.55%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       15.65 ms →       15.66 ms   (+0.00%) |     201   →     201              |        3.15 s  →        3.15 s    (+0.00%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       17.57 ms →       17.56 ms   (-0.06%) |     163   →     163              |        2.86 s  →        2.86 s    (-0.06%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.83 ms →        5.83 ms   (+0.05%) |     489   →     489              |        2.85 s  →        2.85 s    (+0.05%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       22.27 ms →       22.29 ms   (+0.06%) |     201   →     201              |        4.48 s  →        4.48 s    (+0.06%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       20.93 ms →       20.99 ms   (+0.30%) |     201   →     201              |        4.21 s  →        4.22 s    (+0.30%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |      136.99 ns →      125.43 ns   (-8.44%) |     201   →     201              |       27.53 μs →       25.21 μs   (-8.44%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       16.04 ms →       16.08 ms   (+0.22%) |     201   →     201              |        3.22 s  →        3.23 s    (+0.22%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       24.75 ns →       20.37 ns  (-17.71%) |     201   →     201              |        4.97 μs →        4.09 μs  (-17.71%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       47.03 ms →       47.35 ms   (+0.68%) |     201   →     201              |        9.45 s  →        9.52 s    (+0.68%) | 
  │ │ │ │   ├ sirius::residuals                                         |       16.22 ms →       16.03 ms   (-1.21%) |     196   →     196              |        3.18 s  →        3.14 s    (-1.21%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       17.08 ms →       16.83 ms   (-1.47%) |     164   →     164              |        2.80 s  →        2.76 s    (-1.47%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        8.03 ms →        8.03 ms   (-0.01%) |     328   →     328              |        2.64 s  →        2.63 s    (-0.01%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.56 ms →        1.56 ms   (-0.30%) |     164   →     164              |      256.08 ms →      255.30 ms   (-0.30%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.98 ms →       51.70 ms   (-0.54%) |      80   →      80              |        4.16 s  →        4.14 s    (-0.54%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       33.15 ms →       32.97 ms   (-0.55%) |     122   →     122              |        4.04 s  →        4.02 s    (-0.55%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       24.22 ms →       24.25 ms   (+0.12%) |     164   →     164              |        3.97 s  →        3.98 s    (+0.12%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      524.61 ns →      498.29 ns   (-5.02%) |      38   →      38              |       19.94 μs →       18.93 μs   (-5.02%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       33.87 μs →       38.43 μs  (+13.46%) |      38   →      38              |        1.29 ms →        1.46 ms  (+13.46%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.52 ms →        3.53 ms   (+0.25%) |      38   →      38              |      133.87 ms →      134.20 ms   (+0.25%) | 
  │ │ ├ sirius::Density::generate                                       |      294.15 ms →      294.59 ms   (+0.15%) |      38   →      38              |       11.18 s  →       11.19 s    (+0.15%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      290.16 ms →      290.60 ms   (+0.15%) |      38   →      38              |       11.03 s  →       11.04 s    (+0.15%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       65.13 ms →       65.50 ms   (+0.57%) |      38   →      38              |        2.47 s  →        2.49 s    (+0.57%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       63.86 μs →       66.20 μs   (+3.66%) |      38   →      38              |        2.43 ms →        2.52 ms   (+3.66%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.16 ms →        1.19 ms   (+2.88%) |       2   →       2              |        2.32 ms →        2.39 ms   (+2.88%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       53.85 ms →       54.22 ms   (+0.68%) |      38   →      38              |        2.05 s  →        2.06 s    (+0.68%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.10 ms →       61.29 ms   (+0.31%) |      38   →      38              |        2.32 s  →        2.33 s    (+0.31%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.82 μs →       10.42 μs   (-3.65%) |      38   →      38              |      411.08 μs →      396.07 μs   (-3.65%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms →        2.31 ms   (+0.11%) |      38   →      38              |       87.71 ms →       87.80 ms   (+0.11%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.24 ms →       58.44 ms   (+0.33%) |      38   →      38              |        2.21 s  →        2.22 s    (+0.33%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        6.83 ms →        7.00 ms   (+2.41%) |      38   →      38              |      259.68 ms →      265.95 ms   (+2.41%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      764.32 ns →      775.82 ns   (+1.50%) |      38   →      38              |       29.04 μs →       29.48 μs   (+1.50%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.43 ms →      104.32 ms   (-0.10%) |      38   →      38              |        3.97 s  →        3.96 s    (-0.10%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms →        2.42 ms   (+0.71%) |      38   →      38              |       91.21 ms →       91.85 ms   (+0.71%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.04 ms   (-0.04%) |      38   →      38              |      761.97 ms →      761.68 ms   (-0.04%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.88 ms   (-0.02%) |      38   →      38              |      755.48 ms →      755.33 ms   (-0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      270.58 ns →      258.18 ns   (-4.58%) |      38   →      38              |       10.28 μs →        9.81 μs   (-4.58%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms →        1.25 ms   (-0.29%) |      38   →      38              |       47.74 ms →       47.60 ms   (-0.29%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.74 ms →        2.74 ms   (+0.13%) |      38   →      38              |      103.99 ms →      104.12 ms   (+0.13%) | 
+ │ │ ├ sirius::Density::mix                                            |      129.04 ms →      104.34 ms  (-19.14%) |      38   →      38              |        4.90 s  →        3.96 s   (-19.14%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      256.41 μs →      264.86 μs   (+3.30%) |      38   →      38              |        9.74 ms →       10.06 ms   (+3.30%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        3.69 ms →        2.70 ms  (-26.94%) |      38   →      38              |      140.30 ms →      102.51 ms  (-26.94%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.50 ms →        2.56 ms  (-26.84%) |      38   →      38              |      133.06 ms →       97.35 ms  (-26.84%) | 
  │ │ ├ sirius::Potential::generate                                     |      174.24 ms →      184.20 ms   (+5.72%) |      38   →      38              |        6.62 s  →        7.00 s    (+5.72%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       57.87 ms →       64.70 ms  (+11.80%) |      38   →      38              |        2.20 s  →        2.46 s   (+11.80%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.88 ms →       10.47 ms (+263.35%) |      38   →      38              |      109.47 ms →      397.76 ms (+263.35%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.26 ms →        4.31 ms   (+1.26%) |      38   →      38              |      161.79 ms →      163.83 ms   (+1.26%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.10 ms →        4.10 ms   (+0.03%) |      38   →      38              |      155.70 ms →      155.75 ms   (+0.03%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.10 ms →        4.10 ms   (+0.03%) |      38   →      38              |      155.68 ms →      155.73 ms   (+0.03%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      230.00 μs →      233.74 μs   (+1.63%) |      76   →      76              |       17.48 ms →       17.76 ms   (+1.63%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       91.05 ms →       94.19 ms   (+3.45%) |      38   →      38              |        3.46 s  →        3.58 s    (+3.45%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       90.01 ms →       93.15 ms   (+3.49%) |      38   →      38              |        3.42 s  →        3.54 s    (+3.49%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.59 ms   (+0.38%) |     190   →     190              |      301.43 ms →      302.58 ms   (+0.38%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.50 ms →        2.43 ms   (-2.67%) |     342   →     342              |      853.71 ms →      830.96 ms   (-2.67%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.46 ms →        2.46 ms   (+0.28%) |      38   →      38              |       93.36 ms →       93.62 ms   (+0.28%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      726.12 μs →      727.75 μs   (+0.22%) |     114   →     114              |       82.78 ms →       82.96 ms   (+0.22%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.81 ms →        2.81 ms   (+0.01%) |      38   →      38              |      106.93 ms →      106.94 ms   (+0.01%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms →        2.59 ms   (+0.16%) |      38   →      38              |       98.21 ms →       98.36 ms   (+0.16%) | 
- │ │ │ │   └ sirius::divergence                                        |       19.69 ms →       23.29 ms  (+18.32%) |      38   →      38              |      748.05 ms →      885.12 ms  (+18.32%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.43 ms →        2.44 ms   (+0.36%) |      38   →      38              |       92.38 ms →       92.71 ms   (+0.36%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.38 ms →        3.33 ms   (-1.44%) |      38   →      38              |      128.27 ms →      126.42 ms   (-1.44%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.95 ms →       20.95 ms   (+0.02%) |      38   →      38              |      795.91 ms →      796.04 ms   (+0.02%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      247.32 ns →      203.45 ns  (-17.74%) |      38   →      38              |        9.40 μs →        7.73 μs  (-17.74%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      245.03 ns →      233.16 ns   (-4.84%) |      38   →      38              |        9.31 μs →        8.86 μs   (-4.84%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.28 ms →        2.29 ms   (+0.45%) |      38   →      38              |       86.56 ms →       86.95 ms   (+0.45%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.22 ms →        4.29 ms   (+1.54%) |     266   →     266              |        1.12 s  →        1.14 s    (+1.54%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.10 ms →        4.13 ms   (+0.60%) |     266   →     266              |        1.09 s  →        1.10 s    (+0.60%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.10 ms →        4.13 ms   (+0.60%) |     266   →     266              |        1.09 s  →        1.10 s    (+0.60%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.05 ms →        4.06 ms   (+0.32%) |     114   →     114              |      461.75 ms →      463.24 ms   (+0.32%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        3.91 ms →        3.88 ms   (-0.88%) |     114   →     114              |      445.71 ms →      441.78 ms   (-0.88%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.13 ms →        4.05 ms   (-2.00%) |      38   →      38              |      156.94 ms →      153.81 ms   (-2.00%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      118.51 μs →      121.24 μs   (+2.31%) |      38   →      38              |        4.50 ms →        4.61 ms   (+2.31%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      114.97 μs →      117.62 μs   (+2.31%) |      38   →      38              |        4.37 ms →        4.47 ms   (+2.31%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.29 ms   (+3.39%) |       2   →       2              |       10.24 ms →       10.58 ms   (+3.39%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.30 ms →        4.14 ms   (-3.67%) |       6   →       6              |       25.81 ms →       24.87 ms   (-3.67%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.22 ms →        4.04 ms   (-4.20%) |       6   →       6              |       25.29 ms →       24.23 ms   (-4.20%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.22 ms →        4.04 ms   (-4.20%) |       6   →       6              |       25.29 ms →       24.23 ms   (-4.20%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.05 ms →        4.03 ms   (-0.43%) |       3   →       3              |       12.14 ms →       12.09 ms   (-0.43%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.00 ms →        3.84 ms   (-3.97%) |       3   →       3              |       12.00 ms →       11.52 ms   (-3.97%) | 
  ├ sirius::Periodic_function|inner                                     |        4.08 ms →        4.21 ms   (+3.15%) |       2   →       2              |        8.16 ms →        8.42 ms   (+3.15%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.07 ms →        4.16 ms   (+2.18%) |       2   →       2              |        8.15 ms →        8.33 ms   (+2.18%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.07 ms →        4.16 ms   (+2.18%) |       2   →       2              |        8.15 ms →        8.32 ms   (+2.18%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        3.93 ms →        3.89 ms   (-0.99%) |       1   →       1              |        3.93 ms →        3.89 ms   (-0.99%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        3.88 ms →        3.84 ms   (-1.03%) |       1   →       1              |        3.88 ms →        3.84 ms   (-1.03%) | 
  └ sirius::finalize                                                    |      432.11 ms →      464.70 ms   (+7.54%) |       1   →       1              |      432.11 ms →      464.70 ms   (+7.54%) | 
  ====================================================================================================================================================================================================
```
