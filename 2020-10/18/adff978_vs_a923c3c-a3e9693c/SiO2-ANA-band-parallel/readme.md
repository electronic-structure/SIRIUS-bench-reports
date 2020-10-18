# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      243.36 s  →      223.56 s    (-8.13%) |       1   →       1              |      243.36 s  →      223.56 s    (-8.13%) | 
  ├ sirius::initialize                                                  |        2.67 s  →        2.71 s    (+1.49%) |       1   →       1              |        2.67 s  →        2.71 s    (+1.49%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        2.91 s    (-2.09%) |       1   →       1              |        2.97 s  →        2.91 s    (-2.09%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       34.98 ms →       13.91 ms  (-60.24%) |       1   →       1              |       34.98 ms →       13.91 ms  (-60.24%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      176.25 ms →      137.80 ms  (-21.81%) |       1   →       1              |      176.25 ms →      137.80 ms  (-21.81%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       76.60 ms →       57.54 ms  (-24.89%) |       2   →       2              |      153.21 ms →      115.08 ms  (-24.89%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.96 ms →       22.65 ms   (-1.35%) |       1   →       1              |       22.96 ms →       22.65 ms   (-1.35%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.30 ms →        6.26 ms   (-0.53%) |       1   →       1              |        6.30 ms →        6.26 ms   (-0.53%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.62 ms →       16.35 ms   (-1.66%) |       1   →       1              |       16.62 ms →       16.35 ms   (-1.66%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.60 ms →       16.33 ms   (-1.67%) |       1   →       1              |       16.60 ms →       16.33 ms   (-1.67%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (-0.04%) |       1   →       1              |        4.16 ms →        4.16 ms   (-0.04%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.59%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.59%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.04 μs →      102.12 μs   (+1.07%) |       1   →       1              |      101.04 μs →      102.12 μs   (+1.07%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.71 s    (+0.09%) |       1   →       1              |        2.71 s  →        2.71 s    (+0.09%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.88 ms →       10.79 ms   (-0.77%) |       1   →       1              |       10.88 ms →       10.79 ms   (-0.77%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.43 ms   (-0.00%) |       1   →       1              |        4.43 ms →        4.43 ms   (-0.00%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.42 ms →        6.33 ms   (-1.32%) |       1   →       1              |        6.42 ms →        6.33 ms   (-1.32%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.40 ms →        6.31 ms   (-1.31%) |       1   →       1              |        6.40 ms →        6.31 ms   (-1.31%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.91 ms →        3.82 ms   (-2.23%) |       1   →       1              |        3.91 ms →        3.82 ms   (-2.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.31 ms   (-0.55%) |       1   →       1              |        2.32 ms →        2.31 ms   (-0.55%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.55 μs →       99.16 μs   (-1.38%) |       1   →       1              |      100.55 μs →       99.16 μs   (-1.38%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.57 ms →       63.76 ms   (+1.91%) |       2   →       2              |      125.13 ms →      127.52 ms   (+1.91%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.21 ms   (+1.15%) |       2   →       2              |       10.31 ms →       10.43 ms   (+1.15%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.15%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.15%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.74 ms →       21.72 ms   (-0.10%) |       2   →       2              |       43.48 ms →       43.44 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.83 ms   (-0.12%) |       2   →       2              |       29.70 ms →       29.67 ms   (-0.12%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.85 ms →       19.85 ms   (+0.03%) |       4   →       4              |       79.39 ms →       79.41 ms   (+0.03%) | 
  │   ├ sddk::Gvec::init                                                |      180.09 ms →      174.94 ms   (-2.86%) |       2   →       2              |      360.19 ms →      349.89 ms   (-2.86%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      137.19 ms →      130.28 ms   (-5.04%) |       2   →       2              |      274.39 ms →      260.57 ms   (-5.04%) | 
  │   ├ sddk::Gvec_shells                                               |      178.55 ms →      177.49 ms   (-0.59%) |       1   →       1              |      178.55 ms →      177.49 ms   (-0.59%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (+0.37%) |       1   →       1              |        1.32 ms →        1.32 ms   (+0.37%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.87 ms →      302.14 ms   (+2.47%) |       2   →       2              |      589.73 ms →      604.28 ms   (+2.47%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       80.15 ms →       74.19 ms   (-7.43%) |       1   →       1              |       80.15 ms →       74.19 ms   (-7.43%) | 
- │ ├ sirius::K_point::K_point                                          |        2.34 μs →        2.76 μs  (+17.97%) |       4   →       4              |        9.35 μs →       11.03 μs  (+17.97%) | 
  │ └ sirius::K_point_set::initialize                                   |       80.04 ms →       74.10 ms   (-7.43%) |       1   →       1              |       80.04 ms →       74.10 ms   (-7.43%) | 
  │   └ sirius::K_point::initialize                                     |       20.00 ms →       18.50 ms   (-7.48%) |       4   →       4              |       80.00 ms →       74.01 ms   (-7.48%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.31 ms →       13.94 ms   (-8.94%) |       4   →       4              |       61.24 ms →       55.76 ms   (-8.94%) | 
  │     │ └ sddk::Gvec::init                                            |        3.99 ms →        3.87 ms   (-2.92%) |       4   →       4              |       15.94 ms →       15.48 ms   (-2.92%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.18 μs →        9.34 μs   (+1.73%) |       4   →       4              |       36.72 μs →       37.35 μs   (+1.73%) | 
  │     └ sirius::K_point::update                                       |        3.34 ms →        3.28 ms   (-1.60%) |       4   →       4              |       13.35 ms →       13.13 ms   (-1.60%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.78 ms   (+0.89%) |       4   →       4              |        7.06 ms →        7.12 ms   (+0.89%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      937.15 μs →      951.94 μs   (+1.58%) |       4   →       4              |        3.75 ms →        3.81 ms   (+1.58%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.19 ms →        5.28 ms   (+1.70%) |       2   →       2              |       10.38 ms →       10.56 ms   (+1.70%) | 
  ├ sirius::Potential                                                   |      160.42 ms →      159.28 ms   (-0.71%) |       1   →       1              |      160.42 ms →      159.28 ms   (-0.71%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.89 ms   (+1.63%) |       6   →       6              |       34.75 ms →       35.32 ms   (+1.63%) | 
  │ └ sirius::Potential::update                                         |      124.98 ms →      123.23 ms   (-1.40%) |       1   →       1              |      124.98 ms →      123.23 ms   (-1.40%) | 
  │   └ sirius::Potential::generate_local_potential                     |      124.25 ms →      122.44 ms   (-1.46%) |       1   →       1              |      124.25 ms →      122.44 ms   (-1.46%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.48 ms →      109.42 ms   (-1.85%) |       1   →       1              |      111.48 ms →      109.42 ms   (-1.85%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       11.88 ms →       12.14 ms   (+2.13%) |       1   →       1              |       11.88 ms →       12.14 ms   (+2.13%) | 
  ├ sirius::Density                                                     |      134.57 ms →      136.44 ms   (+1.39%) |       1   →       1              |      134.57 ms →      136.44 ms   (+1.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.16 ms →        5.20 ms   (+0.83%) |       2   →       2              |       10.32 ms →       10.40 ms   (+0.83%) | 
  │ └ sirius::Density::update                                           |      123.99 ms →      125.77 ms   (+1.44%) |       1   →       1              |      123.99 ms →      125.77 ms   (+1.44%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.56 ms →      125.33 ms   (+1.43%) |       1   →       1              |      123.56 ms →      125.33 ms   (+1.43%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.77 μs →      106.17 μs   (+3.30%) |       1   →       1              |      102.77 μs →      106.17 μs   (+3.30%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.82 ms →      110.78 ms   (-1.80%) |       1   →       1              |      112.82 ms →      110.78 ms   (-1.80%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       10.20 ms →       13.98 ms  (+37.10%) |       1   →       1              |       10.20 ms →       13.98 ms  (+37.10%) | 
  ├ sirius::Density::initial_density                                    |      177.89 ms →      176.85 ms   (-0.59%) |       1   →       1              |      177.89 ms →      176.85 ms   (-0.59%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.54 ms →      109.09 ms   (-2.20%) |       1   →       1              |      111.54 ms →      109.09 ms   (-2.20%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.74 ms →       12.56 ms  (+16.96%) |       2   →       2              |       21.47 ms →       25.11 ms  (+16.96%) | 
+ │ └ sirius::Periodic_function::integrate                              |       12.48 ms →       10.19 ms  (-18.38%) |       1   →       1              |       12.48 ms →       10.19 ms  (-18.38%) | 
  ├ sirius::Potential::generate                                         |      592.51 ms →      594.34 ms   (+0.31%) |       1   →       1              |      592.51 ms →      594.34 ms   (+0.31%) | 
  │ ├ sirius::Potential::poisson                                        |      136.47 ms →      138.03 ms   (+1.15%) |       1   →       1              |      136.47 ms →      138.03 ms   (+1.15%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       15.68 ms →       19.44 ms  (+24.00%) |       1   →       1              |       15.68 ms →       19.44 ms  (+24.00%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.34 ms →       10.21 ms   (-1.27%) |       1   →       1              |       10.34 ms →       10.21 ms   (-1.27%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.89 ms   (+0.08%) |       1   →       1              |        9.89 ms →        9.89 ms   (+0.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →        9.89 ms   (+0.08%) |       1   →       1              |        9.89 ms →        9.89 ms   (+0.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      545.56 μs →      551.05 μs   (+1.01%) |       2   →       2              |        1.09 ms →        1.10 ms   (+1.01%) | 
  │ ├ sirius::Potential::xc                                             |       56.04 ms →       53.77 ms   (-4.04%) |       1   →       1              |       56.04 ms →       53.77 ms   (-4.04%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.76 ms →       51.36 ms   (-4.46%) |       1   →       1              |       53.76 ms →       51.36 ms   (-4.46%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.61 ms →        5.73 ms   (+2.11%) |       2   →       2              |       11.23 ms →       11.47 ms   (+2.11%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        6.19 ms →        5.18 ms  (-16.33%) |       1   →       1              |        6.19 ms →        5.18 ms  (-16.33%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.60 ms →        5.79 ms   (+3.34%) |       1   →       1              |        5.60 ms →        5.79 ms   (+3.34%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.71 ms →       92.82 ms   (+0.12%) |       1   →       1              |       92.71 ms →       92.82 ms   (+0.12%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.28 ms →      301.44 ms   (+0.72%) |       1   →       1              |      299.28 ms →      301.44 ms   (+0.72%) | 
  ├ sirius::Hamiltonian0                                                |        8.37 ms →        8.39 ms   (+0.27%) |       1   →       1              |        8.37 ms →        8.39 ms   (+0.27%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        8.04 ms   (+0.09%) |       1   →       1              |        8.03 ms →        8.04 ms   (+0.09%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.78 ms   (+0.57%) |       1   →       1              |        4.75 ms →        4.78 ms   (+0.57%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.32 ms   (-1.52%) |       1   →       1              |        2.36 ms →        2.32 ms   (-1.52%) | 
  │ ├ sirius::Non_local_operator                                        |       62.40 μs →       61.69 μs   (-1.13%) |       2   →       2              |      124.80 μs →      123.38 μs   (-1.13%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.31 μs →       99.62 μs   (+5.63%) |       1   →       1              |       94.31 μs →       99.62 μs   (+5.63%) | 
  │ └ sirius::Q_operator::initialize                                    |       68.07 μs →       73.04 μs   (+7.30%) |       1   →       1              |       68.07 μs →       73.04 μs   (+7.30%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.10 s  →        3.11 s    (+0.55%) |       1   →       1              |        3.10 s  →        3.11 s    (+0.55%) | 
  │ ├ sirius::Hamiltonian_k                                             |      362.51 μs →      373.32 μs   (+2.98%) |       4   →       4              |        1.45 ms →        1.49 ms   (+2.98%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      357.69 μs →      367.58 μs   (+2.77%) |       4   →       4              |        1.43 ms →        1.47 ms   (+2.77%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |        3.06 μs →        3.74 μs  (+22.00%) |       4   →       4              |       12.26 μs →       14.95 μs  (+22.00%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      773.80 ms →      778.08 ms   (+0.55%) |       4   →       4              |        3.10 s  →        3.11 s    (+0.55%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.77 ms →       32.79 ms   (+0.06%) |      16   →      16              |      524.27 ms →      524.60 ms   (+0.06%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.52 ms →       14.38 ms   (-0.97%) |       4   →       4              |       58.07 ms →       57.51 ms   (-0.97%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.36 ms →        5.30 ms   (-1.02%) |       4   →       4              |       21.44 ms →       21.22 ms   (-1.02%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      350.50 ms →      355.51 ms   (+1.43%) |       4   →       4              |        1.40 s  →        1.42 s    (+1.43%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      253.92 ms →      258.43 ms   (+1.78%) |       4   →       4              |        1.02 s  →        1.03 s    (+1.78%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       61.60 ms →       63.34 ms   (+2.81%) |       4   →       4              |      246.42 ms →      253.35 ms   (+2.81%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.49 ms →       16.54 ms   (+0.30%) |       4   →       4              |       65.96 ms →       66.16 ms   (+0.30%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.49 ms →       16.54 ms   (+0.30%) |       4   →       4              |       65.96 ms →       66.15 ms   (+0.30%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       38.64 ms →       40.32 ms   (+4.34%) |       4   →       4              |      154.57 ms →      161.28 ms   (+4.34%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.47 ms →       16.51 ms   (+0.25%) |       4   →       4              |       65.86 ms →       66.03 ms   (+0.25%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.46 ms →       16.50 ms   (+0.25%) |       4   →       4              |       65.85 ms →       66.02 ms   (+0.25%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.05 ms →       53.05 ms   (+1.93%) |       4   →       4              |      208.19 ms →      212.20 ms   (+1.93%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       33.98 ms →       34.98 ms   (+2.95%) |       4   →       4              |      135.90 ms →      139.91 ms   (+2.95%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.94 ms   (-0.04%) |       4   →       4              |        7.78 ms →        7.78 ms   (-0.04%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.46 ms →       40.80 ms   (+0.82%) |       4   →       4              |      161.85 ms →      163.18 ms   (+0.82%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.39 ms →        7.63 ms   (+3.26%) |       4   →       4              |       29.55 ms →       30.52 ms   (+3.26%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.07 ms →       27.15 ms   (+0.29%) |       8   →       8              |      216.55 ms →      217.17 ms   (+0.29%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.32 ms →       15.19 ms   (-0.90%) |       8   →       8              |      122.59 ms →      121.49 ms   (-0.90%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.28 ms →       15.14 ms   (-0.88%) |       8   →       8              |      122.20 ms →      121.13 ms   (-0.88%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       27.88 ns →       35.13 ns  (+26.01%) |       8   →       8              |      223.00 ns →      281.00 ns  (+26.01%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.10 ms →       14.97 ms   (-0.86%) |       8   →       8              |      120.78 ms →      119.74 ms   (-0.86%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.00 ns →       36.50 ns  (+65.91%) |       8   →       8              |      176.00 ns →      292.00 ns  (+65.91%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      123.12 ms →      123.11 ms   (-0.00%) |       4   →       4              |      492.46 ms →      492.45 ms   (-0.00%) | 
  │ │ └ sddk::wf_trans                                                  |       23.97 ms →       23.51 ms   (-1.93%) |       4   →       4              |       95.89 ms →       94.04 ms   (-1.93%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.83 ms →       23.28 ms   (-2.29%) |       4   →       4              |       95.30 ms →       93.12 ms   (-2.29%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      497.75 ns →      330.75 ns  (-33.55%) |       4   →       4              |        1.99 μs →        1.32 μs  (-33.55%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      232.62 s  →      212.84 s    (-8.50%) |       1   →       1              |      232.62 s  →      212.84 s    (-8.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.80 ms   (+1.53%) |      19   →      19              |      108.59 ms →      110.26 ms   (+1.53%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.93 s  →        7.87 s   (-11.88%) |      26   →      27     (+3.85%) |      232.24 s  →      212.52 s    (-8.49%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.65 ms →        4.42 ms   (-4.91%) |      26   →      27     (+3.85%) |      120.84 ms →      119.33 ms   (-1.25%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.29 ms →        4.06 ms   (-5.31%) |      26   →      27     (+3.85%) |      111.55 ms →      109.70 ms   (-1.66%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      985.79 μs →      966.56 μs   (-1.95%) |      26   →      27     (+3.85%) |       25.63 ms →       26.10 ms   (+1.82%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.21 ms   (-8.63%) |      26   →      27     (+3.85%) |       62.85 ms →       59.63 ms   (-5.11%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.62 μs →       64.48 μs   (-0.21%) |      52   →      54     (+3.85%) |        3.36 ms →        3.48 ms   (+3.63%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.14 μs →       93.73 μs   (+0.64%) |      26   →      27     (+3.85%) |        2.42 ms →        2.53 ms   (+4.51%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.38 μs →       65.49 μs   (-1.34%) |      26   →      27     (+3.85%) |        1.73 ms →        1.77 ms   (+2.45%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.84 s  →        5.78 s   (-15.42%) |      26   →      27     (+3.85%) |      177.78 s  →      156.14 s   (-12.17%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      337.63 μs →      338.65 μs   (+0.30%) |     104   →     108     (+3.85%) |       35.11 ms →       36.57 ms   (+4.16%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      332.21 μs →      333.36 μs   (+0.35%) |     104   →     108     (+3.85%) |       34.55 ms →       36.00 ms   (+4.21%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.83 μs →        3.77 μs   (-1.49%) |     104   →     108     (+3.85%) |      398.36 μs →      407.53 μs   (+2.30%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.71 s  →        1.45 s   (-15.43%) |     104   →     108     (+3.85%) |      177.74 s  →      156.10 s   (-12.17%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.05 ms →       11.96 ms   (-0.81%) |     104   →     108     (+3.85%) |        1.25 s  →        1.29 s    (+3.00%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      694.13 ns →      657.71 ns   (-5.25%) |     624   →     648     (+3.85%) |      433.14 μs →      426.20 μs   (-1.60%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.83 ms   (-0.34%) |     104   →     108     (+3.85%) |      190.98 ms →      197.66 ms   (+3.50%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.88 μs →      354.27 μs   (+0.68%) |     104   →     108     (+3.85%) |       36.60 ms →       38.26 ms   (+4.55%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      552.47 μs →      549.46 μs   (-0.55%) |     208   →     216     (+3.85%) |      114.91 ms →      118.68 ms   (+3.28%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.69 s  →        1.42 s   (-15.63%) |     104   →     108     (+3.85%) |      175.36 s  →      153.64 s   (-12.39%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       67.19 ms →       66.73 ms   (-0.68%) |     934   →    1.00 K   (+7.28%) |       62.76 s  →       66.87 s    (+6.55%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.59 ms →       42.47 ms   (-0.30%) |     934   →    1.00 K   (+7.28%) |       39.78 s  →       42.55 s    (+6.96%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.16 ms →        8.42 ms   (+3.25%) |     934   →    1.00 K   (+7.28%) |        7.62 s  →        8.44 s   (+10.77%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      223.00 μs →      215.88 μs   (-3.20%) |     934   →    1.00 K   (+7.28%) |      208.29 ms →      216.31 ms   (+3.85%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.99 ms →        1.99 ms   (+0.00%) |     104   →     108     (+3.85%) |      206.47 ms →      214.41 ms   (+3.85%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.36 ms →        6.48 ms   (+1.77%) |     934   →    1.00 K   (+7.28%) |        5.94 s  →        6.49 s    (+9.18%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       86.00 μs →       82.56 μs   (-3.99%) |     934   →    1.00 K   (+7.28%) |       80.32 ms →       82.73 ms   (+3.00%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      749.26 μs →      741.68 μs   (-1.01%) |     104   →     108     (+3.85%) |       77.92 ms →       80.10 ms   (+2.80%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.11 ms →        9.34 ms   (+2.55%) |     934   →    1.00 K   (+7.28%) |        8.51 s  →        9.36 s   (+10.02%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.57 ms →        5.90 ms   (+6.04%) |     934   →    1.00 K   (+7.28%) |        5.20 s  →        5.91 s   (+13.76%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.21%) |     934   →    1.00 K   (+7.28%) |        1.42 s  →        1.52 s    (+7.06%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.48 ms →        8.32 ms   (-1.90%) |     934   →    1.00 K   (+7.28%) |        7.92 s  →        8.33 s    (+5.24%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.28 ms →        1.34 ms   (+4.54%) |     934   →    1.00 K   (+7.28%) |        1.20 s  →        1.34 s   (+12.15%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.29 ms →        7.21 ms   (-1.14%) |    1.87 K →    2.00 K   (+7.28%) |       13.61 s  →       14.44 s    (+6.06%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.23 ms →       25.97 ms   (-4.63%) |     934   →    1.00 K   (+7.28%) |       25.43 s  →       26.02 s    (+2.32%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.97 ms →        1.91 ms   (-3.20%) |    1.76 K →    1.90 K   (+7.48%) |        3.48 s  →        3.62 s    (+4.04%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       65.43 ns →       62.33 ns   (-4.74%) |    1.76 K →    1.90 K   (+7.48%) |      115.42 μs →      118.18 μs   (+2.39%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.96 ms →        1.90 ms   (-3.19%) |    1.76 K →    1.90 K   (+7.48%) |        3.46 s  →        3.60 s    (+4.05%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       57.64 ns →       61.94 ns   (+7.46%) |    1.76 K →    1.90 K   (+7.48%) |      101.68 μs →      117.43 μs  (+15.50%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      779.59 μs →      791.52 μs   (+1.53%) |     934   →    1.00 K   (+7.28%) |      728.13 ms →      793.10 ms   (+8.92%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      751.40 μs →      727.29 μs   (-3.21%) |     934   →    1.00 K   (+7.28%) |      701.81 ms →      728.75 ms   (+3.84%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.25 ms →        4.97 ms   (-5.32%) |    3.63 K →    3.90 K   (+7.38%) |       19.06 s  →       19.38 s    (+1.67%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.56 ms →        3.37 ms   (-5.41%) |    5.29 K →    5.69 K   (+7.48%) |       18.86 s  →       19.18 s    (+1.67%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.32 ms →        5.20 ms   (-2.25%) |     934   →    1.00 K   (+7.28%) |        4.97 s  →        5.21 s    (+4.87%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.59 ms →        3.41 ms   (-5.12%) |     934   →    1.00 K   (+7.28%) |        3.35 s  →        3.41 s    (+1.79%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       52.89 ns →       49.80 ns   (-5.84%) |     934   →    1.00 K   (+7.28%) |       49.40 μs →       49.90 μs   (+1.02%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.58 ms →        3.39 ms   (-5.12%) |     934   →    1.00 K   (+7.28%) |        3.34 s  →        3.40 s    (+1.79%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       64.22 ns →       47.23 ns  (-26.46%) |     934   →    1.00 K   (+7.28%) |       59.98 μs →       47.33 μs  (-21.10%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       66.35 ms →       33.22 ms  (-49.93%) |     934   →    1.00 K   (+7.28%) |       61.97 s  →       33.29 s   (-46.29%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.35 ms →        9.81 ms   (-5.20%) |     912   →     973     (+6.69%) |        9.44 s  →        9.54 s    (+1.14%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        9.96 ms →        9.35 ms   (-6.10%) |     868   →     930     (+7.14%) |        8.64 s  →        8.70 s    (+0.61%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        4.94 ms →        4.64 ms   (-6.12%) |    1.74 K →    1.86 K   (+7.14%) |        8.58 s  →        8.63 s    (+0.59%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      618.23 μs →      635.18 μs   (+2.74%) |     868   →     930     (+7.14%) |      536.63 ms →      590.72 ms  (+10.08%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.46 ms →       36.01 ms  (-30.02%) |     209   →     352    (+68.42%) |       10.75 s  →       12.68 s   (+17.86%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.14 ms →       21.14 ms  (-38.07%) |     314   →     596    (+89.81%) |       10.72 s  →       12.60 s   (+17.55%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.43 ms →       14.89 ms  (-41.44%) |     419   →     840   (+100.48%) |       10.66 s  →       12.51 s   (+17.39%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      581.26 ns →      484.30 ns  (-16.68%) |     104   →     108     (+3.85%) |       60.45 μs →       52.30 μs  (-13.48%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.55 μs →       22.57 μs   (+4.72%) |      26   →      27     (+3.85%) |      560.40 μs →      609.43 μs   (+8.75%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      602.41 μs →      609.12 μs   (+1.11%) |      26   →      27     (+3.85%) |       15.66 ms →       16.45 ms   (+5.00%) | 
  │ │ ├ sirius::Density::generate                                       |      889.01 ms →      892.02 ms   (+0.34%) |      26   →      27     (+3.85%) |       23.11 s  →       24.08 s    (+4.20%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      521.29 ms →      526.51 ms   (+1.00%) |      26   →      27     (+3.85%) |       13.55 s  →       14.22 s    (+4.88%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.41 ms →       24.40 ms   (+4.25%) |     104   →     108     (+3.85%) |        2.43 s  →        2.64 s    (+8.26%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.52 μs →        8.84 μs   (+3.81%) |     104   →     108     (+3.85%) |      885.99 μs →      955.15 μs   (+7.81%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.06 μs →       15.41 μs   (+2.32%) |       8   →       8              |      120.51 μs →      123.31 μs   (+2.32%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.28 ms →       20.29 ms   (+5.24%) |     104   →     108     (+3.85%) |        2.01 s  →        2.19 s    (+9.28%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.85 ms →       30.19 ms   (+1.16%) |     104   →     108     (+3.85%) |        3.10 s  →        3.26 s    (+5.05%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.54 μs →        9.65 μs   (+1.18%) |     104   →     108     (+3.85%) |      991.98 μs →        1.04 ms   (+5.07%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.02%) |     104   →     108     (+3.85%) |      151.34 ms →      157.19 ms   (+3.87%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.92 ms →       28.25 ms   (+1.20%) |     104   →     108     (+3.85%) |        2.90 s  →        3.05 s    (+5.09%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.79 ms →        4.12 ms   (+8.63%) |     104   →     108     (+3.85%) |      394.61 ms →      445.14 ms  (+12.81%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      726.11 ns →      594.04 ns  (-18.19%) |     104   →     108     (+3.85%) |       75.52 μs →       64.16 μs  (-15.04%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.68 ms →       42.73 ms   (+0.10%) |     104   →     108     (+3.85%) |        4.44 s  →        4.61 s    (+3.95%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.06%) |      26   →      27     (+3.85%) |       42.70 ms →       44.37 ms   (+3.91%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.89 ms →       88.85 ms   (-0.05%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.79%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.65 ms →       88.62 ms   (-0.04%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.81%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.02 ms →      274.48 ms   (-0.19%) |      26   →      27     (+3.85%) |        7.15 s  →        7.41 s    (+3.65%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.02 ms →      274.48 ms   (-0.19%) |      26   →      27     (+3.85%) |        7.15 s  →        7.41 s    (+3.65%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.38 ms →       24.78 ms   (+1.67%) |      26   →      27     (+3.85%) |      633.77 ms →      669.12 ms   (+5.58%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      224.89 ms →      224.22 ms   (-0.30%) |      26   →      27     (+3.85%) |        5.85 s  →        6.05 s    (+3.53%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.98 ms →       23.68 ms   (-1.29%) |      26   →      27     (+3.85%) |      623.59 ms →      639.24 ms   (+2.51%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.84 ms →       80.32 ms   (-0.64%) |      26   →      27     (+3.85%) |        2.10 s  →        2.17 s    (+3.18%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.12 ms →        7.11 ms  (-12.41%) |      26   →      27     (+3.85%) |      211.18 ms →      192.09 ms   (-9.04%) | 
  │ │ ├ sirius::Density::mix                                            |      219.05 ms →      214.38 ms   (-2.13%) |      26   →      27     (+3.85%) |        5.70 s  →        5.79 s    (+1.63%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      973.36 μs →      927.03 μs   (-4.76%) |      26   →      27     (+3.85%) |       25.31 ms →       25.03 ms   (-1.10%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.75 ms →       10.30 ms   (-4.16%) |     334   →     349     (+4.49%) |        3.59 s  →        3.59 s    (+0.14%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms →        9.98 ms   (-3.97%) |     334   →     349     (+4.49%) |        3.47 s  →        3.48 s    (+0.34%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms →        9.98 ms   (-3.97%) |     334   →     349     (+4.49%) |        3.47 s  →        3.48 s    (+0.34%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.20 ms →        6.57 ms   (+5.89%) |      26   →      27     (+3.85%) |      161.27 ms →      177.33 ms   (+9.96%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.37 ms →        5.76 ms   (+7.27%) |      26   →      27     (+3.85%) |      139.67 ms →      155.59 ms  (+11.40%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.19 ms →      580.20 ms   (+0.17%) |      26   →      27     (+3.85%) |       15.06 s  →       15.67 s    (+4.03%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.84 ms →      138.17 ms   (+0.97%) |      26   →      27     (+3.85%) |        3.56 s  →        3.73 s    (+4.85%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.55 ms →       19.29 ms  (+24.04%) |      26   →      27     (+3.85%) |      404.24 ms →      520.72 ms  (+28.81%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.44 ms →       10.37 ms   (-0.71%) |      26   →      27     (+3.85%) |      271.44 ms →      279.87 ms   (+3.11%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.94 ms →        9.95 ms   (+0.10%) |      26   →      27     (+3.85%) |      258.36 ms →      268.57 ms   (+3.95%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.94 ms →        9.95 ms   (+0.11%) |      26   →      27     (+3.85%) |      258.34 ms →      268.56 ms   (+3.96%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.35 μs →      548.26 μs   (-0.38%) |      52   →      54     (+3.85%) |       28.62 ms →       29.61 ms   (+3.45%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.29 ms →       49.30 ms   (+0.02%) |      26   →      27     (+3.85%) |        1.28 s  →        1.33 s    (+3.87%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.94 ms →       46.97 ms   (+0.07%) |      26   →      27     (+3.85%) |        1.22 s  →        1.27 s    (+3.92%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.03 ms   (+0.21%) |      52   →      54     (+3.85%) |      157.24 ms →      163.63 ms   (+4.06%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.32 ms →        5.45 ms   (+2.53%) |      26   →      27     (+3.85%) |      138.26 ms →      147.22 ms   (+6.48%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.55 ms →        6.70 ms   (+2.27%) |      26   →      27     (+3.85%) |      170.26 ms →      180.82 ms   (+6.21%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       91.06 ms   (+0.19%) |      26   →      27     (+3.85%) |        2.36 s  →        2.46 s    (+4.04%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.24 ms →      292.57 ms   (-0.23%) |      26   →      27     (+3.85%) |        7.62 s  →        7.90 s    (+3.61%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.15 ms →      276.23 ms   (-1.40%) |      26   →      27     (+3.85%) |        7.28 s  →        7.46 s    (+2.39%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.15 ms →      276.23 ms   (-1.40%) |      26   →      27     (+3.85%) |        7.28 s  →        7.46 s    (+2.39%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.21 ms →       27.17 ms   (-0.16%) |      26   →      27     (+3.85%) |      707.52 ms →      733.56 ms   (+3.68%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.43 ms →      221.48 ms   (-1.75%) |      26   →      27     (+3.85%) |        5.86 s  →        5.98 s    (+2.03%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.69 ms →       23.81 ms   (+0.50%) |      26   →      27     (+3.85%) |      616.02 ms →      642.94 ms   (+4.37%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.48 ms →        5.72 ms   (+4.38%) |      26   →      27     (+3.85%) |      142.51 ms →      154.48 ms   (+8.40%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.37 ms →       10.35 ms   (-0.23%) |     182   →     189     (+3.85%) |        1.89 s  →        1.96 s    (+3.60%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.98 ms →        9.83 ms   (-1.55%) |     182   →     189     (+3.85%) |        1.82 s  →        1.86 s    (+2.24%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.98 ms →        9.83 ms   (-1.55%) |     182   →     189     (+3.85%) |        1.82 s  →        1.86 s    (+2.24%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.17 ms →       10.56 ms   (-5.49%) |      78   →      81     (+3.85%) |      871.14 ms →      855.00 ms   (-1.85%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.77 ms →       10.19 ms   (-5.39%) |      78   →      81     (+3.85%) |      839.81 ms →      825.09 ms   (-1.75%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.05 ms →        9.98 ms   (-0.65%) |      26   →      27     (+3.85%) |      261.31 ms →      269.59 ms   (+3.17%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      126.68 μs →      114.25 μs   (-9.81%) |      26   →      27     (+3.85%) |        3.29 ms →        3.08 ms   (-6.34%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      120.51 μs →      108.42 μs  (-10.03%) |      26   →      27     (+3.85%) |        3.13 ms →        2.93 ms   (-6.57%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.47 ms →        5.16 ms   (-5.63%) |       2   →       2              |       10.93 ms →       10.32 ms   (-5.63%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.05 ms →        9.74 ms   (-3.15%) |       6   →       6              |       60.32 ms →       58.43 ms   (-3.15%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.68 ms →        9.69 ms   (+0.09%) |       6   →       6              |       58.08 ms →       58.13 ms   (+0.09%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.68 ms →        9.69 ms   (+0.09%) |       6   →       6              |       58.07 ms →       58.13 ms   (+0.09%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.83 ms →       10.13 ms   (-6.50%) |       3   →       3              |       32.49 ms →       30.38 ms   (-6.50%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.49 ms →       10.04 ms   (-4.27%) |       3   →       3              |       31.47 ms →       30.12 ms   (-4.27%) | 
  ├ sirius::Periodic_function|inner                                     |        9.96 ms →        9.97 ms   (+0.16%) |       2   →       2              |       19.91 ms →       19.94 ms   (+0.16%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.68 ms →        9.65 ms   (-0.31%) |       2   →       2              |       19.37 ms →       19.31 ms   (-0.31%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →        9.65 ms   (-0.31%) |       2   →       2              |       19.37 ms →       19.31 ms   (-0.31%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.92 ms →       10.18 ms   (-6.79%) |       1   →       1              |       10.92 ms →       10.18 ms   (-6.79%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.02 ms   (-4.33%) |       1   →       1              |       10.47 ms →       10.02 ms   (-4.33%) | 
  └ sirius::finalize                                                    |      319.13 ms →      315.10 ms   (-1.26%) |       1   →       1              |      319.13 ms →      315.10 ms   (-1.26%) | 
  ====================================================================================================================================================================================================
```
