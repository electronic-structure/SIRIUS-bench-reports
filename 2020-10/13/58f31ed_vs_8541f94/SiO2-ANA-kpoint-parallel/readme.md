# Benchmark 8541f94e2e0e288633941ac63ad4d565828afb1d vs 58f31ed08f2b4e9e6d289f9ed116027f00413e03
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      162.44 s  →      133.67 s   (-17.71%) |       1   →       1              |      162.44 s  →      133.67 s   (-17.71%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.76 s    (+0.25%) |       1   →       1              |        2.75 s  →        2.76 s    (+0.25%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        3.21 s    (+7.91%) |       1   →       1              |        2.97 s  →        3.21 s    (+7.91%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      427.45 μs →      243.17 μs  (-43.11%) |       1   →       1              |      427.45 μs →      243.17 μs  (-43.11%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      185.20 ms →      451.50 ms (+143.79%) |       1   →       1              |      185.20 ms →      451.50 ms (+143.79%) | 
- │ │ ├ sirius::Atom_type::init                                         |       80.83 ms →      214.29 ms (+165.12%) |       2   →       2              |      161.66 ms →      428.58 ms (+165.12%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.46 ms →       22.81 ms   (-2.75%) |       1   →       1              |       23.46 ms →       22.81 ms   (-2.75%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.55 ms →        5.45 ms  (-16.80%) |       1   →       1              |        6.55 ms →        5.45 ms  (-16.80%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.86 ms →       17.30 ms   (+2.64%) |       1   →       1              |       16.86 ms →       17.30 ms   (+2.64%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.83 ms →       17.28 ms   (+2.66%) |       1   →       1              |       16.83 ms →       17.28 ms   (+2.66%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (+0.02%) |       1   →       1              |        4.16 ms →        4.16 ms   (+0.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (-0.12%) |       1   →       1              |        2.34 ms →        2.34 ms   (-0.12%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.64 μs →      100.77 μs   (-1.82%) |       1   →       1              |      102.64 μs →      100.77 μs   (-1.82%) | 
  │ └ sirius::Simulation_context::update                                |        2.74 s  →        2.71 s    (-1.22%) |       1   →       1              |        2.74 s  →        2.71 s    (-1.22%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.01 ms →       10.79 ms   (-1.98%) |       1   →       1              |       11.01 ms →       10.79 ms   (-1.98%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.62 ms →        4.35 ms   (-5.97%) |       1   →       1              |        4.62 ms →        4.35 ms   (-5.97%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.40 ms   (+0.89%) |       1   →       1              |        6.35 ms →        6.40 ms   (+0.89%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.38 ms   (+0.91%) |       1   →       1              |        6.33 ms →        6.38 ms   (+0.91%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.90 ms   (+1.78%) |       1   →       1              |        3.83 ms →        3.90 ms   (+1.78%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.50%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.50%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.44 μs →      101.29 μs   (+0.85%) |       1   →       1              |      100.44 μs →      101.29 μs   (+0.85%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.32 ms →       62.98 ms   (+1.07%) |       2   →       2              |      124.63 ms →      125.96 ms   (+1.07%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.13 ms   (+0.02%) |       2   →       2              |       10.27 ms →       10.27 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.48 ms   (+0.28%) |       1   →       1              |        4.46 ms →        4.48 ms   (+0.28%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.79 ms →       21.80 ms   (+0.04%) |       2   →       2              |       43.58 ms →       43.60 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.78 ms →       14.82 ms   (+0.24%) |       2   →       2              |       29.57 ms →       29.64 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.94 ms →       19.75 ms   (-0.92%) |       4   →       4              |       79.75 ms →       79.01 ms   (-0.92%) | 
  │   ├ sddk::Gvec::init                                                |      180.23 ms →      177.21 ms   (-1.68%) |       2   →       2              |      360.47 ms →      354.42 ms   (-1.68%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.00 ms →      134.09 ms   (+0.07%) |       2   →       2              |      268.00 ms →      268.18 ms   (+0.07%) | 
  │   ├ sddk::Gvec_shells                                               |      185.94 ms →      175.15 ms   (-5.80%) |       1   →       1              |      185.94 ms →      175.15 ms   (-5.80%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.35 ms →        1.31 ms   (-2.69%) |       1   →       1              |        1.35 ms →        1.31 ms   (-2.69%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.24 ms →      292.95 ms   (-0.78%) |       2   →       2              |      590.49 ms →      585.90 ms   (-0.78%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       38.82 ms →       35.48 ms   (-8.59%) |       1   →       1              |       38.82 ms →       35.48 ms   (-8.59%) | 
+ │ ├ sirius::K_point::K_point                                          |        3.14 μs →        2.20 μs  (-29.97%) |       4   →       4              |       12.55 μs →        8.79 μs  (-29.97%) | 
  │ └ sirius::K_point_set::initialize                                   |       38.73 ms →       35.38 ms   (-8.65%) |       1   →       1              |       38.73 ms →       35.38 ms   (-8.65%) | 
  │   └ sirius::K_point::initialize                                     |       38.65 ms →       35.29 ms   (-8.68%) |       1   →       1              |       38.65 ms →       35.29 ms   (-8.68%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.99 ms →       18.08 ms   (-9.56%) |       1   →       1              |       19.99 ms →       18.08 ms   (-9.56%) | 
  │     │ └ sddk::Gvec::init                                            |        8.92 ms →        8.05 ms   (-9.72%) |       1   →       1              |        8.92 ms →        8.05 ms   (-9.72%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       12.34 μs →        9.39 μs  (-23.89%) |       1   →       1              |       12.34 μs →        9.39 μs  (-23.89%) | 
  │     └ sirius::K_point::update                                       |       13.11 ms →       12.42 ms   (-5.23%) |       1   →       1              |       13.11 ms →       12.42 ms   (-5.23%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.16 ms   (+1.11%) |       1   →       1              |        6.09 ms →        6.16 ms   (+1.11%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.50 ms →        3.57 ms   (+1.75%) |       1   →       1              |        3.50 ms →        3.57 ms   (+1.75%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.21 ms →        5.20 ms   (-0.32%) |       2   →       2              |       10.43 ms →       10.39 ms   (-0.32%) | 
  ├ sirius::Potential                                                   |      157.36 ms →      158.23 ms   (+0.55%) |       1   →       1              |      157.36 ms →      158.23 ms   (+0.55%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.96 ms →        5.82 ms   (-2.38%) |       6   →       6              |       35.78 ms →       34.92 ms   (-2.38%) | 
  │ └ sirius::Potential::update                                         |      120.84 ms →      122.56 ms   (+1.42%) |       1   →       1              |      120.84 ms →      122.56 ms   (+1.42%) | 
  │   └ sirius::Potential::generate_local_potential                     |      120.07 ms →      121.79 ms   (+1.43%) |       1   →       1              |      120.07 ms →      121.79 ms   (+1.43%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.08 ms →      110.67 ms   (-2.13%) |       1   →       1              |      113.08 ms →      110.67 ms   (-2.13%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.43 ms →       10.21 ms  (+58.83%) |       1   →       1              |        6.43 ms →       10.21 ms  (+58.83%) | 
  ├ sirius::Density                                                     |      130.98 ms →      135.05 ms   (+3.10%) |       1   →       1              |      130.98 ms →      135.05 ms   (+3.10%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.18 ms →        5.15 ms   (-0.59%) |       2   →       2              |       10.36 ms →       10.30 ms   (-0.59%) | 
  │ └ sirius::Density::update                                           |      120.35 ms →      124.48 ms   (+3.43%) |       1   →       1              |      120.35 ms →      124.48 ms   (+3.43%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      119.92 ms →      124.04 ms   (+3.44%) |       1   →       1              |      119.92 ms →      124.04 ms   (+3.44%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       102.67 μs            |                   1              |                       102.67 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.65 ms →      111.69 ms   (-1.72%) |       1   →       1              |      113.65 ms →      111.69 ms   (-1.72%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.81 ms →       11.80 ms (+103.14%) |       1   →       1              |        5.81 ms →       11.80 ms (+103.14%) | 
  ├ sirius::Density::initial_density                                    |      164.26 ms →      177.58 ms   (+8.10%) |       1   →       1              |      164.26 ms →      177.58 ms   (+8.10%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.65 ms →      109.72 ms   (-1.73%) |       1   →       1              |      111.65 ms →      109.72 ms   (-1.73%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.15 ms →       11.46 ms (+122.61%) |       2   →       2              |       10.29 ms →       22.91 ms (+122.61%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.04 ms →       12.38 ms  (+23.37%) |       1   →       1              |       10.04 ms →       12.38 ms  (+23.37%) | 
  ├ sirius::Potential::generate                                         |      573.15 ms →      594.84 ms   (+3.79%) |       1   →       1              |      573.15 ms →      594.84 ms   (+3.79%) | 
  │ ├ sirius::Potential::poisson                                        |      126.80 ms →      136.28 ms   (+7.48%) |       1   →       1              |      126.80 ms →      136.28 ms   (+7.48%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.39 ms →       16.93 ms (+214.02%) |       1   →       1              |        5.39 ms →       16.93 ms (+214.02%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.95 ms →        9.99 ms   (-8.77%) |       1   →       1              |       10.95 ms →        9.99 ms   (-8.77%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.23 ms →        9.82 ms   (-4.01%) |       1   →       1              |       10.23 ms →        9.82 ms   (-4.01%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.23 ms →        9.81 ms   (-4.08%) |       1   →       1              |       10.23 ms →        9.81 ms   (-4.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      559.86 μs →      544.59 μs   (-2.73%) |       2   →       2              |        1.12 ms →        1.09 ms   (-2.73%) | 
  │ ├ sirius::Potential::xc                                             |       51.34 ms →       54.46 ms   (+6.08%) |       1   →       1              |       51.34 ms →       54.46 ms   (+6.08%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.33 ms →       52.14 ms   (+1.57%) |       1   →       1              |       51.33 ms →       52.14 ms   (+1.57%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.66 ms   (-0.69%) |       2   →       2              |       11.40 ms →       11.33 ms   (-0.69%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.51 ms →        5.20 ms   (-5.60%) |       1   →       1              |        5.51 ms →        5.20 ms   (-5.60%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.01 ms →        5.57 ms   (-7.32%) |       1   →       1              |        6.01 ms →        5.57 ms   (-7.32%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.78 ms →       93.61 ms   (+0.90%) |       1   →       1              |       92.78 ms →       93.61 ms   (+0.90%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.67 ms →      302.49 ms   (+3.00%) |       1   →       1              |      293.67 ms →      302.49 ms   (+3.00%) | 
  ├ sirius::Hamiltonian0                                                |        8.76 ms →        8.42 ms   (-3.81%) |       1   →       1              |        8.76 ms →        8.42 ms   (-3.81%) | 
  │ ├ sirius::Local_operator                                            |        8.38 ms →        8.07 ms   (-3.70%) |       1   →       1              |        8.38 ms →        8.07 ms   (-3.70%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.79 ms →        4.80 ms   (+0.30%) |       1   →       1              |        4.79 ms →        4.80 ms   (+0.30%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.65 ms →        2.35 ms  (-11.63%) |       1   →       1              |        2.65 ms →        2.35 ms  (-11.63%) | 
  │ ├ sirius::Non_local_operator                                        |       64.14 μs →       62.86 μs   (-1.99%) |       2   →       2              |      128.27 μs →      125.72 μs   (-1.99%) | 
+ │ ├ sirius::D_operator::initialize                                    |      107.89 μs →       95.00 μs  (-11.95%) |       1   →       1              |      107.89 μs →       95.00 μs  (-11.95%) | 
  │ └ sirius::Q_operator::initialize                                    |       80.53 μs →       75.95 μs   (-5.69%) |       1   →       1              |       80.53 μs →       75.95 μs   (-5.69%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.88 s  →        1.88 s    (-0.23%) |       1   →       1              |        1.88 s  →        1.88 s    (-0.23%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.08 ms →       18.69 ms   (+3.36%) |       1   →       1              |       18.08 ms →       18.69 ms   (+3.36%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      201.59 μs →      181.98 μs   (-9.73%) |       1   →       1              |      201.59 μs →      181.98 μs   (-9.73%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       17.87 ms →       18.50 ms   (+3.51%) |       1   →       1              |       17.87 ms →       18.50 ms   (+3.51%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.86 s  →        1.86 s    (-0.26%) |       1   →       1              |        1.86 s  →        1.86 s    (-0.26%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      131.37 ms →      128.15 ms   (-2.45%) |       4   →       4              |      525.50 ms →      512.61 ms   (-2.45%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       54.01 ms →       52.45 ms   (-2.90%) |       1   →       1              |       54.01 ms →       52.45 ms   (-2.90%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.64 ms →       21.05 ms   (-2.75%) |       1   →       1              |       21.64 ms →       21.05 ms   (-2.75%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      639.33 ms →      636.90 ms   (-0.38%) |       1   →       1              |      639.33 ms →      636.90 ms   (-0.38%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      299.82 ms →      297.91 ms   (-0.63%) |       1   →       1              |      299.82 ms →      297.91 ms   (-0.63%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.93 μs →        3.84 μs   (-2.42%) |       1   →       1              |        3.93 μs →        3.84 μs   (-2.42%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.71 μs →        2.90 μs   (+6.91%) |       1   →       1              |        2.71 μs →        2.90 μs   (+6.91%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      431.00 ns →      411.00 ns   (-4.64%) |       1   →       1              |      431.00 ns →      411.00 ns   (-4.64%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      579.00 ns →      590.00 ns   (+1.90%) |       1   →       1              |      579.00 ns →      590.00 ns   (+1.90%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (+0.06%) |       1   →       1              |        9.22 ms →        9.22 ms   (+0.06%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.07 ms →      121.25 ms   (+0.15%) |       1   →       1              |      121.07 ms →      121.25 ms   (+0.15%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.59 ms →      104.24 ms   (-0.34%) |       2   →       2              |      209.18 ms →      208.48 ms   (-0.34%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.64 ms →       40.44 ms   (+4.65%) |       2   →       2              |       77.28 ms →       80.88 ms   (+4.65%) | 
  │ │ │ ├ sddk::inner                                                   |       38.08 ms                             |       2                          |       76.17 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       31.58 μs                             |       2                          |       63.17 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.89 ms            |                   2              |                        79.77 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        19.50 ns            |                   2              |                        39.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.41 ms            |                   2              |                        78.81 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        15.50 ns            |                   2              |                        31.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       62.20 ms →       57.42 ms   (-7.68%) |       1   →       1              |       62.20 ms →       57.42 ms   (-7.68%) | 
  │ │ ├ sddk::transform                                                 |       31.56 ms                             |       1                          |       31.56 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       13.16 μs                             |       1                          |       13.16 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       12.79 μs                             |       1                          |       12.79 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.76 ms            |                   1              |                        30.76 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.76 ms            |                   1              |                        30.76 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      570.00 ns →      732.00 ns  (+28.42%) |       1   →       1              |      570.00 ns →      732.00 ns  (+28.42%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      152.76 s  →      123.65 s   (-19.05%) |       1   →       1              |      152.76 s  →      123.65 s   (-19.05%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.91 ms →        5.82 ms   (-1.42%) |      19   →      19              |      112.20 ms →      110.60 ms   (-1.42%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        6.90 s  →        4.74 s   (-31.32%) |      22   →      26    (+18.18%) |      151.88 s  →      123.28 s   (-18.83%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.65 ms →        4.52 ms   (-2.70%) |      22   →      26    (+18.18%) |      102.23 ms →      117.56 ms  (+14.99%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.26 ms →        4.16 ms   (-2.46%) |      22   →      26    (+18.18%) |       93.74 ms →      108.06 ms  (+15.28%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      944.20 μs →      965.08 μs   (+2.21%) |      22   →      26    (+18.18%) |       20.77 ms →       25.09 ms  (+20.80%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.42 ms →        2.30 ms   (-5.01%) |      22   →      26    (+18.18%) |       53.29 ms →       59.82 ms  (+12.26%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       64.79 μs →       64.35 μs   (-0.67%) |      44   →      52    (+18.18%) |        2.85 ms →        3.35 ms  (+17.39%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      101.85 μs →       88.46 μs  (-13.14%) |      22   →      26    (+18.18%) |        2.24 ms →        2.30 ms   (+2.65%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       79.76 μs →       79.00 μs   (-0.95%) |      22   →      26    (+18.18%) |        1.75 ms →        2.05 ms  (+17.06%) | 
+ │ │ ├ sirius::Band::solve                                             |        4.93 s  →        2.77 s   (-43.87%) |      22   →      26    (+18.18%) |      108.47 s  →       71.95 s   (-33.67%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      172.99 μs →      153.82 μs  (-11.08%) |      22   →      26    (+18.18%) |        3.81 ms →        4.00 ms   (+5.09%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      165.54 μs →      146.83 μs  (-11.31%) |      22   →      26    (+18.18%) |        3.64 ms →        3.82 ms   (+4.82%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.73 μs →        5.05 μs  (-11.82%) |      22   →      26    (+18.18%) |      125.98 μs →      131.30 μs   (+4.22%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        4.89 s  →        2.61 s   (-46.62%) |      22   →      26    (+18.18%) |      107.62 s  →       67.90 s   (-36.91%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      105.50 ms →       96.19 ms   (-8.83%) |      22   →      26    (+18.18%) |        2.32 s  →        2.50 s    (+7.75%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.23 ms →        7.69 ms  (-16.61%) |     132   →     156    (+18.18%) |        1.22 s  →        1.20 s    (-1.45%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.02 ms →        5.95 ms   (-1.24%) |      22   →      26    (+18.18%) |      132.45 ms →      154.58 ms  (+16.71%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.87 μs →      351.79 μs   (-0.30%) |      22   →      26    (+18.18%) |        7.76 ms →        9.15 ms  (+17.82%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.35 ms →        2.30 ms   (-2.38%) |      44   →      52    (+18.18%) |      103.58 ms →      119.50 ms  (+15.37%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        4.74 s  →        2.47 s   (-47.87%) |      22   →      26    (+18.18%) |      104.38 s  →       64.31 s   (-38.39%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      157.67 ms →      130.15 ms  (-17.45%) |     313   →     271    (-13.42%) |       49.35 s  →       35.27 s   (-28.53%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       65.65 ms →       52.15 ms  (-20.56%) |     313   →     271    (-13.42%) |       20.55 s  →       14.13 s   (-31.22%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.93 μs →        2.00 μs   (+3.58%) |     313   →     271    (-13.42%) |      605.41 μs →      542.92 μs  (-10.32%) | 
! │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.62 μs →        1.73 μs   (+6.77%) |     313   →     271    (-13.42%) |      506.82 μs →      468.54 μs   (-7.55%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      337.36 ns →      362.60 ns   (+7.48%) |     313   →     271    (-13.42%) |      105.59 μs →       98.26 μs   (-6.94%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      602.50 ns →      430.73 ns  (-28.51%) |     313   →     271    (-13.42%) |      188.58 μs →      116.73 μs  (-38.10%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.52 ms →        7.43 ms   (-1.20%) |     313   →     271    (-13.42%) |        2.35 s  →        2.01 s   (-14.46%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       27.91 ms →       23.90 ms  (-14.37%) |     313   →     271    (-13.42%) |        8.74 s  →        6.48 s   (-25.86%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       28.28 ms →       23.33 ms  (-17.53%) |     626   →     542    (-13.42%) |       17.71 s  →       12.64 s   (-28.60%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       45.58 ms →       34.92 ms  (-23.39%) |     313   →     271    (-13.42%) |       14.27 s  →        9.46 s   (-33.67%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        6.32 ms                             |     604                          |        3.82 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.23 μs                             |     604                          |       15.84 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         6.06 ms            |                 516              |                         3.13 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        67.24 ns            |                 516              |                        34.70 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         4.95 ms            |                 516              |                         2.55 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        53.08 ns            |                 516              |                        27.39 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      610.68 μs →      625.37 μs   (+2.41%) |     313   →     271    (-13.42%) |      191.14 ms →      169.48 ms  (-11.34%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.01 ms →        9.77 ms   (-2.44%) |     313   →     271    (-13.42%) |        3.13 s  →        2.65 s   (-15.53%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       24.48 ms                             |     291                          |        7.12 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.10 μs                             |     291                          |        6.14 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        8.54 μs                             |     873                          |        7.46 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.36 ms            |                 245              |                         3.52 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.79 ms            |                 735              |                         3.52 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       11.09 ms →       10.50 ms   (-5.30%) |     313   →     271    (-13.42%) |        3.47 s  →        2.85 s   (-18.01%) | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.78 ms                             |     313                          |        3.38 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.56 μs                             |     313                          |        8.63 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        10.23 ms            |                 271              |                         2.77 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        63.55 ns            |                 271              |                        17.22 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         9.12 ms            |                 271              |                         2.47 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        68.86 ns            |                 271              |                        18.66 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       48.64 ms →       33.74 ms  (-30.64%) |     313   →     271    (-13.42%) |       15.22 s  →        9.14 s   (-39.94%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       64.49 ms →       13.77 ms  (-78.64%) |     298   →     262    (-12.08%) |       19.22 s  →        3.61 s   (-81.22%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       57.18 ms                             |     298                          |       17.04 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.91 μs                             |     298                          |        4.74 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.96 μs                             |     596                          |        5.94 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        12.44 ms            |                 252              |                         3.14 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         6.22 ms            |                 504              |                         3.13 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        7.27 ms →        1.63 ms  (-77.63%) |     298   →     252    (-15.44%) |        2.17 s  →      409.92 ms  (-81.08%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       35.90 ms →       74.92 ms (+108.69%) |      79   →      53    (-32.91%) |        2.84 s  →        3.97 s   (+40.01%) | 
  │ │ │ │     ├ sddk::transform                                         |       35.45 ms                             |      79                          |        2.80 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |        8.12 μs                             |      79                          |      641.85 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       10.58 μs                             |      79                          |      835.72 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        49.41 ms            |                  80              |                         3.95 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        36.94 ms            |                 107              |                         3.95 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      436.09 ns →      592.12 ns  (+35.78%) |      22   →      26    (+18.18%) |        9.59 μs →       15.39 μs  (+60.46%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       28.34 μs →       29.98 μs   (+5.76%) |      22   →      26    (+18.18%) |      623.51 μs →      779.36 μs  (+24.99%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      622.84 μs →      587.67 μs   (-5.65%) |      22   →      26    (+18.18%) |       13.70 ms →       15.28 ms  (+11.51%) | 
- │ │ ├ sirius::Density::generate                                       |      784.00 ms →      770.75 ms   (-1.69%) |      22   →      26    (+18.18%) |       17.25 s  →       20.04 s   (+16.18%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      402.25 ms →      401.30 ms   (-0.24%) |      22   →      26    (+18.18%) |        8.85 s  →       10.43 s   (+17.90%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.74 μs →        8.30 μs   (-5.00%) |      22   →      26    (+18.18%) |      192.17 μs →      215.75 μs  (+12.27%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.77 μs →        7.73 μs   (-0.49%) |      22   →      26    (+18.18%) |      170.93 μs →      201.01 μs  (+17.60%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.82 ms →      100.23 ms   (+0.41%) |      22   →      26    (+18.18%) |        2.20 s  →        2.61 s   (+18.67%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.35 μs →        7.28 μs   (-0.94%) |      22   →      26    (+18.18%) |      161.73 μs →      189.34 μs  (+17.07%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.07%) |      22   →      26    (+18.18%) |      156.57 ms →      185.16 ms  (+18.26%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.73 ms →       91.19 ms   (+0.50%) |      22   →      26    (+18.18%) |        2.00 s  →        2.37 s   (+18.78%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      861.68 ns →      733.27 ns  (-14.90%) |      22   →      26    (+18.18%) |       18.96 μs →       19.07 μs   (+0.57%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.27 ms →      162.71 ms   (-0.95%) |      22   →      26    (+18.18%) |        3.61 s  →        4.23 s   (+17.06%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.81%) |      22   →      26    (+18.18%) |       36.08 ms →       42.99 ms  (+19.14%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.37 ms   (+0.06%) |      22   →      26    (+18.18%) |        1.94 s  →        2.30 s   (+18.26%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms →       88.15 ms   (+0.07%) |      22   →      26    (+18.18%) |        1.94 s  →        2.29 s   (+18.27%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      287.00 ms →      274.24 ms   (-4.45%) |      22   →      26    (+18.18%) |        6.31 s  →        7.13 s   (+12.93%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      287.00 ms →      274.24 ms   (-4.44%) |      22   →      26    (+18.18%) |        6.31 s  →        7.13 s   (+12.93%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.41 ms →       23.78 ms  (-16.31%) |      22   →      26    (+18.18%) |      625.07 ms →      618.25 ms   (-1.09%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.69 ms →      225.98 ms   (-2.04%) |      22   →      26    (+18.18%) |        5.08 s  →        5.88 s   (+15.77%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.75 ms →       23.28 ms  (-12.97%) |      22   →      26    (+18.18%) |      588.53 ms →      605.35 ms   (+2.86%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.05 ms →       82.90 ms   (+1.04%) |      22   →      26    (+18.18%) |        1.81 s  →        2.16 s   (+19.41%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.11 ms →        8.73 ms   (-4.18%) |      22   →      26    (+18.18%) |      200.34 ms →      226.87 ms  (+13.24%) | 
- │ │ ├ sirius::Density::mix                                            |      209.24 ms →      217.96 ms   (+4.17%) |      22   →      26    (+18.18%) |        4.60 s  →        5.67 s   (+23.11%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      960.64 μs →      968.21 μs   (+0.79%) |      22   →      26    (+18.18%) |       21.13 ms →       25.17 ms  (+19.11%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |       10.40 ms →       10.71 ms   (+2.99%) |     274   →     334    (+21.90%) |        2.85 s  →        3.58 s   (+25.54%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.91 ms →       10.36 ms   (+4.54%) |     274   →     334    (+21.90%) |        2.72 s  →        3.46 s   (+27.43%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.91 ms →       10.36 ms   (+4.54%) |     274   →     334    (+21.90%) |        2.72 s  →        3.46 s   (+27.43%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.66 ms →        5.95 ms  (-10.65%) |      22   →      26    (+18.18%) |      146.55 ms →      154.74 ms   (+5.59%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.81 ms →        5.14 ms  (-11.56%) |      22   →      26    (+18.18%) |      127.82 ms →      133.59 ms   (+4.52%) | 
- │ │ ├ sirius::Potential::generate                                     |      560.32 ms →      577.35 ms   (+3.04%) |      22   →      26    (+18.18%) |       12.33 s  →       15.01 s   (+21.77%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      126.89 ms →      136.51 ms   (+7.58%) |      22   →      26    (+18.18%) |        2.79 s  →        3.55 s   (+27.14%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.66 ms →       16.72 ms (+195.37%) |      22   →      26    (+18.18%) |      124.56 ms →      434.82 ms (+249.08%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.75 ms →       10.40 ms   (-3.25%) |      22   →      26    (+18.18%) |      236.58 ms →      270.49 ms  (+14.34%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.30 ms →       10.02 ms   (-2.73%) |      22   →      26    (+18.18%) |      226.53 ms →      260.41 ms  (+14.96%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.30 ms →       10.02 ms   (-2.73%) |      22   →      26    (+18.18%) |      226.51 ms →      260.39 ms  (+14.96%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      562.09 μs →      548.05 μs   (-2.50%) |      44   →      52    (+18.18%) |       24.73 ms →       28.50 ms  (+15.23%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       46.59 ms →       48.82 ms   (+4.80%) |      22   →      26    (+18.18%) |        1.02 s  →        1.27 s   (+23.85%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.59 ms →       46.49 ms   (-0.21%) |      22   →      26    (+18.18%) |        1.02 s  →        1.21 s   (+17.93%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.99 ms →        3.01 ms   (+0.83%) |      44   →      52    (+18.18%) |      131.52 ms →      156.72 ms  (+19.16%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.50 ms →        5.19 ms   (-5.74%) |      22   →      26    (+18.18%) |      121.10 ms →      134.90 ms  (+11.40%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.66 ms →        6.32 ms   (-5.04%) |      22   →      26    (+18.18%) |      146.54 ms →      164.45 ms  (+12.22%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.05 ms →       90.93 ms   (-0.13%) |      22   →      26    (+18.18%) |        2.00 s  →        2.36 s   (+18.03%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.70 ms →      292.39 ms   (+1.98%) |      22   →      26    (+18.18%) |        6.31 s  →        7.60 s   (+20.53%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      292.05 ms →      281.26 ms   (-3.70%) |      22   →      26    (+18.18%) |        6.43 s  →        7.31 s   (+13.81%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      292.05 ms →      281.26 ms   (-3.70%) |      22   →      26    (+18.18%) |        6.43 s  →        7.31 s   (+13.81%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       30.45 ms →       27.30 ms  (-10.36%) |      22   →      26    (+18.18%) |      669.94 ms →      709.75 ms   (+5.94%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      230.11 ms →      226.52 ms   (-1.56%) |      22   →      26    (+18.18%) |        5.06 s  →        5.89 s   (+16.34%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.73 ms →       23.62 ms  (-14.82%) |      22   →      26    (+18.18%) |      610.03 ms →      614.13 ms   (+0.67%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.55 ms →        5.30 ms   (-4.61%) |      22   →      26    (+18.18%) |      122.19 ms →      137.75 ms  (+12.73%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.70 ms →       10.39 ms   (-2.88%) |     154   →     182    (+18.18%) |        1.65 s  →        1.89 s   (+14.77%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |       10.17 ms →        9.91 ms   (-2.60%) |     154   →     182    (+18.18%) |        1.57 s  →        1.80 s   (+15.11%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.17 ms →        9.91 ms   (-2.60%) |     154   →     182    (+18.18%) |        1.57 s  →        1.80 s   (+15.11%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.54 ms →       11.15 ms   (+5.80%) |      66   →      78    (+18.18%) |      695.68 ms →      869.82 ms  (+25.03%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.06 ms →       10.69 ms   (+6.34%) |      66   →      78    (+18.18%) |      663.64 ms →      834.05 ms  (+25.68%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        9.92 ms →       10.13 ms   (+2.02%) |      22   →      26    (+18.18%) |      218.35 ms →      263.27 ms  (+20.57%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      169.12 μs →      113.27 μs  (-33.03%) |      22   →      26    (+18.18%) |        3.72 ms →        2.94 ms  (-20.85%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      164.56 μs →      108.27 μs  (-34.21%) |      22   →      26    (+18.18%) |        3.62 ms →        2.81 ms  (-22.25%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.90 ms →        5.21 ms  (-24.42%) |       2   →       2              |       13.80 ms →       10.43 ms  (-24.42%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.61 ms →       11.50 ms   (+8.43%) |       6   →       6              |       63.65 ms →       69.01 ms   (+8.43%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.59 ms →        9.85 ms   (-7.01%) |       6   →       6              |       63.57 ms →       59.11 ms   (-7.01%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.59 ms →        9.85 ms   (-7.01%) |       6   →       6              |       63.57 ms →       59.11 ms   (-7.01%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |       10.07 ms →       12.37 ms  (+22.81%) |       3   →       3              |       30.20 ms →       37.10 ms  (+22.81%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.06 ms →       10.52 ms   (+4.58%) |       3   →       3              |       30.18 ms →       31.56 ms   (+4.58%) | 
  ├ sirius::Periodic_function|inner                                     |       10.56 ms →       11.19 ms   (+5.97%) |       2   →       2              |       21.13 ms →       22.39 ms   (+5.97%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.56 ms →        9.67 ms   (-8.40%) |       2   →       2              |       21.11 ms →       19.34 ms   (-8.40%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.56 ms →        9.67 ms   (-8.40%) |       2   →       2              |       21.11 ms →       19.34 ms   (-8.40%) | 
- ├ sirius::Smooth_periodic_function|inner                              |       10.09 ms →       12.12 ms  (+20.16%) |       1   →       1              |       10.09 ms →       12.12 ms  (+20.16%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.08 ms →       10.48 ms   (+4.00%) |       1   →       1              |       10.08 ms →       10.48 ms   (+4.00%) | 
- └ sirius::finalize                                                    |      183.49 ms →      231.46 ms  (+26.14%) |       1   →       1              |      183.49 ms →      231.46 ms  (+26.14%) | 
  ====================================================================================================================================================================================================
```
