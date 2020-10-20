# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      166.44 s  →      129.43 s   (-22.23%) |       1   →       1              |      166.44 s  →      129.43 s   (-22.23%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.75 s    (+1.91%) |       1   →       1              |        2.69 s  →        2.75 s    (+1.91%) | 
  ├ sirius::Simulation_context::initialize                              |        3.02 s  →        2.93 s    (-2.86%) |       1   →       1              |        3.02 s  →        2.93 s    (-2.86%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |        7.66 ms →      225.23 μs  (-97.06%) |       1   →       1              |        7.66 ms →      225.23 μs  (-97.06%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      177.74 ms →      221.32 ms  (+24.52%) |       1   →       1              |      177.74 ms →      221.32 ms  (+24.52%) | 
- │ │ ├ sirius::Atom_type::init                                         |       76.83 ms →       98.46 ms  (+28.15%) |       2   →       2              |      153.66 ms →      196.93 ms  (+28.15%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.99 ms →       24.31 ms   (+1.34%) |       1   →       1              |       23.99 ms →       24.31 ms   (+1.34%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.40 ms →        6.31 ms   (-1.47%) |       1   →       1              |        6.40 ms →        6.31 ms   (-1.47%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.55 ms →       17.96 ms   (+2.36%) |       1   →       1              |       17.55 ms →       17.96 ms   (+2.36%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.52 ms →       17.94 ms   (+2.40%) |       1   →       1              |       17.52 ms →       17.94 ms   (+2.40%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.15 ms   (-0.44%) |       1   →       1              |        4.17 ms →        4.15 ms   (-0.44%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.30 ms   (-1.59%) |       1   →       1              |        2.34 ms →        2.30 ms   (-1.59%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.73 μs →      118.71 μs  (+13.35%) |       1   →       1              |      104.73 μs →      118.71 μs  (+13.35%) | 
  │ └ sirius::Simulation_context::update                                |        2.79 s  →        2.67 s    (-4.45%) |       1   →       1              |        2.79 s  →        2.67 s    (-4.45%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.99 ms →       10.66 ms   (-3.02%) |       1   →       1              |       10.99 ms →       10.66 ms   (-3.02%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.59 ms →        4.23 ms   (-7.77%) |       1   →       1              |        4.59 ms →        4.23 ms   (-7.77%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.39 ms   (+0.37%) |       1   →       1              |        6.36 ms →        6.39 ms   (+0.37%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.37 ms   (+0.39%) |       1   →       1              |        6.34 ms →        6.37 ms   (+0.39%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.85 ms →        3.89 ms   (+1.03%) |       1   →       1              |        3.85 ms →        3.89 ms   (+1.03%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.55%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.55%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      101.71 μs →       99.31 μs   (-2.36%) |       1   →       1              |      101.71 μs →       99.31 μs   (-2.36%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |       83.94 ms →       62.96 ms  (-24.99%) |       2   →       2              |      167.87 ms →      125.93 ms  (-24.99%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.15 ms   (+0.10%) |       2   →       2              |       10.29 ms →       10.30 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (-0.08%) |       1   →       1              |        4.48 ms →        4.48 ms   (-0.08%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.78 ms →       21.80 ms   (+0.10%) |       2   →       2              |       43.56 ms →       43.60 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.82 ms   (-0.00%) |       2   →       2              |       29.64 ms →       29.64 ms   (-0.00%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.68 ms →       19.87 ms   (+1.00%) |       4   →       4              |       78.70 ms →       79.49 ms   (+1.00%) | 
  │   ├ sddk::Gvec::init                                                |      189.18 ms →      172.19 ms   (-8.98%) |       2   →       2              |      378.37 ms →      344.39 ms   (-8.98%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      141.64 ms →      129.56 ms   (-8.53%) |       2   →       2              |      283.28 ms →      259.12 ms   (-8.53%) | 
+ │   ├ sddk::Gvec_shells                                               |      201.61 ms →      168.60 ms  (-16.37%) |       1   →       1              |      201.61 ms →      168.60 ms  (-16.37%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.35 ms →        1.32 ms   (-2.31%) |       1   →       1              |        1.35 ms →        1.32 ms   (-2.31%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.31 ms →      293.95 ms   (-0.12%) |       2   →       2              |      588.61 ms →      587.90 ms   (-0.12%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       39.16 ms →       36.14 ms   (-7.72%) |       1   →       1              |       39.16 ms →       36.14 ms   (-7.72%) | 
+ │ ├ sirius::K_point::K_point                                          |        3.13 μs →        2.46 μs  (-21.27%) |       4   →       4              |       12.50 μs →        9.84 μs  (-21.27%) | 
  │ └ sirius::K_point_set::initialize                                   |       39.07 ms →       36.04 ms   (-7.77%) |       1   →       1              |       39.07 ms →       36.04 ms   (-7.77%) | 
  │   └ sirius::K_point::initialize                                     |       38.99 ms →       35.93 ms   (-7.84%) |       1   →       1              |       38.99 ms →       35.93 ms   (-7.84%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       20.27 ms →       18.54 ms   (-8.53%) |       1   →       1              |       20.27 ms →       18.54 ms   (-8.53%) | 
  │     │ └ sddk::Gvec::init                                            |        8.96 ms →        8.25 ms   (-7.85%) |       1   →       1              |        8.96 ms →        8.25 ms   (-7.85%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.86 μs →       10.14 μs   (+2.78%) |       1   →       1              |        9.86 μs →       10.14 μs   (+2.78%) | 
  │     └ sirius::K_point::update                                       |       13.09 ms →       12.55 ms   (-4.11%) |       1   →       1              |       13.09 ms →       12.55 ms   (-4.11%) | 
  │       └ sirius::Beta_projectors                                     |        6.05 ms →        6.34 ms   (+4.82%) |       1   →       1              |        6.05 ms →        6.34 ms   (+4.82%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.45 ms →        3.71 ms   (+7.50%) |       1   →       1              |        3.45 ms →        3.71 ms   (+7.50%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.16 ms →        5.47 ms   (+5.92%) |       2   →       2              |       10.32 ms →       10.93 ms   (+5.92%) | 
  ├ sirius::Potential                                                   |      168.29 ms →      153.04 ms   (-9.06%) |       1   →       1              |      168.29 ms →      153.04 ms   (-9.06%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.79 ms →        5.90 ms   (+1.94%) |       6   →       6              |       34.75 ms →       35.43 ms   (+1.94%) | 
+ │ └ sirius::Potential::update                                         |      132.84 ms →      116.88 ms  (-12.01%) |       1   →       1              |      132.84 ms →      116.88 ms  (-12.01%) | 
+ │   └ sirius::Potential::generate_local_potential                     |      132.14 ms →      116.14 ms  (-12.11%) |       1   →       1              |      132.14 ms →      116.14 ms  (-12.11%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.91 ms →      106.26 ms   (-5.05%) |       1   →       1              |      111.91 ms →      106.26 ms   (-5.05%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       19.68 ms →        8.98 ms  (-54.36%) |       1   →       1              |       19.68 ms →        8.98 ms  (-54.36%) | 
  ├ sirius::Density                                                     |      140.05 ms →      128.33 ms   (-8.37%) |       1   →       1              |      140.05 ms →      128.33 ms   (-8.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.10 ms →        5.37 ms   (+5.27%) |       2   →       2              |       10.20 ms →       10.74 ms   (+5.27%) | 
  │ └ sirius::Density::update                                           |      129.58 ms →      117.29 ms   (-9.48%) |       1   →       1              |      129.58 ms →      117.29 ms   (-9.48%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.16 ms →      116.85 ms   (-9.53%) |       1   →       1              |      129.16 ms →      116.85 ms   (-9.53%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       108.11 μs            |                   1              |                       108.11 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.24 ms →      108.77 ms   (-3.09%) |       1   →       1              |      112.24 ms →      108.77 ms   (-3.09%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.48 ms →        7.51 ms  (-54.45%) |       1   →       1              |       16.48 ms →        7.51 ms  (-54.45%) | 
  ├ sirius::Density::initial_density                                    |      175.15 ms →      164.67 ms   (-5.98%) |       1   →       1              |      175.15 ms →      164.67 ms   (-5.98%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.48 ms →      108.73 ms   (-1.59%) |       1   →       1              |      110.48 ms →      108.73 ms   (-1.59%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.94 ms →        6.09 ms  (-44.37%) |       2   →       2              |       21.88 ms →       12.17 ms  (-44.37%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.57 ms →       10.96 ms   (+3.67%) |       1   →       1              |       10.57 ms →       10.96 ms   (+3.67%) | 
  ├ sirius::Potential::generate                                         |      584.06 ms →      581.14 ms   (-0.50%) |       1   →       1              |      584.06 ms →      581.14 ms   (-0.50%) | 
  │ ├ sirius::Potential::poisson                                        |      137.55 ms →      124.70 ms   (-9.34%) |       1   →       1              |      137.55 ms →      124.70 ms   (-9.34%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       15.97 ms →        6.86 ms  (-57.02%) |       1   →       1              |       15.97 ms →        6.86 ms  (-57.02%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.85 ms →       10.57 ms   (-2.63%) |       1   →       1              |       10.85 ms →       10.57 ms   (-2.63%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.25 ms →       10.05 ms   (-1.92%) |       1   →       1              |       10.25 ms →       10.05 ms   (-1.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.24 ms →       10.04 ms   (-1.98%) |       1   →       1              |       10.24 ms →       10.04 ms   (-1.98%) | 
  │ ├ sirius::Periodic_function::add                                    |      557.13 μs →      559.90 μs   (+0.50%) |       2   →       2              |        1.11 ms →        1.12 ms   (+0.50%) | 
  │ ├ sirius::Potential::xc                                             |       52.21 ms →       54.88 ms   (+5.11%) |       1   →       1              |       52.21 ms →       54.88 ms   (+5.11%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.21 ms →       52.47 ms   (+0.49%) |       1   →       1              |       52.21 ms →       52.47 ms   (+0.49%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.68 ms →        5.76 ms   (+1.40%) |       2   →       2              |       11.36 ms →       11.52 ms   (+1.40%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.27 ms →        5.45 ms   (+3.48%) |       1   →       1              |        5.27 ms →        5.45 ms   (+3.48%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.73 ms →        5.99 ms   (+4.64%) |       1   →       1              |        5.73 ms →        5.99 ms   (+4.64%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.70 ms →       93.68 ms   (+1.06%) |       1   →       1              |       92.70 ms →       93.68 ms   (+1.06%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.44 ms →      299.37 ms   (+2.02%) |       1   →       1              |      293.44 ms →      299.37 ms   (+2.02%) | 
  ├ sirius::Hamiltonian0                                                |        8.39 ms →        8.45 ms   (+0.76%) |       1   →       1              |        8.39 ms →        8.45 ms   (+0.76%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        8.10 ms   (+0.84%) |       1   →       1              |        8.03 ms →        8.10 ms   (+0.84%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.68 ms →        4.80 ms   (+2.58%) |       1   →       1              |        4.68 ms →        4.80 ms   (+2.58%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        2.38 ms   (-2.15%) |       1   →       1              |        2.43 ms →        2.38 ms   (-2.15%) | 
  │ ├ sirius::Non_local_operator                                        |       62.69 μs →       62.32 μs   (-0.60%) |       2   →       2              |      125.39 μs →      124.64 μs   (-0.60%) | 
  │ ├ sirius::D_operator::initialize                                    |      101.10 μs →       94.87 μs   (-6.16%) |       1   →       1              |      101.10 μs →       94.87 μs   (-6.16%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.81 μs →       76.20 μs   (-0.79%) |       1   →       1              |       76.81 μs →       76.20 μs   (-0.79%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.88 s  →        1.85 s    (-1.48%) |       1   →       1              |        1.88 s  →        1.85 s    (-1.48%) | 
  │ ├ sirius::Hamiltonian_k                                             |       19.76 ms →       18.69 ms   (-5.43%) |       1   →       1              |       19.76 ms →       18.69 ms   (-5.43%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      197.14 μs →      189.45 μs   (-3.90%) |       1   →       1              |      197.14 μs →      189.45 μs   (-3.90%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       19.56 ms →       18.49 ms   (-5.44%) |       1   →       1              |       19.56 ms →       18.49 ms   (-5.44%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.86 s  →        1.84 s    (-1.44%) |       1   →       1              |        1.86 s  →        1.84 s    (-1.44%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      129.06 ms →      126.88 ms   (-1.69%) |       4   →       4              |      516.25 ms →      507.51 ms   (-1.69%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.52 ms →       54.17 ms   (+1.23%) |       1   →       1              |       53.52 ms →       54.17 ms   (+1.23%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.46 ms →       21.65 ms   (+0.88%) |       1   →       1              |       21.46 ms →       21.65 ms   (+0.88%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.47 ms →      635.46 ms   (-0.16%) |       1   →       1              |      636.47 ms →      635.46 ms   (-0.16%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.08 ms →      297.47 ms   (-0.21%) |       1   →       1              |      298.08 ms →      297.47 ms   (-0.21%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.33 μs →        3.20 μs   (-3.82%) |       1   →       1              |        3.33 μs →        3.20 μs   (-3.82%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.38 μs →        2.14 μs  (-10.37%) |       1   →       1              |        2.38 μs →        2.14 μs  (-10.37%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      492.00 ns →      342.00 ns  (-30.49%) |       1   →       1              |      492.00 ns →      342.00 ns  (-30.49%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      550.00 ns →      626.00 ns  (+13.82%) |       1   →       1              |      550.00 ns →      626.00 ns  (+13.82%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (+0.01%) |       1   →       1              |        9.22 ms →        9.22 ms   (+0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.65 ms →      120.53 ms   (-0.10%) |       1   →       1              |      120.65 ms →      120.53 ms   (-0.10%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.24 ms →      104.10 ms   (-0.13%) |       2   →       2              |      208.49 ms →      208.21 ms   (-0.13%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.36 ms →       40.10 ms   (+4.54%) |       2   →       2              |       76.72 ms →       80.20 ms   (+4.54%) | 
  │ │ │ ├ sddk::inner                                                   |       37.81 ms                             |       2                          |       75.63 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       29.75 μs                             |       2                          |       59.49 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.57 ms            |                   2              |                        79.14 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        35.50 ns            |                   2              |                        71.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.09 ms            |                   2              |                        78.19 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        26.50 ns            |                   2              |                        53.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       61.11 ms →       56.63 ms   (-7.32%) |       1   →       1              |       61.11 ms →       56.63 ms   (-7.32%) | 
  │ │ ├ sddk::transform                                                 |       31.55 ms                             |       1                          |       31.55 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       12.60 μs                             |       1                          |       12.60 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       13.70 μs                             |       1                          |       13.70 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.74 ms            |                   1              |                        30.74 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.73 ms            |                   1              |                        30.73 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      702.00 ns →      555.00 ns  (-20.94%) |       1   →       1              |      702.00 ns →      555.00 ns  (-20.94%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      156.34 s  →      119.77 s   (-23.39%) |       1   →       1              |      156.34 s  →      119.77 s   (-23.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.90 ms →        5.83 ms   (-1.18%) |      19   →      19              |      112.11 ms →      110.79 ms   (-1.18%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.59 s  →        4.56 s    (-0.51%) |      34   →      26    (-23.53%) |      155.99 s  →      118.68 s   (-23.92%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.52 ms →        5.43 ms  (+20.31%) |      34   →      26    (-23.53%) |      153.53 ms →      141.24 ms   (-8.00%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.12 ms →        5.07 ms  (+22.83%) |      34   →      26    (-23.53%) |      140.25 ms →      131.73 ms   (-6.07%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.01 ms →        1.03 ms   (+1.77%) |      34   →      26    (-23.53%) |       34.37 ms →       26.75 ms  (-22.17%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.21 ms →        3.15 ms  (+42.16%) |      34   →      26    (-23.53%) |       75.27 ms →       81.83 ms   (+8.71%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.92 μs →       64.51 μs   (-0.64%) |      68   →      52    (-23.53%) |        4.41 ms →        3.35 ms  (-24.02%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      106.34 μs →       88.46 μs  (-16.82%) |      34   →      26    (-23.53%) |        3.62 ms →        2.30 ms  (-36.39%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       80.44 μs →       77.26 μs   (-3.95%) |      34   →      26    (-23.53%) |        2.73 ms →        2.01 ms  (-26.55%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.61 s  →        2.60 s    (-0.63%) |      34   →      26    (-23.53%) |       88.88 s  →       67.54 s   (-24.01%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      169.83 μs →      155.57 μs   (-8.40%) |      34   →      26    (-23.53%) |        5.77 ms →        4.04 ms  (-29.95%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      162.20 μs →      148.59 μs   (-8.39%) |      34   →      26    (-23.53%) |        5.51 ms →        3.86 ms  (-29.95%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.79 μs →        5.03 μs  (-13.14%) |      34   →      26    (-23.53%) |      196.87 μs →      130.77 μs  (-33.57%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.55 s  →        2.46 s    (-3.65%) |      34   →      26    (-23.53%) |       86.69 s  →       63.88 s   (-26.32%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      102.82 ms →       94.96 ms   (-7.65%) |      34   →      26    (-23.53%) |        3.50 s  →        2.47 s   (-29.38%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.82 ms →        7.60 ms  (-13.84%) |     204   →     156    (-23.53%) |        1.80 s  →        1.19 s   (-34.11%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.94 ms →        5.99 ms   (+0.89%) |      34   →      26    (-23.53%) |      201.98 ms →      155.83 ms  (-22.85%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      348.70 μs →      347.19 μs   (-0.43%) |      34   →      26    (-23.53%) |       11.86 ms →        9.03 ms  (-23.86%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.32 ms →        2.31 ms   (-0.33%) |      68   →      52    (-23.53%) |      157.92 ms →      120.37 ms  (-23.78%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.40 s  →        2.32 s    (-3.52%) |      34   →      26    (-23.53%) |       81.76 s  →       60.32 s   (-26.22%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      112.06 ms →      136.18 ms  (+21.52%) |     338   →     262    (-22.49%) |       37.88 s  →       35.68 s    (-5.80%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.94 ms →       55.28 ms  (+25.80%) |     338   →     262    (-22.49%) |       14.85 s  →       14.48 s    (-2.48%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.30 μs →        1.80 μs  (-22.03%) |     338   →     262    (-22.49%) |      778.80 μs →      470.68 μs  (-39.56%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.90 μs →        1.50 μs  (-21.10%) |     338   →     262    (-22.49%) |      643.21 μs →      393.40 μs  (-38.84%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      418.43 ns →      375.10 ns  (-10.36%) |     338   →     262    (-22.49%) |      141.43 μs →       98.28 μs  (-30.51%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      577.03 ns →      447.41 ns  (-22.46%) |     338   →     262    (-22.49%) |      195.04 μs →      117.22 μs  (-39.90%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.37 ms →        7.45 ms   (+1.13%) |     338   →     262    (-22.49%) |        2.49 s  →        1.95 s   (-21.61%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.09 ms →       24.67 ms  (+22.82%) |     338   →     262    (-22.49%) |        6.79 s  →        6.46 s    (-4.80%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       20.32 ms →       24.38 ms  (+19.96%) |     676   →     524    (-22.49%) |       13.74 s  →       12.78 s    (-7.01%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       31.36 ms →       35.86 ms  (+14.35%) |     338   →     262    (-22.49%) |       10.60 s  →        9.40 s   (-11.36%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.66 ms                             |     642                          |        2.99 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.32 μs                             |     642                          |       17.54 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         6.22 ms            |                 498              |                         3.10 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        52.68 ns            |                 498              |                        26.24 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         5.11 ms            |                 498              |                         2.54 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        48.95 ns            |                 498              |                        24.37 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      536.36 μs →      667.99 μs  (+24.54%) |     338   →     262    (-22.49%) |      181.29 ms →      175.01 ms   (-3.46%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.57 ms →       10.31 ms  (+20.35%) |     338   →     262    (-22.49%) |        2.90 s  →        2.70 s    (-6.71%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       14.89 ms                             |     304                          |        4.53 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       23.10 μs                             |     304                          |        7.02 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       52.29 μs                             |     912                          |       47.68 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.50 ms            |                 236              |                         3.42 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.83 ms            |                 708              |                         3.42 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.86 ms →       10.39 ms   (+5.37%) |     338   →     262    (-22.49%) |        3.33 s  →        2.72 s   (-18.32%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.99 ms                             |     338                          |        3.04 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       33.72 μs                             |     338                          |       11.40 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        10.18 ms            |                 262              |                         2.67 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        28.42 ns            |                 262              |                         7.45 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         9.07 ms            |                 262              |                         2.38 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        47.39 ns            |                 262              |                        12.42 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       68.75 ms →       17.71 ms  (-74.23%) |     338   →     262    (-22.49%) |       23.24 s  →        4.64 s   (-80.03%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       14.40 ms →       13.14 ms   (-8.76%) |     328   →     252    (-23.17%) |        4.72 s  →        3.31 s   (-29.90%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.37 ms                             |     314                          |        4.20 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.29 μs                             |     314                          |        5.74 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       46.21 μs                             |     628                          |       29.02 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        11.71 ms            |                 242              |                         2.83 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.85 ms            |                 484              |                         2.83 s             | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.46 ms →        1.71 ms  (+17.76%) |     314   →     242    (-22.93%) |      457.21 ms →      414.97 ms   (-9.24%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.88 ms →       53.74 ms   (-2.07%) |      36   →      85   (+136.11%) |        1.98 s  →        4.57 s  (+131.22%) | 
  │ │ │ │     ├ sddk::transform                                         |       51.77 ms                             |      38                          |        1.97 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       13.55 μs                             |      38                          |      514.76 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       14.54 μs                             |      40                          |      581.49 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        31.45 ms            |                 144              |                         4.53 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        22.31 ms            |                 203              |                         4.53 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      501.74 ns →      422.81 ns  (-15.73%) |      34   →      26    (-23.53%) |       17.06 μs →       10.99 μs  (-35.56%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       35.16 μs →       34.50 μs   (-1.86%) |      34   →      26    (-23.53%) |        1.20 ms →      897.12 μs  (-24.95%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      616.56 μs →      606.90 μs   (-1.57%) |      34   →      26    (-23.53%) |       20.96 ms →       15.78 ms  (-24.73%) | 
+ │ │ ├ sirius::Density::generate                                       |      777.05 ms →      771.98 ms   (-0.65%) |      34   →      26    (-23.53%) |       26.42 s  →       20.07 s   (-24.03%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      403.69 ms →      402.48 ms   (-0.30%) |      34   →      26    (-23.53%) |       13.73 s  →       10.46 s   (-23.76%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.26 μs →        8.75 μs   (+5.90%) |      34   →      26    (-23.53%) |      280.87 μs →      227.46 μs  (-19.02%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.27 μs →        8.27 μs  (+13.77%) |      34   →      26    (-23.53%) |      247.08 μs →      214.96 μs  (-13.00%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.77 ms →      100.21 ms   (+0.44%) |      34   →      26    (-23.53%) |        3.39 s  →        2.61 s   (-23.19%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.55 μs →        7.81 μs   (+3.40%) |      34   →      26    (-23.53%) |      256.73 μs →      203.00 μs  (-20.93%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.04%) |      34   →      26    (-23.53%) |      242.01 ms →      185.00 ms  (-23.56%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.77 ms →       91.17 ms   (+0.44%) |      34   →      26    (-23.53%) |        3.09 s  →        2.37 s   (-23.20%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      566.91 ns →      521.27 ns   (-8.05%) |      34   →      26    (-23.53%) |       19.27 μs →       13.55 μs  (-29.69%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.95 ms →      163.68 ms   (-0.77%) |      34   →      26    (-23.53%) |        5.61 s  →        4.26 s   (-24.12%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.66 ms   (+0.77%) |      34   →      26    (-23.53%) |       55.91 ms →       43.09 ms  (-22.94%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.23 ms →       88.30 ms   (+0.08%) |      34   →      26    (-23.53%) |        3.00 s  →        2.30 s   (-23.46%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       87.99 ms →       88.07 ms   (+0.09%) |      34   →      26    (-23.53%) |        2.99 s  →        2.29 s   (-23.46%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.36 ms →      276.54 ms   (-1.36%) |      34   →      26    (-23.53%) |        9.53 s  →        7.19 s   (-24.57%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.36 ms →      276.54 ms   (-1.36%) |      34   →      26    (-23.53%) |        9.53 s  →        7.19 s   (-24.57%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.61 ms →       24.32 ms  (-14.99%) |      34   →      26    (-23.53%) |      972.75 ms →      632.38 ms  (-34.99%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      223.24 ms →      228.08 ms   (+2.17%) |      34   →      26    (-23.53%) |        7.59 s  →        5.93 s   (-21.87%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.30 ms →       22.94 ms  (-15.98%) |      34   →      26    (-23.53%) |      928.16 ms →      596.35 ms  (-35.75%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.23 ms →       80.75 ms   (-0.59%) |      34   →      26    (-23.53%) |        2.76 s  →        2.10 s   (-23.98%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.18 ms →        8.61 ms   (+5.26%) |      34   →      26    (-23.53%) |      278.24 ms →      223.95 ms  (-19.51%) | 
+ │ │ ├ sirius::Density::mix                                            |      215.09 ms →      220.63 ms   (+2.58%) |      34   →      26    (-23.53%) |        7.31 s  →        5.74 s   (-21.56%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      957.06 μs →      942.44 μs   (-1.53%) |      34   →      26    (-23.53%) |       32.54 ms →       24.50 ms  (-24.70%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.27 ms →       10.82 ms   (+5.30%) |     440   →     334    (-24.09%) |        4.52 s  →        3.61 s   (-20.07%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.93 ms →       10.36 ms   (+4.38%) |     440   →     334    (-24.09%) |        4.37 s  →        3.46 s   (-20.77%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.93 ms →       10.36 ms   (+4.38%) |     440   →     334    (-24.09%) |        4.37 s  →        3.46 s   (-20.77%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.71 ms →        7.56 ms  (+12.78%) |      34   →      26    (-23.53%) |      228.05 ms →      196.68 ms  (-13.76%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.88 ms →        6.74 ms  (+14.59%) |      34   →      26    (-23.53%) |      200.04 ms →      175.29 ms  (-12.37%) | 
+ │ │ ├ sirius::Potential::generate                                     |      570.86 ms →      566.42 ms   (-0.78%) |      34   →      26    (-23.53%) |       19.41 s  →       14.73 s   (-24.12%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.06 ms →      124.33 ms   (-9.29%) |      34   →      26    (-23.53%) |        4.66 s  →        3.23 s   (-30.63%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.82 ms →        6.49 ms  (-58.95%) |      34   →      26    (-23.53%) |      537.87 ms →      168.86 ms  (-68.61%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.34 ms →       10.41 ms   (+0.72%) |      34   →      26    (-23.53%) |      351.47 ms →      270.71 ms  (-22.98%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.99 ms →        9.99 ms   (+0.10%) |      34   →      26    (-23.53%) |      339.50 ms →      259.87 ms  (-23.46%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.98 ms →        9.99 ms   (+0.10%) |      34   →      26    (-23.53%) |      339.48 ms →      259.85 ms  (-23.46%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      555.86 μs →      576.00 μs   (+3.62%) |      68   →      52    (-23.53%) |       37.80 ms →       29.95 ms  (-20.76%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       45.55 ms →       49.33 ms   (+8.31%) |      34   →      26    (-23.53%) |        1.55 s  →        1.28 s   (-17.18%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       45.55 ms →       46.92 ms   (+3.02%) |      34   →      26    (-23.53%) |        1.55 s  →        1.22 s   (-21.22%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.26 ms →        3.08 ms (+145.41%) |      68   →      52    (-23.53%) |       85.47 ms →      160.40 ms  (+87.67%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |       12.03 ms →        5.30 ms  (-55.96%) |      34   →      26    (-23.53%) |      408.91 ms →      137.69 ms  (-66.33%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.92 ms →        6.58 ms  (-17.01%) |      34   →      26    (-23.53%) |      269.37 ms →      170.95 ms  (-36.54%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.93 ms →       90.92 ms   (-0.00%) |      34   →      26    (-23.53%) |        3.09 s  →        2.36 s   (-23.53%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      287.01 ms →      292.78 ms   (+2.01%) |      34   →      26    (-23.53%) |        9.76 s  →        7.61 s   (-21.99%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      283.62 ms →      281.36 ms   (-0.80%) |      34   →      26    (-23.53%) |        9.64 s  →        7.32 s   (-24.14%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      283.62 ms →      281.36 ms   (-0.80%) |      34   →      26    (-23.53%) |        9.64 s  →        7.32 s   (-24.14%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       30.98 ms →       27.22 ms  (-12.14%) |      34   →      26    (-23.53%) |        1.05 s  →      707.60 ms  (-32.81%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.45 ms →      226.18 ms   (+1.22%) |      34   →      26    (-23.53%) |        7.60 s  →        5.88 s   (-22.59%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       28.06 ms →       24.12 ms  (-14.02%) |      34   →      26    (-23.53%) |      953.99 ms →      627.20 ms  (-34.25%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.55 ms →        5.38 ms   (-3.14%) |      34   →      26    (-23.53%) |      188.83 ms →      139.87 ms  (-25.93%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.47 ms →       10.38 ms   (-0.88%) |     238   →     182    (-23.53%) |        2.49 s  →        1.89 s   (-24.20%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.71 ms →        9.73 ms   (+0.23%) |     238   →     182    (-23.53%) |        2.31 s  →        1.77 s   (-23.35%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.70 ms →        9.73 ms   (+0.23%) |     238   →     182    (-23.53%) |        2.31 s  →        1.77 s   (-23.35%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.67 ms →       10.67 ms   (+0.03%) |     102   →      78    (-23.53%) |        1.09 s  →      832.52 ms  (-23.50%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.08 ms →       10.11 ms   (+0.32%) |     102   →      78    (-23.53%) |        1.03 s  →      788.48 ms  (-23.28%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.82 ms →       10.09 ms   (-6.77%) |      34   →      26    (-23.53%) |      367.89 ms →      262.27 ms  (-28.71%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      112.24 μs →      113.80 μs   (+1.39%) |      34   →      26    (-23.53%) |        3.82 ms →        2.96 ms  (-22.47%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.01 μs →      108.88 μs   (+1.74%) |      34   →      26    (-23.53%) |        3.64 ms →        2.83 ms  (-22.20%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.33 ms →        5.24 ms   (-1.72%) |       2   →       2              |       10.65 ms →       10.47 ms   (-1.72%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.14 ms →        9.69 ms   (-4.42%) |       6   →       6              |       60.81 ms →       58.13 ms   (-4.42%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.12 ms →        9.63 ms   (-4.90%) |       6   →       6              |       60.75 ms →       57.77 ms   (-4.90%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.12 ms →        9.63 ms   (-4.90%) |       6   →       6              |       60.75 ms →       57.77 ms   (-4.90%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.32 ms →       10.28 ms   (-0.37%) |       3   →       3              |       30.97 ms →       30.85 ms   (-0.37%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.30 ms →       10.05 ms   (-2.46%) |       3   →       3              |       30.91 ms →       30.15 ms   (-2.46%) | 
  ├ sirius::Periodic_function|inner                                     |       10.19 ms →        9.69 ms   (-4.96%) |       2   →       2              |       20.39 ms →       19.38 ms   (-4.96%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.19 ms →        9.68 ms   (-4.97%) |       2   →       2              |       20.37 ms →       19.36 ms   (-4.97%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.19 ms →        9.68 ms   (-4.97%) |       2   →       2              |       20.37 ms →       19.36 ms   (-4.97%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.54 ms →       10.10 ms   (-4.22%) |       1   →       1              |       10.54 ms →       10.10 ms   (-4.22%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.53 ms →       10.03 ms   (-4.83%) |       1   →       1              |       10.53 ms →       10.03 ms   (-4.83%) | 
- └ sirius::finalize                                                    |      184.27 ms →      236.87 ms  (+28.55%) |       1   →       1              |      184.27 ms →      236.87 ms  (+28.55%) | 
  ====================================================================================================================================================================================================
```
