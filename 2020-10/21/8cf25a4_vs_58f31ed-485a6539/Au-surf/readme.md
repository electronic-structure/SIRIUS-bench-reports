# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs 8cf25a48a521cee28df94fe46e001c67fed20f54
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      132.63 s  →      132.29 s    (-0.25%) |       1   →       1              |      132.63 s  →      132.29 s    (-0.25%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.64 s    (-0.51%) |       1   →       1              |        2.65 s  →        2.64 s    (-0.51%) | 
  ├ sirius::Simulation_context::initialize                              |        2.10 s  →        2.14 s    (+1.72%) |       1   →       1              |        2.10 s  →        2.14 s    (+1.72%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       32.25 ms →       97.46 ms (+202.22%) |       1   →       1              |       32.25 ms →       97.46 ms (+202.22%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |       75.77 ms →       47.39 ms  (-37.46%) |       1   →       1              |       75.77 ms →       47.39 ms  (-37.46%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       49.24 ms →       22.13 ms  (-55.06%) |       1   →       1              |       49.24 ms →       22.13 ms  (-55.06%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.48 ms →       25.20 ms   (-4.80%) |       1   →       1              |       26.48 ms →       25.20 ms   (-4.80%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.10 ms →       10.30 ms   (+1.90%) |       1   →       1              |       10.10 ms →       10.30 ms   (+1.90%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.35 ms →       14.88 ms   (-8.95%) |       1   →       1              |       16.35 ms →       14.88 ms   (-8.95%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.76 ms →       14.31 ms   (-9.22%) |       1   →       1              |       15.76 ms →       14.31 ms   (-9.22%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |       15.54 ms →       14.10 ms   (-9.29%) |       1   →       1              |       15.54 ms →       14.10 ms   (-9.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      205.40 μs →      195.83 μs   (-4.66%) |       1   →       1              |      205.40 μs →      195.83 μs   (-4.66%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.35 μs →        2.62 μs  (+11.77%) |       1   →       1              |        2.35 μs →        2.62 μs  (+11.77%) | 
  │ └ sirius::Simulation_context::update                                |        1.94 s  →        1.94 s    (-0.04%) |       1   →       1              |        1.94 s  →        1.94 s    (-0.04%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.71 ms →       13.07 ms   (+2.79%) |       1   →       1              |       12.71 ms →       13.07 ms   (+2.79%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.91 ms →        8.39 ms   (+6.08%) |       1   →       1              |        7.91 ms →        8.39 ms   (+6.08%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        4.78 ms →        4.66 ms   (-2.62%) |       1   →       1              |        4.78 ms →        4.66 ms   (-2.62%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        4.36 ms →        4.24 ms   (-2.71%) |       1   →       1              |        4.36 ms →        4.24 ms   (-2.71%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.04 ms   (-2.51%) |       1   →       1              |        4.14 ms →        4.04 ms   (-2.51%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      216.95 μs →      201.99 μs   (-6.89%) |       1   →       1              |      216.95 μs →      201.99 μs   (-6.89%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.23 μs →        1.20 μs   (-2.12%) |       1   →       1              |        1.23 μs →        1.20 μs   (-2.12%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       15.08 ms →       16.12 ms   (+6.85%) |       2   →       2              |       30.17 ms →       32.23 ms   (+6.85%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms →        1.09 ms   (+0.07%) |       2   →       2              |        2.18 ms →        2.18 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      952.63 μs →      954.47 μs   (+0.19%) |       1   →       1              |      952.63 μs →      954.47 μs   (+0.19%) | 
+ │   ├ sirius::Radial_integrals|vloc                                   |        5.75 ms →        5.13 ms  (-10.85%) |       2   →       2              |       11.51 ms →       10.26 ms  (-10.85%) | 
+ │   ├ sirius::Radial_integrals|beta                                   |        4.11 ms →        3.64 ms  (-11.31%) |       2   →       2              |        8.22 ms →        7.29 ms  (-11.31%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.77 ms →       15.64 ms   (-0.86%) |       4   →       4              |       63.09 ms →       62.55 ms   (-0.86%) | 
  │   ├ sddk::Gvec::init                                                |      158.08 ms →      159.38 ms   (+0.83%) |       2   →       2              |      316.16 ms →      318.77 ms   (+0.83%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      124.56 ms →      125.82 ms   (+1.01%) |       2   →       2              |      249.13 ms →      251.65 ms   (+1.01%) | 
+ │   ├ sddk::Gvec_shells                                               |      137.23 ms →      120.45 ms  (-12.23%) |       1   →       1              |      137.23 ms →      120.45 ms  (-12.23%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.03 ms   (-1.24%) |       1   →       1              |        1.04 ms →        1.03 ms   (-1.24%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      218.23 ms →      217.58 ms   (-0.30%) |       1   →       1              |      218.23 ms →      217.58 ms   (-0.30%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       25.68 ms →       25.57 ms   (-0.42%) |       1   →       1              |       25.68 ms →       25.57 ms   (-0.42%) | 
  │ ├ sirius::K_point::K_point                                          |        1.73 μs →        1.65 μs   (-4.48%) |       2   →       2              |        3.46 μs →        3.31 μs   (-4.48%) | 
  │ └ sirius::K_point_set::initialize                                   |       25.64 ms →       25.53 ms   (-0.42%) |       1   →       1              |       25.64 ms →       25.53 ms   (-0.42%) | 
  │   └ sirius::K_point::initialize                                     |       25.58 ms →       25.48 ms   (-0.40%) |       1   →       1              |       25.58 ms →       25.48 ms   (-0.40%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.17 ms →       19.11 ms   (-0.30%) |       1   →       1              |       19.17 ms →       19.11 ms   (-0.30%) | 
  │     │ └ sddk::Gvec::init                                            |        4.89 ms →        4.88 ms   (-0.24%) |       1   →       1              |        4.89 ms →        4.88 ms   (-0.24%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       12.29 μs →       10.15 μs  (-17.40%) |       1   →       1              |       12.29 μs →       10.15 μs  (-17.40%) | 
  │     └ sirius::K_point::update                                       |        4.13 ms →        4.09 ms   (-0.97%) |       1   →       1              |        4.13 ms →        4.09 ms   (-0.97%) | 
  │       └ sirius::Beta_projectors                                     |        1.74 ms →        1.69 ms   (-3.07%) |       1   →       1              |        1.74 ms →        1.69 ms   (-3.07%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      884.51 μs →      893.62 μs   (+1.03%) |       1   →       1              |      884.51 μs →      893.62 μs   (+1.03%) | 
  ├ sirius::Smooth_periodic_function                                    |        1.49 ms →        1.47 ms   (-1.12%) |       2   →       2              |        2.98 ms →        2.95 ms   (-1.12%) | 
  ├ sirius::Potential                                                   |       94.10 ms →       99.39 ms   (+5.62%) |       1   →       1              |       94.10 ms →       99.39 ms   (+5.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.48 ms →        2.46 ms   (-0.65%) |       6   →       6              |       14.88 ms →       14.79 ms   (-0.65%) | 
  │ └ sirius::Potential::update                                         |       78.88 ms →       84.23 ms   (+6.78%) |       1   →       1              |       78.88 ms →       84.23 ms   (+6.78%) | 
  │   └ sirius::Potential::generate_local_potential                     |       78.71 ms →       84.02 ms   (+6.75%) |       1   →       1              |       78.71 ms →       84.02 ms   (+6.75%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.17 ms →       56.86 ms   (+8.99%) |       1   →       1              |       52.17 ms →       56.86 ms   (+8.99%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       17.46 ms →       18.42 ms   (+5.51%) |       1   →       1              |       17.46 ms →       18.42 ms   (+5.51%) | 
  ├ sirius::Density                                                     |       74.94 ms →       76.21 ms   (+1.69%) |       1   →       1              |       74.94 ms →       76.21 ms   (+1.69%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.87 ms →        4.75 ms   (-2.43%) |       2   →       2              |        9.74 ms →        9.50 ms   (-2.43%) | 
  │ └ sirius::Density::update                                           |       65.18 ms →       66.68 ms   (+2.31%) |       1   →       1              |       65.18 ms →       66.68 ms   (+2.31%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       65.00 ms →       66.51 ms   (+2.33%) |       1   →       1              |       65.00 ms →       66.51 ms   (+2.33%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |        3.10 ms →        3.17 ms   (+2.22%) |       1   →       1              |        3.10 ms →        3.17 ms   (+2.22%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.20 ms →       57.61 ms   (+8.29%) |       1   →       1              |       53.20 ms →       57.61 ms   (+8.29%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.42 ms →        4.49 ms  (-39.45%) |       1   →       1              |        7.42 ms →        4.49 ms  (-39.45%) | 
  ├ sirius::Density::initial_density                                    |       78.40 ms →       78.86 ms   (+0.58%) |       1   →       1              |       78.40 ms →       78.86 ms   (+0.58%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       53.42 ms →       57.82 ms   (+8.24%) |       1   →       1              |       53.42 ms →       57.82 ms   (+8.24%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.62 ms →        2.55 ms  (-44.70%) |       2   →       2              |        9.24 ms →        5.11 ms  (-44.70%) | 
  │ └ sirius::Periodic_function::integrate                              |        3.96 ms →        4.35 ms   (+9.91%) |       1   →       1              |        3.96 ms →        4.35 ms   (+9.91%) | 
  ├ sirius::Potential::generate                                         |      186.80 ms →      185.44 ms   (-0.73%) |       1   →       1              |      186.80 ms →      185.44 ms   (-0.73%) | 
  │ ├ sirius::Potential::poisson                                        |       63.51 ms →       64.09 ms   (+0.92%) |       1   →       1              |       63.51 ms →       64.09 ms   (+0.92%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.30 ms →        2.80 ms  (-66.27%) |       1   →       1              |        8.30 ms →        2.80 ms  (-66.27%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.25 ms →        4.46 ms   (+4.91%) |       1   →       1              |        4.25 ms →        4.46 ms   (+4.91%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.04 ms →        4.45 ms   (+9.92%) |       1   →       1              |        4.04 ms →        4.45 ms   (+9.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.04 ms →        4.44 ms   (+9.92%) |       1   →       1              |        4.04 ms →        4.44 ms   (+9.92%) | 
  │ ├ sirius::Periodic_function::add                                    |      240.47 μs →      232.23 μs   (-3.43%) |       2   →       2              |      480.93 μs →      464.45 μs   (-3.43%) | 
  │ ├ sirius::Potential::xc                                             |       96.89 ms →       94.96 ms   (-1.99%) |       1   →       1              |       96.89 ms →       94.96 ms   (-1.99%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       95.84 ms →       93.94 ms   (-1.99%) |       1   →       1              |       95.84 ms →       93.94 ms   (-1.99%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.01 ms →        1.98 ms   (-1.71%) |       5   →       5              |       10.05 ms →        9.88 ms   (-1.71%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.38 ms →        2.37 ms   (-0.19%) |       9   →       9              |       21.40 ms →       21.36 ms   (-0.19%) | 
  │ │   ├ sirius::gradient                                              |        7.64 ms →        7.55 ms   (-1.23%) |       1   →       1              |        7.64 ms →        7.55 ms   (-1.23%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.46 ms →        2.41 ms   (-1.75%) |       3   →       3              |        7.37 ms →        7.24 ms   (-1.75%) | 
  │ │   ├ sirius::dot                                                   |        2.82 ms →        2.80 ms   (-0.87%) |       1   →       1              |        2.82 ms →        2.80 ms   (-0.87%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.57 ms →        2.56 ms   (-0.55%) |       1   →       1              |        2.57 ms →        2.56 ms   (-0.55%) | 
  │ │   └ sirius::divergence                                            |       21.28 ms →       19.71 ms   (-7.40%) |       1   →       1              |       21.28 ms →       19.71 ms   (-7.40%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.60 ms →        2.43 ms   (-6.58%) |       1   →       1              |        2.60 ms →        2.43 ms   (-6.58%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.18 ms →        3.20 ms   (+0.61%) |       1   →       1              |        3.18 ms →        3.20 ms   (+0.61%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.15 ms →       22.15 ms   (+0.02%) |       1   →       1              |       22.15 ms →       22.15 ms   (+0.02%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      289.00 ns →      134.00 ns  (-53.63%) |       1   →       1              |      289.00 ns →      134.00 ns  (-53.63%) | 
  ├ sirius::Hamiltonian0                                                |       14.25 ms →       13.70 ms   (-3.86%) |       1   →       1              |       14.25 ms →       13.70 ms   (-3.86%) | 
  │ ├ sirius::Local_operator                                            |       13.93 ms →       13.39 ms   (-3.92%) |       1   →       1              |       13.93 ms →       13.39 ms   (-3.92%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.78 ms →        7.13 ms   (-8.43%) |       1   →       1              |        7.78 ms →        7.13 ms   (-8.43%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.71 ms →        4.83 ms   (+2.51%) |       1   →       1              |        4.71 ms →        4.83 ms   (+2.51%) | 
  │ ├ sirius::Non_local_operator                                        |       59.38 μs →       60.27 μs   (+1.49%) |       2   →       2              |      118.77 μs →      120.54 μs   (+1.49%) | 
  │ ├ sirius::D_operator::initialize                                    |       78.92 μs →       74.53 μs   (-5.57%) |       1   →       1              |       78.92 μs →       74.53 μs   (-5.57%) | 
  │ └ sirius::Q_operator::initialize                                    |       65.71 μs →       64.48 μs   (-1.86%) |       1   →       1              |       65.71 μs →       64.48 μs   (-1.86%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.44 s  →        2.45 s    (+0.51%) |       1   →       1              |        2.44 s  →        2.45 s    (+0.51%) | 
  │ ├ sirius::Hamiltonian_k                                             |        8.35 ms →        8.35 ms   (+0.06%) |       1   →       1              |        8.35 ms →        8.35 ms   (+0.06%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      237.76 μs →      240.04 μs   (+0.96%) |       1   →       1              |      237.76 μs →      240.04 μs   (+0.96%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.11 ms →        8.11 ms   (+0.03%) |       1   →       1              |        8.11 ms →        8.11 ms   (+0.03%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.43 s  →        2.44 s    (+0.51%) |       1   →       1              |        2.43 s  →        2.44 s    (+0.51%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       88.55 ms →       86.58 ms   (-2.23%) |       4   →       4              |      354.21 ms →      346.31 ms   (-2.23%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.62 ms →       25.71 ms   (+0.35%) |       1   →       1              |       25.62 ms →       25.71 ms   (+0.35%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.73 ms →       14.67 ms   (-0.42%) |       1   →       1              |       14.73 ms →       14.67 ms   (-0.42%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.19 s  →        1.21 s    (+1.60%) |       1   →       1              |        1.19 s  →        1.21 s    (+1.60%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      968.45 ms →      987.68 ms   (+1.99%) |       1   →       1              |      968.45 ms →      987.68 ms   (+1.99%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      304.76 ms →      315.19 ms   (+3.42%) |       1   →       1              |      304.76 ms →      315.19 ms   (+3.42%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      177.79 ms →      175.55 ms   (-1.26%) |       1   →       1              |      177.79 ms →      175.55 ms   (-1.26%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      177.79 ms →      175.54 ms   (-1.26%) |       1   →       1              |      177.79 ms →      175.54 ms   (-1.26%) | 
- │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      108.50 ms →      121.18 ms  (+11.68%) |       1   →       1              |      108.50 ms →      121.18 ms  (+11.68%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      173.25 ms →      172.02 ms   (-0.71%) |       1   →       1              |      173.25 ms →      172.02 ms   (-0.71%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      173.25 ms →      172.01 ms   (-0.71%) |       1   →       1              |      173.25 ms →      172.01 ms   (-0.71%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      159.66 ms →      170.02 ms   (+6.49%) |       1   →       1              |      159.66 ms →      170.02 ms   (+6.49%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      108.99 ms →      119.53 ms   (+9.67%) |       1   →       1              |      108.99 ms →      119.53 ms   (+9.67%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.76 ms →        3.75 ms   (-0.31%) |       1   →       1              |        3.76 ms →        3.75 ms   (-0.31%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.07 ms →       88.85 ms   (-0.24%) |       1   →       1              |       89.07 ms →       88.85 ms   (-0.24%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.42 ms →       11.20 ms   (-1.94%) |       1   →       1              |       11.42 ms →       11.20 ms   (-1.94%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.21 ms →       64.22 ms   (+0.00%) |       2   →       2              |      128.43 ms →      128.43 ms   (+0.00%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |      188.03 ms →      190.88 ms   (+1.52%) |       2   →       2              |      376.06 ms →      381.76 ms   (+1.52%) | 
  │ │ │ └ sddk::wf_inner                                                |      187.93 ms →      190.78 ms   (+1.52%) |       2   →       2              |      375.85 ms →      381.56 ms   (+1.52%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       23.00 ns →       25.50 ns  (+10.87%) |       2   →       2              |       46.00 ns →       51.00 ns  (+10.87%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |      186.45 ms →      189.21 ms   (+1.48%) |       2   →       2              |      372.90 ms →      378.43 ms   (+1.48%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       38.50 ns (+102.63%) |       2   →       2              |       38.00 ns →       77.00 ns (+102.63%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.01 ms →      115.71 ms   (-0.27%) |       1   →       1              |      116.01 ms →      115.71 ms   (-0.27%) | 
  │ │ └ sddk::wf_trans                                                  |       35.68 ms →       35.90 ms   (+0.62%) |       1   →       1              |       35.68 ms →       35.90 ms   (+0.62%) | 
  │ │   └ sddk::wf_trans|pw                                             |       35.66 ms →       35.69 ms   (+0.08%) |       1   →       1              |       35.66 ms →       35.69 ms   (+0.08%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      723.00 ns →      527.00 ns  (-27.11%) |       1   →       1              |      723.00 ns →      527.00 ns  (-27.11%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.89 s  →      123.48 s    (-0.33%) |       1   →       1              |      123.89 s  →      123.48 s    (-0.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms →        2.14 ms   (-1.17%) |      31   →      31              |       67.28 ms →       66.49 ms   (-1.17%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.75 s  →        2.74 s    (-0.33%) |      45   →      45              |      123.53 s  →      123.12 s    (-0.33%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.55 ms →        7.10 ms   (-5.94%) |      45   →      45              |      339.71 ms →      319.53 ms   (-5.94%) | 
  │ │ │ ├ sirius::Local_operator                                        |        7.22 ms →        6.77 ms   (-6.14%) |      45   →      45              |      324.79 ms →      304.84 ms   (-6.14%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.46 ms →        1.49 ms   (+1.75%) |      45   →      45              |       65.87 ms →       67.02 ms   (+1.75%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.31 ms →        3.85 ms  (-10.72%) |      45   →      45              |      193.90 ms →      173.11 ms  (-10.72%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.45 μs →       60.90 μs   (-0.90%) |      90   →      90              |        5.53 ms →        5.48 ms   (-0.90%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       80.58 μs →       79.75 μs   (-1.03%) |      45   →      45              |        3.63 ms →        3.59 ms   (-1.03%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       68.21 μs →       65.86 μs   (-3.44%) |      45   →      45              |        3.07 ms →        2.96 ms   (-3.44%) | 
  │ │ ├ sirius::Band::solve                                             |        2.08 s  →        2.07 s    (-0.41%) |      45   →      45              |       93.47 s  →       93.09 s    (-0.41%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      206.16 μs →      205.52 μs   (-0.31%) |      45   →      45              |        9.28 ms →        9.25 ms   (-0.31%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.58 μs →      198.27 μs   (-0.16%) |      45   →      45              |        8.94 ms →        8.92 ms   (-0.16%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.56 μs →        5.31 μs   (-4.48%) |      45   →      45              |      250.05 μs →      238.85 μs   (-4.48%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.06 s  →        2.06 s    (-0.23%) |      45   →      45              |       92.85 s  →       92.64 s    (-0.23%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       55.78 ms →       55.69 ms   (-0.16%) |      45   →      45              |        2.51 s  →        2.51 s    (-0.16%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        3.97 ms →        3.89 ms   (-2.04%) |     270   →     270              |        1.07 s  →        1.05 s    (-2.04%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.90 ms →        1.62 ms  (-14.72%) |      45   →      45              |       85.28 ms →       72.73 ms  (-14.72%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      417.52 μs →      421.24 μs   (+0.89%) |      45   →      45              |       18.79 ms →       18.96 ms   (+0.89%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        1.20 ms →      940.39 μs  (-21.41%) |      45   →      45              |       53.85 ms →       42.32 ms  (-21.41%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.98 s  →        1.98 s    (-0.22%) |      45   →      45              |       89.17 s  →       88.97 s    (-0.22%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      192.19 ms →      192.05 ms   (-0.07%) |     245   →     245              |       47.09 s  →       47.05 s    (-0.07%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      135.61 ms →      135.54 ms   (-0.05%) |     245   →     245              |       33.23 s  →       33.21 s    (-0.05%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       24.64 ms →       24.61 ms   (-0.12%) |     245   →     245              |        6.04 s  →        6.03 s    (-0.12%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      567.70 μs →      556.34 μs   (-2.00%) |     245   →     245              |      139.09 ms →      136.30 ms   (-2.00%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.08 ms →        3.02 ms   (-1.97%) |      45   →      45              |      138.52 ms →      135.79 ms   (-1.97%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       19.98 ms →       20.03 ms   (+0.26%) |     245   →     245              |        4.89 s  →        4.91 s    (+0.26%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      569.54 μs →      562.34 μs   (-1.26%) |     245   →     245              |      139.54 ms →      137.77 ms   (-1.26%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.09 ms →        3.05 ms   (-1.19%) |      45   →      45              |      138.86 ms →      137.20 ms   (-1.19%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       30.32 ms →       30.52 ms   (+0.66%) |     245   →     245              |        7.43 s  →        7.48 s    (+0.66%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       18.89 ms →       19.12 ms   (+1.21%) |     245   →     245              |        4.63 s  →        4.68 s    (+1.21%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.61 ms →        2.61 ms   (+0.12%) |     245   →     245              |      639.69 ms →      640.46 ms   (+0.12%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.10 ms →       20.10 ms   (+0.01%) |     245   →     245              |        4.92 s  →        4.92 s    (+0.01%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.98 ms →        1.98 ms   (-0.31%) |     245   →     245              |      485.49 ms →      483.99 ms   (-0.31%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       16.92 ms →       16.88 ms   (-0.22%) |     490   →     490              |        8.29 s  →        8.27 s    (-0.22%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       51.99 ms →       51.95 ms   (-0.09%) |     245   →     245              |       12.74 s  →       12.73 s    (-0.09%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |       12.17 ms →       12.14 ms   (-0.23%) |     445   →     445              |        5.42 s  →        5.40 s    (-0.23%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       62.81 ns →       61.10 ns   (-2.73%) |     445   →     445              |       27.95 μs →       27.19 μs   (-2.73%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        8.52 ms →        8.48 ms   (-0.41%) |     445   →     445              |        3.79 s  →        3.77 s    (-0.41%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       57.89 ns →       69.61 ns  (+20.25%) |     445   →     445              |       25.76 μs →       30.98 μs  (+20.25%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        2.93 ms →        2.94 ms   (+0.35%) |     245   →     245              |      718.78 ms →      721.28 ms   (+0.35%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       14.32 ms →       14.32 ms   (+0.02%) |     245   →     245              |        3.51 s  →        3.51 s    (+0.02%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       15.47 ms →       15.45 ms   (-0.08%) |     200   →     200              |        3.09 s  →        3.09 s    (-0.08%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        5.12 ms →        5.12 ms   (-0.01%) |     600   →     600              |        3.07 s  →        3.07 s    (-0.01%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       19.64 ms →       19.40 ms   (-1.22%) |     245   →     245              |        4.81 s  →        4.75 s    (-1.22%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       18.24 ms →       18.04 ms   (-1.09%) |     245   →     245              |        4.47 s  →        4.42 s    (-1.09%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       72.06 ns →       68.96 ns   (-4.30%) |     245   →     245              |       17.65 μs →       16.89 μs   (-4.30%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |       14.47 ms →       14.47 ms   (+0.03%) |     245   →     245              |        3.54 s  →        3.55 s    (+0.03%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       20.94 ns →       31.81 ns  (+51.90%) |     245   →     245              |        5.13 μs →        7.79 μs  (+51.90%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       69.27 ms →       68.13 ms   (-1.66%) |     245   →     245              |       16.97 s  →       16.69 s    (-1.66%) | 
  │ │ │ │   ├ sirius::residuals                                         |       15.88 ms →       16.50 ms   (+3.91%) |     239   →     239              |        3.80 s  →        3.94 s    (+3.91%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       16.17 ms →       16.89 ms   (+4.46%) |     208   →     208              |        3.36 s  →        3.51 s    (+4.46%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        7.57 ms →        7.57 ms   (-0.02%) |     416   →     416              |        3.15 s  →        3.15 s    (-0.02%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.42 ms →        1.41 ms   (-0.57%) |     208   →     208              |      295.10 ms →      293.41 ms   (-0.57%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       62.60 ms →       63.24 ms   (+1.03%) |      60   →      60              |        3.76 s  →        3.79 s    (+1.03%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       49.54 ms →       50.06 ms   (+1.05%) |      75   →      75              |        3.72 s  →        3.75 s    (+1.05%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       40.67 ms →       40.67 ms   (-0.01%) |      90   →      90              |        3.66 s  →        3.66 s    (-0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      560.33 ns →      536.60 ns   (-4.24%) |      45   →      45              |       25.21 μs →       24.15 μs   (-4.24%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.43 μs →       23.87 μs   (+1.88%) |      45   →      45              |        1.05 ms →        1.07 ms   (+1.88%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.52 ms →        3.47 ms   (-1.35%) |      45   →      45              |      158.20 ms →      156.06 ms   (-1.35%) | 
  │ │ ├ sirius::Density::generate                                       |      293.89 ms →      292.55 ms   (-0.46%) |      45   →      45              |       13.23 s  →       13.16 s    (-0.46%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      289.96 ms →      288.67 ms   (-0.44%) |      45   →      45              |       13.05 s  →       12.99 s    (-0.44%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       66.79 ms →       65.86 ms   (-1.39%) |      45   →      45              |        3.01 s  →        2.96 s    (-1.39%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       59.28 μs →       54.93 μs   (-7.34%) |      45   →      45              |        2.67 ms →        2.47 ms   (-7.34%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.17 ms →        1.15 ms   (-0.95%) |       2   →       2              |        2.33 ms →        2.31 ms   (-0.95%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.30 ms →       54.45 ms   (-1.54%) |      45   →      45              |        2.49 s  →        2.45 s    (-1.54%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       59.72 ms →       59.84 ms   (+0.19%) |      45   →      45              |        2.69 s  →        2.69 s    (+0.19%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.41 μs →       11.04 μs  (+17.40%) |      45   →      45              |      423.32 μs →      496.99 μs  (+17.40%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.32 ms →        2.31 ms   (-0.29%) |      45   →      45              |      104.21 ms →      103.91 ms   (-0.29%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       56.86 ms →       56.99 ms   (+0.24%) |      45   →      45              |        2.56 s  →        2.56 s    (+0.24%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.44 ms →        5.56 ms   (+2.25%) |      45   →      45              |      244.88 ms →      250.38 ms   (+2.25%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      795.98 ns →      740.11 ns   (-7.02%) |      45   →      45              |       35.82 μs →       33.30 μs   (-7.02%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.60 ms →      104.14 ms   (-0.44%) |      45   →      45              |        4.71 s  →        4.69 s    (-0.44%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.46 ms →        2.41 ms   (-2.05%) |      45   →      45              |      110.57 ms →      108.31 ms   (-2.05%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.05 ms →       20.06 ms   (+0.04%) |      45   →      45              |      902.18 ms →      902.54 ms   (+0.04%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.88 ms →       19.90 ms   (+0.07%) |      45   →      45              |      894.68 ms →      895.29 ms   (+0.07%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      308.24 ns →      289.16 ns   (-6.19%) |      45   →      45              |       13.87 μs →       13.01 μs   (-6.19%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms →        1.26 ms   (+0.51%) |      45   →      45              |       56.30 ms →       56.59 ms   (+0.51%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.68 ms →        2.62 ms   (-2.49%) |      45   →      45              |      120.82 ms →      117.81 ms   (-2.49%) | 
  │ │ ├ sirius::Density::mix                                            |      132.14 ms →      133.40 ms   (+0.96%) |      45   →      45              |        5.95 s  →        6.00 s    (+0.96%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      246.00 μs →      253.70 μs   (+3.13%) |      45   →      45              |       11.07 ms →       11.42 ms   (+3.13%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        2.62 ms →        2.55 ms   (-2.58%) |      45   →      45              |      117.96 ms →      114.91 ms   (-2.58%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        2.43 ms →        2.37 ms   (-2.80%) |      45   →      45              |      109.57 ms →      106.51 ms   (-2.80%) | 
  │ │ ├ sirius::Potential::generate                                     |      181.61 ms →      178.83 ms   (-1.53%) |      45   →      45              |        8.17 s  →        8.05 s    (-1.53%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.07 ms →       64.03 ms   (-0.07%) |      45   →      45              |        2.88 s  →        2.88 s    (-0.07%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.80 ms →        2.76 ms  (-68.65%) |      45   →      45              |      395.78 ms →      124.08 ms  (-68.65%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.59 ms →        4.42 ms   (-3.74%) |      45   →      45              |      206.62 ms →      198.89 ms   (-3.74%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.09 ms →        4.29 ms   (+4.85%) |      45   →      45              |      184.22 ms →      193.16 ms   (+4.85%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.09 ms →        4.29 ms   (+4.85%) |      45   →      45              |      184.19 ms →      193.13 ms   (+4.85%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      229.69 μs →      230.59 μs   (+0.39%) |      90   →      90              |       20.67 ms →       20.75 ms   (+0.39%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       92.31 ms →       89.65 ms   (-2.89%) |      45   →      45              |        4.15 s  →        4.03 s    (-2.89%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       91.31 ms →       88.62 ms   (-2.94%) |      45   →      45              |        4.11 s  →        3.99 s    (-2.94%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.59 ms →        1.59 ms   (-0.08%) |     225   →     225              |      357.48 ms →      357.18 ms   (-0.08%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.52 ms →        2.43 ms   (-3.28%) |     405   →     405              |        1.02 s  →      985.87 ms   (-3.28%) | 
  │ │ │ │   ├ sirius::gradient                                          |        2.39 ms →        2.46 ms   (+2.90%) |      45   →      45              |      107.76 ms →      110.89 ms   (+2.90%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      703.59 μs →      725.28 μs   (+3.08%) |     135   →     135              |       94.98 ms →       97.91 ms   (+3.08%) | 
  │ │ │ │   ├ sirius::dot                                               |        2.88 ms →        2.83 ms   (-1.54%) |      45   →      45              |      129.52 ms →      127.53 ms   (-1.54%) | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.63 ms →        2.59 ms   (-1.50%) |      45   →      45              |      118.54 ms →      116.76 ms   (-1.50%) | 
  │ │ │ │   └ sirius::divergence                                        |       20.77 ms →       18.94 ms   (-8.83%) |      45   →      45              |      934.74 ms →      852.17 ms   (-8.83%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.43 ms →        2.45 ms   (+0.80%) |      45   →      45              |      109.53 ms →      110.41 ms   (+0.80%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.31 ms →        3.28 ms   (-0.94%) |      45   →      45              |      148.97 ms →      147.57 ms   (-0.94%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.90 ms →       20.88 ms   (-0.08%) |      45   →      45              |      940.38 ms →      939.66 ms   (-0.08%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      282.44 ns →      160.00 ns  (-43.35%) |      45   →      45              |       12.71 μs →        7.20 μs  (-43.35%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      296.36 ns →      288.13 ns   (-2.77%) |      45   →      45              |       13.34 μs →       12.97 μs   (-2.77%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.25 ms →        2.24 ms   (-0.37%) |      45   →      45              |      101.23 ms →      100.85 ms   (-0.37%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.18 ms →        4.77 ms  (+14.24%) |     315   →     315              |        1.32 s  →        1.50 s   (+14.24%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        3.99 ms →        4.47 ms  (+12.10%) |     315   →     315              |        1.26 s  →        1.41 s   (+12.10%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.99 ms →        4.47 ms  (+12.10%) |     315   →     315              |        1.26 s  →        1.41 s   (+12.10%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.45 ms →        4.02 ms   (-9.70%) |     135   →     135              |      600.98 ms →      542.68 ms   (-9.70%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.22 ms →        3.90 ms   (-7.48%) |     135   →     135              |      569.52 ms →      526.92 ms   (-7.48%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.06 ms →        4.01 ms   (-1.28%) |      45   →      45              |      182.66 ms →      180.31 ms   (-1.28%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      129.96 μs →       98.24 μs  (-24.41%) |      45   →      45              |        5.85 ms →        4.42 ms  (-24.41%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      126.45 μs →       94.87 μs  (-24.97%) |      45   →      45              |        5.69 ms →        4.27 ms  (-24.97%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.35 ms →        5.25 ms   (-1.78%) |       2   →       2              |       10.69 ms →       10.50 ms   (-1.78%) | 
- │ ├ sirius::Periodic_function|inner                                   |        4.04 ms →        4.69 ms  (+16.01%) |       6   →       6              |       24.24 ms →       28.12 ms  (+16.01%) | 
- │ │ └ sirius::Periodic_function|inner_local                           |        3.97 ms →        4.64 ms  (+16.88%) |       6   →       6              |       23.82 ms →       27.84 ms  (+16.88%) | 
- │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.97 ms →        4.64 ms  (+16.88%) |       6   →       6              |       23.82 ms →       27.84 ms  (+16.88%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.31 ms →        4.26 ms   (-0.96%) |       3   →       3              |       12.92 ms →       12.79 ms   (-0.96%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.29 ms →        4.15 ms   (-3.20%) |       3   →       3              |       12.86 ms →       12.45 ms   (-3.20%) | 
- ├ sirius::Periodic_function|inner                                     |        3.94 ms →        4.66 ms  (+18.32%) |       2   →       2              |        7.88 ms →        9.32 ms  (+18.32%) | 
- │ └ sirius::Periodic_function|inner_local                             |        3.93 ms →        4.61 ms  (+17.44%) |       2   →       2              |        7.86 ms →        9.23 ms  (+17.44%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        3.93 ms →        4.61 ms  (+17.44%) |       2   →       2              |        7.86 ms →        9.23 ms  (+17.44%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.28 ms →        4.01 ms   (-6.21%) |       1   →       1              |        4.28 ms →        4.01 ms   (-6.21%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.26 ms →        4.00 ms   (-6.21%) |       1   →       1              |        4.26 ms →        4.00 ms   (-6.21%) | 
- └ sirius::finalize                                                    |      268.81 ms →      299.27 ms  (+11.33%) |       1   →       1              |      268.81 ms →      299.27 ms  (+11.33%) | 
  ====================================================================================================================================================================================================
```
