# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.00 s  →      128.85 s    (-3.12%) |       1   →       1              |      133.00 s  →      128.85 s    (-3.12%) | 
  ├ sirius::initialize                                                  |        2.76 s  →        2.71 s    (-1.76%) |       1   →       1              |        2.76 s  →        2.71 s    (-1.76%) | 
  ├ sirius::Simulation_context::initialize                              |        2.87 s  →        2.96 s    (+3.08%) |       1   →       1              |        2.87 s  →        2.96 s    (+3.08%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       16.06 ms →       13.31 ms  (-17.08%) |       1   →       1              |       16.06 ms →       13.31 ms  (-17.08%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      128.79 ms →      219.06 ms  (+70.09%) |       1   →       1              |      128.79 ms →      219.06 ms  (+70.09%) | 
- │ │ ├ sirius::Atom_type::init                                         |       52.68 ms →       96.95 ms  (+84.05%) |       2   →       2              |      105.35 ms →      193.91 ms  (+84.05%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.36 ms →       25.07 ms   (+7.29%) |       1   →       1              |       23.36 ms →       25.07 ms   (+7.29%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.32 ms →        6.51 ms   (+3.01%) |       1   →       1              |        6.32 ms →        6.51 ms   (+3.01%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.01 ms →       18.50 ms   (+8.80%) |       1   →       1              |       17.01 ms →       18.50 ms   (+8.80%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.98 ms →       18.48 ms   (+8.83%) |       1   →       1              |       16.98 ms →       18.48 ms   (+8.83%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.15 ms   (+0.15%) |       1   →       1              |        4.14 ms →        4.15 ms   (+0.15%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.12%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.12%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |      113.36 μs →      100.70 μs  (-11.17%) |       1   →       1              |      113.36 μs →      100.70 μs  (-11.17%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.69 s    (+0.08%) |       1   →       1              |        2.68 s  →        2.69 s    (+0.08%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.78 ms →       10.82 ms   (+0.32%) |       1   →       1              |       10.78 ms →       10.82 ms   (+0.32%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.33 ms →        4.41 ms   (+1.94%) |       1   →       1              |        4.33 ms →        4.41 ms   (+1.94%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.42 ms →        6.37 ms   (-0.80%) |       1   →       1              |        6.42 ms →        6.37 ms   (-0.80%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.41 ms →        6.35 ms   (-0.81%) |       1   →       1              |        6.41 ms →        6.35 ms   (-0.81%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.87 ms   (-0.59%) |       1   →       1              |        3.89 ms →        3.87 ms   (-0.59%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.32 ms   (-1.06%) |       1   →       1              |        2.35 ms →        2.32 ms   (-1.06%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      102.93 μs →       99.08 μs   (-3.74%) |       1   →       1              |      102.93 μs →       99.08 μs   (-3.74%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.99 ms →       62.36 ms   (-0.99%) |       2   →       2              |      125.97 ms →      124.72 ms   (-0.99%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.15 ms   (+0.35%) |       2   →       2              |       10.27 ms →       10.31 ms   (+0.35%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.48 ms   (+0.40%) |       1   →       1              |        4.46 ms →        4.48 ms   (+0.40%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.75 ms →       21.72 ms   (-0.14%) |       2   →       2              |       43.50 ms →       43.43 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.82 ms   (-0.04%) |       2   →       2              |       29.65 ms →       29.63 ms   (-0.04%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.83 ms →       19.82 ms   (-0.09%) |       4   →       4              |       79.34 ms →       79.27 ms   (-0.09%) | 
  │   ├ sddk::Gvec::init                                                |      173.43 ms →      172.83 ms   (-0.35%) |       2   →       2              |      346.86 ms →      345.65 ms   (-0.35%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.63 ms →      130.13 ms   (-0.38%) |       2   →       2              |      261.26 ms →      260.26 ms   (-0.38%) | 
  │   ├ sddk::Gvec_shells                                               |      177.00 ms →      179.20 ms   (+1.24%) |       1   →       1              |      177.00 ms →      179.20 ms   (+1.24%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.66%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.66%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.78 ms →      292.15 ms   (-0.55%) |       2   →       2              |      587.55 ms →      584.31 ms   (-0.55%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.06 ms →       35.78 ms   (-0.79%) |       1   →       1              |       36.06 ms →       35.78 ms   (-0.79%) | 
  │ ├ sirius::K_point::K_point                                          |        2.65 μs →        2.74 μs   (+3.41%) |       4   →       4              |       10.61 μs →       10.97 μs   (+3.41%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.95 ms →       35.68 ms   (-0.75%) |       1   →       1              |       35.95 ms →       35.68 ms   (-0.75%) | 
  │   └ sirius::K_point::initialize                                     |       35.86 ms →       35.59 ms   (-0.76%) |       1   →       1              |       35.86 ms →       35.59 ms   (-0.76%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.22 ms →       18.10 ms   (-0.65%) |       1   →       1              |       18.22 ms →       18.10 ms   (-0.65%) | 
  │     │ └ sddk::Gvec::init                                            |        8.18 ms →        8.23 ms   (+0.59%) |       1   →       1              |        8.18 ms →        8.23 ms   (+0.59%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.12 μs →        9.16 μs   (-9.50%) |       1   →       1              |       10.12 μs →        9.16 μs   (-9.50%) | 
  │     └ sirius::K_point::update                                       |       12.60 ms →       12.69 ms   (+0.69%) |       1   →       1              |       12.60 ms →       12.69 ms   (+0.69%) | 
  │       └ sirius::Beta_projectors                                     |        6.25 ms →        6.48 ms   (+3.77%) |       1   →       1              |        6.25 ms →        6.48 ms   (+3.77%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.67 ms →        3.88 ms   (+5.70%) |       1   →       1              |        3.67 ms →        3.88 ms   (+5.70%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.11 ms →        5.55 ms   (+8.72%) |       2   →       2              |       10.21 ms →       11.10 ms   (+8.72%) | 
  ├ sirius::Potential                                                   |      160.00 ms →      158.34 ms   (-1.04%) |       1   →       1              |      160.00 ms →      158.34 ms   (-1.04%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.91 ms   (+2.91%) |       6   →       6              |       34.45 ms →       35.45 ms   (+2.91%) | 
  │ └ sirius::Potential::update                                         |      124.81 ms →      122.12 ms   (-2.15%) |       1   →       1              |      124.81 ms →      122.12 ms   (-2.15%) | 
  │   └ sirius::Potential::generate_local_potential                     |      124.09 ms →      121.37 ms   (-2.19%) |       1   →       1              |      124.09 ms →      121.37 ms   (-2.19%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.80 ms →      106.43 ms   (-0.35%) |       1   →       1              |      106.80 ms →      106.43 ms   (-0.35%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.38 ms →       14.04 ms  (-14.29%) |       1   →       1              |       16.38 ms →       14.04 ms  (-14.29%) | 
  ├ sirius::Density                                                     |      135.35 ms →      135.87 ms   (+0.39%) |       1   →       1              |      135.35 ms →      135.87 ms   (+0.39%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.13 ms →        5.77 ms  (+12.53%) |       2   →       2              |       10.26 ms →       11.54 ms  (+12.53%) | 
  │ └ sirius::Density::update                                           |      124.82 ms →      124.03 ms   (-0.64%) |       1   →       1              |      124.82 ms →      124.03 ms   (-0.64%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.41 ms →      123.57 ms   (-0.68%) |       1   →       1              |      124.41 ms →      123.57 ms   (-0.68%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      102.80 μs →      115.47 μs  (+12.33%) |       1   →       1              |      102.80 μs →      115.47 μs  (+12.33%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.31 ms →      109.15 ms   (-0.15%) |       1   →       1              |      109.31 ms →      109.15 ms   (-0.15%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.55 ms →       13.84 ms   (-4.84%) |       1   →       1              |       14.55 ms →       13.84 ms   (-4.84%) | 
  ├ sirius::Density::initial_density                                    |      174.54 ms →      175.27 ms   (+0.42%) |       1   →       1              |      174.54 ms →      175.27 ms   (+0.42%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.70 ms →      108.12 ms   (-0.54%) |       1   →       1              |      108.70 ms →      108.12 ms   (-0.54%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.80 ms →       12.40 ms   (+5.15%) |       2   →       2              |       23.60 ms →       24.81 ms   (+5.15%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.82 ms →       10.08 ms   (+2.64%) |       1   →       1              |        9.82 ms →       10.08 ms   (+2.64%) | 
  ├ sirius::Potential::generate                                         |      604.78 ms →      593.19 ms   (-1.92%) |       1   →       1              |      604.78 ms →      593.19 ms   (-1.92%) | 
  │ ├ sirius::Potential::poisson                                        |      138.00 ms →      137.26 ms   (-0.54%) |       1   →       1              |      138.00 ms →      137.26 ms   (-0.54%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.16 ms →       19.13 ms   (-0.18%) |       1   →       1              |       19.16 ms →       19.13 ms   (-0.18%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.91 ms →       10.31 ms   (-5.51%) |       1   →       1              |       10.91 ms →       10.31 ms   (-5.51%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.83 ms   (-0.61%) |       1   →       1              |        9.89 ms →        9.83 ms   (-0.61%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.82 ms   (-0.62%) |       1   →       1              |        9.88 ms →        9.82 ms   (-0.62%) | 
  │ ├ sirius::Periodic_function::add                                    |      543.46 μs →      563.91 μs   (+3.76%) |       2   →       2              |        1.09 ms →        1.13 ms   (+3.76%) | 
  │ ├ sirius::Potential::xc                                             |       55.20 ms →       53.75 ms   (-2.64%) |       1   →       1              |       55.20 ms →       53.75 ms   (-2.64%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.90 ms →       51.30 ms   (-3.03%) |       1   →       1              |       52.90 ms →       51.30 ms   (-3.03%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.62 ms →        5.77 ms   (+2.72%) |       2   →       2              |       11.24 ms →       11.54 ms   (+2.72%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.79 ms →        5.09 ms  (-12.18%) |       1   →       1              |        5.79 ms →        5.09 ms  (-12.18%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.04 ms →        5.85 ms   (-3.09%) |       1   →       1              |        6.04 ms →        5.85 ms   (-3.09%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.78 ms →       92.78 ms   (+0.00%) |       1   →       1              |       92.78 ms →       92.78 ms   (+0.00%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      310.34 ms →      300.99 ms   (-3.01%) |       1   →       1              |      310.34 ms →      300.99 ms   (-3.01%) | 
  ├ sirius::Hamiltonian0                                                |        8.61 ms →        8.43 ms   (-2.09%) |       1   →       1              |        8.61 ms →        8.43 ms   (-2.09%) | 
  │ ├ sirius::Local_operator                                            |        8.26 ms →        8.08 ms   (-2.22%) |       1   →       1              |        8.26 ms →        8.08 ms   (-2.22%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.68 ms →        4.81 ms   (+2.68%) |       1   →       1              |        4.68 ms →        4.81 ms   (+2.68%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.67 ms →        2.35 ms  (-12.16%) |       1   →       1              |        2.67 ms →        2.35 ms  (-12.16%) | 
  │ ├ sirius::Non_local_operator                                        |       63.13 μs →       64.75 μs   (+2.58%) |       2   →       2              |      126.25 μs →      129.50 μs   (+2.58%) | 
  │ ├ sirius::D_operator::initialize                                    |       95.21 μs →       96.79 μs   (+1.66%) |       1   →       1              |       95.21 μs →       96.79 μs   (+1.66%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.01 μs →       75.48 μs   (-0.69%) |       1   →       1              |       76.01 μs →       75.48 μs   (-0.69%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.85 s    (-0.27%) |       1   →       1              |        1.86 s  →        1.85 s    (-0.27%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.68 ms →       18.67 ms   (-0.09%) |       1   →       1              |       18.68 ms →       18.67 ms   (-0.09%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      176.32 μs →      184.24 μs   (+4.49%) |       1   →       1              |      176.32 μs →      184.24 μs   (+4.49%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.48 ms   (-0.14%) |       1   →       1              |       18.50 ms →       18.48 ms   (-0.14%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.83 s    (-0.27%) |       1   →       1              |        1.84 s  →        1.83 s    (-0.27%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      130.38 ms →      126.98 ms   (-2.61%) |       4   →       4              |      521.54 ms →      507.92 ms   (-2.61%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.06 ms →       53.61 ms   (+2.99%) |       1   →       1              |       52.06 ms →       53.61 ms   (+2.99%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.02 ms →       21.68 ms   (+3.13%) |       1   →       1              |       21.02 ms →       21.68 ms   (+3.13%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.68 ms →      634.40 ms   (-0.36%) |       1   →       1              |      636.68 ms →      634.40 ms   (-0.36%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.79 ms →      297.58 ms   (-0.07%) |       1   →       1              |      297.79 ms →      297.58 ms   (-0.07%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.24 μs →        3.02 μs   (-6.67%) |       1   →       1              |        3.24 μs →        3.02 μs   (-6.67%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.33 μs →        1.99 μs  (-14.90%) |       1   →       1              |        2.33 μs →        1.99 μs  (-14.90%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      375.00 ns →      362.00 ns   (-3.47%) |       1   →       1              |      375.00 ns →      362.00 ns   (-3.47%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      413.00 ns →      547.00 ns  (+32.45%) |       1   →       1              |      413.00 ns →      547.00 ns  (+32.45%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.21 ms   (-0.12%) |       1   →       1              |        9.22 ms →        9.21 ms   (-0.12%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.18 ms →      120.53 ms   (-0.53%) |       1   →       1              |      121.18 ms →      120.53 ms   (-0.53%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.23 ms →      103.52 ms   (-0.68%) |       2   →       2              |      208.46 ms →      207.04 ms   (-0.68%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.13 ms →       40.14 ms   (+0.03%) |       2   →       2              |       80.25 ms →       80.28 ms   (+0.03%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.58 ms →       39.58 ms   (-0.02%) |       2   →       2              |       79.17 ms →       79.15 ms   (-0.02%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       17.50 ns →       29.00 ns  (+65.71%) |       2   →       2              |       35.00 ns →       58.00 ns  (+65.71%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.11 ms →       39.10 ms   (-0.03%) |       2   →       2              |       78.22 ms →       78.20 ms   (-0.03%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       25.00 ns  (+31.58%) |       2   →       2              |       38.00 ns →       50.00 ns  (+31.58%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.77 ms →       56.35 ms   (-0.74%) |       1   →       1              |       56.77 ms →       56.35 ms   (-0.74%) | 
  │ │ └ sddk::wf_trans                                                  |       30.77 ms →       30.76 ms   (-0.02%) |       1   →       1              |       30.77 ms →       30.76 ms   (-0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.76 ms →       30.76 ms   (-0.02%) |       1   →       1              |       30.76 ms →       30.76 ms   (-0.02%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      666.00 ns →      488.00 ns  (-26.73%) |       1   →       1              |      666.00 ns →      488.00 ns  (-26.73%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.33 s  →      119.20 s    (-3.35%) |       1   →       1              |      123.33 s  →      119.20 s    (-3.35%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.89 ms   (+2.62%) |      19   →      19              |      109.14 ms →      112.00 ms   (+2.62%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.73 s  →        4.57 s    (-3.48%) |      26   →      26              |      123.01 s  →      118.73 s    (-3.48%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.95 ms →        5.15 ms   (+3.91%) |      26   →      26              |      128.80 ms →      133.84 ms   (+3.91%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.58 ms →        4.78 ms   (+4.37%) |      26   →      26              |      119.17 ms →      124.38 ms   (+4.37%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.01 ms →      988.61 μs   (-1.87%) |      26   →      26              |       26.19 ms →       25.70 ms   (-1.87%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.68 ms →        2.91 ms   (+8.36%) |      26   →      26              |       69.78 ms →       75.62 ms   (+8.36%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.69 μs →       64.34 μs   (-0.53%) |      52   →      52              |        3.36 ms →        3.35 ms   (-0.53%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       89.25 μs →       87.21 μs   (-2.29%) |      26   →      26              |        2.32 ms →        2.27 ms   (-2.29%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       79.84 μs →       78.55 μs   (-1.62%) |      26   →      26              |        2.08 ms →        2.04 ms   (-1.62%) | 
  │ │ ├ sirius::Band::solve                                             |        2.76 s  →        2.61 s    (-5.34%) |      26   →      26              |       71.64 s  →       67.81 s    (-5.34%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      152.96 μs →      157.05 μs   (+2.68%) |      26   →      26              |        3.98 ms →        4.08 ms   (+2.68%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      146.02 μs →      150.62 μs   (+3.15%) |      26   →      26              |        3.80 ms →        3.92 ms   (+3.15%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.07 μs →        4.62 μs   (-8.88%) |      26   →      26              |      131.79 μs →      120.08 μs   (-8.88%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        2.46 s    (-6.24%) |      26   →      26              |       68.14 s  →       63.89 s    (-6.24%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.70 ms →       96.16 ms   (+0.48%) |      26   →      26              |        2.49 s  →        2.50 s    (+0.48%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.80 ms →        7.84 ms   (+0.50%) |     156   →     156              |        1.22 s  →        1.22 s    (+0.50%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.95 ms →        5.95 ms   (-0.03%) |      26   →      26              |      154.73 ms →      154.69 ms   (-0.03%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.33 μs →      348.30 μs   (-1.15%) |      26   →      26              |        9.16 ms →        9.06 ms   (-1.15%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.30 ms   (-0.03%) |      52   →      52              |      119.77 ms →      119.73 ms   (-0.03%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.48 s  →        2.32 s    (-6.61%) |      26   →      26              |       64.57 s  →       60.31 s    (-6.61%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      127.41 ms →      136.72 ms   (+7.30%) |     277   →     261     (-5.78%) |       35.29 s  →       35.68 s    (+1.10%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.82 ms →       55.71 ms   (+9.61%) |     277   →     261     (-5.78%) |       14.08 s  →       14.54 s    (+3.28%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.84 μs →        1.89 μs   (+2.51%) |     277   →     261     (-5.78%) |      509.79 μs →      492.38 μs   (-3.41%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.58 μs   (+0.21%) |     277   →     261     (-5.78%) |      436.88 μs →      412.52 μs   (-5.57%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      329.10 ns →      365.95 ns  (+11.19%) |     277   →     261     (-5.78%) |       91.16 μs →       95.51 μs   (+4.77%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      409.20 ns →      445.82 ns   (+8.95%) |     277   →     261     (-5.78%) |      113.35 μs →      116.36 μs   (+2.66%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.46%) |     277   →     261     (-5.78%) |        2.06 s  →        1.95 s    (-5.34%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.22 ms →       24.61 ms   (+6.01%) |     277   →     261     (-5.78%) |        6.43 s  →        6.42 s    (-0.12%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.97 ms →       24.46 ms   (+6.51%) |     554   →     522     (-5.78%) |       12.72 s  →       12.77 s    (+0.36%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.33 ms →       35.97 ms   (+4.77%) |     277   →     261     (-5.78%) |        9.51 s  →        9.39 s    (-1.28%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.96 ms →        6.24 ms   (+4.59%) |     528   →     496     (-6.06%) |        3.15 s  →        3.09 s    (-1.75%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       72.42 ns →       50.70 ns  (-30.00%) |     528   →     496     (-6.06%) |       38.24 μs →       25.15 μs  (-34.24%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.85 ms →        5.12 ms   (+5.58%) |     528   →     496     (-6.06%) |        2.56 s  →        2.54 s    (-0.82%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       51.65 ns →       29.69 ns  (-42.52%) |     528   →     496     (-6.06%) |       27.27 μs →       14.73 μs  (-46.00%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      612.89 μs →      669.40 μs   (+9.22%) |     277   →     261     (-5.78%) |      169.77 ms →      174.71 ms   (+2.91%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.56 ms →       10.34 ms   (+8.15%) |     277   →     261     (-5.78%) |        2.65 s  →        2.70 s    (+1.90%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.11 ms →       14.55 ms   (+3.13%) |     251   →     235     (-6.37%) |        3.54 s  →        3.42 s    (-3.44%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.70 ms →        4.85 ms   (+3.13%) |     753   →     705     (-6.37%) |        3.54 s  →        3.42 s    (-3.45%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.32 ms →       10.41 ms   (+0.88%) |     277   →     261     (-5.78%) |        2.86 s  →        2.72 s    (-4.95%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.05 ms →       10.21 ms   (+1.54%) |     277   →     261     (-5.78%) |        2.78 s  →        2.66 s    (-4.33%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       44.97 ns →       27.49 ns  (-38.87%) |     277   →     261     (-5.78%) |       12.46 μs →        7.18 μs  (-42.40%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.94 ms →        9.09 ms   (+1.70%) |     277   →     261     (-5.78%) |        2.48 s  →        2.37 s    (-4.17%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       69.23 ns →       48.15 ns  (-30.45%) |     277   →     261     (-5.78%) |       19.18 μs →       12.57 μs  (-34.47%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.59 ms →       17.74 ms  (-47.20%) |     277   →     261     (-5.78%) |        9.31 s  →        4.63 s   (-50.25%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.52 ms →       13.20 ms   (-2.35%) |     268   →     251     (-6.34%) |        3.62 s  →        3.31 s    (-8.54%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.20 ms →       11.71 ms   (-3.99%) |     258   →     242     (-6.20%) |        3.15 s  →        2.83 s    (-9.95%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.10 ms →        5.85 ms   (-4.00%) |     516   →     484     (-6.20%) |        3.15 s  →        2.83 s    (-9.95%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.60 ms →        1.72 ms   (+7.88%) |     258   →     242     (-6.20%) |      411.91 ms →      416.80 ms   (+1.19%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.97 ms →       53.75 ms  (-28.30%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+15.00%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.43 ms →       31.46 ms  (-36.35%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.58%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.96 ms →       22.32 ms  (-39.61%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.57%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      614.65 ns →      438.50 ns  (-28.66%) |      26   →      26              |       15.98 μs →       11.40 μs  (-28.66%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       31.31 μs →       28.60 μs   (-8.66%) |      26   →      26              |      814.16 μs →      743.65 μs   (-8.66%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      602.06 μs →      607.13 μs   (+0.84%) |      26   →      26              |       15.65 ms →       15.79 ms   (+0.84%) | 
  │ │ ├ sirius::Density::generate                                       |      772.98 ms →      769.62 ms   (-0.44%) |      26   →      26              |       20.10 s  →       20.01 s    (-0.44%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      404.09 ms →      401.00 ms   (-0.77%) |      26   →      26              |       10.51 s  →       10.43 s    (-0.77%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.15 μs →        8.66 μs   (+6.29%) |      26   →      26              |      211.83 μs →      225.16 μs   (+6.29%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.65 μs →        7.84 μs   (+2.55%) |      26   →      26              |      198.90 μs →      203.97 μs   (+2.55%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.38 ms →      100.17 ms   (-0.21%) |      26   →      26              |        2.61 s  →        2.60 s    (-0.21%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.45 μs →        7.79 μs   (+4.48%) |      26   →      26              |      193.80 μs →      202.47 μs   (+4.48%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.11 ms   (-0.04%) |      26   →      26              |      185.06 ms →      184.98 ms   (-0.04%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.37 ms →       91.17 ms   (-0.22%) |      26   →      26              |        2.38 s  →        2.37 s    (-0.22%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      677.00 ns →      568.88 ns  (-15.97%) |      26   →      26              |       17.60 μs →       14.79 μs  (-15.97%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.37 ms →      162.14 ms   (-0.76%) |      26   →      26              |        4.25 s  →        4.22 s    (-0.76%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.20%) |      26   →      26              |       42.70 ms →       42.78 ms   (+0.20%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.28 ms →       88.44 ms   (+0.18%) |      26   →      26              |        2.30 s  →        2.30 s    (+0.18%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.05 ms →       88.21 ms   (+0.18%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.18%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.01 ms →      275.03 ms   (-0.36%) |      26   →      26              |        7.18 s  →        7.15 s    (-0.36%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.01 ms →      275.03 ms   (-0.36%) |      26   →      26              |        7.18 s  →        7.15 s    (-0.36%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.12 ms →       24.43 ms   (+1.29%) |      26   →      26              |      627.05 ms →      635.16 ms   (+1.29%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.92 ms →      226.26 ms   (-0.73%) |      26   →      26              |        5.93 s  →        5.88 s    (-0.73%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.78 ms →       23.14 ms   (+1.57%) |      26   →      26              |      592.29 ms →      601.60 ms   (+1.57%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.44 ms →       81.68 ms   (+1.55%) |      26   →      26              |        2.09 s  →        2.12 s    (+1.55%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.84 ms →        8.29 ms   (-6.24%) |      26   →      26              |      229.97 ms →      215.62 ms   (-6.24%) | 
  │ │ ├ sirius::Density::mix                                            |      218.27 ms →      206.10 ms   (-5.57%) |      26   →      26              |        5.67 s  →        5.36 s    (-5.57%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      957.28 μs →      936.93 μs   (-2.13%) |      26   →      26              |       24.89 ms →       24.36 ms   (-2.13%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.69 ms →       10.36 ms   (-3.12%) |     334   →     320     (-4.19%) |        3.57 s  →        3.31 s    (-7.18%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.37 ms →        9.92 ms   (-4.38%) |     334   →     320     (-4.19%) |        3.46 s  →        3.17 s    (-8.38%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.37 ms →        9.92 ms   (-4.38%) |     334   →     320     (-4.19%) |        3.46 s  →        3.17 s    (-8.39%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.35 ms →        6.01 ms   (-5.49%) |      26   →      26              |      165.22 ms →      156.14 ms   (-5.49%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.50 ms →        5.14 ms   (-6.58%) |      26   →      26              |      142.98 ms →      133.57 ms   (-6.58%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.62 ms →      579.12 ms   (+0.09%) |      26   →      26              |       15.04 s  →       15.06 s    (+0.09%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.33 ms →      137.34 ms   (+0.01%) |      26   →      26              |        3.57 s  →        3.57 s    (+0.01%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       19.26 ms →       19.41 ms   (+0.75%) |      26   →      26              |      500.87 ms →      504.60 ms   (+0.75%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.35 ms →       10.38 ms   (+0.32%) |      26   →      26              |      269.05 ms →      269.92 ms   (+0.32%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.98 ms →        9.89 ms   (-0.89%) |      26   →      26              |      259.39 ms →      257.07 ms   (-0.89%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.98 ms →        9.89 ms   (-0.89%) |      26   →      26              |      259.37 ms →      257.06 ms   (-0.89%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      552.13 μs →      563.49 μs   (+2.06%) |      52   →      52              |       28.71 ms →       29.30 ms   (+2.06%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.19 ms →       49.38 ms   (+0.39%) |      26   →      26              |        1.28 s  →        1.28 s    (+0.39%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.78 ms →       46.99 ms   (+0.45%) |      26   →      26              |        1.22 s  →        1.22 s    (+0.45%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.08 ms →        3.06 ms   (-0.55%) |      52   →      52              |      159.94 ms →      159.05 ms   (-0.55%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.43 ms →        5.41 ms   (-0.43%) |      26   →      26              |      141.26 ms →      140.66 ms   (-0.43%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.53 ms →        6.40 ms   (-2.04%) |      26   →      26              |      169.78 ms →      166.32 ms   (-2.04%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       91.00 ms   (+0.05%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.05%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.20 ms →      292.53 ms   (+0.12%) |      26   →      26              |        7.60 s  →        7.61 s    (+0.12%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      279.41 ms →      278.32 ms   (-0.39%) |      26   →      26              |        7.26 s  →        7.24 s    (-0.39%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      279.41 ms →      278.32 ms   (-0.39%) |      26   →      26              |        7.26 s  →        7.24 s    (-0.39%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.20 ms →       27.07 ms   (-0.47%) |      26   →      26              |      707.18 ms →      703.87 ms   (-0.47%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.60 ms →      223.51 ms   (-0.04%) |      26   →      26              |        5.81 s  →        5.81 s    (-0.04%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.79 ms →       23.94 ms   (-3.41%) |      26   →      26              |      644.44 ms →      622.47 ms   (-3.41%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.44 ms →        5.59 ms   (+2.75%) |      26   →      26              |      141.45 ms →      145.33 ms   (+2.75%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.37 ms →       10.24 ms   (-1.24%) |     182   →     182              |        1.89 s  →        1.86 s    (-1.24%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.91 ms →        9.71 ms   (-1.99%) |     182   →     182              |        1.80 s  →        1.77 s    (-1.99%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.91 ms →        9.71 ms   (-1.99%) |     182   →     182              |        1.80 s  →        1.77 s    (-1.99%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.95 ms →       10.58 ms   (-3.33%) |      78   →      78              |      853.98 ms →      825.51 ms   (-3.33%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.71 ms →       10.08 ms   (-5.88%) |      78   →      78              |      835.05 ms →      785.97 ms   (-5.88%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.96 ms →       10.15 ms   (+1.97%) |      26   →      26              |      258.88 ms →      263.98 ms   (+1.97%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      115.67 μs →      112.01 μs   (-3.17%) |      26   →      26              |        3.01 ms →        2.91 ms   (-3.17%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      110.96 μs →      107.44 μs   (-3.18%) |      26   →      26              |        2.89 ms →        2.79 ms   (-3.18%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.28 ms →        5.07 ms   (-3.89%) |       2   →       2              |       10.55 ms →       10.14 ms   (-3.89%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.33 ms →       10.02 ms   (-2.98%) |       6   →       6              |       61.97 ms →       60.12 ms   (-2.98%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.93 ms →        9.76 ms   (-1.74%) |       6   →       6              |       59.59 ms →       58.56 ms   (-1.74%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.93 ms →        9.76 ms   (-1.73%) |       6   →       6              |       59.59 ms →       58.56 ms   (-1.73%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       11.27 ms →       10.39 ms   (-7.81%) |       3   →       3              |       33.82 ms →       31.18 ms   (-7.81%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.75 ms →       10.11 ms   (-5.92%) |       3   →       3              |       32.25 ms →       30.34 ms   (-5.92%) | 
  ├ sirius::Periodic_function|inner                                     |       10.31 ms →       10.01 ms   (-2.97%) |       2   →       2              |       20.63 ms →       20.01 ms   (-2.97%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.68 ms →        9.75 ms   (+0.76%) |       2   →       2              |       19.36 ms →       19.51 ms   (+0.76%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →        9.75 ms   (+0.75%) |       2   →       2              |       19.36 ms →       19.51 ms   (+0.75%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       11.24 ms →       10.44 ms   (-7.09%) |       1   →       1              |       11.24 ms →       10.44 ms   (-7.09%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.52 ms →       10.13 ms   (-3.70%) |       1   →       1              |       10.52 ms →       10.13 ms   (-3.70%) | 
+ └ sirius::finalize                                                    |      240.81 ms →      199.17 ms  (-17.29%) |       1   →       1              |      240.81 ms →      199.17 ms  (-17.29%) | 
  ====================================================================================================================================================================================================
```
