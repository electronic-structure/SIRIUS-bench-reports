# Benchmark 8541f94e2e0e288633941ac63ad4d565828afb1d vs 58f31ed08f2b4e9e6d289f9ed116027f00413e03
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      161.28 s  →      134.54 s   (-16.58%) |       1   →       1              |      161.28 s  →      134.54 s   (-16.58%) | 
  ├ sirius::initialize                                                  |        2.76 s  →        2.73 s    (-1.26%) |       1   →       1              |        2.76 s  →        2.73 s    (-1.26%) | 
  ├ sirius::Simulation_context::initialize                              |        2.99 s  →        3.24 s    (+8.11%) |       1   →       1              |        2.99 s  →        3.24 s    (+8.11%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       32.74 ms →       48.48 ms  (+48.08%) |       1   →       1              |       32.74 ms →       48.48 ms  (+48.08%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      141.85 ms →      455.20 ms (+220.89%) |       1   →       1              |      141.85 ms →      455.20 ms (+220.89%) | 
- │ │ ├ sirius::Atom_type::init                                         |       59.22 ms →      215.92 ms (+264.61%) |       2   →       2              |      118.44 ms →      431.84 ms (+264.61%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.33 ms →       23.28 ms   (-0.21%) |       1   →       1              |       23.33 ms →       23.28 ms   (-0.21%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.93 ms →        6.26 ms   (+5.55%) |       1   →       1              |        5.93 ms →        6.26 ms   (+5.55%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.36 ms →       16.97 ms   (-2.23%) |       1   →       1              |       17.36 ms →       16.97 ms   (-2.23%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.33 ms →       16.95 ms   (-2.21%) |       1   →       1              |       17.33 ms →       16.95 ms   (-2.21%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.15 ms   (-0.32%) |       1   →       1              |        4.17 ms →        4.15 ms   (-0.32%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (-0.15%) |       1   →       1              |        2.34 ms →        2.34 ms   (-0.15%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.75 μs →      102.67 μs   (-3.82%) |       1   →       1              |      106.75 μs →      102.67 μs   (-3.82%) | 
  │ └ sirius::Simulation_context::update                                |        2.78 s  →        2.70 s    (-3.07%) |       1   →       1              |        2.78 s  →        2.70 s    (-3.07%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.47 ms →       10.86 ms   (-5.30%) |       1   →       1              |       11.47 ms →       10.86 ms   (-5.30%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.79 ms →        4.49 ms   (-6.28%) |       1   →       1              |        4.79 ms →        4.49 ms   (-6.28%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.64 ms →        6.33 ms   (-4.68%) |       1   →       1              |        6.64 ms →        6.33 ms   (-4.68%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.62 ms →        6.31 ms   (-4.69%) |       1   →       1              |        6.62 ms →        6.31 ms   (-4.69%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.12 ms →        3.82 ms   (-7.27%) |       1   →       1              |        4.12 ms →        3.82 ms   (-7.27%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.19%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.19%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.14 μs →       99.09 μs   (-1.04%) |       1   →       1              |      100.14 μs →       99.09 μs   (-1.04%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.61 ms →       64.44 ms   (+2.93%) |       2   →       2              |      125.21 ms →      128.88 ms   (+2.93%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.12 ms →        5.18 ms   (+1.10%) |       2   →       2              |       10.25 ms →       10.36 ms   (+1.10%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.52 ms   (+0.82%) |       1   →       1              |        4.48 ms →        4.52 ms   (+0.82%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.67 ms →       21.98 ms   (+1.43%) |       2   →       2              |       43.34 ms →       43.96 ms   (+1.43%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.79 ms →       15.28 ms   (+3.32%) |       2   →       2              |       29.58 ms →       30.56 ms   (+3.32%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.83 ms →       20.29 ms   (+2.30%) |       4   →       4              |       79.33 ms →       81.16 ms   (+2.30%) | 
  │   ├ sddk::Gvec::init                                                |      172.97 ms →      171.69 ms   (-0.74%) |       2   →       2              |      345.94 ms →      343.39 ms   (-0.74%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.76 ms →      129.08 ms   (-1.28%) |       2   →       2              |      261.52 ms →      258.16 ms   (-1.28%) | 
  │   ├ sddk::Gvec_shells                                               |      174.17 ms →      180.61 ms   (+3.70%) |       1   →       1              |      174.17 ms →      180.61 ms   (+3.70%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.39 ms →        1.35 ms   (-2.45%) |       1   →       1              |        1.39 ms →        1.35 ms   (-2.45%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      306.15 ms →      293.50 ms   (-4.13%) |       2   →       2              |      612.30 ms →      587.00 ms   (-4.13%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.52 ms →       35.61 ms   (+0.23%) |       1   →       1              |       35.52 ms →       35.61 ms   (+0.23%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.93 μs →        2.14 μs  (-26.92%) |       4   →       4              |       11.74 μs →        8.58 μs  (-26.92%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.43 ms →       35.51 ms   (+0.20%) |       1   →       1              |       35.43 ms →       35.51 ms   (+0.20%) | 
  │   └ sirius::K_point::initialize                                     |       35.34 ms →       35.41 ms   (+0.18%) |       1   →       1              |       35.34 ms →       35.41 ms   (+0.18%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.13 ms →       17.92 ms   (-1.14%) |       1   →       1              |       18.13 ms →       17.92 ms   (-1.14%) | 
  │     │ └ sddk::Gvec::init                                            |        8.15 ms →        8.03 ms   (-1.45%) |       1   →       1              |        8.15 ms →        8.03 ms   (-1.45%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        7.20 μs →        6.40 μs  (-11.14%) |       1   →       1              |        7.20 μs →        6.40 μs  (-11.14%) | 
  │     └ sirius::K_point::update                                       |       12.39 ms →       12.68 ms   (+2.26%) |       1   →       1              |       12.39 ms →       12.68 ms   (+2.26%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.33 ms   (+3.94%) |       1   →       1              |        6.09 ms →        6.33 ms   (+3.94%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.47 ms →        3.70 ms   (+6.69%) |       1   →       1              |        3.47 ms →        3.70 ms   (+6.69%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.58 ms →        5.15 ms   (-7.72%) |       2   →       2              |       11.16 ms →       10.30 ms   (-7.72%) | 
  ├ sirius::Potential                                                   |      172.87 ms →      159.38 ms   (-7.80%) |       1   →       1              |      172.87 ms →      159.38 ms   (-7.80%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        6.50 ms →        5.79 ms  (-10.79%) |       6   →       6              |       38.98 ms →       34.77 ms  (-10.79%) | 
  │ └ sirius::Potential::update                                         |      133.12 ms →      123.89 ms   (-6.93%) |       1   →       1              |      133.12 ms →      123.89 ms   (-6.93%) | 
  │   └ sirius::Potential::generate_local_potential                     |      132.30 ms →      123.17 ms   (-6.90%) |       1   →       1              |      132.30 ms →      123.17 ms   (-6.90%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      125.50 ms →      110.47 ms  (-11.97%) |       1   →       1              |      125.50 ms →      110.47 ms  (-11.97%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.26 ms →       11.77 ms  (+88.02%) |       1   →       1              |        6.26 ms →       11.77 ms  (+88.02%) | 
  ├ sirius::Density                                                     |      141.84 ms →      136.55 ms   (-3.73%) |       1   →       1              |      141.84 ms →      136.55 ms   (-3.73%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.28 ms →        5.09 ms   (-3.69%) |       2   →       2              |       10.57 ms →       10.18 ms   (-3.69%) | 
  │ └ sirius::Density::update                                           |      130.96 ms →      126.11 ms   (-3.71%) |       1   →       1              |      130.96 ms →      126.11 ms   (-3.71%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      130.50 ms →      125.70 ms   (-3.68%) |       1   →       1              |      130.50 ms →      125.70 ms   (-3.68%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       102.57 μs            |                   1              |                       102.57 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      123.80 ms →      112.40 ms   (-9.21%) |       1   →       1              |      123.80 ms →      112.40 ms   (-9.21%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.24 ms →       12.74 ms (+104.11%) |       1   →       1              |        6.24 ms →       12.74 ms (+104.11%) | 
  ├ sirius::Density::initial_density                                    |      176.71 ms →      175.07 ms   (-0.93%) |       1   →       1              |      176.71 ms →      175.07 ms   (-0.93%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.75 ms →      111.85 ms   (-8.88%) |       1   →       1              |      122.75 ms →      111.85 ms   (-8.88%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.70 ms →       10.50 ms  (+84.45%) |       2   →       2              |       11.39 ms →       21.01 ms  (+84.45%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.18 ms →        9.84 ms   (-3.30%) |       1   →       1              |       10.18 ms →        9.84 ms   (-3.30%) | 
  ├ sirius::Potential::generate                                         |      585.45 ms →      600.11 ms   (+2.50%) |       1   →       1              |      585.45 ms →      600.11 ms   (+2.50%) | 
  │ ├ sirius::Potential::poisson                                        |      138.50 ms →      136.88 ms   (-1.17%) |       1   →       1              |      138.50 ms →      136.88 ms   (-1.17%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.67 ms →       17.33 ms (+159.99%) |       1   →       1              |        6.67 ms →       17.33 ms (+159.99%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.81 ms →        9.95 ms   (-7.97%) |       1   →       1              |       10.81 ms →        9.95 ms   (-7.97%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.62 ms →        9.89 ms   (-6.93%) |       1   →       1              |       10.62 ms →        9.89 ms   (-6.93%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.62 ms →        9.88 ms   (-7.00%) |       1   →       1              |       10.62 ms →        9.88 ms   (-7.00%) | 
  │ ├ sirius::Periodic_function::add                                    |      574.57 μs →      552.49 μs   (-3.84%) |       2   →       2              |        1.15 ms →        1.10 ms   (-3.84%) | 
  │ ├ sirius::Potential::xc                                             |       50.94 ms →       53.90 ms   (+5.81%) |       1   →       1              |       50.94 ms →       53.90 ms   (+5.81%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.94 ms →       51.58 ms   (+1.26%) |       1   →       1              |       50.94 ms →       51.58 ms   (+1.26%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.73 ms →        5.60 ms   (-2.11%) |       2   →       2              |       11.45 ms →       11.21 ms   (-2.11%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.12 ms →        5.52 ms   (+7.91%) |       1   →       1              |        5.12 ms →        5.52 ms   (+7.91%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.75 ms →        5.88 ms   (+2.25%) |       1   →       1              |        5.75 ms →        5.88 ms   (+2.25%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.54 ms →       92.67 ms   (-0.93%) |       1   →       1              |       93.54 ms →       92.67 ms   (-0.93%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      294.19 ms →      308.33 ms   (+4.81%) |       1   →       1              |      294.19 ms →      308.33 ms   (+4.81%) | 
  ├ sirius::Hamiltonian0                                                |        8.44 ms →        8.42 ms   (-0.21%) |       1   →       1              |        8.44 ms →        8.42 ms   (-0.21%) | 
  │ ├ sirius::Local_operator                                            |        8.08 ms →        8.07 ms   (-0.19%) |       1   →       1              |        8.08 ms →        8.07 ms   (-0.19%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.71 ms   (-1.33%) |       1   →       1              |        4.77 ms →        4.71 ms   (-1.33%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.39 ms →        2.45 ms   (+2.43%) |       1   →       1              |        2.39 ms →        2.45 ms   (+2.43%) | 
  │ ├ sirius::Non_local_operator                                        |       62.57 μs →       63.55 μs   (+1.57%) |       2   →       2              |      125.14 μs →      127.11 μs   (+1.57%) | 
  │ ├ sirius::D_operator::initialize                                    |      103.21 μs →      100.33 μs   (-2.79%) |       1   →       1              |      103.21 μs →      100.33 μs   (-2.79%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.98 μs →       74.80 μs   (-2.83%) |       1   →       1              |       76.98 μs →       74.80 μs   (-2.83%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.86 s    (-0.52%) |       1   →       1              |        1.87 s  →        1.86 s    (-0.52%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.68 ms   (-0.13%) |       1   →       1              |       18.70 ms →       18.68 ms   (-0.13%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      200.31 μs →      173.38 μs  (-13.44%) |       1   →       1              |      200.31 μs →      173.38 μs  (-13.44%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.50 ms   (+0.02%) |       1   →       1              |       18.50 ms →       18.50 ms   (+0.02%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.84 s    (-0.52%) |       1   →       1              |        1.85 s  →        1.84 s    (-0.52%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      131.15 ms →      128.26 ms   (-2.21%) |       4   →       4              |      524.61 ms →      513.03 ms   (-2.21%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.28 ms →       51.51 ms   (-3.33%) |       1   →       1              |       53.28 ms →       51.51 ms   (-3.33%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.03 ms →       21.00 ms   (-0.15%) |       1   →       1              |       21.03 ms →       21.00 ms   (-0.15%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      637.05 ms →      634.40 ms   (-0.42%) |       1   →       1              |      637.05 ms →      634.40 ms   (-0.42%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.74 ms →      297.77 ms   (+0.01%) |       1   →       1              |      297.74 ms →      297.77 ms   (+0.01%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.45 μs →        3.19 μs   (-7.44%) |       1   →       1              |        3.45 μs →        3.19 μs   (-7.44%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.53 μs →        2.26 μs  (-10.72%) |       1   →       1              |        2.53 μs →        2.26 μs  (-10.72%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      437.00 ns →      394.00 ns   (-9.84%) |       1   →       1              |      437.00 ns →      394.00 ns   (-9.84%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      817.00 ns →      459.00 ns  (-43.82%) |       1   →       1              |      817.00 ns →      459.00 ns  (-43.82%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.21 ms   (-0.16%) |       1   →       1              |        9.23 ms →        9.21 ms   (-0.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.78 ms →      120.69 ms   (-0.90%) |       1   →       1              |      121.78 ms →      120.69 ms   (-0.90%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.13 ms →      103.35 ms   (-0.75%) |       2   →       2              |      208.26 ms →      206.70 ms   (-0.75%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.45 ms →       40.17 ms   (+4.47%) |       2   →       2              |       76.91 ms →       80.34 ms   (+4.47%) | 
  │ │ │ ├ sddk::inner                                                   |       37.89 ms                             |       2                          |       75.79 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       35.31 μs                             |       2                          |       70.61 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.60 ms            |                   2              |                        79.20 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        16.00 ns            |                   2              |                        32.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.12 ms            |                   2              |                        78.24 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        21.50 ns            |                   2              |                        43.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.07 ms →       56.27 ms   (+0.36%) |       1   →       1              |       56.07 ms →       56.27 ms   (+0.36%) | 
  │ │ ├ sddk::transform                                                 |       31.56 ms                             |       1                          |       31.56 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.13 μs                             |       1                          |       11.13 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.96 μs                             |       1                          |       11.96 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.82 ms            |                   1              |                        30.82 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.81 ms            |                   1              |                        30.81 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      555.00 ns →      357.00 ns  (-35.68%) |       1   →       1              |      555.00 ns →      357.00 ns  (-35.68%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      151.50 s  →      124.61 s   (-17.75%) |       1   →       1              |      151.50 s  →      124.61 s   (-17.75%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms →        5.75 ms   (-1.95%) |      19   →      19              |      111.33 ms →      109.16 ms   (-1.95%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        6.87 s  →        4.78 s   (-30.42%) |      22   →      26    (+18.18%) |      151.08 s  →      124.24 s   (-17.77%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.32 ms →        4.99 ms   (-6.22%) |      22   →      26    (+18.18%) |      117.09 ms →      129.77 ms  (+10.83%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.94 ms →        4.62 ms   (-6.53%) |      22   →      26    (+18.18%) |      108.64 ms →      120.01 ms  (+10.46%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.03 ms →      968.00 μs   (-5.85%) |      22   →      26    (+18.18%) |       22.62 ms →       25.17 ms  (+11.27%) | 
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.02 ms →        2.75 ms   (-8.84%) |      22   →      26    (+18.18%) |       66.46 ms →       71.60 ms   (+7.74%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       64.76 μs →       64.74 μs   (-0.03%) |      44   →      52    (+18.18%) |        2.85 ms →        3.37 ms  (+18.14%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      100.86 μs →       90.40 μs  (-10.37%) |      22   →      26    (+18.18%) |        2.22 ms →        2.35 ms   (+5.93%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       78.01 μs →       81.80 μs   (+4.87%) |      22   →      26    (+18.18%) |        1.72 ms →        2.13 ms  (+23.93%) | 
+ │ │ ├ sirius::Band::solve                                             |        4.89 s  →        2.80 s   (-42.66%) |      22   →      26    (+18.18%) |      107.59 s  →       72.91 s   (-32.24%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      155.17 μs →      155.22 μs   (+0.03%) |      22   →      26    (+18.18%) |        3.41 ms →        4.04 ms  (+18.22%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      148.89 μs →      147.23 μs   (-1.12%) |      22   →      26    (+18.18%) |        3.28 ms →        3.83 ms  (+16.86%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.88 μs →        6.06 μs  (+24.04%) |      22   →      26    (+18.18%) |      107.41 μs →      157.45 μs  (+46.59%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        4.84 s  →        2.64 s   (-45.55%) |      22   →      26    (+18.18%) |      106.48 s  →       68.52 s   (-35.65%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      104.31 ms →       94.89 ms   (-9.03%) |      22   →      26    (+18.18%) |        2.29 s  →        2.47 s    (+7.51%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.20 ms →        7.71 ms  (-16.21%) |     132   →     156    (+18.18%) |        1.21 s  →        1.20 s    (-0.98%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.10 ms →        6.00 ms   (-1.58%) |      22   →      26    (+18.18%) |      134.12 ms →      156.01 ms  (+16.32%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      348.33 μs →      349.81 μs   (+0.43%) |      22   →      26    (+18.18%) |        7.66 ms →        9.10 ms  (+18.69%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.36 ms →        2.36 ms   (-0.28%) |      44   →      52    (+18.18%) |      104.00 ms →      122.57 ms  (+17.85%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        4.69 s  →        2.50 s   (-46.77%) |      22   →      26    (+18.18%) |      103.26 s  →       64.96 s   (-37.09%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      157.49 ms →      127.10 ms  (-19.30%) |     312   →     278    (-10.90%) |       49.14 s  →       35.33 s   (-28.09%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       65.44 ms →       51.13 ms  (-21.87%) |     312   →     278    (-10.90%) |       20.42 s  →       14.21 s   (-30.38%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.81 μs →        1.99 μs   (+9.86%) |     312   →     278    (-10.90%) |      563.89 μs →      552.00 μs   (-2.11%) | 
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.54 μs →        1.70 μs   (+9.80%) |     312   →     278    (-10.90%) |      481.93 μs →      471.50 μs   (-2.16%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      292.18 ns →      432.32 ns  (+47.96%) |     312   →     278    (-10.90%) |       91.16 μs →      120.18 μs  (+31.84%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      426.95 ns →      614.35 ns  (+43.89%) |     312   →     278    (-10.90%) |      133.21 μs →      170.79 μs  (+28.21%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.53 ms →        7.42 ms   (-1.46%) |     312   →     278    (-10.90%) |        2.35 s  →        2.06 s   (-12.20%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       28.05 ms →       22.83 ms  (-18.61%) |     312   →     278    (-10.90%) |        8.75 s  →        6.35 s   (-27.48%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       28.23 ms →       22.85 ms  (-19.04%) |     624   →     556    (-10.90%) |       17.61 s  →       12.70 s   (-27.87%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       45.58 ms →       34.17 ms  (-25.04%) |     312   →     278    (-10.90%) |       14.22 s  →        9.50 s   (-33.21%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        6.33 ms                             |     602                          |        3.81 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       22.17 μs                             |     602                          |       13.35 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         5.93 ms            |                 530              |                         3.14 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        76.21 ns            |                 530              |                        40.39 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         4.82 ms            |                 530              |                         2.56 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        60.20 ns            |                 530              |                        31.91 μs            | 
! │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      608.66 μs →      615.44 μs   (+1.11%) |     312   →     278    (-10.90%) |      189.90 ms →      171.09 ms   (-9.90%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.04 ms →        9.52 ms   (-5.16%) |     312   →     278    (-10.90%) |        3.13 s  →        2.65 s   (-15.50%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       24.45 ms                             |     290                          |        7.09 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.60 μs                             |     290                          |        5.10 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        6.84 μs                             |     870                          |        5.95 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.04 ms            |                 252              |                         3.54 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.68 ms            |                 756              |                         3.54 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       11.08 ms →       10.29 ms   (-7.16%) |     312   →     278    (-10.90%) |        3.46 s  →        2.86 s   (-17.28%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.79 ms                             |     312                          |        3.37 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.91 μs                             |     312                          |        6.84 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        10.02 ms            |                 278              |                         2.79 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        45.44 ns            |                 278              |                        12.63 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         8.91 ms            |                 278              |                         2.48 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        71.81 ns            |                 278              |                        19.96 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       46.40 ms →       34.81 ms  (-24.98%) |     312   →     278    (-10.90%) |       14.48 s  →        9.68 s   (-33.16%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       64.40 ms →       13.43 ms  (-79.14%) |     297   →     269     (-9.43%) |       19.13 s  →        3.61 s   (-81.11%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       57.10 ms                             |     297                          |       16.96 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       12.95 μs                             |     297                          |        3.85 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        8.75 μs                             |     594                          |        5.20 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        12.13 ms            |                 259              |                         3.14 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         6.06 ms            |                 518              |                         3.14 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        7.26 ms →        1.59 ms  (-78.15%) |     297   →     259    (-12.79%) |        2.16 s  →      410.96 ms  (-80.94%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       35.87 ms →       74.89 ms (+108.78%) |      79   →      53    (-32.91%) |        2.83 s  →        3.97 s   (+40.07%) | 
  │ │ │ │     ├ sddk::transform                                         |       35.41 ms                             |      79                          |        2.80 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |        7.75 μs                             |      79                          |      612.07 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |        9.83 μs                             |      79                          |      776.65 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        49.39 ms            |                  80              |                         3.95 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        36.92 ms            |                 107              |                         3.95 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      442.73 ns →      661.58 ns  (+49.43%) |      22   →      26    (+18.18%) |        9.74 μs →       17.20 μs  (+76.60%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.92 μs →       29.80 μs   (-0.38%) |      22   →      26    (+18.18%) |      658.16 μs →      774.83 μs  (+17.73%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      620.52 μs →      617.85 μs   (-0.43%) |      22   →      26    (+18.18%) |       13.65 ms →       16.06 ms  (+17.67%) | 
- │ │ ├ sirius::Density::generate                                       |      775.42 ms →      767.15 ms   (-1.07%) |      22   →      26    (+18.18%) |       17.06 s  →       19.95 s   (+16.92%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      400.88 ms →      401.98 ms   (+0.28%) |      22   →      26    (+18.18%) |        8.82 s  →       10.45 s   (+18.51%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        9.46 μs →        8.79 μs   (-7.09%) |      22   →      26    (+18.18%) |      208.10 μs →      228.49 μs   (+9.80%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.59 μs →        8.25 μs   (-3.93%) |      22   →      26    (+18.18%) |      188.88 μs →      214.45 μs  (+13.53%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.74 ms →      100.20 ms   (+0.46%) |      22   →      26    (+18.18%) |        2.19 s  →        2.61 s   (+18.73%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.91 μs →        7.85 μs   (-0.81%) |      22   →      26    (+18.18%) |      174.04 μs →      204.02 μs  (+17.22%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.11 ms   (-0.09%) |      22   →      26    (+18.18%) |      156.64 ms →      184.95 ms  (+18.07%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.68 ms →       91.16 ms   (+0.53%) |      22   →      26    (+18.18%) |        2.00 s  →        2.37 s   (+18.81%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      648.32 ns →      813.50 ns  (+25.48%) |      22   →      26    (+18.18%) |       14.26 μs →       21.15 μs  (+48.29%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.16 ms →      164.68 ms   (+1.55%) |      22   →      26    (+18.18%) |        3.57 s  →        4.28 s   (+20.01%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.36%) |      22   →      26    (+18.18%) |       36.16 ms →       42.58 ms  (+17.75%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       88.30 ms →       88.23 ms   (-0.09%) |      22   →      26    (+18.18%) |        1.94 s  →        2.29 s   (+18.08%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.07 ms →       88.00 ms   (-0.08%) |      22   →      26    (+18.18%) |        1.94 s  →        2.29 s   (+18.09%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      281.66 ms →      271.61 ms   (-3.57%) |      22   →      26    (+18.18%) |        6.20 s  →        7.06 s   (+13.96%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      281.66 ms →      271.61 ms   (-3.57%) |      22   →      26    (+18.18%) |        6.20 s  →        7.06 s   (+13.97%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.29 ms →       24.41 ms   (+0.49%) |      22   →      26    (+18.18%) |      534.49 ms →      634.78 ms  (+18.76%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      233.22 ms →      223.18 ms   (-4.31%) |      22   →      26    (+18.18%) |        5.13 s  →        5.80 s   (+13.09%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.96 ms →       22.83 ms   (-0.60%) |      22   →      26    (+18.18%) |      505.19 ms →      593.47 ms  (+17.47%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.00 ms →       81.07 ms   (+0.08%) |      22   →      26    (+18.18%) |        1.78 s  →        2.11 s   (+18.28%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.28 ms →        8.89 ms   (+7.41%) |      22   →      26    (+18.18%) |      182.08 ms →      231.13 ms  (+26.94%) | 
- │ │ ├ sirius::Density::mix                                            |      212.15 ms →      214.64 ms   (+1.18%) |      22   →      26    (+18.18%) |        4.67 s  →        5.58 s   (+19.57%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      976.40 μs →      955.59 μs   (-2.13%) |      22   →      26    (+18.18%) |       21.48 ms →       24.85 ms  (+15.66%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.63 ms →       10.36 ms   (-2.59%) |     274   →     334    (+21.90%) |        2.91 s  →        3.46 s   (+18.74%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.34 ms →        9.92 ms   (-4.11%) |     274   →     334    (+21.90%) |        2.83 s  →        3.31 s   (+16.88%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.34 ms →        9.92 ms   (-4.11%) |     274   →     334    (+21.90%) |        2.83 s  →        3.31 s   (+16.89%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.17 ms →        7.60 ms  (+23.18%) |      22   →      26    (+18.18%) |      135.75 ms →      197.61 ms  (+45.57%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.31 ms →        6.75 ms  (+27.10%) |      22   →      26    (+18.18%) |      116.93 ms →      175.63 ms  (+50.20%) | 
- │ │ ├ sirius::Potential::generate                                     |      571.78 ms →      588.83 ms   (+2.98%) |      22   →      26    (+18.18%) |       12.58 s  →       15.31 s   (+21.71%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      138.60 ms →      137.18 ms   (-1.03%) |      22   →      26    (+18.18%) |        3.05 s  →        3.57 s   (+16.97%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        6.63 ms →       16.96 ms (+155.71%) |      22   →      26    (+18.18%) |      145.90 ms →      440.93 ms (+202.21%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.95 ms →       10.32 ms   (-5.77%) |      22   →      26    (+18.18%) |      240.87 ms →      268.24 ms  (+11.36%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.43 ms →        9.92 ms   (-4.89%) |      22   →      26    (+18.18%) |      229.56 ms →      258.03 ms  (+12.40%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.43 ms →        9.92 ms   (-4.89%) |      22   →      26    (+18.18%) |      229.55 ms →      258.01 ms  (+12.40%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      570.54 μs →      554.99 μs   (-2.73%) |      44   →      52    (+18.18%) |       25.10 ms →       28.86 ms  (+14.96%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       47.11 ms →       49.35 ms   (+4.77%) |      22   →      26    (+18.18%) |        1.04 s  →        1.28 s   (+23.82%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.11 ms →       46.98 ms   (-0.26%) |      22   →      26    (+18.18%) |        1.04 s  →        1.22 s   (+17.87%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms →        3.00 ms   (-1.04%) |      44   →      52    (+18.18%) |      133.33 ms →      155.93 ms  (+16.96%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.17 ms →        5.66 ms   (+9.60%) |      22   →      26    (+18.18%) |      113.64 ms →      147.20 ms  (+29.53%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.32 ms →        6.58 ms   (+4.10%) |      22   →      26    (+18.18%) |      139.07 ms →      171.10 ms  (+23.03%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       90.91 ms   (-0.00%) |      22   →      26    (+18.18%) |        2.00 s  →        2.36 s   (+18.18%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.39 ms →      302.42 ms   (+5.60%) |      22   →      26    (+18.18%) |        6.30 s  →        7.86 s   (+24.79%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      289.79 ms →      275.88 ms   (-4.80%) |      22   →      26    (+18.18%) |        6.38 s  →        7.17 s   (+12.51%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      289.79 ms →      275.88 ms   (-4.80%) |      22   →      26    (+18.18%) |        6.38 s  →        7.17 s   (+12.51%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.57 ms →       27.30 ms   (-0.98%) |      22   →      26    (+18.18%) |      606.63 ms →      709.90 ms  (+17.02%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      234.72 ms →      220.91 ms   (-5.88%) |      22   →      26    (+18.18%) |        5.16 s  →        5.74 s   (+11.23%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.68 ms →       23.88 ms   (+0.81%) |      22   →      26    (+18.18%) |      521.06 ms →      620.77 ms  (+19.14%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.53 ms →        6.04 ms   (+9.15%) |      22   →      26    (+18.18%) |      121.76 ms →      157.07 ms  (+28.99%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.81 ms →       10.25 ms   (-5.16%) |     154   →     182    (+18.18%) |        1.66 s  →        1.87 s   (+12.08%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |       10.16 ms →        9.72 ms   (-4.32%) |     154   →     182    (+18.18%) |        1.56 s  →        1.77 s   (+13.07%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.16 ms →        9.72 ms   (-4.32%) |     154   →     182    (+18.18%) |        1.56 s  →        1.77 s   (+13.08%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.10 ms →       11.38 ms  (+12.59%) |      66   →      78    (+18.18%) |      666.92 ms →      887.43 ms  (+33.06%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.68 ms →       10.13 ms   (+4.62%) |      66   →      78    (+18.18%) |      638.72 ms →      789.75 ms  (+23.65%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        9.94 ms →        9.99 ms   (+0.58%) |      22   →      26    (+18.18%) |      218.57 ms →      259.80 ms  (+18.86%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      112.84 μs →      110.94 μs   (-1.69%) |      22   →      26    (+18.18%) |        2.48 ms →        2.88 ms  (+16.19%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.77 μs →      105.76 μs   (-1.86%) |      22   →      26    (+18.18%) |        2.37 ms →        2.75 ms  (+15.98%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.50 ms →        5.10 ms  (-31.99%) |       2   →       2              |       15.01 ms →       10.21 ms  (-31.99%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.42 ms →        9.92 ms   (-4.77%) |       6   →       6              |       62.50 ms →       59.52 ms   (-4.77%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.11 ms →        9.84 ms   (-2.61%) |       6   →       6              |       60.64 ms →       59.06 ms   (-2.61%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.11 ms →        9.84 ms   (-2.61%) |       6   →       6              |       60.64 ms →       59.06 ms   (-2.61%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.97 ms →       10.22 ms   (+2.48%) |       3   →       3              |       29.92 ms →       30.66 ms   (+2.48%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.62 ms →       10.04 ms   (+4.30%) |       3   →       3              |       28.87 ms →       30.11 ms   (+4.30%) | 
  ├ sirius::Periodic_function|inner                                     |       10.35 ms →        9.75 ms   (-5.77%) |       2   →       2              |       20.70 ms →       19.50 ms   (-5.77%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.09 ms →        9.64 ms   (-4.49%) |       2   →       2              |       20.18 ms →       19.28 ms   (-4.49%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.09 ms →        9.64 ms   (-4.49%) |       2   →       2              |       20.18 ms →       19.27 ms   (-4.49%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.70 ms →       10.15 ms   (+4.62%) |       1   →       1              |        9.70 ms →       10.15 ms   (+4.62%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.60 ms →       10.11 ms   (+5.31%) |       1   →       1              |        9.60 ms →       10.11 ms   (+5.31%) | 
  └ sirius::finalize                                                    |      205.97 ms →      185.75 ms   (-9.82%) |       1   →       1              |      205.97 ms →      185.75 ms   (-9.82%) | 
  ====================================================================================================================================================================================================
```
